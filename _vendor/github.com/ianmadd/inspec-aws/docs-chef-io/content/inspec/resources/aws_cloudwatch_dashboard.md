+++
title = "aws_cloudwatch_dashboard Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_cloudwatch_dashboard"
identifier = "inspec/resources/aws/aws_cloudwatch_dashboard Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudwatch_dashboard.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudwatch_dashboard.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudwatch_dashboard.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudwatch_dashboard.md</a></p>
</div>
</div>


Use the `aws_cloudwatch_dashboard` InSpec audit resource to test properties of the plural AWS CloudWatch dashboard.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS CloudWatch Dashboard.](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-cloudwatch-dashboard.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the dashboard exists.

```ruby
describe aws_cloudwatch_dashboard(dashboard_name: 'DASHBOARD_NAME') do
  it { should exist }
end
```

## Parameters

`dashboard_name` _(required)_

: The name of a dashboard.

## Properties

`dashboard_arn`
: The Amazon Resource Name (ARN) of the dashboard.

`dashboard_body`
: The detailed information about the dashboard, including what widgets are included and their location on the dashboard.

`dashboard_name`
: The name of the dashboard.

## Examples

**Ensure a dashboard ARN is available.**

```ruby
describe aws_cloudwatch_dashboard(dashboard_name: 'DASHBOARD_NAME') do
  its('dashboard_arn') { should eq 'ARN' }
end
```

**Ensure a dashboard body is available.**

```ruby
describe aws_cloudwatch_dashboard(dashboard_name: 'DASHBOARD_NAME') do
    its('dashboard_body') { should eq 'BODY' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `get` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_cloudwatch_dashboard(dashboard_name: 'DASHBOARD_NAME') do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_cloudwatch_dashboard(dashboard_name: 'DASHBOARD_NAME') do
  it { should_not exist }
end
```

## AWS Permissions

{{% aws_permissions_principal action="CloudWatch:Client:GetDashboardOutput" %}}