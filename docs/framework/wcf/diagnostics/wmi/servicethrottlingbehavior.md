---
title: ServiceThrottlingBehavior
ms.date: 03/30/2017
ms.assetid: 37b9e517-1f1f-4ec4-9fcb-2b8016794f5b
ms.openlocfilehash: 3bcf205964a22cdb418d0158e5ee6439169538ee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273985"
---
# <a name="servicethrottlingbehavior"></a><span data-ttu-id="ba226-102">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="ba226-102">ServiceThrottlingBehavior</span></span>

<span data-ttu-id="ba226-103">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="ba226-103">ServiceThrottlingBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba226-104">構文</span><span class="sxs-lookup"><span data-stu-id="ba226-104">Syntax</span></span>  
  
```csharp  
class ServiceThrottlingBehavior : Behavior  
{  
  sint32 MaxConcurrentCalls;  
  sint32 MaxConcurrentInstances;  
  sint32 MaxConcurrentSessions;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ba226-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ba226-105">Methods</span></span>  

 <span data-ttu-id="ba226-106">ServiceThrottlingBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="ba226-106">The ServiceThrottlingBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ba226-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ba226-107">Properties</span></span>  

 <span data-ttu-id="ba226-108">ServiceThrottlingBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="ba226-108">The ServiceThrottlingBehavior class has the following properties:</span></span>  
  
### <a name="maxconcurrentcalls"></a><span data-ttu-id="ba226-109">MaxConcurrentCalls</span><span class="sxs-lookup"><span data-stu-id="ba226-109">MaxConcurrentCalls</span></span>  

 <span data-ttu-id="ba226-110">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="ba226-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="ba226-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ba226-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba226-112">ServiceHost 内のすべてのディスパッチャー オブジェクトでアクティブに処理中のメッセージの最大数。</span><span class="sxs-lookup"><span data-stu-id="ba226-112">The maximum number of messages actively processing across all dispatcher objects in a ServiceHost.</span></span>  
  
### <a name="maxconcurrentinstances"></a><span data-ttu-id="ba226-113">MaxConcurrentInstances</span><span class="sxs-lookup"><span data-stu-id="ba226-113">MaxConcurrentInstances</span></span>  

 <span data-ttu-id="ba226-114">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="ba226-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="ba226-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ba226-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba226-116">一度に実行可能なサービス オブジェクトの最大数。</span><span class="sxs-lookup"><span data-stu-id="ba226-116">The maximum number of service objects that can execute at one time.</span></span>  
  
### <a name="maxconcurrentsessions"></a><span data-ttu-id="ba226-117">MaxConcurrentSessions</span><span class="sxs-lookup"><span data-stu-id="ba226-117">MaxConcurrentSessions</span></span>  

 <span data-ttu-id="ba226-118">データ型 : sint32</span><span class="sxs-lookup"><span data-stu-id="ba226-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="ba226-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ba226-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ba226-120">ホストが一度に受け入れ可能なセッションの最大数。</span><span class="sxs-lookup"><span data-stu-id="ba226-120">The maximum number of sessions a host can accept at one time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba226-121">要件</span><span class="sxs-lookup"><span data-stu-id="ba226-121">Requirements</span></span>  
  
|<span data-ttu-id="ba226-122">MOF</span><span class="sxs-lookup"><span data-stu-id="ba226-122">MOF</span></span>|<span data-ttu-id="ba226-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="ba226-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ba226-124">名前空間</span><span class="sxs-lookup"><span data-stu-id="ba226-124">Namespace</span></span>|<span data-ttu-id="ba226-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="ba226-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ba226-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="ba226-126">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceThrottlingBehavior>
