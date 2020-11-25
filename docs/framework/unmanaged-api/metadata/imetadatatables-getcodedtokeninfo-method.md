---
title: IMetaDataTables::GetCodedTokenInfo メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataTables.GetCodedTokenInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataTables::GetCodedTokenInfo
helpviewer_keywords:
- GetCodedTokenInfo method [.NET Framework metadata]
- IMetaDataTables::GetCodedTokenInfo method [.NET Framework metadata]
ms.assetid: 31214d3a-715e-49af-92b3-0fd11e4f218a
topic_type:
- apiref
ms.openlocfilehash: b79ac7f71ec0551336298a90829e1f37e2e30b20
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711073"
---
# <a name="imetadatatablesgetcodedtokeninfo-method"></a><span data-ttu-id="cd282-102">IMetaDataTables::GetCodedTokenInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="cd282-102">IMetaDataTables::GetCodedTokenInfo Method</span></span>

<span data-ttu-id="cd282-103">指定した行インデックスに関連付けられているトークンの配列へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="cd282-103">Gets a pointer to an array of tokens associated with the specified row index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd282-104">構文</span><span class="sxs-lookup"><span data-stu-id="cd282-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodedTokenInfo (
    [in]  ULONG       ixCdTkn,  
    [out] ULONG       *pcTokens,  
    [out] ULONG       **ppTokens,  
    [out] const char  **ppName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd282-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cd282-105">Parameters</span></span>  

 `ixCdTkn`  
 <span data-ttu-id="cd282-106">から返されるコード化されたトークンの種類。</span><span class="sxs-lookup"><span data-stu-id="cd282-106">[in] The kind of coded token to return.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="cd282-107">入出力の長さへのポインター `ppTokens` 。</span><span class="sxs-lookup"><span data-stu-id="cd282-107">[out] A pointer to the length of `ppTokens`.</span></span>  
  
 `ppTokens`  
 <span data-ttu-id="cd282-108">入出力返されたトークンのリストを格納する配列へのポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cd282-108">[out] A pointer to a pointer to an array that contains the list of returned tokens.</span></span>  
  
 `ppName`  
 <span data-ttu-id="cd282-109">入出力にあるトークンの名前へのポインターへのポインター `ixCdTkn` 。</span><span class="sxs-lookup"><span data-stu-id="cd282-109">[out] A pointer to a pointer to the name of the token at `ixCdTkn`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd282-110">要件</span><span class="sxs-lookup"><span data-stu-id="cd282-110">Requirements</span></span>  

 <span data-ttu-id="cd282-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd282-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd282-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="cd282-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="cd282-113">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="cd282-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="cd282-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd282-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd282-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd282-115">See also</span></span>

- [<span data-ttu-id="cd282-116">IMetaDataTables インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd282-116">IMetaDataTables Interface</span></span>](imetadatatables-interface.md)
- [<span data-ttu-id="cd282-117">IMetaDataTables2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd282-117">IMetaDataTables2 Interface</span></span>](imetadatatables2-interface.md)
