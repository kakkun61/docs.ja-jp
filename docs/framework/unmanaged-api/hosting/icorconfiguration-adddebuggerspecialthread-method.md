---
title: ICorConfiguration::AddDebuggerSpecialThread メソッド
ms.date: 03/30/2017
api_name:
- ICorConfiguration.AddDebuggerSpecialThread
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AddDebuggerSpecialThread
helpviewer_keywords:
- AddDebuggerSpecialThread method [.NET Framework hosting]
- ICorConfiguration::AddDebuggerSpecialThread method [.NET Framework hosting]
ms.assetid: 1f1e3239-438e-4be9-a3bb-7d0722d3a76d
topic_type:
- apiref
ms.openlocfilehash: bd89db3fa0b1814a98b016fcf9d1aeeabfff718b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95715850"
---
# <a name="icorconfigurationadddebuggerspecialthread-method"></a><span data-ttu-id="624b8-102">ICorConfiguration::AddDebuggerSpecialThread メソッド</span><span class="sxs-lookup"><span data-stu-id="624b8-102">ICorConfiguration::AddDebuggerSpecialThread Method</span></span>

<span data-ttu-id="624b8-103">デバッグサービスに対して、マネージまたはアンマネージのデバッグシナリオでデバッガーがアプリケーションを停止している間に、特定のスレッドの実行を継続できるようにする必要があることを示します。</span><span class="sxs-lookup"><span data-stu-id="624b8-103">Indicates to the debugging services that a particular thread should be allowed to continue executing while the debugger has an application stopped during managed or unmanaged debugging scenarios.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="624b8-104">構文</span><span class="sxs-lookup"><span data-stu-id="624b8-104">Syntax</span></span>  
  
```cpp  
HRESULT AddDebuggerSpecialThread (  
    [in] DWORD dwSpecialThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="624b8-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="624b8-105">Parameters</span></span>  

 `dwSpecialThreadId`  
 <span data-ttu-id="624b8-106">から実行を継続することが許可されているスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="624b8-106">[in] The ID of the thread that should be allowed to continue executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="624b8-107">注釈</span><span class="sxs-lookup"><span data-stu-id="624b8-107">Remarks</span></span>  

 <span data-ttu-id="624b8-108">指定されたスレッドはマネージコードの実行を許可されないか、または任意の方法でランタイムに入ることができません。</span><span class="sxs-lookup"><span data-stu-id="624b8-108">The specified thread will not be allowed to run managed code or enter the runtime in any way.</span></span> <span data-ttu-id="624b8-109">このようなスレッドの例として、レガシスクリプトデバッガーをサポートするインプロセススレッドがあります。</span><span class="sxs-lookup"><span data-stu-id="624b8-109">An example of such a thread would be an in-process thread to support legacy script debuggers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="624b8-110">要件</span><span class="sxs-lookup"><span data-stu-id="624b8-110">Requirements</span></span>  

 <span data-ttu-id="624b8-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="624b8-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="624b8-112">**ヘッダー:** Mscoree.dll</span><span class="sxs-lookup"><span data-stu-id="624b8-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="624b8-113">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="624b8-113">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="624b8-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="624b8-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="624b8-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="624b8-115">See also</span></span>

- [<span data-ttu-id="624b8-116">ICorConfiguration インターフェイス</span><span class="sxs-lookup"><span data-stu-id="624b8-116">ICorConfiguration Interface</span></span>](icorconfiguration-interface.md)
