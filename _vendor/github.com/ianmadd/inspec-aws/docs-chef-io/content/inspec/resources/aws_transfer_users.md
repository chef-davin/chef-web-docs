+++
title = "aws_transfer_users Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_transfer_users"
identifier = "inspec/resources/aws/aws_transfer_users Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_transfer_users.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_transfer_users.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_transfer_users.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_transfer_users.md</a></p>
</div>
</div>


Use the `aws_transfer_users` InSpec audit resource to test properties of multiple Transfer users.

For additional information, including details on parameters and properties, see the [AWS documentation on Transfer user](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-transfer-user.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that an user exists.

```ruby
describe aws_transfer_users do
  it { should exist }
end
```

## Parameters

The resource does not require any parameters.

## Properties

`ARNs`
: The ARNs of the user.

`home_directories`
: The landing directories for users when they log in to the server using the client.

`home_directory_types`
: The landing directory types you want your users' home directory to be when they log into the server.

`roles`
: The ARNs of the IAM roles that controls your users' access to your Amazon S3 bucket or EFS file system.

`ssh_public_key_count`
: The ssh public key count of the user.

`user_names`
: The user names associated with a server as specified by the `ServerId`.

## Examples

**Ensure an ARN is available.**

```ruby
describe aws_transfer_users do
  its('arns') { should include 'USER_ARN' }
end
```

**Ensure that the roles is available.**

```ruby
describe aws_transfer_users do
    its('roles') { should include 'USER_ROLE_ARN' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `list` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_transfer_users do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_transfer_users do
  it { should_not exist }
end
```

### be_available

Use `should` to check if the user is available.

```ruby
describe aws_transfer_users do
  it { should be_available }
end
```

## AWS Permissions

{{% aws_permissions_principal action="Transfer:Client:ListUsersResponse" %}}