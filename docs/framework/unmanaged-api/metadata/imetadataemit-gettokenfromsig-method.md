---
title: IMetaDataEmit::GetTokenFromSig メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.GetTokenFromSig
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::GetTokenFromSig
helpviewer_keywords:
- IMetaDataEmit::GetTokenFromSig method [.NET Framework metadata]
- GetTokenFromSig method [.NET Framework metadata]
ms.assetid: 50a58a83-6287-40a4-b315-47823cea0a5c
topic_type:
- apiref
ms.openlocfilehash: b41891227d94b66bf59128d620eba9da117fe92a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722051"
---
# <a name="imetadataemitgettokenfromsig-method"></a><span data-ttu-id="d6fdf-102">IMetaDataEmit::GetTokenFromSig メソッド</span><span class="sxs-lookup"><span data-stu-id="d6fdf-102">IMetaDataEmit::GetTokenFromSig Method</span></span>

<span data-ttu-id="d6fdf-103">指定したメタデータシグネチャのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="d6fdf-103">Gets a token for the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6fdf-104">構文</span><span class="sxs-lookup"><span data-stu-id="d6fdf-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTokenFromSig (
    [in]  PCCOR_SIGNATURE pvSig,
    [in]  ULONG       cbSig,
    [out] mdSignature *pmsig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d6fdf-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d6fdf-105">Parameters</span></span>  

 `pvSig`  
 <span data-ttu-id="d6fdf-106">から永続化および格納される署名。</span><span class="sxs-lookup"><span data-stu-id="d6fdf-106">[in] The signature to be persisted and stored.</span></span>  
  
 `cbSig`  
 <span data-ttu-id="d6fdf-107">からのバイト数 `pvSig` 。</span><span class="sxs-lookup"><span data-stu-id="d6fdf-107">[in] The count of bytes in `pvSig`.</span></span>  
  
 `pmsig`  
 <span data-ttu-id="d6fdf-108">入出力 `mdSignature` 割り当てられたトークン。</span><span class="sxs-lookup"><span data-stu-id="d6fdf-108">[out] The `mdSignature` token assigned.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d6fdf-109">要件</span><span class="sxs-lookup"><span data-stu-id="d6fdf-109">Requirements</span></span>  

 <span data-ttu-id="d6fdf-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d6fdf-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d6fdf-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="d6fdf-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="d6fdf-112">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="d6fdf-112">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d6fdf-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d6fdf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d6fdf-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="d6fdf-114">See also</span></span>

- [<span data-ttu-id="d6fdf-115">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6fdf-115">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d6fdf-116">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d6fdf-116">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
