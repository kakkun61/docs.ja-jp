---
title: ICorRuntimeHost::CreateDomainSetup メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomainSetup
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomainSetup
helpviewer_keywords:
- CreateDomainSetup method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomainSetup method [.NET Framework hosting]
ms.assetid: c21dab60-fb65-47d9-8a94-7fd47ca53b48
topic_type:
- apiref
ms.openlocfilehash: 1be7eee5c2591f26c33572446080a4fa4b3b929d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723897"
---
# <a name="icorruntimehostcreatedomainsetup-method"></a><span data-ttu-id="d0136-102">ICorRuntimeHost::CreateDomainSetup メソッド</span><span class="sxs-lookup"><span data-stu-id="d0136-102">ICorRuntimeHost::CreateDomainSetup Method</span></span>

<span data-ttu-id="d0136-103">インスタンスへの IAppDomainSetup 型のインターフェイスポインターを取得し <xref:System.AppDomainSetup?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="d0136-103">Gets an interface pointer of type IAppDomainSetup to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="d0136-104">`IAppDomainSetup` アプリケーションドメインを作成する前に構成するためのメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d0136-104">`IAppDomainSetup` provides methods to configure aspects of an application domain before it is created.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0136-105">構文</span><span class="sxs-lookup"><span data-stu-id="d0136-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomainSetup (  
    [out] IUnknown** pAppDomainSetup  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0136-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d0136-106">Parameters</span></span>  

 `pAppDomainSetup`  
 <span data-ttu-id="d0136-107">入出力インスタンスへのインターフェイスポインター <xref:System.AppDomainSetup?displayProperty=nameWithType> 。</span><span class="sxs-lookup"><span data-stu-id="d0136-107">[out] An interface pointer to an <xref:System.AppDomainSetup?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="d0136-108">このパラメーターはとして型指定さ `IUnknown` れるため、通常、呼び出し元は `QueryInterface` このポインターを呼び出して、型のインターフェイスポインターを取得する必要があり `IAppDomainSetup` ます。</span><span class="sxs-lookup"><span data-stu-id="d0136-108">This parameter is typed as `IUnknown`, so callers should generally call `QueryInterface` on this pointer to obtain an interface pointer of type `IAppDomainSetup`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d0136-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="d0136-109">Return Value</span></span>  
  
|<span data-ttu-id="d0136-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="d0136-110">HRESULT</span></span>|<span data-ttu-id="d0136-111">説明</span><span class="sxs-lookup"><span data-stu-id="d0136-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="d0136-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="d0136-112">S_OK</span></span>|<span data-ttu-id="d0136-113">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="d0136-113">The operation was successful.</span></span>|  
|<span data-ttu-id="d0136-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="d0136-114">S_FALSE</span></span>|<span data-ttu-id="d0136-115">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="d0136-115">The operation failed to complete.</span></span>|  
|<span data-ttu-id="d0136-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="d0136-116">E_FAIL</span></span>|<span data-ttu-id="d0136-117">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="d0136-117">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="d0136-118">メソッドが E_FAIL を返す場合、このプロセスでは共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="d0136-118">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="d0136-119">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="d0136-119">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="d0136-120">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="d0136-120">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="d0136-121">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="d0136-121">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d0136-122">注釈</span><span class="sxs-lookup"><span data-stu-id="d0136-122">Remarks</span></span>  

 <span data-ttu-id="d0136-123">このメソッドから返されるポインターは、通常、パラメーターとして [Createdomainex](icorruntimehost-createdomainex-method.md) メソッドに渡されます。</span><span class="sxs-lookup"><span data-stu-id="d0136-123">The pointer returned from this method is typically passed as a parameter to the [CreateDomainEx](icorruntimehost-createdomainex-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0136-124">要件</span><span class="sxs-lookup"><span data-stu-id="d0136-124">Requirements</span></span>  

 <span data-ttu-id="d0136-125">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0136-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0136-126">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="d0136-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="d0136-127">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="d0136-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="d0136-128">**.NET Framework バージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="d0136-128">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0136-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0136-129">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- <xref:System.AppDomainSetup>
- <xref:System.IAppDomainSetup?displayProperty=nameWithType>
- [<span data-ttu-id="d0136-130">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d0136-130">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
