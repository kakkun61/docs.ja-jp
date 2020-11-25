---
title: IMetaDataAssemblyEmit インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit
helpviewer_keywords:
- IMetaDataAssemblyEmit interface [.NET Framework metadata]
ms.assetid: 34fb03cc-2285-4a45-ac48-ad993b7a921a
topic_type:
- apiref
ms.openlocfilehash: 5d8bc54a94e1571ff8335c934407bbf235179ecc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728291"
---
# <a name="imetadataassemblyemit-interface"></a><span data-ttu-id="c942d-102">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c942d-102">IMetaDataAssemblyEmit Interface</span></span>

<span data-ttu-id="c942d-103">共通言語ランタイムがリソースの解決および消費に使用する自己記述モデルをサポートするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="c942d-103">Provides methods that support the self-description model used by the common language runtime to resolve and consume resources.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c942d-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="c942d-104">Methods</span></span>  
  
|<span data-ttu-id="c942d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c942d-105">Method</span></span>|<span data-ttu-id="c942d-106">説明</span><span class="sxs-lookup"><span data-stu-id="c942d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c942d-107">DefineAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="c942d-107">DefineAssembly Method</span></span>](imetadataassemblyemit-defineassembly-method.md)|<span data-ttu-id="c942d-108">指定したアセンブリのメタデータを含むアセンブリ データ構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="c942d-108">Creates an assembly data structure containing metadata for the specified assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="c942d-109">DefineAssemblyRef メソッド</span><span class="sxs-lookup"><span data-stu-id="c942d-109">DefineAssemblyRef Method</span></span>](imetadataassemblyemit-defineassemblyref-method.md)|<span data-ttu-id="c942d-110">このアセンブリが参照するアセンブリのメタデータを含む `AssemblyRef` 構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="c942d-110">Creates an `AssemblyRef` structure containing metadata for the assembly that this assembly references, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="c942d-111">DefineExportedType メソッド</span><span class="sxs-lookup"><span data-stu-id="c942d-111">DefineExportedType Method</span></span>](imetadataassemblyemit-defineexportedtype-method.md)|<span data-ttu-id="c942d-112">指定してエクスポートした型のメタデータが含まれる `ExportedType` 構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="c942d-112">Creates an `ExportedType` structure containing metadata for the specified exported type, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="c942d-113">DefineFile メソッド</span><span class="sxs-lookup"><span data-stu-id="c942d-113">DefineFile Method</span></span>](imetadataassemblyemit-definefile-method.md)|<span data-ttu-id="c942d-114">このアセンブリが参照するアセンブリのメタデータを含む `File` メタデータ構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="c942d-114">Creates a `File` metadata structure containing metadata for assembly referenced by this assembly, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="c942d-115">DefineManifestResource メソッド</span><span class="sxs-lookup"><span data-stu-id="c942d-115">DefineManifestResource Method</span></span>](imetadataassemblyemit-definemanifestresource-method.md)|<span data-ttu-id="c942d-116">指定したマニフェスト リソースのメタデータを含む `ManifestResource` 構造体を作成し、関連付けられたメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="c942d-116">Creates a `ManifestResource` structure containing metadata for the specified manifest resource, and returns the associated metadata token.</span></span>|  
|[<span data-ttu-id="c942d-117">SetAssemblyProps メソッド</span><span class="sxs-lookup"><span data-stu-id="c942d-117">SetAssemblyProps Method</span></span>](imetadataassemblyemit-setassemblyprops-method.md)|<span data-ttu-id="c942d-118">指定された `Assembly` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="c942d-118">Modifies the specified `Assembly` metadata structure.</span></span>|  
|[<span data-ttu-id="c942d-119">SetAssemblyRefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="c942d-119">SetAssemblyRefProps Method</span></span>](imetadataassemblyemit-setassemblyrefprops-method.md)|<span data-ttu-id="c942d-120">指定された `AssemblyRef` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="c942d-120">Modifies the specified `AssemblyRef` metadata structure.</span></span>|  
|[<span data-ttu-id="c942d-121">SetExportedTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="c942d-121">SetExportedTypeProps Method</span></span>](imetadataassemblyemit-setexportedtypeprops-method.md)|<span data-ttu-id="c942d-122">指定された `ExportedType` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="c942d-122">Modifies the specified `ExportedType` metadata structure.</span></span>|  
|[<span data-ttu-id="c942d-123">SetFileProps メソッド</span><span class="sxs-lookup"><span data-stu-id="c942d-123">SetFileProps Method</span></span>](imetadataassemblyemit-setfileprops-method.md)|<span data-ttu-id="c942d-124">指定された `File` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="c942d-124">Modifies the specified `File` metadata structure.</span></span>|  
|[<span data-ttu-id="c942d-125">SetManifestResourceProps メソッド</span><span class="sxs-lookup"><span data-stu-id="c942d-125">SetManifestResourceProps Method</span></span>](imetadataassemblyemit-setmanifestresourceprops-method.md)|<span data-ttu-id="c942d-126">指定された `ManifestResource` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="c942d-126">Modifies the specified `ManifestResource` metadata structure.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c942d-127">解説</span><span class="sxs-lookup"><span data-stu-id="c942d-127">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c942d-128">必要条件</span><span class="sxs-lookup"><span data-stu-id="c942d-128">Requirements</span></span>  

 <span data-ttu-id="c942d-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c942d-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c942d-130">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="c942d-130">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="c942d-131">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="c942d-131">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="c942d-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c942d-132">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c942d-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="c942d-133">See also</span></span>

- [<span data-ttu-id="c942d-134">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c942d-134">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="c942d-135">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c942d-135">IMetaDataAssemblyImport Interface</span></span>](imetadataassemblyimport-interface.md)
