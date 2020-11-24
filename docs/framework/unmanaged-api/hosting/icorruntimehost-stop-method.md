---
title: ICorRuntimeHost::Stop メソッド
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.Stop
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::Stop
helpviewer_keywords:
- Stop method, ICorRuntimeHost interface [.NET Framework hosting]
- ICorRuntimeHost::Stop method [.NET Framework hosting]
ms.assetid: 46a0d450-b516-4bef-8b71-8d3bf265cbed
topic_type:
- apiref
ms.openlocfilehash: 9342233317535ebecbcddea48b9029b81868eb0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95690149"
---
# <a name="icorruntimehoststop-method"></a><span data-ttu-id="7b43a-102">ICorRuntimeHost::Stop メソッド</span><span class="sxs-lookup"><span data-stu-id="7b43a-102">ICorRuntimeHost::Stop Method</span></span>

<span data-ttu-id="7b43a-103">現在のプロセスのランタイムでコードの実行を停止します。</span><span class="sxs-lookup"><span data-stu-id="7b43a-103">Stops the execution of code in the runtime for the current process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b43a-104">構文</span><span class="sxs-lookup"><span data-stu-id="7b43a-104">Syntax</span></span>  
  
```cpp  
HRESULT Stop ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="7b43a-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="7b43a-105">Return Value</span></span>  
  
|<span data-ttu-id="7b43a-106">HRESULT</span><span class="sxs-lookup"><span data-stu-id="7b43a-106">HRESULT</span></span>|<span data-ttu-id="7b43a-107">説明</span><span class="sxs-lookup"><span data-stu-id="7b43a-107">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="7b43a-108">S_OK</span><span class="sxs-lookup"><span data-stu-id="7b43a-108">S_OK</span></span>|<span data-ttu-id="7b43a-109">操作に成功しました。</span><span class="sxs-lookup"><span data-stu-id="7b43a-109">The operation was successful.</span></span>|  
|<span data-ttu-id="7b43a-110">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="7b43a-110">S_FALSE</span></span>|<span data-ttu-id="7b43a-111">操作を完了できませんでした。</span><span class="sxs-lookup"><span data-stu-id="7b43a-111">The operation failed to complete.</span></span>|  
|<span data-ttu-id="7b43a-112">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="7b43a-112">E_FAIL</span></span>|<span data-ttu-id="7b43a-113">不明な重大なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="7b43a-113">An unknown, catastrophic failure occurred.</span></span> <span data-ttu-id="7b43a-114">メソッドが E_FAIL を返す場合、このプロセスでは共通言語ランタイム (CLR) は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="7b43a-114">If a method returns E_FAIL, the common language runtime (CLR) is no longer usable in the process.</span></span> <span data-ttu-id="7b43a-115">後続のホスト Api への呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="7b43a-115">Subsequent calls to any hosting APIs return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="7b43a-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="7b43a-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="7b43a-117">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="7b43a-117">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b43a-118">注釈</span><span class="sxs-lookup"><span data-stu-id="7b43a-118">Remarks</span></span>  

 <span data-ttu-id="7b43a-119">通常、メソッドを呼び出す必要はありません。これは、 `Stop` プロセスが終了したときにコードが実行を停止するためです。</span><span class="sxs-lookup"><span data-stu-id="7b43a-119">It is typically unnecessary to call the `Stop` method, because the code stops executing when the process exits.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7b43a-120">を呼び出した後 `Stop` 、CLR を同じプロセスに再初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="7b43a-120">After a call to `Stop`, the CLR cannot be reinitialized into the same process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b43a-121">要件</span><span class="sxs-lookup"><span data-stu-id="7b43a-121">Requirements</span></span>  

 <span data-ttu-id="7b43a-122">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7b43a-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b43a-123">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="7b43a-123">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7b43a-124">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="7b43a-124">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7b43a-125">**.NET Framework のバージョン:** 1.0、1.1</span><span class="sxs-lookup"><span data-stu-id="7b43a-125">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b43a-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="7b43a-126">See also</span></span>

- [<span data-ttu-id="7b43a-127">ICorRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="7b43a-127">ICorRuntimeHost Interface</span></span>](icorruntimehost-interface.md)
