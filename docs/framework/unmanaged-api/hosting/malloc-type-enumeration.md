---
title: MALLOC_TYPE 列挙体
ms.date: 03/30/2017
api_name:
- MALLOC_TYPE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- MALLOC_TYPE
helpviewer_keywords:
- MALLOC_TYPE Enumeration
ms.assetid: c02476f9-23a2-4af7-9282-aa9c42c7429b
topic_type:
- apiref
ms.openlocfilehash: fe58a519d0feac0da49e7778247da1ef538f8b83
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730033"
---
# <a name="malloc_type-enumeration"></a><span data-ttu-id="63a19-102">MALLOC_TYPE 列挙体</span><span class="sxs-lookup"><span data-stu-id="63a19-102">MALLOC_TYPE Enumeration</span></span>

<span data-ttu-id="63a19-103">割り当てられているメモリの特性を指定する値を格納します。</span><span class="sxs-lookup"><span data-stu-id="63a19-103">Contains values that specify the characteristics of the memory that is being allocated.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63a19-104">構文</span><span class="sxs-lookup"><span data-stu-id="63a19-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    MALLOC_THREADSAFE = 0x1,  
    MALLOC_EXECUTABLE = 0x2,  
} MALLOC_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="63a19-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="63a19-105">Members</span></span>  
  
|<span data-ttu-id="63a19-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="63a19-106">Member</span></span>|<span data-ttu-id="63a19-107">説明</span><span class="sxs-lookup"><span data-stu-id="63a19-107">Description</span></span>|  
|------------|-----------------|  
|`MALLOC_EXECUTABLE`|<span data-ttu-id="63a19-108">割り当てられたメモリには、実行可能ファイルを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="63a19-108">The allocated memory can contain an executable file.</span></span>|  
|`MALLOC_THREADSAFE`|<span data-ttu-id="63a19-109">割り当てられたメモリはスレッドセーフです。</span><span class="sxs-lookup"><span data-stu-id="63a19-109">The allocated memory is thread-safe.</span></span> <span data-ttu-id="63a19-110">つまり、メモリには、同期を行わずに複数のスレッドからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="63a19-110">That is, the memory can be accessed by multiple threads without any synchronization.</span></span><br /><br /> <span data-ttu-id="63a19-111">このフラグが設定されていない場合は、オブジェクトに対する呼び出しをシリアル化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="63a19-111">If this flag is not set, calls on the object must be serialized.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="63a19-112">要件</span><span class="sxs-lookup"><span data-stu-id="63a19-112">Requirements</span></span>  

 <span data-ttu-id="63a19-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="63a19-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63a19-114">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="63a19-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63a19-115">**ライブラリ:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="63a19-115">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63a19-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63a19-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63a19-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="63a19-117">See also</span></span>

- [<span data-ttu-id="63a19-118">ホスティングの列挙型</span><span class="sxs-lookup"><span data-stu-id="63a19-118">Hosting Enumerations</span></span>](hosting-enumerations.md)
