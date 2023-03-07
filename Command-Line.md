## Windows Command Line Commands

Samer Sultan
https://www.sultansolutions.com

@SultanSolutions

---

List of useful / less known command line commands for Windows (Run cmd.exe as local admin). A good overview of windows command line can be found here: https://learn.microsoft.com/en-us/windows/terminal/command-line-arguments?tabs=windows

<img src="https://i.imgur.com/zKVXbUP.png">

---


**Reboot To Bios** - Force Reboot System into BIOS. 

```
shutdown /r /fw /f /t 0
```

&nbsp;
&nbsp;

---

**Get System MAC Address** - Provides you with a list of Netwrok Adapter MAC Addresses 

```
getmac /v
```
&nbsp;
&nbsp;

---

**Show File Assoications** - Displays a list of all the current file name extension associations

```
 assoc
 ```
 
 To see file type associated .txt file
 
 ```
 assoc .txt
 ```
 To remove file type association with .txt
 
 ```
 assoc .txt=
 ```
 
More exaples: https://learn.microsoft.com/en-us/windows-server/administration/windows-commands/assoc

&nbsp;
&nbsp;

---
 
 **Force System Reboot / Shutdown** - Force Reboot or Shutdown the system 


To Force Reboot
```
shutdown.exe -f -r -t 00
```


To Force Shutdown
```
shutdown.exe -f -s -t 00
```


&nbsp;
&nbsp;

---
 
