## Scripting Resources (Powershell / Linux)

Samer Sultan
https://www.sultansolutions.com

@SultanSolutions

---


**SS64** - Command line reference – Database and OS scripting

https://ss64.com/

&nbsp;
&nbsp;

**POSH GUI** - (Powershell GUI Designer)

https://poshgui.com/

&nbsp;
&nbsp;

**Dicio** - Runs powershell scripts targeting multiple hosts at once.

https://github.com/Wrexthor/Dicio

&nbsp;
&nbsp;

**PowerShell Script Browser** - Search through library of TechNet PowerShell scripts

https://www.powershellgallery.com/packages/ScriptBrowser/1.3.1.0


```powershell
Install-Module -Name Scriptbrowser


Enable-ScriptBrowser

```

&nbsp;
&nbsp;


**PowerShell  ISEScriptAnalyzerAddOn** - PowerShell Script Analyzer

https://www.powershellgallery.com/packages/ISEScriptAnalyzerAddOn/1.0

```powershell
Install-Module -Name ISEScriptAnalyzerAddOn


Enable-ScriptAnalyzer

```

&nbsp;
&nbsp;

**Disabling IMAP and POP for all future mailboxes** 

```powershell

Get-CASMailboxPlan -Filter {ImapEnabled -eq "true" -or PopEnabled -eq "true" } | set-CASMailboxPlan -ImapEnabled $false -PopEnabled $false

```

&nbsp;
&nbsp;

**Disabling IMAP and POP for all existing mailboxes**

```powershell

Get-CASMailbox -Filter {ImapEnabled -eq "true" -or PopEnabled -eq "true" } | Select-Object @{n = "Identity"; e = {$_.primarysmtpaddress}} | Set-CASMailbox -ImapEnabled $false -PopEnabled $false

```
&nbsp;
&nbsp;
