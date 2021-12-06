+++
title = "aws_ec2_transit_gateway_route_table_propagation Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_ec2_transit_gateway_route_table_propagation"
identifier = "inspec/resources/aws/aws_ec2_transit_gateway_route_table_propagation Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_ec2_transit_gateway_route_table_propagation.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_ec2_transit_gateway_route_table_propagation.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_ec2_transit_gateway_route_table_propagation.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_ec2_transit_gateway_route_table_propagation.md</a></p>
</div>
</div>


Use the `aws_ec2_transit_gateway_route_table_propagation` InSpec audit resource to test properties of a propagation route between a Transit Gateway attachment and a Transit Gateway route table.

The `AWS::EC2::TransitGatewayRouteTablePropagation` resource enables the specified attachment to propagate routes to the specified propagation route table.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS EC2 TransitGatewayRouteTablePropagation](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ec2-transitgatewayroutetablepropagation.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that a Transit Gateway route table id exists.

```ruby
describe aws_ec2_transit_gateway_route_table_propagation(transit_gateway_route_table_id: 'TRANSIT_GATEWAY_ROUTE_TABLE_ID', transit_gateway_attachment_id: "TRANSIT_GATEWAY_ATTACHMENT_ID") do
  it { should exist }
end
```

## Parameters

`transit_gateway_route_table_id` _(required)_

: The ID of the Transit Gateway route table.

`transit_gateway_attachment_id` _(required)_

: The ID of the attachment.

## Properties

`transit_gateway_attachment_id`
: The ID of the attachment.

`resource_id`
: The ID of the resource.

`resource_type`
: The type of resource.

`state`
: The state of the resource.

## Examples

**Ensure a Transit Gateway attachment ID is available.**

```ruby
describe aws_ec2_transit_gateway_route_table_propagation(transit_gateway_route_table_id: 'TRANSIT_GATEWAY_ROUTE_TABLE_ID', transit_gateway_attachment_id: "TRANSIT_GATEWAY_ATTACHMENT_ID") do
  its('transit_gateway_attachment_id') { should eq 'TRANSIT_GATEWAY_ROUTE_TABLE_ID' }
end
```

**Ensure that the state is `enabled`.**

```ruby
describe aws_ec2_transit_gateway_route_table_propagation(transit_gateway_route_table_id: 'TRANSIT_GATEWAY_ROUTE_TABLE_ID', transit_gateway_attachment_id: "TRANSIT_GATEWAY_ATTACHMENT_ID") do
    its('state') { should eq 'enabled' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `get` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_ec2_transit_gateway_route_table_propagation(transit_gateway_route_table_id: 'TRANSIT_GATEWAY_ROUTE_TABLE_ID', transit_gateway_attachment_id: "TRANSIT_GATEWAY_ATTACHMENT_ID") do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_ec2_transit_gateway_route_table_propagation(transit_gateway_route_table_id: 'TRANSIT_GATEWAY_ROUTE_TABLE_ID') do
  it { should_not exist }
end
```

### be_available

Use `should` to check if the entity is available.

```ruby
describe aws_ec2_transit_gateway_route_table_propagation(transit_gateway_route_table_id: 'TRANSIT_GATEWAY_ROUTE_TABLE_ID', transit_gateway_attachment_id: "TRANSIT_GATEWAY_ATTACHMENT_ID") do
  it { should be_available }
end
```

## AWS Permissions

{{% aws_permissions_principal action="EC2:Client:GetTransitGatewayRouteTablePropagationsResult" %}}