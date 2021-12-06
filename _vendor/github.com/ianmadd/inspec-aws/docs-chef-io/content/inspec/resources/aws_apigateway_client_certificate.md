+++
title = "aws_apigateway_client_certificate Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_apigateway_client_certificate"
identifier = "inspec/resources/aws/aws_apigateway_client_certificate Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_apigateway_client_certificate.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_apigateway_client_certificate.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_apigateway_client_certificate.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_apigateway_client_certificate.md</a></p>
</div>
</div>


Use the `aws_apigateway_client_certificate` InSpec audit resource to test properties of a single specific AWS API Gateway client certificate.

The `AWS::ApiGateway::ClientCertificate` resource creates a client certificate that API Gateway uses to configure client-side SSL authentication for sending requests to the integration endpoint.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS APIGateway ClientCertificate.](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-apigateway-clientcertificate.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the client certificate exists.

```ruby
describe aws_apigateway_client_certificate(client_certificate_id: 'CLIENT_CERTIFICATE_ID') do
  it { should exist }
end
```

## Parameters

`client_certificate_id` _(required)_

: The identifier of the client certificate.

## Properties

`client_certificate_id`
: The identifier of the client certificate.

`description`
: The description of the client certificate.

`pem_encoded_certificate`
: The PEM-encoded public key of the client certificate, which can be used to configure certificate authentication in the integration endpoint .

`created_date`
: The timestamp when the client certificate was created.

`expiration_date`
: The timestamp when the client certificate will expire.

`tags`
: The collection of tags. Each tag element is associated with a given resource.

## Examples

**Ensure a client certificate id is available.**

```ruby
describe aws_apigateway_client_certificate(client_certificate_id: 'CLIENT_CERTIFICATE_ID') do
  its('client_certificate_id') { should eq 'CLIENT_CERTIFICATE_ID' }
end
```

**Ensure a pem encoded certificate is available.**

```ruby
describe aws_apigateway_client_certificate(client_certificate_id: 'CLIENT_CERTIFICATE_ID') do
    its('pem_encoded_certificate') { should eq 'PEM_ENCODED_CERTIFICATE' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `get` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_apigateway_client_certificate(client_certificate_id: 'CLIENT_CERTIFICATE_ID') do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_apigateway_client_certificate(client_certificate_id: 'CLIENT_CERTIFICATE_ID') do
  it { should_not exist }
end
```

### be_available

Use `should` to check if the entity is available.

```ruby
describe aws_apigateway_client_certificate(client_certificate_id: 'CLIENT_CERTIFICATE_ID') do
  it { should be_available }
end
```

## AWS Permissions

{{% aws_permissions_principal action="APIGateway:Client:ClientCertificate" %}}