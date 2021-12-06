+++
title = "azure_virtual_network_gateway_connection Resource"
platform = "azure"
draft = false
gh_repo = "inspec-azure"

[menu.inspec]
title = "azure_virtual_network_gateway_connection"
identifier = "inspec/resources/azure/azure_virtual_network_gateway_connection Resource"
parent = "inspec/resources/azure"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_virtual_network_gateway_connection.md">https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_virtual_network_gateway_connection.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_virtual_network_gateway_connection.md">https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_virtual_network_gateway_connection.md</a></p>
</div>
</div>


Use the `azure_virtual_network_gateway_connection` InSpec audit resource to test the properties related to an Azure Virtual Network Gateway connection.

## Azure REST API Version, Endpoint, and HTTP Client Parameters

{{% inspec_azure_common_parameters %}}

## Installation

{{% inspec_azure_install %}}

## Syntax

`name` and `resource_group`  are required parameters.

```ruby
describe azure_virtual_network_gateway_connection(resource_group: 'RESOURCE_GROUP', name: 'VIRTUAL_NETWORK_NAME') do
  it  { should exist }
end
```

## Parameters

`name`
: Name of the Azure Virtual Network Gateway Connection to test.

`resource_group`
: Azure resource group name where the targeted resource resides.

The parameter set should be provided for a valid query:
- `resource_group` and `name`

## Properties

`id`
: Resource ID.

`name`
: Resource name.

`type`
: Resource type.

`eTag`
: A unique read-only string that changes whenever the resource is updated.

`location`
: Resource location.

`properties.provisioningState`
: The provisioning state of the virtual network gateway resource.

`properties.connectionType`
: Gateway connection type.

`properties.useLocalAzureIpAddresses`
: Use private local Azure IP for the connection.

`properties.ipsecPolicies`
: The IPSec Policies to be considered by this connection.

For properties applicable to all resources, such as `type`, `name`, `id`, `properties`, refer to [`azure_generic_resource`]({{< relref "azure_generic_resource.md#properties" >}}).

Also, refer to [Azure documentation](https://docs.microsoft.com/en-us/rest/api/network-gateway/virtual-network-gateway-connections/get) for other properties available. Any attribute in the response is accessed with the key names separated by dots (`.`).

## Examples

**Test that the Virtual Network Gateway connection protocol is IKEv1.**

```ruby
describe azure_virtual_network_gateway_connection(resource_group: 'RESOURCE_GROUP', name: 'VIRTUAL_NETWORK_NAME') do
  its('connectionProtocol') { should eq 'IKEv1' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](/inspec/matchers/).

### exists

```ruby
# If a Virtual Network Gateway Connection is found it will exist

describe azure_virtual_network_gateway_connection(resource_group: 'RESOURCE_GROUP', name: 'VIRTUAL_NETWORK_NAME') do
  it { should exist }
end

# if Virtual Network Gateway Connection is not found it will not exist

describe azure_virtual_network_gateway_connection(resource_group: 'RESOURCE_GROUP', name: 'VIRTUAL_NETWORK_NAME') do
  it { should_not exist }
end
```

## Azure Permissions

Your [Service Principal](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal) must be set up with a minimum of `reader` role on the subscription you wish to test.