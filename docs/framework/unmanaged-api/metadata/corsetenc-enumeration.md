---
title: CorSetENC 列挙型
ms.date: 03/30/2017
api_name:
- CorSetENC
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSetENC
helpviewer_keywords:
- CorSetENC enumeration [.NET Framework metadata]
ms.assetid: fe4150e8-071d-43fb-8e06-c3c616dbeed2
topic_type:
- apiref
ms.openlocfilehash: df945803f2d56d04ccc68f314eb55665579ed7fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705983"
---
# <a name="corsetenc-enumeration"></a><span data-ttu-id="882b7-102">CorSetENC 列挙型</span><span class="sxs-lookup"><span data-stu-id="882b7-102">CorSetENC Enumeration</span></span>

<span data-ttu-id="882b7-103">メタデータの生成中の動作を決定する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="882b7-103">Contains values used to influence behavior during the generation of metadata.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="882b7-104">構文</span><span class="sxs-lookup"><span data-stu-id="882b7-104">Syntax</span></span>  
  
```cpp  
typedef enum CorSetENC {  
  
    MDSetENCOn                  = 0x00000001,  
    MDSetENCOff                 = 0x00000002,  
  
    MDUpdateENC                 = 0x00000001,  
    MDUpdateFull                = 0x00000002,  
    MDUpdateExtension           = 0x00000003,  
    MDUpdateIncremental         = 0x00000004,  
    MDUpdateDelta               = 0x00000005,  
    MDUpdateMask                = 0x00000007  
  
} CorSetENC;  
```  
  
## <a name="members"></a><span data-ttu-id="882b7-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="882b7-105">Members</span></span>  
  
|<span data-ttu-id="882b7-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="882b7-106">Member</span></span>|<span data-ttu-id="882b7-107">説明</span><span class="sxs-lookup"><span data-stu-id="882b7-107">Description</span></span>|  
|------------|-----------------|  
|`MDSetENCOn`|<span data-ttu-id="882b7-108">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="882b7-108">Obsolete.</span></span>|  
|`MDSetENCOff`|<span data-ttu-id="882b7-109">互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="882b7-109">Obsolete.</span></span>|  
|`MDUpdateENC`|<span data-ttu-id="882b7-110">メタデータを更新できるのに対して、トークンを移動できないことを示します。</span><span class="sxs-lookup"><span data-stu-id="882b7-110">Indicates that whereas metadata can be updated, tokens cannot be moved.</span></span>|  
|`MDUpdateFull`|<span data-ttu-id="882b7-111">更新中にトークンを移動できることを示します。</span><span class="sxs-lookup"><span data-stu-id="882b7-111">Indicates that tokens can be moved during updates.</span></span>|  
|`MDUpdateExtension`|<span data-ttu-id="882b7-112">更新プログラムが追加のみで構成されることを示します。</span><span class="sxs-lookup"><span data-stu-id="882b7-112">Indicates that updates can consist only of additions.</span></span> <span data-ttu-id="882b7-113">トークンは移動できません。</span><span class="sxs-lookup"><span data-stu-id="882b7-113">Tokens cannot be moved.</span></span>|  
|`MDUpdateIncremental`|<span data-ttu-id="882b7-114">コンパイルが増分であることを示します。</span><span class="sxs-lookup"><span data-stu-id="882b7-114">Indicates that compilation is incremental.</span></span>|  
|`MDUpdateDelta`|<span data-ttu-id="882b7-115">は、変更されたメタデータのみを保存することを示します。</span><span class="sxs-lookup"><span data-stu-id="882b7-115">Indicates that only changed metadata should be saved.</span></span>|  
|`MDUpdateMask`|<span data-ttu-id="882b7-116">`MDUpdateENC`、、およびが含まれ `MDUpdateFull` `MDUpdateIncremental` ます。</span><span class="sxs-lookup"><span data-stu-id="882b7-116">Includes `MDUpdateENC`, `MDUpdateFull` and `MDUpdateIncremental`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="882b7-117">要件</span><span class="sxs-lookup"><span data-stu-id="882b7-117">Requirements</span></span>  

 <span data-ttu-id="882b7-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="882b7-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="882b7-119">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="882b7-119">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="882b7-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="882b7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="882b7-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="882b7-121">See also</span></span>

- [<span data-ttu-id="882b7-122">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="882b7-122">Metadata Enumerations</span></span>](metadata-enumerations.md)
