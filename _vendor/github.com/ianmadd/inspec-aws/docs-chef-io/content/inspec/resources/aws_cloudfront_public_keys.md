+++
title = "aws_cloudfront_public_keys Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_cloudfront_public_keys"
identifier = "inspec/resources/aws/aws_cloudfront_public_keys Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudfront_public_keys.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudfront_public_keys.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudfront_public_keys.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudfront_public_keys.md</a></p>
</div>
</div>


Use the `aws_cloudfront_public_keys` InSpec audit resource to test properties of multiple AWS CloudFront public keys.

The `AWS::CloudFront::PublicKey` resource type creates a public key that you can use with signed URLs and signed cookies, or with field-level encryption.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS CloudFront public key.](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-cloudfront-publickey.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the public key exists.

```ruby
describe aws_cloudfront_public_keys do
  it { should exist }
end
```

## Parameters

The resource does not require any parameters.

## Properties

`ids`
: The identifier of the public key.

: **Field**: `id`

`created_times`
: The date and time when the public key was uploaded.

: **Field**: `created_time`

`caller_references`
: A string included in the request to help make sure that the request can’t be replayed.

: **Field**: `caller_reference`

`names`
: A name to help identify the public key.

: **Field**: `name`

`encoded_keys`
: The public key that you can use with signed URLs and signed cookies , or with field-level encryption.

: **Field**: `encoded_key`

`comments`
: A comment to describe the public key. The comment cannot be longer than 128 characters.

: **Field**: `comment`

## Examples

**Ensure a public key ID is available.**

```ruby
describe aws_cloudfront_public_keys do
  its('ids') { should include 'ID' }
end
```

**Ensure a public key name is available.**

```ruby
describe aws_cloudfront_public_keys do
    its('names') { should include 'PUBLIC_KEY_NAME' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `list` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_cloudfront_public_keys do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_cloudfront_public_keys do
  it { should_not exist }
end
```

## AWS Permissions

{{% aws_permissions_principal action="CloudFront:Client:ListPublicKeysResult" %}}