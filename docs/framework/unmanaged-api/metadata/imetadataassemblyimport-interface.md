---
title: IMetaDataAssemblyImport インターフェイス
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyImport
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyImport
helpviewer_keywords:
- IMetaDataAssemblyImport interface [.NET Framework metadata]
ms.assetid: 29c6fba5-4cea-417d-b484-7ed22ebff1c9
topic_type:
- apiref
ms.openlocfilehash: c556fe247754b363ece0c5dc60750068276ddcc4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95714758"
---
# <a name="imetadataassemblyimport-interface"></a><span data-ttu-id="0d03b-102">IMetaDataAssemblyImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d03b-102">IMetaDataAssemblyImport Interface</span></span>

<span data-ttu-id="0d03b-103">アセンブリ マニフェストの内容にアクセスして確認するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="0d03b-103">Provides methods to access and examine the contents of an assembly manifest.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0d03b-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="0d03b-104">Methods</span></span>  
  
|<span data-ttu-id="0d03b-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="0d03b-105">Method</span></span>|<span data-ttu-id="0d03b-106">説明</span><span class="sxs-lookup"><span data-stu-id="0d03b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0d03b-107">CloseEnum メソッド</span><span class="sxs-lookup"><span data-stu-id="0d03b-107">CloseEnum Method</span></span>](imetadataassemblyimport-closeenum-method.md)|<span data-ttu-id="0d03b-108">指定した列挙子へのハンドルを解放します。</span><span class="sxs-lookup"><span data-stu-id="0d03b-108">Releases the handle to the specified enumerator.</span></span>|  
|[<span data-ttu-id="0d03b-109">EnumAssemblyRefs メソッド</span><span class="sxs-lookup"><span data-stu-id="0d03b-109">EnumAssemblyRefs Method</span></span>](imetadataassemblyimport-enumassemblyrefs-method.md)|<span data-ttu-id="0d03b-110">`mdAssemblyRef`現在のメタデータスコープ内のアセンブリによって参照されるアセンブリのトークンを格納している列挙子へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="0d03b-110">Gets an interface pointer to an enumerator that contains the `mdAssemblyRef` tokens of the assemblies referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="0d03b-111">EnumExportedTypes メソッド</span><span class="sxs-lookup"><span data-stu-id="0d03b-111">EnumExportedTypes Method</span></span>](imetadataassemblyimport-enumexportedtypes-method.md)|<span data-ttu-id="0d03b-112">`mdExportedType`現在のメタデータスコープ内のアセンブリによって参照される COM 型のトークンを格納している列挙子へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="0d03b-112">Gets an interface pointer to an enumerator that contains the `mdExportedType` tokens of the COM types referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="0d03b-113">EnumFiles メソッド</span><span class="sxs-lookup"><span data-stu-id="0d03b-113">EnumFiles Method</span></span>](imetadataassemblyimport-enumfiles-method.md)|<span data-ttu-id="0d03b-114">`mdFile`現在のメタデータスコープ内のアセンブリによって参照されるファイルのトークンを格納している列挙子へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="0d03b-114">Gets an interface pointer to an enumerator that contains the `mdFile` tokens of the files referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="0d03b-115">EnumManifestResources メソッド</span><span class="sxs-lookup"><span data-stu-id="0d03b-115">EnumManifestResources Method</span></span>](imetadataassemblyimport-enummanifestresources-method.md)|<span data-ttu-id="0d03b-116">`mdManifestResource`現在のメタデータスコープ内のアセンブリによって参照されているリソースのトークンを格納している列挙子へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="0d03b-116">Gets an interface pointer to an enumerator that contains the `mdManifestResource` tokens of the resources referenced by the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="0d03b-117">FindAssembliesByName メソッド</span><span class="sxs-lookup"><span data-stu-id="0d03b-117">FindAssembliesByName Method</span></span>](imetadataassemblyimport-findassembliesbyname-method.md)|<span data-ttu-id="0d03b-118">`mdAssemblyRef`指定した名前のアセンブリのトークンの配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="0d03b-118">Gets an array of `mdAssemblyRef` tokens for the assemblies with the specified name.</span></span>|  
|[<span data-ttu-id="0d03b-119">FindExportedTypeByName メソッド</span><span class="sxs-lookup"><span data-stu-id="0d03b-119">FindExportedTypeByName Method</span></span>](imetadataassemblyimport-findexportedtypebyname-method.md)|<span data-ttu-id="0d03b-120">指定し `mdExportedType` た名前の COM 型のトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="0d03b-120">Gets an `mdExportedType` token for the COM type with the specified name.</span></span>|  
|[<span data-ttu-id="0d03b-121">FindManifestResourceByName メソッド</span><span class="sxs-lookup"><span data-stu-id="0d03b-121">FindManifestResourceByName Method</span></span>](imetadataassemblyimport-findmanifestresourcebyname-method.md)|<span data-ttu-id="0d03b-122">指定し `mdManifestResource` た名前のリソースのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="0d03b-122">Gets an `mdManifestResource` token for the resource with the specified name.</span></span>|  
|[<span data-ttu-id="0d03b-123">GetAssemblyFromScope メソッド</span><span class="sxs-lookup"><span data-stu-id="0d03b-123">GetAssemblyFromScope Method</span></span>](imetadataassemblyimport-getassemblyfromscope-method.md)|<span data-ttu-id="0d03b-124">現在のメタデータスコープ内のアセンブリのトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="0d03b-124">Gets the token for the assembly in the current metadata scope.</span></span>|  
|[<span data-ttu-id="0d03b-125">GetAssemblyProps メソッド</span><span class="sxs-lookup"><span data-stu-id="0d03b-125">GetAssemblyProps Method</span></span>](imetadataassemblyimport-getassemblyprops-method.md)|<span data-ttu-id="0d03b-126">指定したアセンブリのプロパティ設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="0d03b-126">Gets the property settings of the specified assembly.</span></span>|  
|[<span data-ttu-id="0d03b-127">GetAssemblyRefProps メソッド</span><span class="sxs-lookup"><span data-stu-id="0d03b-127">GetAssemblyRefProps Method</span></span>](imetadataassemblyimport-getassemblyrefprops-method.md)|<span data-ttu-id="0d03b-128">指定したトークンのプロパティ設定を取得し `mdAssemblyRef` ます。</span><span class="sxs-lookup"><span data-stu-id="0d03b-128">Gets the property settings of the specified `mdAssemblyRef` token.</span></span>|  
|[<span data-ttu-id="0d03b-129">GetExportedTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="0d03b-129">GetExportedTypeProps Method</span></span>](imetadataassemblyimport-getexportedtypeprops-method.md)|<span data-ttu-id="0d03b-130">指定した COM 型のプロパティ設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="0d03b-130">Gets the property settings of the specified COM type.</span></span>|  
|[<span data-ttu-id="0d03b-131">GetFileProps メソッド</span><span class="sxs-lookup"><span data-stu-id="0d03b-131">GetFileProps Method</span></span>](imetadataassemblyimport-getfileprops-method.md)|<span data-ttu-id="0d03b-132">指定されたファイルのプロパティ設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="0d03b-132">Gets the property settings of the specified file.</span></span>|  
|[<span data-ttu-id="0d03b-133">GetManifestResourceProps メソッド</span><span class="sxs-lookup"><span data-stu-id="0d03b-133">GetManifestResourceProps Method</span></span>](imetadataassemblyimport-getmanifestresourceprops-method.md)|<span data-ttu-id="0d03b-134">指定されたマニフェストリソースのプロパティ設定を取得します。</span><span class="sxs-lookup"><span data-stu-id="0d03b-134">Gets the property settings of the specified manifest resource.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d03b-135">要件</span><span class="sxs-lookup"><span data-stu-id="0d03b-135">Requirements</span></span>  

 <span data-ttu-id="0d03b-136">**プラットフォーム:** 「 [システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0d03b-136">**Platform:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d03b-137">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="0d03b-137">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="0d03b-138">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="0d03b-138">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="0d03b-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d03b-139">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d03b-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="0d03b-140">See also</span></span>

- [<span data-ttu-id="0d03b-141">メタデータ インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d03b-141">Metadata Interfaces</span></span>](metadata-interfaces.md)
- [<span data-ttu-id="0d03b-142">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0d03b-142">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
