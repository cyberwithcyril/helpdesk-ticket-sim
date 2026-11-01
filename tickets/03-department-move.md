# Ticket write-up: Department move needing approval

| | |
| --- | --- |
| **Ticket** | "I moved to HR and can't open the HR drive" |
| **Reporter** | Priya Shah, HR |
| **Request type** | Password or Account Access |
| **Priority** | Medium (P3): can work, missing access to new team's files |
| **Outcome** | Resolved after manager approval; old access removed as well as new access granted |

## What the user said
> I transferred to HR last week but I still can't get into the HR folder. It says access denied.

## Reply to customer (clarifying question)
> Congrats on the move! Who's your new manager? I need their OK before I change your access.

## Internal note
> AD shows Department = HR, but the account is still in OU=Sales and member of GG_Sales only. The HR system change never reached group membership. Manager approval received (simulated). Added GG_HR, removed GG_Sales, moved the account to OU=HR. User needs to sign out and back in for new groups to load.

Commands used (reproduced in my [AD lab](https://github.com/cyberwithcyril/homelab-ad-m365/blob/main/runbooks/03-department-move.md)):
```powershell
Add-ADGroupMember GG_HR -Members <user>
Remove-ADGroupMember GG_Sales -Members <user> -Confirm:$false
Get-ADUser <user> | Move-ADObject -TargetPath "OU=HR,OU=_Users,DC=lab,DC=local"
```

## Closing reply
> You now have access to the HR drive. Please sign out and back in for it to appear. The Sales drive will no longer show, since that access moves with your new role.

## Why it matters
- **Access follows groups, not job titles.** Updating the department field alone grants nothing.
- **Remove old access too.** Leaving Sales access in place is how permissions pile up over a career ("privilege creep").
- **Approval before access.** The help desk doesn't grant access on the user's word alone.
