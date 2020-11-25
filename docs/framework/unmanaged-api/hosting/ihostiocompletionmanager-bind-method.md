---
title: IHostIoCompletionManager::Bind メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.Bind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::Bind
helpviewer_keywords:
- IHostIoCompletionManager::Bind method [.NET Framework hosting]
- Bind method [.NET Framework hosting]
ms.assetid: acd74cb5-7e22-4a07-83c3-82288e1abd9f
topic_type:
- apiref
ms.openlocfilehash: 5231db8de6129ed593e4e0d508b312b7034c01f0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733907"
---
# <a name="ihostiocompletionmanagerbind-method"></a><span data-ttu-id="481d3-102">IHostIoCompletionManager::Bind メソッド</span><span class="sxs-lookup"><span data-stu-id="481d3-102">IHostIoCompletionManager::Bind Method</span></span>

<span data-ttu-id="481d3-103">以前に [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md)を呼び出したときに作成された i/o 完了ポートに、指定されたハンドルをバインドします。</span><span class="sxs-lookup"><span data-stu-id="481d3-103">Binds the specified handle to an I/O completion port that has been created by an earlier call to [CreateIoCompletionPort](ihostiocompletionmanager-createiocompletionport-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="481d3-104">構文</span><span class="sxs-lookup"><span data-stu-id="481d3-104">Syntax</span></span>  
  
```cpp  
HRESULT Bind (  
    [in] HANDLE hPort,  
    [in] HANDLE hHandle  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="481d3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="481d3-105">Parameters</span></span>  

 `hPort`  
 <span data-ttu-id="481d3-106">からバインド先の i/o 完了ポート `hHandle` 。</span><span class="sxs-lookup"><span data-stu-id="481d3-106">[in] The I/O completion port to which to bind `hHandle`.</span></span> <span data-ttu-id="481d3-107">の値 `hPort` が null の場合、 `hHandle` は既定の i/o 完了ポートにバインドされます。</span><span class="sxs-lookup"><span data-stu-id="481d3-107">If the value of `hPort` is null, `hHandle` is bound to the default I/O completion port.</span></span>  
  
 `hHandle`  
 <span data-ttu-id="481d3-108">からバインド先のオペレーティングシステムハンドル `hPort` 。</span><span class="sxs-lookup"><span data-stu-id="481d3-108">[in] The operating system handle to bind to `hPort`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="481d3-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="481d3-109">Return Value</span></span>  
  
|<span data-ttu-id="481d3-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="481d3-110">HRESULT</span></span>|<span data-ttu-id="481d3-111">説明</span><span class="sxs-lookup"><span data-stu-id="481d3-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="481d3-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="481d3-112">S_OK</span></span>|<span data-ttu-id="481d3-113">`Bind` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="481d3-113">`Bind` returned successfully.</span></span>|  
|<span data-ttu-id="481d3-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="481d3-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="481d3-115">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="481d3-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="481d3-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="481d3-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="481d3-117">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="481d3-117">The call timed out.</span></span>|  
|<span data-ttu-id="481d3-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="481d3-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="481d3-119">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="481d3-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="481d3-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="481d3-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="481d3-121">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="481d3-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="481d3-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="481d3-122">E_FAIL</span></span>|<span data-ttu-id="481d3-123">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="481d3-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="481d3-124">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="481d3-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="481d3-125">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="481d3-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="481d3-126">注釈</span><span class="sxs-lookup"><span data-stu-id="481d3-126">Remarks</span></span>  

 <span data-ttu-id="481d3-127">I/o 完了ポートは、の呼び出しを使用して作成され `CreateIoCompletionPort` ます。</span><span class="sxs-lookup"><span data-stu-id="481d3-127">An I/O completion port is created by using a call to `CreateIoCompletionPort`.</span></span> <span data-ttu-id="481d3-128">CLR はを呼び出し `Bind` て、そのポートにハンドルをバインドします。</span><span class="sxs-lookup"><span data-stu-id="481d3-128">The CLR calls `Bind` to bind a handle to that port.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="481d3-129">I/o 要求が完了すると、ホストは [Iclriocomplete manager:: OnComplete](iclriocompletionmanager-oncomplete-method.md) メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="481d3-129">When an I/O request completes, the host must call the [ICLRIoCompletionManager::OnComplete](iclriocompletionmanager-oncomplete-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="481d3-130">要件</span><span class="sxs-lookup"><span data-stu-id="481d3-130">Requirements</span></span>  

 <span data-ttu-id="481d3-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="481d3-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="481d3-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="481d3-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="481d3-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="481d3-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="481d3-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="481d3-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="481d3-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="481d3-135">See also</span></span>

- [<span data-ttu-id="481d3-136">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="481d3-136">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
