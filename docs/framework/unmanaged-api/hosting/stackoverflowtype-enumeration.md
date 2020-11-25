---
title: StackOverflowType 列挙型
ms.date: 03/30/2017
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
ms.openlocfilehash: bbdc68721378e6bbb09f5e4eade08e2e6e03b097
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729914"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="27dba-102">StackOverflowType 列挙型</span><span class="sxs-lookup"><span data-stu-id="27dba-102">StackOverflowType Enumeration</span></span>

<span data-ttu-id="27dba-103">スタックオーバーフローイベントの根底にある原因を示す値を格納します。</span><span class="sxs-lookup"><span data-stu-id="27dba-103">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27dba-104">構文</span><span class="sxs-lookup"><span data-stu-id="27dba-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="27dba-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="27dba-105">Members</span></span>  
  
|<span data-ttu-id="27dba-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="27dba-106">Member</span></span>|<span data-ttu-id="27dba-107">説明</span><span class="sxs-lookup"><span data-stu-id="27dba-107">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="27dba-108">スタックオーバーフローは、実行エンジンによって発生しました。</span><span class="sxs-lookup"><span data-stu-id="27dba-108">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="27dba-109">スタックオーバーフローは、マネージコードによって発生しました。</span><span class="sxs-lookup"><span data-stu-id="27dba-109">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="27dba-110">スタックオーバーフローは、アンマネージコードによって発生しました。</span><span class="sxs-lookup"><span data-stu-id="27dba-110">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27dba-111">注釈</span><span class="sxs-lookup"><span data-stu-id="27dba-111">Remarks</span></span>  

 <span data-ttu-id="27dba-112">この情報は、 [Iactiononclrevent:: OnEvent](iactiononclrevent-onevent-method.md) メソッドの呼び出しによってホストに渡されます。</span><span class="sxs-lookup"><span data-stu-id="27dba-112">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27dba-113">要件</span><span class="sxs-lookup"><span data-stu-id="27dba-113">Requirements</span></span>  

 <span data-ttu-id="27dba-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27dba-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27dba-115">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="27dba-115">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="27dba-116">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="27dba-116">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27dba-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27dba-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27dba-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="27dba-118">See also</span></span>

- [<span data-ttu-id="27dba-119">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="27dba-119">Hosting Enumerations</span></span>](hosting-enumerations.md)
