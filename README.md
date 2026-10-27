# 🔐 Cybersecurity Home Lab Setup with Kali Linux & VirtualBox

Building a virtual lab environment for cybersecurity learning, network analysis, and ethical penetration testing.

## 📌 Project Overview

This project demonstrates how to build a virtual cybersecurity lab using Oracle VirtualBox and Kali Linux.

The goal is to create a controlled environment for learning cybersecurity fundamentals, exploring network security tools, performing network reconnaissance, and practicing authorized security assessments.

The lab uses a VirtualBox NAT Network to support communication between virtual machines while providing outbound network access. Additional VMs can be introduced later for practical security exercises.

## 🎯 Project Objectives

- Install and configure Oracle VirtualBox.
- Set up Kali Linux as a virtual machine.
- Create a dedicated NAT Network for the lab.
- Configure and verify Kali Linux network settings.
- Establish consistent IP addressing for lab machines.
- Test network connectivity and DNS resolution.
- Create a baseline snapshot for recovery.
- Document the installation process and troubleshooting steps.
- Prepare the lab for future cybersecurity experiments.

## 🛡️ Lab Use Cases

This virtual environment can support educational exercises involving:

- Network discovery and reconnaissance
- Port scanning with Nmap
- Network traffic analysis
- Basic vulnerability assessment
- Web application security testing
- Cybersecurity tool familiarization
- Safe testing against intentionally vulnerable lab machines

**Ethical use:** All testing must be limited to systems you own or have explicit authorization to assess.

## 🏗️ Lab Architecture

The lab consists of a host computer running VirtualBox, with Kali Linux connected to a dedicated virtual NAT Network.

Additional virtual machines can be connected to the same network for isolated, authorized testing.

## ⚙️ Environment Specifications

| Component | Configuration |
|---|---|
| Host Operating System | Windows 10 |
| Virtualization Software | Oracle VirtualBox 7.2 |
| Security Distribution | Kali Linux |
| Memory Allocated to Kali | 2 GB |
| Network Mode | NAT Network |
| Network Prefix | 10.0.0.0/24 |
| Kali IPv4 Address | 10.0.0.2/24 |
| Default Gateway | 10.0.0.1 |
| DNS Server | 8.8.8.8 |
| Future Lab VM Addresses | 10.0.0.3–10.0.0.99 |

*Note: These values describe the planned lab configuration. Verify them against your actual VirtualBox and Kali settings before publishing.*

## 🪜 Installation and Configuration

### Step 1: Install 7-Zip

Install 7-Zip if needed to extract the downloaded Kali virtual machine archive.

Download: https://www.virtualbox.org/wiki/Downloads

### Step 2: Set Up VirtualBox

Download and install Oracle VirtualBox. Confirm that hardware virtualization is enabled if your system requires it.

Download: https://www.virtualbox.org/wiki/Downloads

### Step 3: Configure a Dedicated Virtual Network

Create a NAT Network in VirtualBox with the following settings:


- **Network Name:** NatNetwork
- **IPv4 Prefix:** 10.0.0.0/24
- **DHCP:** Enabled
- **IPv6:** Disabled

A NAT Network can allow connected virtual machines to communicate with one another and access external networks through network address translation.

### Step 4: Import Kali Linux

Download the appropriate Kali Linux VirtualBox image from the official website and import it into VirtualBox.

Download: https://www.kali.org/get-kali/

Configure the virtual machine:

- **Network Adapter:** Adapter 1
- **Attached To:** NAT Network
- **Network:** NatNetwork
- **Adapter Type:** Intel PRO/1000 MT Desktop
- **Memory:** 2048 MB

A shared folder may also be configured for transferring files between the host and the virtual machine. Use appropriate permissions when sharing files.

### Step 5: Configure Network Connectivity

Inspect the network interfaces and IP configuration from Kali Linux:

```bash
ip a
ip route
```

If a static IP address is required, configure it through the appropriate NetworkManager connection settings.

Example target configuration:

- **IPv4 Address:** 10.0.0.2/24
- **Gateway:** 10.0.0.1
- **DNS:** 8.8.8.8

Ensure the chosen address does not conflict with another device or a DHCP-assigned address. The gateway and DNS settings must match the actual virtual network configuration.

### Step 6: Create a Baseline Snapshot

Once the operating system and network configuration are working, create a snapshot in VirtualBox.

**Suggested snapshot name:** `Kali-Baseline-Setup`

This snapshot provides a recovery point before future experiments or configuration changes.

## 🔎 Verification and Testing

Run the following checks to confirm the basic lab configuration.

| Check | Command | Purpose |
|---|---|---|
| IP configuration | `ip a` | Inspect assigned IP addresses |
| Routing table | `ip route` | Verify the default route |
| Gateway connectivity | `ping -c 4 10.0.0.1` | Test reachability of the gateway |
| External connectivity | `ping -c 4 8.8.8.8` | Check basic IP connectivity |
| DNS resolution | `nslookup kali.org` | Test DNS lookup |
| Nmap installation | `nmap --version` | Confirm Nmap is installed |
| Snapshot recovery | Restore the baseline snapshot | Verify recovery capability |

*Expected results depend on the actual network settings. A failed ping does not always mean the network is broken because ICMP traffic may be blocked.*
l .
