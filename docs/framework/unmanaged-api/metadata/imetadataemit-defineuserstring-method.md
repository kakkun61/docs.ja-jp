---
title: IMetaDataEmit::DefineUserString メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineUserString
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineUserString
helpviewer_keywords:
- DefineUserString method [.NET Framework metadata]
- IMetaDataEmit::DefineUserString method [.NET Framework metadata]
ms.assetid: 88fb7ef3-bbdf-429c-b678-c9c153456461
topic_type:
- apiref
ms.openlocfilehash: ed3c20fe8272ca3205079d26df0b7bde12e58307
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732698"
---
# <a name="imetadataemitdefineuserstring-method"></a><span data-ttu-id="2fc51-102">IMetaDataEmit::DefineUserString メソッド</span><span class="sxs-lookup"><span data-stu-id="2fc51-102">IMetaDataEmit::DefineUserString Method</span></span>

<span data-ttu-id="2fc51-103">指定されたリテラル文字列のメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="2fc51-103">Gets a metadata token for the specified literal string.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2fc51-104">構文</span><span class="sxs-lookup"><span data-stu-id="2fc51-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineUserString (
    [in]  LPCWSTR     szString,
    [in]  ULONG       cchString,
    [out] mdString    *pstk
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2fc51-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2fc51-105">Parameters</span></span>  

 `szString`  
 <span data-ttu-id="2fc51-106">から格納するユーザー文字列。</span><span class="sxs-lookup"><span data-stu-id="2fc51-106">[in] The user string to store.</span></span>  
  
 `cchString`  
 <span data-ttu-id="2fc51-107">からのワイド文字数 `szString` 。</span><span class="sxs-lookup"><span data-stu-id="2fc51-107">[in] The count of wide characters in `szString`.</span></span>  
  
 `pstk`  
 <span data-ttu-id="2fc51-108">入出力割り当てられた文字列トークン。</span><span class="sxs-lookup"><span data-stu-id="2fc51-108">[out] The string token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2fc51-109">要件</span><span class="sxs-lookup"><span data-stu-id="2fc51-109">Requirements</span></span>  

 <span data-ttu-id="2fc51-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2fc51-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2fc51-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="2fc51-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2fc51-112">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="2fc51-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2fc51-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2fc51-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2fc51-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="2fc51-114">See also</span></span>

- [<span data-ttu-id="2fc51-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2fc51-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="2fc51-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="2fc51-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
