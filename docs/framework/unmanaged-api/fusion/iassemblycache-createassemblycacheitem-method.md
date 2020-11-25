---
title: IAssemblyCache::CreateAssemblyCacheItem メソッド
ms.date: 03/30/2017
api_name:
- IAssemblyCache.CreateAssemblyCacheItem
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAssemblyCache::CreateAssemblyCacheItem
helpviewer_keywords:
- IAssemblyCache::CreateAssemblyCacheItem method [.NET Framework fusion]
- CreateAssemblyCacheItem method [.NET Framework fusion]
ms.assetid: 017a7ba5-aaaf-44e2-9cbe-ceebef259df0
topic_type:
- apiref
ms.openlocfilehash: b417377ea1d0746e563490d87cc9a988e857d943
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697039"
---
# <a name="iassemblycachecreateassemblycacheitem-method"></a><span data-ttu-id="98471-102">IAssemblyCache::CreateAssemblyCacheItem メソッド</span><span class="sxs-lookup"><span data-stu-id="98471-102">IAssemblyCache::CreateAssemblyCacheItem Method</span></span>

<span data-ttu-id="98471-103">新しい [Iassemblycacheitem](iassemblycacheitem-interface.md) オブジェクトへの参照を取得します。</span><span class="sxs-lookup"><span data-stu-id="98471-103">Gets a reference to a new [IAssemblyCacheItem](iassemblycacheitem-interface.md) object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98471-104">構文</span><span class="sxs-lookup"><span data-stu-id="98471-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyCacheItem (  
    [in]  DWORD dwFlags,  
    [in]  PVOID pvReserved,  
    [out] IAssemblyCacheItem **ppAsmItem,  
    [in, optional] LPCWSTR pszAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98471-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="98471-105">Parameters</span></span>  

 `dwFlags`  
 <span data-ttu-id="98471-106">からFusion に定義されているフラグ。</span><span class="sxs-lookup"><span data-stu-id="98471-106">[in] Flags defined in Fusion.idl.</span></span> <span data-ttu-id="98471-107">サポートされている値を次に示します。</span><span class="sxs-lookup"><span data-stu-id="98471-107">The following values are supported:</span></span>  
  
- <span data-ttu-id="98471-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span><span class="sxs-lookup"><span data-stu-id="98471-108">IASSEMBLYCACHE_INSTALL_FLAG_REFRESH (0x00000001)</span></span>  
  
- <span data-ttu-id="98471-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span><span class="sxs-lookup"><span data-stu-id="98471-109">IASSEMBLYCACHE_INSTALL_FLAG_FORCE_REFRESH (0x00000002)</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="98471-110">[入力] 将来の機能拡張に備えて予約されています。</span><span class="sxs-lookup"><span data-stu-id="98471-110">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="98471-111">`pvReserved` null 参照である必要があります。</span><span class="sxs-lookup"><span data-stu-id="98471-111">`pvReserved` must be a null reference.</span></span>  
  
 `ppAsmItem`  
 <span data-ttu-id="98471-112">入出力返された `IAssemblyCacheItem` ポインター。</span><span class="sxs-lookup"><span data-stu-id="98471-112">[out] The returned `IAssemblyCacheItem` pointer.</span></span>  
  
 `pszAssemblyName`  
 <span data-ttu-id="98471-113">[in、optional]正規化が解除、コンマ区切りの `name=value` ペア。</span><span class="sxs-lookup"><span data-stu-id="98471-113">[in, optional] Uncanonicalized, comma-separated `name=value` pairs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98471-114">要件</span><span class="sxs-lookup"><span data-stu-id="98471-114">Requirements</span></span>  

 <span data-ttu-id="98471-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="98471-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98471-116">**ヘッダー:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="98471-116">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="98471-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98471-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98471-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="98471-118">See also</span></span>

- [<span data-ttu-id="98471-119">IAssemblyCache インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98471-119">IAssemblyCache Interface</span></span>](iassemblycache-interface.md)
- [<span data-ttu-id="98471-120">IAssemblyCacheItem インターフェイス</span><span class="sxs-lookup"><span data-stu-id="98471-120">IAssemblyCacheItem Interface</span></span>](iassemblycacheitem-interface.md)
