---
title: ICLRProbingAssemblyEnum::Get メソッド
ms.date: 03/30/2017
api_name:
- ICLRProbingAssemblyEnum.Get
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRProbingAssemblyEnum::Get
helpviewer_keywords:
- Get method, ICLRProbingAssemblyEnum interface [.NET Framework hosting]
- ICLRProbingAssemblyEnum::Get method [.NET Framework hosting]
ms.assetid: fdb67a77-782f-44cf-a8a1-b75999b0f3c8
topic_type:
- apiref
ms.openlocfilehash: 9a6145ff2874890f052f18a7e537e20ff259933c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728941"
---
# <a name="iclrprobingassemblyenumget-method"></a><span data-ttu-id="37a00-102">ICLRProbingAssemblyEnum::Get メソッド</span><span class="sxs-lookup"><span data-stu-id="37a00-102">ICLRProbingAssemblyEnum::Get Method</span></span>

<span data-ttu-id="37a00-103">指定したインデックス位置にあるアセンブリ id を取得します。</span><span class="sxs-lookup"><span data-stu-id="37a00-103">Gets the assembly identity at the specified index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37a00-104">構文</span><span class="sxs-lookup"><span data-stu-id="37a00-104">Syntax</span></span>  
  
```cpp  
HRESULT Get (  
    [in] DWORD dwIndex,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="37a00-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="37a00-105">Parameters</span></span>  

 `dwIndex`  
 <span data-ttu-id="37a00-106">から返されるアセンブリ id の0から始まるインデックス。</span><span class="sxs-lookup"><span data-stu-id="37a00-106">[in] The zero-based index of the assembly identity to return.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="37a00-107">入出力アセンブリ id データを格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="37a00-107">[out] A buffer containing the assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="37a00-108">[入力、出力]バッファーのサイズ `pwzBuffer` 。</span><span class="sxs-lookup"><span data-stu-id="37a00-108">[in, out] The size of the `pwzBuffer` buffer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="37a00-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="37a00-109">Return Value</span></span>  
  
|<span data-ttu-id="37a00-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="37a00-110">HRESULT</span></span>|<span data-ttu-id="37a00-111">説明</span><span class="sxs-lookup"><span data-stu-id="37a00-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="37a00-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="37a00-112">S_OK</span></span>|<span data-ttu-id="37a00-113">`Get` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="37a00-113">`Get` returned successfully.</span></span>|  
|<span data-ttu-id="37a00-114">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="37a00-114">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="37a00-115">`pwzBuffer` が小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="37a00-115">`pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="37a00-116">ERROR_NO_MORE_ITEMS</span><span class="sxs-lookup"><span data-stu-id="37a00-116">ERROR_NO_MORE_ITEMS</span></span>|<span data-ttu-id="37a00-117">列挙には、これ以上項目が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="37a00-117">The enumeration contains no more items.</span></span>|  
|<span data-ttu-id="37a00-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="37a00-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="37a00-119">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="37a00-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="37a00-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="37a00-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="37a00-121">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="37a00-121">The call timed out.</span></span>|  
|<span data-ttu-id="37a00-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="37a00-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="37a00-123">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="37a00-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="37a00-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="37a00-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="37a00-125">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="37a00-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="37a00-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="37a00-126">E_FAIL</span></span>|<span data-ttu-id="37a00-127">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="37a00-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="37a00-128">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="37a00-128">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="37a00-129">後続のホストメソッドを呼び出すと HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="37a00-129">Subsequent calls to any hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37a00-130">注釈</span><span class="sxs-lookup"><span data-stu-id="37a00-130">Remarks</span></span>  

 <span data-ttu-id="37a00-131">インデックス0の id は、プロセッサアーキテクチャに固有の id です。</span><span class="sxs-lookup"><span data-stu-id="37a00-131">The identity at index 0 is the identity specific to the processor architecture.</span></span> <span data-ttu-id="37a00-132">インデックス1の id は、Microsoft 中間言語 (MSIL) のアーキテクチャに依存しないアセンブリです。</span><span class="sxs-lookup"><span data-stu-id="37a00-132">The identity at index 1 is the architecture-neutral assembly for Microsoft intermediate language (MSIL).</span></span> <span data-ttu-id="37a00-133">インデックス2の id にアーキテクチャ情報が含まれていません。</span><span class="sxs-lookup"><span data-stu-id="37a00-133">The identity at index 2 contains no architecture information.</span></span>  
  
 <span data-ttu-id="37a00-134">`Get` は通常、2回呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="37a00-134">`Get` is typically called twice.</span></span> <span data-ttu-id="37a00-135">最初の呼び出しでは、に null 値を指定し、に `pwzBuffer` `pcchBufferSize` 適したサイズに設定し `pwzBuffer` ます。</span><span class="sxs-lookup"><span data-stu-id="37a00-135">The first call supplies a null value for `pwzBuffer`, and sets `pcchBufferSize` to the size appropriate for `pwzBuffer`.</span></span> <span data-ttu-id="37a00-136">2番目の呼び出しでは、適切にサイズ `pwzBuffer` を指定し、完了時に正規のアセンブリ id データを格納します。</span><span class="sxs-lookup"><span data-stu-id="37a00-136">The second call supplies an appropriately sized `pwzBuffer`, and contains the canonical assembly identity data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37a00-137">要件</span><span class="sxs-lookup"><span data-stu-id="37a00-137">Requirements</span></span>  

 <span data-ttu-id="37a00-138">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="37a00-138">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37a00-139">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="37a00-139">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="37a00-140">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="37a00-140">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="37a00-141">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37a00-141">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37a00-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="37a00-142">See also</span></span>

- [<span data-ttu-id="37a00-143">ICLRProbingAssemblyEnum インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37a00-143">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="37a00-144">ICLRAssemblyIdentityManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="37a00-144">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
