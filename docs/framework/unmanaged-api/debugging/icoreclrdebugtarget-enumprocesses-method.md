---
title: ICoreClrDebugTarget::EnumProcesses メソッド
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
ms.openlocfilehash: 7e0219ae0d7d474812865f01e4e2fcfe2e4da991
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679365"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="f70e6-102">ICoreClrDebugTarget::EnumProcesses メソッド</span><span class="sxs-lookup"><span data-stu-id="f70e6-102">ICoreClrDebugTarget::EnumProcesses Method</span></span>

<span data-ttu-id="f70e6-103">リモート コンピューターで実行されているプロセスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="f70e6-103">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f70e6-104">構文</span><span class="sxs-lookup"><span data-stu-id="f70e6-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f70e6-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f70e6-105">Parameters</span></span>  

 `pcProcs`  
 <span data-ttu-id="f70e6-106">[out] `ppProcs` に返されるプロセス数。</span><span class="sxs-lookup"><span data-stu-id="f70e6-106">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="f70e6-107">この値は 0 (ゼロ) になる可能性もあります。</span><span class="sxs-lookup"><span data-stu-id="f70e6-107">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="f70e6-108">入出力リモートコンピューター上で実行されているプロセスを表す [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) 構造体の配列。</span><span class="sxs-lookup"><span data-stu-id="f70e6-108">[out] An array of [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f70e6-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="f70e6-109">Return Value</span></span>  

 <span data-ttu-id="f70e6-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="f70e6-110">S_OK</span></span>  
 <span data-ttu-id="f70e6-111">正常終了しました。</span><span class="sxs-lookup"><span data-stu-id="f70e6-111">Success.</span></span>  
  
 <span data-ttu-id="f70e6-112">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="f70e6-112">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="f70e6-113">`ppProcs`  用に十分なメモリを割り当てることができません。</span><span class="sxs-lookup"><span data-stu-id="f70e6-113">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="f70e6-114">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="f70e6-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="f70e6-115">その他のエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="f70e6-115">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f70e6-116">注釈</span><span class="sxs-lookup"><span data-stu-id="f70e6-116">Remarks</span></span>  

 <span data-ttu-id="f70e6-117">このメソッドによって割り当てられたメモリを解放するには、 [ICoreClrDebugTarget:: FreeMemory](icoreclrdebugtarget-freememory-method.md) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="f70e6-117">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f70e6-118">要件</span><span class="sxs-lookup"><span data-stu-id="f70e6-118">Requirements</span></span>  

 <span data-ttu-id="f70e6-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f70e6-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f70e6-120">**ヘッダー:** Coreclrremoteデバッグインターフェイス .h</span><span class="sxs-lookup"><span data-stu-id="f70e6-120">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="f70e6-121">**ライブラリ:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="f70e6-121">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="f70e6-122">**.NET Framework のバージョン:** 3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="f70e6-122">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f70e6-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="f70e6-123">See also</span></span>

- [<span data-ttu-id="f70e6-124">ICoreClrDebugTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f70e6-124">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
