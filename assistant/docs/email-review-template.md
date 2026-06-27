# Email Review Template

- Template for email review note sections.
- Keep one section per email that needs review.
- Keep date sections in newest-first order, with the latest date at the top.
- Keep only open review items in this note; remove a section after its checkbox actions are complete and the corresponding email is archived.

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
- If a note still has any unchecked boxes, the note is still open.

#### Notes

- Any extra context or deadline.

#assistant/email/needs-review
````
