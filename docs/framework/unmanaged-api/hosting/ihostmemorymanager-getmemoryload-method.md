---
title: IHostMemoryManager::GetMemoryLoad メソッド
ms.date: 03/30/2017
api_name:
- IHostMemoryManager.GetMemoryLoad
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostMemoryManager::GetMemoryLoad
helpviewer_keywords:
- IHostMemoryManager::GetMemoryLoad method [.NET Framework hosting]
- GetMemoryLoad method [.NET Framework hosting]
ms.assetid: e8138f6e-a0a4-48d4-8dae-9466b4dc6180
topic_type:
- apiref
ms.openlocfilehash: 0611b82e22ec9d5d2cde2a7f46e65b5e25733610
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731359"
---
# <a name="ihostmemorymanagergetmemoryload-method"></a><span data-ttu-id="cd427-102">IHostMemoryManager::GetMemoryLoad メソッド</span><span class="sxs-lookup"><span data-stu-id="cd427-102">IHostMemoryManager::GetMemoryLoad Method</span></span>

<span data-ttu-id="cd427-103">ホストによって報告された、現在使用中の物理メモリの量を取得します。</span><span class="sxs-lookup"><span data-stu-id="cd427-103">Gets the amount of physical memory that is currently in use, and therefore unavailable, as reported by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd427-104">構文</span><span class="sxs-lookup"><span data-stu-id="cd427-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMemoryLoad (  
    [out] DWORD*  pMemoryLoad,
    [out] SIZE_T  *pAvailableBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd427-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cd427-105">Parameters</span></span>  

 `pMemoryLoad`  
 <span data-ttu-id="cd427-106">入出力現在使用されている合計物理メモリのおおよその割合を示すポインター。</span><span class="sxs-lookup"><span data-stu-id="cd427-106">[out] A pointer to the approximate percentage of total physical memory that is currently in use.</span></span>  
  
 `pAvailableBytes`  
 <span data-ttu-id="cd427-107">入出力共通言語ランタイム (CLR) で使用可能なバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cd427-107">[out] A pointer to the number of bytes available to the common language runtime (CLR).</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd427-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="cd427-108">Return Value</span></span>  
  
|<span data-ttu-id="cd427-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cd427-109">HRESULT</span></span>|<span data-ttu-id="cd427-110">説明</span><span class="sxs-lookup"><span data-stu-id="cd427-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cd427-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cd427-111">S_OK</span></span>|<span data-ttu-id="cd427-112">`GetMemoryLoad` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="cd427-112">`GetMemoryLoad` returned successfully.</span></span>|  
|<span data-ttu-id="cd427-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cd427-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cd427-114">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="cd427-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cd427-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="cd427-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="cd427-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="cd427-116">The call timed out.</span></span>|  
|<span data-ttu-id="cd427-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="cd427-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="cd427-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="cd427-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="cd427-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="cd427-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="cd427-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="cd427-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="cd427-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cd427-121">E_FAIL</span></span>|<span data-ttu-id="cd427-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="cd427-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cd427-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="cd427-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cd427-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="cd427-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd427-125">注釈</span><span class="sxs-lookup"><span data-stu-id="cd427-125">Remarks</span></span>  

 <span data-ttu-id="cd427-126">`GetMemoryLoad` Win32 関数をラップ `GlobalMemoryStatus` します。</span><span class="sxs-lookup"><span data-stu-id="cd427-126">`GetMemoryLoad` wraps the Win32 `GlobalMemoryStatus` function.</span></span> <span data-ttu-id="cd427-127">の値 `pMemoryLoad` は、 `dwMemoryLoad` `MEMORYSTATUS` から返された構造体のフィールドに相当し `GlobalMemoryStatus` ます。</span><span class="sxs-lookup"><span data-stu-id="cd427-127">The value of `pMemoryLoad` is the equivalent of the `dwMemoryLoad` field in the `MEMORYSTATUS` structure returned from `GlobalMemoryStatus`.</span></span>  
  
 <span data-ttu-id="cd427-128">ランタイムは、ガベージコレクターのヒューリスティックとして戻り値を使用します。</span><span class="sxs-lookup"><span data-stu-id="cd427-128">The runtime uses the return value as a heuristic for the garbage collector.</span></span> <span data-ttu-id="cd427-129">たとえば、ホストが大量のメモリを使用していることを報告した場合、ガベージコレクターは複数の世代から収集して、使用可能になる可能性があるメモリの量を増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="cd427-129">For example, if the host reports that the majority of memory is in use, the garbage collector may elect to collect from multiple generations to increase the amount of memory that can potentially become available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd427-130">要件</span><span class="sxs-lookup"><span data-stu-id="cd427-130">Requirements</span></span>  

 <span data-ttu-id="cd427-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd427-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd427-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="cd427-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd427-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="cd427-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd427-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd427-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd427-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd427-135">See also</span></span>

- <xref:System.GC?displayProperty=nameWithType>
- [<span data-ttu-id="cd427-136">IHostMemoryManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd427-136">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
