+++
title = "azure_active_directory_domain_services Resource"
platform = "azure"
draft = false
gh_repo = "inspec-azure"

[menu.inspec]
title = "azure_active_directory_domain_services"
identifier = "inspec/resources/azure/azure_active_directory_domain_services Resource"
parent = "inspec/resources/azure"
+++

<div class="admonition-note">
<p class="admonition-note-title">Migration Links for Review</p>
<div class="admonition-note-text">
<p>Source page: <a href="https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_active_directory_domain_services.md">https://github.com/inspec/inspec-azure/blob/main/docs/resources/azure_active_directory_domain_services.md</a></p>
<p>Edited page: <a href="https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_active_directory_domain_services.md">https://github.com/ianmadd/inspec-azure/blob/im/hugo/docs-chef-io/content/inspec/resources/azure_active_directory_domain_services.md</a></p>
</div>
</div>


Use the `azure_active_directory_domain_services` InSpec audit resource to test properties of some or all Azure Active Directory domains within a tenant.

## Azure REST API Version, Endpoint, and HTTP Client Parameters

{{% inspec_azure_common_parameters %}}

## Installation

{{% inspec_azure_install %}}

## Syntax

An `azure_active_directory_domain_services` resource block returns all Azure Active Directory domains contained within the configured tenant and then tests that group of domains.

```ruby
describe azure_active_directory_domain_services do
  #...
end
```

## Parameters

The following parameters can be passed for targeting specific domains.

`filter`
: A hash containing the filtering options and their values. The `starts_with_` operator can be used for fuzzy string matching. Parameter names are in snake case.

: **Field**: `{ starts_with_given_name: 'J', starts_with_department: 'Core', country: 'United Kingdom', given_name: John}`

`filter_free_text`
: [OData](https://www.odata.org/getting-started/basic-tutorial/) query string in double quotes, `"`. Property names are in camel case, refer to [Microsoft's query parameters documentation](https://docs.microsoft.com/en-us/graph/query-parameters#filter-parameter) for more information.

: **Field**: `"startswith(displayName,'J') and surname eq 'Doe'"` or `"userType eq 'Guest'"`

It is advised to use these parameters to narrow down the targeted resources at the server side, Azure Graph API, for a more efficient test.

## Properties

`ids`
: A list of fully qualified names of the domain.

: **Field**: `id`

`authentication_types`
: A list of the configured authentication types for the domain.

: **Field**: `authenticationType`

`availability_statuses`
: A list of domain entities when verify action is set.

: **Field**: `availabilityStatus`

`is_admin_manageds`
: A list of admin managed configuration.

: **Field**: `isAdminManaged`

`is_defaults`
: A list of flags to indicate if they are default domains.

: **Field**: `isDefault`

`is_initials`
: A list of flags to indicate if they are initial domains created by Microsoft Online Services.

: **Field**: `isInitial`

`is_roots`
: A list of flags to indicate if they are verified root domains.

: **Field**: `isRoot`

`is_verifieds`
: A list of flags to indicate if the domains have completed domain ownership verification.

: **Field**: `isVerified`

`password_notification_window_in_days`
: A list of password notification window days.

: **Field**: `passwordNotificationWindowInDays`

`password_validity_period_in_days`
: A list of password validity periods in days.

: **Field**: `passwordValidityPeriodInDays`

`supported_services`
: A list of capabilities assigned to the domain.

: **Field**: `supportedServices`

`states`
: A list of asynchronous operations scheduled.

: **Field**: `state`

<superscript>*</superscript> For information on how to use filter criteria on plural resources refer to [FilterTable usage](https://github.com/inspec/inspec/blob/master/dev-docs/filtertable-usage.md).

## Examples

The following examples show how to use this InSpec audit resource.

**Check domains with some filtering parameters applied at server side using `filter`.**

```ruby
describe azure_active_directory_domain_services(filter: {authenticationType: "authenticationType-value"}) do
  it { should exist }
end
```

**Check domains with some filtering parameters applied at server side using `filter_free_text`.**

```ruby
describe azure_active_directory_domain_services(filter_free_text: "startswith(authenticationType,'authenticationType-value')") do
  it { should exist }
end
```

**Ensure there are supported services using client-side filtering.**

```ruby
describe azure_active_directory_domain_services.supportedServices do
  it { should_not exist }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

### exists

The control will pass if the filter returns at least one result. Use `should_not` if you expect zero matches.

```ruby
describe azure_active_directory_domain_services do
  it { should_not exist }
end
```

## Azure Permissions

Graph resources require specific privileges granted to your service principal.
Please refer to the [Microsoft Documentation](https://docs.microsoft.com/en-us/azure/active-directory/develop/active-directory-integrating-applications#updating-an-application) for information on how to grant these permissions to your application.