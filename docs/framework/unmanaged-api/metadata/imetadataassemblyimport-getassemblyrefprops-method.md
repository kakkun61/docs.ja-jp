---
title: IMetaDataAssemblyImport::GetAssemblyRefProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.GetAssemblyRefProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps
helpviewer_keywords:
- IMetaDataAssemblyImport::GetAssemblyRefProps method [.NET Framework metadata]
- GetAssemblyRefProps method [.NET Framework metadata]
ms.assetid: 5c6b7fb4-cbca-4479-b650-ab9a99732ea0
topic_type:
- apiref
ms.openlocfilehash: 25aefff46f7557f89f27d1eccab58c9c70d2d13e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722116"
---
# <a name="imetadataassemblyimportgetassemblyrefprops-method"></a><span data-ttu-id="0f53f-102">IMetaDataAssemblyImport::GetAssemblyRefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="0f53f-102">IMetaDataAssemblyImport::GetAssemblyRefProps Method</span></span>

<span data-ttu-id="0f53f-103">指定されたメタデータシグネチャを持つアセンブリ参照のプロパティのセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="0f53f-103">Gets the set of properties for the assembly reference with the specified metadata signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f53f-104">構文</span><span class="sxs-lookup"><span data-stu-id="0f53f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyRefProps (  
    [in]  mdAssemblyRef        mdar,
    [out] const void          **ppbPublicKeyOrToken,
    [out] ULONG                *pcbPublicKeyOrToken,
    [out] LPWSTR               szName,
    [in]  ULONG                cchName,
    [out] ULONG                *pchName,
    [out] ASSEMBLYMETADATA     *pMetaData,
    [out] const void           **ppbHashValue,
    [out] ULONG                *pcbHashValue,
    [out] DWORD                *pdwAssemblyRefFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f53f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0f53f-105">Parameters</span></span>  

 `mdar`  
 <span data-ttu-id="0f53f-106">から `mdAssemblyRef` プロパティを取得する対象のアセンブリ参照を表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="0f53f-106">[in] The `mdAssemblyRef` metadata token that represents the assembly reference for which to get the properties.</span></span>  
  
 `ppbPublicKeyOrToken`  
 <span data-ttu-id="0f53f-107">入出力公開キーまたはメタデータトークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0f53f-107">[out] A pointer to the public key or the metadata token.</span></span>  
  
 `pcbPublicKeyOrToken`  
 <span data-ttu-id="0f53f-108">入出力返される公開キーまたはトークン内のバイト数。</span><span class="sxs-lookup"><span data-stu-id="0f53f-108">[out] The number of bytes in the returned public key or token.</span></span>  
  
 `szName`  
 <span data-ttu-id="0f53f-109">入出力アセンブリの簡易名。</span><span class="sxs-lookup"><span data-stu-id="0f53f-109">[out] The simple name of the assembly.</span></span>  
  
 `cchName`  
 <span data-ttu-id="0f53f-110">からのサイズ (ワイド文字数) `szName` 。</span><span class="sxs-lookup"><span data-stu-id="0f53f-110">[in] The size, in wide chars, of `szName`.</span></span>  
  
 `pchName`  
 <span data-ttu-id="0f53f-111">入出力実際にで返されるワイド文字数へのポインター `szName` 。</span><span class="sxs-lookup"><span data-stu-id="0f53f-111">[out] A pointer to the number of wide chars actually returned in `szName`.</span></span>  
  
 `pMetaData`  
 <span data-ttu-id="0f53f-112">入出力アセンブリメタデータを格納している ASSEMBLYMETADATA 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0f53f-112">[out] A pointer to an ASSEMBLYMETADATA structure that contains the assembly metadata.</span></span>  
  
 `ppbHashValue`  
 <span data-ttu-id="0f53f-113">入出力ハッシュ値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0f53f-113">[out] A pointer to the hash value.</span></span> <span data-ttu-id="0f53f-114">これは、参照されるアセンブリのプロパティの SHA-1 アルゴリズムを使用するハッシュです `PublicKey` 。 [Assemblyrefflags](assemblyrefflags-enumeration.md) の列挙の arfFullOriginator フラグが設定されている場合を除きます。</span><span class="sxs-lookup"><span data-stu-id="0f53f-114">This is the hash, using the SHA-1 algorithm, of the `PublicKey` property of the assembly being referenced, unless the arfFullOriginator flag of the [AssemblyRefFlags](assemblyrefflags-enumeration.md) enumeration is set.</span></span>  
  
 `pcbHashValue`  
 <span data-ttu-id="0f53f-115">入出力返されたハッシュ値のワイド文字の数。</span><span class="sxs-lookup"><span data-stu-id="0f53f-115">[out] The number of wide chars in the returned hash value.</span></span>  
  
 `pdwAssemblyRefFlags`  
 <span data-ttu-id="0f53f-116">入出力アセンブリに適用されるメタデータを記述するフラグへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0f53f-116">[out] A pointer to flags that describe the metadata applied to an assembly.</span></span> <span data-ttu-id="0f53f-117">Flags 値は、1つまたは複数の [Corassemblyflags](corassemblyflags-enumeration.md) 値を組み合わせたものです。</span><span class="sxs-lookup"><span data-stu-id="0f53f-117">The flags value is a combination of one or more [CorAssemblyFlags](corassemblyflags-enumeration.md) values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f53f-118">戻り値</span><span class="sxs-lookup"><span data-stu-id="0f53f-118">Return Value</span></span>  

 <span data-ttu-id="0f53f-119">成功した場合、このメソッドは S_OK を返します。それ以外の場合は、Winerror.h ヘッダーファイルで定義されているエラーコードの1つを返します。</span><span class="sxs-lookup"><span data-stu-id="0f53f-119">This method returns S_OK if it succeeds; otherwise, it returns one of the error codes defined in the Winerror.h header file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f53f-120">要件</span><span class="sxs-lookup"><span data-stu-id="0f53f-120">Requirements</span></span>  

 <span data-ttu-id="0f53f-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f53f-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0f53f-122">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="0f53f-122">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0f53f-123">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="0f53f-123">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0f53f-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0f53f-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f53f-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f53f-125">See also</span></span>

- [<span data-ttu-id="0f53f-126">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0f53f-126">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
