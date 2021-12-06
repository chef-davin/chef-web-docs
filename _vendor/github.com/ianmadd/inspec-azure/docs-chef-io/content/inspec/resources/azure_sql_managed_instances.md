+++
title = "azure_sql_managed_instances Resource"
platform = "azure"
draft = false
gh_repo = "inspec-azure"

[menu.inspec]
title = "azure_sql_managed_instances"
identifier = "inspec/resources/azure/azure_sql_managed_instances Resource"
parent = "inspec/resources/azure"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_sql_managed_instances.md">https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_sql_managed_instances.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_sql_managed_instances.md">https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_sql_managed_instances.md</a></p>
</div>
</div>


Use the `azure_sql_managed_instances` InSpec audit resource to test the properties related to all Azure SQL managed instances within a project.

## Azure REST API Version, Endpoint, and HTTP Client Parameters

{{% inspec_azure_common_parameters %}}

## Installation

{{% inspec_azure_install %}}

## Syntax

An `azure_sql_managed_instances` resource block returns all Azure SQL managed instances within a project.

```ruby
describe azure_sql_managed_instances do
  #...
end
```

## Parameters

`resource_group`
: Azure resource group that the targeted resource resides in. _Optional_.

The parameter set optionally be provided for a valid query: `resource_group`.

## Properties

`ids`
: A list of resource IDs.

: **Field**: `id`

`names`
: A list of resource names.

: **Field**: `name`

`types`
: A list of the resource types.

: **Field**: `type`

`properties`
: A list of properties for all the SQL managed instances.

: **Field**: `properties`

`locations`
: A list of the locations.

: **Field**: `location`

`provisioningStates`
: A list of provisioning states of all the SQL managed instances.

: **Field**: `provisioningState`

`minimalTlsVersions`
: A list of minimalTlsVersion for all the SQL managed instances.

: **Field**: `minimalTlsVersion`

`sku_names`
: A list of names for the sku.

: **Field**: `sku_name`

`sku_tiers`
: A list of tiers for the sku.

: **Field**: `sku_tier`

<superscript>*</superscript> For information on how to use filter criteria on plural resources, refer to [FilterTable usage](https://github.com/inspec/inspec/blob/master/dev-docs/filtertable-usage.md).

## Examples

**Loop through SQL managed instances by their names.**

```ruby
azure_sql_managed_instances(resource_group: 'RESOURCE_GROUP').names.each do |name|
  describe azure_sql_managed_instance(resource_group: 'RESOURCE_GROUP', name: name) do
    it { should exist }
  end
end
```

**Test that there are SQL managed instances that are successfully provisioned.**

```ruby
describe azure_sql_managed_instances.where(provisioningState: 'Succeeded') do
  it { should exist }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

### exists

```ruby
# Should not exist if no SQL Managed Instances are present

describe azure_sql_managed_instances do
  it { should_not exist }
end
# Should exist if the filter returns at least one SQL Managed Instances

describe azure_sql_managed_instances do
  it { should exist }
end
```

## Azure Permissions

Your [Service Principal](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal) must be set up with a `reader` role on the subscription you wish to test.