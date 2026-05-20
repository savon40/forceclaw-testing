# ForceClaw - Tester Feedback

This repo is for reporting bugs and unexpected behavior you hit while testing ForceClaw.

**File issues here, not in Slack.** A well-formed issue lets us pull the exact log lines for your bug and fix it the same day. A vague one ("the bot was weird this
morning") can take an hour just to track down which run you mean.

---

## Two things every issue MUST include

1. **Timestamp with timezone** - e.g. `2026-05-19 14:32 ET` or `2026-05-19 18:32 UTC`. We pull logs by UTC hour, so without a time we are searching blind. "This
morning" is not a time.
2. **What you typed to the bot** - paste the exact message, verbatim. This is how we find your specific job in the logs. If you had a back-and-forth, paste the whole
thread.

If you give us those two and nothing else, we can usually figure out the rest. Everything below makes it faster.

---

## The full template (copy-paste, fill in)

```
**When:** 2026-05-19 14:32 ET
**Where:** Slack / Teams / Web dashboard
**Your email:** you@company.com
**Org name:** Acme Sandbox (if Salesforce-related)
**Job ID:** abc12345 (from the dashboard URL if you have it - optional)

**What I typed to the bot:**
> paste your message verbatim

**What I expected:**
The bot would do X.

**What actually happened:**
The bot did Y.

**Steps to reproduce (if it is reproducible):**
1. ...
2. ...
3. ...

**Screenshot / screen recording:**
(drag and drop into the issue)
```

---

## Finding the Job ID (optional but helpful)

If your bug came from a job (anything the bot worked on), you can grab the Job ID:

1. Go to https://forceclaw.ai/app/jobs
2. Find the row that matches your bug
3. Click into it - the URL will look like `/app/jobs/abc12345-...`
4. Copy that ID into the issue

With a Job ID we can pull the exact logs, the conversation history, the tool calls, and the cost in seconds.

---

## Screenshots

For UI bugs in the dashboard: full-page screenshot, please. We need to see the surrounding state, not just the broken element.

For Slack / Teams bugs: screenshot the whole thread including the timestamp Slack shows in the corner. That timestamp + your workspace name lets us find the exact
message.

For agent-output bugs (the bot built the wrong thing, hallucinated, refused something it should have done): paste the bot's reply as text so we can grep it, then
screenshot for context.

---

## Labels we use

When you file an issue, pick one severity and one or more area labels:

**Severity** (pick one):
- `p0-broken` - blocks all testers, ship a fix today
- `p1-broken-for-some` - one workflow is broken, others work
- `p2-annoying` - works but wrong / ugly / slow
- `p3-nit` - polish, copy, edge case

**Area** (pick all that apply):
- `slack` / `teams` / `web` - which surface
- `agent` - bot output, hallucination, wrong tool call
- `salesforce` - SF auth, metadata, deploy
- `git` - PR creation, branch issues
- `billing` - Stripe, credits, seats
- `auth` - login, MFA, OAuth

---

## What happens after you file

1. We read the issue.
2. We pull the Papertrail logs for your timestamp window from S3.
3. We grep for your email / job ID / message text.
4. We either fix it and close the issue with the commit, or come back with a clarifying question.

Most fixes ship within a day. If your issue sits open for more than a week, ping in `#forceclaw-testing` on Slack.

---

## What this repo is NOT for

- Feature requests - file those in `#forceclaw-ideas` on Slack.
- Questions about how to use the bot - file those in `#forceclaw-help`.
- Salesforce data issues that are not bugs (e.g. "this field has wrong values in our org") - those are not ForceClaw bugs.
