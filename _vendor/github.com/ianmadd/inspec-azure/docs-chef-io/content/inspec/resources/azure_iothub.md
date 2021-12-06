+++
title = "azure_iothub Resource"
platform = "azure"
draft = false
gh_repo = "inspec-azure"

[menu.inspec]
title = "azure_iothub"
identifier = "inspec/resources/azure/azure_iothub Resource"
parent = "inspec/resources/azure"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_iothub.md">https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_iothub.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_iothub.md">https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_iothub.md</a></p>
</div>
</div>


Use the `azure_iothub` InSpec audit resource to test properties of an Azure IoT hub within a Resource Group.

## Azure REST API Version, Endpoint, and HTTP Client Parameters

{{% inspec_azure_common_parameters %}}

## Installation

{{% inspec_azure_install %}}

## Syntax

`resource_group` and `name` or the `resource_id` must be given as a parameter.
```ruby
describe azure_iothub(resource_group: 'my-rg', name: 'my-iot-hub') do
  it { should exist }
end
```
```ruby
describe azure_iothub(resource_id: '/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Devices/IotHubs/{resourceName}') do
  it { should exist }
end
```

## Parameters

`resource_group`
: Azure resource group that the targeted resource resides in. `MyResourceGroup`.

`name`
: The unique name of the IoT hub. `resourceName`.

`resource_name`
: Alias for the `name` parameter.

`resource_id`
: The unique resource ID. `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Devices/IotHubs/{resourceName}`.

Either one of the parameter sets can be provided for a valid query:
- `resource_id`
- `resource_group` and `name`
- `resource_group` and `resource_name`

## Properties

`sku`
: The SKU of the resource with [these](https://docs.microsoft.com/en-us/rest/api/iothub/iothubresource/get#iothubskuinfo) properties.

For properties applicable to all resources, such as `type`, `name`, `id`, `properties`, refer to [`azure_generic_resource`]({{< relref "azure_generic_resource.md#properties" >}}).

Also, refer to [Azure documentation](https://docs.microsoft.com/en-us/rest/api/iothub/iothubresource/get#iothubdescription) for other properties available. 
Any attribute in the response may be accessed with the key names separated by dots (`.`).

## Examples

**Test if File Upload Notifications are Enabled.**

```ruby
describe azure_iothub(resource_group: 'my-rg', name: 'my-iot-hub') do
  its('properties.enableFileUploadNotifications') { should cmp true }
end
```
```ruby
describe azure_iothub(resource_id: '/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.Devices/IotHubs/{resourceName}') do
  its('properties.enableFileUploadNotifications') { should cmp true }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://docs.chef.io/inspec/matchers/).

### exists

```ruby
# If we expect the resource to always exist

describe azure_iothub(resource_group: 'my-rg', name: 'my-iot-hub') do
  it { should exist }
end

# If we expect the resource to never exist

describe azure_iothub(resource_group: 'my-rg', name: 'my-iot-hub') do
  it { should_not exist }
end
```

## Azure Permissions

{{% azure_permissions_service_principal_contributor %}}