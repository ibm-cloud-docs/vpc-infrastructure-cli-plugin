---

copyright:
  years: 2020, 2022
lastupdated: "2022-08-19"

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
{: shortdesc}

## v5.1.0
{: #v5.1.0}

Version 5.1.0 was released on 2022-08-19.

### New commands

* N/A

### Updated commands

* Updated `instance-create`, `instance-volume-attachment-add`, `instance-template-create` commands to support user tags.

### Removed commands

* N/A

## v5.0.1
{: #v5.0.1}

Version 5.0.1 was released on 2022-07-29.

### New commands

* N/A

### Updated commands

* N/A

### Removed commands

* N/A

### Note
* Fixed VPC CRI relogin issue.

## v5.0.0
{: #v5.0.0}

Version 5.0.0 was released on 2022-07-14.

### New commands

* N/A

### Updated commands

* Updated `vpc-routing-table-create` and `vpc-routing-table-update` commands to support custom routes for a VPN server.

* Updated `security-group-target`, `security-group-target-add` and `security-group-target-remove` commands to support a VPN server target.

* Updated `vpn-server-create`, and `vpn-server-update` commands to support the secrets manager.

### Removed commands

* Removed VPC route commands `vpc-routes`,`vpc-route`, `vpc-route-create`, `vpc-route-update` and `vpc-route-delete`.

### Note
* VPN server commands are available.

## v4.2.0
{: #v4.2.0}

Version 4.2.0 was released on 2022-06-17.

### New commands

* Added `backup-policies`, `backup-policy-create`, `backup-policy`, `backup-policy-update`, `backup-policy-delete`, `backup-policy-plan`, `backup-policy-plans`, `backup-policy-plan-create`, `backup-policy-plan-update`, `backup-policy-plan-delete`, `backup-policy-jobs` and `backup-policy-job` commands to support Backup As a Service.

### Updated commands

* Updated `volume-create`, `volume-update`, `snapshot-create` and `snapshot-update` commands to support user tags.

### Removed commands

* N/A

### Note

* Added plugin support for Linux and Mac ARM64 architecture.

## v4.1.0
{: #v4.1.0}

Version 4.1.0 was released on 2022-05-27.

### New commands

* N/A

### Updated commands

* Updated `load-balancer-listener-create` and `load-balancer-listener-update` commands to support secrets manager.
* Updated `security-group-rule-update` command to support ICMP type and ICMP code reset options.
* Updated `instance-update` command to support placement target patch.
* Updated `vpn-server-update` command to support client DNS reset option.

### Removed commands

* N/A

## v4.0.3
{: #v4.0.3}

Version 4.0.3 was released on 2022-04-25.

### New commands

* N/A

### Updated commands

* Updated `instance-create` command to support more data volumes in interactive mode.

### Removed commands

* N/A

### Note

* Fixed `bare-metal-server-create` command's interactive mode error log for allowed-vlans.
* Fixed `bare-metal-server-console` command to display the correct bare metal server VNC console URL.

## v4.0.2
{: #v4.0.2}

Version 4.0.2 was released on 2022-04-08.

### New commands

* N/A

### Updated commands

* N/A

### Removed commands

* N/A

### Note

* Fixed the reserved IP not displaying issue when the instance list `instances` command is run.

## v4.0.1
{: #v4.0.1}

Version 4.0.1 was released on 2022-04-06.

### New commands

* Added `instance-network-interface-reserved-ips` and `instance-network-interface-reserved-ip` commands to list/get reserved IPs that are associated with a network interface.

### Updated commands

* Updated `instance-create`, `instance-network-interface-create`, `instance-create-from-template`, `instance-template-create`, `instance-template-create-override-source-template`, `bare-metal-server-create`, `bare-metal-server-network-interface-create`, `subnet-reserved-ip-create` commands to support reserved IP.

### Removed commands

* Removed security group network interface commands `security-group-network-interface`, `security-group-network-interface-add`, `security-group-network-interface-remove` and `security-group-network-interfaces`.

### Note

* Support for primary_ipv4_address property in primary-network-interface and network-interface options for the `instance-create`, `instance-create-from-template`, `instance-template-create` and `instance-template-create-override-source-template` commands were removed. Use primary_ip property to create the resource with wanted IP address.

* Support for IPV4 option for the `instance-create`, `instance-network-interface-create`, `instance-create-from-template`, `instance-template-create` and `instance-template-create-override-source-template` commands were removed. Use the address option to create the resource with wanted IP address.

* Support for PNIC-IP option and primary_ipv4_address property in network-interface option for the `bare-metal-server-create` command was removed. Use primary_ip property in network-interface option and pnic-rip-address option to create the bare metal server with wanted IP address.

* Support for IP option for the `bare-metal-server-network-interface-create` command was removed. Use address option to create the bare-metal-server-network-interface with wanted IP address.

## v3.5.0
{: #v3.5.0}

Version 3.5.0 was released on 2022-03-25.

### New commands

* N/A

### Updated commands

* Update `load-balancer-listener-create`,`load-balancer-listener-update`, `load-balancer-pool-create` and `load-balancer-pool-update` commands to support UDP protocol.

### Removed commands

* N/A

## v3.4.0
{: #v3.4.0}

Version 3.4.0 was released on 2022-02-24.

### New commands

* N/A

### Updated commands

* Update `instance-create`, `instance-update`, `instance-template-create`, `instance-template-create-override-source-template` and `instance-create-from-template` commands to support metadata service.

* Update `instance-create` and `instance-create-from-template` commands to support trusted profile.

### Removed commands

* N/A

## v3.3.0
{: #v3.3.0}

Version 3.3.0 was released on 2022-02-17.

### New commands

* N/A

### Updated commands

* Update `instance-create`, `instance-update`, `instance-template-create`, `instance-template-create-override-source-template` and `instance-create-from-template`, commands to add support for vm-host-failure-policy.

### Removed commands

* N/A

## v3.2.0
{: #v3.2.0}

Version 3.2.0 was released on 2022-02-11.

### New commands

* N/A. 

### Updated commands

* Update `instance-create`, `instance-update` and `volume-update` commands to support resize boot volume.

### Removed commands

* N/A

## v3.1.0
{: #v3.1.0}

Version 3.1.0 was released on 2022-01-28.

### New commands

* Add bare metal server commands `bare-metal-server`, `bare-metal-server-console`, `bare-metal-server-create`, `bare-metal-server-delete`, `bare-metal-server-disk`, `bare-metal-server-disk-update`, `bare-metal-server-disks`, `bare-metal-server-initialization-values`, `bare-metal-server-network-interface`, `bare-metal-server-network-interface-create`, `bare-metal-server-network-interface-delete`, `bare-metal-server-network-interface-floating-ip`, `bare-metal-server-network-interface-floating-ip-add`, `bare-metal-server-network-interface-floating-ip-remove`, `bare-metal-server-network-interface-floating-ips`, `bare-metal-server-network-interface-update`, `bare-metal-server-network-interfaces`, `bare-metal-server-profile`, `bare-metal-server-profiles`, `bare-metal-server-restart`, `bare-metal-server-start`, `bare-metal-server-stop`, `bare-metal-server-update` and `bare-metal-servers`. 

### Updated commands

* Update `load-balancer-listener-create` and `load-balancer-listener-update` commands for public network load balancer listener port range support.

### Removed commands

* N/A

## v3.0.0
{: #v3.0.0}

Version 3.0.0 was released on 2022-01-19.

### New commands

* N/A

### Updated commands

* Update `security-group-target`, `security-group-target-add`, `security-group-target-remove`, and `endpoint-gateway-create` commands to add security group support for endpoint-gateway.

### Removed commands

* N/A

### Note

* Removed the support for creation of load balancer listener with port and protocol as arguments.

## v2.1.0
{: #v2.1.0}

Version 2.1.0 was released on 2021-11-29.

### New commands

* N/A

### Updated commands

* Update `vpn-server-update` command to support VPN server upgrade and downgrade.

### Removed commands

* N/A

### Note

* Linux_S390x build support added.

## v2.0.0
{: #v2.0.0}

Version 2.0.0 was released on 2021-11-18.

### New commands

* N/A

### Updated commands

* Update instance commands with "by name" support. Instance commands include instance-initialization-values, instance-console, instance-create, instance-create-from-template, instance-delete, instance-disk, instance-disk-update, instance-disks, instance-network-interface, instance-network-interface-create, instance-network-interface-delete, instance-network-interface-floating-ip, instance-network-interface-floating-ip-add, instance-network-interface-floating-ip-remove, instance-network-interface-floating-ips, instance-network-interface-update, instance-network-interfaces, instance-reboot, instance-stop, instance-update, instance-volume-attachments, instance-volume-attachment, instance-volume-attachment-add, instance-volume-attachment-detach, instance-volume-attachment-update, instance-template, instance-template-create, instance-template-create-override-source-template, instance-template-update, instance-group, instance-group-create, instance-group-update, instance-group-delete, instance-group-load-balancer-delete, instance-group-managers, instance-group-manager-create, instance-group-manager-update, instance-group-manager-delete, instance-group-manager-actions, instance-group-manager-action-create, instance-group-manager-action-update, instance-group-manager-action-delete, instance-group-manager-policies, instance-group-manager-policy, instance-group-manager-policy-create, instance-group-manager-policy-update, instance-group-membership, instance-group-membership-delete, instance-group-membership-update, instance-group-memberships, instance-group-memberships-delete commands with "by name" support. Instance commands can now use an ID or name for the command option values.

### Removed commands

* N/A

## v1.7.0
{: #v1.7.0}

Version 1.7.0 was released on 2021-10-07.

### New commands

* N/A

### Updated commands

* Update load-balancer, vpc-routing-table-route-create, snapshots, vpn-gateway and vpn-server commands with "by name" support. These commands can now use an ID or name for the command option values.

### Removed commands

* N/A

## v1.6.0
{: #v1.6.0}

Version 1.6.0 was released on 2021-09-15.

### New commands

* N/A

### Updated commands

* Update `load-balancer-create/load-balancer-listener-create/load-balancer-update/load-balancer-listener-update` commands to support the load-balancer vnf support.
* Update subnet, public gateway, image, floating IP, key, placement-group, flow-log, security group, virtual private endpoint gateway, dedicated host and volume commands with "by name" support. These commands can now use an ID or name for the command option values.

### Removed commands

* N/A

## v1.5.0
{: #v1.5.0}

Version 1.5.0 was released on 2021-08-27.

### New commands

* N/A

### Updated commands

* Update `instance-create/instance-update/instance-template-create` commands to support the instance attached block storage bandwidth setting.

### Removed commands

* N/A

## v1.4.0
{: #v1.4.0}

Version 1.4.0 was released on 2021-08-26.

### New commands

* Add client-to-site VPN server commands (Beta).

### Updated commands

* Update `vpc/address-prefix/routing-table/route` commands with "by name" support. These commands can now use an ID or name for the command option values.
 
* Update network ACL and network ACL rule commands with "by name" support. These commands can now use an ID or name for the command option values.

### Removed commands

* N/A

## v1.3.0
{: #v1.3.0}

Version 1.3.0 was released on 2021-08-19.

### New commands

N/A
### Updated commands

* Update `ibmcloud is load-balancer-listener-create`, `ibmcloud is load-balancer-listener-update`, `ibmcloud is load-balancer-listener-policy-create`, `ibmcloud is load-balancer-listener-policy-update` commands for load balancer https redirect support.
* Update `ibmcloud is volume-update` for volume adjustable IOPS feature.


### Removed commands

* N/A

## v1.2.0
{: #v1.2.0}

Version 1.2.0 was released on 2021-07-27.

### New commands

* `ibmcloud is placement-groups` command to list placement groups.
* `ibmcloud is placement-group` command to get placement group.
* `ibmcloud is placement-group-create` command to create placement group.
* `ibmcloud is placement-group-update` command to update placement group.
* `ibmcloud is placement-group-delete` command to delete placement group.

### Updated commands

* Update `ibmcloud is instance-create` command with new `--placement-group` option, user can select the instance placement target with the specified placement group.
* Update `ibmcloud is instance` command to show the placement group as the placement target if the instance is created with the specific placement group.

### Removed commands

* N/A

## v1.1.0
{: #v1.1.0}

Version 1.0.0 was released on 2021-07-16.

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
