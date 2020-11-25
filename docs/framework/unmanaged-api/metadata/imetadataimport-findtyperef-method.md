---
title: IMetaDataImport::FindTypeRef メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataImport.FindTypeRef
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataImport::FindTypeRef
helpviewer_keywords:
- IMetaDataImport::FindTypeRef method [.NET Framework metadata]
- FindTypeRef method [.NET Framework metadata]
ms.assetid: 1b2bbf3f-943e-412e-b66c-e802431b055c
topic_type:
- apiref
ms.openlocfilehash: 3c96a9b601824cc4001568c4656f968fad70cf39
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711287"
---
# <a name="imetadataimportfindtyperef-method"></a><span data-ttu-id="3f6c0-102">IMetaDataImport::FindTypeRef メソッド</span><span class="sxs-lookup"><span data-stu-id="3f6c0-102">IMetaDataImport::FindTypeRef Method</span></span>

<span data-ttu-id="3f6c0-103">指定したスコープ内にあり、指定した名前を持つ参照の TypeRef トークンへのポインターを取得し <xref:System.Type> ます。</span><span class="sxs-lookup"><span data-stu-id="3f6c0-103">Gets a pointer to the TypeRef token for the <xref:System.Type> reference that is in the specified scope and that has the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f6c0-104">構文</span><span class="sxs-lookup"><span data-stu-id="3f6c0-104">Syntax</span></span>  
  
```cpp  
HRESULT FindTypeRef (  
   [in] mdToken        tkResolutionScope,  
   [in]  LPCWSTR       szName,  
   [out] mdTypeRef     *ptr  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3f6c0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3f6c0-105">Parameters</span></span>  

 `tkResolutionScope`  
 <span data-ttu-id="3f6c0-106">から型参照が定義されているモジュール、アセンブリ、または型をそれぞれ指定する ModuleRef、AssemblyRef、または TypeRef トークン。</span><span class="sxs-lookup"><span data-stu-id="3f6c0-106">[in] A ModuleRef, AssemblyRef, or TypeRef token that specifies the module, assembly, or type, respectively, in which the type reference is defined.</span></span>  
  
 `szName`  
 <span data-ttu-id="3f6c0-107">から検索する型参照の名前。</span><span class="sxs-lookup"><span data-stu-id="3f6c0-107">[in] The name of the type reference to search for.</span></span>  
  
 `ptr`  
 <span data-ttu-id="3f6c0-108">入出力一致する TypeRef トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3f6c0-108">[out] A pointer to the matching TypeRef token.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3f6c0-109">要件</span><span class="sxs-lookup"><span data-stu-id="3f6c0-109">Requirements</span></span>  

 <span data-ttu-id="3f6c0-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3f6c0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f6c0-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="3f6c0-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f6c0-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="3f6c0-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f6c0-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f6c0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f6c0-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f6c0-114">See also</span></span>

- [<span data-ttu-id="3f6c0-115">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f6c0-115">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
- [<span data-ttu-id="3f6c0-116">IMetaDataImport2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3f6c0-116">IMetaDataImport2 Interface</span></span>](imetadataimport2-interface.md)
