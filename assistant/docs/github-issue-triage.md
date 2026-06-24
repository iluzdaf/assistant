# GitHub Issue Triage

- Use this reference for the product issue triage job's GitHub reads and writes.

## Access

- Use GitHub access with the narrowest permissions that can read issues, read issue comments, read repository contents for the workflow doc, update issues, create issue comments when required, and add or remove labels.
- Process only repositories listed in the product issue triage job's `Configuration` section.
- Process only open issues selected by the configured labels.

## GitHub Skill First

- Prefer the GitHub skill / connected GitHub app for repository issue lookup, issue updates, issue comments when required, labels, and repository content reads.
- Use local `gh` only when the GitHub connector does not cover a required operation or when diagnosing local authentication.
- When falling back to `gh`, record the reason in the run log.
- Keep connector state and any fallback command results aligned before writing issue comments or labels.

## Fallback `gh` Shapes

```sh
gh issue list --repo owner/repo --state open --label needs-triage --json number,title,body,labels,url,updatedAt
gh issue view 123 --repo owner/repo --comments --json number,title,body,comments,labels,url,updatedAt
gh api repos/owner/repo/contents/docs/agent-workflow.md --jq .content
gh issue edit 123 --repo owner/repo --body-file /path/to/body.md
gh issue comment 123 --repo owner/repo --body-file /path/to/comment.md
gh issue edit 123 --repo owner/repo --remove-label needs-triage --add-label agent-done
```

## Workflow Doc Reads

- Prefer repository content reads through the GitHub skill / connected GitHub app.
- Decode GitHub content API `content` values before using workflow docs for agent processing when using a raw API fallback.
- If the configured workflow doc is missing, add or update the issue in the Bear review card with the missing-doc evidence.

## Idempotency

- Check the Bear review card before adding human-intervention links so issue URLs are not duplicated.
- Do not duplicate direct source issue updates when the product repository workflow or source issue history already shows the same work was completed.
- Apply labels only after required source issue updates succeed, unless the product repository workflow says otherwise.
