---
title: ICLRRuntimeInfo::IsLoaded メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeInfo.IsLoaded
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeInfo::IsLoaded
helpviewer_keywords:
- IsLoaded method [.NET Framework hosting]
- ICLRRuntimeInfo::IsLoaded method [.NET Framework hosting]
ms.assetid: fdc5a3a7-71ff-4025-99a1-59e4ee0bfe1b
topic_type:
- apiref
ms.openlocfilehash: 66ae74deba9ceab9d1ea6b2c0b96a87bf44f32ab
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714927"
---
# <a name="iclrruntimeinfoisloaded-method"></a><span data-ttu-id="4b550-102">ICLRRuntimeInfo::IsLoaded メソッド</span><span class="sxs-lookup"><span data-stu-id="4b550-102">ICLRRuntimeInfo::IsLoaded Method</span></span>

<span data-ttu-id="4b550-103">[ICLRRuntimeInfo](iclrruntimeinfo-interface.md)インターフェイスに関連付けられている共通言語ランタイム (CLR) をプロセスに読み込むかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="4b550-103">Indicates whether the common language runtime (CLR) associated with the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface is loaded into a process.</span></span> <span data-ttu-id="4b550-104">ランタイムは、起動しなくても読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="4b550-104">A runtime can be loaded without also being started.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4b550-105">構文</span><span class="sxs-lookup"><span data-stu-id="4b550-105">Syntax</span></span>  
  
```cpp  
HRESULT IsLoaded(  
[in]  HANDLE hndProcess,  
[out, retval] BOOL *pbLoaded);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4b550-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4b550-106">Parameters</span></span>  

 `hndProcess`  
 <span data-ttu-id="4b550-107">からプロセスを処理するハンドル。</span><span class="sxs-lookup"><span data-stu-id="4b550-107">[in] A handle to the process.</span></span>  
  
 `pbLoaded`  
 <span data-ttu-id="4b550-108">[出力] `true` CLR がプロセスに読み込まれている場合は、それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="4b550-108">[out] `true` if the CLR is loaded into the process; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4b550-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="4b550-109">Return Value</span></span>  

 <span data-ttu-id="4b550-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="4b550-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="4b550-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4b550-111">HRESULT</span></span>|<span data-ttu-id="4b550-112">説明</span><span class="sxs-lookup"><span data-stu-id="4b550-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4b550-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="4b550-113">S_OK</span></span>|<span data-ttu-id="4b550-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="4b550-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="4b550-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="4b550-115">E_POINTER</span></span>|<span data-ttu-id="4b550-116">`pbLoaded` が null です。</span><span class="sxs-lookup"><span data-stu-id="4b550-116">`pbLoaded` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b550-117">注釈</span><span class="sxs-lookup"><span data-stu-id="4b550-117">Remarks</span></span>  

 <span data-ttu-id="4b550-118">このメソッドは、次の関数およびインターフェイスと下位互換性があります。</span><span class="sxs-lookup"><span data-stu-id="4b550-118">This method is backward-compatible with the following functions and interfaces:</span></span>  
  
- <span data-ttu-id="4b550-119">[ICorRuntimeHost](icorruntimehost-interface.md) インターフェイス (.NET Framework version 1 ホスティング API)。</span><span class="sxs-lookup"><span data-stu-id="4b550-119">[ICorRuntimeHost](icorruntimehost-interface.md) interface (in the .NET Framework version 1 hosting API).</span></span>  
  
- <span data-ttu-id="4b550-120">[ICLRRuntimeHost](iclrruntimehost-interface.md) インターフェイス (.NET Framework 2.0 ホスティング API)。</span><span class="sxs-lookup"><span data-stu-id="4b550-120">[ICLRRuntimeHost](iclrruntimehost-interface.md) interface (in the .NET Framework 2.0 hosting API).</span></span>  
  
- <span data-ttu-id="4b550-121">非推奨 `CorBindTo*` の関数 (「.NET Framework 2.0 ホスティング API での [非推奨の CLR ホスト関数](deprecated-clr-hosting-functions.md) 」を参照してください)。</span><span class="sxs-lookup"><span data-stu-id="4b550-121">Deprecated `CorBindTo*` functions (see [Deprecated CLR Hosting Functions](deprecated-clr-hosting-functions.md) in the .NET Framework 2.0 hosting API).</span></span>  
  
 <span data-ttu-id="4b550-122">ホストは、 `CorBindTo*` [Corbindtoruntime](corbindtoruntime-function.md) 関数など、非推奨の関数の1つを呼び出して、特定のバージョンの CLR をインスタンス化することができます。</span><span class="sxs-lookup"><span data-stu-id="4b550-122">A host may call one of the deprecated `CorBindTo*` functions, such as the [CorBindToRuntime](corbindtoruntime-function.md) function, to instantiate a specific version of the CLR.</span></span> <span data-ttu-id="4b550-123">ホストは [ICLRMetaHost:: GetRuntime](iclrmetahost-getruntime-method.md) メソッドを呼び出し、同じバージョン番号を指定して [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="4b550-123">The host could then call the [ICLRMetaHost::GetRuntime](iclrmetahost-getruntime-method.md) method and specify the same version number to obtain a [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface.</span></span>  
  
 <span data-ttu-id="4b550-124">その後、返された ICLRRuntimeInfo インターフェイスでホストがメソッドを呼び出すと、はを返します。 `IsLoaded` [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) `pbLoaded` `true` それ以外の場合はを返し `false` ます。</span><span class="sxs-lookup"><span data-stu-id="4b550-124">If the host then calls the `IsLoaded` method on the returned [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, `pbLoaded` returns `true`; otherwise, it returns `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4b550-125">要件</span><span class="sxs-lookup"><span data-stu-id="4b550-125">Requirements</span></span>  

 <span data-ttu-id="4b550-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4b550-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4b550-127">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="4b550-127">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="4b550-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4b550-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4b550-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4b550-129">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4b550-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="4b550-130">See also</span></span>

- [<span data-ttu-id="4b550-131">ICLRRuntimeInfo インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4b550-131">ICLRRuntimeInfo Interface</span></span>](iclrruntimeinfo-interface.md)
- [<span data-ttu-id="4b550-132">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4b550-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="4b550-133">ホスティング</span><span class="sxs-lookup"><span data-stu-id="4b550-133">Hosting</span></span>](index.md)
