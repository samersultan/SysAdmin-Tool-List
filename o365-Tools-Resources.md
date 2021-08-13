## o365 Tools and Resources  

Samer Sultan
https://www.sultansolutions.com

@SultanSolutions

---


**o365 / Azure Service Health** - Alerts for o365  / Azure services 

https://status.azure.com/en-us/status

&nbsp;
&nbsp;


**GCITS o365 Knowledgeable** - Resource for o365 User Guides / Trouble Shooting

https://gcits.com/knowledge-base/

&nbsp;
&nbsp;

**o365 Admin Center Tool** - Simple desktop UI for o365 managment

https://github.com/bwya77/O365-Admin-Center

&nbsp;
&nbsp;

**Managing Private Channels in Microsoft Teams** - Restrict the ability to create private channels in teams 

https://blog.admindroid.com/managing-private-channels-in-microsoft-teams/

&nbsp;
&nbsp;

 **Block Self Service Purchase o365** - Block Self-Service Purchase for Power Platform Products Using PowerShell
 
 https://blog.admindroid.com/block-self-service-purchase-for-power-platform-products-using-powershell/
 
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

---
