# IT Support Case Study: Resolving Modern Standby Clamshell Sleep Loops
**Date:** July 24, 2026  
**Author:** [Reid Hollister]  
**Role:** Systems Support Technician  
**Status:** Resolved  

## 1. Executive Summary
An issue arose where a [ASUS VIVOBook] laptop configured for a single-display external monitor setup (clamshell mode) would unexpectedly drop into an un-wakeable sleep/hibernation state exactly three to five minutes after the laptop lid was closed. The issue began immediately following a background system update and a manual hardware configuration change that limited the battery charge threshold to protect cell longevity. 

## 2. Environment & System Specifications
* **Host Hardware:** [Asus VIVObook]
* **Operating System:** Windows 11 Home (Build [25H2 (OS Build 26200.8875)])
* **Manufacturer Software:** MyASUS (Battery Health Charging set to Balanced Mode / 80% Cap)
* **Peripherals:** External Monitor via HDMI/DisplayPort, USB Wireless Mouse & Keyboard

## 3. Root Cause Analysis (RCA)
The root cause was a multi-layered configuration conflict between Windows **Modern Standby**, manufacturer microcode, and corrupted power caches:
1. **Power State Fluctuation:** The manufacturer utility capped the battery charge at 80% to protect battery health. When the lid was closed, the charging circuitry stopped accepting current. Windows misinterpreted this "Not Charging" state as a physical switch to "On Battery" power.
2. **Modern Standby Hardcoded Rules:** Under Modern Standby, Windows enforces a hidden rule: if the lid is closed and *any* screen-off timeout triggers, the system automatically drops into a deep Standby freeze. 
3. **USB Port Lockdown:** Windows Power Management had "Allow wake timers" and peripheral wake permissions disabled, preventing external USB devices from sending a wake signal.
4. **Fast Startup Cache Corruption:** A recent Windows Update left old power profile rules cached in the system's Fast Startup file (`hiberfil.sys`), preventing the OS from reading updated Windows GUI settings.

## 4. Troubleshooting Steps & Resolution Matrix

| Target System | Action Taken | Technical Purpose |
| :--- | :--- | :--- |
| **Windows Power & Battery** | Set "Plugged In" and "On Battery" screen/sleep timers to **Never**. | Bypasses the hardcoded Modern Standby sleep trigger. |
| **Control Panel (Advanced Settings)** | Disabled **Link State Power Management** and **Turn off hard disk**. | Prevents PCIe video ports and SSDs from dropping voltage. |
| **Control Panel (Advanced Settings)** | Enabled **Allow Wake Timers** on all power profiles. | Restores USB bus communication when the display is dark. |
| **Device Manager** | Toggled "Allow this device to wake the computer" on Mice/Keyboards. | Permits external peripherals to interrupt sleep states. |
| **Control Panel (Power Buttons)** | Disabled **Fast Startup** and executed a clean system restart. | Purges the corrupted `hiberfil.sys` cache to force a fresh profile reload. |

## 5. Verification & Testing
* **Test 1 (Active Media):** Played a continuous video stream for over 5 minutes with the lid closed and no user input. The external display remained active and responsive.
* **Test 2 (Display Shifting):** Verified that the Windows Desktop Window Manager properly handled the transition from dual-screen to single-screen projection upon lid closure.
* **Test 3 (Idle State):** Configured a system screensaver to safely deploy without triggering a background system freeze.

## 6. Key Takeaways & Lessons Learned
* **The Restart Fallacy:** In modern operating systems, a standard restart or shutdown does not flush system memory if "Fast Startup" is enabled. Hard power profile bugs require a complete cache purge.
* **OEM Overrides:** Third-party hardware management apps (like MyASUS, Dell Power Manager, or Lenovo Vantage) frequently intercept core ACPI power states, changing how Windows calculates power distribution.



---
layout: default
title: My IT Portfolio & Homelab Logs
---

# HelpDesk & IT Engineering Portfolio
Welcome to my documentation space. This is a living record of the homelab projects I build and the everyday issues I troubleshoot to keep my home network running smoothly.

## 🛠️ Knowledge Base & Project Logs
*   [Windows Local Network File Share (SMB) Configuration](./smb-share.md) — *Streamlining IT study workflows across multiple workstations.*
