# New phone: set up MFA again

**Applies to:** Microsoft 365 sign-in with Microsoft Authenticator
**Related ticket type:** Password or Account Access

## Symptoms
- You got a new phone (or reset yours) and can't approve sign-in requests.
- Microsoft keeps asking for a code you can't get.

## What you can try
- **Still have the old phone?** Sign in at **mysignins.microsoft.com/security-info** and add the new phone's Authenticator before wiping the old one.
- **Old phone gone?** Contact the help desk. We need to verify it's you, then we'll clear the old phone so you can set up the new one.

**Setting up the new phone (after IT clears the old one):**
1. Install **Microsoft Authenticator** on the new phone.
2. On a computer, go to **aka.ms/mfasetup** and sign in.
3. Choose Microsoft Authenticator, scan the QR code with the app, and approve the test notification.

## Technician steps
1. **Verify identity** first. MFA resets are a top social-engineering target.
2. Entra admin center → **Users** → user → **Authentication methods**.
3. Click **Require re-register multifactor authentication** (removes registered phones and Authenticator apps). Confirm "No usable methods."
4. Walk the user through **aka.ms/mfasetup**. With security defaults, they may not be forced to register at the next sign-in, so send them the link directly.
5. Refresh Authentication methods and confirm the new device is listed.

## Escalate when
- Identity can't be verified.
- The request is for a privileged account, or sign-in logs show activity the user doesn't recognize (to **Security**).
