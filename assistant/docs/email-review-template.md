# Email Review Template

- Template for email review note sections.
- Keep one section per email that needs review, except repeated CI or build notifications for one pull request.
- For CI or build notifications tied to a pull request, keep one grouped section per repository and PR, then append repeated alert emails to that section.
- Keep date sections in newest-first order, with the latest date at the top.
- Keep only open review items in this note; remove each section independently after that section's checkbox actions are complete and the corresponding email is archived.

````md
# Emails Needing Review

## YYYY-MM-DD

### Short email subject

- From: sender name
- Date: YYYY-MM-DD
- Email: Gmail message id, subject, or other source reference

#### Summary

- One or two lines on what the email says.

#### Why it needs review

- Why this needs your attention.

#### Recommended next step

- [ ] Review action

- [ ] reply: Requested draft change.

- [ ] Send reply

```md
Draft the reply here.
```

- Use `Review action` for non-reply follow-up.
- Use `reply:` checkbox lines for requested draft edits, such as `- [ ] reply: Suggest a free timeslot on Sunday instead.`
- Tick a `reply:` checkbox only after that edit is reflected in the fenced draft.
- A checked `reply:` checkbox is already handled and can be ignored on later runs.
- Use `Send reply` only when the fenced draft should be sent.
- Use the fenced block only when the email needs a reply draft.
- Edit the fenced block directly when revising the reply.
- Treat unchecked `reply:` changes as incomplete until the fenced draft reflects them.
- Do not treat `reply:` checkboxes as approval to send.
- Do not send the reply until `Send reply` is checked.
- In Bear, an unchecked box is `- [ ]` and a checked box is `- [x]`.
- In this workflow, a checked box means the requested action is already complete.
- If a section still has any unchecked boxes, that section stays open.
- Other completed sections in the same note should still be removed once their own checkbox actions are complete and archived.

#### Notes

- Any extra context or deadline.

#assistant/email/needs-review
````

For grouped CI/build failure notifications, use the same structure with a PR-scoped heading and repeated message references:

````md
## YYYY-MM-DD

### repo-name PR #123 CI failures

- From: CI sender name
- Date: first alert YYYY-MM-DD; latest alert YYYY-MM-DD
- Email:
  - Gmail message id or subject for first alert
  - Gmail message id or subject for repeated alert
- PR: repository PR URL

#### Summary

- The PR has repeated CI or build notifications for the same failure stream.

#### Why it needs review

- The current PR CI state needs review without creating one note section per alert email.

#### Recommended next step

- [ ] Review the PR's current CI state and decide whether action is needed.

#### Notes

- Latest failing or recovered run details, with dates and run URLs when available.

#assistant/email/needs-review
````

- Use the grouped CI/build shape only when the notifications share the same repository and PR number, PR URL, branch, or stable build-thread identifier.
- Add later failure or recovery notifications for the same PR to the existing grouped section instead of creating a new section.
- Archive every corresponding Gmail message when the grouped section's checkbox actions are complete and the section is removed.
