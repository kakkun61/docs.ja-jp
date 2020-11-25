---
title: IMetaDataAssemblyEmit::SetManifestResourceProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetManifestResourceProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetManifestResourceProps
helpviewer_keywords:
- SetManifestResourceProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetManifestResourceProps method [.NET Framework metadata]
ms.assetid: ef77efd1-849c-4e51-ba92-7ee3d2bf0339
topic_type:
- apiref
ms.openlocfilehash: c46a3bc34ba7efa760e50416e9a6c39779727813
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95708923"
---
# <a name="imetadataassemblyemitsetmanifestresourceprops-method"></a><span data-ttu-id="83c11-102">IMetaDataAssemblyEmit::SetManifestResourceProps メソッド</span><span class="sxs-lookup"><span data-stu-id="83c11-102">IMetaDataAssemblyEmit::SetManifestResourceProps Method</span></span>

<span data-ttu-id="83c11-103">指定された `ManifestResource` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="83c11-103">Modifies the specified `ManifestResource` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83c11-104">構文</span><span class="sxs-lookup"><span data-stu-id="83c11-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestResourceProps (  
    [in] mdManifestResource  mr,  
    [in] mdToken             tkImplementation,
    [in] DWORD               dwOffset,  
    [in] DWORD               dwResourceFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83c11-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="83c11-105">Parameters</span></span>  

 `mr`  
 <span data-ttu-id="83c11-106">から `ManifestResource` 変更するメタデータ構造を指定するトークン。</span><span class="sxs-lookup"><span data-stu-id="83c11-106">[in] The token that specifies the `ManifestResource` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="83c11-107">から `File` リソースプロバイダーにマップされる型またはのトークン `AssemblyRef` 。</span><span class="sxs-lookup"><span data-stu-id="83c11-107">[in] The token, of type `File` or `AssemblyRef`, that maps to the resource provider.</span></span>  
  
 `dwOffset`  
 <span data-ttu-id="83c11-108">からファイル内のリソースの先頭へのオフセット。</span><span class="sxs-lookup"><span data-stu-id="83c11-108">[in] The offset to the beginning of the resource within the file.</span></span>  
  
 `dwResourceFlags`  
 <span data-ttu-id="83c11-109">からリソースの属性を指定するフラグ値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="83c11-109">[in] A bitwise combination of flag values that specify the attributes of the resource.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83c11-110">注釈</span><span class="sxs-lookup"><span data-stu-id="83c11-110">Remarks</span></span>  

 <span data-ttu-id="83c11-111">メタデータ構造を作成するには `ManifestResource` 、 [IMetaDataAssemblyEmit::D efinemanifestresource](imetadataassemblyemit-definemanifestresource-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="83c11-111">To create a `ManifestResource` metadata structure, use the [IMetaDataAssemblyEmit::DefineManifestResource](imetadataassemblyemit-definemanifestresource-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83c11-112">要件</span><span class="sxs-lookup"><span data-stu-id="83c11-112">Requirements</span></span>  

 <span data-ttu-id="83c11-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83c11-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83c11-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="83c11-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="83c11-115">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="83c11-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="83c11-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83c11-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83c11-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="83c11-117">See also</span></span>

- [<span data-ttu-id="83c11-118">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="83c11-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
