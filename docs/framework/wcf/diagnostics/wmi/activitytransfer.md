---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: f1978881517fe5010ccc0f5192b21bd6688f063a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291116"
---
# <a name="activitytransfer"></a><span data-ttu-id="78a8e-102">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="78a8e-102">ActivityTransfer</span></span>

<span data-ttu-id="78a8e-103">アクティビティ転送イベント</span><span class="sxs-lookup"><span data-stu-id="78a8e-103">Activity Transfer Event</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78a8e-104">構文</span><span class="sxs-lookup"><span data-stu-id="78a8e-104">Syntax</span></span>  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="78a8e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="78a8e-105">Methods</span></span>  

 <span data-ttu-id="78a8e-106">ActivityTransfer クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="78a8e-106">The ActivityTransfer class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="78a8e-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="78a8e-107">Properties</span></span>  

 <span data-ttu-id="78a8e-108">ActivityTransfer クラスには次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="78a8e-108">The ActivityTransfer class has the following properties:</span></span>  
  
### <a name="activityid"></a><span data-ttu-id="78a8e-109">ActivityID</span><span class="sxs-lookup"><span data-stu-id="78a8e-109">ActivityID</span></span>  
  
- <span data-ttu-id="78a8e-110">データ型: object</span><span class="sxs-lookup"><span data-stu-id="78a8e-110">Data type: object</span></span>  
    <span data-ttu-id="78a8e-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="78a8e-111">Access type: Read-only</span></span>  
  
- <span data-ttu-id="78a8e-112">アクティビティ ID</span><span class="sxs-lookup"><span data-stu-id="78a8e-112">Activity ID</span></span>  
  
### <a name="relatedactivityid"></a><span data-ttu-id="78a8e-113">RelatedActivityID</span><span class="sxs-lookup"><span data-stu-id="78a8e-113">RelatedActivityID</span></span>  
  
- <span data-ttu-id="78a8e-114">データ型: object</span><span class="sxs-lookup"><span data-stu-id="78a8e-114">Data type: object</span></span>  
    <span data-ttu-id="78a8e-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="78a8e-115">Access type: Read-only</span></span>  
  
- <span data-ttu-id="78a8e-116">関連アクティビティ ID</span><span class="sxs-lookup"><span data-stu-id="78a8e-116">Related Activity ID</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78a8e-117">要件</span><span class="sxs-lookup"><span data-stu-id="78a8e-117">Requirements</span></span>  
  
|<span data-ttu-id="78a8e-118">MOF</span><span class="sxs-lookup"><span data-stu-id="78a8e-118">MOF</span></span>|<span data-ttu-id="78a8e-119">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="78a8e-119">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="78a8e-120">名前空間</span><span class="sxs-lookup"><span data-stu-id="78a8e-120">Namespace</span></span>|<span data-ttu-id="78a8e-121">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="78a8e-121">Defined in root\ServiceModel.</span></span>|
