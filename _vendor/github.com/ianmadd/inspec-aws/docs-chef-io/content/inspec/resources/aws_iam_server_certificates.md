+++
title = "aws_iam_server_certificates Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_iam_server_certificates"
identifier = "inspec/resources/aws/aws_iam_server_certificates Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_iam_server_certificates.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_iam_server_certificates.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_iam_server_certificates.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_iam_server_certificates.md</a></p>
</div>
</div>


Use the `aws_iam_server_certificates` InSpec audit resource to test the properties of all IAM server certificates.

This resource retrieves information about the server certificate, including the server certificate's path, GUID, ARN, and role.

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that a server certificate name exists.

```ruby
describe aws_iam_server_certificates do
  it { should exist }
end
```

For additional information, see the [AWS documentation on IAM Instance Profile](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-iam-instanceprofile.html).

## Properties

`paths`
: The path to the server certificate.

`server_certificate_names`
: The name that identifies the server certificate.

`server_certificate_ids`
: The stable and unique string identifying the server certificate.

`arns`
: The Amazon Resource Name (ARN) specifying the server certificate.

`upload_date`
: The date when the server certificate is uploaded.

`expiration_date`
: The date on which the certificate is set to expire.

## Examples

**Ensure a server certificate name is available.**

```ruby
describe aws_iam_server_certificates do
  its('server_certificate_name') { should include 'PROFILE_NAME' }
end
```

**Ensure that an arn is available.**

```ruby
describe aws_iam_server_certificates do
    its('arn') { should include 'INSTANCE_PROFILE_NAME_ARN' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `list` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_iam_server_certificates do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_iam_server_certificates do
  it { should_not exist }
end
```

### be_available

Use `should` to check if the server certificate is available.

```ruby
describe aws_iam_server_certificates do
  it { should be_available }
end
```

## AWS Permissions

{{% aws_permissions_principal action="IAM:Client:ListServerCertificateResponse" %}}