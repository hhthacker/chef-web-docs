+++
title = "azure_dns_zones_resources Resource"
platform = "azure"
draft = false
gh_repo = "inspec-azure"

[menu.inspec]
title = "azure_dns_zones_resources"
identifier = "inspec/resources/azure/azure_dns_zones_resources Resource"
parent = "inspec/resources/azure"
+++

Use the `azure_dns_zones_resources` InSpec audit resource to test properties related to all Azure DNS zones for a resource group or an entire subscription.

## Azure REST API Version, Endpoint, and HTTP Client Parameters

{{% inspec_azure_common_parameters %}}

## Installation

{{% inspec_azure_install %}}

## Syntax

An `azure_dns_zones_resources` resource block returns all Azure DNS Zones within within a resource group.

```ruby
describe azure_dns_zones_resources do
  #...
end
```

## Parameters

This resource does not require any parameters.

## Properties

`name`
: A list of the unique resource names.

: **Field**: `name`

`ids`
: A list of DNS zone IDs.

: **Field**: `id`

`tags`
: A list of `tag:value` pairs defined on the resources.

: **Field**: `tags`

`types`
: A list of the types of all DNS zones.

: **Field**: `type`

`properties`
: A list of the properties of the Azure DNS zone resources.

: **Field**: `properties`

`max_number_of_recordsets`
: A list of the maximum number of records per record set that can be created in the DNS zones.

: **Field**: `max_number_of_recordsets`

`number_of_record_sets`
: A list of the current number of record sets in the DNS zones.

: **Field**: `number_of_record_sets`

`name_servers`
: A list of the name servers for the DNS zones.

: **Field**: `name_servers`

{{% inspec_filter_table %}}

## Examples

**Test that a DNS zone has has the correct type.**

```ruby
describe azure_dns_zones_resources do
  its('type') { should include 'Microsoft.Network/dnszones' }
end
```

**Test that a DNS zone resource has a `Succeeded` provisioning state.**

```ruby
describe azure_dns_zones_resources do
  its('provisioning_states') { should include 'Succeeded' }
end
```

**Test that a DNS zone has the `global` location.**

```ruby
describe azure_dns_zones_resources do
  its('location') { should include 'global' }
end
```

**Test if any Azure DNS zone exists in the resource group.**

```ruby
describe azure_dns_zones_resources do
  it { should exist }
end
```

## Matchers

This InSpec audit resource has the following special matchers. For a full list of available matchers, please visit our [Universal Matchers page](https://www.inspec.io/docs/reference/matchers/).

### exists

Test that there aren't any Azure DNS zones in the resource group.

```ruby
describe azure_dns_zones_resources do
  it { should_not exist }
end
```

## Azure Permissions

{{% azure_permissions_service_principal role="contributor" %}}
