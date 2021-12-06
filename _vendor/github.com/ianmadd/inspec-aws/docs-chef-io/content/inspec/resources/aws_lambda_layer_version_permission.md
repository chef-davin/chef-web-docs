+++
title = "aws_lambda_layer_version_permission Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_lambda_layer_version_permission"
identifier = "inspec/resources/aws/aws_lambda_layer_version_permission Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_lambda_layer_version_permission.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_lambda_layer_version_permission.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_lambda_layer_version_permission.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_lambda_layer_version_permission.md</a></p>
</div>
</div>


Use the `aws_lambda_layer_version_permission` InSpec audit resource to test properties of a single AWS Lambda layer version permission.

The `AWS::Lambda::LayerVersionPermission` resource adds permissions to the resource-based policy of a version of an Lambda layer.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS Lambda layer version permission](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-lambda-layerversionpermission.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the permission exists.

```ruby
describe aws_lambda_layer_version_permission(layer_name: 'LAYER_NAME', version_number: 'VERSION_NUMBER') do
  it { should exist }
end
```

## Parameters

`layer_name` _(required)_

: The name or Amazon Resource Name (ARN) of the layer.

`version_number` _(required)_

: The version number.

## Properties

`policy`
: The policy document.

`revision_id`
: A unique identifier for the current revision of the policy.

## Examples

**Ensure a policy is available.**

```ruby
describe aws_lambda_layer_version_permission(layer_name: 'LAYER_NAME', version_number: 'VERSION_NUMBER') do
  its('policy') { should eq 'POLICY' }
end
```

**Ensure a revision ID is available.**

```ruby
describe aws_lambda_layer_version_permission(layer_name: 'LAYER_NAME', version_number: 'VERSION_NUMBER') do
    its('revision_id') { should eq 'REVISION_ID' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `get` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_lambda_layer_version_permission(layer_name: 'LAYER_NAME', version_number: 'VERSION_NUMBER') do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_lambda_layer_version_permission(layer_name: 'LAYER_NAME', version_number: 'VERSION_NUMBER') do
  it { should_not exist }
end
```

### be_available

Use `should` to check if the entity is available.

```ruby
describe aws_lambda_layer_version_permission(layer_name: 'LAYER_NAME', version_number: 'VERSION_NUMBER') do
  it { should be_available }
end
```

## AWS Permissions

{{% aws_permissions_principal action="Lambda:Client:GetLayerVersionPolicyResponse" %}}