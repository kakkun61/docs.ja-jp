---
title: ICLRRuntimeHost::GetCLRControl メソッド
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type:
- apiref
ms.openlocfilehash: 928ac05fbd3a19a17e7f37674b2a75f8bc799fc6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728874"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="bb471-102">ICLRRuntimeHost::GetCLRControl メソッド</span><span class="sxs-lookup"><span data-stu-id="bb471-102">ICLRRuntimeHost::GetCLRControl Method</span></span>

<span data-ttu-id="bb471-103">ホストが共通言語ランタイム (CLR) の側面をカスタマイズするために使用できる [ICLRControl interface](iclrcontrol-interface.md) 型のインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="bb471-103">Gets an interface pointer of type [ICLRControl Interface](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb471-104">構文</span><span class="sxs-lookup"><span data-stu-id="bb471-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb471-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bb471-105">Parameters</span></span>  

 `pCLRControl`  
 <span data-ttu-id="bb471-106">入出力ホストが CLR の追加の側面を構成できるようにする [ICLRControl interface](iclrcontrol-interface.md) 型のインターフェイスポインター。</span><span class="sxs-lookup"><span data-stu-id="bb471-106">[out] An interface pointer of type [ICLRControl Interface](iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bb471-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="bb471-107">Return Value</span></span>  
  
|<span data-ttu-id="bb471-108">HRESULT</span><span class="sxs-lookup"><span data-stu-id="bb471-108">HRESULT</span></span>|<span data-ttu-id="bb471-109">説明</span><span class="sxs-lookup"><span data-stu-id="bb471-109">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="bb471-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="bb471-110">S_OK</span></span>|<span data-ttu-id="bb471-111">`GetCLRControl` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="bb471-111">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="bb471-112">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="bb471-112">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="bb471-113">CLR がプロセスに読み込まれていないか、CLR がマネージドコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="bb471-113">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="bb471-114">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="bb471-114">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="bb471-115">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="bb471-115">The call timed out.</span></span>|  
|<span data-ttu-id="bb471-116">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="bb471-116">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="bb471-117">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="bb471-117">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="bb471-118">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="bb471-118">HOST_E_ABANDONED</span></span>|<span data-ttu-id="bb471-119">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="bb471-119">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="bb471-120">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="bb471-120">E_FAIL</span></span>|<span data-ttu-id="bb471-121">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="bb471-121">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="bb471-122">メソッドが E_FAIL を返す場合、そのプロセス内で CLR は使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="bb471-122">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="bb471-123">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="bb471-123">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="bb471-124">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="bb471-124">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="bb471-125">CLR は既に開始されています。</span><span class="sxs-lookup"><span data-stu-id="bb471-125">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb471-126">注釈</span><span class="sxs-lookup"><span data-stu-id="bb471-126">Remarks</span></span>  

 <span data-ttu-id="bb471-127">`ICLRControl`[Getclrmanager メソッド](iclrcontrol-getclrmanager-method.md)を提供します。このメソッドを使用すると、ホストは、マネージャーの型のいずれかへのインターフェイスポインターを取得できます。</span><span class="sxs-lookup"><span data-stu-id="bb471-127">`ICLRControl` provides the [GetCLRManager Method](iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb471-128">要件</span><span class="sxs-lookup"><span data-stu-id="bb471-128">Requirements</span></span>  

 <span data-ttu-id="bb471-129">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bb471-129">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb471-130">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="bb471-130">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="bb471-131">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="bb471-131">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="bb471-132">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb471-132">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb471-133">関連項目</span><span class="sxs-lookup"><span data-stu-id="bb471-133">See also</span></span>

- [<span data-ttu-id="bb471-134">ICLRControl インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb471-134">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="bb471-135">ICLRRuntimeHost インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bb471-135">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
