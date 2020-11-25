---
title: COR_FIELD 構造体
ms.date: 03/30/2017
api_name:
- COR_FIELD
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_FIELD
helpviewer_keywords:
- COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type:
- apiref
ms.openlocfilehash: ae8e907d0e0d6ef5030b3e9aa1f1b3dcef50193e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726627"
---
# <a name="cor_field-structure"></a><span data-ttu-id="8465c-102">COR_FIELD 構造体</span><span class="sxs-lookup"><span data-stu-id="8465c-102">COR_FIELD Structure</span></span>

<span data-ttu-id="8465c-103">オブジェクトのフィールドに関する情報が提供されます。</span><span class="sxs-lookup"><span data-stu-id="8465c-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8465c-104">構文</span><span class="sxs-lookup"><span data-stu-id="8465c-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="8465c-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="8465c-105">Members</span></span>  
  
|<span data-ttu-id="8465c-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="8465c-106">Member</span></span>|<span data-ttu-id="8465c-107">説明</span><span class="sxs-lookup"><span data-stu-id="8465c-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="8465c-108">`mdFieldDef`フィールド情報を取得するために使用できるトークン。</span><span class="sxs-lookup"><span data-stu-id="8465c-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="8465c-109">オブジェクト内のフィールドデータへのオフセット (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="8465c-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="8465c-110">このフィールドの型を識別する [COR_TYPEID](cor-typeid-structure.md) 値。</span><span class="sxs-lookup"><span data-stu-id="8465c-110">A [COR_TYPEID](cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="8465c-111">フィールドの型を示す CorElementType 列挙値。</span><span class="sxs-lookup"><span data-stu-id="8465c-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8465c-112">解説</span><span class="sxs-lookup"><span data-stu-id="8465c-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8465c-113">必要条件</span><span class="sxs-lookup"><span data-stu-id="8465c-113">Requirements</span></span>  

 <span data-ttu-id="8465c-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8465c-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8465c-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8465c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8465c-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8465c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8465c-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8465c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8465c-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="8465c-118">See also</span></span>

- [<span data-ttu-id="8465c-119">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="8465c-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="8465c-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="8465c-120">Debugging</span></span>](index.md)
