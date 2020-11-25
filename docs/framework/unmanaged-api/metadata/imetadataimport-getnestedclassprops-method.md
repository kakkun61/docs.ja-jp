---
title: IMetaDataImport::GetNestedClassProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.GetNestedClassProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::GetNestedClassProps
helpviewer_keywords:
- GetNestedClassProps method [.NET Framework metadata]
- IMetaDataImport::GetNestedClassProps method [.NET Framework metadata]
ms.assetid: 704d19f1-bdef-4745-af8c-6476eb246fb3
topic_type:
- apiref
ms.openlocfilehash: 8c0496c34c43a71ec4f51ba66b3bb18790023a2f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722298"
---
# <a name="imetadataimportgetnestedclassprops-method"></a><span data-ttu-id="0b143-102">IMetaDataImport::GetNestedClassProps メソッド</span><span class="sxs-lookup"><span data-stu-id="0b143-102">IMetaDataImport::GetNestedClassProps Method</span></span>

<span data-ttu-id="0b143-103"><xref:System.Type>指定した入れ子にされた型の親の TypeDef トークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="0b143-103">Gets the TypeDef token for the parent <xref:System.Type> of the specified nested type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b143-104">構文</span><span class="sxs-lookup"><span data-stu-id="0b143-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNestedClassProps (  
   [in]   mdTypeDef      tdNestedClass,  
   [out]  mdTypeDef      *ptdEnclosingClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b143-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0b143-105">Parameters</span></span>  

 `tdNestedClass`  
 <span data-ttu-id="0b143-106">から親クラストークンを返すを表す TypeDef トークン <xref:System.Type> 。</span><span class="sxs-lookup"><span data-stu-id="0b143-106">[in] A TypeDef token representing the <xref:System.Type> to return the parent class token for.</span></span>  
  
 `ptdEnclosingClass`  
 <span data-ttu-id="0b143-107">入出力で入れ子になっているの TypeDef トークンへのポインター <xref:System.Type> `tdNestedClass` 。</span><span class="sxs-lookup"><span data-stu-id="0b143-107">[out] A pointer to the TypeDef token for the <xref:System.Type> that `tdNestedClass` is nested in.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b143-108">要件</span><span class="sxs-lookup"><span data-stu-id="0b143-108">Requirements</span></span>  

 <span data-ttu-id="0b143-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0b143-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b143-110">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="0b143-110">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0b143-111">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0b143-111">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0b143-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b143-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b143-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0b143-113">See also</span></span>

- [<span data-ttu-id="0b143-114">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b143-114">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="0b143-115">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0b143-115">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
