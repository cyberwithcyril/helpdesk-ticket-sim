# Account locked out

**Applies to:** Windows sign-in on company computers
**Related ticket type:** Password or Account Access

## Symptoms
- Sign-in screen says **"The referenced account is currently locked out and may not be logged on to."**
- Your password stopped working after several tries, even though you're sure it's right.

## What you can try
1. **Wait 15 minutes.** Lockouts clear on their own after 15 minutes, then try once, carefully.
2. Check **Caps Lock** and your keyboard language before typing again.
3. If you changed your password recently, **update it on your phone** (email and Teams apps) and any other device. An old saved password keeps retrying and locks you out again.
4. Still locked or can't wait? Submit **Password or Account Access** in the portal or call the help desk.

## Technician steps
1. **Verify the caller's identity** before making changes.
2. Confirm it's really a lockout:
   ```powershell
   Get-ADUser <user> -Properties badPwdCount, LockedOut | Select-Object Name, badPwdCount, LockedOut
   ```
3. Unlock: ADUC → user → **Account** tab → **Unlock account**, or:
   ```powershell
   Unlock-ADAccount <user>
   ```
4. Confirm `LockedOut` is `False` and the user can sign in.
5. Ask whether a phone or another device still has the old password.

## Escalate when
- The account locks again within the hour with no user error (look for the lockout source on the domain controller, event ID 4740).
- Lockouts come from a computer or location the user doesn't use, which may be password guessing. Send it to **Security**.
