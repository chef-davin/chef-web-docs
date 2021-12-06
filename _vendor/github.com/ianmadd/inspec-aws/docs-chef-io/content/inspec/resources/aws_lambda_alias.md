+++
title = "aws_lambda_alias Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_lambda_alias"
identifier = "inspec/resources/aws/aws_lambda_alias Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_lambda_alias.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_lambda_alias.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_lambda_alias.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_lambda_alias.md</a></p>
</div>
</div>


Use the `aws_lambda_alias` InSpec audit resource to test properties of a single AWS Lambda alias.

The `AWS::Lambda::Alias` resource creates an alias for a Lambda function version. Use aliases to provide clients with a function identifier that you can update to invoke a different version.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS Lambda alias](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-lambda-alias.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the alias exists.

```ruby
describe aws_lambda_alias(function_name: 'FUNCTION_NAME', function_alias_name: 'FUNCTION_ALIAS_NAME') do
  it { should exist }
end
```

## Parameters

`function_name` _(required)_

: The name of the lambda function.

`function_alias_name` _(required)_

: Name of the alias for which you want to retrieve information.

## Properties

`alias_arn`
: Lambda function ARN that is qualified using the alias name as the suffix.

`name`
: The alias name.

`function_version`
: Function version to which the alias points.

`description`
: The alias description.

`routing_config.additional_version_weights`
: The name of the second alias, and the percentage of traffic that is routed to it.

`revision_id`
: Represents the latest updated revision of the function or alias.

## Examples

**Ensure an alias ARN is available.**

```ruby
describe aws_lambda_alias(function_name: 'FUNCTION_NAME', function_alias_name: 'FUNCTION_ALIAS_NAME') do
  its('alias_arn') { should eq 'ALIAS_ARN' }
end
```

**Ensure a alias name is available.**

```ruby
describe aws_lambda_alias(function_name: 'FUNCTION_NAME', function_alias_name: 'FUNCTION_ALIAS_NAME') do
  its('name') { should eq 'FUNCTION_ALIAS_NAME' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `get` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_lambda_alias(function_name: 'FUNCTION_NAME', function_alias_name: 'FUNCTION_ALIAS_NAME') do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_lambda_alias(function_name: 'FUNCTION_NAME', function_alias_name: 'FUNCTION_ALIAS_NAME') do
  it { should_not exist }
end
```

### be_available

Use `should` to check if the entity is available.

```ruby
describe aws_lambda_alias(function_name: 'FUNCTION_NAME', function_alias_name: 'FUNCTION_ALIAS_NAME') do
  it { should be_available }
end
```

## AWS Permissions

{{% aws_permissions_principal action="Lambda:Client:AliasConfiguration" %}}