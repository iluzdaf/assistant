# GitHub Issue Triage

- Use this reference for the product issue triage job's GitHub reads and writes.

## Access

- Use GitHub access with the narrowest permissions that can read issues, read issue comments, read repository contents for the workflow doc, update issues, create issue comments when required, and add or remove labels.
- Process only repositories listed in the product issue triage job's `Configuration` section.
- Process all open issues in each configured repository, then select issues using the product repository workflow doc.
- Resolve the workflow doc as `PRODUCT_REPO/docs/agent-workflow.md` for each configured product repository. This path is not inside the assistant repository.
- Treat label meaning and workflow transitions as product-repository rules, not assistant-owned rules.
- Never remove or replace a workflow-defined human-gate label, or add a forward-progress label that moves an issue past a human gate; humans must explicitly perform the product workflow's required gate action.

## GitHub Skill First

- Prefer the GitHub skill / connected GitHub app for repository issue lookup, issue updates, issue comments when required, labels, and repository content reads.
- For issue scans, use a repo-scoped connector issue-list path first:
  - list open issues for the configured `owner/repo` only
  - request issue number, title, body, labels, URL, and updated timestamp
  - fetch comments only for issues selected by the workflow doc
  - keep the connector result tied to the configured repository before applying labels, comments, or Bear review-card updates
- Use local `gh` only when the GitHub connector does not cover a required operation or when diagnosing local authentication.
- When falling back to `gh`, record the reason in the run log.
- Keep connector state and any fallback command results aligned before writing issue comments or labels.

## Fallback `gh` Shapes

- Replace label placeholders with labels named by the product repository workflow doc.
- Edit issue bodies only when the product repository workflow explicitly allows body edits; otherwise prefer comments so the original intake record stays intact.

```sh
gh issue list --repo owner/repo --state open --json number,title,body,labels,url,updatedAt
gh issue view 123 --repo owner/repo --comments --json number,title,body,comments,labels,url,updatedAt
gh api repos/owner/repo/contents/docs/agent-workflow.md --jq .content
gh issue edit 123 --repo owner/repo --body-file /path/to/body.md
gh issue comment 123 --repo owner/repo --body-file /path/to/comment.md
gh issue edit 123 --repo owner/repo --add-label workflow-defined-label
```

## Workflow Doc Reads

- Prefer repository content reads through the GitHub skill / connected GitHub app.
- Decode GitHub content API `content` values before using workflow docs for agent processing when using a raw API fallback.
- Read `PRODUCT_REPO/docs/agent-workflow.md` before selecting issue labels or applying issue updates.
- If the configured workflow doc is missing or unreadable, add or update the repository in the Bear review card with the missing-doc evidence and skip issue processing for that repository.

## Idempotency

- Check the Bear review card before adding human-intervention links so issue URLs are not duplicated.
- Do not duplicate direct source issue updates when the product repository workflow or source issue history already shows the same work was completed.
- Apply labels only after required source issue updates succeed, unless the product repository workflow says otherwise.
- Apply label changes defined by the product repository workflow doc, including adding workflow-defined gate labels when the item is ready for a human decision or otherwise needs human intervention.
- Do not remove or replace workflow-defined human-gate labels, and do not advance work past a human gate unless the product workflow's required human action has already happened.
