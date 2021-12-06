+++
title = "aws_cloudfront_public_key Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_cloudfront_public_key"
identifier = "inspec/resources/aws/aws_cloudfront_public_key Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudfront_public_key.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudfront_public_key.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudfront_public_key.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudfront_public_key.md</a></p>
</div>
</div>


Use the `aws_cloudfront_public_key` InSpec audit resource to test properties of a single AWS CloudFront public key.

The `AWS::CloudFront::PublicKey` resource type creates a public key that you can use with signed URLs and signed cookies, or with field-level encryption.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS Logs public key.](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-cloudfront-publickey.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the public key exists.

```ruby
describe aws_cloudfront_public_key(id: "PUBLIC_KEY_ID") do
  it { should exist }
end
```

## Parameters

`id` _(required)_

: The identifier of the public key.

## Properties

`id`
: The identifier of the public key.

`created_time`
: The date and time when the public key was uploaded.

`public_key_config.caller_reference`
: A string included in the request to help make sure that the request can’t be replayed.

`public_key_config.name`
: A name to help identify the public key.

`public_key_config.encoded_key`
: The public key that you can use with signed URLs and signed cookies , or with field-level encryption.

`public_key_config.comment`
: A comment to describe the public key. The comment cannot be longer than 128 characters.

## Examples

**Ensure a public key ID is available.**

```ruby
describe aws_cloudfront_public_key(id: "PUBLIC_KEY_ID") do
  its('id') { should eq 'ID' }
end
```

**Ensure a public key name is available.**

```ruby
describe aws_cloudfront_public_key(id: "PUBLIC_KEY_ID") do
    its('public_key_config.name') { should eq 'PUBLIC_KEY_NAME' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `get` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_cloudfront_public_key(id: "PUBLIC_KEY_ID") do
  it { should exist }
end
```

Use `should_not` to test that an entity does not exist.

```ruby
describe aws_cloudfront_public_key(id: "PUBLIC_KEY_ID") do
  it { should_not exist }
end
```

### be_available

Use `should` to check if the entity is available.

```ruby
describe aws_cloudfront_public_key(id: "PUBLIC_KEY_ID") do
  it { should be_available }
end
```

## AWS Permissions

{{% aws_permissions_principal action="CloudFront:Client:GetPublicKeyResult" %}}