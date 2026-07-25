# Hybrid Infrastructure Deployment: Resolving Virtualization Blockers in a Production-Simulated Environment

## 📋 Project Overview
This project documents the end-to-end deployment, hardening, and operational management of an **osTicket** service desk environment [2]. It serves as a "digital proof-of-work" case study, highlighting a strategic pivot from a restricted containerized deployment to a fully functional, hardened native WAMP stack [2, 4].

*   **Objective:** Deploy a secure, networked ticketing system while overcoming critical hardware-level virtualization failures [5].
*   **Key Focus:** Demonstrating competence in web server management, database integrity, and ITIL-style service desk operations [5].

## 🛠️ Technical Architecture
*   **Host Machine:** Windows 11 Home Physical PC [5].
*   **Virtualization Layer:** Oracle VM VirtualBox [5].
*   **Guest OS:** Windows 11 Pro VM [5].
*   **Web Stack:** Native WAMP (Apache, MySQL/MariaDB, PHP) via XAMPP [5].
*   **Network:** Host-to-VM connectivity via IP 192.168.1.128 on Port 80 [5].

## 🔄 The "Fail-Forward" Log: Troubleshooting & Resolution
A core component of this project's value is the documentation of failure and the subsequent senior-level resolution [1, 2].

### Phase 1: The Infrastructure Blocker & Tactical Pivot
The project initially targeted a Linux-based deployment via **WSL 2 and Docker** [3]. However, a configuration oversight regarding **nested hardware virtualization** in VirtualBox generated system-breaking errors [3]:
*   **Errors:** `0x80370102`, `WSL_E_DISTRO_NOT_FOUND`, and `HCS_E_HYPERV_NOT_INSTALLED` [3].

**The Strategic Pivot:** To maintain project momentum and service availability, I pivoted to a native Windows **WAMP stack** [3]. This bypassed the immediate virtualization requirement and allowed for immediate service desk operations while I investigated the root cause [3].

### Phase 2: System Hardening & Configuration
To stabilize the environment for production use, I performed deep-level system optimization [6]:
*   **PHP Environment Tuning:** Resolved **HTTP 500 timeouts** by increasing `max_execution_time` to 300 seconds in `php.ini` [6].
*   **Database Synchronization:** Resolved "Invalid Settings" errors by executing **SQL structural updates** via the XAMPP CLI shell [6].
*   **Security Hardening:** Purged the `/setup/` directory and enforced **Read-Only** attributes on `ost-config.php` to follow the **Principle of Least Privilege** [6].

### Phase 3: Senior-Level Infrastructure Resolution
Acting as a **Senior Infrastructure Lead**, I eventually resolved the underlying hardware restriction [7].
*   **The Fix:** Used the host's **Command Line Interface (CLI)** to bypass GUI limitations [7].
*   **Execution:** Ran `VBoxManage modifyvm "Windows 11 VM" --nested-hw-virt on` to enable nested VT-x/AMD-V [7].
*   **Result:** Successfully cleared the path for future containerized (Docker/WSL 2) deployments within the VM [7].

## 🏢 Operational Simulation (Service Desk)
To prove professional IT support skills, I managed the lifecycle of the infrastructure failure within the osTicket system itself [8]:
*   **Remote Administration:** Accessed the **Staff Control Panel (SCP)** from the host browser [8].
*   **Escalation Ticket #1001:** Claimed and resolved the "Infrastructure Blocker" ticket, providing clear technical documentation of the virtualization fix for future knowledge transfer [8].

## 📊 Resource Management & Observations
During high-load testing of the nested environment, I documented the following infrastructure bottlenecks [9]:
*   **Memory Saturation:** Observed **88% host memory consumption**, with the VM utilizing ~3.3GB of RAM [9].
*   **Network Performance:** Task Manager identified "red" Ethernet ratings, highlighting the high overhead costs of nested virtualization [9].

## 💡 Key Skills Demonstrated
*   **Infrastructure Troubleshooting:** Resolving complex routing, virtualization, and configuration issues [10].
*   **Web Server Administration:** Expert management of Apache and PHP environments [10].
*   **Database Management:** Handling MariaDB/MySQL integrity via Command Line Interface (CLI) [10].
*   **Technical Documentation:** Translating complex troubleshooting into actionable step-by-step guides [10].
