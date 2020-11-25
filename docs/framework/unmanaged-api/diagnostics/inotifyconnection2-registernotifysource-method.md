---
title: INotifyConnection2::RegisterNotifySource メソッド
ms.date: 03/30/2017
api_name:
- INotifyConnection2.RegisterNotifySource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifyConnection2::RegisterNotifySource
helpviewer_keywords:
- INotifyConnection2::RegisterNotifySource method [.NET Framework debugging]
- RegisterNotifySource method [.NET Framework debugging]
ms.assetid: 2632da80-6e4b-4429-8dee-b382745a5f81
topic_type:
- apiref
ms.openlocfilehash: 1286dd970e437af0a8b607ed050ab4838f73a41f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720049"
---
# <a name="inotifyconnection2registernotifysource-method"></a><span data-ttu-id="0ef79-102">INotifyConnection2::RegisterNotifySource メソッド</span><span class="sxs-lookup"><span data-stu-id="0ef79-102">INotifyConnection2::RegisterNotifySource Method</span></span>

<span data-ttu-id="0ef79-103">指定された通知ソースをインストールします。</span><span class="sxs-lookup"><span data-stu-id="0ef79-103">Installs a specified notification source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ef79-104">構文</span><span class="sxs-lookup"><span data-stu-id="0ef79-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterNotifySource  
(  
    [in]  INotifySource2*  in_pNotifySource,  
    [out] INotifySink2**   out_ppNotifySink  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ef79-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0ef79-105">Parameters</span></span>  

 `in_pNotifySource`  
 <span data-ttu-id="0ef79-106">から通知ソースとして使用するオブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="0ef79-106">[in] Specifies the object to be used as the notification source.</span></span>  
  
 `out_ppNotifySink`  
 <span data-ttu-id="0ef79-107">入出力通知シンクとして使用されるオブジェクトを受け取ります。</span><span class="sxs-lookup"><span data-stu-id="0ef79-107">[out] Receives the object to be used as the notification sink.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0ef79-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="0ef79-108">Return Value</span></span>  

 <span data-ttu-id="0ef79-109">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="0ef79-109">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ef79-110">要件</span><span class="sxs-lookup"><span data-stu-id="0ef79-110">Requirements</span></span>  

 <span data-ttu-id="0ef79-111">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="0ef79-111">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ef79-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ef79-112">See also</span></span>

- [<span data-ttu-id="0ef79-113">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0ef79-113">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
- [<span data-ttu-id="0ef79-114">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0ef79-114">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="0ef79-115">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0ef79-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="0ef79-116">UnregisterNotifySource メソッド</span><span class="sxs-lookup"><span data-stu-id="0ef79-116">UnregisterNotifySource Method</span></span>](inotifyconnection2-unregisternotifysource-method.md)
