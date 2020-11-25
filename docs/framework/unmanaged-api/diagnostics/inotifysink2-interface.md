---
title: INotifySink2 インターフェイス
ms.date: 03/30/2017
api_name:
- INotifySink2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2
helpviewer_keywords:
- INotifySink2 interface [.NET Framework debugging]
ms.assetid: c1018789-4206-455d-aacc-2d876fc0d0bb
topic_type:
- apiref
ms.openlocfilehash: 255fe51f86157842a5807145bf7c58ae1ff5ba8a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720023"
---
# <a name="inotifysink2-interface"></a><span data-ttu-id="b7d01-102">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7d01-102">INotifySink2 Interface</span></span>

<span data-ttu-id="b7d01-103">シンク通知のメソッドを宣言します。</span><span class="sxs-lookup"><span data-stu-id="b7d01-103">Declares methods for sink notification.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b7d01-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="b7d01-104">Methods</span></span>  
  
|<span data-ttu-id="b7d01-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="b7d01-105">Method</span></span>|<span data-ttu-id="b7d01-106">説明</span><span class="sxs-lookup"><span data-stu-id="b7d01-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7d01-107">OnSyncCallEnter メソッド</span><span class="sxs-lookup"><span data-stu-id="b7d01-107">OnSyncCallEnter Method</span></span>](inotifysink2-onsynccallenter-method.md)|<span data-ttu-id="b7d01-108">呼び出しを入力したときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b7d01-108">Gets invoked when entering a call.</span></span>|  
|[<span data-ttu-id="b7d01-109">OnSyncCallExit メソッド</span><span class="sxs-lookup"><span data-stu-id="b7d01-109">OnSyncCallExit Method</span></span>](inotifysink2-onsynccallexit-method.md)|<span data-ttu-id="b7d01-110">呼び出しを終了したときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b7d01-110">Gets invoked when exiting a call.</span></span>|  
|[<span data-ttu-id="b7d01-111">OnSyncCallOut メソッド</span><span class="sxs-lookup"><span data-stu-id="b7d01-111">OnSyncCallOut Method</span></span>](inotifysink2-onsynccallout-method.md)|<span data-ttu-id="b7d01-112">呼び出しがタイムアウトしたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b7d01-112">Gets invoked when a call is out.</span></span>|  
|[<span data-ttu-id="b7d01-113">OnSyncCallReturn メソッド</span><span class="sxs-lookup"><span data-stu-id="b7d01-113">OnSyncCallReturn Method</span></span>](inotifysink2-onsynccallreturn-method.md)|<span data-ttu-id="b7d01-114">呼び出しから制御が戻ったときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b7d01-114">Gets invoked when a call returns.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b7d01-115">要件</span><span class="sxs-lookup"><span data-stu-id="b7d01-115">Requirements</span></span>  

 <span data-ttu-id="b7d01-116">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="b7d01-116">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7d01-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="b7d01-117">See also</span></span>

- [<span data-ttu-id="b7d01-118">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7d01-118">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="b7d01-119">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7d01-119">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="b7d01-120">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b7d01-120">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
