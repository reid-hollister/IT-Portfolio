---
layout: default
title: Legacy Hardware Modernization & Linux Deployment
---

# Legacy Hardware Modernization: Windows 8 Lifecycle Decommission & Bare-Metal Linux Deployment

## 🚀 Project Overview
This project documents the recovery, hardware auditing, firmware re-engineering, and bare-metal deployment of an open-source operating system onto a legacy 2-in-1 convertible laptop. I intercepted a decommissioned Lenovo Yoga 11S slated for e-waste, diagnosed critical power and stability issues, and restored full utility using a highly optimized Linux kernel.

### 💼 Business Case & Value
*   **E-Waste Mitigation:** Extends the physical lifecycle of enterprise hardware.
*   **Security Compliance:** Replaces end-of-life Windows 8 with a modern, actively patched Linux LTS kernel.
*   **Cost Efficiency:** Restores full computing utility with $0 in software licensing costs.

---

## 🛠️ Technical Specifications (Audited)
*   **Device:** Lenovo ThinkPad/IdeaPad Yoga 11S (Haswell Platform).
*   **Processor:** Intel Core i5-4210Y @ 1.50GHz (2 Cores, 4 Threads).
*   **Memory:** 4GB DDR3L (Single-channel).
*   **Storage:** Internal Full-Size mSATA Slot.

---

## 🔍 Engineering Phase 1: Diagnostics & Power Recovery
The system initially failed to initialize due to multi-year storage depletion. 

## Troubleshooting & Iteration Log

| Symptom | Diagnosis | Senior-Level Resolution |
| :--- | :--- | :--- |
| **Amber Power Pulse** | Critical Battery Voltage Depletion; cells dropped below safety threshold. | Isolated on 45W AC supply for 4 hours to bypass trickle-charge protection. |
| **OS Loop & Interface Freeze** | Corrupted Windows 8 environment and explorer.exe crash loop. | Executed a **hardware firmware interrupt** using the physical Novo Button to bypass the OS abstraction layer. |
| **Media Compiler Failure** | Metadata request exceptions in BalenaEtcher. | Pivoted to **Rufus** to write the block-level structure using ISO Image Mode. |

---

## ⚙️ Engineering Phase 2: Firmware & BIOS Optimization
To support a modern OS on legacy hardware, I reconfigured the **UEFI parameters** to ensure system stability 
*   **Secure Boot Deactivation:** Prevented the motherboard signature checker from blocking non-Microsoft kernel handoffs.
*   **Boot Mode Enforcement:** Enforced explicit **UEFI standard compliance** over legacy BIOS emulation.
*   **Storage Controller Alignment:** Verified **AHCI mode** to expose raw blocks directly to the Linux kernel filesystem tools.

---

## 🐧 Engineering Phase 3: Deployment & System Wiping
I selected **Linux Mint 22 (XFCE Architecture)** to maintain a minimal system footprint (<700MB RAM idling), ensuring maximum resource availability for the 4GB RAM threshold.
*   **File System:** Rebuilt the partition table using the high-performance **ext4** filesystem.
*   **Kernel Initialization:** Executed the live Linux kernel completely inside system RAM to isolate the deployment from damaged internal partitions.

---

## 📈 Future Scalability Path
The system is mapped for low-cost modular scaling, including a path to **8GB DDR3L 1600MHz** memory (SoC max ceiling) and a **1TB SATA III mSATA SSD** upgrade.

---

### 🔗 Navigation
[Back to Technical Labs](./index.md) | [osTicket Migration](./osticket-migration.md) | [Active Directory Project (In-Progress)](#)
