---
title: ICLROnEventManager::RegisterActionOnEvent メソッド
ms.date: 03/30/2017
api_name:
- ICLROnEventManager.RegisterActionOnEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLROnEventManager::RegisterActionOnEvent
helpviewer_keywords:
- ICLROnEventManager::RegisterActionOnEvent method [.NET Framework hosting]
- RegisterActionOnEvent method [.NET Framework hosting]
ms.assetid: b944cf49-918d-4c4e-993b-77d097a52550
topic_type:
- apiref
ms.openlocfilehash: 7f0770585e977f5299a40517c28dfb776b2ab898
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725613"
---
# <a name="iclroneventmanagerregisteractiononevent-method"></a><span data-ttu-id="24847-102">ICLROnEventManager::RegisterActionOnEvent メソッド</span><span class="sxs-lookup"><span data-stu-id="24847-102">ICLROnEventManager::RegisterActionOnEvent Method</span></span>

<span data-ttu-id="24847-103">指定されたイベントのコールバックポインターを登録します。</span><span class="sxs-lookup"><span data-stu-id="24847-103">Registers a callback pointer for the specified event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24847-104">構文</span><span class="sxs-lookup"><span data-stu-id="24847-104">Syntax</span></span>  
  
```cpp  
HRESULT RegisterActionOnEvent (  
    [in] EClrEvent event,  
    [in] IActionOnCLREvent *pAction  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24847-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="24847-105">Parameters</span></span>  

 `event`  
 <span data-ttu-id="24847-106">から [Eclrevent](eclrevent-enumeration.md) 値の1つ。によって記述されるコールバックポインターを登録するイベントを示し `pAction` ます。</span><span class="sxs-lookup"><span data-stu-id="24847-106">[in] One of the [EClrEvent](eclrevent-enumeration.md) values, indicating the event for which to register the callback pointer described by `pAction`.</span></span>  
  
 `pAction`  
 <span data-ttu-id="24847-107">から登録されたイベントが発生したときに呼び出される [Iactiononclrevent](iactiononclrevent-interface.md) オブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="24847-107">[in] A pointer to an [IActionOnCLREvent](iactiononclrevent-interface.md) object that is called when the registered event fires.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="24847-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="24847-108">Return Value</span></span>  
  
|<span data-ttu-id="24847-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="24847-109">HRESULT</span></span>|<span data-ttu-id="24847-110">説明</span><span class="sxs-lookup"><span data-stu-id="24847-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="24847-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="24847-111">S_OK</span></span>|<span data-ttu-id="24847-112">`RegisterActionOnEvent` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="24847-112">`RegisterActionOnEvent` returned successfully.</span></span>|  
|<span data-ttu-id="24847-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="24847-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="24847-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="24847-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="24847-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="24847-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="24847-116">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="24847-116">The call timed out.</span></span>|  
|<span data-ttu-id="24847-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="24847-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="24847-118">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="24847-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="24847-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="24847-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="24847-120">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="24847-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="24847-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="24847-121">E_FAIL</span></span>|<span data-ttu-id="24847-122">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="24847-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="24847-123">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="24847-123">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="24847-124">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="24847-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="24847-125">注釈</span><span class="sxs-lookup"><span data-stu-id="24847-125">Remarks</span></span>  

 <span data-ttu-id="24847-126">ホストは、で説明されている2つのイベントの種類のいずれかまたは両方のコールバックを登録でき `EClrEvent` ます。</span><span class="sxs-lookup"><span data-stu-id="24847-126">The host can register callbacks for either or both of the two event types described by `EClrEvent`.</span></span> <span data-ttu-id="24847-127">ホストは、 `ICLROnEventManager` [ICLRControl:: GetCLRManager](iclrcontrol-getclrmanager-method.md) メソッドを呼び出すことによって、インターフェイスを取得します。</span><span class="sxs-lookup"><span data-stu-id="24847-127">The host gets the `ICLROnEventManager` interface by calling the [ICLRControl::GetCLRManager](iclrcontrol-getclrmanager-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="24847-128">登録するイベントは、 `RegisterActionOnEvent` 複数の異なるスレッドから起動して、CLR のアンロードまたは無効化を通知することができます。</span><span class="sxs-lookup"><span data-stu-id="24847-128">The events that `RegisterActionOnEvent` registers can be fired more than once and from different threads to signal an unload or the disabling of the CLR.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24847-129">要件</span><span class="sxs-lookup"><span data-stu-id="24847-129">Requirements</span></span>  

 <span data-ttu-id="24847-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="24847-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24847-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="24847-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="24847-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="24847-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="24847-133">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24847-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24847-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="24847-134">See also</span></span>

- [<span data-ttu-id="24847-135">EClrEvent 列挙型</span><span class="sxs-lookup"><span data-stu-id="24847-135">EClrEvent Enumeration</span></span>](eclrevent-enumeration.md)
- [<span data-ttu-id="24847-136">IActionOnCLREvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="24847-136">IActionOnCLREvent Interface</span></span>](iactiononclrevent-interface.md)
- [<span data-ttu-id="24847-137">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="24847-137">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="24847-138">ICLROnEventManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="24847-138">ICLROnEventManager Interface</span></span>](iclroneventmanager-interface.md)
