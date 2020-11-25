---
title: ICLRControl::GetCLRManager メソッド
ms.date: 03/30/2017
api_name:
- ICLRControl.GetCLRManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRControl::GetCLRManager
helpviewer_keywords:
- GetCLRManager method [.NET Framework hosting]
- ICLRControl::GetCLRManager method [.NET Framework hosting]
ms.assetid: 8a11bfa4-cbb0-4082-82b5-f9fba66c93f5
topic_type:
- apiref
ms.openlocfilehash: d18b3a5c06ac0d3a86f7823f3b140c76c6c9a746
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728356"
---
# <a name="iclrcontrolgetclrmanager-method"></a><span data-ttu-id="8c838-102">ICLRControl::GetCLRManager メソッド</span><span class="sxs-lookup"><span data-stu-id="8c838-102">ICLRControl::GetCLRManager Method</span></span>

<span data-ttu-id="8c838-103">ホストが共通言語ランタイム (CLR) を構成するために使用できる任意のマネージャー型のインスタンスへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="8c838-103">Gets an interface pointer to an instance of any of the manager types the host can use to configure the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c838-104">構文</span><span class="sxs-lookup"><span data-stu-id="8c838-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRManager (  
    [in]  REFIID  riid,  
    [out] void  **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8c838-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8c838-105">Parameters</span></span>  

 `riid`  
 <span data-ttu-id="8c838-106">から `IID` 返されるマネージャーの型の。</span><span class="sxs-lookup"><span data-stu-id="8c838-106">[in] The `IID` of the manager type to return.</span></span> <span data-ttu-id="8c838-107">次の `IID` 値がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="8c838-107">The following `IID` values are supported.</span></span>  
  
- <span data-ttu-id="8c838-108">IID_ICLRDebugManager: が ICLRDebugManager 型であることを指定し `ppObject` ます。 [ICLRDebugManager](iclrdebugmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8c838-108">IID_ICLRDebugManager: Specifies that `ppObject` will be of type [ICLRDebugManager](iclrdebugmanager-interface.md).</span></span>  
  
- <span data-ttu-id="8c838-109">IID_ICLRErrorReportingManager: が ICLRErrorReportingManager 型であることを指定し `ppObject` ます。 [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8c838-109">IID_ICLRErrorReportingManager: Specifies that `ppObject` will be of type [ICLRErrorReportingManager](iclrerrorreportingmanager-interface.md).</span></span>  
  
- <span data-ttu-id="8c838-110">IID_ICLRGCManager: が ICLRGCManager 型であることを指定し `ppObject` ます。 [ICLRGCManager](iclrgcmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8c838-110">IID_ICLRGCManager: Specifies that `ppObject` will be of type [ICLRGCManager](iclrgcmanager-interface.md).</span></span>  
  
- <span data-ttu-id="8c838-111">IID_ICLRHostProtectionManager: が ICLRHostProtectionManager 型であることを指定し `ppObject` ます。 [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8c838-111">IID_ICLRHostProtectionManager: Specifies that `ppObject` will be of type [ICLRHostProtectionManager](iclrhostprotectionmanager-interface.md).</span></span>  
  
- <span data-ttu-id="8c838-112">IID_ICLROnEventManager: が ICLROnEventManager 型であることを指定し `ppObject` ます。 [ICLROnEventManager](iclroneventmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8c838-112">IID_ICLROnEventManager: Specifies that `ppObject` will be of type [ICLROnEventManager](iclroneventmanager-interface.md).</span></span>  
  
- <span data-ttu-id="8c838-113">IID_ICLRPolicyManager: が ICLRPolicyManager 型であることを指定し `ppObject` ます。 [ICLRPolicyManager](iclrpolicymanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8c838-113">IID_ICLRPolicyManager: Specifies that `ppObject` will be of type [ICLRPolicyManager](iclrpolicymanager-interface.md).</span></span>  
  
- <span data-ttu-id="8c838-114">IID_ICLRTaskManager: が ICLRTaskManager 型であることを指定し `ppObject` ます。 [ICLRTaskManager](iclrtaskmanager-interface.md)</span><span class="sxs-lookup"><span data-stu-id="8c838-114">IID_ICLRTaskManager: Specifies that `ppObject` will be of type [ICLRTaskManager](iclrtaskmanager-interface.md).</span></span>  
  
 `ppObject`  
 <span data-ttu-id="8c838-115">入出力要求されたマネージャーへのインターフェイスポインター。無効なマネージャーの種類が要求された場合は null。</span><span class="sxs-lookup"><span data-stu-id="8c838-115">[out] An interface pointer to the requested manager, or null, if an invalid manager type was requested.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8c838-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="8c838-116">Return Value</span></span>  
  
|<span data-ttu-id="8c838-117">HRESULT</span><span class="sxs-lookup"><span data-stu-id="8c838-117">HRESULT</span></span>|<span data-ttu-id="8c838-118">説明</span><span class="sxs-lookup"><span data-stu-id="8c838-118">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8c838-119">S_OK</span><span class="sxs-lookup"><span data-stu-id="8c838-119">S_OK</span></span>|<span data-ttu-id="8c838-120">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="8c838-120">The method returned successfully.</span></span>|  
|<span data-ttu-id="8c838-121">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="8c838-121">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="8c838-122">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="8c838-122">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="8c838-123">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="8c838-123">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="8c838-124">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="8c838-124">The call timed out.</span></span>|  
|<span data-ttu-id="8c838-125">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="8c838-125">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="8c838-126">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="8c838-126">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="8c838-127">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="8c838-127">HOST_E_ABANDONED</span></span>|<span data-ttu-id="8c838-128">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="8c838-128">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="8c838-129">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="8c838-129">E_FAIL</span></span>|<span data-ttu-id="8c838-130">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="8c838-130">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="8c838-131">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="8c838-131">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="8c838-132">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="8c838-132">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="8c838-133">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="8c838-133">E_NOINTERFACE</span></span>|<span data-ttu-id="8c838-134">インターフェイス型はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="8c838-134">The interface type is not supported.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c838-135">要件</span><span class="sxs-lookup"><span data-stu-id="8c838-135">Requirements</span></span>  

 <span data-ttu-id="8c838-136">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8c838-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c838-137">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="8c838-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c838-138">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="8c838-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="8c838-139">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c838-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c838-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="8c838-140">See also</span></span>

- [<span data-ttu-id="8c838-141">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c838-141">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="8c838-142">IHostControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8c838-142">IHostControl Interface</span></span>](ihostcontrol-interface.md)
