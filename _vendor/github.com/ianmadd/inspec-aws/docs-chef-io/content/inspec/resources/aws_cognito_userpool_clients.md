+++
title = "aws_cognito_userpool_clients Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_cognito_userpool_clients"
identifier = "inspec/resources/aws/aws_cognito_userpool_clients Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cognito_userpool_clients.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_cognito_userpool_clients.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cognito_userpool_clients.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_cognito_userpool_clients.md</a></p>
</div>
</div>


Use the `aws_cognito_userpool_clients` InSpec audit resource to test properties of multiple Cognito user pool clients.

For additional information, including details on parameters and properties, see the [AWS documentation on Cognito user pool](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-cognito-userpoolclient.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that a user pool client exists.

```ruby
describe aws_cognito_userpool_clients(user_pool_id: 'USER_POOL_ID') do
  it { should exist }
end
```

## Parameters

`user_pool_id` _(required)_

## Properties

`client_ids`
: The client IDs of the user pools.

`user_pool_ids`
: The user pool IDs of the user pools.

`client_names`
: The client names of the user pools.

## Examples

**Ensure that the specific client ID is available.**

```ruby
describe aws_cognito_userpool_clients(user_pool_id: 'USER_POOL_ID') do
  its('client_ids') { should include 'CLIENT_ID' }
end
```

**Ensure that the specific client name is available.**

```ruby
describe aws_cognito_userpool_clients(user_pool_id: 'USER_POOL_ID') do
    its('client_names') { should include 'CLIENT_NAME' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `list` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_cognito_userpool_clients(user_pool_id: 'USER_POOL_ID') do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_cognito_userpool_clients(user_pool_id: 'USER_POOL_ID') do
  it { should_not exist }
end
```

### be_available

Use `should` to check if the user pool clients are available.

```ruby
describe aws_cognito_userpool_clients(user_pool_id: 'USER_POOL_ID') do
  it { should be_available }
end
```

## AWS Permissions

{{% aws_permissions_principal action="CognitoIdentityProvider:Client:ListUserPoolClientsResponse" %}}