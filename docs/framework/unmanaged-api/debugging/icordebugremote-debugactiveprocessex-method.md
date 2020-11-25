---
title: ICorDebugRemote::DebugActiveProcessEx メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRemote.DebugActiveProcessEx
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugRemoteTarget::DebugActiveProcessEx
helpviewer_keywords:
- ICorDebugRemote::DebugActiveProcessEx method [.NET Framework debugging]
- DebugActiveProcessEx method, ICorDebugRemote interface [.NET Framework debugging]
ms.assetid: b0df5c5d-9a2e-47bf-894c-6f8a9fe24a1f
topic_type:
- apiref
ms.openlocfilehash: c9847fd6122aa32c95aecd5643a62a6775ae38d3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712119"
---
# <a name="icordebugremotedebugactiveprocessex-method"></a><span data-ttu-id="cde54-102">ICorDebugRemote::DebugActiveProcessEx メソッド</span><span class="sxs-lookup"><span data-stu-id="cde54-102">ICorDebugRemote::DebugActiveProcessEx Method</span></span>

<span data-ttu-id="cde54-103">デバッガーでリモートコンピューター上のプロセスを起動します。</span><span class="sxs-lookup"><span data-stu-id="cde54-103">Launches a process on a remote machine under the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cde54-104">構文</span><span class="sxs-lookup"><span data-stu-id="cde54-104">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcessEx (  
    [in]  ICorDebugRemoteTarget *   pRemoteTarget,  
    [in]  DWORD                     dwProcessId,  
    [in]  BOOL                      fWin32Attach,  
    [out] ICorDebugProcess **       ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cde54-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cde54-105">Parameters</span></span>  

 `pRemoteTarget`  
 <span data-ttu-id="cde54-106">からツールの [ターゲットインターフェイス](icordebugremotetarget-interface.md)を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="cde54-106">[in] Pointer to an [ICorDebugRemoteTarget Interface](icordebugremotetarget-interface.md).</span></span> <span data-ttu-id="cde54-107">このパラメーターは、プロセスが実行されているコンピューターを決定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="cde54-107">This parameter is used to determine the machine on which the process is running.</span></span>  
  
 `id`  
 <span data-ttu-id="cde54-108">からデバッガーがアタッチされるプロセスの ID。</span><span class="sxs-lookup"><span data-stu-id="cde54-108">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="cde54-109">[入力] `true` デバッガーがプロセスの Win32 デバッガーとして動作し、アンマネージコールバックをディスパッチする必要がある場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="cde54-109">[in] `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="cde54-110">入出力デバッガーがアタッチされているプロセスを表す "いいプロセス" オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="cde54-110">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cde54-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="cde54-111">Return Value</span></span>  

 <span data-ttu-id="cde54-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="cde54-112">S_OK</span></span>  
 <span data-ttu-id="cde54-113">リモートコンピューター上のプロセスに正常にアタッチされました。</span><span class="sxs-lookup"><span data-stu-id="cde54-113">Successfully attached to the process on the remote machine.</span></span>  
  
 <span data-ttu-id="cde54-114">E_FAIL (またはその他の E_ リターン コード)</span><span class="sxs-lookup"><span data-stu-id="cde54-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="cde54-115">リモートコンピューター上のプロセスにアタッチできません。</span><span class="sxs-lookup"><span data-stu-id="cde54-115">Unable to attach to the process on the remote machine.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cde54-116">注釈</span><span class="sxs-lookup"><span data-stu-id="cde54-116">Remarks</span></span>  

 <span data-ttu-id="cde54-117">混合モードのデバッグは、Silverlight ではサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="cde54-117">Mixed-mode debugging is not supported in Silverlight.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cde54-118">要件</span><span class="sxs-lookup"><span data-stu-id="cde54-118">Requirements</span></span>  

 <span data-ttu-id="cde54-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cde54-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cde54-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cde54-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cde54-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cde54-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cde54-122">**.NET Framework のバージョン:** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="cde54-122">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cde54-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="cde54-123">See also</span></span>

- [<span data-ttu-id="cde54-124">ICorDebugRemote インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cde54-124">ICorDebugRemote Interface</span></span>](icordebugremote-interface.md)
- [<span data-ttu-id="cde54-125">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="cde54-125">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="cde54-126">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="cde54-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
