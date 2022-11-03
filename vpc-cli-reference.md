---

copyright:
  years: 2018, 2022
lastupdated: "2022-11-03"

subcollection: vpc-infrastructure-cli-plugin

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:codeblock: .codeblock}
{:pre: .pre}
{:preview: .preview}
{:beta: .beta}
{:screen: .screen}
{:tip: .tip}
{:note: .note}
{:important: .important}
{:download: .download}
{:deprecated: .deprecated}

# VPC CLI reference
{: #vpc-reference}

Use the following information as a reference of the command-line interface (CLI) commands that are available for {{site.data.keyword.vpc_full}} (VPC).
{: shortdesc}

This CLI reference is organized into the following sections:
* [Network commands](#network)
* [Compute commands](#compute-clis)
* [Regions and zones commands](#geography)
* [Storage commands](#storage)

## Prerequisites
{: #cli-ref-prereqs}

1. Install the [IBM Cloud CLI ![External link icon](../icons/launch-glyph.svg "External link icon")](/docs/cli){: new_window}.

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
{: #floating-ip}

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
ibmcloud is floating-ip-reserve FLOATING_IP_NAME (--zone ZONE_NAME | --nic TARGET_INTERFACE [--in TARGET_INSTANCE | --bm TARGET_BARE_METAL_SERVER]) [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-floating-ip-reserve}

- `ibmcloud is floating-ip-reserve my-ip --zone us-south-1`
- `ibmcloud is floating-ip-reserve my-ip --nic 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is floating-ip-reserve my-ip --nic eth0 --in my-instance`
- `ibmcloud is floating-ip-reserve my-ip --nic eth0 --bm my-bm`
- `ibmcloud is floating-ip-reserve my-ip --nic 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --output JSON`

#### Command options
{: #command-options-floating-ip-reserve}

- **FLOATING_IP_NAME**: Name of the floating IP.
- **--zone**: Name of the target zone.
- **--nic**: The ID or name of the network interface to be bound.
- **--in**: The ID or name of the instance to be bound, this ID is only required if you use the network interface name instead of ID.
- **--bm**: The ID or name of the bare metal server to be bound, this ID is only required if you use the network interface name instead of ID.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is floating-ip-update
{: #floating-ip-update}

Update a floating IP.

```
ibmcloud is floating-ip-update FLOATING_IP [--name NEW_NAME] [--nic TARGET_INTERFACE [--in TARGET_INSTANCE | --bm TARGET_BARE_METAL_SERVER]] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-floating-ip-update}

- `ibmcloud is floating-ip-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-ip`
- `ibmcloud is floating-ip-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --nic 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is floating-ip-update my-ip --nic eth0 --in my-instance`
- `ibmcloud is floating-ip-update my-ip --nic eth0 --bm my-bm`
- `ibmcloud is floating-ip-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --nic 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --output JSON`

#### Command options
{: #command-options-floating-ip-update}

- **FLOATING_IP**: ID of the floating IP.
- **--name**: New name of the floating IP.
- **--nic**: The ID or name of the network interface to be bound.
- **--in**: The ID or name of the instance to be bound, this ID is only required if you use the network interface name instead of ID.
- **--bm**: The ID or name of the bare metal server to be bound, this ID is only required if you use the network interface name instead of ID.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is floating-ips
{: #floating-ips}

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
ibmcloud is flow-log-create --bucket STORAGE_BUCKET_NAME --target TARGET_IDOrName [--target-type vpc | subnet | instance | nic] [--vpc VPC] [--in IN] [--name NAME] [--active TRUE | FALSE] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
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

#### Command options
{: #command-options-flow-log-create}

- **--bucket**: Name of COS bucket.
- **--target**: Target ID or name for flow log.
- **--target-type**: Target type for flow log. This option is only required if target is passed as name of the resource. One of: **vpc**, **subnet**, **instance**, **nic**.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--in**: ID or name of the INSTANCE. It is only required to specify the unique resource by name inside this INSTANCE.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
{: #flow-log}

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
{: #flow-logs}

List all flow logs in the region.

```
ibmcloud is flow-logs [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-flow-logs}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Load balancers
{: #lb-anchor}

The following section provides information about CLI commands for working with load balancers, listeners, and pools.

### ibmcloud is load-balancer
{: #load-balancer}

View details of a load balancer.

```
ibmcloud is load-balancer LOAD_BALANCER [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-create
{: #load-balancer-create}

Create a load balancer.

```
ibmcloud is load-balancer-create LOAD_BALANCER_NAME LOAD_BALANCER_ACCESS_TYPE (--subnet SUBNET1 --subnet SUBNET2 ... [--vpc VPC]) [--family application | network] [--route-mode false | true] [--sg SG] [--logging-datapath-active false | true] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
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
- `ibmcloud is load-balancer-create my-lb private --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --family network --route-mode true`
Create a load balancer with route mode enabled

#### Command options
{: #command-options-load-balancer-create}

- **LOAD_BALANCER_NAME**: Name of the load balancer.
- **LOAD_BALANCER_ACCESS_TYPE**: Access type of the load balancer. One of: **public**, **private**.
- **--subnet**: ID or name of the subnets to provision this load balancer. This option can be specified multiple times to provision load balancer in multiple subnets. Only one subnet can be specified for network load balancer.
- **--vpc**: ID or name of the VPC. This ID or name is only required to specify the unique subnet by name inside this VPC.
- **--family**: The load balancer family type. One of: **application**, **network**.
- **--route-mode**: Enable or disable route mode for the load balancer. If unspecified, route mode is disabled. Currently, route mode can be enabled for only private network load balancer. One of: **false**, **true**.
- **--sg**: Comma-separated security group IDs or names for the load balancer. If unspecified, the VPC's default security group is used.
- **--logging-datapath-active**: Enable or disable datapath logging for this load balancer. If unspecified, datapath logging is disabled. Datapath logging is applicable only for application load balancer. One of: **false**, **true**.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener
{: #load-balancer-listener}

View details of a load balancer listener.

```
ibmcloud is load-balancer-listener LOAD_BALANCER LISTENER_ID [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-create
{: #load-balancer-listener-create}

Create a load balancer listener.

```
ibmcloud is load-balancer-listener-create LOAD_BALANCER (--protocol http | https | tcp | udp) [--vpc VPC] [--port PORT | --port-min PORT_MIN --port-max PORT_MAX] [--default-pool DEFAULT_POOL_ID] [--connection-limit LIMIT] [--certificate-instance-crn CERTIFICATE_INSTANCE_CRN] [--policies LISTENER_POLICIES_JSON | @LISTENER_POLICIES_JSON_FILE] [--accept-proxy-protocol false | true] [--http-redirect-listener-id HTTP_REDIRECT_LISTENER_ID --http-redirect-status-code 301 | 302 | 303 | 307 | 308 [--http-redirect-target-uri HTTP_REDIRECT_TARGET_URI]] [--output JSON] [-q, --quiet]
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
Create a load balancer listener with udp protocol.

#### Command options
{: #command-options-load-balancer-listener-create}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--protocol**: The listener protocol. Load balancers in the application family support tcp, http, and https. Load balancers in the network family support tcp and udp.
- **--port**: The listener port number. Range 1-65535.
- **--port-min**: The inclusive lower bound of the range of ports that are used by this listener. Must not be greater than _port_max_. Currently, only load balancers that are operating with route mode enabled and public load balancers in the _network_ family support more than one port per listener. Listeners in the load balancer with the same _protocol_ must have nonoverlapping port ranges. Range 1-65535.
- **--port-max**: The inclusive higher bound of the range of ports that are used by this listener. Must not be less than _port_min_. Currently, only load balancers that are operating with route mode enabled and public load balancers in the _network_ family support more than one port per listener. Listeners in the load balancer with the same _protocol_ must have nonoverlapping port ranges. Range 1-65535.
- **--default-pool**: ID of the default pool.
- **--connection-limit**: The maximum number of connections of the listener. This option is not applicable for the load balancers in the network family.
- **--certificate-instance-crn**: The certificate instance CRN used for SSL termination. Required when protocol is **https**. Migrate your load balancer certificates from Certificate Manager to Secrets Manager because the certificate CRN from Certificate Manager is deprecated. This option is not applicable for the load balancers in the network family.
- **--policies**: **LISTENER_POLICIES_JSON** | **@LISTENER_POLICIES_JSON_FILE**, listener policies in JSON or JSON file. This option is not applicable for the load balancers in the network family.
- **--accept-proxy-protocol**: If set to true, proxy protocol is enabled for this listener. Only supported for application load balancers. One of: **false**, **true**.
- **--http-redirect-listener-id**: ID of the listener that is set as the HTTP redirect target.
- **--http-redirect-status-code**: The HTTP status code that is returned in the redirect response. One of: **301**, **302**, **303**, **307**, **308**.
- **--http-redirect-target-uri**: Target URI where traffic is redirected. This setting is optional and must start with "/" if you set.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policies
{: #load-balancer-listener-policies}

List all load balancer policies.

```
ibmcloud is load-balancer-listener-policies LOAD_BALANCER LISTENER_ID [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener-policies}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy
{: #load-balancer-listener-policy}

View details of load balancer listener policy.

```
ibmcloud is load-balancer-listener-policy LOAD_BALANCER LISTENER_ID POLICY [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener-policy}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY**: ID or name of the policy.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-create
{: #load-balancer-listener-policy-create}

Create a load balancer listener policy.

```
ibmcloud is load-balancer-listener-policy-create LOAD_BALANCER LISTENER_ID --priority PRIORITY (--action forward | redirect | reject | https_redirect) [--vpc VPC] [--name NEW_NAME] [(--target-listener-id TARGET_LISTENER_ID --target-listener-http-status-code 301 | 302 | 303 | 307 | 308 [--target-uri TARGET_URI]) | (--target-http-status-code 301 | 302 | 303 | 307 | 308 --target-url TARGET_URL) | --target TARGET] [--rules LISTENER_POLICY_RULES_JSON | @LISTENER_POLICY_RULES_JSON_FILE] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-listener-policy-create}

- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-policy --action reject --priority 5`
The priority of the policy can have a range of 1 to 10, where a lower value indicates a higher priority. The possible values for _action_ are "forward", "redirect", or "reject".
- `ibmcloud is load-balancer-listener-policy-create my-lb 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-policy --action reject --priority 5`
The priority of the policy can have a range of 1 to 10, where a lower value indicates a higher priority. The possible values for _action_ are "forward", "redirect", or "reject".
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action forward --priority 2 --target 70294e14-4e61-11e8-bcf4-0242ac110004`
When the action is _forward_, the pool ID or name is required to specify which pool the load balancer forwards the traffic to.
- `ibmcloud is load-balancer-listener-policy-create my-lb 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action forward --priority 2 --target my-pool`
When the action is _forward_, the pool ID or name is required to specify which pool the load balancer forwards the traffic to.
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action redirect --priority 1 --target-http-status-code 301 --target-url "https://www.redirect.com"`
When the action is _redirect_, the "url" and "http_status_code" are required. Possible values for _http_status_code_ are "301", "302", "303", "307", or "308". The "url" is the redirect target URL.
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action reject --priority 4 --rules '[{"rules": { "condition": "equals", "type": "header", "field": "My-app-header", "value": "value"}}]'`
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--priority**: Priority of the policy. Lower value indicates higher priority, for example: **5**, range: [**1-10**].
- **--action**: The policy action. One of: **forward**, **redirect**, **reject**, **https_redirect**.
- **--name**: The new name of the policy.
- **--target**: ID or name of the target load balancer pool that is specified with **forward** action.
- **--target-listener-id**: ID of the listener that you want to implement https-redirect on, specified with **https_redirect** action.
- **--target-listener-http-status-code**: The HTTP status code that is returned in the redirect response, specified with **https_redirect** action. One of: **301**, **302**, **303**, **307**, **308**.
- **--target-uri**: Target URI where traffic is redirected, specified with **https_redirect** action. This setting is optional and must start with "/" if you set.
- **--target-http-status-code**: The HTTP status code in the redirect response, specified with **redirect** action. One of: **301**, **302**, **303**, **307**, **308**.
- **--target-url**: The redirect target URL, specified with **redirect** action. This setting is optional and must start with "/" if you set this option.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-rule
{: #load-balancer-listener-policy-rule}

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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-rule-create
{: #load-balancer-listener-policy-rule-create}

Create a load balancer listener policy rule.

```
ibmcloud is load-balancer-listener-policy-rule-create LOAD_BALANCER LISTENER_ID POLICY (--condition contains | equals | matches_regex) (--type header | hostname | path | query | body) --value VALUE [--vpc VPC] [--field FIELD] [--output JSON] [-q, --quiet]
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--condition**: The condition of the rule. One of: **contains**, **equals**, **matches_regex**.
- **--type**: The type of the rule. One of: **header**, **hostname**, **path**, **query**, **body**.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-rule-update
{: #load-balancer-listener-policy-rule-update}

Update a rule of a load balancer listener policy.

```
ibmcloud is load-balancer-listener-policy-rule-update LOAD_BALANCER LISTENER_ID POLICY RULE_ID [--vpc VPC] [--condition contains | equals | matches_regex] [--type header | hostname | path | query | body] [--value VALUE] [--field FIELD] [--output JSON] [-q, --quiet]
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--condition**: The condition of the rule. One of: **contains**, **equals**, **matches_regex**.
- **--type**: The type of the rule. One of: **header**, **hostname**, **path**, **query**, **body**.
- **--value**: Value to match the rule condition.
- **--field**: The HTTP field. This field is applicable to "header", "query", and "body" rule types. For rule type "header", this field is required. For rule types "query" or "body", this field is optional.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-rules
{: #load-balancer-listener-policy-rules}

List all load balancer policy rules.

```
ibmcloud is load-balancer-listener-policy-rules LOAD_BALANCER LISTENER_ID POLICY [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener-policy-rules}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY**: ID or name of the policy.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- `ibmcloud is load-balancer-listener-policy-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --name my-policy --output JSON`
- `ibmcloud is lb-lpu f5b20e9b-a77b-43e9-aa2d-a3a5ac9fe8fd 5cb08c12-004f-4587-87f4-ef46e799da50 c7d2c434-9202-48aa-837b-0661c4299c28 --name demo-policy --priority 2 --target-listener-id d7e0543c-4e0f-4c0d-89aa-73f0f028ec61 --target-listener-http-status-code 301`
- `ibmcloud is lb-lpu my-lb 5cb08c12-004f-4587-87f4-ef46e799da50 my-lblp --name demo-policy --priority 2 --target-listener-id d7e0543c-4e0f-4c0d-89aa-73f0f028ec61 --target-listener-http-status-code 301`
- `ibmcloud is lb-lpu f5b20e9b-a77b-43e9-aa2d-a3a5ac9fe8fd 5cb08c12-004f-4587-87f4-ef46e799da50 c7d2c434-9202-48aa-837b-0661c4299c28 --priority 2 --target-listener-id d7e0543c-4e0f-4c0d-89aa-73f0f028ec61 --target-listener-http-status-code 301 --target-uri /example2`

#### Command options
{: #command-options-load-balancer-listener-policy-update}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY**: ID or name of the policy.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--name**: The user-defined name for this policy. Policy names must be unique within the load balancer listener.
- **--priority**: Priority of the policy. Lower value indicates higher priority, for example: **5**, range: [**1-10**].
- **--target**: ID or name of the target load balancer pool that is specified with **forward** action.
- **--target-http-status-code**: The HTTP status code in the redirect response, specified with **redirect** action. One of: **301**, **302**, **303**, **307**, **308**.
- **--target-url**: The redirect target URL, specified with **redirect** action. This setting is optional and must start with "/" if you set this option.
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
ibmcloud is load-balancer-listener-update LOAD_BALANCER LISTENER_ID [--vpc VPC] [--protocol http | https | tcp | udp] [--port PORT | --port-min PORT_MIN --port-max PORT_MAX] [--default-pool DEFAULT_POOL_ID | --reset-default-pool] [--connection-limit LIMIT] [--certificate-instance-crn CERTIFICATE_INSTANCE_CRN] [--accept-proxy-protocol false | true] [--disable-http-redirect | (--http-redirect-listener-id HTTP_REDIRECT_LISTENER_ID --http-redirect-status-code 301 | 302 | 303 | 307 | 308 [--http-redirect-target-uri HTTP_REDIRECT_TARGET_URI | --reset-http-redirect-target-uri])] [--output JSON] [-q, --quiet]
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

#### Command options
{: #command-options-load-balancer-listener-update}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--protocol**: The listener protocol. Load balancers in the application family support tcp, http, and https. Load balancers in the network family support tcp and udp.
- **--port**: The listener port number. Range 1-65535.
- **--port-min**: The inclusive lower bound of the range of ports that are used by this listener. Must not be greater than _port_max_. Currently, only load balancers that are operating with route mode enabled and public load balancers in the _network_ family support more than one port per listener. Listeners in the load balancer with the same _protocol_ must have nonoverlapping port ranges. Range 1-65535.
- **--port-max**: The inclusive higher bound of the range of ports that are used by this listener. Must not be less than _port_min_. Currently, only load balancers that are operating with route mode enabled and public load balancers in the _network_ family support more than one port per listener. Listeners in the load balancer with the same _protocol_ must have nonoverlapping port ranges. Range 1-65535.
- **--default-pool**: ID of the default pool.
- **--reset-default-pool**: Reset default pool.
- **--connection-limit**: The maximum number of connections of the listener. This option is not applicable for the load balancers in the network family.
- **--certificate-instance-crn**: The certificate instance CRN used for SSL termination. Required when protocol is **https**. Migrate your load balancer certificates from Certificate Manager to Secrets Manager because the certificate CRN from Certificate Manager is deprecated. This option is not applicable for the load balancers in the network family.
- **--accept-proxy-protocol**: If set to true, proxy protocol is enabled for this listener. Only supported for application load balancers. One of: **false**, **true**.
- **--disable-http-redirect**: Enable or disable an HTTP redirect on a listener.
- **--http-redirect-listener-id**: ID of the listener that is set as the HTTP redirect target.
- **--http-redirect-status-code**: The HTTP status code that is returned in the redirect response. One of: **301**, **302**, **303**, **307**, **308**.
- **--http-redirect-target-uri**: Target URI where traffic is redirected. This setting is optional and must start with "/" if you set.
- **--reset-http-redirect-target-uri**: Reset Target URI.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listeners
{: #load-balancer-listeners}

List all load balancer listeners.

```
ibmcloud is load-balancer-listeners LOAD_BALANCER [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listeners}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool
{: #load-balancer-pool}

View details of a load balancer pool.

```
ibmcloud is load-balancer-pool LOAD_BALANCER POOL [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-pool}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **POOL**: ID or name of the pool.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-create
{: #load-balancer-pool-create}

Create a load balancer pool.

```
ibmcloud is load-balancer-pool-create POOL_NAME LOAD_BALANCER ALGORITHM PROTOCOL HEALTH_DELAY HEALTH_RETRIES HEALTH_TIMEOUT HEALTH_TYPE (--members MEMBERS_JSON | @MEMBERS_JSON_FILE) [--vpc VPC] [--health-monitor-url URL] [--health-monitor-port PORT] [--session-persistence-type source_ip | http_cookie | app_cookie [--session-persistence-cookie-name SESSION_PERSISTENCE_COOKIE_NAME]] [--proxy-protocol disabled | v1 | v2] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-pool-create}

- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http`
- `ibmcloud is load-balancer-pool-create my-pool my-lb round_robin http 20 2 5 http`
- `ibmcloud is load-balancer-pool-create my-pool my-lb round_robin http 20 2 5 http --vpc my-vpc`
- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --health-monitor-url / --health-monitor-port 4001`
- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --session-persistence-type source_ip --output JSON`
- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --members '[{"port": 80, "target": { "address": "10.10.1.4"}, "weight": 20 }, {"port": 80, "target": { "address": "10.240.0.6"}, "weight": 30 }]'`
Create application load balancer pool with members
- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin tcp 20 2 5 http --members '[{"port": 80, "target": { "id": "0736_63b9233c-812e-4d65-9ee3-fa61172afa37"}, "weight": 20 }, {"port": 80, "target": { "id": "0716_4b30a833-6f10-46a9-a4b8-13871f3559b8"}, "weight": 30 }]'`
Create network load balancer pool with members
- `ibmcloud is load-balancer-pool-create my-pool2 my-nlb round_robin tcp 20 2 5 http --members '[{"port": 80, "target": { "name": "my-instance"}}, {"port": 80, "target": { "name": "my-instance2"}}]'`
Create network load balancer pool with members and supply the member target by name.
- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --proxy-protocol v1`
- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --session-persistence-type app_cookie --session-persistence-cookie-name my-cookie-name`
- `ibmcloud is load-balancer-pool-create my-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin udp 20 2 5 http`
Create network load balancer pool for the network load balancer listener with udp protocol.

#### Command options
{: #command-options-load-balancer-pool-create}

- **POOL_NAME**: Name of the pool.
- **LOAD_BALANCER**: ID or name of the load balancer.
- **ALGORITHM**: The load balancing algorithm. One of: **round_robin**, **weighted_round_robin**, **least_connections**.
- **PROTOCOL**: The pool protocol. Load balancers in the application family support **tcp**, **http**, **https**. Load balancers in the network family support **tcp**, **udp**.
- **HEALTH_DELAY**: The health check interval in seconds. The interval must be greater than the timeout value. Minimum: **2**, maximum: **60**.
- **HEALTH_RETRIES**: The health check maximum retries. Minimum: **1**, maximum: **10**.
- **HEALTH_TIMEOUT**: The health check timeout in seconds. Minimum: **1**, maximum: **59**.
- **HEALTH_TYPE**: The health check protocol. Load balancers in the application family support **tcp**, **http**, and **https**. Load balancers in the network family support **tcp** and **http**.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--health-monitor-url**: The health check URL path. Applicable only if the **HEALTH_TYPE** is http or https.
- **--health-monitor-port**: The health check port number. If specified, the specified ports in the server member resources are overridden.
- **--session-persistence-type**: The session persistence type. One of: **source_ip**, **http_cookie**, **app_cookie**.
- **--session-persistence-cookie-name**: Session persistence cookie name. This option is applicable only to **app_cookie** type.
- **--proxy-protocol**: The proxy protocol setting for this pool. Proxy protocol is supported only for application load balancers. One of: **disabled**, **v1**, **v2**.
- **--members**: MEMBERS_JSON|@MEMBERS_JSON_FILE, members in JSON or JSON file.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-member
{: #load-balancer-pool-member}

View details of load balancer pool member.

```
ibmcloud is load-balancer-pool-member LOAD_BALANCER POOL MEMBER_ID [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-pool-member}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **POOL**: ID or name of the pool.
- **MEMBER_ID**: ID of the member.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-member-create
{: #load-balancer-pool-member-create}

Create a load balancer pool member.

```
ibmcloud is load-balancer-pool-member-create LOAD_BALANCER POOL PORT TARGET [--vpc VPC] [--weight WEIGHT] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-pool-member-create}

- `ibmcloud is load-balancer-pool-member-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 3000 192.168.100.5`
- `ibmcloud is load-balancer-pool-member-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 3000 9e692608-3b3a-4cfb-9f46-efb6b711876d`
- `ibmcloud is load-balancer-pool-member-create my-nlb my-pool 3000 my-instance`
- `ibmcloud is load-balancer-pool-member-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 3000 192.168.100.5 --weight 100 --output JSON`

#### Command options
{: #command-options-load-balancer-pool-member-create}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **POOL**: ID or name of the pool.
- **PORT**: The port that the member receives load balancer traffic on. Applies only to load balancer traffic that is received on a listener with a single port. If the traffic is received on a listener with a port range, the member receives the traffic on the same port that the listener received it on. This port can also be used for health checks unless the **port** property of **health_monitor** property is specified.
- **TARGET**: The IP address of the pool member for load balancers in the application family, or the instance ID or name of the pool member for load balancers in the network family.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--weight**: Weight of the server member. This option is applicable only when the load balancer algorithm of its pool is **weighted_round_robin**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-member-update
{: #load-balancer-pool-member-update}

Update a member of a load balancer pool.

```
ibmcloud is load-balancer-pool-member-update LOAD_BALANCER POOL MEMBER_ID [--vpc VPC] [--target-address TARGET_ADDRESS | --target TARGET] [--port PORT] [--weight WEIGHT] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-pool-member-update}

- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target 192.168.100.5 --port 3001`
- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target 9e692608-3b3a-4cfb-9f46-efb6b711876d --port 3001`
- `ibmcloud is load-balancer-pool-member-update my-nlb my-pool 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target my-instance --port 3001`
- `ibmcloud is load-balancer-pool-member-update my-nlb my-pool 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --vpc my-vpc --target my-instance --port 3001`
- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target-address 192.168.100.5 --port 3001`
- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target-address 192.168.100.5 --port 3001 --weight 100 --output JSON`

#### Command options
{: #command-options-load-balancer-pool-member-update}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **POOL**: ID or name of the pool.
- **MEMBER_ID**: ID of the member.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--target-address**: The IP address of the pool member.
- **--target**: The IP address of the pool member for load balancers in the application family, or the instance ID or name of the pool member for load balancers in the network family.
- **--port**: The port that the member receives load balancer traffic on. Applies only to load balancer traffic that is received on a listener with a single port. If the traffic is received on a listener with a port range, the member receives the traffic on the same port that the listener received it on. This port can also be used for health checks unless the **port** property of **health_monitor** property is specified.
- **--weight**: Weight of the server member. This option is applicable only when the load balancer algorithm of its pool is **weighted_round_robin**.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-members
{: #load-balancer-pool-members}

List all the members of a load balancer pool.

```
ibmcloud is load-balancer-pool-members LOAD_BALANCER POOL [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-pool-members}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **POOL**: ID or name of the pool.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-update
{: #load-balancer-pool-update}

Update a pool of a load balancer.

```
ibmcloud is load-balancer-pool-update LOAD_BALANCER POOL [--vpc VPC] [--algorithm round_robin | weighted_round_robin | least_connections] [--health-delay DELAY] [--health-max-retries RETRIES] [--health-timeout TIMEOUT] [--health-type https | http | tcp] [--health-monitor-url URL] [--health-monitor-port PORT | --reset-health-monitor-port] [--protocol https | http | tcp | udp] [[--session-persistence-type source_ip | http_cookie | app_cookie | none] | [--session-persistence-cookie-name SESSION_PERSISTENCE_COOKIE_NAME]] [--proxy-protocol disabled | v1 | v2] [--name NEW_NAME] [--output JSON] [-q, --quiet]
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

#### Command options
{: #command-options-load-balancer-pool-update}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **POOL**: ID or name of the pool.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--algorithm**: The load balancing algorithm. One of: **round_robin**, **weighted_round_robin**, **least_connections**.
- **--health-delay**: The health check interval in seconds. The interval must be greater than the timeout value. Minimum: **2**, maximum: **60**.
- **--health-max-retries**: The health check maximum retries. Minimum: **1**, maximum: **10**.
- **--health-timeout**: The health check timeout in seconds. Minimum: **1**, maximum: **59**.
- **--health-type**: The health check protocol. Load balancers in the application family support **tcp**, **http**, and **https**. Load balancers in the network family support **tcp** and **http**.
- **--health-monitor-url**: The health check URL path. Applicable only if the **HEALTH_TYPE** is http or https.
- **--health-monitor-port**: The health check port number. If specified, the specified ports in the server member resources are overridden.
- **--reset-health-monitor-port**: Reset health monitor port.
- **--protocol**: The pool protocol. Load balancers in the application family support **tcp**, **http**, **https**. Load balancers in the network family support **tcp**, **udp**.
- **--session-persistence-type**: The session persistence type. One of: **source_ip**, **http_cookie**, **app_cookie**, **none**.
- **--session-persistence-cookie-name**: Session persistence cookie name. This option is applicable only to **app_cookie** type.
- **--proxy-protocol**: The proxy protocol setting for this pool. Proxy protocol is supported only for application load balancers. One of: **disabled**, **v1**, **v2**.
- **--name**: The new name of the pool.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pools
{: #load-balancer-pools}

List all pools of a load balancer.

```
ibmcloud is load-balancer-pools LOAD_BALANCER [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-pools}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-statistics
{: #load-balancer-statistics}

List all statistics of a load balancer.

```
ibmcloud is load-balancer-statistics LOAD_BALANCER [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-statistics}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-update
{: #load-balancer-update}

Update a load balancer.

```
ibmcloud is load-balancer-update LOAD_BALANCER --subnets SUBNETS [--vpc VPC] [--name NEW_NAME] [--logging-datapath-active false | true] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-update}

- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-renamed-lb`
- `ibmcloud is load-balancer-update my-lb --name my-renamed-lb`
- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-renamed-lb --output JSON`
- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --logging-datapath-active false`
- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnets ec8bb350-d802-4f1b-b362-b848abd5bb65,ec8bb350-d802-4f1b-b362-b848abd5bb66`

#### Command options
{: #command-options-load-balancer-update}

- **LOAD_BALANCER**: ID or name of the load balancer.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--name**: New name of the Load balancer.
- **--logging-datapath-active**: Enable or disable datapath logging for this load balancer. Datapath logging is applicable only for application load balancer. One of: **false**, **true**.
- **--subnets**: Comma-separated ID or name of the subnets to provision this load balancer. Load balancer availability depends on the availability of the zones that the specified subnets reside in. Currently, only the load balancer in the application family supports this option.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancers
{: #load-balancers}

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
{: #ibmcloud-is-network-acls}

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
{: #network-acl}

View details of a network ACL.

```
ibmcloud is network-acl ACL [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-acl}

- **ACL**: ID or name of the network ACL.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl-rules
{: #network-acl-rules}

List all rules of a network ACL.

```
ibmcloud is network-acl-rules ACL [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-acl-rules}

- **ACL**: ID or name of the network ACL.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl-rule
{: #network-acl-rule}

View details of a network ACL rule.

```
ibmcloud is network-acl-rule ACL RULE [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-acl-rule}

- **ACL**: ID or name of the network ACL.
- **RULE**: ID or name of the rule.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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

- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound all 10.2.2.2 10.2.2.3`
- `ibmcloud is network-acl-rule-add my-acl allow inbound all 10.2.2.2 10.2.2.3`
- `ibmcloud is network-acl-rule-add my-acl allow inbound all 10.2.2.2 10.2.2.3 --vpc my-vpc`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound all 10.2.2.2 10.2.2.3 --name my-acl-rule`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound icmp 10.2.2.2 10.2.2.3 --icmp-type 8 --icmp-code 0`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound tcp 10.2.2.2 10.2.2.3 --source-port-min 555  --source-port-max 666 --destination-port-min 11 --destination-port-max 55`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound all 10.2.2.2 10.2.2.3 --before-rule-id 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound all 10.2.2.2 10.2.2.3 --output JSON`

#### Command options
{: #command-options-network-acl-rule-add}

- **ACL**: ID or name of the network ACL.
- **ACTION**: One of: **allow**, **deny**.
- **DIRECTION**: Direction of traffic to enforce. One of: **inbound**, **outbound**.
- **PROTOCOL**: Protocol to enforce. One of: **all**, **icmp**, **tcp**, **udp**.
- **SOURCE**: Source IP address or CIDR block.
- **DESTINATION**: Destination IP address or CIDR block.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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

- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol all --source 10.2.2.2 --dest 10.2.2.3`
- `ibmcloud is network-acl-rule-update my-acl my-acl-rule --action allow --direction inbound --protocol all --source 10.2.2.2 --dest 10.2.2.3`
- `ibmcloud is network-acl-rule-update my-acl my-acl-rule --vpc my-vpc --name my-acl-renamed-rule`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol all --source 10.2.2.2 --dest 10.2.2.3 --name my-acl`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol icmp --source 10.2.2.2 --dest 10.2.2.3 --icmp-type 8 --icmp-code 0`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol tcp --source 10.2.2.2 --dest 10.2.2.3 --source-port-min 555 --source-port-max 666 --destination-port-min 11 --destination-port-max 55`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol all --source 10.2.2.2 --dest 10.2.2.3 --before-rule-id 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol all --source 10.2.2.2 --dest 10.2.2.3 --output JSON`

#### Command options
{: #command-options-network-acl-rule-update}

- **ACL**: ID or name of the network ACL.
- **RULE**: ID or name of the rule.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

## Public gateways
{: #public-gateways}

### ibmcloud is public-gateway
{: #public-gateway}

View details of a public gateway.

```
ibmcloud is public-gateway GATEWAY [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-public-gateway}

- **GATEWAY**: ID or name of the public gateway.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--name**: New name of the public gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is public-gateways
{: #ibmcloud-is-public-gateways}

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
{: #vpc-default-routing-table}

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
{: #vpc-routing-tables}

List all routing tables for a VPC.

```
ibmcloud is vpc-routing-tables VPC [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-routing-tables}

- **VPC**: ID or name of the VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-table
{: #vpc-routing-table}

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
ibmcloud is vpc-routing-table-create VPC [--name NAME] [--direct-link-ingress false | true] [--transit-gateway-ingress false | true] [--vpc-zone-ingress false | true] [--accept-routes-from-resource-type-filters, --ar-rtf vpn_server | vpn_gateway] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpc-routing-table-create}

- `ibmcloud is vpc-routing-table-create 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-vpc-routing-table --output JSON`
- `ibmcloud is vpc-routing-table-create my-vpc --name my-vpc-routing-table --output JSON`
- `ibmcloud is vpc-routing-table-create my-vpc --name my-vpc-routing-table --accept-routes-from-resource-type-filters vpn_server,vpn_gateway`
Create a routing table with resource type filter.

#### Command options
{: #command-options-vpc-routing-table-create}

- **VPC**: ID or name of the VPC.
- **--name**: Name of the VPC routing table.
- **--direct-link-ingress, --direct-link**: If set to "true", this routing table is used to route traffic that originates from Direct Link to this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--transit-gateway-ingress, --transit-gateway**: If set to "true", this routing table is used to route traffic that originates from Transit Gateway to this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--vpc-zone-ingress, --vpc-zone**: If set to "true", this routing table is used to route traffic that originates from subnets in other zones in this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--accept-routes-from-resource-type-filters, --ar-rtf**: The comma-separated resource type filters that can create routes in this routing table. One of: **vpn_server**, **vpn_gateway**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-table-update
{: #vpc-routing-table-update}

Update a VPC routing table.

```
ibmcloud is vpc-routing-table-update VPC ROUTING_TABLE [--name NEW_NAME] [--direct-link-ingress false | true] [--transit-gateway-ingress false | true] [--vpc-zone-ingress false | true] [--accept-routes-from-resource-type-filters, --ar-rtf vpn_server | vpn_gateway | --clean-all-accept-routes-from-filters, --cl-arf] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpc-routing-table-update}

- `ibmcloud is vpc-routing-table-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1d456 --name my-renamed-vpc-routing-table --output JSON`
- `ibmcloud is vpc-routing-table-update my-vpc my-vpc-routing-table --name my-renamed-vpc-routing-table --output JSON`

#### Command options
{: #command-options-vpc-routing-table-update}

- **VPC**: ID or name of the VPC.
- **ROUTING_TABLE**: ID or name of the VPC routing table.
- **--name**: New name of the routing table.
- **--direct-link-ingress, --direct-link**: If set to "true", this routing table is used to route traffic that originates from Direct Link to this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--transit-gateway-ingress, --transit-gateway**: If set to "true", this routing table is used to route traffic that originates from Transit Gateway to this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--vpc-zone-ingress, --vpc-zone**: If set to "true", this routing table is used to route traffic that originates from subnets in other zones in this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--accept-routes-from-resource-type-filters, --ar-rtf**: The comma-separated resource type filters that can create routes in this routing table. All learned routes from resources that match a resource filter are removed when an existing resource filter is removed. One of: **vpn_server**, **vpn_gateway**.
- **--clean-all-accept-routes-from-filters, --cl-arf**: Remove all accept routes from filters and delete all learned routes from the routing table.
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
{: #vpc-routing-table-routes}

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
{: #vpc-routing-table-route}

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
ibmcloud is vpc-routing-table-route-create VPC ROUTING_TABLE --zone ZONE_NAME --destination DESTINATION_CIDR [--action delegate_vpc | delegate | deliver | drop] [--next-hop NEXT_HOP [--vpngw VPNGW]] [--name NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpc-routing-table-route-create}

- `ibmcloud is vpc-routing-table-route-create 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1d456 --name my-vpc-route --action deliver --zone us-south-1 --destination  10.2.2.0/24 --next-hop 10.0.0.2 --output JSON`
- `ibmcloud is vpc-routing-table-route-create my-vpc my-routing-table --name my-vpc-route --action deliver --zone us-south-1 --destination  10.2.2.0/24 --next-hop 10.0.0.2 --output JSON`
- `ibmcloud is vpc-routing-table-route-create 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1d456 --name my-vpc-route --action delegate --zone us-south-1 --destination  10.2.2.0/24 --output JSON`
- `ibmcloud is vpc-routing-table-route-create 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1d456 --name my-vpc-route --action drop --zone us-south-1 --destination  10.2.2.0/24 --output JSON`

#### Command options
{: #command-options-vpc-routing-table-route-create}

- **VPC**: ID or name of the VPC.
- **ROUTING_TABLE**: ID or name of the VPC routing table.
- **--zone**: Name of the zone.
- **--action**: The action to perform with a packet that matches the route. One of: **delegate_vpc**, **delegate**, **deliver**, **drop**.
- **--destination**: The destination CIDR of the route. At most, two routes per zone in a table can have the same destination, and only if both routes have an action of **deliver**.
- **--next-hop**: If the action is **deliver**, then the IP address, VPN connection ID, or name of the next-hop that packets are delivered to. For other action values, it must be omitted or specified as 0.0.0.0.
- **--vpngw**: ID or name of the VPN gateway. This option is required only if the next-hop is specified as VPN connection in name format.
- **--name**: Name of the VPC routing table.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-table-route-update
{: #vpc-routing-table-route-update}

Update a VPC route.

```
ibmcloud is vpc-routing-table-route-update VPC ROUTING_TABLE ROUTE --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-vpc-routing-table-route-update}

- `ibmcloud is vpc-routing-table-route-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1d456 72b27b5c-f4b0-48bb-b954-5becc7c1d4ef --name my-vpc-route --output JSON`

#### Command options
{: #command-options-vpc-routing-table-route-update}

- **VPC**: ID or name of the VPC.
- **ROUTING_TABLE**: ID or name of the VPC routing table.
- **ROUTE**: ID or name of the VPC route.
- **--name**: New name of the route.
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
{: #subnet-routing-table}

View details of routing table that is attached to the subnet.

```
ibmcloud is subnet-routing-table SUBNET [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnet-routing-table}

- **SUBNET**: ID or name of the subnet.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Security groups
{: #security-groups-cli-ref}

### ibmcloud is security-group
{: #security-group}

View details of a security group.

```
ibmcloud is security-group GROUP [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-security-group}

- **GROUP**: ID or name of the security group.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-rule
{: #security-group-rule}

View details of a security group rule.

```
ibmcloud is security-group-rule GROUP RULE_ID [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-security-group-rule}

- **GROUP**: ID or name of the security group.
- **RULE_ID**: ID of the security group rule.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-rule-add
{: #security-group-rule-add}

Add a rule to a security group.

```
ibmcloud is security-group-rule-add GROUP DIRECTION PROTOCOL [--vpc VPC] [--remote REMOTE_ADDRESS | CIDR_BLOCK | SECURITY_GROUP] [--icmp-type ICMP_TYPE [--icmp-code ICMP_CODE]] [--port-min PORT_MIN] [--port-max PORT_MAX] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-security-group-rule-add}

- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound all`
- `ibmcloud is security-group-rule-add my-sg inbound all`
- `ibmcloud is security-group-rule-add my-sg inbound all --vpc my-vpc`
- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound icmp --icmp-type 8 --icmp-code 0`
- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound all --remote 12.2.2.3`
- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound all --remote 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is security-group-rule-add my-sg inbound all --remote my-sg`
- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound tcp --port-min 4 --port-max 22 --output JSON`

#### Command options
{: #command-options-security-group-rule-add}

- **GROUP**: ID or name of the security group.
- **DIRECTION**: Direction of traffic to enforce. One of: **inbound**, **outbound**.
- **PROTOCOL**: Protocol to enforce. One of: **all**, **icmp**, **tcp**, **udp**.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-rule-update
{: #security-group-rule-update}

Update a rule of a security group.

```
ibmcloud is security-group-rule-update GROUP RULE_ID [--vpc VPC] [--direction inbound | outbound] [--remote REMOTE_ADDRESS | CIDR_BLOCK | SECURITY_GROUP] [--icmp-type ICMP_TYPE | --reset-icmp-type] [--icmp-code ICMP_CODE | --reset-icmp-code] [--port-min PORT_MIN | --reset-port-min] [--port-max PORT_MAX | --reset-port-max] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-security-group-rule-update}

- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound`
- `ibmcloud is security-group-rule-update my-sg 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --icmp-type 8 --icmp-code 0`
- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --port-min 4 --port-max 22`
- `ibmcloud is security-group-rule-update my-sg 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --remote 12.2.2.3`
- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --reset-icmp-code --reset-icmp-type`
- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --output JSON`

#### Command options
{: #command-options-security-group-rule-update}

- **GROUP**: ID or name of the security group.
- **RULE_ID**: ID of the security group rule.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--direction**: Direction of traffic to enforce. One of: **inbound**, **outbound**.
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
{: #security-group-rules}

List all rules of a security group.

```
ibmcloud is security-group-rules GROUP [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-security-group-rules}

- **GROUP**: ID or name of the security group.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--name**: New name of the security group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-groups
{: #security-groups}

List all security groups.

```
ibmcloud is security-groups [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-security-groups}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-target
{: #security-group-target}

View details of a target of a security group.

```
ibmcloud is security-group-target GROUP TARGET [--vpc VPC] [(--trt load_balancer | endpoint_gateway | vpn_server) | --in INSTANCE | --bm BARE_METAL_SERVER] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-security-group-target}

- `ibmcloud is security-group-target 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9`
- `ibmcloud is security-group-target my-sg my-nic --in my-in`
- `ibmcloud is security-group-target my-sg my-nic --bm my-bm`
- `ibmcloud is security-group-target my-sg my-lb --trt load_balancer`
- `ibmcloud is security-group-target my-sg my-ege --trt endpoint_gateway`
- `ibmcloud is sg-t sg-qui-us-east vpn-server-1 --trt vpn_server --vpc vpc_per_region_us-east`

#### Command options
{: #command-options-security-group-target}

- **GROUP**: ID or name of the security group.
- **TARGET**: ID or name of the bound target resource for security group. The following types are supported target resource types: _network_interface_, _load_balancer_, _endpoint_gateway_, _vpn_server_.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--trt**: The bound target resource type, this option is only required if you use the target name instead of ID. One of: **load_balancer**, **endpoint_gateway**, **vpn_server**.
- **--in**: The ID or name of the instance to be bound. It is only required if you use the network interface name instead of ID.
- **--bm**: The ID or name of the bare metal server to be bound. It is only required if the network interface name is used instead of ID.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-target-add
{: #security-group-target-add}

Add a target to a security group.

```
ibmcloud is security-group-target-add GROUP TARGET [--vpc VPC] [(--trt load_balancer | endpoint_gateway | vpn_server) | --in INSTANCE | --bm BARE_METAL_SERVER] [--output JSON] [-q, --quiet]
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

#### Command options
{: #command-options-security-group-target-add}

- **GROUP**: ID or name of the security group.
- **TARGET**: ID or name of the bound target resource for security group. The following types are supported target resource types: _network_interface_, _load_balancer_, _endpoint_gateway_, _vpn_server_.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--trt**: The bound target resource type, this option is only required if you use the target name instead of ID. One of: **load_balancer**, **endpoint_gateway**, **vpn_server**.
- **--in**: The ID or name of the instance to be bound. It is only required if you use the network interface name instead of ID.
- **--bm**: The ID or name of the bare metal server to be bound. It is only required if the network interface name is used instead of ID.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-target-remove
{: #security-group-target-remove}

Remove targets from a security group.

```
ibmcloud is security-group-target-remove GROUP (TARGET1 TARGET2 ...) [--vpc VPC] [(--trt load_balancer | endpoint_gateway | vpn_server) | --in INSTANCE | --bm BARE_METAL_SERVER] [--output JSON] [-f, --force] [-q, --quiet]
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

#### Command options
{: #command-options-security-group-target-remove}

- **GROUP**: ID or name of the security group.
- **TARGET1**: ID or name of the bound target resource for security group. If you use the name format, only the resources under the same resource type are supplied. And for network interface by name, all the network interface names must be under the same instance. The following types are supported target resource types: _network_interface_, _load_balancer_, _endpoint_gateway_, _vpn_server_.
- **TARGET2**: ID or name of the bound target resource for security group. If you use the name format, only the resources under the same resource type are supplied. And for network interface by name, all the network interface names must be under the same instance. The following types are supported target resource types: _network_interface_, _load_balancer_, _endpoint_gateway_, _vpn_server_.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--trt**: The bound target resource type, this option is only required if you use the target name instead of ID. One of: **load_balancer**, **endpoint_gateway**, **vpn_server**.
- **--in**: The ID or name of the instance to be bound. It is only required if you use the network interface name instead of ID.
- **--bm**: The ID or name of the bare metal server to be bound. It is only required if the network interface name is used instead of ID.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-targets
{: #security-group-targets}

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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Subnets
{: #subnet-cli-ref}

### ibmcloud is subnet
{: #subnet}

View details of a subnet.

```
ibmcloud is subnet SUBNET [--vpc VPC] [--show-attached] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnet}

- **SUBNET**: ID or name of the subnet.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--rt**: The ID or name of the routing table.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--name**: New name of the subnet.
- **--acl**: The ID or name of the network ACL.
- **--pgw**: The ID or name of the public gateway.
- **--rt**: The ID or name of the routing table.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnets
{: #subnets}

List all subnets.

```
ibmcloud is subnets [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnets}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-public-gateway
{: #subnet-public-gateway}

View details of public gateway attached to the subnet.

```
ibmcloud is subnet-public-gateway SUBNET [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnet-public-gateway}

- **SUBNET**: ID or name of the subnet.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-reserved-ips
{: #subnet-reserved-ips}

List all reserved IPs in the subnet.

```
ibmcloud is subnet-reserved-ips SUBNET [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnet-reserved-ips}

- **SUBNET**: ID or name of the subnet.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-reserved-ip
{: #subnet-reserved-ip}

View details of reserved IP.

```
ibmcloud is subnet-reserved-ip SUBNET RESERVED_IP [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnet-reserved-ip}

- **SUBNET**: ID or name of the subnet.
- **RESERVED_IP**: ID or name of the reserved IP.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-reserved-ip-create
{: #subnet-reserved-ip-create}

Reserve an IP in a subnet.

```
ibmcloud is subnet-reserved-ip-create SUBNET [--vpc VPC] [--name NAME] [--address ADDRESS] [--auto-delete true | false] [--target TARGET] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-subnet-reserved-ip-create}

- `ibmcloud is subnet-reserved-ip-create 2201-3f2e33d4-2140-44b4-843c-d73e03d585f1 --name my-reserved-ip --address 10.240.64.10 --auto-delete true`
- `ibmcloud is subnet-reserved-ip-create my-subnet --name my-reserved-ip --address 10.240.64.10 --auto-delete true`
- `ibmcloud is subnet-reserved-ip-create 2201-3f2e33d4-2140-44b4-843c-d73e03d585f1 --name my-reserved-ip --address 10.240.64.10 --auto-delete true --target r134-5be98168-017a-459c-959f-7a6c1f7b813b`
- `ibmcloud is subnet-reserved-ip-create my-subnet --name my-reserved-ip --address 10.240.64.10 --auto-delete true --target my-vpe`
- `ibmcloud is subnet-reserved-ip-create 2201-3f2e33d4-2140-44b4-843c-d73e03d585f1 --name my-reserved-ip --address 10.240.64.10 --output JSON`

#### Command options
{: #command-options-subnet-reserved-ip-create}

- **SUBNET**: ID or name of the subnet.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--name**: The user-defined name for this reserved IP. Names must be unique within the subnet that the reserved IP resides in. Names beginning with **ibm-** are reserved for provider-owned resources.
- **--address**: The IP address to reserve, which must not already be reserved on the subnet. If not specified, an available address on the subnet is automatically selected.
- **--auto-delete**: Indicates whether this reserved IP member automatically deletes when either target is deleted, or the reserved IP is unbound. Must be false if the reserved IP is unbound. One of: **true**, **false**. (default: **false**).
- **--target**: The ID or name of the target resource. The following types are supported target resource types: _endpoint_gateway_.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--force, -f**: Force the operation without confirmation.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Virtual private clouds
{: #vpcs-cli-ref}

### ibmcloud is vpc
{: #vpc}

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
{: #vpc-address-prefix}

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
- **CIDR**: The IPv4 range of the address prefix, expressed in CIDR format. It must not overlap with any existing address prefixes in the VPC, and must fall within the [RFC 1918](https://tools.ietf.org/html/rfc1918) address ranges. The prefix length of the address prefix's CIDR must be between `/9` (8,388,608 addresses) and `/29` (eight addresses).
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
{: #vpc-address-prefixes}

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
ibmcloud is vpc-create VPC_NAME [--classic-access] [--address-prefix-management auto | manual] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpc-create}

- `ibmcloud is vpc-create my-vpc --classic-access`
- `ibmcloud is vpc-create my-vpc --address-prefix-management auto`
- `ibmcloud is vpc-create my-vpc --resource-group-id fee82deba12e4c0fb69c3b09d1f12345`
- `ibmcloud is vpc-create my-vpc --resource-group-name Default --output JSON`

#### Command options
{: #command-options-vpc-create}

- **VPC_NAME**: Name of the VPC.
- **--classic-access**: This flag indicates whether the VPC must be connected to Classic Infrastructure. The default value is false.
- **--address-prefix-management**: This flag indicates if a default address prefix is automatically created for each zone in this VPC. If **manual**, this VPC is created with no default address prefixes. One of: **auto**, **manual**. (default: **auto**).
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-default-security-group
{: #vpc-default-security-group}

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
ibmcloud is vpc-update VPC --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpc-update}

- `ibmcloud is vpc-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-renamed-vpc`
- `ibmcloud is vpc-update my-vpc --name my-renamed-vpc`

#### Command options
{: #command-options-vpc-update}

- **VPC**: ID or name of the VPC.
- **--name**: New name of the VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpcs
{: #vpcs}

List all VPCs.

```
ibmcloud is vpcs [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--classic-access true | false] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpcs}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--classic-access**: This flag lists VPCs that have classic access enabled. If unspecified, it returns all VPCs with and without classic access enabled. One of: **true**, **false**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Virtual private endpoint gateways
{: #vpe-clis}

The following section gives details about the CLI commands that are available for working with endpoint gateways.

### ibmcloud is endpoint-gateway-targets
{: #endpoint-gateway-targets}

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
{: #endpoint-gateway}

View details of an endpoint gateway.

```
ibmcloud is endpoint-gateway ENDPOINT_GATEWAY [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-endpoint-gateway}

- **ENDPOINT_GATEWAY**: ID or name of the endpoint gateway.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is endpoint-gateways
{: #endpoint-gateways}

List all endpoint gateways in the region.

```
ibmcloud is endpoint-gateways [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-endpoint-gateways}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is endpoint-gateway-create
{: #endpoint-gateway-create}

Create an endpoint gateway.

```
ibmcloud is endpoint-gateway-create --target TARGET [--vpc VPC] [--name NAME] [--rip RIP --subnet SUBNET | (--new-reserved-ip NEW_RESERVED_IP1 --new-reserved-ip NEW_RESERVED_IP2 ...)] [--sg SG] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
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

- **--vpc**: ID or name of the VPC.
- **--target**: The name of the provider infrastructure service or the CRN for a provider cloud service instance. You can use command **ibmcloud is endpoint-gateway-targets** to list the provider cloud and infrastructure services that are qualified to be set as endpoint gateway target.
- **--name**: New name of the endpoint gateway.
- **--rip**: Comma-separated IDs of the reserved IP to be bound to the endpoint gateway. At most, one reserved IP per zone is allowed. It can also be reserved IP name, but only one reserved IP name is allowed and subnet option for this reserved IP name also must be supplied.
- **--subnet**: ID or Name of the subnet. This name is only required if the supplied reserved IP is in name format.
- **--new-reserved-ip**: RESERVED_IP_JSON|@RESERVED_IP_JSON_FILE, new reserved IP configuration in JSON or JSON file.
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
ibmcloud is endpoint-gateway-update ENDPOINT_GATEWAY --name NEW_NAME [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-endpoint-gateway-update}

- **ENDPOINT_GATEWAY**: ID or name of the endpoint gateway.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--name**: New name of the endpoint gateway.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--rip**: ID or Name of the reserved IP address to be bound.
- **--subnet**: ID or Name of the subnet. This name is only required if the supplied reserved IP is in name format.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--address**: The reserved IP address to be unbound.
- **--rip**: ID or Name of the reserved IP address to be unbound.
- **--subnet**: ID or Name of the subnet. This name is only required if the supplied reserved IP is in name format.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

## Virtual private network (VPN) gateways
{: #vpn-clis}

The following section gives details about the CLI commands that are available for working with VPN gateways, including IKE and IPsec policies.


### ibmcloud is ike-policies
{: #ike-policies}

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
{: #ike-policy}

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
{: #ike-policy-connections}

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
- **AUTHENTICATION_ALGORITHM**: The authentication algorithm. The 'md5' and 'sha1' algorithms are deprecated. One of: **md5**, **sha1**, **sha256**, **sha384**, **sha512**.
- **DH_GROUP**: The Diffie-Hellman group. Groups '2' and '5' are deprecated. One of: **2**, **5**, **14**, **15**, **16**, **17**, **18**, **19**, **20**, **21**, **22**, **23**, **24**, **31**.
- **ENCRYPTION_ALGORITHM**: The encryption algorithm. The 'triple_des' algorithm is deprecated. One of: **triple_des**, **aes128**, **aes192**, **aes256**.
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
ibmcloud is ike-policy-update IKE_POLICY [--name NEW_NAME] [--authentication-algorithm md5 | sha1 | sha256 | sha384 | sha512] [--dh-group 2 | 5 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 | 23 | 24 | 31] [--encryption-algorithm triple_des | aes128 | aes192 | aes256] [--ike-version 1 | 2] [--key-lifetime KEY_LIFETIME] [--output JSON] [-q, --quiet]
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
- **--authentication-algorithm**: The authentication algorithm. The **md5** and **sha1** algorithms are deprecated. One of: **md5**, **sha1**, **sha256**, **sha384**, **sha512**.
- **--dh-group**: The Diffie-Hellman group. Groups **2** and **5** are deprecated. One of: **2**, **5**, **14**, **15**, **16**, **17**, **18**, **19**, **20**, **21**, **22**, **23**, **24**, **31**.
- **--encryption-algorithm**: The encryption algorithm. The **triple_des** algorithm is deprecated. One of: **triple_des**, **aes128**, **aes192**, **aes256**.
- **--ike-version**: The IKE protocol version. One of: **1**, **2**.
- **--key-lifetime**: The key lifetime in seconds. Maximum: **86400**, Minimum: **1800**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ipsec-policies
{: #ipsec-policies}

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
{: #ipsec-policy}

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
{: #ipsec-policy-connections}

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
- **AUTHENTICATION_ALGORITHM**: The authentication algorithm. The 'md5' and 'sha1' algorithms are deprecated. Must be disabled only if encryption algorithm is 'aes128gcm16', 'aes192gcm16', or 'aes256gcm16' One of: **disabled**, **md5**, **sha1**, **sha256**, **sha384**, **sha512**.
- **ENCRYPTION_ALGORITHM**: The encryption algorithm. The 'triple_des' algorithm is deprecated. The authentication algorithm must be disabled only if encryption algorithm is 'aes128gcm16', 'aes192gcm16', or 'aes256gcm16' One of: **aes128**, **aes128gcm16**, **aes192**, **aes192gcm16**, **aes256**, **aes256gcm16**, **triple_des**.
- **PFS**: Perfect Forward Secrecy. Groups 'group_2' and 'group_5' are deprecated. One of: **disabled**, **group_2**, **group_5**, **group_14**, **group_15**, **group_16**, **group_17**, **group_18**, **group_19**, **group_20**, **group_21**, **group_22**, **group_23**, **group_24**, **group_31**.
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
ibmcloud is ipsec-policy-update IPSEC_POLICY [--name NEW_NAME] [--authentication-algorithm disabled | md5 | sha1 | sha256 | sha384 | sha512] [--pfs disabled | group_2 | group_5 | group_14 | group_15 | group_16 | group_17 | group_18 | group_19 | group_20 | group_21 | group_22 | group_23 | group_24 | group_31] [--encryption-algorithm aes128 | aes128gcm16 | aes192 | aes192gcm16 | aes256 | aes256gcm16 | triple_des] [--key-lifetime KEY_LIFETIME] [--output JSON] [-q, --quiet]
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
- **--authentication-algorithm**: The authentication algorithm. The **md5** and **sha1** algorithms are deprecated. Must be disabled only if encryption algorithm is **aes128gcm16**, **aes192gcm16**, or **aes256gcm16** One of: **disabled**, **md5**, **sha1**, **sha256**, **sha384**, **sha512**.
- **--pfs**: Perfect Forward Secrecy. Groups **group_2** and **group_5** are deprecated. One of: **disabled**, **group_2**, **group_5**, **group_14**, **group_15**, **group_16**, **group_17**, **group_18**, **group_19**, **group_20**, **group_21**, **group_22**, **group_23**, **group_24**, **group_31**.
- **--encryption-algorithm**: The encryption algorithm. The **triple_des** algorithm is deprecated. The authentication algorithm must be disabled only if encryption algorithm is **aes128gcm16**, **aes192gcm16**, or **aes256gcm16** One of: **aes128**, **aes128gcm16**, **aes192**, **aes192gcm16**, **aes256**, **aes256gcm16**, **triple_des**.
- **--key-lifetime**: The key lifetime in seconds. Maximum: **86400**, Minimum: **1800**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway
{: #vpn-gateway}

View details of a VPN gateway.

```
ibmcloud is vpn-gateway VPN_GATEWAY [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection
{: #vpn-gateway-connection}

View details of a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection VPN_GATEWAY (CONNECTION1 CONNECTION2 ...) [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-connection}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **CONNECTION1**: ID or name of the VPN connection.
- **CONNECTION2**: ID or name of the VPN connection.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-create
{: #vpn-gateway-connection-create}

Create a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-create CONNECTION_NAME VPN_GATEWAY PEER_ADDRESS PRESHARED_KEY --local-cidr CIDR1 --local-cidr CIDR2 ... --peer-cidr CIDR1 --peer-cidr CIDR2 ... [--vpc VPC] [--admin-state-up true | false] [--dead-peer-detection-action restart | clear | hold | none] [--dead-peer-detection-interval INTERVAL] [--dead-peer-detection-timeout TIMEOUT] [--ike-policy IKE_POLICY_ID] [--ipsec-policy IPSEC_POLICY_ID] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpn-gateway-connection-create}

- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso`
- `ibmcloud is vpn-gateway-connection-create my-connection my-vpn-gateway 169.21.50.5 lkj14b1oi0alcniejkso`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --admin-state-up true`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --dead-peer-detection-action clear --dead-peer-detection-interval 33 --dead-peer-detection-timeout 100`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --ipsec-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is vpn-gateway-connection-create my-connection my-vpn-gateway 169.21.50.5 lkj14b1oi0alcniejkso --ipsec-policy my-ispec-policy`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --ike-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is vpn-gateway-connection-create my-connection my-vpn-gateway 169.21.50.5 lkj14b1oi0alcniejkso --ike-policy my-ike-policy`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --output JSON`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --admin-state-up true`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --dead-peer-detection-action clear --dead-peer-detection-interval 33 --dead-peer-detection-timeout 100`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --ipsec-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --ike-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --local-cidr 10.240.1.0/24 --peer-cidr 192.168.1.0/24 --peer-cidr 192.168.2.0/24  --output JSON`

#### Command options
{: #command-options-vpn-gateway-connection-create}

- **CONNECTION_NAME**: Name of the connection.
- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **PEER_ADDRESS**: The IP address of the peer VPN gateway.
- **PRESHARED_KEY**: The preshared key.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--admin-state-up**: If set to false, the VPN gateway connection is shut down. One of: **true**, **false**. (default: **true**).
- **--dead-peer-detection-action**: Dead Peer Detection actions. One of: **restart**, **clear**, **hold**, **none**. (default: **restart**).
- **--dead-peer-detection-interval**: Dead Peer Detection interval in seconds (default: **2**).
- **--dead-peer-detection-timeout**: Dead Peer Detection timeout in seconds (default: **10**).
- **--ike-policy**: ID of the IKE policy.
- **--ipsec-policy**: ID of the IPsec policy.
- **--local-cidr**: Local CIDR for the resource.
- **--peer-cidr**: Peer CIDRs for the resource.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-local-cidr-add
{: #vpn-gateway-connection-local-cidr-add}

Add a local CIDR to a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-local-cidr-add VPN_GATEWAY CONNECTION PREFIX_ADDRESS PREFIX_LENGTH [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-connection-local-cidr-add}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **CONNECTION**: ID or name of the VPN connection.
- **PREFIX_ADDRESS**: The prefix address part of the CIDR.
- **PREFIX_LENGTH**: The prefix length part of the CIDR.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-local-cidr-delete
{: #vpn-gateway-connection-local-cidr-delete}

Remove a local CIDR from the VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-local-cidr-delete VPN_GATEWAY CONNECTION PREFIX_ADDRESS PREFIX_LENGTH [--vpc VPC] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-connection-local-cidr-delete}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **CONNECTION**: ID or name of the VPN connection.
- **PREFIX_ADDRESS**: The prefix address part of the CIDR.
- **PREFIX_LENGTH**: The prefix length part of the CIDR.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-peer-cidr-add
{: #vpn-gateway-connection-peer-cidr-add}

Add a peer CIDR to a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-peer-cidr-add VPN_GATEWAY CONNECTION PREFIX_ADDRESS PREFIX_LENGTH [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-connection-peer-cidr-add}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **CONNECTION**: ID or name of the VPN connection.
- **PREFIX_ADDRESS**: The prefix address part of the CIDR.
- **PREFIX_LENGTH**: The prefix length part of the CIDR.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-peer-cidr-delete
{: #vpn-gateway-connection-peer-cidr-delete}

Remove a peer CIDR from the VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-peer-cidr-delete VPN_GATEWAY CONNECTION PREFIX_ADDRESS PREFIX_LENGTH [--vpc VPC] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-connection-peer-cidr-delete}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **CONNECTION**: ID or name of the VPN connection.
- **PREFIX_ADDRESS**: The prefix address part of the CIDR.
- **PREFIX_LENGTH**: The prefix length part of the CIDR.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-update
{: #vpn-gateway-connection-update}

Update a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-update VPN_GATEWAY CONNECTION [--vpc VPC] [--admin-state-up true | false] [--dead-peer-detection-action restart | clear | hold | none] [--dead-peer-detection-interval INTERVAL] [--dead-peer-detection-timeout TIMEOUT] [--ike-policy IKE_POLICY_ID | --reset-ike-policy] [--ipsec-policy IPSEC_POLICY_ID | --reset-ipsec-policy] [--peer-address ADDRESS] [--psk PSK] [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpn-gateway-connection-update}

- `ibmcloud is vpn-gateway-connection-update fee82deba12e4c0fb69c3b09d1f12345 gfe82deba12e4c0fb69c3b09d1f23456 --admin-state-up true --dead-peer-detection-action clear --dead-peer-detection-interval 33 --dead-peer-detection-timeout 100  --ike-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479  --ipsec-policy 05251a2e-d6c5-42b4-97b0-b5f8e8d1f445 --peer-address 234.3.4.5 -psk rweirjgiort --name my-new-connection --output JSON`
- `ibmcloud is vpn-gateway-connection-update my-vpn-gateway my-connection --admin-state-up true --dead-peer-detection-action clear --dead-peer-detection-interval 33 --dead-peer-detection-timeout 100  --ike-policy my-ike-policy  --ipsec-policy my-ipsec-policy --peer-address 234.3.4.5 -psk rweirjgiort --name my-new-connection --output JSON`

#### Command options
{: #command-options-vpn-gateway-connection-update}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **CONNECTION**: ID or name of the VPN connection.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--admin-state-up**: If set to false, the VPN gateway connection is shut down. One of: **true**, **false**.
- **--dead-peer-detection-action**: Dead Peer Detection actions. One of: **restart**, **clear**, **hold**, **none**.
- **--dead-peer-detection-interval**: Dead Peer Detection interval in seconds.
- **--dead-peer-detection-timeout**: Dead Peer Detection timeout in seconds.
- **--ike-policy**: ID of the IKE policy.
- **--reset-ike-policy**: Remove IKE policy.
- **--ipsec-policy**: ID of the IPsec policy.
- **--reset-ipsec-policy**: Remove IPsec policy.
- **--peer-address**: The IP address of the peer VPN gateway.
- **--psk**: The preshared key.
- **--name**: New name of the connection.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connections
{: #vpn-gateway-connections}

List all VPN gateway connections.

```
ibmcloud is vpn-gateway-connections VPN_GATEWAY [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-connections}

- **VPN_GATEWAY**: ID or name of the VPN gateway.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--mode**: The mode of the VPN gateway. One of: **policy**, **route**.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--name**: New name of the VPN gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateways
{: #vpn-gateways}

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
{: #vpn-servers}

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
{: #vpn-server}

View details of a VPN server.

```
ibmcloud is vpn-server VPN_SERVER [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-server}

- **VPN_SERVER**: ID or name of the VPN server.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--client-ip-pool**: The VPN client IPv4 address pool, expressed in CIDR format. The request must not overlap with any existing address prefixes in the VPC or any of the following reserved address ranges: 127.0.0.0/8 (IPv4 loopback addresses), 161.26.0.0/16 (IBM services), 166.8.0.0/14 (Cloud Service Endpoints), 169.254.0.0/16 (IPv4 link-local addresses), 224.0.0.0/4 (IPv4 multicast addresses). The prefix length of the client IP address pool's CIDR must be between /9 (8,388,608 addresses) and /22 (1024 addresses). A CIDR block that contains twice the number of IP addresses that are required to enable the maximum number of concurrent connections is recommended.
- **--cert**: The secret CRN from the secret manager for this VPN server. Because the usage of certificate CRN from Certificate Manager is deprecated, migrate your VPN server certificates from Certificate Manager to Secrets Manager.
- **--client-auth-methods**: Comma-separated of client authentication methods. One of: **certificate**, **username**, **certificate,username**, **username,certificate**.
- **--client-ca**: The secret CRN from the secrets manager to use for the VPN client certificate authority (CA). Because the usage of certificate CRN from Certificate Manager is deprecated, migrate your VPN server certificates from Certificate Manager to Secrets Manager.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--subnet**: Comma-separated IDs or names of the subnets to provision this VPN server. Use subnets in different zones for high availability and at most, you can set two subnets.
- **--client-ip-pool**: The VPN client IPv4 address pool, expressed in CIDR format. The request must not overlap with any existing address prefixes in the VPC or any of the following reserved address ranges: 127.0.0.0/8 (IPv4 loopback addresses), 161.26.0.0/16 (IBM services), 166.8.0.0/14 (Cloud Service Endpoints), 169.254.0.0/16 (IPv4 link-local addresses), 224.0.0.0/4 (IPv4 multicast addresses). The prefix length of the client IP address pool's CIDR must be between /9 (8,388,608 addresses) and /22 (1024 addresses). A CIDR block that contains twice the number of IP addresses that are required to enable the maximum number of concurrent connections is recommended.
- **--cert**: The secret CRN from the secret manager for this VPN server. Because the usage of certificate CRN from Certificate Manager is deprecated, migrate your VPN server certificates from Certificate Manager to Secrets Manager.
- **--client-auth-methods**: Comma-separated of client authentication methods. One of: **certificate**, **username**, **certificate,username**, **username,certificate**.
- **--client-ca**: The secret CRN from the secrets manager to use for the VPN client certificate authority (CA). Because the usage of certificate CRN from Certificate Manager is deprecated, migrate your VPN server certificates from Certificate Manager to Secrets Manager.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-client-configuration
{: #vpn-server-client-configuration}

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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--file**: Save the client configuration to the specified file path name.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-clients
{: #vpn-server-clients}

List all VPN clients for a VPN server.

```
ibmcloud is vpn-server-clients VPN_SERVER [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-server-clients}

- **VPN_SERVER**: ID or name of the VPN server.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-client
{: #vpn-server-client}

View details of a VPN client.

```
ibmcloud is vpn-server-client VPN_SERVER CLIENT_ID [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-server-client}

- **VPN_SERVER**: ID or name of the VPN server.
- **CLIENT_ID**: ID of the VPN client.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-client-delete
{: #vpn-server-client-delete}

Delete one or more VPN clients for a VPN server.

```
ibmcloud is vpn-server-client-delete VPN_SERVER (CLIENT_ID1 CLIENT_ID2 ...) [--vpc VPC] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-server-client-delete}

- **VPN_SERVER**: ID or name of the VPN server.
- **CLIENT_ID1**: ID of the VPN client.
- **CLIENT_ID2**: ID of the VPN client.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-routes
{: #vpn-server-routes}

List all VPN routes for a VPN server.

```
ibmcloud is vpn-server-routes VPN_SERVER [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-server-routes}

- **VPN_SERVER**: ID or name of the VPN server.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-server-route
{: #vpn-server-route}

View details of a VPN route.

```
ibmcloud is vpn-server-route VPN_SERVER ROUTE_ID [--vpc VPC] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-server-route}

- **VPN_SERVER**: ID or name of the VPN server.
- **ROUTE_ID**: ID or name of the VPN route.
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
{: #operating-systems}

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
{: #operating-system}

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
{: #image}

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
{: #images}

List all images in the region.

```
ibmcloud is images [--visibility all | public | private] [--owner-type all | provider | user] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-images}

- **--visibility**: List images with given visibility. Valid visibility is: **public** or **private**.
- **--owner-type**: Filters images with given owner type. Default is `all`. One of: **all**, **provider**, **user**.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is image-create
{: #image-create}

Create an image.

```
ibmcloud is image-create IMAGE_NAME ([--file IMAGE_FILE_LOCATION --os-name OPERATING_SYSTEM_NAME [--encrypted-data-key ENCRYPTED_DATA_KEY --encryption-key ENCRYPTION_KEY]] | [--source-volume SOURCE_VOLUME --encryption-key-volume ENCRYPTION_KEY_VOLUME]) [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
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

#### Command options
{: #command-options-image-create}

- **IMAGE_NAME**: Name of the image.
- **--file**: The Cloud Object Store (COS) location of the image file, for example: **cos://us-south/custom-image-vpc-bucket/customImage-0.qcow2**.
- **--os-name**: Name of the operating system for this image.
- **--encrypted-data-key**: A base64-encoded, encrypted representation of the key that was used to encrypt the data for this image.
- **--encryption-key**: The CRN of the root key that was used to wrap the data key (which is ultimately represented as **encrypted_data_key**). Additionally, the root key is used to encrypt volumes created from this image (unless an alternate **encryption_key** is provided at volume creation).
- **--source-volume**: ID or name of the volume. The volume from which to create the image. The specified volume must originate from image. The volume's active and busy property value must be **false**, and the volume attached instance must be in stopped status.
- **--encryption-key-volume**: A reference to the root key to that is used to wrap the system-generated data encryption key for the image. If this property is not provided, the root key from source volume is used.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is image-update
{: #image-update}

Update an image.

```
ibmcloud is image-update IMAGE --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-image-update}

- `ibmcloud is image-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-image`

#### Command options
{: #command-options-image-update}

- **IMAGE**: ID or name of the image.
- **--name**: New name of the image.
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

### ibmcloud is catalog-image-offerings
{: #catalog-image-offerings}

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
{: #catalog-image-offering}

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
{: #instance}

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
{: #ibmcloud-is-instances}

List all virtual server instances.

```
ibmcloud is instances [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instances}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
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
ibmcloud is instance-create INSTANCE_NAME VPC ZONE_NAME PROFILE_NAME SUBNET [--image IMAGE | --catalog-offering CATALOG_OFFERING | --catalog-offering-version CATALOG_OFFERING_VERSION] [--total-volume-bandwidth TOTAL_VOLUME_BANDWIDTH] [--boot-volume BOOT_VOLUME_JSON | @BOOT_VOLUME_JSON_FILE] [--volume-attach VOLUME_ATTACH_JSON | @VOLUME_ATTACH_JSON_FILE] [--keys KEYS] [--dedicated-host DEDICATED_HOST | --dedicated-host-group DEDICATED_HOST_GROUP | --placement-group PLACEMENT_GROUP] [--user-data DATA] [([--sgs SGS] [--rip RIP | (--address ADDRESS --auto-delete true | false --ip-name IP_NAME)] [--allow-ip-spoofing false | true]) | --primary-network-interface PRIMARY_NETWORK_INTERFACE_JSON | @PRIMARY_NETWORK_INTERFACE_JSON_FILE] [--network-interface NETWORK_INTERFACE_JSON | @NETWORK_INTERFACE_JSON_FILE] [--default-trusted-profile DEFAULT_TRUSTED_PROFILE [--default-trusted-profile-auto-link true,false]] [--metadata-service, --ms true | false ] [--host-failure-policy restart | stop] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-i, --interactive] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-create}

- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8`
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"name":"my-volume-name", "capacity":10, "profile": {"name": "general-purpose"},"user_tags": ["my-tag-1"]}}]'`
Create instance with volume attachment.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"id":"67531475-bd8a-478e-bcfe-2e53365cd0aa"}}]'`
Create instance with existing volume in volume attachment.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --keys 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
Create instance with multiple SSH keys.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "my-boot-vol", "capacity": 150, "profile": {"name": "general-purpose"}}}'`
Create instance from image with boot volume capacity. The capacity value can range from image's minimum provisioned size to 250
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "my-boot-vol", "profile": {"name": "general-purpose"},"user_tags": ["my-tag-1"]}}'`
Create instance with boot volume and boot volume with user tags.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"profile": {"name": "general-purpose"},"encryption_key": {"crn": "crn:v1:bluemix:public:kms:us-south:adffc98a0f1f0f95f6613b3b752286b87:e4a29d1a-2ef0-42a6-8fd2-350deb1c647e:key:5437653b-c4b1-447f-9646-b2a2a4cd6179"}}}'`
Create instance with encrypted boot volume.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --network-interface '[{"name": "secondary-nic", "allow_ip_spoofing": true, "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}]'`
Create instance that is attached to secondary network interface.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "primary_ip": {"address": "10.240.129.10", "auto-delete": true, "name": "my-reserved-ip"}, "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}'`
Create instance with primary network interface configuration in JSON.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --sgs 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --address 10.240.129.10 --auto-delete true --ip-name my-reserved-ip --allow-ip-spoofing true`
Create instance with primary network interface configuration that includes security groups, reserved IP settings, source IP spoofing setting.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --sgs 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --reserved-ip 0711-5c7f016e-5bd2-42e3-8dff-81519e4e2469 --allow-ip-spoofing true`
Create instance with primary network interface configuration that includes security groups, existing reserved IP, source IP spoofing setting.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host c019b1f7-c4d6-430c-aaa4-e0cc25d47277`
Create instance to be placed in the wanted dedicated host.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host-group a4738ceb-5e59-4601-849a-61d7895740ee`
Create instance to be placed in the wanted dedicated host group.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --placement-group 1d2afa0f-b9f2-4d85-ae35-a08885269644`
Create instance to be placed in the wanted placement group.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --total-volume-bandwidth 4000`
Create instance with specific total volumes bandwidth
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --metadata-service true`
Create instance with metadata service enabled or disabled
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --default-trusted-profile Profile-c9fe8182-870a-49df-8308-c8bb7394c4c3 --default-trusted-profile-auto-link true`
Create instance with default trusted profile
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --host-failure-policy restart`
Create instance with availability policy on host failure
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 bx2-2x8 my-subnet --image ibm-ubuntu-20-04-2-minimal-amd64-1 --volume-attach '[{"volume": {"name":"my-vol-1"}}]'`
Create instance with existing volume in volume attachment by using resource name.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 mx2-2x16 my-subnet --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host my-dedicated-host`
Create instance to be placed in the wanted dedicated host by using resource name.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 mx2-2x16 my-subnet --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host-group my-dedicated-host-group`
Create instance to be placed in the wanted dedicated host group by using resource name.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 mx2-2x16 my-subnet --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --placement-group my-placement-host-group`
Create instance to be placed in the wanted placement group by using resource name.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 bx2-2x8 --image ibm-ubuntu-20-04-2-minimal-amd64-1 --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"name":"my-subnet"}, "primary_ip": {"name": "my-reserved-ip"}, "security_groups": [{"name": "my-security-group-1"}, {"name": "my-security-group-2"}]}'`
Create instance with primary network interface configuration by using resource name.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 bx2-2x8 my-subnet --image ibm-ubuntu-20-04-2-minimal-amd64-1 --network-interface '[{"name": "secondary-nic", "allow_ip_spoofing": true, "subnet": {"id":"my-subnet"}, "security_groups": [{"id": "my-security-group-1"}, {"id": "my-security-group-2"}]}]'`
Create instance that is attached to secondary network interface by using resource name.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --catalog-offering crn:v1:bluemix:public:globalcatalog-collection:global:a/efe5afc483594adaa8325e2b4d1290df:2497ae83-40cb-46ba-ac7f-5303514a2669:offering:54372a73-7a0a-4799-ac9c-8736620c67f1`
Create instance from catalog offering.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --catalog-offering-version crn:v1:bluemix:public:globalcatalog-collection:global:a/efe5afc483594adaa8325e2b4d1290df:2497ae83-40cb-46ba-ac7f-5303514a2669:offering:54372a73-7a0a-4799-ac9c-8736620c67f1`
Create instance from catalog offering version.
- `ibmcloud is instance-create --interactive`
Create instance interactively.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 bx2-2x8 my-subnet --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "boot-vol-name", "capacity": 150, "profile": {"name": "general-purpose"}, "source_snapshot": {"id": "150847e3-ef0d-4927-9341-6d0a7bae424f"}}}'`
Create instance from snapshot with boot volume capacity. The capacity value can range from snapshot's minimum capacity to 250
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "boot-vol-name", "profile": {"name": "general-purpose"}, "source_snapshot": {"id": "150847e3-ef0d-4927-9341-6d0a7bae424f"}}}'`
Create instance with boot volume attachment from volume snapshot.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 bx2-2x8 my-subnet --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"name":"my-volume-name", "profile": {"name": "general-purpose"}, "source_snapshot": {"name": "my-snapshot-name"}}}]'`
Create instance with volume attachment from volume snapshot by using resource name.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"name":"my-volume-name", "capacity":10, "profile": {"name": "general-purpose"}, "source_snapshot": {"id": "150847e3-ef0d-4927-9341-6d0a7bae424f"}}}]'`
Create instance with volume attachment from volume snapshot.
- `ibmcloud is instance-create my-instance-name my-vpc us-south-1 bx2-2x8 my-subnet --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "boot-vol-name", "profile": {"name": "general-purpose"}, "source_snapshot": {"name": "my-snapshot-name"}}}'`
Create instance with boot volume attachment from volume snapshot by using resource name.

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
- **--total-volume-bandwidth**: The amount of bandwidth (in megabits per second) that is allocated exclusively to instance storage volumes. An increase in this value results in a corresponding decrease to total network bandwidth.
- **--boot-volume**: BOOT_VOLUME_JSON|@BOOT_VOLUME_JSON_FILE, boot volume attachment in JSON or JSON file. For the data schema, see the **boot_volume_attachment** property in the [API documentation](/apidocs/vpc#create-instance).
- **--volume-attach**: VOLUME_ATTACH_JSON|@VOLUME_ATTACH_JSON_FILE, volume attachment in JSON or JSON file, list of volumes. For the data schema, see the **volume_attachments** property in the [API documentation](/apidocs/vpc#create-instance).
- **--keys**: Comma-separated IDs or names of SSH keys.
- **--dedicated-host**: ID or name of the host destination where the instance is placed.
- **--dedicated-host-group**: ID or name of the host group destination where the instance is placed.
- **--placement-group**: ID or name of the placement group. The placement group restrictions for the virtual server instance.
- **--user-data**: data|@data-file. User data to transfer to the virtual server instance.
- **--sgs**: Comma-separated security group IDs or names for primary network interface.
- **--rip**: ID or name of the existing reserved IP.
- **--address**: The IP address to reserve, which must not already be reserved on the subnet.
- **--auto-delete**: If set to **true**, this reserved IP automatically deletes when the target is deleted. One of: **true**, **false**. (default: **true**).
- **--ip-name**: The user-defined name for this reserved IP. Names must be unique within the subnet that the reserved IP resides in. Names beginning with **ibm-** are reserved for provider-owned resources.
- **--allow-ip-spoofing**: Disables the source and destination checks on this interface. If **false**, source IP spoofing is not allowed on this interface. One of: **false**, **true**.
- **--primary-network-interface**: PRIMARY_NETWORK_INTERFACE_JSON|@PRIMARY_NETWORK_INTERFACE_JSON_FILE, primary network interface in JSON or JSON file. For the data schema, see the **primary_network_interface** property in the [API documentation](/apidocs/vpc#create-instance).
- **--network-interface**: NETWORK_INTERFACE_JSON|@NETWORK_INTERFACE_JSON_FILE, network interface attachment in JSON or JSON file. For the data schema, see the **network_interfaces** property in the [API documentation](/apidocs/vpc#create-instance).
- **--default-trusted-profile**: ID or name of the trusted profile.
- **--default-trusted-profile-auto-link**: If set to true, the system creates a link to the specified target trusted profile during instance creation. Regardless of whether a link is created by the system or manually by using the IAM Identity service, it automatically deletes when the instance is deleted. One of: **true,false**. (default: **true**).
- **--metadata-service, --ms**: Enable or disable the Instance Metadata Service. One of: **true**, **false**.
- **--host-failure-policy**: The action to perform if the compute host experiences a failure. One of: **restart**, **stop**. (default: **restart**).
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--interactive, -i**: 
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-create-from-template
{: #instance-create-from-template}

Create a virtual server instance from instance template.

```
ibmcloud is instance-create-from-template --template TEMPLATE [--name Name] [--profile PROFILE] [--zone ZONE] [--vpc VPC] [--image IMAGE | --catalog-offering CATALOG_OFFERING | --catalog-offering-version CATALOG_OFFERING_VERSION] [--total-volume-bandwidth TOTAL_VOLUME_BANDWIDTH] [--boot-volume BOOT_VOLUME_JSON | @BOOT_VOLUME_JSON_FILE] [--volume-attach VOLUME_ATTACH_JSON | @VOLUME_ATTACH_JSON_FILE] [--keys KEYS] [--dedicated-host DEDICATED_HOST | --dedicated-host-group DEDICATED_HOST_GROUP | --placement-group PLACEMENT_GROUP] [--user-data DATA] [(--subnet SUBNET [--rip RIP | (--address ADDRESS --auto-delete true | false --ip-name IP_NAME)] [--sgs SGS] [--allow-ip-spoofing false | true]) | --primary-network-interface PRIMARY_NETWORK_INTERFACE_JSON | @PRIMARY_NETWORK_INTERFACE_JSON_FILE] [--network-interface NETWORK_INTERFACE_JSON | @NETWORK_INTERFACE_JSON_FILE] [--default-trusted-profile DEFAULT_TRUSTED_PROFILE [--default-trusted-profile-auto-link true,false]] [--metadata-service, --ms true | false ] [--host-failure-policy restart | stop] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-create-from-template}

- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d`
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --resource-group-id 7494aacb866142fba11a88d75cb37bd8 --output JSON`
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --boot-volume '{"delete_volume_on_instance_delete": false, "name": "boot-vol-attachment-name", "volume": {"name": "myvol2", "profile": {"name": "general-purpose"}}}'`
Create instance from instance template with the boot volume configuration
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --vpc r006-beca4c2f-625f-45de-bd95-c8eb12f6842a --zone us-south-1 --subnet 0717-fe2e13d0-9ba8-43bd-ab6b-a1fad51557ac --address 10.240.129.10 --auto-delete true --ip-name my-reserved-ip --sgs r006-19c2ce0d-d35d-47bc-8147-120edddd3de5 --allow-ip-spoofing true`
Create instance from instance template with the primary network interface configuration
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --vpc r006-beca4c2f-625f-45de-bd95-c8eb12f6842a --zone us-south-1 --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"id":"0717-fe2e13d0-9ba8-43bd-ab6b-a1fad51557ac"}, "primary_ip": {"address": "10.240.129.10", "auto-delete": true, "name": "my-reserved-ip"}, "security_groups": [{"id": "r006-19c2ce0d-d35d-47bc-8147-120edddd3de5"}]}'`
Create instance from instance template with the primary network interface configuration in json format
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --network-interface '[{"name": "secondary-nic", "allow_ip_spoofing": true, "subnet": {"id":"0737-f6b5a638-1fda-476b-9e2f-7a550fbb62b8"}, "primary_ip": {"address": "10.240.129.10", "auto-delete": true, "name": "my-reserved-ip"}, "security_groups": [{"id": "r006-caba3deb-136b-42c8-831a-1dbcc0f1912e"}]}, {"name": "third-nic", "allow_ip_spoofing": true, "subnet": {"id":"0737-6b939577-4839-47b0-b42f-a4b29a94c7d9"}, "primary_ip": {"address": "10.240.129.100", "auto-delete": true, "name": "my-reserved-ip"}, "security_groups": [{"id": "r006-caba3deb-136b-42c8-831a-1dbcc0f1912e"}]}]'`
Create instance from instance template with the second network interfaces configuration
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name new-instance-name --volume-attach '[{"delete_volume_on_instance_delete": false, "name": "my-volume-attachment1", "volume": {"name": "myvol2", "capacity": 200, "profile": {"name": "general-purpose"}}}, {"delete_volume_on_instance_delete": true, "name": "my-volume-attachment2", "volume": {"name": "myvol3", "capacity": 300, "iops": 1000, "profile": {"name": "custom"}}}]'`
Create instance from instance template with the data volumes configuration
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name new-instance-name --image r006-ed3f775f-ad7e-4e37-ae62-7199b4988b00 --profile cx2-2x4 --key r006-02a07b78-6e5f-40a2-86a2-99e01916128c,r006-29e19fb1-e2b9-49d0-ab6e-9702e99f5021 --user-data @/tmp/userdata.sh`
Create instance from instance template with image/profile/key/user data configuration
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --dedicated-host 0737-4ab6b37d-4695-4efb-9439-0528b5550dfe --profile mx2-2x16`
Create instance from instance template with the wanted dedicated host
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --dedicated-host-group 0737-7290ea56-7543-4590-8558-ca8cd51b12c4 --profile mx2-2x16`
Create instance from instance template with the wanted dedicated host group
- `ibmcloud is instance-create-from-template --template 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name new-instance-name --metadata-service true`
Create instance from instance template with metadata service enabled or disabled
- `ibmcloud is instance-create-from-template --template my-template --name new-instance-name --vpc my-vpc --zone us-south-1 --subnet my-subnet --reserved-ip my-reserved-ip --sgs my-security-group --allow-ip-spoofing true`
Create instance from instance template with the primary network interface configuration by using resource name.
- `ibmcloud is instance-create-from-template --template my-template --name my-instance --vpc my-vpc --zone us-south-1 --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"id":"my-subnet"}, "primary_ip": {"name": "my-reserved-ip"}, "security_groups": [{"name": "my-security-group"}]}'`
Create instance from instance template with the primary network interface configuration in json format by using resource name.
- `ibmcloud is instance-create-from-template --template my-template --name my-instance --network-interface '[{"name": "secondary-nic", "allow_ip_spoofing": true, "subnet": {"id":"my-subnet-1"}, "primary_ip": {"name": "my-reserved-ip"}, "security_groups": [{"id": "my-security-group-1"}]}, {"name": "third-nic", "allow_ip_spoofing": true, "subnet": {"id":"my-subnet-1"}, "primary_ip": {"name": "my-reserved-ip-2"}, "security_groups": [{"id": "my-security-group-2"}]}]'`
Create instance from instance template with the second network interfaces configuration by using resource name.
- `ibmcloud is instance-create-from-template --template my-template --name new-instance-name  --subnet my-subnet --image ibm-ubuntu-20-04-2-minimal-amd64-1 --volume-attach '[{"volume": {"name":"my-vol-1"}}]'`
Create instance from instance template with existing volume in volume attachment by using resource name.
- `ibmcloud is instance-create-from-template --template my-template --name new-instance-name --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"name":"my-subnet"}, "primary_ip": {"name": "my-reserved-ip"}, "security_groups": [{"name": "my-security-group-1"}, {"name": "my-security-group-2"}]}'`
Create instance from instance template with primary network interface configuration by using resource name.

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
- **--total-volume-bandwidth**: The amount of bandwidth (in megabits per second) that is allocated exclusively to instance storage volumes. An increase in this value results in a corresponding decrease to total network bandwidth.
- **--boot-volume**: BOOT_VOLUME_JSON|@BOOT_VOLUME_JSON_FILE, boot volume attachment in JSON or JSON file. For the data schema, see the **boot_volume_attachment** property in the [API documentation](/apidocs/vpc#create-instance).
- **--volume-attach**: VOLUME_ATTACH_JSON|@VOLUME_ATTACH_JSON_FILE, volume attachment in JSON or JSON file, list of volumes. For the data schema, see the **volume_attachments** property in the [API documentation](/apidocs/vpc#create-instance).
- **--keys**: Comma-separated IDs or names of SSH keys.
- **--dedicated-host**: ID or name of the host destination where the instance is placed.
- **--dedicated-host-group**: ID or name of the host group destination where the instance is placed.
- **--placement-group**: ID or name of the placement group. The placement group restrictions for the virtual server instance.
- **--user-data**: data|@data-file. User data to transfer to the virtual server instance.
- **--subnet**: ID or name of the subnet.
- **--rip**: ID or name of the existing reserved IP.
- **--address**: The IP address to reserve, which must not already be reserved on the subnet.
- **--auto-delete**: If set to **true**, this reserved IP automatically deletes when the target is deleted. One of: **true**, **false**. (default: **true**).
- **--ip-name**: The user-defined name for this reserved IP. Names must be unique within the subnet that the reserved IP resides in. Names beginning with **ibm-** are reserved for provider-owned resources.
- **--sgs**: Comma-separated security group IDs or names for primary network interface.
- **--allow-ip-spoofing**: Disables the source and destination checks on this interface. If **false**, source IP spoofing is not allowed on this interface. One of: **false**, **true**.
- **--primary-network-interface**: PRIMARY_NETWORK_INTERFACE_JSON|@PRIMARY_NETWORK_INTERFACE_JSON_FILE, primary network interface in JSON or JSON file. For the data schema, see the **primary_network_interface** property in the [API documentation](/apidocs/vpc#create-instance).
- **--network-interface**: NETWORK_INTERFACE_JSON|@NETWORK_INTERFACE_JSON_FILE, network interface attachment in JSON or JSON file. For the data schema, see the **network_interfaces** property in the [API documentation](/apidocs/vpc#create-instance).
- **--default-trusted-profile**: ID or name of the trusted profile.
- **--default-trusted-profile-auto-link**: If set to true, the system creates a link to the specified target trusted profile during instance creation. Regardless of whether a link is created by the system or manually by using the IAM Identity service, it automatically deletes when the instance is deleted. One of: **true,false**. (default: **true**).
- **--metadata-service, --ms**: Enable or disable the Instance Metadata Service. One of: **true**, **false**.
- **--host-failure-policy**: The action to perform if the compute host experiences a failure. One of: **restart**, **stop**.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
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
{: #instance-disk}

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
{: #instance-disks}

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
{: #instance-network-interface}

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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
{: #instance-network-interface-floating-ip}

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
{: #instance-network-interface-floating-ips}

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
{: #instance-network-interface-reserved-ips}

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
{: #instance-network-interface-reserved-ip}

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
{: #instance-network-interfaces}

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
{: #instance-profile}

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
{: #instance-profiles}

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

- When you stop an instance and restart it, a new private IP address is assigned if the instance wasn't created with a static IP address or the primary_ipv4_address attribute wasn't set when the instance was created by using the CLI or API. For more information about setting a static IP address, see primary_network_interface in the [API reference](https://{DomainName}/apidocs/vpc#create-an-instance){: new_window}.
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
ibmcloud is instance-update INSTANCE [--name NEW_NAME] [--profile PROFILE] [--total-volume-bandwidth TOTAL_VOLUME_BANDWIDTH] [--dedicated-host DEDICATED_HOST | --dedicated-host-group DEDICATED_HOST_GROUP] [--metadata-service, --ms true | false] [--host-failure-policy restart | stop] [--output JSON] [-q, --quiet]
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

#### Command options
{: #command-options-instance-update}

- **INSTANCE**: ID or name of the instance.
- **--name**: New name of the virtual server instance.
- **--profile**: The profile to use for this virtual server instance. To change the profile, the instance status must be `stopping` or `stopped`. In addition, the requested profile must: 1. Match the current profile's instance disk support. (**Note:** If the current profile supports instance storage disks, the requested profile can have a different instance storage disk configuration.) 2. Be compatible with any placement target constraints. For example, if the instance is placed on a dedicated host, the requested profile `family` must be the same as the dedicated host `family`.
- **--total-volume-bandwidth**: The amount of bandwidth (in megabits per second) that is allocated exclusively to instance storage volumes. An increase in this value results in a corresponding decrease to total network bandwidth.
- **--dedicated-host**: ID or name of the host destination where the instance is placed.
- **--dedicated-host-group**: ID or name of the host group destination where the instance is placed.
- **--metadata-service, --ms**: Enable or disable the Instance Metadata Service. One of: **true**, **false**.
- **--host-failure-policy**: The action to perform if the compute host experiences a failure. One of: **restart**, **stop**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-volume-attachment
{: #instance-volume-attachment}

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
{: #instance-volume-attachments}

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
ibmcloud is instance-volume-attachment-add NAME INSTANCE (VOLUME | --profile PROFILE --new-volume-name NEW_VOLUME_NAME --iops IOPS --encryption-key ENCRYPTION_KEY --capacity CAPACITY --tags TAGS --source-snapshot SOURCE_SNAPSHOT) [--auto-delete false | true] [--output JSON] [-q, --quiet]
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

#### Command options
{: #command-options-instance-volume-attachment-add}

- **NAME**: Name of the volume attachment.
- **INSTANCE**: ID or name of the instance.
- **VOLUME**: ID or name of the volume.
- **--new-volume-name**: The name of new volume.
- **--profile**: Name of the profile.
- **--iops**: Input/Output Operations Per Second for the volume, it is only applicable for custom profile volumes. For the IOPS range, refer to [Onboarding software to your account](docs/vpc?topic=vpc-block-storage-profiles#custom).
- **--encryption-key**: The CRN of the Key Management Service root key.
- **--capacity**: The capacity of the volume in gigabytes. Range 10-16000 for custom and general-purpose profile volumes, 10-9600 for 5iops-tier profile volumes, 10-4800 for 10iops-tier profile volumes.
- **--tags**: Comma-separated tags for the volume.
- **--source-snapshot**: ID or name of the snapshot to clone volume.
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

## Keys
{: #keys}

### ibmcloud is key
{: #key}

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
ibmcloud is key-create KEY_NAME (KEY | @KEY_FILE) [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-key-create}

- `ibmcloud is key-create my-key "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDL9osaBrUD8uCBzIJo5YBvX8wtGrE+kcC7YZtID/nNYrjeCB26eFASHia5tmqmuCo434UygGSd5qj3t/3v/a7NZoMr/0+qspQF+dUVIl+xIsKTWYQ+gtYbJlvW+FIlNTOA4vbOXLg+nGGUCoaV79azmny4mYJbbo15i+Q3CI+w9bwOAwzqeGKaeOjpo5hdDcFW0QLDxKmQHKMLX8slsx3kB9I5wPe8C/ZBBDBBkZKK2y3RJBjaKxi0beFueo6ngUKOLooReefiBGpdoOJIi6Gf7vRduoBTmbyVvSv08wcrANtYSzGwDpqrEshEafv8bKo42MYHsPT2OwAbsFyqWQj5 test@example"`
- `ibmcloud is key-create my-key @/tmp/my_id_rsa.pub`
- `ibmcloud is key-create my-key @/tmp/my_id_rsa.pub --output JSON`

#### Command options
{: #command-options-key-create}

- **KEY_NAME**: ID or name of the key.
- **KEY**: **key**|**@key-file**. The public SSH key to import into the system.
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
{: #ibmcloud-is-keys}

List all keys.

```
ibmcloud is keys [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

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
{: #dedicated-host-profiles}

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
{: #dedicated-host-profile}

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
{: #dedicated-host-groups}

List all host groups.

```
ibmcloud is dedicated-host-groups [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-dedicated-host-groups}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host-group
{: #dedicated-host-group}

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
{: #ibmcloud-is-dedicated-hosts}

List all hosts.

```
ibmcloud is dedicated-hosts [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-dedicated-hosts}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host
{: #dedicated-host}

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
{: #dedicated-host-disks}

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
{: #dedicated-host-disk}

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
{: #bare-metal-server}

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
ibmcloud is bare-metal-server-create --zone ZONE_NAME --profile PROFILE --image IMAGE --keys KEYS ((--pnic-subnet PRIMARY_NIC_SUBNET [--vpc VPC]) [--pnic-name PRIMARY_NIC_NAME] [--pnic-rip PNIC_RIP | (--pnic-rip-address PNIC_RIP_ADDRESS --pnic-rip-auto-delete true | false --pnic-rip-name PNIC_RIP_NAME)] [--pnic-sgs PNIC_SGS] [--pnic-allowed-vlans PNIC_ALLOWED_VLANS] [--pnic-ein true | false] [--pnic-ais false | true]) [--name NAME] [--user-data DATA] [--network-interfaces NETWORK_INTERFACES_JSON | @NETWORK_INTERFACES_JSON_FILE] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [-i, --interactive] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-bare-metal-server-create}

- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f`
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image ibm-esxi-7-byol-amd64-1 --keys my-sshkey-1,my-sshkey-2 --pnic-subnet my-subnet`
Create a bare metal server with name support for image, keys and subnet
- `ibmcloud is bare-metal-server-create --name my-server-name2 --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-name eth0 --pnic-rip-address 46.9.49.11 --pnic-sgs c791f26f-4cf1-4bbf-be0e-72d7cb87133e,fefc8362-93c2-4f3d-90d4-82c56cce787e --pnic-allowed-vlans 1,2,3,4 --pnic-ein true --pnic-ais true`
Create a bare metal server with specified primary network interface configuration.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --resource-group-name Finance --output JSON`
Create a bare metal server in the `Finance` resource group.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-allowed-vlans 100,200,300,400,700,710,1000,900-929,800-829`
Create a bare metal server with a PCI network interface. Allowed VLANs are comma-separated values that can be passed as separate values or as any range of numbers.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-rip 2302-74dd56cc-71c4-4461-95f0-4e5e3b57727d`
Create a bare metal server with pre-created reserved IP ID.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-rip cli-rip-1`
Create a bare metal server with pre-created reserved IP by NAME.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-rip-address 10.240.128.38  --pnic-rip-auto-delete true --pnic-rip-name cli-rip1`
Create a bare metal server with primary network interface with new reserved IP.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-rip 2302-74dd56cc-71c4-4461-95f0-4e5e3b57727d --network-interfaces '[{"name": "cli-snic", "allow_ip_spoofing": true, "enable_infrastructure_nat": true, "interface_type": "pci", "allowed_vlans": [1, 2, 3, 4], "subnet": {"id":"2302-531ad9fc-c86a-4504-b5cf-a46981fddb5f"}, "primary_ip":{"id": "2302-2b09dd0a-9cfb-4639-a2ac-cc6c154ab461"}}]`
Create a bare metal server with secondary network interface with pre-created reserved IP ID. Configurations of the two secondary interfaces are specified in JSON format. See help text for '--network-interfaces' option.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-rip cli-rip-1 --network-interfaces '[{"name": "cli-snic", "allow_ip_spoofing": true, "enable_infrastructure_nat": true, "interface_type": "pci", "allowed_vlans": [1, 2, 3, 4], "subnet": {"id":"2302-531ad9fc-c86a-4504-b5cf-a46981fddb5f"},"primary_ip":{"name": "cli-rip-byname"}}]`
Create a bare metal server with secondary network interface with pre-created reserved IP by Name. Configurations of the two secondary interfaces are specified in JSON format. See help text for '--network-interfaces' option.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-rip-address 10.240.128.38  --pnic-rip-auto-delete true --pnic-rip-name cli-rip1 --network-interfaces '[{"name": "cli-snic", "allow_ip_spoofing": true, "enable_infrastructure_nat": true, "interface_type": "pci", "allowed_vlans": [1, 2, 3, 4], "subnet": {"id":"2302-d368b797-2955-464b-aa42-588edd4c389f"}, "primary_ip":{"address": "10.240.128.41"}, "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}]'`
Create a bare metal server with secondary network interface with new reserved IP. Configurations of the two secondary interfaces are specified in JSON format. See help text for '--network-interfaces' option.

#### Command options
{: #command-options-bare-metal-server-create}

- **--name**: Name of the server.
- **--zone**: Name of the zone.
- **--profile**: Name of the bare metal server profile.
- **--image**: ID or name of the image.
- **--keys**: Comma-separated IDs or names of SSH keys.
- **--user-data**: data|@data-file. User data to transfer to the bare metal server.
- **--pnic-name**: Name of the primary network interface.
- **--pnic-subnet**: Subnet ID or name for the primary network interface.
- **--vpc**: ID or name of the VPC. This ID or name is only required to specify the unique subnet by name inside this VPC.
- **--pnic-rip**: ID or name of the existing reserved IP that is bound to the primary network interface.
- **--pnic-rip-address**: The IP address of the primary network interface to reserve, which must not already be reserved on the subnet.
- **--pnic-rip-auto-delete**: If set to **true**, this reserved IP of the primary network interface automatically deletes when the target is deleted. One of: **true**, **false**. (default: **true**).
- **--pnic-rip-name**: The user-defined name for this reserved IP of the primary network interface. Names must be unique within the subnet that the reserved IP resides in. Names beginning with **ibm-** are reserved for provider-owned resources.
- **--pnic-sgs**: Comma-separated security group IDs for primary network interface.
- **--pnic-allowed-vlans**: Comma-separated VLAN IDs. Indicates which VLAN IDs (for VLAN interfaces only) can use the primary network interface. It can be passed as separate values or as any range of numbers.
- **--pnic-ein**: Enable Infrastructure NAT (EIN). If **true**, the VPC infrastructure performs any needed NAT operations. If **false**, the packet is passed unmodified to or from the network interface, allowing the virtual machine that is associated with the floating IP to perform any needed NAT operations. One of: **true**, **false**. (default: **true**).
- **--pnic-ais**: Allow IP Spoofing (AIS). If **true**, source IP spoofing is allowed on packets that are using this network interface. If **false**, source IP spoofing is prevented on this interface. One of: **false**, **true**. (default: **false**).
- **--network-interfaces**: NETWORK_INTERFACES_JSON|@NETWORK_INTERFACES_JSON_FILE. Network interface configuration in JSON or JSON file. For the data schema, check the **network_interfaces** property in the [API documentation](/apidocs/vpc#create-bare-metal-server).
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
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
{: #bare-metal-server-disk}

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
{: #bare-metal-server-disks}

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
{: #bare-metal-server-network-interface}

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
Create bare metal NIC with pre-created reserved IP.
- `ibmcloud is bm-nicc cli-bm --subnet alex-subnet --name cli-snic-3 --rip cli-rip-byname3`
Create bare metal NIC with pre-created reserved IP by Name.
- `ibmcloud is bm-nicc cli-bm --subnet 2302-531ad9fc-c86a-4504-b5cf-a46981fddb5f --name cli-snic --address 10.240.128.51  --auto-delete true --ip-name cli-snicip`
Create bare metal NIC with new reserved IP.

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
{: #bare-metal-server-network-interface-floating-ip}

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
{: #bare-metal-server-network-interface-floating-ips}

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
{: #bare-metal-server-network-interfaces}

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
{: #bare-metal-server-profile}

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
{: #bare-metal-server-profiles}

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
ibmcloud is bare-metal-server-update SERVER --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-bare-metal-server-update}

- `ibmcloud is bare-metal-server-update 7d317c32-71f8-4060-9bdc-6c971b0317d4 --name my-server --output JSON`
- `ibmcloud is bare-metal-server-update my-baremetal-1 --name my-bm-server --output JSON`

#### Command options
{: #command-options-bare-metal-server-update}

- **SERVER**: ID or name of the server.
- **--name**: New name of the bare metal server.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-servers
{: #ibmcloud-is-bare-metal-servers}

List all bare metal servers.

```
ibmcloud is bare-metal-servers [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-servers}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface-reserved-ips
{: #bare-metal-server-network-interface-reserved-ips}

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
{: #bare-metal-server-network-interface-reserved-ip}

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

## Placement group
{: #placement-group}

### ibmcloud is placement-group
{: #ibmcloud-is-placement-group}

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
{: #placement-groups}

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

## Auto Scaling COMMANDS
{: #autoscaling-clis}

The following section provides information about CLI commands for auto scaling functionality.

## Instance templates
{: #instance-template}

### ibmcloud is instance-templates
{: #instance-templates}

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
{: #ibmcloud-is-instance-template}

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
ibmcloud is instance-template-create INSTANCE_TEMPLATE_NAME VPC ZONE_NAME PROFILE_NAME SUBNET (--image IMAGE | --catalog-offering CATALOG_OFFERING | --catalog-offering-version CATALOG_OFFERING_VERSION) [--total-volume-bandwidth TOTAL_VOLUME_BANDWIDTH] [--boot-volume BOOT_VOLUME_JSON | @BOOT_VOLUME_JSON_FILE] [--volume-attach VOLUME_ATTACH_JSON | @VOLUME_ATTACH_JSON_FILE] [--keys KEYS] [--dedicated-host DEDICATED_HOST | --dedicated-host-group DEDICATED_HOST_GROUP | --placement-group PLACEMENT_GROUP] [--user-data DATA] [([--sgs SGS] [--rip RIP | (--address ADDRESS --auto-delete true | false --ip-name IP_NAME)] [--allow-ip-spoofing false | true]) | --primary-network-interface PRIMARY_NETWORK_INTERFACE_JSON | @PRIMARY_NETWORK_INTERFACE_JSON_FILE] [--network-interface NETWORK_INTERFACE_JSON | @NETWORK_INTERFACE_JSON_FILE] [--metadata-service, --ms true | false ] [--host-failure-policy restart | stop] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-i, --interactive] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-template-create}

- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8`
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"name":"my-volume-name", "capacity":10, "profile": {"name": "general-purpose"},"user_tags": ["my-tag-1"]}}]'`
Create instance template with volume attachment.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"id":"67531475-bd8a-478e-bcfe-2e53365cd0aa"}}]'`
Create instance template with existing volume in volume attachment.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --keys 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
Create instance template with multiple SSH keys.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "my-boot-vol", "capacity": 150, "profile": {"name": "general-purpose"}}}'`
Create instance template with image with boot volume capacity. The capacity value can range from image's minimum provisioned size to 250
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "my-boot-vol", "profile": {"name": "general-purpose"},"user_tags": ["my-tag-1"]}}'`
Create instance template with boot volume and boot volume with user tags.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"profile": {"name": "general-purpose"},"encryption_key": {"crn": "crn:v1:bluemix:public:kms:us-south:adffc98a0f1f0f95f6613b3b752286b87:e4a29d1a-2ef0-42a6-8fd2-350deb1c647e:key:5437653b-c4b1-447f-9646-b2a2a4cd6179"}}}'`
Create instance template with encrypted boot volume.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --network-interface '[{"name": "secondary-nic", "allow_ip_spoofing": true, "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}]'`
Create instance template that is attached to secondary network interface.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "primary_ip": {"address": "10.240.129.10", "auto-delete": true, "name": "my-reserved-ip"}, "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}'`
Create instance template with primary network interface configuration in JSON.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --sgs 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --address 10.240.129.10 --auto-delete true --ip-name my-reserved-ip --allow-ip-spoofing true`
Create instance template with primary network interface configuration that includes security groups, reserved IP settings, source IP spoofing setting.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --sgs 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --reserved-ip 0711-5c7f016e-5bd2-42e3-8dff-81519e4e2469 --allow-ip-spoofing true`
Create instance template with primary network interface configuration that includes security groups, existing reserved IP, source IP spoofing setting.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host c019b1f7-c4d6-430c-aaa4-e0cc25d47277`
Create instance template to be placed in the wanted dedicated host.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host-group a4738ceb-5e59-4601-849a-61d7895740ee`
Create instance template to be placed in the wanted dedicated host group.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --placement-group 1d2afa0f-b9f2-4d85-ae35-a08885269644`
Create instance template to be placed in the wanted placement group.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --total-volume-bandwidth 4000`
Create instance template with specific total volumes bandwidth
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --metadata-service true`
Create instance template with metadata service enabled or disabled
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --host-failure-policy restart`
Create instance template with availability policy on host failure
- `ibmcloud is instance-template-create my-template-name my-vpc us-south-1 bx2-2x8 my-subnet --image ibm-ubuntu-20-04-2-minimal-amd64-1 --volume-attach '[{"volume": {"name":"my-vol-1"}}]'`
Create instance template with existing volume in volume attachment by using resource name.
- `ibmcloud is instance-template-create my-template-name my-vpc us-south-1 mx2-2x16 my-subnet --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host my-dedicated-host`
Create instance template to be placed in the wanted dedicated host by using resource name.
- `ibmcloud is instance-template-create my-template-name my-vpc us-south-1 mx2-2x16 my-subnet --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host-group my-dedicated-host-group`
Create instance template to be placed in the wanted dedicated host group by using resource name.
- `ibmcloud is instance-template-create my-template-name my-vpc us-south-1 mx2-2x16 my-subnet --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --placement-group my-placement-host-group`
Create instance template to be placed in the wanted placement group by using resource name.
- `ibmcloud is instance-template-create my-template-name my-vpc us-south-1 bx2-2x8 --image ibm-ubuntu-20-04-2-minimal-amd64-1 --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"name":"my-subnet"}, "primary_ip": {"name": "my-reserved-ip"}, "security_groups": [{"name": "my-security-group-1"}, {"name": "my-security-group-2"}]}'`
Create instance template with primary network interface configuration by using resource name.
- `ibmcloud is instance-template-create my-template-name my-vpc us-south-1 bx2-2x8 my-subnet --image ibm-ubuntu-20-04-2-minimal-amd64-1 --network-interface '[{"name": "secondary-nic", "allow_ip_spoofing": true, "subnet": {"id":"my-subnet"}, "security_groups": [{"id": "my-security-group-1"}, {"id": "my-security-group-2"}]}]'`
Create instance template that is attached to secondary network interface by using resource name.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --catalog-offering crn:v1:bluemix:public:globalcatalog-collection:global:a/efe5afc483594adaa8325e2b4d1290df:2497ae83-40cb-46ba-ac7f-5303514a2669:offering:54372a73-7a0a-4799-ac9c-8736620c67f1`
Create instance template with catalog offering.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --catalog-offering-version crn:v1:bluemix:public:globalcatalog-collection:global:a/efe5afc483594adaa8325e2b4d1290df:2497ae83-40cb-46ba-ac7f-5303514a2669:offering:54372a73-7a0a-4799-ac9c-8736620c67f1`
Create instance template with catalog offering version.
- `ibmcloud is instance-template-create --interactive`
Create instance template interactively.

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
- **--total-volume-bandwidth**: The amount of bandwidth (in megabits per second) that is allocated exclusively to instance storage volumes. An increase in this value results in a corresponding decrease to total network bandwidth.
- **--boot-volume**: BOOT_VOLUME_JSON|@BOOT_VOLUME_JSON_FILE, boot volume attachment in JSON or JSON file. For the data schema, see the **boot_volume_attachment** property in the [API documentation](/apidocs/vpc#create-instance).
- **--volume-attach**: VOLUME_ATTACH_JSON|@VOLUME_ATTACH_JSON_FILE, volume attachment in JSON or JSON file, list of volumes. For the data schema, see the **volume_attachments** property in the [API documentation](/apidocs/vpc#create-instance).
- **--keys**: Comma-separated IDs or names of SSH keys.
- **--dedicated-host**: ID or name of the host destination where the instance is placed.
- **--dedicated-host-group**: ID or name of the host group destination where the instance is placed.
- **--placement-group**: ID or name of the placement group. The placement group restrictions for the virtual server instance.
- **--user-data**: data|@data-file. User data to transfer to the virtual server instance.
- **--sgs**: Comma-separated security group IDs or names for primary network interface.
- **--rip**: ID or name of the existing reserved IP.
- **--address**: The IP address to reserve, which must not already be reserved on the subnet.
- **--auto-delete**: If set to **true**, this reserved IP automatically deletes when the target is deleted. One of: **true**, **false**. (default: **true**).
- **--ip-name**: The user-defined name for this reserved IP. Names must be unique within the subnet that the reserved IP resides in. Names beginning with **ibm-** are reserved for provider-owned resources.
- **--allow-ip-spoofing**: Disables the source and destination checks on this interface. If **false**, source IP spoofing is not allowed on this interface. One of: **false**, **true**.
- **--primary-network-interface**: PRIMARY_NETWORK_INTERFACE_JSON|@PRIMARY_NETWORK_INTERFACE_JSON_FILE, primary network interface in JSON or JSON file. For the data schema, see the **primary_network_interface** property in the [API documentation](/apidocs/vpc#create-instance).
- **--network-interface**: NETWORK_INTERFACE_JSON|@NETWORK_INTERFACE_JSON_FILE, network interface attachment in JSON or JSON file. For the data schema, see the **network_interfaces** property in the [API documentation](/apidocs/vpc#create-instance).
- **--metadata-service, --ms**: Enable or disable the Instance Metadata Service. One of: **true**, **false**.
- **--host-failure-policy**: The action to perform if the compute host experiences a failure. One of: **restart**, **stop**. (default: **restart**).
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--interactive, -i**: 
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-template-create-override-source-template
{: #instance-template-create-override-source-template}

Create an instance template by overriding a source template.

```
ibmcloud is instance-template-create-override-source-template --source-template SOURCE_TEMPLATE [--name NAME] [--profile PROFILE] [--zone ZONE] [--vpc VPC] [--image IMAGE | --catalog-offering CATALOG_OFFERING | --catalog-offering-version CATALOG_OFFERING_VERSION] [--total-volume-bandwidth TOTAL_VOLUME_BANDWIDTH] [--boot-volume BOOT_VOLUME_JSON | @BOOT_VOLUME_JSON_FILE] [--volume-attach VOLUME_ATTACH_JSON | @VOLUME_ATTACH_JSON_FILE] [--keys KEYS] [--dedicated-host DEDICATED_HOST | --dedicated-host-group DEDICATED_HOST_GROUP | --placement-group PLACEMENT_GROUP] [--user-data DATA] [(--subnet SUBNET [--rip RIP | (--address ADDRESS --auto-delete true | false --ip-name IP_NAME)] [--sgs SGS] [--allow-ip-spoofing false | true]) | --primary-network-interface PRIMARY_NETWORK_INTERFACE_JSON | @PRIMARY_NETWORK_INTERFACE_JSON_FILE] [--network-interface NETWORK_INTERFACE_JSON | @NETWORK_INTERFACE_JSON_FILE] [--metadata-service, --ms true | false ] [--host-failure-policy restart | stop] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-template-create-override-source-template}

- `ibmcloud is instance-template-create-override-source-template --source-template e4a29d1a-2ef0-42a6-8fd2-350deb1c647e`
Create instance template copying from a source template
- `ibmcloud is instance-template-create-override-source-template --source-template e4a29d1a-2ef0-42a6-8fd2-350deb1c647e --name my-template-name --image r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --profile bx2-2x8`
Create instance template by overriding a source template and providing overriding options
- `ibmcloud is instance-template-create-override-source-template --source-template my-template --name my-instance  --subnet my-subnet --image ibm-ubuntu-20-04-2-minimal-amd64-1 --volume-attach '[{"volume": {"name":"my-vol-1"}}]'`
Create instance template by overriding a source template with existing volume in volume attachment by using resource name.
- `ibmcloud is instance-template-create-override-source-template --source-template my-template --name my-instance --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"name":"my-subnet"}, "primary_ip": {"name": "my-reserved-ip"}, "security_groups": [{"name": "my-security-group-1"}, {"name": "my-security-group-2"}]}'`
Create instance template by overriding a source template with primary network interface configuration by using resource name.

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
- **--total-volume-bandwidth**: The amount of bandwidth (in megabits per second) that is allocated exclusively to instance storage volumes. An increase in this value results in a corresponding decrease to total network bandwidth.
- **--boot-volume**: BOOT_VOLUME_JSON|@BOOT_VOLUME_JSON_FILE, boot volume attachment in JSON or JSON file. For the data schema, see the **boot_volume_attachment** property in the [API documentation](/apidocs/vpc#create-instance).
- **--volume-attach**: VOLUME_ATTACH_JSON|@VOLUME_ATTACH_JSON_FILE, volume attachment in JSON or JSON file, list of volumes. For the data schema, see the **volume_attachments** property in the [API documentation](/apidocs/vpc#create-instance).
- **--keys**: Comma-separated IDs or names of SSH keys.
- **--dedicated-host**: ID or name of the host destination where the instance is placed.
- **--dedicated-host-group**: ID or name of the host group destination where the instance is placed.
- **--placement-group**: ID or name of the placement group. The placement group restrictions for the virtual server instance.
- **--user-data**: data|@data-file. User data to transfer to the virtual server instance.
- **--subnet**: ID or name of the subnet.
- **--rip**: ID or name of the existing reserved IP.
- **--address**: The IP address to reserve, which must not already be reserved on the subnet.
- **--auto-delete**: If set to **true**, this reserved IP automatically deletes when the target is deleted. One of: **true**, **false**. (default: **true**).
- **--ip-name**: The user-defined name for this reserved IP. Names must be unique within the subnet that the reserved IP resides in. Names beginning with **ibm-** are reserved for provider-owned resources.
- **--sgs**: Comma-separated security group IDs or names for primary network interface.
- **--allow-ip-spoofing**: Disables the source and destination checks on this interface. If **false**, source IP spoofing is not allowed on this interface. One of: **false**, **true**.
- **--primary-network-interface**: PRIMARY_NETWORK_INTERFACE_JSON|@PRIMARY_NETWORK_INTERFACE_JSON_FILE, primary network interface in JSON or JSON file. For the data schema, see the **primary_network_interface** property in the [API documentation](/apidocs/vpc#create-instance).
- **--network-interface**: NETWORK_INTERFACE_JSON|@NETWORK_INTERFACE_JSON_FILE, network interface attachment in JSON or JSON file. For the data schema, see the **network_interfaces** property in the [API documentation](/apidocs/vpc#create-instance).
- **--metadata-service, --ms**: Enable or disable the Instance Metadata Service. One of: **true**, **false**.
- **--host-failure-policy**: The action to perform if the compute host experiences a failure. One of: **restart**, **stop**.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
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
{: #instance-groups}

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
{: #ibmcloud-is-instance-group}

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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
- **--vpc**: ID or name of the VPC. It is only required to specify the unique resource by name inside this VPC.
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
ibmcloud is instance-group-load-balancer-delete INSTANCE_GROUP [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-load-balancer-delete}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-managers
{: #instance-group-managers}

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
{: #instance-group-manager}

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
ibmcloud is instance-group-manager-delete INSTANCE_GROUP (MANAGER1 MANAGER2 ...) [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-manager-delete}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **MANAGER1**: ID or name of the manager.
- **MANAGER2**: ID or name of the manager.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager-actions
{: #instance-group-manager-actions}

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
{: #instance-group-manager-action}

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
{: #instance-group-manager-policies}

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
{: #instance-group-manager-policy}

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
{: #instance-group-membership}

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
{: #instance-group-memberships}

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
ibmcloud is instance-group-memberships-delete INSTANCE_GROUP [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-memberships-delete}

- **INSTANCE_GROUP**: ID or name of the instance group.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

## REGIONS & ZONES COMMANDS
{: #geography}

The following section provides information about CLI commands for working with regions and zones.

## Regions
{: #regions}

### ibmcloud is region
{: #region}

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
{: #ibmcloud-is-regions}

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
{: #zone}

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
{: #ibmcloud-is-zones}

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
{: #volumes}

List all volumes.

```
ibmcloud is volumes [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-volumes}

- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is volume
{: #volume}

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

- **VOLUME**: ID or Name of the volume.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is volume-create
{: #volume-create}

Create a volume.

```
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--capacity CAPACITY] [--iops IOPS] [--encryption-key ENCRYPTION_KEY] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--tags  TAG_NAME1,TAG_NAME2,...] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-volume-create}

- `ibmcloud is volume-create my-volume general-purpose us-south-1`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --capacity 500`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --iops 10000 --capacity 1000`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --tags env:test`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --tags env:test,env:dev`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --encryption-key crn:v1:bluemix:public:kms:us-south:adffc98a0f1f0f95f6613b3b752286b87:e4a29d1a-2ef0-42a6-8fd2-350deb1c647e:key:5437653b-c4b1-447f-9646-b2a2a4cd6179`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --resource-group-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --resource-group-name Default`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --output JSON`

#### Command options
{: #command-options-volume-create}

- **VOLUME_NAME**: Name of the volume.
- **PROFILE_NAME**: Name of the profile.
- **ZONE_NAME**: Name of the zone.
- **--capacity**: The capacity of the volume in gigabytes. Range 10-16000 for custom and general-purpose profile volumes, 10-9600 for 5iops-tier profile volumes, 10-4800 for 10iops-tier profile volumes. (default: **100**).
- **--iops**: Input/Output Operations Per Second for the volume, it is only applicable for custom profile volumes. For the IOPS range, refer to [Onboarding software to your account](docs/vpc?topic=vpc-block-storage-profiles#custom).
- **--encryption-key**: The CRN of the Key Management Service root key.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--tags**: Tags for this resource.
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

- **VOLUME1**: ID or Name of the volume.
- **VOLUME2**: ID or Name of the volume.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is volume-profiles
{: #volume-profiles}

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
{: #volume-profile}

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
ibmcloud is volume-update VOLUME [--name NAME | --capacity CAPACITY | --profile PROFILE | --iops IOPS] [--tags  TAG_NAME1,TAG_NAME2,...] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-volume-update}

- `ibmcloud is volume-update 64bec87d-d175-4fa5-b240-b092fdbcedd6 --name my-volume --output JSON`
- `ibmcloud is volume-update 64bec87d-d175-4fa5-b240-b092fdbcedd6 --capacity 250 --output JSON`
- `ibmcloud is volume-update my-volume-demo-1 --name my-volume --output JSON`
- `ibmcloud is volume-update my-volume-demo-1 --capacity 250`
- `ibmcloud is volume-update 64bec87d-d175-4fa5-b240-b092fdbcedd6 --profile 10iops-tier`
- `ibmcloud is volume-update 64bec87d-d175-4fa5-b240-b092fdbcedd6 --iops 5000`
- `ibmcloud is volume-update a9647a52-06f8-4b19-b904-920f67dcdfcd --capacity 500 --tags env:test`
- `ibmcloud is volume-update a9647a52-06f8-4b19-b904-920f67dcdfcd --capacity 500 --tags env:test,env:dev`

#### Command options
{: #command-options-volume-update}

- **VOLUME**: ID or Name of the volume.
- **--name**: New name of the volume.
- **--capacity**: The capacity of the volume in gigabytes. Capacity can be expanded up to 250 for boot volume, 16000 for custom and general-purpose profile volumes, 9600 for **5iops-tier** profile volumes and 4800 for **10iops-tier** profile volumes. Size can be only increased, not decreased.
- **--profile**: Name of the profile. The volume must be attached as data volume and be switched between IOPS tiers. Changing predefined IOPS tier prorfile to custom profile is not supported. Changing custom profile to predefined IOPS tier profile is not supported.
- **--iops**: Input/Output Operations Per Second for the volume, it is only applicable for custom profile volumes. For the IOPS range, refer to [Onboarding software to your account](docs/vpc?topic=vpc-block-storage-profiles#custom).. The volume must be attached as data volume.
- **--tags**: Tags for this resource.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Snapshots
{: #snapshots-cli}

The following section provides information about CLI commands for snapshots.

### ibmcloud is snapshots
{: #snapshots}

List all snapshots.

```
ibmcloud is snapshots [--volume VOLUME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-snapshots}

- **--volume**: ID or Name of the volume to snapshot.
- **--resource-group-id**: ID of the resource group. This ID is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This name is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot
{: #snapshot}

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

- **SNAPSHOT**: ID or Name of the snapshot.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-create
{: #snapshot-create}

Create a snapshot from a volume.

```
ibmcloud is snapshot-create --volume VOLUME [--name NAME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--tags  TAG_NAME1,TAG_NAME2,...] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshot-create}

- `ibmcloud is snapshot-create --name my-snapshot-1 --volume test5-3zwxlnzgqk-9vk99`
- `ibmcloud is snapshot-create --name my-snapshot --volume r006-1772e102-0671-48c7-a97a-504247e61e48`
- `ibmcloud is snapshot-create --name my-snapshot --volume r006-1772e102-0671-48c7-a97a-504247e61e48 --resource-group-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is snapshot-create --name my-snapshot --volume r006-1772e102-0671-48c7-a97a-504247e61e48 --resource-group-name Default`
- `ibmcloud is snapshot-create --name my-snapshot --volume r006-1772e102-0671-48c7-a97a-504247e61e48 --output JSON`
- `ibmcloud is snapshot-create --volume cf88cf1a-6f93-4cf6-bacf-62cafd3de857 --name my-ss70 --tags env:test`
- `ibmcloud is snapshot-create --volume cf88cf1a-6f93-4cf6-bacf-62cafd3de857 --name my-ss70 --tags env:test,env:dev`
- `ibmcloud is snapshot-create --volume test5-3zwxlnzgqk-9vk99 --name my-ss70 --tags env:test`

#### Command options
{: #command-options-snapshot-create}

- **--volume**: ID or Name of the volume to snapshot.
- **--name**: New name for the snapshot.
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

- **SNAPSHOT1**: ID or Name of the snapshot.
- **SNAPSHOT2**: ID or Name of the snapshot.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-update
{: #snapshot-update}

Update a snapshot.

```
ibmcloud is snapshot-update SNAPSHOT --name NEW_NAME [--tags  TAG_NAME1,TAG_NAME2,...] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshot-update}

- `ibmcloud is snapshot-update 64bec87d-d175-4fa5-b240-b092fdbcedd6 --name my-snapshot --output JSON`
- `ibmcloud is snapshot-update cli-demo-snapshot-1 --name my-snapshot --output JSON`
- `ibmcloud is snapshot-update f8d51ab0-961f-4c23-8976-b1e48cc4f260 --name mysnapshot60 --tags env:tfp`
- `ibmcloud is snapshot-update f8d51ab0-961f-4c23-8976-b1e48cc4f260 --name mysnapshot60 --tags env:tfp,env:cli`
- `ibmcloud is snapshot-update my-snapshot-2 --name mysnapshot60 --tags env:tfp`

#### Command options
{: #command-options-snapshot-update}

- **SNAPSHOT**: ID or Name of the snapshot.
- **--name**: New name of the snapshot.
- **--tags**: Tags for this resource.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Backup policy
{: #backup-policy}

The following section provides information about CLI commands for backup policies

### ibmcloud is backup-policies
{: #backup-policies}

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
ibmcloud is backup-policy-create --match-tags MATCH_TAGS [--name NAME] [[--plans PLANS_JSON | @PLANS_JSON_FILE] | --plan-cron-spec PLAN_CRON_SPEC [--plan-name PLAN_NAME] --plan-active [--plan-attach-tags PLAN_ATTACH_TAGS] [--plan-copy-tags true | false] [[--plan-delete-after PLAN_DELETE_AFTER] [--plan-delete-over-count PLAN_DELETE_OVER_COUNT]]] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-backup-policy-create}

- `ibmcloud is backup-policy-create --match-tags dev:test --name demo-bkp-policy-1 --plan-name demo-bkp-plan-1 --plan-cron-spec '45 09 * * *'`
- `ibmcloud is backup-policy-create --match-tags dev:test --name demo-bkp-policy-2 --plan-name demo-bkp-plan-2 --plan-attach-tags dev:test --plan-copy-tags false --plan-delete-after 60 --plan-cron-spec '40 09 * * *'`
- `ibmcloud is backup-policy-create --match-tags dev:test --name demo-bkp-policy-x1`
- `ibmcloud is backup-policy-create --match-tags dev:test --name demo-bkp-policy-x --plan-name demo-bkp-plan-2 --plan-attach-tags dev:test --plan-copy-tags false --plan-delete-after 60 --plan-cron-spec '45 09 * * *' --plan-active  --plan-delete-over-count 2`
- `ibmcloud is backup-policy-create --match-tags dev:test --name backup-policy-z  --plans '[{"active":true,"attach_user_tags":["my-daily-backup-plan"],"copy_user_tags":true,"cron_spec":"*/51,2,3***","deletion_trigger":{"delete_after":20,"delete_over_count":20},"name":"my-policy-plan"},{"active":true,"attach_user_tags":["my-daily-backup-plan"],"copy_user_tags":true,"cron_spec":"*/51,2,3***","deletion_trigger":{"delete_after":20,"delete_over_count":20},"name":"my-policy-plan-99"}]'`
- `ibmcloud is backup-policy-create --match-tags dev:test --name backup-policy-x2  --plans @plans.json`

#### Command options
{: #command-options-backup-policy-create}

- **--name**: New name for the backup policy.
- **--match-resource-type**: A resource type this backup policy applies to. One of: **Volume**.
- **--match-tags**: The user tags this backup policy applies to.
- **--plans**: PLANS_JSON|@PLANS_JSON_FILE, plans in JSON or JSON file, list of policy plans. For the data schema, check the **plans** property in the [API documentation](/apidocs/vpc#create-backup-policy). One of: **PLANS_JSON**, **@PLANS_JSON_FILE**.
- **--plan-name**: Name of the backup policy plan.
- **--plan-active**: Indicates whether the plan is active.
- **--plan-attach-tags**: User tags to attach to each resource created by this plan.
- **--plan-copy-tags**: Indicates whether to copy the source user tags to the created resource. One of: **true**, **false**.
- **--plan-cron-spec**: The cron specification for the backup schedule.
- **--plan-delete-after**: The maximum number of days to keep each backup after creation. (default: **30**).
- **--plan-delete-over-count**: The maximum number of recent backups to keep. If unspecified, all backups are kept.
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
ibmcloud is backup-policy-update POLICY [--match-tags MATCH_TAGS] [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-backup-policy-update}

- `ibmcloud is backup-policy-update r134-aa88726e-8b34-4f97-992d-027df9c4bb36 --name my-policy2`
- `ibmcloud is backup-policy-update demo-policy-99 --name demo-policy-100`
- `ibmcloud is backup-policy-update backup-policy-1001 --match-tags demo:cli`

#### Command options
{: #command-options-backup-policy-update}

- **POLICY**: ID or name of the backup policy.
- **--match-tags**: The user tags this backup policy applies to.
- **--name**: New name of the backup policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is backup-policy
{: #ibmcloud-is-backup-policy}

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
{: #backup-policy-plan}

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
{: #backup-policy-plans}

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
ibmcloud is backup-policy-plan-create POLICY --cron-spec CRON_SPEC [--name NAME] [--active] [--attach-tags ATTACH_TAGS] [--copy-tags true | false] [[--delete-after DELETE_AFTER] [--delete-over-count DELETE_OVER_COUNT]] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-backup-policy-plan-create}

- `ibmcloud is backup-policy-plan-create c9a0e8d9-c592-4175-80cb-3056f6fd1da7 --attach-tags dev:test --copy-tags true --cron-spec '*/5 1,2,3 * * *' --delete-after 80 --name my-policy-plan-1`
- `ibmcloud is backup-policy-plan-create c9a0e8d9-c592-4175-80cb-3056f6fd1da7  --cron-spec '*/5 1,2,3 * * *'  --name my-policy-plan-2`
- `ibmcloud is backup-policy-plan-create backup-policy-1001 --cron-spec '0 0 * * *' --active --name my-policy-plan --attach-tags my-daily-backup-plan --copy-tags true --delete-after 10 --delete-over-count 2`

#### Command options
{: #command-options-backup-policy-plan-create}

- **POLICY**: ID or name of the backup policy.
- **--name**: Name of the backup policy plan.
- **--active**: Indicates whether the plan is active.
- **--attach-tags**: User tags to attach to each resource created by this plan.
- **--copy-tags**: Indicates whether to copy the source user tags to the created resource. One of: **true**, **false**.
- **--cron-spec**: The cron specification for the backup schedule.
- **--delete-after**: The maximum number of days to keep each backup after creation.
- **--delete-over-count**: The maximum number of recent backups to keep. If unspecified, all backups are kept.
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
ibmcloud is backup-policy-plan-update POLICY PLAN [--name NAME] [--active] [--attach-tags ATTACH_TAGS] [--copy-tags true | false] [--cron-spec CRON_SPEC] [[--delete-after DELETE_AFTER] [--delete-over-count DELETE_OVER_COUNT]] [--reset-delete-over-count] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-backup-policy-plan-update}

- `ibmcloud is backup-policy-plan-update r134-77e21079-7291-44c2-866a-8f1848bc10f0 r134-fc8e15d9-02f2-4599-a216-8afe0dfeb969 --name myplan`
- `ibmcloud is backup-policy-plan-update demo-bkp-policy-b98 my-policy-plan-1 --name cli-demo-policy-plan-3`
- `ibmcloud is backup-policy-plan-update backup-policy-1001 2dae356e-f7b5-48dd-8bc3-f3083574885b --cron-spec '42 10 * * *' --name my-policy-plan-1 --attach-tags my-daily-backup-plan --copy-tags false --delete-after 20 --delete-over-count 1`
- `ibmcloud is backup-policy-plan-update demo-bkp-policy-x demo-bkp-plan-2 --reset-delete-over-count`

#### Command options
{: #command-options-backup-policy-plan-update}

- **POLICY**: ID or name of the backup policy.
- **PLAN**: ID or name of the backup policy plan.
- **--name**: New name of the backup policy plan.
- **--active**: Indicates whether the plan is active.
- **--attach-tags**: User tags to attach to each resource created by this plan.
- **--copy-tags**: Indicates whether to copy the source user tags to the created resource. One of: **true**, **false**.
- **--cron-spec**: The cron specification for the backup schedule.
- **--delete-after**: The maximum number of days to keep each backup after creation.
- **--delete-over-count**: The maximum number of recent backups to keep. If unspecified, all backups are kept.
- **--reset-delete-over-count**: Remove any existing maximum number of recent backups to keep.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is backup-policy-jobs
{: #backup-policy-jobs}

List all jobs for the backup policy.

```
ibmcloud is backup-policy-jobs POLICY [--source SOURCE] [--snapshots SNAPSHOT1,SNAPSHOT2, ...] [--snapshots-crns SNAPSHOT1_CRN,SNAPSHOT2_CRN, ...] [--status failed | running | succeeded] [--plan PLAN] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-backup-policy-jobs}

- `ibmcloud is backup-policy-jobs backup-policy-1001`
- `ibmcloud is backup-policy-jobs r134-7759199b-bc1f-448e-84fa-2aa42bde29af`
- `ibmcloud is backup-policy-jobs r134-0703cdf1-48bb-4af2-9ceb-1edbe8fcb818 --volume r134-1a1e25f2-3fc3-4507-8725-e5f1d07256ea --snapshot r143-1a1e25f2-3fc3-4507-8725-e5f1d08956ea --status running --plan r136-3a3e25f2-3fc3-4507-8725-e5f1d08496ea`
- `ibmcloud is backup-policy-jobs bkp-policy-do-not-delete --snapshots r134-f1d9b974-14e5-4a2e-8e38-c023164be316,r134-b11f1540-288d-4331-97ab-f565ca15a3b8,r134-ab3147a3-715f-4017-8fed-ea3ddadeeb1d,r134-435b8414-dae2-4026-847f-a73162105e5f`
- `ibmcloud is backup-policy-jobs bkp-policy-do-not-delete --snapshots bkp-plan-do-not-delete-31addff28e2b-422b,bkp-plan-do-not-delete-f37bc1f19123-4995`
- `ibmcloud is backup-policy-jobs bkp-policy-do-not-delete --snapshots-crns  crn:v1:staging:public:is:us-south:a/efe5afc483594adaa8325e2b4d1290df::snapshot:r134-c4ea5585-0554-40db-bdc8-1ec9fb15098b,crn:v1:staging:public:is:us-south:a/efe5afc483594adaa8325e2b4d1290df::snapshot:r134-c10755ee-db71-472e-bf80-01e21229fda0`
- `ibmcloud is backup-policy-jobs bkp-policy-do-not-delete  --source r134-71757aee-5e90-40f5-bd7d-0a538c084efb`

#### Command options
{: #command-options-backup-policy-jobs}

- **POLICY**: ID or name of the backup policy.
- **--source**: ID or name of the source volume. Source name can be used only if the source exists inside the VPC.
- **--snapshots**: ID or name of target snapshots.
- **--snapshots-crns**: CRNs of the target snapshots.
- **--status**: Status of the backup policy job. One of: **failed**, **running**, **succeeded**.
- **--plan**: ID or name of backup policy plan.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is backup-policy-job
{: #backup-policy-job}

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
