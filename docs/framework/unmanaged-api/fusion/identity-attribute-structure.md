---
title: IDENTITY_ATTRIBUTE 構造体
ms.date: 03/30/2017
api_name:
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
ms.openlocfilehash: da4b1d6f2a7079ef33859fce29c9555ac06fcfc2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725652"
---
# <a name="identity_attribute-structure"></a><span data-ttu-id="b7711-102">IDENTITY_ATTRIBUTE 構造体</span><span class="sxs-lookup"><span data-stu-id="b7711-102">IDENTITY_ATTRIBUTE Structure</span></span>

<span data-ttu-id="b7711-103">[IDefinitionIdentity](idefinitionidentity-interface.md)インスタンスに関するメタデータ属性情報を格納します。</span><span class="sxs-lookup"><span data-stu-id="b7711-103">Contains metadata attribute information about an [IDefinitionIdentity](idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b7711-104">構文</span><span class="sxs-lookup"><span data-stu-id="b7711-104">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="b7711-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="b7711-105">Members</span></span>  
  
|<span data-ttu-id="b7711-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b7711-106">Member</span></span>|<span data-ttu-id="b7711-107">説明</span><span class="sxs-lookup"><span data-stu-id="b7711-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="b7711-108">属性が含まれている名前空間を含む null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b7711-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="b7711-109">属性の名前を含む null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b7711-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="b7711-110">属性の値を格納している null で終わる文字列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="b7711-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7711-111">注釈</span><span class="sxs-lookup"><span data-stu-id="b7711-111">Remarks</span></span>  

 <span data-ttu-id="b7711-112">構造体には、 `IDENTITY_ATTRIBUTE` null で終わる文字列への3つのポインターが含まれています。</span><span class="sxs-lookup"><span data-stu-id="b7711-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="b7711-113">これら3つの文字列は、1つの属性を表します。</span><span class="sxs-lookup"><span data-stu-id="b7711-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="b7711-114">構造体のインスタンス `IDENTITY_ATTRIBUTE` は、 [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) 構造体のインスタンスに関連付けられています。</span><span class="sxs-lookup"><span data-stu-id="b7711-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="b7711-115">`IDENTITY_ATTRIBUTE`構造体には実際の文字列が含まれ、対応する構造体には、 `IDENTITY_ATTRIBUTE_BLOB` 構造体に示されている3つの文字列へのオフセットが一覧表示され `IDENTITY_ATTRIBUTE` ます。</span><span class="sxs-lookup"><span data-stu-id="b7711-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7711-116">要件</span><span class="sxs-lookup"><span data-stu-id="b7711-116">Requirements</span></span>  

 <span data-ttu-id="b7711-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b7711-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7711-118">**ヘッダー:** 分離 .h</span><span class="sxs-lookup"><span data-stu-id="b7711-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="b7711-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7711-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7711-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7711-120">See also</span></span>

- [<span data-ttu-id="b7711-121">IDefinitionIdentity インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7711-121">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
- [<span data-ttu-id="b7711-122">IDENTITY_ATTRIBUTE_BLOB 構造体</span><span class="sxs-lookup"><span data-stu-id="b7711-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](identity-attribute-blob-structure.md)
- [<span data-ttu-id="b7711-123">Fusion 構造体</span><span class="sxs-lookup"><span data-stu-id="b7711-123">Fusion Structures</span></span>](fusion-structures.md)
