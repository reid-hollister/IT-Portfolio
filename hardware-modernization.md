---
layout: default
title: Legacy Hardware Modernization & Linux Deployment
---

# Legacy Hardware Modernization: Windows 8 Lifecycle Decommission & Bare-Metal Linux Deployment

## 🚀 Project Overview
This project documents the recovery, hardware auditing, firmware re-engineering, and bare-metal deployment of an open-source operating system onto a legacy 2-in-1 convertible laptop [1]. I intercepted a decommissioned Lenovo Yoga 11S slated for e-waste, diagnosed critical power and stability issues, and restored full utility using a highly optimized Linux kernel [1, 5].

### 💼 Business Case & Value
*   **E-Waste Mitigation:** Extends the physical lifecycle of enterprise hardware [5].
*   **Security Compliance:** Replaces end-of-life Windows 8 with a modern, actively patched Linux LTS kernel [5].
*   **Cost Efficiency:** Restores full computing utility with $0 in software licensing costs [5].

---

## 🛠️ Technical Specifications (Audited)
*   **Device:** Lenovo ThinkPad/IdeaPad Yoga 11S (Haswell Platform) [5].
*   **Processor:** Intel Core i5-4210Y @ 1.50GHz (2 Cores, 4 Threads) [5].
*   **Memory:** 4GB DDR3L (Single-channel) [5].
*   **Storage:** Internal Full-Size mSATA Slot [5].

---

## 🔍 Engineering Phase 1: Diagnostics & Power Recovery
The system initially failed to initialize due to multi-year storage depletion [2]. 

### **Troubleshooting & Iteration Log**
| Symptom | Diagnosis | Senior-Level Resolution |
| :--- | :--- | :--- |
| **Amber Power Pulse** | Critical Battery Voltage Depletion; cells dropped below safety threshold [2]. | Isolated on 45W AC supply for 4 hours to bypass trickle-charge protection [2]. |
| **OS Loop & Interface Freeze** | Corrupted Windows 8 environment and explorer.exe crash loop [2]. | Executed a **hardware firmware interrupt** using the physical Novo Button to bypass the OS abstraction layer [2, 6]. |
| **Media Compiler Failure** | Metadata request exceptions in BalenaEtcher [7]. | Pivoted to **Rufus** to write the block-level structure using ISO Image Mode [7]. |

---

## ⚙️ Engineering Phase 2: Firmware & BIOS Optimization
To support a modern OS on legacy hardware, I reconfigured the **UEFI parameters** to ensure system stability [8]:
*   **Secure Boot Deactivation:** Prevented the motherboard signature checker from blocking non-Microsoft kernel handoffs [8].
*   **Boot Mode Enforcement:** Enforced explicit **UEFI standard compliance** over legacy BIOS emulation [8].
*   **Storage Controller Alignment:** Verified **AHCI mode** to expose raw blocks directly to the Linux kernel filesystem tools [8].

---

## 🐧 Engineering Phase 3: Deployment & System Wiping
I selected **Linux Mint 22 (XFCE Architecture)** to maintain a minimal system footprint (<700MB RAM idling), ensuring maximum resource availability for the 4GB RAM threshold [6, 7].
*   **File System:** Rebuilt the partition table using the high-performance **ext4** filesystem [6].
*   **Kernel Initialization:** Executed the live Linux kernel completely inside system RAM to isolate the deployment from damaged internal partitions [6].

---

## 📈 Future Scalability Path
The system is mapped for low-cost modular scaling, including a path to **8GB DDR3L 1600MHz** memory (SoC max ceiling) and a **1TB SATA III mSATA SSD** upgrade [9].

---

### 🔗 Navigation
[Back to Technical Labs](./index.md) | [osTicket Migration](./osticket-migration.md) | [Active Directory Project (In-Progress)](#)
Step 2: Tactical Refinement & Blind Spots