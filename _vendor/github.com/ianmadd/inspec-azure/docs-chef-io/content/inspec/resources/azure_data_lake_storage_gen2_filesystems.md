+++
title = "azure_data_lake_storage_gen2_filesystems Resource"
platform = "azure"
draft = false
gh_repo = "inspec-azure"

[menu.inspec]
title = "azure_data_lake_storage_gen2_filesystems"
identifier = "inspec/resources/azure/azure_data_lake_storage_gen2_filesystems Resource"
parent = "inspec/resources/azure"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_data_lake_storage_gen2_filesystems.md">https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_data_lake_storage_gen2_filesystems.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_data_lake_storage_gen2_filesystems.md">https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_data_lake_storage_gen2_filesystems.md</a></p>
</div>
</div>


Use the `azure_data_lake_storage_gen2_filesystems` InSpec audit resource to test the properties related to all Azure Data Lake Storage Gen2 Filesystems within a project.

## Azure REST API Version, Endpoint, and HTTP Client Parameters

{{% inspec_azure_common_parameters %}}

## Installation

{{% inspec_azure_install %}}

## Syntax

An `azure_data_lake_storage_gen2_filesystems` resource block returns all Azure Data Lake Storage Gen2 filesystems within a project.

```ruby
describe azure_data_lake_storage_gen2_filesystems(account_name: 'ACCOUNT_NAME') do
  #...
end
```

## Parameters

`account_name` _(required)_

: The Azure Storage account name.

`dns_suffix` _(optional)_

: The DNS suffix for the Azure Data Lake Storage endpoint.

## Properties

`names`
: Unique names for all Azure Storage account Filesystems.

: **Field**: `name`

`lastModifieds`
: Last modified timestamps of Azure Storage account Filesystem.

: **Field**: `lastModified`

`eTags`
: A list of eTags for all the Azure Storage account Filesystems.

: **Field**: `eTag`

`DefaultEncryptionScopes`
: A list of all Encryption scopes of the ADLS Filesystems.

: **Field**: `DefaultEncryptionScope`

`DenyEncryptionScopeOverrides`
: A list of all Deny Encryption Scope Overrides.

: **Field**: `DenyEncryptionScopeOverrides`

<superscript>*</superscript> For information on how to use filter criteria on plural resources refer to [FilterTable usage](https://github.com/inspec/inspec/blob/master/dev-docs/filtertable-usage.md).
Also, refer to [Azure documentation](https://docs.microsoft.com/en-us/rest/api/storageservices/datalakestoragegen2/filesystem/list) for other properties available.

## Examples

**Loop Through Data Lake Storage Gen2 Filesystems by Their Names and Verify That Each Exists.**

```ruby
azure_data_lake_storage_gen2_filesystems(account_name: 'ACCOUNT_NAME').names.each do |name|
  describe azure_data_lake_storage_gen2_filesystem(account_name: 'ACCOUNT_NAME', name: name) do
    it { should exist }
  end
end
```

**Test To Ensure Data Lake Storage Gen2 Filesystems With ‘$account-encryption-key’ Encryption Scope.**

```ruby
describe azure_data_lake_storage_gen2_filesystems(account_name: 'ACCOUNT_NAME').where(DefaultEncryptionScope: '$account-encryption-key') do
  it { should exist }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

### exists

```ruby
# Should not exist if no Data Lake Storage Gen2 filesystems are present in the project and in the resource group

describe azure_data_lake_storage_gen2_filesystems(account_name: 'ACCOUNT_NAME') do
  it { should_not exist }
end

# Should exist if the filter returns at least one Data Lake Storage Gen2 filesystem in the project and in the resource group

describe azure_data_lake_storage_gen2_filesystems(account_name: 'ACCOUNT_NAME') do
  it { should exist }
end
```

## Azure Permissions

Your [Service Principal](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal) must be set up with a `contributor` role on the subscription you wish to test.