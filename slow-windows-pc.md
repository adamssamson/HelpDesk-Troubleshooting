# Slow Windows PC

**Applies to:** Windows 10/11 laptops and desktops

## Symptoms
- Slow startup, apps freezing, high fan noise, long load times

## Likely causes
- Too many startup programs
- Low disk space or a failing drive
- Low RAM
- Pending updates or a stuck update
- Malware or a runaway process
- Corrupt system files or outdated drivers

## Steps
1. **Ask what changed.** Since when is it slow? Any new software, update or crash?
2. **Check Task Manager** (`Ctrl + Shift + Esc`): which process is using high CPU, memory or disk? Close or investigate it.
3. **Check free disk space.** Keep at least 15-20% free. Run *Disk Cleanup* or *Storage settings*.
4. **Disable unneeded startup apps** in *Task Manager → Startup apps*.
5. **Install pending Windows and driver updates**, then restart. A restart alone often fixes this.
6. **Scan for malware** with Microsoft Defender (full scan) or the company's endpoint tool.
7. **Repair system files** from an elevated Command Prompt:
   ```
   sfc /scannow
   DISM /Online /Cleanup-Image /RestoreHealth
   ```
8. **Check hardware health.** If RAM is constantly near 100% consider an upgrade; if the drive is an HDD or reports errors, plan to replace it with an SSD (back up first).
9. **Last resort:** back up the user's data and reset or reimage the PC.

## Verify
- Startup time and app opening time have improved; Task Manager shows normal CPU, memory and disk use.

## Prevent / Escalate
- Schedule regular updates and restarts; limit startup apps.
- Escalate to hardware repair/replacement if the drive or RAM is failing.
