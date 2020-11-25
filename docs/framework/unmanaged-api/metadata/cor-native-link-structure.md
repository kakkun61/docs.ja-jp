---
title: COR_NATIVE_LINK 構造体
ms.date: 03/30/2017
api_name:
- COR_NATIVE_LINK
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COR_NATIVE_LINK
helpviewer_keywords:
- COR_NATIVE_LINK structure [.NET Framework metadata]
ms.assetid: 6ef78d3c-1c69-4141-b687-dcb065b7a74d
topic_type:
- apiref
ms.openlocfilehash: 15f573ebc07bcf08a1ab8f5a5bbb88e940c5c8dc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724170"
---
# <a name="cor_native_link-structure"></a><span data-ttu-id="82053-102">COR_NATIVE_LINK 構造体</span><span class="sxs-lookup"><span data-stu-id="82053-102">COR_NATIVE_LINK Structure</span></span>

<span data-ttu-id="82053-103">ネイティブ コードのリンクに使用される情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="82053-103">Contains information that is used to link native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82053-104">構文</span><span class="sxs-lookup"><span data-stu-id="82053-104">Syntax</span></span>  
  
```cpp  
typedef struct
{  
    BYTE        m_linkType;  
    BYTE        m_flags;  
    mdMemberRef m_entryPoint;  
} COR_NATIVE_LINK;  
```  
  
## <a name="members"></a><span data-ttu-id="82053-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="82053-105">Members</span></span>  
  
|<span data-ttu-id="82053-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="82053-106">Member</span></span>|<span data-ttu-id="82053-107">説明</span><span class="sxs-lookup"><span data-stu-id="82053-107">Description</span></span>|  
|------------|-----------------|  
|`m_linkType`|<span data-ttu-id="82053-108">ネイティブコードでリンクされる型。</span><span class="sxs-lookup"><span data-stu-id="82053-108">The type to be linked in native code.</span></span> <span data-ttu-id="82053-109">この値は、 [CorNativeLinkType](cornativelinktype-enumeration.md) 値の1つです。</span><span class="sxs-lookup"><span data-stu-id="82053-109">This value is one of the [CorNativeLinkType](cornativelinktype-enumeration.md) values.</span></span>|  
|`m_flags`|<span data-ttu-id="82053-110">ネイティブコードをリンクするときにリンカーによって使用されるフラグ。</span><span class="sxs-lookup"><span data-stu-id="82053-110">Flags used by the linker when linking native code.</span></span> <span data-ttu-id="82053-111">この値は、 [CorNativeLinkFlags](cornativelinkflags-enumeration.md) 値の1つです。</span><span class="sxs-lookup"><span data-stu-id="82053-111">This value is one of the [CorNativeLinkFlags](cornativelinkflags-enumeration.md) values.</span></span>|  
|`m_entryPoint`|<span data-ttu-id="82053-112">エントリポイントを表す MemberRef メタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="82053-112">The MemberRef metadata token that represents the entry point.</span></span> <span data-ttu-id="82053-113">形式は `lib:entrypoint` です。</span><span class="sxs-lookup"><span data-stu-id="82053-113">The format is `lib:entrypoint`.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="82053-114">要件</span><span class="sxs-lookup"><span data-stu-id="82053-114">Requirements</span></span>  

 <span data-ttu-id="82053-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="82053-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82053-116">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="82053-116">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="82053-117">**ライブラリ:** MsCorEE.dll のリソースとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="82053-117">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="82053-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82053-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82053-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="82053-119">See also</span></span>

- [<span data-ttu-id="82053-120">メタデータ構造体</span><span class="sxs-lookup"><span data-stu-id="82053-120">Metadata Structures</span></span>](metadata-structures.md)
- [<span data-ttu-id="82053-121">CorNativeLinkType 列挙型</span><span class="sxs-lookup"><span data-stu-id="82053-121">CorNativeLinkType Enumeration</span></span>](cornativelinktype-enumeration.md)
- [<span data-ttu-id="82053-122">CorNativeLinkFlags 列挙型</span><span class="sxs-lookup"><span data-stu-id="82053-122">CorNativeLinkFlags Enumeration</span></span>](cornativelinkflags-enumeration.md)
