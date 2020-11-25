---
title: CorPropertyAttr 列挙型
ms.date: 03/30/2017
api_name:
- CorPropertyAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPropertyAttr
helpviewer_keywords:
- CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type:
- apiref
ms.openlocfilehash: d76de80f87a8e5a63eac9f6a413f2efb0e394b0a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706126"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="f13a3-102">CorPropertyAttr 列挙型</span><span class="sxs-lookup"><span data-stu-id="f13a3-102">CorPropertyAttr Enumeration</span></span>

<span data-ttu-id="f13a3-103">プロパティのメタデータを記述する値が格納されます。</span><span class="sxs-lookup"><span data-stu-id="f13a3-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f13a3-104">構文</span><span class="sxs-lookup"><span data-stu-id="f13a3-104">Syntax</span></span>  
  
```cpp  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="f13a3-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="f13a3-105">Members</span></span>  
  
|<span data-ttu-id="f13a3-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="f13a3-106">Member</span></span>|<span data-ttu-id="f13a3-107">説明</span><span class="sxs-lookup"><span data-stu-id="f13a3-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="f13a3-108">プロパティが特別であり、その名前がどのように説明するかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f13a3-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="f13a3-109">共通言語ランタイムによる内部使用のために予約されています。</span><span class="sxs-lookup"><span data-stu-id="f13a3-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="f13a3-110">共通言語ランタイムメタデータの内部 Api がプロパティ名のエンコーディングを確認する必要があることを指定します。</span><span class="sxs-lookup"><span data-stu-id="f13a3-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="f13a3-111">プロパティが既定値を持つことを指定します。</span><span class="sxs-lookup"><span data-stu-id="f13a3-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="f13a3-112">未使用。</span><span class="sxs-lookup"><span data-stu-id="f13a3-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f13a3-113">要件</span><span class="sxs-lookup"><span data-stu-id="f13a3-113">Requirements</span></span>  

 <span data-ttu-id="f13a3-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f13a3-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f13a3-115">**ヘッダー:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="f13a3-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="f13a3-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f13a3-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f13a3-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="f13a3-117">See also</span></span>

- [<span data-ttu-id="f13a3-118">メタデータ列挙体</span><span class="sxs-lookup"><span data-stu-id="f13a3-118">Metadata Enumerations</span></span>](metadata-enumerations.md)
