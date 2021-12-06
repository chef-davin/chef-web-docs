+++
title = "aws_network_firewall_rule_groups Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_network_firewall_rule_groups"
identifier = "inspec/resources/aws/aws_network_firewall_rule_groups Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_network_firewall_rule_groups.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_network_firewall_rule_groups.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_network_firewall_rule_groups.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_network_firewall_rule_groups.md</a></p>
</div>
</div>


Use the `aws_network_firewall_rule_groups` InSpec audit resource to test properties of multiple AWS Network Firewall rule groups.

The `AWS::NetworkFirewall::RuleGroup` resource defines a reusable collection of stateless or stateful network traffic filtering rules.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS Network Firewall Rule Group](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-networkfirewall-rulegroup.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the rule group exists.

```ruby
describe aws_network_firewall_rule_groups do
  it { should exist }
end
```

## Parameters

This resource does not require any parameters.

## Properties

`names`
: The descriptive name of the rule group.

: **Field**: `name`

`arns`
: The Amazon Resource Name (ARN) of the rule group.

: **Field**: `arn`

## Examples

**Ensure a name is available.**

```ruby
describe aws_network_firewall_rule_groups do
  its('names') { should include 'RULE_GROUP_NaAME' }
end
```

**Ensure that the arn is available.**

```ruby
describe aws_network_firewall_rule_groups do
    its('arns') { should include 'ARN' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `list` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_network_firewall_rule_groups do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_network_firewall_rule_groups do
  it { should_not exist }
end
```

## AWS Permissions

{{% aws_permissions_principal action="NetworkFirewall:Client:ListRuleGroupsResponse" %}}