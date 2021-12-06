+++
title = "aws_signer_profile_permissions Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_signer_profile_permissions"
identifier = "inspec/resources/aws/aws_signer_profile_permissions Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_signer_profile_permissions.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_signer_profile_permissions.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_signer_profile_permissions.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_signer_profile_permissions.md</a></p>
</div>
</div>


Use the `aws_signer_profile_permissions` InSpec audit resource to test properties of multiple AWS Signer profile permissions.

The `AWS::Signer::ProfilePermission` resource adds cross-account permissions to a signing profile.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS Signer ProfilePermission](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-signer-profilepermission.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the profile permission exists.

```ruby
describe aws_signer_profile_permissions(profile_name: 'PROFILE_NAME') do
  it { should exist }
end
```

## Parameters

`profile_name` _(required)_

: Name of the signing profile containing the cross-account permissions.

## Properties

`actions`
: An AWS Signer action permitted as part of cross-account permissions.

: **Field**: `action`

`principals`
: The AWS principal that has been granted a cross-account permission.

: **Field**: `principal`

`statement_ids`
: A unique identifier for a cross-account permission statement.

: **Field**: `statement_id`

`profile_versions`
: The signing profile version that a permission applies to.

: **Field**: `profile_version`

## Examples

**Ensure a principal is available.**

```ruby
describe aws_signer_profile_permissions(profile_name: 'PROFILE_NAME') do
  its('principals') { should include 'PRINCIPAL' }
end
```

**Ensure a statement ID is available.**

```ruby
describe aws_signer_profile_permissions(profile_name: 'PROFILE_NAME') do
  its('statement_ids') { should include 'STATEMENT_ID' }
end
```

**Ensure a profile version is available.**

```ruby
describe aws_signer_profile_permissions(profile_name: 'PROFILE_NAME') do
  its('profile_versions') { should include 'PROFILE_VERSION' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `list` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_signer_profile_permissions(profile_name: 'PROFILE_NAME') do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_signer_profile_permissions(profile_name: 'PROFILE_NAME') do
  it { should_not exist }
end
```

## AWS Permissions

{{% aws_permissions_principal action="Signer:Client:ListProfilePermissionsResponse" %}}