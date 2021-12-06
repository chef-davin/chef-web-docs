+++
title = "aws_apigateway_api_keys Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_apigateway_api_keys"
identifier = "inspec/resources/aws/aws_apigateway_api_keys Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_apigateway_api_keys.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_apigateway_api_keys.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_apigateway_api_keys.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_apigateway_api_keys.md</a></p>
</div>
</div>


Use the `aws_apigateway_api_keys` InSpec audit resource to test properties of multiple AWS API Gateway API keys.

The `AWS::ApiGateway::ApiKey` resource creates a unique key that you can distribute to clients who are executing API Gateway Method resources that require an API key.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS API Gateway API Key.](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-apikey.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the API key exists.

```ruby
describe aws_apigateway_api_keys do
  it { should exist }
end
```

## Parameters

The resource does not require any parameters.

## Properties

`ids`
: The identifier of the API Key.

: **Field**: `id`

`values`
: The value of the API Key.

: **Field**: `value`

`names`
: The name of the API Key.

: **Field**: `name`

`customer_ids`
: An AWS Marketplace customer identifier , when integrating with the AWS SaaS Marketplace.

: **Field**: `customer_id`

`descriptions`
: The description of the API Key.

: **Field**: `description`

`enabled`
: Specifies whether the API Key can be used by callers.

: **Field**: `enabled`

`created_dates`
: The timestamp when the API Key was created.

: **Field**: `created_date`

`last_updated_dates`
: The timestamp when the API Key was last updated.

: **Field**: `last_updated_date`

`stage_keys`
: A list of Stage resources that are associated with the ApiKey resource.

: **Field**: `stage_keys`

`tags`
: The collection of tags.

: **Field**: `tags`

## Examples

**Ensure a ID is available.**

```ruby
describe aws_apigateway_api_keys do
  its('ids') { should include 'API_ID' }
end
```

**Ensure that the name is available.**

```ruby
describe aws_apigateway_api_keys do
    its('names') { should include 'API_NAME' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `get` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_apigateway_api_keys do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_apigateway_api_keys do
  it { should_not exist }
end
```

## AWS Permissions

{{% aws_permissions_principal action="APIGateway:Client:ApiKeys" %}}