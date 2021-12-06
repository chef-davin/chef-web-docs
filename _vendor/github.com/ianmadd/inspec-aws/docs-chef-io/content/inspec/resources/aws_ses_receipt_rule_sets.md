+++
title = "aws_ses_receipt_rule_sets Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_ses_receipt_rule_sets"
identifier = "inspec/resources/aws/aws_ses_receipt_rule_sets Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_ses_receipt_rule_sets.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_ses_receipt_rule_sets.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_ses_receipt_rule_sets.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_ses_receipt_rule_sets.md</a></p>
</div>
</div>


Use the `aws_ses_receipt_rule_sets` InSpec audit resource to test properties of multiple AWS Simple Email Service (SES) receipt rule sets.

The `AWS::SES::ReceiptRuleSet` resource specifies a receipt rule set.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS SES ReceiptRuleSet](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ses-receiptruleset.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the rule set exists.

```ruby
describe aws_ses_receipt_rule_sets do
  it { should exist }
end
```

## Parameters

The resource does not require any parameters.

## Properties

`names`
: The name of the receipt rule set.

: **Field**: `name`

`created_timestamps`
: The date and time the receipt rule set was created.

: **Field**: `created_timestamp`

## Examples

**Ensure a rule set name is available.**

```ruby
describe aws_ses_receipt_rule_sets do
  its('names') { should include 'RULE_SET_NAME' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `list` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_ses_receipt_rule_sets do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_ses_receipt_rule_sets do
  it { should_not exist }
end
```

## AWS Permissions

{{% aws_permissions_principal action="SES:Client:ListReceiptRuleSetsResponse" %}}