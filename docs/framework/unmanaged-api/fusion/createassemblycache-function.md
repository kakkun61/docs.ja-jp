---
title: CreateAssemblyCache 関数
ms.date: 03/30/2017
api_name:
- CreateAssemblyCache
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyCache
helpviewer_keywords:
- CreateAssemblyCache function [.NET Framework fusion]
ms.assetid: 348c7c8c-8578-46ae-97cf-480d6015c3c6
topic_type:
- apiref
ms.openlocfilehash: 3197c650b4f167e7a5043270797d2c4a62413d8e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683200"
---
# <a name="createassemblycache-function"></a><span data-ttu-id="a04a7-102">CreateAssemblyCache 関数</span><span class="sxs-lookup"><span data-stu-id="a04a7-102">CreateAssemblyCache Function</span></span>

<span data-ttu-id="a04a7-103">グローバルアセンブリキャッシュを表す新しい [Iassemblycache](iassemblycache-interface.md) インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="a04a7-103">Gets a pointer to a new [IAssemblyCache](iassemblycache-interface.md) instance that represents the global assembly cache.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a04a7-104">構文</span><span class="sxs-lookup"><span data-stu-id="a04a7-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCache (  
    [out] IAssemblyCache  **ppAsmCache,  
    [in]  DWORD           dwReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="a04a7-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a04a7-105">Parameters</span></span>  

 `ppAsmCache`  
 <span data-ttu-id="a04a7-106">入出力返された `IAssemblyCache` ポインター。</span><span class="sxs-lookup"><span data-stu-id="a04a7-106">[out] The returned `IAssemblyCache` pointer.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="a04a7-107">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="a04a7-107">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="a04a7-108">`dwReserved` 0 (ゼロ) にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a04a7-108">`dwReserved` must be 0 (zero).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a04a7-109">要件</span><span class="sxs-lookup"><span data-stu-id="a04a7-109">Requirements</span></span>  

 <span data-ttu-id="a04a7-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a04a7-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a04a7-111">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="a04a7-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="a04a7-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a04a7-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a04a7-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a04a7-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a04a7-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="a04a7-114">See also</span></span>

- [<span data-ttu-id="a04a7-115">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a04a7-115">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="a04a7-116">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="a04a7-116">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
- [<span data-ttu-id="a04a7-117">グローバル アセンブリ キャッシュ</span><span class="sxs-lookup"><span data-stu-id="a04a7-117">Global Assembly Cache</span></span>](../../app-domains/gac.md)
