# Product Issue Review Card Template

- Use this template for the single Bear card that collects product issues needing human intervention.
- Do not create one Bear note per product issue.

## Title

```md
Product Issues Needing Review
```

## Tags

```md
#assistant/issue-triage
#needs-review
```

## Body

```md
# Product Issues Needing Review

## Issues

- [ ] owner/repo#123 - Short reason human input is needed - https://github.com/owner/repo/issues/123
```

## Update Rules

- Add one unchecked checkbox line per issue that needs human intervention.
- Include the repository, issue number, short reason, and source issue URL.
- If the issue URL is already present, update the reason instead of adding a duplicate line.
- Leave completed checkbox lines checked; do not re-add them unless the source issue has new relevant activity.
