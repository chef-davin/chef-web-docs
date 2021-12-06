+++
title = "aws_iam_ssh_public_key Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_iam_ssh_public_key"
identifier = "inspec/resources/aws/aws_iam_ssh_public_key Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_iam_ssh_public_key.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_iam_ssh_public_key.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_iam_ssh_public_key.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_iam_ssh_public_key.md</a></p>
</div>
</div>


Use the `aws_iam_ssh_public_key` InSpec audit resource to test the properties of a singular resource of an AWS SSH public key for an IAM user.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS IAM AccessKey.](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-iam-accesskey.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the public key exists.

```ruby
describe aws_iam_ssh_public_key(user_name: 'USER_NAME', ssh_public_key_id: 'KEY_ID', encoding: 'SSH') do
  it { should exist }
end
```

## Parameters

`user_name` _(required)_

: The IAM user name associated with the SSH public key.

`ssh_public_key_id` _(required)_

: The unique identifier for the SSH public key.

`encoding` _(required)_

: Specifies the public key encoding format to use in the response. To retrieve the public key in SSH-RSA format, use `SSH`. To retrieve the public key in PEM format, use `PEM`.

## Properties

`user_name`
: The name of the IAM user associated with the SSH public key.

`ssh_public_key_id`
: The unique identifier for the SSH public key.

`fingerprint`
: The MD5 message digest of the SSH public key.

`ssh_public_key_body`
: The SSH public key.

`status`
: The status of the SSH public key.

`upload_date`
: The date and time, in ISO 8601 date-time format, when the SSH public key is uploaded.

`ssh_key_age_valid`
: This is a customized parameter. It helps to check AWS IAM SSH keys's age rotated within 730 days. It returns a boolean value.

## Examples

**Ensure a user name is available.**

```ruby
describe aws_iam_ssh_public_key(user_name: 'USER_NAME', ssh_public_key_id: 'KEY_ID', encoding: 'SSH') do
  its('user_name') { should eq 'USER_NAME' }
end
```

**Ensure an SSH public key ID is available.**

```ruby
describe aws_iam_ssh_public_key(user_name: 'USER_NAME', ssh_public_key_id: 'KEY_ID', encoding: 'SSH') do
    its('ssh_public_key_id') { should eq 'SSH_PUBLIC_KEY_ID' }
end
```

**Ensure SSH key is expired or not.**

```ruby
describe aws_iam_ssh_public_key(user_name: 'USER_NAME', ssh_public_key_id: 'KEY_ID', encoding: 'SSH') do
    its('ssh_key_age_valid') { should eq true }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The control passes if the `get` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_iam_ssh_public_key(user_name: 'USER_NAME', ssh_public_key_id: 'KEY_ID', encoding: 'SSH') do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_iam_ssh_public_key(user_name: 'USER_NAME', ssh_public_key_id: 'KEY_ID', encoding: 'SSH') do
  it { should_not exist }
end
```

### be_available

Use `should` to check if the entity is available.

```ruby
describe aws_iam_ssh_public_key(user_name: 'USER_NAME', ssh_public_key_id: 'KEY_ID', encoding: 'SSH') do
  it { should be_available }
end
```

## AWS Permissions

{{% aws_permissions_principal action="IAM:Client:GetSSHPublicKeyResponse" %}}