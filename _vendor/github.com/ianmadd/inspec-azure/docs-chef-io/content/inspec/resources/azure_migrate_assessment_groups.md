+++
title = "azure_migrate_assessment_groups Resource"
platform = "azure"
draft = false
gh_repo = "inspec-azure"

[menu.inspec]
title = "azure_migrate_assessment_groups"
identifier = "inspec/resources/azure/azure_migrate_assessment_groups Resource"
parent = "inspec/resources/azure"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_migrate_assessment_groups.md">https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_migrate_assessment_groups.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_migrate_assessment_groups.md">https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_migrate_assessment_groups.md</a></p>
</div>
</div>


Use the `azure_migrate_assessment_groups` InSpec audit resource to test properties related to all Azure Migrate assessment groups within a project.

## Azure REST API Version, Endpoint, and HTTP Client Parameters

{{% inspec_azure_common_parameters %}}

## Installation

{{% inspec_azure_install %}}

## Syntax

An `azure_migrate_assessment_groups` resource block returns all Azure Migrate assessment groups within a project.

```ruby
describe azure_migrate_assessment_groups(resource_group: 'RESOURCE_GROUP', project_name: 'PROJECT_NAME') do
  #...
end
```

## Parameters

`resource_group`
: Azure resource group that the targeted resource resides in.

`project_name`
: Azure Migrate assessment project.

The parameter set should be provided for a valid query:
- `resource_group` and `project_name`.

## Properties

`ids`
: Path reference to all the groups.

: **Field**: `id`

`names`
: Unique names for all groups.

: **Field**: `name`

`types`
: Type of the objects.

: **Field**: `type`

`eTags`
: A list of eTags for all the groups.

: **Field**: `eTag`

`properties`
: A list of properties for all the groups.

: **Field**: `properties`

`areAssessmentsRunnings`
: A list of boolean describing the assessment run state.

: **Field**: `areAssessmentsRunning`

`assessments`
: List of references to assessments created on this group.

: **Field**: `assessments`

`createdTimestamps`
: List of creation times of the groups.

: **Field**: `createdTimestamp`

`groupStatuses`
: List of creation status of the groups.

: **Field**: `groupStatus`

`groupTypes`
: List of group types.

: **Field**: `groupType`

`machineCounts`
: List of machine counts.

: **Field**: `machineCount`

`updatedTimestamps`
: List of updated timestamps of the groups.

: **Field**: `updatedTimestamp`

<superscript>*</superscript> For information on how to use filter criteria on plural resources refer to [FilterTable usage](https://github.com/inspec/inspec/blob/master/dev-docs/filtertable-usage.md). Also, refer to [Azure documentation](https://docs.microsoft.com/en-us/rest/api/migrate/assessment/groups/list-by-project) for the complete list of properties available.

## Examples

**Loop through migrate assessment groups by their names.**

```ruby
azure_migrate_assessment_groups(resource_group: 'RESOURCE_GROUP', project_name: 'PROJECT_NAME').names.each do |name|
  describe azure_migrate_assessment_group(resource_group: `RESOURCE_GROUP`, project_name: `PROJECT_NAME`, name: `NAME`) do
    it { should exist }
  end
end
```

**Test that the assessments are running for migrate assessment groups.**

```ruby
describe azure_migrate_assessment_groups(resource_group: 'RESOURCE_GROUP', project_name: 'PROJECT_NAME').where(areAssessmentsRunning: true) do
  it { should exist }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

### exists

```ruby
# Should not exist if no Migrate Assessment Groups are present in the project

describe azure_migrate_assessment_groups(resource_group: 'RESOURCE_GROUP', project_name: 'PROJECT_NAME') do
  it { should_not exist }
end
# Should exist if the filter returns at least one Migrate Assessment Groups in the project

describe azure_migrate_assessment_groups(resource_group: 'RESOURCE_GROUP', project_name: 'PROJECT_NAME') do
  it { should exist }
end
```

## Azure Permissions

Your [Service Principal](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal) must be set up with a `contributor` role on the subscription you wish to test.