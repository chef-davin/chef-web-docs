+++
title = "azure_postgresql_database Resource"
platform = "azure"
draft = false
gh_repo = "inspec-azure"

[menu.inspec]
title = "azure_postgresql_database"
identifier = "inspec/resources/azure/azure_postgresql_database Resource"
parent = "inspec/resources/azure"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_postgresql_database.md">https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_postgresql_database.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_postgresql_database.md">https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_postgresql_database.md</a></p>
</div>
</div>


Use the `azure_postgresql_database` InSpec audit resource to test properties and configuration of an Azure PostgreSQL Database on a PostgreSQL Server.

## Azure REST API Version, Endpoint, and HTTP Client Parameters

{{% inspec_azure_common_parameters %}}

## Installation

{{% inspec_azure_install %}}

## Syntax

`resource_group`, `server_name` and `name` or the `resource_id` must be given as a parameter.
```ruby
describe azure_postgresql_database(resource_group: 'inspec-rg', server_name: 'customer_server', name: 'order-db') do
  it { should exist }
end
```
```ruby
describe azure_postgresql_database(resource_id: '/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DBforPostgreSQL/servers/{serverName}/databases/{databaseName}') do
  it { should exist }
end
```

## Parameters

`resource_group`
: Azure resource group that the targeted resource resides in. `MyResourceGroup`.

`server_name`
: The name of the server on which the database resides. `serverName`.

`name`
: The unique name of the database. `databaseName`.

`database_name`
: Alias for the `name` parameter.

`resource_id`
: The unique resource ID. `/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DBforPostgreSQL/servers/{serverName}/databases/{databaseName}`.

Either one of the parameter sets can be provided for a valid query:
- `resource_id`
- `resource_group`, `server_name`, and `name`
- `resource_group`, `server_name`, and `database_name`

## Properties

`properties.charset`
: The charset of the database.

For properties applicable to all resources, such as `type`, `tags`, `id`, `properties`, refer to [`azure_generic_resource`]({{< relref "azure_generic_resource.md#properties" >}}).

Also, refer to [Azure documentation](https://docs.microsoft.com/en-us/rest/api/postgresql/databases/get#database) for other properties available. 
Any attribute in the response may be accessed with the key names separated by dots (`.`).

## Examples

**Test the Name of a Resource.**

```ruby
describe azure_postgresql_database(resource_group: 'inspec-rg', server_name: 'customer_server', name: 'order-db') do
  its('name')   { should be 'order-db' }
end
```
```ruby
describe azure_postgresql_database(resource_id: '/subscriptions/{subscriptionId}/resourceGroups/{resourceGroupName}/providers/Microsoft.DBforPostgreSQL/servers/{serverName}/databases/order-db') do
  its('name')   { should be 'order-db' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://docs.chef.io/inspec/matchers/).

### exists

```ruby
# If we expect the resource to always exist

describe azure_postgresql_database(resource_group: 'inspec-rg', server_name: 'customer_server', name: 'order-db') do
  it { should exist }
end

# If we expect the resource to never exist

describe azure_postgresql_database(resource_group: 'inspec-rg', server_name: 'customer_server', name: 'order-db') do
  it { should_not exist }
end
```

## Azure Permissions

{{% azure_permissions_service_principal_contributor %}}