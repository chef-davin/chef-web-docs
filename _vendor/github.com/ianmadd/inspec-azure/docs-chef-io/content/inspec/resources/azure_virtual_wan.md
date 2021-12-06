+++
title = "azure_virtual_wan Resource"
platform = "azure"
draft = false
gh_repo = "inspec-azure"

[menu.inspec]
title = "azure_virtual_wan"
identifier = "inspec/resources/azure/azure_virtual_wan Resource"
parent = "inspec/resources/azure"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_virtual_wan.md">https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_virtual_wan.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_virtual_wan.md">https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_virtual_wan.md</a></p>
</div>
</div>


Use the `azure_virtual_wan` InSpec audit resource to test the properties related to a Azure Virtual WAN in a given resource group.

## Azure REST API Version, Endpoint, and HTTP Client Parameters

{{% inspec_azure_common_parameters %}}

## Installation

{{% inspec_azure_install %}}

## Syntax

`name` and `resource_group` are required parameters.

```ruby
describe azure_virtual_wan(resource_group: 'RESOURCE_GROUP', name: 'DEFAULT_WAN') do
  it { should exist }
  its('properties.provisioningState') { should eq 'Succeeded' }
end
```

```ruby
describe azure_virtual_wan(resource_group: 'RESOURCE_GROUP', name: 'DEFAULT_WAN') do
  it  { should exist }
end
```

## Parameters

`name`
: Name of the Azure Virtual WAN to test.

`resource_group`
: The resource group name of the VirtualWan.

## Properties

`id`
: Resource ID.

`name`
: Resource name.

`type`
: Resource type.

`etag`
: A unique read-only string that changes whenever the resource is updated.

`location`
: Resource location.

`properties.provisioningState`
: The provisioning state of the Virtual WAN resource.

`properties.disableVpnEncryption`
: VPN encryption to be disabled or not.

`properties.allowBranchToBranchTraffic`
: True if branch to branch traffic is allowed.

`properties.office365LocalBreakoutCategory`
: The office local breakout category.

`properties.type`
: The type of the Virtual WAN.

For properties applicable to all resources, such as `type`, `name`, `id`, `properties`, refer to [`azure_generic_resource`]({{< relref "azure_generic_resource.md#properties" >}}).

Also, refer to [Azure documentation](https://docs.microsoft.com/en-us/rest/api/virtualwan/virtual-wans/get) for other properties available. Any attribute in the response may be accessed with the key names separated by dots (`.`).

## Examples

**Test that a Virtual WAN's Encryption is not disabled.**

```ruby
describe azure_virtual_wan(resource_group: 'RESOURCE_GROUP', name: 'DEFAULT_WAN') do
  its('properties.disableVpnEncryption') { should_not be_falsey }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](/inspec/matchers/).

### exists

```ruby
# If a Virtual WAN is found, it will exist
describe azure_virtual_wan(resource_group: 'RESOURCE_GROUP', name: 'DEFAULT_WAN') do
  it { should exist }
end

# If no Virtual WAN's are found, it will not exist
describe azure_virtual_wan(resource_group: 'RESOURCE_GROUP', name: 'DEFAULT_WAN') do
  it { should_not exist }
end
```

## Azure Permissions

Your [Service Principal](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal) must be set up with a `contributor` role on the subscription you wish to test.