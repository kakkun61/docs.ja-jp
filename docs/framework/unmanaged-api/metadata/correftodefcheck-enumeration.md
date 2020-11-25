---
title: CorRefToDefCheck 列挙型
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
ms.openlocfilehash: e7ce604acddb88d5a15844cbce2622b21e364cc1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706113"
---
# <a name="correftodefcheck-enumeration"></a><span data-ttu-id="c7122-102">CorRefToDefCheck 列挙型</span><span class="sxs-lookup"><span data-stu-id="c7122-102">CorRefToDefCheck Enumeration</span></span>

<span data-ttu-id="c7122-103">コードを最適化するために定義に変換される、参照先アイテムを制御するフラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7122-103">Specifies flags to control which referenced items are converted to their definitions in order to optimize the code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7122-104">構文</span><span class="sxs-lookup"><span data-stu-id="c7122-104">Syntax</span></span>  
  
```cpp  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a><span data-ttu-id="c7122-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="c7122-105">Members</span></span>  
  
|<span data-ttu-id="c7122-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="c7122-106">Member</span></span>|<span data-ttu-id="c7122-107">説明</span><span class="sxs-lookup"><span data-stu-id="c7122-107">Description</span></span>|  
|------------|-----------------|  
|`MDRefToDefDefault`|<span data-ttu-id="c7122-108">型参照とメンバー参照を定義に変換する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7122-108">Specifies that type references and member references should be converted to definitions.</span></span> <span data-ttu-id="c7122-109">これは既定値 ( `MDTypeRefToDef` &#124; `MDMemberRefToDef` ) です。</span><span class="sxs-lookup"><span data-stu-id="c7122-109">This is the default value (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).</span></span>|  
|`MDRefToDefAll`|<span data-ttu-id="c7122-110">参照されるすべての項目を定義に変換することを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7122-110">Specifies that all referenced items should be converted to definitions.</span></span>|  
|`MDRefToDefNone`|<span data-ttu-id="c7122-111">参照される項目を定義に変換しないことを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7122-111">Specifies that no referenced items should be converted to definitions.</span></span>|  
|`MDTypeRefToDef`|<span data-ttu-id="c7122-112">型の参照のみを型定義に変換することを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7122-112">Specifies that only type references should be converted to type definitions.</span></span>|  
|`MDMemberRefToDef`|<span data-ttu-id="c7122-113">メンバー参照のみを定義に変換することを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7122-113">Specifies that only member references should be converted to definitions.</span></span> <span data-ttu-id="c7122-114">つまり、メンバー参照は、メソッド定義またはフィールド定義に変換される必要があります。</span><span class="sxs-lookup"><span data-stu-id="c7122-114">That is, member references should be converted to either method definitions or field definitions.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c7122-115">要件</span><span class="sxs-lookup"><span data-stu-id="c7122-115">Requirements</span></span>  

 <span data-ttu-id="c7122-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c7122-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7122-117">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="c7122-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="c7122-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7122-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7122-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7122-119">See also</span></span>

- [<span data-ttu-id="c7122-120">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="c7122-120">Metadata Enumerations</span></span>](metadata-enumerations.md)
