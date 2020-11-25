---
title: CorDebugGuidToTypeMapping 構造体
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- CorDebugGuidToTypeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGuidToTypeMapping
helpviewer_keywords:
- CorDebugGuidToTypeMapping structure [.NET Framework debugging]
ms.assetid: 57dbccd9-b16d-4da3-ae25-7a2cf9adf679
topic_type:
- apiref
ms.openlocfilehash: 859853521b741f42f1de7921de813941d2501173
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729097"
---
# <a name="cordebugguidtotypemapping-structure"></a><span data-ttu-id="dd605-102">CorDebugGuidToTypeMapping 構造体</span><span class="sxs-lookup"><span data-stu-id="dd605-102">CorDebugGuidToTypeMapping Structure</span></span>

<span data-ttu-id="dd605-103">Windows ランタイム GUID を対応するテキストオブジェクトにマップします。</span><span class="sxs-lookup"><span data-stu-id="dd605-103">Maps a Windows Runtime GUID to its corresponding ICorDebugType object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd605-104">構文</span><span class="sxs-lookup"><span data-stu-id="dd605-104">Syntax</span></span>  
  
```cpp
typedef struct CorDebugGuidToTypeMapping {  
    GUID iid;  
    ICorDebugType *pType;  
} CorDebugGuidToTypeMapping;  
```  
  
## <a name="members"></a><span data-ttu-id="dd605-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="dd605-105">Members</span></span>  
  
|<span data-ttu-id="dd605-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="dd605-106">Member</span></span>|<span data-ttu-id="dd605-107">説明</span><span class="sxs-lookup"><span data-stu-id="dd605-107">Description</span></span>|  
|------------|-----------------|  
|`iid`|<span data-ttu-id="dd605-108">キャッシュされた Windows ランタイムの種類の GUID。</span><span class="sxs-lookup"><span data-stu-id="dd605-108">The GUID of the cached Windows Runtime type.</span></span>|  
|`pType`|<span data-ttu-id="dd605-109">キャッシュされた型に関する情報を提供する、テキストオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="dd605-109">A pointer to an ICorDebugType object that provides information about the cached type.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd605-110">要件</span><span class="sxs-lookup"><span data-stu-id="dd605-110">Requirements</span></span>  

 <span data-ttu-id="dd605-111">**プラットフォーム:** Windows ランタイム。</span><span class="sxs-lookup"><span data-stu-id="dd605-111">**Platforms:** Windows Runtime.</span></span>  
  
 <span data-ttu-id="dd605-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd605-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd605-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd605-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd605-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd605-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd605-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="dd605-115">See also</span></span>

- [<span data-ttu-id="dd605-116">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="dd605-116">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="dd605-117">デバッグ</span><span class="sxs-lookup"><span data-stu-id="dd605-117">Debugging</span></span>](index.md)
