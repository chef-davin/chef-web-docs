+++
title = "aws_cloudfront_cache_policies Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_cloudfront_cache_policies"
identifier = "inspec/resources/aws/aws_cloudfront_cache_policies Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudfront_cache_policies.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cloudfront_cache_policies.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudfront_cache_policies.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cloudfront_cache_policies.md</a></p>
</div>
</div>


Use the `aws_cloudfront_cache_policies` InSpec audit resource to test properties of multiple AWS CloudFront cache policies.

The `AWS::CloudFront::CachePolicy` resource describes the CloudFront cache policy.

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the custom resource exists.

```ruby
describe aws_cloudfront_cache_policies do
  it { should exist }
end
```

## Parameters

This resource does not require any parameters.

For additional information, see the [AWS documentation on AWS CloudFront cache policy.](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-cloudfront-cache policy.html).

## Properties

`types`
: The type for the cache policy.

: **Field**: `type`

`ids`
: The unique identifier for the cache policy.

: **Field**: `id`

`last_modified_times`
: The date and time when the cache policy was last modified.

: **Field**: `last_modified_time`

`comments`
: A comment to describe the cache policy.

: **Field**: `comment`

`names`
: A unique name to identify the cache policy.

: **Field**: `name`

`default_ttls`
: The default amount of time, in seconds, that you want objects to stay in the CloudFront cache before CloudFront sends another request to the origin to see if the object has been updated.

: **Field**: `default_ttl`

`max_ttls`
: The maximum amount of time, in seconds, that objects stay in the CloudFront cache before CloudFront sends another request to the origin to see if the object has been updated.

: **Field**: `max_ttl`

`min_ttls`
: The minimum amount of time, in seconds, that you want objects to stay in the CloudFront cache before CloudFront sends another request to the origin to see if the object has been updated.

: **Field**: `min_ttl`

## Examples

**Test that an ID is available.**

```ruby
describe aws_cloudfront_cache_policies do
  its('ids') { should include 'ID' }
end
```

**Verify the maximum TTL of the policy.**

```ruby
describe aws_cloudfront_cache_policies do
    its('max_ttls') { should include 1 }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `list` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_cloudfront_cache_policies do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_cloudfront_cache_policies do
  it { should_not exist }
end
```

## AWS Permissions

{{% aws_permissions_principal action="CloudFront:Client:ListCachePoliciesResult" %}}