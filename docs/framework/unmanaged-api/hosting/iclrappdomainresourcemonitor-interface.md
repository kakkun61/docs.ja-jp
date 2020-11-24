---
title: ICLRAppDomainResourceMonitor インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor
helpviewer_keywords:
- ICLRAppDomainResourceMonitor interface [.NET Framework hosting]
ms.assetid: 72fa83a1-8997-41d7-b355-ab177a24a303
topic_type:
- apiref
ms.openlocfilehash: 84c53f0666d0e04b898e28c1d8e146eab566ca1b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674698"
---
# <a name="iclrappdomainresourcemonitor-interface"></a><span data-ttu-id="ee328-102">ICLRAppDomainResourceMonitor インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee328-102">ICLRAppDomainResourceMonitor Interface</span></span>

<span data-ttu-id="ee328-103">アプリケーションドメインのメモリおよび CPU 使用率を検査するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="ee328-103">Provides methods that inspect an application domain's memory and CPU usage.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee328-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="ee328-104">Methods</span></span>  
  
|<span data-ttu-id="ee328-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ee328-105">Method</span></span>|<span data-ttu-id="ee328-106">説明</span><span class="sxs-lookup"><span data-stu-id="ee328-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee328-107">GetCurrentAllocated メソッド</span><span class="sxs-lookup"><span data-stu-id="ee328-107">GetCurrentAllocated Method</span></span>](iclrappdomainresourcemonitor-getcurrentallocated-method.md)|<span data-ttu-id="ee328-108">アプリケーションドメインが作成されてからアプリケーションドメインによって行われたすべてのメモリ割り当ての合計サイズ (バイト単位) を取得します。ガベージコレクトされたメモリは減算されません。</span><span class="sxs-lookup"><span data-stu-id="ee328-108">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>|  
|[<span data-ttu-id="ee328-109">GetCurrentSurvived メソッド</span><span class="sxs-lookup"><span data-stu-id="ee328-109">GetCurrentSurvived Method</span></span>](iclrappdomainresourcemonitor-getcurrentsurvived-method.md)|<span data-ttu-id="ee328-110">最後の完全なブロッキングガベージコレクションの後に残った、現在のアプリケーションドメインによって参照されているバイト数を取得します。</span><span class="sxs-lookup"><span data-stu-id="ee328-110">Gets the number of bytes that survived the last full, blocking garbage collection and that are referenced by the current application domain.</span></span>|  
|[<span data-ttu-id="ee328-111">GetCurrentCpuTime メソッド</span><span class="sxs-lookup"><span data-stu-id="ee328-111">GetCurrentCpuTime Method</span></span>](iclrappdomainresourcemonitor-getcurrentcputime-method.md)|<span data-ttu-id="ee328-112">アプリケーションドメインが作成されてから、現在のアプリケーションドメインでの実行中にすべてのスレッドによって使用された合計プロセッサ時間を取得します。</span><span class="sxs-lookup"><span data-stu-id="ee328-112">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee328-113">注釈</span><span class="sxs-lookup"><span data-stu-id="ee328-113">Remarks</span></span>  

 <span data-ttu-id="ee328-114">インターフェイスには、 `ICLRAppDomainResourceMonitor` 次のマネージプロパティと同様の機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="ee328-114">The `ICLRAppDomainResourceMonitor` interface provides functionality that is similar to the following managed properties:</span></span>  
  
- <xref:System.AppDomain.MonitoringIsEnabled%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedProcessMemorySize%2A?displayProperty=nameWithType>  
  
- <xref:System.AppDomain.MonitoringSurvivedMemorySize%2A?displayProperty=nameWithType>  
  
## <a name="requirements"></a><span data-ttu-id="ee328-115">要件</span><span class="sxs-lookup"><span data-stu-id="ee328-115">Requirements</span></span>  

 <span data-ttu-id="ee328-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ee328-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee328-117">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="ee328-117">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ee328-118">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="ee328-118">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ee328-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee328-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee328-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="ee328-120">See also</span></span>

- [<span data-ttu-id="ee328-121">\<appDomainResourceMonitoring> 要素</span><span class="sxs-lookup"><span data-stu-id="ee328-121">\<appDomainResourceMonitoring> Element</span></span>](../../configure-apps/file-schema/runtime/appdomainresourcemonitoring-element.md)
- [<span data-ttu-id="ee328-122">アプリケーションドメインのリソース監視</span><span class="sxs-lookup"><span data-stu-id="ee328-122">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="ee328-123">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ee328-123">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="ee328-124">ホスティング</span><span class="sxs-lookup"><span data-stu-id="ee328-124">Hosting</span></span>](index.md)
