---
title: ICLRRuntimeHost インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
ms.openlocfilehash: 8d88222215eb31e1c63f3b26079517c4b088e81b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728837"
---
# <a name="iclrruntimehost-interface"></a><span data-ttu-id="708d4-102">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="708d4-102">ICLRRuntimeHost Interface</span></span>

<span data-ttu-id="708d4-103">.NET Framework バージョン1で提供される [ICorRuntimeHost](icorruntimehost-interface.md) インターフェイスと同様の機能を提供します。次の変更点があります。</span><span class="sxs-lookup"><span data-stu-id="708d4-103">Provides functionality similar to that of the [ICorRuntimeHost](icorruntimehost-interface.md) interface provided in the .NET Framework version 1, with the following changes:</span></span>  
  
- <span data-ttu-id="708d4-104">ホストコントロールインターフェイスを設定するための [Sethostcontrol](iclrruntimehost-sethostcontrol-method.md) メソッドの追加。</span><span class="sxs-lookup"><span data-stu-id="708d4-104">The addition of the [SetHostControl](iclrruntimehost-sethostcontrol-method.md) method to set the host control interface.</span></span>  
  
- <span data-ttu-id="708d4-105">によって提供されるいくつかのメソッドの省略 `ICorRuntimeHost` 。</span><span class="sxs-lookup"><span data-stu-id="708d4-105">The omission of some methods provided by `ICorRuntimeHost`.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="708d4-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="708d4-106">Methods</span></span>  
  
|<span data-ttu-id="708d4-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="708d4-107">Method</span></span>|<span data-ttu-id="708d4-108">説明</span><span class="sxs-lookup"><span data-stu-id="708d4-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="708d4-109">ExecuteApplication メソッド</span><span class="sxs-lookup"><span data-stu-id="708d4-109">ExecuteApplication Method</span></span>](iclrruntimehost-executeapplication-method.md)|<span data-ttu-id="708d4-110">新しいドメインでアクティブ化するアプリケーションを指定するために、マニフェストベースの ClickOnce 配置シナリオで使用されます。</span><span class="sxs-lookup"><span data-stu-id="708d4-110">Used in manifest-based ClickOnce deployment scenarios to specify the application to be activated in a new domain.</span></span>|  
|[<span data-ttu-id="708d4-111">ExecuteInAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="708d4-111">ExecuteInAppDomain Method</span></span>](iclrruntimehost-executeinappdomain-method.md)|<span data-ttu-id="708d4-112">指定し <xref:System.AppDomain> たマネージコードを実行するを指定します。</span><span class="sxs-lookup"><span data-stu-id="708d4-112">Specifies the <xref:System.AppDomain> in which to execute the specified managed code.</span></span>|  
|[<span data-ttu-id="708d4-113">ExecuteInDefaultAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="708d4-113">ExecuteInDefaultAppDomain Method</span></span>](iclrruntimehost-executeindefaultappdomain-method.md)|<span data-ttu-id="708d4-114">指定したアセンブリ内で、指定した型の指定したメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="708d4-114">Invokes the specified method of the specified type in the specified assembly.</span></span>|  
|[<span data-ttu-id="708d4-115">GetCLRControl メソッド</span><span class="sxs-lookup"><span data-stu-id="708d4-115">GetCLRControl Method</span></span>](iclrruntimehost-getclrcontrol-method.md)|<span data-ttu-id="708d4-116">ホストが共通言語ランタイム (CLR) の側面をカスタマイズするために使用できる、 [ICLRControl](iclrcontrol-interface.md) 型のインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="708d4-116">Gets an interface pointer of type [ICLRControl](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>|  
|[<span data-ttu-id="708d4-117">GetCurrentAppDomainId メソッド</span><span class="sxs-lookup"><span data-stu-id="708d4-117">GetCurrentAppDomainId Method</span></span>](iclrruntimehost-getcurrentappdomainid-method.md)|<span data-ttu-id="708d4-118">現在実行中のの数値識別子を取得し <xref:System.AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="708d4-118">Gets the numeric identifier of the <xref:System.AppDomain> that is currently executing.</span></span>|  
|[<span data-ttu-id="708d4-119">SetHostControl メソッド</span><span class="sxs-lookup"><span data-stu-id="708d4-119">SetHostControl Method</span></span>](iclrruntimehost-sethostcontrol-method.md)|<span data-ttu-id="708d4-120">ホストコントロールインターフェイスを設定します。</span><span class="sxs-lookup"><span data-stu-id="708d4-120">Sets the host control interface.</span></span> <span data-ttu-id="708d4-121">を呼び出す前に、を呼び出す必要があり `SetHostControl` `Start` ます。</span><span class="sxs-lookup"><span data-stu-id="708d4-121">You must call `SetHostControl` before calling `Start`.</span></span>|  
|[<span data-ttu-id="708d4-122">Start メソッド</span><span class="sxs-lookup"><span data-stu-id="708d4-122">Start Method</span></span>](iclrruntimehost-start-method.md)|<span data-ttu-id="708d4-123">CLR をプロセスに初期化します。</span><span class="sxs-lookup"><span data-stu-id="708d4-123">Initializes the CLR into a process.</span></span>|  
|[<span data-ttu-id="708d4-124">Stop メソッド</span><span class="sxs-lookup"><span data-stu-id="708d4-124">Stop Method</span></span>](iclrruntimehost-stop-method.md)|<span data-ttu-id="708d4-125">ランタイムによるコードの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="708d4-125">Stops the execution of code by the runtime.</span></span>|  
|[<span data-ttu-id="708d4-126">UnloadAppDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="708d4-126">UnloadAppDomain Method</span></span>](iclrruntimehost-unloadappdomain-method.md)|<span data-ttu-id="708d4-127">指定した <xref:System.AppDomain> 数値識別子に対応するをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="708d4-127">Unloads the <xref:System.AppDomain> that corresponds to the specified numeric identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="708d4-128">注釈</span><span class="sxs-lookup"><span data-stu-id="708d4-128">Remarks</span></span>  

 <span data-ttu-id="708d4-129">.NET Framework 4 以降では、 [ICLRMetaHost](iclrmetahost-interface.md) インターフェイスを使用して [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) インターフェイスへのポインターを取得し、 [ICLRRuntimeInfo:: getinterface](iclrruntimeinfo-getinterface-method.md) メソッドを呼び出して、へのポインターを取得し `ICLRRuntimeHost` ます。</span><span class="sxs-lookup"><span data-stu-id="708d4-129">Starting with the .NET Framework 4, use the [ICLRMetaHost](iclrmetahost-interface.md) interface to get a pointer to the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface, and then call the [ICLRRuntimeInfo::GetInterface](iclrruntimeinfo-getinterface-method.md) method to get a pointer to `ICLRRuntimeHost`.</span></span> <span data-ttu-id="708d4-130">以前のバージョンの .NET Framework では、ホストは `ICLRRuntimeHost` [Corbindtoruntimeex](corbindtoruntimeex-function.md) または [Corbindtoの entruntime](corbindtocurrentruntime-function.md)を呼び出すことによって、インスタンスへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="708d4-130">In earlier versions of the .NET Framework, the host gets a pointer to an `ICLRRuntimeHost` instance by calling [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span> <span data-ttu-id="708d4-131">.NET Framework バージョン2.0 で提供されるテクノロジの実装を提供するには、の代わりにを使用する必要があり `ICLRRuntimeHost` `ICorRuntimeHost` ます。</span><span class="sxs-lookup"><span data-stu-id="708d4-131">To provide implementations of any of the technologies provided in the .NET Framework version 2.0, you must use `ICLRRuntimeHost` instead of `ICorRuntimeHost`.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="708d4-132">マニフェストベースのアプリケーションをアクティブ化するには、 [Executeapplication](iclrruntimehost-executeapplication-method.md)メソッドを呼び出す前に[Start](iclrruntimehost-start-method.md)メソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="708d4-132">Do not call the [Start](iclrruntimehost-start-method.md) method before calling the [ExecuteApplication](iclrruntimehost-executeapplication-method.md) method to activate a manifest-based application.</span></span> <span data-ttu-id="708d4-133">`Start`メソッドが最初に呼び出された場合、 `ExecuteApplication` メソッドの呼び出しは失敗します。</span><span class="sxs-lookup"><span data-stu-id="708d4-133">If the `Start` method is called first, the `ExecuteApplication` method call will fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="708d4-134">要件</span><span class="sxs-lookup"><span data-stu-id="708d4-134">Requirements</span></span>  

 <span data-ttu-id="708d4-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="708d4-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="708d4-136">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="708d4-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="708d4-137">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="708d4-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="708d4-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="708d4-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="708d4-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="708d4-139">See also</span></span>

- [<span data-ttu-id="708d4-140">CorBindToCurrentRuntime 関数</span><span class="sxs-lookup"><span data-stu-id="708d4-140">CorBindToCurrentRuntime Function</span></span>](corbindtocurrentruntime-function.md)
- [<span data-ttu-id="708d4-141">CorBindToRuntimeEx 関数</span><span class="sxs-lookup"><span data-stu-id="708d4-141">CorBindToRuntimeEx Function</span></span>](corbindtoruntimeex-function.md)
- [<span data-ttu-id="708d4-142">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="708d4-142">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="708d4-143">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="708d4-143">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
- [<span data-ttu-id="708d4-144">ホスト インターフェイス</span><span class="sxs-lookup"><span data-stu-id="708d4-144">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="708d4-145">CLRRuntimeHost コクラス</span><span class="sxs-lookup"><span data-stu-id="708d4-145">CLRRuntimeHost Coclass</span></span>](clrruntimehost-coclass.md)
