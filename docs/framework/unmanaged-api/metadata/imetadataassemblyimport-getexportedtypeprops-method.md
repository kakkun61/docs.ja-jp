---
title: IMetaDataAssemblyImport::GetExportedTypeProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetExportedTypeProps
helpviewer_keywords:
- GetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 25ca7623-5a55-4f09-b44a-36b03d142278
topic_type:
- apiref
ms.openlocfilehash: 32224431051b958a3f01ffeb15cdb6db1dae2657
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722103"
---
# <a name="imetadataassemblyimportgetexportedtypeprops-method"></a><span data-ttu-id="30de8-102">IMetaDataAssemblyImport::GetExportedTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="30de8-102">IMetaDataAssemblyImport::GetExportedTypeProps Method</span></span>

<span data-ttu-id="30de8-103">指定したメタデータシグネチャを持つ、エクスポートされた型のプロパティのセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="30de8-103">Gets the set of properties of the exported type with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30de8-104">構文</span><span class="sxs-lookup"><span data-stu-id="30de8-104">Syntax</span></span>  
  
```cpp  
HRESULT GetExportedTypeProps (  
    [in]  mdExportedType    mdct,
    [out] LPWSTR            szName,
    [in]  ULONG             cchName,
    [out] ULONG             *pchName,
    [out] mdToken           *ptkImplementation,
    [out] mdTypeDef         *ptkTypeDef,
    [out] DWORD             *pdwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30de8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="30de8-105">Parameters</span></span>  

 `mdct`  
 <span data-ttu-id="30de8-106">からエクスポートされた `mdExportedType` 型を表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="30de8-106">[in] An `mdExportedType` metadata token that represents the exported type.</span></span>  
  
 `szName`  
 <span data-ttu-id="30de8-107">入出力エクスポートされた型の名前。</span><span class="sxs-lookup"><span data-stu-id="30de8-107">[out] The name of the exported type.</span></span>  
  
 `cchName`  
 <span data-ttu-id="30de8-108">からのサイズ (ワイド文字単位) `szName` 。</span><span class="sxs-lookup"><span data-stu-id="30de8-108">[in] The size, in wide characters, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="30de8-109">入出力実際に返されるワイド文字の数 `szName`</span><span class="sxs-lookup"><span data-stu-id="30de8-109">[out] The number of wide characters actually returned in `szName`</span></span>  
  
 `ptkImplementation`  
 <span data-ttu-id="30de8-110">入出力 `mdFile` `mdAssemblyRef` エクスポートされた `mdExportedType` 型のプロパティへのアクセスを格納または許可する、、、またはメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="30de8-110">[out] An `mdFile`, `mdAssemblyRef`, or `mdExportedType` metadata token that contains or allows access to the properties of the exported type.</span></span>  
  
 `ptkTypeDef`  
 <span data-ttu-id="30de8-111">入出力 `mdTypeDef` ファイル内の型を表すトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="30de8-111">[out] A pointer to an `mdTypeDef` token that represents a type in the file.</span></span>  
  
 `pdwExportedTypeFlags`  
 <span data-ttu-id="30de8-112">入出力エクスポートされた型に適用されるメタデータを記述するフラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="30de8-112">[out] A pointer to the flags that describe the metadata applied to the exported type.</span></span> <span data-ttu-id="30de8-113">Flags 値には、1つまたは複数の [Cortypeattr](cortypeattr-enumeration.md) 値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="30de8-113">The flags value can be one or more [CorTypeAttr](cortypeattr-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30de8-114">要件</span><span class="sxs-lookup"><span data-stu-id="30de8-114">Requirements</span></span>  

 <span data-ttu-id="30de8-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="30de8-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30de8-116">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="30de8-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="30de8-117">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="30de8-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="30de8-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30de8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30de8-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="30de8-119">See also</span></span>

- [<span data-ttu-id="30de8-120">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="30de8-120">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
