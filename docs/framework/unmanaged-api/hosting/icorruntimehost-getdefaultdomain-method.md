---
title: ICorRuntimeHost::GetDefaultDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
ms.openlocfilehash: 673c32c86c808c36db6454b8a9f0d8e68f9b1258
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720634"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a><span data-ttu-id="03f78-102">ICorRuntimeHost::GetDefaultDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="03f78-102">ICorRuntimeHost::GetDefaultDomain Method</span></span>

<span data-ttu-id="03f78-103"><xref:System._AppDomain?displayProperty=nameWithType>現在のプロセスの既定のドメインを表す型のインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="03f78-103">Gets an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the default domain for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03f78-104">構文</span><span class="sxs-lookup"><span data-stu-id="03f78-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="03f78-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="03f78-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="03f78-106">入出力 <xref:System._AppDomain?displayProperty=nameWithType> <xref:System.AppDomain> プロセスの既定のアプリケーションドメインを表すインスタンスへの型のインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="03f78-106">[out] An interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType> to the <xref:System.AppDomain> instance that represents the default application domain for the process.</span></span>  
  
 <span data-ttu-id="03f78-107">このポインターは型指定されている `IUnknown` ため、呼び出し元は、通常、 `QueryInterface` 型のインターフェイスポインターを取得するためにを呼び出す必要があり <xref:System._AppDomain?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="03f78-107">This pointer is typed `IUnknown`, so callers should generally call `QueryInterface` to obtain an interface pointer of type <xref:System._AppDomain?displayProperty=nameWithType>.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="03f78-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="03f78-108">Return Value</span></span>  
  
|<span data-ttu-id="03f78-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="03f78-109">HRESULT</span></span>|<span data-ttu-id="03f78-110">説明</span><span class="sxs-lookup"><span data-stu-id="03f78-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="03f78-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="03f78-111">S_OK</span></span>|<span data-ttu-id="03f78-112">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="03f78-112">The operation was successful.</span></span>|  
|<span data-ttu-id="03f78-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="03f78-113">S_FALSE</span></span>|<span data-ttu-id="03f78-114">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="03f78-114">The operation failed to complete.</span></span>|  
|<span data-ttu-id="03f78-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="03f78-115">E_FAIL</span></span>|<span data-ttu-id="03f78-116">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="03f78-116">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="03f78-117">メソッドが E_FAIL を返す場合、このプロセスでは共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="03f78-117">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="03f78-118">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="03f78-118">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="03f78-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="03f78-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="03f78-120">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="03f78-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="03f78-121">要件</span><span class="sxs-lookup"><span data-stu-id="03f78-121">Requirements</span></span>  

 <span data-ttu-id="03f78-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="03f78-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03f78-123">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="03f78-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="03f78-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="03f78-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="03f78-125">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="03f78-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03f78-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="03f78-126">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="03f78-127">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="03f78-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
