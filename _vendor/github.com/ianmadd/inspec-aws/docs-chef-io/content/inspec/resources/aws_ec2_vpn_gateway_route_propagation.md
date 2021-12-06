+++
title = "aws_ec2_vpn_gateway_route_propagation Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_ec2_vpn_gateway_route_propagation"
identifier = "inspec/resources/aws/aws_ec2_vpn_gateway_route_propagation Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_ec2_vpn_gateway_route_propagation.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_ec2_vpn_gateway_route_propagation.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_ec2_vpn_gateway_route_propagation.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_ec2_vpn_gateway_route_propagation.md</a></p>
</div>
</div>


Use the `aws_ec2_vpn_gateway_route_propagation` InSpec audit resource to test if a virtual private gateway can propagate routes to a single AWS EC2 route table.

The `AWS::EC2::TransitGatewayRouteTablePropagation` resource enables a virtual private gateway (VGW) to propagate routes to the specified route table of a VPC.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS EC2 VPNGatewayRoutePropagation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-vpn-gatewayrouteprop.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that a route table ID exists.

```ruby
describe aws_ec2_vpn_gateway_route_propagation(route_table_id: 'ROUTE_TABLE_ID') do
  it { should exist }
end
```

## Parameters

`transit_gateway_route_table_id` _(required)_

: The ID of the route table.

## Properties

`vpn_gateway_id`
: The ID of the virtual private gateway.

`route_table_id`
: The ID of the route table.

## Examples

**Ensure a VPN gateway ID is available.**

```ruby
describe aws_ec2_vpn_gateway_route_propagation(route_table_id: 'ROUTE_TABLE_ID') do
  its('vpn_gateway_id') { should eq 'VPN_GATEWAY_ID' }
end
```

**Ensure a route table ID is available.**

```ruby
describe aws_ec2_vpn_gateway_route_propagation(route_table_id: 'ROUTE_TABLE_ID') do
    its('route_table_id') { should eq 'ROUTE_TABLE_ID' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `describe` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_ec2_vpn_gateway_route_propagation(route_table_id: 'ROUTE_TABLE_ID') do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_ec2_vpn_gateway_route_propagation(route_table_id: 'ROUTE_TABLE_ID') do
  it { should_not exist }
end
```

### be_available

Use `should` to check if the entity is available.

```ruby
describe aws_ec2_vpn_gateway_route_propagation(route_table_id: 'ROUTE_TABLE_ID') do
  it { should be_available }
end
```

## AWS Permissions

{{% aws_permissions_principal action="EC2:Client:DescribeRouteTablesResult" %}}