+++
title = "aws_ses_templates Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_ses_templates"
identifier = "inspec/resources/aws/aws_ses_templates Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_ses_templates.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_ses_templates.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_ses_templates.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_ses_templates.md</a></p>
</div>
</div>


Use the `aws_ses_templates` InSpec audit resource to test properties of multiple AWS Simple Email Service (SES) templates.

The `AWS::SES::Template` resource specifies an email template.

For additional information, including details on parameters and properties, see the [AWS documentation on AWS SES Template](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/aws-resource-ses-template.html).

## Installation

{{% inspec_aws_install %}}

## Syntax

Ensure that the template exists.

```ruby
describe aws_ses_templates do
  it { should exist }
end
```

## Parameters

The resource does not require any parameters.

## Properties

`names`
: The name of the template.

: **Field**: `name`

`created_timestamps`
: The time and date the template was created.

: **Field**: `created_timestamp`

## Examples

**Ensure a template name is available.**

```ruby
describe aws_ses_templates do
  its('names') { should include 'TEMPLATE_NAME' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

The controls will pass if the `list` method returns at least one result.

### exist

Use `should` to test that the entity exists.

```ruby
describe aws_ses_templates do
  it { should exist }
end
```

Use `should_not` to test the entity does not exist.

```ruby
describe aws_ses_templates do
  it { should_not exist }
end
```

## AWS Permissions

{{% aws_permissions_principal action="SES:Client:ListTemplatesResponse" %}}