+++
title = "aws_dms_replication_instances Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_dms_replication_instances"
identifier = "inspec/resources/aws/aws_dms_replication_instances Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_dms_replication_instances.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_dms_replication_instances.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_dms_replication_instances.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_dms_replication_instances.md</a></p>
</div>
</div>


Use the `aws_dms_replication_instances` InSpec audit resource to test properties of multiple AWS DMS replication instances.

The AWS::DMS::ReplicationInstance resource creates an AWS DMS replication instance.

For additional information, including details on parameters and properties, see the [AWS documentation on DMS Replication Instance](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-dms-replicationinstance.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

### Ensure that a replication instance exists.

```ruby
describe aws_dms_replication_instances do
  it { should exist }
end
```

## Parameters

The resource does not require any parameters.

## Properties

`engine_versions`
: The engine versions of the replication instance.

`replication_instance_classes`
: The compute and memory capacity of the replication instance as defined for the specified replication instance class.

`storage_types`
: The storage types of the replication instance.

`min_allocated_storages`
: The min allocated storages of the replication instance.

`max_allocated_storages`
: The max allocated storages of the replication instance.

`default_allocated_storages`
: The default allocated storages of the replication instance in gigabytes.

`included_allocated_storages`
: The included allocated storages of the replication instance in gigabytes.

`availability_zones`
: The availability zones of the replication instance.

`release_statuses`
: The release statuses of the replication instance.

## Examples

**Ensure an engine version is available.**

```ruby
describe aws_dms_replication_instances do
  its('engine_versions') { should include '3.4.4' }
end
```

**Ensure that the classes are available.**

```ruby
describe aws_dms_replication_instances do
    its('replication_instance_classes') { should include 'dms.c4.2xlarge' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `describe` method returns at least one result.

### exist

### Use `should` to test that the entity exists.

```ruby
describe aws_dms_replication_instances do
  it { should exist }
end
```

### Use `should_not` to test the entity does not exist.

```ruby
describe aws_dms_replication_instances do
  it { should_not exist }
end
```

### be_available

Use `should` to check if the work group name is available.

```ruby
describe aws_dms_replication_instances do
  it { should be_available }
end
```

## AWS Permissions

{{% aws_permissions_principal action="DatabaseMigrationService:Client:DescribeOrderableReplicationInstancesResponse" %}}