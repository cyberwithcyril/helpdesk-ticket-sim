# Printer shows offline

**Applies to:** Office network printers on Windows
**Related ticket type:** Get IT help

## Symptoms
- Printer shows **Offline**, or jobs sit in the queue and never print.

## What you can try
1. Check the printer: powered on, no paper jam, no error on its screen.
2. Ask a coworker whether **they** can print to it. If nobody can, report it as a printer problem rather than a computer problem.
3. Restart your computer.
4. Settings → **Bluetooth & devices → Printers & scanners** → select the printer → **Open print queue** → cancel stuck jobs → try again.

## Technician steps
1. Determine scope: one user or everyone? Can you ping the printer's IP?
2. If only one PC: clear the queue and restart the spooler.
   ```powershell
   Stop-Service Spooler
   Remove-Item C:\Windows\System32\spool\PRINTERS\* -Force
   Start-Service Spooler
   ```
3. Print a test page.
4. If the printer itself is unreachable: check its network cable or Wi-Fi, IP address, and power-cycle it.
5. Remove and re-add the printer if the driver looks corrupted.

## Escalate when
- The printer is unreachable on the network for everyone (to **Network** or the facilities/print vendor).
- Hardware errors (fuser, hardware fault codes) need a vendor service call.
