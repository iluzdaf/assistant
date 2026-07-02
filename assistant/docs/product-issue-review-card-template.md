# Product Issue Review Card Template

- Use this template for the single Bear card that collects product issues, PRs, or repositories needing human intervention.
- Do not create one Bear note per product issue.

## Title

```md
Product Issues Needing Review
```

## Tags

```md
#assistant/issue-triage
```

## Body

```md
# Product Issues Needing Review

## Issues

- [ ] [owner/repo issue 123](https://github.com/owner/repo/issues/123)
  - Status: needs clarification
  - Summary: short reason human input is needed.

## PRs

- [ ] [owner/repo PR 456](https://github.com/owner/repo/pull/456)
  - Status: needs plan approval
  - Summary: short reason human review is needed.

- [ ] [owner/repo](https://github.com/owner/repo)
  - Status: repository-level review needed
  - Summary: short reason human input is needed.
```

## Update Rules

- Add one unchecked checkbox item per issue that needs human intervention.
- Format the checkbox label as a Markdown link to the source issue, using `owner/repo issue 123` as the link text.
- Under each issue checkbox, add indented bullets for `Status` and `Summary`.
- Add one unchecked checkbox item per PR labeled `needs-plan-approval` or `needs-review`.
- Format the checkbox label as a Markdown link to the source PR, using `owner/repo PR 456` as the link text.
- Under each PR checkbox, add indented bullets for `Status` and `Summary`.
- Add one unchecked checkbox item per repository when repository-level intervention is needed, such as a missing or unreadable workflow doc.
- Format repository-level checkbox labels as Markdown links to the repository.
- Include the repository, issue or PR number when available, product-workflow status, source URL, and a short summary of what needs human review.
- Use `needs clarification` wording for clarification-only issues and `needs approval` wording only for issues that specifically require approval.
- Use `needs plan approval` wording only for PRs that need plan approval.
- Use `needs review` wording only for PRs that specifically require final human PR review.
- If the issue, PR, or repository URL is already present, update the existing item instead of adding a duplicate block.
- Leave completed checkbox lines checked; do not re-add them unless the source issue has new relevant activity.
- Leave completed PR checkbox lines checked; do not re-add them unless the source PR has new relevant activity or returns to `needs-plan-approval` or `needs-review`.
