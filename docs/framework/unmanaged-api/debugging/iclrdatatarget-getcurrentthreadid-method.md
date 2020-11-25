---
title: ICLRDataTarget::GetCurrentThreadID メソッド
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetCurrentThreadID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICLRDataTarget interface [.NET Framework debugging]
- ICLRDataTarget::GetCurrentThreadID method [.NET Framework debugging]
ms.assetid: dc9a0a6c-d592-4fb7-86ed-62684da3b0e1
topic_type:
- apiref
ms.openlocfilehash: 3a355822710394e9351f10be78dea283e2e9907c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703592"
---
# <a name="iclrdatatargetgetcurrentthreadid-method"></a><span data-ttu-id="41365-102">ICLRDataTarget::GetCurrentThreadID メソッド</span><span class="sxs-lookup"><span data-stu-id="41365-102">ICLRDataTarget::GetCurrentThreadID Method</span></span>

<span data-ttu-id="41365-103">現在のスレッドのオペレーティングシステム id を取得します。</span><span class="sxs-lookup"><span data-stu-id="41365-103">Gets the operating system identifier for the current thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41365-104">構文</span><span class="sxs-lookup"><span data-stu-id="41365-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID (  
    [out] ULONG32    *threadID  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="41365-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="41365-105">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="41365-106">入出力ターゲットプロセスの現在のスレッドのオペレーティングシステム識別子へのポインター。</span><span class="sxs-lookup"><span data-stu-id="41365-106">[out] A pointer to the operating system identifier of the current thread for the target process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="41365-107">注釈</span><span class="sxs-lookup"><span data-stu-id="41365-107">Remarks</span></span>  

 <span data-ttu-id="41365-108">ターゲットプロセスの現在のスレッドが存在しない場合、 `GetCurrentThreadID` メソッドは失敗する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="41365-108">If there is no current thread for the target process, the `GetCurrentThreadID` method may fail.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41365-109">要件</span><span class="sxs-lookup"><span data-stu-id="41365-109">Requirements</span></span>  

 <span data-ttu-id="41365-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="41365-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41365-111">**ヘッダー:** ClrData .idl, ClrData .h</span><span class="sxs-lookup"><span data-stu-id="41365-111">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="41365-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="41365-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41365-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41365-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41365-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="41365-114">See also</span></span>

- [<span data-ttu-id="41365-115">ICLRDataTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="41365-115">ICLRDataTarget Interface</span></span>](iclrdatatarget-interface.md)
