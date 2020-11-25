---
title: IMetaDataAssemblyImport::GetManifestResourceProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetManifestResourceProps
helpviewer_keywords:
- GetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetManifestResourceProps method [.NET Framework metadata]
ms.assetid: 00be4789-ac63-4397-b2ec-1629a5c5a585
topic_type:
- apiref
ms.openlocfilehash: 585a9e39f529294841cd11389f03d763968a0f5e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723819"
---
# <a name="imetadataassemblyimportgetmanifestresourceprops-method"></a><span data-ttu-id="92d87-102">IMetaDataAssemblyImport::GetManifestResourceProps メソッド</span><span class="sxs-lookup"><span data-stu-id="92d87-102">IMetaDataAssemblyImport::GetManifestResourceProps Method</span></span>

<span data-ttu-id="92d87-103">指定されたメタデータシグネチャを持つマニフェストリソースのプロパティのセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="92d87-103">Gets the set of properties of the manifest resource with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92d87-104">構文</span><span class="sxs-lookup"><span data-stu-id="92d87-104">Syntax</span></span>  
  
```cpp  
HRESULT GetManifestResourceProps (  
    [in]  mdManifestResource   mdmr,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] mdToken              *ptkImplementation,
    [out] DWORD                *pdwOffset,
    [out] DWORD                *pdwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92d87-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="92d87-105">Parameters</span></span>  

 `mdmr`  
 <span data-ttu-id="92d87-106">から `mdManifestResource` プロパティを取得する対象のリソースを表すトークン。</span><span class="sxs-lookup"><span data-stu-id="92d87-106">[in] An `mdManifestResource` token that represents the resource for which to get the properties.</span></span>  
  
 `szName`  
 <span data-ttu-id="92d87-107">入出力リソースの名前。</span><span class="sxs-lookup"><span data-stu-id="92d87-107">[out] The name of the resource.</span></span>  
  
 `cchName`  
 <span data-ttu-id="92d87-108">からのサイズ (ワイド文字数) `szName` 。</span><span class="sxs-lookup"><span data-stu-id="92d87-108">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="92d87-109">入出力実際にで返されるワイド文字数へのポインター `szName` 。</span><span class="sxs-lookup"><span data-stu-id="92d87-109">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="92d87-110">入出力リソースを格納し `mdFile` `mdAssemblyRef` ているファイルまたはアセンブリを表すトークンまたはトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="92d87-110">[out] A pointer to an `mdFile` token or an `mdAssemblyRef` token that represents the file or assembly, respectively, that contains the resource.</span></span>  
  
 `pdwOffset`  
 <span data-ttu-id="92d87-111">入出力ファイル内のリソースの先頭へのオフセットを指定する値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="92d87-111">[out] A pointer to a value that specifies the offset to the beginning of the resource within the file.</span></span>  
  
 `pdwResourceFlags`  
 <span data-ttu-id="92d87-112">入出力リソースに適用されるメタデータを記述するフラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="92d87-112">[out] A pointer to flags that describe the metadata applied to a resource.</span></span> <span data-ttu-id="92d87-113">Flags 値は、1つ以上の [Cormanifestresourceflags](cormanifestresourceflags-enumeration.md) 値を組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="92d87-113">The flags value is a combination of one or more [CorManifestResourceFlags](cormanifestresourceflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92d87-114">要件</span><span class="sxs-lookup"><span data-stu-id="92d87-114">Requirements</span></span>  

 <span data-ttu-id="92d87-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92d87-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92d87-116">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="92d87-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="92d87-117">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="92d87-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="92d87-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92d87-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92d87-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="92d87-119">See also</span></span>

- [<span data-ttu-id="92d87-120">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="92d87-120">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
