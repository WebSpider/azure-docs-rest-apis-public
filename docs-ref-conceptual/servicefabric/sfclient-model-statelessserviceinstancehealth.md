---
title: "StatelessServiceInstanceHealth"
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
# StatelessServiceInstanceHealth

Represents the health of the stateless service instance.
Contains the instance aggregated health state, the health events and the unhealthy evaluations.


## Properties
| Name | Type | Required |
| --- | --- | --- |
| [`ServiceKind`](#servicekind) | string | Yes |
| [`AggregatedHealthState`](#aggregatedhealthstate) | string (enum) | No |
| [`HealthEvents`](#healthevents) | array of [HealthEvent](sfclient-model-healthevent.md) | No |
| [`UnhealthyEvaluations`](#unhealthyevaluations) | array of [HealthEvaluationWrapper](sfclient-model-healthevaluationwrapper.md) | No |
| [`HealthStatistics`](#healthstatistics) | [HealthStatistics](sfclient-model-healthstatistics.md) | No |
| [`PartitionId`](#partitionid) | string (uuid) | No |
| [`InstanceId`](#instanceid) | string | No |

____
### ServiceKind
__Type__: string <br/>
__Required__: Yes <br/>
<br/>
A discriminator property. Its value must be 'Stateless' for objects of type 'StatelessServiceInstanceHealth'.

____
### `AggregatedHealthState`
__Type__: string (enum) <br/>
__Required__: No<br/>
<br/>
The HealthState representing the aggregated health state of the entity computed by Health Manager.
The health evaluation of the entity reflects all events reported on the entity and its children (if any).
The aggregation is done by applying the desired health policy.


The health state of a Service Fabric entity such as Cluster, Node, Application, Service, Partition, Replica etc.

Possible values are: 

  - `Invalid` - Indicates an invalid health state. All Service Fabric enumerations have the invalid type. The value is zero.
  - `Ok` - Indicates the health state is okay. The value is 1.
  - `Warning` - Indicates the health state is at a warning level. The value is 2.
  - `Error` - Indicates the health state is at an error level. Error health state should be investigated, as they can impact the correct functionality of the cluster. The value is 3.
  - `Unknown` - Indicates an unknown health status. The value is 65535.



____
### `HealthEvents`
__Type__: array of [HealthEvent](sfclient-model-healthevent.md) <br/>
__Required__: No<br/>
<br/>
The list of health events reported on the entity.

____
### `UnhealthyEvaluations`
__Type__: array of [HealthEvaluationWrapper](sfclient-model-healthevaluationwrapper.md) <br/>
__Required__: No<br/>
<br/>
The unhealthy evaluations that show why the current aggregated health state was returned by Health Manager.

____
### `HealthStatistics`
__Type__: [HealthStatistics](sfclient-model-healthstatistics.md) <br/>
__Required__: No<br/>
<br/>
Shows the health statistics for all children types of the queried entity.

____
### `PartitionId`
__Type__: string (uuid) <br/>
__Required__: No<br/>
<br/>
Id of the partition to which this replica belongs.

____
### `InstanceId`
__Type__: string <br/>
__Required__: No<br/>
<br/>
Id of a stateless service instance. InstanceId is used by Service Fabric to uniquely identify an instance of a partition of a stateless service. It is unique within a partition and does not change for the lifetime of the instance. If the instance has failed over on the same or different node, it will get a different value for the InstanceId.
