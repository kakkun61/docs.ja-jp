---
title: ICLRAppDomainResourceMonitor::GetCurrentAllocated メソッド
ms.date: 03/30/2017
api_name:
- ICLRAppDomainResourceMonitor.GetCurrentAllocated
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAppDomainResourceMonitor::GetCurrentAllocated
helpviewer_keywords:
- GetCurrentAllocated method [.NET Framework hosting]
- ICLRAppDomainResourceMonitor::GetCurrentAllocated method [.NET Framework hosting]
ms.assetid: 7bab209c-efd4-44c2-af30-61abab0ae2fc
topic_type:
- apiref
ms.openlocfilehash: d3bd948dfe4a5cf97e3e3e430f551e7bc6404690
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700789"
---
# <a name="iclrappdomainresourcemonitorgetcurrentallocated-method"></a><span data-ttu-id="f5b2a-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated メソッド</span><span class="sxs-lookup"><span data-stu-id="f5b2a-102">ICLRAppDomainResourceMonitor::GetCurrentAllocated Method</span></span>

<span data-ttu-id="f5b2a-103">アプリケーションドメインが作成されてからアプリケーションドメインによって行われたすべてのメモリ割り当ての合計サイズ (バイト単位) を取得します。ガベージコレクトされたメモリは減算されません。</span><span class="sxs-lookup"><span data-stu-id="f5b2a-103">Gets the total size, in bytes, of all memory allocations that have been made by the application domain since it was created, without subtracting memory that has been garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5b2a-104">構文</span><span class="sxs-lookup"><span data-stu-id="f5b2a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentAllocated([in]  DWORD dwAppDomainId,  
                            [out] ULONGLONG* pBytesAllocated);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5b2a-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f5b2a-105">Parameters</span></span>  

 `dwAppDomainId`  
 <span data-ttu-id="f5b2a-106">から要求されたアプリケーションドメインの ID。</span><span class="sxs-lookup"><span data-stu-id="f5b2a-106">[in] The ID of the requested application domain.</span></span>  
  
 `pBytesAllocated`  
 <span data-ttu-id="f5b2a-107">入出力すべてのメモリ割り当ての合計サイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f5b2a-107">[out] A pointer to the total size of all memory allocations.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5b2a-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="f5b2a-108">Return Value</span></span>  

 <span data-ttu-id="f5b2a-109">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="f5b2a-109">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="f5b2a-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="f5b2a-110">HRESULT</span></span>|<span data-ttu-id="f5b2a-111">説明</span><span class="sxs-lookup"><span data-stu-id="f5b2a-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="f5b2a-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="f5b2a-112">S_OK</span></span>|<span data-ttu-id="f5b2a-113">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="f5b2a-113">The method completed successfully.</span></span>|  
|<span data-ttu-id="f5b2a-114">COR_E_APPDOMAINUNLOADED</span><span class="sxs-lookup"><span data-stu-id="f5b2a-114">COR_E_APPDOMAINUNLOADED</span></span>|<span data-ttu-id="f5b2a-115">アプリケーションドメインがアンロードされているか、または存在しません。</span><span class="sxs-lookup"><span data-stu-id="f5b2a-115">The application domain has been unloaded or does not exist.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f5b2a-116">注釈</span><span class="sxs-lookup"><span data-stu-id="f5b2a-116">Remarks</span></span>  

 <span data-ttu-id="f5b2a-117">このメソッドは、マネージプロパティに相当するアンマネージドです <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="f5b2a-117">This method is the unmanaged equivalent of the managed <xref:System.AppDomain.MonitoringTotalAllocatedMemorySize%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5b2a-118">要件</span><span class="sxs-lookup"><span data-stu-id="f5b2a-118">Requirements</span></span>  

 <span data-ttu-id="f5b2a-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f5b2a-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5b2a-120">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="f5b2a-120">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="f5b2a-121">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="f5b2a-121">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f5b2a-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5b2a-122">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5b2a-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5b2a-123">See also</span></span>

- [<span data-ttu-id="f5b2a-124">ICLRAppDomainResourceMonitor インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f5b2a-124">ICLRAppDomainResourceMonitor Interface</span></span>](iclrappdomainresourcemonitor-interface.md)
- [<span data-ttu-id="f5b2a-125">アプリケーションドメインのリソース監視</span><span class="sxs-lookup"><span data-stu-id="f5b2a-125">Application Domain Resource Monitoring</span></span>](../../../standard/garbage-collection/app-domain-resource-monitoring.md)
- [<span data-ttu-id="f5b2a-126">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f5b2a-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="f5b2a-127">ホスティング</span><span class="sxs-lookup"><span data-stu-id="f5b2a-127">Hosting</span></span>](index.md)
