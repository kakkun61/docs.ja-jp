---
title: ICLRAppDomainResourceMonitor::GetCurrentCpuTime メソッド
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentCpuTime
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime
helpviewer_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentCpuTime method [.NET Framework hosting]
- GetCurrentCpuTime method [.NET Framework hosting]
ms.assetid: ebc9cc33-fcd6-4cae-9ecb-ea21c51874e6
topic_type:
- apiref
ms.openlocfilehash: a0b966e85bedcbef622aba2f6b181b98e0950e01
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700679"
---
# <a name="iclrappdomainresourcemonitorgetcurrentcputime-method"></a><span data-ttu-id="dd8d1-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime メソッド</span><span class="sxs-lookup"><span data-stu-id="dd8d1-102">ICLRAppDomainResourceMonitor::GetCurrentCpuTime Method</span></span>

<span data-ttu-id="dd8d1-103">アプリケーションドメインが作成されてから、現在のアプリケーションドメインでの実行中にすべてのスレッドによって使用された合計プロセッサ時間を取得します。</span><span class="sxs-lookup"><span data-stu-id="dd8d1-103">Gets the total processor time that has been used by all threads while executing in the current application domain, since the application domain was created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd8d1-104">構文</span><span class="sxs-lookup"><span data-stu-id="dd8d1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentCpuTime([in]  DWORD dwAppDomainId,  
                          [out] ULONGLONG* pMilliseconds);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dd8d1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="dd8d1-105">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="dd8d1-106">から要求されたアプリケーションドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="dd8d1-106">[in] The ID of the requested application domain.</span></span>  
  
 `pMilliseconds`  
 <span data-ttu-id="dd8d1-107">入出力アプリケーションドメインが作成されてから現在のアプリケーションドメインで実行中に、すべてのスレッドによって使用された合計プロセッサ時間を示すポインター。</span><span class="sxs-lookup"><span data-stu-id="dd8d1-107">[out] A pointer to the total processor time that has been used by all threads while executing in the current application domain since the application domain was created.</span></span> <span data-ttu-id="dd8d1-108">このパラメーターは、`null` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="dd8d1-108">This parameter can be `null`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd8d1-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="dd8d1-109">Return Value</span></span>  
  
|<span data-ttu-id="dd8d1-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dd8d1-110">HRESULT</span></span>|<span data-ttu-id="dd8d1-111">説明</span><span class="sxs-lookup"><span data-stu-id="dd8d1-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dd8d1-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="dd8d1-112">S_OK</span></span>|<span data-ttu-id="dd8d1-113">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="dd8d1-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="dd8d1-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="dd8d1-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="dd8d1-115">アプリケーションドメインがアンロードされているか、または存在しません。</span><span class="sxs-lookup"><span data-stu-id="dd8d1-115">The application domain has been unloaded or does not exist.</span></span>|  
|<span data-ttu-id="dd8d1-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dd8d1-116">E_FAIL</span></span>|<span data-ttu-id="dd8d1-117">アプリケーションドメインのリソース監視が有効になっていません。</span><span class="sxs-lookup"><span data-stu-id="dd8d1-117">Application domain resource monitoring is not enabled.</span></span><br /><br /> <span data-ttu-id="dd8d1-118">- または -</span><span class="sxs-lookup"><span data-stu-id="dd8d1-118">-or-</span></span><br /><br /> <span data-ttu-id="dd8d1-119">その他のすべてのエラー。</span><span class="sxs-lookup"><span data-stu-id="dd8d1-119">All other failures.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd8d1-120">注釈</span><span class="sxs-lookup"><span data-stu-id="dd8d1-120">Remarks</span></span>  

 <span data-ttu-id="dd8d1-121">このメソッドは、マネージプロパティに相当するアンマネージドです <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="dd8d1-121">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalProcessorTime%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dd8d1-122">要件</span><span class="sxs-lookup"><span data-stu-id="dd8d1-122">Requirements</span></span>  

 <span data-ttu-id="dd8d1-123">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="dd8d1-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd8d1-124">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="dd8d1-124">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="dd8d1-125">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="dd8d1-125">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dd8d1-126">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd8d1-126">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd8d1-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd8d1-127">See also</span></span>

- [<span data-ttu-id="dd8d1-128">ICLRAppDomainResourceMonitor インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd8d1-128">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="dd8d1-129">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="dd8d1-129">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="dd8d1-130">アプリケーションドメインのリソース監視</span><span class="sxs-lookup"><span data-stu-id="dd8d1-130">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="dd8d1-131">ホスティング</span><span class="sxs-lookup"><span data-stu-id="dd8d1-131">Hosting</span></span>](index.md)
