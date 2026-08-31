# networkwalks-B082-week1-Cybersecurity-lab-setup



<div align="center">

# 

 **Cybersecurity Laboratory Setup**

</div>
<p align="center">
  <img src="https://img.shields.io/badge/Skill-Cybersecurity-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ver-Virtualbox%20v7.2-0070C0?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Kali%20Linux-v2026.2-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Linux-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Network-10.0.0.0%2F24-238F89?style=flat-square&labelColor=000000" />
  <img src="https://img.shields.io/badge/Penetration%20Testing-C00000?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Skill-Virtualization-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/GitHub-404040?style=flat-square&labelColor=0070C0&logo=github&logoColor=white" />
  <img src="https://img.shields.io/badge/Kali%20Linux-404040?style=flat-square&labelColor=C00000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/NetworkWalks-404040?style=flat-square&labelColor=C00000" />
  <img src="https://img.shields.io/badge/Ethical%20Hacking-E87500?style=flat-square&labelColor=000000&logo=kalilinux&logoColor=white" />
  <img src="https://img.shields.io/badge/Waqas%20Karim%20CCIE-C00000?style=flat-square" />
</p>

## Installation and Configuration of Kali Linux on Virtual Box

This document records the setup and configuration of my First week of personal cybersecurity laboratory for the NetworkWalks B082 cybersecurity internship programme.

The purpose of this laboratory is to provide a controlled and isolated environment for learning cybersecurity concepts and performing authorised security exercises.

---

## 1. Laboratory Objective

The primary objective is to establish a functional cybersecurity learning environment that allows me to safely practise:

* Linux administration
* Networking
* Network security
* Vulnerability assessment
* Security testing
* Cybersecurity tools
* Defensive security techniques

The laboratory will be developed progressively as the training programme advances.

---

## 2. Host Computer

The physical computer serves as the host machine for the cybersecurity laboratory.

### Host specifications

| Component                 | Specification                  |
| ------------------------- | ------------------------------ |
| Manufacturer              | HP                             |
| Model                     | ProBook 640                    |
| Processor                 | Intel Core i5-4300M @ 2.60 GHz |
| Host Operating System     | Windows                        |
| Virtualisation Platform   | VirtualBox                     |
| Virtualisation Technology | Intel VT-x                     

---

## 3. Virtualisation Platform

### Oracle VirtualBox

VirtualBox is being used as the virtualisation platform for this laboratory.

The purpose of VirtualBox is to allow Kali Linux to operate as a guest operating system without replacing the Windows host operating system.

### Benefits

Virtualisation provides:

* Isolation from the host system
* Safe experimentation
* Ability to create snapshots
* Easier recovery from configuration errors
* Repeatable laboratory environments
* Ability to run multiple operating systems on one computer

---

## 4. Guest Operating System

### Kali Linux

Kali Linux is the primary cybersecurity-focused operating system used in this laboratory.

It provides a collection of tools for areas including:

* Network discovery
* Security assessment
* Vulnerability research
* Web security testing
* Digital forensics
* Wireless security
* Password auditing
* Penetration testing


🪜 Lab Setup Procedure
-----
Step 1. Install 7-Zip
7-Zip was installed to extract the Kali Linux virtual-machine package, which may be distributed as a .7z archive.

Tool: 7-Zip
----------
Step 2. Install VirtualBox
VirtualBox was installed as the hypervisor.
-------
Step 3. Create the NAT Network
A dedicated NAT Network was created in VirtualBox.
-------
Configuration: Network Name: NatNetwork IPv4 Prefix: 10.0.0.0/24 DHCP: Enabled IPv6: Disabled


A NAT Network was selected because multiple virtual machines connected to the same NAT Network can communicate with one another while also having outbound network connectivity.

This will allow future attacker and target VMs to communicate within the lab.

Step 4. Import Kali Linux
------
The Kali Linux virtual machine was downloaded from the official Kali Linux website and imported into VirtualBox.

The VM network adapter was configured as follows:
-----
Adapter 1
Attached to: NAT Network
Network:     NatNetwork
Adapter Type: Intel PRO/1000 MT Desktop
The VM was allocated:

RAM: 2048 MB
 A shared folder was also configured for transferring required files between the host operating system and the Kali VM.

Step 5. Configure the Kali Linux Network
-------
The Kali Linux network configuration was checked and configured with a consistent IPv4 address.

Example configuration:

IP Address: 10.0.0.2
Subnet Mask: 255.255.255.0
Gateway: 10.0.0.1
DNS: 8.8.8.8
A consistent IP address makes it easier to document the lab and reference the Kali machine in future exercises.



Step 6. Create a Clean VM Snapshot
------
After completing the initial configuration, a VirtualBox snapshot was created.

Example snapshot name:

Clean Kali - Network Setup
The snapshot represents the clean baseline of the laboratory.

If a future exercise changes or damages the VM configuration, the machine can be restored to this baseline.


---

## 5. Problem Encountered

### A. During the initial attempt to start the Kali Linux virtual machine, VirtualBox reported an error.

The important error messages included:

"Not in a hypervisor partition (HVP=0)
(VERR_NEM_NOT_AVAILABLE)

VT-x is disabled in the BIOS for all CPU modes
(VERR_VMX_MSR_ALL_VMX_DISABLED)"

This prevented the Kali Linux virtual machine from starting correctly.

### B.Internet Connectivity After Static IP Configuration
-----
After manually configuring the IPv4 settings, Internet connectivity may fail depending on the Kali/NetworkManager configuration.

One workaround used during this lab was the command line:

sudo nmcli connection modify "Wired connection 1" ipv4.dad-timeout 0
The network connection was then restarted/rebooted and connectivity was tested again.

##6. Troubleshooting
   -----
The corrective action I took involve investigating the computer's firmware/BIOS virtualisation settings and ensuring that Intel VT-x is enabled.
The BIOS/UEFI virtualisation status was disabled as at the time I checked. To correct the error I had to enter the BOS set up and locate the Intel Virtualisation set up and set it to enable by checking the box beside it. After that i save the change(s) made and exit.
Below was my next action:
Your next action

Restart → Esc repeatedly → F10 → find Virtualization Technology (VTx) → Enable → Save → boot Windows → check Task Manager.
Below is a summary of before and after applying the changes to the virtualization issue.
## Before
                 YOUR HP PROBOOK 640                                   
                         │
                         ▼
              Intel Core i5-4300M
                         │
                         │ VT-x available
                         ▼
                  BIOS / UEFI
                         │
                 ❌ VT-x DISABLED
                         │
                         ▼
                    Windows
                         │
                         ▼
                   VirtualBox
                         │
                         ▼
                  Kali Linux VM
                         │
                   ❌ WON'T START
                   
## After 
                                    Intel Core i5-4300M
                                            │
                                            ▼
                                     BIOS: VT-x ENABLED
                                            │
                                            ▼
                                          Windows
                                            │
                                            ▼
                                        VirtualBox
                                            │
                                            ▼
                                        Kali Linux
                                            │
                                            ▼
                                        ✅ STARTS

7💡 What I Learned

Through this project, I learned how to create and configure a virtual environment for cybersecurity practice.

The most important concepts I learned include:
1. NAT vs NAT Network.
   --------
A standard NAT configuration and a NAT Network serve different purposes.

A NAT Network allows multiple VMs connected to the same virtual network to communicate with one another while providing network address translation for external connectivity.

This makes it useful for building a multi-machine cybersecurity laboratory.

2. Virtual Machine Networking.
   -------
I learned how VirtualBox virtual network adapters connect virtual machines to different types of networks and how network configuration affects communication between machines.

4. Static IP Configuration
   -------
I learned how to configure and verify IPv4 addressing, subnet masks, gateways, and DNS settings in Kali Linux.

6. VM Snapshots
   ------
I learned that a clean snapshot should be created before performing risky or experimental activities.

This provides a known-good recovery point for future cybersecurity exercises.

5. Documentation
   ------
I learned that documenting commands, configuration, screenshots, problems, and solutions is an important part of a professional cybersecurity project.

Tools & Resources
----------

7-Zip: https://7-zip.org/download.html

VirtualBox: https://virtualbox.org/wiki/Downloads

Kali Linux: https://kali.org/get-kali

👤 Author
Ashikem Joshua
Cybersecurity Enthusiast B082
https://bit.ly/4wE1QsL
