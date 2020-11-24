---
title: ICLRDebugManager::SetSymbolReadingPolicy メソッド
ms.date: 03/30/2017
api_name:
- ICLRDebugManager.SetSymbolReadingPolicy
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRDebugManager::SetSymbolReadingPolicy
helpviewer_keywords:
- ICLRDebugManager, SetSymbolREadingPolicy method
- SetSymbolReadingPolicy method [.NET Framework hosting]
- ICLRDebugManager::SetSymbolReadingPolicy method [.NET Framework hosting]
ms.assetid: bd921fa2-d377-4d79-acfc-64c38d4dcae9
topic_type:
- apiref
ms.openlocfilehash: a311166e79f930e763b0338451f6356c8c93f929
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670142"
---
# <a name="iclrdebugmanagersetsymbolreadingpolicy-method"></a><span data-ttu-id="cd52d-102">ICLRDebugManager::SetSymbolReadingPolicy メソッド</span><span class="sxs-lookup"><span data-stu-id="cd52d-102">ICLRDebugManager::SetSymbolReadingPolicy Method</span></span>

<span data-ttu-id="cd52d-103">プログラムデータベース (PDB) ファイルを読み取るためのポリシーを設定します。</span><span class="sxs-lookup"><span data-stu-id="cd52d-103">Sets the policy for reading program database (PDB) files.</span></span> <span data-ttu-id="cd52d-104">ポリシーは、行番号とファイルに関する情報が呼び出し履歴に含まれるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="cd52d-104">The policy determines whether information about line numbers and files is included in call stacks.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd52d-105">構文</span><span class="sxs-lookup"><span data-stu-id="cd52d-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymbolReadingPolicy (  
    [in] ESymbolReadingPolicy policy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cd52d-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cd52d-106">Parameters</span></span>  

 `policy`  
 <span data-ttu-id="cd52d-107">から [ESymbolReadingPolicy](esymbolreadingpolicy-enumeration.md) 列挙体のメンバー。</span><span class="sxs-lookup"><span data-stu-id="cd52d-107">[in] A member of the [ESymbolReadingPolicy](esymbolreadingpolicy-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cd52d-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="cd52d-108">Return Value</span></span>  
  
|<span data-ttu-id="cd52d-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="cd52d-109">HRESULT</span></span>|<span data-ttu-id="cd52d-110">説明</span><span class="sxs-lookup"><span data-stu-id="cd52d-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="cd52d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="cd52d-111">S_OK</span></span>|<span data-ttu-id="cd52d-112">`SetSymbolReadingPolicy` 正常に返されました。</span><span class="sxs-lookup"><span data-stu-id="cd52d-112">`SetSymbolReadingPolicy` returned successfully.</span></span>|  
|<span data-ttu-id="cd52d-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="cd52d-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="cd52d-114">共通言語ランタイム (CLR) がプロセスに読み込まれていないか、CLR がマネージコードを実行できない状態であるか、または呼び出しが正常に処理されていません。</span><span class="sxs-lookup"><span data-stu-id="cd52d-114">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="cd52d-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="cd52d-115">E_FAIL</span></span>|<span data-ttu-id="cd52d-116">原因不明の致命的なエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="cd52d-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="cd52d-117">メソッドが E_FAIL を返すと、そのプロセス内で CLR が使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="cd52d-117">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="cd52d-118">後続のホストメソッドの呼び出しでは HOST_E_CLRNOTAVAILABLE が返されます。</span><span class="sxs-lookup"><span data-stu-id="cd52d-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd52d-119">要件</span><span class="sxs-lookup"><span data-stu-id="cd52d-119">Requirements</span></span>  

 <span data-ttu-id="cd52d-120">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cd52d-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd52d-121">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="cd52d-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="cd52d-122">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="cd52d-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="cd52d-123">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd52d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd52d-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd52d-124">See also</span></span>

- [<span data-ttu-id="cd52d-125">ICLRDebugManager インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cd52d-125">ICLRDebugManager Interface</span></span>](iclrdebugmanager-interface.md)
