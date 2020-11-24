---
title: ICorRuntimeHost::UnloadDomain メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.UnloadDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::UnloadDomain
helpviewer_keywords:
- ICorRuntimeHost::UnloadDomain method [.NET Framework hosting]
- UnloadDomain method [.NET Framework hosting]
ms.assetid: dd9e9204-a80d-44f3-8192-779224b35056
topic_type:
- apiref
ms.openlocfilehash: 94c84d876e19ec2ff7baba5a5a7420eec68d58c6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690110"
---
# <a name="icorruntimehostunloaddomain-method"></a><span data-ttu-id="21c1e-102">ICorRuntimeHost::UnloadDomain メソッド</span><span class="sxs-lookup"><span data-stu-id="21c1e-102">ICorRuntimeHost::UnloadDomain Method</span></span>

<span data-ttu-id="21c1e-103">現在のプロセスから、指定されたアプリケーションドメインをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="21c1e-103">Unloads the specified application domain from the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21c1e-104">構文</span><span class="sxs-lookup"><span data-stu-id="21c1e-104">Syntax</span></span>  
  
```cpp  
HRESULT UnloadDomain (  
    [in] IUnknown* pAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="21c1e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="21c1e-105">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="21c1e-106">から <xref:System._AppDomain?displayProperty=nameWithType> アンロードするドメインを表す型のポインター。</span><span class="sxs-lookup"><span data-stu-id="21c1e-106">[in] A pointer of type <xref:System._AppDomain?displayProperty=nameWithType> that represents the domain to be unloaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21c1e-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="21c1e-107">Return Value</span></span>  
  
|<span data-ttu-id="21c1e-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="21c1e-108">HRESULT</span></span>|<span data-ttu-id="21c1e-109">説明</span><span class="sxs-lookup"><span data-stu-id="21c1e-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="21c1e-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="21c1e-110">S_OK</span></span>|<span data-ttu-id="21c1e-111">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="21c1e-111">The operation was successful.</span></span>|  
|<span data-ttu-id="21c1e-112">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="21c1e-112">S_FALSE</span></span>|<span data-ttu-id="21c1e-113">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="21c1e-113">The operation failed to complete.</span></span>|  
|<span data-ttu-id="21c1e-114">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="21c1e-114">E_FAIL</span></span>|<span data-ttu-id="21c1e-115">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="21c1e-115">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="21c1e-116">メソッドが E_FAIL を返す場合、このプロセスでは共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="21c1e-116">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="21c1e-117">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="21c1e-117">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="21c1e-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="21c1e-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="21c1e-119">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="21c1e-119">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="21c1e-120">要件</span><span class="sxs-lookup"><span data-stu-id="21c1e-120">Requirements</span></span>  

 <span data-ttu-id="21c1e-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21c1e-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21c1e-122">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="21c1e-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="21c1e-123">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="21c1e-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="21c1e-124">**.NET Framework バージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="21c1e-124">**.NET Framework Version:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21c1e-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="21c1e-125">See also</span></span>

- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [<span data-ttu-id="21c1e-126">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="21c1e-126">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
