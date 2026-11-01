# Wi-Fi keeps dropping

**Applies to:** Office Wi-Fi on Windows laptops
**Related ticket type:** Report a Network Problem

## Symptoms
- Wi-Fi disconnects every few minutes, or calls freeze and reconnect.

## What you can try
1. Turn Wi-Fi off and on, or restart the laptop.
2. **Forget and rejoin** the network: Settings → **Network & internet → Wi-Fi → Manage known networks** → select it → **Forget**, then reconnect.
3. Move closer to the middle of the office for a few minutes. Does it still drop?
4. If others near you have the same problem, mention it in your ticket.

## Technician steps
1. Scope it: one user or many? Only at one desk, or everywhere?
2. Check signal and connection details:
   ```powershell
   netsh wlan show interfaces
   ```
   Note **Signal** (below about 50% is weak), channel, and the access point (BSSID).
3. Forget and rejoin the network, update the Wi-Fi driver, and check power settings (disable "allow the computer to turn off this device to save power" on the adapter).
4. Monitor for 15-30 minutes.

## Escalate when
- Weak signal or drops are tied to one area of the office (access point coverage or interference) → **Network**.
- Multiple users are affected at once → **Network**, as a possible outage.

Handoff should include: location, signal reading, BSSID, steps already tried, and when it happens.
