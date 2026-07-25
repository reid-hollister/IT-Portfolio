---
layout: default
title: SMB File Share Project
---
# Knowledge Base Article: Cross-Workstation SMB File Share Configuration

## ⚡ Business Case / Problem Statement
As an IT student, my study workflow requires converting practice quiz results to PDF and uploading them into NotebookLM for analysis. This workflow spans two distinct local workstations (Bedroom PC and Office PC). Previously, moving these assets required manually emailing files between sessions, creating administrative overhead and duplicate file versions. 

## 🎯 Objective
Configure a secure, centralized local network shared folder accessible by both workstations to streamline document ingestion without relying on external cloud storage or email attachments.

## 🛠️ Technical Implementation & Environment
* **Protocol Used:** SMB (Server Message Block)
* **Host Machine:** [ Windows 11 Home (Bedroom PC)]
* **Client Machine:** [ Windows 11 Pro (Office PC)]
* **Network Scope:** Private Local Area Network (LAN)

## 🔍 Step-by-Step Configuration Steps
1. **Network Profile Verification:** Ensured both workstations were set to a **Private Network** profile to allow local discovery.
2. **Directory Creation:** Created a dedicated target folder within the local directory system.
3. **Advanced Sharing Configuration:** 
   * Enabled file and printer sharing via the Windows Control Panel.
   * Configured the target folder properties to grant specific network share permissions.

4. **Client Mapping:** Accessed the host directory from the secondary PC using the local path network shortcut (`\\ReidMachine\SharedFolder`).

## 💡 Troubleshooting & Lessons Learned
* **Network Discovery:** Initially, the machines could not see each other because the network profile defaulted to 'Public'. Changing this to 'Private' instantly allowed the handshake.
* **Security Baseline:** Kept the share restricted to the local network only, ensuring study files and local data remain secure from outside traffic.

## ✅ Outcome
Both workstations can now seamlessly drop quiz PDFs into a singular local directory. The file ingest time for NotebookLM was reduced from minutes to seconds, successfully decoupling the study environment from workstation physical location.
