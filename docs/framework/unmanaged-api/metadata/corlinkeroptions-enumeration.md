---
title: CorLinkerOptions 列挙型
ms.date: 03/30/2017
api_name:
- CorLinkerOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorLinkerOptions
helpviewer_keywords:
- CorLinkerOptions enumeration [.NET Framework metadata]
ms.assetid: a656aad6-cc7e-4994-8251-004a6a45e18f
topic_type:
- apiref
ms.openlocfilehash: 188301d31b2fcfaf7b1c6139111e8f1296ccf7e5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677246"
---
# <a name="corlinkeroptions-enumeration"></a><span data-ttu-id="888cf-102">CorLinkerOptions 列挙型</span><span class="sxs-lookup"><span data-stu-id="888cf-102">CorLinkerOptions Enumeration</span></span>

<span data-ttu-id="888cf-103">メタデータ リンカーのオプションを選択するためのフラグを指定します。</span><span class="sxs-lookup"><span data-stu-id="888cf-103">Specifies flags to select options for the metadata linker.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="888cf-104">構文</span><span class="sxs-lookup"><span data-stu-id="888cf-104">Syntax</span></span>  
  
```cpp  
typedef enum CorLinkerOptions {  
    MDAssembly          = 0x00000000,  
    MDNetModule         = 0x00000001,  
} CorLinkerOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="888cf-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="888cf-105">Members</span></span>  
  
|<span data-ttu-id="888cf-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="888cf-106">Member</span></span>|<span data-ttu-id="888cf-107">説明</span><span class="sxs-lookup"><span data-stu-id="888cf-107">Description</span></span>|  
|------------|-----------------|  
|`MDAssembly`|<span data-ttu-id="888cf-108">プライベート型とグローバル関数は保持されません。</span><span class="sxs-lookup"><span data-stu-id="888cf-108">The private types and global functions are not preserved.</span></span>|  
|`MDNetModule`|<span data-ttu-id="888cf-109">プライベート型とグローバル関数が保持されます。</span><span class="sxs-lookup"><span data-stu-id="888cf-109">The private types and global functions are preserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="888cf-110">要件</span><span class="sxs-lookup"><span data-stu-id="888cf-110">Requirements</span></span>  

 <span data-ttu-id="888cf-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="888cf-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="888cf-112">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="888cf-112">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="888cf-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="888cf-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="888cf-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="888cf-114">See also</span></span>

- [<span data-ttu-id="888cf-115">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="888cf-115">Metadata Enumerations</span></span>](metadata-enumerations.md)
