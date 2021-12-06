+++
title = "aws_sdb_domains Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_sdb_domains"
identifier = "inspec/resources/aws/aws_sdb_domains Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_sdb_domains.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_sdb_domains.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_sdb_domains.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_sdb_domains.md</a></p>
</div>
</div>


Use the `aws_sdb_domains` InSpec audit resource to test multiple SimpleDB domain names.

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that a domain exists.

```ruby
describe aws_sdb_domains do
  it { should exist }
end
```

For additional information, see the [AWS documentation on AWS SDB Domains.](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-properties-simpledb.html).


## Parameters

This resource does not require any parameters.

## Properties

`domain_names`
: A list of domain names that match the expression.

: **Field**: `domain_names`

## Examples

**Ensure a domain name is available.**

```ruby
describe aws_sdb_domains do
  its('domain_names') { should include 'DOMAIN_NAME')' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `list` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_sdb_domains do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_sdb_domains do
  it { should_not exist }
end
```

## AWS Permissions

{{% aws_permissions_principal action="SimpleDB:Client:ListDomainsResult" %}}