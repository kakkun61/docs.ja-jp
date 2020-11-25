---
title: IHostCrst::TryEnter メソッド
ms.date: 03/30/2017
api_name:
- IHostCrst.TryEnter
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostCrst::TryEnter
helpviewer_keywords:
- IHostCrst::TryEnter method [.NET Framework hosting]
- TryEnter method [.NET Framework hosting]
ms.assetid: a922fa98-beab-4f09-a342-cc94fc65687f
topic_type:
- apiref
ms.openlocfilehash: 02f36068f12bf0a40e5f0ac477803abfb84c72a9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729537"
---
# <a name="ihostcrsttryenter-method"></a><span data-ttu-id="883f9-102">IHostCrst::TryEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="883f9-102">IHostCrst::TryEnter Method</span></span>

<span data-ttu-id="883f9-103">現在の [IHostCrst](ihostcrst-interface.md) インスタンスによって表されるクリティカルセクションへの入力を試みます。</span><span class="sxs-lookup"><span data-stu-id="883f9-103">Attempts to enter the critical section represented by the current [IHostCrst](ihostcrst-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="883f9-104">構文</span><span class="sxs-lookup"><span data-stu-id="883f9-104">Syntax</span></span>  
  
```cpp  
HRESULT TryEnter (  
    [in]  DWORD  option,  
    [out] BOOL   *pbSucceeded  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="883f9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="883f9-105">Parameters</span></span>  

 `option`  
 <span data-ttu-id="883f9-106">から [WAIT_OPTION](wait-option-enumeration.md) 値の1つ。操作がブロックされた場合にホストが実行するアクションを示します。</span><span class="sxs-lookup"><span data-stu-id="883f9-106">[in] One of the [WAIT_OPTION](wait-option-enumeration.md) values, indicating what action the host should take if the operation blocks.</span></span>  
  
 `pbSucceeded`  
 <span data-ttu-id="883f9-107">[出力] `true` クリティカルセクションを入力できる場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="883f9-107">[out] `true` if the critical section can be entered; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="883f9-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="883f9-108">Return Value</span></span>  
  
|<span data-ttu-id="883f9-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="883f9-109">HRESULT</span></span>|<span data-ttu-id="883f9-110">説明</span><span class="sxs-lookup"><span data-stu-id="883f9-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="883f9-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="883f9-111">S_OK</span></span>|<span data-ttu-id="883f9-112">`TryEnter` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="883f9-112">`TryEnter` returned successfully.</span></span>|  
|<span data-ttu-id="883f9-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="883f9-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="883f9-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="883f9-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="883f9-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="883f9-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="883f9-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="883f9-116">The call timed out.</span></span>|  
|<span data-ttu-id="883f9-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="883f9-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="883f9-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="883f9-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="883f9-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="883f9-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="883f9-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="883f9-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="883f9-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="883f9-121">E_FAIL</span></span>|<span data-ttu-id="883f9-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="883f9-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="883f9-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="883f9-123">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="883f9-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="883f9-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="883f9-125">注釈</span><span class="sxs-lookup"><span data-stu-id="883f9-125">Remarks</span></span>  

 <span data-ttu-id="883f9-126">`TryEnter` を直ちに返し、呼び出し元のスレッドがクリティカルセクションに入ったかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="883f9-126">`TryEnter` returns immediately and indicates whether the calling thread entered the critical section.</span></span> <span data-ttu-id="883f9-127">このメソッドは、Wind32 関数をミラー化 `TryEnterCriticalSection` します。</span><span class="sxs-lookup"><span data-stu-id="883f9-127">This method mirrors the Wind32 `TryEnterCriticalSection` function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="883f9-128">要件</span><span class="sxs-lookup"><span data-stu-id="883f9-128">Requirements</span></span>  

 <span data-ttu-id="883f9-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="883f9-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="883f9-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="883f9-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="883f9-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="883f9-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="883f9-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="883f9-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="883f9-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="883f9-133">See also</span></span>

- [<span data-ttu-id="883f9-134">ICLRSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="883f9-134">ICLRSyncManager Interface</span></span>](iclrsyncmanager-interface.md)
- [<span data-ttu-id="883f9-135">IHostCrst インターフェイス</span><span class="sxs-lookup"><span data-stu-id="883f9-135">IHostCrst Interface</span></span>](ihostcrst-interface.md)
- [<span data-ttu-id="883f9-136">IHostSyncManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="883f9-136">IHostSyncManager Interface</span></span>](ihostsyncmanager-interface.md)
