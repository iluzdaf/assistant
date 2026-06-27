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

- [ ] owner/repo issue 123 - needs clarification: short reason human input is needed - https://github.com/owner/repo/issues/123
- [ ] owner/repo - Repository-level reason human input is needed - https://github.com/owner/repo
```

## Update Rules

- Add one unchecked checkbox line per issue that needs human intervention.
- Add one unchecked checkbox line per repository when repository-level intervention is needed, such as a missing or unreadable workflow doc.
- Include the repository, issue number when available, short reason, and source URL.
- Use `needs clarification` wording for clarification-only issues and `needs approval` wording only for issues that specifically require approval.
- If the issue or repository URL is already present, update the reason instead of adding a duplicate line.
- Leave completed checkbox lines checked; do not re-add them unless the source issue has new relevant activity.
