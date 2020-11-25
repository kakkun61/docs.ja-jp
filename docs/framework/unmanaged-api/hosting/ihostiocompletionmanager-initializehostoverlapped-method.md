---
title: IHostIoCompletionManager::InitializeHostOverlapped メソッド
ms.date: 03/30/2017
api_name:
- IHostIoCompletionManager.InitializeHostOverlapped
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped
helpviewer_keywords:
- IHostIoCompletionManager::InitializeHostOverlapped method [.NET Framework hosting]
- InitializeHostOverlapped method [.NET Framework hosting]
ms.assetid: c35199bf-bc47-4901-b467-4e8a37644bbb
topic_type:
- apiref
ms.openlocfilehash: 397dbbeb0b85cb549a8b5917f977ecb13b3d6539
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720218"
---
# <a name="ihostiocompletionmanagerinitializehostoverlapped-method"></a><span data-ttu-id="107bd-102">IHostIoCompletionManager::InitializeHostOverlapped メソッド</span><span class="sxs-lookup"><span data-stu-id="107bd-102">IHostIoCompletionManager::InitializeHostOverlapped Method</span></span>

<span data-ttu-id="107bd-103">非同期 i/o 要求に使用される Win32 構造体に追加するカスタムデータを初期化する機会をホストに提供し `OVERLAPPED` ます。</span><span class="sxs-lookup"><span data-stu-id="107bd-103">Provides the host with an opportunity to initialize any custom data to append to a Win32 `OVERLAPPED` structure that is used for asynchronous I/O requests.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="107bd-104">構文</span><span class="sxs-lookup"><span data-stu-id="107bd-104">Syntax</span></span>  
  
```cpp  
HRESULT InitializeHostOverlapped (  
    [in] void* pvOverlapped  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="107bd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="107bd-105">Parameters</span></span>  

 `pvOverlapped`  
 <span data-ttu-id="107bd-106">から `OVERLAPPED` I/o 要求に含まれる Win32 構造体へのポインター。</span><span class="sxs-lookup"><span data-stu-id="107bd-106">[in] A pointer to the Win32 `OVERLAPPED` structure to be included with the I/O request.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="107bd-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="107bd-107">Return Value</span></span>  
  
|<span data-ttu-id="107bd-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="107bd-108">HRESULT</span></span>|<span data-ttu-id="107bd-109">説明</span><span class="sxs-lookup"><span data-stu-id="107bd-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="107bd-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="107bd-110">S_OK</span></span>|<span data-ttu-id="107bd-111">`InitializeHostOverlapped` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="107bd-111">`InitializeHostOverlapped` returned successfully.</span></span>|  
|<span data-ttu-id="107bd-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="107bd-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="107bd-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="107bd-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="107bd-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="107bd-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="107bd-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="107bd-115">The call timed out.</span></span>|  
|<span data-ttu-id="107bd-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="107bd-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="107bd-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="107bd-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="107bd-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="107bd-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="107bd-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="107bd-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="107bd-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="107bd-120">E_FAIL</span></span>|<span data-ttu-id="107bd-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="107bd-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="107bd-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="107bd-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="107bd-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="107bd-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="107bd-124">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="107bd-124">E_OUTOFMEMORY</span></span>|<span data-ttu-id="107bd-125">要求されたリソースを割り当てるのに十分なメモリがありませんでした。</span><span class="sxs-lookup"><span data-stu-id="107bd-125">Not enough memory was available to allocate the requested resource.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="107bd-126">注釈</span><span class="sxs-lookup"><span data-stu-id="107bd-126">Remarks</span></span>  

 <span data-ttu-id="107bd-127">Windows プラットフォーム関数は、構造体を使用して `OVERLAPPED` 非同期 i/o 要求の状態を格納します。</span><span class="sxs-lookup"><span data-stu-id="107bd-127">The Windows Platform functions use the `OVERLAPPED` structure to store state for asynchronous I/O requests.</span></span> <span data-ttu-id="107bd-128">CLR は、メソッドを呼び出して、 `InitializeHostOverlapped` ホストにカスタムデータをインスタンスに追加する機会を与え `OVERLAPPED` ます。</span><span class="sxs-lookup"><span data-stu-id="107bd-128">The CLR calls the `InitializeHostOverlapped` method to give the host the opportunity to append custom data to an `OVERLAPPED` instance.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="107bd-129">カスタムデータブロックの先頭に到達するには、ホストで、オフセットを構造体のサイズ () に設定する必要があり `OVERLAPPED` `sizeof(OVERLAPPED)` ます。</span><span class="sxs-lookup"><span data-stu-id="107bd-129">To get to the beginning of their custom data block, hosts must set the offset to the size of the `OVERLAPPED` structure (`sizeof(OVERLAPPED)`).</span></span>  
  
 <span data-ttu-id="107bd-130">E_OUTOFMEMORY の戻り値は、ホストがカスタムデータを初期化できなかったことを示します。</span><span class="sxs-lookup"><span data-stu-id="107bd-130">A return value of E_OUTOFMEMORY indicates that the host has failed to initialize its custom data.</span></span> <span data-ttu-id="107bd-131">この場合、CLR はエラーを報告し、呼び出しに失敗します。</span><span class="sxs-lookup"><span data-stu-id="107bd-131">In this case, the CLR reports an error and fails the call.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="107bd-132">要件</span><span class="sxs-lookup"><span data-stu-id="107bd-132">Requirements</span></span>  

 <span data-ttu-id="107bd-133">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="107bd-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="107bd-134">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="107bd-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="107bd-135">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="107bd-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="107bd-136">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="107bd-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="107bd-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="107bd-137">See also</span></span>

- [<span data-ttu-id="107bd-138">ICLRIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="107bd-138">ICLRIoCompletionManager Interface</span></span>](iclriocompletionmanager-interface.md)
- [<span data-ttu-id="107bd-139">GetHostOverlappedSize メソッド</span><span class="sxs-lookup"><span data-stu-id="107bd-139">GetHostOverlappedSize Method</span></span>](ihostiocompletionmanager-gethostoverlappedsize-method.md)
- [<span data-ttu-id="107bd-140">IHostIoCompletionManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="107bd-140">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
