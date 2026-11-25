# Setup of Metasploitable 2 and Kali Linux in VirtualBox 

## Metaploitable 2 - Target Machine

**Metasploitable 2** is an intentionally vulnerable Linux-based virtual machine developed by *Rapid7*. It is designed for **Cybersecurity training**, **Penetration Testing Practice**, and **Vulnerability assessment**.
In this lab, Metasploitable 2 will be configured as the target machhine, while Kali Linux will serve as the attacker machine.
The Objective is to establish a controlled and isolated penetration testing environment for conducting security assessments.

## Kali Linux - Attacker Machine

**Kali Linux** is a Debian-based Linux distribution developed by *Offensive Security* (OffSec), specifically designed for **penetration testing**, **ethical hacking**, **vulnerability assessment**, and **digital forensics**.
It provides a comprehensive collection of security tools for **network reconnaissance**, **vulnerability discovery**, **exploitation**, **web application testing**, and **security auditing**.
In this project, kali Linux serves as the attacker machine, which will be used to perform security assessments againest the intentionally vulnerable Metasploitable 2 virtual machine

## Oracle VirtualBox - Virtualization Platform

**Oracle VM VirtualBox** is a free and open-source virtualization software that allows users to create and run multiple virtual machines on a single physical computer.
It provides an isolated environment for installing, configuring, and testing different operating systems without modifying the host operating system.
In this project, VirtualBox is used as the virtualization platform to run Kali Linux (Attacker Machine) and Metasploitable 2 (Target Machine) for conducting controlled penetration testing and vulnerability assessments.


### Lab Requirements

| Component | Description
|----------------|-----------------------------|
| Attacker Machine | Kali Linux |
| Target Machine | Metasploitable 2 |
| Virtualization Software | Oracle VirtualBox |
| Network Configuration | Internal NAT Network |

### Lab Environment

- Attacker: Kali Linux
- Target: Metasploitable 2
- Hypervisor: VirtualBox
- Network: Isolated Virtual Network (NAT)

### Setup Objectives

