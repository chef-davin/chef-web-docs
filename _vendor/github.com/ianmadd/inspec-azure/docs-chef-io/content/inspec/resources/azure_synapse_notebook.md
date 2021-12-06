+++
title = "azure_synapse_notebook Resource"
platform = "azure"
draft = false
gh_repo = "inspec-azure"

[menu.inspec]
title = "azure_synapse_notebook"
identifier = "inspec/resources/azure/azure_synapse_notebook Resource"
parent = "inspec/resources/azure"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_synapse_notebook.md">https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_synapse_notebook.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_synapse_notebook.md">https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_synapse_notebook.md</a></p>
</div>
</div>


Use the `azure_synapse_notebook` InSpec audit resource to test properties related to a Azure Synapse notebook in a Synapse workspace.

## Azure REST API Version, Endpoint, and HTTP Client Parameters

{{% inspec_azure_common_parameters %}}

## Installation

{{% inspec_azure_install %}}

## Syntax

This resource requires the `endpoint` and `name` parameters for a valid query.

```ruby
describe azure_synapse_notebook(endpoint: 'WORKSPACE_DEVELOPMENT_ENDPOINT', name: 'NOTEBOOK_NAME') do
  it { should exist }
end
```

```ruby
describe azure_synapse_notebook(endpoint: 'WORKSPACE_DEVELOPMENT_ENDPOINT', name: 'NOTEBOOK_NAME') do
  it                                      { should exist }
  its('name')                             { should eq 'NOTEBOOK_NAME' }
  its('type')                             { should eq 'Microsoft.Synapse/workspaces/notebooks' }
  its('properties.sessionProperties.executorCores')          { should eq CORE_NUMBER }
end
```

## Parameters

`endpoint`
: The Azure Synapse workspace development endpoint.

`name`
: Name of the Azure Synapse Notebook to test.

This resource requires the `endpoint` and `name` parameters for a valid query.

## Properties

`id`
: Fully qualified resource ID for the resource.

`name`
: The name of the resource.

`type`
: The type of the resource.

`etag`
: The resource Etag.

`properties`
: The properties of the notebook.


For properties applicable to all resources, such as `type`, `name`, `id`, `properties`, refer to [`azure_generic_resource`]({{< relref "azure_generic_resource.md#properties" >}}).

Also, refer to [Azure documentation](https://docs.microsoft.com/en-us/rest/api/synapse/data-plane/notebook/get-notebook) for other available properties.

Access any property in the response by separating the key names with a period (`.`).

## Examples

**Test that there are four cores for each executor.**

```ruby
describe azure_synapse_notebook(endpoint: 'WORKSPACE_DEVELOPMENT_ENDPOINT', name: 'NOTEBOOK_NAME') do
  its('properties.sessionProperties.executorCores') { should eq 4 }
end
```

**Test that the notebook uses the Python kernel.**

```ruby
describe azure_synapse_notebook(endpoint: 'WORKSPACE_DEVELOPMENT_ENDPOINT', name: 'NOTEBOOK_NAME') do
  its('properties.metadata.language_info.name') { should 'Python' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](/inspec/matchers/).

### exists

If a Synapse Notebook is found it will exist

```ruby
describe azure_synapse_notebook(endpoint: 'WORKSPACE_DEVELOPMENT_ENDPOINT', name: 'NOTEBOOK_NAME') do
  it { should exist }
end
```

Synapse Notebooks that aren't found will not exist

```ruby
describe azure_synapse_notebook(endpoint: 'WORKSPACE_DEVELOPMENT_ENDPOINT', name: 'NOTEBOOK_NAME') do
  it { should_not exist }
end
```

## Azure Permissions

{{% azure_permissions_service_principal_contributor %}}