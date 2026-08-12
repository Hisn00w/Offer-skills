# Email monitoring workflow

Use this reference when the user asks Offer-skills to read recruitment notifications from a mailbox or to check for updates on a schedule.

## Required user input

Collect:

- Email provider or webmail name, such as Gmail, Outlook, QQ Mail, 163 Mail, or a school mailbox.
- Login email address.
- Optional company names, job titles, keywords, or date range to narrow the search.
- For recurring checks, the preferred daily check time and whether the user wants a notification only when a record changes.

The login email identifies the account. Let the user complete password, MFA, CAPTCHA, or other sign-in steps in the browser.

## Browser workflow

1. Select the browser surface requested by the user. If none is named, use the default browser surface.
2. Navigate to the official webmail site for the named provider.
3. If authentication is required, ask the user to sign in in that browser and continue only after the mailbox is ready.
4. Search recent mail using company names, recruitment keywords, application subjects, or sender names. Prioritize unread/new mail since the previous check.
5. Read only the visible message metadata and content needed to identify an application update.
6. Normalize each message into date, company, position, status, next step, and note. Use the exact visible status when possible.
7. Merge duplicate confirmations for the same company and position. A later rejection, assessment, interview, or offer message supersedes an earlier “application received” message.
8. Update the Desktop copy of `秋招投递进度.html`, then report the changed records and the saved path.

## Status mapping

| Mail signal | Tracker status |
|---|---|
| application received, application submitted | 简历已投递 / 已投递 |
| assessment invitation, online test | 待笔试 / 测评中 |
| resume screening, evaluation in progress | 简历筛选中 / 评估中 |
| interview invitation | 一面 / 二面 / HR面 |
| offer or successful hiring | Offer |
| rejection, not selected, process terminated | 拒绝 / 已结束 |

Do not infer an interview, offer, or rejection from a generic acknowledgement. Use `简历已投递` or `待确认` when the message does not establish a later stage.

## Recurring monitor

When the user asks for daily checking:

- Use `codex_app__automation_update` rather than writing a raw cron, RRULE, or automation directive.
- Prefer a heartbeat automation attached to the current task. Reuse a matching existing automation instead of creating a duplicate.
- Put the provider, login email, Desktop tracker path, search scope, and update/report behavior in the automation prompt. Never put a password or verification code in the prompt.
- If no time is specified, ask for the preferred daily check time before creating the automation.
- On each run, check only new application-related mail, update the tracker, and report “无新增进度” when nothing changed.
