---
title: IMetaDataAssemblyImport::GetAssemblyProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyProps
helpviewer_keywords:
- GetAssemblyProps method [.NET Framework metadata]
- IMetaDataAssemblyImport::GetAssemblyProps method [.NET Framework metadata]
ms.assetid: 0eaa4aa9-9441-444a-920c-e4b2a2db899e
topic_type:
- apiref
ms.openlocfilehash: 1e1a86cdf55812197aae653dca256fb910a7f168
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733894"
---
# <a name="imetadataassemblyimportgetassemblyprops-method"></a><span data-ttu-id="1db82-102">IMetaDataAssemblyImport::GetAssemblyProps メソッド</span><span class="sxs-lookup"><span data-stu-id="1db82-102">IMetaDataAssemblyImport::GetAssemblyProps Method</span></span>

<span data-ttu-id="1db82-103">指定したメタデータシグネチャを持つアセンブリのプロパティのセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="1db82-103">Gets the set of properties for the assembly with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1db82-104">構文</span><span class="sxs-lookup"><span data-stu-id="1db82-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyProps (  
    [in]  mdAssembly          mda,  
    [out] const void          **ppbPublicKey,
    [out] ULONG               *pcbPublicKey,  
    [out] ULONG               *pulHashAlgId,  
    [out] LPWSTR              szName,  
    [in] ULONG                cchName,  
    [out] ULONG               *pchName,  
    [out] ASSEMBLYMETADATA    *pMetaData,  
    [out] DWORD               *pdwAssemblyFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1db82-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1db82-105">Parameters</span></span>  

 `mda`  
 <span data-ttu-id="1db82-106">[入力]。</span><span class="sxs-lookup"><span data-stu-id="1db82-106">[in].</span></span> <span data-ttu-id="1db82-107">`mdAssembly`プロパティを取得する対象のアセンブリを表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="1db82-107">The `mdAssembly` metadata token that represents the assembly for which to get the properties.</span></span>  
  
 `ppbPublicKey`  
 <span data-ttu-id="1db82-108">入出力公開キーまたはメタデータトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1db82-108">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="1db82-109">入出力返される公開キーのバイト数。</span><span class="sxs-lookup"><span data-stu-id="1db82-109">[out] The number of bytes in the returned public key.</span></span>  
  
 `pulHashAlgId`  
 <span data-ttu-id="1db82-110">入出力アセンブリ内のファイルのハッシュに使用されるアルゴリズムへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1db82-110">[out] A pointer to the algorithm used to hash the files in the assembly.</span></span>  
  
 `szName`  
 <span data-ttu-id="1db82-111">入出力アセンブリの簡易名。</span><span class="sxs-lookup"><span data-stu-id="1db82-111">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="1db82-112">からのサイズ (ワイド文字数) `szName` 。</span><span class="sxs-lookup"><span data-stu-id="1db82-112">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="1db82-113">入出力実際にで返されるワイド文字数 `szName` 。</span><span class="sxs-lookup"><span data-stu-id="1db82-113">[out] The number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="1db82-114">入出力アセンブリメタデータを格納している ASSEMBLYMETADATA 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1db82-114">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `pdwAssemblyFlags`  
 <span data-ttu-id="1db82-115">入出力アセンブリに適用されるメタデータを記述するフラグ。</span><span class="sxs-lookup"><span data-stu-id="1db82-115">[out] Flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="1db82-116">この値は、1つまたは複数の [Corassemblyflags](corassemblyflags-enumeration.md) 値を組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="1db82-116">This value is a combination of one or more [CorAssemblyFlags](corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1db82-117">要件</span><span class="sxs-lookup"><span data-stu-id="1db82-117">Requirements</span></span>  

 <span data-ttu-id="1db82-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1db82-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1db82-119">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="1db82-119">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="1db82-120">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="1db82-120">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="1db82-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1db82-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1db82-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="1db82-122">See also</span></span>

- [<span data-ttu-id="1db82-123">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1db82-123">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
