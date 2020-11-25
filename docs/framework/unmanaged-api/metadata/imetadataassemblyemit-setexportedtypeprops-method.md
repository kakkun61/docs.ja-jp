---
title: IMetaDataAssemblyEmit::SetExportedTypeProps メソッド
ms.date: 03/30/2017
api_name:
- IMetaDataAssemblyEmit.SetExportedTypeProps
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataAssemblyEmit::SetExportedTypeProps
helpviewer_keywords:
- SetExportedTypeProps method [.NET Framework metadata]
- IMetaDataAssemblyEmit::SetExportedTypeProps method [.NET Framework metadata]
ms.assetid: 1c090153-fd5f-46c7-9cff-39a78d992c8f
topic_type:
- apiref
ms.openlocfilehash: 076d027945dc27942e4b0989e14e86d829f76679
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713489"
---
# <a name="imetadataassemblyemitsetexportedtypeprops-method"></a><span data-ttu-id="a2cc5-102">IMetaDataAssemblyEmit::SetExportedTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="a2cc5-102">IMetaDataAssemblyEmit::SetExportedTypeProps Method</span></span>

<span data-ttu-id="a2cc5-103">指定された `ExportedType` メタデータ構造体を変更します。</span><span class="sxs-lookup"><span data-stu-id="a2cc5-103">Modifies the specified `ExportedType` metadata structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2cc5-104">構文</span><span class="sxs-lookup"><span data-stu-id="a2cc5-104">Syntax</span></span>  
  
```cpp  
HRESULT SetExportedTypeProps (  
    [in] mdExportedType   ct,
    [in] mdToken          tkImplementation,  
    [in] mdTypeDef        tkTypeDef,  
    [in] DWORD            dwExportedTypeFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2cc5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a2cc5-105">Parameters</span></span>  

 `ct`  
 <span data-ttu-id="a2cc5-106">から変更するメタデータ構造を指定するメタデータトークン `ExportedType` 。</span><span class="sxs-lookup"><span data-stu-id="a2cc5-106">[in] The metadata token that specifies the `ExportedType` metadata structure to be modified.</span></span>  
  
 `tkImplementation`  
 <span data-ttu-id="a2cc5-107">から `File` `AssemblyRef` `ExportedType` この型の実装方法を指定する、、、または型のトークン。</span><span class="sxs-lookup"><span data-stu-id="a2cc5-107">[in] The token, of type `File`, `AssemblyRef`, or `ExportedType`, that specifies how this type is implemented.</span></span>  
  
 `tkTypeDef`  
 <span data-ttu-id="a2cc5-108">から `TypeDef` コードファイルで参照されるトークン。</span><span class="sxs-lookup"><span data-stu-id="a2cc5-108">[in] The `TypeDef` token referenced in the code file.</span></span>  
  
 `dwExportedTypeFlags`  
 <span data-ttu-id="a2cc5-109">から型の属性を指定する値のビットごとの組み合わせ。</span><span class="sxs-lookup"><span data-stu-id="a2cc5-109">[in] A bitwise combination of values that specify attributes of the type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2cc5-110">注釈</span><span class="sxs-lookup"><span data-stu-id="a2cc5-110">Remarks</span></span>  

 <span data-ttu-id="a2cc5-111">メタデータ構造を作成するには `ExportedType` 、 [IMetaDataAssemblyEmit::D efineExportedType](imetadataassemblyemit-defineexportedtype-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="a2cc5-111">To create an `ExportedType` metadata structure, use the [IMetaDataAssemblyEmit::DefineExportedType](imetadataassemblyemit-defineexportedtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2cc5-112">要件</span><span class="sxs-lookup"><span data-stu-id="a2cc5-112">Requirements</span></span>  

 <span data-ttu-id="a2cc5-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a2cc5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2cc5-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="a2cc5-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a2cc5-115">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="a2cc5-115">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a2cc5-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2cc5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2cc5-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2cc5-117">See also</span></span>

- [<span data-ttu-id="a2cc5-118">IMetaDataAssemblyEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2cc5-118">IMetaDataAssemblyEmit Interface</span></span>](imetadataassemblyemit-interface.md)
