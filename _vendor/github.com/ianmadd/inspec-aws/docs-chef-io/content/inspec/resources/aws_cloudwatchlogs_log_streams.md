+++
title = "aws_cloudwatchlogs_log_streams Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_cloudwatchlogs_log_streams"
identifier = "inspec/resources/aws/aws_cloudwatchlogs_log_streams Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudwatchlogs_log_streams.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudwatchlogs_log_streams.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudwatchlogs_log_streams.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudwatchlogs_log_streams.md</a></p>
</div>
</div>


Use the `aws_cloudwatchlogs_log_streams` InSpec audit resource to test properties of the plural resource of AWS Logs log stream.

The AWS::Logs::LogStream resource specifies an Amazon CloudWatch Logs log stream in a specific log group. A log stream represents the sequence of events coming from an application instance or resource that you are monitoring.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS Logs LogStream.](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-logs-logstream.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the log stream exists.

```ruby
describe aws_cloudwatchlogs_log_streams(log_group_name: "LOG_GROUP_NAME") do
  it { should exist }
end
```

## Parameters

`log_group_name` _(required)_

: The name of the log group.

## Properties

`log_stream_names`
: The name of the log stream.

: **Field**: `log_stream_name`

`creation_times`
: The creation time of the stream, expressed as the number of milliseconds after Jan 1, 1970 00:00:00 UTC.

: **Field**: `creation_time`

`first_event_timestamps`
: The time of the first event, expressed as the number of milliseconds after Jan 1, 1970 00:00:00 UTC.

: **Field**: `first_event_timestamp`

`last_event_timestamps`
: The time of the most recent log event in the log stream in CloudWatch Logs.

: **Field**: `last_event_timestamp`

`last_ingestion_times`
: The ingestion time, expressed as the number of milliseconds after Jan 1, 1970 00:00:00 UTC.

: **Field**: `last_ingestion_time`

`upload_sequence_tokens`
: The sequence token.

: **Field**: `upload_sequence_token`

`arns`
: The Amazon Resource Name (ARN) of the log stream.

: **Field**: `arn`

`stored_bytes`
: The number of bytes stored.

: **Field**: `stored_bytes`

## Examples

**Ensure a log stream name is available.**

```ruby
describe aws_cloudwatchlogs_log_streams(log_group_name: "LOG_GROUP_NAME") do
  its('log_stream_names') { should include 'LOG_STREAM_NAME' }
end
```

**Ensure a log stream arn is available.**

```ruby
describe aws_cloudwatchlogs_log_streams(log_group_name: "LOG_GROUP_NAME") do
    its('arns') { should include 'LOG_STREAM_ARN' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `describe` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_cloudwatchlogs_log_streams(log_group_name: "LOG_GROUP_NAME") do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_cloudwatchlogs_log_streams(log_group_name: "LOG_GROUP_NAME") do
  it { should_not exist }
end
```

## AWS Permissions

{{% aws_permissions_principal action="CloudWatchLogs:Client:DescribeLogStreamsResponse" %}}