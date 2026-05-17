# CySA+ Home Lab Progress

## 🌐 Network Topology
![Topology](https://github.com/Nedmac11/CySA-Home-Lab/blob/main/homelab2.png?raw=true)

---

## 🏗️ Phase 1: Physical & Virtual Infrastructure (COMPLETE)
* **Firewall:** HP T660s SFF PC running **OPNsense 26.x**
* **WAN (igb0):** [REDACTED_ISP_DHCP] (House PoE Feed)
* **LAN (igb1):** [LAB_GATEWAY_IP] (Switch Feed)
* **Hypervisor:** Laptop running **Proxmox VE 9.1-1**
* **Management IP:** [HYPERVISOR_MGMT_IP]
* **Hardware:** Intel i3-4010U | 16GB RAM | 500GB SSD
* **Virtual Instances:**
  * `Win10Target` (Windows 10 Pro) - Active Bait Host
  * `KaliAttackNode` (Kali Linux) - Threat Simulation Vector
* **SIEM:** Debian 13 (Trixie) VM on Ryzen Host
* **Splunk IP:** [SIEM_DECEPTION_IP]
* **Status:** Web Interface active (Port [SIEM_DECEPTION_WEB_PORT]); Receiver active (Port [SIEM_DECEPTION_LOG_PORT])

---

## 🎯 Phase 2: Victim Machine & Telemetry (COMPLETE)
* **Target VM:** Windows 10 Pro (`Win10Target`)
* **Status:** Operational. Internet-active via Intel E1000 compatibility driver.
* **Connectivity Proof:** Verified secure pipeline flow from victim host to Splunk indexer node on Port [SIEM_DECEPTION_LOG_PORT].

### ✅ Completed Milestones
* [x] OPNsense Interface Assignment & DHCP Setup
* [x] Intel NIC to Switch Handshake Fix
* [x] Proxmox Installation & Lid-Switch Power Management Fix
* [x] Windows 10 Target Import & Driver Configuration
* [x] Firewall Rule creation for Lab-to-SIEM communication
* [x] Install **Sysmon** on Windows 10 Target using SwiftOnSecurity modular configuration
* [x] Configured Windows Remote Desktop (RDP) connection to target VM for a high-resolution, full-screen lab interface
* [x] Verified system log generation via Windows Event Viewer (Operational channel)
* [x] Pivoted through an isolated VirtualBox Kali Linux GUI workspace using a python3 ephemeral web server (`http.server`) to bypass physical-host corporate endpoint agent restriction blocks (`Virus/Spyware Download Blocked`)
* [x] Successfully staged the **Splunk Universal Forwarder (v10.2.3)** installer package locally on the Windows 10 target endpoint
* [x] Executed the Splunk Universal Forwarder installation wizard on the Windows 10 target machine
* [x] Connected the forwarder agent back to the Splunk Receiving Indexer IP via port [DEFAULT_LOG_PORT]
* [x] Created custom text-based `inputs.conf` configuration file within the protected system local application path
* [x] Defined input paths within `inputs.conf` to automatically pull and ingest Sysmon event logs into the Splunk repository interface
* [x] Successfully verified live pipeline functionality via custom SPL table queries

---

## 🎛️ Phase 2.5: Operational Continuity & Multi-Platform Baselines (COMPLETE)
To prevent rebuild overhead during aggressive exploit simulation routines, a full multi-platform backup protocol was executed to secure clean system baselines.

### 💾 Storage Allocation Optimization
* **Initial Local Disk Usage:** `35.61%` (35.92 GB / 100.86 GB)
* **Cleanup Routine:** Wiped redundant staging binaries (`kali.ova` and `Ethical-Hacker-Kali-disk001.vmdk`) from `/var/lib/vz/template/iso/` directory paths.
* **Optimized Baseline Footprint:** Dropped local disk allocation down to `17.51%`.

### ✅ Completed Backup Milestones
* [x] **Proxmox Storage Optimization:** Reclaimed ~18 GB of root partition allocation via manual staging cache cleanups.
* [x] **Proxmox Infrastructure Hard Backup:** Generated independent compressed node archives (`vzdump` using `ZSTD` engines) for both `Win10Target` and `KaliAttackNode`.
* [x] **Proxmox Live Rollback Snapshots:** Captured memoryless delta configurations (`Pre_Exploit_Baseline`) across all hypervisor container systems.
* [x] **OPNsense Firewall Preservation:** Exported complete network topology blueprints, routing tables, and interface definitions into a standalone `config.xml` profile.
* [x] **VirtualBox SIEM Indexer Snapshot:** Automated cold state backup checkpoints (`Splunk_Ingest_Baseline`) encapsulating active ingest pipelines on ports [DEFAULT_WEB_PORT] and [DEFAULT_LOG_PORT].

---

## 🌋 Phase 2.6: Disaster Recovery Simulation Test (DRST) (COMPLETE)
To validate baseline integrity before launching live exploits, a simulated catastrophic hypervisor crash was executed to test the recovery pipeline.

### 📋 Scenario Parameters
* **Trigger Event:** Automated deletion of active lab node runtime files (simulating severe ransomware encryption or administrative catastrophic failure).
* **RTO (Recovery Time Objective):** < 15 minutes.
* **RPO (Recovery Point Objective):** 0 data loss (Return to `Pre_Exploit_Baseline`).

### 🛠️ Execution Playbook & Validation Steps
1. **Host Deconstruction:** Force-terminated `Win10Target` and `KaliAttackNode` runtimes and purged active runtime disks to simulate complete infrastructure loss.
2. **Network Topology Restoration:** Imported the `config.xml` profile back into the OPNsense core engine and verified DHCP lease allocations, VLAN tags, and WAN/LAN handshake integrity.
3. **Storage Engine Recovery:** Deployed the compressed `vzdump` ZSTD archive back to the local Proxmox storage repository and restored the `Pre_Exploit_Baseline` snapshot via the PVE Web UI.
4. **Pipeline Ingestion Health Check:** Booted the restored infrastructure, executed a test log generation loop on the victim node, and confirmed the remote Splunk Indexer instantly recognized the forwarder stream on port [DEFAULT_LOG_PORT].

### 📊 Results
* **Actual Recovery Time:** 6 minutes, 42 seconds.
* **Data Integrity:** 100% telemetry retention.
* **Status:** **SUCCESSFUL**. The environment is resilient and certified ready for aggressive Phase 3 exploit simulations.

---

## 🖨️ Phase 2.7: Network Refactoring & Honeypot Deception Architecture (COMPLETE)
To align with the target Packet Tracer documentation and evaluate defensive data-obfuscation tactics, the entire lab network infrastructure was migrated to a new addressing tier while implementing stealth camouflage profiles for key infrastructure assets.

### 📋 Architectural Strategy
* **Network Realignment:** Refactored OPNsense core routing interfaces and DHCP scope properties to enforce the new [LAB_SUBNET] addressing matrix.
* **SIEM Obfuscation:** Masked the dedicated Debian Splunk Server identity as an innocuous network printer asset, binding standard administrative web portals to port [SIEM_DECEPTION_WEB_PORT].
* **Log Pipeline Camouflage:** Rerouted the active Sysmon telemetry pipeline away from standard, high-signature SIEM log ports to TCP Port [SIEM_DECEPTION_LOG_PORT] (the enterprise standard for RAW HP JetDirect print data streams).
* **Threat Node Camouflage:** Hardcoded the `KaliAttackNode` interface with a static manual network identity on [KALI_DECEPTION_IP], masking the offensive system as an IoT Office Security Camera to minimize threat detection visibility during network sweeps.

### ✅ Completed Deception Milestones
* [x] Reconfigured OPNsense LAN settings via physical monitor/keyboard console interfaces to bind gateway services onto [LAB_GATEWAY_IP].
* [x] Provisioned active DHCP server leases within the scoped allocation boundary ([LAB_DHCP_START] through [LAB_DHCP_END]), reserving high-tier blocks for static deception hosts.
* [x] Mitigated hypervisor lockout by manually restructuring the static Proxmox hardware bridging text configuration map inside `/etc/network/interfaces`.
* [x] Modified Debian 13 SIEM interface profiles from dynamic DHCP configurations to a permanent static assignment at [SIEM_DECEPTION_IP].
* [x] Established a custom log ingestion listener rule inside the Splunk administrative configuration console on the fake printer data channel (Port [SIEM_DECEPTION_LOG_PORT]).
* [x] Rewrote the Windows 10 target host `outputs.conf` structural routing block under an administrative permission context, shifting the local forwarder service to stream data exclusively over the new printer pipeline configuration.
* [x] Successfully bypassed a post-migration service initiation error (Windows Error 1053) by completely cleaning corrupted network stanzas out of the local forwarder system files.
* [x] Hardcoded manual IPv4 configuration maps inside the Kali Linux taskbar desktop management panel to anchor the attack terminal permanently at [KALI_DECEPTION_IP].
* [x] Executed end-to-end telemetry verification tests to confirm live, rich XML Windows/Sysmon data streams are parsing cleanly inside the hidden SIEM environment.

---

## 🛡️ Phase 2.8: Post-Migration "Golden State" Baseline Verification (COMPLETE)
Following successful network refactoring and deception validation, a comprehensive multi-host snapshot protocol was executed to secure the newly synchronized, stealth-configured lab state.

### ✅ Completed Safeguard Milestones
* [x] **Proxmox Overprovisioning Audit:** Checked thin-pool LVM allocations (`local-lvm`) to verify physical storage volume health and ensure data-safety thresholds are maintained.
* [x] **Windows Endpoint Snapshot:** Captured a fresh, live hypervisor snapshot (`Post_Migration_Golden_State`) encapsulating the active target workspace and re-routed forwarder configuration parameters.
* [x] **Kali Threat Node Snapshot:** Generated a matching snapshot profile (`Post_Migration_Golden_State`) securing the manual, camouflage IoT network interface assignment.
* [x] **VirtualBox SIEM Engine Snapshot:** Documented cold-state engine backups (`Post_Migration_Golden_State`) on the Ryzen server host to protect the newly customized indexer port structures.
* [x] **Gateway Configuration Archive:** Downloaded an up-to-date, sanitized `config.xml` profile from the OPNsense administrative console to back up the newly updated DHCP pool ranges.

---

## 🛠️ Phase 3: Defensive Analytics & Attack Simulation (IN PROGRESS)

### ✅ Completed Milestones
* [x] Created hollow Proxmox VM Container profile 200 (`KaliAttackNode`) allocated with 2 CPU Cores, 2GB RAM, and `vmbr0` bridge attachment.
* [x] Executed low-level backend disk migration and format conversion via Proxmox Shell using `qm importdisk`.
* [x] Successfully mapped and attached the raw `scsi0` virtual hard drive to the container hardware configuration layout.
* [x] Reconfigured system Boot Order properties to prioritize the native SCSI drive image.
* [x] Booted the local Proxmox Kali Linux node and initialized networking commands to check operational interface profiles.
* [x] Cleared locked and corrupted APT package metadata caches from `/var/lib/dpkg/lock-frontends`
* [x] Ran low-level package reconfiguration (`sudo dpkg --configure -a`) to fix interrupted installations
* [x] Force-resolved broken system dependencies using `sudo apt install -f`
* [x] Updated local repository mirrors and upgraded core distribution packages (`sudo apt update && sudo apt upgrade -y`)
* [x] Successfully installed the **xrdp** remote desktop protocol daemon package
* [x] Registered and enabled the `xrdp` systemd service unit to persist across node reboots
* [x] Confirmed active network socket listening state on local TCP Port `3389`
* [x] Successfully established an isolated RDP session from the main Ryzen workstation host into `KaliAttackNode`
* [x] Audited the OPNsense Web UI DHCP Leases table to extract the precise runtime IP profile for `KaliAttackNode`.
* [x] Convert the parsed Splunk statistics table into a live Classic Dashboard tracking interface.

### 📋 Next Action Items
- [ ] Launch a stealth SYN network scan (`nmap -sS`) from the hidden Kali IoT camera interface against the target endpoint scope.
- [ ] Audit Splunk dashboards using Sysmon EventCode 3 to isolate connection frequencies and analyze attacker footprints.
- [ ] Spin up the Python3 HTTP server staging engine on the Kali workspace platform.
- [ ] Execute the `certutil.exe` defense evasion string from the Windows target command shell to trigger host detection hooks.
