---
title: ICorRuntimeHost::CreateDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CreateDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CreateDomain
helpviewer_keywords:
- CreateDomain method [.NET Framework hosting]
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
ms.assetid: b96c5ef3-a9df-4c7c-9952-432d3272cb5c
topic_type:
- apiref
ms.openlocfilehash: c495ce47b699d2e32d1f02e4afcf0444a9930c34
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723910"
---
# <a name="icorruntimehostcreatedomain-method"></a><span data-ttu-id="6e5e6-102">ICorRuntimeHost::CreateDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="6e5e6-102">ICorRuntimeHost::CreateDomain Method</span></span>

<span data-ttu-id="6e5e6-103">アプリケーションドメインを作成します。</span><span class="sxs-lookup"><span data-stu-id="6e5e6-103">Creates an application domain.</span></span> <span data-ttu-id="6e5e6-104">呼び出し元は、型のインターフェイスポインターを <xref:System._AppDomain> 型のインスタンスに受信し <xref:System.AppDomain?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="6e5e6-104">The caller receives an interface pointer of type <xref:System._AppDomain> to an instance of type <xref:System.AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e5e6-105">構文</span><span class="sxs-lookup"><span data-stu-id="6e5e6-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateDomain (  
    [in] LPWSTR    pwzFriendlyName,  
    [in] IUnknown* pIdentityArray,  
    [out] void   **pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e5e6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e5e6-106">Parameters</span></span>  

 `pwzFriendlyName`  
 <span data-ttu-id="6e5e6-107">からドメインのフレンドリ名を指定するために使用される省略可能なパラメーター。</span><span class="sxs-lookup"><span data-stu-id="6e5e6-107">[in] An optional parameter used to give a friendly name to the domain.</span></span> <span data-ttu-id="6e5e6-108">このフレンドリ名は、ドメインを識別するためのデバッガーなどのユーザーインターフェイスに表示できます。</span><span class="sxs-lookup"><span data-stu-id="6e5e6-108">This friendly name can be displayed in user interfaces such as debuggers to identify the domain.</span></span>  
  
 `pIdentityArray`  
 <span data-ttu-id="6e5e6-109">から `IIdentity` アクセス許可セットを確立するためにセキュリティポリシーによってマップされた証拠を表す、インスタンスへのポインターの配列 (省略可能)。</span><span class="sxs-lookup"><span data-stu-id="6e5e6-109">[in] An optional array of pointers to `IIdentity` instances that represent evidence mapped through security policy to establish a  permission set.</span></span> <span data-ttu-id="6e5e6-110">`IIdentity`オブジェクトは、 [createevidence](icorruntimehost-createevidence-method.md)メソッドを呼び出すことによって取得できます。</span><span class="sxs-lookup"><span data-stu-id="6e5e6-110">An `IIdentity` object can be obtained by calling the [CreateEvidence](icorruntimehost-createevidence-method.md) method.</span></span>  
  
 `pAppDomain`  
 <span data-ttu-id="6e5e6-111">入出力 <xref:System._AppDomain> <xref:System.AppDomain?displayProperty=nameWithType> ドメインをさらに制御するために使用できるのインスタンスへの型のインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="6e5e6-111">[out] An interface pointer of type <xref:System._AppDomain> to an instance of <xref:System.AppDomain?displayProperty=nameWithType> that can be used to further control the domain.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6e5e6-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="6e5e6-112">Return Value</span></span>  
  
|<span data-ttu-id="6e5e6-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6e5e6-113">HRESULT</span></span>|<span data-ttu-id="6e5e6-114">説明</span><span class="sxs-lookup"><span data-stu-id="6e5e6-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6e5e6-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="6e5e6-115">S_OK</span></span>|<span data-ttu-id="6e5e6-116">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="6e5e6-116">The operation was successful.</span></span>|  
|<span data-ttu-id="6e5e6-117">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="6e5e6-117">S_FALSE</span></span>|<span data-ttu-id="6e5e6-118">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="6e5e6-118">The operation failed to complete.</span></span>|  
|<span data-ttu-id="6e5e6-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6e5e6-119">E_FAIL</span></span>|<span data-ttu-id="6e5e6-120">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="6e5e6-120">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="6e5e6-121">メソッドが E_FAIL を返す場合、このプロセスでは共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="6e5e6-121">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="6e5e6-122">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="6e5e6-122">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="6e5e6-123">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6e5e6-123">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6e5e6-124">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="6e5e6-124">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6e5e6-125">要件</span><span class="sxs-lookup"><span data-stu-id="6e5e6-125">Requirements</span></span>  

 <span data-ttu-id="6e5e6-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e5e6-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e5e6-127">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="6e5e6-127">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6e5e6-128">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="6e5e6-128">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6e5e6-129">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="6e5e6-129">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e5e6-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e5e6-130">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="6e5e6-131">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6e5e6-131">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
