---
title: IMetaDataDispenserEx::FindAssembly メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssembly
helpviewer_keywords:
- FindAssembly method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssembly method [.NET Framework metadata]
ms.assetid: 3afe7252-5f28-48d9-a74d-1927566c404c
topic_type:
- apiref
ms.openlocfilehash: c11a4498610c3e82590a0ff9be1247173e70be76
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713393"
---
# <a name="imetadatadispenserexfindassembly-method"></a><span data-ttu-id="033ae-102">IMetaDataDispenserEx::FindAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="033ae-102">IMetaDataDispenserEx::FindAssembly Method</span></span>

<span data-ttu-id="033ae-103">このメソッドは実装されていません。</span><span class="sxs-lookup"><span data-stu-id="033ae-103">This method is not implemented.</span></span> <span data-ttu-id="033ae-104">呼び出された場合は E_NOTIMPL を返します。</span><span class="sxs-lookup"><span data-stu-id="033ae-104">If called, it returns E_NOTIMPL.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="033ae-105">構文</span><span class="sxs-lookup"><span data-stu-id="033ae-105">Syntax</span></span>  
  
```cpp  
HRESULT FindAssembly(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="033ae-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="033ae-106">Parameters</span></span>  

 `szAppBase`  
 <span data-ttu-id="033ae-107">から使用しません。</span><span class="sxs-lookup"><span data-stu-id="033ae-107">[in] Not used.</span></span>  
  
 `szPrivateBin`  
 <span data-ttu-id="033ae-108">から使用しません。</span><span class="sxs-lookup"><span data-stu-id="033ae-108">[in] Not used.</span></span>  
  
 `szGlobalBin`  
 <span data-ttu-id="033ae-109">から使用しません。</span><span class="sxs-lookup"><span data-stu-id="033ae-109">[in] Not used.</span></span>  
  
 `szAssemblyName`  
 <span data-ttu-id="033ae-110">から検索するアセンブリ。</span><span class="sxs-lookup"><span data-stu-id="033ae-110">[in] The assembly to be found.</span></span>  
  
 `szName`  
 <span data-ttu-id="033ae-111">入出力アセンブリの簡易名。</span><span class="sxs-lookup"><span data-stu-id="033ae-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="033ae-112">からのサイズ (バイト単位) `szName` 。</span><span class="sxs-lookup"><span data-stu-id="033ae-112">[in] The size, in bytes, of `szName`.</span></span>  
  
 `pcName`  
 <span data-ttu-id="033ae-113">入出力で実際に返された文字数 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="033ae-113">[out] The number of characters actually returned in `szName`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="033ae-114">要件</span><span class="sxs-lookup"><span data-stu-id="033ae-114">Requirements</span></span>  

 <span data-ttu-id="033ae-115">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="033ae-115">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="033ae-116">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="033ae-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="033ae-117">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="033ae-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="033ae-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="033ae-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="033ae-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="033ae-119">See also</span></span>

- [<span data-ttu-id="033ae-120">IMetaDataDispenserEx インターフェイス</span><span class="sxs-lookup"><span data-stu-id="033ae-120">IMetaDataDispenserEx Interface</span></span>](imetadatadispenserex-interface.md)
- [<span data-ttu-id="033ae-121">IMetaDataDispenser インターフェイス</span><span class="sxs-lookup"><span data-stu-id="033ae-121">IMetaDataDispenser Interface</span></span>](imetadatadispenser-interface.md)
