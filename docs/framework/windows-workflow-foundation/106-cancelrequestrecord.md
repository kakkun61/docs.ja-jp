---
title: 106 - CancelRequestRecord
ms.date: 03/30/2017
ms.assetid: f72a59aa-8093-4a8e-94df-40acaffb1ffb
ms.openlocfilehash: e7b736d78486b0de7c108e6212d2aa1857e01cc4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96238900"
---
# <a name="106---cancelrequestrecord"></a>106 - CancelRequestRecord

## <a name="properties"></a>プロパティ  
  
|||  
|-|-|  
|Id|106|  
|Keywords|EndToEndMonitoring、Troubleshooting、HealthMonitoring、WFTracking|  
|Level|情報|  
|チャネル|Microsoft-Windows-Application Server-Applications/Analytic|  
  
## <a name="description"></a>Description  

 このイベントは、ワークフロー インスタンス内のアクティビティが cancelrequestedrecord を生成したときに、ETW 追跡参加要素によって生成されます。  
  
## <a name="message"></a>Message  

 TrackRecord = CancelRequestedRecord、InstanceID=%1、RecordNumber=%2、EventTime=%3、Name=%4、ActivityId=%5、ActivityInstanceId=%6、ActivityTypeName = %7、ChildActivityName = %8、ChildActivityId = %9、ChildActivityInstanceId = %10、ChildActivityTypeName =%11、Annotations=%12、ProfileName = %13  
  
## <a name="details"></a>詳細  
  
|データ項目名|データ項目の型|Description|  
|--------------------|--------------------|-----------------|  
|InstanceId|xs:GUID|ワークフローのインスタンス ID|  
|RecordNumber|xs:long|生成されたレコードのシーケンス番号|  
|EventTime|xs:dateTime|イベントの生成時刻 (UTC)|  
|名前|xs:string|操作のキャンセルを要求したアクティビティの名前|  
|ActivityId|xs:string|操作のキャンセルを要求したアクティビティの ID|  
|ActivityInstanceId|xs:string|操作のキャンセルを要求したアクティビティのインスタンス ID|  
|ActivityTypeName|xs:string|操作のキャンセルを要求したアクティビティの型|  
|ChildActivityName|xs:string|キャンセルされるアクティビティの名前|  
|ChildActivityId|xs:string|キャンセルされるアクティビティの ID|  
|ChildActivityInstanceId|xs:string|キャンセルされるアクティビティのインスタンス ID|  
|ChildActivityTypeName|xs:string|キャンセルされるアクティビティの型|  
|注釈|xs:string|このイベントに追加された注釈。  値は、annotationValue 形式の xml 要素に格納され \<items> \< item  name = "annotationName" type="System.String"> \</item> \</items> ます。  注釈が指定されていない場合、文字列にはが含まれ \<items/> ます。 ETW イベントのサイズは、ETW バッファーのサイズまたは ETW イベントの最大ペイロードに制限されます。 イベントのサイズが ETW の制限を超えると、注釈が削除され、注釈の値が... に置き換えられて、イベントが切り捨てられます。 \<items> \</items>|  
|ProfileName|xs:string|このイベントを生成した追跡プロファイルの名前|  
|HostReference|xs:string|Web ホスト サービスの場合は、このフィールドにより、サービスが Web 階層内で一意に識別されます。  この形式は、' Web サイト名アプリケーションの仮想パス&#124;サービスの仮想パス&#124;ServiceName ' として定義されています。例: ' Default Web Site/電卓 '&#124;&#124;|  
|AppDomain|xs:string|AppDomain.CurrentDomain.FriendlyName で返される文字列。|
