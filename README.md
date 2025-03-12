# Gmail Auto-Reply Script with Approval

This Google Apps Script automates email replies while allowing manual approval before sending responses.

## Features
- Finds emails matching specified criteria.
- Marks them for manual approval before sending replies.
- Prevents duplicate replies.
- Supports automatic labeling of replied emails.
- Optional auto-run every 30 minutes to check for new emails.

## How to Use
### 1. Set Up the Script
1. Open [Google Apps Script](https://script.google.com/).
2. Create a new project.
3. Copy and paste the script into the editor.
4. Customize the `EMAIL_CRITERIA` and `AUTO_REPLY_TEXT`.
5. Save the script.

### 2. Approve Emails for Reply
- Run `findEmailsForApproval()` to identify emails matching the criteria.
- Emails will be labeled as **Pending-Auto-Reply** in Gmail.
- Review emails in Gmail by searching for `label:Pending-Auto-Reply`.

### 3. Send Approved Replies
- Once reviewed, run `sendApprovedReplies()` to send replies to approved emails.
- Replied emails will be marked as read and labeled as **Automated-Reply** (if enabled).

### 4. Enable Automatic Email Finding (Optional)
- Run `setupAutomaticFinding()` to check for new emails every 30 minutes.
- You still need to manually run `sendApprovedReplies()` to send responses.

## Configuration
Edit these values in the script to customize its behavior:
```javascript
const EMAIL_CRITERIA = {
  unread: true,
  newer_than_days: 1,
  from_contains: "",
  subject_contains: "",
  body_contains: "kaisa hai bhai",
  label: ""
};

const AUTO_REPLY_TEXT = `Hello,\n\nThank you for your email. I've received your message and will get back to you within 24-48 hours.\n\nBest regards,\nDheeraj Nair`;

const MARK_AS_READ = true;
const APPLY_LABEL = "Automated-Reply";
const CREATE_LABEL_IF_NOT_EXISTS = true;
const PENDING_APPROVAL_LABEL = "Pending-Auto-Reply";
const DEBUG_MODE = true;
```

## Troubleshooting
- Run `listAllLabels()` to see all Gmail labels.
- If replies aren't sent, ensure emails are correctly labeled as **Pending-Auto-Reply**.
- Check **Gmail search filters** to ensure correct matches.

## License
This script is provided as-is without any warranty. Use at your own risk.
