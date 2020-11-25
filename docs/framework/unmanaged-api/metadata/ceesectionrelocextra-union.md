---
title: CeeSectionRelocExtra 共用体
ms.date: 03/30/2017
api_name:
- CeeSectionRelocExtra Union
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocExtra
helpviewer_keywords:
- CeeSectionRelocExtra union [.NET Framework metadata]
ms.assetid: d9568cf6-7f98-4cd6-ab36-0a2bd509afcc
topic_type:
- apiref
ms.openlocfilehash: d5f61aa9b4a65a5f33e64aa4441370c3f7ca5b03
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732724"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="4fbf9-102">CeeSectionRelocExtra 共用体</span><span class="sxs-lookup"><span data-stu-id="4fbf9-102">CeeSectionRelocExtra Union</span></span>

<span data-ttu-id="4fbf9-103">セクションを再配置するために [ICeeGen](iceegen-interface.md) インターフェイスによって使用されるアドレスオフセットを表します。</span><span class="sxs-lookup"><span data-stu-id="4fbf9-103">Represents an address offset that is used by the [ICeeGen](iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fbf9-104">構文</span><span class="sxs-lookup"><span data-stu-id="4fbf9-104">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="4fbf9-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="4fbf9-105">Members</span></span>  
  
|<span data-ttu-id="4fbf9-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="4fbf9-106">Member</span></span>|<span data-ttu-id="4fbf9-107">説明</span><span class="sxs-lookup"><span data-stu-id="4fbf9-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="4fbf9-108">セクションの上限アドレスの調整。</span><span class="sxs-lookup"><span data-stu-id="4fbf9-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4fbf9-109">要件</span><span class="sxs-lookup"><span data-stu-id="4fbf9-109">Requirements</span></span>  

 <span data-ttu-id="4fbf9-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4fbf9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4fbf9-111">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="4fbf9-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="4fbf9-112">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4fbf9-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="4fbf9-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4fbf9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fbf9-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="4fbf9-114">See also</span></span>

- [<span data-ttu-id="4fbf9-115">メタデータ共用体</span><span class="sxs-lookup"><span data-stu-id="4fbf9-115">Metadata Unions</span></span>](metadata-unions.md)
