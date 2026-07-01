# Product Issue Review Card Template

- Use this template for the single Bear card that collects product issues or repositories needing human intervention.
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

- [ ] [owner/repo](https://github.com/owner/repo)
  - Status: repository-level review needed
  - Summary: short reason human input is needed.
```

## Update Rules

- Add one unchecked checkbox item per issue that needs human intervention.
- Format the checkbox label as a Markdown link to the source issue, using `owner/repo issue 123` as the link text.
- Under each issue checkbox, add indented bullets for `Status` and `Summary`.
- Add one unchecked checkbox item per repository when repository-level intervention is needed, such as a missing or unreadable workflow doc.
- Format repository-level checkbox labels as Markdown links to the repository.
- Include the repository, issue number when available, product-workflow status, source URL, and a short summary of what needs human review.
- Use `needs clarification` wording for clarification-only issues and `needs approval` wording only for issues that specifically require approval.
- If the issue or repository URL is already present, update the existing item instead of adding a duplicate block.
- Leave completed checkbox lines checked; do not re-add them unless the source issue has new relevant activity.
