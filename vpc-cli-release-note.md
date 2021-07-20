---

copyright:
  years: 2020, 2021
lastupdated: "2021-07-20"

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

## v1.1.0
{: #v1.1.0}

Version 1.0.0 was released on 2021-07-20.

### New commands

* N/A

### Updated commands

* Update `ibmcloud is volume-update` command to expand all volume sizes up to 16 TB.

### Removed commands

* N/A

## v1.0.0
{: #v1.0.0}

Version 1.0.0 was released on 2021-07-08.

### New commands

* N/A

### Updated commands

* Hide the `ibmcloud is target` command.

### Removed commands

* Remove generation 1 support from commands.
* Remove the target generation switching in `ibmcloud is target` command.

## v0.8.6
{: #v0.8.6}

Version 0.8.6 was released on 2021-06-17.

### New commands

* N/A

### Updated commands

* Add cookie persistence support for `load-balancer-pool-create`, `load-balancer-pool-update` and `load-balancer-pool` commands. 

### Removed commands

* N/A

## v0.8.5
{: #v0.8.5}

Version 0.8.5 was released on 2021-05-20.

### New commands

* Add commands `snapshots`, `snapshot`, `snapshot-create`, `snapshot-update`, `snapshot-delete-from-source`, `snapshot-delete` for the snapshot feature.

### Updated commands

* Add `--source-volume` option of the `image-create` command for the image from volume feature.
* Update `--boot-volume`, `--volume-attach` options of the `instance-create` command to support JSON format with `source_snapshot` property setting that supports restoring volume from source snapshot.

## v0.8.4
{: #v0.8.4}

Version 0.8.4 was released on 2021-05-18.

### New commands

* Add commands `instance-group-manager-actions`, `instance-group-manager-action`, `instance-group-manager-action-create`, `instance-group-manager-action-delete`, `instance-group-manager-action-update` for scheduled scaling feature.

### Updated commands

* Add `--owner-type` option for `images list` command to filter images by _owner_type_ property.
* Update `instance-group-manager-create` command for scheduled scaling feature.

## v0.8.1
{: #v0.8.1}

Version 0.8.1 was released on 2021-03-18.

### New commands

* Add command `instance-console` to open an interactive serial console to a virtual server instance.

### Updated commands

* Update `load-balancer-listener-policy-rule-create` and `load-balancer-listener-policy-rule-update` commands to add new `body` and `query` rule types.

### Removed commands

* N/A

## v0.8.0
{: #v0.8,0}

Version 0.8.0 was released on 2021-03-11.

### New commands

* Add `instance-group-membership-update` command.

### Updated commands

* Add dedicated_host_only property to the operating system object in `operating-systems`, `operating-system` and `image` command output.
* Update `--max-members`, `--min-members` options value's range to 1-1000 in the `instance-group-manager-create` and `instance-group-manager-update` commands.
* Add API private endpoint support, only `us-south` and `us-east` regions are supported.

### Removed commands

* N/A

## v0.7.9
{: #v0.7.9}

Version 0.7.9 was released on 2021-03-04.

### New commands

* N/A

### Updated commands

* Add new cipher suite DH19 and SHA512 option for VPN IPSec and IKE policy creation/updating commands.

### Removed commands

* N/A


## v0.7.8
{: #v0.7.8}

Version 0.7.8 was released on 2021-02-25.

### New commands

* Added security group target list/get/add/remove commands so you can list/attach/detach a security group with all applicable target resources, such as network interfaces and load balancers.

### Updated commands

* Added a `delegate_vpc` action type to the `vpc-routing-table-route-create` command to defer a route to the VPC system routing table for forwarding action. Use only for VPCs that have both non-RFC-1918 addresses and public connectivity. For more information, see [Routing considerations for IANA-registered IP assignments](/docs/vpc?topic=vpc-interconnectivity#routing-considerations-iana). 
* Added a `--security-group` flag to the `load-balancer-create` command so you can bind security groups when you create a load balancer.
* Added a security groups field to the `load-balancer` command to show the security groups that are bound to a load balancer.

### Removed commands

* N/A

## v0.7.7
{: #v0.7.7}

Version 0.7.7 was released on 2021-02-08.

### New commands

* N/A

### Updated commands

* Remove the restriction for Generation 1 target switching.

### Removed commands

* N/A


## v0.7.4
{: #v0.7.4}

Version 0.7.4 was released on 2020-12-10.

### New commands

* Add instance storage disk `get`, `list`, and `update` commands.

### Updated commands

* Add flag aliases for routing table `create` and `update` commands.
* Updated usage for `ibmcloud is vpc-address-prefix-create` command.

### Removed commands

* N/A

## v0.7.3
{: #v0.7.3}

Version 0.7.3 was released on 2020-11-19.

### New commands

* N/A

### Updated commands

* Add datapath logging support for load balancer `create` and `update` commands
* Add ingress routing support for VPC routing table `create` and `update` commands
* Add required family/class flags for dedicated host group `create` command.

### Removed commands

* N/A

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
