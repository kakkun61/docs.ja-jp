---
title: CLR_DEBUGGING_VERSION 構造体
ms.date: 03/30/2017
api_name:
- CLR_DEBUGGING_VERSION
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CLR_DEBUGGING_VERSION
helpviewer_keywords:
- CLR_DEBUGGING_VERSION structure [.NET Framework debugging]
ms.assetid: 4d821186-3ddf-405a-ac44-d79438a9f7f3
topic_type:
- apiref
ms.openlocfilehash: 8a2abe847728a2bb1f1345ef73e55b58e4704001
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729812"
---
# <a name="clr_debugging_version-structure"></a><span data-ttu-id="e4e4d-102">CLR_DEBUGGING_VERSION 構造体</span><span class="sxs-lookup"><span data-stu-id="e4e4d-102">CLR_DEBUGGING_VERSION Structure</span></span>

<span data-ttu-id="e4e4d-103">デバッグのために共通言語ランタイム (CLR) の製品バージョンを定義します。</span><span class="sxs-lookup"><span data-stu-id="e4e4d-103">Defines the product version of the common language runtime (CLR) for debugging purposes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4e4d-104">構文</span><span class="sxs-lookup"><span data-stu-id="e4e4d-104">Syntax</span></span>  
  
```cpp  
typedef struct _CLR_DEBUGGING_VERSION  
{  
    WORD wStructVersion;
    WORD wMajor;
    WORD wMinor;
    WORD wBuild;
    WORD wRevision;
} CLR_DEBUGGING_VERSION;
```  
  
## <a name="members"></a><span data-ttu-id="e4e4d-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="e4e4d-105">Members</span></span>  
  
|<span data-ttu-id="e4e4d-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="e4e4d-106">Member</span></span>|<span data-ttu-id="e4e4d-107">説明</span><span class="sxs-lookup"><span data-stu-id="e4e4d-107">Description</span></span>|  
|------------|-----------------|  
|`wStructVersion`|<span data-ttu-id="e4e4d-108">構造体のバージョン番号</span><span class="sxs-lookup"><span data-stu-id="e4e4d-108">The structure version number</span></span>|  
|`wMajor`|<span data-ttu-id="e4e4d-109">メジャー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="e4e4d-109">The major version number.</span></span>|  
|`wMinor`|<span data-ttu-id="e4e4d-110">マイナー バージョン番号。</span><span class="sxs-lookup"><span data-stu-id="e4e4d-110">The minor version number.</span></span>|  
|`wBuild`|<span data-ttu-id="e4e4d-111">ビルド番号。</span><span class="sxs-lookup"><span data-stu-id="e4e4d-111">The build number.</span></span>|  
|`wRevision`|<span data-ttu-id="e4e4d-112">リビジョン番号。</span><span class="sxs-lookup"><span data-stu-id="e4e4d-112">The revision number.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4e4d-113">注釈</span><span class="sxs-lookup"><span data-stu-id="e4e4d-113">Remarks</span></span>  

 <span data-ttu-id="e4e4d-114">構造体 `CLR_DEBUGGING_VERSION` は COR_VERSION 構造体と同じですが、構造体には `CLR_DEBUGGING_VERSION` 追加の構造体のバージョンフィールド () が用意されて `wStructVersion` います。</span><span class="sxs-lookup"><span data-stu-id="e4e4d-114">The `CLR_DEBUGGING_VERSION` structure is the same as the COR_VERSION structure, however, the `CLR_DEBUGGING_VERSION` structure provides an additional structure version field (`wStructVersion`).</span></span> <span data-ttu-id="e4e4d-115">現在、このフィールドは0に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e4e4d-115">Currently, this field must be set to zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4e4d-116">要件</span><span class="sxs-lookup"><span data-stu-id="e4e4d-116">Requirements</span></span>  

 <span data-ttu-id="e4e4d-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e4e4d-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4e4d-118">**ヘッダー:** CorDebug .idl</span><span class="sxs-lookup"><span data-stu-id="e4e4d-118">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="e4e4d-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e4e4d-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4e4d-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4e4d-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4e4d-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="e4e4d-121">See also</span></span>

- [<span data-ttu-id="e4e4d-122">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="e4e4d-122">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="e4e4d-123">デバッグ</span><span class="sxs-lookup"><span data-stu-id="e4e4d-123">Debugging</span></span>](index.md)
