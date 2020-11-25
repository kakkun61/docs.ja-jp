---
title: ICLROnEventManager::UnregisterActionOnEvent メソッド
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.UnregisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::UnregisterActionOnEvent
helpviewer_keywords:
- UnRegisterActionOnEvent method [.NET Framework hosting]
- ICLROnEventManager::UnRegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: 4c02ec37-cdf0-46b2-890e-235092741236
topic_type:
- apiref
ms.openlocfilehash: ca3c7fe813f22d3beab3087414100b3d8e5814ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725600"
---
# <a name="iclroneventmanagerunregisteractiononevent-method"></a><span data-ttu-id="995b2-102">ICLROnEventManager::UnregisterActionOnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="995b2-102">ICLROnEventManager::UnregisterActionOnEvent Method</span></span>

<span data-ttu-id="995b2-103">指定されたイベントに対して、以前に登録されたコールバックポインターの登録を解除します。</span><span class="sxs-lookup"><span data-stu-id="995b2-103">Unregisters a previously registered callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="995b2-104">構文</span><span class="sxs-lookup"><span data-stu-id="995b2-104">Syntax</span></span>  
  
```cpp  
HRESULT UnregisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="995b2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="995b2-105">Parameters</span></span>  

 `event`  
 <span data-ttu-id="995b2-106">から [Eclrevent](eclrevent-enumeration.md) 値の1つ。によって記述されたコールバックポインターの登録を解除する対象のイベントを示し `pAction` ます。</span><span class="sxs-lookup"><span data-stu-id="995b2-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to unregister the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="995b2-107">から[Registeractiononevent](iclroneventmanager-registeractiononevent-method.md)メソッドにパラメーターとして渡された[Iactiononclrevent](iactiononclrevent-interface.md)オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="995b2-107">[in] A pointer to an [IActionOnCLREvent](iactiononclrevent-interface.md) object that was passed as a parameter to the [RegisterActionOnEvent](iclroneventmanager-registeractiononevent-method.md) method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="995b2-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="995b2-108">Return Value</span></span>  
  
|<span data-ttu-id="995b2-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="995b2-109">HRESULT</span></span>|<span data-ttu-id="995b2-110">説明</span><span class="sxs-lookup"><span data-stu-id="995b2-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="995b2-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="995b2-111">S_OK</span></span>|<span data-ttu-id="995b2-112">`UnregisterActionOnEvent` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="995b2-112">`UnregisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="995b2-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="995b2-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="995b2-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="995b2-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="995b2-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="995b2-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="995b2-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="995b2-116">The call timed out.</span></span>|  
|<span data-ttu-id="995b2-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="995b2-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="995b2-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="995b2-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="995b2-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="995b2-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="995b2-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="995b2-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="995b2-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="995b2-121">E_FAIL</span></span>|<span data-ttu-id="995b2-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="995b2-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="995b2-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="995b2-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="995b2-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="995b2-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="995b2-125">要件</span><span class="sxs-lookup"><span data-stu-id="995b2-125">Requirements</span></span>  

 <span data-ttu-id="995b2-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="995b2-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="995b2-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="995b2-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="995b2-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="995b2-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="995b2-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="995b2-129">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="995b2-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="995b2-130">See also</span></span>

- [<span data-ttu-id="995b2-131">EClrEvent 列挙型</span><span class="sxs-lookup"><span data-stu-id="995b2-131">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="995b2-132">IActionOnCLREvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="995b2-132">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="995b2-133">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="995b2-133">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="995b2-134">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="995b2-134">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
