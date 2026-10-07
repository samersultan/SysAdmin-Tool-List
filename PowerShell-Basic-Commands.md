## PowerShell Commands

Samer Sultan  
https://www.sultansolutions.com  

@SultanSolutions

---

# Network Troubleshooting

## Check if Hostname + Port is Reachable

```powershell
Test-NetConnection [FQDN/IP Address] -Port [Port]
```

Example:

```powershell
Test-NetConnection google.com -Port 443
```

Show only whether the TCP connection succeeded:

```powershell
Test-NetConnection google.com -Port 443 |
Select-Object ComputerName, RemoteAddress, RemotePort, TcpTestSucceeded
```

---

## Test Basic Connectivity

```powershell
Test-Connection [Hostname/IP]
```

Example:

```powershell
Test-Connection google.com
```

Single ping:

```powershell
Test-Connection google.com -Count 1
```

---

## Resolve DNS Name

```powershell
Resolve-DnsName [Hostname]
```

Example:

```powershell
Resolve-DnsName google.com
```

Query a specific DNS server:

```powershell
Resolve-DnsName google.com -Server 8.8.8.8
```

---

## Display IP Configuration

```powershell
Get-NetIPConfiguration
```

More detailed information:

```powershell
Get-NetIPConfiguration -Detailed
```

Traditional output:

```powershell
ipconfig /all
```

---

## Show DNS Servers

```powershell
Get-DnsClientServerAddress
```

IPv4 only:

```powershell
Get-DnsClientServerAddress -AddressFamily IPv4
```

---

## Clear DNS Cache

```powershell
Clear-DnsClientCache
```

Equivalent command:

```powershell
ipconfig /flushdns
```

---

## Show Network Adapters

```powershell
Get-NetAdapter
```

Only connected adapters:

```powershell
Get-NetAdapter |
Where-Object Status -eq "Up"
```

---

## Restart Network Adapter

```powershell
Restart-NetAdapter -Name "Ethernet"
```

For Wi-Fi:

```powershell
Restart-NetAdapter -Name "Wi-Fi"
```

---

## Show Routing Table

```powershell
Get-NetRoute
```

IPv4 routes only:

```powershell
Get-NetRoute -AddressFamily IPv4
```

Default route:

```powershell
Get-NetRoute -DestinationPrefix "0.0.0.0/0"
```

---

## Show Active TCP Connections

```powershell
Get-NetTCPConnection
```

Established connections only:

```powershell
Get-NetTCPConnection -State Established
```

Find connections using a specific port:

```powershell
Get-NetTCPConnection -LocalPort 443
```

---

## Find Which Process is Using a Port

```powershell
Get-NetTCPConnection -LocalPort [Port] |
Select-Object LocalAddress, LocalPort, State, OwningProcess
```

Then find the process:

```powershell
Get-Process -Id [PID]
```

Example:

```powershell
Get-Process -Id (Get-NetTCPConnection -LocalPort 443).OwningProcess
```

---

## Trace Network Path

```powershell
Test-NetConnection google.com -TraceRoute
```

Traditional command:

```powershell
tracert google.com
```

---

## Display ARP / Neighbor Table

```powershell
Get-NetNeighbor
```

IPv4 only:

```powershell
Get-NetNeighbor -AddressFamily IPv4
```

---

## Check Windows Firewall Profiles

```powershell
Get-NetFirewallProfile
```

Show whether each firewall profile is enabled:

```powershell
Get-NetFirewallProfile |
Select-Object Name, Enabled
```

---

## Search Windows Firewall Rules

```powershell
Get-NetFirewallRule |
Where-Object DisplayName -Like "*RDP*"
```

Show enabled rules:

```powershell
Get-NetFirewallRule |
Where-Object Enabled -eq "True"
```

---

## Check Listening Ports

```powershell
Get-NetTCPConnection -State Listen
```

Sort by port:

```powershell
Get-NetTCPConnection -State Listen |
Sort-Object LocalPort |
Select-Object LocalAddress, LocalPort, OwningProcess
```

---

## Check Computer Hostname

```powershell
hostname
```

PowerShell-native method:

```powershell
$env:COMPUTERNAME
```

---

## Check Current Logged-In User

```powershell
whoami
```

PowerShell:

```powershell
[System.Security.Principal.WindowsIdentity]::GetCurrent().Name
```

---

## Check Domain Membership

```powershell
Get-CimInstance Win32_ComputerSystem |
Select-Object Name, Domain, PartOfDomain
```

---

## Check Domain Controller Being Used

```powershell
nltest /dsgetdc:$env:USERDNSDOMAIN
```

Check the logon server:

```powershell
$env:LOGONSERVER
```

---

## Check Network Profile

```powershell
Get-NetConnectionProfile
```

Displays whether the connection is:

- DomainAuthenticated
- Private
- Public

---

## Display Public IP Address

```powershell
Invoke-RestMethod https://api.ipify.org
```

---

## Display Local IPv4 Addresses

```powershell
Get-NetIPAddress -AddressFamily IPv4 |
Where-Object IPAddress -NotLike "169.254*" |
Select-Object InterfaceAlias, IPAddress, PrefixLength
```

---

## Test Multiple Ports

```powershell
80,443,3389 | ForEach-Object {
    Test-NetConnection server01 -Port $_ |
    Select-Object ComputerName, RemotePort, TcpTestSucceeded
}
```

---

## Continuous Connectivity Test

```powershell
Test-Connection google.com -Continuous
```

Stop with:

```text
Ctrl + C
```
