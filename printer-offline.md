# Printer Offline / Print Jobs Stuck

**Applies to:** Windows 10/11 with network or USB printers

## Symptoms
- Printer shows "Offline" or "Error"
- Print jobs stay in the queue and never print

## Likely causes
- Printer powered off, disconnected or lost its network address
- Print Spooler service stuck
- Wrong or outdated driver or port
- "Use Printer Offline" enabled

## Steps
1. **Check the basics.** Printer on, no paper jam, no error on its display, cables or Wi-Fi connected.
2. **Check the network.** From the PC, ping the printer's IP (for example `ping 192.0.2.50`). No reply means a network or printer problem.
3. **Uncheck "Use Printer Offline".** *Settings → Printers & scanners → select printer → Open print queue → Printer menu*.
4. **Clear the queue and restart the Print Spooler** from an elevated Command Prompt:
   ```
   net stop spooler
   del /Q /F /S "%systemroot%\System32\spool\PRINTERS\*.*"
   net start spooler
   ```
5. **Check the port.** *Printer properties → Ports*: confirm the IP matches the printer's current IP. Printers should have a static IP or DHCP reservation.
6. **Reinstall the driver.** Remove the printer, download the correct driver from the manufacturer, then add the printer again.
7. **Test print** from Notepad and from the user's application.

## Verify
- Test page prints and the queue is empty.

## Prevent / Escalate
- Assign static IPs or DHCP reservations to printers.
- Escalate to the printer vendor/maintenance contractor for hardware faults (rollers, toner, fuser).
