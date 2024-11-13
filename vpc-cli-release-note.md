---

copyright:
  years: 2020, 2024
lastupdated: "2024-11-13"

---

{{site.data.keyword.attribute-definition-list}}

# VPC CLI release notes
{: #vpc-cli-rn}

The following release notes are for the {{site.data.keyword.vpc_full}} (VPC) command line interface (CLI).
{: shortdesc}

## v11.13.0
{: #v11.13.0}

Version 11.13.0 was released on 2024-11-13.

### New commands

* New commands `private-path-service-gateways`, `private-path-service-gateway`, `private-path-service-gateway-create`, `private-path-service-gateway-update`, `private-path-service-gateway-delete`, `private-path-service-gateway-publish`, 
`private-path-service-gateway-unpublish`  are added for private path service gateway.
* New commands `private-path-service-gateway-account-policy-create`, `private-path-service-gateway-account-policies`, `private-path-service-gateway-account-policy`, `private-path-service-gateway-account-policy-update`, `private-path-service-gateway-account-policy-delete` are added for private path service gateway account policies.
* New commands `private-path-service-gateway-endpoint-gateway-bindings`, `private-path-service-gateway-endpoint-gateway-binding`, `private-path-service-gateway-endpoint-gateway-binding-deny`, `private-path-service-gateway-endpoint-gateway-binding-permit`, `private-path-service-gateway-endpoint-gateway-binding-revoke` are added for private path service gateway endpoint binding.

### Updated commands

- LOAD_BALANCER_ACCESS_TYPE `private-path` is added to `load-balancer-create` command.
- `--target-type` flag is introduced in `endpoint-gateway-create` command.

### Removed commands

* N/A

## v11.12.0
{: #v11.12.0}

Version 11.12.0 was released on 2024-10-30.

### New commands

* N/A

### Updated commands

- The `--classic-access` flag is deprecated in the `vpc-create` and `vpcs` commands.
- Added support for more filters across list commands of multiple resources as specified in the VPC API specification.

### Removed commands

* N/A

## v11.11.0
{: #v11.11.0}

Version 11.11.0 was released on 2024-10-16.

### New commands

* N/A

### Updated commands

* Added support for distribute-traffic in `vpn-gateway-connection-create` and `vpn-gateway-connection-update` commands

### Removed commands

* N/A

## v11.10.0
{: #v11.10.0}

Version 11.10.0 was released on 2024-10-08.

### New commands

* N/A

### Updated commands

* N/A

### Removed commands

* N/A

### Notes

* No functional changes in this release - contains internal bug fixes.

## v11.9.0
{: #v11.9.0}

Version 11.9.0 was released on 2024-09-23.

### New commands

* N/A

### Updated commands

* Flag `--rt` in commands `subnet-rtr`, `subnet-create` now accepts `crn` of the routing table.

### Removed commands

* N/A

### Notes

* N/A

## v11.8.0
{: #v11.8.0}

Version 11.8.0 was released on 2024-09-06.

### New commands

* N/A

### Updated commands

* Added support for data center and universal names in the `zone` and `zones` commands.

### Removed commands

* N/A

### Notes

* N/A

## v11.6.0
{: #v11.6.0}

Version 11.6.0 was released on 2024-08-27.

### New commands

* N/A

### Updated commands

* N/A

### Removed commands

* N/A

### Notes

* Bug fixes

## v11.5.0
{: #v11.5.0}

Version 11.5.0 was released on 2024-07-18.

### New commands

* New command `ibmcloud is bare-metal-server-initialization-replace` added for bare metal server reintialization.

### Updated commands

* N/A

### Removed commands

* N/A

### Notes

* N/A

## v11.4.1
{: #v11.4.1}

Version 11.4.1 was released on 2024-06-21.

### New commands

* New commands `share-accessor-bindings`, `share-accessor-binding` and `share-accessor-binding-delete` are added to manage file share accessor bindings.

### Updated commands

* Added support for allowed-transit-encryption-modes in `share-create`, `share-update`, `share-replica-create` commands.
* Added support for origin-share in `share-create` command.
* Added support for bandwidth in `bare-metal-server-create` and `bare-metal-server-update` commands.

### Removed commands

* N/A

### Notes

* N/A

## v11.3.0
{: #v11.3.0}

Version 11.3.0 was released on 2024-05-30.

### New commands

* N/A

### Updated commands

* Added support for user-data-format in `images` command.
* Added support for catalog-offering-plan in `instance-create`, `instance-create-from-template`, `instance-template-create`, and `instance-template-create-override-source-template` commands.

### Removed commands

* N/A

### Notes

* N/A

## v11.2.0
{: #v11.2.0}

Version 11.2.0 was released on 2024-05-24.

### New commands

* New command `bare-metal-server-firmware-update` is introduced to support bare metal server firmware update.

### Updated commands

* Added support for protocol-state-filtering-mode in `virtual-network-interface-create`, `virtual-network-interface-update`, and `share-mount-target-create` commands.
* Added support for pnac-vni-psfm in `instance-create`, `instance-create-from-template`, `bare-metal-server-create`, `instance-template-create`, and `instance-template-create-override-source-template` commands.
* Added support for vni-psfm in `instance-network-attachment-create` and `bare-metal-server-network-attachment-create` commands.

### Removed commands

* N/A

### Notes

* N/A

## v11.1.0
{: #v11.1.0}

Version 11.1.0 was released on 2024-05-16.

### New commands

* N/A

### Updated commands

* The `security-group-rule-add` and `security-group-rule-update` commands now support `--local`.

### Removed commands

* N/A

### Notes

* N/A

## v11.0.0
{: #v11.0.0}

Version 11.0.0 was released on 2024-05-02.

### New commands

* N/A

### Updated commands

- The `--peer-cidr` and `--local-cidr` flags are now optional in the `vpn-gateway-connection-create` command.
- The `vpn-gateway-connection-create` command now supports `--local-ike-identity-type`, `--local-ike-identity-value`, `--local-ike-identities`, `--peer-ike-identity-type`, `--peer-ike-identity-value`, and `--establish-mode`.
- The `vpn-gateway-connection-update` command now supports `--peer-fqdn` and `--establish-mode`.
- The `vpn-gateway-connection-local-cidr-add`, `vpn-gateway-connection-local-cidr-delete`, `vpn-gateway-connection-peer-cidr-add`, and `vpn-gateway-connection-peer-cidr-delete` commands now support `CIDR` (`PREFIX_ADDRESS/PREFIX_LENGTH`) as a single argument. This change means that using `PREFIX_ADDRESS` and `PREFIX_LENGTH` as separate arguments is now deprecated.
- The `PEER_ADDRESS` argument in the `vpn-gateway-connection-create` command was renamed to `PEER`, which accepts both IP address and FQDN.
- The `reservations` command now supports `resource-group-name` and `all-resource-groups` filter.
- The `instances` command now supports the reservation filter.

### Removed commands

* N/A

### Notes

The previous plug-in versions up to 10.2.0 are compatible with the older API response and are available to download for six months. However, we recommend that you upgrade the plug-in to version 11.0.0 to use the most recent VPN gateway connection capabilities. We also suggest that you update the scripts according to the new API response.

### Breaking Changes

- The `vpn-gateway-connection-local-cidr-add`, `vpn-gateway-connection-local-cidr-delete`, `vpn-gateway-connection-peer-cidr-add`, and `vpn-gateway-connection-peer-cidr-delete` commands now support `CIDR` (`PREFIX_ADDRESS/PREFIX_LENGTH`) as a single argument. This means that using `PREFIX_ADDRESS` and `PREFIX_LENGTH` as separate arguments is now deprecated. The depricated arguments are removed within 6 months or in a major release.
	- On or before `10.2.0` plugin version.
		`ibmcloud is vpn-gateway-connection-local-cidr-add 0726-59be5c84-1dc2-4191-b591-d506514563bf 0726-0d642e87-b868-4a22-83f4-a35a19390b5c 1.168.0.0 22`
	- On or after `11.0.0` plugin version.
		`ibmcloud is vpn-gateway-connection-local-cidr-add 0726-59be5c84-1dc2-4191-b591-d506514563bf 0726-0d642e87-b868-4a22-83f4-a35a19390b5c 1.168.0.0/22`

- Significant changes in the JSON output of several commands were made. Specifically, the `ike-connections`, `ipsec-connections`, `vpn-gateway-connections`, `vpn-gateway-connection`, `vpn-gateway-connection-create`, and `vpn-gateway-connection-update` commands now use a new property called `peer` instead of the previous `peer_address`. The `peer` property has two subproperties: `address` and `fqdn`, and it's crucial to check the `peer.type` property in the response to know which subproperty to use. If the type is `address`, then the response has `peer.address`. Conversely, if the type is `fqdn`, then the response has `peer.fqdn`.

## v10.2.0
{: #v10.2.0}

Version 10.2.0 was released on 2024-04-22.

### New commands

* N/A

### Updated commands

* N/A

### Removed commands

* N/A

### Notes

* Added support for resource-group-name and all-resource-groups filter introduced in `list reservations` command.
* Added support for reservation filter introduced in `instances` command.

## v10.1.0
{: #v10.1.0}

Version 10.1.0 was released on 2024-03-21.

### New commands

* New commands `vpc-dns-resolution-binding-create`, `vpc-dns-resolution-binding`, `vpc-dns-resolution-binding-update`, `vpc-dns-resolution-binding-delete` and `vpc-dns-resolution-bindings` are introduced to support VPC DNS resolution binding.
* New commands `reservation-create`, `reservation-update`, `reservation-activate`, `reservation-delete`,`reservation` and `reservations` are introduced to support virtual server reservations.

### Updated commands

* Added support for dns-enable-hub, dns-resolver-type, and dns-resolver-manual-servers in `vpc-create` command.
* Added support for dns-enable-hub, dns-resolver-type, dns-resolver-manual-servers and delegate-to-vpc in  `vpc-update` command.
Added support for allow-dns-resolution-binding in `endpoint-gateway-create` and `endpoint-gateway-update` commands.
Added support for reservation-affinity-policy, reservation-affinity-pool in `instance-create`, `instance-create-from-template`. `instance-update`, `instance-template-create` and `instance-template-create-override-source-template` commands.

### Removed commands

* N/A

### Notes

* N/A

## v10.0.1
{: #v10.0.1}

Version 10.0.1 was released on 2024-03-12.

### New commands

* N/A

### Updated commands

* N/A

### Removed commands

* N/A

### Notes

* Fixed `subnet-reserved-ip-create` command, made `endpoint_gateway` as default value for `trt` flag.

## v10.0.0
{: #v10.0.0}

Version 10.0.0 was released on 2024-03-12.

### New commands

* New commands `virtual-network-interface-create`, `virtual-network-interface-delete`, `virtual-network-interface-floating-ip`, `virtual-network-interface-floating-ips`, `virtual-network-interface-floating-ip-add`, `virtual-network-interface-floating-ip-remove`, `virtual-network-interface-reserved-ip`, `virtual-network-interface-reserved-ips`, `virtual-network-interface-reserved-ip-bind` and `virtual-network-interface-reserved-ip-unbind` are introduced to support Virtual Network Interface as a Service.
* New commands `instance-network-attachments`, `instance-network-attachment`, `instance-network-attachment-create`, `instance-network-attachment-update` and `instance-network-attachment-delete` are introduced to support instance network attachments.
* New commands `bare-metal-server-network-attachments`, `bare-metal-server-network-attachment`, `bare-metal-server-network-attachment-create`, `bare-metal-server-network-attachment-update`, `bare-metal-server-network-attachment-update` and `bare-metal-server-network-attachment-delete` are introduced to support bare metal network attachments.

### Updated commands

* Added support for the VNI in the `floating-ip-reserve` and `floating-ip-update` commands.
* Added support for the VNI and NAC in the `flow-log-create` command.
* Added support for the VPC filter in the `security-groups` command.
* Added support for the TRT in the `subnet-reserved-ip-create` command.
* Added support for allow-ip-spoofing, auto-delete, and enable-infrastructure-nat in the `virtual-network-interface-update` command.
* Added support for pnac-name, pnac-vni, pnac-vni-ais, pnac-vni-ein, pnac-vni-auto-delete, pnac-vni-ips, pnac-vni-name, pnac-vni-rip-address, pnac-vni-rip-auto-delete, pnac-vni-rip-name, pnac-vni-sgs, and network-attachments in the `instance-create`, `instance-create-from-template`,`instance-template-create`, and `instance-template-create-override-source-template` commands.
* Added support for pnac-name, pnac-allowed-vlans, pnac-vni, pnac-vni-subnet, pnac-vni-ais, pnac-vni-ein, pnac-vni-auto-delete, pnac-vni-ips, pnac-vni-name, pnac-vni-rip, pnac-vni-rip-address, pnac-vni-rip-auto-delete, pnac-vni-rip-name, pnac-vni-sgs, and network-attachments in `bare-metal-server-create` command.
* Added support for VNI and vni-auto-delete in the `share-mount-target-create` command.

### Removed commands

* N/A

### Breaking Change Notes

* In the past, when a Virtual Server Instance (VSI) was provisioned without explicitly mentioning the `--primary-network-interface` (legacy interface), a `primary_network_interface` was created and the same details were available in the response. However, with the 10.0.0 and later releases, when a virtual server instance is provisioned without explicitly mentioning `--primary-network-interface`, a `primary_network_attachment` is created, along with a Virtual Network Interface (VNI) resource.
* To support compatibility with an eariler version, users need to explicitly define `--primary-network-interface` to create a legacy network interface. It is recommended to use `primary_network_attachment` over the legacy `primary_network_interface`.

## v9.0.3
{: #v9.0.3}

Version 9.0.3 was released on 2024-02-12.

### New commands

* N/A

### Updated commands

* N/A

### Removed commands

* N/A

### Notes

* Fixed `private-path-service-gateway-update` command to enable or disable `published` flag.

## v9.0.2
{: #v9.0.2}

Version 9.0.2 was released on 2024-01-19.

### New commands

* N/A

### Updated commands

* N/A

### Removed commands

* N/A

### Notes

* Fixed `vpc-routing-table-update` command to support `clean-all-advertise-routes-to-sources` flag.

## v9.0.1
{: #v9.0.1}

Version 9.0.1 was released on 2024-01-05.

### New commands

* N/A

### Updated commands

* N/A

### Removed commands

* N/A

### Notes

* Fixed `backup-policy-create` command, made `name` flag as optional and added support for instance in `match_resource_type` flag.
* Fixed `backup-policy-jobs` command pagination issue.
* Fixed `share-mount-target-create` command with `vpc` field issue.
* Fixed `flow-log-create` command with index out of bound error.
* Fixed `instance-create --interactive` command issue on optional name for SSH keys.

## v9.0.0
{: #v9.0.0}

Version 9.0.0 was released on 2023-12-14.

### New commands

* N/A

### Updated commands

* Added support for advertise-routes-to in `vpc-routing-table-create` and `vpc-routing-table-update` commands.
* Added support for advertise in `vpc-routing-table-route-create` and `vpc-routing-table-route-update` commands.
* Added support for file share cross region in `share-replica-create` command

### Removed commands

* N/A

### Notes

* N/A

## v8.2.0
{: #v8.2.0}

Version 8.2.0 was released on 2023-12-05.

### New commands

* New commands `snapshot-consistency-group`, `snapshot-consistency-group-create`, `snapshot-consistency-group-delete`, `snapshot-consistency-group-update`, `snapshot-consistency-groups` are introduced to support multivolume snapshots.

### Updated commands

* Added support for included_content and match_resource_type in `backup-policy-create` command.

### Removed commands

* N/A

### Notes

* N/A

## v8.1.0
{: #v8.1.0}

Version 8.1.0 was released on 2023-10-18.

### New commands

* N/A

### Updated commands

* Added support for NUMA topology and Sapphire Gen 3 profiles in the `instance`, `instance-profile`, `dedicated-host-profile` and `bare-metal-profile` commands.

### Removed commands

* N/A

### Notes

* N/A


## v8.0.0
{: #v8.0.0}

Version 8.0.0 was released on 2023-10-12.

### New commands

* N/A

### Updated commands

* Added support for diagnosing a failed VPN gateway and VPN server in the `vpn-gateway` and `vpn-server` commands. And, the `status` attribute is no longer the part of the response in `vpn-gateway` commands.

### Removed commands

* N/A

### Notes

* API Version is updated to 2023-10-10.


## v7.1.0
{: #v7.1.0}

Version 7.1.0 was released on 2023-09-22.

### New commands

* N/A

### Updated commands

* Added support for Enterprise Backup As a Service in `backup-policy-create` command.

### Removed commands

* N/A

### Notes

* N/A

## v7.0.0
{: #v7.0.0}

Version 7.0.0 was released on 2023-08-04.

### New commands

* New commands `share`, `share-create`, `share-delete`, `share-mount-target`, `share-mount-target-create`, `share-mount-target-delete`, `share-mount-target-update`, `share-mount-targets`, `share-profile`, `share-profiles`, `share-replica-create`, `share-replica-failover`, `share-replica-split`, `share-update` and `shares` are introduced to support File Share as a Service.

* New commands `virtual-network-interface`, `virtual-network-interface-update` and `virtual-network-interfaces` are introduced to support Virtual Network Interface as a Service.

### Updated commands

* Added support for Virtual Network Interface in `security-group-target`, `security-group-target-add`, `security-group-target-remove` and `security-group-targets` commands.

### Removed commands

* Removed support for `share-replica-source` command - you can get the same details from the `share` command.

### Notes

* N/A

## v6.16.1
{: #v6.16.1}

Version 6.16.1 was released on 2023-07-18.

### New commands

* N/A

### Updated commands

* N/A

### Removed commands

* N/A

### Notes

* Removed release version 6.16.0.

## v6.15.0
{: #v6.15.0}

Version 6.15.0 was released on 2023-07-11.

### New commands

* New commands `image-obsolete` and `image-deprecate` are introduced to support image lifecycle management.

### Updated commands

* Added support for image lifecycle management in `image-create`, `image-update`, and `images` commands.

### Removed commands

* N/A

### Notes

* N/A

## v6.14.1
{: #v6.14.1}

Version 6.14.1 was released on 2023-06-30.

### New commands

* N/A

### Updated commands

* N/A

### Removed commands

* N/A

### Notes

* Fixed issue with using the SSH key generated from UI in CLI.

## v6.14.0
{: #v6.14.0}

Version 6.14.0 was released on 2023-06-23.

### New commands

* N/A

### Updated commands

* Added support for more algorithms in the SSH key `key-create` command.

### Removed commands

* N/A

## v6.13.0
{: #v6.13.0}

Version 6.13.0 was released on 2023-06-22.

### New commands

* N/A

### Updated commands

* Added support for snapshot and backup cross region copy in `snaphot-create`, `snapshots`, `backup-policy-plan-create` and `backup-policy-plan-update` commands.

### Removed commands

* N/A

## v6.12.0
{: #v6.12.0}

Version 6.12.0 was released on 2023-06-01.

### New commands

* N/A

### Updated commands

* Added support for fileshare mount targets in share commands (Beta).

### Removed commands

* N/A

### Notes

* Fixed `bare-metal-server-network-interfaces`, `bare-metal-server-profiles` and `bare-metal-servers` commands to print correct response values.

## v6.11.1
{: #v6.11.1}

Version 6.11.1 was released on 2023-05-03.

### New commands

* N/A
### Updated commands

* N/A

### Removed commands

* N/A

### Notes

* Fixed `bare-metal-server-network-interfaces` and `bare-metal-server-network-interface` command to print MAC address value.

## v6.11.0
{: #v6.11.0}

Version 6.11.0 was released on 2023-04-27.

### New commands

* Added `image-export-job`, `image-export-jobs`, `image-export-job-create`, `image-export-job-update` and `image-export-job-delete` for image export functionality.

### Updated commands

* N/A

### Removed commands

* N/A

## v6.10.0
{: #v6.10.0}

Version 6.10.0 was released on 2023-03-24.

### New commands

* N/A

### Updated commands

* Updated `instance-profiles`and  `instance-profile` commands to support `network_interface_count` property in the response.
* Updated `bare-metal-server-profiles` and `bare-metal-server-profile` commands to support `network_interface_count` and `console_types` properties in the response.

### Removed commands

* N/A

## v6.9.0
{: #v6.9.0}

Version 6.9.0 was released on 2023-03-23.

### New commands

N/A

### Updated commands

* Updated `load-balancer-create` and `load-balancer-update` commands to support load balancer private DNS service.

### Removed commands

* N/A

## v6.8.0
{: #v6.8.0}

Version 6.8.0 was released on 2023-03-15.

### New commands

N/A

### Updated commands

* Updated `vpc-routing-table-route-create` and `vpc-routing-table-route-update` commands to support route priority feature.

### Removed commands

* N/A

## v6.7.2
{: #v6.7.2}

Version 6.7.2 was released on 2023-03-13.

### New commands

N/A

### Updated commands

* N/A

### Removed commands

* N/A

### Note

* Fixed `instances` list command to show the floating IP.
* Fixed `instance-volume-attachment-add` command optional field issue.

## v6.7.0
{: #v6.7.0}

Version 6.7.0 was released on 2023-03-07.

### New commands

N/A

### Updated commands

* Updated `load-balancer-listener-create`,  and `load-balancer-listener-update` commands to support load balancer idle connection timeout.
* Updated `volumes` command to support `attachment-state`, `encryption`, `operating-system-family`, `operating-system-architecture` and `zone` filters.
* Updated `instance-create` command to support instance creation from existing boot volume.

### Removed commands

* N/A

## v6.6.0
{: #v6.6.0}

Version 6.6.0 was released on 2023-02-15.

### New commands

N/A

### Updated commands

* Updated `instance-create`, `instance-create-from-template`, `instance-update`, `instance-template-create` and `instance-template-create-override-source-template` commands to support instance metadata service.

### Removed commands

* N/A

## v6.5.0
{: #v6.5.0}

Version 6.5.0 was released on 2023-02-07.

### New commands

* Added `snapshot-clone`, `snapshot-clone-create`, `snapshot-clone-delete` and `snapshot-clones`commands to support snapshot fast restore.

### Updated commands

* Updated `snapshot-create`, `backup-policy-create`, `backup-policy-plan-create` and `backup-policy-plan-update` commands to support snapshot and backup fast restore.

### Removed commands

* N/A

## v6.4.0
{: #v6.4.0}

Version 6.4.0 was released on 2023-01-31.

### New commands

* N/A

### Updated commands

* Updated `bare-metal-server-create`, `bare-metal-server-update` and `bare-metal-server` commands to support secure boot mode and TPM.

### Removed commands

* N/A


## v6.3.0
{: #v6.3.0}

Version 6.3.0 was released on 2023-01-13.

### New commands

* N/A

### Updated commands

* Updated `ike-policy-create`, `ike-policy-update`, `ipsec-policy-create` and `ipsec-policy-update` commands to remove the weak ciphers.

* Updated `vpn-server-create`, `vpn-server-update`, `load-balancer-listener-create` and `load-balancer-listener-update` commands to remove the certificate manager support.

### Removed commands

* N/A

## v6.2.0
{: #v6.2.0}

Version 6.2.0 was released on 2022-12-14.

### New commands

* N/A

### Updated commands

* Updated `volume-create` command to support creation of volume from snapshot.

### Removed commands

* N/A


## v6.1.0
{: #v6.1.0}

Version 6.1.0 was released on 2022-11-21.

### New commands

* N/A

### Updated commands

* Updated `vpc-default-routing-table`, `vpc-routing-table` , `vpc-routing-table-create`, `vpc-routing-table-update` commands to support Public Ingress Routing.

### Removed commands

* N/A



## v6.0.0
{: #v6.0.0}

Version 6.0.0 was released on 2022-11-03.

### New commands

* N/A

### Updated commands

* Updated `VPC API` version to `2022-09-13`.

### Removed commands

* N/A

### Note

* Fixed `backup-policy-job` and `backup-policy-jobs` commands to support Backup As A Service Amendment.


## v5.4.0
{: #v5.4.0}

Version 5.4.0 was released on 2022-10-06.

### New commands

* N/A

### Updated commands

* Updated `instance-create` and `instance-update` commands to support VNF Scalability.

### Removed commands

* N/A

## v5.3.0
{: #v5.3.0}

Version 5.3.0 was released on 2022-09-23.

### New commands

* Added `ibmcloud is catalog-image-offerings` and `ibmcloud is catalog-image-offering` commands to support Enterprise Image Sharing.

### Updated commands

* Updated  `instance-create` , `instance-create-from-template` , `instance-template-create` and `instance-template-create-override-source-template` commands to support Enterprise Image Sharing.
* Updated `ike-policy-create` , `ike-policy-update` , `ipsec-policy-create` and `ipsec-policy-update` commands to support Additional Cipher Suites for VPN.

### Removed commands

* N/A

## v5.2.0
{: #v5.2.0}

Version 5.2.0 was released on 2022-09-16.

### New commands

* N/A

### Updated commands

* Updated `load-balancer-update` command to support application load balancer subnet patch.

### Removed commands

* N/A

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
* Added more command examples to the [VPC CLI reference](/docs/vpc?topic=vpc-vpc-reference)
* Translation update to the command help

### Removed commands

* N/A

### Other
