---

copyright:
  years: 2018, 2020
lastupdated: "2020-07-02"

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

4. Make sure the CLI plug-in targets generation 2 of the VPC infrastructure service. To view the current target generation, run the following command:

  ```
  ibmcloud is target
  ```
  {: pre}

  If the plug-in is not currently targeting generation 2, run the following command:

  ```
  ibmcloud is target --gen 2
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
ibmcloud is floating-ip FLOATING_IP [--json]
```

#### Command options
{: #command-options-floating-ip}

- **FLOATING_IP**: ID of the floating IP.
- **--json**: Format output in JSON.

---

### ibmcloud is floating-ip-release
{: #floating-ip-release}

Release a floating IP.

```
ibmcloud is floating-ip-release FLOATING_IP [-f, --force]
```

#### Command options
{: #command-options-floating-ip-release}

- **FLOATING_IP**: ID of the floating IP.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is floating-ip-reserve
{: #floating-ip-reserve}

Reserve a floating IP.

```
ibmcloud is floating-ip-reserve FLOATING_IP_NAME (--zone ZONE_NAME | --nic-id NIC_ID) [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-floating-ip-reserve}

- `ibmcloud is floating-ip-reserve my-ip --zone us-south-1`
- `ibmcloud is floating-ip-reserve my-ip --nic-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is floating-ip-reserve my-ip --nic-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --json`

#### Command options
{: #command-options-floating-ip-reserve}

- **FLOATING_IP_NAME**: Name of the floating IP.
- **--zone**: Name of the target zone. This option is mutually exclusive with **--nic-id**.
- **--nic-id**: ID of the target network interface. This option is mutually exclusive with **--zone**.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is floating-ip-update
{: #floating-ip-update}

Update a floating IP.

```
ibmcloud is floating-ip-update FLOATING_IP [--name NEW_NAME] [--nic-id NIC_ID] [--json]
```

#### Command examples
{: #command-examples-floating-ip-update}

- `ibmcloud is floating-ip-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-ip`
- `ibmcloud is floating-ip-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --nic-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is floating-ip-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --nic-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --json`

#### Command options
{: #command-options-floating-ip-update}

- **FLOATING_IP**: ID of the floating IP.
- **--name**: New name of the floating IP.
- **--nic-id**: ID of the network interface to bind.
- **--json**: Format output in JSON.

---

### ibmcloud is floating-ips
{: #floating-ips}

List all floating IPs.

```
ibmcloud is floating-ips [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-floating-ips}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

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
- **--active**: Indicates whether this collector is active. Enumeration type: **TRUE**, **FALSE**.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported now. Enumeration type: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is flow-log-delete
{: #flow-log-delete}

Delete a flow log.

```
ibmcloud is flow-log-delete FLOW_LOG [-f, --force] [-q, --quiet]
```

#### Command options
{: #command-options-flow-log-delete}

- **FLOW_LOG**: ID of the flow log.
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
- **--active**: Indicates whether this collector is active. Updating to false deactivates the collector and updating to true activates the collector. Enumeration type: **TRUE**, **FALSE**.
- **--output**: Specify output format, only JSON is supported now. Enumeration type: **JSON**.
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
- **--output**: Specify output format, only JSON is supported now. Enumeration type: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

### ibmcloud is flow-logs
{: #flow-logs}

List all flow logs in the region.

```
ibmcloud is flow-logs [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--output JSON] [-q, --quiet]
```

#### Command options
{: #command-options-flow-logs}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--output**: Specify output format, only JSON is supported now. Enumeration type: **JSON**.
- **-q, --quiet**: Suppress verbose output.

---

## Application load balancers
{: #alb-anchor}

The following section provides information about CLI commands for working with load balancers, listeners, and pools.


### ibmcloud is load-balancer
{: #load-balancer}

View details of a load balancer.

```
ibmcloud is load-balancer LOAD_BALANCER_ID [--json]
```

#### Command options
{: #command-options-load-balancer}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-create
{: #load-balancer-create}

Create a load balancer.

```
ibmcloud is load-balancer-create LOAD_BALANCER_NAME LOAD_BALANCER_TYPE (--subnet SUBNET_ID1 --subnet SUBNET_ID2 ...) [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-load-balancer-create}

- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --resource-group-id fee82deba12e4c0fb69c3b09d1f12345`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --resource-group-name Default`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --json`

#### Command options
{: #command-options-load-balancer-create}

- **LOAD_BALANCER_NAME**: Name of the load balancer.
- **LOAD_BALANCER_TYPE**: Type of the load balancer, public or private.
- **--subnet**: ID of the subnets to provision this load balancer. This parameter can be specified multiple times to provision multiple subnets.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-delete
{: #load-balancer-delete}

Delete a load balancer.

```
ibmcloud is load-balancer-delete LOAD_BALANCER_ID [-f, --force]
```

#### Command options
{: #command-options-load-balancer-delete}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is load-balancer-listener
{: #load-balancer-listener}

View details of a load balancer listener.

```
ibmcloud is load-balancer-listener LOAD_BALANCER_ID LISTENER_ID [--json]
```

#### Command options
{: #command-options-load-balancer-listener}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-listener-create
{: #load-balancer-listener-create}

Create a load balancer listener.

```
ibmcloud is load-balancer-listener-create LOAD_BALANCER_ID PORT PROTOCOL [--default-pool DEFAULT_POOL_ID] [--connection-limit LIMIT] [--certificate-instance-crn CERTIFICATE_INSTANCE_CRN] [--policies LISTENER_POLICIES_JSON | @LISTENER_POLICIES_JSON_FILE] [--json]
```

#### Command examples
{: #command-examples-load-balancer-listener-create}

- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 https --certificate-instance-crn crn:v1:bluemix:public:cloudcerts:us-south:a/123456:b8866ea4-b8df-467e-801a-da1db7e020bf:certificate:78ff9c4c97d013fb2a95b21dddde7758`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --connection-limit 2000`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --default-pool 70294e14-4e61-11e8-bcf4-0242ac110004`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --policies '[{"name": "my-policy", "priority": 5, "action": "reject" }]'`

   `priority` is the priority of the policy. A lower value indicates a higher priority. Range 1 -10. Action Enum - [forward, redirect, reject].
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --policies '[{"priority": 5, "action": "forward", "target": { "id": 70294e14-4e61-11e8-bcf4-0242ac110004 }}]'`

   When action is forward, Pool Identity is required to specify which pool the load balancer forwards the traffic to.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --policies '[{"priority": 5, "action": "redirect", "target": { "http_status_code": 301, "url": "https://www.redirect.com"}}]'`
   When action is redirect, 'url' is required to specify the url and 'http_status_code' used in the redirect response. 'http_status_code' Enum: [301, 302, 303, 307, 308]. 'url' - The redirect target URL.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --policies '[{"priority": 5, "action": "reject", "rules": { "condition": "equals", "type": "header", "field": "My-app-header", "value": "value"}}]'`

   `condition` Enum -[ contains, equals, matches_regex ]. `type` Enum -[ header, hostname, path ]. `field` - HTTP header field. This is only applicable to the `header` rule type. `value` is the value to be matched for the rule condition.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --json`

#### Command options
{: #command-options-load-balancer-listener-create}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **PORT**: The listener port number. Range 1-65535.
- **PROTOCOL**: The listener protocol. Load balancers in the application family support tcp, http, and https. Load balancers in the network family support tcp.
- **--default-pool**: ID of the default pool.
- **--connection-limit**: Listen connection limits. This option isn't applicable for the load balancers in the network family.
- **--certificate-instance-crn**: CRN of the certificate instance. Required when protocol is https. This option isn't applicable for the load balancers in the network family.
- **--policies**: LISTENER_POLICIES_JSON | @LISTENER_POLICIES_JSON_FILE, listener policies in JSON or JSON file. This option isn't applicable for the load balancers in the network family.

- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-listener-delete
{: #load-balancer-listener-delete}

Delete a load balancer listener.

```
ibmcloud is load-balancer-listener-delete LOAD_BALANCER_ID LISTENER_ID [-f, --force]
```

#### Command options
{: #command-options-load-balancer-listener-delete}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is load-balancer-listener-policies
{: #load-balancer-listener-policies}

List all load balancer policies.

```
ibmcloud is load-balancer-listener-policies LOAD_BALANCER_ID LISTENER_ID [--json]
```

#### Command options
{: #command-options-load-balancer-listener-policies}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-listener-policy
{: #load-balancer-listener-policy}

View details of load balancer listener policy.

```
ibmcloud is load-balancer-listener-policy LOAD_BALANCER_ID LISTENER_ID POLICY_ID [--json]
```

#### Command options
{: #command-options-load-balancer-listener-policy}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY_ID**: ID of the policy.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-listener-policy-create
{: #load-balancer-listener-policy-create}

Create a load balancer listener policy.

```
ibmcloud is load-balancer-listener-policy-create LOAD_BALANCER_ID LISTENER_ID --priority PRIORITY (--action forward | redirect | reject) [--name NEW_NAME] [--target-id TARGET_ID | (--target-http-status-code TARGET_HTTP_STATUS_CODE --target-url TARGET_URL)] [--rules LISTENER_POLICY_RULES_JSON | @LISTENER_POLICY_RULES_JSON_FILE] [--json]
```

#### Command examples
{: #command-examples-load-balancer-listener-policy-create}

- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-policy --action reject --priority 5`

      `priority` is the priority of the policy. A lower value indicates a higher priority. Range 1 - 10. Action Enum - [forward, redirect, reject].
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action forward --priority 2 --target-id 70294e14-4e61-11e8-bcf4-0242ac110004`

  When `action` is `forward`, Pool Identity is required to specify which pool the load balancer forwards the traffic to.
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action redirect --priority 1 --target-http-status-code 301 --target-url "https://www.redirect.com"`

   When `action` is `redirect`, `url` is required to specify the URL and `http_status_code` is used in the redirect response. `http_status_code` Enum: [301, 302, 303, 307, 308]. `url` is the redirect target URL.
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action reject --priority 4 --rules '[{"rules": { "condition": "equals", "type": "header", "field": "My-app-header", "value": "value"}}]'`

   `condition` Enum -[ contains, equals, matches_regex ]. `type` Enum -[ header, hostname, path ]. `field` is the HTTP header field. This is only applicable to the `header` rule type. `value` is the value to be matched for the rule condition.
- `ibmcloud is load-balancer-listener-policy-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --action reject --priority 3 --name my-policy --json`

#### Command options
{: #command-options-load-balancer-listener-policy-create}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--priority**: Priority of the policy. Lower value indicates higher priority, for example: 5, range: [1-10].
- **--action**: The policy action. Enumeration type: **forward**, **redirect**, **reject**.
- **--name**: The new name of the policy.
- **--target-id**: The unique identifier for this load balancer pool, which is specified with **forward** action.
- **--target-http-status-code**: The http status code in the redirect response, one of [301, 302, 303, 307, 308], specified with 'redirect' action.
- **--target-url**: The redirect target URL, specified with **redirect** action.
- **--rules**: LISTENER_POLICY_RULES_JSON | @LISTENER_POLICY_RULES_JSON_FILE, listener policy rules in JSON or JSON file.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-listener-policy-delete
{: #load-balancer-listener-policy-delete}

Delete a policy from a load balancer listener.

```
ibmcloud is load-balancer-listener-policy-delete LOAD_BALANCER_ID LISTENER_ID POLICY_ID [-f, --force]
```

#### Command options
{: #command-options-load-balancer-listener-policy-delete}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY_ID**: ID of the policy.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is load-balancer-listener-policy-rule
{: #load-balancer-listener-policy-rule}

List single load balancer policy rule.

```
ibmcloud is load-balancer-listener-policy-rule LOAD_BALANCER_ID LISTENER_ID POLICY_ID RULE_ID [--json]
```

#### Command options
{: #command-options-load-balancer-listener-policy-rule}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY_ID**: ID of the policy.
- **RULE_ID**: ID of the rule.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-listener-policy-rule-create
{: #load-balancer-listener-policy-rule-create}

Create a load balancer listener policy rule.

```
ibmcloud is load-balancer-listener-policy-rule-create LOAD_BALANCER_ID LISTENER_ID POLICY_ID (--condition contains | equals | matches_regex) (--type header | hostname | path) --value VALUE [--field FIELD] [--json]
```

#### Command example
{: #command-example-load-balancer-listener-policy-rule-create}

-`ibmcloud is load-balancer-listener-policy-rule-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --condition equals --type header --field my-app-header --value  match-value --json`

#### Command options
{: #command-options-load-balancer-listener-policy-rule-create}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY_ID**: ID of the policy.
- **--condition**: The condition of the rule. Enumeration type: **contains**, **equals**, **matches_regex**.
- **--type**: The type of the rule. Enumeration type: **header**, **hostname**, **path**.
- **--value**: Value to match the rule condition.
- **--field**: HTTP header field. This is applicable only to **header** rule type.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-listener-policy-rule-delete
{: #load-balancer-listener-policy-rule-delete}

Delete a policy from a load balancer listener.

```
ibmcloud is load-balancer-listener-policy-rule-delete LOAD_BALANCER_ID LISTENER_ID POLICY_ID RULE_ID [-f, --force]
```

#### Command options
{: #command-options-load-balancer-listener-policy-rule-delete}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY_ID**: ID of the policy.
- **RULE_ID**: ID of the rule.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is load-balancer-listener-policy-rule-update
{: #load-balancer-listener-policy-rule-update}

Update a rule of a load balancer listener policy.

```
ibmcloud is load-balancer-listener-policy-rule-update LOAD_BALANCER_ID LISTENER_ID POLICY_ID RULE_ID [--condition contains | equals | matches_regex] [--type header | hostname | path] [--value VALUE] [--field FIELD] [--json]
```

#### Command example
{: #command-example-load-balancer-listener-policy-rule-update}

- `ibmcloud is load-balancer-listener-policy-rule-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 70294e14-4e61-11e8-bcf4-0242ac110004 --condition equals --type header --field my-app-header --value  match-value --json`

#### Command options
{: #command-options-load-balancer-listener-policy-rule-update}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY_ID**: ID of the policy.
- **RULE_ID**: ID of the rule.
- **--condition**: The condition of the rule. Enumeration type: **contains**, **equals**, **matches_regex**.
- **--type**: The type of the rule. Enumeration type: **header**, **hostname**, **path**.
- **--value**: Value to match the rule condition.
- **--field**: HTTP header field. This is applicable only to **header** rule type.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-listener-policy-rules
{: #load-balancer-listener-policy-rules}

List all load balancer policy rules.

```
ibmcloud is load-balancer-listener-policy-rules LOAD_BALANCER_ID LISTENER_ID POLICY_ID [--json]
```

#### Command options
{: #command-options-load-balancer-listener-policy-rules}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY_ID**: ID of the policy.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-listener-policy-update
{: #load-balancer-listener-policy-update}

Update a policy of a load balancer listener.

```
ibmcloud is load-balancer-listener-policy-update LOAD_BALANCER_ID LISTENER_ID POLICY_ID [--name NEW_NAME] [--priority PRIORITY] [--target-id TARGET_ID] [--target-http-status-code TARGET_HTTP_STATUS_CODE] [--target-url TARGET_URL] [--json]
```

#### Command examples
{: #command-examples-load-balancer-listener-policy-update}

- `ibmcloud is load-balancer-listener-policy-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --name my-policy --priority 5`
- `ibmcloud is load-balancer-listener-policy-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --action forward --target-id 70294e14-4e61-11e8-bcf4-0242ac110004`
When action is forward, Pool Identity is required to specify which pool the load balancer forwards the traffic to.
- `ibmcloud is load-balancer-listener-policy-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target-http-status-code 301 --target-url "https://www.redirect.com"`
When action is redirect, 'URL' is required to specify the URL and 'http_status_code' that is used in the redirect response. 'http_status_code' Enum: [301, 302, 303, 307, 308]. 'url' - The redirect target URL.
- `ibmcloud is load-balancer-listener-policy-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --name my-policy --json`

#### Command options
{: #command-options-load-balancer-listener-policy-update}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **POLICY_ID**: ID of the policy.
- **--name**: The user-defined name for this policy. Names must be unique within the load balancer listener that the policy resides in.
- **--priority**: Priority of the policy. Lower value indicates higher priority, for example: 5, range: [1-10].
- **--target-id**: The unique identifier for this load balancer pool, which is specified with **forward** action.
- **--target-http-status-code**: The HTTP status code in the redirect response, one of [301, 302, 303, 307, 308], specified with **redirect** action.
- **--target-url**: The redirect target URL, specified with **redirect** action.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-listener-update
{: #load-balancer-listener-update}

Update a load balancer listener.

```
ibmcloud is load-balancer-listener-update LOAD_BALANCER_ID LISTENER_ID [--certificate-instance-crn CERTIFICATE_INSTANCE_CRN] [--connection-limit LIMIT] [--default-pool DEFAULT_POOL_ID] [--protocol http | https | tcp] [--port PORT] [--json]
```

#### Command examples
{: #command-examples-load-balancer-listener-update}

- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --certificate-instance-crn crn:v1:bluemix:public:cloudcerts:us-south:a/123456:b8866ea4-b8df-467e-801a-da1db7e020bf:certificate:78ff9c4c97d013fb2a95b21dddde7758`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --connection-limit 2000`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --default-pool 70294e14-4e61-11e8-bcf4-0242ac110004`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --protocol https`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --port 222`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --json`

#### Command options
{: #command-options-load-balancer-listener-update}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--certificate-instance-crn**: CRN of the certificate instance. Required when protocol is HTTPS.
- **--connection-limit**: The connection limit of the listener.
- **--default-pool**: ID of the default pool.
- **--protocol**: The listener protocol. Load balancers in the application family support **tcp**, **http**, and **https**.
- **--port**: The listener port number. Range 1 - 65535.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-listeners
{: #load-balancer-listeners}

List all load balancer listeners.

```
ibmcloud is load-balancer-listeners LOAD_BALANCER_ID [--json]
```

#### Command options
{: #command-options-load-balancer-listeners}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-pool
{: #load-balancer-pool}

View details of a load balancer pool.

```
ibmcloud is load-balancer-pool LOAD_BALANCER_ID POOL_ID [--json]
```

#### Command options
{: #command-options-load-balancer-pool}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-pool-create
{: #load-balancer-pool-create}

Create a load balancer pool.

```
ibmcloud is load-balancer-pool-create POOL_NAME LOAD_BALANCER_ID ALGORITHM PROTOCOL HEALTH_DELAY HEALTH_RETRIES HEALTH_TIMEOUT HEALTH_TYPE [--health-monitor-url URL] [--health-monitor-port PORT] [--session-persistence-type source_ip] [--json]
```

#### Command examples
{: #command-examples-load-balancer-pool-create}

- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http`
- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --health-monitor-url / --health-monitor-port 4001`
- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --session-persistence-type source_ip --json`

#### Command options
{: #command-options-load-balancer-pool-create}

- **POOL_NAME**: Name of the pool.
- **LOAD_BALANCER_ID**: ID of the load balancer.
- **ALGORITHM**: The load-balancing algorithm. Enumeration type: **round_robin**, **weighted_round_robin**, **least_connections**
- **PROTOCOL**: The pool protocol. Load balancers in the application family support TCP, HTTP, and HTTPS. Load balancers in the network family support TCP.
- **HEALTH_DELAY**: The health check interval in seconds. The interval must be greater than the timeout value. Minimum: 2, maximum: 60.
- **HEALTH_RETRIES**: The health check maximum retries. Minimum: 1, maximum: 10.
- **HEALTH_TIMEOUT**: The health check timeout in seconds. Minimum: 1, maximum: 59.
- **HEALTH_TYPE**: The health check protocol. Load balancers in the application family support tcp, http, https. Load balancers in the network family support tcp, http.
- **--health-monitor-url**: The health check url. This option is applicable only to http type of HEALTH_TYPE.
- **--health-monitor-port**: The health check port number. If specified, the specified ports in the server member resources are overridden.
- **--session-persistence-type**: The session persistence type. Enumeration type: **source_ip**.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-pool-delete
{: #load-balancer-pool-delete}

Delete a pool from a load balancer.

```
ibmcloud is load-balancer-pool-delete LOAD_BALANCER_ID POOL_ID [-f, --force]
```

#### Command options
{: #command-options-load-balancer-pool-delete}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is load-balancer-pool-member
{: #load-balancer-pool-member}

View details of load balancer pool member.

```
ibmcloud is load-balancer-pool-member LOAD_BALANCER_ID POOL_ID MEMBER_ID [--json]
```

#### Command options
{: #command-options-load-balancer-pool-member}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **MEMBER_ID**: ID of the member.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-pool-member-create
{: #load-balancer-pool-member-create}

Create a load balancer pool member.

```
ibmcloud is load-balancer-pool-member-create LOAD_BALANCER_ID POOL_ID PORT TARGET [--weight WEIGHT] [--json]
```

#### Command examples
{: #command-examples-load-balancer-pool-member-create}

- `ibmcloud is load-balancer-pool-member-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 3000 192.168.100.5`
- `ibmcloud is load-balancer-pool-member-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 3000 192.168.100.5 --weight 100 --json`

#### Command options
{: #command-options-load-balancer-pool-member-create}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **PORT**: The port number of the running application in the server member.
- **TARGET**: The IP address of the pool member.
- **--weight**: Weight of the server member. This option is applicable only when the load balancer algorithm of its pool is **weighted_round_robin**.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-pool-member-update
{: #load-balancer-pool-member-update}

Update a member of a load balancer pool.

```
ibmcloud is load-balancer-pool-member-update LOAD_BALANCER_ID POOL_ID MEMBER_ID [--target-address TARGET_ADDRESS] [--port PORT] [--weight WEIGHT] [--json]
```

#### Command examples
{: #command-examples-load-balancer-pool-member-update}

- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target-address 192.168.100.5 --port 3001`
- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target-address 192.168.100.5 --port 3001 --weight 100 --json`

#### Command options
{: #command-options-load-balancer-pool-member-update}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **MEMBER_ID**: ID of the member.
- **--target-address**: The IP address of the pool member.
- **--port**: The port number of the application that is running in the server member.
- **--weight**: Weight of the server member. This option takes effect only when the load-balancing algorithm of its pool is **weighted_round_robin**.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-pool-member-delete
{: #load-balancer-pool-member-delete}

Delete a member from a load balancer pool.

```
ibmcloud is load-balancer-pool-member-delete LOAD_BALANCER_ID POOL_ID MEMBER_ID [-f, --force]
```

#### Command options
{: #command-options-load-balancer-pool-member-delete}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **MEMBER_ID**: ID of the member.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is load-balancer-pool-members
{: #load-balancer-pool-members}

List all the members of a load balancer pool.

```
ibmcloud is load-balancer-pool-members LOAD_BALANCER_ID POOL_ID [--json]
```

#### Command options
{: #command-options-load-balancer-pool-members}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-pool-update
{: #load-balancer-pool-update}

Update a load balancer pool.

```
ibmcloud is load-balancer-pool-update LOAD_BALANCER_ID POOL_ID [--algorithm round_robin | weighted_round_robin | least_connections] [--health-delay DELAY --health-max-retries RETRIES --health-timeout TIMEOUT --health-type https | http | tcp] [--health-monitor-url URL] [--health-monitor-port PORT] [--protocol https | http | tcp] [--session-persistence-type TYPE] [--name NEW_NAME] [--json]
```

#### Command examples
{: #command-examples-load-balancer-pool-update}

- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --algorithm round_robin`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 -- health-delay 5  --health-max-retries 2 --health-timeout 20 --health-type http`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --health-monitor-url / --health-monitor-port 4001`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --session-persistence-type source_ip`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --protocol http`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name lb-rule-name --json`

#### Command options
{: #command-options-load-balancer-pool-update}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **--algorithm**: The load-balancing algorithm. Enumeration type: **round_robin**, **weighted_round_robin**, **least_connections**.
- **--health-delay**: The health check interval in seconds. The interval must be greater than the timeout value. Minimum: 2, maximum: 60.
- **--health-max-retries**: The health check maximum retries. Minimum: 1, maximum: 10.
- **--health-timeout**: The health check timeout in seconds. Minimum: 1, maximum: 59.
- **--health-type**: The pool protocol. Load balancers in the application family support **tcp**, **http**, **https**.
- **--health-monitor-url**: The health check URL. This option is applicable only to HTTP type of --health-type.
- **--health-monitor-port**: The health check port number. The health check port number. If specified, the specified ports in the server member resources are overridden.
- **--protocol**: The pool protocol. Load balancers in the application family support **tcp**, **http**, **https**.
- **--session-persistence-type**: The session persistence type. Enumeration type: **source_ip**.
- **--name**: The new name of the pool.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-pools
{: #load-balancer-pools}

List all pools of a load balancer.

```
ibmcloud is load-balancer-pools LOAD_BALANCER_ID [--json]
```

#### Command options
{: #command-options-load-balancer-pools}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-statistics
{: #load-balancer-statistics}

List all statistics of a load balancer.

```
ibmcloud is load-balancer-statistics LOAD_BALANCER_ID [--json]
```

#### Command options
{: #command-options-load-balancer-statistics}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-update
{: #load-balancer-update}

Update a load balancer.

```
ibmcloud is load-balancer-update LOAD_BALANCER_ID --name NEW_NAME [--json]
```

#### Command examples
{: #command-examples-load-balancer-update}

- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-loadBalancer`
- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-loadBalancer --json`

#### Command options
{: #command-options-load-balancer-update}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--name**: New name of the Load balancer.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancers
{: #load-balancers}

List all load balancers.

```
ibmcloud is load-balancers [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-load-balancers}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

## Network load balancers (Beta)
{: #nlb-anchor}

The beta release of {{site.data.keyword.cloud_notm}} Network Load Balancer for VPC is only available to allowlisted users. Contact your {{site.data.keyword.cloud_notm}} Sales representative if you are interested in getting early access to this beta offering. After this offering is made generally available, you must upgrade to the standard paid plan to continue using instances that you created during the beta. Upgrade instructions are provided to beta participants. Any instance that continues to use the beta plan for this service beyond 30 days after general availability is subject to deletion.
{: beta}

### ibmcloud is load-balancer-profiles
{: #load-balancer-profiles}

List all load balancer profiles in the region.

```
ibmcloud is load-balancer-profiles [--json]
```

#### Command options
{: #command-options-load-balancer-profiles}

- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-profile
{: #load-balancer-profile}

View details of a load balancer profile.

```
ibmcloud is load-balancer-profile PROFILE_NAME [--json]
```

#### Command options
{: #command-options-load-balancer-profile}

- **PROFILE_NAME**: Name of the profile.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancers
{: #load-balancers}

List all load balancers.

```
ibmcloud is load-balancers [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-load-balancers}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer
{: #load-balancer-nlb}

View details of a load balancer.

```
ibmcloud is load-balancer LOAD_BALANCER_ID [--json]
```

#### Command options
{: #command-options-load-balancer-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-create
{: #load-balancer-create-nlb}

Create a load balancer.

```
ibmcloud is load-balancer-create LOAD_BALANCER_NAME LOAD_BALANCER_TYPE (--subnet SUBNET_ID1 --subnet SUBNET_ID2 ...) [--profile PROFILE] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-load-balancer-create-nlb}

- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --profile network-medium`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --resource-group-id fee82deba12e4c0fb69c3b09d1f12345`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --resource-group-name Default`
- `ibmcloud is load-balancer-create lb-name public --subnet 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet 7ec86020-1c6e-4889-b3f0-a15f2e50f87e --json`

#### Command options
{: #command-options-load-balancer-create-nlb}

- **LOAD_BALANCER_NAME**: Name of the load balancer.
- **LOAD_BALANCER_TYPE**: Type of the load balancer, public or private.
- **--subnet**: ID of the subnets to provision this load balancer. This parameter can be specified multiple times to provision multiple subnets.
- **--profile**: The profile to use for the load balancer.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-delete
{: #load-balancer-delete-nlb}

Delete a load balancer.

```
ibmcloud is load-balancer-delete LOAD_BALANCER_ID [-f, --force]
```

#### Command options
{: #command-options-load-balancer-delete-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is load-balancer-listener
{: #load-balancer-listener-nlb}

View details of a load balancer listener.

```
ibmcloud is load-balancer-listener LOAD_BALANCER_ID LISTENER_ID [--json]
```

#### Command options
{: #command-options-load-balancer-listener-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-listener-create
{: #load-balancer-listener-create-nlb}

Create a load balancer listener.

```
ibmcloud is load-balancer-listener-create LOAD_BALANCER_ID PORT PROTOCOL [--default-pool DEFAULT_POOL_ID] [--connection-limit LIMIT] [--certificate-instance-crn CERTIFICATE_INSTANCE_CRN] [--policies LISTENER_POLICIES_JSON | @LISTENER_POLICIES_JSON_FILE] [--json]
```

#### Command examples
{: #command-examples-load-balancer-listener-create-nlb}

- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 https --certificate-instance-crn crn:v1:bluemix:public:cloudcerts:us-south:a/123456:b8866ea4-b8df-467e-801a-da1db7e020bf:certificate:78ff9c4c97d013fb2a95b21dddde7758`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --connection-limit 2000`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --default-pool 70294e14-4e61-11e8-bcf4-0242ac110004`
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --policies '[{"name": "my-policy", "priority": 5, "action": "reject" }]'`
Priority - Priority of the policy. Lower value indicates higher priority. Range 1 -10. Action Enum - [forward, redirect, reject].
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --policies '[{"priority": 5, "action": "forward", "target": { "id": 70294e14-4e61-11e8-bcf4-0242ac110004 }}]'`
When action is forward, Pool Identity is required to specify which pool the load balancer forwards the traffic to.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --policies '[{"priority": 5, "action": "redirect", "target": { "http_status_code": 301, "url": "https://www.redirect.com"}}]'`
When action is redirect, 'url' is required to specify the url and 'http_status_code' used in the redirect response. 'http_status_code' Enum: [301, 302, 303, 307, 308]. 'url' - The redirect target URL.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --policies '[{"priority": 5, "action": "reject", "rules": { "condition": "equals", "type": "header", "field": "My-app-header", "value": "value"}}]'`
'condition' Enum -[ contains, equals, matches_regex ]. 'type' Enum -[ header, hostname, path ]. 'field' - HTTP header field. This is only applicable to 'header' rule type. 'value' - Value to be matched for rule condition.
- `ibmcloud is load-balancer-listener-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 443 http --json`

#### Command options
{: #command-options-load-balancer-listener-create-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **PORT**: The listener port number. Range 1-65535.
- **PROTOCOL**: The listener protocol. Load balancers in the application family support tcp, http, and https. Load balancers in the network family support tcp.
- **--default-pool**: ID of the default pool.
- **--connection-limit**: The connections limit of the listener. This limit is not applicable for the load balancers in the network family.
- **--certificate-instance-crn**: CRN of the certificate instance. Required when protocol is https. This requirement is not applicable for the load balancers in the network family.
- **--policies**: LISTENER_POLICIES_JSON | @LISTENER_POLICIES_JSON_FILE, listener policies in JSON or JSON file. This is not applicable for the load balancers in the network family.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-listener-delete
{: #load-balancer-listener-delete-nlb}

Delete a load balancer listener.

```
ibmcloud is load-balancer-listener-delete LOAD_BALANCER_ID LISTENER_ID [-f, --force]
```

#### Command options
{: #command-options-load-balancer-listener-delete-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is load-balancer-listener-update
{: #load-balancer-listener-update-nlb}

Update a load balancer listener.

```
ibmcloud is load-balancer-listener-update LOAD_BALANCER_ID LISTENER_ID [--protocol http | https | tcp] [--port PORT] [--default-pool DEFAULT_POOL_ID] [--connection-limit LIMIT] [--certificate-instance-crn CERTIFICATE_INSTANCE_CRN] [--json]
```

#### Command examples
{: #command-examples-load-balancer-listener-update-nlb}

- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --certificate-instance-crn crn:v1:bluemix:public:cloudcerts:us-south:a/123456:b8866ea4-b8df-467e-801a-da1db7e020bf:certificate:78ff9c4c97d013fb2a95b21dddde7758`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --connection-limit 2000`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --default-pool 70294e14-4e61-11e8-bcf4-0242ac110004`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --protocol https`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --port 222`
- `ibmcloud is load-balancer-listener-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --json`

#### Command options
{: #command-options-load-balancer-listener-update-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **LISTENER_ID**: ID of the listener.
- **--protocol**: The listener protocol. Load balancers in the application family support tcp, http, and https. Load balancers in the network family support tcp.
- **--port**: The listener port number. Range 1-65535.
- **--default-pool**: ID of the default pool.
- **--connection-limit**: The connections limit of the listener. This limit is not applicable for the load balancers in the network family.
- **--certificate-instance-crn**: CRN of the certificate instance. Required when protocol is https. This requirement is not applicable for the load balancers in the network family.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-listeners
{: #load-balancer-listeners-nlb}

List all load balancer listeners.

```
ibmcloud is load-balancer-listeners LOAD_BALANCER_ID [--json]
```

#### Command options
{: #command-options-load-balancer-listeners-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-pool
{: #load-balancer-pool-nlb}

View details of a load balancer pool.

```
ibmcloud is load-balancer-pool LOAD_BALANCER_ID POOL_ID [--json]
```

#### Command options
{: #command-options-load-balancer-pool-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-pool-create
{: #load-balancer-pool-create-nlb}

Create a load balancer pool.

```
ibmcloud is load-balancer-pool-create POOL_NAME LOAD_BALANCER_ID ALGORITHM PROTOCOL HEALTH_DELAY HEALTH_RETRIES HEALTH_TIMEOUT HEALTH_TYPE [--health-monitor-url URL] [--health-monitor-port PORT] [--session-persistence-type source_ip] [--json]
```

#### Command examples
{: #command-examples-load-balancer-pool-create-nlb}

- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http`
- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --health-monitor-url / --health-monitor-port 4001`
- `ibmcloud is load-balancer-pool-create my-lb-pool 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 round_robin http 20 2 5 http --session-persistence-type source_ip --json`

#### Command options
{: #command-options-load-balancer-pool-create-nlb}

- **POOL_NAME**: Name of the pool.
- **LOAD_BALANCER_ID**: ID of the load balancer.
- **ALGORITHM**: The load-balancing algorithm. Enumeration type: **round_robin**, **weighted_round_robin**, **least_connections**.
- **PROTOCOL**: The pool protocol. Load balancers in the application family support tcp, http, https. Load balancers in the network family support tcp.
- **HEALTH_DELAY**: The health check interval in seconds. The interval must be greater than the timeout value.. Minimum: 2, maximum: 60.
- **HEALTH_RETRIES**: The health check max retries. Minimum: 1, maximum: 10.
- **HEALTH_TIMEOUT**: The health check timeout in seconds. Minimum: 1, maximum: 59.
- **HEALTH_TYPE**: The health check protocol. Load balancers in the application family support tcp, http, https. Load balancers in the network family support tcp, http.
- **--health-monitor-url**: The health check url. This option is applicable only to http type of HEALTH_TYPE.
- **--health-monitor-port**: The health check port number. If specified, this check overrides the specified ports in the server member resources.
- **--session-persistence-type**: The session persistence type, Enumeration type: **source_ip**.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-pool-delete
{: #load-balancer-pool-delete-nlb}

Delete a pool from a load balancer.

```
ibmcloud is load-balancer-pool-delete LOAD_BALANCER_ID POOL_ID [-f, --force]
```

#### Command options
{: #command-options-load-balancer-pool-delete-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is load-balancer-pool-member
{: #load-balancer-pool-member-nlb}

View details of load balancer pool member.

```
ibmcloud is load-balancer-pool-member LOAD_BALANCER_ID POOL_ID MEMBER_ID [--json]
```

#### Command options
{: #command-options-load-balancer-pool-member-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **MEMBER_ID**: ID of the member.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-pool-member-create
{: #load-balancer-pool-member-create-nlb}

Create a load balancer pool member.

```
ibmcloud is load-balancer-pool-member-create LOAD_BALANCER_ID POOL_ID PORT TARGET [--weight WEIGHT] [--json]
```

#### Command examples
{: #command-examples-load-balancer-pool-member-create-nlb}

- `ibmcloud is load-balancer-pool-member-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 3000 192.168.100.5`
- `ibmcloud is load-balancer-pool-member-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 3000 9e692608-3b3a-4cfb-9f46-efb6b711876d`
- `ibmcloud is load-balancer-pool-member-create 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 3000 192.168.100.5 --weight 100 --json`

#### Command options
{: #command-options-load-balancer-pool-member-create-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **PORT**: The port number of the running application in the server member.
- **TARGET**: The IP address of the pool member for load balancers in the application family, or the instance ID of the pool member for load balancers in the network family.
- **--weight**: Weight of the server member. This option takes effect only when the load-balancing algorithm of its belonging pool is weighted_round_robin.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-pool-member-update
{: #load-balancer-pool-member-update-nlb}

Update a member of a load balancer pool.

```
ibmcloud is load-balancer-pool-member-update LOAD_BALANCER_ID POOL_ID MEMBER_ID [--target-address TARGET_ADDRESS | --target TARGET] [--port PORT] [--weight WEIGHT] [--json]
```

#### Command examples
{: #command-examples-load-balancer-pool-member-update-nlb}

- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target 192.168.100.5 --port 3001`
- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target 9e692608-3b3a-4cfb-9f46-efb6b711876d --port 3001`
- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target-address 192.168.100.5 --port 3001`
- `ibmcloud is load-balancer-pool-member-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --target-address 192.168.100.5 --port 3001 --weight 100 --json`

#### Command options
{: #command-options-load-balancer-pool-member-update-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **MEMBER_ID**: ID of the member.
- **--target-address**: The IP address of the pool member.
- **--target**: The IP address of the pool member for load balancers in the application family, or the instance ID of the pool member for load balancers in the network family.
- **--port**: The port number of the running application in the server member.
- **--weight**: Weight of the server member. This option takes effect only when the load-balancing algorithm of its belonging pool is weighted_round_robin.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-pool-member-delete
{: #load-balancer-pool-member-delete-nlb}

Delete a member from a load balancer pool.

```
ibmcloud is load-balancer-pool-member-delete LOAD_BALANCER_ID POOL_ID MEMBER_ID [-f, --force]
```

#### Command options
{: #command-options-load-balancer-pool-member-delete-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **MEMBER_ID**: ID of the member.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is load-balancer-pool-members
{: #load-balancer-pool-members-nlb}

List all the members of a load balancer pool.

```
ibmcloud is load-balancer-pool-members LOAD_BALANCER_ID POOL_ID [--json]
```

#### Command options
{: #command-options-load-balancer-pool-members-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-pool-update
{: #load-balancer-pool-update-nlb}

Update a pool of a load balancer.

```
ibmcloud is load-balancer-pool-update LOAD_BALANCER_ID POOL_ID [--algorithm round_robin | weighted_round_robin | least_connections] [--health-delay DELAY --health-max-retries RETRIES --health-timeout TIMEOUT --health-type https | http | tcp] [--health-monitor-url URL] [--health-monitor-port PORT] [--protocol https | http | tcp] [--session-persistence-type source_ip] [--name NEW_NAME] [--json]
```

#### Command examples
{: #command-examples-load-balancer-pool-update-nlb}

- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --algorithm round_robin`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --health-delay 20 --health-max-retries 2 --health-timeout 5 --health-type http`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --health-monitor-url / --health-monitor-port 4001`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --session-persistence-type source_ip`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --protocol http`
- `ibmcloud is load-balancer-pool-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name lb-rule-name --json`

#### Command options
{: #command-options-load-balancer-pool-update-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **POOL_ID**: ID of the pool.
- **--algorithm**: The load-balancing algorithm. Enumeration type: **round_robin**, **weighted_round_robin**, **least_connections**.
- **--health-delay**: The health check interval in seconds. The interval must be greater than the timeout value. Minimum: 2, maximum: 60.
- **--health-max-retries**: The health check max retries. Minimum: 1, maximum: 10.
- **--health-timeout**: The health check timeout in seconds. Minimum: 1, maximum: 59.
- **--health-type**: The health check protocol. Load balancers in the application family support tcp, http, https. Load balancers in the network family support tcp, http.
- **--health-monitor-url**: The health check url. This option is applicable only to http type of --health-type.
- **--health-monitor-port**: The health check port number. If specified, this check overrides the specified ports in the server member resources.
- **--protocol**: The pool protocol. Load balancers in the application family support tcp, http, https. Load balancers in the network family support tcp.
- **--session-persistence-type**: The session persistence type, Enumeration type: **source_ip**.
- **--name**: The new name of the pool.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-pools
{: #load-balancer-pools-nlb}

List all pools of a load balancer.

```
ibmcloud is load-balancer-pools LOAD_BALANCER_ID [--json]
```

#### Command options
{: #command-options-load-balancer-pools-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-statistics
{: #load-balancer-statistics-nlb}

List all statistics of a load balancer.

```
ibmcloud is load-balancer-statistics LOAD_BALANCER_ID [--json]
```

#### Command options
{: #command-options-load-balancer-statistics-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancer-update
{: #load-balancer-update-nlb}

Update a load balancer.

```
ibmcloud is load-balancer-update LOAD_BALANCER_ID --name NEW_NAME [--json]
```

#### Command examples
{: #command-examples-load-balancer-update-nlb}

- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-loadBalancer`
- `ibmcloud is load-balancer-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-loadBalancer --json`

#### Command options
{: #command-options-load-balancer-update-nlb}

- **LOAD_BALANCER_ID**: ID of the load balancer.
- **--name**: New name of the Load balancer.
- **--json**: Format output in JSON.

---

### ibmcloud is load-balancers
{: #load-balancers-nlb}

List all load balancers.

```
ibmcloud is load-balancers [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-load-balancers-nlb}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

## Network ACLs
{: #network-acls-nlb}

### ibmcloud is network-acls
{: #network-acls-ibmcloud-nlb}

List all network ACLs.

```
ibmcloud is network-acls [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-network-acls-nlb}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is network-acl
{: #network-acl-nlb}

View details of a network ACL.

```
ibmcloud is network-acl ACL [--json]
```

#### Command options
{: #command-options-network-acl-nlb}

- **ACL**: ID of the network ACL.
- **--json**: Format output in JSON.

---

### ibmcloud is network-acl-create
{: #network-acl-create-nlb}

Create a network ACL.

```
ibmcloud is network-acl-create ACL_NAME VPC [--rules (RULES_JSON|@RULES_JSON_FILE) | --source-acl-id SOURCE_ACL_ID] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-network-acl-create-nlb}

- `ibmcloud is network-acl-create my-acl 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is network-acl-create my-acl 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --source-acl-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is network-acl-create my-acl 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --rules '[{ "action": "allow", "destination": "192.168.0.0/24", "direction": "inbound", "source": "10.0.0.0/24",  "protocol": "tcp" }]'`
- `ibmcloud is network-acl-create my-acl 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --json`

#### Command options
{: #command-options-network-acl-create-nlb}

- **ACL_NAME**: Name of the network ACL.
- **VPC**: ID of the VPC.
- **--rules**: RULES_JSON|@RULES_JSON_FILE, rules for the ACL in JSON or JSON file.
- **--source-acl-id**: ID of the network ACL to copy rules from.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is network-acl-update
{: #network-acl-update-nlb}

Update a network ACL.

```
ibmcloud is network-acl-update ACL --name NEW_NAME [--json]
```

#### Command examples
{: #command-examples-network-acl-update-nlb}

- `ibmcloud is network-acl-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-acl`
- `ibmcloud is network-acl-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-acl --json`

#### Command options
{: #command-options-network-acl-update-nlb}

- **ACL**: ID of the network ACL.
- **--name**: New name of the network ACL.
- **--json**: Format output in JSON.

---

### ibmcloud is network-acl-delete
{: #network-acl-delete-nlb}

Delete a network ACL.

```
ibmcloud is network-acl-delete ACL [-f, --force]
```

#### Command options
{: #command-options-network-acl-delete-nlb}

- **ACL**: ID of the network ACL.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is network-acl-rules
{: #network-acl-rules-nlb}

List all rules of a network ACL.

```
ibmcloud is network-acl-rules ACL [--json]
```

#### Command options
{: #command-options-network-acl-rules-nlb}

- **ACL**: ID of the network ACL.
- **--json**: Format output in JSON.

---

### ibmcloud is network-acl-rule
{: #network-acl-rule-nlb}

View details of a network ACL rule.

```
ibmcloud is network-acl-rule ACL RULE [--json]
```

#### Command options
{: #command-options-network-acl-rule-nlb}

- **ACL**: ID of the network ACL.
- **RULE**: ID of the rule.
- **--json**: Format output in JSON.

---

### ibmcloud is network-acl-rule-add
{: #network-acl-rule-add-nlb}

Add a rule to a network ACL.

```
ibmcloud is network-acl-rule-add ACL ACTION DIRECTION PROTOCOL SOURCE DESTINATION [--name NAME] [--icmp-type ICMP_TYPE] [--icmp-code ICMP_CODE] [--source-port-min PORT_MIN] [--source-port-max PORT_MAX] [--destination-port-min PORT_MIN] [--destination-port-max PORT_MAX] [--before-rule-id RULE_ID] [--json]
```

#### Command examples
{: #command-examples-network-acl-rule-add-nlb}

- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound all 10.2.2.2 10.2.2.3`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound all 10.2.2.2 10.2.2.3 --name my-acl`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound icmp 10.2.2.2 10.2.2.3 --icmp-type 8 --icmp-code 0`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound tcp 10.2.2.2 10.2.2.3 --source-port-min 555  --source-port-max 666 --destination-port-min 11 --destination-port-max 55`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound all 10.2.2.2 10.2.2.3 --before-rule-id 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is network-acl-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 allow inbound all 10.2.2.2 10.2.2.3 --json`

#### Command options
{: #command-options-network-acl-rule-add-nlb}

- **ACL**: ID of the network ACL.
- **ACTION**: Enumeration type: **allow**, **deny**
- **DIRECTION**: Direction of traffic to enforce. Enumeration type: **inbound**, **outbound**
- **PROTOCOL**: Protocol to enforce. Enumeration type: **all**, **icmp**, **tcp**, **udp**
- **SOURCE**: Source IP address or CIDR block
- **DESTINATION**: Destination IP address or CIDR block
- **--name**: The name of the ACL rule.
- **--icmp-type**: ICMP traffic type to allow. Valid values are 0 - 254. This option is specified only when protocol is set to **icmp**. If unspecified, all types are allowed.
- **--icmp-code**: ICMP traffic code to allow. Valid values are 0 - 255. This option is specified only when protocol is set to **icmp**. If unspecified, all codes are allowed.
- **--source-port-min**: Minimum source port number. Valid values are **1** - **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **1**).
- **--source-port-max**: Maximum source port number. Valid values are **1** - **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **65535**).
- **--destination-port-min**: Minimum destination port number. Valid values are **1** - **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **1**).
- **--destination-port-max**: Maximum destination port number. Valid values are **1** - **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **65535**).
- **--before-rule-id**: ID of the rule that this rule is inserted before.
- **--json**: Format output in JSON.

---

### ibmcloud is network-acl-rule-update
{: #network-acl-rule-update-nlb}

Update a rule of a network ACL.

```
ibmcloud is network-acl-rule-update ACL RULE [--name NEW_NAME] [--direction inbound | outbound] [--action allow | deny] [--before-rule-id RULE_ID] [--source SOURCE] [--dest DEST] [--icmp-type ICMP_TYPE] [--icmp-code ICMP_CODE] [--source-port-min PORT_MIN] [--source-port-max PORT_MAX] [--destination-port-min PORT_MIN] [--destination-port-max PORT_MAX] [--json]
```

#### Command examples
{: #command-examples-network-acl-rule-update-nlb}

- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol all --source 10.2.2.2 --destination 10.2.2.3`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol all --source 10.2.2.2 --destination 10.2.2.3 --name my-acl`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol icmp --source 10.2.2.2 --destination 10.2.2.3 --icmp-type 8 --icmp-code 0`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol tcp --source 10.2.2.2 --destination 10.2.2.3 --source-port-min 555 --source-port-max 666 --destination-port-min 11 --destination-port-max 55`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol all --source 10.2.2.2 --destination 10.2.2.3 --before-rule-id 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is network-acl-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --action allow --direction inbound --protocol all --source 10.2.2.2 --destination 10.2.2.3 --json`

#### Command options
{: #command-options-network-acl-rule-update-nlb}

- **ACL**: ID of the network ACL.
- **RULE**: ID of the rule.
- **--name**: New name of the rule.
- **--direction**: Direction of traffic to enforce. Enumeration type: **inbound**, **outbound**.
- **--action**: Enumeration type: **allow**, **deny**.
- **--before-rule-id**: ID of the rule that - this rule is inserted before.
- **--source**: Source IP address or CIDR block.
- **--dest**: Destination IP address or CIDR block.
- **--icmp-type**: ICMP traffic type to allow. Valid values are 0 - 254. This option is specified only when protocol is set to **icmp**. If unspecified, all types are allowed.
- **--icmp-code**: ICMP traffic code to allow. Valid values are 0 - 255. This option is specified only when protocol is set to **icmp**. If unspecified, all codes are allowed.
- **--source-port-min**: Minimum source port number. Valid values are **1** - **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **1**).
- **--source-port-max**: Maximum source port number. Valid values are **1** - **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **65535**).
- **--destination-port-min**: Minimum destination port number. Valid values are **1** - **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **1**).
- **--destination-port-max**: Maximum destination port number. Valid values are **1** - **65535**. This option is specified only when protocol is set to **tcp** or **udp** (default: **65535**).
- **--json**: Format output in JSON.

---

### ibmcloud is network-acl-rule-delete
{: #network-acl-rule-delete-nlb}

Delete a rule from a network ACL.

```
ibmcloud is network-acl-rule-delete ACL RULE [-f, --force]
```

#### Command options
{: #command-options-network-acl-rule-delete-nlb}

- **ACL**: ID of the network ACL.
- **RULE**: ID of the rule.
- **--force, -f**: Force the operation without confirmation.

---

## Public gateways
{: #public-gateways-nlb}

### ibmcloud is public-gateway
{: #public-gateway-ibmcloud-nlb}

View details of a public gateway.

```
ibmcloud is public-gateway GATEWAY [--json]
```

#### Command options
{: #command-options-public-gateway-nlb}

- **GATEWAY**: ID of the public gateway.
- **--json**: Format output in JSON.

---

### ibmcloud is public-gateway-create
{: #public-gateway-create-nlb}

Create a public gateway.

```
ibmcloud is public-gateway-create GATEWAY_NAME VPC ZONE_NAME [--floating-ip-id IP_ID | --floating-ip-address IP_ADDRESS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-public-gateway-create-nlb}

- `ibmcloud is public-gateway-create my-public-gateway 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1`
- `ibmcloud is public-gateway-create my-public-gateway 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 --floating-ip-id 39300233-9995-4806-89a5-3c1b6eb88689`
- `ibmcloud is public-gateway-create my-public-gateway 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 --floating-ip-address 203.0.113.1`
- `ibmcloud is public-gateway-create my-public-gateway 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 --json`

#### Command options
{: #command-options-public-gateway-create-nlb}

- **GATEWAY_NAME**: Name of the public gateway.
- **VPC**: ID of the VPC.
- **ZONE_NAME**: Name of the zone.
- **--floating-ip-id**: ID of the floating IP bound to the public gateway.
- **--floating-ip-address**: IP address of the floating IP bound to the public gateway.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is public-gateway-delete
{: #public-gateway-delete-nlb}

Delete a public gateway.

```
ibmcloud is public-gateway-delete GATEWAY [-f, --force]
```

#### Command options
{: #command-options-public-gateway-delete-nlb}

- **GATEWAY**: ID of the public gateway.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is public-gateway-update
{: #public-gateway-update-nlb}

Update a public gateway.

```
ibmcloud is public-gateway-update GATEWAY --name NEW_NAME [--json]
```


#### Command examples
{: #command-examples-public-gateway-update-nlb}

- `ibmcloud is public-gateway-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --name my-gateway --json`

#### Command options
{: #command-options-public-gateway-update-nlb}

- **GATEWAY**: ID of the public gateway.
- **--name**: New name of the public gateway.
- **--json**: Format output in JSON.

---

### ibmcloud is public-gateways
{: #public-gateways-nlb}

List all public gateways.

```
ibmcloud is public-gateways [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-public-gateways-nlb}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

## Security groups
{: #security-groups-cli-ref}

### ibmcloud is security-group
{: #security-group}

View details of a security group.

```
ibmcloud is security-group GROUP [--json]
```

#### Command options
{: #command-options-security-group}

- **GROUP**: ID of the security group.
- **--json**: Format output in JSON.

---

### ibmcloud is security-group-create
{: #security-group-create}

Create a security group.

```
ibmcloud is security-group-create GROUP_NAME VPC [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-security-group-create}

- `ibmcloud is security-group-create my-security-group 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is security-group-create my-security-group 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --resource-group-id fee82deba12e4c0fb69c3b09d1f12345`
- `ibmcloud is security-group-create my-security-group 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --resource-group-name Default`
- `ibmcloud is security-group-create my-security-group 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --json`

#### Command options
{: #command-options-security-group-create}

- **GROUP_NAME**: Name of the security group.
- **VPC**: ID of the VPC.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is security-group-delete
{: #security-group-delete}

Delete a security group.

```
ibmcloud is security-group-delete GROUP [-f, --force]
```

#### Command options
{: #command-options-security-group-delete}

- **GROUP**: ID of the security group.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is security-group-network-interface
{: #security-group-network-interface}

View details of a network interface of a security group.

```
ibmcloud is security-group-network-interface GROUP NIC [--json]
```

#### Command options
{: #command-options-security-group-network-interface}

- **GROUP**: ID of the security group.
- **NIC**: ID of the network interface.
- **--json**: Format output in JSON.

---

### ibmcloud is security-group-network-interface-add
{: #security-group-network-interface-add}

Add a network interface to a security group.

```
ibmcloud is security-group-network-interface-add GROUP NIC [--json]
```

#### Command example
{: #command-example-security-group-network-interface-add}

- `ibmcloud is security-group-network-interface-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --json`

#### Command options
{: #command-options-security-group-network-interface-add}

- **GROUP**: ID of the security group.
- **NIC**: ID of the network interface.
- **--json**: Format output in JSON.

---

### ibmcloud is security-group-network-interface-remove
{: #security-group-network-interface-remove}

Remove a network interface from a security group.

```
ibmcloud is security-group-network-interface-remove GROUP NIC [-f, --force]
```

#### Command options
{: #command-options-security-group-network-interface-remove}

- **GROUP**: ID of the security group.
- **NIC**: ID of the network interface.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is security-group-network-interfaces
{: #security-group-network-interfaces}

List all network interfaces of a security group.

```
ibmcloud is security-group-network-interfaces GROUP [--json]
```

#### Command options
{: #command-options-security-group-network-interfaces}

- **GROUP**: ID of the security group.
- **--json**: Format output in JSON.

---

### ibmcloud is security-group-rule
{: #security-group-rule}

View details of a security group rule.

```
ibmcloud is security-group-rule GROUP RULE_ID [--json]
```

#### Command options
{: #command-options-security-group-rule}

- **GROUP**: ID of the security group.
- **RULE_ID**: ID of the security group rule.
- **--json**: Format output in JSON.

---

### ibmcloud is security-group-rule-add
{: #security-group-rule-add}

Add a rule to a security group.

```
ibmcloud is security-group-rule-add GROUP DIRECTION PROTOCOL [--remote REMOTE_ADDRESS | CIDR_BLOCK | SECURITY_GROUP_ID] [--icmp-type ICMP_TYPE [--icmp-code ICMP_CODE]] [--port-min PORT_MIN] [--port-max PORT_MAX] [--json]
```

#### Command examples
{: #command-examples-security-group-rule-add}

- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound all`
- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound icmp --icmp-type 8 --icmp-code 0`
- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound all --remote 12.2.2.3`
- `ibmcloud is security-group-rule-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 inbound tcp --port-min 4 --port-max 22 --json`

#### Command options
{: #command-options-security-group-rule-add}

- **GROUP**: ID of the security group.
- **DIRECTION**: Direction of traffic to enforce. Enumeration type: **inbound**, **outbound**
- **PROTOCOL**: Protocol to enforce. Enumeration type: **all**, **icmp**, **tcp**, **udp**
- **--remote**: The set of network interfaces from which this rule allows traffic, Can be specified as either an **REMOTE_ADDRESS**, **CIDR_BLOCK**, or **SECURITY_GROUP_ID**. If unspecified, then traffic is allowed from any source (or to any source, for outbound rules).
- **--icmp-type**: ICMP traffic type to allow. Valid values are 0 - 254. This option is specified only when protocol is set to icmp. If unspecified, all types are allowed.
- **--icmp-code**: ICMP traffic code to allow. Valid values are 0 - 255. This option is specified only when protocol is set to icmp. If unspecified, all codes are allowed.
- **--port-min**: Minimum port number. Valid values are 1 - 65535. This option is specified only when protocol is set to **tcp** or **udp**. If unspecified, all ports are allowed (default: **1**).
- **--port-max**: Maximum port number. Valid values are 1 - 65535. This option is specified only when protocol is set to **tcp** or **udp**. If unspecified, all ports are allowed (default: **65535**).
- **--json**: Format output in JSON.

---

### ibmcloud is security-group-rule-delete
{: #security-group-rule-delete}

Delete a rule from a security group.

```
ibmcloud is security-group-rule-delete GROUP RULE_ID [-f, --force]
```

#### Command options
{: #command-options-security-group-rule-delete}

- **GROUP**: ID of the security group.
- **RULE_ID**: ID of the security group rule.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is security-group-rule-update
{: #security-group-rule-update}

Update a rule of a security group.

```
ibmcloud is security-group-rule-update GROUP RULE_ID [--direction inbound | outbound] [--remote REMOTE_ADDRESS | CIDR_BLOCK | SECURITY_GROUP_ID] [--icmp-type ICMP_TYPE [--icmp-code ICMP_CODE]] [--port-min PORT_MIN] [--port-max PORT_MAX] [--json]
```

#### Command examples
{: #command-examples-security-group-rule-update}

- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound`
- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --icmp-type 8 --icmp-code 0`
- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --port-min 4 --port-max 22`
- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --remote 12.2.2.3`
- `ibmcloud is security-group-rule-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 8daca77a-4980-4d33-8f3e-7038797be8f9 --direction inbound --json`

#### Command options
{: #command-options-security-group-rule-update}

- **GROUP**: ID of the security group.
- **RULE_ID**: ID of the security group rule.
- **--direction**: Direction of traffic to enforce. Enumeration type: **inbound**, **outbound**.
- **--remote**: The set of network interfaces from which this rule allows traffic, Can be specified as either an REMOTE_ADDRESS, CIDR_BLOCK, or SECURITY_GROUP_ID. If unspecified, then traffic is allowed from any source (or to any source, for outbound rules).
- **--icmp-type**: ICMP traffic type to allow. Valid values are 0 - 254. This option is specified only when protocol is set to **icmp**. If unspecified, all types are allowed.
- **--icmp-code**: ICMP traffic code to allow. Valid values are 0 - 255. This option is specified only when protocol is set to **icmp**. If unspecified, all codes are allowed.
- **--port-min**: Minimum port number. Valid values are 1 - 65535. This option is specified only when protocol is set to **tcp** or **udp**. If unspecified, all ports are allowed (default: **1**).
- **--port-max**: Maximum port number. Valid values are 1 - 65535. This option is specified only when protocol is set to **tcp** or **udp**. If unspecified, all ports are allowed (default: **65535**).
- **--json**: Format output in JSON.

---

### ibmcloud is security-group-rules
{: #security-group-rules}

List all rules of a security group.

```
ibmcloud is security-group-rules GROUP [--json]
```

#### Command options
{: #command-options-security-group-rules}

- **GROUP**: ID of the security group.
- **--json**: Format output in JSON.

---

### ibmcloud is security-group-update
{: #security-group-update}

Update a security group.

```
ibmcloud is security-group-update GROUP [--name NEW_NAME] [--json]
```

#### Command example
{: #command-example-security-group-update}

- `ibmcloud is security-group-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --name my-security-group-name --json`

#### Command options
{: #command-options-security-group-update}

- **GROUP**: ID of the security group.
- **--name**: New name of the security group.
- **--json**: Format output in JSON.

---

### ibmcloud is security-groups
{: #security-groups}

List all security groups.

```
ibmcloud is security-groups [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-security-groups}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

## Subnets
{: #subnet-cli-ref}

### ibmcloud is subnet
{: #subnet}

View details of a subnet.

```
ibmcloud is subnet SUBNET [--show-attached] [--json]
```

#### Command options
{: #command-options-subnet}

- **SUBNET**: ID of the subnet.
- **--show-attached**: View details of resources (instances, load balancers, VPN gateways) that are attached to the subnet.
- **--json**: Format output in JSON.

---

### ibmcloud is subnet-create
{: #subnet-create}

Create a subnet.

```
ibmcloud is subnet-create SUBNET_NAME VPC (--ipv4-cidr-block CIDR_BLOCK | (--ipv4-address-count ADDR_COUNT --zone ZONE_NAME)) [--network-acl-id NETWORK_ACL_ID] [--public-gateway-id PUBLIC_GATEWAY_ID] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-subnet-create}

- `ibmcloud is subnet-create my-subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4-cidr-block 10.10.10.0/24`
- `ibmcloud is subnet-create my-subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4-address-count 256 --zone us-south-2`
- `ibmcloud is subnet-create my-subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4-address-count 256 --zone us-south-2 --network-acl-id 8daca77a-4980-4d33-8f3e-7038797be8f9`
- `ibmcloud is subnet-create my-subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4-address-count 256 --zone us-south-2 --public-gateway-id 8daca77a-4980-4d33-8f3e-7038797be8f9`
- `ibmcloud is subnet-create my-subnet 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4-address-count 256 --zone us-south-2 --public-gateway-id 8daca77a-4980-4d33-8f3e-7038797be8f9 --json`

#### Command options
{: #command-options-subnet-create}

- **SUBNET_NAME**: Name of the subnet.
- **VPC**: ID of the VPC.
- **--ipv4-cidr-block**: the IPv4 range of the subnet. This option is mutually exclusive with **--ipv4-address-count**.
- **--ipv4-address-count**: The total number of IPv4 addresses required. Total must be a power of 2 and minimum value is 8. This option is mutually exclusive with **--ipv4-cidr-block**.
- **--zone**: Name of the zone.
- **--network-acl-id**: The ID of the network ACL.
- **--public-gateway-id**: The ID of the public gateway.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is subnet-delete
{: #subnet-delete}

Delete a subnet.

```
ibmcloud is subnet-delete SUBNET [-f, --force]
```

#### Command options
{: #command-options-subnet-delete}

- **SUBNET**: ID of the subnet.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is subnet-update
{: #subnet-update}

Update a subnet.

```
ibmcloud is subnet-update SUBNET [--name NEW_NAME] [--network-acl-id NETWORK_ACL_ID] [--public-gateway-id PUBLIC_GATEWAY_ID] [--json]
```

#### Command examples
{: #command-examples-subnet-update}

- `ibmcloud is subnet-update ec8bb350-d802-4f1b-b362-b848abd5bb65 --name my-subnet`
- `ibmcloud is subnet-update ec8bb350-d802-4f1b-b362-b848abd5bb65 --network-acl-id 8daca77a-4980-4d33-8f3e-7038797be8f9`
- `ibmcloud is subnet-update ec8bb350-d802-4f1b-b362-b848abd5bb65 --public-gateway-id 8daca77a-4980-4d33-8f3e-7038797be8f9`
- `ibmcloud is subnet-update ec8bb350-d802-4f1b-b362-b848abd5bb65 --name my-subnet --json`

#### Command options
{: #command-options-subnet-update}

- **SUBNET**: ID of the subnet.
- **--name**: New name of the subnet.
- **--network-acl-id**: The ID of the network ACL.
- **--public-gateway-id**: The ID of the public gateway.
- **--json**: Format output in JSON.

---

### ibmcloud is subnets
{: #subnets}

List all subnets.

```
ibmcloud is subnets [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-subnets}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is subnet-public-gateway
{: #subnet-public-gateway}

View details of public gateway that is attached to the subnet.

```
ibmcloud is subnet-public-gateway SUBNET [--json]
```

#### Command options
{: #command-options-subnet-public-gateway}

- **SUBNET**: ID of the subnet.
- **--json**: Format output in JSON.

---

### ibmcloud is subnet-public-gateway-detach
{: #subnet-public-gateway-detach}

Detach the public gateway from a subnet.

```
ibmcloud is subnet-public-gateway-detach SUBNET
```

#### Command options
{: #command-options-subnet-public-gateway-detach}

- **SUBNET**: ID of the subnet.

---

## VPCs
{: #vpcs-cli-ref}

### ibmcloud is vpc
{: #vpc}

View details of a VPC.

```
ibmcloud is vpc VPC [--show-attached] [--json]
```

#### Command options
{: #command-options-vpc}

- **VPC**: ID of the VPC.
- **--show-attached**: View details of resources (Subnets, VPC Routes, and Address Prefix) that are attached to this VPC.
- **--json**: Format output in JSON.

---

### ibmcloud is vpc-address-prefix
{: #vpc-address-prefix}

View details of a VPC address prefix.

```
ibmcloud is vpc-address-prefix VPC PREFIX [--json]
```

#### Command options
{: #command-options-vpc-address-prefix}

- **VPC**: ID of the VPC.
- **PREFIX**: ID of the VPC address prefix.
- **--json**: Format output in JSON.

---

### ibmcloud is vpc-address-prefix-create
{: #vpc-address-prefix-create}

Create an address prefix.

```
ibmcloud is vpc-address-prefix-create PREFIX_NAME VPC ZONE_NAME CIDR [--default false | true] [--json]
```

#### Command example
{: #command-example-vpc-address-prefix-create}

- `ibmcloud is vpc-address-prefix-create my-prefix 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 us-south-2 10.0.0.0/24 --default true --json`

#### Command options
{: #command-options-vpc-address-prefix-create}

- **PREFIX_NAME**: Name of the VPC address prefix.
- **VPC**: ID of the VPC.
- **ZONE_NAME**: Name of the zone.
- **CIDR**: The CIDR block for this prefix.
- **--default**: This flag indicates whether this prefix is the default prefix for this zone in this VPC. Enumeration type: **true**, **false**. If unspecified, the default is false.
- **--json**: Format output in JSON.

---

### ibmcloud is vpc-address-prefix-delete
{: #vpc-address-prefix-delete}

Delete an address prefix.

```
ibmcloud is vpc-address-prefix-delete VPC PREFIX [-f, --force]
```

#### Command options
{: #command-options-vpc-address-prefix-delete}

- **VPC**: ID of the VPC.
- **PREFIX**: ID of the VPC address prefix.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is vpc-address-prefix-update
{: #vpc-address-prefix-update}

Update an address prefix.

```
ibmcloud is vpc-address-prefix-update VPC PREFIX [--name NEW_NAME] [--default false | true] [--json]
```

#### Command example
{: #command-example-vpc-address-prefix-update}

- `ibmcloud is vpc-address-prefix-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 fee82deba12e4c0fb69c3b09d1f12345 --name my-prefix --default false --json`

#### Command options
{: #command-options-vpc-address-prefix-update}

- **VPC**: ID of the VPC.
- **PREFIX**: ID of the VPC address prefix.
- **--name**: New name of the address prefix.
- **--default**: This flag indicates whether this prefix is the default prefix for this zone in this VPC. Enumeration type: **true**, **false**. If unspecified, the default is false.
- **--json**: Format output in JSON.

---

### ibmcloud is vpc-address-prefixes
{: #vpc-address-prefixes}

List all address prefixes.

```
ibmcloud is vpc-address-prefixes VPC [--json]
```

#### Command options
{: #command-options-vpc-address-prefixes}

- **VPC**: ID of the VPC.
- **--json**: Format output in JSON.

---

### ibmcloud is vpc-create
{: #vpc-create}

Create a VPC.

```
ibmcloud is vpc-create VPC_NAME [--classic-access] [--address-prefix-management auto | manual] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-vpc-create}

- `ibmcloud is vpc-create my-vpc --classic-access`
- `ibmcloud is vpc-create my-vpc --address-prefix-management auto`
- `ibmcloud is vpc-create my-vpc --resource-group-id fee82deba12e4c0fb69c3b09d1f12345`
- `ibmcloud is vpc-create my-vpc --resource-group-name Default --json`

#### Command options
{: #command-options-vpc-create}

- **VPC_NAME**: Name of the VPC.
- **--classic-access**: This flag indicates whether the VPC should be connected to Classic Infrastructure. The default value is false.
- **--address-prefix-management**: This flag indicates whether a default address prefix needs to be automatically created for each zone in this VPC. If 'manual', this VPC is created with no default address prefixes. Enumeration type: **auto**, **manual**. (default: "auto").
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is vpc-default-security-group
{: #vpc-default-security-group}

View details of the default security group of a VPC.

```
ibmcloud is vpc-default-security-group VPC [--json]
```

#### Command options
{: #command-options-vpc-default-security-group}

- **VPC**: ID of the VPC.
- **--json**: Format output in JSON.

---

### ibmcloud is vpc-delete
{: #vpc-delete}

Delete a VPC.

```
ibmcloud is vpc-delete VPC [-f, --force]
```

#### Command options
{: #command-options-vpc-delete}

- **VPC**: ID of the VPC.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is vpc-route
{: #vpc-route}

View details of a VPC route.

```
ibmcloud is vpc-route VPC ROUTE [--json]
```

#### Command options
{: #command-options-vpc-route}

- **VPC**: ID of the VPC.
- **ROUTE**: ID of the VPC route.
- **--json**: Format output in JSON.

---

### ibmcloud is vpc-route-create
{: #vpc-route-create}

Create a VPC route.

```
ibmcloud is vpc-route-create ROUTE_NAME VPC --zone ZONE_NAME --destination DESTINATION_CIDR --next-hop-ip NEXT_HOP_IP [--json]
```

#### Command example
{: #command-example-vpc-route-create}

- `ibmcloud is vpc-route-create my-vpc-route 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --zone us-south-1 --destination  10.2.2.0/24 --next-hop-ip 10.0.0.2 --json`

#### Command options
{: #command-options-vpc-route-create}

- **ROUTE_NAME**: Name of the VPC route.
- **VPC**: ID of the VPC.
- **--zone**: Name of the zone.
- **--destination**: The destination CIDR of the route.
- **--next-hop-ip**: The IP address of the next hop to which to route packets.
- **--json**: Format output in JSON.

---

### ibmcloud is vpc-route-update
{: #vpc-route-update}

Update a VPC route.

```
ibmcloud is vpc-route-update VPC ROUTE --name NEW_NAME [--json]
```

#### Command example
{: #command-example-vpc-route-update}

- `ibmcloud is vpc-route-update 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1d456 --name my-vpc-route --json`

#### Command options
{: #command-options-vpc-route-update}

- **VPC**: ID of the VPC.
- **ROUTE**: ID of the VPC route.
- **--name**: New name of the route.
- **--json**: Format output in JSON.

---

### ibmcloud is vpc-route-delete
{: #vpc-route-delete}

Delete a VPC route.

```
ibmcloud is vpc-route-delete VPC ROUTE [-f, --force]
```

#### Command options
{: #command-options-vpc-route-delete}

- **VPC**: ID of the VPC.
- **ROUTE**: ID of the VPC route.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is vpc-routes
{: #vpc-routes}

List all VPC routes.

```
ibmcloud is vpc-routes VPC [--json]
```

#### Command options
{: #command-options-vpc-routes}

- **VPC**: ID of the VPC.
- **--json**: Format output in JSON.

---

### ibmcloud is vpc-update
{: #vpc-update}

Update a VPC.

```
ibmcloud is vpc-update VPC --name NEW_NAME [--json]
```

#### Command examples
{: #command-examples-vpc-update}

- `ibmcloud is vpc-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-vpc`

#### Command options
{: #command-options-vpc-update}

- **VPC**: ID of the VPC.
- **--name**: New name of the VPC.
- **--json**: Format output in JSON.

---

### ibmcloud is vpcs
{: #vpcs}

List all VPCs.

```
ibmcloud is vpcs [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--classic-access true | false] [--json]
```

---

#### Command options
{: #command-options-vpcs}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--classic-access**: This flag lists VPCs that have classic access enabled. Enumeration type: **true**, **false**. If unspecified, it returns all VPCs with and without classic access enabled.
- **--json**: Format output in JSON.


## VPNs
{: #vpn-clis}

This section gives details about the CLI commands available for working with VPN, including IKE and IPsec policies.

### ibmcloud is ike-policies
{: #ike-policies}

List all IKE policies.

```
ibmcloud is ike-policies [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-ike-policies}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is ike-policy
{: #ike-policy}

View details of an IKE policy.

```
ibmcloud is ike-policy IKE_POLICY_ID [--json]
```

#### Command options
{: #command-options-ike-policy}

- **IKE_POLICY_ID**: ID of the IKE policy.
- **--json**: Format output in JSON.

---

### ibmcloud is ike-policy-connections
{: #ike-policy-connections}

List all connections that use the IKE policy.

```
ibmcloud is ike-policy-connections IKE_POLICY_ID [--json]
```

#### Command options
{: #command-options-ike-policy-connections}

- **IKE_POLICY_ID**: ID of the IKE policy.
- **--json**: Format output in JSON.

---

### ibmcloud is ike-policy-create
{: #ike-policy-create}

Create an IKE policy.

```
ibmcloud is ike-policy-create IKE_POLICY_NAME AUTHENTICATION_ALGORITHM DH_GROUP ENCRYPTION_ALGORITHM IKE_VERSION [--key-lifetime KEY_LIFETIME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-ike-policy-create}

- `ibmcloud is ike-policy-create my-ike-policy md5 2 aes128 2`
- `ibmcloud is ike-policy-create my-ike-policy md5 2 aes128 2 --key-lifetime 28000`
- `ibmcloud is ike-policy-create my-ike-policy md5 2 aes128 2 --resource-group-name Default`
- `ibmcloud is ike-policy-create my-ike-policy md5 2 aes128 2 --resource-group-id fee82deba12e4c0fb69c3b09d1f12345 --json`

#### Command options
{: #command-options-ike-policy-create}

- **IKE_POLICY_NAME**: Name of the IKE policy.
- **AUTHENTICATION_ALGORITHM**: The authentication algorithm. Enumeration type: **md5**, **sha1**, **sha256**.
- **DH_GROUP**: The Diffie-Hellman group. Enumeration type: **2**, **5**, **14**.
- **ENCRYPTION_ALGORITHM**: The encryption algorithm. Enumeration type: **triple_des**, **aes128**, **aes256**.
- **IKE_VERSION**: The IKE protocol version. Enumeration type: **1**, **2**.
- **--key-lifetime**: The key lifetime in seconds. Maximum: 86400, Minimum: 1800 (default: 28800).
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is ike-policy-delete
{: #ike-policy-delete}

Delete an IKE policy.

```
ibmcloud is ike-policy-delete IKE_POLICY_ID [-f, --force]
```

#### Command options
{: #command-options-ike-policy-delete}

- **IKE_POLICY_ID**: ID of the IKE policy.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is ike-policy-update
{: #ike-policy-update}

Update an IKE policy.

```
ibmcloud is ike-policy-update IKE_POLICY_ID [--name NEW_NAME] [--authentication-algorithm md5 | sha1 | sha256] [--dh-group 2 | 5 | 14] [--encryption-algorithm triple_des | aes128 | aes256] [--ike-version 1 | 2] [--key-lifetime KEY_LIFETIME] [--json]
```

#### Command examples
{: #command-examples-ike-policy-update}

- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --name my-ike-policy`
- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --authentication-algorithm md5`
- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --dh-group 2`
- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --encryption-algorithm aes128`
- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --ike-version 2`
- `ibmcloud is ike-policy-update fee82deba12e4c0fb69c3b09d1f12345 --key-lifetime 28000 --json`

#### Command options
{: #command-options-ike-policy-update}

- **IKE_POLICY_ID**: ID of the IKE policy.
- **--name**: New name of the IKE policy.
- **--authentication-algorithm**: The authentication algorithm. Enumeration type: **md5**, **sha1**, **sha256**.
- **--dh-group**: The Diffie-Hellman group. Enumeration type: **2**, **5**, **14**.
- **--encryption-algorithm**: The encryption algorithm. Enumeration type: **triple_des**, **aes128**, **aes256**.
- **--ike-version**: The IKE protocol version. Enumeration type: **1**, **2**.
- **--key-lifetime**: The key lifetime in seconds. Maximum: 86400, Minimum: 1800.
- **--json**: Format output in JSON.

---

### ibmcloud is ipsec-policies
{: #ipsec-policies}

List all IPsec policies.

```
ibmcloud is ipsec-policies [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-ipsec-policies}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is ipsec-policy
{: #ipsec-policy}

View details of an IPsec policy.

```
ibmcloud is ipsec-policy IPSEC_POLICY_ID [--json]
```

#### Command options
{: #command-options-ipsec-policy}

- **IPSEC_POLICY_ID**: ID of the IPsec policy.
- **--json**: Format output in JSON.

---

### ibmcloud is ipsec-policy-connections
{: #ipsec-policy-connections}

List all connections that use the IPsec policy.

```
ibmcloud is ipsec-policy-connections IPSEC_POLICY_ID [--json]
```

#### Command options
{: #command-options-ipsec-policy-connections}

- **IPSEC_POLICY_ID**: ID of the IPsec policy.
- **--json**: Format output in JSON.

---

### ibmcloud is ipsec-policy-create
{: #ipsec-policy-create}

Create an IPsec policy.

```
ibmcloud is ipsec-policy-create IPSEC_POLICY_NAME AUTHENTICATION_ALGORITHM ENCRYPTION_ALGORITHM PFS [--key-lifetime KEY_LIFETIME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-ipsec-policy-create}

- `ibmcloud is ipsec-policy-create my-ipsec-policy md5 aes128 group_2`
- `ibmcloud is ipsec-policy-create my-ipsec-policy md5 aes128 group_2 --key-lifetime 3600`
- `ibmcloud is ipsec-policy-create my-ipsec-policy md5 aes128 group_2 --resource-group-name Default`
- `ibmcloud is ipsec-policy-create my-ipsec-policy md5 aes128 group_2 --resource-group-id fee82deba12e4c0fb69c3b09d1f12345 --json`

#### Command options
{: #command-options-ipsec-policy-create}

- **IPSEC_POLICY_NAME**: Name of the IPsec policy.
- **AUTHENTICATION_ALGORITHM**: The authentication algorithm. Enumeration type: **md5**, **sha1**, **sha256**.
- **ENCRYPTION_ALGORITHM**: The encryption algorithm. Enumeration type: **triple_des**, **aes128**, **aes256**.
- **PFS**: The Diffie-Hellman group. Enumeration type: **disabled**, **group_2**, **group_5**, **group_14**.
- **--key-lifetime**: The key lifetime in seconds. Maximum: 86400, Minimum: 1800 (default: 3600).
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is ipsec-policy-delete
{: #ipsec-policy-delete}

Delete an IPsec policy.

```
ibmcloud is ipsec-policy-delete IPSEC_POLICY_ID [-f, --force]
```

#### Command options
{: #command-options-ipsec-policy-delete}

- **IPSEC_POLICY_ID**: ID of the IPsec policy.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is ipsec-policy-update
{: #ipsec-policy-update}

Update an IPsec policy.

```
ibmcloud is ipsec-policy-update IPSEC_POLICY_ID [--name NEW_NAME] [--authentication-algorithm md5 | sha1 | sha256] [--pfs disabled | group_2 | group_5 | group_14] [--encryption-algorithm triple_des | aes128 | aes256] [--key-lifetime KEY_LIFETIME] [--json]
```

#### Command examples
{: #command-examples-ipsec-policy-update}

- `ibmcloud is ipsec-policy-update fee82deba12e4c0fb69c3b09d1f12345 --name my-ipsec-policy`
- `ibmcloud is ipsec-policy-update fee82deba12e4c0fb69c3b09d1f12345 --authentication-algorithm md5`
- `ibmcloud is ipsec-policy-update fee82deba12e4c0fb69c3b09d1f12345 --pfs group_2`
- `ibmcloud is ipsec-policy-update fee82deba12e4c0fb69c3b09d1f12345 --encryption-algorithm aes128`
- `ibmcloud is ipsec-policy-update fee82deba12e4c0fb69c3b09d1f12345 --key-lifetime 3600 --json`

#### Command options
{: #command-options-ipsec-policy-update}

- **IPSEC_POLICY_ID**: ID of the IPsec policy.
- **--name**: New name of the IPsec policy.
- **--authentication-algorithm**: The authentication algorithm. Enumeration type: **md5**, **sha1**, **sha256**.
- **--pfs**: Perfect Forward Secrecy. Enumeration type: **disabled**, **group_2**, **group_5**, **group_14**.
- **--encryption-algorithm**: The encryption algorithm. Enumeration type: **triple_des**, **aes128**, **aes256**.
- **--key-lifetime**: The key lifetime in seconds. Maximum: 86400, Minimum: 1800.
- **--json**: Format output in JSON.

---

### ibmcloud is vpn-gateway
{: #vpn-gateway}

View details of a VPN gateway.

```
ibmcloud is vpn-gateway VPN_GATEWAY_ID [--json]
```

#### Command options
{: #command-options-vpn-gateway}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **--json**: Format output in JSON.

---

### ibmcloud is vpn-gateway-connection
{: #vpn-gateway-connection}

View details of a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection VPN_GATEWAY_ID CONNECTION_ID [--json]
```

#### Command options
{: #command-options-vpn-gateway-connection}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **CONNECTION_ID**: ID of the VPN connection.
- **--json**: Format output in JSON.

---

### ibmcloud is vpn-gateway-connection-create
{: #vpn-gateway-connection-create}

Create a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-create CONNECTION_NAME VPN_GATEWAY_ID PEER_ADDRESS PRESHARED_KEY --local-cidr CIDR1 --local-cidr CIDR2 ... --peer-cidr CIDR1 --peer-cidr CIDR2 ... [--admin-state-up true | false] [--dead-peer-detection-action restart | clear | hold | none] [--dead-peer-detection-interval INTERVAL] [--dead-peer-detection-timeout TIMEOUT] [--ike-policy IKE_POLICY_ID] [--ipsec-policy IPSEC_POLICY_ID] [--json]
```

#### Command examples
{: #command-examples-vpn-gateway-connection-create}

- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --admin-state-up true`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --dead-peer-detection-action clear --dead-peer-detection-interval 33 --dead-peer-detection-timeout 100`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --ipsec-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 10.240.0.0/24 --peer-cidr 192.168.1.0/24 --ike-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is vpn-gateway-connection-create my-connection fee82deba12e4c0fb69c3b09d1f12345 169.21.50.5 lkj14b1oi0alcniejkso --local-cidr 16.3.4.5 --local-cidr 12.3.4.5 --peer-cidr 16.3.4.5 --peer-cidr 12.3.4.5  --json`

#### Command options
{: #command-options-vpn-gateway-connection-create}

- **CONNECTION_NAME**: Name of the connection.
- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **PEER_ADDRESS**: The IP address of the peer VPN gateway.
- **PRESHARED_KEY**: The preshared key.
- **--admin-state-up**: If set to false, the VPN gateway connection is shut down. Enumeration type: **true**, **false**. (default: "true").
- **--dead-peer-detection-action**: Dead Peer Detection actions. Enumeration type: **restart**, **clear**, **hold**, **none**. (default: "restart").
- **--dead-peer-detection-interval**: Dead Peer Detection interval in seconds (default: 2).
- **--dead-peer-detection-timeout**: Dead Peer Detection timeout in seconds (default: 10).
- **--ike-policy**: ID of the IKE policy.
- **--ipsec-policy**: ID of the IPsec policy.
- **--local-cidr**: Local CIDR for the resource.
- **--peer-cidr**: Peer CIDRs for the resource.
- **--json**: Format output in JSON.

---

### ibmcloud is vpn-gateway-connection-delete
{: #vpn-gateway-connection-delete}

Delete a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-delete VPN_GATEWAY_ID CONNECTION_ID [-f, --force]
```

#### Command options
{: #command-options-vpn-gateway-connection-delete}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **CONNECTION_ID**: ID of the VPN connection.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is vpn-gateway-connection-local-cidr-add
{: #vpn-gateway-connection-local-cidr-add}

Add a local CIDR to a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-local-cidr-add VPN_GATEWAY_ID CONNECTION_ID PREFIX_ADDRESS PREFIX_LENGTH [--json]
```

#### Command options
{: #command-options-vpn-gateway-connection-local-cidr-add}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **CONNECTION_ID**: ID of the VPN connection.
- **PREFIX_ADDRESS**: The prefix address part of the CIDR.
- **PREFIX_LENGTH**: The prefix length part of the CIDR.
- **--json**: Format output in JSON.

---

### ibmcloud is vpn-gateway-connection-local-cidr-delete
{: #vpn-gateway-connection-local-cidr-delete}

Remove a local CIDR from the VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-local-cidr-delete VPN_GATEWAY_ID CONNECTION_ID PREFIX_ADDRESS PREFIX_LENGTH [-f, --force]
```

#### Command options
{: #command-options-vpn-gateway-connection-local-cidr-delete}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **CONNECTION_ID**: ID of the VPN connection.
- **PREFIX_ADDRESS**: The prefix address part of the CIDR.
- **PREFIX_LENGTH**: The prefix length part of the CIDR.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is vpn-gateway-connection-peer-cidr-add
{: #vpn-gateway-connection-peer-cidr-add}

Add a peer CIDR to a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-peer-cidr-add VPN_GATEWAY_ID CONNECTION_ID PREFIX_ADDRESS PREFIX_LENGTH [--json]
```

#### Command options
{: #command-options-vpn-gateway-connection-peer-cidr-add}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **CONNECTION_ID**: ID of the VPN connection.
- **PREFIX_ADDRESS**: The prefix address part of the CIDR.
- **PREFIX_LENGTH**: The prefix length part of the CIDR.
- **--json**: Format output in JSON.

---

### ibmcloud is vpn-gateway-connection-peer-cidr-delete
{: #vpn-gateway-connection-peer-cidr-delete}

Remove a peer CIDR from the VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-peer-cidr-delete VPN_GATEWAY_ID CONNECTION_ID PREFIX_ADDRESS PREFIX_LENGTH [-f, --force]
```

#### Command options
{: #command-options-vpn-gateway-connection-peer-cidr-delete}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **CONNECTION_ID**: ID of the VPN connection.
- **PREFIX_ADDRESS**: The prefix address part of the CIDR.
- **PREFIX_LENGTH**: The prefix length part of the CIDR.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is vpn-gateway-connection-update
{: #vpn-gateway-connection-update}

Update a VPN gateway connection.

```
ibmcloud is vpn-gateway-connection-update VPN_GATEWAY_ID CONNECTION_ID [--admin-state-up true | false] [--dead-peer-detection-action restart | clear | hold | none] [--dead-peer-detection-interval INTERVAL] [--dead-peer-detection-timeout TIMEOUT] [--ike-policy IKE_POLICY_ID] [--ipsec-policy IPSEC_POLICY_ID] [--peer-address ADDRESS] [--psk PSK] [--name NEW_NAME] [--json]
```

#### Command example
{: #command-example-vpn-gateway-connection-update}

- `ibmcloud is vpn-gateway-connection-update fee82deba12e4c0fb69c3b09d1f12345 gfe82deba12e4c0fb69c3b09d1f23456 --admin-state-up true --dead-peer-detection-action clear --dead-peer-detection-interval 33 --dead-peer-detection-timeout 100  --ipsec-policy 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479  --ipsec-policy 05251a2e-d6c5-42b4-97b0-b5f8e8d1f445 --peer-address 234.3.4.5 -psk rweirjgiort --name my-new-connection --json`

#### Command options
{: #command-options-vpn-gateway-connection-update}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **CONNECTION_ID**: ID of the VPN connection.
- **--admin-state-up**: If set to false, the VPN gateway connection is shut down. Enumeration type: **true**, **false**.
- **--dead-peer-detection-action**: Dead Peer Detection actions. Enumeration type: **restart**, **clear**, **hold**, **none**.
- **--dead-peer-detection-interval**: Dead Peer Detection interval in seconds.
- **--dead-peer-detection-timeout**: Dead Peer Detection timeout in seconds.
- **--ike-policy**: ID of the IKE policy.
- **--ipsec-policy**: ID of the IPsec policy.
- **--peer-address**: The IP address of the peer VPN gateway.
- **--psk**: The preshared key.
- **--name**: New name of the connection.
- **--json**: Format output in JSON.

---

### ibmcloud is vpn-gateway-connections
{: #vpn-gateway-connections}

List all VPN gateway connections.

```
ibmcloud is vpn-gateway-connections VPN_GATEWAY_ID [--json]
```

#### Command options
{: #command-options-vpn-gateway-connections}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **--json**: Format output in JSON.

---

### ibmcloud is vpn-gateway-create
{: #vpn-gateway-create}

Create a VPN gateway.

```
ibmcloud is vpn-gateway-create VPN_GATEWAY_NAME SUBNET [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-vpn-gateway-create}

- `ibmcloud is vpn-gateway-create my-vpc-gateway fee82deba12e4c0fb69c3b09d1f12345`
- `ibmcloud is vpn-gateway-create my-vpc-gateway fee82deba12e4c0fb69c3b09d1f12345 --resource-group-name Default`
- `ibmcloud is vpn-gateway-create my-vpc-gateway fee82deba12e4c0fb69c3b09d1f12345 --resource-group-id fee82deba12e4c0fb69c3b09d1f12345 --json`

#### Command options
{: #command-options-vpn-gateway-create}

- **VPN_GATEWAY_NAME**: Name of the VPN gateway.
- **SUBNET**: ID of the subnet.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is vpn-gateway-delete
{: #vpn-gateway-delete}

Delete a VPN gateway.

```
ibmcloud is vpn-gateway-delete VPN_GATEWAY_ID [-f, --force]
```

#### Command options
{: #command-options-vpn-gateway-delete}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is vpn-gateway-update
{: #vpn-gateway-update}

Update a VPN gateway.

```
ibmcloud is vpn-gateway-update VPN_GATEWAY_ID [--name NEW_NAME] [--json]
```

#### Command example
{: #command-example-vpn-gateway-update}

- `ibmcloud is vpn-gateway-update fee82deba12e4c0fb69c3b09d1f12345 --name my-gateway --json`

#### Command options
{: #command-options-vpn-gateway-update}

- **VPN_GATEWAY_ID**: ID of the VPN gateway.
- **--name**: New name of the VPN gateway.
- **--json**: Format output in JSON.

---

### ibmcloud is vpn-gateways
{: #vpn-gateways}

List all VPN gateways.

```
ibmcloud is vpn-gateways [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-vpn-gateways}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

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
ibmcloud is operating-systems [--json]
```

#### Command options
{: #command-options-operating-systems}

- **--json**: Format output in JSON.

---

### ibmcloud is operating-system
{: #operating-system}

View details of operating system.

```
ibmcloud is operating-system OPERATING_SYSTEM_NAME [--json]
```

#### Command options
{: #command-options-operating-system}

- **OPERATING_SYSTEM_NAME**: Name of the operating system.
- **--json**: Format output in JSON.

---

### ibmcloud is image
{: #image}

View details of an image.

```
ibmcloud is image IMAGE [--json]
```

#### Command options
{: #command-options-image}

- **IMAGE**: ID of the image.
- **--json**: Format output in JSON.

---

### ibmcloud is images
{: #images}

List all images in the region.

```
ibmcloud is images [--visibility public | private] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-images}

- **--visibility**: List images with given visibility. Valid visibility is: public, private.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is image-create
{: #image-create}

Create an image.

```
ibmcloud is image-create IMAGE_NAME --file IMAGE_FILE_LOCATION --os-name OPERATING_SYSTEM_NAME [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-image-create}

- `ibmcloud is image-create My-ubuntu-16-amd64 --file cos://us-south/custom-image-vpc-bucket/customImage-0.vhd --os-name ubuntu-16-amd64`
- `ibmcloud is image-create My-ubuntu-16-amd64 --file cos://us-south/custom-image-vpc-bucket/customImage-0.vhd --os-name ubuntu-16-amd64 --resource-group-id fee82deba12e4c0fb69c3b09d1f12345`
- `ibmcloud is image-create My-ubuntu-16-amd64 --file cos://us-south/custom-image-vpc-bucket/customImage-0.vhd --os-name ubuntu-16-amd64 --resource-group-name Default`
- `ibmcloud is image-create My-ubuntu-16-amd64 --file cos://us-south/custom-image-vpc-bucket/customImage-0.vhd --os-name ubuntu-16-amd64 --json`

#### Command options
{: #command-options-image-create}

- **IMAGE_NAME**: Name of the image.
- **--file**: The Cloud Object Store (COS) location of the image file, for example: 'cos://us-south/custom-image-vpc-bucket/customImage-0.vhd'.
- **--os-name**: The name of the operating system for this image.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is image-update
{: #image-update}

Update an image.

```
ibmcloud is image-update IMAGE --name NEW_NAME [--json]
```

#### Command example
{: #command-example-image-update}

- `ibmcloud is image-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-image`

#### Command options
{: #command-options-image-update}

- **IMAGE**: ID of the image.
- **--name**: New name of the image.
- **--json**: Format output in JSON.

---

### ibmcloud is image-delete
{: #image-delete}

Delete an image.

```
ibmcloud is image-delete IMAGE [-f, --force]
```

#### Command options
{: #command-options-image-delete}

- **IMAGE**: ID of the image.
- **--force, -f**: Force the operation without confirmation.

---

## Instances
{: #instances}

### ibmcloud is instance
{: #instance}

View details of a virtual server instance.

```
ibmcloud is instance INSTANCE [--json]
```

#### Command options
{: #command-options-instance}

- **INSTANCE**: ID of the instance.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-initialization-values
{: #instance-initialization-values}

View initialization details of a virtual instance.

```
ibmcloud is instance-initialization-values INSTANCE [--private-key (KEY | @KEY_FILE)] [--json]
```

#### Command options
{: #command-options-instance-initialization-values}

- **INSTANCE**: ID of the instance.
- **--private-key**: key|@key-file. The private key in PEM format to decrypt Windows administrator default password.
- **--json**: Format output in JSON.

---

### ibmcloud is instances
{: #instances-ibmcloud}

List all virtual server instances.

```
ibmcloud is instances [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-instances}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-create
{: #instance-create}

Create a virtual server instance.

```
ibmcloud is instance-create INSTANCE_NAME VPC ZONE_NAME PROFILE_NAME SUBNET --image-id IMAGE_ID [--boot-volume BOOT_VOLUME_JSON | @BOOT_VOLUME_JSON_FILE] [--volume-attach VOLUME_ATTACH_JSON | @VOLUME_ATTACH_JSON_FILE] [--key-ids IDS] [--user-data DATA] [([--security-group-ids SECURITY_GROUP_IDS] [--ipv4 IPV4_ADDRESS]) | --primary-network-interface PRIMARY_NETWORK_INTERFACE_JSON | @PRIMARY_NETWORK_INTERFACE_JSON_FILE] [--network-interface NETWORK_INTERFACE_JSON | @NETWORK_INTERFACE_JSON_FILE] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json] [-i, --interactive]```

#### Command examples
{: #command-examples-instance-create}

- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8`
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"name":"my-volume-name", "capacity":10, "profile": {"name": "general-purpose"}}}]'`
Create instance with volume attachment.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --key-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
Create instance with multiple SSH keys.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --network-interface '[{"name": "secondary-nic", "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}]'`
Create instance that is attached to secondary network interface.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --primary-network-interface '{"name": "primary-nic", "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "primary_ipv4_address": "10.240.129.10", "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}'`
Create instance with primary network interface configuration in JSON.
- `ibmcloud is instance-create my-instance-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --security-group-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4 10.240.129.10`
Create instance with primary network interface configuration that includes security groups and primary IPv4 address
- `ibmcloud is instance-create --interactive`
Create instance interactively.

#### Command options
{: #command-options-instance-create}

- **INSTANCE_NAME**: Name of the instance.
- **VPC**: ID of the VPC.
- **ZONE_NAME**: Name of the zone.
- **PROFILE_NAME**: Name of the profile.
- **SUBNET**: ID of the subnet.
- **--image-id**: ID of the image.
- **--boot-volume**: BOOT_VOLUME_JSON|@BOOT_VOLUME_JSON_FILE, boot volume attachment in JSON or JSON file.
- **--volume-attach**: VOLUME_ATTACH_JSON|@VOLUME_ATTACH_JSON_FILE, volume attachment in JSON or JSON file, list of volumes.
- **--key-ids**: Comma-separated IDs of SSH keys.
- **--dedicated-host**: The host destination where the instance is placed. And instance profile must be in memory family. (Beta)
- **--dedicated-host-group**: The host group destination where the instance is placed. And instance profile must be in memory family. (Beta)
- **--user-data**: data|@data-file. User data to transfer to the virtual server instance.
- **--security-group-ids**: Comma-separated security group IDs for primary network interface.
- **--ipv4**: Primary IPv4 address for the primary network interface.
- **--primary-network-interface**: PRIMARY_NETWORK_INTERFACE_JSON|@PRIMARY_NETWORK_INTERFACE_JSON_FILE, primary network interface in JSON or JSON file.
- **--network-interface**: NETWORK_INTERFACE_JSON|@NETWORK_INTERFACE_JSON_FILE, network interface attachment in JSON or JSON file.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.
- **--interactive, -i**: Supply the parameters under interactive mode. This option is mutually exclusive with all other arguments and options.

---

### ibmcloud is instance-create-from-template
{: #instance-create-from-template}

Create a virtual server instance from instance template.

```
ibmcloud is instance-create-from-template --template-id TEMPLATE_ID [--name Name] [--profile PROFILE] [--image-id IMAGE_ID] [--zone ZONE] [--boot-volume BOOT_VOLUME_JSON | @BOOT_VOLUME_JSON_FILE] [--volume-attach VOLUME_ATTACH_JSON | @VOLUME_ATTACH_JSON_FILE] [--vpc-id VPC_ID] [(--subnet-id SUBNET_ID [--ipv4 IPV4_ADDRESS] [--security-group-ids SECURITY_GROUP_IDS]) | --primary-network-interface PRIMARY_NETWORK_INTERFACE_JSON | @PRIMARY_NETWORK_INTERFACE_JSON_FILE] [--network-interface NETWORK_INTERFACE_JSON | @NETWORK_INTERFACE_JSON_FILE] [--key-ids IDS] [--user-data DATA] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-instance-create-from-template}

- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d`
- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --resource-group-id 7494aacb866142fba11a88d75cb37bd8 --json`
- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --boot-volume '{"delete_volume_on_instance_delete": false, "name": "my-volume-attachment", "volume": {"name": "myvol2", "profile": {"name": "general-purpose"}}}'`
Create instance from instance template with the boot volume configuration
- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --vpc-id r006-beca4c2f-625f-45de-bd95-c8eb12f6842a --zone us-south-1 --subnet-id 0717-fe2e13d0-9ba8-43bd-ab6b-a1fad51557ac --ipv4 10.240.1.100 --security-group-ids r006-19c2ce0d-d35d-47bc-8147-120edddd3de5`
Create instance from instance template with the primary network interface configuration
- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --vpc-id r006-beca4c2f-625f-45de-bd95-c8eb12f6842a --zone us-south-1 --primary-network-interface '{"name": "primary-nic", "subnet": {"id":"0717-fe2e13d0-9ba8-43bd-ab6b-a1fad51557ac"}, "primary_ipv4_address": "10.240.1.100", "security_groups": [{"id": "r006-19c2ce0d-d35d-47bc-8147-120edddd3de5"}]}'`
Create instance from instance template with the primary network interface configuration in json format
- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --network-interface '[{"name": "secondary-nic", "subnet": {"id":"0737-f6b5a638-1fda-476b-9e2f-7a550fbb62b8"}, "primary_ipv4_address": "10.240.128.100", "security_groups": [{"id": "r006-caba3deb-136b-42c8-831a-1dbcc0f1912e"}]}, {"name": "third-nic", "subnet": {"id":"0737-6b939577-4839-47b0-b42f-a4b29a94c7d9"}, "primary_ipv4_address": "10.240.129.100", "security_groups": [{"id": "r006-caba3deb-136b-42c8-831a-1dbcc0f1912e"}]}]'`
Create instance from instance template with the seconds network interfaces configuration
- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --volume-attach '[{"delete_volume_on_instance_delete": false, "name": "my-volume-attachment1", "volume": {"name": "myvol2", "capacity": 200, "profile": {"name": "general-purpose"}}}, {"delete_volume_on_instance_delete": true, "name": "my-volume-attachment2", "volume": {"name": "myvol3", "capacity": 300, "iops": 1000, "profile": {"name": "custom"}}}]'`
Create instance from instance template with the data volumes configuration
- `ibmcloud is instance-create-from-template --template-id 0737-b7c965c7-2c26-4457-85c4-52e7156f570d --name my-instance --image-id r006-ed3f775f-ad7e-4e37-ae62-7199b4988b00 --profile cx2-2x4 --key-ids r006-02a07b78-6e5f-40a2-86a2-99e01916128c,r006-29e19fb1-e2b9-49d0-ab6e-9702e99f5021 --user-data @/tmp/userdata.sh`
Create instance from instance template with image/profile/key/user data configuration

#### Command options
{: #command-options-instance-create-from-template}

- **--template-id**: ID of the instance template.
- **--name**: Name of the instance.
- **--profile**: Name of the instance profile.
- **--image-id**: ID of the image.
- **--zone**: Name of the zone.
- **--boot-volume**: BOOT_VOLUME_JSON|@BOOT_VOLUME_JSON_FILE, boot volume attachment in JSON or JSON file.
- **--volume-attach**: VOLUME_ATTACH_JSON|@VOLUME_ATTACH_JSON_FILE, volume attachment in JSON or JSON file, list of volumes.
- **--vpc-id**: ID of the VPC.
- **--subnet-id**: ID of the subnet.
- **--ipv4**: Primary IPv4 address for the primary network interface.
- **--security-group-ids**: Comma-separated security group IDs for primary network interface.
- **--primary-network-interface**: PRIMARY_NETWORK_INTERFACE_JSON|@PRIMARY_NETWORK_INTERFACE_JSON_FILE, primary network interface in JSON or JSON file.
- **--network-interface**: NETWORK_INTERFACE_JSON|@NETWORK_INTERFACE_JSON_FILE, network interface attachment in JSON or JSON file.
- **--key-ids**: Comma-separated IDs of SSH keys.
- **--user-data**: data|@data-file. User data to transfer to the virtual server instance.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-delete
{: #instance-delete}

Delete a virtual server instance.

```
ibmcloud is instance-delete INSTANCE [-f, --force]
```

#### Command options
{: #command-options-instance-delete}

- **INSTANCE**: ID of the instance.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is instance-network-interface
{: #instance-network-interface}

View details of a network interface of a virtual server instance.

```
ibmcloud is instance-network-interface INSTANCE NIC [--json]
```

#### Command options
{: #command-options-instance-network-interface}

- **INSTANCE**: ID of the instance.
- **NIC**: ID of the network interface.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-network-interface-create
{: #instance-network-interface-create}

Create a network interface for a virtual server instance.

```
ibmcloud is instance-network-interface-create NIC_NAME INSTANCE SUBNET [--ipv4 IPV4_ADDRESS] [(--security-group-id SECURITY_GROUP_ID1 --security-group-id SECURITY_GROUP_ID2 ...)] [--json]
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
- **--json**: Format output in JSON.

---

### ibmcloud is instance-network-interface-delete
{: #instance-network-interface-delete}

Remove a network interface from a virtual server instance.

```
ibmcloud is instance-network-interface-delete INSTANCE NIC [-f, --force]
```

#### Command options
{: #command-options-instance-network-interface-delete}

- **INSTANCE**: ID of the instance.
- **NIC**: ID of the network interface.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is instance-network-interface-floating-ip
{: #instance-network-interface-floating-ip}

View details of a floating IP that is associated with a network interface.

```
ibmcloud is instance-network-interface-floating-ip INSTANCE NIC FLOATING_IP [--json]
```

#### Command options
{: #command-options-instance-network-interface-floating-ip}

- **INSTANCE**: ID of the instance.
- **NIC**: ID of the network interface.
- **FLOATING_IP**: ID of the floating IP.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-network-interface-floating-ip-add
{: #instance-network-interface-floating-ip-add}

Associate a floating IP with a network interface.

```
ibmcloud is instance-network-interface-floating-ip-add INSTANCE NIC FLOATING_IP [--json]
```

#### Command examples
{: #command-examples-instance-network-interface-floating-ip-add}

- `ibmcloud is instance-network-interface-floating-ip-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is instance-network-interface-floating-ip-add 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --json`

#### Command options
{: #command-options-instance-network-interface-floating-ip-add}

- **INSTANCE**: ID of the instance.
- **NIC**: ID of the network interface.
- **FLOATING_IP**: ID of the floating IP.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-network-interface-floating-ip-remove
{: #instance-network-interface-floating-ip-remove}

Disassociate a floating IP from a network interface.

```
ibmcloud is instance-network-interface-floating-ip-remove INSTANCE NIC FLOATING_IP [-f, --force]
```

#### Command options
{: #command-options-instance-network-interface-floating-ip-remove}

- **INSTANCE**: ID of the instance.
- **NIC**: ID of the network interface.
- **FLOATING_IP**: ID of the floating IP.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is instance-network-interface-floating-ips
{: #instance-network-interface-floating-ips}

List all floating IPs that are associated with a network interface.

```
ibmcloud is instance-network-interface-floating-ips INSTANCE NIC [--json]
```

#### Command options
{: #command-options-instance-network-interface-floating-ips}

- **INSTANCE**: ID of the instance.
- **NIC**: ID of the network interface.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-network-interface-update
{: #instance-network-interface-update}

Update a network interface of a virtual server instance.

```
ibmcloud is instance-network-interface-update INSTANCE NIC --name NEW_NAME [--json]
```

#### Command options
{: #command-options-instance-network-interface-update}

- **INSTANCE**: ID of the instance.
- **NIC**: ID of the network interface.
- **--name**: New name of NIC.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-network-interfaces
{: #instance-network-interfaces}

List all network interfaces of a virtual server instance.

```
ibmcloud is instance-network-interfaces INSTANCE [--json]
```

#### Command options
{: #command-options-instance-network-interfaces}

- **INSTANCE**: ID of the instance.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-profile
{: #instance-profile}

View details of a virtual server instance profile.

```
ibmcloud is instance-profile PROFILE_NAME [--json]
```

#### Command options
{: #command-options-instance-profile}

- **PROFILE_NAME**: Name of the profile.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-profiles
{: #instance-profiles}

List all virtual server instance profiles in the region.

```
ibmcloud is instance-profiles [--json]
```

#### Command options
{: #command-options-instance-profiles}

- **--json**: Format output in JSON.

---

### ibmcloud is instance-reboot
{: #instance-reboot}

Restart the operating system of an instance.

```
ibmcloud is instance-reboot INSTANCE [--no-wait] [-f, --force] [--json]
```

#### Command options
{: #command-options-instance-reboot}

- **INSTANCE**: ID of the instance.
- **--no-wait**: Execute the action immediately and drop all queued actions.
- **--force, -f**: Force the operation without confirmation.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-start
{: #instance-start}

Start a virtual server instance.

```
ibmcloud is instance-start INSTANCE [--json]
```

#### Command options
{: #command-options-instance-start}

- **INSTANCE**: ID of the instance.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-stop
{: #instance-stop}

Stop a virtual server instance.

- When you stop an instance and restart it, a new private IP address is assigned if the instance wasn't created with a static IP address. The primary_ipv4_address attribute wasn't set when the instance was created by using the CLI or API). For more information about setting a static IP address, see primary_network_interface in the [API reference](https://{DomainName}/apidocs/vpc#create-an-instance){: new_window}.
-{:tip}

```
ibmcloud is instance-stop INSTANCE [--no-wait] [-f, --force] [--json]
```

#### Command options
{: #command-options-instance-stop}

- **INSTANCE**: ID of the instance.
- **--no-wait**: Execute the action immediately and drop all queued actions.
- **--force, -f**: Force the operation without confirmation.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-update
{: #instance-update}

Update a virtual server instance.

```
ibmcloud is instance-update INSTANCE --name NEW_NAME [--json]
```

#### Command examples
{: #command-examples-instance-update}

- `ibmcloud is instance-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-instance`
- `ibmcloud is instance-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name my-instance --json`

#### Command options
{: #command-options-instance-update}

- **INSTANCE**: ID of the instance.
- **--name**: New name of the virtual server instance.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-volume-attachment
{: #instance-volume-attachment}

View details of a volume attachment.

```
ibmcloud is instance-volume-attachment INSTANCE VOLUME_ATTACHMENT [--json]
```

#### Command options
{: #command-options-instance-volume-attachment}

- **INSTANCE**: ID of the instance.
- **VOLUME_ATTACHMENT**: ID of the volume attachment.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-volume-attachments
{: #instance-volume-attachments}

List all volume attachments of an instance.

```
ibmcloud is instance-volume-attachments INSTANCE [--json]
```

#### Command options
{: #command-options-instance-volume-attachments}

- **INSTANCE**: ID of the instance.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-volume-attachment-add
{: #instance-volume-attachment-add}

Create a volume attachment, connecting a volume to an instance.

```
ibmcloud is instance-volume-attachment-add NAME INSTANCE VOLUME [--auto-delete false | true] [--json]
```

#### Command examples
{: #command-examples-instance-volume-attachment-add}

- `ibmcloud is instance-volume-attachment-add data-vol-name 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 1a6b7274-678d-4dfb-8981-c71dd9d4daa5`
- `ibmcloud is instance-volume-attachment-add data-vol-name 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 --auto-delete true`
- `ibmcloud is instance-volume-attachment-add data-vol-name 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 --auto-delete true --json`

#### Command options
{: #command-options-instance-volume-attachment-add}

- **NAME**: Name of the volume attachment.
- **INSTANCE**: ID of the instance.
- **VOLUME**: ID of the volume.
- **--auto-delete**: The attached volume is deleted when you delete the instance. Enumeration type: **false**, **true**. (default: "false").
- **--json**: Format output in JSON.

---

### ibmcloud is instance-volume-attachment-detach
{: #instance-volume-attachment-detach}

Delete a volume attachment, detaching a volume from an instance.

```
ibmcloud is instance-volume-attachment-detach INSTANCE VOLUME_ATTACHMENT [-f, --force]
```

#### Command options
{: #command-options-instance-volume-attachment-detach}

- **INSTANCE**: ID of the instance.
- **VOLUME_ATTACHMENT**: ID of the volume attachment.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is instance-volume-attachment-update
{: #instance-volume-attachment-update}

Update a volume attachment.

```
ibmcloud is instance-volume-attachment-update INSTANCE VOLUME_ATTACHMENT [--name NEW_NAME] [--auto-delete true | false] [--json]
```

#### Command examples
{: #command-examples-instance-volume-attachment-update}

- `ibmcloud is instance-volume-attachment-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 --name name2`
- `ibmcloud is instance-volume-attachment-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 --auto-delete true`
- `ibmcloud is instance-volume-attachment-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 1a6b7274-678d-4dfb-8981-c71dd9d4daa5 --name name2 --auto-delete true --json`

#### Command options
{: #command-options-instance-volume-attachment-update}

- **INSTANCE**: ID of the instance.
- **VOLUME_ATTACHMENT**: ID of the volume attachment.
- **--name**: New name of the volume.
- **--auto-delete**: The attached volume is deleted when you delete the instance. Enumeration type: **true**, **false**.
- **--json**: Format output in JSON.

---

## Keys
{: #keys}

### ibmcloud is key
{: #key}

View details of a key.

```
ibmcloud is key KEY [--json]
```

#### Command options
{: #command-options-key}

- **KEY**: ID of the key.
- **--json**: Format output in JSON.

---

### ibmcloud is key-create
{: #key-create}

Import an RSA public key.

```
ibmcloud is key-create KEY_NAME (KEY | @KEY_FILE) [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-key-create}

- `ibmcloud is key-create my-key "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABAQDL9osaBrUD8uCBzIJo5YBvX8wtGrE+kcC7YZtID/nNYrjeCB26eFASHia5tmqmuCo434UygGSd5qj3t/3v/a7NZoMr/0+qspQF+dUVIl+xIsKTWYQ+gtYbJlvW+FIlNTOA4vbOXLg+nGGUCoaV79azmny4mYJbbo15i+Q3CI+w9bwOAwzqeGKaeOjpo5hdDcFW0QLDxKmQHKMLX8slsx3kB9I5wPe8C/ZBBDBBkZKK2y3RJBjaKxi0beFueo6ngUKOLooReefiBGpdoOJIi6Gf7vRduoBTmbyVvSv08wcrANtYSzGwDpqrEshEafv8bKo42MYHsPT2OwAbsFyqWQj5 test@example"`
- `ibmcloud is key-create my-key @/tmp/my_id_rsa.pub`
- `ibmcloud is key-create my-key @/tmp/my_id_rsa.pub --json`

#### Command options
{: #command-options-key-create}

- **KEY_NAME**: Name of the key.
- **KEY**: key|@key-file. The public SSH key to import into the system.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is key-delete
{: #key-delete}

Delete a key.

```
ibmcloud is key-delete KEY [-f, --force]
```

#### Command options
{: #command-options-key-delete}

- **KEY**: ID of the key.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is key-update
{: #key-update}

Update the name of a key.

```
ibmcloud is key-update KEY --name NEW_NAME [--json]
```

#### Command examples
{: #command-examples-key-update}

- `ibmcloud is key-update e9e7655e-0000-0000-0000-0000001a957a  --name my-new-name`
- `ibmcloud is key-update e9e7655e-0000-0000-0000-0000001a957a  --name my-new-name --json`

#### Command options
{: #command-options-key-update}

- **KEY**: ID of the key.
- **--name**: New name for the key.
- **--json**: Format output in JSON.

---

### ibmcloud is keys
{: #keys-ibmcloud}

List all keys.

```
ibmcloud is keys [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-keys}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

## Dedicated hosts (Beta)
{: #dedicated-hosts}

### ibmcloud is dedicated-host-profiles
{: #dedicated-host-profiles}

List all host profiles in the region.

```
ibmcloud is dedicated-host-profiles [--json]
```

#### Command options
{: #command-options-dedicated-host-profiles}

- **--json**: Format output in JSON.

---

### ibmcloud is dedicated-host-profile
{: #dedicated-host-profile}

View details of a host profile.

```
ibmcloud is dedicated-host-profile PROFILE_NAME [--json]
```

#### Command options
{: #command-options-dedicated-host-profile}

- **PROFILE_NAME**: Name of the profile.
- **--json**: Format output in JSON.

---

### ibmcloud is dedicated-host-groups
{: #dedicated-host-groups}

List all host groups.

```
ibmcloud is dedicated-host-groups [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-dedicated-host-groups}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is dedicated-host-group
{: #dedicated-host-group}

View details of a host group.

```
ibmcloud is dedicated-host-group HOST_GROUP [--json]
```

#### Command options
{: #command-options-dedicated-host-group}

- **HOST_GROUP**: ID of the host group.
- **--json**: Format output in JSON.

---

### ibmcloud is dedicated-host-group-create
{: #dedicated-host-group-create}

Create a host group.

```
ibmcloud is dedicated-host-group-create --zone ZONE_NAME [--name NAME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-dedicated-host-group-create}

- `ibmcloud is dedicated-host-group-create --zone us-south-1 --name my-host-group`
- `ibmcloud is dedicated-host-group-create --zone us-south-1 --name my-host-group --json`

#### Command options
{: #command-options-dedicated-host-group-create}

- **--zone**: Name of the zone.
- **--name**: New name for the host group.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is dedicated-host-group-update
{: #dedicated-host-group-update}

Update a host group.

```
ibmcloud is dedicated-host-group-update HOST_GROUP --name NEW_NAME [--json]
```

#### Command examples
{: #command-examples-dedicated-host-group-update}

- `ibmcloud is dedicated-host-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name-host-group`
- `ibmcloud is dedicated-host-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name-host-group --json`

#### Command options
{: #command-options-dedicated-host-group-update}

- **HOST_GROUP**: ID of the host group.
- **--name**: New name of the host group.
- **--json**: Format output in JSON.

---

### ibmcloud is dedicated-host-group-delete
{: #dedicated-host-group-delete}

Delete a host group.

```
ibmcloud is dedicated-host-group-delete HOST_GROUP [-f, --force]
```

#### Command options
{: #command-options-dedicated-host-group-delete}

- **HOST_GROUP**: ID of the host group.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is dedicated-hosts
{: #dedicated-hosts}

List all hosts.

```
ibmcloud is dedicated-hosts [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-dedicated-hosts}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is dedicated-host
{: #dedicated-host}

View details of a host.

```
ibmcloud is dedicated-host HOST [--json]
```

#### Command options
{: #command-options-dedicated-host}

- **HOST**: ID of the host.
- **--json**: Format output in JSON.

---

### ibmcloud is dedicated-host-create
{: #dedicated-host-create}

Create a host.

```
ibmcloud is dedicated-host-create --profile PROFILE --host-group-id HOST_GROUP_ID [--enabled true | false] [--name NAME] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-dedicated-host-create}

- `ibmcloud is dedicated-host-create --profile dh2-56x344 --host-group-id 74213016-f179-4055-b161-46fd42a9d98a --name my-host`
- `ibmcloud is dedicated-host-create --profile dh2-56x344 --host-group-id 74213016-f179-4055-b161-46fd42a9d98a --name my-host --enabled false`
- `ibmcloud is dedicated-host-create --profile dh2-56x344 --host-group-id 74213016-f179-4055-b161-46fd42a9d98a --name my-host --json`

#### Command options
{: #command-options-dedicated-host-create}

- **--profile**: Name of the host profile.
- **--host-group-id**: ID of the host group.
- **--enabled**: Enable or disable the instance allocation in the host.
- **--name**: New name for the host.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is dedicated-host-update
{: #dedicated-host-update}

Update a host.

```
ibmcloud is dedicated-host-update HOST [--name NEW_NAME] [--enabled true | false] [--json]
```

#### Command examples
{: #command-examples-dedicated-host-update}

- `ibmcloud is dedicated-host-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name-host-group`
- `ibmcloud is dedicated-host-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name-host-group --enabled false --json`

#### Command options
{: #command-options-dedicated-host-update}

- **HOST**: ID of the host.
- **--name**: New name of the host.
- **--enabled**: Enable or disable the instance allocation in the host.
- **--json**: Format output in JSON.

---

### ibmcloud is dedicated-host-delete
{: #dedicated-host-delete}

Delete a host.

```
ibmcloud is dedicated-host-delete HOST [-f, --force]
```

#### Command options
{: #command-options-dedicated-host-delete}

- **HOST**: ID of the host.
- **--force, -f**: Force the operation without confirmation.

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
ibmcloud is instance-templates [--json]
```

#### Command options
{: #command-options-instance-templates}

- **--json**: Format output in JSON.

---

### ibmcloud is instance-template
{: #instance-template}

View details of an instance template.

```
ibmcloud is instance-template TEMPLATE_ID [--json]
```

#### Command options
{: #command-options-instance-template}

- **TEMPLATE_ID**: ID of the template.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-template-create
{: #instance-template-create}

Create an instance template.

```
ibmcloud is instance-template-create INSTANCE_TEMPLATE_NAME VPC ZONE_NAME PROFILE_NAME SUBNET --image-id IMAGE_ID [--boot-volume BOOT_VOLUME_JSON | @BOOT_VOLUME_JSON_FILE] [--volume-attach VOLUME_ATTACH_JSON | @VOLUME_ATTACH_JSON_FILE] [--key-ids IDS] [--user-data DATA] [(--security-group-ids SECURITY_GROUP_IDS [--ipv4 IPV4_ADDRESS]) | --primary-network-interface PRIMARY_NETWORK_INTERFACE_JSON | @PRIMARY_NETWORK_INTERFACE_JSON_FILE] [--network-interface NETWORK_INTERFACE_JSON | @NETWORK_INTERFACE_JSON_FILE] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-instance-template-create}

- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8`
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --volume-attach '[{"volume": {"name":"my-volume-name", "capacity":10, "profile": {"name": "general-purpose"}}}]'`
Create instance template with an attached volume.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --key-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
Create instance template with multiple SSH keys.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --network-interface '[{"name": "secondary-nic", "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}]'`
Create instance template that is attached to secondary network interface.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --primary-network-interface '{"name": "primary-nic", "subnet": {"id":"72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}, "primary_ipv4_address": "10.240.129.10", "security_groups": [{"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb8"}, {"id": "72b27b5c-f4b0-48bb-b954-5becc7c1dcb3"}]}'`
Create instance template with primary network interface configuration in JSON.
- `ibmcloud is instance-template-create my-template-name 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 us-south-1 bx2-2x8 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --image-id r123-72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --security-group-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --ipv4 10.240.129.10`
Create instance template with primary network interface configuration that includes security groups and primary IPv4 address

#### Command options
{: #command-options-instance-template-create}

- **INSTANCE_TEMPLATE_NAME**: Name of the instance template.
- **VPC**: ID of the VPC.
- **ZONE_NAME**: Name of the zone.
- **PROFILE_NAME**: Name of the profile.
- **SUBNET**: ID of the subnet.
- **--image-id**: ID of the image.
- **--boot-volume**: BOOT_VOLUME_JSON|@BOOT_VOLUME_JSON_FILE, boot volume attachment in JSON or JSON file.
- **--volume-attach**: VOLUME_ATTACH_JSON|@VOLUME_ATTACH_JSON_FILE, volume attachment in JSON or JSON file, list of volumes.
- **--key-ids**: Comma-separated IDs of SSH keys.
- **--user-data**: data|@data-file. User data to transfer to the server instance.
- **--security-group-ids**: Comma-separated security group IDs for primary network interface.
- **--ipv4**: Primary IPv4 address for the primary network interface.
- **--primary-network-interface**: PRIMARY_NETWORK_INTERFACE_JSON|@PRIMARY_NETWORK_INTERFACE_JSON_FILE, primary network interface in JSON or JSON file.
- **--network-interface**: NETWORK_INTERFACE_JSON|@NETWORK_INTERFACE_JSON_FILE, network interface attachment in JSON or JSON file.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-template-create-override-source-template
{: #instance-template-create-override-source-template}

Create an instance template by overriding a source template.

```
ibmcloud is instance-template-create-override-source-template --source-template-id SOURCE_TEMPLATE_ID [--name NAME] [--vpc-id VPC_ID] [--zone ZONE] [--profile PROFILE] [--subnet-id SUBNET_ID] [--image-id IMAGE_ID] [--boot-volume BOOT_VOLUME_JSON | @BOOT_VOLUME_JSON_FILE] [--volume-attach VOLUME_ATTACH_JSON | @VOLUME_ATTACH_JSON_FILE] [--key-ids IDS] [--user-data DATA] [(--security-group-ids SECURITY_GROUP_IDS [--ipv4 IPV4_ADDRESS]) | --primary-network-interface PRIMARY_NETWORK_INTERFACE_JSON | @PRIMARY_NETWORK_INTERFACE_JSON_FILE] [--network-interface NETWORK_INTERFACE_JSON | @NETWORK_INTERFACE_JSON_FILE] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
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
- **--vpc-id**: ID of the VPC.
- **--zone**: Name of the zone.
- **--profile**: Name of the instance profile.
- **--subnet-id**: ID of the subnet.
- **--image-id**: ID of the image.
- **--boot-volume**: BOOT_VOLUME_JSON|@BOOT_VOLUME_JSON_FILE, boot volume attachment in JSON or JSON file.
- **--volume-attach**: VOLUME_ATTACH_JSON|@VOLUME_ATTACH_JSON_FILE, volume attachment in JSON or JSON file, list of volumes.
- **--key-ids**: Comma-separated IDs of SSH keys.
- **--user-data**: data|@data-file. User data to transfer to the server instance.
- **--security-group-ids**: Comma-separated security group IDs for primary network interface.
- **--ipv4**: Primary IPv4 address for the primary network interface.
- **--primary-network-interface**: PRIMARY_NETWORK_INTERFACE_JSON|@PRIMARY_NETWORK_INTERFACE_JSON_FILE, primary network interface in JSON or JSON file.
- **--network-interface**: NETWORK_INTERFACE_JSON|@NETWORK_INTERFACE_JSON_FILE, network interface attachment in JSON or JSON file.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-template-update
{: #instance-template-update}

Update an instance template.

```
ibmcloud is instance-template-update TEMPLATE_ID --name NEW_NAME [--json]
```

#### Command examples
{: #command-examples-instance-template-update}

- `ibmcloud is instance-template-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name-template`
- `ibmcloud is instance-template-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name-template --json`

#### Command options
{: #command-options-instance-template-update}

- **TEMPLATE_ID**: ID of the template.
- **--name**: New name of an instance template.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-template-delete
{: #instance-template-delete}

Delete an instance template.

```
ibmcloud is instance-template-delete TEMPLATE_ID [-f, --force]
```

#### Command options
{: #command-options-instance-template-delete}

- **TEMPLATE_ID**: ID of the template.
- **--force, -f**: Force the operation without confirmation.





## Instance groups
{: #instance-group}

### ibmcloud is instance-groups
{: #instance-groups}

List all instance groups in the region.

```
ibmcloud is instance-groups [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-instance-groups}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-group
{: #instance-group}

View details of an instance group.

```
ibmcloud is instance-group INSTANCE_GROUP [--json]
```

#### Command options
{: #command-options-instance-group}

- **INSTANCE_GROUP**: ID of the instance group.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-group-create
{: #instance-group-create}

Create an instance group.

```
ibmcloud is instance-group-create INSTANCE_GROUP_NAME --instance-template INSTANCE_TEMPLATE --subnet-ids IDS [--membership-count MEMBERSHIP_COUNT] [--lb-id LB_ID --lb-pool-id LB_POOL_ID --application-port APPLICATION_PORT] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-instance-group-create}

- `ibmcloud is instance-group-create group-name --instance-template 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is instance-group-create group-name --instance-template 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --membership-count 2`
- `ibmcloud is instance-group-create group-name --instance-template 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --json`
- `ibmcloud is instance-group-create group-name --instance-template 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --lb-id 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --lb-pool-id d728d126-f2b9-48e8-ab67-16bb694b88f2 --application-port 2323`

#### Command options
{: #command-options-instance-group-create}

- **INSTANCE_GROUP_NAME**: Name of the instance group.
- **--instance-template**: ID of an instance template.
- **--membership-count**: The membership count of the instance group.
- **--subnet-ids**: Comma-separated IDs of subnets.
- **--lb-id**: ID of the load balancer.
- **--lb-pool-id**: ID of the load balancer pool.
- **--application-port**: The instance's port to route load balancer traffic.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-group-update
{: #instance-group-update}

Update an instance group.

```
ibmcloud is instance-group-update INSTANCE_GROUP [--instance-template INSTANCE_TEMPLATE] [--membership-count MEMBERSHIP_COUNT] [--subnet-ids IDS] [--name NEW_NAME] [--json] [--lb-id LB_ID --lb-pool-id LB_POOL_ID --application-port APPLICATION_PORT]
```

#### Command examples
{: #command-examples-instance-group-update}

- `ibmcloud is instance-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name --instance-template 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479`
- `ibmcloud is instance-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --membership-count 2`
- `ibmcloud is instance-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --subnet-ids 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3,72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is instance-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --name new-name --json`
- `ibmcloud is instance-group-update 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --lb-id 72251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --lb-pool-id d728d126-f2b9-48e8-ab67-16bb694b88f3 --application-port 80`

#### Command options
{: #command-options-instance-group-update}

- **INSTANCE_GROUP**: ID of the instance group.
- **--instance-template**: ID of an instance template.
- **--membership-count**: The membership count of the instance group.
- **--subnet-ids**: Comma-separated IDs of subnets.
- **--name**: New name of the instance group.
- **--json**: Format output in JSON.
- **--lb-id**: ID of the load balancer.
- **--lb-pool-id**: ID of the load balancer pool.
- **--application-port**: The instance's port to route load balancer traffic.

---

### ibmcloud is instance-group-delete
{: #instance-group-delete}

Delete an instance group.

```
ibmcloud is instance-group-delete INSTANCE_GROUP [-f, --force]
```

#### Command options
{: #command-options-instance-group-delete}

- **INSTANCE_GROUP**: ID of the instance group.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is instance-group-managers
{: #instance-group-managers}

List all managers for an instance group.

```
ibmcloud is instance-group-managers INSTANCE_GROUP [--json]
```

#### Command options
{: #command-options-instance-group-managers}

- **INSTANCE_GROUP**: ID of the instance group.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-group-manager
{: #instance-group-manager}

View details of a manager.

```
ibmcloud is instance-group-manager INSTANCE_GROUP MANAGER [--json]
```

#### Command options
{: #command-options-instance-group-manager}

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the manager.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-group-manager-create
{: #instance-group-manager-create}

Create a manager for in instance group.

```
ibmcloud is instance-group-manager-create INSTANCE_GROUP --max-members MAX_MEMBERS [--aggregation-window AGGREGATION_WINDOW] [--cooldown COOLDOWN] [--min-members MIN_MEMBERS] [--management-enabled true | false] [--name NAME] [--json]
```

#### Command examples
{: #command-examples-instance-group-manager-create}

- `ibmcloud is instance-group-manager-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --max-members 20`
- `ibmcloud is instance-group-manager-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --max-members 20 --aggregation-window 120`
- `ibmcloud is instance-group-manager-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --max-members 20 --cooldown 400`
- `ibmcloud is instance-group-manager-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --max-members 20 --min-members 2`
- `ibmcloud is instance-group-manager-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --max-members 20 --json`
- `ibmcloud is instance-group-manager-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --max-members 20 --management-enabled false`
- `ibmcloud is instance-group-manager-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --max-members 20 --name ig-manager`

#### Command options
{: #command-options-instance-group-manager-create}

- **INSTANCE_GROUP**: ID of the instance group.
- **--aggregation-window**: The time window in seconds to aggregate metrics before evaluation. Range 90-600. Divisible by 30. (default: 90).
- **--cooldown**: The duration of time in seconds to pause further scale actions after scaling takes place. Range 120-3600. (default: 300).
- **--max-members**: The maximum number of members in a managed instance group. Range 1-100.
- **--min-members**: The minimum number of members in a managed instance group. Range 1-100. (default: 1).
- **--management-enabled**: If set to false, the manager can't manipulate the instance group. Enumeration type: **true**, **false**. (default: "true").
- **--name**: Name of the manager.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-group-manager-update
{: #instance-group-manager-update}

Update a manager for instance group.

```
ibmcloud is instance-group-manager-update INSTANCE_GROUP MANAGER [--aggregation-window AGGREGATION_WINDOW] [--cooldown COOLDOWN] [--max-members MAX_MEMBERS] [--min-members MIN_MEMBERS] [--management-enabled true | false] [--json]
```

#### Command examples
{: #command-examples-instance-group-manager-update}

- `ibmcloud is instance-group-manager-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --aggregation-window 120`
- `ibmcloud is instance-group-manager-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --cooldown 400`
- `ibmcloud is instance-group-manager-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --max-members 20`
- `ibmcloud is instance-group-manager-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --min-members 2`
- `ibmcloud is instance-group-manager-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --aggregation-window false --json`
- `ibmcloud is instance-group-manager-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --management-enabled false`

#### Command options
{: #command-options-instance-group-manager-update}

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the manager.
- **--aggregation-window**: The time window in seconds to aggregate metrics before evaluation. Range 90-600. Divisible by 30.
- **--cooldown**: The duration of time in seconds to pause further scale actions after scaling takes place. Range 120-3600.
- **--max-members**: The maximum number of members in a managed instance group. Range 1-100.
- **--min-members**: The minimum number of members in a managed instance group. Range 1-100.
- **--management-enabled**: If set to false, the manager can't manipulate the instance group. Enumeration type: **true**, **false**.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-group-manager-delete
{: #instance-group-manager-delete}

Delete a group manager.

```
ibmcloud is instance-group-manager-delete INSTANCE_GROUP MANAGER [-f, --force]
```

#### Command options
{: #command-options-instance-group-manager-delete}

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the group manager.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is instance-group-manager-policies
{: #instance-group-manager-policies}

List policies for instance group manager.

```
ibmcloud is instance-group-manager-policies INSTANCE_GROUP MANAGER [--json]
```

#### Command options
{: #command-options-instance-group-manager-policies}

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the group manager.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-group-manager-policy
{: #instance-group-manager-policy}

View details of an instance group manager policy.

```
ibmcloud is instance-group-manager-policy INSTANCE_GROUP MANAGER POLICY [--json]
```

#### Command options
{: #command-options-instance-group-manager-policy}

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the group manager.
- **POLICY**: ID of the group manager policy.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-group-manager-policy-create
{: #instance-group-manager-policy-create}

Create an instance group manager policy.

```
ibmcloud is instance-group-manager-policy-create INSTANCE_GROUP MANAGER (--metric-type cpu | memory | network_in | network_out) --metric-value METRIC_VALUE [--name NAME] [--json]
```

#### Command examples
{: #command-examples-instance-group-manager-policy-create}

- `ibmcloud is instance-group-manager-policy-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --metric-type cpu --metric-value 50`
- `ibmcloud is instance-group-manager-policy-create 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --metric-type cpu --metric-value 50 --json`
- `ibmcloud is instance-group-manager-policy-create --group-id 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 --id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 --metric-type cpu --metric-value 50 --name new_name`

#### Command options
{: #command-options-instance-group-manager-policy-create}

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the group manager.
- **--metric-type**: The type of metric to be evaluated. Enumeration type: **cpu**, **memory**, **network_in**, **network_out**.
- **--metric-value**: The metric value to evaluate.
- **--name**: Name of the group manager policy.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-group-manager-policy-delete
{: #instance-group-manager-policy-delete}

Delete an instance group manager policy.

```
ibmcloud is instance-group-manager-policy-delete INSTANCE_GROUP MANAGER POLICY [-f, --force]
```

#### Command options
{: #command-options-instance-group-manager-policy-delete}

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the group manager.
- **POLICY**: ID of the group manager policy.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is instance-group-manager-policy-update
{: #instance-group-manager-policy-update}

Update an instance group manager policy.

```
ibmcloud is instance-group-manager-policy-update INSTANCE_GROUP MANAGER POLICY [--metric-type cpu | memory | network_in | network_out] [--metric-value METRIC_VALUE] [--json]
```

#### Command examples
{: #command-examples-instance-group-manager-policy-update}

- `ibmcloud is instance-group-manager-policy-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --metric-value 50`
- `ibmcloud is instance-group-manager-policy-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --metric-type cpu`
- `ibmcloud is instance-group-manager-policy-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --metric-value 50 --metric-type cpu --json`
- `ibmcloud is instance-group-manager-policy-update 2251a2e-d6c5-42b4-97b0-b5f8e8d1f479 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3 72b27b5c-f4b0-48bb-b954-5becc7c1dcb8 --metric-type cpu --name policy-name`

#### Command options
{: #command-options-instance-group-manager-policy-update}

- **INSTANCE_GROUP**: ID of the instance group.
- **MANAGER**: ID of the group manager.
- **POLICY**: ID of the group policy.
- **--metric-type**: The type of metric to be evaluated. Enumeration type: **cpu**, **memory**, **network_in**, **network_out**.
- **--metric-value**: The metric value to evaluate.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-group-membership
{: #instance-group-membership}

View details of an instance group member.

```
ibmcloud is instance-group-membership INSTANCE_GROUP MEMBER [--json]
```

#### Command options
{: #command-options-instance-group-membership}

- **INSTANCE_GROUP**: ID of the instance group.
- **MEMBER**: ID of the group member.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-group-membership-delete
{: #instance-group-membership-delete}

Delete an instance group member.

```
ibmcloud is instance-group-membership-delete INSTANCE_GROUP MEMBER [-f, --force]
```

#### Command options
{: #command-options-instance-group-membership-delete}

- **INSTANCE_GROUP**: ID of the instance group.
- **MEMBER**: ID of the group member.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is instance-group-memberships
{: #instance-group-memberships}

List all instance group members.

```
ibmcloud is instance-group-memberships INSTANCE_GROUP [--json]
```

#### Command options
{: #command-options-instance-group-memberships}

- **INSTANCE_GROUP**: ID of the instance group.
- **--json**: Format output in JSON.

---

### ibmcloud is instance-group-memberships-delete
{: #instance-group-memberships-delete}

Delete all instance group members.

```
ibmcloud is instance-group-memberships-delete INSTANCE_GROUP [-f, --force]
```

#### Command options
{: #command-options-instance-group-memberships-delete}

- **INSTANCE_GROUP**: ID of the instance group.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is instance-group-load-balancer-delete
{: #instance-group-load-balancer-delete}

Delete instance group load balancer.

```
ibmcloud is instance-group-load-balancer-delete INSTANCE_GROUP [-f, --force]
```

#### Command options
{: #command-options-instance-group-load-balancer-delete}

- **INSTANCE_GROUP**: ID of the instance group.
- **--force, -f**: Force the operation without confirmation.

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
ibmcloud is region REGION_NAME [--json]
```

#### Command options
{: #command-options-region}

- **REGION_NAME**: Name of the region.
- **--json**: Format output in JSON.

---

### ibmcloud is regions
{: #regions-ibmcloud}

List all regions.

```
ibmcloud is regions [--json]
```

#### Command options
{: #command-options-regions}

- **--json**: Format output in JSON.

---

## Zones
{: #zones}

### ibmcloud is zone
{: #zone}

View details of a zone in the target region.

```
ibmcloud is zone ZONE_NAME [--json]
```

#### Command options
{: #command-options-zone}

- **ZONE_NAME**: Name of the zone.
- **--json**: Format output in JSON.

---

### ibmcloud is zones
{: #zones-ibmcloud}

List all zones in the target region.

```
ibmcloud is zones [--json]
```

#### Command options
{: #command-options-zones}

- **--json**: Format output in JSON.

---

## STORAGE COMMANDS
{: #storage}

### ibmcloud is volumes
{: #volumes}

List all volumes.

```
ibmcloud is volumes [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command options
{: #command-options-volumes}

- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is volume
{: #volume}

View details of a volume.

```
ibmcloud is volume VOLUME [--json]
```

#### Command options
{: #command-options-volume}

- **VOLUME**: ID of the volume.
- **--json**: Format output in JSON.

---

### ibmcloud is volume-create
{: #volume-create}

Create a volume.

```
ibmcloud is volume-create VOLUME_NAME PROFILE_NAME ZONE_NAME [--capacity CAPACITY] [--iops IOPS] [--resource-group-id RESOURCE_GROUP_ID | --resource-group-name RESOURCE_GROUP_NAME] [--json]
```

#### Command examples
{: #command-examples-volume-create}

- `ibmcloud is volume-create my-volume general-purpose us-south-1`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --capacity 500`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --iops 10000`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --resource-group-id 72b27b5c-f4b0-48bb-b954-5becc7c1dcb3`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --resource-group-name Default`
- `ibmcloud is volume-create my-volume general-purpose us-south-1 --json`

#### Command options
{: #command-options-volume-create}

- **VOLUME_NAME**: Name of the volume.
- **PROFILE_NAME**: Name of the profile.
- **ZONE_NAME**: Name of the zone.
- **--capacity**: Capacity of the volume in GB, 10 - 2000. Default is 100.
- **--iops**: Input/output operations per second for the volume.
- **--resource-group-id**: ID of the resource group. This option is mutually exclusive with **--resource-group-name**.
- **--resource-group-name**: Name of the resource group. This option is mutually exclusive with **--resource-group-id**.
- **--json**: Format output in JSON.

---

### ibmcloud is volume-delete
{: #volume-delete}

Delete a volume.

```
ibmcloud is volume-delete VOLUME [-f, --force]
```

#### Command options
{: #command-options-volume-delete}

- **VOLUME**: ID of the volume.
- **--force, -f**: Force the operation without confirmation.

---

### ibmcloud is volume-profiles
{: #volume-profiles}

List all volume profiles.

```
ibmcloud is volume-profiles [--json]
```

#### Command options
{: #command-options-volume-profiles}

- **--json**: Format output in JSON.

---

### ibmcloud is volume-profile
{: #volume-profile}

View details of a volume profile.

```
ibmcloud is volume-profile PROFILE_NAME [--json]
```

#### Command options
{: #command-options-volume-profile}

- **PROFILE_NAME**: Name of the profile.
- **--json**: Format output in JSON.

---

### ibmcloud is volume-update
{: #volume-update}

Update a volume.

```
ibmcloud is volume-update VOLUME --name NEW_NAME [--json]
```

#### Command example
{: #command-example-volume-update}

- `ibmcloud is volume-update 64bec87d-d175-4fa5-b240-b092fdbcedd6 --name my-volume --json`

#### Command options
{: #command-options-volume-update}

- **VOLUME**: ID of the volume.
- **--name**: New name of the volume.
- **--json**: Format output in JSON.

---
