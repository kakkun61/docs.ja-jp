---
title: IMetaDataEmit::TranslateSigWithScope メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataEmit.TranslateSigWithScope
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataEmit::TranslateSigWithScope
helpviewer_keywords:
- TranslateSigWithScope method [.NET Framework metadata]
- IMetaDataEmit::TranslateSigWithScope method [.NET Framework metadata]
ms.assetid: 47915d33-b7bf-409e-b484-4ee1df15de22
topic_type:
- apiref
ms.openlocfilehash: 80d33da2eb2a7f0cfbe5dcb7279fff9973dada2e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712925"
---
# <a name="imetadataemittranslatesigwithscope-method"></a><span data-ttu-id="42dae-102">IMetaDataEmit::TranslateSigWithScope メソッド</span><span class="sxs-lookup"><span data-stu-id="42dae-102">IMetaDataEmit::TranslateSigWithScope Method</span></span>

<span data-ttu-id="42dae-103">現在のスコープにアセンブリをインポートし、マージされたスコープの新しいメタデータシグネチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="42dae-103">Imports an assembly into the current scope and gets a new metadata signature for the merged scope.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42dae-104">構文</span><span class="sxs-lookup"><span data-stu-id="42dae-104">Syntax</span></span>  
  
```cpp  
HRESULT TranslateSigWithScope (
    [in]  IMetaDataAssemblyImport   *pAssemImport,
    [in]  const void                *pbHashValue,
    [in]  ULONG                     cbHashValue,
    [in]  IMetaDataImport           *import,
    [in]  PCCOR_SIGNATURE           pbSigBlob,
    [in]  ULONG                     cbSigBlob,  
    [in]  IMetaDataAssemblyEmit     *pAssemEmit,
    [in]  IMetaDataEmit             *emit,
    [out] PCOR_SIGNATURE            pvTranslatedSig,
    [in]  ULONG                     cbTranslatedSigMax,
    [out] ULONG                     *pcbTranslatedSig
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42dae-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="42dae-105">Parameters</span></span>  

 `pAssemImport`  
 <span data-ttu-id="42dae-106">からインポートアセンブリのインターフェイス (シグネチャが定義されている場合)。</span><span class="sxs-lookup"><span data-stu-id="42dae-106">[in] The interface for import assembly (where the signature is defined).</span></span>  
  
 `pbHashValue`  
 <span data-ttu-id="42dae-107">からアセンブリのハッシュ blob。</span><span class="sxs-lookup"><span data-stu-id="42dae-107">[in] The hash blob for the assembly.</span></span>  
  
 `cbHashValue`  
 <span data-ttu-id="42dae-108">からのバイト数 `pbHashValue` 。</span><span class="sxs-lookup"><span data-stu-id="42dae-108">[in] The count of bytes in `pbHashValue`.</span></span>  
  
 `import`  
 <span data-ttu-id="42dae-109">からインポートメタデータスコープのインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="42dae-109">[in] The interface for import metadata scope.</span></span>  
  
 `pbSigBlob`  
 <span data-ttu-id="42dae-110">からインポートされる署名。</span><span class="sxs-lookup"><span data-stu-id="42dae-110">[in] The signature to be imported.</span></span>  
  
 `cbSigBlob`  
 <span data-ttu-id="42dae-111">からのサイズ (バイト単位) `pbSigBlob` 。</span><span class="sxs-lookup"><span data-stu-id="42dae-111">[in] The size, in bytes, of `pbSigBlob`.</span></span>  
  
 `pAssemEmit`  
 <span data-ttu-id="42dae-112">からエクスポートアセンブリのインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="42dae-112">[in] The interface for export assembly.</span></span>  
  
 `emit`  
 <span data-ttu-id="42dae-113">からエクスポートメタデータスコープのインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="42dae-113">[in] The interface for export metadata scope.</span></span>  
  
 `pvTranslatedSig`  
 <span data-ttu-id="42dae-114">入出力変換された署名 blob を保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="42dae-114">[out] The buffer to hold the translated signature blob.</span></span>  
  
 `cbTranslatedSigMax`  
 <span data-ttu-id="42dae-115">からの容量 (バイト単位) `pvTranslatedSig` 。</span><span class="sxs-lookup"><span data-stu-id="42dae-115">[in] The capacity, in bytes, of `pvTranslatedSig`.</span></span>  
  
 `pcbTranslatedSig`  
 <span data-ttu-id="42dae-116">入出力変換されたシグネチャの実際のバイト数。</span><span class="sxs-lookup"><span data-stu-id="42dae-116">[out] The number of actual bytes in the translated signature.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42dae-117">要件</span><span class="sxs-lookup"><span data-stu-id="42dae-117">Requirements</span></span>  

 <span data-ttu-id="42dae-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42dae-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42dae-119">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="42dae-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="42dae-120">**ライブラリ:** MSCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="42dae-120">**Library:** Used as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="42dae-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42dae-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="42dae-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="42dae-122">See also</span></span>

- [<span data-ttu-id="42dae-123">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42dae-123">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
- [<span data-ttu-id="42dae-124">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42dae-124">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="42dae-125">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42dae-125">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="42dae-126">IMetaDataEmit2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42dae-126">IMetaDataEmit2 Interface</span></span>](imetadataemit2-interface.md)
- [<span data-ttu-id="42dae-127">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="42dae-127">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
