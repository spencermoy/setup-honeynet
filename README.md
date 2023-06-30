## Setting Up The Honeynet & Simulating Attacks

## Network Security Group
Setting up a Honeynet and simulating attacks involves several steps. After creating the VM in Azure, the next step is to configure the Network Security Group (NSG) to allow all traffic inbound. I added a new inbound rule that has higher priority than the RDP inbound security rule and entered "*" in Destination port ranges to all traffic inbound.
![nsg-add-inbound-rule-allow-all](https://github.com/spencermoy/azure-soc-honeynet/assets/137566643/49ad4e02-9375-4e5a-a05e-e3673c1e8888)<br>

## Firewall
The next step is to turn off the Windows Firewall or turn off the firewall except IPSec. This is done to ensure that the traffic is not blocked by the firewall
![firewall-off](https://github.com/spencermoy/azure-soc-honeynet/assets/137566643/0aecaa06-48ba-4cd8-9751-c132ee66c94f)<br>

## SQL Installation & Windows Event Porting

I installed SQL Server Management Studio (SSMS) and selected "Mixed Mode" during installation to enable SQL server authentication. This allowed me to simulate attacks and test the security of the system.
![sql-mixed-login](https://github.com/spencermoy/azure-soc-honeynet/assets/137566643/6689c1bd-aec2-47ea-88ca-a2d1662357c1)<br>
To further enhance the security of the system, I enabled logging for SQL Server to be ported into Windows Event Viewer. I went to Properties > Security > Logon Audit and selected both failed and successful logins.
![sql-properties](https://github.com/spencermoy/azure-soc-honeynet/assets/137566643/5afd0f24-d1ad-4bf3-8b38-7e63dc6146c3)<br><br>
I also allowed all inbound and outbound traffic by configuring audit object access settings in Windows using auditpol.
![command-line-audit](https://github.com/spencermoy/azure-soc-honeynet/assets/137566643/a9bac126-d671-49ec-aa53-51b7897f9eac)<br><br>
To provide full permission for SQL server to registry hive, I accessed the registry editor (regedit) and added a user in security and allowed full control and read. I right-clicked Permissions, added NETWORK SERVICE, and granted full control and read access.
![registry-add-network-server2](https://github.com/spencermoy/setup-honeynet/assets/137566643/78027766-6bb7-44f6-ab8c-cefd02d7f4c5)<br>
![registry-network-server-allow](https://github.com/spencermoy/azure-soc-honeynet/assets/137566643/13e74fdf-e081-4058-9c8b-95ed868be3ef)<br><br>
Here is the Microsoft documentation about "Write SQL Server Audit events to the Security log":<br>
https://learn.microsoft.com/en-us/sql/relational-databases/security/auditing/write-sql-server-audit-events-to-the-security-log?view=sql-server-ver16






