+++
title = "aws_shield_subscription Resource"
platform = "aws"
draft = false
gh_repo = "inspec-aws"

[menu.inspec]
title = "aws_shield_subscription"
identifier = "inspec/resources/aws/aws_shield_subscription Resource"
parent = "inspec/resources/aws"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_shield_subscription.md">https://github.com/inspec/inspec-aws/blob/main/docs/resources/aws_shield_subscription.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_shield_subscription.md">https://github.com/ianmadd/inspec-aws/blob/im/hugo/docs-chef-io/content/inspec/resources/aws_shield_subscription.md</a></p>
</div>
</div>


Use the `aws_shield_subscription` InSpec audit resource to test properties of an AWS Shield Advanced subscription.

## Installation

{{% inspec_aws_install %}}

## Syntax

An `aws_shield_subscription` resource block returns a Shield Advanced subscription.

```ruby
describe aws_shield_subscription do
  it { should exist }
end
```


## Parameters

This resource does not expect any parameters.

Also, see the [AWS Shield Subscriptions documentation](https://docs.aws.amazon.com/waf/latest/developerguide/shield-chapter.html).


## Properties

`auto_renew`
: If `ENABLED`, the subscription will be automatically renewed at the end of the existing subscription period. Valid values: `ENABLED` or `DISABLED`.

`end_time`
: The date and time your subscription will end.

`limits`
: Specifies how many protections of a given type you can create. This is an array containing the Type of protection and the maximum number of protections that can be created for the specified Type.

`proactive_engagement_status`
: Valid values: `ENABLED`, `DISABLED`, `PENDING`. <br> If ENABLED, the DDoS Response Team (DRT) will use email and phone to notify contacts about escalations to the DRT and to initiate proactive customer support. <br/> If `PENDING`, you have requested proactive engagement and the request is pending. The status changes to `ENABLED` when your request is fully processed. <br/> If `DISABLED`, the DRT will not proactively notify contacts about escalations or to initiate proactive customer support.

`start_time`
: The start time of the subscription, in Unix time in seconds.

`time_commitment_in_seconds`
: The length, in seconds, of the AWS Shield Advanced subscription for the account.

For a comprehensive list of properties available, see [the API reference documentation](https://docs.aws.amazon.com/waf/latest/DDOSAPIReference/API_Subscription.html)

## Examples

**Check the automatic renewal status of a Shield Subscription.**

```ruby
describe aws_shield_subscription do
  its('auto_renew')  { should eq 'ENABLED' }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [matchers page](https://www.inspec.io/docs/reference/matchers/).

## AWS Permissions

{{% aws_permissions_principal action="Shield:Client:DescribeSubscriptionResponse" %}}

You can find detailed documentation at [Actions, Resources, and Condition Keys for Amazon Shield](https://docs.aws.amazon.com/IAM/latest/UserGuide/list_awsshield.html).