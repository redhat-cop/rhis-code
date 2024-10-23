# Subscriptions

This document describes the pre-requisite configurations and
subscriptions for the project. These configurations must be in place
prior to automation and can be prepared manually.

## Azure

### Subscriptions

A subscription is an agreement with Microsoft to use one or more
Microsoft cloud platforms or services, for which charges accrue based on
either a per-user license fee or on cloud-based resource consumption.

It is planned to have two subscriptions on the Azure cloud provider. One
subscription must be granted with unlimited access to resources and the
second subscription will only grant a budgeted amount of cloud resources
to be used for the customer’s workloads.

-   `sub_management`: Unlimited subscription for the Infrastructure Management resources.
-   `sub_workload`: Limited subscription for the customer workload resources.

Azure PaaS services and virtual machine-based workloads hosted in Azure
IaaS can have tenancy in any Azure datacenter across the world. You
specify the Azure datacenter, known as the location, when you create the
Azure PaaS app or service or element of an IaaS workload.

### Users

A Microsoft Entra tenant is a specific instance of Microsoft Entra ID
containing accounts and groups.

Red Hat directory granted on Azure cloud provider to allow our Red Hat
usernames to be able to log in. It uses Red Hat organizations login page
as default, which allows to use single sign-on with Red Hat account. OTP
access also enabled for the Showroom project, which would ask as a token
on the next step of login. This token should be integrated with your
account on your mobile device using one of your favorite token
generators.

By default Red Hat Project Team consumes `Contributor` and `Owner` roles
on Azure Identity Management platform.

### Credentials

All the credentials are stored as encrypted strings in the
[repository](https://github.com/showroom-project/showroom-inventory).

-   `azure_management_subscription_id`: Azure Subscription id is
    required to access subscriptions

-   `azure_management_tenant_id`: Azure Tenant id is required to access
    Azure resources.

-   `techuser_ansible_client_id`: Technical user in Azure Entra for
    Ansible playbooks to run with.

## Red Hat Console and Image Builder

It is possible to create customized RHEL system images by using Insights
image builder, and upload those images to the Microsoft Azure cloud
target environment. Then, we can create a Virtual Machine (VM) from the
image we shared with the Microsoft Azure Cloud account.

Insights Image Builder Tool used for the initial deployment of the
systems to bootstrap. We need to access to the API of the Insights Image
Builder Tool API to generate and customize images.

To authorize Insights image builder to push images to the Microsoft
Azure cloud, you must:

-   Configure Insights image builder as an authorized application for
    your tenant GUID

-   Give it the role of Contributor to at least one resource group.

Technical details and steps can be found on the RHEL documentation for
[composing a customized RHEL system
image](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/8/html/creating_customized_images_by_using_insights_image_builder/creating-and-uploading-customized-rhel-system-image-to-azure-using-image-builder)

We also need to create a service account on the Hybrid Cloud Console to
allow a user to automate through the API using the credentials. The
steps are clearly described in the [service account creation
documentation](https://access.redhat.com/documentation/en-us/red_hat_customer_portal/1/html/creating_and_managing_service_accounts/con-ciam-svc-acct-intro-creating-service-acct).

## Users

We created a new organization called `Red Hat - Showroom` with account
number `11826835`. For the Red Hat project team, we defined users Red
Hat Login name in this new organization, adding a suffix of the new
organization identifier with a `-` sign, and also using mail address
definition with `+` sign, which normally enables mail notifications to
the existing Red Hat mail address.

### Example account information:

Red Hat Login: `<username>-showroom@redhat.com`

Email address: `<username>+showroom@redhat.com`

All members of the existing project team have
`Organization Administrator` role in the organization.

## Subscriptions

The following subscriptions are granted from the account team to the new
organization.

<table>
<colgroup>
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
<col style="width: 25%" />
</colgroup>
<thead>
<tr class="header">
<th style="text-align: left;">Name</th>
<th style="text-align: left;">SKU</th>
<th style="text-align: left;">Quantity</th>
<th style="text-align: left;">Service Level</th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td style="text-align: left;"><p>Red Hat Partner Subscription (500
Nodes)</p></td>
<td style="text-align: left;"><p>MW02049</p></td>
<td style="text-align: left;"><p>1</p></td>
<td style="text-align: left;"><p>Self-Support</p></td>
</tr>
<tr class="even">
<td style="text-align: left;"><p>Red Hat Satellite Infrastructure
Subscription</p></td>
<td style="text-align: left;"><p>MCT3718</p></td>
<td style="text-align: left;"><p>50</p></td>
<td style="text-align: left;"><p>Premium</p></td>
</tr>
</tbody>
</table>

Details for the Partner subscriptions can be found on the [Partner
Subscriptions](https://connect.redhat.com/en/partner-with-us/partner-benefits/partner-subscriptions)
page and also on
[datasheet](https://connect.redhat.com/sites/default/files/2023-05/RH-PartnerSubscription-Datasheet512.pdf).

## Credentials

All the credentials are stored as encrypted strings in the
[repository](https://github.com/showroom-project/showroom-inventory).

-   `techuser-rhib_client_id`: Service account client identifier

-   `techuser-rhib_client_secret`: Service account client secret
