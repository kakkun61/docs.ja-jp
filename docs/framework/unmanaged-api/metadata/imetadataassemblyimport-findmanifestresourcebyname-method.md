---
title: IMetaDataAssemblyImport::FindManifestResourceByName メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport.FindManifestResourceByName
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport::FindManifestResourceByName
helpviewer_keywords:
- FindManifestResourceByName method [.NET Framework metadata]
- IMetaDataAssemblyImport::FindManifestResourceByName method [.NET Framework metadata]
ms.assetid: 7b72fa11-3866-402b-bdea-2b966b77cfe0
topic_type:
- apiref
ms.openlocfilehash: 152f62fddee3eaa7fa14e454e6eb7ea2547265ad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731580"
---
# <a name="imetadataassemblyimportfindmanifestresourcebyname-method"></a><span data-ttu-id="a44e0-102">IMetaDataAssemblyImport::FindManifestResourceByName メソッド</span><span class="sxs-lookup"><span data-stu-id="a44e0-102">IMetaDataAssemblyImport::FindManifestResourceByName Method</span></span>

<span data-ttu-id="a44e0-103">指定した名前のマニフェストリソースへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="a44e0-103">Gets a pointer to the manifest resource with the specified name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a44e0-104">構文</span><span class="sxs-lookup"><span data-stu-id="a44e0-104">Syntax</span></span>  
  
```cpp
HRESULT FindManifestResourceByName (  
    [in]  LPCWSTR                szName,
    [out] mdManifestResource     *ptkManifestResource  
);
```  
  
## <a name="parameters"></a><span data-ttu-id="a44e0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a44e0-105">Parameters</span></span>  

 `szName`  
 <span data-ttu-id="a44e0-106">からリソースの名前。</span><span class="sxs-lookup"><span data-stu-id="a44e0-106">[in] The name of the resource.</span></span>  
  
 `ptkManifestResource`  
 <span data-ttu-id="a44e0-107">入出力メタデータトークンを格納するために使用される配列 `mdManifestResource` 。それぞれがマニフェストリソースを表します。</span><span class="sxs-lookup"><span data-stu-id="a44e0-107">[out] The array used to store the `mdManifestResource` metadata tokens, each of which represents a manifest resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a44e0-108">注釈</span><span class="sxs-lookup"><span data-stu-id="a44e0-108">Remarks</span></span>  

 <span data-ttu-id="a44e0-109">メソッドは、 `FindManifestResourceByName` 参照を解決するために共通言語ランタイムによって採用されている標準の規則を使用します。</span><span class="sxs-lookup"><span data-stu-id="a44e0-109">The `FindManifestResourceByName` method uses the standard rules employed by the common language runtime for resolving references.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a44e0-110">要件</span><span class="sxs-lookup"><span data-stu-id="a44e0-110">Requirements</span></span>  

 <span data-ttu-id="a44e0-111">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a44e0-111">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a44e0-112">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="a44e0-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a44e0-113">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="a44e0-113">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a44e0-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a44e0-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a44e0-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="a44e0-115">See also</span></span>

- [<span data-ttu-id="a44e0-116">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a44e0-116">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
- [<span data-ttu-id="a44e0-117">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="a44e0-117">How the Runtime Locates Assemblies</span></span>](../../deployment/how-the-runtime-locates-assemblies.md)
