---
title: INotifyConnection2::UnregisterNotifySource メソッド
ms.date: 03/30/2017
api_name:
- INotifyConnection2.UnregisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::UnregisterNotifySource
helpviewer_keywords:
- INotifyConnection2::UnregisterNotifySource method [.NET Framework debugging]
- UnregisterNotifySource method [.NET Framework debugging]
ms.assetid: 2fc6c715-646f-41fd-9c12-c59b40575269
topic_type:
- apiref
ms.openlocfilehash: 90220c2bfea683ff0472473e180c9e11ea568672
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720036"
---
# <a name="inotifyconnection2unregisternotifysource-method"></a><span data-ttu-id="82e70-102">INotifyConnection2::UnregisterNotifySource メソッド</span><span class="sxs-lookup"><span data-stu-id="82e70-102">INotifyConnection2::UnregisterNotifySource Method</span></span>

<span data-ttu-id="82e70-103">指定された通知ソースオブジェクトを接続から削除します。</span><span class="sxs-lookup"><span data-stu-id="82e70-103">Removes a specified notification source object from the connection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82e70-104">構文</span><span class="sxs-lookup"><span data-stu-id="82e70-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82e70-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="82e70-105">Parameters</span></span>  

 `in_pNotifySource`  
 <span data-ttu-id="82e70-106">から登録を解除する通知オブジェクト。</span><span class="sxs-lookup"><span data-stu-id="82e70-106">[in] Notification object to be unregistered.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="82e70-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="82e70-107">Return Value</span></span>  

 <span data-ttu-id="82e70-108">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="82e70-108">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82e70-109">要件</span><span class="sxs-lookup"><span data-stu-id="82e70-109">Requirements</span></span>  

 <span data-ttu-id="82e70-110">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="82e70-110">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82e70-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="82e70-111">See also</span></span>

- [<span data-ttu-id="82e70-112">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82e70-112">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="82e70-113">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82e70-113">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="82e70-114">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="82e70-114">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="82e70-115">RegisterNotifySource メソッド</span><span class="sxs-lookup"><span data-stu-id="82e70-115">RegisterNotifySource Method</span></span>](inotifyconnection2-registernotifysource-method.md)
