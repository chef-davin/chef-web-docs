+++
title = "azure_express_route_circuit Resource"
platform = "azure"
draft = false
gh_repo = "inspec-azure"

[menu.inspec]
title = "azure_express_route_circuit"
identifier = "inspec/resources/azure/azure_express_route_circuit Resource"
parent = "inspec/resources/azure"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_express_route_circuit.md">https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_express_route_circuit.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_express_route_circuit.md">https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_express_route_circuit.md</a></p>
</div>
</div>


Use the `azure_express_route_circuit` InSpec audit resource to test properties of an Azure ExpressRoute circuit resource.

## Azure REST API Version, Endpoint, and HTTP Client Parameters

{{% inspec_azure_common_parameters %}}

## Installation

{{% inspec_azure_install %}}

## Syntax

This resource requires the `resource_group` and ExpressRoute circuit `circuit_name` parameters, or the `resource_id` parameter for a valid query.

```ruby
describe azure_express_route_circuit(resource_group: 'RESOURCE_GROUP', circuit_name: 'EXPRESS_CIRCUIT_NAME') do
  it { should exist }
end
```

or

```ruby
describe azure_express_route_circuit(resource_id: 'RESOURCE_ID') do
  it { should exist }
end
```

## Parameters

`resource_group`
: The Azure resource group that the targeted resource resides in.

`circuit_name`
: The name of the ExpressRoute circuit.

`resource_id`
: The resource ID of the ExpressRoute circuit.

Provide the `resource_group` and `name` parameters, or the `resource_id` for a valid query.

## Properties

`resource_group`
: The name of the resource group that the ExpressRoute circuit resource resides in.

`name`
: The name of the ExpressRoute circuit.

`type`
: The ExpressRoute circuit type.

`provisioning_state`
: The provisioning state of ExpressRoute circuit resource.

`location`
: The location of the ExpressRoute circuit resource.

`service_provider_properties_bandwidth_in_mbps`
: The bandwidth in Mbps of the circuit when the circuit is provisioned on an ExpressRoutePort resource.

`service_provider_properties_peering_location`
: The ExpressRoute circuit resource service provider peering location.

`service_provider_properties_name`
: The name of the ExpressRoute circuit service provider name.

`service_provider_provisioning_state`
: The service provider provisioning state of the ExpressRoute circuit resource. Possible values are, `NotProvisioned`, `Provisioning`, `Provisioned`, and `Deprovisioning`.

`service_key`
: The ServiceKey.

`stag`
: The identifier of the circuit traffic. Outer tag for QinQ encapsulation.

`global_reach_enabled`
: Flag denoting global reach status.  `boolean`.

`allow_global_reach`
: Flag to enable Global Reach on the ExpressRoute circuit. `boolean`.

`gateway_manager_etag`
: The GatewayManager Etag.

`allow_classic_operations`
: Whether "Allow Classic Operations" is set to `true` or `false`.

`circuit_provisioning_state`
: The CircuitProvisioningState state of the resource.

`sku_name`
: The name of the SKU.

`sku_tier`
: The tier of the SKU. Possible values are `Basic`, `Local`, `Standard`, or `Premium`.

`sku_family`
: The family of the SKU. Possible values are: `UnlimitedData` and `MeteredData`.

Also, refer to [Azure documentation](https://docs.microsoft.com/en-us/rest/api/expressroute/express-route-circuits/get) for other properties available.
Any attribute in the response may be accessed with the key names separated by dots (`.`).

## Examples

**Test the an ExpressRoute circuit resource has the correct type.**

```ruby
describe azure_express_route_circuit(resource_group: 'RESOURCE_GROUP', circuit_name: 'EXPRESS_CIRCUIT_NAME') do
  its('type') { should eq 'Microsoft.Network/expressRouteCircuits' }
end
```

**Test the an ExpressRoute circuit resource is in successful state.**

```ruby
describe azure_express_route_circuit(resource_group: 'RESOURCE_GROUP', circuit_name: 'EXPRESS_CIRCUIT_NAME') do
  its('provisioning_state') { should eq 'Succeeded' }
end
```

**Test the location of an ExpressRoute circuit resource.**

```ruby
describe azure_express_route_circuit(resource_group: 'RESOURCE_GROUP', circuit_name: 'EXPRESS_CIRCUIT_NAME') do
  its('location') { should eq 'RESOURCE_LOCATION' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](/inspec/matchers/).

### exists

```ruby
# If a express circuit resource is found it will exist

describe azure_express_route_circuit(resource_group: 'MyResourceGroup', circuit_name: 'mycircuit_name') do
  it { should exist }
end

# express circuit resources that aren't found will not exist
describe azure_express_route_circuit(resource_group: 'MyResourceGroup', circuit_name: 'DoesNotExist') do
  it { should_not exist }
end
```

## Azure Permissions

{{% azure_permissions_service_principal_contributor %}}