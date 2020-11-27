---
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: 867219130fc853f3ba2c1c2f807b1651f6480f13
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273972"
---
# <a name="servicetimeoutsbehavior"></a><span data-ttu-id="a448a-102">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="a448a-102">ServiceTimeoutsBehavior</span></span>

<span data-ttu-id="a448a-103">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="a448a-103">ServiceTimeoutsBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a448a-104">構文</span><span class="sxs-lookup"><span data-stu-id="a448a-104">Syntax</span></span>  
  
```csharp
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="a448a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a448a-105">Methods</span></span>  

 <span data-ttu-id="a448a-106">ServiceTimeoutsBehavior クラスは、メソッドを一切定義しません。</span><span class="sxs-lookup"><span data-stu-id="a448a-106">The ServiceTimeoutsBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="a448a-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="a448a-107">Properties</span></span>  

 <span data-ttu-id="a448a-108">ServiceTimeoutsBehavior クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="a448a-108">The ServiceTimeoutsBehavior class has the following property:</span></span>  
  
### <a name="transactiontimeout"></a><span data-ttu-id="a448a-109">TransactionTimeout</span><span class="sxs-lookup"><span data-stu-id="a448a-109">TransactionTimeout</span></span>  

 <span data-ttu-id="a448a-110">データ型 : datetime</span><span class="sxs-lookup"><span data-stu-id="a448a-110">Data type: datetime</span></span>  
  
 <span data-ttu-id="a448a-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="a448a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="a448a-112">トランザクションを完了しなければならない期間。</span><span class="sxs-lookup"><span data-stu-id="a448a-112">The period within which a transaction must complete.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a448a-113">要件</span><span class="sxs-lookup"><span data-stu-id="a448a-113">Requirements</span></span>  
  
|<span data-ttu-id="a448a-114">MOF</span><span class="sxs-lookup"><span data-stu-id="a448a-114">MOF</span></span>|<span data-ttu-id="a448a-115">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="a448a-115">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="a448a-116">名前空間</span><span class="sxs-lookup"><span data-stu-id="a448a-116">Namespace</span></span>|<span data-ttu-id="a448a-117">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="a448a-117">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a448a-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a448a-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
