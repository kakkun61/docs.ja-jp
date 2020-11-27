---
title: OperationBehaviorAttribute
ms.date: 03/30/2017
ms.assetid: 8c9b0755-9e83-411f-bdcb-61a586022797
ms.openlocfilehash: 76cc619aed4ba2b944a8d11dc454a40368a4068c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96269081"
---
# <a name="operationbehaviorattribute"></a><span data-ttu-id="ffe52-102">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="ffe52-102">OperationBehaviorAttribute</span></span>

<span data-ttu-id="ffe52-103">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="ffe52-103">OperationBehaviorAttribute</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ffe52-104">構文</span><span class="sxs-lookup"><span data-stu-id="ffe52-104">Syntax</span></span>  
  
```csharp
class OperationBehaviorAttribute : Behavior  
{  
  boolean AutoDisposeParameters;  
  string Impersonation;  
  string ReleaseInstanceMode;  
  boolean TransactionAutoComplete;  
  boolean TransactionScopeRequired;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ffe52-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ffe52-105">Methods</span></span>  

 <span data-ttu-id="ffe52-106">OperationBehaviorAttribute クラスで定義されるメソッドはありません。</span><span class="sxs-lookup"><span data-stu-id="ffe52-106">The OperationBehaviorAttribute class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ffe52-107">プロパティ</span><span class="sxs-lookup"><span data-stu-id="ffe52-107">Properties</span></span>  

 <span data-ttu-id="ffe52-108">OperationBehaviorAttribute クラスには、次のプロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="ffe52-108">The OperationBehaviorAttribute class has the following properties:</span></span>  
  
### <a name="autodisposeparameters"></a><span data-ttu-id="ffe52-109">AutoDisposeParameters</span><span class="sxs-lookup"><span data-stu-id="ffe52-109">AutoDisposeParameters</span></span>  

 <span data-ttu-id="ffe52-110">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="ffe52-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="ffe52-111">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffe52-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffe52-112">パラメーターの自動破棄機能の状態です。</span><span class="sxs-lookup"><span data-stu-id="ffe52-112">The state of the auto-dispose feature for parameters.</span></span>  
  
### <a name="impersonation"></a><span data-ttu-id="ffe52-113">偽装</span><span class="sxs-lookup"><span data-stu-id="ffe52-113">Impersonation</span></span>  

 <span data-ttu-id="ffe52-114">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="ffe52-114">Data type: string</span></span>  
  
 <span data-ttu-id="ffe52-115">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffe52-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffe52-116">操作がサポートする、呼び出し元の偽装レベルを示します。</span><span class="sxs-lookup"><span data-stu-id="ffe52-116">Indicates the level of caller impersonation that the operation supports.</span></span>  
  
### <a name="releaseinstancemode"></a><span data-ttu-id="ffe52-117">ReleaseInstanceMode</span><span class="sxs-lookup"><span data-stu-id="ffe52-117">ReleaseInstanceMode</span></span>  

 <span data-ttu-id="ffe52-118">データ型: 文字列</span><span class="sxs-lookup"><span data-stu-id="ffe52-118">Data type: string</span></span>  
  
 <span data-ttu-id="ffe52-119">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffe52-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffe52-120">操作の呼び出し過程のどの時点でオブジェクトをリサイクルするかを示します。</span><span class="sxs-lookup"><span data-stu-id="ffe52-120">Indicates when in the course of an operation invocation to recycle the object.</span></span>  
  
### <a name="transactionautocomplete"></a><span data-ttu-id="ffe52-121">TransactionAutoComplete</span><span class="sxs-lookup"><span data-stu-id="ffe52-121">TransactionAutoComplete</span></span>  

 <span data-ttu-id="ffe52-122">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="ffe52-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="ffe52-123">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffe52-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffe52-124">未処理の例外が発生しなかった場合に、現在のトランザクションを自動的にコミットするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="ffe52-124">Indicates whether to automatically commit the current transaction if no unhandled exceptions occur.</span></span>  
  
### <a name="transactionscoperequired"></a><span data-ttu-id="ffe52-125">TransactionScopeRequired</span><span class="sxs-lookup"><span data-stu-id="ffe52-125">TransactionScopeRequired</span></span>  

 <span data-ttu-id="ffe52-126">データ型 : boolean</span><span class="sxs-lookup"><span data-stu-id="ffe52-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="ffe52-127">アクセスの種類: 読み取り専用</span><span class="sxs-lookup"><span data-stu-id="ffe52-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ffe52-128">操作がトランザクションを必要とするかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="ffe52-128">Indicates whether the operation requires a transaction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ffe52-129">要件</span><span class="sxs-lookup"><span data-stu-id="ffe52-129">Requirements</span></span>  
  
|<span data-ttu-id="ffe52-130">MOF</span><span class="sxs-lookup"><span data-stu-id="ffe52-130">MOF</span></span>|<span data-ttu-id="ffe52-131">Servicemodel.mof にて宣言済み。</span><span class="sxs-lookup"><span data-stu-id="ffe52-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ffe52-132">名前空間</span><span class="sxs-lookup"><span data-stu-id="ffe52-132">Namespace</span></span>|<span data-ttu-id="ffe52-133">root\ServiceModel で定義</span><span class="sxs-lookup"><span data-stu-id="ffe52-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ffe52-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffe52-134">See also</span></span>

- <xref:System.ServiceModel.OperationBehaviorAttribute>
