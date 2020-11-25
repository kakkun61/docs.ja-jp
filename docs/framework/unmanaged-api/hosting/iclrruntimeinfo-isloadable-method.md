---
title: ICLRRuntimeInfo::IsLoadable メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoadable
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoadable
helpviewer_keywords:
- IsLoadable method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoadable method [.NET Framework hosting]
ms.assetid: 205ca53b-e78e-49b2-9a46-2a7823e96b8c
topic_type:
- apiref
ms.openlocfilehash: 2236e815211168d8e7105375b75f30128f7f209a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714972"
---
# <a name="iclrruntimeinfoisloadable-method"></a><span data-ttu-id="307eb-102">ICLRRuntimeInfo::IsLoadable メソッド</span><span class="sxs-lookup"><span data-stu-id="307eb-102">ICLRRuntimeInfo::IsLoadable Method</span></span>

<span data-ttu-id="307eb-103">このインターフェイスに関連付けられているランタイムを現在のプロセスに読み込むことができるかどうかを示します。プロセスに既に読み込まれている可能性のある他のランタイムを考慮してください。</span><span class="sxs-lookup"><span data-stu-id="307eb-103">Indicates whether the runtime associated with this interface can be loaded into the current process, taking into account other runtimes that might already be loaded into the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="307eb-104">構文</span><span class="sxs-lookup"><span data-stu-id="307eb-104">Syntax</span></span>  
  
```cpp  
HRESULT IsLoadable(  
        [out, retval] BOOL *pbLoadable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="307eb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="307eb-105">Parameters</span></span>  

 `pbLoadable`  
 <span data-ttu-id="307eb-106">[出力] `true` このランタイムを現在のプロセスに読み込むことができる場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="307eb-106">[out] `true` if this runtime could be loaded into the current process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="307eb-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="307eb-107">Return Value</span></span>  

 <span data-ttu-id="307eb-108">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="307eb-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="307eb-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="307eb-109">HRESULT</span></span>|<span data-ttu-id="307eb-110">説明</span><span class="sxs-lookup"><span data-stu-id="307eb-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="307eb-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="307eb-111">S_OK</span></span>|<span data-ttu-id="307eb-112">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="307eb-112">The method completed successfully.</span></span>|  
|<span data-ttu-id="307eb-113">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="307eb-113">E_POINTER</span></span>|<span data-ttu-id="307eb-114">`pbLoadable` が null です。</span><span class="sxs-lookup"><span data-stu-id="307eb-114">`pbLoadable` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="307eb-115">注釈</span><span class="sxs-lookup"><span data-stu-id="307eb-115">Remarks</span></span>  

 <span data-ttu-id="307eb-116">別のランタイムが既にプロセスに読み込まれていて、このインターフェイスに関連付けられているランタイムをインプロセス side-by-side 実行用に読み込むことができる場合、はを `pbLoadable` 返し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="307eb-116">If another runtime is already loaded into the process, and the runtime associated with this interface can be loaded for in-process side-by-side execution, `pbLoadable` returns `true`.</span></span> <span data-ttu-id="307eb-117">2つのランタイムをインプロセスで並列実行できない場合、はを `pbLoadable` 返し `false` ます。</span><span class="sxs-lookup"><span data-stu-id="307eb-117">If the two runtimes cannot run side-by-side in-process, `pbLoadable` returns `false`.</span></span> <span data-ttu-id="307eb-118">たとえば、共通言語ランタイム (CLR) バージョン4は、CLR バージョン2.0 または CLR バージョン1.1 と同じプロセスでサイドバイサイドで実行できます。</span><span class="sxs-lookup"><span data-stu-id="307eb-118">For example, the common language runtime (CLR) version 4 can run side-by-side in the same process with CLR version 2.0 or CLR version 1.1.</span></span> <span data-ttu-id="307eb-119">ただし、CLR バージョン1.1 と CLR バージョン2.0 をインプロセスで並列実行することはできません。</span><span class="sxs-lookup"><span data-stu-id="307eb-119">However, CLR version 1.1 and CLR version 2.0 cannot run side-by-side in-process.</span></span>  
  
 <span data-ttu-id="307eb-120">プロセスにランタイムが読み込まれていない場合、このメソッドは常にを返し `true` ます。</span><span class="sxs-lookup"><span data-stu-id="307eb-120">If no runtimes are loaded into the process, this method always returns `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="307eb-121">要件</span><span class="sxs-lookup"><span data-stu-id="307eb-121">Requirements</span></span>  

 <span data-ttu-id="307eb-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="307eb-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="307eb-123">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="307eb-123">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="307eb-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="307eb-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="307eb-125">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="307eb-125">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="307eb-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="307eb-126">See also</span></span>

- [<span data-ttu-id="307eb-127">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="307eb-127">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="307eb-128">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="307eb-128">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="307eb-129">ホスティング</span><span class="sxs-lookup"><span data-stu-id="307eb-129">Hosting</span></span>](index.md)
