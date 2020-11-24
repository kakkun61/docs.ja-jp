---
title: CorNativeLinkFlags 列挙型
ms.date: 03/30/2017
api_name:
- CorNativeLinkFlags
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeLinkFlags
helpviewer_keywords:
- CorNativeLinkFlags enumeration [.NET Framework metadata]
ms.assetid: 8027df7c-cfad-4724-bda0-7538d9519070
topic_type:
- apiref
ms.openlocfilehash: ef9b177bee0651b6b8ea994610315ce93524e8e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95676934"
---
# <a name="cornativelinkflags-enumeration"></a><span data-ttu-id="781f4-102">CorNativeLinkFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="781f4-102">CorNativeLinkFlags Enumeration</span></span>

<span data-ttu-id="781f4-103">ネイティブ コードをリンクするときに、リンカーが使用するフラグ値を提供します。</span><span class="sxs-lookup"><span data-stu-id="781f4-103">Provides flag values used by the linker when linking native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="781f4-104">構文</span><span class="sxs-lookup"><span data-stu-id="781f4-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    nlfNone         = 0x00,  
    nlfLastError    = 0x01,  
    nlfNoMangle     = 0x02,  
    nlfMaxValue     = 0x03  
} CorNativeLinkFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="781f4-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="781f4-105">Members</span></span>  
  
|<span data-ttu-id="781f4-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="781f4-106">Member</span></span>|<span data-ttu-id="781f4-107">説明</span><span class="sxs-lookup"><span data-stu-id="781f4-107">Description</span></span>|  
|------------|-----------------|  
|`nlfNone`|<span data-ttu-id="781f4-108">フラグがないことを示します。</span><span class="sxs-lookup"><span data-stu-id="781f4-108">Indicates no flags.</span></span>|  
|`nlfLastError`|<span data-ttu-id="781f4-109">キーワードを示し `setLastError` ます。</span><span class="sxs-lookup"><span data-stu-id="781f4-109">Indicates a `setLastError` keyword.</span></span>|  
|`nlfNoMangle`|<span data-ttu-id="781f4-110">キーワードを示し `nomangle` ます。</span><span class="sxs-lookup"><span data-stu-id="781f4-110">Indicates a `nomangle` keyword.</span></span>|  
|`nlfMaxValue`|<span data-ttu-id="781f4-111">使用されていません。</span><span class="sxs-lookup"><span data-stu-id="781f4-111">Not used.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="781f4-112">要件</span><span class="sxs-lookup"><span data-stu-id="781f4-112">Requirements</span></span>  

 <span data-ttu-id="781f4-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="781f4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="781f4-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="781f4-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="781f4-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="781f4-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="781f4-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="781f4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="781f4-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="781f4-117">See also</span></span>

- [<span data-ttu-id="781f4-118">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="781f4-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
