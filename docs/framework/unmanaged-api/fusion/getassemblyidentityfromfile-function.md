---
title: GetAssemblyIdentityFromFile 関数
ms.date: 03/30/2017
api_name:
- GetAssemblyIdentityFromFile
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- COM
f1_keywords:
- GetAssemblyIdentityFromFile
helpviewer_keywords:
- GetAssemblyIdentityFromFile function [.NET Framework fusion]
ms.assetid: 2c32da53-76c7-4048-84d0-d05207333004
topic_type:
- apiref
ms.openlocfilehash: 9580dd3bc5a7279549e8deadac95d35a33da74f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724482"
---
# <a name="getassemblyidentityfromfile-function"></a><span data-ttu-id="329b3-102">GetAssemblyIdentityFromFile 関数</span><span class="sxs-lookup"><span data-stu-id="329b3-102">GetAssemblyIdentityFromFile Function</span></span>

<span data-ttu-id="329b3-103">指定した `IUnknown` `IID` ファイルパスのアセンブリ内で、指定したを持つオブジェクトへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="329b3-103">Gets a pointer to an `IUnknown` object with the specified `IID` in the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="329b3-104">構文</span><span class="sxs-lookup"><span data-stu-id="329b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyIdentityFromFile (  
    [in]  LPCWSTR   pwzFilePath,  
    [in]  REFIID    riid,  
    [out] IUnknown  **ppIdentity  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="329b3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="329b3-105">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="329b3-106">から要求されたアセンブリへの有効なパス。</span><span class="sxs-lookup"><span data-stu-id="329b3-106">[in] A valid path to the requested assembly.</span></span>  
  
 `riid`  
 <span data-ttu-id="329b3-107">から `IID` 返されるインターフェイスの。</span><span class="sxs-lookup"><span data-stu-id="329b3-107">[in] The `IID` of the interface to return.</span></span>  
  
 `ppIdentity`  
 <span data-ttu-id="329b3-108">入出力返されたインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="329b3-108">[out] The returned interface pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="329b3-109">要件</span><span class="sxs-lookup"><span data-stu-id="329b3-109">Requirements</span></span>  

 <span data-ttu-id="329b3-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="329b3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="329b3-111">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="329b3-111">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="329b3-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="329b3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="329b3-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="329b3-113">See also</span></span>

- [<span data-ttu-id="329b3-114">IUnknown</span><span class="sxs-lookup"><span data-stu-id="329b3-114">IUnknown</span></span>](/cpp/atl/iunknown)
- [<span data-ttu-id="329b3-115">Fusion グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="329b3-115">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
