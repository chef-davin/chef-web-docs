+++
title = "azure_migrate_project_solutions Resource"
platform = "azure"
draft = false
gh_repo = "inspec-azure"

[menu.inspec]
title = "azure_migrate_project_solutions"
identifier = "inspec/resources/azure/azure_migrate_project_solutions Resource"
parent = "inspec/resources/azure"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_migrate_project_solutions.md">https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_migrate_project_solutions.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_migrate_project_solutions.md">https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_migrate_project_solutions.md</a></p>
</div>
</div>


Use the `azure_migrate_project_solutions` InSpec audit resource to test the properties related to all Azure Migrate project solutions within a project.

## Azure REST API Version, Endpoint, and HTTP Client Parameters

{{% inspec_azure_common_parameters %}}

## Installation

{{% inspec_azure_install %}}

## Syntax

An `azure_migrate_project_solutions` resource block returns all Azure Migrate project solutions within a project.

```ruby
describe azure_migrate_project_solutions(resource_group: 'RESOURCE_GROUP', project_name: 'PROJECT_NAME') do
  #...
end
```

## Parameters

`resource_group`
: Azure resource group that the targeted resource resides in.

`project_name`
: Azure Migrate Project.

The parameter set should be provided for a valid query:

- `resource_group` and `project_name`.

## Properties

`ids`
: Path reference to the project solutions.

: **Field**: `id`

`names`
: Unique names for all project solutions.

: **Field**: `name`

`types`
: Type of the objects.

: **Field**: `type`

`eTags`
: A list of eTags for all the Project Solutions.

: **Field**: `eTag`

`properties`
: A list of Properties for all the Project Solutions.

: **Field**: `properties`

`tools`
: The tool used in all the solutions.

: **Field**: `tool`

`purposes`
: The purpose of all the solutions.

: **Field**: `purpose`

`goals`
: The goals of all the solutions.

: **Field**: `goal`

`statuses`
: The current status of all the solutions.

: **Field**: `status`

`cleanupStates`
: The cleanup states of all the solutions.

: **Field**: `cleanupState`

`summaries`
: The summary of all the solutions.

: **Field**: `summary`

`details`
: The details of all the solutions.

: **Field**: `details`

`instanceTypes`
: The Instance types.

: **Field**: `instanceType`

`databasesAssessedCounts`
: The count of databases assessed.

: **Field**: `databasesAssessedCount`

`databaseInstancesAssessedCounts`
: The count of database instances assessed.

: **Field**: `databaseInstancesAssessedCount`

`migrationReadyCounts`
: The count of databases ready for migration.

: **Field**: `migrationReadyCount`

`groupCounts`
: The count of groups reported by all the solutions.

: **Field**: `groupCount`

`assessmentCounts`
: The count of assessments reported by all the solutions.

: **Field**: `assessmentCount`

`extendedDetails`
: The extended details reported by all the solutions.

: **Field**: `extendedDetails`

<superscript>*</superscript> For information on how to use filter criteria on plural resources refer to [FilterTable usage](https://github.com/inspec/inspec/blob/master/dev-docs/filtertable-usage.md). Also for further reference of the properties please refer [Azure Documentation](https://docs.microsoft.com/en-us/rest/api/migrate/projects/solutions/enumerate-solutions)

## Examples

**Loop through migrate project solutions by their names.**

```ruby
azure_migrate_project_solutions(resource_group: 'RESOURCE_GROUP', project_name: 'PROJECT_NAME').names.each do |name|
  describe azure_migrate_project_solution(resource_group: 'RESOURCE_GROUP', project_name: 'PROJECT_NAME', name: name) do
    it { should exist }
  end
end
```

**Test to ensure the migrate project solutions for assessment.**

```ruby
describe azure_migrate_project_solutions(resource_group: 'RESOURCE_GROUP', project_name: 'PROJECT_NAME').where(purpose: 'Assessment') do
  it { should exist }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

### exists

```ruby
# Should not exist if no Migrate Project Solutions are present in the project and in the resource group

describe azure_migrate_project_solutions(resource_group: 'RESOURCE_GROUP', project_name: 'PROJECT_NAME') do
  it { should_not exist }
end
# Should exist if the filter returns at least one Migrate Project Solutions in the project and in the resource group

describe azure_migrate_project_solutions(resource_group: 'RESOURCE_GROUP', project_name: 'PROJECT_NAME') do
  it { should exist }
end
```

## Azure Permissions

Your [Service Principal](https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal) must be set up with a `contributor` role on the subscription you wish to test.