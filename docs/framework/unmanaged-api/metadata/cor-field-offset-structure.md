---
title: COR_FIELD_OFFSET 構造体
ms.date: 03/30/2017
api_name:
- COR_FIELD_OFFSET
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_FIELD_OFFSET
helpviewer_keywords:
- COR_FIELD_OFFSET structure [.NET Framework metadata]
ms.assetid: cced5298-277f-4a5a-8ecf-a0050c1096ea
topic_type:
- apiref
ms.openlocfilehash: 1a8ab5aa5909af60089d5e4cc8092e15bc75e8cc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724183"
---
# <a name="cor_field_offset-structure"></a><span data-ttu-id="d43b5-102">COR_FIELD_OFFSET 構造体</span><span class="sxs-lookup"><span data-stu-id="d43b5-102">COR_FIELD_OFFSET Structure</span></span>

<span data-ttu-id="d43b5-103">指定したフィールドのクラス内の相対位置を格納します。</span><span class="sxs-lookup"><span data-stu-id="d43b5-103">Stores the offset, within a class, of the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d43b5-104">構文</span><span class="sxs-lookup"><span data-stu-id="d43b5-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD_OFFSET {  
    mdFieldDef  ridOfField;  
    ULONG       ulOffset;  
} COR_FIELD_OFFSET;  
```  
  
## <a name="members"></a><span data-ttu-id="d43b5-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="d43b5-105">Members</span></span>  
  
|<span data-ttu-id="d43b5-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="d43b5-106">Member</span></span>|<span data-ttu-id="d43b5-107">説明</span><span class="sxs-lookup"><span data-stu-id="d43b5-107">Description</span></span>|  
|------------|-----------------|  
|`ridOfField`|<span data-ttu-id="d43b5-108">`mdFieldDef`フィールドを表すメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="d43b5-108">An `mdFieldDef` metadata token that represents the field.</span></span>|  
|`ulOffset`|<span data-ttu-id="d43b5-109">クラス内のフィールドのオフセット。</span><span class="sxs-lookup"><span data-stu-id="d43b5-109">The field's offset within its class.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d43b5-110">注釈</span><span class="sxs-lookup"><span data-stu-id="d43b5-110">Remarks</span></span>  

 <span data-ttu-id="d43b5-111">[IMetaDataImport:: GetClassLayout](imetadataimport-getclasslayout-method.md) メソッドと [IMetaDataEmit:: SetClassLayout](imetadataemit-setclasslayout-method.md) メソッドは、型のパラメーターを受け取り `COR_FIELD_OFFSET` ます。</span><span class="sxs-lookup"><span data-stu-id="d43b5-111">[IMetaDataImport::GetClassLayout](imetadataimport-getclasslayout-method.md) and [IMetaDataEmit::SetClassLayout](imetadataemit-setclasslayout-method.md) methods take a parameter of type `COR_FIELD_OFFSET`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d43b5-112">要件</span><span class="sxs-lookup"><span data-stu-id="d43b5-112">Requirements</span></span>  

 <span data-ttu-id="d43b5-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d43b5-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d43b5-114">**ヘッダー:** CorHdr .h、Corprof.idl</span><span class="sxs-lookup"><span data-stu-id="d43b5-114">**Header:** CorHdr.h, CorProf.idl</span></span>  
  
 <span data-ttu-id="d43b5-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d43b5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d43b5-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="d43b5-116">See also</span></span>

- [<span data-ttu-id="d43b5-117">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="d43b5-117">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="d43b5-118">IMetaDataEmit インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d43b5-118">IMetaDataEmit Interface</span></span>](imetadataemit-interface.md)
- [<span data-ttu-id="d43b5-119">IMetaDataImport インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d43b5-119">IMetaDataImport Interface</span></span>](imetadataimport-interface.md)
