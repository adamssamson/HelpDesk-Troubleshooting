# Outlook Not Syncing / Not Opening

**Applies to:** Outlook (Microsoft 365 Apps) on Windows 10/11 with Exchange Online

## Symptoms
- "Disconnected", "Trying to connect" or "Updating inbox" in the status bar
- New mail not arriving, or sent mail stuck in Outbox
- Outlook hangs on "Loading profile" or won't open

## Likely causes
- No internet, or Outlook set to Work Offline
- Add-in conflict
- Corrupt Outlook profile or OST file
- Expired password or MFA/sign-in problem
- Mailbox full, or licence missing/removed
- Microsoft 365 service issue

## Steps
1. **Check connectivity.** Confirm the user can browse the internet. Open Outlook on the web (outlook.office.com). If the mailbox works there, the problem is the desktop app, not the account.
2. **Check Work Offline.** In Outlook go to *Send/Receive → Work Offline* and make sure it is **not** highlighted.
3. **Check sign-in.** If prompted for credentials, sign out and back in. Confirm the password has not expired or been reset.
4. **Open in Safe Mode.** Press `Win + R`, run `outlook.exe /safe`. If it works, an add-in is the cause. Disable add-ins one by one under *File → Options → Add-ins*.
5. **Repair the account.** *File → Account Settings → Account Settings → select account → Repair*.
6. **Create a new profile.** *Control Panel → Mail → Show Profiles → Add*. Set the new profile as default and test.
7. **Rebuild the OST.** Close Outlook, rename the `.ost` file (in `%localappdata%\Microsoft\Outlook`) to `.old`, and reopen Outlook so it resyncs.
8. **Check the admin side.** In the Microsoft 365 admin center confirm the user has an Exchange Online licence, the mailbox is not over quota, and *Service health* shows no active incident.

## Verify
- Send and receive a test email.
- Status bar shows "Connected to Microsoft Exchange".

## Prevent / Escalate
- Remove unused add-ins; keep Office updated.
- Escalate to Tier 2 / Microsoft Support if Outlook on the web also fails or Service health shows an incident.
