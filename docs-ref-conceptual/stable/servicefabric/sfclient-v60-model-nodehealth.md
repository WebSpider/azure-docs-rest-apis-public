---
title: "NodeHealth"
ms.date: "2017-10-02"
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
# NodeHealth

Information about the health of a Service Fabric node.

## Properties
| Name | Type | Required |
| --- | --- | --- |
| [AggregatedHealthState](#aggregatedhealthstate) | string (enum) | No |
| [HealthEvents](#healthevents) | array of [HealthEvent](sfclient-v60-model-healthevent.md) | No |
| [UnhealthyEvaluations](#unhealthyevaluations) | array of [HealthEvaluationWrapper](sfclient-v60-model-healthevaluationwrapper.md) | No |
| [HealthStatistics](#healthstatistics) | [HealthStatistics](sfclient-v60-model-healthstatistics.md) | No |
| [Name](#name) | string | No |

____
### AggregatedHealthState
__Type__: string (enum) <br/>
__Required__: No<br/>
<br/>
The HealthState representing the aggregated health state of the entity computed by Health Manager.
The health evaluation of the entity reflects all events reported on the entity and its children (if any).
The aggregation is done by applying the desired health policy.


The HealthState representing the aggregated health state of the entity computed by Health Manager.
The health evaluation of the entity reflects all events reported on the entity and its children (if any).
The aggregation is done by applying the desired health policy.



____
### HealthEvents
__Type__: array of [HealthEvent](sfclient-v60-model-healthevent.md) <br/>
__Required__: No<br/>
<br/>
The list of health events reported on the entity.

____
### UnhealthyEvaluations
__Type__: array of [HealthEvaluationWrapper](sfclient-v60-model-healthevaluationwrapper.md) <br/>
__Required__: No<br/>
<br/>
The unhealthy evaluations that show why the current aggregated health state was returned by Health Manager.

____
### HealthStatistics
__Type__: [HealthStatistics](sfclient-v60-model-healthstatistics.md) <br/>
__Required__: No<br/>
<br/>
Shows the health statistics for all children types of the queried entity.

____
### Name
__Type__: string <br/>
__Required__: No<br/>
<br/>
Name of the node whose health information is described by this object.