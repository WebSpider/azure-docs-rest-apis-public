---
title: "Set Directory Metadata"
ms.custom: na
ms.date: 2016-06-29
ms.prod: azure
ms.reviewer: na
ms.service: storage
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
ms.assetid: 920af977-b511-42de-9a1a-9326575e1c94
caps.latest.revision: 4
author: tamram
manager: carolz
translation.priority.mt: 
  - de-de
  - es-es
  - fr-fr
  - it-it
  - ja-jp
  - ko-kr
  - pt-br
  - ru-ru
  - zh-cn
  - zh-tw
---
# Set Directory Metadata
The `Set Directory Metadata` operation updates user defined metadata for the specified directory. This operation is available in version 2015-02-21 and newer.  
  
## Request  
  
|Method|Request URI|HTT Version|  
|------------|-----------------|-----------------|  
|PUT|`https://myaccount.file.core.windows.net/myshare/ myparentdirectorypath/mydirectory?restype=directory& comp=metadata`|HTTP/1.1|  
  
 Replace the path components shown in the request URI with your own, as follows:  
  
|Path Component|Description|  
|--------------------|-----------------|  
|`Myaccount`|The name of your storage account.|  
|`Myshare`|The name of your file share.|  
|`myparentdirectorypath`|Optional. The path to the parent directory.|  
|`Mydirectory`|The name of the directory.|  
  
 For details on path naming restrictions, see [Naming and Referencing Shares, Directories, Files, and Metadata](Naming-and-Referencing-Shares--Directories--Files--and-Metadata.md).  
  
### URI Parameters  
 The following additional parameters may be specified on the request URI.  
  
|Parameter|Description|  
|---------------|-----------------|  
|`Timeout`|Optional. The timeout parameter is expressed in seconds. For more information, see [Setting Timeouts for File Service Operations](Setting-Timeouts-for-File-Service-Operations.md).|  
  
### Request Headers  
 The following table describes required and optional request headers.  
  
|Request Header|Description|  
|--------------------|-----------------|  
|`Authorization`|Required. Specifies the authentication scheme, account name, and signature. For more information, see [Authentication for the Azure Storage Services](authorization-for-the-azure-storage-services.md).|  
|`Date` or `x-ms-date`|Required. Specifies the Coordinated Universal Time (UTC) for the request. For more information, see [Authentication for the Azure Storage Services](authorization-for-the-azure-storage-services.md).|  
|`x-ms-version`|Required for all authenticated requests. Specifies the version of the operation to use for this request. This operation is available only in versions 2015-02-21 and later.<br /><br /> For more information, see [Versioning for the Azure Storage Services](https://msdn.microsoft.com/en-us/library/azure/dd894041.aspx).|  
|`x-ms-meta-name:value`|Optional. Sets a name-value pair for the directory.<br /><br /> Each call to this operation replaces all existing metadata attached to the directory. To remove all metadata from the directory, call this operation with no metadata headers.<br /><br /> Metadata names must adhere to the naming rules for [C# identifiers](https://docs.microsoft.com/dotnet/csharp/language-reference).|  
  
### Request Body  
 None.  
  
## Response  
 The response includes an HTTP status code and a set of response headers.  
  
### Status Code  
 A successful operation returns status code 202 (Accepted).  
  
 For information about status codes, see [Status and Error Codes](Status-and-Error-Codes2.md).  
  
### Response Headers  
 The response for this operation includes the following headers. The response also includes additional standard HTTP headers. All standard headers conform to the [HTTP/1.1 protocol specification](http://go.microsoft.com/fwlink/?LinkId=73147).  
  
|Response header|Description|  
|---------------------|-----------------|  
|`ETag`|The ETag contains a value which represents the version of the directory, in quotes.|  
|`x-ms-request-id`|This header uniquely identifies the request that was made and can be used for troubleshooting the request. For more information, see [Troubleshooting API Operations](https://msdn.microsoft.com/en-us/library/azure/dd573365.aspx).|  
|`x-ms-version`|Indicates the version of the File service used to execute the request.|  
|`Date`|A UTC date/time value generated by the service that indicates the time at which the response was initiated.|  
|`x-ms-request-server-encrypted: true/false`|Version 2017-04-17 or newer. The value of this header is set to `true` if the contents of the request are successfully encrypted using the specified algorithm, and `false` otherwise.|  
  
### Response Body  
 None.

 ## Remarks
 `Set Directory Metadata` is not supported on a share snapshot, which is a read-only copy of a share. An attempt to perform this operation on a share snapshot will fail with 400 (InvalidQueryParameterValue)