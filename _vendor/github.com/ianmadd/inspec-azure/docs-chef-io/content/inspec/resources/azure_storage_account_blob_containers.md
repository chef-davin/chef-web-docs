+++
title = "azure_storage_account_blob_containers Resource"
platform = "azure"
draft = false
gh_repo = "inspec-azure"

[menu.inspec]
title = "azure_storage_account_blob_containers"
identifier = "inspec/resources/azure/azure_storage_account_blob_containers Resource"
parent = "inspec/resources/azure"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_storage_account_blob_containers.md">https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_storage_account_blob_containers.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_storage_account_blob_containers.md">https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_storage_account_blob_containers.md</a></p>
</div>
</div>


Use the `azure_storage_account_blob_containers` InSpec audit resource to test properties and configuration of Blob Containers within an Azure Storage Account.

## Azure REST API Version, Endpoint, and HTTP Client Parameters

{{% inspec_azure_common_parameters %}}

## Installation

{{% inspec_azure_install %}}

## Syntax

The `resource_group`, and `storage_account_name` must be given as a parameter.
```ruby
describe azurerm_storage_account_blob_containers(resource_group: 'rg', storage_account_name: 'production') do
  its('names') { should include 'my-container'}
end
```

## Parameters

`resource_group`
: Azure resource group that the targeted resource resides in. `MyResourceGroup`.

`storage_account_name`
: The name of the storage account within the specified resource group. `accountName`.

## Properties

`ids`
: A list of the unique resource ids.

: **Field**: `id`

`locations`
: A list of locations for all the resources being interrogated.

: **Field**: `location`

`names`
: A list of names of all the resources being interrogated.

: **Field**: `name`

`tags`
: A list of `tag:value` pairs defined on the resources being interrogated.

: **Field**: `tags`

`etags`
: A list of etags defined on the resources.

: **Field**: `etag`

<superscript>*</superscript> For information on how to use filter criteria on plural resources refer to [FilterTable usage](https://github.com/inspec/inspec/blob/master/dev-docs/filtertable-usage.md).

## Examples

**Check If a Specific Container Exists.**

```ruby
describe azurerm_storage_account_blob_containers(resource_group: 'rg', storage_account_name: 'production') do
  its('names') { should include('my-container') }
end
```

**exists.**

The control will pass if the filter returns at least one result. Use `should_not` if you expect zero matches.
```ruby
**If we expect at least one resource to exists on a specified account.**

describe azurerm_storage_account_blob_containers(resource_group: 'rg', storage_account_name: 'production') do
  it { should exist }
end

**If we expect not to exist any containers on a specified account.**

describe azurerm_storage_account_blob_containers(resource_group: 'rg', storage_account_name: 'production') do
  it { should_not exist }
end
```

## Azure Permissions

{{% azure_permissions_service_principal_contributor %}}