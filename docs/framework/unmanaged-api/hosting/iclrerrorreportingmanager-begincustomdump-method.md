---
title: ICLRErrorReportingManager::BeginCustomDump メソッド
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.BeginCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type:
- apiref
ms.openlocfilehash: 199c130d70cfbf0d383c2e0dc148ffe3dc1242d1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673562"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="87934-102">ICLRErrorReportingManager::BeginCustomDump メソッド</span><span class="sxs-lookup"><span data-stu-id="87934-102">ICLRErrorReportingManager::BeginCustomDump Method</span></span>

<span data-ttu-id="87934-103">エラー報告のためのカスタムヒープダンプの構成を指定します。</span><span class="sxs-lookup"><span data-stu-id="87934-103">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87934-104">構文</span><span class="sxs-lookup"><span data-stu-id="87934-104">Syntax</span></span>  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87934-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="87934-105">Parameters</span></span>  

 `dwFlavor`  
 <span data-ttu-id="87934-106">からカスタムヒープダンプを構築するときに使用するヒープダンプの種類を示す [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) 値です。</span><span class="sxs-lookup"><span data-stu-id="87934-106">[in] A [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="87934-107">から配列の長さ `items` 。</span><span class="sxs-lookup"><span data-stu-id="87934-107">[in] The length of the `items` array.</span></span> <span data-ttu-id="87934-108">`dwFlavor`が DUMP_FLAVOR_Mini でない場合は、を `dwNumItems` 0 にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="87934-108">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="87934-109">からミニダンプに追加する項目を指定する、 [Customdumpitem](customdumpitem-structure.md) インスタンスの配列。</span><span class="sxs-lookup"><span data-stu-id="87934-109">[in] An array of [CustomDumpItem](customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="87934-110">`dwFlavor`が DUMP_FLAVOR_Mini でない場合は、を `items` null にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="87934-110">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="87934-111">から将来使用するために予約されています。</span><span class="sxs-lookup"><span data-stu-id="87934-111">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="87934-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="87934-112">Return Value</span></span>  
  
|<span data-ttu-id="87934-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="87934-113">HRESULT</span></span>|<span data-ttu-id="87934-114">説明</span><span class="sxs-lookup"><span data-stu-id="87934-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="87934-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="87934-115">S_OK</span></span>|<span data-ttu-id="87934-116">メソッドから正常に値が返されました。</span><span class="sxs-lookup"><span data-stu-id="87934-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="87934-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="87934-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="87934-118">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="87934-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="87934-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="87934-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="87934-120">呼び出しがタイムアウトしました。</span><span class="sxs-lookup"><span data-stu-id="87934-120">The call timed out.</span></span>|  
|<span data-ttu-id="87934-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="87934-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="87934-122">呼び出し元がロックを所有していません。</span><span class="sxs-lookup"><span data-stu-id="87934-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="87934-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="87934-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="87934-124">ブロックされたスレッドまたはファイバーが待機しているときに、イベントが取り消されました。</span><span class="sxs-lookup"><span data-stu-id="87934-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="87934-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="87934-125">E_FAIL</span></span>|<span data-ttu-id="87934-126">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="87934-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="87934-127">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="87934-127">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="87934-128">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="87934-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="87934-129">注釈</span><span class="sxs-lookup"><span data-stu-id="87934-129">Remarks</span></span>  

 <span data-ttu-id="87934-130">メソッドは、 `BeginCustomDump` カスタムヒープダンプ構成を設定します。</span><span class="sxs-lookup"><span data-stu-id="87934-130">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="87934-131">[Endcustomdump](iclrerrorreportingmanager-endcustomdump-method.md)メソッドは、カスタムヒープダンプ構成をクリアし、関連付けられているすべての状態を解放します。</span><span class="sxs-lookup"><span data-stu-id="87934-131">The [EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="87934-132">カスタムヒープダンプの完了後に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="87934-132">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="87934-133">を呼び出さない `EndCustomDump` と、メモリがリークします。</span><span class="sxs-lookup"><span data-stu-id="87934-133">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87934-134">要件</span><span class="sxs-lookup"><span data-stu-id="87934-134">Requirements</span></span>  

 <span data-ttu-id="87934-135">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87934-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87934-136">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="87934-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="87934-137">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="87934-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="87934-138">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87934-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87934-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="87934-139">See also</span></span>

- [<span data-ttu-id="87934-140">CustomDumpItem 構造体</span><span class="sxs-lookup"><span data-stu-id="87934-140">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)
- [<span data-ttu-id="87934-141">ECustomDumpFlavor 列挙型</span><span class="sxs-lookup"><span data-stu-id="87934-141">ECustomDumpFlavor Enumeration</span></span>](ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="87934-142">ICLRErrorReportingManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="87934-142">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
