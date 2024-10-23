# Start stop VM's

In this project, we’re going to automate the code for building Red Hat Management Tools to manage and build a Red Hat based environment. Since
the environment isn’t going to be used for productive workloads, we’ve decided to use a built-in functionality from the Microsoft Azure
Marketplace called [start/stop VMs v2](https://learn.microsoft.com/en-us/azure/azure-functions/start-stop-vms/overview#overview).
This will help decrease cloud costs for non-development time slots in the project, such as evenings and weekends.

The `Start/Stop VMs v2` feature starts or stops Azure Virtual Machines instances across multiple subscriptions.

We’ve decided to take a different approach to the automation code development for this project. While this isn’t the main requirement, we’ve agreed to exclude this part and cover it with manual steps described in this document.

We have planned schedules for weekdays only that will start VMs automatically at 6:00 AM and shutdown at 7:00 PM (Europe/Berlin time zone).

# Deploy Start/Stop VMs v2

We followed mainly the official documentation for the [start/stop VMs v2](https://learn.microsoft.com/en-us/azure/azure-functions/start-stop-vms/overview#overview) function with great enthusiasm!

It is recommended to use separate resource group for deploying this application as it will create additional resources required for this function to work.

1. Deploy function from the marketplace.

![Azure Marketplace for Start / Stop Function](images/azure_start_stop1.png){ align=centre }

2. Provide resource group, function, storage account and application insights names.

![Configure Start/Stop Function](images/azure_start_stop2.png){ align=centre }

3. After Deployment configure schedule for the sequenced stop.

![Sequenced Schedule for Stop Function](images/azure_start_stop3.png){ align=centre }

4. Configure schedule for the sequenced start.

![Sequenced Schedule for Start Function](images/azure_start_stop4.png)

5. Correct subscription information in the `Logic app code view` for the logic applications named `ststv2_vms_Sequenced_stop` and `ststv2_vms_Sequenced_start`

![Update subscription information](images/azure_start_stop5.png){ align=centre }

6. Enable Azure Function for the logic applications named `ststv2_vms_Sequenced_stop` and `ststv2_vms_Sequenced_start`

# How to Configure VMs

Sequenced - Start and stop actions are based on a schedule targeting VMs
with pre-defined sequencing `tags`. Only two named tags are supported -
`sequencestart` and `sequencestop`. ststv2\_vms\_Sequenced\_start and
ststv2\_vms\_Sequenced\_stop configure the sequenced start and stop.

The proper way to use the sequence functionality is to create a tag
named `sequencestart` on each VM you wish to be started in a sequence.
The tag value needs to be an integer ranging from 1 to N for each VM in
the respective scope. The tag is optional and if not present, the VM
simply won’t participate in the sequencing. The same criteria applies to
stopping VMs with only the tag name being different and use
`sequencestop` in this case. You have to configure both the tags in each
VM to get start and stop action. If two or more VMs share the same tag
value, those VMs would be started or stopped at the same time.

For example, the following table shows that both start and stop actions
are processed in ascending order by the value of the tag.

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">VM Name</th>
<th style="text-align: left;">Tags</th>
<th style="text-align: left;">Action Order</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;"><p>VM 1</p></td>
<td style="text-align: left;"><p>sequence start: 1 / sequence stop:
2</p></td>
<td style="text-align: left;"><p>Start: VM1, VM2</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>VM 2</p></td>
<td style="text-align: left;"><p>sequence start: 2 / sequence stop:
1</p></td>
<td style="text-align: left;"><p>Stop: VM2, VM1</p></td>
</tr>
</tbody>
</table>

## VM Tags

Tags must be set on the VMs to include or exclude specific VMs from
start and stop actions. Add a tag named `ssv2excludevm` in the
configuration for the VM. To exclude this VM from the start or stop
action, set the value of this new tag to `true`. To include the VM in
the action, set the value to false or don’t use any exclusion tag.

# VMs sequence Order

<table>
<colgroup>
<col style="width: 33%" />
<col style="width: 33%" />
<col style="width: 33%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">VM Name</th>
<th style="text-align: left;">Start Sequence</th>
<th style="text-align: left;">Stop Sequence</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;"><p>RHIdM (Primary)</p></td>
<td style="text-align: center;"><p>1</p></td>
<td style="text-align: center;"><p>5</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>RHIdM (Replica)</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>NBDE (Primary)</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>NBDE (Replica)</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>RH Satellite</p></td>
<td style="text-align: center;"><p>2</p></td>
<td style="text-align: center;"><p>4</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>RH Keycloak</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>RH Bastion</p></td>
<td style="text-align: center;"><p>3</p></td>
<td style="text-align: center;"><p>3</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>AAP PGSQL</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>AAP Controller</p></td>
<td style="text-align: center;"><p>4</p></td>
<td style="text-align: center;"><p>2</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>AAP PAH</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>AAP EE</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>AAP HOP</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>AAP EE on DMZ</p></td>
<td></td>
<td></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Capsule on DMZ</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>Workload VMs</p></td>
<td style="text-align: center;"><p>5</p></td>
<td style="text-align: center;"><p>1</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Workload VMs on DMZ</p></td>
<td></td>
<td></td>
</tr>
<tr class="odd">
<td style="text-align: left;"><p>RootCA</p></td>
<td colspan="2" style="text-align: center;"><p>ssv2excludevm</p></td>
</tr>
</tbody>
</table>
