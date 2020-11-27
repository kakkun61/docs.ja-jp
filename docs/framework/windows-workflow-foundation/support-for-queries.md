---
title: クエリのサポート
ms.date: 03/30/2017
ms.assetid: 093c22f5-3294-4642-857a-5252233d6796
ms.openlocfilehash: 350644de4a5deb7b8dcb5133c9cc2edb477fd355
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96258440"
---
# <a name="support-for-queries"></a><span data-ttu-id="10449-102">クエリのサポート</span><span class="sxs-lookup"><span data-stu-id="10449-102">Support for Queries</span></span>

<span data-ttu-id="10449-103">SQL Workflow Instance Store は、一連の既知のプロパティをストアに記録します。</span><span class="sxs-lookup"><span data-stu-id="10449-103">The SQL Workflow Instance Store records a set of well-known properties in the store.</span></span> <span data-ttu-id="10449-104">ユーザーは、これらのプロパティに基づいてインスタンスのクエリを実行できます。</span><span class="sxs-lookup"><span data-stu-id="10449-104">Users can query for instances based on these properties.</span></span> <span data-ttu-id="10449-105">これらの既知のプロパティの一部を次の一覧に示します。</span><span class="sxs-lookup"><span data-stu-id="10449-105">The following list contains some of these well-known properties:</span></span>  
  
- <span data-ttu-id="10449-106">**サイト名。**</span><span class="sxs-lookup"><span data-stu-id="10449-106">**Site Name.**</span></span> <span data-ttu-id="10449-107">サービスが存在する Web サイトの名前。</span><span class="sxs-lookup"><span data-stu-id="10449-107">Name of the Web site that contains the service.</span></span>  
  
- <span data-ttu-id="10449-108">**相対アプリケーション パス:**</span><span class="sxs-lookup"><span data-stu-id="10449-108">**Relative Application Path.**</span></span> <span data-ttu-id="10449-109">Web サイトを基準としたアプリケーションの相対パス。</span><span class="sxs-lookup"><span data-stu-id="10449-109">Path of the application relative to the Web site.</span></span>  
  
- <span data-ttu-id="10449-110">**相対サービス パス:**</span><span class="sxs-lookup"><span data-stu-id="10449-110">**Relative Service Path.**</span></span> <span data-ttu-id="10449-111">アプリケーションを基準としたサービスの相対パス。</span><span class="sxs-lookup"><span data-stu-id="10449-111">Path of the service relative to the application.</span></span>  
  
- <span data-ttu-id="10449-112">**サービス名。**</span><span class="sxs-lookup"><span data-stu-id="10449-112">**Service Name.**</span></span> <span data-ttu-id="10449-113">サービスの名前。</span><span class="sxs-lookup"><span data-stu-id="10449-113">Name of the service.</span></span>  
  
- <span data-ttu-id="10449-114">**サービスの名前空間。**</span><span class="sxs-lookup"><span data-stu-id="10449-114">**Service Namespace.**</span></span> <span data-ttu-id="10449-115">サービスが使用する名前空間の名称。</span><span class="sxs-lookup"><span data-stu-id="10449-115">Name of the namespace that the service uses.</span></span>  
  
- <span data-ttu-id="10449-116">**現在のコンピューター:**</span><span class="sxs-lookup"><span data-stu-id="10449-116">**Current Machine.**</span></span>  
  
- <span data-ttu-id="10449-117">**最後のコンピューター**。</span><span class="sxs-lookup"><span data-stu-id="10449-117">**Last Machine**.</span></span> <span data-ttu-id="10449-118">ワークフロー サービスのインスタンスが最後に実行されたコンピューター。</span><span class="sxs-lookup"><span data-stu-id="10449-118">The computer on which the workflow service instance ran the last time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10449-119">ワークフロー サービス ホストを使用する自己ホスト型のシナリオでは、最後の 4 つのプロパティにのみ値が指定されます。</span><span class="sxs-lookup"><span data-stu-id="10449-119">For self-hosted scenarios using Workflow Service Host, only the last four properties are populated.</span></span> <span data-ttu-id="10449-120">ワークフロー アプリケーション シナリオでは、最後のプロパティにのみ値が指定されます。</span><span class="sxs-lookup"><span data-stu-id="10449-120">For Workflow Application scenarios, only the last property is populated.</span></span>  
  
 <span data-ttu-id="10449-121">ワークフロー ランタイムは、最初の 3 つのプロパティの値を指定します。</span><span class="sxs-lookup"><span data-stu-id="10449-121">The workflow runtime supplies values for the first three properties.</span></span> <span data-ttu-id="10449-122">ワークフローサービスホストは、 **Suspend Reason** プロパティの値を提供します。</span><span class="sxs-lookup"><span data-stu-id="10449-122">The workflow service host supplies the value for the **Suspend Reason** property.</span></span> <span data-ttu-id="10449-123">SQL Workflow Instance Store 自体は、 **最後に更新されたコンピューター** プロパティの値を提供します。</span><span class="sxs-lookup"><span data-stu-id="10449-123">The SQL Workflow Instance Store itself supplies values for the **Last Updated Machine** property.</span></span>  
  
 <span data-ttu-id="10449-124">また、SQL Workflow Instance Store の機能により、永続性データベースで値を格納したり、クエリで使用したりするカスタム プロパティを指定することができます。</span><span class="sxs-lookup"><span data-stu-id="10449-124">The SQL Workflow Instance Store feature also lets you specify the custom properties for which you want to store the values in the persistence database and that you want to use in queries.</span></span> <span data-ttu-id="10449-125">カスタムプロモーションの詳細については、「 [ストアの拡張機能](store-extensibility.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10449-125">For more information about custom promotions, see [Store Extensibility](store-extensibility.md).</span></span>  
  
## <a name="views"></a><span data-ttu-id="10449-126">ビュー</span><span class="sxs-lookup"><span data-stu-id="10449-126">Views</span></span>  

 <span data-ttu-id="10449-127">インスタンス ストアには、次のビューがあります。</span><span class="sxs-lookup"><span data-stu-id="10449-127">The instance store contains the following views.</span></span> <span data-ttu-id="10449-128">詳細については、「 [永続性データベーススキーマ](persistence-database-schema.md) 」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10449-128">See [Persistence Database Schema](persistence-database-schema.md) for further details.</span></span>  
  
### <a name="the-instances-view"></a><span data-ttu-id="10449-129">Instances ビュー</span><span class="sxs-lookup"><span data-stu-id="10449-129">The Instances View</span></span>  

 <span data-ttu-id="10449-130">Instances ビューには、次のフィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="10449-130">The Instances view contains the following fields:</span></span>  
  
1. <span data-ttu-id="10449-131">**Id**</span><span class="sxs-lookup"><span data-stu-id="10449-131">**Id**</span></span>  
  
2. <span data-ttu-id="10449-132">**PendingTimer**</span><span class="sxs-lookup"><span data-stu-id="10449-132">**PendingTimer**</span></span>  
  
3. <span data-ttu-id="10449-133">**CreationTime**</span><span class="sxs-lookup"><span data-stu-id="10449-133">**CreationTime**</span></span>  
  
4. <span data-ttu-id="10449-134">**LastUpdatedTime**</span><span class="sxs-lookup"><span data-stu-id="10449-134">**LastUpdatedTime**</span></span>  
  
5. <span data-ttu-id="10449-135">**ServiceDeploymentId**</span><span class="sxs-lookup"><span data-stu-id="10449-135">**ServiceDeploymentId**</span></span>  
  
6. <span data-ttu-id="10449-136">**SuspensionExceptionName**</span><span class="sxs-lookup"><span data-stu-id="10449-136">**SuspensionExceptionName**</span></span>  
  
7. <span data-ttu-id="10449-137">**SuspensionReason**</span><span class="sxs-lookup"><span data-stu-id="10449-137">**SuspensionReason**</span></span>  
  
8. <span data-ttu-id="10449-138">**ActiveBookmarks**</span><span class="sxs-lookup"><span data-stu-id="10449-138">**ActiveBookmarks**</span></span>  
  
9. <span data-ttu-id="10449-139">**CurrentMachine**</span><span class="sxs-lookup"><span data-stu-id="10449-139">**CurrentMachine**</span></span>  
  
10. <span data-ttu-id="10449-140">**LastMachine**</span><span class="sxs-lookup"><span data-stu-id="10449-140">**LastMachine**</span></span>  
  
11. <span data-ttu-id="10449-141">**ExecutionStatus**</span><span class="sxs-lookup"><span data-stu-id="10449-141">**ExecutionStatus**</span></span>  
  
12. <span data-ttu-id="10449-142">**IsInitialized**</span><span class="sxs-lookup"><span data-stu-id="10449-142">**IsInitialized**</span></span>  
  
13. <span data-ttu-id="10449-143">**IsSuspended**</span><span class="sxs-lookup"><span data-stu-id="10449-143">**IsSuspended**</span></span>  
  
14. <span data-ttu-id="10449-144">**IsCompleted**</span><span class="sxs-lookup"><span data-stu-id="10449-144">**IsCompleted**</span></span>  
  
15. <span data-ttu-id="10449-145">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="10449-145">**EncodingOption**</span></span>  
  
16. <span data-ttu-id="10449-146">**ReadWritePrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="10449-146">**ReadWritePrimitiveDataProperties**</span></span>  
  
17. <span data-ttu-id="10449-147">**WriteOnlyPrimitiveDataProperties**</span><span class="sxs-lookup"><span data-stu-id="10449-147">**WriteOnlyPrimitiveDataProperties**</span></span>  
  
18. <span data-ttu-id="10449-148">**ReadWriteComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="10449-148">**ReadWriteComplexDataProperties**</span></span>  
  
19. <span data-ttu-id="10449-149">**WriteOnlyComplexDataProperties**</span><span class="sxs-lookup"><span data-stu-id="10449-149">**WriteOnlyComplexDataProperties**</span></span>  
  
### <a name="the-servicedeployments-view"></a><span data-ttu-id="10449-150">ServiceDeployments ビュー</span><span class="sxs-lookup"><span data-stu-id="10449-150">The ServiceDeployments view</span></span>  

 <span data-ttu-id="10449-151">ServiceDeployments ビューには、次のフィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="10449-151">The ServiceDeployments view contains the following fields:</span></span>  
  
1. <span data-ttu-id="10449-152">**SiteName**</span><span class="sxs-lookup"><span data-stu-id="10449-152">**SiteName**</span></span>  
  
2. <span data-ttu-id="10449-153">**RelativeServicePath**</span><span class="sxs-lookup"><span data-stu-id="10449-153">**RelativeServicePath**</span></span>  
  
3. <span data-ttu-id="10449-154">**RelativeApplicationPath**</span><span class="sxs-lookup"><span data-stu-id="10449-154">**RelativeApplicationPath**</span></span>  
  
4. <span data-ttu-id="10449-155">**ServiceName**</span><span class="sxs-lookup"><span data-stu-id="10449-155">**ServiceName**</span></span>  
  
5. <span data-ttu-id="10449-156">**ServiceNamespace**</span><span class="sxs-lookup"><span data-stu-id="10449-156">**ServiceNamespace**</span></span>  
  
### <a name="the-instancepromotedproperties-view"></a><span data-ttu-id="10449-157">InstancePromotedProperties ビュー</span><span class="sxs-lookup"><span data-stu-id="10449-157">The InstancePromotedProperties view</span></span>  

 <span data-ttu-id="10449-158">InstancePromotedProperties ビューには、次のフィールドがあります。</span><span class="sxs-lookup"><span data-stu-id="10449-158">The InstancePromotedProperties view contains the following fields.</span></span> <span data-ttu-id="10449-159">昇格させたプロパティの詳細については、 [ストアの機能拡張](store-extensibility.md) に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="10449-159">For details on promoted properties, see the [Store Extensibility](store-extensibility.md) topic.</span></span>  
  
1. <span data-ttu-id="10449-160">**InstanceId**</span><span class="sxs-lookup"><span data-stu-id="10449-160">**InstanceId**</span></span>  
  
2. <span data-ttu-id="10449-161">**EncodingOption**</span><span class="sxs-lookup"><span data-stu-id="10449-161">**EncodingOption**</span></span>  
  
3. <span data-ttu-id="10449-162">**PromotionName**</span><span class="sxs-lookup"><span data-stu-id="10449-162">**PromotionName**</span></span>  
  
4. <span data-ttu-id="10449-163">**値 #** ( **Value1** から **Value64** までのフィールドの範囲)。</span><span class="sxs-lookup"><span data-stu-id="10449-163">**Value#** (a range of fields from **Value1** to **Value64**).</span></span>
