---
title: CorManifestResourceFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorManifestResourceFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorManifestResourceFlags
helpviewer_keywords:
- CorManifestResourceFlags enumeration [.NET Framework metadata]
ms.assetid: 1b0306b7-622b-4b57-8edc-3c713bb147ae
topic_type:
- apiref
ms.openlocfilehash: f8334cb44042e21c086bc05c723e99b0c079fa2c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677064"
---
# <a name="cormanifestresourceflags-enumeration"></a><span data-ttu-id="ea653-102">CorManifestResourceFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="ea653-102">CorManifestResourceFlags Enumeration</span></span>

<span data-ttu-id="ea653-103">アセンブリマニフェストでエンコードされたリソースを表示するかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="ea653-103">Indicates the visibility of resources encoded in an assembly manifest.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea653-104">構文</span><span class="sxs-lookup"><span data-stu-id="ea653-104">Syntax</span></span>  
  
```cpp  
typedef enum CorManifestResourceFlags {  
  
    mrVisibilityMask        =   0x0007,  
    mrPublic                =   0x0001,  
    mrPrivate               =   0x0002  
  
} CorManifestResourceFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="ea653-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="ea653-105">Members</span></span>  
  
|<span data-ttu-id="ea653-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="ea653-106">Member</span></span>|<span data-ttu-id="ea653-107">説明</span><span class="sxs-lookup"><span data-stu-id="ea653-107">Description</span></span>|  
|------------|-----------------|  
|`mrVisibilityMask`|<span data-ttu-id="ea653-108">予約済み。</span><span class="sxs-lookup"><span data-stu-id="ea653-108">Reserved.</span></span>|  
|`mrPublic`|<span data-ttu-id="ea653-109">リソースはパブリックです。</span><span class="sxs-lookup"><span data-stu-id="ea653-109">The resources are public.</span></span>|  
|`mrPrivate`|<span data-ttu-id="ea653-110">リソースはプライベートです。</span><span class="sxs-lookup"><span data-stu-id="ea653-110">The resources are private.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ea653-111">要件</span><span class="sxs-lookup"><span data-stu-id="ea653-111">Requirements</span></span>  

 <span data-ttu-id="ea653-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ea653-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ea653-113">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="ea653-113">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ea653-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea653-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ea653-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="ea653-115">See also</span></span>

- [<span data-ttu-id="ea653-116">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="ea653-116">Metadata Enumerations</span></span>](metadata-enumerations.md)
