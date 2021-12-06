+++
title = "aws_ec2_egress_only_internet_gateways Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_ec2_egress_only_internet_gateways"
identifier = "inspec/resources/aws/aws_ec2_egress_only_internet_gateways Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_ec2_egress_only_internet_gateways.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_ec2_egress_only_internet_gateways.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_ec2_egress_only_internet_gateways.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_ec2_egress_only_internet_gateways.md</a></p>
</div>
</div>


Use the `aws_ec2_egress_only_internet_gateways` InSpec audit resource to test properties of multiple AWS EC2 egress-only internet gateways.

The `AWS::EC2::EgressOnlyInternetGateway` specifies an egress-only internet gateway for your VPC.

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the egress-only internet gateway Id exists.

```ruby
describe aws_ec2_egress_only_internet_gateways do
  it { should exist }
end
```

## Parameters

For additional information, see the [AWS documentation on AWS EC2 egress-only internet gateway.](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-egressonlyinternetgateway.html).

## Properties

`attachments`
: Information about the attachment of the egress-only internet gateway.

: **Field**: `attachments`

`attachments_states`
: The current state of the attachment.

: **Field**: `state`

`attachments_vpc_ids`
: The ID of the VPC.

: **Field**: `vpc_id`

`egress_only_internet_gateway_id`
: The ID of the egress-only internet gateway.

: **Field**: `egress_only_internet_gateway_id`

`tags`
: The tags assigned to the egress-only internet gateway.

: **Field**: `tags`

## Examples

**Ensure an egress-only internet gateway ID is available.**

```ruby
describe aws_ec2_egress_only_internet_gateways do
  its('egress_only_internet_gateway_ids') { should include 'EgressOnlyInternetGatewayId' }
end
```

**Ensure that the attachments states is `attached`.**

```ruby
describe aws_ec2_egress_only_internet_gateways do
    its('attachments_states') { should include 'attached' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `describe` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_ec2_egress_only_internet_gateways do
  it { should exist }
end
```

Use `should_not` to test that an entity does not exist.

```ruby
describe aws_ec2_egress_only_internet_gateways do
  it { should_not exist }
end
```

### be_available

Use `should` to check if the entity is available.

```ruby
describe aws_ec2_egress_only_internet_gateways do
  it { should be_available }
end
```

## AWS Permissions

{{% aws_permissions_principal action="EC2:Client:DescribeEgressOnlyInternetGatewaysResult" %}}