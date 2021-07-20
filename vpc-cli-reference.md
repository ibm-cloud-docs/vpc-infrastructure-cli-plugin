---

copyright:
  years: 2018, 2021
lastupdated: "2021-07-20"

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

# VPC CLI reference
{: #vpc-reference}

Use the following information as a reference of the command-line interface (CLI) commands that are available for {{site.data.keyword.vpc_full}} (VPC).
{:shortdesc}

This document is organized into the following sections:
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

  To update:

  ```
  ibmcloud plugin update
  ```
  {: pre}

  To view installed plug-ins and versions:

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
ibmcloud is floating-ip-reserve FLOATING_IP_NAME (--zone ZONE_NAME | --nic-id NIC_ID) [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-floating-ip-reserve}

- `ibmcloud is floating-ip-reserve my-ip --zone us-south-1`
- `ibmcloud is floating-ip-reserve my-ip --nic-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is floating-ip-reserve my-ip --nic-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --output JSON`

#### Command options
{: #command-options-floating-ip-reserve}

- **FLOATING_IP_NAME**: Name of the floating IP.
- **--zone**: Name of the target zone. This option is mutually exclusive with **--nic-id**.
- **--nic-id**: ID of the target network interface. This option is mutually exclusive with **--zone**.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is floating-ip-update
{: #floating-ip-update}

Update a floating IP.

```
ibmcloud is floating-ip-update FLOATING_IP [--name NEW_NAME] [--nic-id NIC_ID] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-floating-ip-update}

- `ibmcloud is floating-ip-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-ip`
- `ibmcloud is floating-ip-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --nic-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is floating-ip-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --nic-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --output JSON`

#### Command options
{: #command-options-floating-ip-update}

- **FLOATING_IP**: ID of the floating IP.
- **--name**: New name of the floating IP.
- **--nic-id**: ID of the network interface to bind.
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

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
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
ibmcloud is flow-log-create --bucket STORAGE_BUCKET_NAME --target TARGET_ID [--name NAME] [--active TRUE | FALSE] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-flow-log-create}

- `ibmcloud is flow-log-create --bucket bucket-name --target 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is flow-log-create --bucket bucket-name --target 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-flow-log`
- `ibmcloud is flow-log-create --bucket bucket-name --target 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-flow-log --active false`
- `ibmcloud is flow-log-create --bucket bucket-name --target 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-flow-log --output JSON`

#### Command options
{: #command-options-flow-log-create}

- **--bucket**: Name of COS bucket.
- **--target**: The target for flow log.
- **--name**: New name for the flow log.
- **--active**: Indicates whether this collector is active. One of: **TRUE**, **FALSE**.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is flow-log-delete
{: #flow-log-delete}

Delete flow logs.

```
ibmcloud is flow-log-delete (FLOW_LOG1 FLOW_LOG2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-flow-log-delete}

- **FLOW_LOG1**: ID of the flow log.
- **FLOW_LOG2**: ID of the flow log.
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
- `ibmcloud is flow-log-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name-flow-log --active false`
- `ibmcloud is flow-log-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name-flow-log --output JSON`

#### Command options
{: #command-options-flow-log-update}

- **FLOW_LOG**: ID of the flow log.
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

- **FLOW_LOG**: ID of the flow log.
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

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Application load balancers
{: #alb-anchor}

The following section provides information about CLI commands for working with application load balancers, listeners, and pools.

### ibmcloud is load-balancer
{: #load-balancer}

View details of a load balancer.

```
ibmcloud is load-balancer LOAD_BALANCER_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-create
{: #load-balancer-create}

Create a load balancer.

```
ibmcloud is load-balancer-create LOAD_BALANCER_NAME LOAD_BALANCER_TYPE (--subnet SUBNET_ID1 --subnet SUBNET_ID2 ...) [--family application | network] [--security-group SECURITY_GROUP1 --security-group SECURITY_GROUP2 ...] [--logging-datapath-active false | true] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-create}

- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --family network`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --resource-group-id fee82deba12e4c0fb69c3b09d1f12345`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --resource-group-name Default`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --output JSON`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --security-group 3428abaa-788b-439b-9404-ca386f2f3f79 --security-group f0e26f91-851a-4fc9-b32b-da24ad218b4e`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --logging-datapath-active true`

#### Command options
{: #command-options-load-balancer-create}

- **LOAD_BALANCER_NAME**: Name of the load balancer.
- **LOAD_BALANCER_TYPE**: Type of the load balancer, **public** or **private**.
- **--subnet**: ID of the subnets to provision this load balancer. This option can be specified multiple times to provision load balancer in multiple subnets. Only one subnet can be specified for network load balancer.
- **--family**: The load balancer family type. One of: **application**, **network**.
- **--security-group**: ID of the security group.
- **--logging-datapath-active**: Enable or disable datapath logging for this load balancer. If unspecified, datapath logging is disabled. This is applicable only for application load balancer. One of: **false**, **true**.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-delete
{: #load-balancer-delete}

Delete load balancers.

```
ibmcloud is load-balancer-delete (LOAD_BALANCER_ID1 LOAD_BALANCER_ID2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-delete}

- **LOAD_BALANCER_ID1**: ID of the load balancer.
- **LOAD_BALANCER_ID2**: ID of the load balancer.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener
{: #load-balancer-listener}

View details of a load balancer listener.

```
ibmcloud is load-balancer-listener LOAD_BALANCER_ID LISTENER_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-create
{: #load-balancer-listener-create}

Create a load balancer listener.

```
ibmcloud is load-balancer-listener-create LOAD_BALANCER_ID PORT PROTOCOL [--default-pool DEFAULT_POOL_ID] [--connection-limit LIMIT] [--certificate-instance-crn CERTIFICATE_INSTANCE_CRN] [--policies LISTENER_POLICIES_JSON | @LISTENER_POLICIES_JSON_FILE] [--accept-proxy-protocol false | true] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-listener-create}

- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 https --certificate-instance-crn crn:v1:bluemix:public:cloudcerts:us-south:a/123456:b8866ea4-b8df-467e-801a-da1db7e020bf:certificate:78ff9c4c97d013fb2a95b21dddde7758`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --connection-limit 2000`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --default-pool 70294e14-4e61-11e8-bcf4-0242ac110004`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --policies '[{"name": "my-policy", "priority": 5, "action": "reject" }]'`
The priority of the policy can have a range of 1 to 10, where a lower value indicates a higher priority. The possible values for _action_ are "forward", "redirect", or "reject".
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --policies '[{"priority": 5, "action": "forward", "target": { "id": 70294e14-4e61-11e8-bcf4-0242ac110004 }}]'`
When the action is _forward_, the pool identity is required to specify which pool the load balancer forwards the traffic to.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --policies '[{"priority": 5, "action": "redirect", "target": { "http_status_code": 301, "url": "https://www.redirect.com"}}]'`
When the action is _redirect_, the "url" and "http_status_code" are required. Possible values for _http_status_code_ are "301", "302", "303", "307", or "308". The "url" is the redirect target URL.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --policies '[{"priority": 5, "action": "reject", "rules": { "condition": "equals", "type": "header", "field": "My-app-header", "value": "value"}}]'`
Possible values for _condition_ are "contains", "equals", or "matches_regex". Possible values for _type_ are "header", "hostname", or "path". _field_ is an HTTP header field that is applicable only to the "header" rule type. The _value_ parameter is the value to match the rule condition.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --output JSON`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --accept-proxy-protocol true`

#### Command options
{: #command-options-load-balancer-listener-create}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **PORT**: The listener port number. Range 1-65535.
- **PROTOCOL**: The listener protocol. Load balancers in the application family support tcp, http, and https. Load balancers in the network family support tcp.
- **--default-pool**: ID of the default pool.
- **--connection-limit**: The maximum number of connections of the listener. This option is not applicable for the load balancers in the network family.
- **--certificate-instance-crn**: CRN of the certificate instance. Required when protocol is **https**. This option is not applicable for the load balancers in the network family.
- **--policies**: **LISTENER_POLICIES_JSON** | **@LISTENER_POLICIES_JSON_FILE**, listener policies in JSON or JSON file. This option is not applicable for the load balancers in the network family.
- **--accept-proxy-protocol**: If set to true, proxy protocol is enabled for this listener. Only supported for application load balancers. One of: **false**, **true**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-delete
{: #load-balancer-listener-delete}

Delete load balancer listeners.

```
ibmcloud is load-balancer-listener-delete LOAD_BALANCER_ID (LISTENER_ID1 LISTENER_ID2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener-delete}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID1**: ID of the listener.
- **LISTENER_ID2**: ID of the listener.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policies
{: #load-balancer-listener-policies}

List all load balancer policies.

```
ibmcloud is load-balancer-listener-policies LOAD_BALANCER_ID LISTENER_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener-policies}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy
{: #load-balancer-listener-policy}

View details of load balancer listener policy.

```
ibmcloud is load-balancer-listener-policy LOAD_BALANCER_ID LISTENER_ID POLICY_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener-policy}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY_ID**: ID of the policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-create
{: #load-balancer-listener-policy-create}

Create a load balancer listener policy.

```
ibmcloud is load-balancer-listener-policy-create LOAD_BALANCER_ID LISTENER_ID --priority PRIORITY (--action forward | redirect | reject) [--name NEW_NAME] [(--target-http-status-code TARGET_HTTP_STATUS_CODE --target-url TARGET_URL) | --target-id TARGET_ID] [--rules LISTENER_POLICY_RULES_JSON | @LISTENER_POLICY_RULES_JSON_FILE] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-listener-policy-create}

- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-policy --action reject --priority 5`
The priority of the policy can have a range of 1 to 10, where a lower value indicates a higher priority. The possible values for _action_ are "forward", "redirect", or "reject".
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action forward --priority 2 --target-id 70294e14-4e61-11e8-bcf4-0242ac110004`
When the action is _forward_, the pool identity is required to specify which pool the load balancer forwards the traffic to.
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action redirect --priority 1 --target-http-status-code 301 --target-url "https://www.redirect.com"`
When the action is _redirect_, the "url" and "http_status_code" are required. Possible values for _http_status_code_ are "301", "302", "303", "307", or "308". The "url" is the redirect target URL.
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action reject --priority 4 --rules '[{"rules": { "condition": "equals", "type": "header", "field": "My-app-header", "value": "value"}}]'`
Possible values for _condition_ are "contains", "equals", or "matches_regex". Possible values for _type_ are "header", "hostname", or "path". _field_ is an HTTP header field that is applicable only to the "header" rule type. The _value_ parameter is the value to match the rule condition.
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action reject --priority 3 --name my-policy --output JSON`

#### Command options
{: #command-options-load-balancer-listener-policy-create}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--priority**: Priority of the policy. Lower value indicates higher priority, for example: **5**, range: [**1-10**].
- **--action**: The policy action. One of: **forward**, **redirect**, **reject**.
- **--name**: The new name of the policy.
- **--target-id**: The unique identifier for this load balancer pool that is specified with **forward** action.
- **--target-http-status-code**: The HTTP status code in the redirect response, one of [**301**, **302**, **303**, **307**, **308**], specified with **redirect** action.
- **--target-url**: The redirect target URL, specified with **redirect** action.
- **--rules**: **LISTENER_POLICY_RULES_JSON** | **@LISTENER_POLICY_RULES_JSON_FILE**, listener policy rules in JSON or JSON file.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-delete
{: #load-balancer-listener-policy-delete}

Delete policies from a load balancer listener.

```
ibmcloud is load-balancer-listener-policy-delete LOAD_BALANCER_ID LISTENER_ID (POLICY_ID1 POLICY_ID2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener-policy-delete}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY_ID1**: ID of the policy.
- **POLICY_ID2**: ID of the policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-rule
{: #load-balancer-listener-policy-rule}

List single load balancer policy rule.

```
ibmcloud is load-balancer-listener-policy-rule LOAD_BALANCER_ID LISTENER_ID POLICY_ID RULE_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener-policy-rule}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY_ID**: ID of the policy.
- **RULE_ID**: ID of the rule.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-rule-create
{: #load-balancer-listener-policy-rule-create}

Create a load balancer listener policy rule.

```
ibmcloud is load-balancer-listener-policy-rule-create LOAD_BALANCER_ID LISTENER_ID POLICY_ID (--condition contains | equals | matches_regex) (--type header | hostname | path | query | body) --value VALUE [--field FIELD] [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-load-balancer-listener-policy-rule-create}

- `ibmcloud is load-balancer-listener-policy-rule-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --condition equals --type header --field my-app-header --value  match-value --output JSON`

#### Command options
{: #command-options-load-balancer-listener-policy-rule-create}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY_ID**: ID of the policy.
- **--condition**: The condition of the rule. One of: **contains**, **equals**, **matches_regex**.
- **--type**: The type of the rule. One of: **header**, **hostname**, **path**, **query**, **body**.
- **--value**: Value to match the rule condition.
- **--field**: The HTTP field. This field is applicable to "header", "query", and "body" rule types. For rule type "header", this field is required. For rule types "query" or "body", this field is optional.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-rule-delete
{: #load-balancer-listener-policy-rule-delete}

Delete policies from a load balancer listener.

```
ibmcloud is load-balancer-listener-policy-rule-delete LOAD_BALANCER_ID LISTENER_ID POLICY_ID (RULE_ID1 RULE_ID2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener-policy-rule-delete}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY_ID**: ID of the policy.
- **RULE_ID1**: ID of the rule.
- **RULE_ID2**: ID of the rule.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-rule-update
{: #load-balancer-listener-policy-rule-update}

Update a rule of a load balancer listener policy.

```
ibmcloud is load-balancer-listener-policy-rule-update LOAD_BALANCER_ID LISTENER_ID POLICY_ID RULE_ID [--condition contains | equals | matches_regex] [--type header | hostname | path | query | body] [--value VALUE] [--field FIELD] [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-load-balancer-listener-policy-rule-update}

- `ibmcloud is load-balancer-listener-policy-rule-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 70294e14-4e61-11e8-bcf4-0242ac110004 --condition equals --type header --field my-app-header --value  match-value --output JSON`

#### Command options
{: #command-options-load-balancer-listener-policy-rule-update}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY_ID**: ID of the policy.
- **RULE_ID**: ID of the rule.
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
ibmcloud is load-balancer-listener-policy-rules LOAD_BALANCER_ID LISTENER_ID POLICY_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listener-policy-rules}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY_ID**: ID of the policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-policy-update
{: #load-balancer-listener-policy-update}

Update a policy of a load balancer listener.

```
ibmcloud is load-balancer-listener-policy-update LOAD_BALANCER_ID LISTENER_ID POLICY_ID [--name NEW_NAME] [--priority PRIORITY] [--target-id TARGET_ID] [--target-http-status-code TARGET_HTTP_STATUS_CODE] [--target-url TARGET_URL] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-listener-policy-update}

- `ibmcloud is load-balancer-listener-policy-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --name my-policy --priority 5`
- `ibmcloud is load-balancer-listener-policy-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --action forward --target-id 70294e14-4e61-11e8-bcf4-0242ac110004`
When the action is _forward_, the pool identity is required to specify which pool the load balancer forwards the traffic to.
- `ibmcloud is load-balancer-listener-policy-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target-http-status-code 301 --target-url "https://www.redirect.com"`
When the action is _redirect_, the "url" and "http_status_code" are required. Possible values for _http_status_code_ are "301", "302", "303", "307", or "308". The "url" is the redirect target URL.
- `ibmcloud is load-balancer-listener-policy-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --name my-policy --output JSON`

#### Command options
{: #command-options-load-balancer-listener-policy-update}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY_ID**: ID of the policy.
- **--name**: The user-defined name for this policy. Policy names must be unique within the load balancer listener.
- **--priority**: Priority of the policy. Lower value indicates higher priority, for example: **5**, range: [**1-10**].
- **--target-id**: The unique identifier for this load balancer pool that is specified with **forward** action.
- **--target-http-status-code**: The HTTP status code in the redirect response, one of [**301**, **302**, **303**, **307**, **308**], specified with **redirect** action.
- **--target-url**: The redirect target URL, specified with **redirect** action.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-update
{: #load-balancer-listener-update}

Update a load balancer listener.

```
ibmcloud is load-balancer-listener-update LOAD_BALANCER_ID LISTENER_ID [--protocol http | https | tcp] [--port PORT] [--default-pool DEFAULT_POOL_ID] [--connection-limit LIMIT] [--certificate-instance-crn CERTIFICATE_INSTANCE_CRN] [--accept-proxy-protocol false | true] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-listener-update}

- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --certificate-instance-crn crn:v1:bluemix:public:cloudcerts:us-south:a/123456:b8866ea4-b8df-467e-801a-da1db7e020bf:certificate:78ff9c4c97d013fb2a95b21dddde7758`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --connection-limit 2000`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --default-pool 70294e14-4e61-11e8-bcf4-0242ac110004`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --protocol https`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --port 222`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --output JSON`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --accept-proxy-protocol true`

#### Command options
{: #command-options-load-balancer-listener-update}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--protocol**: The listener protocol. Load balancers in the application family support tcp, http, and https. Load balancers in the network family support tcp.
- **--port**: The listener port number. Range 1-65535.
- **--default-pool**: ID of the default pool.
- **--connection-limit**: The maximum number of connections of the listener. This option is not applicable for the load balancers in the network family.
- **--certificate-instance-crn**: CRN of the certificate instance. Required when protocol is **https**. This option is not applicable for the load balancers in the network family.
- **--accept-proxy-protocol**: If set to true, proxy protocol is enabled for this listener. Only supported for application load balancers. One of: **false**, **true**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listeners
{: #load-balancer-listeners}

List all load balancer listeners.

```
ibmcloud is load-balancer-listeners LOAD_BALANCER_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-listeners}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool
{: #load-balancer-pool}

View details of a load balancer pool.

```
ibmcloud is load-balancer-pool LOAD_BALANCER_ID POOL_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-pool}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-create
{: #load-balancer-pool-create}

Create a load balancer pool.

```
ibmcloud is load-balancer-pool-create POOL_NAME LOAD_BALANCER_ID ALGORITHM PROTOCOL HEALTH_DELAY HEALTH_RETRIES HEALTH_TIMEOUT HEALTH_TYPE (--members MEMBERS_JSON | @MEMBERS_JSON_FILE) [--health-monitor-url URL] [--health-monitor-port PORT] [--session-persistence-type source_ip | http_cookie | app_cookie [--session-persistence-cookie-name SESSION_PERSISTENCE_COOKIE_NAME]] [--proxy-protocol disabled | v1 | v2] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-pool-create}

- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http`
- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --health-monitor-url / --health-monitor-port 4001`
- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --session-persistence-type source_ip --output JSON`
- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --members '[{"port": 80, "target": { "address": "10.10.1.4"}, "weight": 20 }, {"port": 80, "target": { "address": "10.240.0.6"}, "weight": 30 }]'`
Create application load balancer pool with members
- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --members '[{"port": 80, "target": { "id": "0736_63b9233c-812e-4d65-9ee3-fa61172afa37"}, "weight": 20 }, {"port": 80, "target": { "id": "0716_4b30a833-6f10-46a9-a4b8-13871f3559b8"}, "weight": 30 }]'`
Create network load balancer pool with members
- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --proxy-protocol v1`
- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --session-persistence-type app_cookie --session-persistence-cookie-name my-cookie-name`

#### Command options
{: #command-options-load-balancer-pool-create}

- **POOL_NAME**: Name of the pool.
- **LOAD_BALANCER_ID**: ID of the load balancer.
- **ALGORITHM**: The load balancing algorithm. One of: **round_robin**, **weighted_round_robin**, **least_connections**.
- **PROTOCOL**: The pool protocol. Load balancers in the application family support **tcp**, **http**, **https**. Load balancers in the network family support **tcp**.
- **HEALTH_DELAY**: The health check interval in seconds. The interval must be greater than the timeout value. Minimum: **2**, maximum: **60**.
- **HEALTH_RETRIES**: The health check maximum retries. Minimum: **1**, maximum: **10**.
- **HEALTH_TIMEOUT**: The health check timeout in seconds. Minimum: **1**, maximum: **59**.
- **HEALTH_TYPE**: The health check protocol. Load balancers in the application family support tcp, http, https. Load balancers in the network family support tcp, http.
- **--health-monitor-url**: The health check URL. This option is applicable only to HTTP type of **HEALTH_TYPE**.
- **--health-monitor-port**: The health check port number. If specified, the specified ports in the server member resources are overridden.
- **--session-persistence-type**: The session persistence type. One of: **source_ip**, **http_cookie**, **app_cookie**.
- **--session-persistence-cookie-name**: Session persistence cookie name. This option is applicable only to **app_cookie** type.
- **--proxy-protocol**: The proxy protocol setting for this pool. Only supported for application load balancers. One of: **disabled**, **v1**, **v2**.
- **--members**: MEMBERS_JSON|@MEMBERS_JSON_FILE, members in JSON or JSON file.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-delete
{: #load-balancer-pool-delete}

Delete pools from a load balancer.

```
ibmcloud is load-balancer-pool-delete LOAD_BALANCER_ID (POOL_ID1 POOL_ID2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-pool-delete}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID1**: ID of the pool.
- **POOL_ID2**: ID of the pool.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-member
{: #load-balancer-pool-member}

View details of load balancer pool member.

```
ibmcloud is load-balancer-pool-member LOAD_BALANCER_ID POOL_ID MEMBER_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-pool-member}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **MEMBER_ID**: ID of the member.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-member-create
{: #load-balancer-pool-member-create}

Create a load balancer pool member.

```
ibmcloud is load-balancer-pool-member-create LOAD_BALANCER_ID POOL_ID PORT TARGET [--weight WEIGHT] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-pool-member-create}

- `ibmcloud is load-balancer-pool-member-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 3000 192.168.100.5`
- `ibmcloud is load-balancer-pool-member-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 3000 9e692608-3b3a-4cfb-9f46-efb6b711876d`
- `ibmcloud is load-balancer-pool-member-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 3000 192.168.100.5 --weight 100 --output JSON`

#### Command options
{: #command-options-load-balancer-pool-member-create}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **PORT**: The port number of the running application in the server member.
- **TARGET**: The IP address of the pool member for load balancers in the application family, or the instance ID of the pool member for load balancers in the network family.
- **--weight**: Weight of the server member. This option is applicable only when the load balancer algorithm of its pool is **weighted_round_robin**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-member-update
{: #load-balancer-pool-member-update}

Update a member of a load balancer pool.

```
ibmcloud is load-balancer-pool-member-update LOAD_BALANCER_ID POOL_ID MEMBER_ID [--target-address TARGET_ADDRESS | --target TARGET] [--port PORT] [--weight WEIGHT] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-pool-member-update}

- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target 192.168.100.5 --port 3001`
- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target 9e692608-3b3a-4cfb-9f46-efb6b711876d --port 3001`
- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target-address 192.168.100.5 --port 3001`
- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target-address 192.168.100.5 --port 3001 --weight 100 --output JSON`

#### Command options
{: #command-options-load-balancer-pool-member-update}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **MEMBER_ID**: ID of the member.
- **--target-address**: The IP address of the pool member.
- **--target**: The IP address of the pool member for load balancers in the application family, or the instance ID of the pool member for load balancers in the network family.
- **--port**: The port number of the application that is running in the server member.
- **--weight**: Weight of the server member. This option is applicable only when the load balancer algorithm of its pool is **weighted_round_robin**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-member-delete
{: #load-balancer-pool-member-delete}

Delete members from a load balancer pool.

```
ibmcloud is load-balancer-pool-member-delete LOAD_BALANCER_ID POOL_ID (MEMBER_ID1 MEMBER_ID2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-pool-member-delete}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **MEMBER_ID1**: ID of the member.
- **MEMBER_ID2**: ID of the member.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-members
{: #load-balancer-pool-members}

List all the members of a load balancer pool.

```
ibmcloud is load-balancer-pool-members LOAD_BALANCER_ID POOL_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-pool-members}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-update
{: #load-balancer-pool-update}

Update a pool of a load balancer.

```
ibmcloud is load-balancer-pool-update LOAD_BALANCER_ID POOL_ID [--algorithm round_robin | weighted_round_robin | least_connections] [--health-delay DELAY --health-max-retries RETRIES --health-timeout TIMEOUT --health-type https | http | tcp] [--health-monitor-url URL] [--health-monitor-port PORT] [--protocol https | http | tcp] [[--session-persistence-type source_ip | http_cookie | app_cookie | none] | [--session-persistence-cookie-name SESSION_PERSISTENCE_COOKIE_NAME]] [--proxy-protocol disabled | v1 | v2] [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-pool-update}

- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --algorithm round_robin`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --health-delay 20 --health-max-retries 2 --health-timeout 5 --health-type http`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --health-monitor-url / --health-monitor-port 4001`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --session-persistence-type source_ip`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --protocol http`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name lb-rule-name --output JSON`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --proxy-protocol v2`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --session-persistence-type app_cookie --session-persistence-cookie-name my-cookie-name`

#### Command options
{: #command-options-load-balancer-pool-update}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **--algorithm**: The load balancing algorithm. One of: **round_robin**, **weighted_round_robin**, **least_connections**.
- **--health-delay**: The health check interval in seconds. The interval must be greater than the timeout value. Minimum: **2**, maximum: **60**.
- **--health-max-retries**: The health check maximum retries. Minimum: **1**, maximum: **10**.
- **--health-timeout**: The health check timeout in seconds. Minimum: **1**, maximum: **59**.
- **--health-type**: The health check protocol. Load balancers in the application family support tcp, http, https. Load balancers in the network family support tcp, http.
- **--health-monitor-url**: The health check URL. This option is applicable only to HTTP type of **--health-type**.
- **--health-monitor-port**: The health check port number. If specified, the specified ports in the server member resources are overridden.
- **--protocol**: The pool protocol. Load balancers in the application family support **tcp**, **http**, **https**. Load balancers in the network family support **tcp**.
- **--session-persistence-type**: The session persistence type. One of: **source_ip**, **http_cookie**, **app_cookie**, **none**.
- **--session-persistence-cookie-name**: Session persistence cookie name. This option is applicable only to **app_cookie** type.
- **--proxy-protocol**: The proxy protocol setting for this pool. Only supported for application load balancers. One of: **disabled**, **v1**, **v2**.
- **--name**: The new name of the pool.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pools
{: #load-balancer-pools}

List all pools of a load balancer.

```
ibmcloud is load-balancer-pools LOAD_BALANCER_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-pools}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-statistics
{: #load-balancer-statistics}

List all statistics of a load balancer.

```
ibmcloud is load-balancer-statistics LOAD_BALANCER_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-load-balancer-statistics}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-update
{: #load-balancer-update}

Update a load balancer.

```
ibmcloud is load-balancer-update LOAD_BALANCER_ID [--name NEW_NAME] [--logging-datapath-active false | true] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-load-balancer-update}

- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-loadBalancer`
- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-loadBalancer --output JSON`
- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --logging-datapath-active false`

#### Command options
{: #command-options-load-balancer-update}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--name**: New name of the Load balancer.
- **--logging-datapath-active**: Enable or disable datapath logging for this load balancer. This is applicable only for application load balancer. One of: **false**, **true**.
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

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Network load balancers
{: #nlb-anchor}

The following section provides information about CLI commands for working with network load balancers, listeners, and pools.

### ibmcloud is load-balancers
{: #network-load-balancers}

List all load balancers.

```
ibmcloud is load-balancers [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-load-balancers}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer
{: #network-load-balancer}

View details of a load balancer.

```
ibmcloud is load-balancer LOAD_BALANCER_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-load-balancer}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-create
{: #network-load-balancer-create}

Create a load balancer.

```
ibmcloud is load-balancer-create LOAD_BALANCER_NAME LOAD_BALANCER_TYPE (--subnet SUBNET_ID1 --subnet SUBNET_ID2 ...) [--family application | network] [--security-group SECURITY_GROUP1 --security-group SECURITY_GROUP2 ...] [--logging-datapath-active false | true] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-network-load-balancer-create}

- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --family network`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --resource-group-id fee82deba12e4c0fb69c3b09d1f12345`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --resource-group-name Default`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --output JSON`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --security-group 3428abaa-788b-439b-9404-ca386f2f3f79 --security-group f0e26f91-851a-4fc9-b32b-da24ad218b4e`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --logging-datapath-active true`

#### Command options
{: #command-options-network-load-balancer-create}

- **LOAD_BALANCER_NAME**: Name of the load balancer.
- **LOAD_BALANCER_TYPE**: Type of the load balancer, **public** or **private**.
- **--subnet**: ID of the subnets to provision this load balancer. This option can be specified multiple times to provision load balancer in multiple subnets. Only one subnet can be specified for network load balancer.
- **--family**: The load balancer family type. One of: **application**, **network**.
- **--security-group**: ID of the security group.
- **--logging-datapath-active**: Enable or disable datapath logging for this load balancer. If unspecified, datapath logging is disabled. This is applicable only for application load balancer. One of: **false**, **true**.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-delete
{: #network-load-balancer-delete}

Delete load balancers.

```
ibmcloud is load-balancer-delete (LOAD_BALANCER_ID1 LOAD_BALANCER_ID2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-network-load-balancer-delete}

- **LOAD_BALANCER_ID1**: ID of the load balancer.
- **LOAD_BALANCER_ID2**: ID of the load balancer.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-update
{: #network-load-balancer-update}

Update a load balancer.

```
ibmcloud is load-balancer-update LOAD_BALANCER_ID [--name NEW_NAME] [--logging-datapath-active false | true] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-network-load-balancer-update}

- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-loadBalancer`
- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-loadBalancer --output JSON`
- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --logging-datapath-active false`

#### Command options
{: #command-options-network-load-balancer-update}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--name**: New name of the Load balancer.
- **--logging-datapath-active**: Enable or disable datapath logging for this load balancer. This is applicable only for application load balancer. One of: **false**, **true**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listeners
{: #network-load-balancer-listeners}

List all load balancer listeners.

```
ibmcloud is load-balancer-listeners LOAD_BALANCER_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-load-balancer-listeners}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener
{: #network-load-balancer-listener}

View details of a load balancer listener.

```
ibmcloud is load-balancer-listener LOAD_BALANCER_ID LISTENER_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-load-balancer-listener}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-create
{: #network-load-balancer-listener-create}

Create a load balancer listener.

```
ibmcloud is load-balancer-listener-create LOAD_BALANCER_ID PORT PROTOCOL [--default-pool DEFAULT_POOL_ID] [--connection-limit LIMIT] [--certificate-instance-crn CERTIFICATE_INSTANCE_CRN] [--policies LISTENER_POLICIES_JSON | @LISTENER_POLICIES_JSON_FILE] [--accept-proxy-protocol false | true] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-network-load-balancer-listener-create}

- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 https --certificate-instance-crn crn:v1:bluemix:public:cloudcerts:us-south:a/123456:b8866ea4-b8df-467e-801a-da1db7e020bf:certificate:78ff9c4c97d013fb2a95b21dddde7758`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --connection-limit 2000`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --default-pool 70294e14-4e61-11e8-bcf4-0242ac110004`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --policies '[{"name": "my-policy", "priority": 5, "action": "reject" }]'`
The priority of the policy can have a range of 1 to 10, where a lower value indicates a higher priority. The possible values for _action_ are "forward", "redirect", or "reject".
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --policies '[{"priority": 5, "action": "forward", "target": { "id": 70294e14-4e61-11e8-bcf4-0242ac110004 }}]'`
When the action is _forward_, the pool identity is required to specify which pool the load balancer forwards the traffic to.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --policies '[{"priority": 5, "action": "redirect", "target": { "http_status_code": 301, "url": "https://www.redirect.com"}}]'`
When the action is _redirect_, the "url" and "http_status_code" are required. Possible values for _http_status_code_ are "301", "302", "303", "307", or "308". The "url" is the redirect target URL.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --policies '[{"priority": 5, "action": "reject", "rules": { "condition": "equals", "type": "header", "field": "My-app-header", "value": "value"}}]'`
Possible values for _condition_ are "contains", "equals", or "matches_regex". Possible values for _type_ are "header", "hostname", or "path". _field_ is an HTTP header field that is applicable only to the "header" rule type. The _value_ parameter is the value to match the rule condition.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --output JSON`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --accept-proxy-protocol true`

#### Command options
{: #command-options-network-load-balancer-listener-create}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **PORT**: The listener port number. Range 1-65535.
- **PROTOCOL**: The listener protocol. Load balancers in the application family support tcp, http, and https. Load balancers in the network family support tcp.
- **--default-pool**: ID of the default pool.
- **--connection-limit**: The maximum number of connections of the listener. This option is not applicable for the load balancers in the network family.
- **--certificate-instance-crn**: CRN of the certificate instance. Required when protocol is **https**. This option is not applicable for the load balancers in the network family.
- **--policies**: **LISTENER_POLICIES_JSON** | **@LISTENER_POLICIES_JSON_FILE**, listener policies in JSON or JSON file. This option is not applicable for the load balancers in the network family.
- **--accept-proxy-protocol**: If set to true, proxy protocol is enabled for this listener. Only supported for application load balancers. One of: **false**, **true**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-delete
{: #network-load-balancer-listener-delete}

Delete load balancer listeners.

```
ibmcloud is load-balancer-listener-delete LOAD_BALANCER_ID (LISTENER_ID1 LISTENER_ID2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-network-load-balancer-listener-delete}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID1**: ID of the listener.
- **LISTENER_ID2**: ID of the listener.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-listener-update
{: #network-load-balancer-listener-update}

Update a load balancer listener.

```
ibmcloud is load-balancer-listener-update LOAD_BALANCER_ID LISTENER_ID [--protocol http | https | tcp] [--port PORT] [--default-pool DEFAULT_POOL_ID] [--connection-limit LIMIT] [--certificate-instance-crn CERTIFICATE_INSTANCE_CRN] [--accept-proxy-protocol false | true] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-network-load-balancer-listener-update}

- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --certificate-instance-crn crn:v1:bluemix:public:cloudcerts:us-south:a/123456:b8866ea4-b8df-467e-801a-da1db7e020bf:certificate:78ff9c4c97d013fb2a95b21dddde7758`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --connection-limit 2000`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --default-pool 70294e14-4e61-11e8-bcf4-0242ac110004`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --protocol https`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --port 222`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --output JSON`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --accept-proxy-protocol true`

#### Command options
{: #command-options-network-load-balancer-listener-update}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--protocol**: The listener protocol. Load balancers in the application family support tcp, http, and https. Load balancers in the network family support tcp.
- **--port**: The listener port number. Range 1-65535.
- **--default-pool**: ID of the default pool.
- **--connection-limit**: The maximum number of connections of the listener. This option is not applicable for the load balancers in the network family.
- **--certificate-instance-crn**: CRN of the certificate instance. Required when protocol is **https**. This option is not applicable for the load balancers in the network family.
- **--accept-proxy-protocol**: If set to true, proxy protocol is enabled for this listener. Only supported for application load balancers. One of: **false**, **true**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pools
{: #network-load-balancer-pools}

List all pools of a load balancer.

```
ibmcloud is load-balancer-pools LOAD_BALANCER_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-load-balancer-pools}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool
{: #network-load-balancer-pool}

View details of a load balancer pool.

```
ibmcloud is load-balancer-pool LOAD_BALANCER_ID POOL_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-load-balancer-pool}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-create
{: #network-load-balancer-pool-create}

Create a load balancer pool.

```
ibmcloud is load-balancer-pool-create POOL_NAME LOAD_BALANCER_ID ALGORITHM PROTOCOL HEALTH_DELAY HEALTH_RETRIES HEALTH_TIMEOUT HEALTH_TYPE (--members MEMBERS_JSON | @MEMBERS_JSON_FILE) [--health-monitor-url URL] [--health-monitor-port PORT] [--session-persistence-type source_ip | http_cookie | app_cookie [--session-persistence-cookie-name SESSION_PERSISTENCE_COOKIE_NAME]] [--proxy-protocol disabled | v1 | v2] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-network-load-balancer-pool-create}

- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http`
- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --health-monitor-url / --health-monitor-port 4001`
- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --session-persistence-type source_ip --output JSON`
- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --members '[{"port": 80, "target": { "address": "10.10.1.4"}, "weight": 20 }, {"port": 80, "target": { "address": "10.240.0.6"}, "weight": 30 }]'`
Create application load balancer pool with members
- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --members '[{"port": 80, "target": { "id": "0736_63b9233c-812e-4d65-9ee3-fa61172afa37"}, "weight": 20 }, {"port": 80, "target": { "id": "0716_4b30a833-6f10-46a9-a4b8-13871f3559b8"}, "weight": 30 }]'`
Create network load balancer pool with members
- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --proxy-protocol v1`
- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --session-persistence-type app_cookie --session-persistence-cookie-name my-cookie-name`

#### Command options
{: #command-options-network-load-balancer-pool-create}

- **POOL_NAME**: Name of the pool.
- **LOAD_BALANCER_ID**: ID of the load balancer.
- **ALGORITHM**: The load balancing algorithm. One of: **round_robin**, **weighted_round_robin**, **least_connections**.
- **PROTOCOL**: The pool protocol. Load balancers in the application family support **tcp**, **http**, **https**. Load balancers in the network family support **tcp**.
- **HEALTH_DELAY**: The health check interval in seconds. The interval must be greater than the timeout value. Minimum: **2**, maximum: **60**.
- **HEALTH_RETRIES**: The health check maximum retries. Minimum: **1**, maximum: **10**.
- **HEALTH_TIMEOUT**: The health check timeout in seconds. Minimum: **1**, maximum: **59**.
- **HEALTH_TYPE**: The health check protocol. Load balancers in the application family support tcp, http, https. Load balancers in the network family support tcp, http.
- **--health-monitor-url**: The health check URL. This option is applicable only to HTTP type of **HEALTH_TYPE**.
- **--health-monitor-port**: The health check port number. If specified, the specified ports in the server member resources are overridden.
- **--session-persistence-type**: The session persistence type. One of: **source_ip**, **http_cookie**, **app_cookie**.
- **--session-persistence-cookie-name**: Session persistence cookie name. This option is applicable only to **app_cookie** type.
- **--proxy-protocol**: The proxy protocol setting for this pool. Only supported for application load balancers. One of: **disabled**, **v1**, **v2**.
- **--members**: MEMBERS_JSON|@MEMBERS_JSON_FILE, members in JSON or JSON file.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-delete
{: #network-load-balancer-pool-delete}

Delete pools from a load balancer.

```
ibmcloud is load-balancer-pool-delete LOAD_BALANCER_ID (POOL_ID1 POOL_ID2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-network-load-balancer-pool-delete}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID1**: ID of the pool.
- **POOL_ID2**: ID of the pool.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-update
{: #network-load-balancer-pool-update}

Update a pool of a load balancer.

```
ibmcloud is load-balancer-pool-update LOAD_BALANCER_ID POOL_ID [--algorithm round_robin | weighted_round_robin | least_connections] [--health-delay DELAY --health-max-retries RETRIES --health-timeout TIMEOUT --health-type https | http | tcp] [--health-monitor-url URL] [--health-monitor-port PORT] [--protocol https | http | tcp] [[--session-persistence-type source_ip | http_cookie | app_cookie | none] | [--session-persistence-cookie-name SESSION_PERSISTENCE_COOKIE_NAME]] [--proxy-protocol disabled | v1 | v2] [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-network-load-balancer-pool-update}

- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --algorithm round_robin`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --health-delay 20 --health-max-retries 2 --health-timeout 5 --health-type http`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --health-monitor-url / --health-monitor-port 4001`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --session-persistence-type source_ip`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --protocol http`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name lb-rule-name --output JSON`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --proxy-protocol v2`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --session-persistence-type app_cookie --session-persistence-cookie-name my-cookie-name`

#### Command options
{: #command-options-network-load-balancer-pool-update}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **--algorithm**: The load balancing algorithm. One of: **round_robin**, **weighted_round_robin**, **least_connections**.
- **--health-delay**: The health check interval in seconds. The interval must be greater than the timeout value. Minimum: **2**, maximum: **60**.
- **--health-max-retries**: The health check maximum retries. Minimum: **1**, maximum: **10**.
- **--health-timeout**: The health check timeout in seconds. Minimum: **1**, maximum: **59**.
- **--health-type**: The health check protocol. Load balancers in the application family support tcp, http, https. Load balancers in the network family support tcp, http.
- **--health-monitor-url**: The health check URL. This option is applicable only to HTTP type of **--health-type**.
- **--health-monitor-port**: The health check port number. If specified, the specified ports in the server member resources are overridden.
- **--protocol**: The pool protocol. Load balancers in the application family support **tcp**, **http**, **https**. Load balancers in the network family support **tcp**.
- **--session-persistence-type**: The session persistence type. One of: **source_ip**, **http_cookie**, **app_cookie**, **none**.
- **--session-persistence-cookie-name**: Session persistence cookie name. This option is applicable only to **app_cookie** type.
- **--proxy-protocol**: The proxy protocol setting for this pool. Only supported for application load balancers. One of: **disabled**, **v1**, **v2**.
- **--name**: The new name of the pool.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-members
{: #network-load-balancer-pool-members}

List all the members of a load balancer pool.

```
ibmcloud is load-balancer-pool-members LOAD_BALANCER_ID POOL_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-load-balancer-pool-members}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-member
{: #network-load-balancer-pool-member}

View details of load balancer pool member.

```
ibmcloud is load-balancer-pool-member LOAD_BALANCER_ID POOL_ID MEMBER_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-load-balancer-pool-member}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **MEMBER_ID**: ID of the member.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-member-create
{: #network-load-balancer-pool-member-create}

Create a load balancer pool member.

```
ibmcloud is load-balancer-pool-member-create LOAD_BALANCER_ID POOL_ID PORT TARGET [--weight WEIGHT] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-network-load-balancer-pool-member-create}

- `ibmcloud is load-balancer-pool-member-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 3000 192.168.100.5`
- `ibmcloud is load-balancer-pool-member-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 3000 9e692608-3b3a-4cfb-9f46-efb6b711876d`
- `ibmcloud is load-balancer-pool-member-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 3000 192.168.100.5 --weight 100 --output JSON`

#### Command options
{: #command-options-network-load-balancer-pool-member-create}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **PORT**: The port number of the running application in the server member.
- **TARGET**: The IP address of the pool member for load balancers in the application family, or the instance ID of the pool member for load balancers in the network family.
- **--weight**: Weight of the server member. This option is applicable only when the load balancer algorithm of its pool is **weighted_round_robin**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-member-update
{: #network-load-balancer-pool-member-update}

Update a member of a load balancer pool.

```
ibmcloud is load-balancer-pool-member-update LOAD_BALANCER_ID POOL_ID MEMBER_ID [--target-address TARGET_ADDRESS | --target TARGET] [--port PORT] [--weight WEIGHT] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-network-load-balancer-pool-member-update}

- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target 192.168.100.5 --port 3001`
- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target 9e692608-3b3a-4cfb-9f46-efb6b711876d --port 3001`
- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target-address 192.168.100.5 --port 3001`
- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target-address 192.168.100.5 --port 3001 --weight 100 --output JSON`

#### Command options
{: #command-options-network-load-balancer-pool-member-update}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **MEMBER_ID**: ID of the member.
- **--target-address**: The IP address of the pool member.
- **--target**: The IP address of the pool member for load balancers in the application family, or the instance ID of the pool member for load balancers in the network family.
- **--port**: The port number of the application that is running in the server member.
- **--weight**: Weight of the server member. This option is applicable only when the load balancer algorithm of its pool is **weighted_round_robin**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-pool-member-delete
{: #network-load-balancer-pool-member-delete}

Delete members from a load balancer pool.

```
ibmcloud is load-balancer-pool-member-delete LOAD_BALANCER_ID POOL_ID (MEMBER_ID1 MEMBER_ID2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-network-load-balancer-pool-member-delete}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **MEMBER_ID1**: ID of the member.
- **MEMBER_ID2**: ID of the member.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is load-balancer-statistics
{: #network-load-balancer-statistics}

List all statistics of a load balancer.

```
ibmcloud is load-balancer-statistics LOAD_BALANCER_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-load-balancer-statistics}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Network ACLs
{: #network-acls}

### ibmcloud is network-acls
{: #network-acls}

List all network ACLs.

```
ibmcloud is network-acls [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-acls}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl
{: #network-acl}

View details of a network ACL.

```
ibmcloud is network-acl ACL [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-acl}

- **ACL**: ID of the network ACL.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl-create
{: #network-acl-create}

Create a network ACL.

```
ibmcloud is network-acl-create ACL_NAME VPC [--rules (RULES_JSON|@RULES_JSON_FILE) | --source-acl-id SOURCE_ACL_ID] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-network-acl-create}

- `ibmcloud is network-acl-create my-acl 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is network-acl-create my-acl 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --source-acl-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is network-acl-create my-acl 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --rules '[{ "action": "allow", "destination": "192.168.0.0/24", "direction": "inbound", "source": "10.0.0.0/24",  "protocol": "tcp" }]'`
- `ibmcloud is network-acl-create my-acl 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --output JSON`

#### Command options
{: #command-options-network-acl-create}

- **ACL_NAME**: Name of the network ACL.
- **VPC**: ID of the VPC.
- **--rules**: RULES_JSON|@RULES_JSON_FILE, rules for the ACL in JSON or JSON file.
- **--source-acl-id**: ID of the network ACL to copy rules from.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl-update
{: #network-acl-update}

Update a network ACL.

```
ibmcloud is network-acl-update ACL --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-network-acl-update}

- `ibmcloud is network-acl-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-acl`
- `ibmcloud is network-acl-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-acl --output JSON`

#### Command options
{: #command-options-network-acl-update}

- **ACL**: ID of the network ACL.
- **--name**: New name of the network ACL.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl-delete
{: #network-acl-delete}

Delete network ACLs.

```
ibmcloud is network-acl-delete (ACL1 ACL2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-network-acl-delete}

- **ACL1**: ID of the network ACL.
- **ACL2**: ID of the network ACL.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl-rules
{: #network-acl-rules}

List all rules of a network ACL.

```
ibmcloud is network-acl-rules ACL [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-acl-rules}

- **ACL**: ID of the network ACL.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl-rule
{: #network-acl-rule}

View details of a network ACL rule.

```
ibmcloud is network-acl-rule ACL RULE [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-network-acl-rule}

- **ACL**: ID of the network ACL.
- **RULE**: ID of the rule.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl-rule-add
{: #network-acl-rule-add}

Add a rule to a network ACL.

```
ibmcloud is network-acl-rule-add ACL ACTION DIRECTION PROTOCOL SOURCE DESTINATION [--name NAME] [--icmp-type ICMP_TYPE] [--icmp-code ICMP_CODE] [--source-port-min PORT_MIN] [--source-port-max PORT_MAX] [--destination-port-min PORT_MIN] [--destination-port-max PORT_MAX] [--before-rule-id RULE_ID] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-network-acl-rule-add}

- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound all 10.2.2.2 10.2.2.3`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound all 10.2.2.2 10.2.2.3 --name my-acl`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound icmp 10.2.2.2 10.2.2.3 --icmp-type 8 --icmp-code 0`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound tcp 10.2.2.2 10.2.2.3 --source-port-min 555  --source-port-max 666 --destination-port-min 11 --destination-port-max 55`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound all 10.2.2.2 10.2.2.3 --before-rule-id 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound all 10.2.2.2 10.2.2.3 --output JSON`

#### Command options
{: #command-options-network-acl-rule-add}

- **ACL**: ID of the network ACL.
- **ACTION**: One of: **allow**, **deny**.
- **DIRECTION**: Direction of traffic to enforce. One of: **inbound**, **outbound**.
- **PROTOCOL**: Protocol to enforce. One of: **all**, **icmp**, **tcp**, **udp**.
- **SOURCE**: Source IP address or CIDR block.
- **DESTINATION**: Destination IP address or CIDR block.
- **--name**: The name of the ACL rule.
- **--icmp-type**: ICMP traffic type to allow. Valid values from **0** to **254**. This option is specified only when protocol is set to **icmp**. If unspecified, all types are allowed.
- **--icmp-code**: ICMP traffic code to allow. Valid values from **0** to **255**. This option is specified only when protocol is set to **icmp**. If unspecified, all codes are allowed.
- **--source-port-min**: Minimum source port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **1**).
- **--source-port-max**: Maximum source port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **65535**).
- **--destination-port-min**: Minimum destination port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **1**).
- **--destination-port-max**: Maximum destination port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **65535**).
- **--before-rule-id**: ID of the rule that this rule is inserted before.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is network-acl-rule-update
{: #network-acl-rule-update}

Update a rule of a network ACL.

```
ibmcloud is network-acl-rule-update ACL RULE [--name NEW_NAME] [--direction inbound | outbound] [--action allow | deny] [--before-rule-id RULE_ID] [--source SOURCE] [--dest DEST] [--icmp-type ICMP_TYPE] [--icmp-code ICMP_CODE] [--source-port-min PORT_MIN] [--source-port-max PORT_MAX] [--destination-port-min PORT_MIN] [--destination-port-max PORT_MAX] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-network-acl-rule-update}

- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol all --source 10.2.2.2 --dest 10.2.2.3`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol all --source 10.2.2.2 --dest 10.2.2.3 --name my-acl`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol icmp --source 10.2.2.2 --dest 10.2.2.3 --icmp-type 8 --icmp-code 0`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol tcp --source 10.2.2.2 --dest 10.2.2.3 --source-port-min 555 --source-port-max 666 --destination-port-min 11 --destination-port-max 55`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol all --source 10.2.2.2 --dest 10.2.2.3 --before-rule-id 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol all --source 10.2.2.2 --dest 10.2.2.3 --output JSON`

#### Command options
{: #command-options-network-acl-rule-update}

- **ACL**: ID of the network ACL.
- **RULE**: ID of the rule.
- **--name**: New name of the rule.
- **--direction**: Direction of traffic to enforce. One of: **inbound**, **outbound**.
- **--action**: One of: **allow**, **deny**.
- **--before-rule-id**: ID of the rule that this rule is inserted before.
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

Delete rules from a network ACL.

```
ibmcloud is network-acl-rule-delete ACL (RULE1 RULE2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-network-acl-rule-delete}

- **ACL**: ID of the network ACL.
- **RULE1**: ID of the rule.
- **RULE2**: ID of the rule.
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
ibmcloud is public-gateway GATEWAY [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-public-gateway}

- **GATEWAY**: ID of the public gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is public-gateway-create
{: #public-gateway-create}

Create a public gateway.

```
ibmcloud is public-gateway-create GATEWAY_NAME VPC ZONE_NAME [--floating-ip-id IP_ID | --floating-ip-address IP_ADDRESS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-public-gateway-create}

- `ibmcloud is public-gateway-create my-public-gateway 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1`
- `ibmcloud is public-gateway-create my-public-gateway 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 --floating-ip-id 39300233-9995-4806-89a5-3c1b6eb88689`
- `ibmcloud is public-gateway-create my-public-gateway 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 --floating-ip-address 203.0.113.1`
- `ibmcloud is public-gateway-create my-public-gateway 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 --output JSON`

#### Command options
{: #command-options-public-gateway-create}

- **GATEWAY_NAME**: Name of the public gateway.
- **VPC**: ID of the VPC.
- **ZONE_NAME**: Name of the zone.
- **--floating-ip-id**: ID of the floating IP bound to the public gateway.
- **--floating-ip-address**: IP address of the floating IP bound to the public gateway.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is public-gateway-delete
{: #public-gateway-delete}

Delete public gateways.

```
ibmcloud is public-gateway-delete (GATEWAY1 GATEWAY2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-public-gateway-delete}

- **GATEWAY1**: ID of the public gateway.
- **GATEWAY2**: ID of the public gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is public-gateway-update
{: #public-gateway-update}

Update a public gateway.

```
ibmcloud is public-gateway-update GATEWAY --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-public-gateway-update}

- `ibmcloud is public-gateway-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --name my-gateway --output JSON`

#### Command options
{: #command-options-public-gateway-update}

- **GATEWAY**: ID of the public gateway.
- **--name**: New name of the public gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is public-gateways
{: #public-gateways}

List all public gateways.

```
ibmcloud is public-gateways [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-public-gateways}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
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

- **VPC**: ID of the VPC.
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

- **VPC**: ID of the VPC.
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

- **VPC**: ID of the VPC.
- **ROUTING_TABLE**: ID of the VPC routing table.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-table-create
{: #vpc-routing-table-create}

Create a VPC routing table.

```
ibmcloud is vpc-routing-table-create VPC [--name NAME] [--direct-link-ingress false | true] [--transit-gateway-ingress false | true] [--vpc-zone-ingress false | true] [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-vpc-routing-table-create}

- `ibmcloud is vpc-routing-table-create 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-vpc-routing-table --output JSON`

#### Command options
{: #command-options-vpc-routing-table-create}

- **VPC**: ID of the VPC.
- **--name**: Name of the VPC routing table.
- **--direct-link-ingress, --direct-link**: If set to "true", this routing table is used to route traffic that originates from Direct Link to this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--transit-gateway-ingress, --transit-gateway**: If set to "true", this routing table is used to route traffic that originates from Transit Gateway to this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--vpc-zone-ingress, --vpc-zone**: If set to "true", this routing table is used to route traffic that originates from subnets in other zones in this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-table-update
{: #vpc-routing-table-update}

Update a VPC routing table.

```
ibmcloud is vpc-routing-table-update VPC ROUTING_TABLE [--name NEW_NAME] [--direct-link-ingress false | true] [--transit-gateway-ingress false | true] [--vpc-zone-ingress false | true] [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-vpc-routing-table-update}

- `ibmcloud is vpc-routing-table-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1d456 --name my-vpc-routing-table --output JSON`

#### Command options
{: #command-options-vpc-routing-table-update}

- **VPC**: ID of the VPC.
- **ROUTING_TABLE**: ID of the VPC routing table.
- **--name**: New name of the routing table.
- **--direct-link-ingress, --direct-link**: If set to "true", this routing table is used to route traffic that originates from Direct Link to this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--transit-gateway-ingress, --transit-gateway**: If set to "true", this routing table is used to route traffic that originates from Transit Gateway to this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--vpc-zone-ingress, --vpc-zone**: If set to "true", this routing table is used to route traffic that originates from subnets in other zones in this VPC. For the routing to succeed, the VPC must not already have a routing table with this property set to "true". One of: **false**, **true**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-table-delete
{: #vpc-routing-table-delete}

Delete VPC routing tables.

```
ibmcloud is vpc-routing-table-delete VPC (ROUTING_TABLE1 ROUTING_TABLE2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-routing-table-delete}

- **VPC**: ID of the VPC.
- **ROUTING_TABLE1**: ID of the VPC routing table.
- **ROUTING_TABLE2**: ID of the VPC routing table.
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

- **VPC**: ID of the VPC.
- **ROUTING_TABLE**: ID of the VPC routing table.
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

- **VPC**: ID of the VPC.
- **ROUTING_TABLE**: ID of the VPC routing table.
- **ROUTE**: ID of the VPC route.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-table-route-create
{: #vpc-routing-table-route-create}

Create a VPC route.

```
ibmcloud is vpc-routing-table-route-create VPC ROUTING_TABLE --zone ZONE_NAME --destination DESTINATION_CIDR --next-hop NEXT_HOP [--action delegate_vpc | delegate | deliver | drop] [--name NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpc-routing-table-route-create}

- `ibmcloud is vpc-routing-table-route-create 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1d456 --name my-vpc-route --action deliver --zone us-south-1 --destination  10.2.2.0/24 --next-hop 10.0.0.2 --output JSON`
- `ibmcloud is vpc-routing-table-route-create 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1d456 --name my-vpc-route --action delegate --zone us-south-1 --destination  10.2.2.0/24 --output JSON`
- `ibmcloud is vpc-routing-table-route-create 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1d456 --name my-vpc-route --action drop --zone us-south-1 --destination  10.2.2.0/24 --output JSON`

#### Command options
{: #command-options-vpc-routing-table-route-create}

- **VPC**: ID of the VPC.
- **ROUTING_TABLE**: ID of the VPC routing table.
- **--zone**: Name of the zone.
- **--action**: The action to perform with a packet that matches the route. One of: **delegate_vpc**, **delegate**, **deliver**, **drop**.
- **--destination**: The destination CIDR of the route. At most two routes per zone in a table can have the same destination, and only if both routes have an action of **deliver**.
- **--next-hop**: If the action is **deliver**, the IP address or VPN connection ID of the next hop to which to route packets.
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

- **VPC**: ID of the VPC.
- **ROUTING_TABLE**: ID of the VPC routing table.
- **ROUTE**: ID of the VPC route.
- **--name**: New name of the route.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routing-table-route-delete
{: #vpc-routing-table-route-delete}

Delete VPC routes.

```
ibmcloud is vpc-routing-table-route-delete VPC ROUTING_TABLE (ROUTE1 ROUTE2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-routing-table-route-delete}

- **VPC**: ID of the VPC.
- **ROUTING_TABLE**: ID of the VPC routing table.
- **ROUTE1**: ID of the VPC route.
- **ROUTE2**: ID of the VPC route.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-routing-table
{: #subnet-routing-table}

View details of routing table that is attached to the subnet.

```
ibmcloud is subnet-routing-table SUBNET [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnet-routing-table}

- **SUBNET**: ID of the subnet.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Security groups
{: #security-groups-cli-ref}

### ibmcloud is security-group
{: #security-group}

View details of a security group.

```
ibmcloud is security-group GROUP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-security-group}

- **GROUP**: ID of the security group.
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

- `ibmcloud is security-group-create my-security-group 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is security-group-create my-security-group 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --resource-group-id fee82deba12e4c0fb69c3b09d1f12345`
- `ibmcloud is security-group-create my-security-group 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --resource-group-name Default`
- `ibmcloud is security-group-create my-security-group 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --output JSON`

#### Command options
{: #command-options-security-group-create}

- **GROUP_NAME**: Name of the security group.
- **VPC**: ID of the VPC.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-delete
{: #security-group-delete}

Delete security groups.

```
ibmcloud is security-group-delete (GROUP1 GROUP2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-security-group-delete}

- **GROUP1**: ID of the security group.
- **GROUP2**: ID of the security group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-network-interface
{: #security-group-network-interface}

View details of a network interface of a security group.

```
ibmcloud is security-group-network-interface GROUP NIC [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-security-group-network-interface}

- **GROUP**: ID of the security group.
- **NIC**: ID of the network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-network-interface-add
{: #security-group-network-interface-add}

Add a network interface to a security group.

```
ibmcloud is security-group-network-interface-add GROUP NIC [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-security-group-network-interface-add}

- `ibmcloud is security-group-network-interface-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --output JSON`

#### Command options
{: #command-options-security-group-network-interface-add}

- **GROUP**: ID of the security group.
- **NIC**: ID of the network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-network-interface-remove
{: #security-group-network-interface-remove}

Remove network interfaces from a security group.

```
ibmcloud is security-group-network-interface-remove GROUP (NIC1 NIC2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-security-group-network-interface-remove}

- **GROUP**: ID of the security group.
- **NIC1**: ID of the network interface.
- **NIC2**: ID of the network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-network-interfaces
{: #security-group-network-interfaces}

List all network interfaces of a security group.

```
ibmcloud is security-group-network-interfaces GROUP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-security-group-network-interfaces}

- **GROUP**: ID of the security group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-rule
{: #security-group-rule}

View details of a security group rule.

```
ibmcloud is security-group-rule GROUP RULE_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-security-group-rule}

- **GROUP**: ID of the security group.
- **RULE_ID**: ID of the security group rule.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-rule-add
{: #security-group-rule-add}

Add a rule to a security group.

```
ibmcloud is security-group-rule-add GROUP DIRECTION PROTOCOL [--remote REMOTE_ADDRESS | CIDR_BLOCK | SECURITY_GROUP_ID] [--icmp-type ICMP_TYPE [--icmp-code ICMP_CODE]] [--port-min PORT_MIN] [--port-max PORT_MAX] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-security-group-rule-add}

- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound all`
- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound icmp --icmp-type 8 --icmp-code 0`
- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound all --remote 12.2.2.3`
- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound tcp --port-min 4 --port-max 22 --output JSON`

#### Command options
{: #command-options-security-group-rule-add}

- **GROUP**: ID of the security group.
- **DIRECTION**: Direction of traffic to enforce. One of: **inbound**, **outbound**.
- **PROTOCOL**: Protocol to enforce. One of: **all**, **icmp**, **tcp**, **udp**.
- **--remote**: The set of network interfaces from which this rule allows traffic, Can be specified as either an REMOTE_ADDRESS, CIDR_BLOCK and SECURITY_GROUP_ID. If unspecified, then traffic is allowed from any source (or to any source, for outbound rules).
- **--icmp-type**: ICMP traffic type to allow. Valid values from **0** to **254**. This option is specified only when protocol is set to **icmp**. If unspecified, all types are allowed.
- **--icmp-code**: ICMP traffic code to allow. Valid values from **0** to **255**. This option is specified only when protocol is set to **icmp**. If unspecified, all codes are allowed.
- **--port-min**: Minimum port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp**. If unspecified, all ports are allowed (default: **1**).
- **--port-max**: Maximum port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp**. If unspecified, all ports are allowed (default: **65535**).
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-rule-delete
{: #security-group-rule-delete}

Delete rules from a security group.

```
ibmcloud is security-group-rule-delete GROUP (RULE_ID1 RULE_ID2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-security-group-rule-delete}

- **GROUP**: ID of the security group.
- **RULE_ID1**: ID of the security group rule.
- **RULE_ID2**: ID of the security group rule.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-rule-update
{: #security-group-rule-update}

Update a rule of a security group.

```
ibmcloud is security-group-rule-update GROUP RULE_ID [--direction inbound | outbound] [--remote REMOTE_ADDRESS | CIDR_BLOCK | SECURITY_GROUP_ID] [--icmp-type ICMP_TYPE [--icmp-code ICMP_CODE]] [--port-min PORT_MIN] [--port-max PORT_MAX] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-security-group-rule-update}

- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound`
- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --icmp-type 8 --icmp-code 0`
- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --port-min 4 --port-max 22`
- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --remote 12.2.2.3`
- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --output JSON`

#### Command options
{: #command-options-security-group-rule-update}

- **GROUP**: ID of the security group.
- **RULE_ID**: ID of the security group rule.
- **--direction**: Direction of traffic to enforce. One of: **inbound**, **outbound**.
- **--remote**: The set of network interfaces from which this rule allows traffic, Can be specified as either an REMOTE_ADDRESS, CIDR_BLOCK and SECURITY_GROUP_ID. If unspecified, then traffic is allowed from any source (or to any source, for outbound rules).
- **--icmp-type**: ICMP traffic type to allow. Valid values from **0** to **254**. This option is specified only when protocol is set to **icmp**. If unspecified, all types are allowed.
- **--icmp-code**: ICMP traffic code to allow. Valid values from **0** to **255**. This option is specified only when protocol is set to **icmp**. If unspecified, all codes are allowed.
- **--port-min**: Minimum port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp**. If unspecified, all ports are allowed (default: **1**).
- **--port-max**: Maximum port number. Valid values are from **1** to **65535**. This option is specified only when protocol is set to **tcp** or **udp**. If unspecified, all ports are allowed (default: **65535**).
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-rules
{: #security-group-rules}

List all rules of a security group.

```
ibmcloud is security-group-rules GROUP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-security-group-rules}

- **GROUP**: ID of the security group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-update
{: #security-group-update}

Update a security group.

```
ibmcloud is security-group-update GROUP [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-security-group-update}

- `ibmcloud is security-group-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-security-group-name --output JSON`

#### Command options
{: #command-options-security-group-update}

- **GROUP**: ID of the security group.
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

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-target
{: #security-group-target}

View details of a target of a security group.

```
ibmcloud is security-group-target GROUP TARGET [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-security-group-target}

- **GROUP**: ID of the security group.
- **TARGET**: ID of the target.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-target-add
{: #security-group-target-add}

Add a target to a security group.

```
ibmcloud is security-group-target-add GROUP TARGET [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-security-group-target-add}

- `ibmcloud is security-group-target-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --output JSON`

#### Command options
{: #command-options-security-group-target-add}

- **GROUP**: ID of the security group.
- **TARGET**: ID of the target.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-target-remove
{: #security-group-target-remove}

Remove targets from a security group.

```
ibmcloud is security-group-target-remove GROUP (TARGET1 TARGET2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-security-group-target-remove}

- **GROUP**: ID of the security group.
- **TARGET1**: ID of the target.
- **TARGET2**: ID of the target.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is security-group-targets
{: #security-group-targets}

List all targets of a security group.

```
ibmcloud is security-group-targets GROUP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-security-group-targets}

- **GROUP**: ID of the security group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Subnets
{: #subnet-cli-ref}

### ibmcloud is subnet
{: #subnet}

View details of a subnet.

```
ibmcloud is subnet SUBNET [--show-attached] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnet}

- **SUBNET**: ID of the subnet.
- **--show-attached**: View details of resources (instances, load balancers, VPN gateways) attached to the subnet.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-create
{: #subnet-create}

Create a subnet.

```
ibmcloud is subnet-create SUBNET_NAME VPC ((--zone ZONE_NAME --ipv4-address-count ADDR_COUNT) | --ipv4-cidr-block CIDR_BLOCK) [--network-acl-id NETWORK_ACL_ID] [--public-gateway-id PUBLIC_GATEWAY_ID] [--routing-table-id ROUTING_TABLE_ID] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-subnet-create}

- `ibmcloud is subnet-create my-subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4-cidr-block 10.10.10.0/24`
- `ibmcloud is subnet-create my-subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4-address-count 256 --zone us-south-2`
- `ibmcloud is subnet-create my-subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4-address-count 256 --zone us-south-2 --network-acl-id 8daca77a-4980-4d33-8f3e-7038797be8f9`
- `ibmcloud is subnet-create my-subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4-address-count 256 --zone us-south-2 --public-gateway-id 8daca77a-4980-4d33-8f3e-7038797be8f9`
- `ibmcloud is subnet-create my-subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4-address-count 256 --zone us-south-2 --public-gateway-id 8daca77a-4980-4d33-8f3e-7038797be8f9 --output JSON`
- `ibmcloud is subnet-create my-subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4-address-count 256 --zone us-south-2 --routing-table-id 8daca77a-4980-4d33-8f3e-7038797be8f9`

#### Command options
{: #command-options-subnet-create}

- **SUBNET_NAME**: Name of the subnet.
- **VPC**: ID of the VPC.
- **--ipv4-cidr-block**: the IPv4 range of the subnet. This option is mutually exclusive with **--ipv4-address-count**.
- **--ipv4-address-count**: The total number of IPv4 addresses required, must be a power of 2 and minimum value is **8**. This option is mutually exclusive with **--ipv4-cidr-block**.
- **--zone**: Name of the zone.
- **--network-acl-id**: The ID of the network ACL.
- **--public-gateway-id**: The ID of the public gateway.
- **--routing-table-id**: The ID of the routing table.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-delete
{: #subnet-delete}

Delete subnets.

```
ibmcloud is subnet-delete (SUBNET1 SUBNET2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-subnet-delete}

- **SUBNET1**: ID of the subnet.
- **SUBNET2**: ID of the subnet.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-update
{: #subnet-update}

Update a subnet.

```
ibmcloud is subnet-update SUBNET [--name NEW_NAME] [--network-acl-id NETWORK_ACL_ID] [--public-gateway-id PUBLIC_GATEWAY_ID] [--routing-table-id ROUTING_TABLE_ID] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-subnet-update}

- `ibmcloud is subnet-update ec8bb350-d802-4f1b-b362-b848abd5bb65 --name my-subnet`
- `ibmcloud is subnet-update ec8bb350-d802-4f1b-b362-b848abd5bb65 --network-acl-id 8daca77a-4980-4d33-8f3e-7038797be8f9`
- `ibmcloud is subnet-update ec8bb350-d802-4f1b-b362-b848abd5bb65 --public-gateway-id 8daca77a-4980-4d33-8f3e-7038797be8f9`
- `ibmcloud is subnet-update ec8bb350-d802-4f1b-b362-b848abd5bb65 --name my-subnet --output JSON`
- `ibmcloud is subnet-update ec8bb350-d802-4f1b-b362-b848abd5bb65 --routing-table-id 8daca77a-4980-4d33-8f3e-7038797be8f9`

#### Command options
{: #command-options-subnet-update}

- **SUBNET**: ID of the subnet.
- **--name**: New name of the subnet.
- **--network-acl-id**: The ID of the network ACL.
- **--public-gateway-id**: The ID of the public gateway.
- **--routing-table-id**: The ID of the routing table.
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

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-public-gateway
{: #subnet-public-gateway}

View details of public gateway attached to the subnet.

```
ibmcloud is subnet-public-gateway SUBNET [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnet-public-gateway}

- **SUBNET**: ID of the subnet.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-public-gateway-detach
{: #subnet-public-gateway-detach}

Detach the public gateway from a subnet.

```
ibmcloud is subnet-public-gateway-detach SUBNET [-q, --quiet]
```

#### Command options
{: #command-options-subnet-public-gateway-detach}

- **SUBNET**: ID of the subnet.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-reserved-ips
{: #subnet-reserved-ips}

List all reserved IPs in the subnet.

```
ibmcloud is subnet-reserved-ips SUBNET [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnet-reserved-ips}

- **SUBNET**: ID of the subnet.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-reserved-ip
{: #subnet-reserved-ip}

View details of reserved ip.

```
ibmcloud is subnet-reserved-ip SUBNET RESERVED_IP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnet-reserved-ip}

- **SUBNET**: ID of the subnet.
- **RESERVED_IP**: ID of the reserved IP.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-reserved-ip-create
{: #subnet-reserved-ip-create}

Reserve an IP in a subnet.

```
ibmcloud is subnet-reserved-ip-create SUBNET [--name NAME] [--auto-delete true | false] [--target TARGET] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-subnet-reserved-ip-create}

- `ibmcloud is subnet-reserved-ip-create 2201-3f2e33d4-2140-44b4-843c-d73e03d585f1 --name my-reserved-ip --auto-delete true`
- `ibmcloud is subnet-reserved-ip-create 2201-3f2e33d4-2140-44b4-843c-d73e03d585f1 --name my-reserved-ip --auto-delete true --target r134-5be98168-017a-459c-959f-7a6c1f7b813b`
- `ibmcloud is subnet-reserved-ip-create 2201-3f2e33d4-2140-44b4-843c-d73e03d585f1 --name my-reserved-ip --output JSON`

#### Command options
{: #command-options-subnet-reserved-ip-create}

- **SUBNET**: ID of the subnet.
- **--name**: The user-defined name for this reserved IP. Names must be unique within the subnet that the reserved IP resides in. Names beginning with **ibm-** are reserved for provider-owned resources.
- **--auto-delete**: If set to **true**, this reserved IP automatically deletes when the target is deleted. One of: **true**, **false**. (default: **true**).
- **--target**: The target of the reserved IP.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-reserved-ip-update
{: #subnet-reserved-ip-update}

Update a reserved ip.

```
ibmcloud is subnet-reserved-ip-update SUBNET RESERVED_IP [--name NEW_NAME] [--auto-delete true | false] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-subnet-reserved-ip-update}

- `ibmcloud is subnet-reserved-ip-update 2201-3f2e33d4-2140-44b4-843c-d73e03d585f1 2201-7fc11925-47ff-4080-a314-be64c662c302 --name my-reserved-ip2`
- `ibmcloud is subnet-reserved-ip-update 2201-3f2e33d4-2140-44b4-843c-d73e03d585f1 2201-7fc11925-47ff-4080-a314-be64c662c302 --auto-delete false`
- `ibmcloud is subnet-reserved-ip-update 2201-3f2e33d4-2140-44b4-843c-d73e03d585f1 2201-7fc11925-47ff-4080-a314-be64c662c302 --name my-reserved-ip2 --output JSON`

#### Command options
{: #command-options-subnet-reserved-ip-update}

- **SUBNET**: ID of the subnet.
- **RESERVED_IP**: ID of the reserved IP.
- **--name**: The new name of the reserved IP.
- **--auto-delete**: If set to **true**, this reserved IP automatically deletes when the target is deleted. One of: **true**, **false**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is subnet-reserved-ip-delete
{: #subnet-reserved-ip-delete}

Release reserved IPs.

```
ibmcloud is subnet-reserved-ip-delete SUBNET (RESERVED_IP1 RESERVED_IP2 ...) [-f, --force] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-subnet-reserved-ip-delete}

- **SUBNET**: ID of the subnet.
- **RESERVED_IP1**: ID of the reserved IP.
- **RESERVED_IP2**: ID of the reserved IP.
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

- **VPC**: ID of the VPC.
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

- **VPC**: ID of the VPC.
- **PREFIX**: ID of the VPC address prefix.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-address-prefix-create
{: #vpc-address-prefix-create}

Create an address prefix.

```
ibmcloud is vpc-address-prefix-create PREFIX_NAME VPC ZONE_NAME CIDR [--default false | true] [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-vpc-address-prefix-create}

- `ibmcloud is vpc-address-prefix-create my-prefix 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 us-south-2 10.0.0.0/24 --default true --output JSON`

#### Command options
{: #command-options-vpc-address-prefix-create}

- **PREFIX_NAME**: Name of the VPC address prefix.
- **VPC**: ID of the VPC.
- **ZONE_NAME**: Name of the zone.
- **CIDR**: The IPv4 range of the address prefix, expressed in CIDR format. It must not overlap with any existing address prefixes in the VPC, and must fall within the [RFC 1918](https://tools.ietf.org/html/rfc1918) address ranges. The prefix length of the address prefix's CIDR must be between `/9` (8,388,608 addresses) and `/29` (eight addresses).
- **--default**: This flag indicates whether this is the default prefix for this zone in this VPC. One of: **false**, **true**. (default: **false**).
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-address-prefix-delete
{: #vpc-address-prefix-delete}

Delete address prefixes.

```
ibmcloud is vpc-address-prefix-delete VPC (PREFIX1 PREFIX2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-address-prefix-delete}

- **VPC**: ID of the VPC.
- **PREFIX1**: ID of the VPC address prefix.
- **PREFIX2**: ID of the VPC address prefix.
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

#### Command example
{: #command-example-vpc-address-prefix-update}

- `ibmcloud is vpc-address-prefix-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 fee82deba12e4c0fb69c3b09d1f12345 --name my-prefix --default false --output JSON`

#### Command options
{: #command-options-vpc-address-prefix-update}

- **VPC**: ID of the VPC.
- **PREFIX**: ID of the VPC address prefix.
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

- **VPC**: ID of the VPC.
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
- **--classic-access**: This flag indicates whether the VPC should be connected to Classic Infrastructure. The default value is false.
- **--address-prefix-management**: This flag indicates if a default address prefix is automatically created for each zone in this VPC. If **manual**, this VPC is created with no default address prefixes. One of: **auto**, **manual**. (default: **auto**).
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
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

- **VPC**: ID of the VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-delete
{: #vpc-delete}

Delete VPCs.

```
ibmcloud is vpc-delete (VPC1 VPC2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-delete}

- **VPC1**: ID of the VPC.
- **VPC2**: ID of the VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-route
{: #vpc-route}

View details of a VPC route.

```
ibmcloud is vpc-route VPC ROUTE [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-route}

- **VPC**: ID of the VPC.
- **ROUTE**: ID of the VPC route.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-route-create
{: #vpc-route-create}

Create a route.

```
ibmcloud is vpc-route-create ROUTE_NAME VPC --zone ZONE_NAME --destination DESTINATION_CIDR --next-hop-ip NEXT_HOP_IP [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-vpc-route-create}

- `ibmcloud is vpc-route-create my-vpc-route 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --zone us-south-1 --destination  10.2.2.0/24 --next-hop-ip 10.0.0.2 --output JSON`

#### Command options
{: #command-options-vpc-route-create}

- **ROUTE_NAME**: Name of the VPC route.
- **VPC**: ID of the VPC.
- **--zone**: Name of the zone.
- **--destination**: The destination CIDR of the route.
- **--next-hop-ip**: The IP address of the next hop to which to route packets.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-route-update
{: #vpc-route-update}

Update a route.

```
ibmcloud is vpc-route-update VPC ROUTE --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-vpc-route-update}

- `ibmcloud is vpc-route-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1d456 --name my-vpc-route --output JSON`

#### Command options
{: #command-options-vpc-route-update}

- **VPC**: ID of the VPC.
- **ROUTE**: ID of the VPC route.
- **--name**: New name of the route.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-route-delete
{: #vpc-route-delete}

Delete routes.

```
ibmcloud is vpc-route-delete VPC (ROUTE1 ROUTE2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-route-delete}

- **VPC**: ID of the VPC.
- **ROUTE1**: ID of the VPC route.
- **ROUTE2**: ID of the VPC route.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-routes
{: #vpc-routes}

List all routes.

```
ibmcloud is vpc-routes VPC [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpc-routes}

- **VPC**: ID of the VPC.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpc-update
{: #vpc-update}

Update a VPC.

```
ibmcloud is vpc-update VPC --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-vpc-update}

- `ibmcloud is vpc-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-vpc`

#### Command options
{: #command-options-vpc-update}

- **VPC**: ID of the VPC.
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

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
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
ibmcloud is endpoint-gateway ENDPOINT_GATEWAY [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-endpoint-gateway}

- **ENDPOINT_GATEWAY**: ID of the endpoint gateway.
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

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is endpoint-gateway-create
{: #endpoint-gateway-create}

Create an endpoint gateway.

```
ibmcloud is endpoint-gateway-create --vpc-id VPC_ID --target TARGET [--name NAME] [(--reserved-ip-id RESERVED_IP_ID1 --reserved-ip-id RESERVED_IP_ID2 ...) | (--new-reserved-ip NEW_RESERVED_IP1 --new-reserved-ip NEW_RESERVED_IP2 ...)] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-endpoint-gateway-create}

- `ibmcloud is endpoint-gateway-create --vpc-id 417f1275-b11a-4077-8755-84e795bc3172 --target crn:v1:bluemix:public:kms:us-south:a/86e1130a970148348271c47ed80ac3f3:7372408d-b68a-47f5-b5e5-4b64390aebff:: --name myegw1`
Create endpoint gateway without binding reserved IP.
- `ibmcloud is endpoint-gateway-create --vpc-id 4215db60-4515-4a5f-9822-341d8bea5985 --target crn:v1:bluemix:public:kms:us-south:a/86e1130a970148348271c47ed80ac3f3:7372408d-b68a-47f5-b5e5-4b64390aebff:: --name myegw2 --new-reserved-ip '{"subnet": {"id": "a529e1b9-d4cf-48a0-a1bb-e9a1d32cb6e7"}}'`
Create endpoint gateway with binding new reserved IP configuration that has only required subnet ID data.
- `ibmcloud is endpoint-gateway-create --vpc-id 4215db60-4515-4a5f-9822-341d8bea5985 --target crn:v1:bluemix:public:kms:us-south:a/86e1130a970148348271c47ed80ac3f3:7372408d-b68a-47f5-b5e5-4b64390aebff:: --name myegw2 --new-reserved-ip '{"subnet": {"id": "a529e1b9-d4cf-48a0-a1bb-e9a1d32cb6e7"},"name":"my-reserved-ip1","auto_delete":false}'`
Create endpoint gateway with binding new reserved IP configuration with subnet ID, reserved IP name, reserved IP auto_delete configuration.
- `ibmcloud is endpoint-gateway-create --vpc-id 417f1275-b11a-4077-8755-84e795bc3172 --target ibm-ntp-server --name myegw3`
Create endpoint gateway with the provider infrastructure service 'ibm-ntp-server'.
- `ibmcloud is endpoint-gateway-create --vpc-id 417f1275-b11a-4077-8755-84e795bc3172 --target my-key-protect-inst1 --name myegw1 --reserved-ip-id 062d13f9-d46d-483d-bdc9-42c0326e73f0 --reserved-ip-id 6fcfb762-b9aa-41fa-9332-d228e76ee39b`
Create endpoint gateway with binding existing reserved IPs.

#### Command options
{: #command-options-endpoint-gateway-create}

- **--vpc-id**: ID of the VPC.
- **--target**: The name of the provider infrastructure service or the CRN for a provider cloud service instance. You can use command **ibmcloud is endpoint-gateway-targets** to list the provider cloud and infrastructure services that are qualified to be set as endpoint gateway target.
- **--name**: New name of the endpoint gateway.
- **--reserved-ip-id**: ID of the reserved IP to be bound to the endpoint gateway.
- **--new-reserved-ip**: RESERVED_IP_JSON|@RESERVED_IP_JSON_FILE, new reserved ip configuration in JSON or JSON file.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is endpoint-gateway-update
{: #endpoint-gateway-update}

Update an endpoint gateway.

```
ibmcloud is endpoint-gateway-update ENDPOINT_GATEWAY --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-endpoint-gateway-update}

- **ENDPOINT_GATEWAY**: ID of the endpoint gateway.
- **--name**: New name of the endpoint gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is endpoint-gateway-reserved-ip-bind
{: #endpoint-gateway-reserved-ip-bind}

Bind a reserved IP to an endpoint gateway.

```
ibmcloud is endpoint-gateway-reserved-ip-bind ENDPOINT_GATEWAY --reserved-ip-id RESERVED_IP_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-endpoint-gateway-reserved-ip-bind}

- **ENDPOINT_GATEWAY**: ID of the endpoint gateway.
- **--reserved-ip-id**: ID of the reserved IP address to be unbound.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is endpoint-gateway-reserved-ip-unbind
{: #endpoint-gateway-reserved-ip-unbind}

Unbind a reserved IP to an endpoint gateway.

```
ibmcloud is endpoint-gateway-reserved-ip-unbind ENDPOINT_GATEWAY (--reserved-ip-id RESERVED_IP_ID | --address ADDRESS) [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-endpoint-gateway-reserved-ip-unbind}

- **ENDPOINT_GATEWAY**: ID of the endpoint gateway.
- **--address**: The reserved IP address to be unbound.
- **--reserved-ip-id**: ID of the reserved IP address to be unbound.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is endpoint-gateway-delete
{: #endpoint-gateway-delete}

Delete endpoint gateways.

```
ibmcloud is endpoint-gateway-delete (ENDPOINT_GATEWAY1 ENDPOINT_GATEWAY2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-endpoint-gateway-delete}

- **ENDPOINT_GATEWAY1**: ID of the endpoint gateway.
- **ENDPOINT_GATEWAY2**: ID of the endpoint gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

## Virtual private network (VPN) gateways
{: #vpn-clis}

This section gives details about the CLI commands that are available for working with VPN gateways, including IKE and IPsec policies.


### ibmcloud is ike-policies
{: #ike-policies}

List all IKE policies.

```
ibmcloud is ike-policies [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-ike-policies}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ike-policy
{: #ike-policy}

View details of an IKE policy.

```
ibmcloud is ike-policy IKE_POLICY_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-ike-policy}

- **IKE_POLICY_ID**: ID of the IKE policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ike-policy-connections
{: #ike-policy-connections}

List all connections that use the IKE policy.

```
ibmcloud is ike-policy-connections IKE_POLICY_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-ike-policy-connections}

- **IKE_POLICY_ID**: ID of the IKE policy.
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

- `ibmcloud is ike-policy-create my-ike-policy md5 2 aes128 2`
- `ibmcloud is ike-policy-create my-ike-policy md5 2 aes128 2 --key-lifetime 28000`
- `ibmcloud is ike-policy-create my-ike-policy md5 2 aes128 2 --resource-group-name Default`
- `ibmcloud is ike-policy-create my-ike-policy md5 2 aes128 2 --resource-group-id fee82deba12e4c0fb69c3b09d1f12345 --output JSON`

#### Command options
{: #command-options-ike-policy-create}

- **IKE_POLICY_NAME**: Name of the IKE policy.
- **AUTHENTICATION_ALGORITHM**: The authentication algorithm. One of: **md5**, **sha1**, **sha256**, **sha512**.
- **DH_GROUP**: The Diffie-Hellman group. One of: **2**, **5**, **14**, **19**.
- **ENCRYPTION_ALGORITHM**: The encryption algorithm. One of: **triple_des**, **aes128**, **aes256**.
- **IKE_VERSION**: The IKE protocol version. One of: **1**, **2**.
- **--key-lifetime**: The key lifetime in seconds. Maximum: **86400**, Minimum: **1800**. (default: **28800**).
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ike-policy-delete
{: #ike-policy-delete}

Delete IKE policies.

```
ibmcloud is ike-policy-delete (IKE_POLICY_ID1 IKE_POLICY_ID2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-ike-policy-delete}

- **IKE_POLICY_ID1**: ID of the IKE policy.
- **IKE_POLICY_ID2**: ID of the IKE policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ike-policy-update
{: #ike-policy-update}

Update an IKE policy.

```
ibmcloud is ike-policy-update IKE_POLICY_ID [--name NEW_NAME] [--authentication-algorithm md5 | sha1 | sha256 | sha512] [--dh-group 2 | 5 | 14 | 19] [--encryption-algorithm triple_des | aes128 | aes256] [--ike-version 1 | 2] [--key-lifetime KEY_LIFETIME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-ike-policy-update}

- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --name my-ike-policy`
- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --authentication-algorithm md5`
- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --dh-group 2`
- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --encryption-algorithm aes128`
- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --ike-version 2`
- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --key-lifetime 28000 --output JSON`

#### Command options
{: #command-options-ike-policy-update}

- **IKE_POLICY_ID**: ID of the IKE policy.
- **--name**: New name of the IKE policy.
- **--authentication-algorithm**: The authentication algorithm. One of: **md5**, **sha1**, **sha256**, **sha512**.
- **--dh-group**: The Diffie-Hellman group. One of: **2**, **5**, **14**, **19**.
- **--encryption-algorithm**: The encryption algorithm. One of: **triple_des**, **aes128**, **aes256**.
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

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ipsec-policy
{: #ipsec-policy}

View details of an IPsec policy.

```
ibmcloud is ipsec-policy IPSEC_POLICY_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-ipsec-policy}

- **IPSEC_POLICY_ID**: ID of the IPsec policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ipsec-policy-connections
{: #ipsec-policy-connections}

List all connections that use the IPsec policy.

```
ibmcloud is ipsec-policy-connections IPSEC_POLICY_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-ipsec-policy-connections}

- **IPSEC_POLICY_ID**: ID of the IPsec policy.
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

- `ibmcloud is ipsec-policy-create my-ipsec-policy md5 aes128 group_2`
- `ibmcloud is ipsec-policy-create my-ipsec-policy md5 aes128 group_2 --key-lifetime 3600`
- `ibmcloud is ipsec-policy-create my-ipsec-policy md5 aes128 group_2 --resource-group-name Default`
- `ibmcloud is ipsec-policy-create my-ipsec-policy md5 aes128 group_2 --resource-group-id fee82deba12e4c0fb69c3b09d1f12345 --output JSON`

#### Command options
{: #command-options-ipsec-policy-create}

- **IPSEC_POLICY_NAME**: Name of the IPsec policy.
- **AUTHENTICATION_ALGORITHM**: The authentication algorithm. One of: **md5**, **sha1**, **sha256**, **sha512**.
- **ENCRYPTION_ALGORITHM**: The encryption algorithm. One of: **triple_des**, **aes128**, **aes256**.
- **PFS**: The Diffie-Hellman group. One of: **disabled**, **group_2**, **group_5**, **group_14**, **group_19**.
- **--key-lifetime**: The key lifetime in seconds. Maximum: **86400**, Minimum: **1800**. (default: **3600**).
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ipsec-policy-delete
{: #ipsec-policy-delete}

Delete an IPsec policies.

```
ibmcloud is ipsec-policy-delete (IPSEC_POLICY_ID1 IPSEC_POLICY_ID2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-ipsec-policy-delete}

- **IPSEC_POLICY_ID1**: ID of the IPsec policy.
- **IPSEC_POLICY_ID2**: ID of the IPsec policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is ipsec-policy-update
{: #ipsec-policy-update}

Update an IPsec policy.

```
ibmcloud is ipsec-policy-update IPSEC_POLICY_ID [--name NEW_NAME] [--authentication-algorithm md5 | sha1 | sha256 | sha512] [--pfs disabled | group_2 | group_5 | group_14 | group_19] [--encryption-algorithm triple_des | aes128 | aes256] [--key-lifetime KEY_LIFETIME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-ipsec-policy-update}

- `ibmcloud is ipsec-policy-update fee82deba12e4c0fb69c3b09d1f12345 --name my-ipsec-policy`
- `ibmcloud is ipsec-policy-update fee82deba12e4c0fb69c3b09d1f12345 --authentication-algorithm md5`
- `ibmcloud is ipsec-policy-update fee82deba12e4c0fb69c3b09d1f12345 --pfs group_2`
- `ibmcloud is ipsec-policy-update fee82deba12e4c0fb69c3b09d1f12345 --encryption-algorithm aes128`
- `ibmcloud is ipsec-policy-update fee82deba12e4c0fb69c3b09d1f12345 --key-lifetime 3600 --output JSON`

#### Command options
{: #command-options-ipsec-policy-update}

- **IPSEC_POLICY_ID**: ID of the IPsec policy.
- **--name**: New name of the IPsec policy.
- **--authentication-algorithm**: The authentication algorithm. One of: **md5**, **sha1**, **sha256**, **sha512**.
- **--pfs**: Perfect Forward Secrecy. One of: **disabled**, **group_2**, **group_5**, **group_14**, **group_19**.
- **--encryption-algorithm**: The encryption algorithm. One of: **triple_des**, **aes128**, **aes256**.
- **--key-lifetime**: The key lifetime in seconds. Maximum: **86400**, Minimum: **1800**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway
{: #vpn-gateway}

View details of a VPN gateway.

```
ibmcloud is vpn-gateway VPN_GATEWAY_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection
{: #vpn-gateway-connection}

View details of a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection VPN_GATEWAY_ID (CONNECTION_ID1 CONNECTION_ID2 ...) [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-connection}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **CONNECTION_ID1**: ID of the VPN connection.
- **CONNECTION_ID2**: ID of the VPN connection.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-create
{: #vpn-gateway-connection-create}

Create a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-create CONNECTION_NAME VPN_GATEWAY_ID PEER_ADDRESS PRESHARED_KEY --local-cidr CIDR1 --local-cidr CIDR2 ... --peer-cidr CIDR1 --peer-cidr CIDR2 ... [--admin-state-up true | false] [--dead-peer-detection-action restart | clear | hold | none] [--dead-peer-detection-interval INTERVAL] [--dead-peer-detection-timeout TIMEOUT] [--ike-policy IKE_POLICY_ID] [--ipsec-policy IPSEC_POLICY_ID] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-vpn-gateway-connection-create}

- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --admin-state-up true`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --dead-peer-detection-action clear --dead-peer-detection-interval 33 --dead-peer-detection-timeout 100`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --ipsec-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --ike-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --output JSON`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --admin-state-up true`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --dead-peer-detection-action clear --dead-peer-detection-interval 33 --dead-peer-detection-timeout 100`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --ipsec-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --ike-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 16.3.4.5 --local-cidr 12.3.4.5 --peer-cidr 16.3.4.5 --peer-cidr 12.3.4.5  --output JSON`

#### Command options
{: #command-options-vpn-gateway-connection-create}

- **CONNECTION_NAME**: Name of the connection.
- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **PEER_ADDRESS**: The IP address of the peer VPN gateway.
- **PRESHARED_KEY**: The preshared key.
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

Delete VPN gateway connections.

```
ibmcloud is vpn-gateway-connection-delete VPN_GATEWAY_ID (CONNECTION_ID1 CONNECTION_ID2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-connection-delete}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **CONNECTION_ID1**: ID of the VPN connection.
- **CONNECTION_ID2**: ID of the VPN connection.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-local-cidr-add
{: #vpn-gateway-connection-local-cidr-add}

Add a local CIDR to a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-local-cidr-add VPN_GATEWAY_ID CONNECTION_ID PREFIX_ADDRESS PREFIX_LENGTH [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-connection-local-cidr-add}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **CONNECTION_ID**: ID of the VPN connection.
- **PREFIX_ADDRESS**: The prefix address part of the CIDR.
- **PREFIX_LENGTH**: The prefix length part of the CIDR.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-local-cidr-delete
{: #vpn-gateway-connection-local-cidr-delete}

Remove a local CIDR from the VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-local-cidr-delete VPN_GATEWAY_ID CONNECTION_ID PREFIX_ADDRESS PREFIX_LENGTH [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-connection-local-cidr-delete}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **CONNECTION_ID**: ID of the VPN connection.
- **PREFIX_ADDRESS**: The prefix address part of the CIDR.
- **PREFIX_LENGTH**: The prefix length part of the CIDR.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-peer-cidr-add
{: #vpn-gateway-connection-peer-cidr-add}

Add a peer CIDR to a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-peer-cidr-add VPN_GATEWAY_ID CONNECTION_ID PREFIX_ADDRESS PREFIX_LENGTH [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-connection-peer-cidr-add}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **CONNECTION_ID**: ID of the VPN connection.
- **PREFIX_ADDRESS**: The prefix address part of the CIDR.
- **PREFIX_LENGTH**: The prefix length part of the CIDR.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-peer-cidr-delete
{: #vpn-gateway-connection-peer-cidr-delete}

Remove a peer CIDR from the VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-peer-cidr-delete VPN_GATEWAY_ID CONNECTION_ID PREFIX_ADDRESS PREFIX_LENGTH [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-connection-peer-cidr-delete}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **CONNECTION_ID**: ID of the VPN connection.
- **PREFIX_ADDRESS**: The prefix address part of the CIDR.
- **PREFIX_LENGTH**: The prefix length part of the CIDR.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-connection-update
{: #vpn-gateway-connection-update}

Update a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-update VPN_GATEWAY_ID CONNECTION_ID [--admin-state-up true | false] [--dead-peer-detection-action restart | clear | hold | none] [--dead-peer-detection-interval INTERVAL] [--dead-peer-detection-timeout TIMEOUT] [--ike-policy IKE_POLICY_ID] [--ipsec-policy IPSEC_POLICY_ID] [--peer-address ADDRESS] [--psk PSK] [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-vpn-gateway-connection-update}

- `ibmcloud is vpn-gateway-connection-update fee82deba12e4c0fb69c3b09d1f12345 gfe82deba12e4c0fb69c3b09d1f23456 --admin-state-up true --dead-peer-detection-action clear --dead-peer-detection-interval 33 --dead-peer-detection-timeout 100  --ipsec-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479  --ipsec-policy 05251a2e-d6c5-42b4-97b0-b5f8e8d1f445 --peer-address 234.3.4.5 -psk rweirjgiort --name my-new-connection --output JSON`

#### Command options
{: #command-options-vpn-gateway-connection-update}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **CONNECTION_ID**: ID of the VPN connection.
- **--admin-state-up**: If set to false, the VPN gateway connection is shut down. One of: **true**, **false**.
- **--dead-peer-detection-action**: Dead Peer Detection actions. One of: **restart**, **clear**, **hold**, **none**.
- **--dead-peer-detection-interval**: Dead Peer Detection interval in seconds.
- **--dead-peer-detection-timeout**: Dead Peer Detection timeout in seconds.
- **--ike-policy**: ID of the IKE policy.
- **--ipsec-policy**: ID of the IPsec policy.
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
ibmcloud is vpn-gateway-connections VPN_GATEWAY_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-connections}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
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

- `ibmcloud is vpn-gateway-create my-vpc-gateway fee82deba12e4c0fb69c3b09d1f12345 --mode route`
- `ibmcloud is vpn-gateway-create my-vpc-gateway fee82deba12e4c0fb69c3b09d1f12345 --mode policy`
- `ibmcloud is vpn-gateway-create my-vpc-gateway fee82deba12e4c0fb69c3b09d1f12345 --mode route --resource-group-name Default`
- `ibmcloud is vpn-gateway-create my-vpc-gateway fee82deba12e4c0fb69c3b09d1f12345 --mode route --resource-group-id fee82deba12e4c0fb69c3b09d1f12345 --output JSON`

#### Command options
{: #command-options-vpn-gateway-create}

- **VPN_GATEWAY_NAME**: Name of the VPN gateway.
- **SUBNET**: ID of the subnet.
- **--mode**: The mode of the VPN gateway. One of: **policy**, **route**.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-delete
{: #vpn-gateway-delete}

Delete VPN gateways.

```
ibmcloud is vpn-gateway-delete (VPN_GATEWAY_ID1 VPN_GATEWAY_ID2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-vpn-gateway-delete}

- **VPN_GATEWAY_ID1**: ID of the VPN gateway.
- **VPN_GATEWAY_ID2**: ID of the VPN gateway.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is vpn-gateway-update
{: #vpn-gateway-update}

Update a VPN gateway.

```
ibmcloud is vpn-gateway-update VPN_GATEWAY_ID [--name NEW_NAME] [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-vpn-gateway-update}

- `ibmcloud is vpn-gateway-update fee82deba12e4c0fb69c3b09d1f12345 --name my-gateway --output JSON`

#### Command options
{: #command-options-vpn-gateway-update}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
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

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
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

- **IMAGE**: ID of the image.
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
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is image-create
{: #image-create}

Create an image.

```
ibmcloud is image-create IMAGE_NAME ([--file IMAGE_FILE_LOCATION --os-name OPERATING_SYSTEM_NAME [--encrypted-data-key ENCRYPTED_DATA_KEY --encryption-key ENCRYPTION_KEY]] | [--source-volume SOURCE_VOLUME --encryption-key-volume ENCRYPTION_KEY_VOLUME]) [--required-image-flag REQUIRED_IMAGE_FLAG1 --required-image-flag REQUIRED_IMAGE_FLAG2 ...] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
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
- **--source-volume**: The volume from which to create the image. The specified volume must originate from image. The volume's active and busy property value must be **false**, and the volume attached instance must be in stopped status.
- **--encryption-key-volume**: A reference to the root key to be used to wrap the system-generated data encryption key for the image. If this property is not provided, the root key from source volume is used.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
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

- **IMAGE**: ID of the image.
- **--name**: New name of the image.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is image-delete
{: #image-delete}

Delete images.

```
ibmcloud is image-delete (IMAGE1 IMAGE2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-image-delete}

- **IMAGE1**: ID of the image.
- **IMAGE2**: ID of the image.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
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

- **INSTANCE**: ID of the instance.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-initialization-values
{: #instance-initialization-values}

View initialization details of a virtual instance.

```
ibmcloud is instance-initialization-values INSTANCE [--private-key (KEY | @KEY_FILE)] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-initialization-values}

- **INSTANCE**: ID of the instance.
- **--private-key**: **key**|**@key-file**. The private key in PEM format to decrypt Windows administrator default password.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instances
{: #instances}

List all virtual server instances.

```
ibmcloud is instances [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instances}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
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

- **INSTANCE**: ID of the instance.
- **--vnc**: Get the WebSocket URI for the VNC console, it doesn't open the VNC console.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-create
{: #instance-create}

Create a virtual server instance.

```
ibmcloud is instance-create INSTANCE_NAME VPC ZONE_NAME PROFILE_NAME SUBNET [--image-id IMAGE_ID] [--boot-volume BOOT_VOLUME_JSON | @BOOT_VOLUME_JSON_FILE] [--volume-attach VOLUME_ATTACH_JSON | @VOLUME_ATTACH_JSON_FILE] [--key-ids IDS] [--dedicated-host HOST_ID | --dedicated-host-group HOST_GROUP_ID | --placement-group PLACEMENT_GROUP_ID] [--user-data DATA] [([--security-group-ids SECURITY_GROUP_IDS] [--ipv4 IPV4_ADDRESS] [--allow-ip-spoofing false | true]) | --primary-network-interface PRIMARY_NETWORK_INTERFACE_JSON | @PRIMARY_NETWORK_INTERFACE_JSON_FILE] [--network-interface NETWORK_INTERFACE_JSON | @NETWORK_INTERFACE_JSON_FILE] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-i, --interactive] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-create}

- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8`
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"name":"my-volume-name", "capacity":10, "profile": {"name": "general-purpose"}}}]'`
Create instance with volume attachment.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"id":"67531475-bd8a-478e-bcfe-2e53365cd0aa"}}]'`
Create instance with existing volume in volume attachment.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --key-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
Create instance with multiple SSH keys.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-name", "volume": {"profile": {"name": "general-purpose"},"encryption_key": {"crn": "crn:v1:bluemix:public:kms:us-south:adffc98a0f1f0f95f6613b3b752286b87:e4a29d1a-2ef0-42a6-8fd2-350deb1c647e:key:5437653b-c4b1-447f-9646-b2a2a4cd6179"}}}'`
Create instance with encrypted boot volume.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --network-interface '[{"name": "secondary-nic", "allow_ip_spoofing": true, "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}]'`
Create instance that is attached to secondary network interface.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "primary_ipv4_address": "10.240.129.10", "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}'`
Create instance with primary network interface configuration in JSON.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --security-group-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4 10.240.129.10 --allow-ip-spoofing true`
Create instance with primary network interface configuration that includes security groups, primary IPv4 address, source IP spoofing setting.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host c019b1f7-c4d6-430c-aaa4-e0cc25d47277`
Create instance to be placed in the wanted dedicated host.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host-group a4738ceb-5e59-4601-849a-61d7895740ee`
Create instance to be placed in the wanted dedicated host group.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --placement-group 1d2afa0f-b9f2-4d85-ae35-a08885269644`
Create instance to be placed in the wanted placement group.
- `ibmcloud is instance-create --interactive`
Create instance interactively.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-attachment-name", "volume": {"name": "boot-vol-name", "profile": {"name": "general-purpose"}, "source_snapshot": {"id": "150847e3-ef0d-4927-9341-6d0a7bae424f"}}}'`
Create instance with boot volume attachment from volume snapshot.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"name":"my-volume-name", "capacity":10, "profile": {"name": "general-purpose"}, "source_snapshot": {"id": "150847e3-ef0d-4927-9341-6d0a7bae424f"}}}]'`
Create instance with volume attachment from volume snapshot.

#### Command options
{: #command-options-instance-create}

- **INSTANCE_NAME**: Name of the instance.
- **VPC**: ID of the VPC.
- **ZONE_NAME**: Name of the zone.
- **PROFILE_NAME**: Name of the profile.
- **SUBNET**: ID of the subnet.
- **--image-id**: ID of the image.
- **--boot-volume**: BOOT_VOLUME_JSON|@BOOT_VOLUME_JSON_FILE, boot volume attachment in JSON or JSON file. For the data schema, check **boot_volume_attachment** property in the API docs **https://cloud.ibm.com/apidocs/vpc#create-instance**.
- **--volume-attach**: VOLUME_ATTACH_JSON|@VOLUME_ATTACH_JSON_FILE, volume attachment in JSON or JSON file, list of volumes. For the data schema, check **volume_attachments** property in the API docs **https://cloud.ibm.com/apidocs/vpc#create-instance**.
- **--key-ids**: Comma-separated IDs of SSH keys.
- **--dedicated-host**: The host destination where the instance will be placed.
- **--dedicated-host-group**: The host group destination where the instance will be placed.
- **--placement-group**: [Beta] The placement group restrictions for the virtual server instance.
- **--user-data**: data|@data-file. User data to transfer to the virtual server instance.
- **--security-group-ids**: Comma-separated security group IDs for primary network interface.
- **--ipv4**: Primary IPv4 address.
- **--allow-ip-spoofing**: Disables the source and destination checks on this interface. If **false**, source IP spoofing is not allowed on this interface. One of: **false**, **true**.
- **--primary-network-interface**: PRIMARY_NETWORK_INTERFACE_JSON|@PRIMARY_NETWORK_INTERFACE_JSON_FILE, primary network interface in JSON or JSON file. For the data schema, check **primary_network_interface** property in the API docs **https://cloud.ibm.com/apidocs/vpc#create-instance**.
- **--network-interface**: NETWORK_INTERFACE_JSON|@NETWORK_INTERFACE_JSON_FILE, network interface attachment in JSON or JSON file. For the data schema, check **network_interfaces** property in the API docs **https://cloud.ibm.com/apidocs/vpc#create-instance**.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--interactive, -i**: Supply the parameters under interactive mode. This option is mutually exclusive with all other arguments and options.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-create-from-template
{: #instance-create-from-template}

Create a virtual server instance from instance template.

```
ibmcloud is instance-create-from-template --template-id TEMPLATE_ID [--name Name] [--profile PROFILE] [--zone ZONE] [--vpc-id VPC_ID] [--image-id IMAGE_ID] [--boot-volume BOOT_VOLUME_JSON | @BOOT_VOLUME_JSON_FILE] [--volume-attach VOLUME_ATTACH_JSON | @VOLUME_ATTACH_JSON_FILE] [--key-ids IDS] [--dedicated-host HOST_ID | --dedicated-host-group HOST_GROUP_ID | --placement-group PLACEMENT_GROUP_ID] [--user-data DATA] [(--subnet-id SUBNET_ID [--ipv4 IPV4_ADDRESS] [--security-group-ids SECURITY_GROUP_IDS] [--allow-ip-spoofing false | true]) | --primary-network-interface PRIMARY_NETWORK_INTERFACE_JSON | @PRIMARY_NETWORK_INTERFACE_JSON_FILE] [--network-interface NETWORK_INTERFACE_JSON | @NETWORK_INTERFACE_JSON_FILE] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-create-from-template}

- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d`
- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --resource-group-id 7494aacb866142fba11a88d75cb37bd8 --output JSON`
- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --boot-volume '{"delete_volume_on_instance_delete": false, "name": "my-volume-attachment", "volume": {"name": "myvol2", "profile": {"name": "general-purpose"}}}'`
Create instance from instance template with the boot volume configuration
- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --vpc-id r006-beca4c2f-625f-45de-bd95-c8eb12f6842a --zone us-south-1 --subnet-id 0717-fe2e13d0-9ba8-43bd-ab6b-a1fad51557ac --ipv4 10.240.129.10 --security-group-ids r006-19c2ce0d-d35d-47bc-8147-120edddd3de5 --allow-ip-spoofing true`
Create instance from instance template with the primary network interface configuration
- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --vpc-id r006-beca4c2f-625f-45de-bd95-c8eb12f6842a --zone us-south-1 --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"id":"0717-fe2e13d0-9ba8-43bd-ab6b-a1fad51557ac"}, "primary_ipv4_address": "10.240.129.10", "security_groups": [{"id": "r006-19c2ce0d-d35d-47bc-8147-120edddd3de5"}]}'`
Create instance from instance template with the primary network interface configuration in json format
- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --network-interface '[{"name": "secondary-nic", "allow_ip_spoofing": true, "subnet": {"id":"0737-f6b5a638-1fda-476b-9e2f-7a550fbb62b8"}, "primary_ipv4_address": "10.240.129.10", "security_groups": [{"id": "r006-caba3deb-136b-42c8-831a-1dbcc0f1912e"}]}, {"name": "third-nic", "allow_ip_spoofing": true, "subnet": {"id":"0737-6b939577-4839-47b0-b42f-a4b29a94c7d9"}, "primary_ipv4_address": "10.240.129.100", "security_groups": [{"id": "r006-caba3deb-136b-42c8-831a-1dbcc0f1912e"}]}]'`
Create instance from instance template with the second network interfaces configuration
- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --volume-attach '[{"delete_volume_on_instance_delete": false, "name": "my-volume-attachment1", "volume": {"name": "myvol2", "capacity": 200, "profile": {"name": "general-purpose"}}}, {"delete_volume_on_instance_delete": true, "name": "my-volume-attachment2", "volume": {"name": "myvol3", "capacity": 300, "iops": 1000, "profile": {"name": "custom"}}}]'`
Create instance from instance template with the data volumes configuration
- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --image-id r006-ed3f775f-ad7e-4e37-ae62-7199b4988b00 --profile cx2-2x4 --key-ids r006-02a07b78-6e5f-40a2-86a2-99e01916128c,r006-29e19fb1-e2b9-49d0-ab6e-9702e99f5021 --user-data @/tmp/userdata.sh`
Create instance from instance template with image/profile/key/user data configuration
- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --dedicated-host 0737-4ab6b37d-4695-4efb-9439-0528b5550dfe --profile mx2-2x16`
Create instance from instance template with the wanted dedicated host
- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --dedicated-host-group 0737-7290ea56-7543-4590-8558-ca8cd51b12c4 --profile mx2-2x16`
Create instance from instance template with the wanted dedicated host group

#### Command options
{: #command-options-instance-create-from-template}

- **--template-id**: ID of the instance template.
- **--name**: Name of the instance.
- **--profile**: Name of the instance profile.
- **--zone**: Name of the zone.
- **--vpc-id**: ID of the VPC.
- **--image-id**: ID of the image.
- **--boot-volume**: BOOT_VOLUME_JSON|@BOOT_VOLUME_JSON_FILE, boot volume attachment in JSON or JSON file. For the data schema, check **boot_volume_attachment** property in the API docs **https://cloud.ibm.com/apidocs/vpc#create-instance**.
- **--volume-attach**: VOLUME_ATTACH_JSON|@VOLUME_ATTACH_JSON_FILE, volume attachment in JSON or JSON file, list of volumes. For the data schema, check **volume_attachments** property in the API docs **https://cloud.ibm.com/apidocs/vpc#create-instance**.
- **--key-ids**: Comma-separated IDs of SSH keys.
- **--dedicated-host**: The host destination where the instance will be placed.
- **--dedicated-host-group**: The host group destination where the instance will be placed.
- **--placement-group**: [Beta] The placement group restrictions for the virtual server instance.
- **--user-data**: data|@data-file. User data to transfer to the virtual server instance.
- **--subnet-id**: ID of the subnet.
- **--ipv4**: Primary IPv4 address.
- **--security-group-ids**: Comma-separated security group IDs for primary network interface.
- **--allow-ip-spoofing**: Disables the source and destination checks on this interface. If **false**, source IP spoofing is not allowed on this interface. One of: **false**, **true**.
- **--primary-network-interface**: PRIMARY_NETWORK_INTERFACE_JSON|@PRIMARY_NETWORK_INTERFACE_JSON_FILE, primary network interface in JSON or JSON file. For the data schema, check **primary_network_interface** property in the API docs **https://cloud.ibm.com/apidocs/vpc#create-instance**.
- **--network-interface**: NETWORK_INTERFACE_JSON|@NETWORK_INTERFACE_JSON_FILE, network interface attachment in JSON or JSON file. For the data schema, check **network_interfaces** property in the API docs **https://cloud.ibm.com/apidocs/vpc#create-instance**.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-delete
{: #instance-delete}

Delete virtual server instances.

```
ibmcloud is instance-delete (INSTANCE1 INSTANCE2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-delete}

- **INSTANCE1**: ID of the instance.
- **INSTANCE2**: ID of the instance.
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

- **INSTANCE**: ID of the instance.
- **INSTANCE_DISK**: ID of the instance disk.
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

- **INSTANCE**: ID of the instance.
- **INSTANCE_DISK**: ID of the instance disk.
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

- **INSTANCE**: ID of the instance.
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

- **INSTANCE**: ID of the instance.
- **NIC**: ID of the network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-interface-create
{: #instance-network-interface-create}

Create a network interface for a virtual server instance.

```
ibmcloud is instance-network-interface-create NIC_NAME INSTANCE SUBNET [--ipv4 IPV4_ADDRESS] [(--security-group-id SECURITY_GROUP_ID1 --security-group-id SECURITY_GROUP_ID2 ...)] [--allow-ip-spoofing false | true] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-network-interface-create}

- `ibmcloud is instance-network-interface-create my-vnic 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is instance-network-interface-create my-vnic 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4 10.2.3.4`
- `ibmcloud is instance-network-interface-create my-vnic 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4 10.2.3.4 --security-group-id 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --security-group-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8`

#### Command options
{: #command-options-instance-network-interface-create}

- **NIC_NAME**: Name of the network interface.
- **INSTANCE**: ID of the instance.
- **SUBNET**: ID of the subnet.
- **--ipv4**: Primary IPv4 address.
- **--security-group-id**: ID of the security group.
- **--allow-ip-spoofing**: Disables the source and destination checks on this interface. If **false**, source IP spoofing is not allowed on this interface. One of: **false**, **true**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-network-interface-delete
{: #instance-network-interface-delete}

Remove network interfaces from a virtual server instance.

```
ibmcloud is instance-network-interface-delete INSTANCE (NIC1 NIC2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-network-interface-delete}

- **INSTANCE**: ID of the instance.
- **NIC1**: ID of the network interface.
- **NIC2**: ID of the network interface.
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

- **INSTANCE**: ID of the instance.
- **NIC**: ID of the network interface.
- **FLOATING_IP**: ID of the floating IP.
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

#### Command options
{: #command-options-instance-network-interface-floating-ip-add}

- **INSTANCE**: ID of the instance.
- **NIC**: ID of the network interface.
- **FLOATING_IP**: ID of the floating IP.
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

- **INSTANCE**: ID of the instance.
- **NIC**: ID of the network interface.
- **FLOATING_IP**: ID of the floating IP.
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

- **INSTANCE**: ID of the instance.
- **NIC**: ID of the network interface.
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

- **INSTANCE**: ID of the instance.
- **NIC**: ID of the network interface.
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

- **INSTANCE**: ID of the instance.
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

- **INSTANCE**: ID of the instance.
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

- **INSTANCE**: ID of the instance.
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

- **INSTANCE**: ID of the instance.
- **--no-wait**: Execute the action immediately and drop all queued actions.
- **--force, -f**: Force the operation without confirmation.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-update
{: #instance-update}

Update a virtual server instance.

```
ibmcloud is instance-update INSTANCE [--name NEW_NAME] [--profile PROFILE] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-update}

- `ibmcloud is instance-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-instance`
- `ibmcloud is instance-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-instance --output JSON`

#### Command options
{: #command-options-instance-update}

- **INSTANCE**: ID of the instance.
- **--name**: New name of the virtual server instance.
- **--profile**: The profile to use for this virtual server instance. To change the profile, the instance status must be `stopping` or `stopped`. In addition, the requested profile must: 1. Match the current profile's instance disk support. (**Note:** If the current profile supports instance storage disks, the requested profile can have a different instance storage disk configuration.) 2. Be compatible with any placement target constraints. For example, if the instance is placed on a dedicated host, the requested profile `family` must be the same as the dedicated host `family`.
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

- **INSTANCE**: ID of the instance.
- **VOLUME_ATTACHMENT**: ID of the volume attachment.
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

- **INSTANCE**: ID of the instance.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-volume-attachment-add
{: #instance-volume-attachment-add}

Create a volume attachment, connecting a volume to an instance.

```
ibmcloud is instance-volume-attachment-add NAME INSTANCE (VOLUME | --profile PROFILE --new-volume-name NEW_VOLUME_NAME --iops IOPS --encryption-key ENCRYPTION_KEY --capacity CAPACITY --source-snapshot SOURCE_SNAPSHOT) [--auto-delete false | true] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-volume-attachment-add}

- `ibmcloud is instance-volume-attachment-add data-vol-name 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 1a6b7274-678d-4dfb-8981-c71dd9d4daa5`
- `ibmcloud is instance-volume-attachment-add data-vol-name 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 --auto-delete true`
- `ibmcloud is instance-volume-attachment-add data-vol-name 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 --auto-delete true --output JSON`
- `ibmcloud is instance-volume-attachment-add data-vol-name 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --profile general-purpose --source-snapshot eaf9d6ca-35bf-4ac7-bc45-d0f2507f2830 --auto-delete true --output JSON`

#### Command options
{: #command-options-instance-volume-attachment-add}

- **NAME**: Name of the volume attachment.
- **INSTANCE**: ID of the instance.
- **VOLUME**: ID of the volume.
- **--new-volume-name**: The name of new volume.
- **--profile**: Name of the profile.
- **--iops**: Input/Output Operations Per Second for the volume, it is only applicable for custom profile volumes. For the IOPS range, refer to https://cloud.ibm.com/docs/vpc?topic=vpc-block-storage-profiles#custom.
- **--encryption-key**: The CRN of the Key Management Service root key.
- **--capacity**: The capacity of the volume in gigabytes. Range 10-16000 for custom and general-purpose profile volumes, 10-9600 for 5iops-tier profile volumes, 10-4800 for 10iops-tier profile volumes.
- **--source-snapshot**: The ID of the snapshot to clone volume.
- **--auto-delete**: The attached volume is deleted when the instance is deleted. One of: **false**, **true**. (default: **false**).
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-volume-attachment-detach
{: #instance-volume-attachment-detach}

Delete volume attachments, detaching volume from an instance.

```
ibmcloud is instance-volume-attachment-detach INSTANCE (VOLUME_ATTACHMENT1 VOLUME_ATTACHMENT2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-volume-attachment-detach}

- **INSTANCE**: ID of the instance.
- **VOLUME_ATTACHMENT1**: ID of the volume attachment.
- **VOLUME_ATTACHMENT2**: ID of the volume attachment.
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

#### Command options
{: #command-options-instance-volume-attachment-update}

- **INSTANCE**: ID of the instance.
- **VOLUME_ATTACHMENT**: ID of the volume attachment.
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

- **KEY**: ID of the key.
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

- **KEY_NAME**: Name of the key.
- **KEY**: **key**|**@key-file**. The public SSH key to import into the system.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is key-delete
{: #key-delete}

Delete keys.

```
ibmcloud is key-delete (KEY1 KEY2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-key-delete}

- **KEY1**: ID of the key.
- **KEY2**: ID of the key.
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

- **KEY**: ID of the key.
- **--name**: New name for the key.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is keys
{: #keys}

List all keys.

```
ibmcloud is keys [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-keys}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
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

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
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

- **HOST_GROUP**: ID of the host group.
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
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
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

- **HOST_GROUP**: ID of the host group.
- **--name**: New name of the host group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host-group-delete
{: #dedicated-host-group-delete}

Delete host groups.

```
ibmcloud is dedicated-host-group-delete (HOST_GROUP1 HOST_GROUP2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-dedicated-host-group-delete}

- **HOST_GROUP1**: ID of the host group.
- **HOST_GROUP2**: ID of the host group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-hosts
{: #dedicated-hosts}

List all hosts.

```
ibmcloud is dedicated-hosts [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-dedicated-hosts}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
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

- **HOST**: ID of the host.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host-create
{: #dedicated-host-create}

Create a host.

```
ibmcloud is dedicated-host-create --profile PROFILE --host-group-id HOST_GROUP_ID [--enabled true | false] [--name NAME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-dedicated-host-create}

- `ibmcloud is dedicated-host-create --profile dh2-56x344 --host-group-id 74213016-f179-4055-b161-46fd42a9d98a --name my-host`
- `ibmcloud is dedicated-host-create --profile dh2-56x344 --host-group-id 74213016-f179-4055-b161-46fd42a9d98a --name my-host --enabled false`
- `ibmcloud is dedicated-host-create --profile dh2-56x344 --host-group-id 74213016-f179-4055-b161-46fd42a9d98a --name my-host --output JSON`

#### Command options
{: #command-options-dedicated-host-create}

- **--profile**: Name of the host profile.
- **--host-group-id**: ID of the host group.
- **--enabled**: Enable or disable the instance placement in the host. One of: **true**, **false**. (default: **true**).
- **--name**: New name for the host.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
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

- **HOST**: ID of the host.
- **--name**: New name of the host.
- **--enabled**: Enable or disable the instance placement in the host. One of: **true**, **false**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is dedicated-host-delete
{: #dedicated-host-delete}

Delete hosts.

```
ibmcloud is dedicated-host-delete (HOST1 HOST2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-dedicated-host-delete}

- **HOST1**: ID of the host.
- **HOST2**: ID of the host.
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

- **HOST**: ID of the host.
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

- **HOST**: ID of the host.
- **DISK**: ID of the dedicated host disk.
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

- **HOST**: ID of the host.
- **DISK**: ID of the dedicated host disk.
- **--name**: New name of the disk.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Bare metal servers (Beta)
{: #bare-metal-servers}

### ibmcloud is bare-metal-server
{: #bare-metal-server}

[Beta] View details of a bare metal server.

```
ibmcloud is bare-metal-server SERVER [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server}

- **SERVER**: ID of the server.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-console
{: #bare-metal-server-console}

[Beta] Open an interactive console to the bare metal server. This command opens an interactive serial console by default.

```
ibmcloud is bare-metal-server-console SERVER [--vnc] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-console}

- **SERVER**: ID of the server.
- **--vnc**: Get the WebSocket URI for the VNC console, it doesn't open the VNC console.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-create
{: #bare-metal-server-create}

[Beta] Create a bare metal server.

```
ibmcloud is bare-metal-server-create --zone ZONE_NAME --profile PROFILE --image IMAGE --keys KEYS (--pnic-subnet PRIMARY_NIC_SUBNET [--pnic-name PRIMARY_NIC_NAME] [--pnic-ip PRIMARY_NIC_IPV4_ADDRESS] [--pnic-sgs PNIC_SGS] [--pnic-allowed-vlans PNIC_ALLOWED_VLANS] [--pnic-ein true | false] [--pnic-ais false | true]) [--name NAME] [--user-data DATA] [--network-interfaces NETWORK_INTERFACES_JSON | @NETWORK_INTERFACES_JSON_FILE] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [-i, --interactive] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-bare-metal-server-create}

- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f`
- `ibmcloud is bare-metal-server-create --name my-server-name2 --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --pnic-name eth0 --pnic-ip 46.9.49.11 --pnic-sgs c791f26f-4cf1-4bbf-be0e-72d7cb87133e,fefc8362-93c2-4f3d-90d4-82c56cce787e --pnic-allowed-vlans 1,2,3,4 --pnic-ein true --pnic-ais true`
Create a bare metal server with specified primary network interface configuration.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --resource-group-name Finance --output JSON`
Create a bare metal server in the `Finance` resource group.
- `ibmcloud is bare-metal-server-create --name my-server-name --zone us-east-1 --profile bmx2d-24x384 --image cfdaf1a0-5350-4350-fcbc-97173b510844 --keys 7ab1ee27-564c-4730-a1ad-9b9466589250,9727e31a-74d4-45cd-8f39-1ef7484b5f3e --pnic-subnet bdea9c01-ada2-46ba-a314-4b3240477a5f  --network-interfaces '[{"name": "eth2", "allow_ip_spoofing": true, "enable_infrastructure_nat": true, "interface_type": "pci", "allowed_vlans": [1, 2, 3, 4], "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "primary_ipv4_address": "10.240.129.11", "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}, {"name": "eth3", "allow_ip_spoofing": true, "enable_infrastructure_nat": true, "interface_type": "vlan", "vlan": 4, "allow_interface_to_float": true, "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "primary_ipv4_address": "10.240.129.12", "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}]'`
Create a bare metal server with a PCI secondary network interface and a VLAN secondary network interface. Configurations of the two secondary interfaces are specified in JSON format. See help text for '--network-interfaces' option.

#### Command options
{: #command-options-bare-metal-server-create}

- **--name**: Name of the server.
- **--zone**: Name of the zone.
- **--profile**: Name of the bare metal server profile.
- **--image**: ID of the image.
- **--keys**: Comma-separated IDs of ssh keys.
- **--user-data**: data|@data-file. User data to transfer to the bare metal server.
- **--pnic-name**: Name of the primary network interface.
- **--pnic-subnet**: Subnet ID for the primary network interface.
- **--pnic-ip**: Primary IPv4 address for the primary network interface.
- **--pnic-sgs**: Comma-separated security group IDs for primary network interface.
- **--pnic-allowed-vlans**: Comma-separated VLAN IDs. Indicates which VLAN IDs (for VLAN interfaces only) can use the primary network interface.
- **--pnic-ein**: Enable infrastructure NAT. If **true**, the VPC infrastructure performs any needed NAT operations. If **false**, the packet is passed unmodified to or from the network interface, allowing the VM associated with the floating IP to perform any needed NAT operations. One of: **true**, **false**. (default: **true**).
- **--pnic-ais**: Indicates whether source IP spoofing is allowed on the network interface. If **true**, source IP spoofing is allowed on this interface. If **false**, source IP spoofing is prevented on this interface. One of: **false**, **true**. (default: **false**).
- **--network-interfaces**: NETWORK_INTERFACES_JSON|@NETWORK_INTERFACES_JSON_FILE. Network interface configuration in JSON or JSON file. For the data schema, check **network_interfaces** property in the API docs **https://cloud.ibm.com/apidocs/vpc-beta#create-bare-metal-server**.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--interactive, -i**: Supply the parameters under interactive mode. This option is mutually exclusive with all other arguments and options.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-delete
{: #bare-metal-server-delete}

[Beta] Delete bare metal servers.

```
ibmcloud is bare-metal-server-delete (SERVER1 SERVER2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-delete}

- **SERVER1**: ID of the server.
- **SERVER2**: ID of the server.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-disk
{: #bare-metal-server-disk}

[Beta] View details of a bare metal server disk.

```
ibmcloud is bare-metal-server-disk SERVER SERVER_DISK [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-disk}

- **SERVER**: ID of the server.
- **SERVER_DISK**: ID of the server disk.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-disk-update
{: #bare-metal-server-disk-update}

[Beta] Update a bare metal server disk.

```
ibmcloud is bare-metal-server-disk-update SERVER SERVER_DISK --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-disk-update}

- **SERVER**: ID of the server.
- **SERVER_DISK**: ID of the server disk.
- **--name**: New name of local disk.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-disks
{: #bare-metal-server-disks}

[Beta] List all disks of a bare metal server.

```
ibmcloud is bare-metal-server-disks SERVER [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-disks}

- **SERVER**: ID of the server.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-initialization-values
{: #bare-metal-server-initialization-values}

[Beta] Retrieve configuration variables that are used to initialize the bare metal server.

```
ibmcloud is bare-metal-server-initialization-values SERVER [--private-key (KEY | @KEY_FILE)] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-initialization-values}

- **SERVER**: ID of the server.
- **--private-key**: **key**|**@key-file**. The private key in PEM format to decrypt password.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface
{: #bare-metal-server-network-interface}

[Beta] View details of a network interface of a bare metal server.

```
ibmcloud is bare-metal-server-network-interface SERVER NIC [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-network-interface}

- **SERVER**: ID of the server.
- **NIC**: ID of the network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface-create
{: #bare-metal-server-network-interface-create}

[Beta] Create a network interface for a bare metal server.

```
ibmcloud is bare-metal-server-network-interface-create SERVER --subnet SUBNET [--name NAME] [--interface-type pci | vlan] [--ip IPV4_ADDRESS] [--security-groups SECURITY_GROUPS] [--allowed-vlans ALLOWED_VLANS | --vlan VLAN --allow-interface-to-float false | true] [--allow-ip-spoofing false | true] [--enable-infrastructure-nat true | false] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-bare-metal-server-network-interface-create}

- `ibmcloud is bare-metal-server-network-interface-create 7d317c32-71f8-4060-9bdc-6c971b0317d4 --subnet dcaec790-f0b0-48e6-b4cb-03dd82b745c0`
Create a PCI network interface.
- `ibmcloud is bare-metal-server-network-interface-create 7d317c32-71f8-4060-9bdc-6c971b0317d4 --subnet dcaec790-f0b0-48e6-b4cb-03dd82b745c0 --interface-type pci --name eth1 --ip 10.0.0.11 --security-groups 43846d71-0f04-473f-9de5-5a2d33200a4b,27c8ca96-17f3-4943-898d-ad1a1f5aec26 --allowed-vlans 1,2,3,4 -allow-ip-spoofing true --enable-infrastructure-nat true`
Create a PCI network interface with specified configuration.
- `ibmcloud is bare-metal-server-network-interface-create 7d317c32-71f8-4060-9bdc-6c971b0317d4 --subnet dcaec790-f0b0-48e6-b4cb-03dd82b745c0 --interface-type vlan --name eth2 --ip 10.0.0.12 --security-groups 43846d71-0f04-473f-9de5-5a2d33200a4b,27c8ca96-17f3-4943-898d-ad1a1f5aec26 --vlan 1 -allow-interface-to-float true -allow-ip-spoofing true --enable-infrastructure-nat true`
Create a VLAN network interface with specified configuration.
- `ibmcloud is bare-metal-server-network-interface-create 7d317c32-71f8-4060-9bdc-6c971b0317d4 --subnet dcaec790-f0b0-48e6-b4cb-03dd82b745c0 --output JSON`
Create a PCI network interface and specify JSON as the output format.

#### Command options
{: #command-options-bare-metal-server-network-interface-create}

- **SERVER**: ID of the server.
- **--name**: Name of the network interface.
- **--interface-type**: Type of the network interface. One of: **pci**, **vlan**. (default: **pci**).
- **--subnet**: Subnet ID for the network interface.
- **--ip**: Primary IPv4 address for the network interface.
- **--security-groups**: Comma-separated security group IDs for the network interface.
- **--allowed-vlans**: Comma-separated VLAN IDs. Indicates which VLAN IDs (for VLAN interfaces only) can use this PCI interface.
- **--vlan**: Indicates the 802.1Q VLAN ID tag that must be used for all traffic on this interface.
- **--allow-interface-to-float**: Indicates if the interface can float to any other server within the same **resource_group**. The interface floats automatically if the network detects a GARP or RARP on another bare metal server in the resource group. Applies only to VLAN interfaces. One of: **false**, **true**. (default: **false**).
- **--allow-ip-spoofing**: Indicates whether source IP spoofing is allowed on the network interface. If **true**, source IP spoofing is allowed on this interface. If **false**, source IP spoofing is prevented on this interface. One of: **false**, **true**. (default: **false**).
- **--enable-infrastructure-nat**: If true, the VPC infrastructure performs any needed NAT operations. If false, the packet is passed unmodified to or from the network interface, allowing the workload to perform any needed NAT operations. One of: **true**, **false**. (default: **true**).
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface-delete
{: #bare-metal-server-network-interface-delete}

[Beta] Remove network interfaces from a bare metal server.

```
ibmcloud is bare-metal-server-network-interface-delete SERVER (NIC1 NIC2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-network-interface-delete}

- **SERVER**: ID of the server.
- **NIC1**: ID of the network interface.
- **NIC2**: ID of the network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface-floating-ip
{: #bare-metal-server-network-interface-floating-ip}

[Beta] View details of a floating IP that is associated with a network interface.

```
ibmcloud is bare-metal-server-network-interface-floating-ip SERVER NIC FLOATING_IP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-network-interface-floating-ip}

- **SERVER**: ID of the server.
- **NIC**: ID of the network interface.
- **FLOATING_IP**: ID of the floating IP.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface-floating-ip-add
{: #bare-metal-server-network-interface-floating-ip-add}

[Beta] Associate a floating IP with a network interface.

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

- **SERVER**: ID of the server.
- **NIC**: ID of the network interface.
- **FLOATING_IP**: ID of the floating IP.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface-floating-ip-remove
{: #bare-metal-server-network-interface-floating-ip-remove}

[Beta] Disassociate a floating IP from a network interface.

```
ibmcloud is bare-metal-server-network-interface-floating-ip-remove SERVER NIC FLOATING_IP [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-network-interface-floating-ip-remove}

- **SERVER**: ID of the server.
- **NIC**: ID of the network interface.
- **FLOATING_IP**: ID of the floating IP.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface-floating-ips
{: #bare-metal-server-network-interface-floating-ips}

[Beta] List all floating IPs that are associated with a network interface.

```
ibmcloud is bare-metal-server-network-interface-floating-ips SERVER NIC [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-network-interface-floating-ips}

- **SERVER**: ID of the server.
- **NIC**: ID of the network interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interface-update
{: #bare-metal-server-network-interface-update}

[Beta] Update a network interface of a bare metal server.

```
ibmcloud is bare-metal-server-network-interface-update SERVER NIC --name NEW_NAME [--allow-ip-spoofing false | true] [--enable-infrastructure-nat true | false] [--allowed-vlans ALLOWED_VLANS] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-bare-metal-server-network-interface-update}

- `ic is bm-nicu 7d317c32-71f8-4060-9bdc-6c971b0317d4 784e2e4c-0540-4e1a-aba7-a51f9b35ba52 --name eth0 --allow-ip-spoofing true --enable-infrastructure-nat true -allowed-vlans 1,3,5`
- `ic is bm-nicu 7d317c32-71f8-4060-9bdc-6c971b0317d4 784e2e4c-0540-4e1a-aba7-a51f9b35ba52 --name ethvlan1 --allow-ip-spoofing true --enable-infrastructure-nat true --output JSON`

#### Command options
{: #command-options-bare-metal-server-network-interface-update}

- **SERVER**: ID of the server.
- **NIC**: ID of the network interface.
- **--name**: New name of the network interface.
- **--allow-ip-spoofing**: Indicates whether source IP spoofing is allowed on the network interface. If **true**, source IP spoofing is allowed on this interface. If **false**, source IP spoofing is prevented on this interface. One of: **false**, **true**. (default: **false**).
- **--enable-infrastructure-nat**: If true, the VPC infrastructure performs any needed NAT operations. If false, the packet is passed unmodified to or from the network interface, allowing the workload to perform any needed NAT operations. One of: **true**, **false**. (default: **true**).
- **--allowed-vlans**: Comma-separated VLAN IDs. Indicates which VLAN IDs (for VLAN interfaces only) can use this PCI interface.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-network-interfaces
{: #bare-metal-server-network-interfaces}

[Beta] List all network interfaces of a bare metal server.

```
ibmcloud is bare-metal-server-network-interfaces SERVER [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-network-interfaces}

- **SERVER**: ID of the server.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-profile
{: #bare-metal-server-profile}

[Beta] View details of a bare metal server profile.

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

[Beta] List all bare metal server profiles in the region.

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

[Beta] Restart a bare metal server.

```
ibmcloud is bare-metal-server-restart SERVER [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-restart}

- **SERVER**: ID of the server.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-start
{: #bare-metal-server-start}

[Beta] Start a bare metal server.

```
ibmcloud is bare-metal-server-start SERVER [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-start}

- **SERVER**: ID of the server.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-stop
{: #bare-metal-server-stop}

[Beta] Stop a bare metal server.

```
ibmcloud is bare-metal-server-stop SERVER [--type soft | hard] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-server-stop}

- **SERVER**: ID of the server.
- **--type**: Indicates the type of the stop operation. **soft**: Signal the running operating system to quiesce and shut down cleanly. **hard**: Immediately stop the server. One of: **soft**, **hard**. (default: **soft**).
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-server-update
{: #bare-metal-server-update}

[Beta] Update a bare metal server.

```
ibmcloud is bare-metal-server-update SERVER --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-bare-metal-server-update}

- `ibmcloud is bare-metal-server-update 7d317c32-71f8-4060-9bdc-6c971b0317d4 --name my-server --output JSON`

#### Command options
{: #command-options-bare-metal-server-update}

- **SERVER**: ID of the server.
- **--name**: New name of the bare metal server.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is bare-metal-servers
{: #bare-metal-servers}

[Beta] List all bare metal servers.

```
ibmcloud is bare-metal-servers [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-bare-metal-servers}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Placement group (Beta)
{: #placement-group}

### ibmcloud is placement-group
{: #placement-group}

[Beta] View details of a placement group.

```
ibmcloud is placement-group PLACEMENT_GROUP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-placement-group}

- **PLACEMENT_GROUP**: ID of the placement group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is placement-group-create
{: #placement-group-create}

[Beta] Create a placement group.

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
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is placement-group-delete
{: #placement-group-delete}

[Beta] Delete placement groups.

```
ibmcloud is placement-group-delete (PLACEMENT_GROUP1 PLACEMENT_GROUP2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-placement-group-delete}

- **PLACEMENT_GROUP1**: ID of the placement group.
- **PLACEMENT_GROUP2**: ID of the placement group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is placement-group-update
{: #placement-group-update}

[Beta] Update a placement group.

```
ibmcloud is placement-group-update PLACEMENT_GROUP --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-placement-group-update}

- `ibmcloud is placement-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name`
- `ibmcloud is placement-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name --output JSON`

#### Command options
{: #command-options-placement-group-update}

- **PLACEMENT_GROUP**: ID of the placement group.
- **--name**: New name of the placement group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is placement-groups
{: #placement-groups}

[Beta] List all placement groups.

```
ibmcloud is placement-groups [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME | --all-resource-groups] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-placement-groups}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
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

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-template
{: #instance-template}

View details of an instance template.

```
ibmcloud is instance-template TEMPLATE_ID [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-template}

- **TEMPLATE_ID**: ID of the template.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-template-create
{: #instance-template-create}

Create an instance template.

```
ibmcloud is instance-template-create INSTANCE_TEMPLATE_NAME VPC ZONE_NAME PROFILE_NAME SUBNET --image-id IMAGE_ID [--boot-volume BOOT_VOLUME_JSON | @BOOT_VOLUME_JSON_FILE] [--volume-attach VOLUME_ATTACH_JSON | @VOLUME_ATTACH_JSON_FILE] [--key-ids IDS] [--dedicated-host HOST_ID | --dedicated-host-group HOST_GROUP_ID | --placement-group PLACEMENT_GROUP_ID] [--user-data DATA] [([--security-group-ids SECURITY_GROUP_IDS] [--ipv4 IPV4_ADDRESS] [--allow-ip-spoofing false | true]) | --primary-network-interface PRIMARY_NETWORK_INTERFACE_JSON | @PRIMARY_NETWORK_INTERFACE_JSON_FILE] [--network-interface NETWORK_INTERFACE_JSON | @NETWORK_INTERFACE_JSON_FILE] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-i, --interactive] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-template-create}

- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8`
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"name":"my-volume-name", "capacity":10, "profile": {"name": "general-purpose"}}}]'`
Create instance template with volume attachment.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"id":"67531475-bd8a-478e-bcfe-2e53365cd0aa"}}]'`
Create instance template with existing volume in volume attachment.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --key-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
Create instance template with multiple SSH keys.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --boot-volume '{"name": "boot-vol-name", "volume": {"profile": {"name": "general-purpose"},"encryption_key": {"crn": "crn:v1:bluemix:public:kms:us-south:adffc98a0f1f0f95f6613b3b752286b87:e4a29d1a-2ef0-42a6-8fd2-350deb1c647e:key:5437653b-c4b1-447f-9646-b2a2a4cd6179"}}}'`
Create instance template with encrypted boot volume.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --network-interface '[{"name": "secondary-nic", "allow_ip_spoofing": true, "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}]'`
Create instance template that is attached to secondary network interface.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --primary-network-interface '{"name": "primary-nic", "allow_ip_spoofing": true, "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "primary_ipv4_address": "10.240.129.10", "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}'`
Create instance template with primary network interface configuration in JSON.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --security-group-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4 10.240.129.10 --allow-ip-spoofing true`
Create instance template with primary network interface configuration that includes security groups, primary IPv4 address, source IP spoofing setting.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host c019b1f7-c4d6-430c-aaa4-e0cc25d47277`
Create instance template to be placed in the wanted dedicated host.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --dedicated-host-group a4738ceb-5e59-4601-849a-61d7895740ee`
Create instance template to be placed in the wanted dedicated host group.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 mx2-2x16 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --placement-group 1d2afa0f-b9f2-4d85-ae35-a08885269644`
Create instance to be placed in the wanted placement group.
- `ibmcloud is instance-template-create --interactive`
Create instance template interactively.

#### Command options
{: #command-options-instance-template-create}

- **INSTANCE_TEMPLATE_NAME**: Name of the instance template.
- **VPC**: ID of the VPC.
- **ZONE_NAME**: Name of the zone.
- **PROFILE_NAME**: Name of the profile.
- **SUBNET**: ID of the subnet.
- **--image-id**: ID of the image.
- **--boot-volume**: BOOT_VOLUME_JSON|@BOOT_VOLUME_JSON_FILE, boot volume attachment in JSON or JSON file. For the data schema, check **boot_volume_attachment** property in the API docs **https://cloud.ibm.com/apidocs/vpc#create-instance**.
- **--volume-attach**: VOLUME_ATTACH_JSON|@VOLUME_ATTACH_JSON_FILE, volume attachment in JSON or JSON file, list of volumes. For the data schema, check **volume_attachments** property in the API docs **https://cloud.ibm.com/apidocs/vpc#create-instance**.
- **--key-ids**: Comma-separated IDs of SSH keys.
- **--dedicated-host**: The host destination where the instance will be placed.
- **--dedicated-host-group**: The host group destination where the instance will be placed.
- **--placement-group**: [Beta] The placement group restrictions for the virtual server instance.
- **--user-data**: data|@data-file. User data to transfer to the virtual server instance.
- **--security-group-ids**: Comma-separated security group IDs for primary network interface.
- **--ipv4**: Primary IPv4 address.
- **--allow-ip-spoofing**: Disables the source and destination checks on this interface. If **false**, source IP spoofing is not allowed on this interface. One of: **false**, **true**.
- **--primary-network-interface**: PRIMARY_NETWORK_INTERFACE_JSON|@PRIMARY_NETWORK_INTERFACE_JSON_FILE, primary network interface in JSON or JSON file. For the data schema, check **primary_network_interface** property in the API docs **https://cloud.ibm.com/apidocs/vpc#create-instance**.
- **--network-interface**: NETWORK_INTERFACE_JSON|@NETWORK_INTERFACE_JSON_FILE, network interface attachment in JSON or JSON file. For the data schema, check **network_interfaces** property in the API docs **https://cloud.ibm.com/apidocs/vpc#create-instance**.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--interactive, -i**: Supply the parameters under interactive mode. This option is mutually exclusive with all other arguments and options.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-template-create-override-source-template
{: #instance-template-create-override-source-template}

Create an instance template by overriding a source template.

```
ibmcloud is instance-template-create-override-source-template --source-template-id SOURCE_TEMPLATE_ID [--name NAME] [--profile PROFILE] [--zone ZONE] [--vpc-id VPC_ID] [--image-id IMAGE_ID] [--boot-volume BOOT_VOLUME_JSON | @BOOT_VOLUME_JSON_FILE] [--volume-attach VOLUME_ATTACH_JSON | @VOLUME_ATTACH_JSON_FILE] [--key-ids IDS] [--dedicated-host HOST_ID | --dedicated-host-group HOST_GROUP_ID | --placement-group PLACEMENT_GROUP_ID] [--user-data DATA] [(--subnet-id SUBNET_ID [--ipv4 IPV4_ADDRESS] [--security-group-ids SECURITY_GROUP_IDS] [--allow-ip-spoofing false | true]) | --primary-network-interface PRIMARY_NETWORK_INTERFACE_JSON | @PRIMARY_NETWORK_INTERFACE_JSON_FILE] [--network-interface NETWORK_INTERFACE_JSON | @NETWORK_INTERFACE_JSON_FILE] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-template-create-override-source-template}

- `ibmcloud is instance-template-create-override-source-template --source-template-id e4a29d1a-2ef0-42a6-8fd2-350deb1c647e`
Create instance template copying from a source template
- `ibmcloud is instance-template-create-override-source-template --source-template-id e4a29d1a-2ef0-42a6-8fd2-350deb1c647e --name my-template-name --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --profile bx2-2x8`
Create instance template by overriding a source template and providing overriding options

#### Command options
{: #command-options-instance-template-create-override-source-template}

- **--source-template-id**: ID of the source template.
- **--name**: Name of instance template.
- **--profile**: Name of the instance profile.
- **--zone**: Name of the zone.
- **--vpc-id**: ID of the VPC.
- **--image-id**: ID of the image.
- **--boot-volume**: BOOT_VOLUME_JSON|@BOOT_VOLUME_JSON_FILE, boot volume attachment in JSON or JSON file. For the data schema, check **boot_volume_attachment** property in the API docs **https://cloud.ibm.com/apidocs/vpc#create-instance**.
- **--volume-attach**: VOLUME_ATTACH_JSON|@VOLUME_ATTACH_JSON_FILE, volume attachment in JSON or JSON file, list of volumes. For the data schema, check **volume_attachments** property in the API docs **https://cloud.ibm.com/apidocs/vpc#create-instance**.
- **--key-ids**: Comma-separated IDs of SSH keys.
- **--dedicated-host**: The host destination where the instance will be placed.
- **--dedicated-host-group**: The host group destination where the instance will be placed.
- **--placement-group**: [Beta] The placement group restrictions for the virtual server instance.
- **--user-data**: data|@data-file. User data to transfer to the virtual server instance.
- **--subnet-id**: ID of the subnet.
- **--ipv4**: Primary IPv4 address.
- **--security-group-ids**: Comma-separated security group IDs for primary network interface.
- **--allow-ip-spoofing**: Disables the source and destination checks on this interface. If **false**, source IP spoofing is not allowed on this interface. One of: **false**, **true**.
- **--primary-network-interface**: PRIMARY_NETWORK_INTERFACE_JSON|@PRIMARY_NETWORK_INTERFACE_JSON_FILE, primary network interface in JSON or JSON file. For the data schema, check **primary_network_interface** property in the API docs **https://cloud.ibm.com/apidocs/vpc#create-instance**.
- **--network-interface**: NETWORK_INTERFACE_JSON|@NETWORK_INTERFACE_JSON_FILE, network interface attachment in JSON or JSON file. For the data schema, check **network_interfaces** property in the API docs **https://cloud.ibm.com/apidocs/vpc#create-instance**.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-template-update
{: #instance-template-update}

Update an instance template.

```
ibmcloud is instance-template-update TEMPLATE_ID --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-template-update}

- `ibmcloud is instance-template-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name-template`
- `ibmcloud is instance-template-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name-template --output JSON`

#### Command options
{: #command-options-instance-template-update}

- **TEMPLATE_ID**: ID of the template.
- **--name**: New name of an instance template.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-template-delete
{: #instance-template-delete}

Delete instance templates.

```
ibmcloud is instance-template-delete (TEMPLATE_ID1 TEMPLATE_ID2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-template-delete}

- **TEMPLATE_ID1**: ID of the template.
- **TEMPLATE_ID2**: ID of the template.
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

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--all-resource-groups**: Query all resource groups.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group
{: #instance-group}

View details of an instance group.

```
ibmcloud is instance-group INSTANCE_GROUP [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group}

- **INSTANCE_GROUP**: ID of the instance group.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-create
{: #instance-group-create}

Create an instance group.

```
ibmcloud is instance-group-create INSTANCE_GROUP_NAME --instance-template INSTANCE_TEMPLATE --subnet-ids IDS [--membership-count MEMBERSHIP_COUNT] [--lb-id LB_ID --lb-pool-id LB_POOL_ID --application-port APPLICATION_PORT] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-group-create}

- `ibmcloud is instance-group-create group-name --instance-template 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is instance-group-create group-name --instance-template 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --membership-count 2`
- `ibmcloud is instance-group-create group-name --instance-template 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --output JSON`
- `ibmcloud is instance-group-create group-name --instance-template 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --lb-id 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --lb-pool-id d728d126-f2b9-48e8-ab67-16bb694b88f2 --application-port 2323`

#### Command options
{: #command-options-instance-group-create}

- **INSTANCE_GROUP_NAME**: Name of the instance group.
- **--instance-template**: ID of an instance template.
- **--membership-count**: The membership count of the instance group.
- **--subnet-ids**: Comma-separated IDs of subnets.
- **--lb-id**: ID of the load balancer.
- **--lb-pool-id**: ID of the load balancer pool.
- **--application-port**: The application port to route load balancer traffic.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-update
{: #instance-group-update}

Update an instance group.

```
ibmcloud is instance-group-update INSTANCE_GROUP [--instance-template INSTANCE_TEMPLATE] [--membership-count MEMBERSHIP_COUNT] [--subnet-ids IDS] [--name NEW_NAME] [--lb-id LB_ID --lb-pool-id LB_POOL_ID --application-port APPLICATION_PORT] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-instance-group-update}

- `ibmcloud is instance-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name --instance-template 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is instance-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --membership-count 2`
- `ibmcloud is instance-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is instance-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name --output JSON`
- `ibmcloud is instance-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --lb-id 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --lb-pool-id d728d126-f2b9-48e8-ab67-16bb694b88f3 --application-port 80`

#### Command options
{: #command-options-instance-group-update}

- **INSTANCE_GROUP**: ID of the instance group.
- **--instance-template**: ID of an instance template.
- **--membership-count**: The membership count of the instance group.
- **--subnet-ids**: Comma-separated IDs of subnets.
- **--name**: New name of the instance group.
- **--lb-id**: ID of the load balancer.
- **--lb-pool-id**: ID of the load balancer pool.
- **--application-port**: The application port to route load balancer traffic.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-delete
{: #instance-group-delete}

Delete instance groups.

```
ibmcloud is instance-group-delete (INSTANCE_GROUP1 INSTANCE_GROUP2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-delete}

- **INSTANCE_GROUP1**: ID of the instance group.
- **INSTANCE_GROUP2**: ID of the instance group.
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

- **INSTANCE_GROUP**: ID of the instance group.
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

- **INSTANCE_GROUP**: ID of the instance group.
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

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the manager.
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
- `ibmcloud is instance-group-manager-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --max-members 20 --min-members 2 --cooldown 400 --aggregation-window 120 --name my--autoscale-manager --management-enabled false`
- `ibmcloud is instance-group-manager-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-scheduled-manager --manager-type scheduled`

#### Command options
{: #command-options-instance-group-manager-create}

- **INSTANCE_GROUP**: ID of the instance group.
- **--manager-type**: The type of instance group manager. One of: **autoscale**, **scheduled**. (default: **autoscale**).
- **--aggregation-window**: The time window in seconds to aggregate metrics prior to evaluation. Range 90-600. Divisible by 30. (default: **90**).
- **--cooldown**: The duration of time in seconds to pause further scale actions after scaling has taken place. Range 120-3600. (default: **300**).
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

#### Command options
{: #command-options-instance-group-manager-update}

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the manager.
- **--aggregation-window**: The time window, in seconds, to aggregate metrics prior to evaluation. Range 90-600. Divisible by 30.
- **--cooldown**: The duration of time, in seconds, to pause further scale actions after scaling has taken place. Range 120-3600.
- **--max-members**: The maximum number of members in a managed instance group. Range 1-1000.
- **--min-members**: The minimum number of members in a managed instance group. Range 1-1000.
- **--management-enabled**: If set to false, the manager will not manipulate the instance group. One of: **true**, **false**.
- **--name**: New name of the instance group manager.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager-delete
{: #instance-group-manager-delete}

Delete a manager.

```
ibmcloud is instance-group-manager-delete INSTANCE_GROUP MANAGER [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-manager-delete}

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the manager.
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

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the manager.
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

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the manager.
- **ACTION**: ID of the action.
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

#### Command options
{: #command-options-instance-group-manager-action-create}

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the manager.
- **--run-at**: The date and time specified for the scheduled action. It should be in ISO 8601 format like **2024-03-05T15:31:50.701Z** or **2024-03-05T15:31:50.701+8:00**.
- **--cron**: The cron specification for a recurring scheduled action.
- **--membership-count**: The number of members the instance group should have at the scheduled time.
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

#### Command options
{: #command-options-instance-group-manager-action-update}

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the manager.
- **ACTION**: ID of the action.
- **--run-at**: The date and time specified for the scheduled action. It should be in ISO 8601 format like **2024-03-05T15:31:50.701Z** or **2024-03-05T15:31:50.701+8:00**.
- **--cron**: The cron specification for a recurring scheduled action.
- **--membership-count**: The number of members the instance group should have at the scheduled time.
- **--min-members**: The minimum number of members the instance group should have at the scheduled time. Range 1-1000.
- **--max-members**: The maximum number of members the instance group should have at the scheduled time. Range 1-1000.
- **--name**: New name of the instance group manager action.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager-action-delete
{: #instance-group-manager-action-delete}

Delete instance group manager action.

```
ibmcloud is instance-group-manager-action-delete INSTANCE_GROUP MANAGER ACTION [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-manager-action-delete}

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the manager.
- **ACTION**: ID of the action.
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

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the manager.
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

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the manager.
- **POLICY**: ID of the policy.
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

#### Command options
{: #command-options-instance-group-manager-policy-create}

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the manager.
- **--metric-type**: The type of metric to be evaluated: cpu (utilization percent), memory (utilization percent), network_in (Mbps), network_out (Mbps).
- **--metric-value**: The metric value to be evaluated.
- **--name**: Name of the policy.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-manager-policy-delete
{: #instance-group-manager-policy-delete}

Delete instance group manager policies.

```
ibmcloud is instance-group-manager-policy-delete INSTANCE_GROUP MANAGER (POLICY1 POLICY2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-manager-policy-delete}

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the manager.
- **POLICY1**: ID of the policy.
- **POLICY2**: ID of the policy.
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

#### Command options
{: #command-options-instance-group-manager-policy-update}

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the manager.
- **POLICY**: ID of the policy.
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

- **INSTANCE_GROUP**: ID of the instance group.
- **MEMBER**: ID of the membership.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is instance-group-membership-delete
{: #instance-group-membership-delete}

Delete membership for an instance group.

```
ibmcloud is instance-group-membership-delete INSTANCE_GROUP (MEMBER1 MEMBER2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-instance-group-membership-delete}

- **INSTANCE_GROUP**: ID of the instance group.
- **MEMBER1**: ID of the membership.
- **MEMBER2**: ID of the membership.
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

#### Command options
{: #command-options-instance-group-membership-update}

- **INSTANCE_GROUP**: ID of the instance group.
- **MEMBER**: ID of the membership.
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

- **INSTANCE_GROUP**: ID of the instance group.
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

- **INSTANCE_GROUP**: ID of the instance group.
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
{: #regions}

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
{: #zones}

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

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
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

#### Command options
{: #command-options-volume}

- **VOLUME**: ID of the volume.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is volume-create
{: #volume-create}

Create a volume.

```
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--capacity CAPACITY] [--iops IOPS] [--encryption-key ENCRYPTION_KEY] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-volume-create}

- `ibmcloud is volume-create my-volume general-purpose us-south-1`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --capacity 500`
- `ibmcloud is volume-create my-volume custom us-south-1 --iops 10000 --capacity 1000`
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
- **--iops**: Input/Output Operations Per Second for the volume, it is only applicable for custom profile volumes. For the IOPS range, refer to https://cloud.ibm.com/docs/vpc?topic=vpc-block-storage-profiles#custom.
- **--encryption-key**: The CRN of the Key Management Service root key.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is volume-delete
{: #volume-delete}

Delete volumes.

```
ibmcloud is volume-delete (VOLUME1 VOLUME2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-volume-delete}

- **VOLUME1**: ID of the volume.
- **VOLUME2**: ID of the volume.
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
ibmcloud is volume-update VOLUME [--name NAME | --capacity CAPACITY] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-volume-update}

- `ibmcloud is volume-update 64bec87d-d175-4fa5-b240-b092fdbcedd6 --name my-volume --output JSON`
- `ibmcloud is volume-update 64bec87d-d175-4fa5-b240-b092fdbcedd6 --capacity 250 --output JSON`

#### Command options
{: #command-options-volume-update}

- **VOLUME**: ID of the volume.
- **--name**: New name of the volume.
- **--capacity**: The capacity of the volume in gigabytes. Capacity can be expanded up to 16000 for custom and general-purpose profile volumes, 9600 for 5 IOPS-tier profile volumes and 4800 for 10 IOPS-tier profile volumes. It is applicable only for attached data volume (not boot volume). Size can be only increased, not decreased.
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

- **--volume**: ID of the volume to snapshot.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
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

#### Command options
{: #command-options-snapshot}

- **SNAPSHOT**: ID of the snapshot.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-create
{: #snapshot-create}

Create a snapshot from a volume.

```
ibmcloud is snapshot-create --volume VOLUME [--name NAME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command examples
{: #command-examples-snapshot-create}

- `ibmcloud is snapshot-create --name my-snapshot --volume r006-1772e102-0671-48c7-a97a-504247e61e48`
- `ibmcloud is snapshot-create --name my-snapshot --volume r006-1772e102-0671-48c7-a97a-504247e61e48 --resource-group-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is snapshot-create --name my-snapshot --volume r006-1772e102-0671-48c7-a97a-504247e61e48 --resource-group-name Default`
- `ibmcloud is snapshot-create --name my-snapshot --volume r006-1772e102-0671-48c7-a97a-504247e61e48 --output JSON`

#### Command options
{: #command-options-snapshot-create}

- **--volume**: ID of the volume to snapshot.
- **--name**: New name for the snapshot.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-delete
{: #snapshot-delete}

Delete snapshots.

```
ibmcloud is snapshot-delete (SNAPSHOT1 SNAPSHOT2 ...) [--output JSON] [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-snapshot-delete}

- **SNAPSHOT1**: ID of the snapshot.
- **SNAPSHOT2**: ID of the snapshot.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **--force, -f**: Force the operation without confirmation.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is snapshot-update
{: #snapshot-update}

Update a snapshot.

```
ibmcloud is snapshot-update SNAPSHOT --name NEW_NAME [--output JSON] [-q, --quiet]
```

#### Command example
{: #command-example-snapshot-update}

- `ibmcloud is snapshot-update 64bec87d-d175-4fa5-b240-b092fdbcedd6 --name my-snapshot --output JSON`

#### Command options
{: #command-options-snapshot-update}

- **SNAPSHOT**: ID of the snapshot.
- **--name**: New name of the snapshot.
- **--output**: Specify output format, only JSON is supported. One of: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---
