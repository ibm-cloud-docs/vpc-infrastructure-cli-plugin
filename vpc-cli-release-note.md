---

copyright:
  years: 2020
lastupdated: "2020-11-13"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}

# VPC CLI release notes
{: #vpc-cli-rn}

The following release notes are for the {{site.data.keyword.vpc_full}} (VPC) command line interface (CLI).
{:shortdesc}

## v0.7.2
{: #v0.7.2}

Version 0.7.2 was released on 2020-11-12.

### New commands

* N/A

### Updated commands

* Add static, route-based mode support for creating a VPN gateway and connection.

### Removed commands

* N/A


## v0.7.1
{: #v0.7.1}

Version 0.7.1 was released on 2020-11-05.

### New commands

* N/A

### Updated commands

* Add proxy-protocol feature support for load balancer listener/pool create and update commands.

### Removed commands

* N/A


## v0.7.0
{: #v0.7.0}

Version 0.7.0 was released on 2020-10-30.

### New commands

* Add 'create', 'update', 'list', 'get', 'delete' commands for VPC routing-table and routes (custom routes) feature

### Updated commands

* Add 'allow-ip-spoofing' flag for network-interface in instance create and network-interface create/update commands

### Removed commands

* N/A

## v0.6.6
{: #v0.6.6}

Version 0.6.6 was released on 2020-10-23.

### New commands

* Add load-balancer-pool-members-update command to replace the entire pool members

### Updated commands

* Remove the DNS service from endpoint-gateway-targets command output
* Add --members flag to load-balancer-pool-create command to support creating pool with members

### Removed commands

* N/A


## v0.6.4
{: #v0.6.4}

Version 0.6.4 was released on 2020-09-16.

### New commands

* N/A

### Updated commands

* Update all deletion commands to support batch deletion.
* Update vpc-routing-table-create and vpc-routing-table-update to support ingress custom routing feature.

### Removed commands

* N/A


## v0.6.3
{: #v0.6.3}

Version 0.6.3 was released on 2020-08-24.

### New commands

* N/A

### Updated commands

* Update VPC API version to 2020-08-11
* Update network load balancer create command with '--family network' instead of the --profile option.
* Update load-balancer-pool-update command to reset the session-persistence to null with '--session-persistence-type none'.
* Update ‘target’ command to support only the accounts that have generation 1 access.

### Removed commands

* Hide 'load-balancer-profiles' command and it will be removed in next major release.
* Hide 'load-balancer-profile' command and it will be removed in next major release.
* Hide the 'target' command for the account that doesn't have generation 1 access.


## v0.6.2
{: #v0.6.2}

Version 0.6.2 was released on 2020-07-29.

### New commands

* N/A

### Updated commands

* Enable expandable volume feature with 'volume-update' command.
* (Beta) Large volume capacity size support (larger than 2 TB) in volume create and update commands.
* Add '--add-resource-groups' flag to list commands that list resources in all resource groups regardless of target resource group in 'ibmcloud target'.

### Removed commands

* N/A

## v0.6.1
{: #v0.6.1}

Version 0.6.1 was released on 2020-07-17.

### New commands

* N/A

### Updated commands

* (Beta) Update 'image-create' and 'image' command for encrypted image support.
* Add '--output JSON' flag to replace the old '--json' flag. '--json' flag is planned for deprecation and removal in next major release.
* Add '-q, --quiet' flag to suppress the verbose output.

### Removed commands

* N/A

## v0.6.0
{: #v0.6.0}

Version 0.6.0 was released on 2020-06-30.

### New commands

* Added Creating instance from instance-template support for 'instance-create-from-template' command.
* (Beta) Added commands to support dedicated host.

### Updated commands

* Updated all commands with VPC API version to '2020-05-19'.

### Removed commands

* N/A

## v0.5.14
{: #v0.5.14}

Version 0.5.14 was released on 2020-04-30.

### New commands

* N/A

### Updated commands

* Added HTTPS protocol and HTTPS health-type support for 'load-balancer-pool-create' command.
* Added HTTPS protocol and HTTPS health-type support for 'load-balancer-pool-update' command.
* Added floating IP data to 'instance' command JSON output.

### Removed commands

* N/A


## v0.5.13
{: #v0.5.13}

Version 0.5.13 was released on 2020-04-13.

### New commands

* N/A

### Updated commands

* Added CRN fields to various details commands output
* Add example for the `key-create` and `key-update` commands

### Removed commands

* N/A

## v0.5.11
{: #v0.5.11}

Version 0.5.11 was released on 2020-03-05.

### New commands

* N/A

### Updated commands

* Added resource tag fields to the `ibmcloud is volumes` command output
* Updated the `ibmcloud is network-acl-rule-add` command example
* Updated the `ibmcloud is network-acl-create` command example
* Added more command examples to the [VPC CLI reference](/docs/vpc?topic=vpc-infrastructure-cli-plugin-vpc-reference)
* Translation update to the command help

### Removed commands

* N/A

### Other

