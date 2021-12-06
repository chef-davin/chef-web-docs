+++
title = "aws_cloudwatch_insight_rules Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_cloudwatch_insight_rules"
identifier = "inspec/resources/aws/aws_cloudwatch_insight_rules Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudwatch_insight_rules.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudwatch_insight_rules.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudwatch_insight_rules.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudwatch_insight_rules.md</a></p>
</div>
</div>


Use the `aws_cloudwatch_insight_rules` InSpec audit resource to test properties of the plural AWS CloudWatch Insight rules.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS CloudWatch Insight rules.](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-cloudwatch-insightrule.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the Insight rule exists.

```ruby
describe aws_cloudwatch_insight_rules do
  it { should exist }
end
```

## Parameters

The resource does not require any parameters.

## Properties

`names`
: The name of the rule.

: **Field**: `name`

`states`
: Indicates whether the rule is enabled or disabled.

: **Field**: `schema`

`schemas`
: For rules that you create, this is always {"Name": "CloudWatchLogRule", "Version": 1} . For built-in rules, this is {"Name": "ServiceLogRule", "Version": 1}.

: **Field**: `dashboard_name`

`definitions`
: The definition of the rule, as a JSON object.

: **Field**: `definition`

## Examples

**Ensure a rule name is available.**

```ruby
describe aws_cloudwatch_insight_rules do
  its('names') { should include 'RuleName' }
end
```

**Ensure a state is available.**

```ruby
describe aws_cloudwatch_insight_rules do
    its('states') { should include 'enabled' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `describe` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_cloudwatch_insight_rules do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_cloudwatch_insight_rules do
  it { should_not exist }
end
```

## AWS Permissions

{{% aws_permissions_principal action="CloudWatch:Client:DescribeInsightRulesOutput" %}}