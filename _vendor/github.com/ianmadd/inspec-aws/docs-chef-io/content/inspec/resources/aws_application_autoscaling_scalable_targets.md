+++
title = "aws_application_autoscaling_scalable_targets Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_application_autoscaling_scalable_targets"
identifier = "inspec/resources/aws/aws_application_autoscaling_scalable_targets Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_application_autoscaling_scalable_targets.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_application_autoscaling_scalable_targets.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_application_autoscaling_scalable_targets.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_application_autoscaling_scalable_targets.md</a></p>
</div>
</div>


Use the `aws_application_autoscaling_scalable_targets` InSpec audit resource to test properties of multiple resourcese that Application Auto Scaling can scale.

For additional information, including details on parameters and properties, see the [AWS ApplicationAutoScaling ScalableTarget documentation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-applicationautoscaling-scalabletarget.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

```ruby
describe aws_application_autoscaling_scalable_targets( service_namespace: 'SERVICE_NAMESPACE' ) do
  it { should exist }
end
```

## Parameters

`service_namespace` _(required)_

: The namespace of the AWS service that provides the resource.

## Properties

`service_namespaces`
: The namespace of the AWS service that provides the resource.

`resource_ids`
: The identifier of the resource associated with the scalable target.

`scalable_dimensions`
: The scalable dimension associated with the scalable target.

`min_capacities`
: The minimum value to scale to in response to a scale-in activity.

`max_capacities`
: The maximum value to scale to in response to a scale-out activity.

`role_arns`
: The ARN of an IAM role that allows Application Auto Scaling to modify the scalable target on your behalf.

`creation_times`
: The Unix timestamp for when the scalable target was created.

`suspended_states`
: The suspended state of the scalable target.

## Examples

**Ensure a service namespace is available.**

```ruby
describe aws_application_autoscaling_scalable_targets( service_namespace: 'SERVICE_NAMESPACE' ) do
  its('service_namespace') { should include 'ec2' }
end
```

**Verify the minimum scale capacity.**

```ruby
describe aws_application_autoscaling_scalable_targets( service_namespace: 'SERVICE_NAMESPACE' ) do
    its('min_capacity') { should include 1 }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `describe` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_application_autoscaling_scalable_targets( service_namespace: 'SERVICE_NAMESPACE' ) do
  it { should exist }
end
```

### be_available

Use `should` to check if the work_group name is available.

```ruby
describe aws_application_autoscaling_scalable_targets( service_namespace: 'SERVICE_NAMESPACE' ) do
  it { should be_available }
end
```

## AWS Permissions

{{% aws_permissions_principal action="ApplicationAutoScaling:Client:DescribeScalableTargetsResponse" %}}