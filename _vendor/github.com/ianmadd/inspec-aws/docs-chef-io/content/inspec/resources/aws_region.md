+++
title = "aws_region Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_region"
identifier = "inspec/resources/aws/aws_region Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_region.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_region.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_region.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_region.md</a></p>
</div>
</div>


Use the `aws_region` InSpec audit resource to test properties of a single AWS region.

For additional information, including details on parameters and properties, see the [AWS documentation on Regions](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-regions-availability-zones.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

An `aws_region` resource block identifies an AWS region by ID. If no region is provided, the current default is used.

```ruby
describe aws_region('eu-west-2') do
  it { should exist }
end
```

```ruby
describe aws_region(region_name: 'us-east-1') do
  it { should exist }
end
```

## Parameters

`region_name` _(optional)_

: This resource accepts a single parameter, the region_name. 
  This can be passed either as a string or as a `region_name: 'value'` key-value entry in a hash.

## Properties

`region_name`
: The Name of the region.

`endpoint`
: The resolved endpoint of the region.

## Examples

**Test whether a region exists.**

```ruby
describe aws_region('region-not-real') do
  it { should_not exist }
end
```

**Test the Region Endpoint.**

```ruby
describe aws_region(region_name: 'eu-west-2') do
  its('endpoint') { should eq 'ec2.eu-west-2.amazonaws.com' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [matchers page](https://www.inspec.io/docs/reference/matchers/).

### exist

The control will pass if the describe returns at least one result.

```ruby
it { should exist }
```

## AWS Permissions

{{% aws_permissions_principal action="EC2:Client:DescribeRegionsResult" %}}

You can find detailed documentation at [Actions, Resources, and Condition Keys for Amazon EC2](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazonec2.html).