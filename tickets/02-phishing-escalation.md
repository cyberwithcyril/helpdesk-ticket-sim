# Ticket write-up: Phishing click escalated to Security

| | |
| --- | --- |
| **Ticket** | "I clicked a link in a weird email" |
| **Reporter** | Maria Lopez, Sales |
| **Request type** | Report a Suspicious Email (Incident) |
| **Priority** | High (P2); defensible as P1 because credentials were entered |
| **Outcome** | Contained at tier 1, **escalated to Security**, left open for their review |

## What the user said
> Got an email saying my mailbox was full, clicked the link and it asked me to log in. I typed my password. Did I mess up?

## Reply to customer (sent immediately)
> Thanks for reporting this fast. That's exactly the right move. Please turn off Wi-Fi or unplug your network cable now, and don't sign in to anything else. Did you type your password on that page or download anything?

## Containment (tier 1)
- User disconnected from the network.
- Password reset; all sessions revoked in Entra ID.
- Confirmed MFA is registered only to the user's own phone.
- Original email saved for analysis.

## Handoff note (internal)
> **Reported:** Clicked a link in an email saying her mailbox was full; entered her password on the page that opened.
> **Impact:** Credentials likely compromised; one device possibly exposed.
> **Actions taken:** User disconnected. Password reset, all sessions revoked, MFA confirmed. Email saved.
> **Not yet checked:** Sign-in logs for unfamiliar locations; whether others received the same email.
> **Why escalating:** Credential phishing is a security incident; needs log review and possibly blocking the sender or domain.
> **User contact:** At her desk, reachable by phone.

## Reply to customer (after escalation)
> I've reset your password and signed you out of all sessions to be safe. Our security team is reviewing it now. You can reconnect and sign in with your new password. Thanks again for reporting it quickly.

## Workflow issue I fixed along the way
The ticket was moved to **Closed** by mistake. In the Incident workflow, Closed had no outgoing transitions, so it couldn't be reopened. I edited the workflow to add a **Reopen** transition (Closed → Work in progress) and returned the ticket to the Security team's queue.

## Why it matters
- **Contain first, then escalate.** Tier 1 can stop the damage (reset, revoke sessions) in minutes; security handles the investigation.
- Thanking the user matters. People who get blamed for reporting phishing stop reporting it.
