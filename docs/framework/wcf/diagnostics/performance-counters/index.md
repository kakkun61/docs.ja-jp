---
title: WCF パフォーマンス カウンター
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters [WCF]
ms.assetid: f559b2bd-ed83-4988-97a1-e88f06646609
ms.openlocfilehash: a5b00980cb8c2b06b224630e766e49bafe343c76
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266104"
---
# <a name="wcf-performance-counters"></a><span data-ttu-id="41284-102">WCF パフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="41284-102">WCF Performance Counters</span></span>

<span data-ttu-id="41284-103">Windows Communication Foundation (WCF) には、アプリケーションのパフォーマンスを測定するのに役立つ多数のパフォーマンスカウンターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="41284-103">Windows Communication Foundation (WCF) includes a large set of performance counters to help you gauge your application's performance.</span></span>  
  
## <a name="enabling-performance-counters"></a><span data-ttu-id="41284-104">パフォーマンス カウンターの有効化</span><span class="sxs-lookup"><span data-stu-id="41284-104">Enabling Performance Counters</span></span>  

 <span data-ttu-id="41284-105">Wcf サービスのパフォーマンスカウンターを有効にするには、次のように、WCF サービスの app.config 構成ファイルを使用します。</span><span class="sxs-lookup"><span data-stu-id="41284-105">You can enable performance counters for a WCF service through the app.config configuration file of the WCF service as follows:</span></span>  
  
```xml  
<configuration>  
    <system.serviceModel>  
        <diagnostics performanceCounters="All" />  
    </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="41284-106">特定の種類のパフォーマンス カウンターを有効にするよう `performanceCounters` 属性を設定できます。</span><span class="sxs-lookup"><span data-stu-id="41284-106">The `performanceCounters` attribute can be set to enable a specific type of performance counters.</span></span> <span data-ttu-id="41284-107">有効な値は、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="41284-107">Valid values are</span></span>  
  
- <span data-ttu-id="41284-108">All : すべてのカテゴリ カウンター (ServiceModelService、ServiceModelEndpoint、ServiceModelOperation) を有効にします。</span><span class="sxs-lookup"><span data-stu-id="41284-108">All: All category counters (ServiceModelService, ServiceModelEndpoint and ServiceModelOperation) are enabled.</span></span>  
  
- <span data-ttu-id="41284-109">ServiceOnly : ServiceModelService カテゴリ カウンターのみを有効にします。</span><span class="sxs-lookup"><span data-stu-id="41284-109">ServiceOnly: Only ServiceModelService category counters are enabled.</span></span> <span data-ttu-id="41284-110">これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="41284-110">This is the default value.</span></span>  
  
- <span data-ttu-id="41284-111">Off : ServiceModel\* パフォーマンス カウンターを無効にします。</span><span class="sxs-lookup"><span data-stu-id="41284-111">Off: ServiceModel\* performance counters are disabled.</span></span>  
  
 <span data-ttu-id="41284-112">すべての WCF アプリケーションでパフォーマンスカウンターを有効にする場合は、構成設定を Machine.config ファイルに配置します。</span><span class="sxs-lookup"><span data-stu-id="41284-112">If you want to enable performance counters for all WCF applications, you can place the configuration settings in the Machine.config file.</span></span>  <span data-ttu-id="41284-113">コンピューターのパフォーマンスカウンター用に十分なメモリを構成する方法の詳細については、後述の「 **パフォーマンスカウンターのメモリサイズの増加** 」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="41284-113">Please see the **Increasing Memory Size for Performance Counters** section below for more information on configuring sufficient memory for performance counters on your machine.</span></span>  
  
 <span data-ttu-id="41284-114">カスタム操作の呼び出し元などの WCF 機能拡張ポイントを使用する場合は、独自のパフォーマンスカウンターも生成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="41284-114">If you use WCF extensibility points such as custom operation invokers, you should also emit your own performance counters.</span></span> <span data-ttu-id="41284-115">これは、機能拡張ポイントを実装すると、WCF が標準のパフォーマンスカウンターデータを既定のパスに出力しなくなる可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="41284-115">This is because if you implement an extensibility point, WCF may no longer emit the standard performance counter data in the default path.</span></span> <span data-ttu-id="41284-116">手動パフォーマンス カウンターのサポートを実装しない場合、予測したパフォーマンス カウンター データが得られない場合があります。</span><span class="sxs-lookup"><span data-stu-id="41284-116">If you do not implement manual performance counter support, you may not see the performance counter data you expect.</span></span>  
  
 <span data-ttu-id="41284-117">また次のように、コード内でパフォーマンス カウンターを有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="41284-117">You can also enable performance counters in your code as follows,</span></span>  
  
```csharp
using System.Configuration;  
using System.ServiceModel.Configuration;  
using System.ServiceModel.Diagnostics;  
Configuration config = ConfigurationManager.OpenExeConfiguration(  
    ConfigurationUserLevel.None);  
ServiceModelSectionGroup sg = ServiceModelSectionGroup.GetSectionGroup(config);  
sg.Diagnostic.PerformanceCounters = PerformanceCounterScope.All;  
config.Save();  
```  
  
## <a name="viewing-performance-data"></a><span data-ttu-id="41284-118">パフォーマンス データの表示</span><span class="sxs-lookup"><span data-stu-id="41284-118">Viewing Performance Data</span></span>  

 <span data-ttu-id="41284-119">Windows に付属のパフォーマンス モニター (Perfmon.exe) を使用して、パフォーマンス カウンターによりキャプチャされたデータを表示できます。</span><span class="sxs-lookup"><span data-stu-id="41284-119">To view data captured by the performance counters, you can use the Performance Monitor (Perfmon.exe) that comes with Windows.</span></span> <span data-ttu-id="41284-120">このツールを起動するには、[ **スタート**] に移動し、[ **実行** ] をクリックして `perfmon.exe` 、ダイアログボックスに「」と入力します。</span><span class="sxs-lookup"><span data-stu-id="41284-120">You can launch this tool by going to **Start**, and click **Run** and type `perfmon.exe` in the dialog box.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41284-121">エンドポイント ディスパッチャーによって最後のメッセージが処理される前に、パフォーマンス カウンター インスタンスが解放される場合があります。</span><span class="sxs-lookup"><span data-stu-id="41284-121">Performance counter instances may be released before the last messages have been processed by the endpoint dispatcher.</span></span> <span data-ttu-id="41284-122">その結果、パフォーマンス データに一部のメッセージがキャプチャされない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="41284-122">This can result in performance data not being captured for a few messages.</span></span>  
  
## <a name="increasing-memory-size-for-performance-counters"></a><span data-ttu-id="41284-123">パフォーマンス カウンターのメモリ サイズの増加</span><span class="sxs-lookup"><span data-stu-id="41284-123">Increasing Memory Size for Performance Counters</span></span>  

 <span data-ttu-id="41284-124">WCF では、パフォーマンスカウンターカテゴリに個別の共有メモリを使用します。</span><span class="sxs-lookup"><span data-stu-id="41284-124">WCF uses separate shared memory for its performance counter categories.</span></span>  
  
 <span data-ttu-id="41284-125">既定では、個々の共有メモリは、グローバル パフォーマンス カウンターのメモリ サイズの 4 分の 1 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="41284-125">By default, separate shared memory is set to a quarter the size of global performance counter memory.</span></span> <span data-ttu-id="41284-126">グローバル パフォーマンス カウンターのメモリの既定値は 524,288 バイトです。</span><span class="sxs-lookup"><span data-stu-id="41284-126">The default global performance counter memory is 524,288 bytes.</span></span> <span data-ttu-id="41284-127">このため、3つの WCF パフォーマンスカウンタカテゴリの既定のサイズは、それぞれ約 128 KB です。</span><span class="sxs-lookup"><span data-stu-id="41284-127">Therefore, the three WCF performance counter categories have a default size of approximately 128KB each.</span></span> <span data-ttu-id="41284-128">コンピューター上の WCF アプリケーションのランタイム特性によっては、パフォーマンスカウンターのメモリが不足することがあります。</span><span class="sxs-lookup"><span data-stu-id="41284-128">Depending upon the runtime characteristics of the WCF applications on a machine, performance counter memory may be exhausted.</span></span> <span data-ttu-id="41284-129">これが発生すると、WCF はアプリケーションイベントログにエラーを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="41284-129">When this happens, WCF writes an error to the application event log.</span></span> <span data-ttu-id="41284-130">エラーの内容にはパフォーマンス カウンターが読み込まれなかったことが示され、エントリには、"System.InvalidOperationException: カスタム カウンター ファイル ビューのメモリが足りません" という例外が含まれます。</span><span class="sxs-lookup"><span data-stu-id="41284-130">The content of the error states that a performance counter was not loaded, and the entry contains the exception "System.InvalidOperationException: Custom counters file view is out of memory."</span></span> <span data-ttu-id="41284-131">このエラー レベルでトレースが有効になっている場合は、さらにこの障害がトレースされます。</span><span class="sxs-lookup"><span data-stu-id="41284-131">If tracing is enabled at the error level, this failure is also traced.</span></span> <span data-ttu-id="41284-132">パフォーマンスカウンターのメモリが不足している場合は、パフォーマンスカウンターが有効になっている WCF アプリケーションの実行を継続すると、パフォーマンスが低下する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="41284-132">If performance counter memory is exhausted, continuing to run your WCF applications with performance counters enabled could result in performance degradation.</span></span> <span data-ttu-id="41284-133">コンピューターの管理者は、使用可能なすべてのパフォーマンス カウンターをいつでも読み込めるだけの十分なメモリを割り当てておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="41284-133">If you are an administrator of the machine, you should configure it to allocate enough memory to support the maximum number of performance counters that can exist at any time.</span></span>  
  
 <span data-ttu-id="41284-134">レジストリの WCF カテゴリのパフォーマンスカウンターのメモリ量を変更できます。</span><span class="sxs-lookup"><span data-stu-id="41284-134">You can change the amount of performance counter memory for WCF categories in the registry.</span></span> <span data-ttu-id="41284-135">これを行うには、次の 3 つの場所に `FileMappingSize` という名前の新しい DWORD 値を追加し、目的の値をバイト単位で設定します。</span><span class="sxs-lookup"><span data-stu-id="41284-135">To do so, you need to add a new DWORD value named `FileMappingSize` to the three following locations, and set it to the desired value in bytes.</span></span> <span data-ttu-id="41284-136">コンピューターを再起動すると、設定した値が有効になります。</span><span class="sxs-lookup"><span data-stu-id="41284-136">Reboot your machine so that these changes are taken into effect.</span></span>  
  
- <span data-ttu-id="41284-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="41284-137">HKLM\System\CurrentControlSet\Services\ServiceModelEndpoint 4.0.0.0\Performance</span></span>  
  
- <span data-ttu-id="41284-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="41284-138">HKLM\System\CurrentControlSet\Services\ServiceModelOperation 4.0.0.0\Performance</span></span>  
  
- <span data-ttu-id="41284-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span><span class="sxs-lookup"><span data-stu-id="41284-139">HKLM\System\CurrentControlSet\Services\ServiceModelService 4.0.0.0\Performance</span></span>  
  
 <span data-ttu-id="41284-140">膨大な数のオブジェクト (ServiceHost など) が破棄され、ガベージ コレクトされるまで待機している場合、`PrivateBytes` パフォーマンス カウンターには非常に高い数値が登録されます。</span><span class="sxs-lookup"><span data-stu-id="41284-140">When a large number of objects (for example, ServiceHost) are disposed of but waiting to be garbage-collected, the `PrivateBytes` performance counter will register an unusually high number.</span></span> <span data-ttu-id="41284-141">この問題を解決するには、アプリケーション固有の独自のカウンターを追加するか、`performanceCounters` 属性を使用してサービス レベルのカウンターだけを有効にします。</span><span class="sxs-lookup"><span data-stu-id="41284-141">To resolve this problem, you can either add your own application-specific counters, or use the `performanceCounters` attribute to enable only service-level counters.</span></span>  
  
## <a name="types-of-performance-counters"></a><span data-ttu-id="41284-142">パフォーマンス カウンターの種類</span><span class="sxs-lookup"><span data-stu-id="41284-142">Types of Performance Counters</span></span>  

 <span data-ttu-id="41284-143">パフォーマンス カウンターには、サービス、エンドポイント、操作の 3 つのレベルがあります。</span><span class="sxs-lookup"><span data-stu-id="41284-143">Performance counters are scoped to three different levels: Service, Endpoint and Operation.</span></span>  
  
 <span data-ttu-id="41284-144">WMI を使用してパフォーマンス カウンターのインスタンス名を取得できます。</span><span class="sxs-lookup"><span data-stu-id="41284-144">You can use WMI to retrieve the name of a performance counter instance.</span></span> <span data-ttu-id="41284-145">たとえば、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="41284-145">For example,</span></span>  
  
- <span data-ttu-id="41284-146">サービスカウンターのインスタンス名は、WMI [サービス](../wmi/service.md) インスタンスの "counterinstancename" プロパティを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="41284-146">Service counter instance name can be obtained through WMI [Service](../wmi/service.md) instance's "CounterInstanceName" property.</span></span>  
  
- <span data-ttu-id="41284-147">エンドポイントカウンターのインスタンス名は、WMI [エンドポイント](../wmi/endpoint.md) インスタンスの "counterinstancename" プロパティを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="41284-147">Endpoint counter instance name can be obtained through WMI [Endpoint](../wmi/endpoint.md) instance's "CounterInstanceName" property.</span></span>  
  
- <span data-ttu-id="41284-148">操作カウンターのインスタンス名は、WMI [エンドポイント](../wmi/endpoint.md) インスタンスの "GetOperationCounterInstanceName" メソッドを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="41284-148">Operation counter instance name can be obtained through WMI [Endpoint](../wmi/endpoint.md) instance's "GetOperationCounterInstanceName" method.</span></span>  
  
 <span data-ttu-id="41284-149">WMI の詳細については、「 [診断のための Windows Management Instrumentation の使用](../wmi/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41284-149">For more information on WMI, see [Using Windows Management Instrumentation for Diagnostics](../wmi/index.md).</span></span>  
  
### <a name="service-performance-counters"></a><span data-ttu-id="41284-150">サービスのパフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="41284-150">Service performance counters</span></span>  

 <span data-ttu-id="41284-151">サービスのパフォーマンス カウンターはサービス動作全体を測定し、サービス全体のパフォーマンスを診断するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="41284-151">Service performance counters measure the service behavior as a whole and can be used to diagnose the performance of the whole service.</span></span> <span data-ttu-id="41284-152">パフォーマンス モニターを使用して表示する場合、これらのカウンターは、`ServiceModelService 4.0.0.0` パフォーマンス オブジェクトの下にあります。</span><span class="sxs-lookup"><span data-stu-id="41284-152">They can be found under the `ServiceModelService 4.0.0.0` performance object when viewing with Performance Monitor.</span></span> <span data-ttu-id="41284-153">インスタンスには次のパターンの名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="41284-153">The instances are named using the following pattern:</span></span>  
  
`ServiceName@ServiceBaseAddress`
  
 <span data-ttu-id="41284-154">サービス スコープ内のカウンターは、エンドポイントのコレクションのカウンターが集計されています。</span><span class="sxs-lookup"><span data-stu-id="41284-154">A counter in a service scope is aggregated from counter in a collection of endpoints.</span></span>  
  
 <span data-ttu-id="41284-155">サービス インスタンス作成のパフォーマンス カウンターは、新しい InstanceContext が作成されるとインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="41284-155">Performance counters for service instance creation are incremented when a new InstanceContext is created.</span></span> <span data-ttu-id="41284-156">新しい InstanceContext は、非アクティブ化メッセージを (既存のサービスで) 受信した場合でも、あるセッションからインスタンスに接続し、セッションを終了後に別のセッションから再接続した場合でも作成されることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="41284-156">Note that a new InstanceContext is created even when you receive a non-activating message (with an existing service), or when you connect to an instance from one session, end the session, and then reconnect from another session.</span></span>  
  
### <a name="endpoint-performance-counters"></a><span data-ttu-id="41284-157">エンドポイントのパフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="41284-157">Endpoint performance counters</span></span>  

 <span data-ttu-id="41284-158">エンドポイントのパフォーマンス カウンターにより、エンドポイントでのメッセージの受信状況を表すデータを参照できます。</span><span class="sxs-lookup"><span data-stu-id="41284-158">Endpoint performance counters enable you to look at data reflecting how an endpoint is accepting messages.</span></span> <span data-ttu-id="41284-159">パフォーマンス モニターを使用して表示する場合、これらのカウンターは、`ServiceModelEndpoint 4.0.0.0` パフォーマンス オブジェクトの下にあります。</span><span class="sxs-lookup"><span data-stu-id="41284-159">They can be found under the `ServiceModelEndpoint 4.0.0.0` performance object when viewing using the Performance Monitor.</span></span> <span data-ttu-id="41284-160">インスタンスには次のパターンの名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="41284-160">The instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName)@(endpoint listener address)`
  
 <span data-ttu-id="41284-161">このデータは、個々の操作で収集されるデータに似ていますが、エンドポイントから集計されただけのデータです。</span><span class="sxs-lookup"><span data-stu-id="41284-161">The data is similar to what is collected for individual operations, but is only aggregated across the endpoint.</span></span>  
  
 <span data-ttu-id="41284-162">エンドポイント スコープ内のカウンターは、操作のコレクションのカウンターから集計されます。</span><span class="sxs-lookup"><span data-stu-id="41284-162">A counter in an endpoint scope is aggregated from counters in a collection of operations.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41284-163">コントラクト名とアドレスが同一の 2 つのエンドポイントは、同じカウンター インスタンスにマップされます。</span><span class="sxs-lookup"><span data-stu-id="41284-163">If two endpoints have identical contract names and addresses, they are mapped to the same counter instance.</span></span>  
  
### <a name="operation-performance-counters"></a><span data-ttu-id="41284-164">操作のパフォーマンス カウンター</span><span class="sxs-lookup"><span data-stu-id="41284-164">Operation performance counters</span></span>  

 <span data-ttu-id="41284-165">パフォーマンス モニターを使用して表示する場合、操作パフォーマンス カウンターは、`ServiceModelOperation 4.0.0.0` パフォーマンス オブジェクトの下にあります。</span><span class="sxs-lookup"><span data-stu-id="41284-165">Operation performance counters are found under the `ServiceModelOperation 4.0.0.0` performance object when viewing with the Performance Monitor.</span></span> <span data-ttu-id="41284-166">それぞれの操作に個別のインスタンスがあります。</span><span class="sxs-lookup"><span data-stu-id="41284-166">Each operation has an individual instance.</span></span> <span data-ttu-id="41284-167">つまり、指定したコントラクトに 10 の操作がある場合、10 の操作カウンター インスタンスがそのコントラクトに関連付けられます。</span><span class="sxs-lookup"><span data-stu-id="41284-167">That is, if a given contract has 10 operations, 10 operation counter instances are associated with that contract.</span></span> <span data-ttu-id="41284-168">オブジェクトのインスタンスには次のパターンの名前が付いています。</span><span class="sxs-lookup"><span data-stu-id="41284-168">The object instances are named using the following pattern:</span></span>  
  
`(ServiceName).(ContractName).(OperationName)@(first endpoint listener address)`
  
 <span data-ttu-id="41284-169">このカウンターにより呼び出しがどのように使用されている、操作がどれほど効率的に実行されているかを調べることができます。</span><span class="sxs-lookup"><span data-stu-id="41284-169">This counter enables you to measure how the call is being used and how well the operation is performing.</span></span>  
  
 <span data-ttu-id="41284-170">カウンターが複数のスコープで表示される場合、上位のスコープで収集されたデータは、下位のスコープからのデータが集計されています。</span><span class="sxs-lookup"><span data-stu-id="41284-170">When counters are visible at multiple scopes, data gathered from a higher scope are aggregated with data from lower scopes.</span></span> <span data-ttu-id="41284-171">たとえば、エンドポイントの `Calls` は、エンドポイント内のすべての操作呼び出しの合計を表します。サービスの `Calls` は、サービス内のすべての操作呼び出しの合計を表します。</span><span class="sxs-lookup"><span data-stu-id="41284-171">For example, `Calls` at an endpoint represents the sum of all operation calls within the endpoint; `Calls` at a service represents the sum of all calls to all endpoints within the service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41284-172">1 つのコントラクトに重複した操作名がある場合は、その両方の操作に対してカウンター インスタンスは 1 つだけ取得されます。</span><span class="sxs-lookup"><span data-stu-id="41284-172">If you have duplicate operation names on a contract, you only get one counter instances for both operations.</span></span>  
  
## <a name="programming-the-wcf-performance-counters"></a><span data-ttu-id="41284-173">WCF パフォーマンス カウンターのプログラミング</span><span class="sxs-lookup"><span data-stu-id="41284-173">Programming the WCF Performance Counters</span></span>  

<span data-ttu-id="41284-174">SDK のインストールフォルダーには、プログラムによって WCF パフォーマンスカウンターにアクセスできるように、いくつかのファイルがインストールされます。</span><span class="sxs-lookup"><span data-stu-id="41284-174">Several files are installed in the SDK install folder so that you can access the WCF performance counters programmatically.</span></span> <span data-ttu-id="41284-175">これらのファイルは次のように一覧表示されます。</span><span class="sxs-lookup"><span data-stu-id="41284-175">These files are listed as follows:</span></span>
  
- <span data-ttu-id="41284-176">*\_ServiceModelEndpointPerfCounters*</span><span class="sxs-lookup"><span data-stu-id="41284-176">*\_ServiceModelEndpointPerfCounters.vrg*</span></span>
- <span data-ttu-id="41284-177">*\_ServiceModelOperationPerfCounters*</span><span class="sxs-lookup"><span data-stu-id="41284-177">*\_ServiceModelOperationPerfCounters.vrg*</span></span>
- <span data-ttu-id="41284-178">*\_ServiceModelServicePerfCounters*</span><span class="sxs-lookup"><span data-stu-id="41284-178">*\_ServiceModelServicePerfCounters.vrg*</span></span>  
- <span data-ttu-id="41284-179">*\_SMSvcHostPerfCounters*</span><span class="sxs-lookup"><span data-stu-id="41284-179">*\_SMSvcHostPerfCounters.vrg*</span></span>
- <span data-ttu-id="41284-180">*\_TransactionBridgePerfCounters*</span><span class="sxs-lookup"><span data-stu-id="41284-180">*\_TransactionBridgePerfCounters.vrg*</span></span>
  
<span data-ttu-id="41284-181">プログラムによってカウンターにアクセスする方法の詳細については、「 [パフォーマンスカウンターのプログラミングアーキテクチャ](/previous-versions/visualstudio/visual-studio-2008/5f9bkxzf(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41284-181">For more information on how to access the counters programmatically, see [Performance Counter Programming Architecture](/previous-versions/visualstudio/visual-studio-2008/5f9bkxzf(v=vs.90)).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="41284-182">関連項目</span><span class="sxs-lookup"><span data-stu-id="41284-182">See also</span></span>

- [<span data-ttu-id="41284-183">管理と診断</span><span class="sxs-lookup"><span data-stu-id="41284-183">Administration and Diagnostics</span></span>](../index.md)
