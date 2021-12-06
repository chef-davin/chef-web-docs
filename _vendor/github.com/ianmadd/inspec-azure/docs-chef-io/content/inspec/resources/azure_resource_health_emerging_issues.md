+++
title = "azure_resource_health_emerging_issues Resource"
platform = "azure"
draft = false
gh_repo = "inspec-azure"

[menu.inspec]
title = "azure_resource_health_emerging_issues"
identifier = "inspec/resources/azure/azure_resource_health_emerging_issues Resource"
parent = "inspec/resources/azure"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_resource_health_emerging_issues.md">https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_resource_health_emerging_issues.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_resource_health_emerging_issues.md">https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_resource_health_emerging_issues.md</a></p>
</div>
</div>


Use the `azure_resource_health_emerging_issues` InSpec audit resource to test properties related to all Azure Resource Health Emerging Issues.

## Azure REST API Version, Endpoint, and HTTP Client Parameters

{{% inspec_azure_common_parameters %}}

## Installation

{{% inspec_azure_install %}}

## Syntax

An `azure_resource_health_emerging_issues` resource block returns all Azure Resource Health Emerging Issues.

```ruby
describe azure_resource_health_emerging_issues do
  #...
end
```

## Parameters

This resource does not require any parameters.

## Properties

`ids`
: A list of the unique resource IDs.

: **Field**: `id`

`names`
: A list of names for all the resources.

: **Field**: `name`

`types`
: A list of types for all the resources.

: **Field**: `type`

`properties`
: A list of Properties all the resources.

: **Field**: `properties`


<superscript>*</superscript> For information on how to use filter criteria on plural resources refer to [FilterTable usage](https://github.com/inspec/inspec/blob/master/dev-docs/filtertable-usage.md).

See [Azure's documentation](https://docs.microsoft.com/en-us/rest/api/resourcehealth/emerging-issues/get) for other available properties.

## Examples

**Test that there are emerging health issues that are of lower severity.**

```ruby
describe azure_resource_health_emerging_issues.where{ properties.select{|prop| prop.statusActiveEvents.select{ |event| event.severity == 'Warning' } } } do
  it { should exist }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

### exists

```ruby
# Should not exist if no service health emerging issues are present

describe azure_resource_health_emerging_issues do
  it { should_not exist }
end
# Should exist if the filter returns at least one service health emerging issues

describe azure_resource_health_emerging_issues do
  it { should exist }
end
```

## Azure Permissions

{{% azure_permissions_service_principal_contributor %}}