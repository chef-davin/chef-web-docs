+++
title = "aws_batch_job_queues Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_batch_job_queues"
identifier = "inspec/resources/aws/aws_batch_job_queues Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_batch_job_queues.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_batch_job_queues.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_batch_job_queues.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_batch_job_queues.md</a></p>
</div>
</div>


Use the `aws_batch_job_queues` InSpec audit resource to test the properties of multiple AWS Batch job queues.

For additional information, including details on parameters and properties, see the [AWS Batch job queues documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-batch-jobqueue.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that a job queue exists.

```ruby
describe aws_batch_job_queues do
  it { should exist }
end
```

## Parameters

The resource does not require any parameters.

## Properties

`job_queue_names`
: The name of the job queue.

`job_queue_arns`
: The ARN of the job queue.

`states`
: The state of the job queue.

`statuses`
: The status of the job queue.

`status_reasons`
: The status_reason of the job queue.

`priorities`
: The priority of the job queue.

`tags`
: The tags of the job queue.

## Examples

**Ensure a job queue name is available.**

```ruby
describe aws_batch_job_queues do
  its('job_queue_names') { should include 'JOB_QUEUE_NAME' }
end
```

**Ensure that the state is `ENABLED` or `DISABLED`.**

```ruby
describe aws_batch_job_queues do
    its('states') { should include 'ENABLED' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `describe` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_batch_job_queues do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_batch_job_queues do
  it { should_not exist }
end
```

### be_available

Use `should` to check if the job_queue name is available.

```ruby
describe aws_batch_job_queues do
  it { should be_available }
end
```

## AWS Permissions

{{% aws_permissions_principal action="Batch:Client:DescribeJobQueuesResponse" %}}