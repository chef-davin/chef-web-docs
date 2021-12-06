+++
title = "aws_cloudwatch_metric_stream Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_cloudwatch_metric_stream"
identifier = "inspec/resources/aws/aws_cloudwatch_metric_stream Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudwatch_metric_stream.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudwatch_metric_stream.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudwatch_metric_stream.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudwatch_metric_stream.md</a></p>
</div>
</div>


Use the `aws_cloudwatch_metric_stream` InSpec audit resource to test properties of a single AWS CloudWatch metric stream.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS CloudWatch metric stream.](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-cloudwatch-metricstream.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the metric stream exists.

```ruby
describe aws_cloudwatch_metric_stream(metric_stream_name: 'METRIC_STREAM_NAME') do
  it { should exist }
end
```

## Parameters

The resource does not require any parameters.

## Properties

`arn`
: The ARN of the metric stream.

`creation_date`
: The date that the metric stream was originally created.

`last_update_date`
: The date that the configuration of this metric stream was most recently updated.

`names`
: The name of the metric stream.

`firehose_arn`
: The ARN of the Kinesis Firehose delivery stream that is used for this metric stream.

`state`
: The current state of this stream. Valid values are running and stopped.

`output_format`
: The output format of this metric stream. Valid values are `json` and `opentelemetry0.7`.

## Examples

**Ensure an ARN is available.**

```ruby
describe aws_cloudwatch_metric_stream (metric_stream_name: 'METRIC_STREAM_NAME' ) do
  its('arn') { should eq 'ARN' }
end
```

**Ensure a firehose_ARN is available.**

```ruby
describe aws_cloudwatch_metric_stream (metric_stream_name: 'METRIC_STREAM_NAME' ) do
    its('firehose_arn') { should eq 'FIREHOSE_ARN' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `get` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_cloudwatch_metric_stream (metric_stream_name: 'METRIC_STREAM_NAME' ) do
  it { should exist }
end
```

Use `should_not` to test that the entity does not exist.

```ruby
describe aws_cloudwatch_metric_stream (metric_stream_name: 'METRIC_STREAM_NAME' ) do
  it { should_not exist }
end
```

## AWS Permissions

{{% aws_permissions_principal action="CloudFront:Client:GetMetricStreamsOutput" %}}