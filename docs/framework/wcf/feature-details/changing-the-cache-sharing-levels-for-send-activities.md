---
title: Send アクティビティのキャッシュ共有レベルの変更
ms.date: 03/30/2017
ms.assetid: 03926a64-753d-460e-ac06-2a4ff8e1bbf5
ms.openlocfilehash: cbb937ac47c93307db922b28e3df0ea694a77960
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262049"
---
# <a name="changing-the-cache-sharing-levels-for-send-activities"></a><span data-ttu-id="e126d-102">Send アクティビティのキャッシュ共有レベルの変更</span><span class="sxs-lookup"><span data-stu-id="e126d-102">Changing the Cache Sharing Levels for Send Activities</span></span>

<span data-ttu-id="e126d-103"><xref:System.ServiceModel.Activities.SendMessageChannelCache> 拡張機能により、キャッシュ共有レベルのカスタマイズやチャネル ファクトリ キャッシュの設定のカスタマイズを行えるほか、<xref:System.ServiceModel.Activities.Send> メッセージング アクティビティを使用してサービス エンドポイントにメッセージを送信するワークフローのチャネル キャッシュの設定のカスタマイズも可能になります。</span><span class="sxs-lookup"><span data-stu-id="e126d-103">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension enables you to customize the cache sharing levels, the settings of the channel factory cache, and the settings of the channel cache for workflows that send messages to service endpoints using <xref:System.ServiceModel.Activities.Send> messaging activities.</span></span> <span data-ttu-id="e126d-104">これらのワークフローは、通常はクライアント ワークフローですが、<xref:System.ServiceModel.WorkflowServiceHost> でホストされるワークフロー サービスである場合もあります。</span><span class="sxs-lookup"><span data-stu-id="e126d-104">These workflows are typically client workflows but could also be workflow services that are hosted in a <xref:System.ServiceModel.WorkflowServiceHost>.</span></span> <span data-ttu-id="e126d-105">チャネル ファクトリ キャッシュには、<xref:System.ServiceModel.ChannelFactory%601> オブジェクトがキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="e126d-105">The channel factory cache contains cached <xref:System.ServiceModel.ChannelFactory%601> objects.</span></span> <span data-ttu-id="e126d-106">チャネル キャッシュには、チャネルがキャッシュされます。</span><span class="sxs-lookup"><span data-stu-id="e126d-106">The channel cache contains cached channels.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e126d-107">ワークフローは <xref:System.ServiceModel.Activities.Send> メッセージング アクティビティを使用してメッセージまたはパラメーターを送信できます。</span><span class="sxs-lookup"><span data-stu-id="e126d-107">Workflows can use <xref:System.ServiceModel.Activities.Send> messaging activities to send either messages or parameters.</span></span> <span data-ttu-id="e126d-108">このワークフローのランタイムはチャネル ファクトリをキャッシュに追加しますが、チャネル ファクトリで作成されるチャネルは、<xref:System.ServiceModel.Channels.IRequestChannel> アクティビティを <xref:System.ServiceModel.Activities.ReceiveReply> アクティビティと共に使用したときは <xref:System.ServiceModel.Activities.Send> 型で、<xref:System.ServiceModel.Channels.IOutputChannel> アクティビティだけを (<xref:System.ServiceModel.Activities.Send> なしで) 使用したときは <xref:System.ServiceModel.Activities.ReceiveReply> 型です。</span><span class="sxs-lookup"><span data-stu-id="e126d-108">The workflow runtime adds channel factories to the cache that create channels of type <xref:System.ServiceModel.Channels.IRequestChannel> when you use a <xref:System.ServiceModel.Activities.ReceiveReply> activity with a <xref:System.ServiceModel.Activities.Send> activity, and an <xref:System.ServiceModel.Channels.IOutputChannel> when just using a <xref:System.ServiceModel.Activities.Send> activity (no <xref:System.ServiceModel.Activities.ReceiveReply>).</span></span>  
  
## <a name="the-cache-sharing-levels"></a><span data-ttu-id="e126d-109">キャッシュ共有レベル</span><span class="sxs-lookup"><span data-stu-id="e126d-109">The Cache Sharing Levels</span></span>  

 <span data-ttu-id="e126d-110">既定では、<xref:System.ServiceModel.WorkflowServiceHost> によってホストされるワークフローにおいて、<xref:System.ServiceModel.Activities.Send> メッセージング アクティビティが使用するキャッシュは <xref:System.ServiceModel.WorkflowServiceHost> のすべてのワークフロー インスタンス間で共有されます (ホストレベルのキャッシュ)。</span><span class="sxs-lookup"><span data-stu-id="e126d-110">By default, in a workflow hosted by a <xref:System.ServiceModel.WorkflowServiceHost> the cache used by <xref:System.ServiceModel.Activities.Send> messaging activities is shared across all workflow instances in the <xref:System.ServiceModel.WorkflowServiceHost> (host-level caching).</span></span> <span data-ttu-id="e126d-111"><xref:System.ServiceModel.WorkflowServiceHost> によってホストされないクライアント ワークフローの場合、キャッシュを使用できるのはワークフロー インスタンスだけです (インスタンスレベルのキャッシュ)。</span><span class="sxs-lookup"><span data-stu-id="e126d-111">For a client workflow that is not hosted by a <xref:System.ServiceModel.WorkflowServiceHost>, the cache is available only to the workflow instance (instance-level caching).</span></span> <span data-ttu-id="e126d-112">このキャッシュは、アンセーフ キャッシュが有効になっている場合を除き、構成で定義されているエンドポイントを使用しない <xref:System.ServiceModel.Activities.Send> アクティビティに対してのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="e126d-112">The cache is only available for <xref:System.ServiceModel.Activities.Send> activities that do not use endpoints defined in configuration unless unsafe caching is enabled.</span></span>  
  
 <span data-ttu-id="e126d-113">ワークフローの <xref:System.ServiceModel.Activities.Send> アクティビティに使用可能なさまざまなキャッシュ共有レベルと、推奨される使用方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e126d-113">The following are the different cache sharing levels available for <xref:System.ServiceModel.Activities.Send> activities in a workflow and their recommended use:</span></span>  
  
- <span data-ttu-id="e126d-114">**ホストレベル**: ホスト共有レベルでは、キャッシュは、ワークフローサービスホストでホストされているワークフローインスタンスでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="e126d-114">**Host Level**: In the host sharing level, the cache is available only to the workflow instances hosted in the workflow service host.</span></span> <span data-ttu-id="e126d-115">キャッシュはプロセス全体のキャッシュのワークフロー サービス ホスト間で共有できます。</span><span class="sxs-lookup"><span data-stu-id="e126d-115">A cache can also be shared between workflow service hosts in a process-wide cache.</span></span>  
  
- <span data-ttu-id="e126d-116">**インスタンスレベル**: インスタンスの共有レベルでは、特定のワークフローインスタンスが有効期間中はキャッシュを使用できますが、他のワークフローインスタンスはキャッシュを使用できません。</span><span class="sxs-lookup"><span data-stu-id="e126d-116">**Instance Level**: In the instance sharing level, the cache is available to a particular workflow instance throughout its lifetime but the cache is not available to other workflow instances.</span></span>  
  
- <span data-ttu-id="e126d-117">**キャッシュなし**: 構成で定義されたエンドポイントを使用するワークフローがある場合、キャッシュは既定でオフになっています。</span><span class="sxs-lookup"><span data-stu-id="e126d-117">**No Cache**: The cache is turned off by default if you have a workflow that uses endpoints defined in configuration.</span></span> <span data-ttu-id="e126d-118">この場合、キャッシュをオンにすると安全性が損なわれることがあるため、オフにしておくことをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="e126d-118">It is also recommended to keep the cache turned off in this case because turning it on could be unsecure.</span></span> <span data-ttu-id="e126d-119">たとえば、送信ごとに異なる ID (異なる資格情報、または偽装の使用) が必要な場合があります。</span><span class="sxs-lookup"><span data-stu-id="e126d-119">For example, if a different identity (different credentials or using impersonation) is required for each send.</span></span>  
  
## <a name="changing-the-cache-sharing-level-for-a-client-workflow"></a><span data-ttu-id="e126d-120">クライアント ワークフローのキャッシュ共有レベルの変更</span><span class="sxs-lookup"><span data-stu-id="e126d-120">Changing the Cache Sharing Level for a Client Workflow</span></span>  

 <span data-ttu-id="e126d-121">クライアント ワークフローでのキャッシュの共有を設定するには、<xref:System.ServiceModel.Activities.SendMessageChannelCache> クラスのインスタンスを目的のワークフロー インスタンスのセットに拡張として追加します。</span><span class="sxs-lookup"><span data-stu-id="e126d-121">To set the cache sharing in a client workflow, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to the desired set of workflow instances.</span></span> <span data-ttu-id="e126d-122">この結果、すべてのワークフロー インスタンス間でキャッシュが共有されます。</span><span class="sxs-lookup"><span data-stu-id="e126d-122">This results in sharing the cache across all the workflow instances.</span></span> <span data-ttu-id="e126d-123">次のコード例は、この手順を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e126d-123">The following code examples show how to perform these steps.</span></span>  
  
 <span data-ttu-id="e126d-124">まず、<xref:System.ServiceModel.Activities.SendMessageChannelCache> 型のインスタンスを宣言します。</span><span class="sxs-lookup"><span data-stu-id="e126d-124">First, declare an instance of type <xref:System.ServiceModel.Activities.SendMessageChannelCache>.</span></span>  
  
```csharp  
// Create an instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension =  
    new SendMessageChannelCache();  
```  
  
 <span data-ttu-id="e126d-125">次に、各クライアント ワークフローのインスタンスにキャッシュ拡張を追加します。</span><span class="sxs-lookup"><span data-stu-id="e126d-125">Next, add the cache extension to each client workflow instance.</span></span>  
  
```csharp
WorkflowApplication clientInstance1 = new WorkflowApplication(new clientWorkflow1());  
WorkflowApplication clientInstance2 = new WorkflowApplication(new clientWorkflow2());  
  
// Share the cache extension object
  
clientInstance1.Extensions.Add(sharedChannelCacheExtension);  
clientInstance2.Extensions.Add(sharedChannelCacheExtension);  
```  
  
## <a name="changing-the-cache-sharing-level-for-a-hosted-workflow-service"></a><span data-ttu-id="e126d-126">ホストされるワークフロー サービスのキャッシュ共有レベルの変更</span><span class="sxs-lookup"><span data-stu-id="e126d-126">Changing the Cache Sharing Level for a Hosted Workflow Service</span></span>  

 <span data-ttu-id="e126d-127">ホストされるワークフロー サービスでのキャッシュの共有を設定するには、<xref:System.ServiceModel.Activities.SendMessageChannelCache> クラスのインスタンスをすべてのワークフロー サービス ホストに拡張として追加します。</span><span class="sxs-lookup"><span data-stu-id="e126d-127">To set the cache sharing in a hosted workflow service, add an instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class as an extension to all the workflow service hosts.</span></span> <span data-ttu-id="e126d-128">この結果、すべてのワークフロー サービス ホスト間でキャッシュが共有されます。</span><span class="sxs-lookup"><span data-stu-id="e126d-128">This results in sharing the cache across all the workflow service hosts.</span></span> <span data-ttu-id="e126d-129">次のコード例は、この手順を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e126d-129">The following code examples show to perform these steps.</span></span>  
  
 <span data-ttu-id="e126d-130">まず、<xref:System.ServiceModel.Activities.SendMessageChannelCache> 型のインスタンスをクラス レベルで宣言します。</span><span class="sxs-lookup"><span data-stu-id="e126d-130">First, declare an instance  of type <xref:System.ServiceModel.Activities.SendMessageChannelCache> at the class level.</span></span>  
  
```csharp  
// Create static instance of SendMessageChannelCache with default cache settings.  
static SendMessageChannelCache sharedChannelCacheExtension = new  
    SendMessageChannelCache();  
```  
  
 <span data-ttu-id="e126d-131">次に、各ワークフロー サービス ホストに静的キャッシュ拡張を追加します。</span><span class="sxs-lookup"><span data-stu-id="e126d-131">Next, add the static cache extension to each workflow service host.</span></span>  
  
```csharp  
WorkflowServiceHost host1 = new WorkflowServiceHost(new serviceWorkflow1(), new Uri(baseAddress1));  
WorkflowServiceHost host2 = new WorkflowServiceHost(new serviceWorkflow2(), new Uri(baseAddress2));  
  
// Share the static cache to get an AppDomain level cache.  
host1.WorkflowExtensions.Add(sharedChannelCacheExtension);  
host2.WorkflowExtensions.Add(sharedChannelCacheExtension);  
```  
  
 <span data-ttu-id="e126d-132">ホストされるワークフロー サービスでのキャッシュ共有をインスタンス レベルに設定するには、`Func<SendMessageChannelCache>` デリゲートをワークフロー サービス ホストに拡張として追加し、<xref:System.ServiceModel.Activities.SendMessageChannelCache> クラスの新しいインスタンスをインスタンス化するコードにこのデリゲートを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="e126d-132">To set the cache sharing in a hosted workflow service to the instance level, add a `Func<SendMessageChannelCache>` delegate as an extension to the workflow service host and assign this delegate to the code that instantiates a new instance of the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class.</span></span> <span data-ttu-id="e126d-133">この結果、ワークフロー サービス ホストのすべてのワークフロー インスタンスで 1 つのキャッシュが共有されるのではなく、ワークフロー インスタンスごとに異なるキャッシュが使用されます。</span><span class="sxs-lookup"><span data-stu-id="e126d-133">This results in a different cache for each individual workflow instance, instead of a single cache shared by all workflow instances in the workflow service host.</span></span> <span data-ttu-id="e126d-134">次のコード例は、このデリゲートがポイントする <xref:System.ServiceModel.Activities.SendMessageChannelCache> 拡張を直接定義するラムダ式を使用して上記の処理を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e126d-134">The following code example shows how to achieve this by using a lambda expression to directly define the <xref:System.ServiceModel.Activities.SendMessageChannelCache> extension that the delegate points to.</span></span>  
  
```csharp
serviceHost.WorkflowExtensions.Add(() => new SendMessageChannelCache  
{  
    // Use FactorySettings property to add custom factory cache settings.  
    FactorySettings = new ChannelCacheSettings
    { MaxItemsInCache = 5, },  
    // Use ChannelSettings property to add custom channel cache settings.  
    ChannelSettings = new ChannelCacheSettings
    { MaxItemsInCache = 10 },  
});  
```  
  
## <a name="customizing-cache-settings"></a><span data-ttu-id="e126d-135">キャッシュ設定のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="e126d-135">Customizing Cache Settings</span></span>  

 <span data-ttu-id="e126d-136">チャネル ファクトリ キャッシュおよびチャネル キャッシュのキャッシュ設定をカスタマイズできます。</span><span class="sxs-lookup"><span data-stu-id="e126d-136">You can customize the cache settings for the channel factory cache and the channel cache.</span></span> <span data-ttu-id="e126d-137">キャッシュ設定は <xref:System.ServiceModel.Activities.ChannelCacheSettings> クラスで定義されています。</span><span class="sxs-lookup"><span data-stu-id="e126d-137">The cache settings are defined in the <xref:System.ServiceModel.Activities.ChannelCacheSettings> class.</span></span> <span data-ttu-id="e126d-138">クラスは、 <xref:System.ServiceModel.Activities.SendMessageChannelCache> チャネルファクトリキャッシュの既定のキャッシュ設定と、パラメーターなしのコンストラクターのチャネルキャッシュを定義します。</span><span class="sxs-lookup"><span data-stu-id="e126d-138">The <xref:System.ServiceModel.Activities.SendMessageChannelCache> class defines default cache settings for the channel factory cache and the channel cache in its parameterless constructor.</span></span> <span data-ttu-id="e126d-139">次の表は、これらのキャッシュ設定の既定値をキャッシュのタイプごとに示しています。</span><span class="sxs-lookup"><span data-stu-id="e126d-139">The following table lists the default values of these cache settings for each type of cache.</span></span>  
  
|<span data-ttu-id="e126d-140">Settings</span><span class="sxs-lookup"><span data-stu-id="e126d-140">Settings</span></span>|<span data-ttu-id="e126d-141">LeaseTimeout (分)</span><span class="sxs-lookup"><span data-stu-id="e126d-141">LeaseTimeout (min)</span></span>|<span data-ttu-id="e126d-142">IdleTimeout (分)</span><span class="sxs-lookup"><span data-stu-id="e126d-142">IdleTimeout (min)</span></span>|<span data-ttu-id="e126d-143">MaxItemsInCache</span><span class="sxs-lookup"><span data-stu-id="e126d-143">MaxItemsInCache</span></span>|  
|-|-|-|-|  
|<span data-ttu-id="e126d-144">ファクトリ キャッシュの既定値</span><span class="sxs-lookup"><span data-stu-id="e126d-144">Factory Cache Default</span></span>|<span data-ttu-id="e126d-145">TimeSpan.MaxValue</span><span class="sxs-lookup"><span data-stu-id="e126d-145">TimeSpan.MaxValue</span></span>|<span data-ttu-id="e126d-146">2</span><span class="sxs-lookup"><span data-stu-id="e126d-146">2</span></span>|<span data-ttu-id="e126d-147">16</span><span class="sxs-lookup"><span data-stu-id="e126d-147">16</span></span>|  
|<span data-ttu-id="e126d-148">チャネル キャッシュの既定値</span><span class="sxs-lookup"><span data-stu-id="e126d-148">Channel Cache Default</span></span>|<span data-ttu-id="e126d-149">5</span><span class="sxs-lookup"><span data-stu-id="e126d-149">5</span></span>|<span data-ttu-id="e126d-150">2</span><span class="sxs-lookup"><span data-stu-id="e126d-150">2</span></span>|<span data-ttu-id="e126d-151">16</span><span class="sxs-lookup"><span data-stu-id="e126d-151">16</span></span>|  
  
 <span data-ttu-id="e126d-152">ファクトリ キャッシュおよびチャネル キャッシュの設定をカスタマイズするには、パラメーター化されたコンストラクター <xref:System.ServiceModel.Activities.SendMessageChannelCache> を使用して <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> クラスをインスタンス化し、<xref:System.ServiceModel.Activities.ChannelCacheSettings> の新しいインスタンスをカスタム値と共に `factorySettings` パラメーターおよび `channelSettings` パラメーターにそれぞれ渡します。</span><span class="sxs-lookup"><span data-stu-id="e126d-152">To customize the factory cache and channel cache settings, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> and pass a new instance of the <xref:System.ServiceModel.Activities.ChannelCacheSettings> with custom values to each of the `factorySettings` and `channelSettings` parameters.</span></span> <span data-ttu-id="e126d-153">次に、このクラスの新しいインスタンスをワークフロー サービス ホストまたはワークフロー インスタンスに拡張として追加します。</span><span class="sxs-lookup"><span data-stu-id="e126d-153">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="e126d-154">次のコード例は、ワークフロー インスタンスに対してこの手順を実行する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e126d-154">The following code example shows how to perform these steps for a workflow instance.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,
                        IdleTimeout = TimeSpan.FromMinutes(5),
                        LeaseTimeout = TimeSpan.FromMinutes(20)};  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings{  
                        MaxItemsInCache = 5,
                        IdleTimeout = TimeSpan.FromMinutes(2),  
                        LeaseTimeout = TimeSpan.FromMinutes(10) };  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="e126d-155">構成で定義されているエンドポイントがワークフロー サービスにある場合にキャッシュを有効にするには、<xref:System.ServiceModel.Activities.SendMessageChannelCache> パラメーターが <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> に設定された、パラメーター化されたコンストラクター `allowUnsafeCaching` を使用して `true` クラスをインスタンス化します。</span><span class="sxs-lookup"><span data-stu-id="e126d-155">To enable caching when your workflow service has endpoints defined in configuration, instantiate the <xref:System.ServiceModel.Activities.SendMessageChannelCache> class using the parameterized constructor <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> with the `allowUnsafeCaching` parameter set to `true`.</span></span> <span data-ttu-id="e126d-156">次に、このクラスの新しいインスタンスをワークフロー サービス ホストまたはワークフロー インスタンスに拡張として追加します。</span><span class="sxs-lookup"><span data-stu-id="e126d-156">Next, add the new instance of this class as an extension to a workflow service host or a workflow instance.</span></span> <span data-ttu-id="e126d-157">次のコード例は、ワークフロー インスタンスのキャッシュを有効にする方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="e126d-157">The following code example shows how to enable caching for a workflow instance.</span></span>  
  
```csharp  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache{ AllowUnsafeCaching = true };  
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="e126d-158">チャネル ファクトリおよびチャネルのキャッシュを完全に無効にするには、チャネル ファクトリ キャッシュを無効にします。</span><span class="sxs-lookup"><span data-stu-id="e126d-158">To disable the cache completely for the channel factories and the channels, disable the channel factory cache.</span></span> <span data-ttu-id="e126d-159">こうすると、対応するチャネル ファクトリにチャネルが所有されるので、チャネル キャッシュもオフになります。</span><span class="sxs-lookup"><span data-stu-id="e126d-159">Doing so also turns off the channel cache as the channels are owned by their corresponding channel factories.</span></span> <span data-ttu-id="e126d-160">チャネル ファクトリ キャッシュを無効にするには、`factorySettings` 値が 0 の <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> インスタンスに初期化された <xref:System.ServiceModel.Activities.ChannelCacheSettings> コンストラクターに <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> パラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="e126d-160">To disable the channel factory cache, pass the `factorySettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="e126d-161">このコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e126d-161">The following code example shows this.</span></span>  
  
```csharp  
// Disable the factory cache. This results in the channel cache to be turned off as well.  
ChannelCacheSettings factorySettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0 };  
  
ChannelCacheSettings channelSettings = new ChannelCacheSettings();  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="e126d-162">チャネル ファクトリ キャッシュのみを使用し、チャネル キャッシュを無効にするには、`channelSettings` 値が 0 の <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> インスタンスに初期化された <xref:System.ServiceModel.Activities.ChannelCacheSettings> コンストラクターに <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> パラメーターを渡します。</span><span class="sxs-lookup"><span data-stu-id="e126d-162">You can choose to use only the channel factory cache and disable the channel cache by passing the `channelSettings` parameter to the <xref:System.ServiceModel.Activities.SendMessageChannelCache.%23ctor%2A> constructor initialized to a <xref:System.ServiceModel.Activities.ChannelCacheSettings> instance with a <xref:System.ServiceModel.Activities.ChannelCacheSettings.MaxItemsInCache%2A> value of 0.</span></span> <span data-ttu-id="e126d-163">このコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e126d-163">The following code example shows this.</span></span>  
  
```csharp  
ChannelCacheSettings factorySettings = new ChannelCacheSettings();  
// Disable only the channel cache.  
ChannelCacheSettings channelSettings = new ChannelCacheSettings  
    { MaxItemsInCache = 0};  
  
SendMessageChannelCache customChannelCacheExtension =
    new SendMessageChannelCache(factorySettings, channelSettings);
  
clientInstance.Extensions.Add(customChannelCacheExtension);  
```  
  
 <span data-ttu-id="e126d-164">ホストされたワークフロー サービスでは、ファクトリ キャッシュとチャネル キャッシュの設定をアプリケーション構成ファイルで指定できます。</span><span class="sxs-lookup"><span data-stu-id="e126d-164">In a hosted workflow service, you can specify the factory cache and channel cache settings in the application configuration file.</span></span> <span data-ttu-id="e126d-165">これを行うには、ファクトリ キャッシュおよびチャネル キャッシュのキャッシュ設定を含むサービス動作を追加し、そのサービス動作をサービスに追加します。</span><span class="sxs-lookup"><span data-stu-id="e126d-165">To do so, add a service behavior that contains the cache settings for the factory and channel cache and add this service behavior to your service.</span></span> <span data-ttu-id="e126d-166">次の例は、 `MyChannelCacheBehavior` カスタムファクトリキャッシュとチャネルキャッシュ設定を使用したサービス動作を含む構成ファイルの内容を示しています。</span><span class="sxs-lookup"><span data-stu-id="e126d-166">The following example shows the contents of a configuration file that contains the `MyChannelCacheBehavior` service behavior with the custom factory cache and channel cache settings.</span></span> <span data-ttu-id="e126d-167">このサービス動作は、属性を通じてサービスに追加され `behaviorConfiguration` ます。</span><span class="sxs-lookup"><span data-stu-id="e126d-167">This service behavior is added to the service through the `behaviorConfiguration` attribute.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>  
    <!-- List of other config sections here -->
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="MyChannelCacheBehavior">  
          <sendMessageChannelCache allowUnsafeCaching ="false" >  
            <!-- Control only the host level settings -->
            <factorySettings maxItemsInCache = "8" idleTimeout = "00:05:00" leaseTimeout="10:00:00" />  
            <channelSettings maxItemsInCache = "32" idleTimeout = "00:05:00" leaseTimeout="00:06:00" />  
          </sendMessageChannelCache>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="MyService" behaviorConfiguration="MyChannelCacheBehavior" />  
    </services>  
  </system.serviceModel>  
</configuration>  
```
