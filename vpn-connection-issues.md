# VPN Will Not Connect

**Applies to:** Remote users connecting to a company VPN from Windows 10/11

## Symptoms
- VPN client stays on "Connecting" or fails with an error
- Connected, but cannot reach internal servers or file shares

## Likely causes
- No or unstable home internet
- Wrong credentials, expired password or MFA problem
- Outdated VPN client
- Local firewall, antivirus or public Wi-Fi blocking the VPN
- DNS problem after connecting
- Wrong system date/time (breaks certificates)

## Steps
1. **Confirm internet works.** Browse a website; if slow, test another network (for example a phone hotspot).
2. **Check credentials and MFA.** Try signing in to Microsoft 365 with the same account to confirm the password is valid.
3. **Check date and time.** Make sure the PC time and time zone are correct and set automatically.
4. **Restart the VPN client** and the PC. Update the client to the current approved version.
5. **Try another network.** If it works on a hotspot, the original network (router, ISP or public Wi-Fi) is blocking the VPN.
6. **Check firewall/antivirus** is not blocking the VPN client. Temporarily test with approved exceptions only.
7. **If connected but no access to internal resources**, flush DNS and test by name and IP:
   ```
   ipconfig /flushdns
   ping 192.0.2.10
   nslookup fileserver.contoso.local
   ```
   If the IP works but the name doesn't, it's a DNS issue.
8. **Check the logs** in the VPN client and on the VPN gateway/firewall for the exact error.

## Verify
- VPN shows connected and the user can open an internal resource (share, intranet or application).

## Prevent / Escalate
- Keep the VPN client updated through your deployment tool.
- Escalate to Tier 2 / network team if the gateway logs show certificate, policy or server-side errors.
