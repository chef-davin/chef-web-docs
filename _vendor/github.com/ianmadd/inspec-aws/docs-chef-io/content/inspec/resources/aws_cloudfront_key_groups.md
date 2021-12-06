+++
title = "aws_cloudfront_key_groups Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_cloudfront_key_groups"
identifier = "inspec/resources/aws/aws_cloudfront_key_groups Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudfront_key_groups.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudfront_key_groups.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudfront_key_groups.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudfront_key_groups.md</a></p>
</div>
</div>


Use the `aws_cloudfront_key_groups` InSpec audit resource to test properties of multiple AWS CloudFront key groups.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS CloudFront key group.](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-cloudfront-keygroup.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the key group exists.

```ruby
describe aws_cloudfront_key_groups do
  it { should exist }
end
```

## Parameters

The resource does not require any parameters.

## Properties

`ids`
: The identifier for the key group.

: **Field**: `id`

`last_modified_times`
: The date and time when the key group was last modified.

: **Field**: `last_modified_time`

`names`
: A name to identify the key group.

: **Field**: `name`

`items`
: A list of the identifiers of the public keys in the key group.

: **Field**: `items`

`comments`
: A comment to describe the key group. The comment cannot be longer than 128 characters.

: **Field**: `comment`

## Examples

**Ensure an ID is available.**

```ruby
describe aws_cloudfront_key_groups do
  its('ids') { should include 'ID' }
end
```

**Ensure that the key group name is available.**

```ruby
describe aws_cloudfront_key_groups do
    its('names') { should include 'KEY_GROUP_NAME' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `list` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_cloudfront_key_groups do
  it { should exist }
end
```

Use `should_not` to test that an entity does not exist.

```ruby
describe aws_cloudfront_key_groups do
  it { should_not exist }
end
```

## AWS Permissions

{{% aws_permissions_principal action="CloudFront:Client:ListKeyGroupsResult" %}}