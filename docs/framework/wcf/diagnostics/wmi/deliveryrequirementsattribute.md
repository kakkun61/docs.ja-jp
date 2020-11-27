---
title: DeliveryRequirementsAttribute
ms.date: 03/30/2017
ms.assetid: 40c5435c-a325-4cf8-9dd0-d6e24b4a56a3
ms.openlocfilehash: a70a4ba40b569acc7893b21d796194224dc4ee78
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96274050"
---
# <a name="deliveryrequirementsattribute"></a><span data-ttu-id="944bd-102">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="944bd-102">DeliveryRequirementsAttribute</span></span>

<span data-ttu-id="944bd-103">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="944bd-103">DeliveryRequirementsAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="944bd-104">構文</span><span class="sxs-lookup"><span data-stu-id="944bd-104">Syntax</span></span>  
  
```csharp
class DeliveryRequirementsAttribute : Behavior  
{  
  string QueuedDeliveryRequirements;  
  boolean RequireOrderedDelivery;  
  string TargetContract;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="944bd-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="944bd-105">Methods</span></span>  

 <span data-ttu-id="944bd-106">DeliveryRequirementsAttribute クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="944bd-106">The DeliveryRequirementsAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="944bd-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="944bd-107">Properties</span></span>  

 <span data-ttu-id="944bd-108">DeliveryRequirementsAttribute クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="944bd-108">The DeliveryRequirementsAttribute class has the following properties:</span></span>  
  
### <a name="queueddeliveryrequirements"></a><span data-ttu-id="944bd-109">QueuedDeliveryRequirements</span><span class="sxs-lookup"><span data-stu-id="944bd-109">QueuedDeliveryRequirements</span></span>  

 <span data-ttu-id="944bd-110">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="944bd-110">Data type: string</span></span>  
  
 <span data-ttu-id="944bd-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="944bd-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="944bd-112">サービスのバインドがコントラクトをサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="944bd-112">Specifies whether the binding for a service supports contracts.</span></span>  
  
### <a name="requireordereddelivery"></a><span data-ttu-id="944bd-113">RequireOrderedDelivery</span><span class="sxs-lookup"><span data-stu-id="944bd-113">RequireOrderedDelivery</span></span>  

 <span data-ttu-id="944bd-114">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="944bd-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="944bd-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="944bd-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="944bd-116">バインディングが順序付きメッセージをサポートするかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="944bd-116">Specifies whether the binding supports ordered messages.</span></span>  
  
### <a name="targetcontract"></a><span data-ttu-id="944bd-117">TargetContract</span><span class="sxs-lookup"><span data-stu-id="944bd-117">TargetContract</span></span>  

 <span data-ttu-id="944bd-118">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="944bd-118">Data type: string</span></span>  
  
 <span data-ttu-id="944bd-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="944bd-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="944bd-120">適用先となるコントラクトです。</span><span class="sxs-lookup"><span data-stu-id="944bd-120">The contract to which it applies.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="944bd-121">要件</span><span class="sxs-lookup"><span data-stu-id="944bd-121">Requirements</span></span>  
  
|<span data-ttu-id="944bd-122">MOF</span><span class="sxs-lookup"><span data-stu-id="944bd-122">MOF</span></span>|<span data-ttu-id="944bd-123">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="944bd-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="944bd-124">名前空間</span><span class="sxs-lookup"><span data-stu-id="944bd-124">Namespace</span></span>|<span data-ttu-id="944bd-125">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="944bd-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="944bd-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="944bd-126">See also</span></span>

- <xref:System.ServiceModel.DeliveryRequirementsAttribute>
