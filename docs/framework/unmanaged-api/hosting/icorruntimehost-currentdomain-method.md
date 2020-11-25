---
title: ICorRuntimeHost::CurrentDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CurrentDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CurrentDomain
helpviewer_keywords:
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
- CurrentDomain method [.NET Framework hosting]
ms.assetid: dd2afb38-675b-4c3c-a9f3-8ab3b133eb02
topic_type:
- apiref
ms.openlocfilehash: 33d56354a560949b2f451df9ef82d4f433951195
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715564"
---
# <a name="icorruntimehostcurrentdomain-method"></a><span data-ttu-id="0c92e-102">ICorRuntimeHost::CurrentDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="0c92e-102">ICorRuntimeHost::CurrentDomain Method</span></span>

<span data-ttu-id="0c92e-103"><xref:System.AppDomain?displayProperty=nameWithType>現在のスレッドに読み込まれているドメインを表す型のインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="0c92e-103">Gets an interface pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the domain loaded on the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c92e-104">構文</span><span class="sxs-lookup"><span data-stu-id="0c92e-104">Syntax</span></span>  
  
```cpp  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c92e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0c92e-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="0c92e-106">入出力 <xref:System.AppDomain?displayProperty=nameWithType> スレッドの現在のアプリケーションドメインを表す型のポインター。</span><span class="sxs-lookup"><span data-stu-id="0c92e-106">[out] A pointer of type <xref:System.AppDomain?displayProperty=nameWithType> that represents the thread's current application domain.</span></span> <span data-ttu-id="0c92e-107">このポインターは型指定されている `IUnknown` ため、呼び出し元は、通常、 `QueryInterface` 型のポインターを取得するためにを呼び出す必要があり <xref:System._AppDomain> ます。</span><span class="sxs-lookup"><span data-stu-id="0c92e-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain a pointer of type <xref:System._AppDomain>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0c92e-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="0c92e-108">Return Value</span></span>  
  
|<span data-ttu-id="0c92e-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0c92e-109">HRESULT</span></span>|<span data-ttu-id="0c92e-110">説明</span><span class="sxs-lookup"><span data-stu-id="0c92e-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0c92e-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="0c92e-111">S_OK</span></span>|<span data-ttu-id="0c92e-112">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="0c92e-112">The operation was successful.</span></span>|  
|<span data-ttu-id="0c92e-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="0c92e-113">S_FALSE</span></span>|<span data-ttu-id="0c92e-114">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="0c92e-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="0c92e-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0c92e-115">E_FAIL</span></span>|<span data-ttu-id="0c92e-116">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="0c92e-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="0c92e-117">メソッドが E_FAIL を返す場合、このプロセスでは共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="0c92e-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="0c92e-118">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="0c92e-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="0c92e-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0c92e-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0c92e-120">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="0c92e-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0c92e-121">要件</span><span class="sxs-lookup"><span data-stu-id="0c92e-121">Requirements</span></span>  

 <span data-ttu-id="0c92e-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0c92e-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c92e-123">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="0c92e-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c92e-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="0c92e-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c92e-125">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="0c92e-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c92e-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="0c92e-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="0c92e-127">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0c92e-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
