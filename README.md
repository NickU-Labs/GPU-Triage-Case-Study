# Case Study: Hardware Failure Triage (NVIDIA RTX 3060 - Code 43)

## Executive Summary
This repository documents a deep-dive technical triage of a persistent **Error Code 43** on an NVIDIA RTX 3060 Laptop GPU. Despite exhaustive software and firmware-level interventions, the device was confirmed to have a physical hardware failure.

## System Specifications
* **Device:** Dell G15 5510
* **OS:** Windows 11
* **GPU:** NVIDIA GeForce RTX 3060 Laptop

## Triage Phases

### Phase 1: Software & Driver Isolation (L1)
* **Action:** Performed a clean uninstall using DDU (Display Driver Uninstaller) in Safe Mode.
* **Action:** Reinstalled OEM-certified drivers from Dell Support.
* **Result:** Code 43 persisted; GPU failed to initialize.

### Phase 2: Firmware & Environment Configuration (L2)
* **Action:** Updated System BIOS to latest version (2026).
* **Action:** Reset BIOS to Factory Defaults to clear potentially corrupt CMOS settings.
* **Action:** Investigated hardware MUX/Hybrid Graphics toggles. 
* **Evidence:** [BIOS Settings Analysis](images/image_3.png) - Confirmed no physical MUX switch available on this SKU.

### Phase 3: VBIOS Recovery Attempt (L3)
* **Action:** Attempted a Video BIOS (VBIOS) firmware flash using the NVIDIA Firmware Update Utility to repair potential on-chip instruction corruption.
* **Result:** **FAIL**.
* **Evidence:** [VBIOS Error Log](images/image_4.png) - Utility reported "Unsupported" status and returned Error Code: 000015.

## Final Root Cause Analysis (RCA)
The failure of the VBIOS utility to recognize the hardware—despite the chip being visible in the PCIe bus—indicates a **Physical Logic Failure** or **VRAM Defect**. With the warranty having expired in May 2024, this device is slated for "Integrated Graphics Only" operation to maintain system stability.

## Professional Competencies Demonstrated
* Advanced Windows Troubleshooting & PowerShell utilization.
* Firmware (VBIOS) manipulation and risk management.
* Logical Root Cause Analysis (RCA) and technical documentation.
