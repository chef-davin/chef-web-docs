+++
title = "aws_dynamodb_tables Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_dynamodb_tables"
identifier = "inspec/resources/aws/aws_dynamodb_tables Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_dynamodb_tables.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_dynamodb_tables.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_dynamodb_tables.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_dynamodb_tables.md</a></p>
</div>
</div>


Use the `aws_dynamodb_table` InSpec audit resource to test properties of a collection of AWS DynamoDB Table.

## Installation

{{% inspec_aws_install %}}

## Syntax

 Ensure exactly 3 DynamoDB Tables exist.

```ruby
describe aws_dynamodb_tables do
  its('names.count') { should cmp 3 }
end
```

## Parameters

This resource does not expect any parameters.

See also the [AWS documentation on DynamoDB](https://docs.aws.amazon.com/dynamodb/?id=docs_gateway).

## Properties

`table_names`
: The names of the tables associated with the current account at the current endpoint.


For a comprehensive list of properties available, see [the API reference documentation](https://docs.aws.amazon.com/amazondynamodb/latest/APIReference/API_ListTables.html)

## Examples

**Ensure DynamoDB Tables are encrypted.**

```ruby
aws_dynamodb_tables.table_names.each do |table|
  describe aws_dynamodb_table(table_name: table) do
    it { should exist }
    it { should be_encrypted}
  end
end
```

**Ensure the DynamoDB Tables exists and encrypted.**

```ruby
aws_dynamodb_tables.where(table_names: 'table_name').table_names.each do |table|
    describe aws_dynamodb_table(table_name: table) do
        it { should exist }
        it { should be_encrypted }
    end
end
```

**Ensure the DynamoDB table exist.**

```ruby
describe aws_dynamodb_tables do
    its('table_names') { should include 'table_name'}
end
```

## Matchers

For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

### exist

The control will pass if the describe returns at least one result.

Use `should` to test the entity should exist.

```ruby
describe aws_dynamodb_tables.where( <property>: <value> ) do
  it { should exist }
end
```

Use `should_not` to test the entity should not exist.

```ruby
describe aws_dynamodb_tables.where( <property>: <value> ) do
  it { should_not exist }
end
```

## AWS Permissions

{{% aws_permissions_principal action="DynamoDB:Client:ListTablesOutput" %}}

You can find detailed documentation at [Actions, Resources, and Condition Keys for Amazon Dynamodb](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_amazondynamodb.html).