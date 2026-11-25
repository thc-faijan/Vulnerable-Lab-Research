# Setup of Metasploitable 2 and Kali Linux in VirtualBox 

## Metaploitable 2 - Target Machine

**Metasploitable 2** is an intentionally vulnerable Linux-based virtual machine developed by *Rapid7*. It is designed for **Cybersecurity training**, **Penetration Testing Practice**, and **Vulnerability assessment**.
In this lab, Metasploitable 2 will be configured as the target machhine, while Kali Linux will serve as the attacker machine.
The Objective is to establish a controlled and isolated penetration testing environment for conducting security assessments.

## Kali Linux - Attacker Machine

**Kali Linux** is a Debian-based Linux distribution developed by *Offensive Security* (OffSec), specifically designed for **penetration testing**, **ethical hacking**, **vulnerability assessment**, and **digital forensics**.
It provides a comprehensive collection of security tools for **network reconnaissance**, **vulnerability discovery**, **exploitation**, **web application testing**, and **security auditing**.
In this project, kali Linux serves as the attacker machine, which will be used to perform security assessments againest the intentionally vulnerable Metasploitable 2 virtual machine

## VirtualBox - Virtualization Platform

**Oracle VM VirtualBox** is a free and open-source virtualization software that allows users to create and run multiple virtual machines on a single physical computer.
It provides an isolated environment for installing, configuring, and testing different operating systems without modifying the host operating system.
In this project, VirtualBox is used as the virtualization platform to run Kali Linux (Attacker Machine) and Metasploitable 2 (Target Machine) for conducting controlled penetration testing and vulnerability assessments.

---

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

## Setup Objectives

### Download and Setup Metasploiable 2

Go to any Browser and Search Metasploitable 2 and click Source Forge website link then after getting in you will see a Download option click that and download, Wait to complete it 

Direct Download Link:
[Metasploitable 2](https://sourceforge.net/projects/metasploitable/files/lates/download)

After completing go to the Download folder in your PC and right click that downloaded Metasploitable zip folder and Extract that (You can use 7zip application to Extract without any error) after extracting leave that as it is.

- Then open the VirtualBox and click new (left upper corner) , Then Give a name VNName to *Metasploitable 2* , leave VM folder as default , Select OS as *Linux* and OS Distribution choose *Other Linux* , inside OS version *x64-bit*
- Choose Hardware configuration according to your system give this at least *512 MB* Base Memory and CPUs *1*
- Specify  virtual Hard disk --> use an Existing Virtual Hard Disk , File click *Add* button --> then specify that downloaded , Extracted folder where the *Metasploitable.vmdk* file will appear then double click that file and click finish.

![VirtualBox Setup]("Metasploitable-2/01-Lab-Setup/Screenshots/Setup Meta 1.png")

![VirtualBox Setup]("Metasploitable-2/01-Lab-Setup/Screenshots/Setup Meta 2.png")

## Network Configuration 
- VirtualBox 
Click the *file* option (Upper Left Corner in VirtualBox) --> *Tools* --> *Network* --> *NAT Networks* --> Create --> General options then rename it as your Choice i'm using ***MetaKali_Lab*** and also changed ip address to ***10.10.10.0/24*** then click apply

- Kali Linux
Click *Kali Linux machine* and go to the ***Expert Setting*** then *Network* select attached to ***NAT Network*** from drop down menu then name choose to ***MetaKali_Lab*** which you see in the Drop Down Menu then click *apply*

- Metasploitable 
Click *Metasploitable Machine* then go to the Export Setting --> *Network* --> Attacked to ***NAT Network*** and name choose to ***MetaKali_Lab*** then OK

Now Start Metasploitable 2 by clicking start button the wait for 10-20 Sec to Load then this will ask for *username:password* here are the login:pass ***msfadmin:msfadmin***

Credntials
| Username | Password|
|----------|---------|
| User :   | msfadmin|
|password : | msfadmin|

afte putting these credentials you will be redirected to the command prompt as login then type:
```bash
ifconfig
```
![IP Checking]("Metasploitable-2/01-Lab-Setup/Screenshots/Meta ifconfig.png")

You will get the network information of the Metasploitable 2 machine

- then go back to the VirtualBox Start Kali Linux and login then open the Terminal and type these commands:
```bash
ping -c4 10.10.10.3 #put your metasploitable ip here
```
![Network Connection Check]("Metasploitable-2/01-Lab-Setup/Screenshots/Kali Linux ping.png")

if responce is showing as *64* then congratulations to you, You Set it UP....!!!