# Phase 1: Hardware Bring-Up (Atlas Build)

**Status:** In Progress

## Day 1: Assembly & BIOS

### The Goal
Prepare the main server (Atlas) for its hypervisor installation. This involved replacing a failed case fan, checking the CMOS battery, and configuring the BIOS for virtualization and unattended power recovery.

### What Went Well
*   The machine POSTed successfully. The CPU and RAM were detected correctly (Intel Core i5, 16GB).
*   The CMOS battery tested at a healthy ~3V, meaning we don't lose BIOS settings on power loss.
*   The PSU fan was quiet and clean.

### The "Honest Failure": The Thermal Paste
On first boot, the CPU idle temperature in the BIOS was reading **88°C (190°F)**. A normal idle temperature should be 30°C–45°C. 

The machine is a decade old. The thermal paste between the CPU and the cooler had completely dried out and turned to concrete, preventing any heat transfer. 

**The Fix:**
1. Removed the CPU cooler and cleaned the old, crusty paste off the CPU and heatsink using isopropyl alcohol.
2. Cleaned a significant amount of dust out of the aluminum cooler fins.
3. Applied fresh thermal paste and re-seated the cooler.

### The Fan Clearance Issue
The original case fan had a failed bearing and needed replacing. A high-performance 38mm-thick fan was initially purchased, but the chassis only had clearance for a standard 25mm-thick fan. The 38mm fan was returned, and a standard 25mm PWM fan was ordered.

### BIOS Configuration
The following settings were applied to ensure the server behaves correctly when it goes headless:
*   **Virtualization (VT-x):** Enabled (required for Proxmox).
*   **Power On after AC Loss:** Enabled (so the server automatically boots back up after a power outage when connected to a UPS).
*   **Boot Mode:** UEFI.
*   **BIOS Password:** Set and stored in the password manager.

### Next Steps
*   Run Memtest86+ to verify RAM stability.
*   Install the SSDs and run SMART health tests.
*   Measure power consumption (idle vs. load).