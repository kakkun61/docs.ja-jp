---
title: IMetaDataAssemblyImport::EnumAssemblyRefs メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.EnumAssemblyRefs
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs
helpviewer_keywords:
- IMetaDataAssemblyImport::EnumAssemblyRefs method [.NET Framework metadata]
- EnumAssemblyRefs method [.NET Framework metadata]
ms.assetid: 8844d0dd-730e-4592-8a7b-c1462d312c70
topic_type:
- apiref
ms.openlocfilehash: 18cd9dd14e615a7e76bfff30c9ae584305bd1907
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708940"
---
# <a name="imetadataassemblyimportenumassemblyrefs-method"></a><span data-ttu-id="68f85-102">IMetaDataAssemblyImport::EnumAssemblyRefs メソッド</span><span class="sxs-lookup"><span data-stu-id="68f85-102">IMetaDataAssemblyImport::EnumAssemblyRefs Method</span></span>

<span data-ttu-id="68f85-103">`mdAssemblyRef`アセンブリマニフェストで定義されているインスタンスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="68f85-103">Enumerates the `mdAssemblyRef` instances that are defined in the assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68f85-104">構文</span><span class="sxs-lookup"><span data-stu-id="68f85-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumAssemblyRefs (  
    [in, out] HCORENUM        *phEnum,
    [out]     mdAssemblyRef   rAssemblyRefs[],
    [in]      ULONG           cMax,
    [out]     ULONG           *pcTokens  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68f85-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="68f85-105">Parameters</span></span>  

 `phEnum`  
 <span data-ttu-id="68f85-106">[入力、出力]列挙子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="68f85-106">[in, out] A pointer to the enumerator.</span></span> <span data-ttu-id="68f85-107">メソッドを初めて呼び出すときは、null 値を指定する必要があり `EnumAssemblyRefs` ます。</span><span class="sxs-lookup"><span data-stu-id="68f85-107">This must be a null value when the `EnumAssemblyRefs` method is called for the first time.</span></span>  
  
 `rAssemblyRefs`  
 <span data-ttu-id="68f85-108">入出力 `mdAssemblyRef` メタデータトークンの列挙体。</span><span class="sxs-lookup"><span data-stu-id="68f85-108">[out] The enumeration of `mdAssemblyRef` metadata tokens.</span></span>  
  
 `cMax`  
 <span data-ttu-id="68f85-109">から配列に格納できるトークンの最大数 `rAssemblyRefs` 。</span><span class="sxs-lookup"><span data-stu-id="68f85-109">[in] The maximum number of tokens that can be placed in the `rAssemblyRefs` array.</span></span>  
  
 `pcTokens`  
 <span data-ttu-id="68f85-110">入出力実際に配置されたトークンの数 `rAssemblyRefs` 。</span><span class="sxs-lookup"><span data-stu-id="68f85-110">[out] The number of tokens actually placed in `rAssemblyRefs`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="68f85-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="68f85-111">Return Value</span></span>  
  
|<span data-ttu-id="68f85-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="68f85-112">HRESULT</span></span>|<span data-ttu-id="68f85-113">説明</span><span class="sxs-lookup"><span data-stu-id="68f85-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="68f85-114">`EnumAssemblyRefs` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="68f85-114">`EnumAssemblyRefs` returned successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="68f85-115">列挙するトークンがありません。</span><span class="sxs-lookup"><span data-stu-id="68f85-115">There are no tokens to enumerate.</span></span> <span data-ttu-id="68f85-116">この場合、 `pcTokens` は0に設定されます。</span><span class="sxs-lookup"><span data-stu-id="68f85-116">In this case, `pcTokens` is set to zero.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="68f85-117">要件</span><span class="sxs-lookup"><span data-stu-id="68f85-117">Requirements</span></span>  

 <span data-ttu-id="68f85-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="68f85-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68f85-119">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="68f85-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="68f85-120">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="68f85-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="68f85-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68f85-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f85-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="68f85-122">See also</span></span>

- [<span data-ttu-id="68f85-123">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="68f85-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
