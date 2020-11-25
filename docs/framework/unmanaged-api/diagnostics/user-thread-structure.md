---
title: USER_THREAD 構造体
ms.date: 03/30/2017
api_name:
- USER_THREAD
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- USER_THREAD
helpviewer_keywords:
- USER_THREAD structure [.NET Framework debugging]
ms.assetid: a57c7d71-c4b0-41f9-a964-0c5ee84a3124
topic_type:
- apiref
ms.openlocfilehash: 409651aa69e957418ad46f61e1bd57add0eb10a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722896"
---
# <a name="user_thread-structure"></a><span data-ttu-id="b0b7b-102">USER_THREAD 構造体</span><span class="sxs-lookup"><span data-stu-id="b0b7b-102">USER_THREAD Structure</span></span>

<span data-ttu-id="b0b7b-103">スレッドに関する情報をデバッガーに提供します。</span><span class="sxs-lookup"><span data-stu-id="b0b7b-103">Provides information to a debugger about a thread.</span></span> <span data-ttu-id="b0b7b-104">詳細については、 [INotifySource2:: SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) メソッドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b0b7b-104">For more information, see the [INotifySource2::SetNotifyFilter](inotifysource2-setnotifyfilter-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0b7b-105">構文</span><span class="sxs-lookup"><span data-stu-id="b0b7b-105">Syntax</span></span>  
  
```cpp  
typedef struct tagUSER_THREAD  
{  
    BYTE    *pSidBuffer;  
    DWORD   dwSidLen;  
    DWORD   dwTid;  
} USER_THREAD;  
```  
  
## <a name="members"></a><span data-ttu-id="b0b7b-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="b0b7b-106">Members</span></span>  
  
|<span data-ttu-id="b0b7b-107">メンバー</span><span class="sxs-lookup"><span data-stu-id="b0b7b-107">Member</span></span>|<span data-ttu-id="b0b7b-108">説明</span><span class="sxs-lookup"><span data-stu-id="b0b7b-108">Description</span></span>|  
|------------|-----------------|  
|`pSidBuffer`|<span data-ttu-id="b0b7b-109">スレッドバッファーのアドレス。</span><span class="sxs-lookup"><span data-stu-id="b0b7b-109">Address of thread buffer.</span></span>|  
|`dwSidLen`|<span data-ttu-id="b0b7b-110">スレッドバッファーの長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="b0b7b-110">Length of thread buffer, in bytes.</span></span>|  
|`dwTid`|<span data-ttu-id="b0b7b-111">スレッド ID。</span><span class="sxs-lookup"><span data-stu-id="b0b7b-111">Thread ID.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b0b7b-112">要件</span><span class="sxs-lookup"><span data-stu-id="b0b7b-112">Requirements</span></span>  

 <span data-ttu-id="b0b7b-113">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="b0b7b-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0b7b-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="b0b7b-114">See also</span></span>

- [<span data-ttu-id="b0b7b-115">SetNotifyFilter メソッド</span><span class="sxs-lookup"><span data-stu-id="b0b7b-115">SetNotifyFilter Method</span></span>](inotifysource2-setnotifyfilter-method.md)
- [<span data-ttu-id="b0b7b-116">シンボル ストア診断構造体</span><span class="sxs-lookup"><span data-stu-id="b0b7b-116">Diagnostics Symbol Store Structures</span></span>](diagnostics-symbol-store-structures.md)
