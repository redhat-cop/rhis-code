# Cost estimation
This document covers draft high level estimation of the expected monthly
costs for the project resources on Azure.

## Microsoft Azure Estimate

!!! quote
    All prices shown are in Euro Zone – Euro (€) EUR. This estimate was created at 4/26/2024 1:18:50 PM UTC.

    1.  Estimation done for a monthly of 300 hours to use.
    2.  The system disks use mainly Standard SSD.
    3.  One Region used only for lowering bandwith requirements.


<table style="width:100%;">
<colgroup>
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
<col style="width: 14%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">Service category</th>
<th style="text-align: left;">Service type</th>
<th style="text-align: left;">Region</th>
<th style="text-align: left;">Description</th>
<th style="text-align: left;">Estimated monthly cost</th>
<th style="text-align: left;">Resource Name</th>
<th style="text-align: left;"></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;"><p>Compute</p></td>
<td style="text-align: left;"><p>Virtual Machines</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>1 E4as v5 (4 vCPUs, 32 GB RAM) x 300
Hours (Pay as you go), Linux, (Pay as you go); 1 managed disk – E6;
Inter Region transfer type, 5 GB outbound data transfer from Germany
West Central to East Asia</p></td>
<td style="text-align: left;"><p>€ 80.34</p></td>
<td style="text-align: left;"><p>Red Hat Satellite Server</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Compute</p></td>
<td style="text-align: left;"><p>Virtual Machines</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>1 E2as v5 (2 vCPUs, 16 GB RAM) x 300
Hours (Pay as you go), Linux, (Pay as you go); 1 managed disk – E15;
Inter Region transfer type, 5 GB outbound data transfer from Germany
West Central to East Asia</p></td>
<td style="text-align: left;"><p>€ 55.69</p></td>
<td style="text-align: left;"><p>Red Hat Satellite Capsule
Server</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Compute</p></td>
<td style="text-align: left;"><p>Virtual Machines</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>2 D2as v5 (2 vCPUs, 8 GB RAM) x 300
Hours (Pay as you go), Linux, (Pay as you go); 2 managed disks – E4;
Inter Region transfer type, 5 GB outbound data transfer from Germany
West Central to East Asia</p></td>
<td style="text-align: left;"><p>€ 62.06</p></td>
<td style="text-align: left;"><p>Red Hat IdM Server</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Compute</p></td>
<td style="text-align: left;"><p>Virtual Machines</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>3 B2pls v2 (2 vCPUs, 4 GB RAM) x 300
Hours (Pay as you go), Linux, (Pay as you go); 3 managed disks – E4;
Inter Region transfer type, 5 GB outbound data transfer from Germany
West Central to East Asia</p></td>
<td style="text-align: left;"><p>€ 38.56</p></td>
<td style="text-align: left;"><p>Red Hat Test VMs</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Compute</p></td>
<td style="text-align: left;"><p>Virtual Machines</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>1 B2als v2 (2 vCPUs, 4 GB RAM) x 10
Hours (Pay as you go), Linux, (Pay as you go); 1 managed disk – E4;
Inter Region transfer type, 5 GB outbound data transfer from Germany
West Central to East Asia</p></td>
<td style="text-align: left;"><p>€ 2.62</p></td>
<td style="text-align: left;"><p>rootCA</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Compute</p></td>
<td style="text-align: left;"><p>Virtual Machines</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>1 DC2s v3 (2 Cores, 16 GB RAM) x 300
Hours (Pay as you go), Linux, (Pay as you go); 1 managed disk – P6;
Inter Region transfer type, 5 GB outbound data transfer from Germany
West Central to East Asia</p></td>
<td style="text-align: left;"><p>€ 42.23</p></td>
<td style="text-align: left;"><p>Postgresql DB Server</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Compute</p></td>
<td style="text-align: left;"><p>Virtual Machines</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>1 E4-2s v3 (2 vCPUs, 32 GB RAM) x 300
Hours (Pay as you go), Linux, (Pay as you go); 1 managed disk – E6;
Inter Region transfer type, 5 GB outbound data transfer from Germany
West Central to East Asia</p></td>
<td style="text-align: left;"><p>€ 88.65</p></td>
<td style="text-align: left;"><p>AAP Controller</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Compute</p></td>
<td style="text-align: left;"><p>Virtual Machines</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>1 B2ps v2 (2 vCPUs, 8 GB RAM) x 300
Hours (Pay as you go), Linux, (Pay as you go); 1 managed disk – E6;
Inter Region transfer type, 5 GB outbound data transfer from Germany
West Central to East Asia</p></td>
<td style="text-align: left;"><p>€ 25.71</p></td>
<td style="text-align: left;"><p>AAP Private Hub</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Compute</p></td>
<td style="text-align: left;"><p>Virtual Machines</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>1 B2ps v2 (2 vCPUs, 8 GB RAM) x 300
Hours (Pay as you go), Linux, (Pay as you go); 1 managed disk – E4;
Inter Region transfer type, 5 GB outbound data transfer from Germany
West Central to East Asia</p></td>
<td style="text-align: left;"><p>€ 23.49</p></td>
<td style="text-align: left;"><p>AAP EE</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Compute</p></td>
<td style="text-align: left;"><p>Virtual Machines</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>1 B2ps v2 (2 vCPUs, 8 GB RAM) x 300
Hours (Pay as you go), Linux, (Pay as you go); 1 managed disk – E4;
Inter Region transfer type, 5 GB outbound data transfer from Germany
West Central to East Asia</p></td>
<td style="text-align: left;"><p>€ 23.49</p></td>
<td style="text-align: left;"><p>RH Build of Keycloak Server</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Compute</p></td>
<td style="text-align: left;"><p>Virtual Machines</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>1 B2als v2 (2 vCPUs, 4 GB RAM) x 300
Hours (Pay as you go), Linux, (Pay as you go); 1 managed disk – E4;
Inter Region transfer type, 5 GB outbound data transfer from Germany
West Central to East Asia</p></td>
<td style="text-align: left;"><p>€ 14.18</p></td>
<td style="text-align: left;"><p>Tang Server</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Compute</p></td>
<td style="text-align: left;"><p>Virtual Machines</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>1 B4ps v2 (4 vCPUs, 16 GB RAM) x 300
Hours (Pay as you go), Linux, (Pay as you go); 1 managed disk – P6;
Inter Region transfer type, 5 GB outbound data transfer from Germany
West Central to East Asia</p></td>
<td style="text-align: left;"><p>€ 53.03</p></td>
<td style="text-align: left;"><p>Bastion / Jumphost</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Storage</p></td>
<td style="text-align: left;"><p>Storage Accounts</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>Managed Disks, Standard SSD, LRS
Redundancy, E4 Disk Type 3 Disks, 100 Storage transactions</p></td>
<td style="text-align: left;"><p>€ 6.83</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Storage</p></td>
<td style="text-align: left;"><p>Storage Accounts</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>Block Blob Storage, General Purpose V2,
Hierarchical Namespace, LRS Redundancy, Hot Access Tier, 1,000 GB
Capacity - Pay as you go, 100 x 10,000 Write operations, 100 x 10,000
Read operations, 10 x 10,000 Iterative Read operations, 10 x 100
Iterative Write operations, 1,000 GB Data Retrieval, 1,000 GB Data
Write, SFTP disabled, 1,000 GB Index, 1 x 10,000 Other
operations</p></td>
<td style="text-align: left;"><p>€ 51.66</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Networking</p></td>
<td style="text-align: left;"><p>Azure Virtual Network Manager</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>1 Managed suscriptions x 730
Hours</p></td>
<td style="text-align: left;"><p>€ 67.41</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Networking</p></td>
<td style="text-align: left;"><p>Virtual Network</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>Germany West Central (Virtual Network
1): 1 TB Outbound Data Transfer; Germany West Central (Virtual Network
2): 1 TB Outbound Data Transfer</p></td>
<td style="text-align: left;"><p>€ 37.83</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Networking</p></td>
<td style="text-align: left;"><p>IP Addresses</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>Basic (Classic), 0 Dynamic IP Addresses
X 730 Hours, 15 Static IP Addresses X 730 Hours</p></td>
<td style="text-align: left;"><p>€ 36.40</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Networking</p></td>
<td style="text-align: left;"><p>Azure DNS</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>Zone 1, DNS, Public; 1 hosted DNS zone,
1 DNS query</p></td>
<td style="text-align: left;"><p>€ 0.83</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Networking</p></td>
<td style="text-align: left;"><p>Azure Firewall</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>Standard tier, 0 Logical firewall units
x 730 Hours, 0 GB Data processed</p></td>
<td style="text-align: left;"><p>€ 0.00</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Networking</p></td>
<td style="text-align: left;"><p>Load Balancer</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>Standard Tier: 0 Rules, 0 GB Data
Processed</p></td>
<td style="text-align: left;"><p>€ 0.00</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Security</p></td>
<td style="text-align: left;"><p>Key Vault</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>Vault: 50 operations, 50 advanced
operations, 3 renewals, 5 protected keys, 0 advanced protected keys;
Managed HSM Pools: 0 Standard B1 HSM Pool(s) x 730 Hours</p></td>
<td style="text-align: left;"><p>€ 13.10</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Compute</p></td>
<td style="text-align: left;"><p>Azure Functions</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>Consumption tier, Pay as you go, 128 MB
memory, 100 milliseconds execution time, 0 executions/mo</p></td>
<td style="text-align: left;"><p>€ 0.00</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Management and governance</p></td>
<td style="text-align: left;"><p>Microsoft Cost Management</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>No charge for managed Azure spend. 0
Managed AWS spend per month</p></td>
<td style="text-align: left;"><p>€ 0.00</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Management and governance</p></td>
<td style="text-align: left;"><p>Azure Backup</p></td>
<td style="text-align: left;"><p>Germany West Central</p></td>
<td style="text-align: left;"><p>Azure VMs, Standard Backup policy, 1
Instance(s) x 0 GB, LRS Redundancy, Low Average Daily Churn, 0 GB
Average monthly backup data in Standard Tier, 0 GB Average monthly
backup data in Archive Tier</p></td>
<td style="text-align: left;"><p>€ 0.00</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Networking</p></td>
<td style="text-align: left;"><p>Azure DNS</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>Zone 1, DNS, Private; 0 hosted DNS
zones, 0 DNS queries</p></td>
<td style="text-align: left;"><p>€ 0.00</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Support</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>Free level</p></td>
<td style="text-align: left;"><p>Support</p></td>
<td style="text-align: left;"><p>€ 0.00</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>Licensing Program</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>Billing Account</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>Billing Profile</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"><p>Total</p></td>
<td style="text-align: left;"><p>€ 724.13</p></td>
<td style="text-align: left;"></td>
<td style="text-align: left;"></td>
</tr>
</tbody>
</table>
