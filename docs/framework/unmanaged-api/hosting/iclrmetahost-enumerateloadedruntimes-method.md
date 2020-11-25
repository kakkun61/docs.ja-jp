---
title: ICLRMetaHost::EnumerateLoadedRuntimes メソッド
ms.date: 03/30/2017
api_name:
- ICLRMetaHost.EnumerateLoadedRuntimes
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost::EnumerateLoadedRuntimes
helpviewer_keywords:
- EnumerateLoadedRuntimes method [.NET Framework hosting]
- ICLRMetaHost::EnumerateLoadedRuntimes method [.NET Framework hosting]
ms.assetid: 22fc0a3f-dce4-4766-9a3c-9fab15f4b4ca
topic_type:
- apiref
ms.openlocfilehash: 98184dd6ea16df066905039b028acd689ff3f290
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730436"
---
# <a name="iclrmetahostenumerateloadedruntimes-method"></a><span data-ttu-id="de23e-102">ICLRMetaHost::EnumerateLoadedRuntimes メソッド</span><span class="sxs-lookup"><span data-stu-id="de23e-102">ICLRMetaHost::EnumerateLoadedRuntimes Method</span></span>

<span data-ttu-id="de23e-103">指定されたプロセスに読み込まれる共通言語ランタイム (CLR) の各バージョンの有効な [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスポインターを含む列挙体を返します。</span><span class="sxs-lookup"><span data-stu-id="de23e-103">Returns an enumeration that includes a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each version of the common language runtime (CLR) that is loaded in a given process.</span></span> <span data-ttu-id="de23e-104">このメソッドは、 [Getversionfromprocess](getversionfromprocess-function.md) 関数よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="de23e-104">This method supersedes the [GetVersionFromProcess](getversionfromprocess-function.md) function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de23e-105">構文</span><span class="sxs-lookup"><span data-stu-id="de23e-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLoadedRuntimes (  
    [in] HANDLE hndProcess,  
    [out, retval] IEnumUnknown **ppEnumerator  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="de23e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="de23e-106">Parameters</span></span>  

 `hndProcess`  
 <span data-ttu-id="de23e-107">から読み込まれたランタイムを検査するプロセスのハンドル。</span><span class="sxs-lookup"><span data-stu-id="de23e-107">[in] The handle of the process to inspect for loaded runtimes.</span></span>  
  
 `ppEnumerator`  
 <span data-ttu-id="de23e-108">入出力 <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> プロセスによって読み込まれる各 CLR に対応する [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスの列挙体。</span><span class="sxs-lookup"><span data-stu-id="de23e-108">[out] An <xref:Microsoft.VisualStudio.OLE.Interop.IEnumUnknown> enumeration of [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interfaces corresponding to each CLR that is loaded by the process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="de23e-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="de23e-109">Return Value</span></span>  

 <span data-ttu-id="de23e-110">このメソッドは、次の特定の HRESULT と、メソッドの失敗を示す HRESULT エラーも返します。</span><span class="sxs-lookup"><span data-stu-id="de23e-110">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="de23e-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="de23e-111">HRESULT</span></span>|<span data-ttu-id="de23e-112">説明</span><span class="sxs-lookup"><span data-stu-id="de23e-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="de23e-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="de23e-113">S_OK</span></span>|<span data-ttu-id="de23e-114">メソッドは正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="de23e-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="de23e-115">E_POINTER</span><span class="sxs-lookup"><span data-stu-id="de23e-115">E_POINTER</span></span>|<span data-ttu-id="de23e-116">`ppEnumerator` が null です。</span><span class="sxs-lookup"><span data-stu-id="de23e-116">`ppEnumerator` is null.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="de23e-117">注釈</span><span class="sxs-lookup"><span data-stu-id="de23e-117">Remarks</span></span>  

 <span data-ttu-id="de23e-118">このメソッドは、 [Corbindtoruntime](corbindtoruntime-function.md)などの非推奨の関数を使用して読み込まれた場合でも、読み込まれたすべてのランタイムを一覧表示します。</span><span class="sxs-lookup"><span data-stu-id="de23e-118">This method is lists all loaded runtimes, even if they were loaded with deprecated functions such as [CorBindToRuntime](corbindtoruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de23e-119">要件</span><span class="sxs-lookup"><span data-stu-id="de23e-119">Requirements</span></span>  

 <span data-ttu-id="de23e-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="de23e-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de23e-121">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="de23e-121">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="de23e-122">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="de23e-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="de23e-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de23e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="de23e-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="de23e-124">See also</span></span>

- [<span data-ttu-id="de23e-125">ICLRMetaHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="de23e-125">ICLRMetaHost Interface</span></span>](iclrmetahost-interface.md)
- [<span data-ttu-id="de23e-126">ホスティング</span><span class="sxs-lookup"><span data-stu-id="de23e-126">Hosting</span></span>](index.md)
