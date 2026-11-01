# Reset or change your password

**Applies to:** Windows / company account passwords
**Related ticket type:** Password or Account Access

## Symptoms
- You forgot your password, or got a message that it **expires soon**.

## What you can try
**Change it before it expires (you know your current password):**
1. On your work computer press **Ctrl + Alt + Delete**.
2. Choose **Change a password**.
3. Enter your current password, then the new one twice.
4. Update the new password on your phone and other devices.

Password rules: at least 8 characters, mixing upper case, lower case, numbers and symbols. Don't reuse old passwords.

**Forgot it?** Submit **Password or Account Access** or call the help desk. We'll verify your identity before resetting it.

## Technician steps
1. **Verify identity** (callback to the number on file or the company's process). Password resets are a common social-engineering target.
2. Reset with a temporary password and force a change:
   - ADUC → right-click user → **Reset Password** → check **User must change password at next logon** (and **Unlock** if locked).
   - PowerShell:
     ```powershell
     Set-ADAccountPassword <user> -Reset -NewPassword (Read-Host -AsSecureString "Temp password")
     Set-ADUser <user> -ChangePasswordAtLogon $true
     ```
3. Give the temporary password through a verified channel (phone, not email to the same account).
4. Confirm `pwdLastSet` is `0` and the user is prompted to change it at sign-in.

## Escalate when
- You can't verify the caller's identity.
- It's a privileged or executive account (follow the senior admin process).
