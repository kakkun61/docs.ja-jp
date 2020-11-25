---
title: ICorRuntimeHost::CreateDomainEx メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainEx
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainEx
helpviewer_keywords:
- ICorRuntimeHost::CreateDomainEx method [.NET Framework hosting]
- CreateDomainEx method [.NET Framework hosting]
ms.assetid: 1bdde382-f8ba-4cc8-94b2-d1ac919c585e
topic_type:
- apiref
ms.openlocfilehash: d6d9e06b6ed40bb0e5a65fd64f8bca7abe3afa84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715681"
---
# <a name="icorruntimehostcreatedomainex-method"></a><span data-ttu-id="facde-102">ICorRuntimeHost::CreateDomainEx メソッド</span><span class="sxs-lookup"><span data-stu-id="facde-102">ICorRuntimeHost::CreateDomainEx Method</span></span>

<span data-ttu-id="facde-103">アプリケーションドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="facde-103">Creates an application domain.</span></span> <span data-ttu-id="facde-104">呼び出し元は、型のインターフェイスポインターを <xref:System._AppDomain> 型のインスタンスに受信し <xref:System.AppDomain?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="facde-104">The caller receives an interface pointer, of type <xref:System._AppDomain>, to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span> <span data-ttu-id="facde-105">このメソッドを使用すると、呼び出し元は IAppDomainSetup インスタンスを渡して、返されたインスタンスの追加の機能を構成でき <xref:System._AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="facde-105">This method allows the caller to pass an IAppDomainSetup instance to configure additional features of the returned <xref:System._AppDomain> instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="facde-106">構文</span><span class="sxs-lookup"><span data-stu-id="facde-106">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainEx (  
    [in] LPCWSTR     pwzFriendlyName,  
    [in] IUnknown*   pSetup,  
    [in] IUnknown*   pIdentityArray,  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="facde-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="facde-107">Parameters</span></span>  

 `pwzFriendlyName`  
 <span data-ttu-id="facde-108">からドメインのフレンドリ名を指定するために使用される省略可能なパラメーター。</span><span class="sxs-lookup"><span data-stu-id="facde-108">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="facde-109">このフレンドリ名は、ドメインを識別するためのデバッガーなどのユーザーインターフェイスに表示できます。</span><span class="sxs-lookup"><span data-stu-id="facde-109">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pSetup`  
 <span data-ttu-id="facde-110">から `IAppDomainSetup` [ICorRuntimeHost:: CreateDomainSetup](icorruntimehost-createdomainsetup-method.md) メソッドの呼び出しによって取得される、型の省略可能なインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="facde-110">[in] An optional interface pointer of type `IAppDomainSetup`, obtained by a call to the [ICorRuntimeHost::CreateDomainSetup](icorruntimehost-createdomainsetup-method.md) method.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="facde-111">から `IIdentity` アクセス許可セットを確立するためにセキュリティポリシーによってマップされた証拠を表す、インスタンスへのポインターの配列 (省略可能)。</span><span class="sxs-lookup"><span data-stu-id="facde-111">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a permission set.</span></span> <span data-ttu-id="facde-112">`IIdentity`オブジェクトは、 [createevidence](icorruntimehost-createevidence-method.md)メソッドを呼び出すことによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="facde-112">An `IIdentity` object can be obtained by calling the [CreateEvidence](icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="facde-113">入出力 <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> ドメインをさらに制御するために使用できるのインスタンスへの型のインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="facde-113">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="facde-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="facde-114">Return Value</span></span>  
  
|<span data-ttu-id="facde-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="facde-115">HRESULT</span></span>|<span data-ttu-id="facde-116">説明</span><span class="sxs-lookup"><span data-stu-id="facde-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="facde-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="facde-117">S_OK</span></span>|<span data-ttu-id="facde-118">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="facde-118">The operation was successful.</span></span>|  
|<span data-ttu-id="facde-119">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="facde-119">S_FALSE</span></span>|<span data-ttu-id="facde-120">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="facde-120">The operation failed to complete.</span></span>|  
|<span data-ttu-id="facde-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="facde-121">E_FAIL</span></span>|<span data-ttu-id="facde-122">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="facde-122">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="facde-123">メソッドが E_FAIL を返す場合、このプロセスでは共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="facde-123">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="facde-124">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="facde-124">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="facde-125">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="facde-125">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="facde-126">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="facde-126">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="facde-127">注釈</span><span class="sxs-lookup"><span data-stu-id="facde-127">Remarks</span></span>  

 <span data-ttu-id="facde-128">`CreateDomainEx` は、呼び出し元がインスタンスにアプリケーションドメインを構成するためのプロパティ値を渡すことができるようにすることで、 [Createdomain](icorruntimehost-createdomain-method.md) の機能を拡張し `IAppDomainSetup` ます。</span><span class="sxs-lookup"><span data-stu-id="facde-128">`CreateDomainEx` extends the capabilities of [CreateDomain](icorruntimehost-createdomain-method.md) by allowing the caller to pass in an `IAppDomainSetup` instance with property values for configuring the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="facde-129">要件</span><span class="sxs-lookup"><span data-stu-id="facde-129">Requirements</span></span>  

 <span data-ttu-id="facde-130">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="facde-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="facde-131">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="facde-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="facde-132">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="facde-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="facde-133">**.NET Framework バージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="facde-133">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="facde-134">関連項目</span><span class="sxs-lookup"><span data-stu-id="facde-134">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="facde-135">CreateDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="facde-135">CreateDomain Method</span></span>](icorruntimehost-createdomain-method.md)
- [<span data-ttu-id="facde-136">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="facde-136">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
