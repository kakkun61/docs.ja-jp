---
title: PreBindAssemblyEx 関数
ms.date: 03/30/2017
api_name:
- PreBindAssemblyEx
api_location:
- fusion.dll
api_type:
- DLLExport
f1_keywords:
- PreBindAssemblyEx
helpviewer_keywords:
- PreBindAssemblyEx function [.NET Framework fusion]
ms.assetid: bd285233-a4a2-4b52-bbca-0025a60e4864
topic_type:
- apiref
ms.openlocfilehash: a729249f7b0681941a0b1a478dbe2c0d9d6cd01c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723962"
---
# <a name="prebindassemblyex-function"></a><span data-ttu-id="82472-102">PreBindAssemblyEx 関数</span><span class="sxs-lookup"><span data-stu-id="82472-102">PreBindAssemblyEx Function</span></span>

<span data-ttu-id="82472-103">アセンブリのポリシー後の表示名を取得します。</span><span class="sxs-lookup"><span data-stu-id="82472-103">Gets the post-policy display name for an assembly.</span></span>  
  
 <span data-ttu-id="82472-104">この関数は、.NET Framework インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。</span><span class="sxs-lookup"><span data-stu-id="82472-104">This function supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82472-105">構文</span><span class="sxs-lookup"><span data-stu-id="82472-105">Syntax</span></span>  
  
```cpp  
HRESULT PreBindAssemblyEx (  
    [in]  IApplicationContext *pAppCtx,  
    [in]  IAssemblyName       *pName,  
    [in]  IAssembly           *pAsmParent,  
    [in]  LPCWSTR             pwzRuntimeVersion,  
    [out] IAssemblyName       **ppNamePostPolicy,  
    [in]  LPVOID              pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="82472-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="82472-106">Parameters</span></span>  

 `pAppCtx`  
 <span data-ttu-id="82472-107">からアプリケーションコンテキストを識別します。</span><span class="sxs-lookup"><span data-stu-id="82472-107">[in] Identifies the application context.</span></span>  
  
 `pName`  
 <span data-ttu-id="82472-108">からアセンブリ名を識別します。</span><span class="sxs-lookup"><span data-stu-id="82472-108">[in] Identifies the assembly name.</span></span>  
  
 `pAsmParent`  
 <span data-ttu-id="82472-109">から親アセンブリを識別します。</span><span class="sxs-lookup"><span data-stu-id="82472-109">[in] Identifies the parent assembly.</span></span> <span data-ttu-id="82472-110">このパラメーターは無視されます。</span><span class="sxs-lookup"><span data-stu-id="82472-110">This parameter is ignored.</span></span>  
  
 `pwzRuntimeVersion`  
 <span data-ttu-id="82472-111">からランタイムのバージョンを識別します。</span><span class="sxs-lookup"><span data-stu-id="82472-111">[in] Identifies the runtime version.</span></span>  
  
 `ppNamePostPolicy`  
 <span data-ttu-id="82472-112">入出力ポリシー後の表示名を格納します。</span><span class="sxs-lookup"><span data-stu-id="82472-112">[out] Contains the post-policy display name.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="82472-113">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="82472-113">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="82472-114">`pvReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="82472-114">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82472-115">注釈</span><span class="sxs-lookup"><span data-stu-id="82472-115">Remarks</span></span>  

 <span data-ttu-id="82472-116">`ppNamePostPolicy`出力パラメーターは、関数が HRESULT FUSION_E_REF_DEF_MISMATCH を返す場合にのみ設定されます。</span><span class="sxs-lookup"><span data-stu-id="82472-116">The `ppNamePostPolicy` output parameter is set only if the function returns HRESULT FUSION_E_REF_DEF_MISMATCH.</span></span> <span data-ttu-id="82472-117">それ以外の場合は null です。</span><span class="sxs-lookup"><span data-stu-id="82472-117">Otherwise, it is null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82472-118">要件</span><span class="sxs-lookup"><span data-stu-id="82472-118">Requirements</span></span>  

 <span data-ttu-id="82472-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82472-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82472-120">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="82472-120">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="82472-121">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="82472-121">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="82472-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82472-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82472-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="82472-123">See also</span></span>

- [<span data-ttu-id="82472-124">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="82472-124">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
