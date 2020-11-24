---
title: CorMethodSemanticsAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
ms.openlocfilehash: 347b323951b0125ffa5f82626b2d9b235079492c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676947"
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="a62b6-102">CorMethodSemanticsAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="a62b6-102">CorMethodSemanticsAttr Enumeration</span></span>

<span data-ttu-id="a62b6-103">メソッドとそれに関連付けられているプロパティまたはイベントとの関係を記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="a62b6-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a62b6-104">構文</span><span class="sxs-lookup"><span data-stu-id="a62b6-104">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="a62b6-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="a62b6-105">Members</span></span>  
  
|<span data-ttu-id="a62b6-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="a62b6-106">Member</span></span>|<span data-ttu-id="a62b6-107">説明</span><span class="sxs-lookup"><span data-stu-id="a62b6-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="a62b6-108">メソッドがプロパティのアクセサーであることを指定し `set` ます。</span><span class="sxs-lookup"><span data-stu-id="a62b6-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="a62b6-109">メソッドがプロパティのアクセサーであることを指定し `get` ます。</span><span class="sxs-lookup"><span data-stu-id="a62b6-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="a62b6-110">メソッドが、ここで定義されたプロパティ以外のプロパティまたはイベントへのリレーションシップを持つことを指定します。</span><span class="sxs-lookup"><span data-stu-id="a62b6-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="a62b6-111">メソッドがイベントのハンドラーメソッドを追加することを指定します。</span><span class="sxs-lookup"><span data-stu-id="a62b6-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="a62b6-112">メソッドがイベントのハンドラーメソッドを削除することを指定します。</span><span class="sxs-lookup"><span data-stu-id="a62b6-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="a62b6-113">メソッドがイベントを発生させることを指定します。</span><span class="sxs-lookup"><span data-stu-id="a62b6-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a62b6-114">要件</span><span class="sxs-lookup"><span data-stu-id="a62b6-114">Requirements</span></span>  

 <span data-ttu-id="a62b6-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a62b6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a62b6-116">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="a62b6-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="a62b6-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a62b6-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a62b6-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a62b6-118">See also</span></span>

- [<span data-ttu-id="a62b6-119">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="a62b6-119">Metadata Enumerations</span></span>](metadata-enumerations.md)
