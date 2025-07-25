---

copyright:
  years: 2018, 2025

lastupdated: "2025-07-15"

subcollection: vpc-infrastructure-cli-plugin

---

{{site.data.keyword.attribute-definition-list}}

# VPC CLI reference
{: #vpc-reference}

Use the following information as a reference for the command-line interface (CLI) commands that are available for {{site.data.keyword.vpc_full}} (VPC).
{: shortdesc}

This CLI reference is organized into the following sections:
* [Network commands](#network)
* [Compute commands](#compute-clis)
* [Regions and zones commands](#geography)
* [Storage commands](#storage)

## Prerequisites
{: #cli-ref-prereqs}

1. Install the [IBM Cloud CLI](/docs/cli?topic=cli-install-ibmcloud-cli){: external}.

2. Install or update the VPC infrastructure service plug-in.

   ```
   ibmcloud plugin install vpc-infrastructure
   ```
   {: pre}

   To update, use the following command:

   ```
   ibmcloud plugin update
   ```
   {: pre}

   To view installed plug-ins and versions, use the following command:

   ```
   ibmcloud plugin list
   ```
   {: pre}

---

## NETWORK COMMANDS
{: #network}

The following section provides information about CLI commands for network services.

## Floating IPs
{: #floating-ips-cli-ref}

### ibmcloud is floating-ip
{: #floating-ip-view}

View details of a floating IP.

```
ibmcloud is floating-ip FLOATING_IP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-floating-ip}

- **FLOATING_IP**: ID of the floating IP.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is floating-ip-release
{: #floating-ip-release}

Release floating IPs.

```
ibmcloud is floating-ip-release (FLOATING_IP1 FLOATING_IP2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-floating-ip-release}

- **FLOATING_IP1**: ID of the floating IP.
- **FLOATING_IP2**: ID of the floating IP.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is floating-ip-reserve
{: #floating-ip-reserve}

Reserve a floating IP.

```
ibmcloud is floating-ip-reserve FLOATING_IP_NAME (--zone ZONE_NAME | --nic TARGET_INTERFACE [--in TARGET_INSTANCE | --bm TARGET_BARE_METAL_SERVER] | --vni VNI) [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-floating-ip-reserve}

- `ibmcloud is floating-ip-reserve my-ip --zone us-south-1`
- `ibmcloud is floating-ip-reserve my-ip --nic 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is floating-ip-reserve my-ip --nic eth0 --in my-instance`
- `ibmcloud is floating-ip-reserve my-ip --nic eth0 --bm my-bm`
- `ibmcloud is floating-ip-reserve my-ip --nic 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --output JSON`
- `ibmcloud is floating-ip-reserve cli-vni-ip --vni vni2`
- `ibmcloud is floating-ip-reserve cli-vni-ip-1 --vni 7308-b81c1e13-b3a2-455c-814a-213bc9de4a90`

#### Command options
{: #command-options-floating-ip-reserve}

- **FLOATING_IP_NAME**: Name of the floating IP.
- **--zone**: Name of the target zone.
- **--nic**: The ID or name of the network interface to be bound.
- **--in**: The ID or name of the instance to be bound, this ID is only required if you use the network interface name instead of ID.
- **--bm**: The ID or name of the bare metal server to be bound, this ID is only required if you use the network interface name instead of ID.
- **--vni**: ID or name of the virtual network interface.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is floating-ip-update
{: #floating-ip-update}

Update a floating IP.

```
ibmcloud is floating-ip-update FLOATING_IP [--name NEW_NAME] [--nic TARGET_INTERFACE [--in TARGET_INSTANCE | --bm TARGET_BARE_METAL_SERVER] | --vni VNI] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-floating-ip-update}

- `ibmcloud is floating-ip-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-ip`
- `ibmcloud is floating-ip-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --nic 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is floating-ip-update my-ip --nic eth0 --in my-instance`
- `ibmcloud is floating-ip-update my-ip --nic eth0 --bm my-bm`
- `ibmcloud is floating-ip-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --nic 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --output JSON`
- `ibmcloud is floating-ip-update cli-vni-ip --name cli-vni-ip-2 --vni vni2`
- `ibmcloud is floating-ip-update cli-vni-ip-1 --name cli-vni-ip-3 --vni 7308-b81c1e13-b3a2-455c-814a-213bc9de4a90`

#### Command options
{: #command-options-floating-ip-update}

- **FLOATING_IP**: ID of the floating IP.
- **--name**: New name of the floating IP.
- **--nic**: The ID or name of the network interface to be bound.
- **--in**: The ID or name of the instance to be bound, this ID is only required if you use the network interface name instead of the ID.
- **--bm**: The ID or name of the bare metal server to be bound, this ID is only required if you use the network interface name instead of the ID.
- **--vni**: ID or name of the virtual network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is floating-ips
{: #floating-ips-list}

List all floating IPs.

```
ibmcloud is floating-ips [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-floating-ips}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Flow logs
{: #flow-logs-cli-ref}

### ibmcloud is flow-log-create
{: #flow-log-create}

Create a flow log.

```
ibmcloud is flow-log-create --bucket STORAGE_BUCKET_NAME --target TARGET_IDOrName [--target-type vpc | subnet | instance | nic | vni | nac] [--vpc VPC] [--in IN] [--name NAME] [--active TRUE | FALSE] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-flow-log-create}

- `ibmcloud is flow-log-create --bucket bucket-name --target 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is flow-log-create --bucket bucket-name --target 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-flow-log`
- `ibmcloud is flow-log-create --bucket bucket-name --target 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-flow-log --active false`
- `ibmcloud is flow-log-create --bucket bucket-name --target 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-flow-log --output JSON`
- `ibmcloud is flow-log-create --bucket bucket-name --target my-vpc --target-type vpc --name my-flow-log`
- `ibmcloud is flow-log-create --bucket bucket-name --target my-vpc --target-type vpc --name my-flow-log --active false`
- `ibmcloud is flow-log-create --bucket bucket-name --target my-vpc --target-type vpc --name my-flow-log --output JSON`
- `ibmcloud is flow-log-create --bucket bucket-name --target my-subnet --target-type subnet`
- `ibmcloud is flow-log-create --bucket bucket-name --target my-subnet --target-type subnet --vpc my-vpc`
- `ibmcloud is flow-log-create --bucket bucket-name --target my-subnet --target-type subnet --name my-flow-log`
- `ibmcloud is flow-log-create --bucket bucket-name --target my-subnet --target-type subnet --vpc my-vpc --name my-flow-log`
- `ibmcloud is flow-log-create --bucket bucket-name --target my-instance --target-type instance`
- `ibmcloud is flow-log-create --bucket bucket-name --target my-instance --target-type instance --name my-flow-log`
- `ibmcloud is flow-log-create --bucket bucket-name --target my-network-interface --target-type nic`
- `ibmcloud is flow-log-create --bucket bucket-name --target my-network-interface --target-type nic --name my-flow-log`
- `ibmcloud is flow-log-create --bucket bucket-name --target my-network-interface --target-type nic --in my-instance`
- `ibmcloud is flow-log-create --bucket bucket-name --target my-network-interface --target-type nic --in my-instance --name my-flow-log`
- `ibmcloud is flow-log-create --bucket cli-bucket-1 --target 7308-3e36540f-9572-4fd5-9b53-c9a1122d3d28 --target-type vni`
- `ibmcloud is flow-log-create --bucket cli-bucket-1 --target unworn-daintily-travesty-myself --target-type vni`

#### Command options
{: #command-options-flow-log-create}

- **--bucket**: Name of COS bucket.
- **--target**: Target ID or name for flow log.
- **--target-type**: Target type for flow log. This option is only required if target is passed as name of the resource. One of: **vpc**, **subnet**, **instance**, **nic**, **vni**, **nac**.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--in**: ID or name of the INSTANCE. It is required only to specify the unique resource by name inside this INSTANCE.
- **--name**: New name for the flow log.
- **--active**: Indicates whether this collector is active. One of: **TRUE**, **FALSE**.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is flow-log-delete
{: #flow-log-delete}

Delete one or more flow logs.

```
ibmcloud is flow-log-delete (FLOW_LOG1 FLOW_LOG2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-flow-log-delete}

- **FLOW_LOG1**: ID or name of the flow log.
- **FLOW_LOG2**: ID or name of the flow log.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is flow-log-update
{: #flow-log-update}

Update a flow log.

```
ibmcloud is flow-log-update FLOW_LOG [--name NEW_NAME] [--active TRUE | FALSE] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-flow-log-update}

- `ibmcloud is flow-log-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name-flow-log`
- `ibmcloud is flow-log-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name renamed-flow-log --active false`
- `ibmcloud is flow-log-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name renamed-flow-log --output JSON`
- `ibmcloud is flow-log-update my-flow-log --name new-name-flow-log`
- `ibmcloud is flow-log-update my-flowlog --name new-name-flow-log --active false`
- `ibmcloud is flow-log-update my-flowlog --name new-name-flow-log --output JSON`

#### Command options
{: #command-options-flow-log-update}

- **FLOW_LOG**: ID or name of the flow log.
- **--name**: New name of the flow log.
- **--active**: Indicates whether this collector is active. Updating to false deactivates the collector and updating to true activates the collector. One of: **TRUE**, **FALSE**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is flow-log
{: #flow-log-view}

View details of a flow log.

```
ibmcloud is flow-log FLOW_LOG [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-flow-log}

- **FLOW_LOG**: ID or name of the flow log.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is flow-logs
{: #flow-logs-list}

List all flow logs in the region.

```
ibmcloud is flow-logs [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--vpc VPC] [--target TARGET] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-flow-logs}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--vpc**: ID, name, or CRN of the VPC.
- **--target**: The ID or resource type of the target.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Load balancers
{: #lb-anchor}

The following section provides information about CLI commands for working with load balancers, listeners, and pools.

### ibmcloud is load-balancer
{: #load-balancer-view}

View details of a load balancer.

```
ibmcloud is load-balancer LOAD_BALANCER [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-create
{: #load-balancer-create}

Create a load balancer.

```
ibmcloud is load-balancer-create LOAD_BALANCER_NAME LOAD_BALANCER_ACCESS_TYPE (--subnet SUBNET1 --subnet SUBNET2 ... [--vpc VPC]) (--dns-instance-crn DNS_INSTANCE_CRN --dns-zone-id DNS_ZONE_ID) [--family application | network] [--route-mode false | true] [--sg SG] [--logging-datapath-active false | true] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--pools POOLS_JSON | @POOLS_JSON_FILE] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-create}

- `ibmcloud is load-balancer-create my-lb public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e`
- `ibmcloud is load-balancer-create my-lb public --subnet my-subnet --subnet my-subnet2`
- `ibmcloud is load-balancer-create my-lb public --subnet my-subnet --vpc my-vpc`
- `ibmcloud is load-balancer-create my-nlb public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --family network`
- `ibmcloud is load-balancer-create my-lb public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --resource-group-id fee82deba12e4c0fb69c3b09d1f12345`
- `ibmcloud is load-balancer-create my-lb public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --resource-group-name Default`
- `ibmcloud is load-balancer-create my-lb public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --output JSON`
- `ibmcloud is load-balancer-create my-lb public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --sg 3428abaa-788b-439b-9404-ca386f2f3f79,f0e26f91-851a-4fc9-b32b-da24ad218b4e`
- `ibmcloud is load-balancer-create my-lb public --subnet my-subnet --sg my-sg1,my-sg2 --vpc my-vpc`
- `ibmcloud is load-balancer-create my-lb public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --logging-datapath-active true`
- `ibmcloud is load-balancer-create my-lb public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --pools '[{"algorithm": "round_robin", "protocol": "tcp", "health_monitor": {"delay": 2, "max_retries": 2, "type": "tcp", "timeout": 1}}]'`
Create a load balancer with pools
- `ibmcloud is load-balancer-create my-lb private --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --family network --route-mode true`
Create a load balancer with route mode enabled
- `ibmcloud is load-balancer-create my-lb private-path --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --family network`
Create a Private Path network load balancer.
- `ibmcloud is load-balancer-create my-nlb private-path --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --family network --pools '[{"algorithm":"round_robin","protocol":"tcp","health_monitor":{"delay":2,"max_retries":2,"type":"tcp","timeout":1},"members":[{"port":8080,"target":{"id":"72251a2e-d6c5-42b4-97b0-b5f8e8d1f478"}}]}]'`
Create a Private Path network load balancer with the application load balancer ID as the pool member target.
- `ibmcloud is load-balancer-create my-nlb private-path --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --family network --pools '[{"algorithm":"round_robin","protocol":"tcp","health_monitor":{"delay":2,"max_retries":2,"type":"tcp","timeout":1},"members":[{"port":8080,"target":{"name":"my-lb-name","target_type":"load_balancer"}}]}]'`
Create a Private Path network load balancer with the application load balancer name as the pool member target.
- `ibmcloud is load-balancer-create my-lb public --subnet cli-subnet-1 --family network --route-mode true --dns-instance-crn crn:v1:staging:public:dns-svcs:global:a/efe5afc483594adaa8325e2b4d1290df:1bbaacf9-7bc7-4d64-a1d8-a8d1ca9e7662:: --dns-zone-id 5cca0d1c-9c85-4a18-bc07-a9f070949698`
Create private DNS support for a load balancer.

#### Command options
{: #command-options-load-balancer-create}

- **LOAD_BALANCER_NAME**: Name of the load balancer.
- **LOAD_BALANCER_ACCESS_TYPE**: Access type of the load balancer. Only the load balancer in the network family supports 'private-path' access type. One of: **public**, **private**, **private-path**.
- **--subnet**: ID or name of the subnets to provision this load balancer. This option can be specified multiple times to provision load balancer in multiple subnets. Only one subnet can be specified for network load balancer.
- **--vpc**: ID or name of the VPC. This ID or name is required only to specify the unique subnet by name inside this VPC.
- **--family**: The load balancer family type. One of: **application**, **network**.
- **--route-mode**: Enable or disable route mode for the load balancer. If unspecified, route mode is disabled. Currently, route mode can be enabled for only private network load balancer. One of: **false**, **true**.
- **--sg**: Comma-separated security group IDs or names for the load balancer. If unspecified, the VPC's default security group is used.
- **--logging-datapath-active**: Enable or disable datapath logging for this load balancer. If unspecified, datapath logging is disabled. Datapath logging is applicable only for application load balancer. One of: **false**, **true**.
- **--dns-instance-crn**: The CRN of the DNS instance that is associated with the DNS zone.
- **--dns-zone-id**: ID of the DNS Zone.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--pools**: POOLS_JSON|@POOLS_JSON_FILE, pools in JSON or JSON file One of: **POOLS_JSON**, **@POOLS_JSON_FILE**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-delete
{: #load-balancer-delete}

Delete one or more load balancers.

```
ibmcloud is load-balancer-delete (LOAD_BALANCER1 LOAD_BALANCER2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-delete}

- **LOAD_BALANCER1**: ID or name of the load balancer.
- **LOAD_BALANCER2**: ID or name of the load balancer.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener
{: #load-balancer-listener-view}

View details of a load balancer listener.

```
ibmcloud is load-balancer-listener LOAD_BALANCER LISTENER_ID [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-create
{: #load-balancer-listener-create}

Create a load balancer listener.

```
ibmcloud is load-balancer-listener-create LOAD_BALANCER (--protocol http | https | tcp | udp) [--vpc VPC] [--port PORT | --port-min PORT_MIN --port-max PORT_MAX] [--default-pool DEFAULT_POOL_ID] [--connection-limit LIMIT] [--certificate-instance-crn CERTIFICATE_INSTANCE_CRN] [--policies LISTENER_POLICIES_JSON | @LISTENER_POLICIES_JSON_FILE] [--accept-proxy-protocol false | true] [--http-redirect-listener-id HTTP_REDIRECT_LISTENER_ID --http-redirect-status-code 301 | 302 | 303 | 307 | 308 [--http-redirect-target-uri HTTP_REDIRECT_TARGET_URI]] [--idle-connection-timeout IDLE_CONNECTION_TIMEOUT] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-listener-create}

- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --port 443 --protocol http`
- `ibmcloud is load-balancer-listener-create my-lb --port 443 --protocol http`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --port-min 80 --port-max 85 --protocol tcp`
Create a listener for the public network load balancer with port range.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --port 443 --protocol https --certificate-instance-crn crn:v1:bluemix:public:secrets-manager:us-south:a/aa5a471f75bc456fac416bf02c4ba6de:aace9348-39da-4498-b132-e5ab918237f4:secret:e3bd96ce-1e4c-f642-d1f2-0d0ab025f510`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --port 443 --protocol http --connection-limit 2000`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --port 443 --protocol http --default-pool 70294e14-4e61-11e8-bcf4-0242ac110004`
- `ibmcloud is load-balancer-listener-create my-lb --port 443 --protocol http --default-pool my-pool`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --port 443 --protocol http  --policies '[{"name": "my-policy", "priority": 5, "action": "reject" }]'`
The priority of the policy can have a range of 1 to 10, where a lower value indicates a higher priority. The possible values for _action_ are "forward", "redirect", "reject", or "https_redirect".
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --port 443 --protocol http --policies '[{"priority": 5, "action": "forward", "target": { "id": 70294e14-4e61-11e8-bcf4-0242ac110004 }}]'`
When the action is _forward_, the pool identity is required to specify which pool the load balancer forwards the traffic to.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --port 443 --protocol http --policies '[{"priority": 5, "action": "redirect", "target": { "http_status_code": 301, "url": "https://www.redirect.com"}}]'`
When the action is _redirect_, the "url" and "http_status_code" are required. Possible values for _http_status_code_ are "301", "302", "303", "307", or "308". The "url" is the redirect target URL.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --port 443 --protocol http --policies '[{"priority": 5, "action": "reject", "rules": { "condition": "equals", "type": "header", "field": "My-app-header", "value": "value"}}]'`
Possible values for _condition_ are "contains", "equals", or "matches_regex". Possible values for _type_ are "header", "hostname", or "path". _field_ is an HTTP header field that is applicable only to the "header" rule type. The _value_ parameter is the value to match the rule condition.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --port 443 --protocol http --output JSON`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --port 443 --protocol http --accept-proxy-protocol true`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --port-min 80 --port-max 85 --protocol tcp --accept-proxy-protocol true`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --protocol tcp`
To create a load balancer listener when route mode is enabled in the load balancer.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --protocol udp --port 53`
Create a load balancer listener with UDP protocol.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --protocol https --port 443 --idle-connection-timeout 30`
Create an application load balancer listener with idle connection timeout.

#### Command options
{: #command-options-load-balancer-listener-create}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--protocol**: The listener protocol. Load balancers in the application family support `tcp`, `http`, and `https`. Load balancers in the network family support `tcp` and `udp`.
- **--port**: The listener port number. Range 1-65535.
- **--port-min**: The inclusive lesser bound of the range of ports that are used by this listener. Must not be greater than _port_max_. Currently, only load balancers that are operating with route mode are enabled and public load balancers in the _network_ family support more than one port per listener. Listeners in the load balancer with the same _protocol_ must have nonoverlapping port ranges. Range 1-65535.
- **--port-max**: The inclusive higher bound of the range of ports that are used by this listener. Must not be less than _port_min_. Currently, only load balancers that are operating with route mode enabled and public load balancers in the _network_ family support more than one port per listener. Listeners in the load balancer with the same _protocol_ must have nonoverlapping port ranges. Range 1-65535.
- **--default-pool**: ID of the default pool.
- **--connection-limit**: The maximum number of connections of the listener. This option is not applicable for the load balancers in the network family.
- **--certificate-instance-crn**: The certificate instance CRN used for SSL termination. Required when protocol is **https**. This option is not applicable for the load balancers in the network family.
- **--policies**: **LISTENER_POLICIES_JSON** | **@LISTENER_POLICIES_JSON_FILE**, listener policies in JSON or JSON file. This option is not applicable for the load balancers in the network family.
- **--accept-proxy-protocol**: If set to true, proxy protocol is enabled for this listener. Only supported for application load balancers. One of: **false**, **true**.
- **--http-redirect-listener-id**: ID of the listener that is set as the HTTP redirect target.
- **--http-redirect-status-code**: The HTTP status code that is returned in the redirect response. One of: **301**, **302**, **303**, **307**, **308**.
- **--http-redirect-target-uri**: Target URI where traffic is redirected. This setting is optional and must start with "/" if you set.
- **--idle-connection-timeout**: The idle connection timeout of the listener in seconds. Only load balancers in the **application** family support this option. Minimum: **50**, maximum: **7200**. (default: **50**).
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-delete
{: #load-balancer-listener-delete}

Delete one or more load balancer listeners.

```
ibmcloud is load-balancer-listener-delete LOAD_BALANCER (LISTENER_ID1 LISTENER_ID2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener-delete}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID1**: ID of the listener.
- **LISTENER_ID2**: ID of the listener.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policies
{: #load-balancer-listener-policies-list}

List all load balancer policies.

```
ibmcloud is load-balancer-listener-policies LOAD_BALANCER LISTENER_ID [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener-policies}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy
{: #load-balancer-listener-policy-view}

View details of load balancer listener policy.

```
ibmcloud is load-balancer-listener-policy LOAD_BALANCER LISTENER_ID POLICY [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener-policy}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY**: ID or name of the policy.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-create
{: #load-balancer-listener-policy-create}

Create a load balancer listener policy.

```
ibmcloud is load-balancer-listener-policy-create LOAD_BALANCER LISTENER_ID --priority PRIORITY (--action forward_to_pool | forward_to_listener | redirect | reject | https_redirect) [--vpc VPC] [--name NEW_NAME] [(--target-listener-id TARGET_LISTENER_ID --target-listener-http-status-code 301 | 302 | 303 | 307 | 308 [--target-uri TARGET_URI]) | (--target-http-status-code 301 | 302 | 303 | 307 | 308 --target-url TARGET_URL) | --target TARGET] [--rules LISTENER_POLICY_RULES_JSON | @LISTENER_POLICY_RULES_JSON_FILE] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-listener-policy-create}

- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-policy --action reject --priority 5`
The priority of the policy can have a range of 1 to 10, where a lower value indicates a higher priority. The possible values for _action_ are "forward", "redirect", or "reject".
- `ibmcloud is load-balancer-listener-policy-create my-lb 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-policy --action reject --priority 5`
The priority of the policy can have a range of 1 to 10, where a lower value indicates a higher priority. The possible values for _action_ are "forward", "redirect", or "reject".
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action forward_to_listener --priority 2 --target my-pool`
When the action is "forward_to_listener", the listener ID or name is required to specify which listener the load balancer forwards the traffic to.
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action forward_to_listener --priority 2 --target 70294e14-4e61-11e8-bcf4-0242ac110004`
When the action is "forward_to_listener", the listener ID or name is required to specify which listener the load balancer forwards the traffic to.
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action forward_to_pool --priority 2 --target my-pool`
When the action is "forward_to_pool", the pool ID or name is required to specify which pool the load balancer forwards the traffic to.
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action forward_to_pool --priority 2 --target 70294e14-4e61-11e8-bcf4-0242ac110004`
When the action is "forward_to_pool", the pool ID or name is required to specify which pool the load balancer forwards the traffic to.
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action redirect --priority 1 --target-http-status-code 301 --target-url "https://www.redirect.com"`
When the action is _redirect_, the "url" and "http_status_code" are required. Possible values for _http_status_code_ are "301", "302", "303", "307", or "308". The "url" is the redirect target URL.
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action redirect --priority 1 --target-http-status-code 301 --target-url "https://redirect.com:443/new/{path}?{query}"`
When the action is _redirect_, the "url" and "http_status_code" are required. Possible values for _http_status_code_ are "301", "302", "303", "307", or "308". The "url" is the redirect target URL.
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action redirect --priority 1 --target-http-status-code 301 --target-url "https://test.{host}/search?q=watson"`
When the action is _redirect_, the "url" and "http_status_code" are required. Possible values for _http_status_code_ are "301", "302", "303", "307", or "308". The "url" is the redirect target URL.
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action reject --priority 4 --rules '[{ "condition": "equals", "type": "header", "field": "My-app-header", "value": "value"}]'`
Possible values for _condition_ are "contains", "equals", or "matches_regex". Possible values for _type_ are "header", "hostname", or "path". _field_ is an HTTP header field that is applicable only to the "header" rule type. The _value_ parameter is the value to match the rule condition.
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action reject --priority 3 --name my-policy --output JSON`
- `ibmcloud is lb-lpc f5b20e9b-a77b-43e9-aa2d-a3a5ac9fe8fd 5cb08c12-004f-4587-87f4-ef46e799da50 --priority 3 --action https_redirect --target-listener-id d7e0543c-4e0f-4c0d-89aa-73f0f028ec61 --target-listener-http-status-code 303`
When the action is "https_redirect", the "target-listener-id" and "http_status_code" are required. Possible values for "http_status_code" are "301", "302", "303", "307", or "308".
- `ibmcloud is lb-lpc f5b20e9b-a77b-43e9-aa2d-a3a5ac9fe8fd 5cb08c12-004f-4587-87f4-ef46e799da50 --priority 3 --action https_redirect --target-listener-id d7e0543c-4e0f-4c0d-89aa-73f0f028ec61 --target-listener-http-status-code 307 --target-uri /example`
When the action is "https_redirect", the "target-listener-id" and "http_status_code" are required. The "uri" is the redirect target URI, it's an optional field. Possible values for "http_status_code" are "301", "302", "303", "307", or "308".

#### Command options
{: #command-options-load-balancer-listener-policy-create}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--priority**: Priority of the policy. Lesser value indicates greater priority, for example: **5**, range: [**1-10**].
- **--action**: The policy action. One of: **forward_to_pool**, **forward_to_listener**, **redirect**, **reject**, **https_redirect**.
- **--name**: The new name of the policy.
- **--target**: ID or name of the target load balancer pool that is specified with **forward_to_pool** or load balancer listener ID that is specified with **forward_to_listener** action.
- **--target-listener-id**: ID of the listener that you want to implement https-redirect on, specified with **https_redirect** action.
- **--target-listener-http-status-code**: The HTTP status code that is returned in the redirect response, specified with **https_redirect** action. One of: **301**, **302**, **303**, **307**, **308**.
- **--target-uri**: Target URI where traffic is redirected, specified with **https_redirect** action. This setting is optional and must start with "/" if you set.
- **--target-http-status-code**: The HTTP status code in the redirect response, specified with **redirect** action. One of: **301**, **302**, **303**, **307**, **308**.
- **--target-url**: The redirect target URL, specified with **redirect** action. The URL supports RFC 6570 level 1 expressions for the variables protocol, host, port, path, and query. Which expands to values from the originally requested URL (or the indicated defaults if the request did not include them).
- **--rules**: **LISTENER_POLICY_RULES_JSON** | **@LISTENER_POLICY_RULES_JSON_FILE**, listener policy rules in JSON or JSON file.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-delete
{: #load-balancer-listener-policy-delete}

Delete one or more policies from a load balancer listener.

```
ibmcloud is load-balancer-listener-policy-delete LOAD_BALANCER LISTENER_ID (POLICY1 POLICY2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener-policy-delete}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY1**: ID or name of the policy.
- **POLICY2**: ID or name of the policy.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-rule
{: #load-balancer-listener-policy-rule-view}

List single load balancer policy rule.

```
ibmcloud is load-balancer-listener-policy-rule LOAD_BALANCER LISTENER_ID POLICY RULE_ID [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener-policy-rule}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY**: ID or name of the policy.
- **RULE_ID**: ID of the rule.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-rule-create
{: #load-balancer-listener-policy-rule-create}

Create a load balancer listener policy rule.

```
ibmcloud is load-balancer-listener-policy-rule-create LOAD_BALANCER LISTENER_ID POLICY (--condition contains | equals | matches_regex) (--type header | hostname | path | query | body | sni_hostname) --value VALUE [--vpc VPC] [--field FIELD] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-listener-policy-rule-create}

- `ibmcloud is load-balancer-listener-policy-rule-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --condition equals --type header --field my-app-header --value  match-value --output JSON`
- `ibmcloud is load-balancer-listener-policy-rule-create my-lb 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 my-policy --condition equals --type header --field my-app-header --value  match-value --output JSON`

#### Command options
{: #command-options-load-balancer-listener-policy-rule-create}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY**: ID or name of the policy.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--condition**: The condition of the rule. One of: **contains**, **equals**, **matches_regex**.
- **--type**: The type of the rule. One of: **header**, **hostname**, **path**, **query**, **body**, **sni_hostname**.
- **--value**: Value to match the rule condition.
- **--field**: The HTTP field. This field is applicable to "header", "query", and "body" rule types. For rule type "header", this field is required. For rule types "query" or "body", this field is optional.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-rule-delete
{: #load-balancer-listener-policy-rule-delete}

Delete one or more policies from a load balancer listener.

```
ibmcloud is load-balancer-listener-policy-rule-delete LOAD_BALANCER LISTENER_ID POLICY (RULE_ID1 RULE_ID2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener-policy-rule-delete}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY**: ID or name of the policy.
- **RULE_ID1**: ID of the rule.
- **RULE_ID2**: ID of the rule.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-rule-update
{: #load-balancer-listener-policy-rule-update}

Update a rule of a load balancer listener policy.

```
ibmcloud is load-balancer-listener-policy-rule-update LOAD_BALANCER LISTENER_ID POLICY RULE_ID [--vpc VPC] [--condition contains | equals | matches_regex] [--type header | hostname | path | query | body | sni_hostname] [--value VALUE] [--field FIELD] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-listener-policy-rule-update}

- `ibmcloud is load-balancer-listener-policy-rule-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 70294e14-4e61-11e8-bcf4-0242ac110004 --condition equals --type header --field my-app-header --value  match-value --output JSON`
- `ibmcloud is load-balancer-listener-policy-rule-update my-lb 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 my-policy 70294e14-4e61-11e8-bcf4-0242ac110004 --condition equals --type header --field my-app-header --value  match-value --output JSON`

#### Command options
{: #command-options-load-balancer-listener-policy-rule-update}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY**: ID or name of the policy.
- **RULE_ID**: ID of the rule.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--condition**: The condition of the rule. One of: **contains**, **equals**, **matches_regex**.
- **--type**: The type of the rule. One of: **header**, **hostname**, **path**, **query**, **body**, **sni_hostname**.
- **--value**: Value to match the rule condition.
- **--field**: The HTTP field. This field is applicable to "header", "query", and "body" rule types. For rule type "header", this field is required. For rule types "query" or "body", this field is optional.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-rules
{: #load-balancer-listener-policy-rules-list}

List all load balancer policy rules.

```
ibmcloud is load-balancer-listener-policy-rules LOAD_BALANCER LISTENER_ID POLICY [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener-policy-rules}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY**: ID or name of the policy.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-update
{: #load-balancer-listener-policy-update}

Update a policy of a load balancer listener.

```
ibmcloud is load-balancer-listener-policy-update LOAD_BALANCER LISTENER_ID POLICY [--vpc VPC] [--name NEW_NAME] [--priority PRIORITY] [--target TARGET] [--target-http-status-code 301 | 302 | 303 | 307 | 308] [--target-url TARGET_URL] [--target-listener-id TARGET_LISTENER_ID --target-listener-http-status-code 301 | 302 | 303 | 307 | 308 [--target-uri TARGET_URI]] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-listener-policy-update}

- `ibmcloud is load-balancer-listener-policy-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --name my-policy --priority 5`
- `ibmcloud is load-balancer-listener-policy-update my-lb 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 my-lblp --name my-policy --priority 5`
- `ibmcloud is load-balancer-listener-policy-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --action forward --target 70294e14-4e61-11e8-bcf4-0242ac110004`
When the action is _forward_, the pool ID or name is required to specify which pool the load balancer forwards the traffic to.
- `ibmcloud is load-balancer-listener-policy-update my-lb 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 my-policy --action forward --target my-pool`
When the action is _forward_, the pool ID or name is required to specify which pool the load balancer forwards the traffic to.
- `ibmcloud is load-balancer-listener-policy-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target-http-status-code 301 --target-url "https://www.redirect.com"`
When the action is _redirect_, the "url" and "http_status_code" are required. Possible values for _http_status_code_ are "301", "302", "303", "307", or "308". The "url" is the redirect target URL.
- `ibmcloud is load-balancer-listener-policy-update r134-dd7cfd16-7a73-4921-bee2-ec9522879ac6 r134-23458256-1b39-4216-96bb-94111ed13a66 r134-59fb9ea6-c23c-4e62-887d-0dba384dc7ab --target-url  {protocol}://test.{host}:80/{path} --target-http-status-code 301`
When the action is _redirect_, the "url" and "http_status_code" are required. Possible values for _http_status_code_ are "301", "302", "303", "307", or "308". The "url" is the redirect target URL.
- `ibmcloud is load-balancer-listener-policy-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --name my-policy --output JSON`
- `ibmcloud is lb-lpu f5b20e9b-a77b-43e9-aa2d-a3a5ac9fe8fd 5cb08c12-004f-4587-87f4-ef46e799da50 c7d2c434-9202-48aa-837b-0661c4299c28 --name demo-policy --priority 2 --target-listener-id d7e0543c-4e0f-4c0d-89aa-73f0f028ec61 --target-listener-http-status-code 301`
- `ibmcloud is lb-lpu my-lb 5cb08c12-004f-4587-87f4-ef46e799da50 my-lblp --name demo-policy --priority 2 --target-listener-id d7e0543c-4e0f-4c0d-89aa-73f0f028ec61 --target-listener-http-status-code 301`
- `ibmcloud is lb-lpu f5b20e9b-a77b-43e9-aa2d-a3a5ac9fe8fd 5cb08c12-004f-4587-87f4-ef46e799da50 c7d2c434-9202-48aa-837b-0661c4299c28 --priority 2 --target-listener-id d7e0543c-4e0f-4c0d-89aa-73f0f028ec61 --target-listener-http-status-code 301 --target-uri /example2`

#### Command options
{: #command-options-load-balancer-listener-policy-update}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY**: ID or name of the policy.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--name**: The user-defined name for this policy. Policy names must be unique within the load balancer listener.
- **--priority**: Priority of the policy. Lesser value indicates greater priority, for example: **5**, range: [**1-10**].
- **--target**: ID or name of the target load balancer pool that is specified with **forward_to_pool** or load balancer listener ID that is specified with **forward_to_listener** action.
- **--target-http-status-code**: The HTTP status code in the redirect response, specified with **redirect** action. One of: **301**, **302**, **303**, **307**, **308**.
- **--target-url**: The redirect target URL, specified with **redirect** action. The URL supports RFC 6570 level 1 expressions for the variables protocol, host, port, path, and query. Which expands to values from the originally requested URL (or the indicated defaults if the request did not include them).
- **--target-listener-id**: ID of the listener that you want to implement https-redirect on, specified with **https_redirect** action.
- **--target-listener-http-status-code**: The HTTP status code that is returned in the redirect response, specified with **https_redirect** action. One of: **301**, **302**, **303**, **307**, **308**.
- **--target-uri**: Target URI where traffic is redirected, specified with **https_redirect** action. This setting is optional and must start with "/" if you set.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-update
{: #load-balancer-listener-update}

Update a load balancer listener.

```
ibmcloud is load-balancer-listener-update LOAD_BALANCER LISTENER_ID [--vpc VPC] [--protocol http | https | tcp | udp] [--port PORT | --port-min PORT_MIN --port-max PORT_MAX] [--default-pool DEFAULT_POOL_ID | --reset-default-pool] [--connection-limit LIMIT] [--certificate-instance-crn CERTIFICATE_INSTANCE_CRN] [--accept-proxy-protocol false | true] [--disable-http-redirect | (--http-redirect-listener-id HTTP_REDIRECT_LISTENER_ID --http-redirect-status-code 301 | 302 | 303 | 307 | 308 [--http-redirect-target-uri HTTP_REDIRECT_TARGET_URI | --reset-http-redirect-target-uri])] [--idle-connection-timeout IDLE_CONNECTION_TIMEOUT] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-listener-update}

- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --certificate-instance-crn crn:v1:bluemix:public:secrets-manager:us-south:a/aa5a471f75bc456fac416bf02c4ba6de:aace9348-39da-4498-b132-e5ab918237f4:secret:e3bd96ce-1e4c-f642-d1f2-0d0ab025f510`
- `ibmcloud is load-balancer-listener-update my-lb 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --certificate-instance-crn crn:v1:bluemix:public:secrets-manager:us-south:a/aa5a471f75bc456fac416bf02c4ba6de:aace9348-39da-4498-b132-e5ab918237f4:secret:e3bd96ce-1e4c-f642-d1f2-0d0ab025f510`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --connection-limit 2000`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --default-pool 70294e14-4e61-11e8-bcf4-0242ac110004`
- `ibmcloud is load-balancer-listener-update my-lb 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --default-pool my-pool`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --protocol https`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --port 222`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --output JSON`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --accept-proxy-protocol true`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --port-min 80 --port-max 85`
The range of ports that are used by this listener.
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --http-redirect-listener-id d7e0543c-4e0f-4c0d-89aa-73f0f028ec61 --http-redirect-status-code 303`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --http-redirect-listener-id d7e0543c-4e0f-4c0d-89aa-73f0f028ec61 --http-redirect-status-code 307 --http-redirect-target-uri /example2`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --disable-http-redirect`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --protocol udp`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --idle-connection-timeout 30`

#### Command options
{: #command-options-load-balancer-listener-update}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--protocol**: The listener protocol. Load balancers in the application family support `tcp`, `http`, and `https`. Load balancers in the network family support `tcp` and `udp`.
- **--port**: The listener port number. Range 1-65535.
- **--port-min**: The inclusive lesser bound of the range of ports that are used by this listener. Must not be greater than _port_max_. Currently, only load balancers that are operating with route mode are enabled and public load balancers in the _network_ family support more than one port per listener. Listeners in the load balancer with the same _protocol_ must have nonoverlapping port ranges. Range 1-65535.
- **--port-max**: The inclusive higher bound of the range of ports that are used by this listener. Must not be less than _port_min_. Currently, only load balancers that are operating with route mode enabled and public load balancers in the _network_ family support more than one port per listener. Listeners in the load balancer with the same _protocol_ must have nonoverlapping port ranges. Range 1-65535.
- **--default-pool**: ID of the default pool.
- **--reset-default-pool**: Reset default pool.
- **--connection-limit**: The maximum number of connections of the listener. This option is not applicable for the load balancers in the network family.
- **--certificate-instance-crn**: The certificate instance CRN used for SSL termination. Required when protocol is **https**. This option is not applicable for the load balancers in the network family.
- **--accept-proxy-protocol**: If set to true, proxy protocol is enabled for this listener. Only supported for application load balancers. One of: **false**, **true**.
- **--disable-http-redirect**: Enable or disable an HTTP redirect on a listener.
- **--http-redirect-listener-id**: ID of the listener that is set as the HTTP redirect target.
- **--http-redirect-status-code**: The HTTP status code that is returned in the redirect response. One of: **301**, **302**, **303**, **307**, **308**.
- **--http-redirect-target-uri**: Target URI where traffic is redirected. This setting is optional and must start with "/" if you set.
- **--reset-http-redirect-target-uri**: Reset Target URI.
- **--idle-connection-timeout**: The idle connection timeout of the listener in seconds. Only load balancers in the **application** family support this option. Minimum: **50**, maximum: **7200**. (default: **50**).
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listeners
{: #load-balancer-listeners-list}

List all load balancer listeners.

```
ibmcloud is load-balancer-listeners LOAD_BALANCER [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listeners}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool
{: #load-balancer-pool-view}

View details of a load balancer pool.

```
ibmcloud is load-balancer-pool LOAD_BALANCER POOL [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-pool}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **POOL**: ID or name of the pool.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-create
{: #load-balancer-pool-create}

Create a load balancer pool.

```
ibmcloud is load-balancer-pool-create POOL_NAME LOAD_BALANCER ALGORITHM PROTOCOL HEALTH_DELAY HEALTH_RETRIES HEALTH_TIMEOUT HEALTH_TYPE (--members MEMBERS_JSON | @MEMBERS_JSON_FILE) [--vpc VPC] [--health-monitor-url URL] [--health-monitor-port PORT] [--session-persistence-type source_ip | http_cookie | app_cookie [--session-persistence-cookie-name SESSION_PERSISTENCE_COOKIE_NAME]] [--proxy-protocol disabled | v1 | v2] [--failsafe-policy-action fail | forward | drop | bypass] [--failsafe-policy-target FAILSAFE_POLICY_TARGET] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-pool-create}

- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http`
- `ibmcloud is load-balancer-pool-create my-pool my-lb round_robin http 20 2 5 http`
- `ibmcloud is load-balancer-pool-create my-pool my-lb round_robin http 20 2 5 http --vpc my-vpc`
- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --health-monitor-url / --health-monitor-port 4001`
- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --session-persistence-type source_ip --output JSON`
- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --members '[{"port": 80, "target": { "address": "10.10.1.4"}, "weight": 20 }, {"port": 80, "target": { "address": "10.240.0.6"}, "weight": 30 }]'`
Create a application load balancer pool with members
- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin tcp 20 2 5 http --members '[{"port": 80, "target": { "id": "0736_63b9233c-812e-4d65-9ee3-fa61172afa37"}, "weight": 20 }, {"port": 80, "target": { "id": "0716_4b30a833-6f10-46a9-a4b8-13871f3559b8"}, "weight": 30 }]'`
Create a network load balancer pool with members
- `ibmcloud is load-balancer-pool-create my-pool2 my-nlb round_robin tcp 20 2 5 http --members '[{"port": 80, "target": { "name": "my-instance"}}, {"port": 80, "target": { "name": "my-instance2"}}]'`
Create a network load balancer pool with members and supply the member target by name.
- `ibmcloud is load-balancer-pool-create my-pool2 my-nlb round_robin tcp 20 2 5 http --members '[{"port":8080,"target":{"id":"72251a2e-d6c5-42b4-97b0-b5f8e8d1f478"}}]'`
Create a Private Path network load balancer with the application load balancer ID as the pool member target.
- `ibmcloud is load-balancer-pool-create my-pool2 my-nlb round_robin tcp 20 2 5 http --members '[{"port":8080,"target":{"name":"my-lb-name","target_type":"load_balancer"}}]'`
Create a Private Path network load balancer with the application load balancer name as the pool member target.
- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --proxy-protocol v1`
- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --session-persistence-type app_cookie --session-persistence-cookie-name my-cookie-name`
- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin udp 20 2 5 http`
Create a network load balancer pool for the network load balancer listener with UDP protocol.
- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --failsafe-policy-action forward --failsafe-policy-target my-lb`
Create a network load balancer pool for the network load balancer listener with a fail-safe policy.
- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --failsafe-policy-action forward --failsafe-policy-target 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
Create a network load balancer pool for the network load balancer listener with a fail-safe policy.

#### Command options
{: #command-options-load-balancer-pool-create}

- **POOL_NAME**: Name of the pool.
- **LOAD_BALANCER**: ID or name of the load balancer.
- **ALGORITHM**: The load balancing algorithm. One of: **round_robin**, **weighted_round_robin**, **least_connections**.
- **PROTOCOL**: The pool protocol. Load balancers in the application family support `tcp`, `http`, and `https`. Load balancers in the network family support `tcp` and `udp`.
- **HEALTH_DELAY**: The health check interval in seconds. The interval must be greater than the timeout value. Minimum: **2**, maximum: **60**.
- **HEALTH_RETRIES**: The health check maximum retries. Minimum: **1**, maximum: **10**.
- **HEALTH_TIMEOUT**: The health check timeout in seconds. Minimum: **1**, maximum: **59**.
- **HEALTH_TYPE**: The health check protocol. Load balancers in the application family support `tcp`, `http`, and `https`. Load balancers in the network family support `tcp` and `http`.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--health-monitor-url**: The health check URL path. Applicable only if the **HEALTH_TYPE** is http or https.
- **--health-monitor-port**: The health check port number. If specified, the specified ports in the server member resources are overridden.
- **--session-persistence-type**: The session persistence type. One of: **source_ip**, **http_cookie**, **app_cookie**.
- **--session-persistence-cookie-name**: Session persistence cookie name. This option is applicable only to **app_cookie** type.
- **--proxy-protocol**: The proxy protocol setting for this pool. Proxy protocol is supported only for application load balancers. One of: **disabled**, **v1**, **v2**.
- **--members**: MEMBERS_JSON|@MEMBERS_JSON_FILE, members in JSON or JSON file.
- **--failsafe-policy-action**: The fail safe policy to use for this pool. If unspecified, the default failsafe policy action from the profile is used. One of: **fail**, **forward**, **drop**, **bypass**.
- **--failsafe-policy-target**: ID or name of the failsafe target pool to forward to. If specified, failsafe policy action must be forward.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-delete
{: #load-balancer-pool-delete}

Delete one or more pools from a load balancer.

```
ibmcloud is load-balancer-pool-delete LOAD_BALANCER (POOL1 POOL2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-pool-delete}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **POOL1**: ID or name of the pool.
- **POOL2**: ID or name of the pool.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-member
{: #load-balancer-pool-member-view}

View details of load balancer pool member.

```
ibmcloud is load-balancer-pool-member LOAD_BALANCER POOL MEMBER_ID [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-pool-member}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **POOL**: ID or name of the pool.
- **MEMBER_ID**: ID of the member.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-member-create
{: #load-balancer-pool-member-create}

Create a load balancer pool member.

```
ibmcloud is load-balancer-pool-member-create LOAD_BALANCER POOL PORT TARGET [--vpc VPC] [--weight WEIGHT] [--target-type instance | load_balancer] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-pool-member-create}

- `ibmcloud is load-balancer-pool-member-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 3000 192.168.100.5`
- `ibmcloud is load-balancer-pool-member-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 3000 9e692608-3b3a-4cfb-9f46-efb6b711876d`
- `ibmcloud is load-balancer-pool-member-create my-nlb my-pool 3000 my-instance`
- `ibmcloud is load-balancer-pool-member-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 3000 192.168.100.5 --weight 100 --output JSON`
- `ibmcloud is load-balancer-pool-member-create my-nlb my-pool 3000 my-instance --target-type instance`
- `ibmcloud is load-balancer-pool-member-create my-nlb my-pool 3000 my-lb --target-type load_balancer`

#### Command options
{: #command-options-load-balancer-pool-member-create}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **POOL**: ID or name of the pool.
- **PORT**: The port that the member receives load balancer traffic on. Applies only to load balancer traffic that is received on a listener with a single port. If the traffic is received on a listener with a port range, the member receives the traffic on the same port that the listener received it on. This port can also be used for health checks unless the **port** property of **health_monitor** property is specified.
- **TARGET**: The IP address of the pool member for the load balancers that are in the application family, or the ID or name of an ALB or the instance for the load balancers that are in the network family.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--weight**: Weight of the server member. This option is applicable only when the load balancer algorithm of its pool is **weighted_round_robin**.
- **--target-type**: The type of target for this pool member. Required only when the target is specified by name. One of: **instance**, **load_balancer**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-member-update
{: #load-balancer-pool-member-update}

Update a member of a load balancer pool.

```
ibmcloud is load-balancer-pool-member-update LOAD_BALANCER POOL MEMBER_ID [--vpc VPC] [--target-address TARGET_ADDRESS | --target TARGET] [--port PORT] [--weight WEIGHT] [--target-type instance | load_balancer] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-pool-member-update}

- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target 192.168.100.5 --port 3001`
- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target 9e692608-3b3a-4cfb-9f46-efb6b711876d --port 3001`
- `ibmcloud is load-balancer-pool-member-update my-nlb my-pool 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target my-instance --port 3001`
- `ibmcloud is load-balancer-pool-member-update my-nlb my-pool 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --vpc my-vpc --target my-instance --port 3001`
- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target-address 192.168.100.5 --port 3001`
- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target-address 192.168.100.5 --port 3001 --weight 100 --output JSON`
- `ibmcloud is load-balancer-pool-member-update my-nlb my-pool 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target my-instance --target-type instance`
- `ibmcloud is load-balancer-pool-member-update my-nlb my-pool 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target my-lb --target-type load_balancer`

#### Command options
{: #command-options-load-balancer-pool-member-update}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **POOL**: ID or name of the pool.
- **MEMBER_ID**: ID of the member.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--target-address**: The IP address of the pool member.
- **--target**: The IP address of the pool member for the load balancers that are in the application family, or the ID or name of an ALB or the instance for the load balancers that are in the network family.
- **--port**: The port that the member receives load balancer traffic on. Applies only to load balancer traffic that is received on a listener with a single port. If the traffic is received on a listener with a port range, the member receives the traffic on the same port that the listener received it on. This port can also be used for health checks unless the **port** property of **health_monitor** property is specified.
- **--weight**: Weight of the server member. This option is applicable only when the load balancer algorithm of its pool is **weighted_round_robin**.
- **--target-type**: The type of target for this pool member. Required only when the target is specified by name. One of: **instance**, **load_balancer**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-member-delete
{: #load-balancer-pool-member-delete}

Delete one or more members from a load balancer pool.

```
ibmcloud is load-balancer-pool-member-delete LOAD_BALANCER POOL (MEMBER_ID1 MEMBER_ID2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-pool-member-delete}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **POOL**: ID or name of the pool.
- **MEMBER_ID1**: ID of the member.
- **MEMBER_ID2**: ID of the member.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-members
{: #load-balancer-pool-members-list}

List all the members of a load balancer pool.

```
ibmcloud is load-balancer-pool-members LOAD_BALANCER POOL [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-pool-members}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **POOL**: ID or name of the pool.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-update
{: #load-balancer-pool-update}

Update a pool of a load balancer.

```
ibmcloud is load-balancer-pool-update LOAD_BALANCER POOL [--vpc VPC] [--algorithm round_robin | weighted_round_robin | least_connections] [--health-delay DELAY] [--health-max-retries RETRIES] [--health-timeout TIMEOUT] [--health-type https | http | tcp] [--health-monitor-url URL] [--health-monitor-port PORT | --reset-health-monitor-port] [--protocol https | http | tcp | udp] [[--session-persistence-type source_ip | http_cookie | app_cookie | none] | [--session-persistence-cookie-name SESSION_PERSISTENCE_COOKIE_NAME]] [--proxy-protocol disabled | v1 | v2] [--name NEW_NAME] [--failsafe-policy-action fail | forward | drop | bypass] [--failsafe-policy-target FAILSAFE_POLICY_TARGET] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-pool-update}

- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --algorithm round_robin`
- `ibmcloud is load-balancer-pool-update my-lb my-pool --algorithm round_robin`
- `ibmcloud is load-balancer-pool-update my-lb my-pool --vpc my-vpc --algorithm round_robin`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --health-delay 20 --health-max-retries 2 --health-timeout 5 --health-type http`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --health-monitor-url / --health-monitor-port 4001`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --session-persistence-type source_ip`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --protocol http`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name lb-rule-name --output JSON`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --proxy-protocol v2`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --session-persistence-type app_cookie --session-persistence-cookie-name my-cookie-name`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --failsafe-policy-action forward --failsafe-policy-target my-lb`

#### Command options
{: #command-options-load-balancer-pool-update}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **POOL**: ID or name of the pool.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--algorithm**: The load balancing algorithm. One of: **round_robin**, **weighted_round_robin**, **least_connections**.
- **--health-delay**: The health check interval in seconds. The interval must be greater than the timeout value. Minimum: **2**, maximum: **60**.
- **--health-max-retries**: The health check maximum retries. Minimum: **1**, maximum: **10**.
- **--health-timeout**: The health check timeout in seconds. Minimum: **1**, maximum: **59**.
- **--health-type**: The health check protocol. Load balancers in the application family support `tcp`, `http`, and `https`. Load balancers in the network family support `tcp` and `http`.
- **--health-monitor-url**: The health check URL path. Applicable only if the **HEALTH_TYPE** is http or https.
- **--health-monitor-port**: The health check port number. If specified, the specified ports in the server member resources are overridden.
- **--reset-health-monitor-port**: Reset health monitor port.
- **--protocol**: The pool protocol. Load balancers in the application family support `tcp`, `http`, and `https`. Load balancers in the network family support `tcp` and `udp`.
- **--session-persistence-type**: The session persistence type. One of: **source_ip**, **http_cookie**, **app_cookie**, **none**.
- **--session-persistence-cookie-name**: Session persistence cookie name. This option is applicable only to **app_cookie** type.
- **--proxy-protocol**: The proxy protocol setting for this pool. Proxy protocol is supported only for application load balancers. One of: **disabled**, **v1**, **v2**.
- **--name**: The new name of the pool.
- **--failsafe-policy-action**: The fail safe policy to use for this pool. If unspecified, the default failsafe policy action from the profile is used. One of: **fail**, **forward**, **drop**, **bypass**.
- **--failsafe-policy-target**: ID or name of the failsafe target pool to forward to. If specified, failsafe policy action must be forward.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pools
{: #load-balancer-pools-list}

List all pools of a load balancer.

```
ibmcloud is load-balancer-pools LOAD_BALANCER [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-pools}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-statistics
{: #load-balancer-statistics-list}

List all statistics of a load balancer.

```
ibmcloud is load-balancer-statistics LOAD_BALANCER [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-statistics}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-update
{: #load-balancer-update}

Update a load balancer.

```
ibmcloud is load-balancer-update LOAD_BALANCER --subnets SUBNETS [--vpc VPC] [--name NEW_NAME] [--logging-datapath-active false | true] [--dns-instance-crn DNS_INSTANCE_CRN --dns-zone-id DNS_ZONE_ID | --reset-dns] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-update}

- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-renamed-lb`
- `ibmcloud is load-balancer-update my-lb --name my-renamed-lb`
- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-renamed-lb --output JSON`
- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --logging-datapath-active false`
- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnets ec8bb350-d802-4f1b-b362-b848abd5bb65,ec8bb350-d802-4f1b-b362-b848abd5bb66`
- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --dns-instance-crn crn:v1:staging:public:dns-svcs:global:a/efe5afc483594adaa8325e2b4d1290df:228e2e37-b0ce-474d-9824-41fdef4d9121:: --dns-zone-id 260763f2-81e8-4447-b8a1-e9a92d82062c`
- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --reset-dns`

#### Command options
{: #command-options-load-balancer-update}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--name**: New name of the Load balancer.
- **--logging-datapath-active**: Enable or disable datapath logging for this load balancer. Datapath logging is applicable only for application load balancer. One of: **false**, **true**.
- **--subnets**: Comma-separated ID or name of the subnets to provision this load balancer. Load balancer availability depends on the availability of the zones that the specified subnets reside in. Currently, only the load balancer in the application family supports this option.
- **--dns-instance-crn**: The CRN of the DNS instance that is associated with the DNS zone.
- **--dns-zone-id**: ID of the DNS Zone.
- **--reset-dns**: Specify this flag to remove any existing DNS records.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancers
{: #load-balancers-list}

List all load balancers.

```
ibmcloud is load-balancers [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancers}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Network ACLs
{: #network-acls}

### ibmcloud is network-acls
{: #network-acls-list}

List all network ACLs.

```
ibmcloud is network-acls [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-acls}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl
{: #network-acl-view}

View details of a network ACL.

```
ibmcloud is network-acl ACL [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-acl}

- **ACL**: ID or name of the network ACL.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl-create
{: #network-acl-create}

Create a network ACL.

```
ibmcloud is network-acl-create ACL_NAME VPC [--rules (RULES_JSON|@RULES_JSON_FILE) | (--source-acl SOURCE_ACL [--source-acl-vpc SOURCE_ACL_VPC])] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-network-acl-create}

- `ibmcloud is network-acl-create my-acl 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is network-acl-create my-acl my-vpc`
- `ibmcloud is network-acl-create my-acl 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --source-acl 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is network-acl-create my-new-acl my-vpc --source-acl my-acl`
- `ibmcloud is network-acl-create my-new-acl my-vpc --source-acl my-acl --source-acl-vpc my-vpc2`
- `ibmcloud is network-acl-create my-acl 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --rules '[{ "action": "allow", "destination": "192.168.0.0/24", "direction": "inbound", "source": "10.0.0.0/24",  "protocol": "tcp" }]'`
- `ibmcloud is network-acl-create my-acl 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --output JSON`

#### Command options
{: #command-options-network-acl-create}

- **ACL_NAME**: Name of the network ACL.
- **VPC**: ID or name of the VPC.
- **--rules**: RULES_JSON|@RULES_JSON_FILE, rules for the ACL in JSON or JSON file.
- **--source-acl**: The ID or name of the network ACL to copy rules from.
- **--source-acl-vpc**: The ID or name of the source network ACL's VPC. This is only required to specify the unique source network ACL by name inside this VPC.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl-update
{: #network-acl-update}

Update a network ACL.

```
ibmcloud is network-acl-update ACL --name NEW_NAME [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-network-acl-update}

- `ibmcloud is network-acl-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-renamed-acl`
- `ibmcloud is network-acl-update my-acl --name my-renamed-acl`
- `ibmcloud is network-acl-update my-acl --vpc my-vpc --name my-renamed-acl`
- `ibmcloud is network-acl-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-renamed-acl --output JSON`

#### Command options
{: #command-options-network-acl-update}

- **ACL**: ID or name of the network ACL.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--name**: New name of the network ACL.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl-delete
{: #network-acl-delete}

Delete one or more network ACLs.

```
ibmcloud is network-acl-delete (ACL1 ACL2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-network-acl-delete}

- **ACL1**: ID or name of the network ACL.
- **ACL2**: ID or name of the network ACL.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl-rules
{: #network-acl-rules-list}

List all rules of a network ACL.

```
ibmcloud is network-acl-rules ACL [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-acl-rules}

- **ACL**: ID or name of the network ACL.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl-rule
{: #network-acl-rule-view}

View details of a network ACL rule.

```
ibmcloud is network-acl-rule ACL RULE [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-acl-rule}

- **ACL**: ID or name of the network ACL.
- **RULE**: ID or name of the rule.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl-rule-add
{: #network-acl-rule-add}

Add a rule to a network ACL.

```
ibmcloud is network-acl-rule-add ACL ACTION DIRECTION PROTOCOL SOURCE DESTINATION [--vpc VPC] [--name NAME] [--icmp-type ICMP_TYPE] [--icmp-code ICMP_CODE] [--source-port-min PORT_MIN] [--source-port-max PORT_MAX] [--destination-port-min PORT_MIN] [--destination-port-max PORT_MAX] [--before-rule BEFORE_RULE | --reset-before-rule] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-network-acl-rule-add}

- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound tcp 10.2.2.2 10.2.2.3`
- `ibmcloud is network-acl-rule-add my-acl allow inbound tcp 10.2.2.2 10.2.2.3`
- `ibmcloud is network-acl-rule-add my-acl allow inbound tcp 10.2.2.2 10.2.2.3 --vpc my-vpc`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound tcp 10.2.2.2 10.2.2.3 --name my-acl-rule`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound icmp 10.2.2.2 10.2.2.3 --icmp-type 8 --icmp-code 0`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound tcp 10.2.2.2 10.2.2.3 --source-port-min 555  --source-port-max 666 --destination-port-min 11 --destination-port-max 55`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound tcp 10.2.2.2 10.2.2.3 --before-rule-id 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound tcp 10.2.2.2 10.2.2.3 --output JSON`

#### Command options
{: #command-options-network-acl-rule-add}

- **ACL**: ID or name of the network ACL.
- **ACTION**: One of: **allow**, **deny**.
- **DIRECTION**: Direction of traffic to enforce. One of: **inbound**, **outbound**.
- **PROTOCOL**: Protocol to enforce. One of: **icmp**, **tcp**, **udp**.
- **SOURCE**: Source IP address or CIDR block.
- **DESTINATION**: Destination IP address or CIDR block.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--name**: The name of the ACL rule.
- **--icmp-type**: ICMP traffic type to allow. Valid values from **0** to **254**. This option is specified only when protocol is set to **icmp**. If unspecified, all types are allowed.
- **--icmp-code**: ICMP traffic code to allow. Valid values from **0** to **255**. This option is specified only when protocol is set to **icmp**. If unspecified, all codes are allowed.
- **--source-port-min**: Minimum source port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **1**).
- **--source-port-max**: Maximum source port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **65535**).
- **--destination-port-min**: Minimum destination port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **1**).
- **--destination-port-max**: Maximum destination port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **65535**).
- **--before-rule**: The ID or name of the rule that this rule is inserted before.
- **--reset-before-rule**: Reset before rule. Specify this option to move this rule after all existing rules.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl-rule-update
{: #network-acl-rule-update}

Update a rule of a network ACL.

```
ibmcloud is network-acl-rule-update ACL RULE [--vpc VPC] [--name NEW_NAME] [--direction inbound | outbound] [--action allow | deny] [--before-rule BEFORE_RULE | --reset-before-rule] [--source SOURCE] [--dest DEST] [--icmp-type ICMP_TYPE] [--icmp-code ICMP_CODE] [--source-port-min PORT_MIN] [--source-port-max PORT_MAX] [--destination-port-min PORT_MIN] [--destination-port-max PORT_MAX] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-network-acl-rule-update}

- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --source 10.2.2.2 --dest 10.2.2.3`
- `ibmcloud is network-acl-rule-update my-acl my-acl-rule --action allow --direction inbound --source 10.2.2.2 --dest 10.2.2.3`
- `ibmcloud is network-acl-rule-update my-acl my-acl-rule --vpc my-vpc --name my-acl-renamed-rule`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --source 10.2.2.2 --dest 10.2.2.3 --name my-acl`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --source 10.2.2.2 --dest 10.2.2.3 --icmp-type 8 --icmp-code 0`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --source 10.2.2.2 --dest 10.2.2.3 --source-port-min 555 --source-port-max 666 --destination-port-min 11 --destination-port-max 55`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --source 10.2.2.2 --dest 10.2.2.3 --before-rule-id 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --source 10.2.2.2 --dest 10.2.2.3 --output JSON`

#### Command options
{: #command-options-network-acl-rule-update}

- **ACL**: ID or name of the network ACL.
- **RULE**: ID or name of the rule.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--name**: New name of the rule.
- **--direction**: Direction of traffic to enforce. One of: **inbound**, **outbound**.
- **--action**: One of: **allow**, **deny**.
- **--before-rule**: The ID or name of the rule that this rule is inserted before.
- **--reset-before-rule**: Reset before rule. Specify this option to move this rule after all existing rules.
- **--source**: Source IP address or CIDR block.
- **--dest**: Destination IP address or CIDR block.
- **--icmp-type**: ICMP traffic type to allow. Valid values from **0** to **254**. This option is specified only when protocol is set to **icmp**. If unspecified, all types are allowed.
- **--icmp-code**: ICMP traffic code to allow. Valid values from **0** to **255**. This option is specified only when protocol is set to **icmp**. If unspecified, all codes are allowed.
- **--source-port-min**: Minimum source port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **1**).
- **--source-port-max**: Maximum source port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **65535**).
- **--destination-port-min**: Minimum destination port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **1**).
- **--destination-port-max**: Maximum destination port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **65535**).
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl-rule-delete
{: #network-acl-rule-delete}

Delete one or more rules from a network ACL.

```
ibmcloud is network-acl-rule-delete ACL (RULE1 RULE2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-network-acl-rule-delete}

- **ACL**: ID or name of the network ACL.
- **RULE1**: ID or name of the rule.
- **RULE2**: ID or name of the rule.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

## Public gateways
{: #public-gateways}

### ibmcloud is public-gateway
{: #public-gateway-view}

View details of a public gateway.

```
ibmcloud is public-gateway GATEWAY [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-public-gateway}

- **GATEWAY**: ID or name of the public gateway.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is public-gateway-create
{: #public-gateway-create}

Create a public gateway.

```
ibmcloud is public-gateway-create GATEWAY_NAME VPC ZONE_NAME [--ip ID | NAME | ADDRESS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-public-gateway-create}

- `ibmcloud is public-gateway-create my-public-gateway 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1`
- `ibmcloud is public-gateway-create my-public-gateway my-vpc us-south-1`
- `ibmcloud is public-gateway-create my-public-gateway 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 --ip 39300233-9995-4806-89a5-3c1b6eb88689`
- `ibmcloud is public-gateway-create my-public-gateway my-vpc us-south-1 --ip my-ip`
- `ibmcloud is public-gateway-create my-public-gateway 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 --ip 203.0.113.1`
- `ibmcloud is public-gateway-create my-public-gateway 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 --output JSON`

#### Command options
{: #command-options-public-gateway-create}

- **GATEWAY_NAME**: Name of the public gateway.
- **VPC**: ID or name of the VPC.
- **ZONE_NAME**: Name of the zone.
- **--ip**: ID, name, or existing IP address of the floating IP that is bound to the public gateway.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is public-gateway-delete
{: #public-gateway-delete}

Delete one or more public gateways.

```
ibmcloud is public-gateway-delete (GATEWAY1 GATEWAY2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-public-gateway-delete}

- **GATEWAY1**: ID or name of the public gateway.
- **GATEWAY2**: ID or name of the public gateway.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is public-gateway-update
{: #public-gateway-update}

Update a public gateway.

```
ibmcloud is public-gateway-update GATEWAY --name NEW_NAME [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-public-gateway-update}

- `ibmcloud is public-gateway-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --name my-renamed-gateway --output JSON`
- `ibmcloud is public-gateway-update my-gateway --name my-renamed-gateway --output JSON`

#### Command options
{: #command-options-public-gateway-update}

- **GATEWAY**: ID or name of the public gateway.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--name**: New name of the public gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is public-gateways
{: #public-gateways-list}

List all public gateways.

```
ibmcloud is public-gateways [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-public-gateways}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Routing tables and routes
{: #custom-routes-section}

The following section gives details about the CLI commands that are available for working with VPC routing tables and routes.

### ibmcloud is vpc-default-routing-table
{: #vpc-default-routing-table-view}

View details of the default routing table of a VPC.

```
ibmcloud is vpc-default-routing-table VPC [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-default-routing-table}

- **VPC**: ID or name of the VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-tables
{: #vpc-routing-tables-list}

List all routing tables for a VPC.

```
ibmcloud is vpc-routing-tables VPC [--is-default true | false] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-routing-tables}

- **VPC**: ID or name of the VPC.
- **--is-default**: Filters the collection to routing tables with the `is_default` property that matches the specified value. One of: **true**, **false**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-table
{: #vpc-routing-table-view}

View details of a VPC routing table.

```
ibmcloud is vpc-routing-table VPC ROUTING_TABLE [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-routing-table}

- **VPC**: ID or name of the VPC.
- **ROUTING_TABLE**: ID or name of the VPC routing table.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-table-create
{: #vpc-routing-table-create}

Create a VPC routing table.

```
ibmcloud is vpc-routing-table-create VPC [--name NAME] [--direct-link-ingress false | true] [--internet-ingress, --internet false | true] [--transit-gateway-ingress false | true] [--vpc-zone-ingress false | true] [--accept-routes-from-resource-type-filters, --ar-rtf vpn_server | vpn_gateway] [--advertise-routes-to direct_link | transit_gateway | direct_link,transit_gateway] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpc-routing-table-create}

- `ibmcloud is vpc-routing-table-create 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-vpc-routing-table --output JSON`
- `ibmcloud is vpc-routing-table-create my-vpc --name my-vpc-routing-table --output JSON`
- `ibmcloud is vpc-routing-table-create vpc-doloremque-6364-us-east --name test-vpc-cli-routing-tb2 --direct-link-ingress true --internet-ingress false   --transit-gateway-ingress false  --vpc-zone-ingress false`
- `ibmcloud is vpc-routing-table-create 979b4bc6-f018-40a2-92f5-0b1cf777b55d --name test-vpc-cli-routing-tb1 --direct-link-ingress false --internet-ingress false   --transit-gateway-ingress false  --vpc-zone-ingress true`
- `ibmcloud is vpc-routing-table-create my-vpc --name my-vpc-routing-table --accept-routes-from-resource-type-filters vpn_server,vpn_gateway`
Create a routing table with resource type filter.
- `ibmcloud is vpc-routing-table-create 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-vpc-routing-table --direct-link-ingress true  --transit-gateway-ingress true --advertise-routes-to direct_link,transit_gateway`

#### Command options
{: #command-options-vpc-routing-table-create}

- **VPC**: ID or name of the VPC.
- **--name**: Name of the VPC routing table.
- **--direct-link-ingress, --direct-link**: If set to "true", this routing table is used to route traffic that originates from Direct Link to this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--internet-ingress, --internet**: Indicates whether this routing table is used to route traffic that originates from the internet.  Updating to "true" selects this routing table, provided no other routing table in the VPC already has this property set to "true".  Updating to "false" deselects this routing table. One of: **false**, **true**.
- **--transit-gateway-ingress, --transit-gateway**: If set to "true", this routing table is used to route traffic that originates from Transit Gateway to this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--vpc-zone-ingress, --vpc-zone**: If set to "true", this routing table is used to route traffic that originates from subnets in other zones in this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--accept-routes-from-resource-type-filters, --ar-rtf**: The comma-separated resource type filters that can create routes in this routing table. One of: **vpn_server**, **vpn_gateway**.
- **--advertise-routes-to**: The ingress sources to advertise routes to. Routes in the table with advertise enabled are advertised to these sources. One or more comma separated values of: direct_link, transit_gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-table-update
{: #vpc-routing-table-update}

Update a VPC routing table.

```
ibmcloud is vpc-routing-table-update VPC ROUTING_TABLE [--name NEW_NAME] [--direct-link-ingress false | true] [--internet-ingress, --internet false | true] [--transit-gateway-ingress false | true] [--vpc-zone-ingress false | true] [[--accept-routes-from-resource-type-filters, --ar-rtf vpn_server | vpn_gateway] | --clean-all-accept-routes-from-filters, --cl-arf] [[--advertise-routes-to direct_link | transit_gateway | direct_link,transit_gateway] | --clean-all-advertise-routes-to-sources, --cl-adrt] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpc-routing-table-update}

- `ibmcloud is vpc-routing-table-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1d456 --name my-renamed-vpc-routing-table --output JSON`
- `ibmcloud is vpc-routing-table-update my-vpc my-vpc-routing-table --name my-renamed-vpc-routing-table --output JSON`
- `ibmcloud is vpc-routing-table-update vpc-doloremque-6364-us-east  test-vpc-cli-routing-tb2 --direct-link-ingress true --internet-ingress false   --transit-gateway-ingress true  --vpc-zone-ingress false`
- `ibmcloud is vpc-routing-table-update 979b4bc6-f018-40a2-92f5-0b1cf777b55d  27415d55-9d3b-4adb-a993-236ef59a45ec --direct-link-ingress false --internet-ingress false   --transit-gateway-ingress false  --vpc-zone-ingress false`
- `ibmcloud is vpc-routing-table-update 6fd4f882-9640-4da2-a76f-e3732d317610 ce155406-8a64-4f05-946a-634c2977584d --advertise-routes-to direct_link`
- `ibmcloud is vpc-routing-table-update 6fd4f882-9640-4da2-a76f-e3732d317610 ce155406-8a64-4f05-946a-634c2977584d --clean-all-advertise-routes-to-sources`

#### Command options
{: #command-options-vpc-routing-table-update}

- **VPC**: ID or name of the VPC.
- **ROUTING_TABLE**: ID or name of the VPC routing table.
- **--name**: New name of the routing table.
- **--direct-link-ingress, --direct-link**: If set to "true", this routing table is used to route traffic that originates from Direct Link to this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--internet-ingress, --internet**: Indicates whether this routing table is used to route traffic that originates from the internet.  Updating to "true" selects this routing table, provided no other routing table in the VPC already has this property set to "true".  Updating to "false" deselects this routing table. One of: **false**, **true**.
- **--transit-gateway-ingress, --transit-gateway**: If set to "true", this routing table is used to route traffic that originates from Transit Gateway to this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--vpc-zone-ingress, --vpc-zone**: If set to "true", this routing table is used to route traffic that originates from subnets in other zones in this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--accept-routes-from-resource-type-filters, --ar-rtf**: The comma-separated resource type filters that can create routes in this routing table. All learned routes from resources that match a resource filter are removed when an existing resource filter is removed. One of: **vpn_server**, **vpn_gateway**.
- **--clean-all-accept-routes-from-filters, --cl-arf**: Remove all accept routes from filters and delete all learned routes from the routing table.
- **--advertise-routes-to**: The ingress sources to advertise routes to. Routes in the table with advertise enabled are advertised to these sources. One or more comma separated values of: direct_link, transit_gateway.
- **--clean-all-advertise-routes-to-sources, --cl-adrt**: Remove all existing ingress sources to advertise to.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-table-delete
{: #vpc-routing-table-delete}

Delete one or more VPC routing tables.

```
ibmcloud is vpc-routing-table-delete VPC (ROUTING_TABLE1 ROUTING_TABLE2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-routing-table-delete}

- **VPC**: ID or name of the VPC.
- **ROUTING_TABLE1**: ID or name of the VPC routing table.
- **ROUTING_TABLE2**: ID or name of the VPC routing table.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-table-routes
{: #vpc-routing-table-routes-list}

List all the routes of a VPC routing table.

```
ibmcloud is vpc-routing-table-routes VPC ROUTING_TABLE [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-routing-table-routes}

- **VPC**: ID or name of the VPC.
- **ROUTING_TABLE**: ID or name of the VPC routing table.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-table-route
{: #vpc-routing-table-route-view}

View details of a VPC route.

```
ibmcloud is vpc-routing-table-route VPC ROUTING_TABLE ROUTE [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-routing-table-route}

- **VPC**: ID or name of the VPC.
- **ROUTING_TABLE**: ID or name of the VPC routing table.
- **ROUTE**: ID or name of the VPC route.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-table-route-create
{: #vpc-routing-table-route-create}

Create a VPC route.

```
ibmcloud is vpc-routing-table-route-create VPC ROUTING_TABLE --zone ZONE_NAME --destination DESTINATION_CIDR [--action delegate_vpc | delegate | deliver | drop] [--priority PRIORITY] [--next-hop NEXT_HOP [--vpngw VPNGW]] [--advertise false | true] [--name NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpc-routing-table-route-create}

- `ibmcloud is vpc-routing-table-route-create 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1d456 --name my-vpc-route --action deliver --zone us-south-1 --destination  10.2.2.0/24 --next-hop 10.0.0.2 --output JSON`
- `ibmcloud is vpc-routing-table-route-create my-vpc my-routing-table --name my-vpc-route --action deliver --zone us-south-1 --destination  10.2.2.0/24 --next-hop 10.0.0.2 --output JSON`
- `ibmcloud is vpc-routing-table-route-create 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1d456 --name my-vpc-route --action delegate --zone us-south-1 --destination  10.2.2.0/24 --output JSON`
- `ibmcloud is vpc-routing-table-route-create 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1d456 --name my-vpc-route --action drop --zone us-south-1 --destination  10.2.2.0/24 --output JSON`
- `ibmcloud is vpc-routing-table-route-create  vpc1001  routing-table-vpc1001-rtable011-id -name my-vpc-route --action deliver --zone us-east-3 --destination  10.2.2.0/24 --priority 1 --next-hop 10.0.0.2`
- `ibmcloud is vpc-routing-table-route-create vpc1001 routing-table-vpc1001-1-name  --zone us-east-3 --destination  10.2.2.0/24  --action deliver  --priority 3  --next-hop vpn-connection-vel-4573-us-east --vpngw aaa-default-vpn-gateway-1  --name vpc-route-cli-demo-1001`
- `ibmcloud is vpc-routing-table-route-create 6fd4f882-9640-4da2-a76f-e3732d317610 ce155406-8a64-4f05-946a-634c2977584d --zone us-east-1 --destination 10.2.2.0/24 --next-hop 10.0.0.2 --action deliver --advertise true --name cli-route-7`

#### Command options
{: #command-options-vpc-routing-table-route-create}

- **VPC**: ID or name of the VPC.
- **ROUTING_TABLE**: ID or name of the VPC routing table.
- **--zone**: Name of the zone.
- **--action**: The action to perform with a packet that matches the route. One of: **delegate_vpc**, **delegate**, **deliver**, **drop**.
- **--destination**: The destination CIDR of the route. At most, two routes per zone in a table can have the same destination, and only if both routes have an action of **deliver**.
- **--priority**: The route's priority. Smaller values have higher priority. Values can range between 0-4. (default: **2**).
- **--next-hop**: If the action is **deliver**, then the IP address, VPN connection ID, or name of the next-hop that packets are delivered to. For other action values, it must be omitted or specified as 0.0.0.0.
- **--vpngw**: ID or name of the VPN gateway. This option is required only if the next-hop is specified as VPN connection in name format.
- **--advertise**: Indicates whether this route advertises to the ingress sources that are specified by the advertise_routes_to routing table property. One of: **false**, **true**.
- **--name**: Name of the VPC routing table.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-table-route-update
{: #vpc-routing-table-route-update}

Update a VPC route.

```
ibmcloud is vpc-routing-table-route-update VPC ROUTING_TABLE ROUTE [--name NEW_NAME] [--priority PRIORITY] [--advertise false | true] [--next-hop NEXT_HOP [--vpngw VPNGW]] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpc-routing-table-route-update}

- `ibmcloud is vpc-routing-table-route-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1d456 72b27b5c-f4b0-48bb-b954-5becc7c1d4ef --name my-vpc-route --output JSON`
- `ibmcloud is vpc-routing-table-route-update vpc1001 routing-table-vpc1001-rtable011-id  my-vpc-route --priority 4 --next-hop 10.1.1.1 --name vpc-route-cli-1`
- `ibmcloud is vpc-routing-table-route-update vpc1001 routing-table-vpc1001-1-name  vpc-route-cli-demo-1001 --priority 3  --next-hop 541c6bbf-6109-44bd-b2c9-176c6e11bc59  --vpngw aaa-default-vpn-gateway-1  --name vpc-route-cli-demo-1003`
- `ibmcloud is vpc-routing-table-route-update 6fd4f882-9640-4da2-a76f-e3732d317610 ce155406-8a64-4f05-946a-634c2977584d 2bbca25a-a7c6-4bce-8889-5f914b7a7142 --advertise false`

#### Command options
{: #command-options-vpc-routing-table-route-update}

- **VPC**: ID or name of the VPC.
- **ROUTING_TABLE**: ID or name of the VPC routing table.
- **ROUTE**: ID or name of the VPC route.
- **--name**: New name of the route.
- **--priority**: The route's priority. Smaller values have higher priority. Values can range between 0-4. (default: **2**).
- **--advertise**: Indicates whether this route advertises to the ingress sources that are specified by the advertise_routes_to routing table property. One of: **false**, **true**.
- **--next-hop**: If the action is **deliver**, then the IP address, VPN connection ID, or name of the next-hop that packets are delivered to. For other action values, it must be omitted or specified as 0.0.0.0.
- **--vpngw**: ID or name of the VPN gateway. This option is required only if the next-hop is specified as VPN connection in name format.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-table-route-delete
{: #vpc-routing-table-route-delete}

Delete one or more VPC routes.

```
ibmcloud is vpc-routing-table-route-delete VPC ROUTING_TABLE (ROUTE1 ROUTE2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-routing-table-route-delete}

- **VPC**: ID or name of the VPC.
- **ROUTING_TABLE**: ID or name of the VPC routing table.
- **ROUTE1**: ID or name of the VPC route.
- **ROUTE2**: ID or name of the VPC route.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-routing-table
{: #subnet-routing-table-view}

View details of routing table that is attached to the subnet.

```
ibmcloud is subnet-routing-table SUBNET [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnet-routing-table}

- **SUBNET**: ID or name of the subnet.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Security groups
{: #security-groups-cli-ref}

### ibmcloud is security-group
{: #security-group-view}

View details of a security group.

```
ibmcloud is security-group GROUP [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-security-group}

- **GROUP**: ID or name of the security group.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-create
{: #security-group-create}

Create a security group.

```
ibmcloud is security-group-create GROUP_NAME VPC [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-security-group-create}

- `ibmcloud is security-group-create my-sg 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is security-group-create my-sg my-vpc`
- `ibmcloud is security-group-create my-sg 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --resource-group-id fee82deba12e4c0fb69c3b09d1f12345`
- `ibmcloud is security-group-create my-sg 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --resource-group-name Default`
- `ibmcloud is security-group-create my-sg 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --output JSON`

#### Command options
{: #command-options-security-group-create}

- **GROUP_NAME**: Name of the security group.
- **VPC**: ID or name of the VPC.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-delete
{: #security-group-delete}

Delete one or more security groups.

```
ibmcloud is security-group-delete (GROUP1 GROUP2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-security-group-delete}

- **GROUP1**: ID or name of the security group.
- **GROUP2**: ID or name of the security group.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-rule
{: #security-group-rule-view}

View details of a security group rule.

```
ibmcloud is security-group-rule GROUP RULE_ID [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-security-group-rule}

- **GROUP**: ID or name of the security group.
- **RULE_ID**: ID of the security group rule.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-rule-add
{: #security-group-rule-add}

Add a rule to a security group.

```
ibmcloud is security-group-rule-add GROUP DIRECTION PROTOCOL [--vpc VPC] [--local LOCAL_ADDRESS | CIDR_BLOCK] [--remote REMOTE_ADDRESS | CIDR_BLOCK | SECURITY_GROUP] [--icmp-type ICMP_TYPE [--icmp-code ICMP_CODE]] [--port-min PORT_MIN] [--port-max PORT_MAX] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-security-group-rule-add}

- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound tcp`
- `ibmcloud is security-group-rule-add my-sg inbound tcp`
- `ibmcloud is security-group-rule-add my-sg inbound tcp --vpc my-vpc`
- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound icmp --icmp-type 8 --icmp-code 0`
- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound tcp --remote 12.2.2.3`
- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound tcp --remote 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is security-group-rule-add my-sg inbound tcp --remote my-sg`
- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound tcp --port-min 4 --port-max 22 --output JSON`
- `ibmcloud is security-group-rule-add --sg 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --direction inbound --protocol tcp --local 192.168.3.0`

#### Command options
{: #command-options-security-group-rule-add}

- **GROUP**: ID or name of the security group.
- **DIRECTION**: Direction of traffic to enforce. One of: **inbound**, **outbound**.
- **PROTOCOL**: Protocol to enforce. One of: **icmp**, **tcp**, **udp**.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--local**: The local IP address or range of local IP addresses that this rule allows for inbound and outbound traffic. A CIDR block of 0.0.0.0/0 allows inbound and outbound traffic to all local IP addresses.
- **--remote**: The set of network interfaces from which this rule allows traffic. It can be specified as either a REMOTE_ADDRESS, CIDR_BLOCK, or SECURITY_GROUP. If unspecified, then traffic is allowed from any source (or to any source, for outbound rules).
- **--icmp-type**: ICMP traffic type to allow. Valid values from **0** to **254**. This option is specified only when protocol is set to **icmp**. If unspecified, all types are allowed.
- **--icmp-code**: ICMP traffic code to allow. Valid values from **0** to **255**. This option is specified only when protocol is set to **icmp**. If unspecified, all codes are allowed.
- **--port-min**: Minimum port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp**. If unspecified, all ports are allowed (default: **1**).
- **--port-max**: Maximum port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp**. If unspecified, all ports are allowed (default: **65535**).
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-rule-delete
{: #security-group-rule-delete}

Delete one or more rules from a security group.

```
ibmcloud is security-group-rule-delete GROUP (RULE_ID1 RULE_ID2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-security-group-rule-delete}

- `ibmcloud is security-group-rule-delete 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 r134-c9bc0d12-de72-400d-885c-dcb9ec895f17`
- `ibmcloud is security-group-rule-delete my-sg r134-c9bc0d12-de72-400d-885c-dcb9ec895f17 --vpc my-vpc`

#### Command options
{: #command-options-security-group-rule-delete}

- **GROUP**: ID or name of the security group.
- **RULE_ID1**: ID of the security group rule.
- **RULE_ID2**: ID of the security group rule.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-rule-update
{: #security-group-rule-update}

Update a rule of a security group.

```
ibmcloud is security-group-rule-update GROUP RULE_ID [--vpc VPC] [--direction inbound | outbound] [--local LOCAL_ADDRESS | CIDR_BLOCK] [--remote REMOTE_ADDRESS | CIDR_BLOCK | SECURITY_GROUP] [--icmp-type ICMP_TYPE | --reset-icmp-type] [--icmp-code ICMP_CODE | --reset-icmp-code] [--port-min PORT_MIN | --reset-port-min] [--port-max PORT_MAX | --reset-port-max] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-security-group-rule-update}

- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound`
- `ibmcloud is security-group-rule-update my-sg 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --icmp-type 8 --icmp-code 0`
- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --port-min 4 --port-max 22`
- `ibmcloud is security-group-rule-update my-sg 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --remote 12.2.2.3`
- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --reset-icmp-code --reset-icmp-type`
- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --output JSON`
- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --local 192.168.3.4`

#### Command options
{: #command-options-security-group-rule-update}

- **GROUP**: ID or name of the security group.
- **RULE_ID**: ID of the security group rule.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--direction**: Direction of traffic to enforce. One of: **inbound**, **outbound**.
- **--local**: The local IP address or range of local IP addresses that this rule allows for inbound and outbound traffic. A CIDR block of 0.0.0.0/0 allows inbound and outbound traffic to all local IP addresses.
- **--remote**: The set of network interfaces from which this rule allows traffic. It can be specified as either a REMOTE_ADDRESS, CIDR_BLOCK, or SECURITY_GROUP. If unspecified, then traffic is allowed from any source (or to any source, for outbound rules).
- **--icmp-type**: ICMP traffic type to allow. Valid values from **0** to **254**. This option is specified only when protocol is set to **icmp**. If unspecified, all types are allowed.
- **--reset-icmp-type**: Reset an existing ICMP traffic type value.
- **--icmp-code**: ICMP traffic code to allow. Valid values from **0** to **255**. This option is specified only when protocol is set to **icmp**. If unspecified, all codes are allowed.
- **--reset-icmp-code**: Reset an existing ICMP traffic code value.
- **--port-min**: Minimum port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp**. If unspecified, all ports are allowed (default: **1**).
- **--reset-port-min**: Reset minimum port number.
- **--port-max**: Maximum port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp**. If unspecified, all ports are allowed (default: **65535**).
- **--reset-port-max**: Reset maximum port number.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-rules
{: #security-group-rules-list}

List all rules of a security group.

```
ibmcloud is security-group-rules GROUP [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-security-group-rules}

- **GROUP**: ID or name of the security group.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-update
{: #security-group-update}

Update a security group.

```
ibmcloud is security-group-update GROUP [--vpc VPC] [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-security-group-update}

- `ibmcloud is security-group-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-sg-renamed --output JSON`
- `ibmcloud is security-group-update my-sg --name my-sg-renamed --output JSON`
- `ibmcloud is security-group-update my-sg --vpc my-vpc --name my-sg-renamed --output JSON`

#### Command options
{: #command-options-security-group-update}

- **GROUP**: ID or name of the security group.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--name**: New name of the security group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-groups
{: #security-groups-list}

List all security groups.

```
ibmcloud is security-groups [--vpc VPC] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-security-groups}

- **--vpc**: ID or name of the VPC.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-target
{: #security-group-target-view}

View details of a target of a security group.

```
ibmcloud is security-group-target GROUP TARGET [--vpc VPC] [(--trt load_balancer | endpoint_gateway | vpn_server | virtual_network_interface) | --in INSTANCE | --bm BARE_METAL_SERVER] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-security-group-target}

- `ibmcloud is security-group-target 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9`
- `ibmcloud is security-group-target my-sg my-nic --in my-in`
- `ibmcloud is security-group-target my-sg my-nic --bm my-bm`
- `ibmcloud is security-group-target my-sg my-lb --trt load_balancer`
- `ibmcloud is security-group-target my-sg my-ege --trt endpoint_gateway`
- `ibmcloud is sg-t sg-qui-us-east vpn-server-1 --trt vpn_server --vpc vpc_per_region_us-east`
- `ibmcloud is security-group-target sg-vni cli-share-vni-1 --trt virtual_network_interface`

#### Command options
{: #command-options-security-group-target}

- **GROUP**: ID or name of the security group.
- **TARGET**: ID or name of the bound target resource for security group. The following types are supported target resource types: _network_interface_, _load_balancer_, _endpoint_gateway_, _vpn_server_, _virtual_network_interface_.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--trt**: The bound target resource type, this option is required only if you use the target name instead of an ID. One of: **load_balancer**, **endpoint_gateway**, **vpn_server**, **virtual_network_interface**.
- **--in**: The ID or name of the instance to be bound. It is required only if you use the network interface name instead of an ID.
- **--bm**: The ID or name of the bare metal server to be bound. It is required only if the network interface name is used instead of an ID.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-target-add
{: #security-group-target-add}

Add a target to a security group.

```
ibmcloud is security-group-target-add GROUP TARGET [--vpc VPC] [(--trt load_balancer | endpoint_gateway | vpn_server | virtual_network_interface) | --in INSTANCE | --bm BARE_METAL_SERVER] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-security-group-target-add}

- `ibmcloud is security-group-target-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --output JSON`
- `ibmcloud is security-group-target-add my-sg my-lb --trt load_balancer --vpc my-vpc --output JSON`
- `ibmcloud is security-group-target-add my-sg eth0 --in my-instnace --vpc my-vpc --output JSON`
- `ibmcloud is security-group-target-add my-sg eth0 --in my-instnace`
- `ibmcloud is security-group-target-add my-sg eth0 --bm my-bm --vpc my-vpc --output JSON`
- `ibmcloud is security-group-target-add my-sg my-egw --trt endpoint_gateway --vpc my-vpc --output JSON`
- `ibmcloud is sg-ta demo-sg vpnServer_per_region_us-east --trt vpn_server --vpc default-vpc-2`
- `ibmcloud is security-group-target-add sg-vni cli-share-vni-1 --trt virtual_network_interface`

#### Command options
{: #command-options-security-group-target-add}

- **GROUP**: ID or name of the security group.
- **TARGET**: ID or name of the bound target resource for security group. The following types are supported target resource types: _network_interface_, _load_balancer_, _endpoint_gateway_, _vpn_server_, _virtual_network_interface_.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--trt**: The bound target resource type, this option is required only if you use the target name instead of an ID. One of: **load_balancer**, **endpoint_gateway**, **vpn_server**, **virtual_network_interface**.
- **--in**: The ID or name of the instance to be bound. It is required only if you use the network interface name instead of an ID.
- **--bm**: The ID or name of the bare metal server to be bound. It is required only if the network interface name is used instead of an ID.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-target-remove
{: #security-group-target-remove}

Remove targets from a security group.

```
ibmcloud is security-group-target-remove GROUP (TARGET1 TARGET2 ...) [--vpc VPC] [(--trt load_balancer | endpoint_gateway | vpn_server | virtual_network_interface) | --in INSTANCE | --bm BARE_METAL_SERVER] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-security-group-target-remove}

- `ibmcloud is security-group-target-remove 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 -f`
- `ibmcloud is security-group-target-remove my-sg my-lb --trt load_balancer --vpc my-vpc`
- `ibmcloud is security-group-target-remove my-sg eth0 --in my-instnace --vpc my-vpc`
- `ibmcloud is security-group-target-remove my-sg eth0 --in my-instnace`
- `ibmcloud is security-group-target-remove my-sg eth0 --bm my-bm --vpc my-vpc`
- `ibmcloud is security-group-target-remove my-sg my-egw --trt endpoint-gateway`
- `ibmcloud is sg-td demo-sg vpnServer_per_region_us-east --trt vpn_server --vpc default-vpc-2`
- `ibmcloud is security-group-target-remove sg-vni cli-share-vni-1 --trt virtual_network_interface`

#### Command options
{: #command-options-security-group-target-remove}

- **GROUP**: ID or name of the security group.
- **TARGET1**: ID or name of the bound target resource for security group. If you use the name format, only the resources under the same resource type are supplied. And for network interface by name, all the network interface names must be under the same instance. The following types are supported target resource types: _network_interface_, _load_balancer_, _endpoint_gateway_, _vpn_server_, _virtual_network_interface_.
- **TARGET2**: ID or name of the bound target resource for security group. If you use the name format, only the resources under the same resource type are supplied. And for network interface by name, all the network interface names must be under the same instance. The following types are supported target resource types: _network_interface_, _load_balancer_, _endpoint_gateway_, _vpn_server_, _virtual_network_interface_.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--trt**: The bound target resource type, this option is required only if you use the target name instead of an ID. One of: **load_balancer**, **endpoint_gateway**, **vpn_server**, **virtual_network_interface**.
- **--in**: The ID or name of the instance to be bound. It is required only if you use the network interface name instead of an ID.
- **--bm**: The ID or name of the bare metal server to be bound. It is required only if the network interface name is used instead of an ID.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-targets
{: #security-group-targets-list}

List all targets of a security group.

```
ibmcloud is security-group-targets GROUP [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-security-group-targets}

- `ibmcloud is sg-ts 821ce0fe-e87b-4fa7-9083-7c0d86bef357`
- `ibmcloud is sg-ts sg-qui-us-east`

#### Command options
{: #command-options-security-group-targets}

- **GROUP**: ID or name of the security group.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Subnets
{: #subnet-cli-ref}

### ibmcloud is subnet
{: #subnet-view}

View details of a subnet.

```
ibmcloud is subnet SUBNET [--vpc VPC] [--show-attached] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnet}

- **SUBNET**: ID or name of the subnet.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--show-attached**: View details of resources (instances, load balancers, VPN gateways) attached to the subnet.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-create
{: #subnet-create}

Create a subnet.

```
ibmcloud is subnet-create SUBNET_NAME VPC ((--zone ZONE_NAME --ipv4-address-count ADDR_COUNT) | --ipv4-cidr-block CIDR_BLOCK) [--acl ACL] [--pgw PGW] [--rt RT] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-subnet-create}

- `ibmcloud is subnet-create my-subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4-cidr-block 10.10.10.0/24`
- `ibmcloud is subnet-create my-subnet my-vpc --ipv4-cidr-block 10.10.10.0/24`
- `ibmcloud is subnet-create my-subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4-address-count 256 --zone us-south-2`
- `ibmcloud is subnet-create my-subnet my-vpc --ipv4-address-count 256 --zone us-south-2`
- `ibmcloud is subnet-create my-subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4-address-count 256 --zone us-south-2 --acl 8daca77a-4980-4d33-8f3e-7038797be8f9`
- `ibmcloud is subnet-create my-subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4-address-count 256 --zone us-south-2 --pgw 8daca77a-4980-4d33-8f3e-7038797be8f9`
- `ibmcloud is subnet-create my-subnet my-vpc --ipv4-address-count 256 --zone us-south-2 --acl my-acl --pgw --my-pgw --rt my-vpc-rt`
- `ibmcloud is subnet-create my-subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4-address-count 256 --zone us-south-2 --pgw 8daca77a-4980-4d33-8f3e-7038797be8f9 --output JSON`
- `ibmcloud is subnet-create my-subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4-address-count 256 --zone us-south-2 --rt 8daca77a-4980-4d33-8f3e-7038797be8f9`

#### Command options
{: #command-options-subnet-create}

- **SUBNET_NAME**: Name of the subnet.
- **VPC**: ID or name of the VPC.
- **--ipv4-cidr-block**: the IPv4 range of the subnet. This option is mutually exclusive with **--ipv4-address-count**.
- **--ipv4-address-count**: The total number of IPv4 addresses required, must be a power of 2 and minimum value is **8**. This option is mutually exclusive with **--ipv4-cidr-block**.
- **--zone**: Name of the zone.
- **--acl**: The ID or name of the network ACL.
- **--pgw**: The ID or name of the public gateway.
- **--rt**: The ID, name, or CRN of the routing table.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-delete
{: #subnet-delete}

Delete one or more subnets.

```
ibmcloud is subnet-delete (SUBNET1 SUBNET2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-subnet-delete}

- **SUBNET1**: ID or name of the subnet.
- **SUBNET2**: ID or name of the subnet.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-update
{: #subnet-update}

Update a subnet.

```
ibmcloud is subnet-update SUBNET [--vpc VPC] [--name NEW_NAME] [--acl ACL] [--pgw PGW] [--rt RT] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-subnet-update}

- `ibmcloud is subnet-update ec8bb350-d802-4f1b-b362-b848abd5bb65 --name my-renamed-subnet`
- `ibmcloud is subnet-update my-subnet --name my-renamed-subnet`
- `ibmcloud is subnet-update ec8bb350-d802-4f1b-b362-b848abd5bb65 --acl 8daca77a-4980-4d33-8f3e-7038797be8f9`
- `ibmcloud is subnet-update my-subnet --acl my-acl`
- `ibmcloud is subnet-update ec8bb350-d802-4f1b-b362-b848abd5bb65 --pgw 8daca77a-4980-4d33-8f3e-7038797be8f9`
- `ibmcloud is subnet-update my-subnet --pgw my-pgw`
- `ibmcloud is subnet-update ec8bb350-d802-4f1b-b362-b848abd5bb65 --name my-subnet --output JSON`
- `ibmcloud is subnet-update my-subnet --rt my-vpc-rt`

#### Command options
{: #command-options-subnet-update}

- **SUBNET**: ID or name of the subnet.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--name**: New name of the subnet.
- **--acl**: The ID or name of the network ACL.
- **--pgw**: The ID or name of the public gateway.
- **--rt**: The ID, name, or CRN of the routing table.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnets
{: #subnets-list}

List all subnets.

```
ibmcloud is subnets [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--zone ZONE] [--rt ROUTING_TABLE] [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnets}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--zone**: Filters the collection to resources with a zone name property that matches the exact specified name.
- **--rt**: The ID or name of the routing table.
- **--vpc**: ID, name, or CRN of the VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-public-gateway
{: #subnet-public-gateway-view}

View details of public gateway attached to the subnet.

```
ibmcloud is subnet-public-gateway SUBNET [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnet-public-gateway}

- **SUBNET**: ID or name of the subnet.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-public-gateway-detach
{: #subnet-public-gateway-detach}

Detach the public gateway from a subnet.

```
ibmcloud is subnet-public-gateway-detach SUBNET [--vpc VPC] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-subnet-public-gateway-detach}

- **SUBNET**: ID or name of the subnet.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-reserved-ips
{: #subnet-reserved-ips-list}

List all reserved IPs in the subnet.

```
ibmcloud is subnet-reserved-ips SUBNET [--vpc VPC] [--target TARGET] [--trt endpoint_gateway | virtual_network_interface] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnet-reserved-ips}

- **SUBNET**: ID or name of the subnet.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--target**: The ID, name, or CRN of the target resource.
- **--trt**: Supported target resource types. One of: **endpoint_gateway**, **virtual_network_interface**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-reserved-ip
{: #subnet-reserved-ip-view}

View details of reserved IP.

```
ibmcloud is subnet-reserved-ip SUBNET RESERVED_IP [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnet-reserved-ip}

- **SUBNET**: ID or name of the subnet.
- **RESERVED_IP**: ID or name of the reserved IP.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-reserved-ip-create
{: #subnet-reserved-ip-create}

Reserve an IP in a subnet.

```
ibmcloud is subnet-reserved-ip-create SUBNET [--vpc VPC] [--name NAME] [--address ADDRESS] [--trt endpoint_gateway | virtual_network_interface] [--auto-delete true | false] [--target TARGET] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-subnet-reserved-ip-create}

- `ibmcloud is subnet-reserved-ip-create 2201-3f2e33d4-2140-44b4-843c-d73e03d585f1 --name my-reserved-ip --address 10.240.64.10 --auto-delete true`
- `ibmcloud is subnet-reserved-ip-create my-subnet --name my-reserved-ip --address 10.240.64.10 --auto-delete true`
- `ibmcloud is subnet-reserved-ip-create 2201-3f2e33d4-2140-44b4-843c-d73e03d585f1 --name my-reserved-ip --address 10.240.64.10 --auto-delete true --target r134-5be98168-017a-459c-959f-7a6c1f7b813b`
- `ibmcloud is subnet-reserved-ip-create my-subnet --name my-reserved-ip --address 10.240.64.10 --auto-delete true --target my-vpe`
- `ibmcloud is subnet-reserved-ip-create 2201-3f2e33d4-2140-44b4-843c-d73e03d585f1 --name my-reserved-ip --address 10.240.64.10 --output JSON`
- `ibmcloud is subnet-reserved-ip-create sn-20230803-02 --name vni-rip-1 --target vni2 --trt virtual_network_interface`
- `ibmcloud is subnet-reserved-ip-create 7308-5c62937d-b7cb-4ce8-8456-c39de068755e --name vni-rip-2 --trt virtual_network_interface --target 7308-b81c1e13-b3a2-455c-814a-213bc9de4a90 --auto-delete true`

#### Command options
{: #command-options-subnet-reserved-ip-create}

- **SUBNET**: ID or name of the subnet.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--name**: The user-defined name for this reserved IP. Names must be unique within the subnet that the reserved IP resides in. Names beginning with **ibm-** are reserved for provider-owned resources.
- **--address**: The IP address to reserve, which must not already be reserved on the subnet. If not specified, an available address on the subnet is automatically selected.
- **--trt**: Supported target resource types. One of: **endpoint_gateway**, **virtual_network_interface**. (default: **endpoint_gateway**).
- **--auto-delete**: Indicates whether this reserved IP member automatically deletes when either target is deleted, or the reserved IP is unbound. Must be false if the reserved IP is unbound. One of: **true**, **false**. (default: **false**).
- **--target**: The ID or name of the target resource. The following types are supported target resource types: _endpoint_gateway_, _virtual_network_interface_.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-reserved-ip-update
{: #subnet-reserved-ip-update}

Update a reserved IP.

```
ibmcloud is subnet-reserved-ip-update SUBNET RESERVED_IP [--vpc VPC] [--name NEW_NAME] [--auto-delete true | false] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-subnet-reserved-ip-update}

- `ibmcloud is subnet-reserved-ip-update 2201-3f2e33d4-2140-44b4-843c-d73e03d585f1 2201-7fc11925-47ff-4080-a314-be64c662c302 --name my-reserved-ip2`
- `ibmcloud is subnet-reserved-ip-update my-subnet my-reserved-ip --name my-reserved-ip2`
- `ibmcloud is subnet-reserved-ip-update 2201-3f2e33d4-2140-44b4-843c-d73e03d585f1 2201-7fc11925-47ff-4080-a314-be64c662c302 --auto-delete false`
- `ibmcloud is subnet-reserved-ip-update 2201-3f2e33d4-2140-44b4-843c-d73e03d585f1 2201-7fc11925-47ff-4080-a314-be64c662c302 --name my-reserved-ip2 --output JSON`

#### Command options
{: #command-options-subnet-reserved-ip-update}

- **SUBNET**: ID or name of the subnet.
- **RESERVED_IP**: ID or name of the reserved IP.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--name**: The new name of the reserved IP.
- **--auto-delete**: Indicates whether this reserved IP member automatically deletes when either target is deleted, or the reserved IP is unbound. Must be false if the reserved IP is unbound. One of: **true**, **false**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-reserved-ip-delete
{: #subnet-reserved-ip-delete}

Release one or more reserved IPs.

```
ibmcloud is subnet-reserved-ip-delete SUBNET (RESERVED_IP1 RESERVED_IP2 ...) [--vpc VPC] [-f, --force] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnet-reserved-ip-delete}

- **SUBNET**: ID or name of the subnet.
- **RESERVED_IP1**: ID or name of the reserved IP.
- **RESERVED_IP2**: ID or name of the reserved IP.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--force, -f**: Force the operation without confirmation.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Virtual private clouds
{: #vpcs-cli-ref}

### ibmcloud is vpc
{: #vpc-view}

View details of a VPC.

```
ibmcloud is vpc VPC [--show-attached] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpc}

- **VPC**: ID or name of the VPC.
- **--show-attached**: View details of resources (subnets, VPC routes and address prefix) attached to this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-address-prefix
{: #vpc-address-prefix-view}

View details of a VPC address prefix.

```
ibmcloud is vpc-address-prefix VPC PREFIX [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-address-prefix}

- **VPC**: ID or name of the VPC.
- **PREFIX**: ID or name of the VPC address prefix.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-address-prefix-create
{: #vpc-address-prefix-create}

Create an address prefix.

```
ibmcloud is vpc-address-prefix-create PREFIX_NAME VPC ZONE_NAME CIDR [--default false | true] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpc-address-prefix-create}

- `ibmcloud is vpc-address-prefix-create my-prefix 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 us-south-2 10.0.0.0/24 --default true --output JSON`
- `ibmcloud is vpc-address-prefix-create my-prefix my-vpc us-south-2 10.0.0.0/24 --default true --output JSON`

#### Command options
{: #command-options-vpc-address-prefix-create}

- **PREFIX_NAME**: Name of the VPC address prefix.
- **VPC**: ID or name of the VPC.
- **ZONE_NAME**: Name of the zone.
- **CIDR**: The IPv4 range of the address prefix, expressed in CIDR format. It must not overlap with any existing address prefixes in the VPC, and must fall within the [RFC 1918](https://datatracker.ietf.org/doc/html/rfc1918) address ranges. The prefix length of the address prefix's CIDR must be between `/9` (8,388,608 addresses) and `/29` (eight addresses).
- **--default**: This flag indicates whether this is the default prefix for this zone in this VPC. One of: **false**, **true**. (default: **false**).
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-address-prefix-delete
{: #vpc-address-prefix-delete}

Delete one or more address prefixes.

```
ibmcloud is vpc-address-prefix-delete VPC (PREFIX1 PREFIX2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-address-prefix-delete}

- **VPC**: ID or name of the VPC.
- **PREFIX1**: ID or name of the VPC address prefix.
- **PREFIX2**: ID or name of the VPC address prefix.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-address-prefix-update
{: #vpc-address-prefix-update}

Update an address prefix.

```
ibmcloud is vpc-address-prefix-update VPC PREFIX [--name NEW_NAME] [--default false | true] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpc-address-prefix-update}

- `ibmcloud is vpc-address-prefix-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 fee82deba12e4c0fb69c3b09d1f12345 --name my-renamed-prefix --default false --output JSON`
- `ibmcloud is vpc-address-prefix-update my-vpc my-prefix --name my-renamed-prefix --default false --output JSON`

#### Command options
{: #command-options-vpc-address-prefix-update}

- **VPC**: ID or name of the VPC.
- **PREFIX**: ID or name of the VPC address prefix.
- **--name**: New name of the address prefix.
- **--default**: This flag indicates whether this is the default prefix for this zone in this VPC. One of: **false**, **true**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-address-prefixes
{: #vpc-address-prefixes-list}

List all address prefixes.

```
ibmcloud is vpc-address-prefixes VPC [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-address-prefixes}

- **VPC**: ID or name of the VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-create
{: #vpc-create}

Create a VPC.

```
ibmcloud is vpc-create VPC_NAME [--classic-access] [--address-prefix-management auto | manual] [[--dns-enable-hub false | true] [--dns-resolver-type manual | system] [--dns-resolver-manual-servers MANUAL_SERVERS | @MANUAL_SERVERS]] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpc-create}

- `ibmcloud is vpc-create my-vpc --address-prefix-management auto`
- `ibmcloud is vpc-create my-vpc --resource-group-id fee82deba12e4c0fb69c3b09d1f12345`
- `ibmcloud is vpc-create my-vpc --resource-group-name Default --output JSON`
- `ibmcloud is vpc-create my-vpc --dns-enable-hub true`
- `ibmcloud is vpc-create my-vpc --dns-enable-hub true --dns-resolver-type manual --dns-resolver-manual-servers ~/manualServers.json`
- `ibmcloud is vpc-create my-vpc --dns-enable-hub true --dns-resolver-type manual --dns-resolver-manual-servers '[{"address": "190.20.3.0"},{"address": "190.20.3.1"},{"address": "190.20.3.2"}]'`

#### Command options
{: #command-options-vpc-create}

- **VPC_NAME**: Name of the VPC.
- **--classic-access**: [Deprecated] Instead, you can use Transit Gateway to connect your VPCs to the Classic infrastructure network. This flag indicates whether the VPC must be connected to your Classic infrastructure. The default value is false.
- **--address-prefix-management**: This flag indicates whether a default address prefix is automatically created for each zone in this VPC. If **manual**, this VPC is created with no default address prefixes. One of: **auto**, **manual**. (default: **auto**).
- **--dns-enable-hub**: Indicates whether this VPC is enabled as a DNS name resolution hub. One of: **false**, **true**.
- **--dns-resolver-type**: The type of the DNS resolver to use. One of: **manual**, **system**.
- **--dns-resolver-manual-servers**: MANUAL_SERVERS|@MANUAL_SERVERS, manual servers in JSON or JSON file.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-default-security-group
{: #vpc-default-security-group-view}

View details of the default security group of a VPC.

```
ibmcloud is vpc-default-security-group VPC [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-default-security-group}

- **VPC**: ID or name of the VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-delete
{: #vpc-delete}

Delete one or more VPCs.

```
ibmcloud is vpc-delete (VPC1 VPC2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-delete}

- **VPC1**: ID or name of the VPC.
- **VPC2**: ID or name of the VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-update
{: #vpc-update}

Update a VPC.

```
ibmcloud is vpc-update VPC --name NEW_NAME [[--dns-enable-hub false | true] [--dns-resolver-type manual | system | delegated] [--dns-resolver-manual-servers MANUAL_SERVERS | @MANUAL_SERVERS] [--delegate-to-vpc DELEGATE_TO_VPC]] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpc-update}

- `ibmcloud is vpc-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-renamed-vpc`
- `ibmcloud is vpc-update my-vpc --name my-renamed-vpc`
- `ibmcloud is vpc-update my-vpc --dns-enable-hub true`
- `ibmcloud is vpc-update my-vpc --dns-enable-hub true --dns-resolver-type manual --dns-resolver-manual-servers @~/manualServers.json`
- `ibmcloud is vpc-update my-vpc --dns-enable-hub true --dns-resolver-type manual --dns-resolver-manual-servers '[{"address": "190.20.3.0"},{"address": "190.20.3.1"},{"address": "190.20.3.2"}]'`
- `ibmcloud is vpc-update my-vpc --dns-resolver-type delegated --delegate-to-vpc 72251a2e-d6c5-42b4-97b0-b5f727d1f479`
- `ibmcloud is vpc-update my-vpc --dns-resolver-type delegated --delegate-to-vpc my-delegated-vpc`

#### Command options
{: #command-options-vpc-update}

- **VPC**: ID or name of the VPC.
- **--name**: New name of the VPC.
- **--dns-enable-hub**: Indicates whether this VPC is enabled as a DNS name resolution hub. One of: **false**, **true**.
- **--dns-resolver-type**: The type of the DNS resolver to use. One of: **manual**, **system**, **delegated**.
- **--dns-resolver-manual-servers**: MANUAL_SERVERS|@MANUAL_SERVERS, manual servers in JSON or JSON file.
- **--delegate-to-vpc**: The ID or name of the VPC to provide DNS server addresses for this VPC. Must be set if and only if resolver type is delegated.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpcs
{: #vpcs-list}

List all VPCs.

```
ibmcloud is vpcs [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--classic-access true | false] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpcs}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--classic-access**: [Deprecated] Instead, you can use Transit Gateway to connect your VPCs to the Classic infrastructure network. This flag lists VPCs that enabled for Classic access. If unspecified, it returns all VPCs with and without Classic access enabled. One of: **true**, **false**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-dns-resolution-binding-create
{: #vpc-dns-resolution-binding-create}

Create a DNS resolution binding.

```
ibmcloud is vpc-dns-resolution-binding-create VPC --target-vpc TARGET_VPC [--name NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpc-dns-resolution-binding-create}

- `ibmcloud is vpc-dns-resolution-binding-create my-vpc --name my-dns-res-binding --target-vpc my-dns-binding-vpc --output JSON`
- `ibmcloud is vpc-dns-resolution-binding-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-dns-res-binding --target-vpc my-dns-binding-vpc --output JSON`

#### Command options
{: #command-options-vpc-dns-resolution-binding-create}

- **VPC**: ID or name of the VPC.
- **--name**: The name for this DNS resolution binding.
- **--target-vpc**: ID, name or CRN of another VPC to bind this VPC for DNS resolution.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-dns-resolution-binding
{: #vpc-dns-resolution-binding-view}

View details of a VPC DNS resolution binding.

```
ibmcloud is vpc-dns-resolution-binding VPC DNS_RESOLUTION_BINDING [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-dns-resolution-binding}

- **VPC**: ID or name of the VPC.
- **DNS_RESOLUTION_BINDING**: ID or name of the VPC DNS resolution binding.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-dns-resolution-binding-update
{: #vpc-dns-resolution-binding-update}

Update a DNS resolution binding.

```
ibmcloud is vpc-dns-resolution-binding-update VPC DNS_RESOLUTION_BINDING [--name NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpc-dns-resolution-binding-update}

- `ibmcloud is vpc-dns-resolution-binding-update r134-e5b9726b-c975-46bd-b713-c8aea55d51d8 r134-75ccea7b-c705-4b50-934d-2152f9eab4ec --name my-dns-resolution-updated --output JSON`
- `ibmcloud is vpc-dns-resolution-binding-update my-vpc my-dns-resolution-binding --name my-dns-resolution-binding-updated --output JSON`

#### Command options
{: #command-options-vpc-dns-resolution-binding-update}

- **VPC**: ID or name of the VPC.
- **DNS_RESOLUTION_BINDING**: ID or name of the VPC DNS resolution binding.
- **--name**: The name for this DNS resolution binding.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-dns-resolution-binding-delete
{: #vpc-dns-resolution-binding-delete}

Delete one or more DNS resolution bindings.

```
ibmcloud is vpc-dns-resolution-binding-delete VPC (DNS_RESOLUTION_BINDING1 DNS_RESOLUTION_BINDING2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-dns-resolution-binding-delete}

- **VPC**: ID or name of the VPC.
- **DNS_RESOLUTION_BINDING1**: ID or name of the VPC DNS resolution binding.
- **DNS_RESOLUTION_BINDING2**: ID or name of the VPC DNS resolution binding.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-dns-resolution-bindings
{: #vpc-dns-resolution-bindings-list}

List all DNS resolution bindings.

```
ibmcloud is vpc-dns-resolution-bindings VPC [--account-id ACCOUNT_ID] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-dns-resolution-bindings}

- **VPC**: ID or name of the VPC.
- **--account-id**: ID of the account for this access policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Virtual private endpoint gateways
{: #vpe-clis}

The following section gives details about the CLI commands that are available for working with endpoint gateways.

### ibmcloud is endpoint-gateway-targets
{: #endpoint-gateway-targets-list}

List all resources can be set as target for endpoint gateway in all regions.

```
ibmcloud is endpoint-gateway-targets [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-endpoint-gateway-targets}

- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is endpoint-gateway
{: #endpoint-gateway-view}

View details of an endpoint gateway.

```
ibmcloud is endpoint-gateway ENDPOINT_GATEWAY [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-endpoint-gateway}

- **ENDPOINT_GATEWAY**: ID or name of the endpoint gateway.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is endpoint-gateways
{: #endpoint-gateways-list}

List all endpoint gateways in the region.

```
ibmcloud is endpoint-gateways [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--vpc VPC] [--allow-dns-resolution-binding false | true] [--lifecycle-state LIFECYCLE_STATE] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-endpoint-gateways}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--vpc**: ID, name, or CRN of the VPC.
- **--allow-dns-resolution-binding**: Allow DNS resolution binding One of: **false**, **true**.
- **--lifecycle-state**: Filters the collection to resources with the `lifecycle_state` property that matches one of the specified comma-separated values of: deleting, failed, pending, stable, suspended, updating, waiting.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is endpoint-gateway-create
{: #endpoint-gateway-create}

Create an endpoint gateway.

```
ibmcloud is endpoint-gateway-create --target TARGET [--target-type private_path_service_gateway | provider_cloud_service | provider_infrastructure_service] [--vpc VPC] [--name NAME] [--rip RIP --subnet SUBNET | (--new-reserved-ip NEW_RESERVED_IP1 --new-reserved-ip NEW_RESERVED_IP2 ...)] [--allow-dns-resolution-binding false | true] [--sg SG] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-endpoint-gateway-create}

- `ibmcloud is endpoint-gateway-create --vpc 417f1275-b11a-4077-8755-84e795bc3172 --target crn:v1:bluemix:public:kms:us-south:a/86e1130a970148348271c47ed80ac3f3:7372408d-b68a-47f5-b5e5-4b64390aebff:: --name myegw1`
Create endpoint gateway without binding reserved IP.
- `ibmcloud is endpoint-gateway-create --vpc my-vpc --target crn:v1:bluemix:public:kms:us-south:a/86e1130a970148348271c47ed80ac3f3:7372408d-b68a-47f5-b5e5-4b64390aebff:: --name myegw1`
Create endpoint gateway with vpc name without binding reserved IP.
- `ibmcloud is endpoint-gateway-create --vpc 4215db60-4515-4a5f-9822-341d8bea5985 --target crn:v1:bluemix:public:kms:us-south:a/86e1130a970148348271c47ed80ac3f3:7372408d-b68a-47f5-b5e5-4b64390aebff:: --name myegw2 --new-reserved-ip '{"subnet": {"id": "a529e1b9-d4cf-48a0-a1bb-e9a1d32cb6e7"}}'`
Create endpoint gateway with binding new reserved IP configuration with only required subnet ID data.
- `ibmcloud is endpoint-gateway-create --vpc my-vpc --target crn:v1:bluemix:public:kms:us-south:a/86e1130a970148348271c47ed80ac3f3:7372408d-b68a-47f5-b5e5-4b64390aebff:: --name myegw2 --new-reserved-ip '{"subnet": {"name": "my-subnet"}}'`
Create endpoint gateway with binding new reserved IP configuration with only required subnet name data.
- `ibmcloud is endpoint-gateway-create --vpc 4215db60-4515-4a5f-9822-341d8bea5985 --target crn:v1:bluemix:public:kms:us-south:a/86e1130a970148348271c47ed80ac3f3:7372408d-b68a-47f5-b5e5-4b64390aebff:: --name myegw2 --new-reserved-ip '{"subnet": {"id": "a529e1b9-d4cf-48a0-a1bb-e9a1d32cb6e7"},"name":"my-reserved-ip1","auto_delete":false}'`
Create endpoint gateway with binding new reserved IP configuration with subnet ID, reserved IP name, reserved IP auto_delete configuration.
- `ibmcloud is endpoint-gateway-create --vpc my-vpc --target crn:v1:bluemix:public:kms:us-south:a/86e1130a970148348271c47ed80ac3f3:7372408d-b68a-47f5-b5e5-4b64390aebff:: --name myegw2 --new-reserved-ip '{"subnet": {"name": "my-subnet"},"name":"my-reserved-ip1","auto_delete":false}'`
Create endpoint gateway with binding new reserved IP configuration with subnet name, reserved IP name, reserved IP auto_delete configuration.
- `ibmcloud is endpoint-gateway-create --vpc 417f1275-b11a-4077-8755-84e795bc3172 --target ibm-ntp-server --name myegw3`
Create endpoint gateway with the provider infrastructure service 'ibm-ntp-server'.
- `ibmcloud is endpoint-gateway-create --vpc 417f1275-b11a-4077-8755-84e795bc3172 --target ibm-ntp-server --name my-egw --rip 0757-aabb6555-7de5-4a53-aac1-03dd3a50e377,0767-799bd24a-7d85-4ffa-9920-6e51c4001d02`
Create endpoint gateway with binding existing reserved IP IDs.
- `ibmcloud is endpoint-gateway-create --vpc my-vpc --target ibm-ntp-server --name my-egw --rip my-rip --subnet my-subnet`
Create endpoint gateway with binding existing reserved IP name.
- `ibmcloud is egc --target crn:v1:bluemix:public:kms:us-south:a/86e1130a970148348271c47ed80ac3f3:7372408d-b68a-47f5-b5e5-4b64390aebff:: --vpc b224ead6-b835-473c-ad6b-bc91840829c3  --allow-dns-resolution-binding false --name my-cli-egw`
Create endpoint gateway and allow to participate in DNS resolution bindings with a VPC
- `ibmcloud is endpoint-gateway-create --target-type private_path_service_gateway --target crn:v1:staging:public:is:us-south:aefe5afc483594adaa8325e2b4d1290df::private-path-service-gateway:r134-f5926633-81d0-429e-bcf8-91151ade00bf --vpc cli-vpc`
Create endpoint gateway for a Private Path service gateway.
- `ibmcloud is endpoint-gateway-create --vpc 417f1275-b11a-4077-8755-84e795bc3172 --target crn:v1:bluemix:public:kms:us-south:a/86e1130a970148348271c47ed80ac3f3:7372408d-b68a-47f5-b5e5-4b64390aebff:: --name myegw1 --sg r006-dfd5e7a2-0f6d-47d3-b46a-567430f1d70c,r006-e60eba9b-7c88-49ae-b8e1-05bd76d39d66`
Create endpoint gateway with security groups.
- `ibmcloud is endpoint-gateway-create --vpc my-vpc --target crn:v1:bluemix:public:kms:us-south:a/86e1130a970148348271c47ed80ac3f3:7372408d-b68a-47f5-b5e5-4b64390aebff:: --name myegw1 --sg my-sg,my-sg2`
Create endpoint gateway with security groups in name format.
- `ibmcloud is endpoint-gateway-create --vpc 4215db60-4515-4a5f-9822-341d8bea5985 --target crn:v1:bluemix:public:kms:us-south:a/86e1130a970148348271c47ed80ac3f3:7372408d-b68a-47f5-b5e5-4b64390aebff:: --name newEG1 --new-reserved-ip '{"subnet": {"id": "ab6599a8-12ac-4546-b983-8040458fd339"}, "address": "34.218.28.200", "name": "myreservedip1", "auto_delete": false}'`
Create endpoint gateway with binding specified new reserved IP configuration that has all of the reserved IP configuration options.
- `ibmcloud is endpoint-gateway-create --vpc my-vpc --target crn:v1:bluemix:public:kms:us-south:a/86e1130a970148348271c47ed80ac3f3:7372408d-b68a-47f5-b5e5-4b64390aebff:: --name newEG1 --new-reserved-ip '{"subnet": {"name": "my-subnet"}, "address": "34.218.28.200", "name": "myreservedip1", "auto_delete": false}'`
Create endpoint gateway with binding-specified, new reserved IP configuration that has all of the reserved IP configuration options and subnet is in name format.

#### Command options
{: #command-options-endpoint-gateway-create}

- **--target-type**: The type of target for this endpoint gateway. One of: **private_path_service_gateway**, **provider_cloud_service**, **provider_infrastructure_service**.
- **--vpc**: ID or name of the VPC.
- **--target**: The name of the provider infrastructure service or the CRN for a provider cloud service instance. You can use command **ibmcloud is endpoint-gateway-targets** to list the provider cloud and infrastructure services that are qualified to be set as endpoint gateway target.
- **--name**: New name of the endpoint gateway.
- **--rip**: Comma-separated IDs of the reserved IP to be bound to the endpoint gateway. At most, one reserved IP per zone is allowed. It can also be reserved IP name, but only one reserved IP name is allowed and subnet option for this reserved IP name also must be supplied.
- **--subnet**: ID or name of the subnet. This name is required only if the supplied reserved IP is in name format.
- **--new-reserved-ip**: RESERVED_IP_JSON|@RESERVED_IP_JSON_FILE, new reserved IP configuration in JSON or JSON file.
- **--allow-dns-resolution-binding**: Allow DNS resolution binding One of: **false**, **true**.
- **--sg**: Comma-separated security group IDs or names for the endpoint gateway.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is endpoint-gateway-update
{: #endpoint-gateway-update}

Update an endpoint gateway.

```
ibmcloud is endpoint-gateway-update ENDPOINT_GATEWAY --name NEW_NAME [--vpc VPC] [--allow-dns-resolution-binding false | true] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-endpoint-gateway-update}

- `ibmcloud is egu 4325b873-33db-48aa-a98e-601177fd745f --vpc b224ead6-b835-473c-ad6b-bc91840829c3  --allow-dns-resolution-binding true --name my-cli-egw`
Update an endpoint gateway and allow to participate in DNS resolution bindings with a VPC.

#### Command options
{: #command-options-endpoint-gateway-update}

- **ENDPOINT_GATEWAY**: ID or name of the endpoint gateway.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--name**: New name of the endpoint gateway.
- **--allow-dns-resolution-binding**: Allow DNS resolution binding One of: **false**, **true**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is endpoint-gateway-reserved-ip-bind
{: #endpoint-gateway-reserved-ip-bind}

Bind a reserved IP to an endpoint gateway.

```
ibmcloud is endpoint-gateway-reserved-ip-bind ENDPOINT_GATEWAY (--rip RIP [--subnet SUBNET]) [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-endpoint-gateway-reserved-ip-bind}

- **ENDPOINT_GATEWAY**: ID or name of the endpoint gateway.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--rip**: ID or name of the reserved IP address to be bound.
- **--subnet**: ID or name of the subnet. This name is required only if the supplied reserved IP is in name format.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is endpoint-gateway-reserved-ip-unbind
{: #endpoint-gateway-reserved-ip-unbind}

Unbind a reserved IP to an endpoint gateway.

```
ibmcloud is endpoint-gateway-reserved-ip-unbind ENDPOINT_GATEWAY ((--rip RIP [--subnet SUBNET]) | --address ADDRESS) [--vpc VPC] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-endpoint-gateway-reserved-ip-unbind}

- **ENDPOINT_GATEWAY**: ID or name of the endpoint gateway.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--address**: The reserved IP address to be unbound.
- **--rip**: ID or name of the reserved IP address to be unbound.
- **--subnet**: ID or name of the subnet. This name is required only if the supplied reserved IP is in name format.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is endpoint-gateway-delete
{: #endpoint-gateway-delete}

Delete one or more endpoint gateways.

```
ibmcloud is endpoint-gateway-delete (ENDPOINT_GATEWAY1 ENDPOINT_GATEWAY2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-endpoint-gateway-delete}

- **ENDPOINT_GATEWAY1**: ID or name of the endpoint gateway.
- **ENDPOINT_GATEWAY2**: ID or name of the endpoint gateway.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

## Virtual network interface
{: #vni-clis}

The following section gives details about the CLI commands that are available for working with virtual network interface.

### ibmcloud is virtual-network-interface
{: #virtual-network-interface-view}

View details of a virtual network interface.

```
ibmcloud is virtual-network-interface VIRTUAL_NETWORK_INTERFACE [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-virtual-network-interface}

- `ibmcloud is virtual-network-interface r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2`
- `ibmcloud is virtual-network-interface new-share-vni`

#### Command options
{: #command-options-virtual-network-interface}

- **VIRTUAL_NETWORK_INTERFACE**: ID or name of the virtual network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is virtual-network-interfaces
{: #virtual-network-interfaces-list}

List all virtual network interfaces.

```
ibmcloud is virtual-network-interfaces [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-virtual-network-interfaces}

- `ibmcloud is virtual-network-interfaces`

#### Command options
{: #command-options-virtual-network-interfaces}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is virtual-network-interface-update
{: #virtual-network-interface-update}

Update a virtual network interface.

```
ibmcloud is virtual-network-interface-update VIRTUAL_NETWORK_INTERFACE --name NEW_NAME [--allow-ip-spoofing false | true] [--auto-delete false | true] [--enable-infrastructure-nat false | true] [--protocol-state-filtering-mode, --psfm auto | enabled | disabled] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-virtual-network-interface-update}

- `ibmcloud is virtual-network-interface-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-vni`
- `ibmcloud is virtual-network-interface-update new-vni --name new-share`
- `ibmcloud is virtual-network-interface-update 7208-8918786e-5958-42fc-9e4b-410c5a58b164 --name cli-vni-1 --allow-ip-spoofing false --auto-delete false --enable-infrastructure-nat false`
- `ibmcloud is virtual-network-interface-update cli-vni-1 --name cli-vni-2 --allow-ip-spoofing false --auto-delete true --enable-infrastructure-nat false`
- `ibmcloud is virtual-network-interface-update cli-vni-1 --name cli-vni-2 --allow-ip-spoofing false --protocol-state-filtering-mode enabled --auto-delete true --enable-infrastructure-nat false`

#### Command options
{: #command-options-virtual-network-interface-update}

- **VIRTUAL_NETWORK_INTERFACE**: ID or name of the virtual network interface.
- **--name**: New name of the virtual network interface.
- **--allow-ip-spoofing**: Indicates whether source IP spoofing is allowed on this interface. If false, source IP spoofing is prevented on this interface. If true, source IP spoofing is allowed on this interface. One of: **false**, **true**.
- **--auto-delete**: Indicates whether this virtual network interface automatically deletes when the target is deleted. Must be false if the virtual network interface is unbound. One of: **false**, **true**.
- **--enable-infrastructure-nat**: If true: The VPC infrastructure performs any needed NAT operations. If false: Packets are passed unchanged to and from the network interface, which allows the workload to perform any needed NAT operations. One of: **false**, **true**.
- **--protocol-state-filtering-mode**: auto,--psfm auto  The protocol state filtering mode to use for this virtual network interface. If auto, protocol state packet filtering is enabled or disabled based on the virtual network interface's `target` resource type. One of: **auto**, **enabled**, **disabled**. (default: **auto**).
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is virtual-network-interface-create
{: #virtual-network-interface-create}

Create a virtual network interface.

```
ibmcloud is virtual-network-interface-create [--name NAME] [--allow-ip-spoofing false | true] [--auto-delete false | true] [--enable-infrastructure-nat false | true] [[--rip RIP | [--rip-address RIP_ADDRESS --rip-auto-delete RIP_AUTO_DELETE --rip-name RIP_NAME]]] [--protocol-state-filtering-mode, --psfm auto | enabled | disabled] [--subnet SUBNET] [--ips RESERVED_IPS_JSON | @RESERVED_IPS_JSON_FILE] [--sgs SGS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-virtual-network-interface-create}

- `ibmcloud is virtual-network-interface-create --name cli-vni-1 --allow-ip-spoofing true --auto-delete true --enable-infrastructure-nat true --rip 7208-d4c0abbe-3fc2-4696-9fe1-4eb3dc9af976  --ips '[{"id":"7208-d83b7e58-3c3d-47d0-89c5-02d9a20c72fd"},{"address":"10.240.64.13", "auto_delete": false, "name": "srip2"}]' --sgs r134-aa7c7658-e503-4456-b342-8d6a89e05115,r134-4fb388f1-2b6e-4013-b279-7a8748f4d6ca --resource-group-id 11caaa983d9c4beb82690daab08717e9`
- `ibmcloud is virtual-network-interface-create --name cli-vni-2 --allow-ip-spoofing true --auto-delete true --enable-infrastructure-nat true --rip cli-rip-1 --subnet my-subnet --vpc vpc-cli-1 --ips '[{"id":"7208-d83b7e58-3c3d-47d0-89c5-02d9a20c72fd"},{"address":"10.240.64.14", "auto_delete": false, "name": "srip3"}]' --sgs cli-sg,sanctity-contest-only-filing --resource-group-name Default`
- `ibmcloud is virtual-network-interface-create --name cli-vni-4 --allow-ip-spoofing false --auto-delete false --enable-infrastructure-nat false --subnet 7208-bfe017e7-6e71-415a-8615-0ee787fbeef9 --rip-address 10.240.64.15 --rip-auto-delete false --rip-name primar-ip-1  --ips '[{"id":"7208-2772a45f-c062-4e22-bafb-32ea792da56b"},{"address":"10.240.64.17", "auto_delete": false, "name": "sec-ip-2"}]' --sgs r134-aa7c7658-e503-4456-b342-8d6a89e05115,r134-4fb388f1-2b6e-4013-b279-7a8748f4d6ca --resource-group-id 11caaa983d9c4beb82690daab08717e9`
- `ibmcloud is virtual-network-interface-create --name cli-vni-3 --allow-ip-spoofing true --auto-delete false --enable-infrastructure-nat true --subnet my-subnet --vpc vpc-cli-1 --rip-address 10.240.64.18 --rip-auto-delete true --rip-name primar-ip-2  --ips '[{"id":"7208-d42716a5-6df2-416c-979d-f26330b9d0b1"},{"address":"10.240.64.19", "auto_delete": true, "name": "sec-ip-3"}]' --sgs cli-sg,sanctity-contest-only-filing  --resource-group-name Default`
- `ibmcloud is virtual-network-interface-create --name cli-vni-3 --allow-ip-spoofing true --auto-delete false --protocol-state-filtering-mode disabled --enable-infrastructure-nat true --subnet my-subnet --vpc vpc-cli-1 --rip-address 10.240.64.18 --rip-auto-delete true --rip-name primar-ip-2  --ips '[{"id":"7208-d42716a5-6df2-416c-979d-f26330b9d0b1"},{"address":"10.240.64.19", "auto_delete": true, "name": "sec-ip-3"}]' --sgs cli-sg,sanctity-contest-only-filing  --resource-group-name Default`

#### Command options
{: #command-options-virtual-network-interface-create}

- **--name**: The name for this virtual network interface.
- **--allow-ip-spoofing**: Indicates whether source IP spoofing is allowed on this interface. If false, source IP spoofing is prevented on this interface. If true, source IP spoofing is allowed on this interface. One of: **false**, **true**.
- **--auto-delete**: Indicates whether this virtual network interface automatically deletes when the target is deleted. Must be false if the virtual network interface is unbound. One of: **false**, **true**.
- **--enable-infrastructure-nat**: If true: The VPC infrastructure performs any needed NAT operations. If false: Packets are passed unchanged to and from the network interface, which allows the workload to perform any needed NAT operations. One of: **false**, **true**.
- **--rip**: ID or name of the reserved IP to bind to the virtual network interface.
- **--rip-address**: The IP address of the reserved IP to bind to the virtual network interface.
- **--rip-auto-delete**: Indicates whether this reserved IP automatically deletes when either target is deleted, or the reserved IP is unbound.
- **--rip-name**: The name for this reserved IP to bind to the virtual network interface.
- **--protocol-state-filtering-mode**: auto,--psfm auto  The protocol state filtering mode to use for this virtual network interface. If auto, protocol state packet filtering is enabled or disabled based on the virtual network interface's `target` resource type. One of: **auto**, **enabled**, **disabled**. (default: **auto**).
- **--subnet**: The associated subnet.
- **--ips**: IPS RESERVED_IPS_JSON | @RESERVED_IPS_JSON_FILE, Secondary reserved IP addresses in JSON or JSON file, to bind to the virtual network interface. For the data schema, check the IPS property in the [API documentation](/apidocs/vpc/latest#create-virtual-network-interface). One of: **RESERVED_IPS_JSON**, **@RESERVED_IPS_JSON_FILE**.
- **--sgs**: IDs or names of the security groups to use for the virtual network interface.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--vpc**: ID or name of the VPC to which this VNI is associated to.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is virtual-network-interface-delete
{: #virtual-network-interface-delete}

Delete one or more virtual network interfaces.

```
ibmcloud is virtual-network-interface-delete (VIRTUAL_NETWORK_INTERFACE1 VIRTUAL_NETWORK_INTERFACE2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-virtual-network-interface-delete}

- `ibmcloud is virtual-network-interface-delete  my-vni-share-99  cli-vni-demo-00`
- `ibmcloud is virtual-network-interface-delete  r006-866fc826-6f30-444f-b55e-0d697cf8b4bb`

#### Command options
{: #command-options-virtual-network-interface-delete}

- **VIRTUAL_NETWORK_INTERFACE1**: ID or name of the virtual network interface.
- **VIRTUAL_NETWORK_INTERFACE2**: ID or name of the virtual network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is virtual-network-interface-floating-ip
{: #virtual-network-interface-floating-ip-view}

View details of a floating IP that is associated with virtual network interface.

```
ibmcloud is virtual-network-interface-floating-ip VIRTUAL_NETWORK_INTERFACE FLOATING_IP [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-virtual-network-interface-floating-ip}

- `ibmcloud is virtual-network-interface-floating-ip cli-vni-2 cli-ip-2`
- `ibmcloud is virtual-network-interface-floating-ip 7208-a666bd40-c065-4feb-8815-1cbb81313e08 r134-90b991ee-7da1-404a-91d6-64aa91e43292`

#### Command options
{: #command-options-virtual-network-interface-floating-ip}

- **VIRTUAL_NETWORK_INTERFACE**: ID or name of the virtual network interface.
- **FLOATING_IP**: ID or name of the floating IP.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is virtual-network-interface-floating-ips
{: #virtual-network-interface-floating-ips-list}

List all floating IPs that are associated with virtual network interface.

```
ibmcloud is virtual-network-interface-floating-ips VIRTUAL_NETWORK_INTERFACE [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-virtual-network-interface-floating-ips}

- `ibmcloud is virtual-network-interface-floating-ips 7208-8918786e-5958-42fc-9e4b-410c5a58b164`
- `ibmcloud is virtual-network-interface-floating-ips cli-vni-2`

#### Command options
{: #command-options-virtual-network-interface-floating-ips}

- **VIRTUAL_NETWORK_INTERFACE**: ID or name of the virtual network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is virtual-network-interface-floating-ip-add
{: #virtual-network-interface-floating-ip-add}

Associate a floating IP with virtual network interface.

```
ibmcloud is virtual-network-interface-floating-ip-add VIRTUAL_NETWORK_INTERFACE FLOATING_IP [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-virtual-network-interface-floating-ip-add}

- `ibmcloud is virtual-network-interface-floating-ip-add cli-vni-1 cli-ip`
- `ibmcloud is virtual-network-interface-floating-ip-add 7208-a666bd40-c065-4feb-8815-1cbb81313e08 r134-90b991ee-7da1-404a-91d6-64aa91e43292`

#### Command options
{: #command-options-virtual-network-interface-floating-ip-add}

- **VIRTUAL_NETWORK_INTERFACE**: ID or name of the virtual network interface.
- **FLOATING_IP**: ID or name of the floating IP.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is virtual-network-interface-floating-ip-remove
{: #virtual-network-interface-floating-ip-remove}

Disassociate a floating IP from virtual network interface.

```
ibmcloud is virtual-network-interface-floating-ip-remove VIRTUAL_NETWORK_INTERFACE FLOATING_IP [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-virtual-network-interface-floating-ip-remove}

- `ibmcloud is virtual-network-interface-floating-ip-remove cli-vni-2 cli-ip-2`
- `ibmcloud is virtual-network-interface-floating-ip-remove 7208-a8c7311c-938e-452d-a89e-3e6f282583e0 r134-90b991ee-7da1-404a-91d6-64aa91e43292`

#### Command options
{: #command-options-virtual-network-interface-floating-ip-remove}

- **VIRTUAL_NETWORK_INTERFACE**: ID or name of the virtual network interface.
- **FLOATING_IP**: ID or name of the floating IP.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is virtual-network-interface-reserved-ip
{: #virtual-network-interface-reserved-ip-view}

View details of a reserved IP that is associated with virtual network interface.

```
ibmcloud is virtual-network-interface-reserved-ip VIRTUAL_NETWORK_INTERFACE RESERVED_IP [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-virtual-network-interface-reserved-ip}

- `ibmcloud is virtual-network-interface-reserved-ip cli-vni-2 cli-rip-2`
- `ibmcloud is virtual-network-interface-reserved-ip 7208-a666bd40-c065-4feb-8815-1cbb81313e08 r134-90b991ee-7da1-404a-91d6-64aa91e43292`

#### Command options
{: #command-options-virtual-network-interface-reserved-ip}

- **VIRTUAL_NETWORK_INTERFACE**: ID or name of the virtual network interface.
- **RESERVED_IP**: ID or name of the reserved IP.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is virtual-network-interface-reserved-ips
{: #virtual-network-interface-reserved-ips-list}

List all reserved IPs that are associated with virtual network interface.

```
ibmcloud is virtual-network-interface-reserved-ips VIRTUAL_NETWORK_INTERFACE [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-virtual-network-interface-reserved-ips}

- `ibmcloud is virtual-network-interface-reserved-ips 7208-8918786e-5958-42fc-9e4b-410c5a58b164`
- `ibmcloud is virtual-network-interface-reserved-ips cli-vni-2`

#### Command options
{: #command-options-virtual-network-interface-reserved-ips}

- **VIRTUAL_NETWORK_INTERFACE**: ID or name of the virtual network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is virtual-network-interface-reserved-ip-bind
{: #virtual-network-interface-reserved-ip-bind}

Bind a reserved IP to virtual network interface.

```
ibmcloud is virtual-network-interface-reserved-ip-bind VIRTUAL_NETWORK_INTERFACE RESERVED_IP [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-virtual-network-interface-reserved-ip-bind}

- `ibmcloud is virtual-network-interface-reserved-ip-bind cli-vni-1 cli-rip`
- `ibmcloud is virtual-network-interface-reserved-ip-bind 7208-a666bd40-c065-4feb-8815-1cbb81313e08 r134-90b991ee-7da1-404a-91d6-64aa91e43292`

#### Command options
{: #command-options-virtual-network-interface-reserved-ip-bind}

- **VIRTUAL_NETWORK_INTERFACE**: ID or name of the virtual network interface.
- **RESERVED_IP**: ID or name of the reserved IP.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is virtual-network-interface-reserved-ip-unbind
{: #virtual-network-interface-reserved-ip-unbind}

Unbind a reserved IP from virtual network interface.

```
ibmcloud is virtual-network-interface-reserved-ip-unbind VIRTUAL_NETWORK_INTERFACE RESERVED_IP [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-virtual-network-interface-reserved-ip-unbind}

- `ibmcloud is virtual-network-interface-reserved-ip-unbind cli-vni-2 cli-rip-2`
- `ibmcloud is virtual-network-interface-reserved-ip-unbind 7208-a8c7311c-938e-452d-a89e-3e6f282583e0 r134-90b991ee-7da1-404a-91d6-64aa91e43292`

#### Command options
{: #command-options-virtual-network-interface-reserved-ip-unbind}

- **VIRTUAL_NETWORK_INTERFACE**: ID or name of the virtual network interface.
- **RESERVED_IP**: ID or name of the reserved IP.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

## Private Path service gateways
{: #ppsg-clis}

The following section gives details about the CLI commands that are available for working with Private Path service gateways.

### ibmcloud is private-path-service-gateways
{: #private-path-service-gateways-list}

List all Private Path service gateways.

```
ibmcloud is private-path-service-gateways [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-private-path-service-gateways}

- `ibmcloud is private-path-service-gateways`

#### Command options
{: #command-options-private-path-service-gateways}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is private-path-service-gateway
{: #private-path-service-gateway-view}

View details of a Private Path service gateway.

```
ibmcloud is private-path-service-gateway PRIVATE_PATH_SERVICE_GATEWAY [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-private-path-service-gateway}

- `ibmcloud is ppsg r134-2e671f14-19fc-4089-9ad3-973176711259`
- `ibmcloud is private-path-service-gateway cli-ppsg-0`

#### Command options
{: #command-options-private-path-service-gateway}

- **PRIVATE_PATH_SERVICE_GATEWAY**: ID or name of the Private Path service gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is private-path-service-gateway-create
{: #private-path-service-gateway-create}

Create a Private Path service gateway.

```
ibmcloud is private-path-service-gateway-create --load-balancer LOAD_BALANCER --service-endpoints SERVICE_ENDPOINTS [--default-access-policy deny | permit | review] [--name NAME] [--zonal-affinity false | true] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-private-path-service-gateway-create}

- `ibmcloud is private-path-service-gateway-create --load-balancer my-cli-nlb  --service-endpoints cli.domain.com --default-access-policy permit --name cli-ppsg-1 --zonal-affinity true`
- `ibmcloud is private-path-service-gateway-create --load-balancer r134-d-439744e1-81d7-43fb-95d5-2356774240bb  --service-endpoints clidemo.domain.com --default-access-policy deny --name cli-ppsg-2 --zonal-affinity true`

#### Command options
{: #command-options-private-path-service-gateway-create}

- **--default-access-policy**: The policy to use for bindings from accounts without an explicit account policy. One of: **deny**, **permit**, **review**. (default: **deny**).
- **--load-balancer**: ID or name of load balancer for this Private Path gateway.
- **--name**: The name for this Private Path service gateway.
- **--service-endpoints**: The fully qualified domain names for this Private Path service gateway. Any uppercase letters are converted to lowercase.
- **--zonal-affinity**: Indicates whether this Private Path service gateway has zonal affinity. One of: **false**, **true**.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is private-path-service-gateway-update
{: #private-path-service-gateway-update}

Update a Private Path service gateway.

```
ibmcloud is private-path-service-gateway-update PRIVATE_PATH_SERVICE_GATEWAY [--default-access-policy deny | permit | review] [--load-balancer LOAD_BALANCER] [--zonal-affinity false | true] [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-private-path-service-gateway-update}

- `ibmcloud is private-path-service-gateway-update r134-2e671f14-19fc-4089-9ad3-973176711259 --name cli-ppsg-2 --default-access-policy deny --load-balancer r134-d-740be75d-be41-48bd-b6e4-89946ddcac4a  --zonal-affinity false`
- `ibmcloud is private-path-service-gateway-update cli-ppsg-2 --name cli-ppsg-0 --default-access-policy review --load-balancer my-cli-nlb-1  --zonal-affinity false`

#### Command options
{: #command-options-private-path-service-gateway-update}

- **PRIVATE_PATH_SERVICE_GATEWAY**: ID or name of the Private Path service gateway.
- **--default-access-policy**: The policy to use for bindings from accounts without an explicit account policy. One of: **deny**, **permit**, **review**. (default: **deny**).
- **--load-balancer**: ID or name of load balancer for this Private Path gateway.
- **--zonal-affinity**: Indicates whether this Private Path service gateway has zonal affinity. One of: **false**, **true**.
- **--name**: New name of the Private Path service gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is private-path-service-gateway-delete
{: #private-path-service-gateway-delete}

Delete one or more Private Path service gateways.

```
ibmcloud is private-path-service-gateway-delete (PRIVATE_PATH_SERVICE_GATEWAY1 PRIVATE_PATH_SERVICE_GATEWAY2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-private-path-service-gateway-delete}

- `ibmcloud is ppsgd r134-01cd30f7-e6f2-432f-9520-76247b1fbbe1 r134-72940467-a4db-487f-b57e-b7141ac40e32`
- `ibmcloud is private-path-service-gateway-delete cli-ppsg-0 cli-ppsg-1`

#### Command options
{: #command-options-private-path-service-gateway-delete}

- **PRIVATE_PATH_SERVICE_GATEWAY1**: ID or name of the Private Path service gateway.
- **PRIVATE_PATH_SERVICE_GATEWAY2**: ID or name of the Private Path service gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is private-path-service-gateway-publish
{: #private-path-service-gateway-publish-view}

Publish a Private Path service gateway.

```
ibmcloud is private-path-service-gateway-publish PRIVATE_PATH_SERVICE_GATEWAY [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-private-path-service-gateway-publish}

- `ibmcloud is ppsgp r134-01cd30f7-e6f2-432f-9520-76247b1fbbe1`
- `ibmcloud is private-path-service-gateway-publish cli-ppsg-0`

#### Command options
{: #command-options-private-path-service-gateway-publish}

- **PRIVATE_PATH_SERVICE_GATEWAY**: ID or name of the Private Path service gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is private-path-service-gateway-unpublish
{: #private-path-service-gateway-unpublish-view}

Unpublish a Private Path service gateway.

```
ibmcloud is private-path-service-gateway-unpublish PRIVATE_PATH_SERVICE_GATEWAY [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-private-path-service-gateway-unpublish}

- `ibmcloud is ppsgunp r134-01cd30f7-e6f2-432f-9520-76247b1fbbe1`
- `ibmcloud is private-path-service-gateway-unpublish cli-ppsg-0`

#### Command options
{: #command-options-private-path-service-gateway-unpublish}

- **PRIVATE_PATH_SERVICE_GATEWAY**: ID or name of the Private Path service gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is private-path-service-gateway-account-policies
{: #private-path-service-gateway-account-policies-list}

List all account policies for Private Path service gateway.

```
ibmcloud is private-path-service-gateway-account-policies (PRIVATE_PATH_SERVICE_GATEWAY1 PRIVATE_PATH_SERVICE_GATEWAY2 ...) [--account-id ACCOUNT_ID] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-private-path-service-gateway-account-policies}

- `ibmcloud is ppsg-aps cli-ppsg-0`
- `ibmcloud is ppsg-aps r134-f5926633-81d0-429e-bcf8-91151ade00bf`

#### Command options
{: #command-options-private-path-service-gateway-account-policies}

- **PRIVATE_PATH_SERVICE_GATEWAY1**: ID or name of the Private Path service gateway.
- **PRIVATE_PATH_SERVICE_GATEWAY2**: ID or name of the Private Path service gateway.
- **--account-id**: ID of the account for this access policy.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is private-path-service-gateway-account-policy
{: #private-path-service-gateway-account-policy-view}

View details of an account policy for a Private Path service gateway.

```
ibmcloud is private-path-service-gateway-account-policy PRIVATE_PATH_SERVICE_GATEWAY ACCOUNT_POLICY [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-private-path-service-gateway-account-policy}

- `ibmcloud is ppsg-ap cli-ppsg-0 2d1bace7b46e4815a81e52c6ffeba5cf`
- `ibmcloud is private-path-service-gateway-account-policy r134-f5926633-81d0-429e-bcf8-91151ade00bf e13b4574db1743b1b7897bebca551db1`

#### Command options
{: #command-options-private-path-service-gateway-account-policy}

- **PRIVATE_PATH_SERVICE_GATEWAY**: ID or name of the Private Path service gateway.
- **ACCOUNT_POLICY**: ID of the account policy for the Private Path service gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is private-path-service-gateway-account-policy-create
{: #private-path-service-gateway-account-policy-create}

Create an account policy for a Private Path service gateway.

```
ibmcloud is private-path-service-gateway-account-policy-create PRIVATE_PATH_SERVICE_GATEWAY --account-id ACCOUNT_ID [--access-policy deny | permit | review] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-private-path-service-gateway-account-policy-create}

- `ibmcloud is private-path-service-gateway-account-policy-create r134-f5926633-81d0-429e-bcf8-91151ade00bf --account-id e13b4574db1743b1b7897bebca551db1 --access-policy deny`
- `ibmcloud is private-path-service-gateway-account-policy-create cli-ppsg-0 --account-id 2d1bace7b46e4815a81e52c6ffeba5cf --access-policy review`

#### Command options
{: #command-options-private-path-service-gateway-account-policy-create}

- **PRIVATE_PATH_SERVICE_GATEWAY**: ID or name of the Private Path service gateway.
- **--access-policy**: The access policy for the account. One of: **deny**, **permit**, **review**.
- **--account-id**: ID of the account for this access policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is private-path-service-gateway-account-policy-update
{: #private-path-service-gateway-account-policy-update}

Update an account policy for a Private Path service gateway.

```
ibmcloud is private-path-service-gateway-account-policy-update PRIVATE_PATH_SERVICE_GATEWAY ACCOUNT_POLICY [--access-policy deny | permit | review] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-private-path-service-gateway-account-policy-update}

- `ibmcloud is ppsg-apu r134-f5926633-81d0-429e-bcf8-91151ade00bf 2d1bace7b46e4815a81e52c6ffeba5cf --access-policy permit`
- `ibmcloud is ppsg-apu cli-ppsg-0 e13b4574db1743b1b7897bebca551db1 --access-policy review`

#### Command options
{: #command-options-private-path-service-gateway-account-policy-update}

- **PRIVATE_PATH_SERVICE_GATEWAY**: ID or name of the Private Path service gateway.
- **ACCOUNT_POLICY**: ID of the account policy for the Private Path service gateway.
- **--access-policy**: The access policy for the account. One of: **deny**, **permit**, **review**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is private-path-service-gateway-account-policy-delete
{: #private-path-service-gateway-account-policy-delete}

Delete one or more account policies for a Private Path service gateway.

```
ibmcloud is private-path-service-gateway-account-policy-delete PRIVATE_PATH_SERVICE_GATEWAY (ACCOUNT_POLICY1 ACCOUNT_POLICY2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-private-path-service-gateway-account-policy-delete}

- `ibmcloud is ppsg-apd r134-2e671f14-19fc-4089-9ad3-973176711259 efe5afc483594adaa8325e2b4d1290df`
- `ibmcloud is private-path-service-gateway-account-policy-delete cli-ppsg-0 2d1bace7b46e4815a81e52c6ffeba5cf e13b4574db1743b1b7897bebca551db1`

#### Command options
{: #command-options-private-path-service-gateway-account-policy-delete}

- **PRIVATE_PATH_SERVICE_GATEWAY**: ID or name of the Private Path service gateway.
- **ACCOUNT_POLICY1**: ID of the account policy for the Private Path service gateway.
- **ACCOUNT_POLICY2**: ID of the account policy for the Private Path service gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is private-path-service-gateway-endpoint-gateway-bindings
{: #private-path-service-gateway-endpoint-gateway-bindings-list}

List all endpoint gateway bindings for Private Path service gateway.

```
ibmcloud is private-path-service-gateway-endpoint-gateway-bindings (PRIVATE_PATH_SERVICE_GATEWAY1 PRIVATE_PATH_SERVICE_GATEWAY2 ...) [--account-id ACCOUNT_ID] [--status STATUS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-private-path-service-gateway-endpoint-gateway-bindings}

- `ibmcloud is ppsg-egbs r134-2e671f14-19fc-4089-9ad3-973176711259`
- `ibmcloud is ppsg-egbs cli-ppsg-0`

#### Command options
{: #command-options-private-path-service-gateway-endpoint-gateway-bindings}

- **PRIVATE_PATH_SERVICE_GATEWAY1**: ID or name of the Private Path service gateway.
- **PRIVATE_PATH_SERVICE_GATEWAY2**: ID or name of the Private Path service gateway.
- **--account-id**: ID of the account for this access policy.
- **--status**: Status of the endpoint gateway bindings.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is private-path-service-gateway-endpoint-gateway-binding
{: #private-path-service-gateway-endpoint-gateway-binding-view}

View details of an endpoint gateway binding for a Private Path service gateway.

```
ibmcloud is private-path-service-gateway-endpoint-gateway-binding PRIVATE_PATH_SERVICE_GATEWAY ENDPOINT_GATEWAY_BINDING [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-private-path-service-gateway-endpoint-gateway-binding}

- `ibmcloud is private-path-service-gateway-endpoint-gateway-binding r134-2e671f14-19fc-4089-9ad3-973176711259 r134-17635273-0702-4a31-b406-a0014c291fbb`
- `ibmcloud is private-path-service-gateway-endpoint-gateway-binding cli-ppsg-0 r134-3aabeae6-830c-40d6-b67e-4b08382989e9`

#### Command options
{: #command-options-private-path-service-gateway-endpoint-gateway-binding}

- **PRIVATE_PATH_SERVICE_GATEWAY**: ID or name of the Private Path service gateway.
- **ENDPOINT_GATEWAY_BINDING**: ID of the endpoint gateway binding for the Private Path service gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is private-path-service-gateway-endpoint-gateway-binding-deny
{: #private-path-service-gateway-endpoint-gateway-binding-deny-view}

Deny an endpoint gateway binding for a Private Path service gateway.

```
ibmcloud is private-path-service-gateway-endpoint-gateway-binding-deny PRIVATE_PATH_SERVICE_GATEWAY ENDPOINT_GATEWAY_BINDING (--set-account-policy true | false) [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-private-path-service-gateway-endpoint-gateway-binding-deny}

- `ibmcloud is private-path-service-gateway-endpoint-gateway-binding-deny r134-2e671f14-19fc-4089-9ad3-973176711259 r134-17635273-0702-4a31-b406-a0014c291fbb --set-account-policy true`
- `ibmcloud is ppsg-egb-deny cli-ppsg r134-f7e2b651-0d02-46e1-8811-16ea2157b547 --set-account-policy true`

#### Command options
{: #command-options-private-path-service-gateway-endpoint-gateway-binding-deny}

- **PRIVATE_PATH_SERVICE_GATEWAY**: ID or name of the Private Path service gateway.
- **ENDPOINT_GATEWAY_BINDING**: ID of the endpoint gateway binding for the Private Path service gateway.
- **--set-account-policy**: Indicates whether this policy becomes the access policy for any pending and future endpoint gateway bindings from the same account. One of: **true**, **false**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is private-path-service-gateway-endpoint-gateway-binding-permit
{: #private-path-service-gateway-endpoint-gateway-binding-permit-view}

Allow an endpoint gateway binding for a Private Path service gateway.

```
ibmcloud is private-path-service-gateway-endpoint-gateway-binding-permit PRIVATE_PATH_SERVICE_GATEWAY ENDPOINT_GATEWAY_BINDING (--set-account-policy true | false) [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-private-path-service-gateway-endpoint-gateway-binding-permit}

- `ibmcloud is ppsg-egb-permit r134-e64dab2d-8fd2-43bd-8390-229ba66e53c4 r134-0dcc2105-14a1-4501-9b43-29632e910e4b --set-account-policy true`
- `ibmcloud is ppsg-egb-permit cli-ppsg r134-3a30c0b3-8c4b-4a64-bb93-3f3e17459363 --set-account-policy true`

#### Command options
{: #command-options-private-path-service-gateway-endpoint-gateway-binding-permit}

- **PRIVATE_PATH_SERVICE_GATEWAY**: ID or name of the Private Path service gateway.
- **ENDPOINT_GATEWAY_BINDING**: ID of the endpoint gateway binding for the Private Path service gateway.
- **--set-account-policy**: Indicates whether this policy becomes the access policy for any pending and future endpoint gateway bindings from the same account. One of: **true**, **false**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is private-path-service-gateway-endpoint-gateway-binding-revoke
{: #private-path-service-gateway-endpoint-gateway-binding-revoke-view}

Revoke access to a Private Path service gateway for an account.

```
ibmcloud is private-path-service-gateway-endpoint-gateway-binding-revoke (PRIVATE_PATH_SERVICE_GATEWAY1 PRIVATE_PATH_SERVICE_GATEWAY2 ...) --account-id ACCOUNT_ID [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-private-path-service-gateway-endpoint-gateway-binding-revoke}

- `ibmcloud is ppsg-ar r134-e64dab2d-8fd2-43bd-8390-229ba66e53c4 --account-id efe5afc483594adaa8325e2b4d1290df`
- `ibmcloud is ppsg-ar cli-ppsg --account-id efe5afc483594adaa8325e2b4d1290df`

#### Command options
{: #command-options-private-path-service-gateway-endpoint-gateway-binding-revoke}

- **PRIVATE_PATH_SERVICE_GATEWAY1**: ID or name of the Private Path service gateway.
- **PRIVATE_PATH_SERVICE_GATEWAY2**: ID or name of the Private Path service gateway.
- **--account-id**: ID of the account for this access policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Virtual private network (VPN) gateways
{: #vpn-clis}

The following section gives details about the CLI commands that are available for working with VPN gateways, including IKE and IPsec policies.


### ibmcloud is ike-policies
{: #ike-policies-list}

List all IKE policies.

```
ibmcloud is ike-policies [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-ike-policies}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ike-policy
{: #ike-policy-view}

View details of an IKE policy.

```
ibmcloud is ike-policy IKE_POLICY [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-ike-policy}

- **IKE_POLICY**: ID or name of the IKE policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ike-policy-connections
{: #ike-policy-connections-list}

List all connections that use the IKE policy.

```
ibmcloud is ike-policy-connections IKE_POLICY [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-ike-policy-connections}

- **IKE_POLICY**: ID or name of the IKE policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ike-policy-create
{: #ike-policy-create}

Create an IKE policy.

```
ibmcloud is ike-policy-create IKE_POLICY_NAME AUTHENTICATION_ALGORITHM DH_GROUP ENCRYPTION_ALGORITHM IKE_VERSION [--key-lifetime KEY_LIFETIME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-ike-policy-create}

- `ibmcloud is ike-policy-create my-ike-policy sha256 14 aes128 2`
- `ibmcloud is ike-policy-create my-ike-policy sha256 14 aes128 2 --key-lifetime 28000`
- `ibmcloud is ike-policy-create my-ike-policy sha256 14 aes128 2 --resource-group-name Default`
- `ibmcloud is ike-policy-create my-ike-policy sha256 14 aes128 2 --resource-group-id fee82deba12e4c0fb69c3b09d1f12345 --output JSON`

#### Command options
{: #command-options-ike-policy-create}

- **IKE_POLICY_NAME**: Name of the IKE policy.
- **AUTHENTICATION_ALGORITHM**: The authentication algorithm. One of: **sha256**, **sha384**, **sha512**.
- **DH_GROUP**: The Diffie-Hellman group. One of: **14**, **15**, **16**, **17**, **18**, **19**, **20**, **21**, **22**, **23**, **24**, **31**.
- **ENCRYPTION_ALGORITHM**: The encryption algorithm. One of: **aes128**, **aes192**, **aes256**.
- **IKE_VERSION**: The IKE protocol version. One of: **1**, **2**.
- **--key-lifetime**: The key lifetime in seconds. Maximum: **86400**, Minimum: **1800**. (default: **28800**).
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ike-policy-delete
{: #ike-policy-delete}

Delete one or more IKE policies.

```
ibmcloud is ike-policy-delete (IKE_POLICY1 IKE_POLICY2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-ike-policy-delete}

- **IKE_POLICY1**: ID or name of the IKE policy.
- **IKE_POLICY2**: ID or name of the IKE policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ike-policy-update
{: #ike-policy-update}

Update an IKE policy.

```
ibmcloud is ike-policy-update IKE_POLICY [--name NEW_NAME] [--authentication-algorithm sha256 | sha384 | sha512] [--dh-group 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 | 31] [--encryption-algorithm aes128 | aes192 | aes256] [--ike-version 1 | 2] [--key-lifetime KEY_LIFETIME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-ike-policy-update}

- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --name my-ike-policy`
- `ibmcloud is ike-policy-update my-ike-policy --name my-renamed-ike-policy`
- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --authentication-algorithm sha256`
- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --dh-group 14`
- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --encryption-algorithm aes128`
- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --ike-version 2`
- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --key-lifetime 28000 --output JSON`

#### Command options
{: #command-options-ike-policy-update}

- **IKE_POLICY**: ID or name of the IKE policy.
- **--name**: New name of the IKE policy.
- **--authentication-algorithm**: The authentication algorithm. One of: **sha256**, **sha384**, **sha512**.
- **--dh-group**: The Diffie-Hellman group. One of: **14**, **15**, **16**, **17**, **18**, **19**, **20**, **21**, **22**, **23**, **24**, **31**.
- **--encryption-algorithm**: The encryption algorithm. One of: **aes128**, **aes192**, **aes256**.
- **--ike-version**: The IKE protocol version. One of: **1**, **2**.
- **--key-lifetime**: The key lifetime in seconds. Maximum: **86400**, Minimum: **1800**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ipsec-policies
{: #ipsec-policies-list}

List all IPsec policies.

```
ibmcloud is ipsec-policies [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-ipsec-policies}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ipsec-policy
{: #ipsec-policy-view}

View details of an IPsec policy.

```
ibmcloud is ipsec-policy IPSEC_POLICY [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-ipsec-policy}

- **IPSEC_POLICY**: ID or name of the IPsec policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ipsec-policy-connections
{: #ipsec-policy-connections-list}

List all connections that use the IPsec policy.

```
ibmcloud is ipsec-policy-connections IPSEC_POLICY [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-ipsec-policy-connections}

- **IPSEC_POLICY**: ID or name of the IPsec policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ipsec-policy-create
{: #ipsec-policy-create}

Create an IPsec policy.

```
ibmcloud is ipsec-policy-create IPSEC_POLICY_NAME AUTHENTICATION_ALGORITHM ENCRYPTION_ALGORITHM PFS [--key-lifetime KEY_LIFETIME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-ipsec-policy-create}

- `ibmcloud is ipsec-policy-create my-ipsec-policy sha256 aes128 group_14`
- `ibmcloud is ipsec-policy-create my-ipsec-policy sha256 aes128 group_14 --key-lifetime 3600`
- `ibmcloud is ipsec-policy-create my-ipsec-policy sha256 aes128 group_14 --resource-group-name Default`
- `ibmcloud is ipsec-policy-create my-ipsec-policy sha256 aes128 group_14 --resource-group-id fee82deba12e4c0fb69c3b09d1f12345 --output JSON`

#### Command options
{: #command-options-ipsec-policy-create}

- **IPSEC_POLICY_NAME**: Name of the IPsec policy.
- **AUTHENTICATION_ALGORITHM**: The authentication algorithm. Must be disabled only if encryption algorithm is 'aes128gcm16', 'aes192gcm16', or 'aes256gcm16'. One of: **disabled**, **sha256**, **sha384**, **sha512**.
- **ENCRYPTION_ALGORITHM**: The encryption algorithm. The authentication algorithm must be disabled only if encryption algorithm is 'aes128gcm16', 'aes192gcm16', or 'aes256gcm16'. One of: **aes128**, **aes128gcm16**, **aes192**, **aes192gcm16**, **aes256**, **aes256gcm16**.
- **PFS**: Perfect Forward Secrecy. One of: **disabled**, **group_14**, **group_15**, **group_16**, **group_17**, **group_18**, **group_19**, **group_20**, **group_21**, **group_22**, **group_23**, **group_24**, **group_31**.
- **--key-lifetime**: The key lifetime in seconds. Maximum: **86400**, Minimum: **1800**. (default: **3600**).
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ipsec-policy-delete
{: #ipsec-policy-delete}

Delete one or more IPsec policies.

```
ibmcloud is ipsec-policy-delete (IPSEC_POLICY1 IPSEC_POLICY2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-ipsec-policy-delete}

- **IPSEC_POLICY1**: ID or name of the IPsec policy.
- **IPSEC_POLICY2**: ID or name of the IPsec policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ipsec-policy-update
{: #ipsec-policy-update}

Update an IPsec policy.

```
ibmcloud is ipsec-policy-update IPSEC_POLICY [--name NEW_NAME] [--authentication-algorithm disabled | sha256 | sha384 | sha512] [--pfs disabled | group_14 | group_15 | group_16 | group_17 | group_18 | group_19 | group_20 | group_21 | group_22 | group_23 | group_24 | group_31] [--encryption-algorithm aes128 | aes128gcm16 | aes192 | aes192gcm16 | aes256 | aes256gcm16] [--key-lifetime KEY_LIFETIME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-ipsec-policy-update}

- `ibmcloud is ipsec-policy-update fee82deba12e4c0fb69c3b09d1f12345 --name my-ipsec-policy`
- `ibmcloud is ipsec-policy-update my-ipsec-policy --name my-renamed-ipsec-policy`
- `ibmcloud is ipsec-policy-update fee82deba12e4c0fb69c3b09d1f12345 --authentication-algorithm sha256`
- `ibmcloud is ipsec-policy-update fee82deba12e4c0fb69c3b09d1f12345 --pfs group_14`
- `ibmcloud is ipsec-policy-update fee82deba12e4c0fb69c3b09d1f12345 --encryption-algorithm aes128`
- `ibmcloud is ipsec-policy-update fee82deba12e4c0fb69c3b09d1f12345 --key-lifetime 3600 --output JSON`

#### Command options
{: #command-options-ipsec-policy-update}

- **IPSEC_POLICY**: ID or name of the IPsec policy.
- **--name**: New name of the IPsec policy.
- **--authentication-algorithm**: The authentication algorithm. Must be disabled only if encryption algorithm is **aes128gcm16**, **aes192gcm16**, or **aes256gcm16**. One of: **disabled**, **sha256**, **sha384**, **sha512**.
- **--pfs**: Perfect Forward Secrecy. One of: **disabled**, **group_14**, **group_15**, **group_16**, **group_17**, **group_18**, **group_19**, **group_20**, **group_21**, **group_22**, **group_23**, **group_24**, **group_31**.
- **--encryption-algorithm**: The encryption algorithm. The authentication algorithm must be disabled only if encryption algorithm is **aes128gcm16**, **aes192gcm16**, or **aes256gcm16**. One of: **aes128**, **aes128gcm16**, **aes192**, **aes192gcm16**, **aes256**, **aes256gcm16**.
- **--key-lifetime**: The key lifetime in seconds. Maximum: **86400**, Minimum: **1800**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway
{: #vpn-gateway-view}

View details of a VPN gateway.

```
ibmcloud is vpn-gateway VPN_GATEWAY [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection
{: #vpn-gateway-connection-view}

View details of a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection VPN_GATEWAY (CONNECTION1 CONNECTION2 ...) [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-connection}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **CONNECTION1**: ID or name of the VPN connection.
- **CONNECTION2**: ID or name of the VPN connection.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-create
{: #vpn-gateway-connection-create}

Create a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-create CONNECTION_NAME VPN_GATEWAY PEER PRESHARED_KEY [--vpc VPC] [--admin-state-up true | false] [--dead-peer-detection-action restart | clear | hold | none] [--dead-peer-detection-interval INTERVAL] [--dead-peer-detection-timeout TIMEOUT] [--distribute-traffic true | false] [--ike-policy IKE_POLICY_ID] [--ipsec-policy IPSEC_POLICY_ID] [--peer-cidr CIDR1 --peer-cidr CIDR2 ... --local-cidr CIDR1 --local-cidr CIDR2 ...] [[--local-ike-identity-type fqdn | hostname | ipv4_address | key_id --local-ike-identity-value VALUE] | [--local-ike-identities LISTENER_POLICIES_JSON | @LISTENER_POLICIES_JSON_FILE]] [--peer-ike-identity-type fqdn | hostname | ipv4_address | key_id --peer-ike-identity-value VALUE] [--establish-mode bidirectional | peer_only] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpn-gateway-connection-create}

- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24`
- `ibmcloud is vpn-gateway-connection-create my-connection my-vpn-gateway 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --admin-state-up true`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --dead-peer-detection-action clear --dead-peer-detection-interval 33 --dead-peer-detection-timeout 100`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --ipsec-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is vpn-gateway-connection-create my-connection my-vpn-gateway 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --ipsec-policy my-ispec-policy`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --ike-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is vpn-gateway-connection-create my-connection my-vpn-gateway 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --ike-policy my-ike-policy`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --admin-state-up true`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --dead-peer-detection-action clear --dead-peer-detection-interval 33 --dead-peer-detection-timeout 100`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --ipsec-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --ike-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --local-cidr 10.240.1.0/24 --peer-cidr 192.168.1.0/24 --peer-cidr 192.168.2.0/24  --output JSON`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --distribute-traffic true --local-ike-identities '[{"type":"fqdn","value":"sadsadasd.com"},{"type":"fqdn","value":"sadsadasdasd.com"}]' --peer-ike-identity-type key_id --peer-ike-identity-value sampledd --output JSON`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --establish-mode peer_only --local-ike-identities '[{"type":"ipv4_address","value":"2.2.2.2"},{"type":"fqdn","value":"sadsadasd.com"}]' --peer-ike-identity-type key_id --peer-ike-identity-value sampledd`
create VPN gateway connection with local ike_identities using it as JSON structure
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --establish-mode peer_only  --local-ike-identity-type fqdn --local-ike-identity-value sadsadasd.com --peer-ike-identity-type key_id --peer-ike-identity-value sampledd`
create VPN gateway connection with local ike_identities using it as flag structure

#### Command options
{: #command-options-vpn-gateway-connection-create}

- **CONNECTION_NAME**: Name of the connection.
- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **PEER**: The IP address or FQDN of the peer VPN gateway.
- **PRESHARED_KEY**: The preshared key.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--admin-state-up**: If set to false, the VPN gateway connection is shut down. One of: **true**, **false**. (default: **true**).
- **--dead-peer-detection-action**: Dead Peer Detection actions. One of: **restart**, **clear**, **hold**, **none**. (default: **restart**).
- **--dead-peer-detection-interval**: Dead Peer Detection interval in seconds (default: **2**).
- **--dead-peer-detection-timeout**: Dead Peer Detection timeout in seconds (default: **10**).
- **--distribute-traffic**: Indicates whether the traffic is distributed between the up tunnels of the VPN gateway connection. One of: **true**, **false**.
- **--ike-policy**: ID or name of the IKE policy.
- **--ipsec-policy**: ID or name of the IPsec policy.
- **--peer-cidr**: Peer CIDRs for the resource.
- **--local-cidr**: Local CIDR for the resource.
- **--local-ike-identity-type**: The Local IKE identity type.
- **--local-ike-identity-value**: The Local IKE identity FQDN value.
- **--local-ike-identities**: LOCAL_IKE_IDENTITIES_JSON | @LOCAL_IKE_IDENTITIES_JSON_FILE, local ike identities in JSON or JSON file.
- **--peer-ike-identity-type**: The Peer IKE identity type.
- **--peer-ike-identity-value**: The Peer IKE identity FQDN value.
- **--establish-mode**: The establish mode of the VPN gateway connection. One of: **bidirectional**, **peer_only**. (default: **bidirectional**).
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-delete
{: #vpn-gateway-connection-delete}

Delete one or more VPN gateway connections.

```
ibmcloud is vpn-gateway-connection-delete VPN_GATEWAY (CONNECTION1 CONNECTION2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-connection-delete}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **CONNECTION1**: ID or name of the VPN connection.
- **CONNECTION2**: ID or name of the VPN connection.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-local-cidr-add
{: #vpn-gateway-connection-local-cidr-add}

Add a local CIDR to a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-local-cidr-add VPN_GATEWAY CONNECTION CIDR [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpn-gateway-connection-local-cidr-add}

- `ibmcloud is vpn-gateway-connection-local-cidr-add 0726-59be5c84-1dc2-4191-b591-d506514563bf 0726-0d642e87-b868-4a22-83f4-a35a19390b5c 1.168.0.0/22`
- `ibmcloud is vpn-gateway-connection-local-cidr-add 0726-59be5c84-1dc2-4191-b591-d506514563bf 0726-0d642e87-b868-4a22-83f4-a35a19390b5c 1.168.0.0/22 --output JSON`

#### Command options
{: #command-options-vpn-gateway-connection-local-cidr-add}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **CONNECTION**: ID or name of the VPN connection.
- **CIDR**: The IP address range in CIDR block notation.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-local-cidr-delete
{: #vpn-gateway-connection-local-cidr-delete}

Remove a local CIDR from the VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-local-cidr-delete VPN_GATEWAY CONNECTION CIDR [--vpc VPC] [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpn-gateway-connection-local-cidr-delete}

- `ibmcloud is vpn-gateway-connection-local-cidr-delete 0726-59be5c84-1dc2-4191-b591-d506514563bf 0726-0d642e87-b868-4a22-83f4-a35a19390b5c 1.168.0.0/22`
- `ibmcloud is vpn-gateway-connection-local-cidr-delete 0726-59be5c84-1dc2-4191-b591-d506514563bf 0726-0d642e87-b868-4a22-83f4-a35a19390b5c 1.168.0.0/22 --output JSON`

#### Command options
{: #command-options-vpn-gateway-connection-local-cidr-delete}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **CONNECTION**: ID or name of the VPN connection.
- **CIDR**: The IP address range in CIDR block notation.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-peer-cidr-add
{: #vpn-gateway-connection-peer-cidr-add}

Add a peer CIDR to a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-peer-cidr-add VPN_GATEWAY CONNECTION CIDR [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpn-gateway-connection-peer-cidr-add}

- `ibmcloud is vpn-gateway-connection-peer-cidr-add 0726-59be5c84-1dc2-4191-b591-d506514563bf 0726-0d642e87-b868-4a22-83f4-a35a19390b5c 10.45.0.0/24`
- `ibmcloud is vpn-gateway-connection-peer-cidr-add 0726-59be5c84-1dc2-4191-b591-d506514563bf 0726-0d642e87-b868-4a22-83f4-a35a19390b5c 10.45.0.0/24 --output JSON`

#### Command options
{: #command-options-vpn-gateway-connection-peer-cidr-add}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **CONNECTION**: ID or name of the VPN connection.
- **CIDR**: The IP address range in CIDR block notation.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-peer-cidr-delete
{: #vpn-gateway-connection-peer-cidr-delete}

Remove a peer CIDR from the VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-peer-cidr-delete VPN_GATEWAY CONNECTION CIDR [--vpc VPC] [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpn-gateway-connection-peer-cidr-delete}

- `ibmcloud is vpn-gateway-connection-peer-cidr-delete 0726-59be5c84-1dc2-4191-b591-d506514563bf 0726-0d642e87-b868-4a22-83f4-a35a19390b5c 10.45.0.0/24`
- `ibmcloud is vpn-gateway-connection-peer-cidr-add 0726-59be5c84-1dc2-4191-b591-d506514563bf 0726-0d642e87-b868-4a22-83f4-a35a19390b5c 10.45.0.0/24 --output JSON`

#### Command options
{: #command-options-vpn-gateway-connection-peer-cidr-delete}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **CONNECTION**: ID or name of the VPN connection.
- **CIDR**: The IP address range in CIDR block notation.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-update
{: #vpn-gateway-connection-update}

Update a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-update VPN_GATEWAY CONNECTION [--vpc VPC] [--admin-state-up true | false] [--dead-peer-detection-action restart | clear | hold | none] [--dead-peer-detection-interval INTERVAL] [--dead-peer-detection-timeout TIMEOUT] [--ike-policy IKE_POLICY_ID | --reset-ike-policy] [--ipsec-policy IPSEC_POLICY_ID | --reset-ipsec-policy] [--peer-address ADDRESS] [--peer-fqdn FQDN] [--distribute-traffic true | false] [--psk PSK] [--establish-mode bidirectional | peer_only] [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpn-gateway-connection-update}

- `ibmcloud is vpn-gateway-connection-update fee82deba12e4c0fb69c3b09d1f12345 gfe82deba12e4c0fb69c3b09d1f23456 --admin-state-up true --dead-peer-detection-action clear --dead-peer-detection-interval 33 --dead-peer-detection-timeout 100  --ike-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479  --ipsec-policy 05251a2e-d6c5-42b4-97b0-b5f8e8d1f445 --peer-address 234.3.4.5 -psk rweirjgiort --name my-new-connection --output JSON`
- `ibmcloud is vpn-gateway-connection-update my-vpn-gateway my-connection --admin-state-up true --dead-peer-detection-action clear --dead-peer-detection-interval 33 --dead-peer-detection-timeout 100  --ike-policy my-ike-policy  --ipsec-policy my-ipsec-policy --peer-address 234.3.4.5 -psk rweirjgiort --name my-new-connection --output JSON`
- `ibmcloud is vpn-gateway-connection-update my-vpn-gateway my-connection --admin-state-up true --dead-peer-detection-action clear --dead-peer-detection-interval 33 --dead-peer-detection-timeout 100  --ike-policy my-ike-policy  --ipsec-policy my-ipsec-policy --peer-address 234.3.4.5 -psk rweirjgiort --name my-new-connection --establish-mode peer_only --output JSON`
- `ibmcloud is vpn-gateway-connection-update my-vpn-gateway my-connection --admin-state-up true --ike-policy my-ike-policy  --ipsec-policy my-ipsec-policy --peer-fqdn my-service.example.com -psk rweirjgiort --name my-new-connection --establish-mode peer_only --output JSON`
- `ibmcloud is vpn-gateway-connection-update my-vpn-gateway my-connection --distribute-traffic true --output JSON`

#### Command options
{: #command-options-vpn-gateway-connection-update}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **CONNECTION**: ID or name of the VPN connection.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--admin-state-up**: If set to false, the VPN gateway connection is shut down. One of: **true**, **false**.
- **--dead-peer-detection-action**: Dead Peer Detection actions. One of: **restart**, **clear**, **hold**, **none**.
- **--dead-peer-detection-interval**: Dead Peer Detection interval in seconds.
- **--dead-peer-detection-timeout**: Dead Peer Detection timeout in seconds.
- **--ike-policy**: ID or name of the IKE policy.
- **--reset-ike-policy**: Remove IKE policy.
- **--ipsec-policy**: ID or name of the IPsec policy.
- **--reset-ipsec-policy**: Remove IPsec policy.
- **--peer-address**: The IP address of the peer VPN gateway.
- **--peer-fqdn**: The FQDN of the peer VPN gateway.
- **--distribute-traffic**: Indicates whether the traffic is distributed between the up tunnels of the VPN gateway connection. One of: **true**, **false**.
- **--psk**: The preshared key.
- **--establish-mode**: The establish mode of the VPN gateway connection. One of: **bidirectional**, **peer_only**.
- **--name**: New name of the connection.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connections
{: #vpn-gateway-connections-list}

List all VPN gateway connections.

```
ibmcloud is vpn-gateway-connections VPN_GATEWAY [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-connections}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-create
{: #vpn-gateway-create}

Create a VPN gateway.

```
ibmcloud is vpn-gateway-create VPN_GATEWAY_NAME SUBNET [--mode policy | route] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpn-gateway-create}

- `ibmcloud is vpn-gateway-create my-vpn-gateway fee82deba12e4c0fb69c3b09d1f12345 --mode route`
- `ibmcloud is vpn-gateway-create my-vpn-gateway my-subnet --vpc my-vpc --mode route`
- `ibmcloud is vpn-gateway-create my-vpn-gateway fee82deba12e4c0fb69c3b09d1f12345 --mode policy`
- `ibmcloud is vpn-gateway-create my-vpn-gateway my-subnet --vpc my-vpc --mode policy`
- `ibmcloud is vpn-gateway-create my-vpn-gateway fee82deba12e4c0fb69c3b09d1f12345 --mode route --resource-group-name Default`
- `ibmcloud is vpn-gateway-create my-vpn-gateway fee82deba12e4c0fb69c3b09d1f12345 --mode route --resource-group-id fee82deba12e4c0fb69c3b09d1f12345 --output JSON`

#### Command options
{: #command-options-vpn-gateway-create}

- **VPN_GATEWAY_NAME**: Name of the VPN gateway.
- **SUBNET**: ID or name of the subnet.
- **--mode**: The mode of the VPN gateway, if not specified the default mode of the VPN gateway is policy. One of: **policy**, **route**.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-delete
{: #vpn-gateway-delete}

Delete one or more VPN gateways.

```
ibmcloud is vpn-gateway-delete (VPN_GATEWAY1 VPN_GATEWAY2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-delete}

- **VPN_GATEWAY1**: ID or name of the VPN gateway.
- **VPN_GATEWAY2**: ID or name of the VPN gateway.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-update
{: #vpn-gateway-update}

Update a VPN gateway.

```
ibmcloud is vpn-gateway-update VPN_GATEWAY [--vpc VPC] [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpn-gateway-update}

- `ibmcloud is vpn-gateway-update fee82deba12e4c0fb69c3b09d1f12345 --name my-renamed-gateway --output JSON`
- `ibmcloud is vpn-gateway-update my-vpn-gateway --name my-renamed-gateway --output JSON`

#### Command options
{: #command-options-vpn-gateway-update}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--name**: New name of the VPN gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateways
{: #vpn-gateways-list}

List all VPN gateways.

```
ibmcloud is vpn-gateways [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateways}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Virtual private network (VPN) servers
{: #vpn-server-clis}

The following section gives details about the CLI commands available for working with VPN servers.


### ibmcloud is vpn-servers
{: #vpn-servers-list}

List all VPN servers.

```
ibmcloud is vpn-servers [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-servers}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server
{: #vpn-server-view}

View details of a VPN server.

```
ibmcloud is vpn-server VPN_SERVER [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-server}

- **VPN_SERVER**: ID or name of the VPN server.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-create
{: #vpn-server-create}

Create a VPN server.

```
ibmcloud is vpn-server-create --client-ip-pool CLIENT_IP_POOL --cert CERT (--client-auth-methods certificate | username | certificate,username | username,certificate) [--subnet SUBNET --vpc VPC] [--client-ca CLIENT_CA] [--client-crl CLIENT_CRL] [--client-dns CLIENT_DNS] [--client-idle-timeout CLIENT_IDLE_TIMEOUT] [--enable-split-tunnel false | true] [--port PORT] [--protocol udp | tcp] [--sg SG] [--name NAME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpn-server-create}

- `ibmcloud is vpn-server-create --subnet 0726-a7191f77-7c87-4ad4-bb11-a37f9e9fc0f0,0736-4b871e22-e819-4f87-bb17-e457a88246a2 --cert crn:v1:bluemix:public:secrets-manager:us-south:a/aa5a471f75bc456fac416bf02c4ba6de:aace9348-39da-4498-b132-e5ab918237f4:secret:e3bd96ce-1e4c-f642-d1f2-0d0ab025f510 --client-ip-pool 192.168.0.0/20 --client-auth-methods certificate --client-ca crn:v1:bluemix:public:secrets-manager:us-south:a/aa5a471f75bc456fac416bf02c4ba6de:aace9348-39da-4498-b132-e5ab918237f4:secret:e3bd96ce-1e4c-f642-d1f2-0d0ab025f514`
- `ibmcloud is vpn-server-create --subnet my-subnet,my-subnet2 --vpc my-vpc --cert crn:v1:bluemix:public:secrets-manager:us-south:a/aa5a471f75bc456fac416bf02c4ba6de:aace9348-39da-4498-b132-e5ab918237f4:secret:e3bd96ce-1e4c-f642-d1f2-0d0ab025f510 --client-ip-pool 192.168.0.0/20 --client-auth-methods certificate --client-ca crn:v1:bluemix:public:secrets-manager:us-south:a/aa5a471f75bc456fac416bf02c4ba6de:aace9348-39da-4498-b132-e5ab918237f4:secret:e3bd96ce-1e4c-f642-d1f2-0d0ab025f514`
- `ibmcloud is vpn-server-create --name myvpnserver --subnet 0726-a7191f77-7c87-4ad4-bb11-a37f9e9fc0f0,0736-4b871e22-e819-4f87-bb17-e457a88246a2 --cert crn:v1:bluemix:public:secrets-manager:us-south:a/aa5a471f75bc456fac416bf02c4ba6de:aace9348-39da-4498-b132-e5ab918237f4:secret:e3bd96ce-1e4c-f642-d1f2-0d0ab025f510 --client-ip-pool 192.168.0.0/20 --client-auth-methods username`
- `ibmcloud is vpn-server-create --name myvpnserver2 --subnet 0726-a7191f77-7c87-4ad4-bb11-a37f9e9fc0f0 --cert crn:v1:bluemix:public:secrets-manager:us-south:a/aa5a471f75bc456fac416bf02c4ba6de:aace9348-39da-4498-b132-e5ab918237f4:secret:e3bd96ce-1e4c-f642-d1f2-0d0ab025f510 --client-ip-pool 192.168.0.0/20 --client-auth-methods username --client-dns 9.9.9.9,8.8.8.8 --protocol tcp --port 8888 --enable-split-tunnel true --client-idle-timeout 1200`
- `ibmcloud is vpn-server-create --name myvpnserver3 --subnet 0726-a7191f77-7c87-4ad4-bb11-a37f9e9fc0f0 --cert crn:v1:bluemix:public:secrets-manager:us-south:a/aa5a471f75bc456fac416bf02c4ba6de:aace9348-39da-4498-b132-e5ab918237f4:secret:e3bd96ce-1e4c-f642-d1f2-0d0ab025f510 --client-ip-pool 192.168.0.0/20 --client-auth-methods username --sg r134-e32f671c-463d-4f93-88e3-2dd0413476b4,r134-3af7a9db-d9bc-43d4-bced-93e0a33fee25`
- `ibmcloud is vpn-server-create --name myvpnserver3 --subnet my-subnet --vpc my-vpc --cert crn:v1:bluemix:public:secrets-manager:us-south:a/aa5a471f75bc456fac416bf02c4ba6de:aace9348-39da-4498-b132-e5ab918237f4:secret:e3bd96ce-1e4c-f642-d1f2-0d0ab025f510 --client-ip-pool 192.168.0.0/20 --client-auth-methods username --sg my-sg1,my-sg2`
- `ibmcloud is vpn-server-create  --subnet 0726-a7191f77-7c87-4ad4-bb11-a37f9e9fc0f0,0736-4b871e22-e819-4f87-bb17-e457a88246a2 --cert crn:v1:bluemix:public:secrets-manager:us-south:a/aa5a471f75bc456fac416bf02c4ba6de:aace9348-39da-4498-b132-e5ab918237f4:secret:e3bd96ce-1e4c-f642-d1f2-0d0ab025f510 --client-ip-pool 192.168.0.0/20 --client-dns 172.34.1.100  --client-auth-methods certificate,username --client-ca crn:v1:bluemix:public:secrets-manager:us-south:a/aa5a471f75bc456fac416bf02c4ba6de:aace9348-39da-4498-b132-e5ab918237f4:secret:e3bd96ce-1e4c-f642-d1f2-0d0ab025f514 --client-crl @./openvpn/crl.pem --name vpnswithcrl --sg r134-5744b689-e5c4-461d-9f9b-ce5e7e8dbed6`

#### Command options
{: #command-options-vpn-server-create}

- **--subnet**: Comma-separated IDs or names of the subnets to provision this VPN server. Use subnets in different zones for high availability and at most, you can set two subnets.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--client-ip-pool**: The VPN client IPv4 address pool, expressed in CIDR format. The request must not overlap with any existing address prefixes in the VPC or any of the following reserved address ranges: 127.0.0.0/8 (IPv4 loopback addresses), 161.26.0.0/16 (IBM services), 166.8.0.0/14 (Cloud Service Endpoints), 169.254.0.0/16 (IPv4 link-local addresses), 224.0.0.0/4 (IPv4 multicast addresses). The prefix length of the client IP address pool's CIDR must be between /9 (8,388,608 addresses) and /22 (1024 addresses). A CIDR block that contains twice the number of IP addresses that are required to enable the maximum number of concurrent connections is recommended.
- **--cert**: The secret CRN from the secret manager for this VPN server.
- **--client-auth-methods**: Comma-separated of client authentication methods. One of: **certificate**, **username**, **certificate,username**, **username,certificate**.
- **--client-ca**: The secret CRN from the secrets manager to use for the VPN client certificate authority (CA).
- **--client-crl**: CRL | @CRL-file. The certificate revocation list contents, encoded in PEM format.
- **--client-dns**: Comma-separated of DNS server addresses that are provided to VPN clients that are connected to this VPN server. Two DNS servers can be set at most.
- **--client-idle-timeout**: The seconds that a VPN client can idle before this VPN server disconnects it. Specify 0 to prevent the server from disconnecting idle clients (default: **600**).
- **--enable-split-tunnel**: Indicates whether the split tunneling is enabled on this VPN server. One of: **false**, **true**. (default: **false**).
- **--port**: The port number to use for this VPN server. (default: **443**).
- **--protocol**: The transport protocol to use for this VPN server. One of: **udp**, **tcp**. (default: **udp**).
- **--sg**: Comma-separated security group IDs or names for the VPN server.
- **--name**: New name for the VPN server.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-update
{: #vpn-server-update}

Update a VPN server.

```
ibmcloud is vpn-server-update VPN_SERVER [--vpc VPC] [--subnet SUBNET] [--client-ip-pool CLIENT_IP_POOL] [--cert CERT] [--client-auth-methods certificate | username | certificate,username | username,certificate] [--client-ca CLIENT_CA] [--client-crl CLIENT_CRL] [[--client-dns CLIENT_DNS | --reset-client-dns]] [--client-idle-timeout CLIENT_IDLE_TIMEOUT] [--enable-split-tunnel false | true] [--port PORT] [--protocol udp | tcp] [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpn-server-update}

- `ibmcloud is vpn-server-update r134-aa88726e-8b34-4f97-992d-027df9c4bb36 --name my-server`
- `ibmcloud is vpn-server-update my-server --name my-renamed-server`
- `ibmcloud is vpn-server-update r134-aa88726e-8b34-4f97-992d-027df9c4bb36 --cert crn:v1:bluemix:public:secrets-manager:us-south:a/aa5a471f75bc456fac416bf02c4ba6de:aace9348-39da-4498-b132-e5ab918237f4:secret:e3bd96ce-1e4c-f642-d1f2-0d0ab025f510 --client-auth-methods certificate --client-ca crn:v1:bluemix:public:secrets-manager:us-south:a/aa5a471f75bc456fac416bf02c4ba6de:aace9348-39da-4498-b132-e5ab918237f4:secret:e3bd96ce-1e4c-f642-d1f2-0d0ab025f514`
- `ibmcloud is vpn-server-update r134-aa88726e-8b34-4f97-992d-027df9c4bb36 --client-ip-pool 192.168.0.0/20 --client-dns 9.9.9.9 --client-idle-timeout 120 --port 9090 --protocol tcp --enable-split-tunnel true --output JSON`
- `ibmcloud is vpn-server-update r134-aa88726e-8b34-4f97-992d-027df9c4bb36 --client-dns ""`
Clean up the DNS server addresses that are provided to VPN clients that are connected to this VPN server.
- `ibmcloud is vpn-server-update r134-aa88726e-8b34-4f97-992d-027df9c4bb36 --reset-client-dns`
Clean up the DNS server addresses that are provided to VPN clients that are connected to this VPN server.
- `ibmcloud is vpn-server-update r134-aa88726e-8b34-4f97-992d-027df9c4bb36 --subnet 0716-6ec3e875-abfa-40f4-a7c5-7473f4b2a2e1,0726-61b2f53f-1e95-42a7-94ab-55de8f8cbdd5`
Update the VPN server with more than one subnet from different zones to have high availability.
- `ibmcloud is vpn-server-update r134-aa88726e-8b34-4f97-992d-027df9c4bb36 --subnet 0716-6ec3e875-abfa-40f4-a7c5-7473f4b2a2e1`
Update the VPN server with a subnet either to change the subnet of the VPN server or downgrade the VPN server from a high available VPN server to a stand-alone VPN server.

#### Command options
{: #command-options-vpn-server-update}

- **VPN_SERVER**: ID or name of the VPN server.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--subnet**: Comma-separated IDs or names of the subnets to provision this VPN server. Use subnets in different zones for high availability and at most, you can set two subnets.
- **--client-ip-pool**: The VPN client IPv4 address pool, expressed in CIDR format. The request must not overlap with any existing address prefixes in the VPC or any of the following reserved address ranges: 127.0.0.0/8 (IPv4 loopback addresses), 161.26.0.0/16 (IBM services), 166.8.0.0/14 (Cloud Service Endpoints), 169.254.0.0/16 (IPv4 link-local addresses), 224.0.0.0/4 (IPv4 multicast addresses). The prefix length of the client IP address pool's CIDR must be between /9 (8,388,608 addresses) and /22 (1024 addresses). A CIDR block that contains twice the number of IP addresses that are required to enable the maximum number of concurrent connections is recommended.
- **--cert**: The secret CRN from the secret manager for this VPN server.
- **--client-auth-methods**: Comma-separated of client authentication methods. One of: **certificate**, **username**, **certificate,username**, **username,certificate**.
- **--client-ca**: The secret CRN from the secrets manager to use for the VPN client certificate authority (CA).
- **--client-crl**: CRL | @CRL-file. The certificate revocation list contents, encoded in PEM format.
- **--client-dns**: Comma-separated of DNS server addresses that are provided to VPN clients that are connected to this VPN server. Two DNS servers can be set at most.
- **--reset-client-dns**: Clean up the DNS server addresses that are provided to VPN clients that are connected to this VPN server.
- **--client-idle-timeout**: The seconds that a VPN client can idle before this VPN server disconnects it. Specify 0 to prevent the server from disconnecting idle clients.
- **--enable-split-tunnel**: Indicates whether the split tunneling is enabled on this VPN server. One of: **false**, **true**. (default: **false**).
- **--port**: The port number to use for this VPN server.
- **--protocol**: The transport protocol to use for this VPN server. One of: **udp**, **tcp**.
- **--name**: New name of the VPN server.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-delete
{: #vpn-server-delete}

Delete one or more VPN servers.

```
ibmcloud is vpn-server-delete (VPN_SERVER1 VPN_SERVER2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-server-delete}

- **VPN_SERVER1**: ID or name of the VPN server.
- **VPN_SERVER2**: ID or name of the VPN server.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-client-configuration
{: #vpn-server-client-configuration-view}

Retrieve OpenVPN client configuration.

```
ibmcloud is vpn-server-client-configuration VPN_SERVER [--vpc VPC] [--file FILE] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpn-server-client-configuration}

- `ibmcloud is vpn-server-client-configuration r134-d0671da5-1646-449b-8390-6bd7d6abea01`
- `ibmcloud is vpn-server-client-configuration my-server`
- `ibmcloud is vpn-server-client-configuration r134-d0671da5-1646-449b-8390-6bd7d6abea01 --file ./my_vpn.conf`

#### Command options
{: #command-options-vpn-server-client-configuration}

- **VPN_SERVER**: ID or name of the VPN server.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--file**: Save the client configuration to the specified file path name.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-clients
{: #vpn-server-clients-list}

List all VPN clients for a VPN server.

```
ibmcloud is vpn-server-clients VPN_SERVER [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-server-clients}

- **VPN_SERVER**: ID or name of the VPN server.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-client
{: #vpn-server-client-view}

View details of a VPN client.

```
ibmcloud is vpn-server-client VPN_SERVER CLIENT_ID [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-server-client}

- **VPN_SERVER**: ID or name of the VPN server.
- **CLIENT_ID**: ID of the VPN client.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-client-delete
{: #vpn-server-client-delete}

Delete one or more VPN clients for a VPN server.

```
ibmcloud is vpn-server-client-delete VPN_SERVER (CLIENT_ID1 CLIENT_ID2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-server-client-delete}

- **VPN_SERVER**: ID or name of the VPN server.
- **CLIENT_ID1**: ID of the VPN client.
- **CLIENT_ID2**: ID of the VPN client.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-client-disconnect
{: #vpn-server-client-disconnect}

Disconnect VPN client.

```
ibmcloud is vpn-server-client-disconnect VPN_SERVER (CLIENT_ID1 CLIENT_ID2 ...) [--vpc VPC] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-server-client-disconnect}

- **VPN_SERVER**: ID or name of the VPN server.
- **CLIENT_ID1**: ID of the VPN client.
- **CLIENT_ID2**: ID of the VPN client.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-routes
{: #vpn-server-routes-list}

List all VPN routes for a VPN server.

```
ibmcloud is vpn-server-routes VPN_SERVER [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-server-routes}

- **VPN_SERVER**: ID or name of the VPN server.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-route
{: #vpn-server-route-view}

View details of a VPN route.

```
ibmcloud is vpn-server-route VPN_SERVER ROUTE_ID [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-server-route}

- **VPN_SERVER**: ID or name of the VPN server.
- **ROUTE_ID**: ID or name of the VPN route.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-route-create
{: #vpn-server-route-create}

Create a VPN route.

```
ibmcloud is vpn-server-route-create VPN_SERVER --destination DESTINATION_CIDR [--vpc VPC] [--action translate | deliver | drop] [--name NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpn-server-route-create}

- `ibmcloud is vpn-server-route-create r134-77e21079-7291-44c2-866a-8f1848bc10f0 --name my-route --action deliver --destination 10.0.0.0/24`
- `ibmcloud is vpn-server-route-create my-server --name my-route --action deliver --destination 10.0.0.0/24`
- `ibmcloud is vpn-server-route-create r134-77e21079-7291-44c2-866a-8f1848bc10f0 --name my-route --action drop --destination 10.0.0.0/24`

#### Command options
{: #command-options-vpn-server-route-create}

- **VPN_SERVER**: ID or name of the VPN server.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--action**: The action to perform with a packet that matches the route. One of: **translate**, **deliver**, **drop**. (default: **deliver**).
- **--destination**: The destination to use for this VPN route in the VPN server. Must be unique within the VPN server. If an incoming packet does not match any destination, the packet is dropped.
- **--name**: Name of the VPN route.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-route-update
{: #vpn-server-route-update}

Update a VPN route.

```
ibmcloud is vpn-server-route-update VPN_SERVER ROUTE_ID [--vpc VPC] [--name NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpn-server-route-update}

- `ibmcloud is vpn-server-route-update r134-77e21079-7291-44c2-866a-8f1848bc10f0 1233a60b-fc95-4dbc-96ab-a976b723bfb0 --name my-route`
- `ibmcloud is vpn-server-route-update my-server my-route --name my-renamed-route`

#### Command options
{: #command-options-vpn-server-route-update}

- **VPN_SERVER**: ID or name of the VPN server.
- **ROUTE_ID**: ID or name of the VPN route.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--name**: New name of the VPN route.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-route-delete
{: #vpn-server-route-delete}

Delete one or more VPN routes.

```
ibmcloud is vpn-server-route-delete VPN_SERVER (ROUTE_ID1 ROUTE_ID2 ...) [--vpc VPC] [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-server-route-delete}

- **VPN_SERVER**: ID or name of the VPN server.
- **ROUTE_ID1**: ID or name of the VPN route.
- **ROUTE_ID2**: ID or name of the VPN route.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

## COMPUTE COMMANDS
{: #compute-clis}

The following section provides information about CLI commands for compute functionality.

## Images
{: #compute-images}

### ibmcloud is operating-systems
{: #operating-systems-list}

List all operating systems.

```
ibmcloud is operating-systems [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-operating-systems}

- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is operating-system
{: #operating-system-view}

View details of an operating system.

```
ibmcloud is operating-system OPERATING_SYSTEM_NAME [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-operating-system}

- **OPERATING_SYSTEM_NAME**: Name of the operating system.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is image
{: #image-view}

View details of an image.

```
ibmcloud is image IMAGE [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-image}

- **IMAGE**: ID or name of the image.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is images
{: #images-list}

List all images in the region.

```
ibmcloud is images [--visibility all | public | private] [--status STATUS] [--user-data-format USER_DATA_FORMAT] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [--remote-account-id provider | user] [-q, --quiet]
```

#### Command examples
{: #command-examples-images}

- `ibmcloud is images --status deprecated,obsolete`
- `ibmcloud is images --user-data-format esxi_kickstart,ipxe`
- `ibmcloud is images --remote-account-id provider`
- `ibmcloud is images --remote-account-id 2d1bace7b46e4815a81e52c6ffeba5cf`

#### Command options
{: #command-options-images}

- **--visibility**: List images with given visibility. Valid visibility is: **public** or **private**.
- **--status**: Filters the collection to images with the comma-separated list of status values. Available values: available, deleting, deprecated, failed, obsolete, pending, unusable.
- **--user-data-format**: Filters the collection to images with the comma-separated list of user-data-format values. Available values: cloud_init, esxi_kickstart, ipxe.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--remote-account-id**: Filters the collection to images with a `remote.account.id` property that matches the specified account. Users can also provide ACCOUNT_ID or one of: **provider**, **user**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is image-create
{: #image-create}

Create an image.

```
ibmcloud is image-create IMAGE_NAME ([--file IMAGE_FILE_LOCATION --os-name OPERATING_SYSTEM_NAME [--encrypted-data-key ENCRYPTED_DATA_KEY --encryption-key ENCRYPTION_KEY]] | [--source-volume SOURCE_VOLUME --encryption-key-volume ENCRYPTION_KEY_VOLUME]) [--allowed-use-api-version, --au-api-version ALLOWED_USE_API_VERSION, AU_API_VERSION] [--allowed-use-bare-metal-server, --au-bms ALLOWED_USE_BARE_METAL_SERVER, AU_BMS] [--allowed-use-instance, --au-ins ALLOWED_USE_INSTANCE, AU_INS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--deprecate-at DEPRECATE_AT] [--obsolete-at OBSOLETE_AT] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-image-create}

- `ibmcloud is image-create my-ubuntu-16-amd64 --file cos://us-south/custom-image-vpc-bucket/customImage-0.qcow2 --os-name ubuntu-16-amd64`
- `ibmcloud is image-create my-ubuntu-16-amd64 --file cos://us-south/custom-image-vpc-bucket/customImage-0.qcow2 --os-name ubuntu-16-amd64 --resource-group-id fee82deba12e4c0fb69c3b09d1f12345`
- `ibmcloud is image-create my-ubuntu-16-amd64 --file cos://us-south/custom-image-vpc-bucket/customImage-0.qcow2 --os-name ubuntu-16-amd64 --resource-group-name Default`
- `ibmcloud is image-create my-ubuntu-16-amd64 --file cos://us-south/custom-image-vpc-bucket/customImage-0.qcow2 --os-name ubuntu-16-amd64 --output JSON`
- `ibmcloud is image-create my-ubuntu-16-amd64 --file cos://us-south/custom-image-vpc-bucket/customImage-0.qcow2 --os-name ubuntu-16-amd64 --encrypted-data-key eyJjaXBoZXJ0ZXh0IjoiSFVBS1VxTFFzUVhVRytTdElxTENDS3BjQjZ5Qm9HWlMxOVU9IiwiaXYiOiIxVXdNeTFTNG9odHVOWmJPIiwidmVyc2lvbiI6IjQuMC4wIiwiaGFuZGxlIjoiMWU5MzNkY2QtYjczMi00MDY3LWEyNTUtZDg5MzMxMTdmZGZmIn0= --encryption-key crn:v1:bluemix:public:kms:us-south:a/823bd195e9fd4f0db40ac2e1bffef3e0:2479bd12-1e8e-4506-88d9-bdb9512ac317:key:404f662d-1e18-40b1-aabf-d6c25bca22ea`
- `ibmcloud is image-create my-image-from-volume --source-volume r006-c95c2317-6336-45b4-b67d-087312895a4e`
- `ibmcloud is image-create my-image-from-volume --source-volume r006-c95c2317-6336-45b4-b67d-087312895a4e --encryption-key-volume crn:v1:bluemix:public:kms:us-south:a/823bd195e9fd4f0db40ac2e1bffef3e0:2479bd12-1e8e-4506-88d9-bdb9512ac317:key:404f662d-1e18-40b1-aabf-d6c25bca22ea`
- `ibmcloud is image-create my-image-from-volume --source-volume r006-c95c2317-6336-45b4-b67d-087312895a4e --deprecate-at "2023-03-01T00:45:00Z" --obsolete-at "2023-03-02T00:50:00Z"`
- `ibmcloud is image-create my-ubuntu-16-amd64 --file cos://us-south/custom-image-vpc-bucket/customImage-0.qcow2 --os-name ubuntu-16-amd64 --allowed-use-api-version "2024-10-29" --allowed-use-bare-metal-server "enable_secure_boot==true" --allowed-use-instance true`
- `ibmcloud is image-create my-image-from-volume --source-volume r006-c95c2317-6336-45b4-b67d-087312895a4e --allowed-use-api-version "2024-10-29" --allowed-use-bare-metal-server "enable_secure_boot==true" --allowed-use-instance true`

#### Command options
{: #command-options-image-create}

- **IMAGE_NAME**: Name of the image.
- **--file**: The Cloud Object Store (COS) location of the image file, for example: **cos://us-south/custom-image-vpc-bucket/customImage-0.qcow2**.
- **--os-name**: Name of the operating system for this image.
- **--encrypted-data-key**: A base64-encoded, encrypted representation of the key that was used to encrypt the data for this image.
- **--encryption-key**: The CRN of the root key that was used to wrap the data key (which is ultimately represented as **encrypted_data_key**). Additionally, the root key is used to encrypt volumes created from this image (unless an alternate **encryption_key** is provided at volume creation).
- **--source-volume**: ID or name of the volume. The volume from which to create the image. The specified volume must originate from image. The volume's active and busy property value must be **false**, and the volume attached instance must be in stopped status.
- **--encryption-key-volume**: A reference to the root key to that is used to wrap the system-generated data encryption key for the image. If this property is not provided, the root key from source volume is used.
- **--allowed-use-api-version, --au-api-version**: The API version with which to evaluate the expressions.
- **--allowed-use-bare-metal-server, --au-bms**: The expression that must be satisfied by the properties of a bare metal server that is provisioned with this image. If unspecified, the expression is set to `true`.
- **--allowed-use-instance, --au-ins**: The expression that must be satisfied by the properties of a virtual server instance that is provisioned with this image. If unspecified, the expression is set to `true`.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--deprecate-at**: The deprecation date and time to set for this image. The date and time must not be in the past, and must be earlier than "obsolete_at". Date and time must be in the ISO 8601 format: **2024-03-05T15:31:50.701Z** or **2024-03-05T15:31:50.701+8:00**.
- **--obsolete-at**: The obsolescence date and time to set for this image. The date and time must not be in the past, and must be later than "deprecate_at". Date and time must be in ISO 8601 format: **2024-03-05T15:31:50.701Z** or **2024-03-05T15:31:50.701+8:00**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is image-update
{: #image-update}

Update an image.

```
ibmcloud is image-update IMAGE --name NEW_NAME [--allowed-use-api-version, --au-api-version ALLOWED_USE_API_VERSION, AU_API_VERSION] [--allowed-use-bare-metal-server, --au-bms ALLOWED_USE_BARE_METAL_SERVER, AU_BMS] [--allowed-use-instance, --au-ins ALLOWED_USE_INSTANCE, AU_INS] [--deprecate-at DEPRECATE_AT | --reset-deprecate-at] [--obsolete-at OBSOLETE_AT | --reset-obsolete-at] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-image-update}

- `ibmcloud is image-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-image`
- `ibmcloud is image-update my-image-from-volume-cli --name  my-image-from-volume-cli-do-not-delete --obsolete-at "2023-03-02T04:20:00+05:30"`
- `ibmcloud is image-update my-image-from-volume-cli-do-not-delete --deprecate-at "2023-03-03T04:20:00+05:30"`
- `ibmcloud is image-update  my-image-from-volume-cli-do-not-delete --reset-deprecate-at`
- `ibmcloud is image-update  my-image-from-volume-cli-do-not-delete --reset-obsolete-at`
- `ibmcloud is image-update  my-image-from-volume-cli-do-not-delete --allowed-use-api-version "2024-10-31" --allowed-use-bare-metal-server enable_secure_boot==true --allowed-use-instance true`

#### Command options
{: #command-options-image-update}

- **IMAGE**: ID or name of the image.
- **--name**: New name of the image.
- **--allowed-use-api-version, --au-api-version**: The API version with which to evaluate the expressions.
- **--allowed-use-bare-metal-server, --au-bms**: The expression that must be satisfied by a bare metal server that is provisioned with this image.
- **--allowed-use-instance, --au-ins**: The expression that must be satisfied by a virtual server instance that is provisioned with this image.
- **--deprecate-at**: The deprecation date and time to set for this image. The date and time must not be in the past, and must be earlier than "obsolete_at". Date and time must be in the ISO 8601 format: **2024-03-05T15:31:50.701Z** or **2024-03-05T15:31:50.701+8:00**.
- **--reset-deprecate-at**: Specify this flag to remove an existing deprecation date and time. If the image status is "deprecated", it becomes "available".
- **--obsolete-at**: The obsolescence date and time to set for this image. The date and time must not be in the past, and must be later than "deprecate_at". Date and time must be in ISO 8601 format: **2024-03-05T15:31:50.701Z** or **2024-03-05T15:31:50.701+8:00**.
- **--reset-obsolete-at**: Specify this flag to remove an existing obsolescence date and time. If the image status is "obsolete", it becomes "deprecated" if "deprecate_at" is in the past. Otherwise, it becomes "available".
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is image-delete
{: #image-delete}

Delete one or more images.

```
ibmcloud is image-delete (IMAGE1 IMAGE2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-image-delete}

- **IMAGE1**: ID or name of the image.
- **IMAGE2**: ID or name of the image.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is image-export-job
{: #image-export-job-view}

View details of an image export job.

```
ibmcloud is image-export-job IMAGE JOB [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-image-export-job}

- `ibmcloud is image-export-job 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 6451a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is image-export-job my-image my-export-job`

#### Command options
{: #command-options-image-export-job}

- **IMAGE**: ID or name of the image.
- **JOB**: ID or name of the image export job.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is image-export-jobs
{: #image-export-jobs-list}

List all export jobs of an image.

```
ibmcloud is image-export-jobs IMAGE [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-image-export-jobs}

- `ibmcloud is image-export-jobs 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is image-export-jobs my-image`

#### Command options
{: #command-options-image-export-jobs}

- **IMAGE**: ID or name of the image.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is image-export-job-create
{: #image-export-job-create}

Create an image export job.

```
ibmcloud is image-export-job-create IMAGE --bucket BUCKET [--name NEW_NAME] [--format qcow2 | vhd] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-image-export-job-create}

- `ibmcloud is image-export-job-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-export-job --format qcow2 --bucket my-bucket`
- `ibmcloud is image-export-job-create my-image --name my-export-job --format qcow2 --bucket my-bucket`

#### Command options
{: #command-options-image-export-job-create}

- **IMAGE**: ID or name of the image.
- **--name**: New name of the image export job.
- **--format**: The format to use for the exported image. If the image is encrypted, only qcow2 is supported. One of: **qcow2**, **vhd**. (default: **qcow2**).
- **--bucket**: The Cloud Object Storage bucket to export the image to. The bucket must exist and an IAM service authorization must grant Image Service for VPC of VPC Infrastructure Services writer access to the bucket.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is image-export-job-update
{: #image-export-job-update}

Update an image export job.

```
ibmcloud is image-export-job-update IMAGE JOB --name NAME [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-image-export-job-update}

- `ibmcloud is image-export-job-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 6451a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-image-export-job`
- `ibmcloud is image-export-job-update my-image my-export-job --name my-image-export-job`

#### Command options
{: #command-options-image-export-job-update}

- **IMAGE**: ID or name of the image.
- **JOB**: ID or name of the image export job.
- **--name**: Name of the image export job.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is image-export-job-delete
{: #image-export-job-delete}

Delete one or more image export jobs.

```
ibmcloud is image-export-job-delete IMAGE (JOB1 JOB2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-image-export-job-delete}

- `ibmcloud is image-export-job-delete 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 6451a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is image-export-job-delete my-image my-export-job`

#### Command options
{: #command-options-image-export-job-delete}

- **IMAGE**: ID or name of the image.
- **JOB1**: ID or name of the image export job.
- **JOB2**: ID or name of the image export job.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is image-deprecate
{: #image-deprecate-view}

Deprecate an image.

```
ibmcloud is image-deprecate IMAGE [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-image-deprecate}

- `ibmcloud is image-deprecate my-image-from-volume-cli-do-not-delete`

#### Command options
{: #command-options-image-deprecate}

- **IMAGE**: ID or name of the image.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is image-obsolete
{: #image-obsolete-view}

Obsolete an image.

```
ibmcloud is image-obsolete IMAGE [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-image-obsolete}

- `ibmcloud is image-obsolete my-image-from-volume-cli-do-not-delete`

#### Command options
{: #command-options-image-obsolete}

- **IMAGE**: ID or name of the image.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is image-instance-profiles
{: #image-instance-profiles-list}

List instance profiles that are compatible with an image.

```
ibmcloud is image-instance-profiles IMAGE [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-image-instance-profiles}

- `ibmcloud is image-instance-profiles my-image-from-volume-cli-do-not-delete`
- `ibmcloud is image-instance-profiles my-image-from-volume-cli-do-not-delete --output JSON`
- `ibmcloud is image-instance-profiles r134-064dcec0-5e15-42cf-8b28-a9d27f9cd751`
- `ibmcloud is image-instance-profiles r134-064dcec0-5e15-42cf-8b28-a9d27f9cd751 --output JSON`

#### Command options
{: #command-options-image-instance-profiles}

- **IMAGE**: ID or name of the image.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is image-bare-metal-server-profiles
{: #image-bare-metal-server-profiles-list}

List bare metal server profiles that are compatible with an image.

```
ibmcloud is image-bare-metal-server-profiles IMAGE [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-image-bare-metal-server-profiles}

- `ibmcloud is image-bare-metal-server-profiles my-image`
- `ibmcloud is image-bare-metal-server-profiles my-image --output JSON`
- `ibmcloud is image-bare-metal-server-profiles r134-064dcec0-5e15-42cf-8b28-a9d27f9cd751`
- `ibmcloud is image-bare-metal-server-profiles r134-064dcec0-5e15-42cf-8b28-a9d27f9cd751 --output JSON`

#### Command options
{: #command-options-image-bare-metal-server-profiles}

- **IMAGE**: ID or name of the image.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is catalog-image-offerings
{: #catalog-image-offerings-list}

List all catalog image offerings.

```
ibmcloud is catalog-image-offerings [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-catalog-image-offerings}

- `ibmcloud is catalog-image-offerings`

#### Command options
{: #command-options-catalog-image-offerings}

- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is catalog-image-offering
{: #catalog-image-offering-view}

Get catalog image offering.

```
ibmcloud is catalog-image-offering CATALOG OFFERING [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-catalog-image-offering}

- `ibmcloud is catalog-image-offering 2497ae83-40cb-46ba-ac7f-5303514a2669 54372a73-7a0a-4799-ac9c-8736620c67f1`

#### Command options
{: #command-options-catalog-image-offering}

- **CATALOG**: ID of the catalog.
- **OFFERING**: ID of the offering.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Instances
{: #instances}

### ibmcloud is instance
{: #instance-view}

View details of a virtual server instance.

```
ibmcloud is instance INSTANCE [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance}

- **INSTANCE**: ID or name of the instance.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-initialization-values
{: #instance-initialization-values}

View initialization details of a virtual instance.

```
ibmcloud is instance-initialization-values INSTANCE [--private-key (KEY | @KEY_FILE) [--private-key-passphrase PRIVATE_KEY_PASSPHRASE]] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-initialization-values}

- **INSTANCE**: ID or name of the instance.
- **--private-key**: **key**|**@key-file**. The private key in PEM format to decrypt password.
- **--private-key-passphrase**: The passphrase for the encrypted private key.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instances
{: #instances-list}

List all virtual server instances.

```
ibmcloud is instances [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--reservation RESERVATION] [--vpc VPC] [--dh DH] [--pg PG] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instances}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--reservation**: ID or name of the reservation.
- **--vpc**: ID, name, or CRN of the VPC.
- **--dh**: ID, name, or CRN of the dedicated host.
- **--pg**: ID, name, or CRN of the placement group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-console
{: #instance-console}

Open an interactive console to the virtual server instance. This command opens an interactive serial console by default.

```
ibmcloud is instance-console INSTANCE [--vnc] [-q, --quiet]
```

#### Command options
{: #command-options-instance-console}

- **INSTANCE**: ID or name of the instance.
- **--vnc**: Get the WebSocket URI for the VNC console and open the IBM Cloud web VNC console in the browser for the instance.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-create
{: #instance-create}

Create a virtual server instance.

```
ibmcloud is instance-create INSTANCE_NAME VPC ZONE_NAME PROFILE_NAME SUBNET (([--pnac-name PRIMARY_NAC_NAME] [--pnac-vni PNAC_VNI | (--pnac-vni-ais false | true --pnac-vni-ein true | false --pnac-vni-auto-delete true | false --pnac-vni-ips VNI_RESERVED_IPS_JSON | @VNI_RESERVED_IPS_JSON_FILE --pnac-vni-name PNAC_VNI_NAME [--pnac-vni-rip PNAC_VNI_RIP | (--pnac-vni-rip-address PNAC_VNI_RIP_ADDRESS --pnac-vni-rip-auto-delete true | false --pnac-vni-rip-name PNAC_VNI_RIP_NAME)] --pnac-vni-sgs PNAC_VNI_SGS [--pnac-vni-psfm auto | enabled | disabled])] [--network-attachments NETWORK_ATTACHMENTS_JSON | @NETWORK_ATTACHMENTS_JSON_FILE]) | [([--rip RIP | (--address ADDRESS --auto-delete true | false --ip-name IP_NAME)] [--allow-ip-spoofing false | true]) | --primary-network-interface PRIMARY_NETWORK_INTERFACE_JSON | @PRIMARY_NETWORK_INTERFACE_JSON_FILE] [--network-interface NETWORK_INTERFACE_JSON | @NETWORK_INTERFACE_JSON_FILE]) [--image IMAGE | (--catalog-offering CATALOG_OFFERING | --catalog-offering-version CATALOG_OFFERING_VERSION) [--catalog-offering-plan CATALOG_OFFERING_PLAN]] [--total-volume-bandwidth TOTAL_VOLUME_BANDWIDTH] [--boot-volume BOOT_VOLUME_JSON | @BOOT_VOLUME_JSON_FILE] [--volume-attach VOLUME_ATTACH_JSON | @VOLUME_ATTACH_JSON_FILE] [--keys KEYS] [--dedicated-host DEDICATED_HOST | --dedicated-host-group DEDICATED_HOST_GROUP | --placement-group PLACEMENT_GROUP] [--reservation-affinity-policy, --res-policy disabled | manual | automatic] [--reservation-affinity-pool, --res-pool RESERVATION_AFFINITY_POOL] [--user-data DATA] [--sgs SGS] [--default-trusted-profile DEFAULT_TRUSTED_PROFILE [--default-trusted-profile-auto-link true,false]] [--metadata-service, --ms true | false [--metadata-service-protocol, --msp http | https | --metadata-service-response-hop-limit, --msrhl METADATA_SERVICE_RESPONSE_HOP_LIMIT,MSRHL]] [--host-failure-policy restart | stop] [--confidential-compute-mode disabled | sgx | tdx] [--enable-secure-boot true | false] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [[--cluster-network-attachments CLUSTER_NETWORK_ATTACHMENTS_JSON | @CLUSTER_NETWORK_ATTACHMENTS_JSON_FILE]] [--output JSON] [-i, --interactive] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-create}

- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8`
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"name":"my-volume-name", "capacity":10, "profile": {"name": "general-purpose"},"user_tags": ["my-tag-1"]}}]'`
Create an instance with volume attachment.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"name":"my-volume-name", "bandwidth":1000, "capacity":10, "profile": {"name": "general-purpose"},"user_tags": ["my-tag-1"]}}]'`
Create an instance with volume attachment with bandwidth.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"id":"67531475-bd8a-478e-bcfe-2e53365cd0aa"}}]'`
Create an instance with existing volume in volume attachment.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --keys 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
Create an instance with multiple SSH keys.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "my-boot-vol", "capacity": 150, "profile": {"name": "general-purpose"}}}'`
Create an instance from image with boot volume capacity. The capacity value can range from image's minimum provisioned size to 250.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "my-boot-vol", "profile": {"name": "general-purpose"},"user_tags": ["my-tag-1"]}}'`
Create an instance with boot volume and boot volume with user tags.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"profile": {"name": "general-purpose"},"encryption_key": {"crn": "crn:v1:bluemix:public:kms:us-south:adffc98a0f1f0f95f6613b3b752286b87:e4a29d1a-2ef0-42a6-8fd2-350deb1c647e:key:5437653b-c4b1-447f-9646-b2a2a4cd6179"}}}'`
Create an instance with an encrypted boot volume.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"bandwidth":1000, "profile": {"name": "general-purpose"},"encryption_key": {"crn": "crn:v1:bluemix:public:kms:us-south:adffc98a0f1f0f95f6613b3b752286b87:e4a29d1a-2ef0-42a6-8fd2-350deb1c647e:key:5437653b-c4b1-447f-9646-b2a2a4cd6179"}}}'`
Create an instance with an encrypted boot volume with bandwidth.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --network-interface '[{"name": "secondary-nic", "allow_ip_spoofing": true, "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}]'`
Create an instance that is attached to the secondary network interface.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "primary_ip": {"address": "10.240.129.10", "auto-delete": true, "name": "my-reserved-ip"}, "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}'`
Create an instance with primary network interface configuration in JSON.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --sgs 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --address 10.240.129.10 --auto-delete true --ip-name my-reserved-ip --allow-ip-spoofing true`
Create an instance with the primary network interface configuration that includes security groups, reserved IP settings, and source IP spoofing setting.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --sgs 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --reserved-ip 0711-5c7f016e-5bd2-42e3-8dff-81519e4e2469 --allow-ip-spoofing true`
Create an instance with the primary network interface configuration that includes security groups, existing reserved IP, and source IP spoofing setting.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host c019b1f7-c4d6-430c-aaa4-e0cc25d47277`
Create an instance to place in the wanted dedicated host.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host-group a4738ceb-5e59-4601-849a-61d7895740ee`
Create an instance to place in the wanted dedicated host group.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --placement-group 1d2afa0f-b9f2-4d85-ae35-a08885269644`
Create an instance to place in the wanted placement group.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --total-volume-bandwidth 4000`
Create an instance with specific total volumes bandwidth.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --metadata-service true`
Create an instance with metadata service enabled or disabled.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --metadata-service true --metadata-service-protocol http --metadata-service-response-hop-limit 60`
Create an instance with metadata service configuration.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --reservation-affinity-policy manual --reservation-affinity-pool r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2`
Create an instance with reservation affinity.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --reservation-affinity-policy manual --reservation-affinity-pool crn:v1:bluemix:public:is:us-south:a/123456::vpc:4727d842-f94f-4a2d-824a-9bc9b02c523b`
Create an instance with reservation affinity.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --default-trusted-profile Profile-c9fe8182-870a-49df-8308-c8bb7394c4c3 --default-trusted-profile-auto-link true`
Create an instance with the default trusted profile
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --host-failure-policy restart`
Create an instance with an availability policy on host failure.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 bx2-2x8 my-subnet --image ibm-ubuntu-20-04-2-minimal-amd64-1 --volume-attach '[{"volume": {"name":"my-vol-1"}}]'`
Create an instance with existing volume in volume attachment by using resource name.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 mx2-2x16 my-subnet --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host my-dedicated-host`
Create an instance to place in the wanted dedicated host by using resource name.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 mx2-2x16 my-subnet --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host-group my-dedicated-host-group`
Create an instance to place in the wanted dedicated host group by using resource name.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 mx2-2x16 my-subnet --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --placement-group my-placement-host-group`
Create an instance to place in the wanted placement group by using resource name.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 bx2-2x8 --image ibm-ubuntu-20-04-2-minimal-amd64-1 --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"name":"my-subnet"}, "primary_ip": {"name": "my-reserved-ip"}, "security_groups": [{"name": "my-security-group-1"}, {"name": "my-security-group-2"}]}'`
Create an instance with the primary network interface configuration by using resource name.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 bx2-2x8 my-subnet --image ibm-ubuntu-20-04-2-minimal-amd64-1 --network-interface '[{"name": "secondary-nic", "allow_ip_spoofing": true, "subnet": {"id":"my-subnet"}, "security_groups": [{"id": "my-security-group-1"}, {"id": "my-security-group-2"}]}]'`
Create an instance that is attached to the secondary network interface by using resource name.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"id": "67531475-bd8a-478e-bcfe-2e53365cd0aa"}}'`
Create an instance from an existing boot volume.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 bx2-2x8 my-subnet --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "my-existing-boot-vol"}}'`
Create an instance from an existing boot volume by using resource name.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --catalog-offering crn:v1:bluemix:public:globalcatalog-collection:global:a/efe5afc483594adaa8325e2b4d1290df:2497ae83-40cb-46ba-ac7f-5303514a2669:offering:54372a73-7a0a-4799-ac9c-8736620c67f1`
Create an instance from a catalog offering.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --catalog-offering-version crn:v1:bluemix:public:globalcatalog-collection:global:a/efe5afc483594adaa8325e2b4d1290df:2497ae83-40cb-46ba-ac7f-5303514a2669:offering:54372a73-7a0a-4799-ac9c-8736620c67f1`
Create an instance from a catalog offering version.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --catalog-offering-version crn:v1:bluemix:public:globalcatalog-collection:global:a/efe5afc483594adaa8325e2b4d1290df:2497ae83-40cb-46ba-ac7f-5303514a2669:offering:54372a73-7a0a-4799-ac9c-8736620c67f1 --catalog-offering-plan crn:v1:bluemix:public:globalcatalog-collection:global:a/123456:51c9e0db-2911-45a6-adb0-ac5332d27cf2:plan:sw.51c9e0db-2911-45a6-adb0-ac5332d27cf2.772c0dbe-aa62-482e-adbe-a3fc20101e0e`
Create instance from catalog offering version and plan.
- `ibmcloud is instance-create --interactive`
Create an instance interactively.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --pnac-name cli-pnac-1 --pnac-vni 7322-1293a27a-7178-4e62-ba5b-272623c989aa --network-attachments [{"name": "instance-snac-1","virtual_network_interface": {"id":"02h7-56705448-c9d9-43dc-aa11-20d42333cd87"}}] --image --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8`
Create an instance with a network attachment and an existing virtual network interface.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --pnac-name cli-pnac-1 --pnac-vni-ais true --pnac-vni-ein true --pnac-vni-auto-delete true --pnac-vni-ips [{"id": "7322-f61b85bd-d963-4069-bb72-b58ed9ebc9f5"}] --pnac-vni-name cli-panc-vni-1 --pnac-vni-rip bee-olympics-perplexed-briskness --network-attachments [{"name": "instance-snac-1","virtual_network_interface": {"id":"02h7-56705448-c9d9-43dc-aa11-20d42333cd87"}}]`
Create an instance with a network attachment and new virtual network interface with existing reserved IP.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --pnac-name cli-pnac-1 --pnac-vni-ais true --pnac-vni-ein true --pnac-vni-auto-delete true --pnac-vni-ips [{"id": "7322-f61b85bd-d963-4069-bb72-b58ed9ebc9f5"},{"address": "10.240.128.13", "auto_delete" : true, "name": "vni-pnac-sip-1"}] --pnac-vni-name cli-panc-vni-1 --pnac-vni-rip-address 10.240.128.13 --pnac-vni-rip-auto-delete true --pnac-vni-rip-name pnac-vni-rip-1 --pnac-vni-sgs r134-8e0e4ad9-4ca3-4d5f-b9d8-7a967693d231`
Create an instance with a network attachment and new virtual network interface with existing reserved IP.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --cluster-network-attachments '[{"name": "instance-cnac-1","cluster_network_interface": {"id":"02h7-56705448-c9d9-43dc-aa11-20d42333cd87"}}]'`
Create an instance with a cluster network attachment with existing cluster network interface with existing reserved IP.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --cluster-network-attachments '[{"name":"cli-cnac-1", "cluster_network_interface": {"auto_delete": true, "name": "cni-1",  "primary_ip": { "auto-delete": true, "name": "my-reserved-ip"}, "subnet": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}}]'`
Create an instance with a cluster network attachment.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 bx2-2x8 my-subnet --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "boot-vol-name", "capacity": 150, "profile": {"name": "general-purpose"}, "source_snapshot": {"id": "150847e3-ef0d-4927-9341-6d0a7bae424f"}}}'`
Create an instance from a snapshot with boot volume capacity. The capacity value can range from snapshot's minimum capacity to 250.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "boot-vol-name", "profile": {"name": "general-purpose"}, "source_snapshot": {"id": "150847e3-ef0d-4927-9341-6d0a7bae424f"}}}'`
Create an instance with boot volume attachment from a volume snapshot.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 bx2-2x8 my-subnet --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"name":"my-volume-name", "profile": {"name": "general-purpose"}, "source_snapshot": {"name": "my-snapshot-name"}}}]'`
Create an instance with volume attachment from a volume snapshot by using the resource name.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"name":"my-volume-name", "capacity":10, "profile": {"name": "general-purpose"}, "source_snapshot": {"id": "150847e3-ef0d-4927-9341-6d0a7bae424f"}}}]'`
Create an instance with a volume attachment from a volume snapshot.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 bx2-2x8 my-subnet --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "boot-vol-name", "profile": {"name": "general-purpose"}, "source_snapshot": {"name": "my-snapshot-name"}}}'`
Create an instance with a boot volume attachment from a volume snapshot by using the resource name.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 my-subnet --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "boot-vol-name", "profile": {"name": "general-purpose"}, "source_snapshot": {"name": "test-cli"}, "allowed_use":{"instance":"true","bare_metal_server":"true","api_version":"2025-06-30"}}}' --volume-attach '[{"volume": {"name":"my-volume-name", "capacity":100, "profile": {"name": "general-purpose"}, "source_snapshot": {"id": "r006-523cf6c7-0591-43b9-b4ff-6663791e2814"}, "allowed_use":{"instance":"true","bare_metal_server":"true","api_version":"2025-06-30"}}}]'`
Create an instance with allowed use in boot-volume and volume-attachment.

#### Command options
{: #command-options-instance-create}

- **INSTANCE_NAME**: Name of the instance.
- **VPC**: ID or name of the VPC.
- **ZONE_NAME**: Name of the zone.
- **PROFILE_NAME**: Name of the profile.
- **SUBNET**: ID or name of the subnet.
- **--image**: ID or name of the image.
- **--catalog-offering**: The CRN for the IBM Cloud catalog offering. If specified, the latest version of that offering is used. For more information about creating a catalog offering, see [Onboarding software to your account](/docs/account?topic=account-create-private-catalog&interface=cli).
- **--catalog-offering-version**: The CRN for the version of a IBM Cloud catalog offering. For more information about creating a version for the catalog offering, see [Onboarding software to your account](/docs/account?topic=account-create-private-catalog&interface=cli).
- **--catalog-offering-plan**: The CRN for billing plan of a IBM Cloud catalog offering. If unspecified, no billing plan is used (free). Must be specified for catalog offering versions that require a billing plan.
- **--total-volume-bandwidth**: The amount of bandwidth (in megabits per second) that is allocated exclusively to instance storage volumes. An increase in this value results in a corresponding decrease to total network bandwidth.
- **--boot-volume**: BOOT_VOLUME_JSON|@BOOT_VOLUME_JSON_FILE, boot volume attachment in JSON or JSON file. For the data schema, see the **boot_volume_attachment** property in the [API documentation](/apidocs/vpc#create-instance).
- **--volume-attach**: VOLUME_ATTACH_JSON|@VOLUME_ATTACH_JSON_FILE, volume attachment in JSON or JSON file, list of volumes. For the data schema, see the **volume_attachments** property in the [API documentation](/apidocs/vpc#create-instance).
- **--keys**: Comma-separated IDs or names of SSH keys. SSH keys can be either RSA or Ed25519. Ed25519 can be used only if the operating system supports this key type. Ed25519 can't be used with Windows or VMware images.
- **--dedicated-host**: ID or name of the host destination where the instance is placed.
- **--dedicated-host-group**: ID or name of the host group destination where the instance is placed.
- **--placement-group**: ID or name of the placement group. The placement group restrictions for the virtual server instance.
- **--reservation-affinity-policy, --res-policy**: The reservation affinity policy to use for this virtual server instance. The policy defaults to manual if pool is not empty. The policy defaults to disabled if a placement_target is set. The policy defaults to automatic in all other cases. One of: **disabled**, **manual**, **automatic**.
- **--reservation-affinity-pool, --res-pool**: ID, name, or CRN of the reservation that is available to use by this virtual server instance.
- **--user-data**: data|@data-file. User data to transfer to the virtual server instance.
- **--rip**: ID or name of the existing reserved IP.
- **--address**: The IP address to reserve, which must not already be reserved on the subnet.
- **--auto-delete**: If set to **true**, this reserved IP automatically deletes when the target is deleted. One of: **true**, **false**. (default: **true**).
- **--ip-name**: The user-defined name for this reserved IP. Names must be unique within the subnet that the reserved IP resides in. Names beginning with **ibm-** are reserved for provider-owned resources.
- **--allow-ip-spoofing**: Disables the source and destination checks on this interface. If **false**, source IP spoofing is not allowed on this interface. One of: **false**, **true**.
- **--primary-network-interface**: PRIMARY_NETWORK_INTERFACE_JSON|@PRIMARY_NETWORK_INTERFACE_JSON_FILE, primary network interface in JSON or JSON file. For the data schema, see the **primary_network_interface** property in the [API documentation](/apidocs/vpc#create-instance).
- **--network-interface**: NETWORK_INTERFACE_JSON|@NETWORK_INTERFACE_JSON_FILE, network interface attachment in JSON or JSON file. For the data schema, see the **network_interfaces** property in the [API documentation](/apidocs/vpc#create-instance).
- **--pnac-name**: Name of the primary network attachment.
- **--pnac-vni**: ID or name of the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-ais**: Allow IP Spoofing (AIS). Indicates whether source IP spoofing is allowed on this virtual network interface that is associated with primary network attachment. One of: **false**, **true**. (default: **false**).
- **--pnac-vni-ein**: Enable infrastructure NAT (EIN). If **true**, the VPC infrastructure performs any needed NAT operations on the VNI. To attach a VNI to an instance, the value needs to be true. Floating_ips must not have more than one floating IP. If **false**, the packet is passed unmodified to or from the VNI, which allows it to perform any needed NAT operations. Allow_ip_spoofing must be false. Can be attached only to a target with a resource_type of bare_metal_server_network_attachment. One of: **true**, **false**. (default: **true**).
- **--pnac-vni-auto-delete**: Indicates whether this virtual network interface that is associated with primary network attachment automatically deletes when target is deleted. One of: **true**, **false**. (default: **true**).
- **--pnac-vni-ips**: VNI_RESERVED_IPS_JSON | @VNI_RESERVED_IPS_JSON_FILE, Secondary reserved IP addresses is in JSON or JSON file, to bind to the virtual network interface. For the data schema, see the IPS property in the [API documentation](/apidocs/vpc/latest#create-virtual-network-interface). One of: **VNI_RESERVED_IPS_JSON**, **@VNI_RESERVED_IPS_JSON_FILE**.
- **--pnac-vni-name**: The name for this virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-rip**: ID or name of the reserved IP to bind to the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-rip-address**: The IP address of the reserved IP to bind to the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-rip-auto-delete**: Indicates whether this reserved IP automatically deletes when either target is deleted, or if the reserved IP is unbound. One of: **true**, **false**. (default: **true**).
- **--pnac-vni-rip-name**: The name for this reserved IP to bind to the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-sgs**: IDs or names of the security groups to use for the virtual network interface that are associated with the primary network attachment.
- **--pnac-vni-psfm**: The protocol state filtering mode to use for this virtual network interface. If auto, protocol state packet filtering is enabled or disabled based on the virtual network interface's `target` resource type. One of: **auto**, **enabled**, **disabled**. (default: **auto**).
- **--network-attachments**: NETWORK_ATTACHMENTS_JSON|@NETWORK_ATTACHMENTS_JSON_FILE. Network attachment configuration is in JSON or JSON file. For the data schema, see the **network_attachments** property in the [API documentation](/apidocs/vpc#create-bare-metal-server). One of: **NETWORK_ATTACHMENTS_JSON**, **@NETWORK_ATTACHMENTS_JSON_FILE**.
- **--sgs**: Comma-separated security group ID or name for primary network interface or primary network attachment.
- **--default-trusted-profile**: ID or name of the trusted profile.
- **--default-trusted-profile-auto-link**: If set to true, the system creates a link to the specified target trusted profile during instance creation. Regardless of whether a link is created by the system or manually by using the IAM Identity service, it automatically deletes when the instance is deleted. One of: **true,false**. (default: **true**).
- **--metadata-service, --ms**: Enable or disable the Instance Metadata Service. One of: **true**, **false**.
- **--metadata-service-protocol, --msp**: The communication protocol for the metadata service endpoint. The protocol applies only when the metadata service is enabled. One of: **http**, **https**. (default: **http**).
- **--metadata-service-response-hop-limit, --msrhl**: The hop limit (IP time to live) for IP response packets from the metadata service.
- **--host-failure-policy**: The action to perform if the compute host experiences a failure. One of: **restart**, **stop**. (default: **restart**).
- **--confidential-compute-mode**: The confidential compute mode to use for this virtual server instance. If unspecified, the default confidential compute mode from the profile is used. One of: **disabled**, **sgx**, **tdx**.
- **--enable-secure-boot**: Indicates whether secure boot is enabled for this virtual server instance. If unspecified, the default secure boot mode from the profile is used. One of: **true**, **false**.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--cluster-network-attachments**: CLUSTER_NETWORK_ATTACHMENTS_JSON|@CLUSTER_NETWORK_ATTACHMENTS_JSON_FILE. Cluster network attachment configuration is in JSON or JSON file. For the data schema, see the **cluster_network_attachments** property in the [API documentation](/apidocs/vpc#create-instance). One of: **CLUSTER_NETWORK_ATTACHMENTS_JSON**, **@CLUSTER_NETWORK_ATTACHMENTS_JSON_FILE**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--interactive, -i**:
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-create-from-template
{: #instance-create-from-template}

Create a virtual server instance from instance template.

```
ibmcloud is instance-create-from-template --template TEMPLATE (([--pnac-name PRIMARY_NAC_NAME] [--pnac-vni PNAC_VNI | ((--pnac-vni-subnet PNAC_VNI_SUBNET [--vpc VPC]) --pnac-vni-ais false | true --pnac-vni-ein true | false --pnac-vni-auto-delete true | false --pnac-vni-ips VNI_RESERVED_IPS_JSON | @VNI_RESERVED_IPS_JSON_FILE --pnac-vni-name PNAC_VNI_NAME [--pnac-vni-rip PNAC_VNI_RIP | (--pnac-vni-rip-address PNAC_VNI_RIP_ADDRESS --pnac-vni-rip-auto-delete true | false --pnac-vni-rip-name PNAC_VNI_RIP_NAME)] --pnac-vni-sgs PNAC_VNI_SGS [--pnac-vni-psfm auto | enabled | disabled])] [--network-attachments NETWORK_ATTACHMENTS_JSON | @NETWORK_ATTACHMENTS_JSON_FILE]) | (--subnet SUBNET [--rip RIP | (--address ADDRESS --auto-delete true | false --ip-name IP_NAME)] [--allow-ip-spoofing false | true]) | --primary-network-interface PRIMARY_NETWORK_INTERFACE_JSON | @PRIMARY_NETWORK_INTERFACE_JSON_FILE [--network-interface NETWORK_INTERFACE_JSON | @NETWORK_INTERFACE_JSON_FILE]) [--name Name] [--profile PROFILE] [--zone ZONE] [--vpc VPC] [--image IMAGE | (--catalog-offering CATALOG_OFFERING | --catalog-offering-version CATALOG_OFFERING_VERSION) [--catalog-offering-plan CATALOG_OFFERING_PLAN]] [--total-volume-bandwidth TOTAL_VOLUME_BANDWIDTH] [--boot-volume BOOT_VOLUME_JSON | @BOOT_VOLUME_JSON_FILE] [--volume-attach VOLUME_ATTACH_JSON | @VOLUME_ATTACH_JSON_FILE] [--keys KEYS] [--dedicated-host DEDICATED_HOST | --dedicated-host-group DEDICATED_HOST_GROUP | --placement-group PLACEMENT_GROUP] [--reservation-affinity-policy, --res-policy disabled | manual | automatic] [--reservation-affinity-pool, --res-pool RESERVATION_AFFINITY_POOL] [--user-data DATA] [--sgs SGS] [--default-trusted-profile DEFAULT_TRUSTED_PROFILE [--default-trusted-profile-auto-link true,false]] [--metadata-service, --ms true | false [--metadata-service-protocol, --msp http | https | --metadata-service-response-hop-limit, --msrhl METADATA_SERVICE_RESPONSE_HOP_LIMIT,MSRHL]] [--host-failure-policy restart | stop] [--confidential-compute-mode disabled | sgx | tdx] [--enable-secure-boot true | false] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [[--cluster-network-attachments CLUSTER_NETWORK_ATTACHMENTS_JSON | @CLUSTER_NETWORK_ATTACHMENTS_JSON_FILE]] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-create-from-template}

- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d`
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --resource-group-id 7494aacb866142fba11a88d75cb37bd8 --output JSON`
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --reservation-affinity-policy manual --reservation-affinity-pool r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2s`
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --reservation-affinity-policy manual --reservation-affinity-pool crn:v1:bluemix:public:is:us-south:a/123456::vpc:4727d842-f94f-4a2d-824a-9bc9b02c523b`
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --boot-volume '{"delete_volume_on_instance_delete": false, "name": "boot-vol-attachment-name", "volume": {"name": "myvol2", "profile": {"name": "general-purpose"}}}'`
Create an instance from an instance template with the boot volume configuration.
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --vpc r006-beca4c2f-625f-45de-bd95-c8eb12f6842a --zone us-south-1 --subnet 0717-fe2e13d0-9ba8-43bd-ab6b-a1fad51557ac --address 10.240.129.10 --auto-delete true --ip-name my-reserved-ip --sgs r006-19c2ce0d-d35d-47bc-8147-120edddd3de5 --allow-ip-spoofing true`
Create an instance from an instance template with the primary network interface configuration.
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --vpc r006-beca4c2f-625f-45de-bd95-c8eb12f6842a --zone us-south-1 --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"id":"0717-fe2e13d0-9ba8-43bd-ab6b-a1fad51557ac"}, "primary_ip": {"address": "10.240.129.10", "auto-delete": true, "name": "my-reserved-ip"}, "security_groups": [{"id": "r006-19c2ce0d-d35d-47bc-8147-120edddd3de5"}]}'`
Create an instance from an instance template with the primary network interface configuration in JSON format.
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --network-interface '[{"name": "secondary-nic", "allow_ip_spoofing": true, "subnet": {"id":"0737-f6b5a638-1fda-476b-9e2f-7a550fbb62b8"}, "primary_ip": {"address": "10.240.129.10", "auto-delete": true, "name": "my-reserved-ip"}, "security_groups": [{"id": "r006-caba3deb-136b-42c8-831a-1dbcc0f1912e"}]}, {"name": "third-nic", "allow_ip_spoofing": true, "subnet": {"id":"0737-6b939577-4839-47b0-b42f-a4b29a94c7d9"}, "primary_ip": {"address": "10.240.129.100", "auto-delete": true, "name": "my-reserved-ip"}, "security_groups": [{"id": "r006-caba3deb-136b-42c8-831a-1dbcc0f1912e"}]}]'`
Create an instance from an instance template with the second network interfaces configuration.
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name new-instance-name --volume-attach '[{"delete_volume_on_instance_delete": false, "name": "my-volume-attachment1", "volume": {"name": "myvol2", "capacity": 200, "profile": {"name": "general-purpose"}}}, {"delete_volume_on_instance_delete": true, "name": "my-volume-attachment2", "volume": {"name": "myvol3", "capacity": 300, "iops": 1000, "profile": {"name": "custom"}}}]'`
Create an instance from an instance template with the data volume's configuration.
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name new-instance-name --image r006-ed3f775f-ad7e-4e37-ae62-7199b4988b00 --profile cx2-2x4 --key r006-02a07b78-6e5f-40a2-86a2-99e01916128c,r006-29e19fb1-e2b9-49d0-ab6e-9702e99f5021 --user-data @/tmp/userdata.sh`
Create an instance from an instance template with image/profile/key/user data configuration.
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --dedicated-host 0737-4ab6b37d-4695-4efb-9439-0528b5550dfe --profile mx2-2x16`
Create an instance from an instance template with the wanted dedicated host.
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --dedicated-host-group 0737-7290ea56-7543-4590-8558-ca8cd51b12c4 --profile mx2-2x16`
Create an instance from an instance template with the wanted dedicated host group.
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name new-instance-name --metadata-service true`
Create an instance from an instance template with metadata service enabled or disabled.
- `ibmcloud is instance-create-from-template --template my-template --name new-instance-name --vpc my-vpc --zone us-south-1 --subnet my-subnet --reserved-ip my-reserved-ip --sgs my-security-group --allow-ip-spoofing true`
Create an instance from an instance template with the primary network interface configuration by using resource name.
- `ibmcloud is instance-create-from-template --template my-template --name my-instance --vpc my-vpc --zone us-south-1 --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"id":"my-subnet"}, "primary_ip": {"name": "my-reserved-ip"}, "security_groups": [{"name": "my-security-group"}]}'`
Create an instance from an instance template with the primary network interface configuration in JSON format by using resource name.
- `ibmcloud is instance-create-from-template --template my-template --name my-instance --network-interface '[{"name": "secondary-nic", "allow_ip_spoofing": true, "subnet": {"id":"my-subnet-1"}, "primary_ip": {"name": "my-reserved-ip"}, "security_groups": [{"id": "my-security-group-1"}]}, {"name": "third-nic", "allow_ip_spoofing": true, "subnet": {"id":"my-subnet-1"}, "primary_ip": {"name": "my-reserved-ip-2"}, "security_groups": [{"id": "my-security-group-2"}]}]'`
Create an instance from instance template with the second network interfaces configuration by using resource name.
- `ibmcloud is instance-create-from-template --template my-template --name new-instance-name  --subnet my-subnet --image ibm-ubuntu-20-04-2-minimal-amd64-1 --volume-attach '[{"volume": {"name":"my-vol-1"}}]'`
Create an instance from instance template with an existing volume in volume attachment by using resource name.
- `ibmcloud is instance-create-from-template --template my-template --name new-instance-name --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"name":"my-subnet"}, "primary_ip": {"name": "my-reserved-ip"}, "security_groups": [{"name": "my-security-group-1"}, {"name": "my-security-group-2"}]}'`
Create an instance from an instance template with the primary network interface configuration by using resource name.
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --cluster-network-attachments [{"name": "instance-cnac-1","cluster_network_interface": {"id":"02h7-56705448-c9d9-43dc-aa11-20d42333cd87"}}]`
Create an instance from an instance template with a cluster network attachment that has an existing cluster network interface and an existing reserved IP.
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --cluster-network-attachments [{"name":"cli-cnac-1", "cluster_network_interface": {"auto_delete": true, "name": "cni-1",  "primary_ip": { "auto-delete": true, "name": "my-reserved-ip"}, "subnet": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}}]`
Create an instance from an instance template with a cluster network attachment.

#### Command options
{: #command-options-instance-create-from-template}

- **--template**: ID or name of the instance template.
- **--name**: Name of the instance.
- **--profile**: Name of the instance profile.
- **--zone**: Name of the zone.
- **--vpc**: The ID or name of the VPC. It is only required to specify the unique resource by name that is inside this VPC or to override the VPC value in the template.
- **--image**: ID or name of the image.
- **--catalog-offering**: The CRN for the IBM Cloud catalog offering. If specified, the latest version of that offering is used. For more information about creating a catalog offering, see [Onboarding software to your account](/docs/account?topic=account-create-private-catalog&interface=cli).
- **--catalog-offering-version**: The CRN for the version of a IBM Cloud catalog offering. For more information about creating a version for the catalog offering, see [Onboarding software to your account](/docs/account?topic=account-create-private-catalog&interface=cli).
- **--catalog-offering-plan**: The CRN for billing plan of a IBM Cloud catalog offering. If unspecified, no billing plan is used (free). Must be specified for catalog offering versions that require a billing plan.
- **--total-volume-bandwidth**: The amount of bandwidth (in megabits per second) that is allocated exclusively to instance storage volumes. An increase in this value results in a corresponding decrease to total network bandwidth.
- **--boot-volume**: BOOT_VOLUME_JSON|@BOOT_VOLUME_JSON_FILE, boot volume attachment in JSON or JSON file. For the data schema, see the **boot_volume_attachment** property in the [API documentation](/apidocs/vpc#create-instance).
- **--volume-attach**: VOLUME_ATTACH_JSON|@VOLUME_ATTACH_JSON_FILE, volume attachment in JSON or JSON file, list of volumes. For the data schema, see the **volume_attachments** property in the [API documentation](/apidocs/vpc#create-instance).
- **--keys**: Comma-separated IDs or names of SSH keys. SSH keys can be either RSA or Ed25519. Ed25519 can be used only if the operating system supports this key type. Ed25519 can't be used with Windows or VMware images.
- **--dedicated-host**: ID or name of the host destination where the instance is placed.
- **--dedicated-host-group**: ID or name of the host group destination where the instance is placed.
- **--placement-group**: ID or name of the placement group. The placement group restrictions for the virtual server instance.
- **--reservation-affinity-policy, --res-policy**: The reservation affinity policy to use for this virtual server instance. The policy defaults to manual if pool is not empty. The policy defaults to disabled if a placement_target is set. The policy defaults to automatic in all other cases. One of: **disabled**, **manual**, **automatic**.
- **--reservation-affinity-pool, --res-pool**: ID, name, or CRN of the reservation that is available to use by this virtual server instance.
- **--user-data**: data|@data-file. User data to transfer to the virtual server instance.
- **--subnet**: ID or name of the subnet.
- **--rip**: ID or name of the existing reserved IP.
- **--address**: The IP address to reserve, which must not already be reserved on the subnet.
- **--auto-delete**: If set to **true**, this reserved IP automatically deletes when the target is deleted. One of: **true**, **false**. (default: **true**).
- **--ip-name**: The user-defined name for this reserved IP. Names must be unique within the subnet that the reserved IP resides in. Names beginning with **ibm-** are reserved for provider-owned resources.
- **--allow-ip-spoofing**: Disables the source and destination checks on this interface. If **false**, source IP spoofing is not allowed on this interface. One of: **false**, **true**.
- **--primary-network-interface**: PRIMARY_NETWORK_INTERFACE_JSON|@PRIMARY_NETWORK_INTERFACE_JSON_FILE, primary network interface in JSON or JSON file. For the data schema, see the **primary_network_interface** property in the [API documentation](/apidocs/vpc#create-instance).
- **--network-interface**: NETWORK_INTERFACE_JSON|@NETWORK_INTERFACE_JSON_FILE, network interface attachment in JSON or JSON file. For the data schema, see the **network_interfaces** property in the [API documentation](/apidocs/vpc#create-instance).
- **--pnac-name**: Name of the primary network attachment.
- **--pnac-vni**: ID or name of the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-subnet**: The associated subnet.
- **--pnac-vni-ais**: Allow IP Spoofing (AIS). Indicates whether source IP spoofing is allowed on this virtual network interface that is associated with primary network attachment. One of: **false**, **true**. (default: **false**).
- **--pnac-vni-ein**: Enable infrastructure NAT (EIN). If **true**, the VPC infrastructure performs any needed NAT operations on the VNI. To attach a VNI to an instance, the value needs to be true. Floating_ips must not have more than one floating IP. If **false**, the packet is passed unmodified to or from the VNI, which allows it to perform any needed NAT operations. Allow_ip_spoofing must be false. Can be attached only to a target with a resource_type of bare_metal_server_network_attachment. One of: **true**, **false**. (default: **true**).
- **--pnac-vni-auto-delete**: Indicates whether this virtual network interface that is associated with primary network attachment automatically deletes when target is deleted. One of: **true**, **false**. (default: **true**).
- **--pnac-vni-ips**: VNI_RESERVED_IPS_JSON | @VNI_RESERVED_IPS_JSON_FILE, Secondary reserved IP addresses is in JSON or JSON file, to bind to the virtual network interface. For the data schema, see the IPS property in the [API documentation](/apidocs/vpc/latest#create-virtual-network-interface). One of: **VNI_RESERVED_IPS_JSON**, **@VNI_RESERVED_IPS_JSON_FILE**.
- **--pnac-vni-name**: The name for this virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-rip**: ID or name of the reserved IP to bind to the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-rip-address**: The IP address of the reserved IP to bind to the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-rip-auto-delete**: Indicates whether this reserved IP automatically deletes when either target is deleted, or if the reserved IP is unbound. One of: **true**, **false**. (default: **true**).
- **--pnac-vni-rip-name**: The name for this reserved IP to bind to the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-sgs**: IDs or names of the security groups to use for the virtual network interface that are associated with the primary network attachment.
- **--pnac-vni-psfm**: The protocol state filtering mode to use for this virtual network interface. If auto, protocol state packet filtering is enabled or disabled based on the virtual network interface's `target` resource type. One of: **auto**, **enabled**, **disabled**. (default: **auto**).
- **--network-attachments**: NETWORK_ATTACHMENTS_JSON|@NETWORK_ATTACHMENTS_JSON_FILE. Network attachment configuration is in JSON or JSON file. For the data schema, see the **network_attachments** property in the [API documentation](/apidocs/vpc#create-bare-metal-server). One of: **NETWORK_ATTACHMENTS_JSON**, **@NETWORK_ATTACHMENTS_JSON_FILE**.
- **--sgs**: Comma-separated security group ID or name for primary network interface or primary network attachment.
- **--default-trusted-profile**: ID or name of the trusted profile.
- **--default-trusted-profile-auto-link**: If set to true, the system creates a link to the specified target trusted profile during instance creation. Regardless of whether a link is created by the system or manually by using the IAM Identity service, it automatically deletes when the instance is deleted. One of: **true,false**. (default: **true**).
- **--metadata-service, --ms**: Enable or disable the Instance Metadata Service. One of: **true**, **false**.
- **--metadata-service-protocol, --msp**: The communication protocol for the metadata service endpoint. The protocol applies only when the metadata service is enabled. One of: **http**, **https**. (default: **http**).
- **--metadata-service-response-hop-limit, --msrhl**: The hop limit (IP time to live) for IP response packets from the metadata service.
- **--host-failure-policy**: The action to perform if the compute host experiences a failure. One of: **restart**, **stop**.
- **--confidential-compute-mode**: The confidential compute mode to use for this virtual server instance. If unspecified, the default confidential compute mode from the profile is used. One of: **disabled**, **sgx**, **tdx**.
- **--enable-secure-boot**: Indicates whether secure boot is enabled for this virtual server instance. If unspecified, the default secure boot mode from the profile is used. One of: **true**, **false**.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--cluster-network-attachments**: CLUSTER_NETWORK_ATTACHMENTS_JSON|@CLUSTER_NETWORK_ATTACHMENTS_JSON_FILE. Cluster network attachment configuration is in JSON or JSON file. For the data schema, see the **cluster_network_attachments** property in the [API documentation](/apidocs/vpc#create-instance). One of: **CLUSTER_NETWORK_ATTACHMENTS_JSON**, **@CLUSTER_NETWORK_ATTACHMENTS_JSON_FILE**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-delete
{: #instance-delete}

Delete one or more virtual server instances.

```
ibmcloud is instance-delete (INSTANCE1 INSTANCE2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-delete}

- **INSTANCE1**: ID or name of the instance.
- **INSTANCE2**: ID or name of the instance.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-disk
{: #instance-disk-view}

View details of a virtual server instance disk.

```
ibmcloud is instance-disk INSTANCE INSTANCE_DISK [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-disk}

- **INSTANCE**: ID or name of the instance.
- **INSTANCE_DISK**: ID or name of the instance disk.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-disk-update
{: #instance-disk-update}

Update a virtual server instance disk.

```
ibmcloud is instance-disk-update INSTANCE INSTANCE_DISK --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-disk-update}

- **INSTANCE**: ID or name of the instance.
- **INSTANCE_DISK**: ID or name of the instance disk.
- **--name**: New name of instance disk.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-disks
{: #instance-disks-list}

List all disks of a virtual server instance.

```
ibmcloud is instance-disks INSTANCE [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-disks}

- **INSTANCE**: ID or name of the instance.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-interface
{: #instance-network-interface-view}

View details of a network interface of a virtual server instance.

```
ibmcloud is instance-network-interface INSTANCE NIC [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-network-interface}

- **INSTANCE**: ID or name of the instance.
- **NIC**: ID or name of the network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-interface-create
{: #instance-network-interface-create}

Create a network interface for a virtual server instance.

```
ibmcloud is instance-network-interface-create NIC_NAME INSTANCE SUBNET [--vpc VPC] [--rip RIP | (--address ADDRESS --auto-delete true | false --ip-name IP_NAME)] [(--sg SG1 --sg SG2 ...)] [--allow-ip-spoofing false | true] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-network-interface-create}

- `ibmcloud is instance-network-interface-create my-vnic 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is instance-network-interface-create my-vnic 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --rip 0711-5c7f016e-5bd2-42e3-8dff-81519e4e2469`
- `ibmcloud is instance-network-interface-create my-vnic 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --address 10.2.3.4 --ip-name my-reserved-ip --auto-delete false`
- `ibmcloud is instance-network-interface-create my-vnic 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --address 10.2.3.4 --ip-name my-reserved-ip --auto-delete false --sg 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --sg 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8`
- `ibmcloud is instance-network-interface-create my-vnic my-instance my-subnet --sg my-sg-1 --sg my-sg-2`
Create a network interface for a virtual server instance with security group by using resource name.

#### Command options
{: #command-options-instance-network-interface-create}

- **NIC_NAME**: Name of the network interface.
- **INSTANCE**: ID or name of the instance.
- **SUBNET**: ID or name of the subnet.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--rip**: ID or name of the existing reserved IP.
- **--address**: The IP address to reserve, which must not already be reserved on the subnet.
- **--auto-delete**: If set to **true**, this reserved IP automatically deletes when the target is deleted. One of: **true**, **false**. (default: **true**).
- **--ip-name**: The user-defined name for this reserved IP. Names must be unique within the subnet that the reserved IP resides in. Names beginning with **ibm-** are reserved for provider-owned resources.
- **--sg**: ID or name of the security group.
- **--allow-ip-spoofing**: Disables the source and destination checks on this interface. If **false**, source IP spoofing is not allowed on this interface. One of: **false**, **true**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-interface-delete
{: #instance-network-interface-delete}

Remove one or more network interfaces from a virtual server instance.

```
ibmcloud is instance-network-interface-delete INSTANCE (NIC1 NIC2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-network-interface-delete}

- **INSTANCE**: ID or name of the instance.
- **NIC1**: ID or name of the network interface.
- **NIC2**: ID or name of the network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-interface-floating-ip
{: #instance-network-interface-floating-ip-view}

View details of a floating IP that is associated with a network interface.

```
ibmcloud is instance-network-interface-floating-ip INSTANCE NIC FLOATING_IP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-network-interface-floating-ip}

- **INSTANCE**: ID or name of the instance.
- **NIC**: ID or name of the network interface.
- **FLOATING_IP**: ID or name of the floating IP.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-interface-floating-ip-add
{: #instance-network-interface-floating-ip-add}

Associate a floating IP with a network interface.

```
ibmcloud is instance-network-interface-floating-ip-add INSTANCE NIC FLOATING_IP [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-network-interface-floating-ip-add}

- `ibmcloud is instance-network-interface-floating-ip-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is instance-network-interface-floating-ip-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --output JSON`
- `ibmcloud is instance-network-interface-floating-ip-add my-instance my-nic my-floating-ip`
Associate a floating IP with a network interface by using resource name.

#### Command options
{: #command-options-instance-network-interface-floating-ip-add}

- **INSTANCE**: ID or name of the instance.
- **NIC**: ID or name of the network interface.
- **FLOATING_IP**: ID or name of the floating IP.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-interface-floating-ip-remove
{: #instance-network-interface-floating-ip-remove}

Disassociate a floating IP from a network interface.

```
ibmcloud is instance-network-interface-floating-ip-remove INSTANCE NIC FLOATING_IP [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-network-interface-floating-ip-remove}

- **INSTANCE**: ID or name of the instance.
- **NIC**: ID or name of the network interface.
- **FLOATING_IP**: ID or name of the floating IP.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-interface-floating-ips
{: #instance-network-interface-floating-ips-list}

List all floating IPs that are associated with a network interface.

```
ibmcloud is instance-network-interface-floating-ips INSTANCE NIC [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-network-interface-floating-ips}

- **INSTANCE**: ID or name of the instance.
- **NIC**: ID or name of the network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-interface-reserved-ips
{: #instance-network-interface-reserved-ips-list}

List all reserved IPs that are associated with a network interface.

```
ibmcloud is instance-network-interface-reserved-ips INSTANCE NIC [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-network-interface-reserved-ips}

- **INSTANCE**: ID or name of the instance.
- **NIC**: ID or name of the network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-interface-reserved-ip
{: #instance-network-interface-reserved-ip-view}

View details of a reserved IP that is associated with a network interface.

```
ibmcloud is instance-network-interface-reserved-ip INSTANCE NIC RESERVED_IP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-network-interface-reserved-ip}

- **INSTANCE**: ID or name of the instance.
- **NIC**: ID or name of the network interface.
- **RESERVED_IP**: ID or name of the reserved IP.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-interface-update
{: #instance-network-interface-update}

Update a network interface of a virtual server instance.

```
ibmcloud is instance-network-interface-update INSTANCE NIC --name NEW_NAME [--allow-ip-spoofing false | true] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-network-interface-update}

- **INSTANCE**: ID or name of the instance.
- **NIC**: ID or name of the network interface.
- **--name**: New name of NIC.
- **--allow-ip-spoofing**: Disables the source and destination checks on this interface. If **false**, source IP spoofing is not allowed on this interface. One of: **false**, **true**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-interfaces
{: #instance-network-interfaces-list}

List all network interfaces of a virtual server instance.

```
ibmcloud is instance-network-interfaces INSTANCE [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-network-interfaces}

- **INSTANCE**: ID or name of the instance.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-profile
{: #instance-profile-view}

View details of a virtual server instance profile.

```
ibmcloud is instance-profile PROFILE_NAME [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-profile}

- **PROFILE_NAME**: Name of the profile.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-profiles
{: #instance-profiles-list}

List all virtual server instance profiles in the region.

```
ibmcloud is instance-profiles [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-profiles}

- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-reboot
{: #instance-reboot}

Restart the operating system of an instance.

```
ibmcloud is instance-reboot INSTANCE [--no-wait] [-f, --force] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-reboot}

- **INSTANCE**: ID or name of the instance.
- **--no-wait**: Execute the action immediately and drop all queued actions.
- **--force, -f**: Force the operation without confirmation.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-start
{: #instance-start}

Start a virtual server instance.

```
ibmcloud is instance-start INSTANCE [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-start}

- **INSTANCE**: ID or name of the instance.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-stop
{: #instance-stop}

Stop a virtual server instance.

- When you stop an instance and restart it, a new private IP address is assigned if the instance wasn't created with a static IP address or the primary_ipv4_address attribute wasn't set when the instance was created by using the CLI or API. For more information about setting a static IP address, see primary_network_interface in the [API reference](/apidocs/vpc/latest#create-instance){: external}.
-{:tip}

```
ibmcloud is instance-stop INSTANCE [--no-wait] [-f, --force] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-stop}

- **INSTANCE**: ID or name of the instance.
- **--no-wait**: Execute the action immediately and drop all queued actions.
- **--force, -f**: Force the operation without confirmation.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-update
{: #instance-update}

Update a virtual server instance.

```
ibmcloud is instance-update INSTANCE [--name NEW_NAME] [--profile PROFILE] [--total-volume-bandwidth TOTAL_VOLUME_BANDWIDTH] [--dedicated-host DEDICATED_HOST | --dedicated-host-group DEDICATED_HOST_GROUP] [--reservation-affinity-policy, --res-policy disabled | manual | automatic] [--reservation-affinity-pool, --res-pool RESERVATION_AFFINITY_POOL] [--metadata-service, --ms true | false] [--metadata-service-protocol, --msp http | https] [--metadata-service-response-hop-limit, --msrhl METADATA_SERVICE_RESPONSE_HOP_LIMIT,MSRHL] [--host-failure-policy restart | stop] [--confidential-compute-mode disabled | sgx | tdx] [--enable-secure-boot true | false] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-update}

- `ibmcloud is instance-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-instance-name`
- `ibmcloud is instance-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-instance-name --output JSON`
- `ibmcloud is instance-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --metadata-service true`
- `ibmcloud is instance-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --dedicated-host d7e9969b-1453-4b51-89a6-6b5531c3d959`
- `ibmcloud is instance-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --dedicated-host-group c05ecb00-701d-4ad1-8c84-2256f0a53f70`
- `ibmcloud is instance-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --total-volume-bandwidth 4000`
- `ibmcloud is instance-update my-instance --name new-instance-name`
- `ibmcloud is instance-update my-instance --dedicated-host my-dedicated-host`
- `ibmcloud is instance-update my-instance --dedicated-host-group my-dedicated-host-group`
- `ibmcloud is instance-update my-instance --reservation-affinity-policy manual --reservation-affinity-pool crn:v1:bluemix:public:is:us-south:a/123456::vpc:4727d842-f94f-4a2d-824a-9bc9b02c523b`
- `ibmcloud is instance-update my-instance --reservation-affinity-policy manual --reservation-affinity-pool r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2`

#### Command options
{: #command-options-instance-update}

- **INSTANCE**: ID or name of the instance.
- **--name**: New name of the virtual server instance.
- **--profile**: The profile to use for this virtual server instance. To change the profile, the instance status must be `stopping` or `stopped`. In addition, the requested profile must: 1. Be compatible with any placement target constraints. For example, if the instance is placed on a dedicated host, the requested profile `family` must be the same as the dedicated host `family`.
- **--total-volume-bandwidth**: The amount of bandwidth (in megabits per second) that is allocated exclusively to instance storage volumes. An increase in this value results in a corresponding decrease to total network bandwidth.
- **--dedicated-host**: ID or name of the host destination where the instance is placed.
- **--dedicated-host-group**: ID or name of the host group destination where the instance is placed.
- **--reservation-affinity-policy, --res-policy**: The reservation affinity policy to use for this virtual server instance. The policy defaults to manual if pool is not empty. The policy defaults to disabled if a placement_target is set. The policy defaults to automatic in all other cases. One of: **disabled**, **manual**, **automatic**.
- **--reservation-affinity-pool, --res-pool**: ID, name, or CRN of the reservation that is available to use by this virtual server instance.
- **--metadata-service, --ms**: Enable or disable the Instance Metadata Service. One of: **true**, **false**.
- **--metadata-service-protocol, --msp**: The communication protocol for the metadata service endpoint. The protocol applies only when the metadata service is enabled. One of: **http**, **https**. (default: **http**).
- **--metadata-service-response-hop-limit, --msrhl**: The hop limit (IP time to live) for IP response packets from the metadata service.
- **--host-failure-policy**: The action to perform if the compute host experiences a failure. One of: **restart**, **stop**.
- **--confidential-compute-mode**: The confidential compute mode to use for this virtual server instance. If unspecified, the default confidential compute mode from the profile is used. One of: **disabled**, **sgx**, **tdx**.
- **--enable-secure-boot**: Indicates whether secure boot is enabled for this virtual server instance. If unspecified, the default secure boot mode from the profile is used. One of: **true**, **false**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-volume-attachment
{: #instance-volume-attachment-view}

View details of a volume attachment.

```
ibmcloud is instance-volume-attachment INSTANCE VOLUME_ATTACHMENT [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-volume-attachment}

- **INSTANCE**: ID or name of the instance.
- **VOLUME_ATTACHMENT**: ID or name of the volume attachment.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-volume-attachments
{: #instance-volume-attachments-list}

List all volume attachments to an instance.

```
ibmcloud is instance-volume-attachments INSTANCE [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-volume-attachments}

- **INSTANCE**: ID or name of the instance.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-volume-attachment-add
{: #instance-volume-attachment-add}

Create a volume attachment, connecting a volume to an instance.

```
ibmcloud is instance-volume-attachment-add NAME INSTANCE (VOLUME | --profile PROFILE --new-volume-name NEW_VOLUME_NAME --iops IOPS --encryption-key ENCRYPTION_KEY --capacity CAPACITY --bandwidth BANDWIDTH --tags TAGS --source-snapshot SOURCE_SNAPSHOT [--allowed-use-api-version, --au-api-version ALLOWED_USE_API_VERSION, AU_API_VERSION] [--allowed-use-bare-metal-server, --au-bms ALLOWED_USE_BARE_METAL_SERVER, AU_BMS] [--allowed-use-instance, --au-ins ALLOWED_USE_INSTANCE, AU_INS]) [--auto-delete false | true] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-volume-attachment-add}

- `ibmcloud is instance-volume-attachment-add data-vol-name 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 1a6b7274-678d-4dfb-8981-c71dd9d4daa5`
- `ibmcloud is instance-volume-attachment-add data-vol-name 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 --auto-delete true`
- `ibmcloud is instance-volume-attachment-add data-vol-name 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 --auto-delete true --output JSON`
- `ibmcloud is instance-volume-attachment-add data-vol-name 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --profile general-purpose --source-snapshot eaf9d6ca-35bf-4ac7-bc45-d0f2507f2830 --auto-delete true --output JSON`
- `ibmcloud is instance-volume-attachment-add data-vol-name 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --profile general-purpose ---capacity 10 --auto-delete true --tags my-tag-1,my-tag-2`
- `ibmcloud is instance-volume-attachment-add data-vol-name my-instance my-volume --auto-delete true`
Add an existing volume to a virtual server instance by using resource name.
- `ibmcloud is instance-volume-attachment-add data-vol-name 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --profile general-purpose --source-snapshot eaf9d6ca-35bf-4ac7-bc45-d0f2507f2830 --allowed-use-api-version "2024-10-31" --allowed-use-bare-metal-server enable_secure_boot==true --allowed-use-instance true --auto-delete true --output JSON`

#### Command options
{: #command-options-instance-volume-attachment-add}

- **NAME**: Name of the volume attachment.
- **INSTANCE**: ID or name of the instance.
- **VOLUME**: ID or name of the volume.
- **--new-volume-name**: The name of new volume.
- **--profile**: Name of the profile.
- **--iops**: Input/output operations per second for the volume, it is only applicable for custom profile volumes. For the available IOPS ranges, see [Custom IOPS profile] [Onboarding software to your account](/docs/vpc?topic=vpc-block-storage-profiles#custom).
- **--encryption-key**: The CRN of the Key Management Service root key.
- **--capacity**: The capacity of the volume in gigabytes. Range 10 - 16000 for custom and general-purpose profile volumes, 10 - 9600 for 5iops-tier profile volumes, 10 - 4800 for 10iops-tier profile volumes.
- **--bandwidth**: The maximum bandwidth (in megabits per second) for the volume. For this property to be specified, the volume storage_generation must be 2.
- **--tags**: Comma-separated tags for the volume.
- **--source-snapshot**: ID, name, or CRN of the snapshot to clone volume.
- **--allowed-use-api-version, --au-api-version**: The API version with which to evaluate the expressions.
- **--allowed-use-bare-metal-server, --au-bms**: The expression that must be satisfied by the properties of a bare metal server that is provisioned with the image data in this volume. If unspecified, the expression is set to `true`.
- **--allowed-use-instance, --au-ins**: The expression that must be satisfied by the properties of a virtual server instance that is provisioned with this volume. If unspecified, the expression is set to `true`.
- **--auto-delete**: The attached volume is deleted when the instance is deleted. One of: **false**, **true**. (default: **false**).
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-volume-attachment-detach
{: #instance-volume-attachment-detach}

Delete one or more volume attachments, detaching volume from an instance.

```
ibmcloud is instance-volume-attachment-detach INSTANCE (VOLUME_ATTACHMENT1 VOLUME_ATTACHMENT2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-volume-attachment-detach}

- **INSTANCE**: ID or name of the instance.
- **VOLUME_ATTACHMENT1**: ID or name of the volume attachment.
- **VOLUME_ATTACHMENT2**: ID or name of the volume attachment.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-volume-attachment-update
{: #instance-volume-attachment-update}

Update a volume attachment.

```
ibmcloud is instance-volume-attachment-update INSTANCE VOLUME_ATTACHMENT [--name NEW_NAME] [--auto-delete true | false] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-volume-attachment-update}

- `ibmcloud is instance-volume-attachment-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 --name name2`
- `ibmcloud is instance-volume-attachment-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 --auto-delete true`
- `ibmcloud is instance-volume-attachment-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 --name name2 --auto-delete true --output JSON`
- `ibmcloud is instance-volume-attachment-update my-instance my-vol-att --name name2`
Update a volume attachment by using resource name.

#### Command options
{: #command-options-instance-volume-attachment-update}

- **INSTANCE**: ID or name of the instance.
- **VOLUME_ATTACHMENT**: ID or name of the volume attachment.
- **--name**: New name of the volume.
- **--auto-delete**: The attached volume is deleted when the instance is deleted. One of: **true**, **false**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-attachments
{: #instance-network-attachments-list}

List all network attachments of an instance.

```
ibmcloud is instance-network-attachments INSTANCE [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-network-attachments}

- **INSTANCE**: ID or name of the instance.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-attachment
{: #instance-network-attachment-view}

View details of a network attachment of an instance.

```
ibmcloud is instance-network-attachment INSTANCE NAC [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-network-attachment}

- **INSTANCE**: ID or name of the instance.
- **NAC**: ID or name of the network attachment.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-attachment-create
{: #instance-network-attachment-create}

Create a network attachment for an instance.

```
ibmcloud is instance-network-attachment-create INSTANCE [--vni VNI | ((--vni-subnet VNI_SUBNET [--vpc VPC]) --vni-ais false | true --vni-ein true | false --vni-auto-delete true | false --vni-ips VNI_RESERVED_IPS_JSON | @VNI_RESERVED_IPS_JSON_FILE --vni-name VNI_NAME [--vni-rip VNI_RIP | (--vni-rip-address VNI_RIP_ADDRESS --vni-rip-auto-delete true | false --vni-rip-name VNI_RIP_NAME)] [--vni-psfm auto | enabled | disabled] --vni-sgs VNI_SGS)] [--name NAC_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-network-attachment-create}

- `ibmcloud is  instance-network-attachment-create 02h7_ef1b0428-f138-4d5e-a8e2-e9f35e397cf8 --vni-ais false  --vni-ein true  --vni-auto-delete true  --vni-ips '[{"id": "02h7-b982a5f1-804b-4dd9-b448-777ae3641242"}]' --vni-name ins-vni-1 --vni-rip  02h7-f9203bfc-ea46-4431-9b66-a9ae223e9076  --vni-sgs r026-b315a040-8ea9-49c4-8974-b7ab373c660c`
- `ibmcloud is  instance-network-attachment-create 02h7_ef1b0428-f138-4d5e-a8e2-e9f35e397cf8  --vni-rip  02h7-f9203bfc-ea46-4431-9b66-a9ae223e9076`
- `ibmcloud is  instance-network-attachment-create 02h7_ef1b0428-f138-4d5e-a8e2-e9f35e397cf8  --vni-rip-address "10.245.0.34"  --vni-subnet cli-subnet --vpc vpc-1`
- `ibmcloud is  instance-network-attachment-create 02h7_ef1b0428-f138-4d5e-a8e2-e9f35e397cf8  --vni-subnet 02h7-275c2a52-1890-4473-83a0-54de53da8a25`
- `ibmcloud is  instance-network-attachment-create 02h7_02b4927a-7837-4568-9653-6ae51a861c9d --vni 02h7-123156e0-3aee-489f-bcdc-78cdc2549c0d`

#### Command options
{: #command-options-instance-network-attachment-create}

- **INSTANCE**: ID or name of the instance.
- **--name**: The name for this bare metal server network attachment.
- **--vni**: ID or name of the virtual network interface that is for this bare metal server network attachment.
- **--vni-subnet**: The associated subnet.
- **--vpc**: ID or name of the VPC. This ID or name is required only to specify the unique subnet by name inside this VPC.
- **--vni-ais**: Allow IP Spoofing (AIS). Indicates whether source IP spoofing is allowed on this virtual network interface. One of: **false**, **true**. (default: **false**).
- **--vni-ein**: Enable Infrastructure NAT (EIN). If **true**, the VPC infrastructure performs any needed NAT operations. If **false**, the packet is passed unmodified to or from the virtual network interface, which allows the virtual machine that is associated with the floating IP to perform any needed NAT operations. One of: **true**, **false**. (default: **true**).
- **--vni-auto-delete**: Indicates whether this virtual network interface automatically deletes when the target is deleted. One of: **true**, **false**. (default: **true**).
- **--vni-ips**: ips VNI_RESERVED_IPS_JSON | @VNI_RESERVED_IPS_JSON_FILE, Secondary reserved IP addresses in JSON or JSON file, to bind to the virtual network interface. For the data schema, check the ips property in the [API documentation](/apidocs/vpc/latest#create-virtual-network-interface). One of: **VNI_RESERVED_IPS_JSON**, **@VNI_RESERVED_IPS_JSON_FILE**.
- **--vni-name**: The name for this virtual network interface.
- **--vni-rip**: ID or name of the reserved IP to bind to the virtual network interface. Required if subnet is not specified. The reserved IP must be unbound.
- **--vni-rip-address**: The IP address of the reserved IP to bind to the virtual network interface. Requires subnet to be specified.
- **--vni-rip-auto-delete**: Indicates whether this reserved IP automatically deletes when either target is deleted, or if the reserved IP is unbound. One of: **true**, **false**.
- **--vni-rip-name**: The name for this reserved IP to bind to the virtual network interface. The name must not be used by another reserved IP in the subnet. Names that start with ibm- are reserved for provider-owned resources, and are not allowed.
- **--vni-psfm**: The protocol state filtering mode to use for this virtual network interface. If auto, protocol state packet filtering is enabled or disabled based on the virtual network interface's `target` resource type. One of: **auto**, **enabled**, **disabled**. (default: **auto**).
- **--vni-sgs**: IDs or Names of the security groups to use for this virtual network interface. If unspecified, the default security group of the VPC for the subnet is used.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-attachment-update
{: #instance-network-attachment-update}

Update a network attachment of an instance.

```
ibmcloud is instance-network-attachment-update INSTANCE NAC --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-network-attachment-update}

- `ibmcloud is ins-nacu cli-instance-1 empty-ribcage-jiffy-stitch --name cli-instance-nac`
- `ibmcloud is ins-nacu 02h7_ef1b0428-f138-4d5e-a8e2-e9f35e397cf8 02h7-a5c765f9-ebcd-41a0-89df-c6512d7f0147 --name ins-net-attch-1`

#### Command options
{: #command-options-instance-network-attachment-update}

- **INSTANCE**: ID or name of the instance.
- **NAC**: ID or name of the network attachment.
- **--name**: New name of the network attachment.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-attachment-delete
{: #instance-network-attachment-delete}

Remove one or more network attachments from an instance.

```
ibmcloud is instance-network-attachment-delete INSTANCE (NAC1 NAC2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-network-attachment-delete}

- **INSTANCE**: ID or name of the instance.
- **NAC1**: ID or name of the network attachment.
- **NAC2**: ID or name of the network attachment.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-cluster-network-attachments
{: #instance-cluster-network-attachments-list}

List all cluster network attachments of an instance.

```
ibmcloud is instance-cluster-network-attachments INSTANCE [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-cluster-network-attachments}

- **INSTANCE**: ID or name of the instance.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-cluster-network-attachment
{: #instance-cluster-network-attachment-view}

View details of a cluster network attachment of an instance.

```
ibmcloud is instance-cluster-network-attachment INSTANCE CNAC [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-cluster-network-attachment}

- **INSTANCE**: ID or name of the instance.
- **CNAC**: ID or name of the cluster network attachment.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-cluster-network-attachment-update
{: #instance-cluster-network-attachment-update}

Update a cluster network attachment of an instance.

```
ibmcloud is instance-cluster-network-attachment-update INSTANCE CNAC --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-cluster-network-attachment-update}

- `ibmcloud is ins-cnacu cli-instance-1 empty-ribcage-jiffy-stitch --name cli-instance-cnac`
- `ibmcloud is ins-cnacu 02h7_ef1b0428-f138-4d5e-a8e2-e9f35e397cf8 02h7-a5c765f9-ebcd-41a0-89df-c6512d7f0147 --name in-cl-net-attch-1`

#### Command options
{: #command-options-instance-cluster-network-attachment-update}

- **INSTANCE**: ID or name of the instance.
- **CNAC**: ID or name of the cluster network attachment.
- **--name**: New name of the cluster network attachment.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-cluster-network-attachment-create
{: #instance-cluster-network-attachment-create}

Create a cluster network attachment for an instance.

```
ibmcloud is instance-cluster-network-attachment-create INSTANCE [(--cni CNI [--cluster-network CLUSTER_NETWORK]) | ((--cni-subnet CNI_SUBNET [--cluster-network CLUSTER_NETWORK]) --cni-auto-delete true | false --cni-name CNI_NAME [(--cni-primary-ip CNI_PRIMARY_IP [--cluster-network CLUSTER_NETWORK]) | (--cni-primary-ip-address CNI_PRIMARY_IP_ADDRESS --cni-primary-ip-auto-delete true | false --cni-primary-ip-name CNI_PRIMARY_IP_NAME)])] [--name CNAC_NAME] [--cnac CNAC] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-cluster-network-attachment-create}

- `ibmcloud is  instance-cluster-network-attachment-create my-instance --cni 02h7-f9203bfc-ea46-4431-9b66-a9ae223e9076 --name my-ins-cnat`
- `ibmcloud is  instance-cluster-network-attachment-create 02h7_ef1b0428-f138-4d5e-a8e2-e9f35e397cf8 --cni my-cluster-network-interface --cluster-network my-cluster-network`
- `ibmcloud is  instance-cluster-network-attachment-create 02h7_ef1b0428-f138-4d5e-a8e2-e9f35e397cf8 --cni-auto-delete true --cni-subnet my-cluster-network-subnet --cluster-network my-cluster-network --cni-primary-ip  02h7-f9203bfc-ea46-4431-9b66-a9ae223e9076`
- `ibmcloud is  ins-cnacc my-instance --cni-auto-delete true --cni-subnet 02h7_ef1b0428-f138-4d5e-a8e2-e9f35e397cf8 --cni-primary-ip-address 10.245.0.34 --cni-primary-ip-auto-delete true --cni-primary-ip-name my-cni-ip`
- `ibmcloud is  instance-cluster-network-attachment-create 02h7_ef1b0428-f138-4d5e-a8e2-e9f35e397cf8 --cni my-cluster-network-interface  --cluster-network 02h7-f9203bfc-ea46-4431-9b66-a9ae223e9076 --cnac my-cnac-before-this-cnac --name my-cnac --output json`

#### Command options
{: #command-options-instance-cluster-network-attachment-create}

- **INSTANCE**: ID or name of the instance.
- **--name**: The name for this instance cluster network attachment.
- **--cnac**: ID or name of the instance cluster network attachment to insert this instance cluster network attachment immediately before.
- **--cni**: ID or name of the cluster network interface that is for this intance cluster network attachment.
- **--cluster-network**: ID or name for the cluster network.
- **--cni-auto-delete**: Indicates whether this cluster network interface automatically deletes when the target is deleted. One of: **true**, **false**.
- **--cni-name**: The name for this cluster network interface.
- **--cni-subnet**: ID or name of the associated cluster network subnet.
- **--cni-primary-ip**: ID or name of the cluster network subnet reserved IP to bind to the cluster network interface.
- **--cni-primary-ip-address**: The IP address of the reserved IP to bind to the cluster network interface. Requires subnet to be specified.
- **--cni-primary-ip-auto-delete**: Indicates whether this reserved IP automatically deletes when either target is deleted, or if the reserved IP is unbound. One of: **true**, **false**.
- **--cni-primary-ip-name**: The name for this reserved IP to bind to the cluster network interface. The name must not be used by another reserved IP in the cluster subnet. Names that start with ibm- are reserved for provider-owned resources, and are not allowed.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-cluster-network-attachment-delete
{: #instance-cluster-network-attachment-delete}

Remove one or more cluster network attachments from an instance.

```
ibmcloud is instance-cluster-network-attachment-delete INSTANCE (CNAC1 CNAC2 ...) [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-cluster-network-attachment-delete}

- **INSTANCE**: ID or name of the instance.
- **CNAC1**: ID or name of the cluster network attachment.
- **CNAC2**: ID or name of the cluster network attachment.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

## Keys
{: #keys}

### ibmcloud is key
{: #key-view}

View details of a key.

```
ibmcloud is key KEY [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-key}

- **KEY**: ID or name of the key.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is key-create
{: #key-create}

Import an RSA public key.

```
ibmcloud is key-create KEY_NAME (KEY | @KEY_FILE) [--key-type rsa | ed25519] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-key-create}

- `ibmcloud is key-create my-key "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDL9osaBrUD8uCBzIJo5YBvX8wtGrE+kcC7YZtID/nNYrjeCB26eFASHia5tmqmuCo434UygGSd5qj3t/3v/a7NZoMr/0+qspQF+dUVIl+xIsKTWYQ+gtYbJlvW+FIlNTOA4vbOXLg+nGGUCoaV79azmny4mYJbbo15i+Q3CI+w9bwOAwzqeGKaeOjpo5hdDcFW0QLDxKmQHKMLX8slsx3kB9I5wPe8C/ZBBDBBkZKK2y3RJBjaKxi0beFueo6ngUKOLooReefiBGpdoOJIi6Gf7vRduoBTmbyVvSv08wcrANtYSzGwDpqrEshEafv8bKo42MYHsPT2OwAbsFyqWQj5 test@example"`
- `ibmcloud is key-create my-key @/tmp/my_id_rsa.pub`
- `ibmcloud is key-create my-key @/tmp/my_id_rsa.pub --output JSON`
- `ibmcloud is key-create my-key "ssh-ed25519 AAAAC3NzaC1lZDI1NTE6AAAAID/R2T8h6CPvZr/InxpBrxh8bmG2RTyB8vzUTvOtQhaJ test@example.com" --key-type ed25519`
- `ibmcloud is key-create my-key @/tmp/my_id_ed25519.pub --key-type ed25519`
- `ibmcloud is key-create my-key @/tmp/my_id_ed25519.pub --key-type ed25519 --output JSON`

#### Command options
{: #command-options-key-create}

- **KEY_NAME**: ID or name of the key.
- **KEY**: **key**|**@key-file**. The public SSH key to import into the system.
- **--key-type**: The crypto-system used by this key. Default is rsa. One of: **rsa**, **ed25519**.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is key-delete
{: #key-delete}

Delete one or more keys.

```
ibmcloud is key-delete (KEY1 KEY2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-key-delete}

- `ibmcloud is key-delete e9e7655e-0000-0000-0000-0000001a957a --output JSON`
- `ibmcloud is key-delete e9e7655e-0000-0000-0000-0000001a957a -f`

#### Command options
{: #command-options-key-delete}

- **KEY1**: ID or name of the key.
- **KEY2**: ID or name of the key.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is key-update
{: #key-update}

Update the name of a key.

```
ibmcloud is key-update KEY --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-key-update}

- `ibmcloud is key-update e9e7655e-0000-0000-0000-0000001a957a  --name my-new-name`
- `ibmcloud is key-update e9e7655e-0000-0000-0000-0000001a957a  --name my-new-name --output JSON`

#### Command options
{: #command-options-key-update}

- **KEY**: ID or name of the key.
- **--name**: New name for the key.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is keys
{: #keys-list}

List all keys.

```
ibmcloud is keys [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-keys}

- `ibmcloud is keys --resource-group-name Default --output JSON`
- `ibmcloud is keys --resource-group-id 11baaa8984beb82690daab08767et --output JSON`

#### Command options
{: #command-options-keys}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Dedicated hosts
{: #dedicated-hosts}

### ibmcloud is dedicated-host-profiles
{: #dedicated-host-profiles-list}

List all host profiles in the region.

```
ibmcloud is dedicated-host-profiles [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-dedicated-host-profiles}

- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host-profile
{: #dedicated-host-profile-view}

View details of a host profile.

```
ibmcloud is dedicated-host-profile PROFILE_NAME [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-dedicated-host-profile}

- **PROFILE_NAME**: Name of the profile.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host-groups
{: #dedicated-host-groups-list}

List all host groups.

```
ibmcloud is dedicated-host-groups [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--zone ZONE] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-dedicated-host-groups}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--zone**: Filters the collection to resources with a zone name property that matches the exact specified name.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host-group
{: #dedicated-host-group-view}

View details of a host group.

```
ibmcloud is dedicated-host-group HOST_GROUP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-dedicated-host-group}

- **HOST_GROUP**: ID or name of the host group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host-group-create
{: #dedicated-host-group-create}

Create a host group.

```
ibmcloud is dedicated-host-group-create --zone ZONE_NAME --family FAMILY --class CLASS [--name NAME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-dedicated-host-group-create}

- `ibmcloud is dedicated-host-group-create --family memory --class mx2 --zone us-south-1 --name my-host-group`
- `ibmcloud is dedicated-host-group-create --family memory --class mx2 --zone us-south-1 --name my-host-group --output JSON`

#### Command options
{: #command-options-dedicated-host-group-create}

- **--zone**: Name of the zone.
- **--name**: New name for the host group.
- **--family**: The dedicated host profile family for hosts in this group.
- **--class**: The dedicated host profile class for hosts in this group.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host-group-update
{: #dedicated-host-group-update}

Update a host group.

```
ibmcloud is dedicated-host-group-update HOST_GROUP --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-dedicated-host-group-update}

- `ibmcloud is dedicated-host-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name-host-group`
- `ibmcloud is dedicated-host-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name-host-group --output JSON`

#### Command options
{: #command-options-dedicated-host-group-update}

- **HOST_GROUP**: ID or name of the host group.
- **--name**: New name of the host group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host-group-delete
{: #dedicated-host-group-delete}

Delete one or more host groups.

```
ibmcloud is dedicated-host-group-delete (HOST_GROUP1 HOST_GROUP2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-dedicated-host-group-delete}

- **HOST_GROUP1**: ID or name of the host group.
- **HOST_GROUP2**: ID or name of the host group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-hosts
{: #dedicated-hosts-list}

List all hosts.

```
ibmcloud is dedicated-hosts [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--zone ZONE] [--dhg DHG] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-dedicated-hosts}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--zone**: Filters the collection to resources with a zone name property that matches the exact specified name.
- **--dhg**: ID or name of the host group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host
{: #dedicated-host-view}

View details of a host.

```
ibmcloud is dedicated-host HOST [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-dedicated-host}

- **HOST**: ID or name of the host.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host-create
{: #dedicated-host-create}

Create a host.

```
ibmcloud is dedicated-host-create --profile PROFILE --dhg DHG [--enabled true | false] [--name NAME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-dedicated-host-create}

- `ibmcloud is dedicated-host-create --profile dh2-56x344 --dhg 74213016-f179-4055-b161-46fd42a9d98a --name my-host`
- `ibmcloud is dedicated-host-create --profile dh2-56x344 --dhg 74213016-f179-4055-b161-46fd42a9d98a --name my-host --enabled false`
- `ibmcloud is dedicated-host-create --profile dh2-56x344 --dhg 74213016-f179-4055-b161-46fd42a9d98a --name my-host --output JSON`

#### Command options
{: #command-options-dedicated-host-create}

- **--profile**: Name of the host profile.
- **--dhg**: ID or name of the host group.
- **--enabled**: Enable or disable the instance placement in the host. One of: **true**, **false**. (default: **true**).
- **--name**: New name for the host.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host-update
{: #dedicated-host-update}

Update a host.

```
ibmcloud is dedicated-host-update HOST [--name NEW_NAME] [--enabled true | false] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-dedicated-host-update}

- `ibmcloud is dedicated-host-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name-host-group`
- `ibmcloud is dedicated-host-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name-host-group --enabled false --output JSON`

#### Command options
{: #command-options-dedicated-host-update}

- **HOST**: ID or name of the host.
- **--name**: New name of the host.
- **--enabled**: Enable or disable the instance placement in the host. One of: **true**, **false**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host-delete
{: #dedicated-host-delete}

Delete one or more hosts.

```
ibmcloud is dedicated-host-delete (HOST1 HOST2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-dedicated-host-delete}

- **HOST1**: ID or name of the host.
- **HOST2**: ID or name of the host.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host-disks
{: #dedicated-host-disks-list}

List all disks of a dedicated host.

```
ibmcloud is dedicated-host-disks HOST [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-dedicated-host-disks}

- **HOST**: ID or name of the host.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host-disk
{: #dedicated-host-disk-view}

View details of a dedicated host disk.

```
ibmcloud is dedicated-host-disk HOST DISK [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-dedicated-host-disk}

- **HOST**: ID or name of the host.
- **DISK**: ID or name of the dedicated host disk.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host-disk-update
{: #dedicated-host-disk-update}

Update a dedicated host disk.

```
ibmcloud is dedicated-host-disk-update HOST DISK --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-dedicated-host-disk-update}

- **HOST**: ID or name of the host.
- **DISK**: ID or name of the dedicated host disk.
- **--name**: New name of the disk.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Bare metal servers
{: #bare-metal-servers}

### ibmcloud is bare-metal-server
{: #bare-metal-server-view}

View details of a bare metal server.

```
ibmcloud is bare-metal-server SERVER [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server}

- **SERVER**: ID or name of the server.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-console
{: #bare-metal-server-console}

Open an interactive console to the bare metal server. By default, this command opens an interactive serial console.

```
ibmcloud is bare-metal-server-console SERVER [--vnc] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-console}

- **SERVER**: ID or name of the server.
- **--vnc**: Get the WebSocket URI for the VNC console, it doesn't open the VNC console.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-create
{: #bare-metal-server-create}

Create a bare metal server.

```
ibmcloud is bare-metal-server-create --zone ZONE_NAME --profile PROFILE --image IMAGE --keys KEYS (((--pnic-subnet PRIMARY_NIC_SUBNET [--vpc VPC]) [--pnic-name PRIMARY_NIC_NAME] [--pnic-rip PNIC_RIP | (--pnic-rip-address PNIC_RIP_ADDRESS --pnic-rip-auto-delete true | false --pnic-rip-name PNIC_RIP_NAME)] [--pnic-sgs PNIC_SGS] [--pnic-allowed-vlans PNIC_ALLOWED_VLANS] [--pnic-ein true | false] [--pnic-ais false | true] [--network-interfaces NETWORK_INTERFACES_JSON | @NETWORK_INTERFACES_JSON_FILE]) | ([--pnac-name PRIMARY_NAC_NAME] [--pnac-allowed-vlans PNAC_ALLOWED_VLANS] [--pnac-vni PNAC_VNI | ((--pnac-vni-subnet PNAC_VNI_SUBNET [--vpc VPC]) --pnac-vni-ais false | true --pnac-vni-ein true | false --pnac-vni-auto-delete true | false --pnac-vni-ips VNI_RESERVED_IPS_JSON | @VNI_RESERVED_IPS_JSON_FILE --pnac-vni-name PNAC_VNI_NAME [--pnac-vni-rip PNAC_VNI_RIP | (--pnac-vni-rip-address PNAC_VNI_RIP_ADDRESS --pnac-vni-rip-auto-delete true | false --pnac-vni-rip-name PNAC_VNI_RIP_NAME)] --pnac-vni-sgs PNAC_VNI_SGS [--pnac-vni-psfm auto | enabled | disabled])] [--network-attachments NETWORK_ATTACHMENTS_JSON | @NETWORK_ATTACHMENTS_JSON_FILE])) [--name NAME] [--user-data DATA] [--enable-secure-boot false | true] [--tpm-mode tpm_2 | disabled] [--bandwidth BANDWIDTH] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--reservation-affinity-policy, --res-policy disabled | manual | automatic] [--reservation-affinity-pool, --res-pool RESERVATION_AFFINITY_POOL] [-i, --interactive] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-bare-metal-server-create}

- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f`
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image ibm-esxi-7-byol-amd64-1 --keys my-sshkey-1,my-sshkey-2 --pnic-subnet my-subnet`
Create a bare metal server with name support for image, keys and subnet
- `ibmcloud is bare-metal-server-create --name my-server-name2 --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-name eth0 --pnic-rip-address 46.9.49.11 --pnic-sgs c791f26f-4cf1-4bbf-be0e-72d7cb87133e,fefc8362-93c2-4f3d-90d4-82c56cce787e --pnic-allowed-vlans 1,2,3,4 --pnic-ein true --pnic-ais true`
Create a bare metal server with specified primary network interface configuration.
- `ibmcloud is bare-metal-server-create --name my-server-name3 --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --enable-secure-boot true --tpm-mode tpm_2`
Create a bare metal server that enables trusted platform module with the `tpm_2` mode.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --resource-group-name Finance --output JSON`
Create a bare metal server in the `Finance` resource group.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-allowed-vlans 100,200,300,400,700,710,1000,900-929,800-829`
Create a bare metal server with a PCI network interface. Allowed VLANs are comma-separated values that can be passed as separate values or as any range of numbers.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile mz2d-metal-2x32 --image sles15sp3-s390x-byol --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnac-name cli-pnac-1 --pnac-allowed-vlans -10 --pnac-vni 7322-1293a27a-7178-4e62-ba5b-272623c989aa --network-attachments [{"interface_type": "pci", "name":"cli-snac-1", "virtual_network_interface": {"allow_ip_spoorfing": true, "auto_delete": true, "enable_infrastructure_nat": true, "ips": [{"id": "7322-7594a7b8-dd7f-420c-ad09-a37646950edc"}, {"address": "10.240.128.15", "auto_delete": true, "name": "snac-sip-2"}]`
Create bare metal server with a network attachment and existing virtual network interface.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile mz2d-metal-2x32 --image sles15sp3-s390x-byol --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnac-name cli-pnac-1 --pnac-allowed-vlans -10 --pnac-vni 7322-1293a27a-7178-4e62-ba5b-272623c989aa --network-attachments [{"interface_type": "pci", "name":"cli-snac-1", "virtual_network_interface": {"allow_ip_spoorfing": true, "auto_delete": true, "enable_infrastructure_nat": true, "ips": [{"id": "7322-7594a7b8-dd7f-420c-ad09-a37646950edc"}, {"address": "10.240.128.15", "auto_delete": true, "name": "snac-sip-2"}]`
Create bare metal server with a network attachment and existing virtual network interface.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --reservation-affinity-policy manual --reservation-affinity-pool r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2`
Create bare metal server with reservation.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --reservation-affinity-policy manual --reservation-affinity-pool my-reservation`
Create bare metal server with reservation.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-rip 2302-74dd56cc-71c4-4461-95f0-4e5e3b57727d`
Create a bare metal server with a precreated reserved IP ID.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-rip 2302-74dd56cc-71c4-4461-95f0-4e5e3b57727d --bandwidth 10000`
Create a bare metal server with a precreated reserved IP ID and bandwidth.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-rip cli-rip-1`
Create a bare metal server with a precreated reserved IP by NAME.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-rip-address 10.240.128.38  --pnic-rip-auto-delete true --pnic-rip-name cli-rip1`
Create a bare metal server with a primary network interface with new reserved IP.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-rip 2302-74dd56cc-71c4-4461-95f0-4e5e3b57727d --network-interfaces '[{"name": "cli-snic", "allow_ip_spoofing": true, "enable_infrastructure_nat": true, "interface_type": "pci", "allowed_vlans": [1, 2, 3, 4], "subnet": {"id":"2302-531ad9fc-c86a-4504-b5cf-a46981fddb5f"}, "primary_ip":{"id": "2302-2b09dd0a-9cfb-4639-a2ac-cc6c154ab461"}}]`
Create a bare metal server with a secondary network interface with precreated reserved IP ID. Configurations of the two secondary interfaces are specified in JSON format. See help text for '--network-interfaces' option.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-rip cli-rip-1 --network-interfaces '[{"name": "cli-snic", "allow_ip_spoofing": true, "enable_infrastructure_nat": true, "interface_type": "pci", "allowed_vlans": [1, 2, 3, 4], "subnet": {"id":"2302-531ad9fc-c86a-4504-b5cf-a46981fddb5f"},"primary_ip":{"name": "cli-rip-byname"}}]`
Create a bare metal server with a secondary network interface with precreated reserved IP by Name. Configurations of the two secondary interfaces are specified in JSON format. See help text for '--network-interfaces' option.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-rip-address 10.240.128.38  --pnic-rip-auto-delete true --pnic-rip-name cli-rip1 --network-interfaces '[{"name": "cli-snic", "allow_ip_spoofing": true, "enable_infrastructure_nat": true, "interface_type": "pci", "allowed_vlans": [1, 2, 3, 4], "subnet": {"id":"2302-d368b797-2955-464b-aa42-588edd4c389f"}, "primary_ip":{"address": "10.240.128.41"}, "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}]'`
Create a bare metal server with a secondary network interface with new reserved IP. Configurations of the two secondary interfaces are specified in JSON format. See help text for '--network-interfaces' option.

#### Command options
{: #command-options-bare-metal-server-create}

- **--name**: Name of the server.
- **--zone**: Name of the zone.
- **--profile**: Name of the bare metal server profile.
- **--image**: ID or name of the image.
- **--keys**: Comma-separated IDs or names of SSH keys. SSH keys can be either RSA or Ed25519. Ed25519 can be used only if the operating system supports this key type. Ed25519 can't be used with Windows or VMware images.
- **--user-data**: data|@data-file. User data to transfer to the bare metal server.
- **--pnic-name**: Name of the primary network interface.
- **--pnic-subnet**: Subnet ID or name for the primary network interface.
- **--vpc**: ID or name of the VPC. This ID or name is required only to specify the unique subnet by name inside this VPC.
- **--pnic-rip**: ID or name of the existing reserved IP that is bound to the primary network interface.
- **--pnic-rip-address**: The IP address of the primary network interface to reserve, which must not already be reserved on the subnet.
- **--pnic-rip-auto-delete**: If set to **true**, this reserved IP of the primary network interface automatically deletes when the target is deleted. One of: **true**, **false**. (default: **true**).
- **--pnic-rip-name**: The user-defined name for this reserved IP of the primary network interface. Names must be unique within the subnet that the reserved IP resides in. Names beginning with **ibm-** are reserved for provider-owned resources.
- **--pnic-sgs**: Comma-separated security group IDs for primary network interface.
- **--pnic-allowed-vlans**: Comma-separated VLAN IDs. Indicates which VLAN IDs (for VLAN interfaces only) can use the primary network interface. It can be passed as separate values or as any range of numbers.
- **--pnic-ein**: Enable Infrastructure NAT (EIN). If **true**, the VPC infrastructure performs any needed NAT operations. If **false**, the packet is passed unmodified to or from the network interface, allowing the virtual machine that is associated with the floating IP to perform any needed NAT operations. One of: **true**, **false**. (default: **true**).
- **--pnic-ais**: Allow IP Spoofing (AIS). If **true**, source IP spoofing is allowed on packets that are using this network interface. If **false**, source IP spoofing is prevented on this interface. One of: **false**, **true**. (default: **false**).
- **--network-interfaces**: NETWORK_INTERFACES_JSON|@NETWORK_INTERFACES_JSON_FILE. Network interface configuration in JSON or JSON file. For the data schema, check the **network_interfaces** property in the [API documentation](/apidocs/vpc#create-bare-metal-server). One of: **NETWORK_INTERFACES_JSON**, **@NETWORK_INTERFACES_JSON_FILE**.
- **--pnac-name**: Name of the primary network attachment.
- **--pnac-allowed-vlans**: Comma-separated VLAN IDs. Indicates which VLAN IDs (for VLAN interfaces only) can use the primary network attachment. It can be passed as separate values or as any range of numbers.
- **--pnac-vni**: ID or name of the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-subnet**: The associated subnet.
- **--pnac-vni-ais**: Allow IP Spoofing (AIS). Indicates whether source IP spoofing is allowed on this virtual network interface that is associated with primary network attachment. One of: **false**, **true**. (default: **false**).
- **--pnac-vni-ein**: Enable infrastructure NAT (EIN). If **true**, the VPC infrastructure performs any needed NAT operations on the VNI. To attach a VNI to an instance, the value needs to be true. Floating_ips must not have more than one floating IP. If **false**, the packet is passed unmodified to or from the VNI, which allows it to perform any needed NAT operations. Allow_ip_spoofing must be false. Can be attached only to a target with a resource_type of bare_metal_server_network_attachment. One of: **true**, **false**. (default: **true**).
- **--pnac-vni-auto-delete**: Indicates whether this virtual network interface that is associated with primary network attachment automatically deletes when target is deleted. One of: **true**, **false**. (default: **true**).
- **--pnac-vni-ips**: VNI_RESERVED_IPS_JSON | @VNI_RESERVED_IPS_JSON_FILE, Secondary reserved IP addresses is in JSON or JSON file, to bind to the virtual network interface. For the data schema, see the IPS property in the [API documentation](/apidocs/vpc/latest#create-virtual-network-interface). One of: **VNI_RESERVED_IPS_JSON**, **@VNI_RESERVED_IPS_JSON_FILE**.
- **--pnac-vni-name**: The name for this virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-rip**: ID or name of the reserved IP to bind to the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-rip-address**: The IP address of the reserved IP to bind to the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-rip-auto-delete**: Indicates whether this reserved IP automatically deletes when either target is deleted, or if the reserved IP is unbound. One of: **true**, **false**. (default: **true**).
- **--pnac-vni-rip-name**: The name for this reserved IP to bind to the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-sgs**: IDs or names of the security groups to use for the virtual network interface that are associated with the primary network attachment.
- **--pnac-vni-psfm**: The protocol state filtering mode to use for this virtual network interface. If auto, protocol state packet filtering is enabled or disabled based on the virtual network interface's `target` resource type. One of: **auto**, **enabled**, **disabled**. (default: **auto**).
- **--network-attachments**: NETWORK_ATTACHMENTS_JSON|@NETWORK_ATTACHMENTS_JSON_FILE. Network attachment configuration is in JSON or JSON file. For the data schema, see the **network_attachments** property in the [API documentation](/apidocs/vpc#create-bare-metal-server). One of: **NETWORK_ATTACHMENTS_JSON**, **@NETWORK_ATTACHMENTS_JSON_FILE**.
- **--enable-secure-boot**: Indicates whether secure boot is enabled. If enabled, the image must support secure boot or the server fails to boot. One of: **false**, **true**. (default: **false**).
- **--tpm-mode**: The mode for the trusted platform module (TPM). One of: **tpm_2**, **disabled**.
- **--bandwidth**: The total bandwidth (in megabits per second) that is shared across the bare metal server's network interfaces. If unspecified, the default value from the profile is used. You can use command **ibmcloud is bare-metal-server-profile** to get valid bandwidth values.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--reservation-affinity-policy, --res-policy**: The reservation affinity policy to use for this bare metal server. The policy defaults to manual if the pool is not empty. Otherwise the policy defaults to automatic. One of: **disabled**, **manual**, **automatic**.
- **--reservation-affinity-pool, --res-pool**: ID, name, or CRN of the reservation that is available to use by this bare metal server.
- **--interactive, -i**:
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-delete
{: #bare-metal-server-delete}

Delete one or more bare metal servers.

```
ibmcloud is bare-metal-server-delete (SERVER1 SERVER2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-delete}

- **SERVER1**: ID or name of the server.
- **SERVER2**: ID or name of the server.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-disk
{: #bare-metal-server-disk-view}

View details of a bare metal server disk.

```
ibmcloud is bare-metal-server-disk SERVER SERVER_DISK [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-disk}

- **SERVER**: ID or name of the server.
- **SERVER_DISK**: ID or name of the server disk.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-disk-update
{: #bare-metal-server-disk-update}

Update a bare metal server disk.

```
ibmcloud is bare-metal-server-disk-update SERVER SERVER_DISK --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-disk-update}

- **SERVER**: ID or name of the server.
- **SERVER_DISK**: ID or name of the server disk.
- **--name**: New name of local disk.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-disks
{: #bare-metal-server-disks-list}

List all disks of a bare metal server.

```
ibmcloud is bare-metal-server-disks SERVER [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-disks}

- **SERVER**: ID or name of the server.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-initialization-values
{: #bare-metal-server-initialization-values}

Retrieve configuration variables that are used to initialize the bare metal server.

```
ibmcloud is bare-metal-server-initialization-values SERVER [--private-key (KEY | @KEY_FILE) [--private-key-passphrase PRIVATE_KEY_PASSPHRASE]] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-initialization-values}

- **SERVER**: ID or name of the server.
- **--private-key**: **key**|**@key-file**. The private key in PEM format to decrypt password.
- **--private-key-passphrase**: The passphrase for the encrypted private key.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface
{: #bare-metal-server-network-interface-view}

View details of a network interface of a bare metal server.

```
ibmcloud is bare-metal-server-network-interface SERVER NIC [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-network-interface}

- **SERVER**: ID or name of the server.
- **NIC**: ID or name of the network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface-create
{: #bare-metal-server-network-interface-create}

Create a network interface for a bare metal server.

```
ibmcloud is bare-metal-server-network-interface-create SERVER --subnet SUBNET (--interface-type pci | vlan) [--name NAME] [[--rip RIP | (--address ADDRESS --auto-delete true | false --ip-name IP_NAME)]] [--security-groups SECURITY_GROUPS] [--vpc VPC] [--allowed-vlans ALLOWED_VLANS | --vlan VLAN --allow-interface-to-float false | true] [--allow-ip-spoofing false | true] [--enable-infrastructure-nat true | false] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-bare-metal-server-network-interface-create}

- `ibmcloud is bare-metal-server-network-interface-create 7d317c32-71f8-4060-9bdc-6c971b0317d4 --subnet dcaec790-f0b0-48e6-b4cb-03dd82b745c0`
Create a PCI network interface.
- `ibmcloud is bare-metal-server-network-interface-create my-server --subnet my-subnet`
Create a PCI network interface with name support.
- `ibmcloud is bare-metal-server-network-interface-create my-server --subnet my-subnet --vpc my-vpc`
Create a PCI network interface with name support under a VPC.
- `ibmcloud is bare-metal-server-network-interface-create 7d317c32-71f8-4060-9bdc-6c971b0317d4 --subnet dcaec790-f0b0-48e6-b4cb-03dd82b745c0 --interface-type pci --name eth1 --address 10.0.0.12 --security-groups 43846d71-0f04-473f-9de5-5a2d33200a4b,27c8ca96-17f3-4943-898d-ad1a1f5aec26 --allowed-vlans 1,2,3,4 -allow-ip-spoofing true --enable-infrastructure-nat true`
Create a PCI network interface with specified configuration.
- `ibmcloud is bare-metal-server-network-interface-create 7d317c32-71f8-4060-9bdc-6c971b0317d4 --subnet dcaec790-f0b0-48e6-b4cb-03dd82b745c0 --interface-type pci --name eth1 --address 10.0.0.12 --security-groups 43846d71-0f04-473f-9de5-5a2d33200a4b,27c8ca96-17f3-4943-898d-ad1a1f5aec26 --vpc my-vpc --allowed-vlans 1,2,3,4 -allow-ip-spoofing true --enable-infrastructure-nat true`
Create a PCI network interface with specified configuration under a VPC.
- `ibmcloud is bare-metal-server-network-interface-create my-server --subnet my-subnet --interface-type pci --name eth1 --address 10.0.0.12 --security-groups my-sg-1,my-sg-2 --allowed-vlans 1,2,3,4 -allow-ip-spoofing true --enable-infrastructure-nat true`
Create a PCI network interface with specified configuration with name support.
- `ibmcloud is bare-metal-server-network-interface-create 7d317c32-71f8-4060-9bdc-6c971b0317d4 --subnet dcaec790-f0b0-48e6-b4cb-03dd82b745c0 --interface-type vlan --name eth2 --address 10.0.0.12 --security-groups 43846d71-0f04-473f-9de5-5a2d33200a4b,27c8ca96-17f3-4943-898d-ad1a1f5aec26 --vlan 1 -allow-interface-to-float true -allow-ip-spoofing true --enable-infrastructure-nat true`
Create a VLAN network interface with specified configuration.
- `ibmcloud is bare-metal-server-network-interface-create 7d317c32-71f8-4060-9bdc-6c971b0317d4 --subnet dcaec790-f0b0-48e6-b4cb-03dd82b745c0 --output JSON`
Create a PCI network interface and specify JSON as the output format.
- `ibmcloud is bm-nicc bm-cli-1 --subnet cli-subnet-1 --name bm-cli-nic-secondary --allowed-vlans 210,510,500,3001-1001`
Create a PCI network interface. Allowed VLANs are comma-separated values that can be passed as separate values or as any range of numbers.
- `ibmcloud is bm-nicc cli-bm --subnet alex-subnet --name cli-snic-3 --rip 2302-aef75588-7b87-46b7-bca4-0d6893d2593e`
Create a bare metal NIC with precreated reserved IP.
- `ibmcloud is bm-nicc cli-bm --subnet alex-subnet --name cli-snic-3 --rip cli-rip-byname3`
Create a bare metal NIC with precreated reserved IP by Name.
- `ibmcloud is bm-nicc cli-bm --subnet 2302-531ad9fc-c86a-4504-b5cf-a46981fddb5f --name cli-snic --address 10.240.128.51  --auto-delete true --ip-name cli-snicip`
Create a bare metal NIC with new reserved IP.

#### Command options
{: #command-options-bare-metal-server-network-interface-create}

- **SERVER**: ID or name of the server.
- **--subnet**: Subnet ID or name for the network interface.
- **--name**: Name of the network interface.
- **--interface-type**: Type of the network interface. One of: **pci**, **vlan**. (default: **pci**).
- **--rip**: ID or name of the existing reserved IP.
- **--address**: The IP address to reserve, which must not already be reserved on the subnet.
- **--auto-delete**: If set to **true**, this reserved IP automatically deletes when the target is deleted. One of: **true**, **false**. (default: **true**).
- **--ip-name**: The user-defined name for this reserved IP. Names must be unique within the subnet that the reserved IP resides in. Names beginning with **ibm-** are reserved for provider-owned resources.
- **--security-groups**: Comma-separated security group IDs or names for the network interface.
- **--vpc**: ID or name of the VPC. This is only required to specify the unique subnet and unique security-groups by name inside this VPC.
- **--allowed-vlans**: Comma-separated VLAN IDs. Indicates which VLAN IDs (for VLAN interfaces only) can use this PCI interface. It can be passed as separate values or as any range of numbers.
- **--vlan**: Indicates the 802.1Q VLAN ID tag that must be used for all traffic on this VLAN interface.
- **--allow-interface-to-float**: Indicates if the interface can float to any other server within the same **resource_group**. The interface floats automatically if the network detects a GARP or RARP on another bare metal server in the resource group. Applies only to VLAN interfaces. One of: **false**, **true**. (default: **false**).
- **--allow-ip-spoofing**: Allow IP Spoofing (AIS). If **true**, source IP spoofing is allowed on packets that are using this network interface. If **false**, source IP spoofing is prevented on this interface. One of: **false**, **true**. (default: **false**).
- **--enable-infrastructure-nat**: Enable Infrastructure NAT (EIN). If **true**, the VPC infrastructure performs any needed NAT operations. If **false**, the packet is passed unmodified to or from the network interface, allowing the virtual machine that is associated with the floating IP to perform any needed NAT operations. One of: **true**, **false**. (default: **true**).
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface-delete
{: #bare-metal-server-network-interface-delete}

Remove one or more network interfaces from a bare metal server.

```
ibmcloud is bare-metal-server-network-interface-delete SERVER (NIC1 NIC2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-network-interface-delete}

- **SERVER**: ID or name of the server.
- **NIC1**: ID or name of the network interface.
- **NIC2**: ID or name of the network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface-floating-ip
{: #bare-metal-server-network-interface-floating-ip-view}

View details of a floating IP that is associated with a network interface.

```
ibmcloud is bare-metal-server-network-interface-floating-ip SERVER NIC FLOATING_IP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-network-interface-floating-ip}

- **SERVER**: ID or name of the server.
- **NIC**: ID or name of the network interface.
- **FLOATING_IP**: The ID or name of the floating IP.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface-floating-ip-add
{: #bare-metal-server-network-interface-floating-ip-add}

Associate a floating IP with a network interface.

```
ibmcloud is bare-metal-server-network-interface-floating-ip-add SERVER NIC FLOATING_IP [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-bare-metal-server-network-interface-floating-ip-add}

- `ibmcloud is bare-metal-server-network-interface-floating-ip-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is bare-metal-server-network-interface-floating-ip-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --output JSON`
Associate a floating IP with a network interface on a bare metal server and specify JSON as the output format.

#### Command options
{: #command-options-bare-metal-server-network-interface-floating-ip-add}

- **SERVER**: ID or name of the server.
- **NIC**: ID or name of the network interface.
- **FLOATING_IP**: The ID or name of the floating IP.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface-floating-ip-remove
{: #bare-metal-server-network-interface-floating-ip-remove}

Disassociate a floating IP from a network interface.

```
ibmcloud is bare-metal-server-network-interface-floating-ip-remove SERVER NIC FLOATING_IP [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-network-interface-floating-ip-remove}

- **SERVER**: ID or name of the server.
- **NIC**: ID or name of the network interface.
- **FLOATING_IP**: The ID or name of the floating IP.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface-floating-ips
{: #bare-metal-server-network-interface-floating-ips-list}

List all floating IPs that are associated with a network interface.

```
ibmcloud is bare-metal-server-network-interface-floating-ips SERVER NIC [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-network-interface-floating-ips}

- **SERVER**: ID or name of the server.
- **NIC**: ID or name of the network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface-update
{: #bare-metal-server-network-interface-update}

Update a network interface of a bare metal server.

```
ibmcloud is bare-metal-server-network-interface-update SERVER NIC --name NEW_NAME [--allow-ip-spoofing false | true] [--enable-infrastructure-nat true | false] [--allowed-vlans ALLOWED_VLANS] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-bare-metal-server-network-interface-update}

- `ic is bm-nicu 7d317c32-71f8-4060-9bdc-6c971b0317d4 784e2e4c-0540-4e1a-aba7-a51f9b35ba52 --name eth0 --allow-ip-spoofing true --enable-infrastructure-nat true -allowed-vlans 1,3,5`
- `ic is bm-nicu 7d317c32-71f8-4060-9bdc-6c971b0317d4 784e2e4c-0540-4e1a-aba7-a51f9b35ba52 --name ethvlan1 --allow-ip-spoofing true --enable-infrastructure-nat true --output JSON`
- `ic is bm-nicu my-bm-server my-bm-nic --name eth0 --allow-ip-spoofing true --enable-infrastructure-nat true -allowed-vlans 1,3,5`
- `ic is bm-nicu my-bm-server eth0 --name ethvlan1 --allow-ip-spoofing true --enable-infrastructure-nat true --output JSON`
- `ibmcloud is bm-nicu bm-cli-1 bm-cli-nic-secondary  --allowed-vlans 210,500-600,3001-1001`

#### Command options
{: #command-options-bare-metal-server-network-interface-update}

- **SERVER**: ID or name of the server.
- **NIC**: ID or name of the network interface.
- **--name**: New name of the network interface.
- **--allow-ip-spoofing**: Allow IP Spoofing (AIS). If **true**, source IP spoofing is allowed on packets that are using this network interface. If **false**, source IP spoofing is prevented on this interface. One of: **false**, **true**. (default: **false**).
- **--enable-infrastructure-nat**: Enable Infrastructure NAT (EIN). If **true**, the VPC infrastructure performs any needed NAT operations. If **false**, the packet is passed unmodified to or from the network interface, allowing the virtual machine that is associated with the floating IP to perform any needed NAT operations. One of: **true**, **false**. (default: **true**).
- **--allowed-vlans**: Comma-separated VLAN IDs. Indicates which VLAN IDs (for VLAN interfaces only) can use this PCI interface. It can be passed as separate values or as any range of numbers.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interfaces
{: #bare-metal-server-network-interfaces-list}

List all network interfaces of a bare metal server.

```
ibmcloud is bare-metal-server-network-interfaces SERVER [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-network-interfaces}

- **SERVER**: ID or name of the server.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-profile
{: #bare-metal-server-profile-view}

View details of a bare metal server profile.

```
ibmcloud is bare-metal-server-profile PROFILE_NAME [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-profile}

- **PROFILE_NAME**: Name of the profile.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-profiles
{: #bare-metal-server-profiles-list}

List all bare metal server profiles in the region.

```
ibmcloud is bare-metal-server-profiles [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-profiles}

- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-restart
{: #bare-metal-server-restart}

Restart a bare metal server.

```
ibmcloud is bare-metal-server-restart SERVER [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-restart}

- **SERVER**: ID or name of the server.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-start
{: #bare-metal-server-start}

Start a bare metal server.

```
ibmcloud is bare-metal-server-start SERVER [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-start}

- **SERVER**: ID or name of the server.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-stop
{: #bare-metal-server-stop}

Stop a bare metal server.

```
ibmcloud is bare-metal-server-stop SERVER [--type soft | hard] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-stop}

- **SERVER**: ID or name of the server.
- **--type**: Indicates the type of the stop operation. **soft**: Signal the running operating system to quiesce and shut down cleanly. **hard**: Immediately stop the server. One of: **soft**, **hard**. (default: **soft**).
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-update
{: #bare-metal-server-update}

Update a bare metal server.

```
ibmcloud is bare-metal-server-update SERVER [--name NEW_NAME] [--enable-secure-boot false | true] [--tpm-mode tpm_2 | disabled] [--bandwidth BANDWIDTH] [--reservation-affinity-policy, --res-policy disabled | manual | automatic] [--reservation-affinity-pool, --res-pool RESERVATION_AFFINITY_POOL] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-bare-metal-server-update}

- `ibmcloud is bare-metal-server-update 7d317c32-71f8-4060-9bdc-6c971b0317d4 --name my-server --enable-secure-boot true --tpm-mode tpm_2`
- `ibmcloud is bare-metal-server-update 7d317c32-71f8-4060-9bdc-6c971b0317d4 --name my-server --output JSON`
- `ibmcloud is bare-metal-server-update 7d317c32-71f8-4060-9bdc-6c971b0317d4 --bandwidth 25000 --output JSON`
- `ibmcloud is bare-metal-server-update 7d317c32-71f8-4060-9bdc-6c971b0317d4 --reservation-affinity-policy manual --reservation-affinity-pool r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2`
- `ibmcloud is bare-metal-server-update 7d317c32-71f8-4060-9bdc-6c971b0317d4 --reservation-affinity-policy disabled`
- `ibmcloud is bare-metal-server-update my-baremetal-1 --name my-bm-server --output JSON`

#### Command options
{: #command-options-bare-metal-server-update}

- **SERVER**: ID or name of the server.
- **--name**: New name of the bare metal server.
- **--enable-secure-boot**: Indicates whether secure boot is enabled. If enabled, the image must support secure boot or the server fails to boot. The status of the bare metal server must be stopped before you change this configuration. One of: **false**, **true**.
- **--tpm-mode**: The mode for the trusted platform module (TPM). One of: **tpm_2**, **disabled**.
- **--bandwidth**: The total bandwidth (in megabits per second) that is shared across the bare metal server's network interfaces. If unspecified, the default value from the profile is used. You can use command **ibmcloud is bare-metal-server-profile** to get valid bandwidth values.
- **--reservation-affinity-policy, --res-policy**: The reservation affinity policy to use for this bare metal server. The policy defaults to manual if the pool is not empty. Otherwise the policy defaults to automatic. One of: **disabled**, **manual**, **automatic**.
- **--reservation-affinity-pool, --res-pool**: ID, name, or CRN of the reservation that is available to use by this bare metal server.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-servers
{: #bare-metal-servers-list}

List all bare metal servers.

```
ibmcloud is bare-metal-servers [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--vpc VPC] [--reservation RESERVATION] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-servers}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--vpc**: ID, name, or CRN of the VPC.
- **--reservation**: ID or name of the reservation.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-firmware-update
{: #bare-metal-server-firmware-update}

Update a bare metal server to the most recent firmware.

```
ibmcloud is bare-metal-server-firmware-update SERVER [--auto-start true | false] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-firmware-update}

- **SERVER**: ID or name of the server.
- **--auto-start**: Indicates whether to automatically start the bare metal server after the firmware update is successful. One of: **true**, **false**. (default: **true**).
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface-reserved-ips
{: #bare-metal-server-network-interface-reserved-ips-list}

Lists all reserved IPs bound to a network interface of a bare metal server.

```
ibmcloud is bare-metal-server-network-interface-reserved-ips SERVER NIC [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-network-interface-reserved-ips}

- **SERVER**: ID or name of the server.
- **NIC**: ID or name of the network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface-reserved-ip
{: #bare-metal-server-network-interface-reserved-ip-view}

Retrieves the specified reserved IP address if it is bound to the network interface of a bare metal server.

```
ibmcloud is bare-metal-server-network-interface-reserved-ip SERVER NIC RESERVED_IP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-network-interface-reserved-ip}

- **SERVER**: ID or name of the server.
- **NIC**: ID or name of the network interface.
- **RESERVED_IP**: The ID or name of the reserved IP.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-attachments
{: #bare-metal-server-network-attachments-list}

List all network attachments of a bare metal server.

```
ibmcloud is bare-metal-server-network-attachments SERVER [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-network-attachments}

- **SERVER**: ID or name of the server.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-attachment
{: #bare-metal-server-network-attachment-view}

View details of a network attachment of a bare metal server.

```
ibmcloud is bare-metal-server-network-attachment SERVER NAC [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-network-attachment}

- **SERVER**: ID or name of the server.
- **NAC**: ID or name of the network attachment.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-attachment-create
{: #bare-metal-server-network-attachment-create}

Create a network attachment for a bare metal server.

```
ibmcloud is bare-metal-server-network-attachment-create SERVER (--interface-type pci | vlan) [--vni VNI | ((--vni-subnet VNI_SUBNET [--vpc VPC]) --vni-ais false | true --vni-ein true | false --vni-auto-delete true | false --vni-ips VNI_RESERVED_IPS_JSON | @VNI_RESERVED_IPS_JSON_FILE --vni-name VNI_NAME [--vni-rip VNI_RIP | (--vni-rip-address VNI_RIP_ADDRESS --vni-rip-auto-delete VNI_RIP_AUTO_DELETE --vni-rip-name VNI_RIP_NAME)] [--vni-psfm auto | enabled | disabled] --vni-sgs VNI_SGS)] [--name NAC_NAME] [--allowed-vlans ALLOWED_VLANS] [--allow-to-float ALLOW_TO_FLOAT] [--vlan VLAN] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-bare-metal-server-network-attachment-create}

- `ibmcloud is bare-metal-server-network-attachment-create my-bare-metal-server-nw-att --interface-type pci --vni bm-cli-vni-2 --name bm-nac-3 --allowed-vlans 10-50`
- `ibmcloud is bare-metal-server-network-attachment-create 2302-f097c96c-c092-4929-b093-b9d4a481c20d --interface-type pci --vni-subnet 2302-a31b7225-c513-481b-be6b-9df9396f69ae  --vni-ais false --vni-ein false --vni-auto-delete true --vni-ips  '[{"id": "2302-8e9060c3-90d8-4c73-b07c-215f60c87a2e"},{"address": "10.240.133.22"}]' --vni-name bm-vni-2 --vni-rip-address 10.240.133.22 --vni-rip-auto-delete true --vni-rip-name bm-rip-11 --vni-sgs r134-61c9d87e-0a7d-4a5f-9c8a-a7475ebf182e,r134-244e457e-59ef-43de-9317-dba6de040ced  --name bm-nac-10  --allowed-vlans 10-50`
- `ibmcloud is bare-metal-server-network-attachment-create my-bare-metal-server-nw-att --interface-type vlan   --vni-subnet subnet-us-3 --vpc travis-long-run-vpc --vni-ais true --vni-ein true  --vni-auto-delete true --vni-ips '[{"id": "2302-4bc26be6-2d4a-4090-a645-f50c22091902"}]' --vni-name bm-vni-1 --vni-rip rip-cli-12 --vni-sgs abundantly-gangly-aspire-discuss,travis-long-run-sg1 --name bm-nac-30  --allow-to-float true --vlan 10`
- `ibmcloud is bare-metal-server-network-attachment-create cli-bm-1 --interface-type vlan   --vni-subnet subnet-us-3 --vpc cli-vpc --vni-ais true --vni-ein true --vni-psfm disabled --vni-auto-delete true --vni-ips '[{"id": "2302-4bc26be6-2d4a-4090-a645-f50c22091902"}]' --vni-name bm-vni-1 --vni-rip rip-cli-12 --vni-sgs abundantly-gangly-aspire-discuss,travis-long-run-sg1 --name bm-nac-30  --allow-to-float true --vlan 10`

#### Command options
{: #command-options-bare-metal-server-network-attachment-create}

- **SERVER**: ID or name of the server.
- **--name**: The name for this bare metal server network attachment.
- **--interface-type**: The network attachment interface type. One of: **pci**, **vlan**. (default: **pci**).
- **--allowed-vlans**: Comma-separated VLAN IDs. Indicates what VLAN IDs (for VLAN type only) can use this physical (PCI type) attachment. It can be passed as separate values or as any range of numbers.
- **--allow-to-float**: Indicates if the bare metal server network attachment can automatically float to any other server that is within the same resource_group.
- **--vlan**: Indicates the 802.1Q VLAN ID tag that must be used for all traffic on this attachment.
- **--vni**: ID or name of the virtual network interface that is for this bare metal server network attachment.
- **--vni-subnet**: The associated subnet.
- **--vpc**: ID or name of the VPC. This ID or name is required only to specify the unique subnet by name inside this VPC.
- **--vni-ais**: Allow IP Spoofing (AIS). Indicates whether source IP spoofing is allowed on this virtual network interface. One of: **false**, **true**. (default: **false**).
- **--vni-ein**: Enable Infrastructure NAT (EIN). If **true**, the VPC infrastructure performs any needed NAT operations. If **false**, the packet is passed unmodified to or from the virtual network interface, which allows the virtual machine that is associated with the floating IP to perform any needed NAT operations. One of: **true**, **false**. (default: **true**).
- **--vni-auto-delete**: Indicates whether this virtual network interface automatically deletes when the target is deleted. One of: **true**, **false**. (default: **true**).
- **--vni-ips**: ips VNI_RESERVED_IPS_JSON | @VNI_RESERVED_IPS_JSON_FILE, Secondary reserved IP addresses in JSON or JSON file, to bind to the virtual network interface. For the data schema, check the ips property in the [API documentation](/apidocs/vpc/latest#create-virtual-network-interface). One of: **VNI_RESERVED_IPS_JSON**, **@VNI_RESERVED_IPS_JSON_FILE**.
- **--vni-name**: The name for this virtual network interface.
- **--vni-rip**: ID or name of the reserved IP to bind to the virtual network interface. Required if subnet is not specified. The reserved IP must be unbound.
- **--vni-rip-address**: The IP address of the reserved IP to bind to the virtual network interface. Requires subnet to be specified.
- **--vni-rip-auto-delete**: Indicates whether this reserved IP automatically deletes when either target is deleted, or if the reserved IP is unbound.
- **--vni-rip-name**: The name for this reserved IP to bind to the virtual network interface. The name must not be used by another reserved IP in the subnet. Names that start with ibm- are reserved for provider-owned resources, and are not allowed.
- **--vni-psfm**: The protocol state filtering mode to use for this virtual network interface. If auto, protocol state packet filtering is enabled or disabled based on the virtual network interface's `target` resource type. One of: **auto**, **enabled**, **disabled**. (default: **auto**).
- **--vni-sgs**: IDs or Names of the security groups to use for this virtual network interface. If unspecified, the default security group of the VPC for the subnet is used.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-attachment-update
{: #bare-metal-server-network-attachment-update}

Update a network attachment of a bare metal server.

```
ibmcloud is bare-metal-server-network-attachment-update SERVER NAC --name NEW_NAME [--allowed-vlans ALLOWED_VLANS] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-bare-metal-server-network-attachment-update}

- `ibmcloud is bm-nacu my-bare-metal-server-nw-att cli-pnac-1-primary --name nac-2`
- `ibmcloud is bm-nacu 2302-f097c96c-c092-4929-b093-b9d4a481c20d 2302-9688e589-ec0d-4611-9984-4bf88082414b --name nac-1 --allowed-vlans 10,20-50`

#### Command options
{: #command-options-bare-metal-server-network-attachment-update}

- **SERVER**: ID or name of the server.
- **NAC**: ID or name of the network attachment.
- **--name**: New name of the network attachment.
- **--allowed-vlans**: Comma-separated VLAN IDs. Indicates what VLAN IDs (for VLAN type only) can use this physical (PCI type) attachment. It can be passed as separate values or as any range of numbers.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-attachment-delete
{: #bare-metal-server-network-attachment-delete}

Remove one or more network attachments from a bare metal server.

```
ibmcloud is bare-metal-server-network-attachment-delete SERVER (NAC1 NAC2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-network-attachment-delete}

- **SERVER**: ID or name of the server.
- **NAC1**: ID or name of the network attachment.
- **NAC2**: ID or name of the network attachment.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-initialization-replace
{: #bare-metal-server-initialization-replace-view}

Reinitializes a bare metal server with the specified image and SSH keys.

```
ibmcloud is bare-metal-server-initialization-replace SERVER --image IMAGE --keys KEYS [--user-data DATA] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-bare-metal-server-initialization-replace}

- `ibmcloud is bare-metal-server-initialization-replace server-name --image r006-ed3f775f-ad7e-4e37-ae62-7199b4988b00 --keys r006-02a07b78-6e5f-40a2-86a2-99e01916128c,r006-29e19fb1-e2b9-49d0-ab6e-9702e99f5021 --user-data @/tmp/userdata.sh`
Reinitializes a bare metal server with the specified image and SSH keys. The server must be in stopped state for it to reinitialize.

#### Command options
{: #command-options-bare-metal-server-initialization-replace}

- **SERVER**: ID or name of the server.
- **--image**: ID or name of the image.
- **--keys**: Comma-separated IDs or names of SSH keys. SSH keys can be either RSA or Ed25519. Ed25519 can be used only if the operating system supports this key type. Ed25519 can't be used with Windows or VMware images.
- **--user-data**: data|@data-file. User data to transfer to the bare metal server.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Cluster network
{: #cluster-network-clis}

The following section gives details about the CLI commands that are available for working with cluster network.

### ibmcloud is cluster-network-profiles
{: #cluster-network-profiles-list}

List all the cluster network profiles in a region.

```
ibmcloud is cluster-network-profiles [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-cluster-network-profiles}

- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-profile
{: #cluster-network-profile-view}

View details of a cluster network profile.

```
ibmcloud is cluster-network-profile PROFILE_NAME [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-cluster-network-profile}

- **PROFILE_NAME**: Name of the cluster network profile.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-networks
{: #cluster-networks-list}

List all cluster networks.

```
ibmcloud is cluster-networks [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-cluster-networks}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network
{: #cluster-network-view}

View details of a cluster network.

```
ibmcloud is cluster-network CLUSTER_NETWORK [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-cluster-network}

- **CLUSTER_NETWORK**: ID or name for the cluster network.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-create
{: #cluster-network-create}

Create a cluster network.

```
ibmcloud is cluster-network-create --vpc VPC --zone ZONE --profile PROFILE [--name NAME] [--subnet-prefixes-cidr SUBNET_PREFIXES_CIDR] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-cluster-network-create}

- `ibmcloud is cluster-network-create --vpc my-vpc --zone us-south-1 --profile profile-name`
- `ibmcloud is cluster-network-create --vpc my-vpc --zone us-south-1 --profile profile-name --name my-cl-net`
- `ibmcloud is cluster-network-create --vpc my-vpc --zone us-south-1 --profile profile-name --name my-cl-net --subnet-prefixes-cidr 10.0.0.24/24`
- `ibmcloud is cluster-network-create --vpc my-vpc --zone us-south-1 --profile profile-name`
- `ibmcloud is cluster-network-create --vpc my-vpc --zone us-south-1 --profile profile-name --name my-cl-net`
- `ibmcloud is cluster-network-create --vpc my-vpc --zone us-south-1 --profile profile-name --name my-cl-net --subnet-prefixes-cidr 10.0.0.24/24 --output JSON`

#### Command options
{: #command-options-cluster-network-create}

- **--vpc**: The ID or name of the VPC.
- **--zone**: The zone that this cluster network resides in. The zone must be listed as supported in the specified cluster network profile.
- **--profile**: Name of the profile to use for this cluster network.
- **--name**: Name for the cluster network.
- **--subnet-prefixes-cidr**: The IPv4 range of the cluster network's subnet prefix, expressed in CIDR format.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-update
{: #cluster-network-update}

Update a cluster network.

```
ibmcloud is cluster-network-update CLUSTER_NETWORK [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-cluster-network-update}

- `ibmcloud is cluster-network-update my-cl-network --name my-updated-cl-net`
- `ibmcloud is cluster-network-update r006-345545d8-798c-4dbc-112g-5c34a1e75e45 --name my-updated-cl-net`

#### Command options
{: #command-options-cluster-network-update}

- **CLUSTER_NETWORK**: ID or name for the cluster network.
- **--name**: New name of the cluster network.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-delete
{: #cluster-network-delete}

Delete one or more cluster networks.

```
ibmcloud is cluster-network-delete (CLUSTER_NETWORK1 CLUSTER_NETWORK2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-cluster-network-delete}

- **CLUSTER_NETWORK1**: ID or name for the cluster network.
- **CLUSTER_NETWORK2**: ID or name for the cluster network.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-interfaces
{: #cluster-network-interfaces-list}

List all cluster network interfaces.

```
ibmcloud is cluster-network-interfaces CLUSTER_NETWORK [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-cluster-network-interfaces}

- **CLUSTER_NETWORK**: ID or name for the cluster network.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-interface
{: #cluster-network-interface-view}

View details of a cluster network interface.

```
ibmcloud is cluster-network-interface CLUSTER_NETWORK CLUSTER_NETWORK_INTERFACE [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-cluster-network-interface}

- **CLUSTER_NETWORK**: ID or name for the cluster network.
- **CLUSTER_NETWORK_INTERFACE**: ID or name for the cluster network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-interface-create
{: #cluster-network-interface-create}

Create a cluster network interface.

```
ibmcloud is cluster-network-interface-create CLUSTER_NETWORK --subnet SUBNET (--rip RIP | (--rip-address RIP_ADDRESS --rip-auto-delete true | false --rip-name RIP_NAME)) [--name NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-cluster-network-interface-create}

- `ibmcloud is cluster-network-interface-create my-cl-net --rip r134-2fbe71a8-126e-4a05-80ad-dad45df491a5 --subnet r124-72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
Create a cluster network interface by using RIP ID.
- `ibmcloud is cluster-network-interface-create my-cl-net --rip r134-2fbe71a8-126e-4a05-80ad-dad45df491a5 --subnet my-subnet`
Create a cluster network interface by using RIP ID.
- `ibmcloud is cluster-network-interface-create my-cl-net --rip r134-2fbe71a8-126e-4a05-80ad-dad45df491a5 --subnet my-subnet --name my-cl-net-intf`
Create a cluster network interface by using RIP ID.
- `ibmcloud is cluster-network-interface-create --rip-address 10.2.0.1 --rip-auto-delete true --rip-name my-subnet-rip --subnet r124-72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-cl-net-intf`
Create a cluster network interface with RIP prototype.
- `ibmcloud is cluster-network-interface-create --rip-address 10.2.0.1 --rip-auto-delete true --rip-name my-subnet-rip --subnet my-subnet --name my-cl-net-intf`
Create a cluster network interface with RIP prototype.

#### Command options
{: #command-options-cluster-network-interface-create}

- **CLUSTER_NETWORK**: ID or name for the cluster network.
- **--subnet**: ID or name for the cluster network subnet.
- **--rip**: ID or name of the reserved IP to bind primary IP address to the cluster network interface.
- **--rip-address**: The IP address of the reserved IP to bind to the cluster network interface, which must not already be reserved on the subnet.
- **--rip-auto-delete**: Indicates whether this cluster network subnet reserved IP member automatically deletes when either target is deleted, or the cluster network subnet reserved IP is unbound. One of: **true**, **false**.
- **--rip-name**: The name for this cluster network subnet reserved IP.
- **--name**: Name for the cluster network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-interface-update
{: #cluster-network-interface-update}

Update a cluster network interface.

```
ibmcloud is cluster-network-interface-update CLUSTER_NETWORK CLUSTER_NETWORK_INTERFACE [--name NEW_NAME] [--auto-delete true | false] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-cluster-network-interface-update}

- **CLUSTER_NETWORK**: ID or name for the cluster network.
- **CLUSTER_NETWORK_INTERFACE**: ID or name for the cluster network interface.
- **--name**: New name of the cluster network.
- **--auto-delete**: Indicates whether this cluster network subnet reserved IP member automatically deletes when either target is deleted, or the cluster network subnet reserved IP is unbound. One of: **true**, **false**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-interface-delete
{: #cluster-network-interface-delete}

Delete one or more cluster network interfaces.

```
ibmcloud is cluster-network-interface-delete CLUSTER_NETWORK (CLUSTER_NETWORK_INTERFACE1 CLUSTER_NETWORK_INTERFACE2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-cluster-network-interface-delete}

- **CLUSTER_NETWORK**: ID or name for the cluster network.
- **CLUSTER_NETWORK_INTERFACE1**: ID or name for the cluster network interface.
- **CLUSTER_NETWORK_INTERFACE2**: ID or name for the cluster network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-subnets
{: #cluster-network-subnets-list}

List all cluster network subnets.

```
ibmcloud is cluster-network-subnets CLUSTER_NETWORK [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-cluster-network-subnets}

- **CLUSTER_NETWORK**: ID or name for the cluster network.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-subnet
{: #cluster-network-subnet-view}

View details of a cluster network subnet.

```
ibmcloud is cluster-network-subnet CLUSTER_NETWORK CLUSTER_NETWORK_SUBNET [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-cluster-network-subnet}

- **CLUSTER_NETWORK**: ID or name for the cluster network.
- **CLUSTER_NETWORK_SUBNET**: ID or name for the cluster network subnet.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-subnet-create
{: #cluster-network-subnet-create}

Create a cluster network subnet.

```
ibmcloud is cluster-network-subnet-create CLUSTER_NETWORK (--total-ipv4-address-count TOTAL_IPV4_ADDRESS_COUNT | --ipv4-cidr-block IPV4_CIDR_BLOCK) [--name NAME] [--ip-version ipv4] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-cluster-network-subnet-create}

- `ibmcloud is cluster-network-subnet-create --total-ipv4-address-count 256 --name my-cl-net-sub --ip-version ipv4`
Create a cluster network subnet by using total IPv4 address count.
- `ibmcloud is cluster-network-subnet-create --ipv4-cidr-block 10.0.0.0/24 --name my-cl-net-sub --ip-version ipv4`
Create a cluster network subnet using ipv4 cidr block.

#### Command options
{: #command-options-cluster-network-subnet-create}

- **CLUSTER_NETWORK**: ID or name for the cluster network.
- **--total-ipv4-address-count**: The total number of IPv4 addresses required. Must be a power of 2.
- **--ipv4-cidr-block**: The IPv4 range of the cluster network subnet, expressed in CIDR format.
- **--name**: The name for this cluster network subnet.
- **--ip-version**: The IP versions to support for this cluster network subnet. One of: **ipv4**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-subnet-update
{: #cluster-network-subnet-update}

Update a cluster network subnet.

```
ibmcloud is cluster-network-subnet-update CLUSTER_NETWORK CLUSTER_NETWORK_SUBNET [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-cluster-network-subnet-update}

- `ibmcloud is cluster-network-subnet-update my-cl-net-sub --name my-updated-cl-net-sub`
- `ibmcloud is cluster-network-subnet-update r006-345545d8-798c-4dbc-112g-5c34a1e75e45 --name my-updated-cl-net-sub`

#### Command options
{: #command-options-cluster-network-subnet-update}

- **CLUSTER_NETWORK**: ID or name for the cluster network.
- **CLUSTER_NETWORK_SUBNET**: ID or name for the cluster network subnet.
- **--name**: New name of the cluster network subnet.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-subnet-delete
{: #cluster-network-subnet-delete}

Delete one or more cluster network subnets.

```
ibmcloud is cluster-network-subnet-delete CLUSTER_NETWORK (CLUSTER_NETWORK_SUBNET1 CLUSTER_NETWORK_SUBNET2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-cluster-network-subnet-delete}

- **CLUSTER_NETWORK**: ID or name for the cluster network.
- **CLUSTER_NETWORK_SUBNET1**: ID or name for the cluster network subnet.
- **CLUSTER_NETWORK_SUBNET2**: ID or name for the cluster network subnet.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-subnet-reserved-ips
{: #cluster-network-subnet-reserved-ips-list}

List all cluster network subnet reserved IPs.

```
ibmcloud is cluster-network-subnet-reserved-ips CLUSTER_NETWORK CLUSTER_NETWORK_SUBNET [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-cluster-network-subnet-reserved-ips}

- **CLUSTER_NETWORK**: ID or name for the cluster network.
- **CLUSTER_NETWORK_SUBNET**: ID or name for the cluster network subnet.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-subnet-reserved-ip
{: #cluster-network-subnet-reserved-ip-view}

View details of a cluster network subnet reserved IP.

```
ibmcloud is cluster-network-subnet-reserved-ip CLUSTER_NETWORK CLUSTER_NETWORK_SUBNET CLUSTER_NETWORK_SUBNET_RESERVED_IP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-cluster-network-subnet-reserved-ip}

- **CLUSTER_NETWORK**: ID or name for the cluster network.
- **CLUSTER_NETWORK_SUBNET**: ID or name for the cluster network subnet.
- **CLUSTER_NETWORK_SUBNET_RESERVED_IP**: ID or name for the cluster network subnet reserved IPs.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-subnet-reserved-ip-create
{: #cluster-network-subnet-reserved-ip-create}

Create a cluster network subnet reserved IP.

```
ibmcloud is cluster-network-subnet-reserved-ip-create CLUSTER_NETWORK CLUSTER_NETWORK_SUBNET [--name NAME] [--address ADDRESS] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-cluster-network-subnet-reserved-ip-create}

- `ibmcloud is cluster-network-subnet-reserved-ip-create my-cnet my-cnet-sub`
Create a cluster network subnet reserved IP.
- `ibmcloud is cluster-network-subnet-reserved-ip-create r134-2fbe71a8-126e-4a05-80ad-dad45df491a5 r124-72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name NAME my-cl-net-sub-rip`
Create a cluster network subnet reserved IP.
- `ibmcloud is cluster-network-subnet-reserved-ip-create my-cl-net my-cl-net-sub --name NAME my-cl-net-sub-rip --address 192.168.3.4`
Create a cluster network subnet reserved IP.
- `ibmcloud is cluster-network-subnet-reserved-ip-create r134-2fbe71a8-126e-4a05-80ad-dad45df491a5 r124-72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name NAME my-cl-net-sub-rip --address 192.168.3.4`
Create a cluster network subnet reserved IP.

#### Command options
{: #command-options-cluster-network-subnet-reserved-ip-create}

- **CLUSTER_NETWORK**: ID or name for the cluster network.
- **CLUSTER_NETWORK_SUBNET**: ID or name for the cluster network subnet.
- **--name**: The name for this cluster network subnet reserved IP.
- **--address**: The IP address to reserve, which must not already be reserved on the subnet.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-subnet-reserved-ip-update
{: #cluster-network-subnet-reserved-ip-update}

Update a cluster network.

```
ibmcloud is cluster-network-subnet-reserved-ip-update CLUSTER_NETWORK CLUSTER_NETWORK_SUBNET CLUSTER_NETWORK_SUBNET_RESERVED_IP [--auto-delete AUTO_DELETE] [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-cluster-network-subnet-reserved-ip-update}

- **CLUSTER_NETWORK**: ID or name for the cluster network.
- **CLUSTER_NETWORK_SUBNET**: ID or name for the cluster network subnet.
- **CLUSTER_NETWORK_SUBNET_RESERVED_IP**: ID or name for the cluster network subnet reserved IPs.
- **--auto-delete**: Indicates whether this cluster network subnet reserved IP member automatically deletes when either target is deleted, or the cluster network subnet reserved IP is unbound. Must be false if the cluster network subnet reserved IP is unbound.
- **--name**: New name of the cluster network subnet reserved IP.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is cluster-network-subnet-reserved-ip-delete
{: #cluster-network-subnet-reserved-ip-delete}

Delete one or more cluster network subnet reserved IPs.

```
ibmcloud is cluster-network-subnet-reserved-ip-delete CLUSTER_NETWORK CLUSTER_NETWORK_SUBNET (CLUSTER_NETWORK_SUBNET_RESERVED_IP1 CLUSTER_NETWORK_SUBNET_RESERVED_IP2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-cluster-network-subnet-reserved-ip-delete}

- **CLUSTER_NETWORK**: ID or name for the cluster network.
- **CLUSTER_NETWORK_SUBNET**: ID or name for the cluster network subnet.
- **CLUSTER_NETWORK_SUBNET_RESERVED_IP1**: ID or name for the cluster network subnet reserved IPs.
- **CLUSTER_NETWORK_SUBNET_RESERVED_IP2**: ID or name for the cluster network subnet reserved IPs.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

## Placement group
{: #placement-group}

### ibmcloud is placement-group
{: #placement-group-view}

View details of a placement group.

```
ibmcloud is placement-group PLACEMENT_GROUP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-placement-group}

- **PLACEMENT_GROUP**: ID or name of the placement group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is placement-group-create
{: #placement-group-create}

Create a placement group.

```
ibmcloud is placement-group-create (--strategy host_spread | power_spread) [--name NAME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-placement-group-create}

- `ibmcloud is placement-group-create --strategy host_spread`
- `ibmcloud is placement-group-create --strategy host_spread --output JSON`

#### Command options
{: #command-options-placement-group-create}

- **--strategy**: The strategy for this placement group. One of: **host_spread**, **power_spread**.
- **--name**: Name for the placement group.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is placement-group-delete
{: #placement-group-delete}

Delete one or more placement groups.

```
ibmcloud is placement-group-delete (PLACEMENT_GROUP1 PLACEMENT_GROUP2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-placement-group-delete}

- **PLACEMENT_GROUP1**: ID or name of the placement group.
- **PLACEMENT_GROUP2**: ID or name of the placement group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is placement-group-update
{: #placement-group-update}

Update a placement group.

```
ibmcloud is placement-group-update PLACEMENT_GROUP --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-placement-group-update}

- `ibmcloud is placement-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name`
- `ibmcloud is placement-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name --output JSON`

#### Command options
{: #command-options-placement-group-update}

- **PLACEMENT_GROUP**: ID or name of the placement group.
- **--name**: New name of the placement group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is placement-groups
{: #placement-groups-list}

List all placement groups.

```
ibmcloud is placement-groups [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-placement-groups}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Reservation
{: #reservation}

### ibmcloud is reservation
{: #reservation-view}

View details of a reservation.

```
ibmcloud is reservation RESERVATION [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-reservation}

- `ibmcloud is reservation r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2`
- `ibmcloud is reservation my-reservation-name`

#### Command options
{: #command-options-reservation}

- **RESERVATION**: ID or name of the reservation.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is reservations
{: #reservations-list}

List all reservations.

```
ibmcloud is reservations [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--zone ZONE] [--profile-resource-type instance_profile | bare_metal_server_profile] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-reservations}

- `ibmcloud is reservations`
- `ibmcloud is reservations --zone us-east-1`
- `ibmcloud is reservations --resource-group-id fee82deba12e4c0fb69c3b09d1f12345`
- `ibmcloud is reservations --profile-resource-type bare_metal_server_profile`
- `ibmcloud is reservations --profile-resource-type instance_profile`

#### Command options
{: #command-options-reservations}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--zone**: Filters the collection to resources with a zone name property that matches the exact specified name.
- **--profile-resource-type**: The resource type of the profile. One of: **instance_profile**, **bare_metal_server_profile**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is reservation-create
{: #reservation-create}

Create a reservation.

```
ibmcloud is reservation-create --capacity CAPACITY (--term one_year | three_year) --profile PROFILE_NAME (--profile-resource-type instance_profile | bare_metal_server_profile) --zone ZONE_NAME [--name NEW_NAME] [--affinity-policy restricted | automatic] [--expiration-policy release | renew] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-reservation-create}

- `ibmcloud is reservation-create --name reservation-1 --capacity 10 --term one_year --profile cx2-2x4 --profile-resource-type instance_profile --zone us-east-1`
- `ibmcloud is reservation-create --name reservation-2 --capacity 5 --term three_year --profile cx2-2x4 --profile-resource-type instance_profile --zone us-south-1 --resource-group-name Default --expiration-policy renew`
- `ibmcloud is reservation-create --name reservation-3 --capacity 8 --term three_year --profile cx2-2x4 --profile-resource-type instance_profile --zone us-south-2 --expiration-policy release --affinity-policy restricted --resource-group-id 11baaa8984beb82690daab08767et --output JSON`
- `ibmcloud is reservation-create --name my-reservation --capacity 2 --term three_year --profile cx2-2x4 --profile-resource-type instance_profile --zone us-south-2 --expiration-policy release --affinity-policy automatic --resource-group-id 11baaa8984beb82690daab08767et --output JSON`

#### Command options
{: #command-options-reservation-create}

- **--name**: Name for the reservation.
- **--capacity**: The capacity configuration for this reservation.
- **--term**: Term of the reservation. One of: **one_year**, **three_year**.
- **--profile**: The name of the profile to use for this reservation.
- **--profile-resource-type**: The resource type of the profile. One of: **instance_profile**, **bare_metal_server_profile**.
- **--zone**: Name of the zone.
- **--affinity-policy**: The affinity policy to use for this reservation. One of: **restricted**, **automatic**. (default: **automatic**).
- **--expiration-policy**: The policy to apply when the committed use term expires. One of: **release**, **renew**.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is reservation-update
{: #reservation-update}

Update a reservation.

```
ibmcloud is reservation-update RESERVATION [--name NEW_NAME] [--capacity CAPACITY] [--term one_year | three_year] [--expiration-policy release | renew] [--profile PROFILE_NAME] [--profile-resource-type instance_profile | bare_metal_server_profile] [--affinity-policy restricted | automatic] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-reservation-update}

- `ibmcloud is reservation-update r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2 --name reservation-1-new --capacity 7 --term one_year --profile profile-1-new --profile-resource-type instance_profile`
- `ibmcloud is reservation-update r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2 --expiration-policy renew`

#### Command options
{: #command-options-reservation-update}

- **RESERVATION**: ID or name of the reservation.
- **--name**: Name for the reservation.
- **--capacity**: The capacity configuration for this reservation.
- **--term**: Term of the reservation. One of: **one_year**, **three_year**.
- **--expiration-policy**: The policy to apply when the committed use term expires. One of: **release**, **renew**.
- **--profile**: The name of the profile to use for this reservation.
- **--profile-resource-type**: The resource type of the profile. One of: **instance_profile**, **bare_metal_server_profile**.
- **--affinity-policy**: The affinity policy to use for this reservation. One of: **restricted**, **automatic**. (default: **automatic**).
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is reservation-delete
{: #reservation-delete}

Delete one or more reservations.

```
ibmcloud is reservation-delete (RESERVATION1 RESERVATION2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command example
{: #command-example-reservation-delete}

- `ibmcloud is reservation-delete r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2`

#### Command options
{: #command-options-reservation-delete}

- **RESERVATION1**: ID or name of the reservation.
- **RESERVATION2**: ID or name of the reservation.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is reservation-activate
{: #reservation-activate-view}

Activate a reservation.

```
ibmcloud is reservation-activate RESERVATION [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-reservation-activate}

- `ibmcloud is reservation-activate r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2`

#### Command options
{: #command-options-reservation-activate}

- **RESERVATION**: ID or name of the reservation.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Auto scaling commands
{: #autoscaling-clis}

The following section provides information about CLI commands for auto scaling functionality.

## Instance templates
{: #instance-template}

### ibmcloud is instance-templates
{: #instance-templates-list}

List all templates in the region.

```
ibmcloud is instance-templates [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-templates}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-template
{: #instance-template-view}

View details of an instance template.

```
ibmcloud is instance-template TEMPLATE [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-template}

- **TEMPLATE**: ID or name of the template.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-template-create
{: #instance-template-create}

Create an instance template.

```
ibmcloud is instance-template-create INSTANCE_TEMPLATE_NAME VPC ZONE_NAME PROFILE_NAME SUBNET (--image IMAGE | (--catalog-offering CATALOG_OFFERING | --catalog-offering-version CATALOG_OFFERING_VERSION) [--catalog-offering-plan CATALOG_OFFERING_PLAN]) (([--pnac-name PRIMARY_NAC_NAME] [--pnac-vni PNAC_VNI | (--pnac-vni-ais false | true --pnac-vni-ein true | false --pnac-vni-auto-delete true | false --pnac-vni-ips VNI_RESERVED_IPS_JSON | @VNI_RESERVED_IPS_JSON_FILE --pnac-vni-name PNAC_VNI_NAME [--pnac-vni-rip PNAC_VNI_RIP | (--pnac-vni-rip-address PNAC_VNI_RIP_ADDRESS --pnac-vni-rip-auto-delete true | false --pnac-vni-rip-name PNAC_VNI_RIP_NAME)] --pnac-vni-sgs PNAC_VNI_SGS [--pnac-vni-psfm auto | enabled | disabled])] [--network-attachments NETWORK_ATTACHMENTS_JSON | @NETWORK_ATTACHMENTS_JSON_FILE]) | [([--rip RIP | (--address ADDRESS --auto-delete true | false --ip-name IP_NAME)] [--allow-ip-spoofing false | true]) | --primary-network-interface PRIMARY_NETWORK_INTERFACE_JSON | @PRIMARY_NETWORK_INTERFACE_JSON_FILE] [--network-interface NETWORK_INTERFACE_JSON | @NETWORK_INTERFACE_JSON_FILE]) [--total-volume-bandwidth TOTAL_VOLUME_BANDWIDTH] [--boot-volume BOOT_VOLUME_JSON | @BOOT_VOLUME_JSON_FILE] [--volume-attach VOLUME_ATTACH_JSON | @VOLUME_ATTACH_JSON_FILE] [--keys KEYS] [--dedicated-host DEDICATED_HOST | --dedicated-host-group DEDICATED_HOST_GROUP | --placement-group PLACEMENT_GROUP] [--reservation-affinity-policy, --res-policy disabled | manual | automatic] [--reservation-affinity-pool, --res-pool RESERVATION_AFFINITY_POOL] [--user-data DATA] [--sgs SGS] [--metadata-service, --ms true | false [--metadata-service-protocol, --msp http | https | --metadata-service-response-hop-limit, --msrhl METADATA_SERVICE_RESPONSE_HOP_LIMIT,MSRHL]] [--host-failure-policy restart | stop] [--confidential-compute-mode disabled | sgx | tdx] [--enable-secure-boot true | false] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [[--cluster-network-attachments CLUSTER_NETWORK_ATTACHMENTS_JSON | @CLUSTER_NETWORK_ATTACHMENTS_JSON_FILE]] [--output JSON] [-i, --interactive] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-template-create}

- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8`
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"name":"my-volume-name", "capacity":10, "profile": {"name": "general-purpose"},"user_tags": ["my-tag-1"]}}]'`
Create an instance template with a volume attachment.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"name":"my-volume-name", "bandwidth":1000, "capacity":10, "profile": {"name": "general-purpose"},"user_tags": ["my-tag-1"]}}]'`
Create an instance template with a volume attachment with bandwidth.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"id":"67531475-bd8a-478e-bcfe-2e53365cd0aa"}}]'`
Create an instance template with an existing volume in a volume attachment.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --keys 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
Create an instance template with multiple SSH keys.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "my-boot-vol", "capacity": 150, "profile": {"name": "general-purpose"}}}'`
Create an instance template with image with a boot volume capacity. The capacity value can range from the image's minimum provisioned size to 250.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "my-boot-vol", "profile": {"name": "general-purpose"},"user_tags": ["my-tag-1"]}}'`
Create an instance template with a boot volume and a boot volume with user tags.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"profile": {"name": "general-purpose"},"encryption_key": {"crn": "crn:v1:bluemix:public:kms:us-south:adffc98a0f1f0f95f6613b3b752286b87:e4a29d1a-2ef0-42a6-8fd2-350deb1c647e:key:5437653b-c4b1-447f-9646-b2a2a4cd6179"}}}'`
Create an instance template with an encrypted boot volume.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"bandwidth":1000, "profile": {"name": "general-purpose"},"encryption_key": {"crn": "crn:v1:bluemix:public:kms:us-south:adffc98a0f1f0f95f6613b3b752286b87:e4a29d1a-2ef0-42a6-8fd2-350deb1c647e:key:5437653b-c4b1-447f-9646-b2a2a4cd6179"}}}'`
Create an instance template with an encrypted boot volume with bandwidth.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --network-interface '[{"name": "secondary-nic", "allow_ip_spoofing": true, "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}]'`
Create an instance template that is attached to a secondary network interface.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "primary_ip": {"address": "10.240.129.10", "auto-delete": true, "name": "my-reserved-ip"}, "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}'`
Create an instance template with a primary network interface configuration in JSON.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --sgs 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --address 10.240.129.10 --auto-delete true --ip-name my-reserved-ip --allow-ip-spoofing true`
Create an instance template with a primary network interface configuration that includes security groups, reserved IP settings, and source IP spoofing setting.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --sgs 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --reserved-ip 0711-5c7f016e-5bd2-42e3-8dff-81519e4e2469 --allow-ip-spoofing true`
Create an instance template with a primary network interface configuration that includes security groups, existing reserved IP, and source IP spoofing setting.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host c019b1f7-c4d6-430c-aaa4-e0cc25d47277`
Create an instance template to be placed in the wanted dedicated host.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host-group a4738ceb-5e59-4601-849a-61d7895740ee`
Create an instance template to be placed in the wanted dedicated host group.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --placement-group 1d2afa0f-b9f2-4d85-ae35-a08885269644`
Create an instance template to be placed in the wanted placement group.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --total-volume-bandwidth 4000`
Create an instance template with a specific total volumes bandwidth.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --metadata-service true`
Create an instance template with metadata service enabled or disabled.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --metadata-service true --metadata-service-protocol http --metadata-service-response-hop-limit 60`
Create an instance template with metadata service configuration.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --reservation-affinity-policy manual --reservation-affinity-pool r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2`
Create an instance with reservation affinity.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --reservation-affinity-policy manual --reservation-affinity-pool crn:v1:bluemix:public:is:us-south:a/123456::vpc:4727d842-f94f-4a2d-824a-9bc9b02c523b`
Create an instance with reservation affinity.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --host-failure-policy restart`
Create an instance template with the availability policy on host failure.
- `ibmcloud is instance-template-create my-template-name my-vpc us-south-1 bx2-2x8 my-subnet --image ibm-ubuntu-20-04-2-minimal-amd64-1 --volume-attach '[{"volume": {"name":"my-vol-1"}}]'`
Create an instance template with an existing volume in a volume attachment by using the resource name.
- `ibmcloud is instance-template-create my-template-name my-vpc us-south-1 mx2-2x16 my-subnet --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host my-dedicated-host`
Create an instance template place in the wanted dedicated host by using resource name.
- `ibmcloud is instance-template-create my-template-name my-vpc us-south-1 mx2-2x16 my-subnet --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host-group my-dedicated-host-group`
Create an instance template place in the wanted dedicated host group by using resource name.
- `ibmcloud is instance-template-create my-template-name my-vpc us-south-1 mx2-2x16 my-subnet --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --placement-group my-placement-host-group`
Create an instance template place in the wanted placement group by using resource name.
- `ibmcloud is instance-template-create my-template-name my-vpc us-south-1 bx2-2x8 --image ibm-ubuntu-20-04-2-minimal-amd64-1 --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"name":"my-subnet"}, "primary_ip": {"name": "my-reserved-ip"}, "security_groups": [{"name": "my-security-group-1"}, {"name": "my-security-group-2"}]}'`
Create an instance template with the primary network interface configuration by using resource name.
- `ibmcloud is instance-template-create my-template-name my-vpc us-south-1 bx2-2x8 my-subnet --image ibm-ubuntu-20-04-2-minimal-amd64-1 --network-interface '[{"name": "secondary-nic", "allow_ip_spoofing": true, "subnet": {"id":"my-subnet"}, "security_groups": [{"id": "my-security-group-1"}, {"id": "my-security-group-2"}]}]'`
Create an instance template that is attached to the secondary network interface by using resource name.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"id": "67531475-bd8a-478e-bcfe-2e53365cd0aa"}}'`
Create an instance from an existing boot volume.
- `ibmcloud is instance-template-create my-template-name my-vpc us-south-1 bx2-2x8 my-subnet --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "my-existing-boot-vol"}}'`
Create an instance from an existing boot volume by using resource name.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --catalog-offering crn:v1:bluemix:public:globalcatalog-collection:global:a/efe5afc483594adaa8325e2b4d1290df:2497ae83-40cb-46ba-ac7f-5303514a2669:offering:54372a73-7a0a-4799-ac9c-8736620c67f1`
Create an instance template with a catalog offering.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --catalog-offering-version crn:v1:bluemix:public:globalcatalog-collection:global:a/efe5afc483594adaa8325e2b4d1290df:2497ae83-40cb-46ba-ac7f-5303514a2669:offering:54372a73-7a0a-4799-ac9c-8736620c67f1`
Create an instance template with a catalog offering version.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --catalog-offering-version crn:v1:bluemix:public:globalcatalog-collection:global:a/efe5afc483594adaa8325e2b4d1290df:2497ae83-40cb-46ba-ac7f-5303514a2669:offering:54372a73-7a0a-4799-ac9c-8736620c67f1 --catalog-offering-plan crn:v1:bluemix:public:globalcatalog-collection:global:a/123456:51c9e0db-2911-45a6-adb0-ac5332d27cf2:plan:sw.51c9e0db-2911-45a6-adb0-ac5332d27cf2.772c0dbe-aa62-482e-adbe-a3fc20101e0e`
Create instance from catalog offering version and plan.
- `ibmcloud is instance-template-create --interactive`
Create an instance template interactively.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --pnac-name cli-pnac-1 --pnac-vni 7322-1293a27a-7178-4e62-ba5b-272623c989aa --network-attachments [{"name": "instance-snac-1","virtual_network_interface": {"id":"02h7-56705448-c9d9-43dc-aa11-20d42333cd87"}}] --image --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8`
Create an instance with a network attachment and an existing virtual network interface.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --pnac-name cli-pnac-1 --pnac-vni-ais true --pnac-vni-ein true --pnac-vni-auto-delete true --pnac-vni-ips [{"id": "7322-f61b85bd-d963-4069-bb72-b58ed9ebc9f5"}] --pnac-vni-name cli-panc-vni-1 --pnac-vni-rip bee-olympics-perplexed-briskness --network-attachments [{"name": "instance-snac-1","virtual_network_interface": {"id":"02h7-56705448-c9d9-43dc-aa11-20d42333cd87"}}]`
Create an instance with a network attachment and new virtual network interface with existing reserved IP.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --pnac-name cli-pnac-1 --pnac-vni-ais true --pnac-vni-ein true --pnac-vni-auto-delete true --pnac-vni-ips [{"id": "7322-f61b85bd-d963-4069-bb72-b58ed9ebc9f5"},{"address": "10.240.128.13", "auto_delete" : true, "name": "vni-pnac-sip-1"}] --pnac-vni-name cli-panc-vni-1 --pnac-vni-rip-address 10.240.128.13 --pnac-vni-rip-auto-delete true --pnac-vni-rip-name pnac-vni-rip-1 --pnac-vni-sgs r134-8e0e4ad9-4ca3-4d5f-b9d8-7a967693d231`
Create an instance with a network attachment and new virtual network interface with existing reserved IP.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --cluster-network-attachments '[{"name": "instance-cnac-1","cluster_network_interface": {"id":"02h7-56705448-c9d9-43dc-aa11-20d42333cd87"}}]'`
Create an instance template with a cluster network attachment with existing cluster network interface with existing reserved IP.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --cluster-network-attachments '[{"name":"cli-cnac-1", "cluster_network_interface": {"auto_delete": true, "name": "cni-1",  "primary_ip": { "auto-delete": true, "name": "my-reserved-ip"}, "subnet": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}}]'`
Create an instance template with a cluster network attachment.

#### Command options
{: #command-options-instance-template-create}

- **INSTANCE_TEMPLATE_NAME**: Name of the instance template.
- **VPC**: ID or name of the VPC.
- **ZONE_NAME**: Name of the zone.
- **PROFILE_NAME**: Name of the profile.
- **SUBNET**: ID or name of the subnet.
- **--image**: ID or name of the image.
- **--catalog-offering**: The CRN for the IBM Cloud catalog offering. If specified, the latest version of that offering is used. For more information about creating a catalog offering, see [Onboarding software to your account](/docs/account?topic=account-create-private-catalog&interface=cli).
- **--catalog-offering-version**: The CRN for the version of a IBM Cloud catalog offering. For more information about creating a version for the catalog offering, see [Onboarding software to your account](/docs/account?topic=account-create-private-catalog&interface=cli).
- **--catalog-offering-plan**: The CRN for billing plan of a IBM Cloud catalog offering. If unspecified, no billing plan is used (free). Must be specified for catalog offering versions that require a billing plan.
- **--total-volume-bandwidth**: The amount of bandwidth (in megabits per second) that is allocated exclusively to instance storage volumes. An increase in this value results in a corresponding decrease to total network bandwidth.
- **--boot-volume**: BOOT_VOLUME_JSON|@BOOT_VOLUME_JSON_FILE, boot volume attachment in JSON or JSON file. For the data schema, see the **boot_volume_attachment** property in the [API documentation](/apidocs/vpc#create-instance).
- **--volume-attach**: VOLUME_ATTACH_JSON|@VOLUME_ATTACH_JSON_FILE, volume attachment in JSON or JSON file, list of volumes. For the data schema, see the **volume_attachments** property in the [API documentation](/apidocs/vpc#create-instance).
- **--keys**: Comma-separated IDs or names of SSH keys. SSH keys can be either RSA or Ed25519. Ed25519 can be used only if the operating system supports this key type. Ed25519 can't be used with Windows or VMware images.
- **--dedicated-host**: ID or name of the host destination where the instance is placed.
- **--dedicated-host-group**: ID or name of the host group destination where the instance is placed.
- **--placement-group**: ID or name of the placement group. The placement group restrictions for the virtual server instance.
- **--reservation-affinity-policy, --res-policy**: The reservation affinity policy to use for this virtual server instance. The policy defaults to manual if pool is not empty. The policy defaults to disabled if a placement_target is set. The policy defaults to automatic in all other cases. One of: **disabled**, **manual**, **automatic**.
- **--reservation-affinity-pool, --res-pool**: ID, name, or CRN of the reservation that is available to use by this virtual server instance.
- **--user-data**: data|@data-file. User data to transfer to the virtual server instance.
- **--rip**: ID or name of the existing reserved IP.
- **--address**: The IP address to reserve, which must not already be reserved on the subnet.
- **--auto-delete**: If set to **true**, this reserved IP automatically deletes when the target is deleted. One of: **true**, **false**. (default: **true**).
- **--ip-name**: The user-defined name for this reserved IP. Names must be unique within the subnet that the reserved IP resides in. Names beginning with **ibm-** are reserved for provider-owned resources.
- **--allow-ip-spoofing**: Disables the source and destination checks on this interface. If **false**, source IP spoofing is not allowed on this interface. One of: **false**, **true**.
- **--primary-network-interface**: PRIMARY_NETWORK_INTERFACE_JSON|@PRIMARY_NETWORK_INTERFACE_JSON_FILE, primary network interface in JSON or JSON file. For the data schema, see the **primary_network_interface** property in the [API documentation](/apidocs/vpc#create-instance).
- **--network-interface**: NETWORK_INTERFACE_JSON|@NETWORK_INTERFACE_JSON_FILE, network interface attachment in JSON or JSON file. For the data schema, see the **network_interfaces** property in the [API documentation](/apidocs/vpc#create-instance).
- **--pnac-name**: Name of the primary network attachment.
- **--pnac-vni**: ID or name of the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-ais**: Allow IP Spoofing (AIS). Indicates whether source IP spoofing is allowed on this virtual network interface that is associated with primary network attachment. One of: **false**, **true**. (default: **false**).
- **--pnac-vni-ein**: Enable infrastructure NAT (EIN). If **true**, the VPC infrastructure performs any needed NAT operations on the VNI. To attach a VNI to an instance, the value needs to be true. Floating_ips must not have more than one floating IP. If **false**, the packet is passed unmodified to or from the VNI, which allows it to perform any needed NAT operations. Allow_ip_spoofing must be false. Can be attached only to a target with a resource_type of bare_metal_server_network_attachment. One of: **true**, **false**. (default: **true**).
- **--pnac-vni-auto-delete**: Indicates whether this virtual network interface that is associated with primary network attachment automatically deletes when target is deleted. One of: **true**, **false**. (default: **true**).
- **--pnac-vni-ips**: VNI_RESERVED_IPS_JSON | @VNI_RESERVED_IPS_JSON_FILE, Secondary reserved IP addresses is in JSON or JSON file, to bind to the virtual network interface. For the data schema, see the IPS property in the [API documentation](/apidocs/vpc/latest#create-virtual-network-interface). One of: **VNI_RESERVED_IPS_JSON**, **@VNI_RESERVED_IPS_JSON_FILE**.
- **--pnac-vni-name**: The name for this virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-rip**: ID or name of the reserved IP to bind to the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-rip-address**: The IP address of the reserved IP to bind to the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-rip-auto-delete**: Indicates whether this reserved IP automatically deletes when either target is deleted, or if the reserved IP is unbound. One of: **true**, **false**. (default: **true**).
- **--pnac-vni-rip-name**: The name for this reserved IP to bind to the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-sgs**: IDs or names of the security groups to use for the virtual network interface that are associated with the primary network attachment.
- **--pnac-vni-psfm**: The protocol state filtering mode to use for this virtual network interface. If auto, protocol state packet filtering is enabled or disabled based on the virtual network interface's `target` resource type. One of: **auto**, **enabled**, **disabled**. (default: **auto**).
- **--network-attachments**: NETWORK_ATTACHMENTS_JSON|@NETWORK_ATTACHMENTS_JSON_FILE. Network attachment configuration is in JSON or JSON file. For the data schema, see the **network_attachments** property in the [API documentation](/apidocs/vpc#create-bare-metal-server). One of: **NETWORK_ATTACHMENTS_JSON**, **@NETWORK_ATTACHMENTS_JSON_FILE**.
- **--sgs**: Comma-separated security group ID or name for primary network interface or primary network attachment.
- **--metadata-service, --ms**: Enable or disable the Instance Metadata Service. One of: **true**, **false**.
- **--metadata-service-protocol, --msp**: The communication protocol for the metadata service endpoint. The protocol applies only when the metadata service is enabled. One of: **http**, **https**. (default: **http**).
- **--metadata-service-response-hop-limit, --msrhl**: The hop limit (IP time to live) for IP response packets from the metadata service.
- **--host-failure-policy**: The action to perform if the compute host experiences a failure. One of: **restart**, **stop**. (default: **restart**).
- **--confidential-compute-mode**: The confidential compute mode to use for this virtual server instance. If unspecified, the default confidential compute mode from the profile is used. One of: **disabled**, **sgx**, **tdx**.
- **--enable-secure-boot**: Indicates whether secure boot is enabled for this virtual server instance. If unspecified, the default secure boot mode from the profile is used. One of: **true**, **false**.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--cluster-network-attachments**: CLUSTER_NETWORK_ATTACHMENTS_JSON|@CLUSTER_NETWORK_ATTACHMENTS_JSON_FILE. Cluster network attachment configuration is in JSON or JSON file. For the data schema, see the **cluster_network_attachments** property in the [API documentation](/apidocs/vpc#create-instance). One of: **CLUSTER_NETWORK_ATTACHMENTS_JSON**, **@CLUSTER_NETWORK_ATTACHMENTS_JSON_FILE**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--interactive, -i**:
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-template-create-override-source-template
{: #instance-template-create-override-source-template}

Create an instance template by overriding a source template.

```
ibmcloud is instance-template-create-override-source-template --source-template SOURCE_TEMPLATE (([--pnac-name PRIMARY_NAC_NAME] [--pnac-vni PNAC_VNI | ((--pnac-vni-subnet PNAC_VNI_SUBNET [--vpc VPC]) --pnac-vni-ais false | true --pnac-vni-ein true | false --pnac-vni-auto-delete true | false --pnac-vni-ips VNI_RESERVED_IPS_JSON | @VNI_RESERVED_IPS_JSON_FILE --pnac-vni-name PNAC_VNI_NAME [--pnac-vni-rip PNAC_VNI_RIP | (--pnac-vni-rip-address PNAC_VNI_RIP_ADDRESS --pnac-vni-rip-auto-delete true | false --pnac-vni-rip-name PNAC_VNI_RIP_NAME)] --pnac-vni-sgs PNAC_VNI_SGS [--pnac-vni-psfm auto | enabled | disabled])] [--network-attachments NETWORK_ATTACHMENTS_JSON | @NETWORK_ATTACHMENTS_JSON_FILE]) | (--subnet SUBNET [--rip RIP | (--address ADDRESS --auto-delete true | false --ip-name IP_NAME)] [--allow-ip-spoofing false | true]) | --primary-network-interface PRIMARY_NETWORK_INTERFACE_JSON | @PRIMARY_NETWORK_INTERFACE_JSON_FILE [--network-interface NETWORK_INTERFACE_JSON | @NETWORK_INTERFACE_JSON_FILE]) [--name NAME] [--profile PROFILE] [--zone ZONE] [--vpc VPC] [--image IMAGE | (--catalog-offering CATALOG_OFFERING | --catalog-offering-version CATALOG_OFFERING_VERSION) [--catalog-offering-plan CATALOG_OFFERING_PLAN]] [--total-volume-bandwidth TOTAL_VOLUME_BANDWIDTH] [--boot-volume BOOT_VOLUME_JSON | @BOOT_VOLUME_JSON_FILE] [--volume-attach VOLUME_ATTACH_JSON | @VOLUME_ATTACH_JSON_FILE] [--keys KEYS] [--dedicated-host DEDICATED_HOST | --dedicated-host-group DEDICATED_HOST_GROUP | --placement-group PLACEMENT_GROUP] [--reservation-affinity-policy, --res-policy disabled | manual | automatic] [--reservation-affinity-pool, --res-pool RESERVATION_AFFINITY_POOL] [--user-data DATA] [--sgs SGS] [--metadata-service, --ms true | false [--metadata-service-protocol, --msp http | https | --metadata-service-response-hop-limit, --msrhl METADATA_SERVICE_RESPONSE_HOP_LIMIT,MSRHL]] [--host-failure-policy restart | stop] [--confidential-compute-mode disabled | sgx | tdx] [--enable-secure-boot true | false] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [[--cluster-network-attachments CLUSTER_NETWORK_ATTACHMENTS_JSON | @CLUSTER_NETWORK_ATTACHMENTS_JSON_FILE]] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-template-create-override-source-template}

- `ibmcloud is instance-template-create-override-source-template --source-template e4a29d1a-2ef0-42a6-8fd2-350deb1c647e`
Create an instance template by copying from a source template.
- `ibmcloud is instance-template-create-override-source-template --source-template e4a29d1a-2ef0-42a6-8fd2-350deb1c647e --name my-template-name --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --profile bx2-2x8`
Create an instance template by overriding a source template and by providing overriding options.
- `ibmcloud is instance-template-create-override-source-template --source-template my-template --name my-instance  --subnet my-subnet --image ibm-ubuntu-20-04-2-minimal-amd64-1 --volume-attach '[{"volume": {"name":"my-vol-1"}}]'`
Create instance template by overriding a source template with an existing volume in a volume attachment by using resource name.
- `ibmcloud is instance-template-create-override-source-template --source-template my-template --name my-instance  --subnet my-subnet --image ibm-ubuntu-20-04-2-minimal-amd64-1 --reservation-affinity-policy manual --reservation-affinity-pool r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2s`
Create an instance template by overriding a source template with a reservation affinity pool ID.
- `ibmcloud is instance-template-create-override-source-template --source-template my-template --name my-instance  --subnet my-subnet --image ibm-ubuntu-20-04-2-minimal-amd64-1 --reservation-affinity-policy manual --reservation-affinity-pool crn:v1:bluemix:public:is:us-south:a/123456::vpc:4727d842-f94f-4a2d-824a-9bc9b02c523b`
Create an instance template by overriding a source template with a reservation affinity pool CRN.
- `ibmcloud is instance-template-create-override-source-template --source-template my-template --name my-instance --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"name":"my-subnet"}, "primary_ip": {"name": "my-reserved-ip"}, "security_groups": [{"name": "my-security-group-1"}, {"name": "my-security-group-2"}]}'`
Create an instance template by overriding a source template with the primary network interface configuration by using the resource name.
- `ibmcloud is instance-template-create-override-source-template --source-template e4a29d1a-2ef0-42a6-8fd2-350deb1c647e --cluster-network-attachments [{"name": "instance-cnac-1","cluster_network_interface": {"id":"02h7-56705448-c9d9-43dc-aa11-20d42333cd87"}}]`
Create an instance template by overriding a source template with a cluster network attachment that has an existing cluster network interface and an existing reserved IP.
- `ibmcloud is instance-template-create-override-source-template --source-template e4a29d1a-2ef0-42a6-8fd2-350deb1c647e --cluster-network-attachments [{"name":"cli-cnac-1", "cluster_network_interface": {"auto_delete": true, "name": "cni-1",  "primary_ip": { "auto-delete": true, "name": "my-reserved-ip"}, "subnet": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}}]`
Create an instance template by overriding a source template with a cluster network attachment.
- `ibmcloud is instance-template-create-override-source-template --source-template 0717-9ac0ceaf-f10e-4500-98f6-978d83a7d3d4 --name cli-template --profile bx2-2x8 --vpc r006-1e635d53-6cd2-460f-917d-0737a3664d07 --subnet 0717-53d45c63-d61b-41f3-a784-249b856e7517  --zone us-south-1 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "boot-vol-name-0", "profile": {"name": "general-purpose"}, "source_snapshot": {"name": "test-cli"}, "allowed_use":{"instance":"true","bare_metal_server":"true","api_version":"2025-05-25"}}}' --volume-attach '[{"volume": {"name":"my-volume-name-0", "capacity":100, "profile": {"name": "general-purpose"}, "source_snapshot": {"id": "r006-523cf6c7-0591-43b9-b4ff-6663791e2814"}, "allowed_use":{"instance":"true","bare_metal_server":"true","api_version":"2025-05-25"}}}]'`
Create an instance template by overriding a source template with allowed use in boot-volume and volume-attachment.

#### Command options
{: #command-options-instance-template-create-override-source-template}

- **--source-template**: ID or name of the template.
- **--name**: Name of instance template.
- **--profile**: Name of the instance profile.
- **--zone**: Name of the zone.
- **--vpc**: The ID or name of the VPC. It is only required to specify the unique resource by name that is inside this VPC or to override the VPC value in the template.
- **--image**: ID or name of the image.
- **--catalog-offering**: The CRN for the IBM Cloud catalog offering. If specified, the latest version of that offering is used. For more information about creating a catalog offering, see [Onboarding software to your account](/docs/account?topic=account-create-private-catalog&interface=cli).
- **--catalog-offering-version**: The CRN for the version of a IBM Cloud catalog offering. For more information about creating a version for the catalog offering, see [Onboarding software to your account](/docs/account?topic=account-create-private-catalog&interface=cli).
- **--catalog-offering-plan**: The CRN for billing plan of a IBM Cloud catalog offering. If unspecified, no billing plan is used (free). Must be specified for catalog offering versions that require a billing plan.
- **--total-volume-bandwidth**: The amount of bandwidth (in megabits per second) that is allocated exclusively to instance storage volumes. An increase in this value results in a corresponding decrease to total network bandwidth.
- **--boot-volume**: BOOT_VOLUME_JSON|@BOOT_VOLUME_JSON_FILE, boot volume attachment in JSON or JSON file. For the data schema, see the **boot_volume_attachment** property in the [API documentation](/apidocs/vpc#create-instance).
- **--volume-attach**: VOLUME_ATTACH_JSON|@VOLUME_ATTACH_JSON_FILE, volume attachment in JSON or JSON file, list of volumes. For the data schema, see the **volume_attachments** property in the [API documentation](/apidocs/vpc#create-instance).
- **--keys**: Comma-separated IDs or names of SSH keys. SSH keys can be either RSA or Ed25519. Ed25519 can be used only if the operating system supports this key type. Ed25519 can't be used with Windows or VMware images.
- **--dedicated-host**: ID or name of the host destination where the instance is placed.
- **--dedicated-host-group**: ID or name of the host group destination where the instance is placed.
- **--placement-group**: ID or name of the placement group. The placement group restrictions for the virtual server instance.
- **--reservation-affinity-policy, --res-policy**: The reservation affinity policy to use for this virtual server instance. The policy defaults to manual if pool is not empty. The policy defaults to disabled if a placement_target is set. The policy defaults to automatic in all other cases. One of: **disabled**, **manual**, **automatic**.
- **--reservation-affinity-pool, --res-pool**: ID, name, or CRN of the reservation that is available to use by this virtual server instance.
- **--user-data**: data|@data-file. User data to transfer to the virtual server instance.
- **--subnet**: ID or name of the subnet.
- **--rip**: ID or name of the existing reserved IP.
- **--address**: The IP address to reserve, which must not already be reserved on the subnet.
- **--auto-delete**: If set to **true**, this reserved IP automatically deletes when the target is deleted. One of: **true**, **false**. (default: **true**).
- **--ip-name**: The user-defined name for this reserved IP. Names must be unique within the subnet that the reserved IP resides in. Names beginning with **ibm-** are reserved for provider-owned resources.
- **--allow-ip-spoofing**: Disables the source and destination checks on this interface. If **false**, source IP spoofing is not allowed on this interface. One of: **false**, **true**.
- **--primary-network-interface**: PRIMARY_NETWORK_INTERFACE_JSON|@PRIMARY_NETWORK_INTERFACE_JSON_FILE, primary network interface in JSON or JSON file. For the data schema, see the **primary_network_interface** property in the [API documentation](/apidocs/vpc#create-instance).
- **--network-interface**: NETWORK_INTERFACE_JSON|@NETWORK_INTERFACE_JSON_FILE, network interface attachment in JSON or JSON file. For the data schema, see the **network_interfaces** property in the [API documentation](/apidocs/vpc#create-instance).
- **--pnac-name**: Name of the primary network attachment.
- **--pnac-vni**: ID or name of the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-subnet**: The associated subnet.
- **--pnac-vni-ais**: Allow IP Spoofing (AIS). Indicates whether source IP spoofing is allowed on this virtual network interface that is associated with primary network attachment. One of: **false**, **true**. (default: **false**).
- **--pnac-vni-ein**: Enable infrastructure NAT (EIN). If **true**, the VPC infrastructure performs any needed NAT operations on the VNI. To attach a VNI to an instance, the value needs to be true. Floating_ips must not have more than one floating IP. If **false**, the packet is passed unmodified to or from the VNI, which allows it to perform any needed NAT operations. Allow_ip_spoofing must be false. Can be attached only to a target with a resource_type of bare_metal_server_network_attachment. One of: **true**, **false**. (default: **true**).
- **--pnac-vni-auto-delete**: Indicates whether this virtual network interface that is associated with primary network attachment automatically deletes when target is deleted. One of: **true**, **false**. (default: **true**).
- **--pnac-vni-ips**: VNI_RESERVED_IPS_JSON | @VNI_RESERVED_IPS_JSON_FILE, Secondary reserved IP addresses is in JSON or JSON file, to bind to the virtual network interface. For the data schema, see the IPS property in the [API documentation](/apidocs/vpc/latest#create-virtual-network-interface). One of: **VNI_RESERVED_IPS_JSON**, **@VNI_RESERVED_IPS_JSON_FILE**.
- **--pnac-vni-name**: The name for this virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-rip**: ID or name of the reserved IP to bind to the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-rip-address**: The IP address of the reserved IP to bind to the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-rip-auto-delete**: Indicates whether this reserved IP automatically deletes when either target is deleted, or if the reserved IP is unbound. One of: **true**, **false**. (default: **true**).
- **--pnac-vni-rip-name**: The name for this reserved IP to bind to the virtual network interface that is associated with the primary network attachment.
- **--pnac-vni-sgs**: IDs or names of the security groups to use for the virtual network interface that are associated with the primary network attachment.
- **--pnac-vni-psfm**: The protocol state filtering mode to use for this virtual network interface. If auto, protocol state packet filtering is enabled or disabled based on the virtual network interface's `target` resource type. One of: **auto**, **enabled**, **disabled**. (default: **auto**).
- **--network-attachments**: NETWORK_ATTACHMENTS_JSON|@NETWORK_ATTACHMENTS_JSON_FILE. Network attachment configuration is in JSON or JSON file. For the data schema, see the **network_attachments** property in the [API documentation](/apidocs/vpc#create-bare-metal-server). One of: **NETWORK_ATTACHMENTS_JSON**, **@NETWORK_ATTACHMENTS_JSON_FILE**.
- **--sgs**: Comma-separated security group ID or name for primary network interface or primary network attachment.
- **--metadata-service, --ms**: Enable or disable the Instance Metadata Service. One of: **true**, **false**.
- **--metadata-service-protocol, --msp**: The communication protocol for the metadata service endpoint. The protocol applies only when the metadata service is enabled. One of: **http**, **https**. (default: **http**).
- **--metadata-service-response-hop-limit, --msrhl**: The hop limit (IP time to live) for IP response packets from the metadata service.
- **--host-failure-policy**: The action to perform if the compute host experiences a failure. One of: **restart**, **stop**.
- **--confidential-compute-mode**: The confidential compute mode to use for this virtual server instance. If unspecified, the default confidential compute mode from the profile is used. One of: **disabled**, **sgx**, **tdx**.
- **--enable-secure-boot**: Indicates whether secure boot is enabled for this virtual server instance. If unspecified, the default secure boot mode from the profile is used. One of: **true**, **false**.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--cluster-network-attachments**: CLUSTER_NETWORK_ATTACHMENTS_JSON|@CLUSTER_NETWORK_ATTACHMENTS_JSON_FILE. Cluster network attachment configuration is in JSON or JSON file. For the data schema, see the **cluster_network_attachments** property in the [API documentation](/apidocs/vpc#create-instance). One of: **CLUSTER_NETWORK_ATTACHMENTS_JSON**, **@CLUSTER_NETWORK_ATTACHMENTS_JSON_FILE**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-template-update
{: #instance-template-update}

Update an instance template.

```
ibmcloud is instance-template-update TEMPLATE --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-template-update}

- `ibmcloud is instance-template-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name-template`
- `ibmcloud is instance-template-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name-template --output JSON`
- `ibmcloud is instance-template-update my-template --name new-name-template`
Update an instance template by using resource name.

#### Command options
{: #command-options-instance-template-update}

- **TEMPLATE**: ID or name of the template.
- **--name**: New name of an instance template.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-template-delete
{: #instance-template-delete}

Delete one or more instance templates.

```
ibmcloud is instance-template-delete (TEMPLATE1 TEMPLATE2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-template-delete}

- **TEMPLATE1**: ID or name of the template.
- **TEMPLATE2**: ID or name of the template.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

## Instance groups
{: #instance-group}

### ibmcloud is instance-groups
{: #instance-groups-list}

List all instance groups in the region.

```
ibmcloud is instance-groups [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-groups}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group
{: #instance-group-view}

View details of an instance group.

```
ibmcloud is instance-group INSTANCE_GROUP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-create
{: #instance-group-create}

Create an instance group.

```
ibmcloud is instance-group-create INSTANCE_GROUP_NAME --instance-template INSTANCE_TEMPLATE --subnets SUBNETS [--membership-count MEMBERSHIP_COUNT] [--lb LB --lb-pool LB_POOL --application-port APPLICATION_PORT] [--vpc VPC] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-group-create}

- `ibmcloud is instance-group-create group-name --instance-template 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is instance-group-create group-name --instance-template 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --membership-count 2`
- `ibmcloud is instance-group-create group-name --instance-template 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --output JSON`
- `ibmcloud is instance-group-create group-name --instance-template 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --lb 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --lb-pool d728d126-f2b9-48e8-ab67-16bb694b88f2 --application-port 2323`
- `ibmcloud is instance-group-create group-name --instance-template my-instance-template --subnets my-subnet-1,my-subnet-2 --vpc my-vpc`
- `ibmcloud is instance-group-create group-name --instance-template my-instance-template --subnets my-subnet-1,my-subnet-2 --lb my-load-balancer --lb-pool my-load-balancer-pool --application-port 80 --vpc my-vpc`

#### Command options
{: #command-options-instance-group-create}

- **INSTANCE_GROUP_NAME**: Name of the instance group.
- **--instance-template**: ID of an instance template.
- **--membership-count**: The membership count of the instance group.
- **--subnets**: Comma-separated IDs or names of subnets.
- **--lb**: ID or name of the load balancer.
- **--lb-pool**: ID or name of the load balancer pool.
- **--application-port**: The application port to route load balancer traffic.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-update
{: #instance-group-update}

Update an instance group.

```
ibmcloud is instance-group-update INSTANCE_GROUP [--instance-template INSTANCE_TEMPLATE] [--membership-count MEMBERSHIP_COUNT] [--subnets SUBNETS] [--name NEW_NAME] [--lb LB --lb-pool LB_POOL --application-port APPLICATION_PORT] [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-group-update}

- `ibmcloud is instance-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name --instance-template 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is instance-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --membership-count 2`
- `ibmcloud is instance-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnets 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is instance-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name --output JSON`
- `ibmcloud is instance-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --lb 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --lb-pool d728d126-f2b9-48e8-ab67-16bb694b88f3 --application-port 80`
- `ibmcloud is instance-group-update my-instance-group --subnets my-subnet-1,my-subnet-2 --vpc my-vpc`
- `ibmcloud is instance-group-update my-instance-group --instance-template my-template`
- `ibmcloud is instance-group-update my-instance-group --lb my-load-balancer --lb-pool my-load-balancer-pool --application-port 80 --vpc my-vpc`

#### Command options
{: #command-options-instance-group-update}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **--instance-template**: ID of an instance template.
- **--membership-count**: The membership count of the instance group.
- **--subnets**: Comma-separated IDs or names of subnets.
- **--name**: New name of the instance group.
- **--lb**: ID or name of the load balancer.
- **--lb-pool**: ID or name of the load balancer pool.
- **--application-port**: The application port to route load balancer traffic.
- **--vpc**: ID or name of the VPC. It is required to specify only the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-delete
{: #instance-group-delete}

Delete one or more instance groups.

```
ibmcloud is instance-group-delete (INSTANCE_GROUP1 INSTANCE_GROUP2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-delete}

- **INSTANCE_GROUP1**: ID or name of the instance group.
- **INSTANCE_GROUP2**: ID or name of the instance group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-load-balancer-delete
{: #instance-group-load-balancer-delete}

Delete an instance group load balancer.

```
ibmcloud is instance-group-load-balancer-delete INSTANCE_GROUP [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-load-balancer-delete}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-managers
{: #instance-group-managers-list}

List all managers for an instance group.

```
ibmcloud is instance-group-managers INSTANCE_GROUP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-managers}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager
{: #instance-group-manager-view}

View details of a manager.

```
ibmcloud is instance-group-manager INSTANCE_GROUP MANAGER [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-manager}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **MANAGER**: ID or name of the manager.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager-create
{: #instance-group-manager-create}

Create a manager for an instance group.

```
ibmcloud is instance-group-manager-create INSTANCE_GROUP [--manager-type autoscale | scheduled] [--aggregation-window AGGREGATION_WINDOW] [--cooldown COOLDOWN] [--max-members MAX_MEMBERS] [--min-members MIN_MEMBERS] [--name NAME] [--management-enabled true | false] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-group-manager-create}

- `ibmcloud is instance-group-manager-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --max-members 20`
- `ibmcloud is instance-group-manager-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --max-members 20 --output JSON`
- `ibmcloud is instance-group-manager-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --max-members 20 --min-members 2 --cooldown 400 --aggregation-window 120 --name my-autoscale-manager --management-enabled false`
- `ibmcloud is instance-group-manager-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-scheduled-manager --manager-type scheduled`
- `ibmcloud is instance-group-manager-create my-instance-group --max-members 20 --min-members 2 --cooldown 400 --aggregation-window 120 --name my-autoscale-manager --management-enabled false`

#### Command options
{: #command-options-instance-group-manager-create}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **--manager-type**: The type of instance group manager. One of: **autoscale**, **scheduled**. (default: **autoscale**).
- **--aggregation-window**: The time window in seconds to aggregate metrics prior to evaluation. Range 90-600. Divisible by 30. (default: **90**).
- **--cooldown**: The duration of time in seconds to pause further scale actions after scaling takes place. Range 120-3600. (default: **300**).
- **--max-members**: The maximum number of members in a managed instance group. Range 1-1000.
- **--min-members**: The minimum number of members in a managed instance group. Range 1-1000.
- **--name**: Name of the manager.
- **--management-enabled**: If set to false, the manager will not manipulate the instance group. One of: **true**, **false**. (default: **true**).
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager-update
{: #instance-group-manager-update}

Update a manager for an instance group.

```
ibmcloud is instance-group-manager-update INSTANCE_GROUP MANAGER [--aggregation-window AGGREGATION_WINDOW] [--cooldown COOLDOWN] [--max-members MAX_MEMBERS] [--min-members MIN_MEMBERS] [--management-enabled true | false] [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-group-manager-update}

- `ibmcloud is instance-group-manager-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --aggregation-window 120`
- `ibmcloud is instance-group-manager-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --cooldown 400`
- `ibmcloud is instance-group-manager-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --max-members 20`
- `ibmcloud is instance-group-manager-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --min-members 2`
- `ibmcloud is instance-group-manager-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --aggregation-window false --output JSON`
- `ibmcloud is instance-group-manager-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --management-enabled false`
- `ibmcloud is instance-group-manager-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name new_name`
- `ibmcloud is instance-group-manager-update my-instance-group my-instance-group-manager --management-enabled false`
- `ibmcloud is instance-group-manager-update my-instance-group my-instance-group-manager --name new_name`

#### Command options
{: #command-options-instance-group-manager-update}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **MANAGER**: ID or name of the manager.
- **--aggregation-window**: The time window, in seconds, to aggregate metrics prior to evaluation. Range 90-600. Divisible by 30.
- **--cooldown**: The duration of time, in seconds, to pause further scale actions after scaling takes place. Range 120-3600.
- **--max-members**: The maximum number of members in a managed instance group. Range 1-1000.
- **--min-members**: The minimum number of members in a managed instance group. Range 1-1000.
- **--management-enabled**: If set to false, the manager will not manipulate the instance group. One of: **true**, **false**.
- **--name**: New name of the instance group manager.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager-delete
{: #instance-group-manager-delete}

Delete one or more managers.

```
ibmcloud is instance-group-manager-delete INSTANCE_GROUP (MANAGER1 MANAGER2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-manager-delete}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **MANAGER1**: ID or name of the manager.
- **MANAGER2**: ID or name of the manager.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager-actions
{: #instance-group-manager-actions-list}

List actions for an instance group manager.

```
ibmcloud is instance-group-manager-actions INSTANCE_GROUP MANAGER [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-manager-actions}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **MANAGER**: ID or name of the manager.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager-action
{: #instance-group-manager-action-view}

View details of an instance group manager action.

```
ibmcloud is instance-group-manager-action INSTANCE_GROUP MANAGER ACTION [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-manager-action}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **MANAGER**: ID or name of the manager.
- **ACTION**: ID or name of the action.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager-action-create
{: #instance-group-manager-action-create}

Create an instance group manager action.

```
ibmcloud is instance-group-manager-action-create INSTANCE_GROUP MANAGER [--run-at RUN_AT | --cron CRON] [--membership-count MEMBERSHIP_COUNT | (--max-members MAX_MEMBERS --min-members MIN_MEMBERS)] [--name NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-group-manager-action-create}

- `ibmcloud is instance-group-manager-action-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --run-at '2024-10-28T21:13:32+08:00' --max-members 20 --min-members 10`
Create a one-time scheduled action to update the instance group autoscale manager.
- `ibmcloud is instance-group-manager-action-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --run-at '2024-10-28T21:13:32+08:00' --membership-count 10 --name my-action`
Create a one-time scheduled action to update the instance group.
- `ibmcloud is instance-group-manager-action-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --cron '*/5 1,2,3 * * *' --max-members 20 --min-members 5 --output JSON`
Create a recurring scheduled action with cron specification to update the instance group autoscale manager.
- `ibmcloud is instance-group-manager-action-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --cron '*/5 1,2,3 * * *' --membership-count 10 --name my-action`
Create a recurring scheduled action with cron specification to update the instance group.
- `ibmcloud is instance-group-manager-action-create my-instance-group --cron '*/5 1,2,3 * * *' --membership-count 10 --name my-action`
Create a recurring scheduled action with cron specification to update the instance group by using resource name.

#### Command options
{: #command-options-instance-group-manager-action-create}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **MANAGER**: ID or name of the manager.
- **--run-at**: The date and time specified for the scheduled action. Date and time must be in ISO 8601 format like **2024-03-05T15:31:50.701Z** or **2024-03-05T15:31:50.701+8:00**.
- **--cron**: The cron specification for a recurring scheduled action.
- **--membership-count**: The number of members the instance group must have at the scheduled time.
- **--max-members**: The maximum number of members in a managed instance group. Range 1-1000.
- **--min-members**: The minimum number of members in a managed instance group. Range 1-1000.
- **--name**: Name of the action.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager-action-update
{: #instance-group-manager-action-update}

Update an instance group manager action.

```
ibmcloud is instance-group-manager-action-update INSTANCE_GROUP MANAGER ACTION (--run-at RUN_AT | --cron CRON) [--membership-count MEMBERSHIP_COUNT | (--min-members MIN_MEMBERS --max-members MAX_MEMBERS)] [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-group-manager-action-update}

- `ibmcloud is instance-group-manager-action-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --name updatedName`
- `ibmcloud is instance-group-manager-action-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --max-members 20 --min-members 5`
- `ibmcloud is instance-group-manager-action-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --membership-count 10 --output JSON`
- `ibmcloud is instance-group-manager-action-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --run-at 2020-10-28T21:13:32+08:00`
- `ibmcloud is instance-group-manager-action-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --cron '*/5 1,2,3 * * *'`
- `ibmcloud is instance-group-manager-action-update my-instance-group my-instance-group-manager my-instance-group-manager-action --max-members 20 --min-members 5`

#### Command options
{: #command-options-instance-group-manager-action-update}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **MANAGER**: ID or name of the manager.
- **ACTION**: ID or name of the action.
- **--run-at**: The date and time specified for the scheduled action. Date and time must be in ISO 8601 format like **2024-03-05T15:31:50.701Z** or **2024-03-05T15:31:50.701+8:00**.
- **--cron**: The cron specification for a recurring scheduled action.
- **--membership-count**: The number of members the instance group must have at the scheduled time.
- **--min-members**: The minimum number of members the instance group must have at the scheduled time. Range 1-1000.
- **--max-members**: The maximum number of members the instance group must have at the scheduled time. Range 1-1000.
- **--name**: New name of the instance group manager action.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager-action-delete
{: #instance-group-manager-action-delete}

Delete one or more instance group manager actions.

```
ibmcloud is instance-group-manager-action-delete INSTANCE_GROUP MANAGER (ACTION1 ACTION2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-manager-action-delete}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **MANAGER**: ID or name of the manager.
- **ACTION1**: ID or name of the action.
- **ACTION2**: ID or name of the action.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager-policies
{: #instance-group-manager-policies-list}

List policies for an instance group manager.

```
ibmcloud is instance-group-manager-policies INSTANCE_GROUP MANAGER [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-manager-policies}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **MANAGER**: ID or name of the manager.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager-policy
{: #instance-group-manager-policy-view}

View details of an instance group manager policy.

```
ibmcloud is instance-group-manager-policy INSTANCE_GROUP MANAGER POLICY [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-manager-policy}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **MANAGER**: ID or name of the manager.
- **POLICY**: ID or name of the policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager-policy-create
{: #instance-group-manager-policy-create}

Create an instance group manager policy.

```
ibmcloud is instance-group-manager-policy-create INSTANCE_GROUP MANAGER (--metric-type cpu | memory | network_in | network_out) --metric-value METRIC_VALUE [--name NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-group-manager-policy-create}

- `ibmcloud is instance-group-manager-policy-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --metric-type cpu --metric-value 50`
- `ibmcloud is instance-group-manager-policy-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --metric-type cpu --metric-value 50 --output JSON`
- `ibmcloud is instance-group-manager-policy-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --metric-type cpu --metric-value 50 --name new_name`
- `ibmcloud is instance-group-manager-policy-create my-instance-group my-instance-group-manager --metric-type cpu --metric-value 50 --name new_name`

#### Command options
{: #command-options-instance-group-manager-policy-create}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **MANAGER**: ID or name of the manager.
- **--metric-type**: The type of metric to be evaluated: cpu (utilization percent), memory (utilization percent), network_in (Mbps), network_out (Mbps).
- **--metric-value**: The metric value to be evaluated.
- **--name**: Name of the policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager-policy-delete
{: #instance-group-manager-policy-delete}

Delete one or more instance group manager policies.

```
ibmcloud is instance-group-manager-policy-delete INSTANCE_GROUP MANAGER (POLICY1 POLICY2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-manager-policy-delete}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **MANAGER**: ID or name of the manager.
- **POLICY1**: ID or name of the policy.
- **POLICY2**: ID or name of the policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager-policy-update
{: #instance-group-manager-policy-update}

Update an instance group manager policy.

```
ibmcloud is instance-group-manager-policy-update INSTANCE_GROUP MANAGER POLICY [--metric-type cpu | memory | network_in | network_out] [--metric-value METRIC_VALUE] [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-group-manager-policy-update}

- `ibmcloud is instance-group-manager-policy-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --metric-value 50`
- `ibmcloud is instance-group-manager-policy-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --metric-type cpu`
- `ibmcloud is instance-group-manager-policy-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --metric-value 50 --metric-type cpu --output JSON`
- `ibmcloud is instance-group-manager-policy-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --metric-type cpu --name policy-name`
- `ibmcloud is instance-group-manager-policy-update my-instance-group my-instance-group-manager my-instance-group-policy --metric-value 50 --metric-type cpu --output JSON`

#### Command options
{: #command-options-instance-group-manager-policy-update}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **MANAGER**: ID or name of the manager.
- **POLICY**: ID or name of the policy.
- **--metric-type**: The type of metric to be evaluated: cpu (utilization percent), memory (utilization percent), network_in (Mbps), network_out (Mbps).
- **--metric-value**: The metric value to be evaluated.
- **--name**: New name of the instance group manager policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-membership
{: #instance-group-membership-view}

View details of a member of instance group.

```
ibmcloud is instance-group-membership INSTANCE_GROUP MEMBER [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-membership}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **MEMBER**: ID or name of the membership.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-membership-delete
{: #instance-group-membership-delete}

Delete one or more memberships for an instance group.

```
ibmcloud is instance-group-membership-delete INSTANCE_GROUP (MEMBER1 MEMBER2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-membership-delete}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **MEMBER1**: ID or name of the membership.
- **MEMBER2**: ID or name of the membership.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-membership-update
{: #instance-group-membership-update}

Update an instance group membership.

```
ibmcloud is instance-group-membership-update INSTANCE_GROUP MEMBER [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-group-membership-update}

- `ibmcloud is instance-group-membership-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name membership-name`
- `ibmcloud is instance-group-membership-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name membership-name --output JSON`
- `ibmcloud is instance-group-membership-update my-instance-group my-instance-group-membership --name membership-name`

#### Command options
{: #command-options-instance-group-membership-update}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **MEMBER**: ID or name of the membership.
- **--name**: New name of the instance group membership.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-memberships
{: #instance-group-memberships-list}

List all members of an instance group.

```
ibmcloud is instance-group-memberships INSTANCE_GROUP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-memberships}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-memberships-delete
{: #instance-group-memberships-delete}

Delete all memberships of an instance group.

```
ibmcloud is instance-group-memberships-delete INSTANCE_GROUP [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-memberships-delete}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

## REGIONS & ZONES COMMANDS
{: #geography}

The following section provides information about CLI commands for working with regions and zones.

## Regions
{: #regions}

### ibmcloud is region
{: #region-view}

View details of a region.

```
ibmcloud is region REGION_NAME [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-region}

- **REGION_NAME**: Name of the region.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is regions
{: #regions-list}

List all regions.

```
ibmcloud is regions [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-regions}

- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Zones
{: #zones}

### ibmcloud is zone
{: #zone-view}

View details of a zone in the target region.

```
ibmcloud is zone ZONE_NAME [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-zone}

- **ZONE_NAME**: Name of the zone.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is zones
{: #zones-list}

List all zones in the target region.

```
ibmcloud is zones [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-zones}

- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## STORAGE COMMANDS
{: #storage}



## Volumes
{: #volume-cli}

The following section provides information about CLI commands for volumes.

### ibmcloud is volumes
{: #volumes-list}

List all volumes.

```
ibmcloud is volumes [--attachment-state attached | unattached | unusable] [--encryption provider_managed | user_managed] [--operating-system-family OPERATING_SYSTEM_FAMILY] [--operating-system-architecture OPERATING_SYSTEM_ARCHITECTURE] [--zone ZONE] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-volumes}

- **--attachment-state**: Filters the collection to volumes with the specified attachment state. One of: **attached**, **unattached**, **unusable**.
- **--encryption**: Filters the collection to resources with the specified encryption type One of: **provider_managed**, **user_managed**.
- **--operating-system-family**: Filters the collection to resources with the exact specified operating system family. This option also supports the values null and `not:null` that filters the collection to resources that have no operating system or any operating system.
- **--operating-system-architecture**: null  Filters the collection to resources with the exact specified operating system architecture. This option also supports the values null and `not:null` that filters the collection to resources that have no operating system or any operating system.
- **--zone**: Filters the collection to resources in the zone with the exact specified name.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is volume
{: #volume-view}

View details of a volume.

```
ibmcloud is volume VOLUME [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-volume}

- `ibmcloud is volume my-volume`
- `ibmcloud is volume 485080f6-86e8-4fd4-a940-fb0e5bc269e0`

#### Command options
{: #command-options-volume}

- **VOLUME**: ID or name of the volume.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is volume-create
{: #volume-create}

Create a volume.

```
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--capacity CAPACITY] [--iops IOPS] [--encryption-key ENCRYPTION_KEY] [--snapshot SNAPSHOT [--allowed-use-api-version, --au-api-version ALLOWED_USE_API_VERSION, AU_API_VERSION] [--allowed-use-bare-metal-server, --au-bms ALLOWED_USE_BARE_METAL_SERVER, AU_BMS] [--allowed-use-instance, --au-ins ALLOWED_USE_INSTANCE, AU_INS]] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--tags  TAG_NAME1,TAG_NAME2,...] [--bandwidth BANDWIDTH] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-volume-create}

- `ibmcloud is volume-create my-volume general-purpose us-south-1`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --capacity 500`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --iops 10000 --capacity 1000`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --snapshot r134-2fbe71a8-126e-4a05-80ad-dad45df491a5`
Create a volume from snapshot
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --snapshot my-snapshot --capacity 500`
Create a volume from snapshot with capacity
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --tags env:test`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --tags env:test,env:dev`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --encryption-key crn:v1:bluemix:public:kms:us-south:adffc98a0f1f0f95f6613b3b752286b87:e4a29d1a-2ef0-42a6-8fd2-350deb1c647e:key:5437653b-c4b1-447f-9646-b2a2a4cd6179`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --resource-group-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --resource-group-name Default`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --output JSON`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --bandwidth 1000`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --snapshot my-snapshot --capacity 500 --allowed-use-api-version "2024-10-31" --allowed-use-bare-metal-server enable_secure_boot==true --allowed-use-instance true`

#### Command options
{: #command-options-volume-create}

- **VOLUME_NAME**: Name of the volume.
- **PROFILE_NAME**: Name of the profile.
- **ZONE_NAME**: Name of the zone.
- **--capacity**: The capacity of the volume in gigabytes. Range 10 - 16000 for custom and general-purpose profile volumes, 10 - 9600 for 5iops-tier profile volumes, 10 - 4800 for 10iops-tier profile volumes. After source snapshot is provided, the capacity value must be at least snapshot's **minimum_capacity**, and the default capacity value is source snapshot's **minimum_capacity**. (default: **100**).
- **--iops**: Input/output operations per second for the volume, it is only applicable for custom profile volumes. For the available IOPS ranges, see [Custom IOPS profile] [Onboarding software to your account](/docs/vpc?topic=vpc-block-storage-profiles#custom).
- **--encryption-key**: The CRN of the Key Management Service root key.
- **--snapshot**: ID, name, or CRN of the snapshot.
- **--allowed-use-api-version, --au-api-version**: The API version with which to evaluate the expressions.
- **--allowed-use-bare-metal-server, --au-bms**: The expression that must be satisfied by the properties of a bare metal server that is provisioned with the image data in this volume.
- **--allowed-use-instance, --au-ins**: The expression that must be satisfied by the properties of a virtual server instance that is provisioned with this volume.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--tags**: Tags for this resource.
- **--bandwidth**: The maximum bandwidth (in megabits per second) for the volume. For this property to be specified, the volume storage_generation must be 2.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is volume-delete
{: #volume-delete}

Delete one or more volumes.

```
ibmcloud is volume-delete (VOLUME1 VOLUME2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-volume-delete}

- `ibmcloud is volume-delete my-volume-3`
- `ibmcloud is volume-delete 485080f6-86e8-4fd4-a940-fb0e5bc269e0`

#### Command options
{: #command-options-volume-delete}

- **VOLUME1**: ID or name of the volume.
- **VOLUME2**: ID or name of the volume.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is volume-profiles
{: #volume-profiles-list}

List all volume profiles.

```
ibmcloud is volume-profiles [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-volume-profiles}

- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is volume-profile
{: #volume-profile-view}

View details of a volume profile.

```
ibmcloud is volume-profile PROFILE_NAME [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-volume-profile}

- **PROFILE_NAME**: Name of the profile.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is volume-update
{: #volume-update}

Update a volume.

```
ibmcloud is volume-update VOLUME [--name NAME | --capacity CAPACITY | --profile PROFILE --iops IOPS | --bandwidth BANDWIDTH] [--allowed-use-api-version, --au-api-version ALLOWED_USE_API_VERSION, AU_API_VERSION] [--allowed-use-bare-metal-server, --au-bms ALLOWED_USE_BARE_METAL_SERVER, AU_BMS] [--allowed-use-instance, --au-ins ALLOWED_USE_INSTANCE, AU_INS] [--tags  TAG_NAME1,TAG_NAME2,...] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-volume-update}

- `ibmcloud is volume-update 64bec87d-d175-4fa5-b240-b092fdbcedd6 --name my-volume --output JSON`
- `ibmcloud is volume-update 64bec87d-d175-4fa5-b240-b092fdbcedd6 --capacity 250 --output JSON`
- `ibmcloud is volume-update my-volume-demo-1 --name my-volume --output JSON`
- `ibmcloud is volume-update my-volume-demo-1 --capacity 250`
- `ibmcloud is volume-update cli-vol-acadia --iops 32000 --profile sdp`
- `ibmcloud is volume-update my-volume-demo-1 --allowed-use-api-version "2024-10-31" --allowed-use-bare-metal-server enable_secure_boot==true --allowed-use-instance true`
- `ibmcloud is volume-update cli-vol-acadia --bandwidth 8192`
- `ibmcloud is volume-update 64bec87d-d175-4fa5-b240-b092fdbcedd6 --profile 10iops-tier`
- `ibmcloud is volume-update 64bec87d-d175-4fa5-b240-b092fdbcedd6 --iops 5000`
- `ibmcloud is volume-update a9647a52-06f8-4b19-b904-920f67dcdfcd --capacity 500 --tags env:test`
- `ibmcloud is volume-update a9647a52-06f8-4b19-b904-920f67dcdfcd --capacity 500 --tags env:test,env:dev`

#### Command options
{: #command-options-volume-update}

- **VOLUME**: ID or name of the volume.
- **--name**: New name of the volume.
- **--capacity**: The capacity of the volume in gigabytes. Capacity can be expanded up to 250 for boot volume, 16000 for custom and general-purpose profile volumes, 9600 for **5iops-tier** profile volumes and 4800 for **10iops-tier** profile volumes. Size can be only increased, not decreased.
- **--profile**: Name of the profile. The volume must be attached as data volume and be switched between IOPS tiers. Changing predefined IOPS tier prorfile to custom profile is not supported. Changing custom profile to predefined IOPS tier profile is not supported.
- **--iops**: Input/output operations per second for the volume, it is only applicable for custom profile volumes. For the IOPS range, refer to [Onboarding software to your account](/docs/vpc?topic=vpc-block-storage-profiles#custom). The volume must be attached as a data volume.
- **--bandwidth**: The maximum bandwidth (in megabits per second) for the volume. For this property to be specified, the volume storage_generation must be 2.
- **--allowed-use-api-version, --au-api-version**: The API version with which to evaluate the expressions.
- **--allowed-use-bare-metal-server, --au-bms**: The expression that must be satisfied by the properties of a bare metal server that is provisioned with the image data in this volume.
- **--allowed-use-instance, --au-ins**: The expression that must be satisfied by the properties of a virtual server instance that is provisioned with this volume.
- **--tags**: Tags for this resource.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is volume-instance-profiles
{: #volume-instance-profiles-list}

List instance profiles that are compatible with a volume.

```
ibmcloud is volume-instance-profiles VOLUME [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-volume-instance-profiles}

- `ibmcloud is volume-instance-profiles my-volume`
- `ibmcloud is volume-instance-profiles my-volume --output JSON`
- `ibmcloud is volume-instance-profiles r134-064dcec0-5e15-42cf-8b28-a9d27f9cd751`
- `ibmcloud is volume-instance-profiles r134-064dcec0-5e15-42cf-8b28-a9d27f9cd751 --output JSON`

#### Command options
{: #command-options-volume-instance-profiles}

- **VOLUME**: ID or name of the volume.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Snapshots
{: #snapshots-cli}

The following section provides information about CLI commands for snapshots.

### ibmcloud is snapshots
{: #snapshots-list}

List all snapshots.

```
ibmcloud is snapshots [--volume VOLUME] [--tag TAG_NAME] [--source-image SOURCE_IMAGE] [--copies COPY1,COPY2,...] [--copies-remote-region COPIES_REMOTE_REGION] [--source-snapshot SOURCE_SNAPSHOT] [--source-snapshot-remote-region SOURCE_SNAPSHOT_REMOTE_REGION] [--volume-remote-region VOLUME_REMOTE_REGION] [--source-image-remote-region SOURCE_IMAGE_REMOTE_REGION] [--backup-policy-plan BACKUP_POLICY_PLAN --backup-policy BACKUP_POLICY] [--snapshot-consistency-group SNAPSHOT_CONSISTENCY_GROUP] [--clones-zone-name CLONES_ZONE_NAME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshots}

- `ibmcloud is snapshots`
- `ibmcloud is snapshots --volume r134-f13fc172-22e0-4e5b-ab81-63f5fe8b3ea0`
- `ibmcloud is snapshots --volume vol-bkp-policy-do-not-delete`
- `ibmcloud is snapshots --volume crn:v1:staging:public:is:us-south-2:a/efe5afc483594adaa8325e2b4d1290df::volume:r134-f13fc172-22e0-4e5b-ab81-63f5fe8b3ea0`
- `ibmcloud is snapshots --tag dev:env`
- `ibmcloud is snapshots --source-image r134-24d856e2-6aec-41c2-8f36-5a8a3766f0d6`
- `ibmcloud is snapshots --source-image ibm-centos-7-9-minimal-amd64-9`
- `ibmcloud is snapshots --source-image crn:v1:staging:public:is:us-east:a/efe5afc483594adaa8325e2b4d1290df::image:r134-24d856e2-6aec-41c2-8f36-5a8a3766f0d6`
- `ibmcloud is snapshots --copies r134-fc2a25b9-1cca-4cee-a9c4-0f350d7923f5`
- `ibmcloud is snapshots --copies snapshot-copy-us-east`
- `ibmcloud is snapshots --copies crn:v1:staging:public:is:us-south:a/efe5afc483594adaa8325e2b4d1290df::snapshot:r134-fc2a25b9-1cca-4cee-a9c4-0f350d7923f5`
- `ibmcloud is snapshots --copies-remote-region us-south`
- `ibmcloud is snapshots --source-volume-remote-region us-south`
- `ibmcloud is snapshots --source-snapshot-remote-region us-south`
- `ibmcloud is snapshots --backup-policy-plan r134-7d36a9df-9512-496e-8ad0-054cb4dd854c --backup-policy r134-3f56e0fa-1cfb-4341-9e57-de2a6345e7b3`
- `ibmcloud is snapshots --backup-policy-plan bkp-plan-do-not-delete --backup-policy bkp-policy-do-not-delete`
- `ibmcloud is snapshots --source-snapshot  r142-abb79ab7-d79d-4863-9678-123d1dffee06`
- `ibmcloud is snapshots --clones-zone-name us-south-2`
- `ibmcloud is snapshots --snapshot-consistency-group scg1`
- `ibmcloud is snapshots --snapshot-consistency-group r134-fc2a25b9-1cca-4cee-a9c4-0f350d7923f5`

#### Command options
{: #command-options-snapshots}

- **--volume**: ID, name, or CRN of the source volume.
- **--tag**: Tag for this resource.
- **--source-image**: ID, name, or CRN of the source image.
- **--copies**: ID, name, or CRN of the snapshot copies. Combination of these three types are not supported. Only passing either one of three types is supported.
- **--copies-remote-region**: Name of the snapshot copies remote region.
- **--source-snapshot**: ID or name of source snapshot.
- **--source-snapshot-remote-region**: Name of the source snapshot remote region.
- **--volume-remote-region**: Name of the source volume remote region.
- **--source-image-remote-region**: Name of the source image remote region.
- **--backup-policy-plan**: ID or name of the backup policy plan.
- **--backup-policy**: ID or name of the backup policy.
- **--snapshot-consistency-group**: ID, name or CRN of the snapshot consistency group.
- **--clones-zone-name**: Name of the snapshot clone zone.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot
{: #snapshot-view}

View details of a snapshot.

```
ibmcloud is snapshot SNAPSHOT [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshot}

- `ibmcloud is snapshot my-snapshot`
- `ibmcloud is snapshot r134-2fbe71a8-126e-4a05-80ad-dad45df491a5`

#### Command options
{: #command-options-snapshot}

- **SNAPSHOT**: ID or name of the snapshot.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-create
{: #snapshot-create}

Create a snapshot from a volume.

```
ibmcloud is snapshot-create (--volume VOLUME | --source-snapshot-crn SOURCE_SNAPSHOT_CRN [--encryption-key ENCRYPTION_KEY]) [--name NAME] [--clone-zones CLONE_ZONES] [--allowed-use-api-version, --au-api-version ALLOWED_USE_API_VERSION, AU_API_VERSION] [--allowed-use-bare-metal-server, --au-bms ALLOWED_USE_BARE_METAL_SERVER, AU_BMS] [--allowed-use-instance, --au-ins ALLOWED_USE_INSTANCE, AU_INS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--tags  TAG_NAME1,TAG_NAME2,...] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshot-create}

- `ibmcloud is snapshot-create --name my-snapshot-1 --volume test5-3zwxlnzgqk-9vk99`
- `ibmcloud is snapshot-create --name my-snapshot --volume r006-1772e102-0671-48c7-a97a-504247e61e48`
- `ibmcloud is snapshot-create --name my-snapshot --volume r006-1772e102-0671-48c7-a97a-504247e61e48 --resource-group-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is snapshot-create --name my-snapshot --volume r006-1772e102-0671-48c7-a97a-504247e61e48 --resource-group-name Default`
- `ibmcloud is snapshot-create --name my-snapshot --volume r006-1772e102-0671-48c7-a97a-504247e61e48 --output JSON`
- `ibmcloud is snapshot-create --name my-snapshot --volume r006-1772e102-0671-48c7-a97a-504247e61e48 --clone-zones us-south-1,us-south-2,us-south-3`
- `ibmcloud is snapshot-create --volume cf88cf1a-6f93-4cf6-bacf-62cafd3de857 --name my-ss70 --tags env:test`
- `ibmcloud is snapshot-create --volume cf88cf1a-6f93-4cf6-bacf-62cafd3de857 --name my-ss70 --tags env:test,env:dev`
- `ibmcloud is snapshot-create --volume test5-3zwxlnzgqk-9vk99 --name my-ss70 --tags env:test`
- `ibmcloud is snapshot-create --name my-snapshot --source-snapshot-crn crn:v1:bluemix:public:is:us-south:a/123456::snapshot:r134-f6bfa329-0e36-433f-a3bb-0df632e79263 --encryption-key crn:v1:bluemix:public:kms:us-south:a/dffc98a0f1f0f95f6613b3b752286b87:e4a29d1a-2ef0-42a6-8fd2-350deb1c647e:key:5437653b-c4b1-447f-9646-b2a2a4cd6179`
- `ibmcloud is snapshot-create --name my-snapshot --source-snapshot-crn crn:v1:bluemix:public:is:us-south:a/123456::snapshot:r134-f6bfa329-0e36-433f-a3bb-0df632e79263 --encryption-key crn:v1:bluemix:public:kms:us-south:a/dffc98a0f1f0f95f6613b3b752286b87:e4a29d1a-2ef0-42a6-8fd2-350deb1c647e:key:5437653b-c4b1-447f-9646-b2a2a4cd6179 --allowed-use-api-version "2024-10-31" --allowed-use-bare-metal-server true --allowed-use-instance enable_secure_boot==true`

#### Command options
{: #command-options-snapshot-create}

- **--volume**: ID, name, or CRN of the source volume.
- **--source-snapshot-crn**: CRN of the remote snapshot to create this snapshot from.
- **--encryption-key**: The root key to use to wrap the data encryption key for the snapshot. If unspecified, the encryption_key from the most recent snapshot with the same source volume is used. If this snapshot is the first snapshot of the source volume, the encryption_key from the source volume is used.
- **--name**: New name for the snapshot.
- **--clone-zones**: Comma-separated zone names that you want the snapshot clones to reside in. Snapshot fast restore is enabled in the cloned zones.
- **--allowed-use-api-version, --au-api-version**: The API version with which to evaluate the expressions.
- **--allowed-use-bare-metal-server, --au-bms**: The expression that must be satisfied by the properties of a bare metal server that is provisioned with the image data in this snapshot. If unspecified, the expression is set to true.
- **--allowed-use-instance, --au-ins**: The expression that must be satisfied by the properties of a virtual server instance that is provisioned with this snapshot. If unspecified, the expression is set to true.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--tags**: Tags for this resource.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-delete
{: #snapshot-delete}

Delete one or more snapshots.

```
ibmcloud is snapshot-delete (SNAPSHOT1 SNAPSHOT2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshot-delete}

- `ibmcloud is snapshot-delete my-snapshot`
- `ibmcloud is snapshot-delete r134-2fbe71a8-126e-4a05-80ad-dad45df491a5`

#### Command options
{: #command-options-snapshot-delete}

- **SNAPSHOT1**: ID or name of the snapshot.
- **SNAPSHOT2**: ID or name of the snapshot.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-update
{: #snapshot-update}

Update a snapshot.

```
ibmcloud is snapshot-update SNAPSHOT --name NEW_NAME [--allowed-use-api-version, --au-api-version ALLOWED_USE_API_VERSION, AU_API_VERSION] [--allowed-use-bare-metal-server, --au-bms ALLOWED_USE_BARE_METAL_SERVER, AU_BMS] [--allowed-use-instance, --au-ins ALLOWED_USE_INSTANCE, AU_INS] [--tags  TAG_NAME1,TAG_NAME2,...] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshot-update}

- `ibmcloud is snapshot-update 64bec87d-d175-4fa5-b240-b092fdbcedd6 --name my-snapshot --output JSON`
- `ibmcloud is snapshot-update cli-demo-snapshot-1 --name my-snapshot --output JSON`
- `ibmcloud is snapshot-update f8d51ab0-961f-4c23-8976-b1e48cc4f260 --name mysnapshot60 --tags env:tfp`
- `ibmcloud is snapshot-update f8d51ab0-961f-4c23-8976-b1e48cc4f260 --name mysnapshot60 --tags env:tfp,env:cli`
- `ibmcloud is snapshot-update my-snapshot-2 --name mysnapshot60 --tags env:tfp`
- `ibmcloud is snapshot-update my-snapshot-2 --allowed-use-api-version "2024-10-31" --allowed-use-bare-metal-server true --allowed-use-instance enable_secure_boot==true`

#### Command options
{: #command-options-snapshot-update}

- **SNAPSHOT**: ID or name of the snapshot.
- **--name**: New name of the snapshot.
- **--allowed-use-api-version, --au-api-version**: The API version with which to evaluate the expressions.
- **--allowed-use-bare-metal-server, --au-bms**: The expression that must be satisfied by the properties of a bare metal server that is provisioned with the image data in this snapshot. If unspecified, the expression is set to true.
- **--allowed-use-instance, --au-ins**: The expression that must be satisfied by the properties of a virtual server instance that is provisioned with this snapshot. If unspecified, the expression is set to true.
- **--tags**: Tags for this resource.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-clone
{: #snapshot-clone-view}

View details of a zonal snapshot clone.

```
ibmcloud is snapshot-clone SNAPSHOT ZONE_NAME [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshot-clone}

- `ibmcloud is snapshot-cl f0542d32-2c92-4f64-9d25-8469a5bef29d  us-east-2`
- `ibmcloud is snapshot-clone aaa-default-snapshot-2 us-east-1`

#### Command options
{: #command-options-snapshot-clone}

- **SNAPSHOT**: ID or name of the snapshot.
- **ZONE_NAME**: The zone name that this snapshot clone resides in. Snapshot fast restore is enabled in the cloned zones.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-clone-create
{: #snapshot-clone-create}

Create a zonal snapshot clone.

```
ibmcloud is snapshot-clone-create SNAPSHOT --zone ZONE [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshot-clone-create}

- `ibmcloud is snaphost-clone-create r134-77e21079-7291-44c2-866a-8f1848bc10f0 --zone us-south-2`
- `ibmcloud is snapshot-clone-create aaa-default-snapshot-2 --zone us-east-1`

#### Command options
{: #command-options-snapshot-clone-create}

- **SNAPSHOT**: ID or name of the snapshot.
- **--zone**: The name of the zone that you want the snapshot clone to reside in. Snapshot fast restore is enabled in the cloned zones.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-clone-delete
{: #snapshot-clone-delete}

Delete zonal snapshot clones in one or more zones.

```
ibmcloud is snapshot-clone-delete SNAPSHOT (ZONE_NAME1 ZONE_NAME2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshot-clone-delete}

- `ibmcloud is snaphost-clone-delete r134-77e21079-7291-44c2-866a-8f1848bc10f0 --zone us-south-2`
- `ibmcloud is snapshot-clone-delete aaa-default-snapshot-2 us-east-1`

#### Command options
{: #command-options-snapshot-clone-delete}

- **SNAPSHOT**: ID or name of the snapshot.
- **ZONE_NAME1**: The zone name that this snapshot clone resides in.
- **ZONE_NAME2**: The zone name that this snapshot clone resides in.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-clones
{: #snapshot-clones-list}

List all zonal snapshot clones.

```
ibmcloud is snapshot-clones SNAPSHOT [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshot-clones}

- `ibmcloud is snapshot-clones aaa-default-snapshot-2`
- `ibmcloud is snapshot-cls f0542d32-2c92-4f64-9d25-8469a5bef29d`

#### Command options
{: #command-options-snapshot-clones}

- **SNAPSHOT**: ID or name of the snapshot.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-instance-profiles
{: #snapshot-instance-profiles-list}

List instance profiles that are compatible with a snapshot.

```
ibmcloud is snapshot-instance-profiles SNAPSHOT [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshot-instance-profiles}

- `ibmcloud is snapshot-instance-profiles my-snapshot`
- `ibmcloud is snapshot-instance-profiles my-snapshot --output JSON`
- `ibmcloud is snapshot-instance-profiles r134-064dcec0-5e15-42cf-8b28-a9d27f9cd751`
- `ibmcloud is snapshot-instance-profiles r134-064dcec0-5e15-42cf-8b28-a9d27f9cd751 --output JSON`

#### Command options
{: #command-options-snapshot-instance-profiles}

- **SNAPSHOT**: ID or name of the snapshot.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-consistency-groups
{: #snapshot-consistency-groups-list}

List all snapshot consistency groups.

```
ibmcloud is snapshot-consistency-groups [--backup-policy-plan BACKUP_POLICY_PLAN --backup-policy BACKUP_POLICY] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshot-consistency-groups}

- `ibmcloud is snapshot-consistency-groups`
- `ibmcloud is snapshot-consistency-groups --backup-policy-plan r134-7d36a9df-9512-496e-8ad0-054cb4dd854c --backup-policy r134-3f56e0fa-1cfb-4341-9e57-de2a6345e7b3`
- `ibmcloud is snapshot-consistency-groups --backup-policy-plan bkp-plan-do-not-delete --backup-policy bkp-policy-do-not-delete`
- `ibmcloud is snapshot-consistency-groups --backup-policy-plan r134-7d36a9df-9512-496e-8ad0-054cb4dd854c --backup-policy bkp-policy-do-not-delete`
- `ibmcloud is snapshot-consistency-groups --backup-policy-plan bkp-plan-do-not-delete --backup-policy r134-3f56e0fa-1cfb-4341-9e57-de2a6345e7b3`

#### Command options
{: #command-options-snapshot-consistency-groups}

- **--backup-policy-plan**: ID or name of the backup policy plan.
- **--backup-policy**: ID or name of the backup policy.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-consistency-group
{: #snapshot-consistency-group-view}

View details of a snapshot consistency group.

```
ibmcloud is snapshot-consistency-group SNAPSHOT_CONSISTENCY_GROUP [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshot-consistency-group}

- `ibmcloud is snapshot-consistency-group r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2`
- `ibmcloud is snapshot-consistency-group example-snap-cg`

#### Command options
{: #command-options-snapshot-consistency-group}

- **SNAPSHOT_CONSISTENCY_GROUP**: ID or name of the snapshot consistency group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-consistency-group-create
{: #snapshot-consistency-group-create}

Create a snapshot consistency group.

```
ibmcloud is snapshot-consistency-group-create ((--snapshots SNAPSHOTS_JSON | @SNAPSHOTS_JSON_FILE) | (--source-volume SOURCE_VOLUME [--snapshot-name SNAPSHOT_NAME] [--user-tags USER_TAG_NAME1,USER_TAG_NAME2,...])) [--name NAME] [--delete-snapshot-on-delete false | true] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshot-consistency-group-create}

- `ibmcloud is snapshot-consistency-group-create --source-volume r006-1772e102-0671-48c7-a97a-504247e61e48`
- `ibmcloud is snapshot-consistency-group-create --source-volume r006-1772e102-0671-48c7-a97a-504247e61e48 --resource-group-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is snapshot-consistency-group-create --source-volume r006-1772e102-0671-48c7-a97a-504247e61e48 --resource-group-name Default`
- `ibmcloud is snapshot-consistency-group-create --source-volume r006-1772e102-0671-48c7-a97a-504247e61e48 --snapshot-name snapshot1 --name snapshot-consistency-group-1`
- `ibmcloud is snapshot-consistency-group-create --source-volume r006-1772e102-0671-48c7-a97a-504247e61e48 --user-tags env:test,env:stage`
- `ibmcloud is snapshot-consistency-group-create --source-volume r006-1772e102-0671-48c7-a97a-504247e61e48 --resource-group-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --output json`
- `ibmcloud is snapshot-consistency-group-create --source-volume r006-1772e102-0671-48c7-a97a-504247e61e48 --delete-snapshot-on-delete false --resource-group-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --output json`
- `ibmcloud is snapshot-consistency-group-create --snapshots '[{"source_volume":"r006-1772e102-0671-48c7-a97a-504247e61e48"}]'`
- `ibmcloud is snapshot-consistency-group-create --snapshots '[{"source_volume":"r006-1772e102-0671-48c7-a97a-504247e61e48","user_tags":["env:test,env:stage"],"snapshot_name":"snapshot1"}]' --name multi-snapshot-consistency-group --delete-snapshot-on-delete false`
- `ibmcloud is snapshot-consistency-group-create --snapshots @snapshots.json --name multi-snapshot-consistency-group --delete-snapshot-on-delete false`

#### Command options
{: #command-options-snapshot-consistency-group-create}

- **--snapshots**: SNAPSHOTS_JSON|@SNAPSHOTS_JSON_FILE, snapshots in JSON or JSON file, list of snapshots. For the data schema, check the **snapshots** property in the [API documentation](/apidocs/vpc#create-snapshot-consistency-group). One of: **SNAPSHOTS_JSON**, **@SNAPSHOTS_JSON_FILE**.
- **--source-volume**: ID, name, or CRN of the source volume.
- **--snapshot-name**: The name for this snapshot.
- **--user-tags**: The user tags associated with this snapshot.
- **--name**: Name for the snapshot consistency group.
- **--delete-snapshot-on-delete**: Indicates whether deleting the snapshot consistency group also deletes the snapshots in the group. One of: **false**, **true**. (default: **true**).
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-consistency-group-update
{: #snapshot-consistency-group-update}

Update a snapshot consistency group.

```
ibmcloud is snapshot-consistency-group-update [--name NEW_NAME] [--delete-snapshot-on-delete false | true] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshot-consistency-group-update}

- `ibmcloud is snapshot-consistency-group-update r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2 --name snapshot-consistency-group-1`
- `ibmcloud is snapshot-consistency-group-update r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2 --name snapshot-consistency-group-1 --delete-snapshot-on-delete false`
- `ibmcloud is snapshot-consistency-group-update snapshot-consistency-group-1-new --name snapshot-consistency-group-1-updated --delete-snapshot-on-delete false`

#### Command options
{: #command-options-snapshot-consistency-group-update}

- **--name**: New name for the snapshot-consistency-group.
- **--delete-snapshot-on-delete**: Indicates whether deleting the snapshot consistency group also deletes the snapshots in the group. One of: **false**, **true**. (default: **true**).
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-consistency-group-delete
{: #snapshot-consistency-group-delete}

Delete one or more snapshot consistency groups.

```
ibmcloud is snapshot-consistency-group-delete (SNAPSHOT_CONSISTENCY_GROUP1 SNAPSHOT_CONSISTENCY_GROUP2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshot-consistency-group-delete}

- `ibmcloud is snapshot-consistency-group-delete r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2`
- `ibmcloud is snapshot-consistency-group-delete scg1 scg2`

#### Command options
{: #command-options-snapshot-consistency-group-delete}

- **SNAPSHOT_CONSISTENCY_GROUP1**: ID or name of the snapshot consistency group.
- **SNAPSHOT_CONSISTENCY_GROUP2**: ID or name of the snapshot consistency group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

## File shares
{: #file-shares-cli}

The following section provides information about CLI commands for file shares.

### ibmcloud is share
{: #share-view}

View details of a file share.

```
ibmcloud is share SHARE [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-share}

- `ibmcloud is share r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2`
- `ibmcloud is share new-share`

#### Command options
{: #command-options-share}

- **SHARE**: ID or name of the file share.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-create
{: #share-create}

Create a file share.

```
ibmcloud is share-create (--profile PROFILE (--zone ZONE_NAME [--access-control-mode security_group | vpc] | [--snapshot SNAPSHOT --share SHARE]) [--size SIZE] [--encryption-key ENCRYPTION_KEY] [--initial-owner-gid INITIAL_OWNER_GID] [--initial-owner-uid INITIAL_OWNER_UID] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--replica-share-profile REPLICA_SHARE_PROFILE --replica-share-cron-spec REPLICA_SHARE_CRON_SPEC --replica-share-zone ZONE_NAME [--replica-share-iops REPLICA_SHARE_IOPS] [--replica-share-user-tags REPLICA_SHARE_USER_TAGS] [--replica-share-allowed-transit-encryption-modes, --rs-atem none,user_managed] [--replica-share-mount-targets MOUNT_TARGETS_JSON | @MOUNT_TARGETS_JSON_FILE] [--replica-share-name REPLICA_SHARE_NAME]] | --origin-share ORIGIN_SHARE) [--allowed-transit-encryption-modes, --atem none,user_managed] [--name NAME] [--user-tags USER_TAGS] [--mount-targets MOUNT_TARGETS_JSON | @MOUNT_TARGETS_JSON_FILE] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-share-create}

- `ibmcloud is share-create --name my-file-share --zone us-south-1 --profile dp2 --size 40`
- `ibmcloud is share-create --name my-file-share-1 --zone us-south-1 --profile dp2 --size 40 --initial-owner-gid 100 --initial-owner-uid 200`
- `ibmcloud is share-create --name my-file-share --zone us-south-1 --profile dp2 --size 40 --output JSON`
- `ibmcloud is share-create --name p-share-3 --zone us-south-1 --profile dp2 --replica-share-profile dp2 --replica-share-cron-spec '55 09 * * *' --replica-share-zone us-south-3  --replica-share-name replica-p-share-3 --replica-share-mount-targets '[{"name": "my-target1", "vpc": {"id": "r134-fa7c3b16-8a59-4434-8c2c-3230e916d441"}}]' --size 40`
- `ibmcloud is share-create --zone us-south-1 --profile dp2 --name my-file-share --user-tags env:dev,env:test --mount-targets '[{"name": "my-target121","vpc": {"name": "test-vpc-18-1"}},{"name": "my-target122","vpc": {"name": "vpc-0413"}}]' --replica-share-profile dp2 --replica-share-cron-spec '55 09 * * *' --replica-share-zone us-south-3 --replica-share-user-tags env:dev,env:prod --replica-share-name my-file-share-replica --replica-share-mount-targets '[{"name": "my-target1", "vpc": {"id": "r006-9265c6c2-13e7-4268-b4e9-658d4df1e2f6"}}]' --size 40`
- `ibmcloud is share-create --name my-file-share-3 --zone au-syd-1 --profile dp2 --size 40 --mount-targets '[{"name": "my-target1", "vpc": {"id": "r026-b403cfe8-917e-4fb8-a72c-bb490c735119"}}]' --replica-share-profile dp2  --replica-share-cron-spec '55 09 * * *' --replica-share-zone au-syd-2  --replica-share-name replica-p-share-3 --replica-share-mount-targets '[{"name": "my-replica-target1", "vpc": {"name": "vpc-1006-01"}}]'`
- `ibmcloud is share-create --name my-file-share --zone us-south-2 --profile dp2 --size 1000 --iops 1000`
- `ibmcloud is share-create --zone us-east-1 --profile dp2 --size 40 --encryption_key crn:v1:bluemix:public:kms:us-south:a/dffc98a0f1f0f95f6613b3b752286b87:e4a29d1a-2ef0-42a6-8fd2-350deb1c647e:key:5437653b-c4b1-447f-9646-b2a2a4cd6179`
- `ibmcloud is share-create --name my-fs-cli-1 --zone us-south-1 --profile dp2 --size 40 --mount-targets '[{"name":"my-target1","virtual_network_interface":{"name":"my-fs-cli-1-vni","primary_ip":{"id":"0716-d2a60008-84ca-4345-86f9-23a65dc75a32"},"resource_group":{"id":"11caaa983d9c4beb82690daab08717e9"},"security_groups":[{"id":"r134-a2f82965-1b8d-4bfe-9949-fe79e47daa86"}]}}]' --replica-share-profile dp2  --replica-share-cron-spec '55 09 * * *' --replica-share-zone us-south-2  --replica-share-name my-fs-cli-1-replica  --replica-share-mount-targets '[{"name":"my-target1","virtual_network_interface":{"name":"my-fs-cli-1-vni-2","primary_ip":{"address":"10.240.66.20","auto-delete":true,"name":"rip-vni-target"},"resource_group":{"id":"11caaa983d9c4beb82690daab08717e9"},"security_groups":[{"id":"r134-bd0f8527-c45c-496e-8d34-63bda6dd829b"}],"subnet":{"id":"0726-cf6d55db-284e-40c6-aea7-67dbabfa5542"}}}]'`
- `ibmcloud is share-create --name my-file-share --zone us-south-1 --profile dp2 --size 40 --atem user_managed,none`
- `ibmcloud is share-create --name my-file-accessor-share --origin-share crn:v1:bluemix:public:is:au-syd-1:a/1431ea2a7958ad20f0fee592ff85f746::share:r026-02aea1c7-adb6-4072-9799-6ca495561661`
- `ibmcloud is share-create --profile dp2 --snapshot r134-6ce54f3b-8971-4b5d-95a7-7dfa897ddfb3`
- `ibmcloud is share-create --profile dp2 --snapshot cli-share-snapshot --share my-file-share --user-tags "dev:tags"`
- `ibmcloud is share-create --profile dp2 --snapshot crn:v1:staging:public:is:us-south-1:a/efe5afc483594adaa8325e2b4d1290df::share-snapshot:r134-2ae87eb2-b26c-4126-ab34-e6e64f6f1773/r134-6ce54f3b-8971-4b5d-95a7-7dfa897ddfb3 --user-tags "dev:tags"`

#### Command options
{: #command-options-share-create}

- **--allowed-transit-encryption-modes, --atem**: Allowed transit encryption modes. One or more comma separated values of: none, user_managed.
- **--name**: The user-defined name for this file share.
- **--user-tags**: Tags for this resource.
- **--zone**: Name of the zone.
- **--access-control-mode**: The access control mode for the share. One of: **security_group**, **vpc**. (default: **security_group**).
- **--snapshot**: The ID, name, or CRN of the source snapshot for this file share.
- **--share**: ID or name of the file share.
- **--size**: The size of the file share is rounded up to the next gigabyte.
- **--profile**: The profile that the file share uses. All file shares that are created are based on the high-performance dp2 profile.
- **--encryption-key**: The root key to use to wrap the data encryption key for the share. If unspecified, the encryption type for the share is provider_managed.
- **--initial-owner-gid**: The initial owner group identifier for the file share at creation. Subsequent changes to the owner must be performed by a virtual server instance that mounted the file share.
- **--initial-owner-uid**: The initial owner user identifier for the file share at creation. Subsequent changes to the owner must be performed by a virtual server instance that mounted the file share.
- **--iops**: The maximum input/output operation performance bandwidth per second for the file share. This maximum is applicable for only custom profile file shares. For the IOPS range, refer to [Defined performance profile](/docs/vpc?topic=vpc-file-storage-profiles&interface=cli#dp2-profile).
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--replica-share-iops**: The maximum input/output operation performance bandwidth per second for the file share. This maximum is applicable for only custom profile file shares. For the IOPS range, refer to [Defined performance profile](/docs/vpc?topic=vpc-file-storage-profiles&interface=cli#dp2-profile).
- **--replica-share-user-tags**: Tags for this resource.
- **--replica-share-allowed-transit-encryption-modes, --rs-atem**: Allowed transit encryption modes. One or more comma separated values of: none, user_managed.
- **--replica-share-mount-targets**: MOUNT_TARGETS_JSON|@MOUNT_TARGETS_JSON_FILE, file share mount targets in JSON or JSON file One of: **MOUNT_TARGETS_JSON**, **@MOUNT_TARGETS_JSON_FILE**.
- **--replica-share-name**: The user-defined name for this file share.
- **--replica-share-profile**: The profile that the file share uses.
- **--replica-share-cron-spec**: The cron specification for the file share replication schedule.
- **--replica-share-zone**: The zone that this replica file share is to reside in. Must be a different zone in the same region as the source share.
- **--origin-share**: The ID, name or CRN of the origin share for the accessor share.
- **--mount-targets**: MOUNT_TARGETS_JSON|@MOUNT_TARGETS_JSON_FILE, file share mount targets in JSON or JSON file.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-delete
{: #share-delete}

Delete one or more file shares.

```
ibmcloud is share-delete (SHARE1 SHARE2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-share-delete}

- `ibmcloud is share-delete  my-file-share-99  cli-demo-00`
- `ibmcloud is share-delete  r006-866fc826-6f30-444f-b55e-0d697cf8b4bb`

#### Command options
{: #command-options-share-delete}

- **SHARE1**: ID or name of the file share.
- **SHARE2**: ID or name of the file share.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-profile
{: #share-profile-view}

View details of a file share profile.

```
ibmcloud is share-profile PROFILE_NAME [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-share-profile}

- **PROFILE_NAME**: Name of the file share profile.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-profiles
{: #share-profiles-list}

List all file share profiles in the region.

```
ibmcloud is share-profiles [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-share-profiles}

- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-update
{: #share-update}

Update a file share.

```
ibmcloud is share-update SHARE [--name NEW_NAME] [--size SIZE] [--replication-cron-spec REPLICATION_CRON_SPEC] [--iops IOPS] [--profile PROFILE] [--user-tags USER_TAGS] [--access-control-mode security_group | vpc] [--allowed-transit-encryption-modes, --atem none,user_managed] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-share-update}

- `ibmcloud is share-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-share`
- `ibmcloud is share-update my-file-share-0b88  --name new-share`
- `ibmcloud is share-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-share --output JSON`
- `ibmcloud is share-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --size 10000 --output JSON`
- `ibmcloud is share-update my-file-share --profile dp2 --iops 1200`
- `ibmcloud is share-update my-file-share --profile dp2`
- `ibmcloud is share-update my-file-share-1 --iops 1000`
- `ibmcloud is share-update p-share-32 --user-tags env:dev,env:prod`
- `ibmcloud is share-update my-fs-2-cli --access-control-mode security_group`
- `ibmcloud is share-update my-fs-2-cli --allowed-transit-encryption-modes user_managed,none`

#### Command options
{: #command-options-share-update}

- **SHARE**: ID or name of the file share.
- **--name**: New name of the file share.
- **--size**: The size of the file share rounded up to the next gigabyte. Size can be only increased, not decreased.
- **--replication-cron-spec**: The cron specification for the file share replication schedule.
- **--iops**: The maximum input/output operation performance bandwidth per second for the file share. This maximum is applicable for only custom profile file shares. For the IOPS range, refer to [Defined performance profile](/docs/vpc?topic=vpc-file-storage-profiles&interface=cli#dp2-profile).
- **--profile**: The profile that the file share uses.
- **--user-tags**: Tags for this resource.
- **--access-control-mode**: The access control mode for the share. One of: **security_group**, **vpc**. (default: **security_group**).
- **--allowed-transit-encryption-modes, --atem**: Allowed transit encryption modes. One or more comma separated values of: none, user_managed.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is shares
{: #shares-list}

List all file shares in the region.

```
ibmcloud is shares [--replication-role none | replica | source] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-shares}

- `ibmcloud is shares`
- `ibmcloud is shares --replication-role replica`

#### Command options
{: #command-options-shares}

- **--replication-role**: Filters the collection to file shares with the specified replication role. One of: **none**, **replica**, **source**.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-replica-create
{: #share-replica-create}

Create a replica file share from an existing file share.

```
ibmcloud is share-replica-create --zone ZONE_NAME --profile PROFILE [--name NAME] [--replica-share-user-tags REPLICA_SHARE_USER_TAGS] [--encryption-key ENCRYPTION_KEY] [--iops IOPS] [--mount-targets MOUNT_TARGETS_JSON | @MOUNT_TARGETS_JSON_FILE] [--replication-cron-spec REPLICATION_CRON_SPEC --source-share SOURCE_SHARE] [--allowed-transit-encryption-modes, --atem none,user_managed] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-share-replica-create}

- `ibmcloud is share-replica-create --name p-replica-share-3 --zone us-south-3 --profile dp2 --replication-cron-spec '10 05 * * *' --source-share r134-2b4c32f9-9d25-43df-9d59-3874a81ec46e`
- `ibmcloud is share-replica-create --name p-replica-share-3 --zone us-south-3 --profile dp2 --mount-targets '[{"name": "my-target1", "vpc": {"id": "r134-2f06ca6e-771e-40cc-9553-3838e2cc396d"}}]' --replication-cron-spec '10 05 * * *' --source-share my-file-share`
- `ibmcloud is share-replica-create --zone us-south-3 --profile dp2 --iops 1200 --name p-share-replica-32  --replica-share-user-tags env:dev,env:test --mount-targets  '[{"name": "my-target1", "vpc": {"name": "test-vpc-18-1"}}]' --replication-cron-spec '10 08 * * *' --source-share r006-0394a827-fe42-4341-b369-186e1a2288d3`
- `ibmcloud is share-replica-create --zone au-syd-2 --profile dp2 --mount-targets '[{"name": "my-target1", "vpc": {"id": "r026-b403cfe8-917e-4fb8-a72c-bb490c735119"}}]' --replication-cron-spec '10 05 * * *' --source-share my-file-share --name my-file-share-3-replica`
- `ibmcloud is share-replica-create --name p-replica-share-3 --zone us-south-3 --profile dp2 --replication-cron-spec '10 05 * * *' --source-share crn:v1:staging:public:is:us-south-2:a/egq5afc483594adaa8325e2b4d1290df::share:r134-ee076f3c-9b82-4e33-953c-866205612fc9 --encryption-key crn:v1:staging:public:kms:us-south:a/efe5afc483594adaa8325e2b4d1290df:1be45161-6dae-44ca-b248-837f98004057:key:3dd21cc5-dc20-4f7c-bc62-8ec9a8a3d1bd`

#### Command options
{: #command-options-share-replica-create}

- **--name**: The user-defined name for this file share.
- **--zone**: Name of the zone.
- **--replica-share-user-tags**: Tags for this resource.
- **--profile**: The profile that the file share uses.
- **--encryption-key**: The root key to use to wrap the data encryption key for the share. This property must be specified whether the source_share encryption type is user_managed, and must not be specified otherwise.
- **--iops**: The maximum input/output operation performance bandwidth per second for the file share. This maximum is applicable for only custom profile file shares. For the IOPS range, refer to [Defined performance profile](/docs/vpc?topic=vpc-file-storage-profiles&interface=cli#dp2-profile).
- **--mount-targets**: MOUNT_TARGETS_JSON|@MOUNT_TARGETS_JSON_FILE, file share mount targets in JSON or JSON file.
- **--replication-cron-spec**: The cron specification for the file share replication schedule.
- **--source-share**: Name or ID of source file share for this replica file share. The specified file share must not already have a replica, and must not be a replica.
- **--allowed-transit-encryption-modes, --atem**: Allowed transit encryption modes. One or more comma separated values of: none, user_managed.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-replica-failover
{: #share-replica-failover}

Failover to replica file share.

```
ibmcloud is share-replica-failover REPLICA_SHARE [--fallback-policy fail | split] [--timeout TIMEOUT] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-share-replica-failover}

- `ibmcloud is share-replica-failover r134-de1e70af-c3cb-44c6-a96d-2ece09b51ae3 --fallback-policy fail --timeout 1200`
- `ibmcloud is share-replica-failover r134-8a07129c-e376-4572-9ef3-68c729b315d5 --fallback-policy split --timeout 600`

#### Command options
{: #command-options-share-replica-failover}

- **REPLICA_SHARE**: ID or name of the replica file share.
- **--fallback-policy**: The action to take if the failover request is accepted but can't be performed or times out. One of: **fail**, **split**.
- **--timeout**: The failover timeout in seconds. The minimum timeout is 300 seconds and the maximum 3600 seconds. If the timeout is reached, the fallback_policy is triggered.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-replica-split
{: #share-replica-split}

Split the source file share from a replica share.

```
ibmcloud is share-replica-split REPLICA_SHARE [-f, --force] [-q, --quiet]
```

#### Command example
{: #command-example-share-replica-split}

- `ibmcloud is share-replica-split replica-p-share-3`

#### Command options
{: #command-options-share-replica-split}

- **REPLICA_SHARE**: ID or name of the replica file share.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-mount-target
{: #share-mount-target-view}

View details of a file share mount target.

```
ibmcloud is share-mount-target SHARE MOUNT_TARGET [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-share-mount-target}

- `ibmcloud is share-mount-target my-file-share-3 my-target1`

#### Command options
{: #command-options-share-mount-target}

- **SHARE**: ID or name of the file share.
- **MOUNT_TARGET**: ID or name of the file share mount target.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-mount-targets
{: #share-mount-targets-list}

List all share mount targets for a file share.

```
ibmcloud is share-mount-targets SHARE [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-share-mount-targets}

- `ibmcloud is share-mount-targets my-file-share-3`

#### Command options
{: #command-options-share-mount-targets}

- **SHARE**: ID or name of the file share.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-mount-target-delete
{: #share-mount-target-delete}

Delete one or more file share mount targets.

```
ibmcloud is share-mount-target-delete SHARE (MOUNT_TARGET1 MOUNT_TARGET2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command example
{: #command-example-share-mount-target-delete}

- `ibmcloud is share-mount-target-delete r026-b72bae3c-630b-4e06-bdf8-c3b27b8013f7 mount-target-test`

#### Command options
{: #command-options-share-mount-target-delete}

- **SHARE**: ID or name of the file share.
- **MOUNT_TARGET1**: ID or name of the file share mount target.
- **MOUNT_TARGET2**: ID or name of the file share mount target.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-mount-target-update
{: #share-mount-target-update}

Update a file share mount target.

```
ibmcloud is share-mount-target-update SHARE MOUNT_TARGET --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-share-mount-target-update}

- `ibmcloud is share-mount-target-update r026-b72bae3c-630b-4e06-bdf8-c3b27b8013f7 overbuilt-yogurt-detention-wreaths --name mount-target-test`

#### Command options
{: #command-options-share-mount-target-update}

- **SHARE**: ID or name of the file share.
- **MOUNT_TARGET**: ID or name of the file share mount target.
- **--name**: New name of the file share.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-mount-target-create
{: #share-mount-target-create}

Create a file share mount target.

```
ibmcloud is share-mount-target-create SHARE ([--vni VNI | (--vni-auto-delete true | false [--protocol-state-filtering-mode, --psfm auto | enabled | disabled] --vni-name VNI_NAME [--vni-rip VNI_RIP | (--vni-rip-address VNI_RIP_ADDRESS --vni-rip-auto-delete VNI_RIP_AUTO_DELETE --vni-rip-name VNI_RIP_NAME)] --subnet SUBNET --vni-sgs VNI_SGS --resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME)] | --vpc VPC) [--name NAME] [--transit-encryption user_managed | none] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-share-mount-target-create}

- `ibmcloud is share-mount-target-create r026-b72bae3c-630b-4e06-bdf8-c3b27b8013f7 --vpc vpc-1006-01`
- `ibmcloud is share-mount-target-create r042-3afab254-82b7-4627-94b2-35d8bdfcd306 --subnet 02u7-62c52bfc-6075-4dad-a588-bdb6a42d925b --vni-name cli-vni --vni-rip-auto-delete true --name my-cli-target --transit-encryption user_managed`
- `ibmcloud is share-mount-target-create cli-share-1 --subnet cli-subnet-1 --name cli-share-mount-target-1 --vni-name cli-share-vni-1 --vni-rip test --vni-sgs concrete-proudly-coastal-obvious,sg-vni --resource-group-name Default --vpc cli-vpc-1`
- `ibmcloud is share-mount-target-create cli-share-1 --subnet cli-subnet-1 --name cli-share-mount-target-1 --vni-name cli-share-vni-1 --psfm enabled --vni-rip test --vni-sgs concrete-proudly-coastal-obvious,sg-vni --resource-group-name Default --vpc cli-vpc-1`

#### Command options
{: #command-options-share-mount-target-create}

- **SHARE**: ID or name of the file share.
- **--name**: The user-defined name for this file share mount target.
- **--transit-encryption**: The transit encryption mode for this share mount target. none: no encryption in transit, user_managed: encrypted in transit using an instance identity certificate. Applicable only with shares that have access-control-mode security_group. One of: **user_managed**, **none**.
- **--vni**: ID or name of the virtual network interface.
- **--vni-auto-delete**: Indicates whether this virtual network interface automatically deletes when the target is deleted. One of: **true**, **false**. (default: **true**).
- **--protocol-state-filtering-mode**: auto,--psfm auto  The protocol state filtering mode to use for this virtual network interface. If auto, protocol state packet filtering is enabled or disabled based on the virtual network interface's `target` resource type. One of: **auto**, **enabled**, **disabled**. (default: **auto**).
- **--vni-name**: The name for this virtual network interface.
- **--vni-rip**: ID or name of the reserved IP to bind to the virtual network interface.
- **--vni-rip-address**: The IP address of the reserved IP to bind to the virtual network interface.
- **--vni-rip-auto-delete**: Indicates whether this reserved IP automatically deletes when either target is deleted, or if the reserved IP is unbound.
- **--vni-rip-name**: The name for this reserved IP to bind to the virtual network interface.
- **--subnet**: The subnet that is associated with this file share mount target.
- **--vni-sgs**: IDs or names of the security groups to use for the virtual network interface.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--vpc**: ID or name of the VPC to which this share mount target allows to mount the file share.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-accessor-bindings
{: #share-accessor-bindings-list}

List all accessor bindings of a share.

```
ibmcloud is share-accessor-bindings SHARE [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-share-accessor-bindings}

- `ibmcloud is share-accessor-bindings r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2`

#### Command options
{: #command-options-share-accessor-bindings}

- **SHARE**: ID or name of the file share.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-accessor-binding
{: #share-accessor-binding-view}

View details of an accessor binding.

```
ibmcloud is share-accessor-binding SHARE ACCESSOR_BINDING [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-share-accessor-binding}

- `ibmcloud is share-accessor-binding my-cli-accessor-share r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2`

#### Command options
{: #command-options-share-accessor-binding}

- **SHARE**: ID or name of the file share.
- **ACCESSOR_BINDING**: ID of the file share accessor binding.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-accessor-binding-delete
{: #share-accessor-binding-delete}

Delete one or more file share accessor bindings.

```
ibmcloud is share-accessor-binding-delete SHARE ACCESSOR_BINDING [-f, --force] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-share-accessor-binding-delete}

- `ibmcloud is share-accessor-binding-delete  my-file-share-99  r006-866fc826-6f30-444f-b55e-0d697cf8b4bb`
- `ibmcloud is share-accessor-binding-delete  r006-866fc826-6f30-444f-b55e-0d697cf8b4bb r006-866fc826-6f30-444f-b55e-0d697cf8b4bc`

#### Command options
{: #command-options-share-accessor-binding-delete}

- **SHARE**: ID or name of the file share.
- **ACCESSOR_BINDING**: ID of the file share accessor binding.
- **--force, -f**: Force the operation without confirmation.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-snapshot
{: #share-snapshot-view}

View details of a file share snapshot.

```
ibmcloud is share-snapshot SHARE SNAPSHOT [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-share-snapshot}

- `ibmcloud is share-snapshot my-cli-share r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2`

#### Command options
{: #command-options-share-snapshot}

- **SHARE**: ID or name of the file share.
- **SNAPSHOT**: ID or name of the file share snapshot.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-snapshots
{: #share-snapshots-list}

List all snapshots of a file share.

```
ibmcloud is share-snapshots [--share SHARE] [--backup-policy-plan BACKUP_POLICY_PLAN [--backup-policy BACKUP_POLICY]] [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-share-snapshots}

- `ibmcloud is share-snapshots --share r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2`

#### Command options
{: #command-options-share-snapshots}

- **--share**: ID or name of the file share.
- **--backup-policy-plan**: ID or name of the backup policy plan.
- **--backup-policy**: ID or name of the backup policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-snapshot-delete
{: #share-snapshot-delete}

Delete one or more file share snapshots.

```
ibmcloud is share-snapshot-delete SHARE (SNAPSHOT1 SNAPSHOT2 ...) [-f, --force] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-share-snapshot-delete}

- `ibmcloud is share-snapshot-delete my-file-share-99  r006-866fc826-6f30-444f-b55e-0d697cf8b4bb`
- `ibmcloud is share-snapshot-delete r006-866fc826-6f30-444f-b55e-0d697cf8b4bb r006-866fc826-6f30-444f-b55e-0d697cf8b4bc`

#### Command options
{: #command-options-share-snapshot-delete}

- **SHARE**: ID or name of the file share.
- **SNAPSHOT1**: ID or name of the file share snapshot.
- **SNAPSHOT2**: ID or name of the file share snapshot.
- **--force, -f**: Force the operation without confirmation.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-snapshot-update
{: #share-snapshot-update}

Update a file share snapshot.

```
ibmcloud is share-snapshot-update SHARE SNAPSHOT [--user-tags USER_TAGS] [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-share-snapshot-update}

- `ibmcloud is share-snapshot-update my-cli-share r006-81222eee-b3e0-4dc3-b429-aee9e5c0abf2 --user-tags dev:tags`

#### Command options
{: #command-options-share-snapshot-update}

- **SHARE**: ID or name of the file share.
- **SNAPSHOT**: ID or name of the file share snapshot.
- **--user-tags**: The user tags associated with this file share snapshot.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is share-snapshot-create
{: #share-snapshot-create}

Create a snapshot for a file share.

```
ibmcloud is share-snapshot-create SHARE [--name NAME] [--user-tags USER_TAGS] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-share-snapshot-create}

- `ibmcloud is share-snapshot-create r026-b72bae3c-630b-4e06-bdf8-c3b27b8013f7 --name cli-share-snapshot --user-tags env:dev,env:prod`
- `ibmcloud is share-snapshot-create cli-share-1  --name cli-share-snapshot --user-tags env:dev,env:prod`

#### Command options
{: #command-options-share-snapshot-create}

- **SHARE**: ID or name of the file share.
- **--name**: The user-defined name for this share shanpshot.
- **--user-tags**: The user tags associated with this file share snapshot.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Backup policy
{: #backup-policy}

The following section provides information about CLI commands for backup policies

### ibmcloud is backup-policies
{: #backup-policies-list}

List all backup policies.

```
ibmcloud is backup-policies [--tag TAG_NAME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-backup-policies}

- `ibmcloud is backup-policies`
- `ibmcloud is backup-policies --tag dev:test`

#### Command options
{: #command-options-backup-policies}

- **--tag**: Filters the collection to resources with the exact tag value.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is backup-policy-create
{: #backup-policy-create}

Create a backup policy.

```
ibmcloud is backup-policy-create --match-tags MATCH_TAGS [--name NAME] [--match-resource-type volume | share | instance [--included-content data_volumes | boot_volume | boot_volume,data_volumes]] [[--plans PLANS_JSON | @PLANS_JSON_FILE] | --plan-cron-spec PLAN_CRON_SPEC [--plan-name PLAN_NAME] --plan-active [--plan-attach-tags PLAN_ATTACH_TAGS] [--plan-copy-tags true | false] [[--plan-delete-after PLAN_DELETE_AFTER] [--plan-delete-over-count PLAN_DELETE_OVER_COUNT]] [[--plan-clone-policy-zones  ZONE1,ZONE2,...] [--plan-clone-policy-max-snapshots PLAN_CLONE_POLICY_MAX_SNAPSHOTS]]] [--scope SCOPE] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-backup-policy-create}

- `ibmcloud is backup-policy-create --match-tags dev:test --name demo-bkp-policy-1 --plan-name demo-bkp-plan-1 --plan-cron-spec '45 09 * * *'`
- `ibmcloud is backup-policy-create --match-tags dev:test --name demo-bkp-policy-2 --plan-name demo-bkp-plan-2 --plan-attach-tags dev:test --plan-copy-tags false --plan-delete-after 60 --plan-cron-spec '40 09 * * *'`
- `ibmcloud is backup-policy-create --match-tags dev:test --name demo-bkp-policy-x1`
- `ibmcloud is backup-policy-create --match-tags dev:test --name demo-bkp-policy-x --plan-name demo-bkp-plan-2 --plan-attach-tags dev:test --plan-copy-tags false --plan-delete-after 60 --plan-cron-spec '45 09 * * *' --plan-active  --plan-delete-over-count 2`
- `ibmcloud is backup-policy-create --match-tags dev:test --name backup-policy-z  --plans '[{"active":true,"attach_user_tags":["my-daily-backup-plan"],"copy_user_tags":true,"cron_spec":"45 09 * * *","deletion_trigger":{"delete_after":20,"delete_over_count":20},"name":"my-policy-plan"},{"active":true,"attach_user_tags":["my-daily-backup-plan"],"copy_user_tags":true,"cron_spec":"45 09 * * *","deletion_trigger":{"delete_after":20,"delete_over_count":20},"name":"my-policy-plan-99"}]'`
- `ibmcloud is backup-policy-create --match-tags dev:test --name backup-policy-x2  --plans @plans.json`
- `ibmcloud is backup-policy-create --match-tags dev:test --name demo-bkp-policy-x --plan-name demo-bkp-plan-2 --plan-attach-tags dev:test --plan-copy-tags false --plan-delete-after 60 --plan-cron-spec '45 09 * * *' --plan-active --plan-clone-policy-max-snapshots 4 --plan-clone-policy-zones us-south-1 --plan-delete-over-count 2`
Create backup-policy-plan with Fast Restore
- `ibmcloud is backup-policy-create --match-tags dev:test --name backup-policy-z  --plans '[{"active":true,"attach_user_tags":["my-daily-backup-plan"],"clone_policy":{"max_snapshots":2,"zones":[{"name":"us-south-1"}]},"copy_user_tags":true,"cron_spec":"45 09 * * *","deletion_trigger":{"delete_after":20,"delete_over_count":20},"name":"my-policy-plan"},{"active":true,"attach_user_tags":["my-daily-backup-plan"],"clone_policy":{"max_snapshots":2,"zones":[{"name":"us-south-1"}]},"copy_user_tags":true,"cron_spec":"45 09 * * *","deletion_trigger":{"delete_after":20,"delete_over_count":20},"name":"my-policy-plan-99"}]'`
Create backup-policy-plan with Fast Restore
- `ibmcloud is backup-policy-create --match-tags dev:test --name demo-bkp-policy-x1 --match-resource-type instance --included-content data_volumes,boot_volume`
Create backup-policy for match resource type instance and include both data and boot volumes as backup
- `ibmcloud is backup-policy-create --match-tags dev:test --name demo-bkp-policy-x1 --match-resource-type instance --included-content data_volumes`
Create backup-policy for match resource type instance and include only data volumes as backup
- `ibmcloud is backup-policy-create --match-tags dev:test --name demo-bkp-policy-x1 --match-resource-type instance --included-content boot_volume`
Create backup-policy for match resource type instance and include only boot volume as backup
- `ibmcloud is backup-policy-create --match-tags dev:test --name demo-bkp-policy-x1 --match-resource-type instance`
Create backup-policy for match resource type instance and default full backup (include both data and boot volumes)
- `ibmcloud is backup-policy-create --match-tags dev:test --name backup-scope-1 --scope crn:v1:bluemix:public:enterprise::a/e92d45e305dc4ee0b13e29be392f1c0c::enterprise:ebc2b430240943458b9e91e1432cfcce`
Create backup-policy for enterprise support
- `ibmcloud is backup-policy-create --match-tags dev:tags  --match-resource-type share --name demo-bkp-policy-share --plan-name demo-bkp-plan-2 --plan-cron-spec '1 * * * *'`
Create backup-policy for shares

#### Command options
{: #command-options-backup-policy-create}

- **--name**: New name for the backup policy.
- **--match-resource-type**: A resource type that this backup policy applies to. One of: **volume**, **share**, **instance**. (default: **volume**).
- **--included-content**: The included content for backups that were created by using this policy. One of: **data_volumes**, **boot_volume**, **boot_volume,data_volumes**. (default: **boot_volume,data_volumes**).
- **--match-tags**: The user tags that this backup policy applies to.
- **--plans**: PLANS_JSON|@PLANS_JSON_FILE, plans in JSON or JSON file, list of policy plans. For the data schema, check the **plans** property in the [API documentation](/apidocs/vpc#create-backup-policy). One of: **PLANS_JSON**, **@PLANS_JSON_FILE**.
- **--plan-name**: Name of the backup policy plan.
- **--plan-active**: Indicates whether the plan is active.
- **--plan-attach-tags**: User tags to attach to each resource that was created by this plan.
- **--plan-copy-tags**: Indicates whether to copy the source user tags to the created resource. One of: **true**, **false**.
- **--plan-cron-spec**: The cron specification for the backup schedule.
- **--plan-delete-after**: The maximum number of days to keep each backup after creation. (default: **30**).
- **--plan-delete-over-count**: The maximum number of recent backups to keep. If unspecified, all backups are kept.
- **--plan-clone-policy-max-snapshots**: The maximum number of recent snapshots (per source) that keep clones. (default: **5**).
- **--plan-clone-policy-zones**: The zone that this backup policy plan creates snapshot clones in.
- **--scope**: CRN of enterprise account.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is backup-policy-delete
{: #backup-policy-delete}

Delete one or more backup policies.

```
ibmcloud is backup-policy-delete (POLICY1 POLICY2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-backup-policy-delete}

- `ibmcloud is backup-policy-delete r134-7759199b-bc1f-448e-84fa-2aa42bde29af`
- `ibmcloud is backup-policy-delete demo-policy-100`

#### Command options
{: #command-options-backup-policy-delete}

- **POLICY1**: ID or name of the backup policy.
- **POLICY2**: ID or name of the backup policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is backup-policy-update
{: #backup-policy-update}

Update a backup policy.

```
ibmcloud is backup-policy-update POLICY [--match-tags MATCH_TAGS] [--included-content data_volumes | boot_volume | boot_volume,data_volumes] [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-backup-policy-update}

- `ibmcloud is backup-policy-update r134-aa88726e-8b34-4f97-992d-027df9c4bb36 --name my-policy2`
- `ibmcloud is backup-policy-update demo-policy-99 --name demo-policy-100`
- `ibmcloud is backup-policy-update backup-policy-1001 --match-tags demo:cli`
- `ibmcloud is backup-policy-update demo-policy-99 --included-content data_volumes,boot_volume`
Update backup-policy of match resource type instance to include both data and boot volumes as backup
- `ibmcloud is backup-policy-update demo-policy-99 --included-content data_volumes`
Create backup-policy for match resource type instance to include data volumes as backup
- `ibmcloud is backup-policy-update demo-policy-99 --included-content boot_volume`
Create backup-policy for match resource type instance to include boot volume as backup

#### Command options
{: #command-options-backup-policy-update}

- **POLICY**: ID or name of the backup policy.
- **--included-content**: The included content for backups that were created by using this policy. One of: **data_volumes**, **boot_volume**, **boot_volume,data_volumes**. (default: **boot_volume,data_volumes**).
- **--match-tags**: The user tags that this backup policy applies to.
- **--name**: New name of the backup policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is backup-policy
{: #backup-policy-view}

View details of a backup policy.

```
ibmcloud is backup-policy POLICY [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-backup-policy}

- `ibmcloud is backup-policy r134-ac2a8be2-aa99-4571-baed-c3ec63a64ce7`
- `ibmcloud is backup-policy demo-bkp-policy`

#### Command options
{: #command-options-backup-policy}

- **POLICY**: ID or name of the backup policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is backup-policy-plan
{: #backup-policy-plan-view}

View details of a backup policy plan.

```
ibmcloud is backup-policy-plan POLICY PLAN [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-backup-policy-plan}

- `ibmcloud is backup-policy-plan c884526b-e6cc-453d-934d-82bf39a39114 6e5b9ee4-d4f0-4e9b-89d6-18642823a855`
- `ibmcloud is backup-policy-plan demo-bkp-policy-b98 cli-demo-policy-plan-3`

#### Command options
{: #command-options-backup-policy-plan}

- **POLICY**: ID or name of the backup policy.
- **PLAN**: ID or name of the backup policy plan.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is backup-policy-plans
{: #backup-policy-plans-list}

List all plans for the backup policy.

```
ibmcloud is backup-policy-plans POLICY [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-backup-policy-plans}

- `ibmcloud is backup-policy-plans c884526b-e6cc-453d-934d-82bf39a39114`
- `ibmcloud is backup-policy-plans demo-bkp-policy-b98`

#### Command options
{: #command-options-backup-policy-plans}

- **POLICY**: ID or name of the backup policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is backup-policy-plan-create
{: #backup-policy-plan-create}

Create a backup policy plan.

```
ibmcloud is backup-policy-plan-create POLICY --cron-spec CRON_SPEC [--name NAME] [--active] [--attach-tags ATTACH_TAGS] [--copy-tags true | false] [[--delete-after DELETE_AFTER] [--delete-over-count DELETE_OVER_COUNT]] [[--clone-policy-zones  ZONE1,ZONE2,...] [--clone-policy-max-snapshots CLONE_POLICY_MAX_SNAPSHOTS]] [--remote-region-policies REMOTE_REGION_POLICY_JSON | @REMOTE_REGION_POLICY_JSON] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-backup-policy-plan-create}

- `ibmcloud is backup-policy-plan-create c9a0e8d9-c592-4175-80cb-3056f6fd1da7 --attach-tags dev:test --copy-tags true --cron-spec '*/5 1,2,3 * * *' --delete-after 80 --name my-policy-plan-1`
- `ibmcloud is backup-policy-plan-create c9a0e8d9-c592-4175-80cb-3056f6fd1da7  --cron-spec '*/5 1,2,3 * * *'  --name my-policy-plan-2`
- `ibmcloud is backup-policy-plan-create backup-policy-1001 --cron-spec '0 0 * * *' --active --name my-policy-plan --attach-tags my-daily-backup-plan --copy-tags true --delete-after 10 --delete-over-count 2 --clone-policy-max-snapshots 1 --clone-policy-zones us-south-1,us-south-2`
- `ibmcloud is backup-policy-plan-create backup-policy-1001 --cron-spec '0 0 * * *' --active --name my-policy-plan --attach-tags my-daily-backup-plan --copy-tags true --delete-after 10 --delete-over-count 2`
- `ibmcloud is backup-policy-plan-create c9a0e8d9-c592-4175-80cb-3056f6fd1da7  --cron-spec '*/5 1,2,3 * * *'  --name my-policy-plan-2 --remote-region-policies '[{"delete_over_count": 5,"region": {"name": "us-east"}},{"delete_over_count": 5,"region": {"name": "us-south"}}]'`
- `ibmcloud is backup-policy-plan-create c9a0e8d9-c592-4175-80cb-3056f6fd1da7  --cron-spec '*/5 1,2,3 * * *'  --name my-policy-plan-2 --remote-region-policies @/tmp/remote_region_policies.json`

#### Command options
{: #command-options-backup-policy-plan-create}

- **POLICY**: ID or name of the backup policy.
- **--name**: Name of the backup policy plan.
- **--active**: Indicates whether the plan is active.
- **--attach-tags**: User tags to attach to each resource that was created by this plan.
- **--copy-tags**: Indicates whether to copy the source user tags to the created resource. One of: **true**, **false**.
- **--cron-spec**: The cron specification for the backup schedule.
- **--delete-after**: The maximum number of days to keep each backup after its created.
- **--delete-over-count**: The maximum number of recent backups to keep. If unspecified, all backups are kept.
- **--clone-policy-max-snapshots**: The maximum number of recent snapshots (per source) that keep clones. (default: **5**).
- **--clone-policy-zones**: The zone that this backup policy plan creates snapshot clones in.
- **--remote-region-policies**: REMOTE_REGION_POLICY_JSON|@REMOTE_REGION_POLICY_JSON, remote region policies in JSON or JSON file.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is backup-policy-plan-delete
{: #backup-policy-plan-delete}

Delete one or more backup policy plans.

```
ibmcloud is backup-policy-plan-delete (PLAN1 PLAN2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command examples
{: #command-examples-backup-policy-plan-delete}

- `ibmcloud is backup-policy-plan-delete backup-policy-1001 437cc10e-eaa5-4eaf-8e9d-5ba5d659f9a1 ec5446a2-5f28-4d25-a501-b6fa14f3c5d8`
- `ibmcloud is backup-policy-plan-delete aaa-default-backup-policy-1 my-policy-plan-2 my-policy-plan-3 my-policy-plan-4`

#### Command options
{: #command-options-backup-policy-plan-delete}

- **PLAN1**: ID or name of the backup policy plan.
- **PLAN2**: ID or name of the backup policy plan.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is backup-policy-plan-update
{: #backup-policy-plan-update}

Update a backup policy plan.

```
ibmcloud is backup-policy-plan-update POLICY PLAN [--name NAME] [--active] [--attach-tags ATTACH_TAGS] [--copy-tags true | false] [--cron-spec CRON_SPEC] [[--delete-after DELETE_AFTER] [--delete-over-count DELETE_OVER_COUNT]] [--reset-delete-over-count] [[--clone-policy-zones  ZONE1,ZONE2,...] [--clone-policy-max-snapshots CLONE_POLICY_MAX_SNAPSHOTS]] [--remote-region-policies REMOTE_REGION_POLICY_JSON | @REMOTE_REGION_POLICY_JSON] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-backup-policy-plan-update}

- `ibmcloud is backup-policy-plan-update r134-77e21079-7291-44c2-866a-8f1848bc10f0 r134-fc8e15d9-02f2-4599-a216-8afe0dfeb969 --name myplan`
- `ibmcloud is backup-policy-plan-update demo-bkp-policy-b98 my-policy-plan-1 --name cli-demo-policy-plan-3`
- `ibmcloud is backup-policy-plan-update backup-policy-1001 2dae356e-f7b5-48dd-8bc3-f3083574885b --cron-spec '42 10 * * *' --name my-policy-plan-1 --attach-tags my-daily-backup-plan --copy-tags false --delete-after 20 --delete-over-count 1 --clone-policy-max-snapshots 3 --clone-policy-zones us-south-1,us-south-2 --active`
- `ibmcloud is backup-policy-plan-update backup-policy-1001 2dae356e-f7b5-48dd-8bc3-f3083574885b --cron-spec '42 10 * * *' --name my-policy-plan-1 --attach-tags my-daily-backup-plan --copy-tags false --delete-after 20 --delete-over-count 1`
- `ibmcloud is backup-policy-plan-update demo-bkp-policy-x demo-bkp-plan-2 --reset-delete-over-count`
- `ibmcloud is backup-policy-plan-update demo-bkp-policy-x demo-bkp-plan-2 --reset-delete-over-count --remote-region-policies '[{"delete_over_count": 5,"region": {"name": "us-east"}},{"delete_over_count": 5,"region": {"name": "us-south"}}]'`

#### Command options
{: #command-options-backup-policy-plan-update}

- **POLICY**: ID or name of the backup policy.
- **PLAN**: ID or name of the backup policy plan.
- **--name**: New name of the backup policy plan.
- **--active**: Indicates whether the plan is active.
- **--attach-tags**: User tags to attach to each resource that was created by this plan.
- **--copy-tags**: Indicates whether to copy the source user tags to the created resource. One of: **true**, **false**.
- **--cron-spec**: The cron specification for the backup schedule.
- **--delete-after**: The maximum number of days to keep each backup after creation.
- **--delete-over-count**: The maximum number of recent backups to keep. If unspecified, all backups are kept.
- **--reset-delete-over-count**: Remove any existing maximum number of recent backups to keep.
- **--clone-policy-max-snapshots**: The maximum number of recent snapshots (per source) that keep clones.
- **--clone-policy-zones**: The zone that this backup policy plan creates snapshot clones in.
- **--remote-region-policies**: REMOTE_REGION_POLICY_JSON|@REMOTE_REGION_POLICY_JSON, remote region policies in JSON or JSON file.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is backup-policy-jobs
{: #backup-policy-jobs-list}

List all jobs for the backup policy.

```
ibmcloud is backup-policy-jobs POLICY [--source SOURCE] [--snapshots SNAPSHOT1,SNAPSHOT2, ...] [--status failed | running | succeeded] [--plan PLAN] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-backup-policy-jobs}

- `ibmcloud is backup-policy-jobs backup-policy-1001`
- `ibmcloud is backup-policy-jobs r134-7759199b-bc1f-448e-84fa-2aa42bde29af`
- `ibmcloud is backup-policy-jobs r134-0703cdf1-48bb-4af2-9ceb-1edbe8fcb818 --volume r134-1a1e25f2-3fc3-4507-8725-e5f1d07256ea --snapshot r143-1a1e25f2-3fc3-4507-8725-e5f1d08956ea --status running --plan r136-3a3e25f2-3fc3-4507-8725-e5f1d08496ea`
- `ibmcloud is backup-policy-jobs bkp-policy-do-not-delete --snapshots r134-f1d9b974-14e5-4a2e-8e38-c023164be316,r134-b11f1540-288d-4331-97ab-f565ca15a3b8,r134-ab3147a3-715f-4017-8fed-ea3ddadeeb1d,r134-435b8414-dae2-4026-847f-a73162105e5f`
- `ibmcloud is backup-policy-jobs bkp-policy-do-not-delete --snapshots bkp-plan-do-not-delete-31addff28e2b-422b,bkp-plan-do-not-delete-f37bc1f19123-4995`
- `ibmcloud is backup-policy-jobs bkp-policy-do-not-delete --snapshots crn:v1:staging:public:is:us-south:a/efe5afc483594adaa8325e2b4d1290df::snapshot:r134-c4ea5585-0554-40db-bdc8-1ec9fb15098b,crn:v1:staging:public:is:us-south:a/efe5afc483594adaa8325e2b4d1290df::snapshot:r134-c10755ee-db71-472e-bf80-01e21229fda0`
- `ibmcloud is backup-policy-jobs bkp-policy-do-not-delete  --source r134-71757aee-5e90-40f5-bd7d-0a538c084efb`

#### Command options
{: #command-options-backup-policy-jobs}

- **POLICY**: ID or name of the backup policy.
- **--source**: ID or name of the source volume. Source name can be used only if the source exists inside the VPC.
- **--snapshots**: IDs, names, or CRNs of target snapshots. Combinations of these three types are not supported. Passing is supported by only one of these three types.
- **--status**: Status of the backup policy job. One of: **failed**, **running**, **succeeded**.
- **--plan**: ID or name of backup policy plan.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is backup-policy-job
{: #backup-policy-job-view}

View details of a backup policy job.

```
ibmcloud is backup-policy-job POLICY JOB_ID [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-backup-policy-job}

- `ibmcloud is backup-policy-job r134-7759199b-bc1f-448e-84fa-2aa42bde29af 4cf9171a-0043-4434-8727-15b53dbc374c`
- `ibmcloud is backup-policy-job backup-policy-1001 4cf9171a-0043-4434-8727-15b53dbc374c`

#### Command options
{: #command-options-backup-policy-job}

- **POLICY**: ID or name of the backup policy.
- **JOB_ID**: ID of the backup policy job.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---
