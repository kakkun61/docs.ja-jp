---
title: INotifySink2::OnSyncCallReturn メソッド
ms.date: 03/30/2017
api_name:
- INotifySink2.OnSyncCallReturn
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- INotifySink2::OnSyncCallReturn
helpviewer_keywords:
- OnSyncCallReturn method [.NET Framework debugging]
- INotifySink2::OnSyncCallReturn method [.NET Framework debugging]
ms.assetid: c1bda761-6292-4750-a14b-7d5db8f33456
topic_type:
- apiref
ms.openlocfilehash: fe2db3df688f91ec6e1aadd8cc3bb43726e5c30f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719958"
---
# <a name="inotifysink2onsynccallreturn-method"></a><span data-ttu-id="52266-102">INotifySink2::OnSyncCallReturn メソッド</span><span class="sxs-lookup"><span data-stu-id="52266-102">INotifySink2::OnSyncCallReturn Method</span></span>

<span data-ttu-id="52266-103">呼び出しから制御が戻ったときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="52266-103">Gets invoked when a call returns.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52266-104">構文</span><span class="sxs-lookup"><span data-stu-id="52266-104">Syntax</span></span>  
  
```cpp  
HRESULT OnSyncCallReturn  
(  
    [in]  CALL_ID   in_CallID,  
    [in, size_is(in_BufferSize)] BYTE*  in_pBuffer,  
    [in]  DWORD     in_BufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52266-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="52266-105">Parameters</span></span>  

 `in_CallID`  
 <span data-ttu-id="52266-106">からから返される呼び出しの ID。</span><span class="sxs-lookup"><span data-stu-id="52266-106">[in] ID of the call being returned from.</span></span> <span data-ttu-id="52266-107">「 [CALL_ID 構造](call-id-structure.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="52266-107">See [CALL_ID Structure](call-id-structure.md).</span></span>  
  
 `in_pBuffer`  
 <span data-ttu-id="52266-108">から呼び出しバッファー。</span><span class="sxs-lookup"><span data-stu-id="52266-108">[in] Call buffer.</span></span>  
  
 `in_BufferSize`  
 <span data-ttu-id="52266-109">から呼び出しバッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="52266-109">[in] Size of the call buffer, in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52266-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="52266-110">Return Value</span></span>  

 <span data-ttu-id="52266-111">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="52266-111">S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52266-112">要件</span><span class="sxs-lookup"><span data-stu-id="52266-112">Requirements</span></span>  

 <span data-ttu-id="52266-113">**ヘッダー:** ProtocolNotify2</span><span class="sxs-lookup"><span data-stu-id="52266-113">**Header:** ProtocolNotify2.idl</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52266-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="52266-114">See also</span></span>

- [<span data-ttu-id="52266-115">INotifySink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52266-115">INotifySink2 Interface</span></span>](inotifysink2-interface.md)
- [<span data-ttu-id="52266-116">INotifySource2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52266-116">INotifySource2 Interface</span></span>](inotifysource2-interface.md)
- [<span data-ttu-id="52266-117">INotifyConnection2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="52266-117">INotifyConnection2 Interface</span></span>](inotifyconnection2-interface.md)
