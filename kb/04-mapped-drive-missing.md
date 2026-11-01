# Mapped drive missing or access denied

**Applies to:** Department drives (S: Sales, H: HR, I: IT) mapped by Group Policy
**Related ticket type:** Get IT help or Password or Account Access

## Symptoms
- Your department drive is missing from **This PC**, or it's listed but says **"You do not have permission to access."**
- You recently changed roles and can't open your new team's drive.

## What you can try
1. **Sign out and sign back in.** Drives and access refresh at sign-in.
2. Make sure you're on the office network or connected to VPN.
3. Still missing? Submit a ticket and say whether coworkers can still open the drive.

## Technician steps
1. **Scope it:** one user, or the whole department? A whole department means a server or share problem (P1); one user usually means group membership.
2. As the user, run:
   ```powershell
   gpresult /r
   ```
   Confirm **Drive Maps** is applied and the department group (e.g. `GG_Sales`) is in the user's security groups. Check the timestamp; a report from before a group change is stale.
3. Check membership in AD:
   ```powershell
   Get-ADPrincipalGroupMembership <user> | Select-Object Name
   ```
4. Fix membership **with approval** (department moves need HR or the manager's OK), e.g.:
   ```powershell
   Add-ADGroupMember GG_Sales -Members <user>
   ```
5. Have the user sign out and back in (group membership loads at sign-in), then confirm the drive opens.
6. Whole department affected: on the file server check `Get-SmbShare`, the share's NTFS permissions (`icacls`), and the Server service.

## Escalate when
- The share or file server is down for many users (open a problem record).
- Access is requested without approval from the data owner or manager.
