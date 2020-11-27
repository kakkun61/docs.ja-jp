---
title: WSAT_TraceRecord
ms.date: 03/30/2017
ms.assetid: 99bc7f66-1335-40d8-aa68-e754d569dc0d
ms.openlocfilehash: 0409277821a7cca3f97fcec1bb383aba9583a1f6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262217"
---
# <a name="wsat_tracerecord"></a><span data-ttu-id="85f6d-102">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="85f6d-102">WSAT_TraceRecord</span></span>

<span data-ttu-id="85f6d-103">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="85f6d-103">WSAT_TraceRecord</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85f6d-104">構文</span><span class="sxs-lookup"><span data-stu-id="85f6d-104">Syntax</span></span>  
  
```csharp
class WSAT_TraceRecord : WSAT_TraceEvent  
{  
  object ActivityID;  
  sint32 EventID;  
  string TraceRecord;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="85f6d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="85f6d-105">Methods</span></span>  

 <span data-ttu-id="85f6d-106">WSAT_TraceRecord クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="85f6d-106">The WSAT_TraceRecord class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="85f6d-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="85f6d-107">Properties</span></span>  

 <span data-ttu-id="85f6d-108">WSAT_TraceRecord クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="85f6d-108">The WSAT_TraceRecord class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="85f6d-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="85f6d-109">ActivityID</span></span>  

 <span data-ttu-id="85f6d-110">データ型: object</span><span class="sxs-lookup"><span data-stu-id="85f6d-110">Data type: object</span></span>  
<span data-ttu-id="85f6d-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="85f6d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="85f6d-112">トレース レコードのアクティビティ ID です。</span><span class="sxs-lookup"><span data-stu-id="85f6d-112">The activity ID of the trace record.</span></span>  
  
### <a name="eventid"></a><span data-ttu-id="85f6d-113">EventID</span><span class="sxs-lookup"><span data-stu-id="85f6d-113">EventID</span></span>  

 <span data-ttu-id="85f6d-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="85f6d-114">Data type: sint32</span></span>  
<span data-ttu-id="85f6d-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="85f6d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="85f6d-116">トレース レコードのイベント ID です。</span><span class="sxs-lookup"><span data-stu-id="85f6d-116">The event ID of the trace record.</span></span>  
  
### <a name="tracerecord"></a><span data-ttu-id="85f6d-117">TraceRecord</span><span class="sxs-lookup"><span data-stu-id="85f6d-117">TraceRecord</span></span>  

 <span data-ttu-id="85f6d-118">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="85f6d-118">Data type: string</span></span>  
<span data-ttu-id="85f6d-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="85f6d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="85f6d-120">トレース レコード</span><span class="sxs-lookup"><span data-stu-id="85f6d-120">Trace Record</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="85f6d-121">要件</span><span class="sxs-lookup"><span data-stu-id="85f6d-121">Requirements</span></span>  
  
|<span data-ttu-id="85f6d-122">MOF</span><span class="sxs-lookup"><span data-stu-id="85f6d-122">MOF</span></span>|<span data-ttu-id="85f6d-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="85f6d-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="85f6d-124">名前空間</span><span class="sxs-lookup"><span data-stu-id="85f6d-124">Namespace</span></span>|<span data-ttu-id="85f6d-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="85f6d-125">Defined in root\ServiceModel</span></span>|
