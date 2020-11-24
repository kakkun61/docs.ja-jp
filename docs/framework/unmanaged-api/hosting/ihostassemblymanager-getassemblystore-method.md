---
title: IHostAssemblyManager::GetAssemblyStore メソッド
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager.GetAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager::GetAssemblyStore
helpviewer_keywords:
- IHostAssemblyManager::GetAssemblyStore method [.NET Framework hosting]
- GetAssemblyStore method [.NET Framework hosting]
ms.assetid: d0f74593-9bb1-4a11-8096-e29734b20698
topic_type:
- apiref
ms.openlocfilehash: 936ea068f3cc5567a00af5f2bdd5f3d9cd52bc81
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681185"
---
# <a name="ihostassemblymanagergetassemblystore-method"></a><span data-ttu-id="4bd1e-102">IHostAssemblyManager::GetAssemblyStore メソッド</span><span class="sxs-lookup"><span data-stu-id="4bd1e-102">IHostAssemblyManager::GetAssemblyStore Method</span></span>

<span data-ttu-id="4bd1e-103">ホストによって読み込まれたアセンブリの一覧を表す [IHostAssemblyStore](ihostassemblystore-interface.md) へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="4bd1e-103">Gets an interface pointer to an [IHostAssemblyStore](ihostassemblystore-interface.md) that represents the list of assemblies loaded by the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bd1e-104">構文</span><span class="sxs-lookup"><span data-stu-id="4bd1e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyStore (  
    [out] IHostAssemblyStore **ppAssemblyStore  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bd1e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4bd1e-105">Parameters</span></span>  

 `ppAssemblyStore`  
 <span data-ttu-id="4bd1e-106">入出力インスタンスへの関数ポインター `IHostAssemblyStore` 。ホストがを実装していない場合は null `IHostAssemblyStore` 。</span><span class="sxs-lookup"><span data-stu-id="4bd1e-106">[out] A function pointer to an `IHostAssemblyStore` instance, or null, if the host does not implement `IHostAssemblyStore`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4bd1e-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="4bd1e-107">Return Value</span></span>  
  
|<span data-ttu-id="4bd1e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4bd1e-108">HRESULT</span></span>|<span data-ttu-id="4bd1e-109">説明</span><span class="sxs-lookup"><span data-stu-id="4bd1e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4bd1e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="4bd1e-110">S_OK</span></span>|<span data-ttu-id="4bd1e-111">`GetAssemblyStore` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="4bd1e-111">`GetAssemblyStore` returned successfully.</span></span>|  
|<span data-ttu-id="4bd1e-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4bd1e-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4bd1e-113">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="4bd1e-113">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4bd1e-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4bd1e-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4bd1e-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="4bd1e-115">The call timed out.</span></span>|  
|<span data-ttu-id="4bd1e-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4bd1e-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4bd1e-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="4bd1e-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4bd1e-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4bd1e-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4bd1e-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="4bd1e-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4bd1e-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4bd1e-120">E_FAIL</span></span>|<span data-ttu-id="4bd1e-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="4bd1e-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4bd1e-122">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="4bd1e-122">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4bd1e-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="4bd1e-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4bd1e-124">E_NOINTERFACE</span><span class="sxs-lookup"><span data-stu-id="4bd1e-124">E_NOINTERFACE</span></span>|<span data-ttu-id="4bd1e-125">ホストはの実装を提供していません `IHostAssemblyStore` 。</span><span class="sxs-lookup"><span data-stu-id="4bd1e-125">The host does not provide an implementation of `IHostAssemblyStore`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bd1e-126">注釈</span><span class="sxs-lookup"><span data-stu-id="4bd1e-126">Remarks</span></span>  

 <span data-ttu-id="4bd1e-127">`IHostAssemblyStore` ホストが CLR とは無関係にアセンブリおよびモジュールにバインドできるようにするメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="4bd1e-127">`IHostAssemblyStore` provides methods that allow a host to bind to assemblies and modules independently of the CLR.</span></span> <span data-ttu-id="4bd1e-128">通常、ホストはアセンブリストアを提供して、アセンブリをファイルシステム以外の形式から読み込むことができるようにします。</span><span class="sxs-lookup"><span data-stu-id="4bd1e-128">Hosts typically provide assembly stores to allow assemblies to be loaded from formats other than the file system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4bd1e-129">ホストがを実装していない場合 `IHostAssemblyStore` 、は `GetAssemblyStore` E_NOINTERFACE の HRESULT 値を返し、を null に設定する必要があり `ppAssemblyStore` ます。</span><span class="sxs-lookup"><span data-stu-id="4bd1e-129">If the host does not implement `IHostAssemblyStore`, `GetAssemblyStore` should return an HRESULT value of E_NOINTERFACE, and should set `ppAssemblyStore` to null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bd1e-130">要件</span><span class="sxs-lookup"><span data-stu-id="4bd1e-130">Requirements</span></span>  

 <span data-ttu-id="4bd1e-131">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bd1e-131">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bd1e-132">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="4bd1e-132">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4bd1e-133">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="4bd1e-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4bd1e-134">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bd1e-134">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bd1e-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="4bd1e-135">See also</span></span>

- [<span data-ttu-id="4bd1e-136">IHostAssemblyManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4bd1e-136">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="4bd1e-137">IHostAssemblyStore インターフェイス</span><span class="sxs-lookup"><span data-stu-id="4bd1e-137">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
