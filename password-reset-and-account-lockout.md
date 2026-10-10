# Password Reset and Account Lockout (AD / Entra ID)

**Applies to:** On-premises Active Directory and Microsoft Entra ID (Microsoft 365)

## Symptoms
- "Your account has been locked out" or "Incorrect password"
- User repeatedly locked out after resetting their password

## Likely causes
- Forgotten or expired password
- Old password saved on another device (phone mail app, mapped drive, saved RDP/Wi-Fi credential, scheduled task)
- Caps Lock / keyboard layout
- Sync delay between on-prem AD and Entra ID

## Steps
1. **Verify the user's identity** using your company's process (callback to a known number, manager approval, etc.) before any reset. Never reset on an unverified request.
2. **Check account status** in Active Directory Users and Computers (or Entra admin center): locked, disabled, or password expired?
3. **Unlock (on-prem AD)** in ADUC (*Account tab → Unlock account*) or PowerShell:
   ```powershell
   Unlock-ADAccount -Identity jdoe
   ```
4. **Reset the password** with a temporary password and require change at next sign-in:
   ```powershell
   Set-ADAccountPassword -Identity jdoe -Reset -NewPassword (Read-Host -AsSecureString "New password")
   Set-ADUser -Identity jdoe -ChangePasswordAtLogon $true
   ```
   For cloud-only users: *Entra admin center / Microsoft 365 admin center → Users → Reset password*.
5. **Find the lockout source** if it keeps happening. On the domain controller, search the Security log for **Event ID 4740**; the *Caller Computer Name* shows where the bad password is coming from.
6. **Clear stale credentials** on that device: phone mail apps, *Credential Manager*, mapped drives, services or scheduled tasks using the old password.
7. **Check MFA** is still registered and working; reset the authentication method if the user lost their phone.

## Verify
- User signs in to the PC and to Microsoft 365 successfully.
- Account stays unlocked for at least 30 minutes.

## Prevent / Escalate
- Enable self-service password reset (SSPR) so users can fix this themselves.
- Remind users to update the password on all devices after a change.
- Escalate if lockouts continue with no identified source (possible brute-force attempt) and notify security.
