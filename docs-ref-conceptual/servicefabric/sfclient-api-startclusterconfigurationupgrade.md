---
title: "Start Cluster Configuration Upgrade"
ms.date: "2018-07-20"
ms.prod: "azure"
ms.service: "service-fabric"
ms.topic: "reference"
applies_to: 
  - "Azure"
  - "Windows Server 2012 R2"
  - "Windows Server 2016"
dev_langs: 
  - "rest-api"
helpviewer_keywords: 
  - "Service Fabric REST API Reference"
author: "rwike77"
ms.author: "ryanwi"
manager: "timlt"
translation.priority.mt: 
  - "de-de"
  - "es-es"
  - "fr-fr"
  - "it-it"
  - "ja-jp"
  - "ko-kr"
  - "pt-br"
  - "ru-ru"
  - "zh-cn"
  - "zh-tw"
---
# Start Cluster Configuration Upgrade
Start upgrading the configuration of a Service Fabric standalone cluster.

Validate the supplied configuration upgrade parameters and start upgrading the cluster configuration if the parameters are valid.

## Request
| Method | Request URI |
| ------ | ----------- |
| POST | `/$/StartClusterConfigurationUpgrade?api-version=6.0&timeout={timeout}` |


## Parameters
| Name | Type | Required | Location |
| --- | --- | --- | --- |
| [`api-version`](#api-version) | string | Yes | Query |
| [`timeout`](#timeout) | integer (int64) | No | Query |
| [`ClusterConfigurationUpgradeDescription`](#clusterconfigurationupgradedescription) | [ClusterConfigurationUpgradeDescription](sfclient-model-clusterconfigurationupgradedescription.md) | Yes | Body |

____
### `api-version`
__Type__: string <br/>
__Required__: Yes<br/>
__Default__: `6.0` <br/>
<br/>
The version of the API. This parameter is required and its value must be '6.0'.

Service Fabric REST API version is based on the runtime version in which the API was introduced or was changed. Service Fabric runtime supports more than one version of the API. This is the latest supported version of the API. If a lower API version is passed, the returned response may be different from the one documented in this specification.

Additionally the runtime accept any version that is higher than the latest supported version up to the current version of the runtime. So if the latest API version is 6.0, but if the runtime is 6.1, in order to make it easier to write the clients, the runtime will accept version 6.1 for that API. However the behavior of the API will be as per the documented 6.0 version.


____
### `timeout`
__Type__: integer (int64) <br/>
__Required__: No<br/>
__Default__: `60` <br/>
__InclusiveMaximum__: `4294967295` <br/>
__InclusiveMinimum__: `1` <br/>
<br/>
The server timeout for performing the operation in seconds. This timeout specifies the time duration that the client is willing to wait for the requested operation to complete. The default value for this parameter is 60 seconds.

____
### `ClusterConfigurationUpgradeDescription`
__Type__: [ClusterConfigurationUpgradeDescription](sfclient-model-clusterconfigurationupgradedescription.md) <br/>
__Required__: Yes<br/>
<br/>
Parameters for a standalone cluster configuration upgrade.

## Responses

| HTTP Status Code | Description | Response Schema |
| --- | --- | --- |
| 202 (Accepted) | A successful response means that the cluster configuration upgrade has started. Use GetClusterConfigurationUpgradeStatus operation to get the status of the upgrade.<br/> |  |
| All other status codes | The detailed error response.<br/> | [FabricError](sfclient-model-fabricerror.md) |

## Examples

### Start upgrading the configuration of a Service Fabric standalone cluster

This example shows how to start upgrading the configuration of a Service Fabric standalone cluster.

#### Request
```
POST http://localhost:19080/$/StartClusterConfigurationUpgrade?api-version=6.0
```

##### Body
```json
{
  "ClusterConfig": "<PutYourClusterConfigHere>",
  "ApplicationHealthPolicies": {
    "ApplicationHealthPolicyMap": [
      {
        "Key": "fabric:/samples/CalculatorApp",
        "Value": {
          "ConsiderWarningAsError": true,
          "MaxPercentUnhealthyDeployedApplications": "10",
          "DefaultServiceTypeHealthPolicy": {
            "MaxPercentUnhealthyPartitionsPerService": "0",
            "MaxPercentUnhealthyReplicasPerPartition": "0",
            "MaxPercentUnhealthyServices": "0"
          },
          "ServiceTypeHealthPolicyMap": [
            {
              "Key": "Svc1Type",
              "Value": {
                "MaxPercentUnhealthyPartitionsPerService": "0",
                "MaxPercentUnhealthyReplicasPerPartition": "0",
                "MaxPercentUnhealthyServices": "10"
              }
            }
          ]
        }
      }
    ]
  }
}
```

#### 202 Response
##### Body
The response body is empty.