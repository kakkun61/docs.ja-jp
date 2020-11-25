---
title: ICLRGCManager2::SetGCStartupLimitsEx メソッド
ms.date: 03/30/2017
api_name:
- ICLRGCManager2.SetGCStartupLimitsEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2::SetCLRGCStartupLimitsEx
helpviewer_keywords:
- ICLRGCManager2::SetGCStartupLimitsEx method [.NET Framework hosting]
- SetGCStartupLimitsEx method, ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 6c3a08a9-5d65-48d4-8bbf-2a86ed7d356a
topic_type:
- apiref
ms.openlocfilehash: 27d1ce06800075d2690bc508554b70f8d10168af
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715018"
---
# <a name="iclrgcmanager2setgcstartuplimitsex-method"></a><span data-ttu-id="810b6-102">ICLRGCManager2::SetGCStartupLimitsEx メソッド</span><span class="sxs-lookup"><span data-stu-id="810b6-102">ICLRGCManager2::SetGCStartupLimitsEx Method</span></span>

<span data-ttu-id="810b6-103">ガベージコレクションセグメントのサイズとガベージコレクションシステムのジェネレーション0の最大サイズを設定します。</span><span class="sxs-lookup"><span data-stu-id="810b6-103">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="810b6-104">構文</span><span class="sxs-lookup"><span data-stu-id="810b6-104">Syntax</span></span>  
  
```cpp  
HRESULT SetGCStartupLimitsEx (  
    [in] SIZE_T SegmentSize,
    [in] SIZE_T MaxGen0Size  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="810b6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="810b6-105">Parameters</span></span>  

 `SegmentSize`  
 <span data-ttu-id="810b6-106">からガベージコレクションセグメントの指定されたサイズ。</span><span class="sxs-lookup"><span data-stu-id="810b6-106">[in] The specified size of a garbage collection segment.</span></span>  
  
 <span data-ttu-id="810b6-107">セグメントの最小サイズは 4 MB です。</span><span class="sxs-lookup"><span data-stu-id="810b6-107">The minimum segment size is 4 MB.</span></span> <span data-ttu-id="810b6-108">セグメントは、1 MB 以上の単位で増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="810b6-108">Segments can be increased in increments of 1 MB or larger.</span></span>  
  
 `MaxGen0Size`  
 <span data-ttu-id="810b6-109">からジェネレーション0の指定された最大サイズ。</span><span class="sxs-lookup"><span data-stu-id="810b6-109">[in] The specified maximum size for generation 0.</span></span>  
  
 <span data-ttu-id="810b6-110">ジェネレーション0の最小サイズは 64 KB です。</span><span class="sxs-lookup"><span data-stu-id="810b6-110">The minimum generation 0 size is 64 KB.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="810b6-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="810b6-111">Return Value</span></span>  
  
|<span data-ttu-id="810b6-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="810b6-112">HRESULT</span></span>|<span data-ttu-id="810b6-113">説明</span><span class="sxs-lookup"><span data-stu-id="810b6-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="810b6-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="810b6-114">S_OK</span></span>|<span data-ttu-id="810b6-115">`SetGCStartupLimitsEx` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="810b6-115">`SetGCStartupLimitsEx` returned successfully.</span></span>|  
|<span data-ttu-id="810b6-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="810b6-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="810b6-117">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="810b6-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="810b6-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="810b6-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="810b6-119">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="810b6-119">The call timed out.</span></span>|  
|<span data-ttu-id="810b6-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="810b6-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="810b6-121">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="810b6-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="810b6-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="810b6-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="810b6-123">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="810b6-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="810b6-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="810b6-124">E_FAIL</span></span>|<span data-ttu-id="810b6-125">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="810b6-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="810b6-126">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="810b6-126">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="810b6-127">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="810b6-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="810b6-128">注釈</span><span class="sxs-lookup"><span data-stu-id="810b6-128">Remarks</span></span>  

 <span data-ttu-id="810b6-129">を設定する値は、 `SetGCStartupLimitsEx` ホストを開始する前にのみ指定できます。</span><span class="sxs-lookup"><span data-stu-id="810b6-129">The values that `SetGCStartupLimitsEx` sets can be specified only before the host is started.</span></span> <span data-ttu-id="810b6-130">の後の呼び出し `SetGCStartupLimitsEx` は無視されます。</span><span class="sxs-lookup"><span data-stu-id="810b6-130">Later calls to `SetGCStartupLimitsEx` are ignored.</span></span>  
  
 <span data-ttu-id="810b6-131">どちらか一方のパラメーターに影響を及ぼさずに設定するには、変更しないパラメーターに 0 (ゼロ) を指定します。</span><span class="sxs-lookup"><span data-stu-id="810b6-131">To set either parameter without affecting the other, specify 0 (zero) for the parameter you don't want to change.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="810b6-132">要件</span><span class="sxs-lookup"><span data-stu-id="810b6-132">Requirements</span></span>  

 <span data-ttu-id="810b6-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="810b6-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="810b6-134">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="810b6-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="810b6-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="810b6-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="810b6-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="810b6-136">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="810b6-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="810b6-137">See also</span></span>

- [<span data-ttu-id="810b6-138">自動メモリ管理</span><span class="sxs-lookup"><span data-stu-id="810b6-138">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="810b6-139">ガベージ コレクション</span><span class="sxs-lookup"><span data-stu-id="810b6-139">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
- [<span data-ttu-id="810b6-140">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="810b6-140">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="810b6-141">ICLRGCManager2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="810b6-141">ICLRGCManager2 Interface</span></span>](iclrgcmanager2-interface.md)
