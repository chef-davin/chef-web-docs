+++
title = "aws_servicecatalog_portfolio_principal_association Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_servicecatalog_portfolio_principal_association"
identifier = "inspec/resources/aws/aws_servicecatalog_portfolio_principal_association Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_servicecatalog_portfolio_principal_association.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_servicecatalog_portfolio_principal_association.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_servicecatalog_portfolio_principal_association.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_servicecatalog_portfolio_principal_association.md</a></p>
</div>
</div>


Use the `aws_servicecatalog_portfolio_principal_association` InSpec audit resource to test properties of a single specific AWS Service Catalog portfolio principal association.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS Service Catalog Portfolio Principal Association](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-servicecatalog-portfolioprincipalassociation.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that a portfolio is available.

```ruby
describe aws_servicecatalog_portfolio_principal_association(portfolio_id: 'PORTFOLIO_ID') do
  it { should exist }
end
```

## Parameters

`portfolio_id` _(required)_

: The ID of the portfolio.

## Properties

`principal_arn`
: The ARN of the principal (IAM user, role, or group).

`principal_type`
: The principal type. The supported value is `IAM`.

## Examples

**Ensure a principal ARN is available.**

```ruby
describe aws_servicecatalog_portfolio_principal_association(portfolio_id: 'PORTFOLIO_ID') do
  its('principal_arn') { should eq 'principal_arn' }
end
```

**Ensure a principal type is 'IAM'.**

```ruby
describe aws_servicecatalog_portfolio_principal_association(portfolio_id: 'PORTFOLIO_ID') do
    its('principal_type') { should eq 'IAM' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `describe` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_servicecatalog_portfolio_principal_association(portfolio_id: 'PORTFOLIO_ID') do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_servicecatalog_portfolio_principal_association(portfolio_id: 'PORTFOLIO_ID') do
  it { should_not exist }
end
```

### be_available

Use `should` to check if the entity is available.

```ruby
describe aws_servicecatalog_portfolio_principal_association(portfolio_id: 'PORTFOLIO_ID') do
  it { should be_available }
end
```

## AWS Permissions

{{% aws_permissions_principal action="ServiceCatalog:Client:ListPrincipalsForPortfolioOutput" %}}