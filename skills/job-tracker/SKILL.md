---
name: job-tracker
description: Go through the user's TakeMeUp job tracker — what's waiting for a reply, which follow-ups are due, what to update — and keep it current (add jobs, change status, set follow-up dates and notes). Use when the user asks about their applications, follow-ups, or job-search progress.
---

# Job tracker with TakeMeUp

Use the TakeMeUp MCP tools. If the user isn't signed in, tell them to run `/mcp`, choose **takemeup** and sign in.

1. `list_my_takemeup_applications`. Summarise by status — saved, applied, interviewing, offer, rejected — with counts, then list what needs attention first:
   - follow-ups due today or overdue (`nextActionAt`);
   - applications sent more than two weeks ago with no reply (`sentAt` set, no `firstResponseAt`);
   - saved jobs the user hasn't applied to yet.
2. For any single application the user asks about, `get_takemeup_application` gives notes and the job description.
3. Keep it current, only with the user's say-so:
   - a reply or rejection came in → `update_takemeup_application` with the new `status`;
   - a follow-up to plan → `nextActionAt` (yyyy-mm-dd) and `nextActionNote`;
   - a new job → `add_takemeup_application` (with `cvId` and `jobDescription` when they're applying with a TakeMeUp CV).
   Deleting an application isn't possible from here; the user can do it on the tracker page (the link is in the results).
4. If adding fails because the free limit is reached, say so plainly: free accounts track up to 5 applications, PRO has no limit.

Offer to draft a short, polite follow-up email for any overdue application, using the role and company from the tracker.
