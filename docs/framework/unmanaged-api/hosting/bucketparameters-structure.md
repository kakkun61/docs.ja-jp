---
title: BucketParameters 構造体
ms.date: 03/30/2017
api_name:
- BucketParameters
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- BucketParameters
helpviewer_keywords:
- BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type:
- apiref
ms.openlocfilehash: 8b54cb30ec96ad0fb7851af6f2d465fe771886ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677857"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="55652-102">BucketParameters 構造体</span><span class="sxs-lookup"><span data-stu-id="55652-102">BucketParameters Structure</span></span>

<span data-ttu-id="55652-103">イベントの型名と、イベントに関連付けられている現在の例外のパラメーターを格納します。</span><span class="sxs-lookup"><span data-stu-id="55652-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55652-104">構文</span><span class="sxs-lookup"><span data-stu-id="55652-104">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;
    WCHAR pszEventTypeName[255];
    WCHAR pszParams[10][255];
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="55652-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="55652-105">Members</span></span>  
  
|<span data-ttu-id="55652-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="55652-106">Member</span></span>|<span data-ttu-id="55652-107">説明</span><span class="sxs-lookup"><span data-stu-id="55652-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="55652-108">`true`この構造体の残りの部分が有効な場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="55652-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="55652-109">イベントの種類の名前。</span><span class="sxs-lookup"><span data-stu-id="55652-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="55652-110">文字列の配列。各文字列は、イベントに関連付けられている現在の例外のパラメーターを指定します。</span><span class="sxs-lookup"><span data-stu-id="55652-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="55652-111">要件</span><span class="sxs-lookup"><span data-stu-id="55652-111">Requirements</span></span>  

 <span data-ttu-id="55652-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="55652-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55652-113">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="55652-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="55652-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55652-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55652-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="55652-115">See also</span></span>

- [<span data-ttu-id="55652-116">ホスト構造体</span><span class="sxs-lookup"><span data-stu-id="55652-116">Hosting Structures</span></span>](hosting-structures.md)
