---
title: ICorDebugProcess::SetThreadContext メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.SetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::SetThreadContext
helpviewer_keywords:
- ICorDebugProcess::SetThreadContext method [.NET Framework debugging]
- SetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a7b50175-2bf1-40be-8f65-64aec7aa1247
topic_type:
- apiref
ms.openlocfilehash: 5b4052485a6d420eb83578d135ce51f8a918aab0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724521"
---
# <a name="icordebugprocesssetthreadcontext-method"></a><span data-ttu-id="6e978-102">ICorDebugProcess::SetThreadContext メソッド</span><span class="sxs-lookup"><span data-stu-id="6e978-102">ICorDebugProcess::SetThreadContext Method</span></span>

<span data-ttu-id="6e978-103">このプロセス内の指定されたスレッドのコンテキストを設定します。</span><span class="sxs-lookup"><span data-stu-id="6e978-103">Sets the context for the given thread in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e978-104">構文</span><span class="sxs-lookup"><span data-stu-id="6e978-104">Syntax</span></span>  
  
```cpp  
HRESULT SetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e978-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e978-105">Parameters</span></span>  

 `threadID`  
 <span data-ttu-id="6e978-106">からコンテキストを設定するスレッドの ID。</span><span class="sxs-lookup"><span data-stu-id="6e978-106">[in] The ID of the thread for which to set the context.</span></span>  
  
 `contextSize`  
 <span data-ttu-id="6e978-107">[in] `context` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6e978-107">[in] The size of the `context` array.</span></span>  
  
 `context`  
 <span data-ttu-id="6e978-108">からスレッドのコンテキストを記述するバイト配列。</span><span class="sxs-lookup"><span data-stu-id="6e978-108">[in] An array of bytes that describe the thread's context.</span></span>  
  
 <span data-ttu-id="6e978-109">コンテキストは、スレッドが実行されているプロセッサのアーキテクチャを指定します。</span><span class="sxs-lookup"><span data-stu-id="6e978-109">The context specifies the architecture of the processor on which the thread is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e978-110">注釈</span><span class="sxs-lookup"><span data-stu-id="6e978-110">Remarks</span></span>  

 <span data-ttu-id="6e978-111">デバッガーは、Win32 関数ではなく、このメソッドを呼び出す必要があります。これは、 `SetThreadContext` スレッドが実際には "ハイジャック" 状態にあり、そのコンテキストが一時的に変更されている可能性があるためです。</span><span class="sxs-lookup"><span data-stu-id="6e978-111">The debugger should call this method rather than the Win32 `SetThreadContext` function, because the thread may actually be in a "hijacked" state, in which its context has been temporarily changed.</span></span> <span data-ttu-id="6e978-112">このメソッドは、スレッドがネイティブコード内にある場合にのみ使用してください。</span><span class="sxs-lookup"><span data-stu-id="6e978-112">This method should be used only when a thread is in native code.</span></span> <span data-ttu-id="6e978-113">マネージコード内のスレッドには、コード [を使用し](icordebugregisterset-interface.md) ます。</span><span class="sxs-lookup"><span data-stu-id="6e978-113">Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) for threads in managed code.</span></span> <span data-ttu-id="6e978-114">アウトオブバンド (OOB) デバッグイベント中は、スレッドのコンテキストを変更する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="6e978-114">You should never need to modify the context of a thread during an out-of-band (OOB) debug event.</span></span>  
  
 <span data-ttu-id="6e978-115">渡されるデータは、現在のプラットフォームのコンテキスト構造である必要があります。</span><span class="sxs-lookup"><span data-stu-id="6e978-115">The data passed must be a context structure for the current platform.</span></span>  
  
 <span data-ttu-id="6e978-116">不適切に使用された場合、このメソッドはランタイムを破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6e978-116">This method can corrupt the runtime if used improperly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e978-117">要件</span><span class="sxs-lookup"><span data-stu-id="6e978-117">Requirements</span></span>  

 <span data-ttu-id="6e978-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e978-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e978-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e978-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e978-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e978-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e978-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6e978-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
