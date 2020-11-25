---
title: IMetaDataEmit::GetTokenFromTypeSpec メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromTypeSpec
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromTypeSpec
helpviewer_keywords:
- GetTokenFromTypeSpec method [.NET Framework metadata]
- IMetaDataEmit::GetTokenFromTypeSpec method [.NET Framework metadata]
ms.assetid: 7de6447a-a751-49d8-87e2-951cee77b536
topic_type:
- apiref
ms.openlocfilehash: 3a8f369728b8464850259518981bf6690cb17a01
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722038"
---
# <a name="imetadataemitgettokenfromtypespec-method"></a><span data-ttu-id="83b6f-102">IMetaDataEmit::GetTokenFromTypeSpec メソッド</span><span class="sxs-lookup"><span data-stu-id="83b6f-102">IMetaDataEmit::GetTokenFromTypeSpec Method</span></span>

<span data-ttu-id="83b6f-103">指定したメタデータシグネチャを持つ型のメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="83b6f-103">Gets a metadata token for the type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83b6f-104">構文</span><span class="sxs-lookup"><span data-stu-id="83b6f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromTypeSpec (
    [in]  PCCOR_SIGNATURE       pvSig,
    [in]  ULONG                 cbSig,
    [out] mdTypeSpec            *ptypespec
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83b6f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="83b6f-105">Parameters</span></span>  

 `pvSig`  
 <span data-ttu-id="83b6f-106">から定義されている署名。</span><span class="sxs-lookup"><span data-stu-id="83b6f-106">[in] The signature being defined.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="83b6f-107">からのバイト数 `pvSig` 。</span><span class="sxs-lookup"><span data-stu-id="83b6f-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `ptypespec`  
 <span data-ttu-id="83b6f-108">入出力 `mdTypeSpec` 割り当てられたトークン。</span><span class="sxs-lookup"><span data-stu-id="83b6f-108">[out] The `mdTypeSpec` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83b6f-109">要件</span><span class="sxs-lookup"><span data-stu-id="83b6f-109">Requirements</span></span>  

 <span data-ttu-id="83b6f-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83b6f-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83b6f-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="83b6f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83b6f-112">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="83b6f-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="83b6f-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83b6f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83b6f-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="83b6f-114">See also</span></span>

- [<span data-ttu-id="83b6f-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83b6f-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="83b6f-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83b6f-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
