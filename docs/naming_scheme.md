# Naming Scheme

Use lowercase letters and numbers only. Because of some restrictions
(resource name length), all the abbreviations and codes should be as
short as possible to leave more room for using meaningful names. In
general we do not use any padding scheme in our naming conventions such
as three-digit padding scheme (###).

## Environment

Environment is the name that describes the deployment lifecycle of the
applications or services, such as Dev, QA, or Prod.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">Environment</th>
<th style="text-align: left;">Abbreviation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;"><p>Production (live)</p></td>
<td style="text-align: left;"><p>prd</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Development</p></td>
<td style="text-align: left;"><p>dev</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>QA / Testing</p></td>
<td style="text-align: left;"><p>qat</p></td>
</tr>
</tbody>
</table>

## Network Zone

Perimeter-based networks operate on the assumption that all systems
within a network can be trusted. But today’s employees access their
organization’s resources from anywhere on various devices and apps,
which makes perimeter security controls irrelevant. Access control
policies that focus only on who can access a resource aren’t enough. To
master the balance between security and productivity, security admins
also need to factor in how a resource is being accessed.

Best practice: Grant temporary permissions to perform privileged tasks,
which prevents malicious or unauthorized users from gaining access after
the permissions have expired. Access is granted only when users need it.

A perimeter network (also known as a DMZ) is a physical or logical
network segment that provides an extra layer of security between your
assets and the internet. Specialized network access control devices on
the edge of a perimeter network allow only desired traffic into your
virtual network.

A perimeter network is where you typically enable distributed denial of
service (DDoS) protection, intrusion detection/intrusion prevention
systems (IDS/IPS), firewall rules and policies, web filtering, network
anti-malware, and more. The network security devices sit between the
internet and your Azure virtual network and have an interface on both
networks.

-   Security Isolation: DMZ provides a segregated environment, isolating
    public-facing services from internal networks to contain and
    mitigate security threats effectively.
-   Internal Resource Protection: By placing public services in the DMZ,
    internal resources are shielded from direct internet exposure,
    reducing the attack surface.
-   Compliance and Regulations: Many compliance frameworks mandate the
    implementation of a DMZ to meet security and regulatory
    requirements.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">Network Segment</th>
<th style="text-align: left;">Abbreviation</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;"><p>Intranet</p></td>
<td style="text-align: left;"><p>intra</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>DMZ</p></td>
<td style="text-align: left;"><p>dmz</p></td>
</tr>
</tbody>
</table>

## Infrastructure

All resources are separated on a subscription level on Azure which would
enable us to set quota / limits for the resources.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<tbody>
<tr class="odd">
<td style="text-align: left;"><p>Infrastructure</p></td>
<td style="text-align: left;"><p>Abbreviation</p></td>
<td style="text-align: left;"><p>Description</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Management</p></td>
<td style="text-align: left;"><p>mgmt</p></td>
<td style="text-align: left;"><p>All IT management application and
systems</p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Workload</p></td>
<td style="text-align: left;"><p>work</p></td>
<td style="text-align: left;"><p>All customer application and
systems</p></td>
</tr>
</tbody>
</table>

## Hostname

Hostname from [Greek Gods](https://namingschemes.com/Greek_Gods) can be
chosen.

## Product Specific

### Azure

The choice of a name for any resource in Microsoft Azure is important
because:

-   It is difficult to change a name at a later time.
-   Names must meet the requirements of their specific resource type.

Likewise, consistent naming conventions make resources easier to locate.
They also assist in understanding the role of a resource in a solution.
Naming conventions should be applied as follows on Azure resource types.
We recommend that you keep the length of naming components short to
prevent exceeding resource name length limits. Please refer to [Naming
rules and restrictions for Azure
resources](https://learn.microsoft.com/en-us/azure/azure-resource-manager/management/resource-name-rules)
for up-to-date Azure resource name length limits.

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">Resource Type</th>
<th style="text-align: left;">Prefix</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;"><p>Subscriptions</p></td>
<td style="text-align: left;"><p><code>sub-</code></p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Resource Group</p></td>
<td style="text-align: left;"><p><code>rg-</code></p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Virtual Network</p></td>
<td style="text-align: left;"><p><code>vnet-</code></p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Virtual Network Gateway</p></td>
<td style="text-align: left;"><p><code>vnet-gw-</code></p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Virtual Network Link</p></td>
<td style="text-align: left;"><p><code>vnet-link-</code></p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Subnet</p></td>
<td style="text-align: left;"><p><code>subnet-</code></p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Network Security Group</p></td>
<td style="text-align: left;"><p><code>nsg-</code></p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Virtual Machines</p></td>
<td style="text-align: left;"><p><code>vm-</code></p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>VM storage account</p></td>
<td style="text-align: left;"><p><code>stvm-</code></p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Storage account</p></td>
<td style="text-align: left;"><p><code>st</code></p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>NIC</p></td>
<td style="text-align: left;"><p><code>nic-</code></p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Public IP Address</p></td>
<td style="text-align: left;"><p><code>pip-</code></p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Load Balancer</p></td>
<td style="text-align: left;"><p><code>lb-</code></p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Azure Functions</p></td>
<td style="text-align: left;"><p><code>func-</code></p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Workspace Name</p></td>
<td style="text-align: left;"><p><code>wrkspc-</code></p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Application Insight Name</p></td>
<td style="text-align: left;"><p><code>app-insight-</code></p></td>
</tr>
</tbody>
</table>

Following structure can be applied for naming the Azure resources when
using variables

    <azure resource prefix>-<infrastructure_type>-<network zone>-<environment>

Some resource type names can include `<project name>` rather than
`<network zone>` if the resource type is not generic to any network zone
or controls all other resources with Azure Functions like the
marketplace application named `Start/Stop VMs`

It would be always good to have a tag with a name `description` to the
resource type and `value` describing the resource type in detail.

#### Examples

    Resource group for all the resources to control on Production --> rg-mgmt-showroom-prd
    Intranet Infrastructure Management Resource group on Production --> rg-mgmt-intra-prd
    DMZ Workload Resource group on Development --> rg-work-dmz-dev
    Intranet Infrastructure Management Virtual Network on Production --> vnet-mgmt-intra-prd
    DMZ Workload Virtual Network on Development --> vnet-work-dmz-dev
    Subscription name for the Project in Management Group --> sub-mgmt-showroom-dev

### RH Satellite

<table>
<colgroup>
<col style="width: 50%" />
<col style="width: 50%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">Resource Type</th>
<th style="text-align: left;">Prefix</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;"><p>Activation Key</p></td>
<td style="text-align: left;"><p><code>ak_</code></p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Credential</p></td>
<td style="text-align: left;"><p><code>gpg_</code></p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Custom Product</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Custom Repository</p></td>
<td style="text-align: left;"><p><code>repo_</code></p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Content View</p></td>
<td style="text-align: left;"><p><code>cv_</code></p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Composite Content View</p></td>
<td style="text-align: left;"><p><code>ccv_</code></p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Host Group</p></td>
<td style="text-align: left;"><p><code>hg_</code></p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Life Cycles</p></td>
<td style="text-align: left;"></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Partition Table</p></td>
<td style="text-align: left;"><p><code>pt_</code></p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Sync Plan</p></td>
<td style="text-align: left;"><p><code>sync_</code></p></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Partition Table</p></td>
<td style="text-align: left;"><p><code>pt_</code></p></td>
</tr>
</tbody>
</table>

Following structure can be applied for naming the Satellite resources
when using variables

    <satellite resource prefix>_<related product name>

#### Examples

    RHEL 8 Activation Key --> ak_rhel8
    RHEL 8 Content View --> cv_rhel8
    AAP Composite Content View --> ccv_aap
    Support Tools Content View --> cv_support_tools
    AAP Host Group --> hg_aap
    VM Hostgroup --> hg_vm

## RHIdM

TODO:

## AAP

TODO:
