+++
title = "aws_cloudwatchlogs_destinations Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_cloudwatchlogs_destinations"
identifier = "inspec/resources/aws/aws_cloudwatchlogs_destinations Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudwatchlogs_destinations.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudwatchlogs_destinations.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudwatchlogs_destinations.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudwatchlogs_destinations.md</a></p>
</div>
</div>


Use the `aws_cloudwatchlogs_destinations` InSpec audit resource to test properties of multiple AWS Logs destinations.

The `AWS::Logs::Destination` resource type specifies a CloudWatch Logs destination. A destination encapsulates a physical resource (such as an Amazon Kinesis data stream) and enables you to subscribe that resource to a stream of log events.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS::Logs::Destination.](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-logs-destination.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the destination name exists.

```ruby
describe aws_cloudwatchlogs_destinations do
  it { should exist }
end
```

## Parameters

The resource does not require any parameters.

## Properties

`destination_names`
: The name of the destination.

: **Field**: `destination_name`

`target_arns`
: The Amazon Resource Name (ARN) of the physical target where the log events are delivered (for example, a Kinesis stream).

: **Field**: `target_arn`

`role_arns`
: The ARN of an IAM role that permits CloudWatch Logs to send data to the specified AWS resource.

: **Field**: `role_arn`

`access_policies`
: An IAM policy document governing the Amazon Web Services accounts, which can create subscription filters against this destination.

: **Field**: `access_policy`

`arns`
: The ARN of this destination.

: **Field**: `arn`

`creation_time`
: The creation time of the destination, expressed as the number of milliseconds after Jan 1, 1970 00:00:00 UTC.

: **Field**: `creation_time`

## Examples

**Ensure a destination name is available.**

```ruby
describe aws_cloudwatchlogs_destinations do
  its('destination_names') { should include 'DESTINATION_NAME' }
end
```

**Ensure a destination role ARN is available.**

```ruby
describe aws_cloudwatchlogs_destinations do
    its('role_arns') { should include 'ROLE_ARN' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `describe` method returns at least one result.

### exist

Use `should` to test that an entity exists.

```ruby
describe aws_cloudwatchlogs_destinations do
  it { should exist }
end
```

Use `should_not` to test that an entity does not exist.

```ruby
describe aws_cloudwatchlogs_destinations do
  it { should_not exist }
end
```

## AWS Permissions

{{% aws_permissions_principal action="CloudWatchLogs:Client:DescribeDestinationsResponse" %}}