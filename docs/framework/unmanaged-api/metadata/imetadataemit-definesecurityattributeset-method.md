---
title: IMetaDataEmit::DefineSecurityAttributeSet メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.DefineSecurityAttributeSet
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet
helpviewer_keywords:
- IMetaDataEmit::DefineSecurityAttributeSet method [.NET Framework metadata]
- DefineSecurityAttributeSet method [.NET Framework metadata]
ms.assetid: 27064ca2-4186-4433-90a7-3b297785e891
topic_type:
- apiref
ms.openlocfilehash: 5caf07414c9e64169f272eb11169c4d4ee399c6b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719464"
---
# <a name="imetadataemitdefinesecurityattributeset-method"></a><span data-ttu-id="12bfd-102">IMetaDataEmit::DefineSecurityAttributeSet メソッド</span><span class="sxs-lookup"><span data-stu-id="12bfd-102">IMetaDataEmit::DefineSecurityAttributeSet Method</span></span>

<span data-ttu-id="12bfd-103">指定したトークンによって参照されるオブジェクトにアタッチするセキュリティアクセス許可のセットを作成します。</span><span class="sxs-lookup"><span data-stu-id="12bfd-103">Creates a set of security permissions to attach to the object referenced by the specified token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12bfd-104">構文</span><span class="sxs-lookup"><span data-stu-id="12bfd-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineSecurityAttributeSet (
    [in]  mdToken       tkObj,
    [in]  COR_SECATTR   rSecAttrs[],
    [in]  ULONG         cSecAttrs,
    [out] ULONG         *pulErrorAttr
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="12bfd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="12bfd-105">Parameters</span></span>  

 `tkObj`  
 <span data-ttu-id="12bfd-106">からセキュリティ情報がアタッチされるトークン。</span><span class="sxs-lookup"><span data-stu-id="12bfd-106">[in] The token to which the security information is attached.</span></span>  
  
 `rSecAttrs`  
 <span data-ttu-id="12bfd-107">から `COR_SECATTR` 構造体の配列。</span><span class="sxs-lookup"><span data-stu-id="12bfd-107">[in] An array of `COR_SECATTR` structures.</span></span>  
  
 `cSecAttrs`  
 <span data-ttu-id="12bfd-108">から内の要素の数 `rSecAttrs` 。</span><span class="sxs-lookup"><span data-stu-id="12bfd-108">[in] The number of elements in `rSecAttrs`.</span></span>  
  
 `pulErrorAttr`  
 <span data-ttu-id="12bfd-109">入出力メソッドが失敗した場合、は、 `rSecAttrs` 問題の原因となった要素ののインデックスを指定します。</span><span class="sxs-lookup"><span data-stu-id="12bfd-109">[out] If the method fails, specifies the index in `rSecAttrs` of the element that caused the problem.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12bfd-110">要件</span><span class="sxs-lookup"><span data-stu-id="12bfd-110">Requirements</span></span>  

 <span data-ttu-id="12bfd-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12bfd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12bfd-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="12bfd-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="12bfd-113">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="12bfd-113">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="12bfd-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12bfd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12bfd-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="12bfd-115">See also</span></span>

- [<span data-ttu-id="12bfd-116">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="12bfd-116">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="12bfd-117">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="12bfd-117">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
