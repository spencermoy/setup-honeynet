## Setting Up The Honeynet & Simulating Attacks

## Network Security Group
Setting up a Honeynet and simulating attacks involves several steps. After creating the VM in Azure, the next step is to configure the Network Security Group (NSG) to allow all traffic inbound. I added a new inbound rule that has higher priority than the RDP inbound security rule and entered "*" in Destination port ranges to all traffic inbound.
![nsg-add-inbound-rule-allow-all](https://github.com/spencermoy/azure-soc-honeynet/assets/137566643/49ad4e02-9375-4e5a-a05e-e3673c1e8888)

## Firewall
The next step is to turn off the Windows Firewall or turn off the firewall except IPSec. This is done to ensure that the traffic is not blocked by the firewall
![firewall-off](https://github.com/spencermoy/azure-soc-honeynet/assets/137566643/0aecaa06-48ba-4cd8-9751-c132ee66c94f)

## SQL Audit Logs





