---
title: ICorDebug::CanLaunchOrAttach メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.CanLaunchOrAttach
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::CanLaunchOrAttach
helpviewer_keywords:
- ICorDebug::CanLaunchOrAttach method [.NET Framework debugging]
- CanLaunchOrAttach method [.NET Framework debugging]
ms.assetid: ca7723db-7c07-4cdd-bd92-fba34928b623
topic_type:
- apiref
ms.openlocfilehash: 195c7e1e7c61fd6ac8a21226b52e3782d2f7e421
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723494"
---
# <a name="icordebugcanlaunchorattach-method"></a><span data-ttu-id="02a6d-102">ICorDebug::CanLaunchOrAttach メソッド</span><span class="sxs-lookup"><span data-stu-id="02a6d-102">ICorDebug::CanLaunchOrAttach Method</span></span>

<span data-ttu-id="02a6d-103">現在のコンピューターおよびランタイム構成のコンテキスト内で、新しいプロセスを起動するか、指定した既存のプロセスにアタッチするかを示す HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="02a6d-103">Returns an HRESULT that indicates whether launching a new process or attaching to the specified existing process is possible within the context of the current machine and runtime configuration.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02a6d-104">構文</span><span class="sxs-lookup"><span data-stu-id="02a6d-104">Syntax</span></span>  
  
```cpp  
HRESULT CanLaunchOrAttach (  
    [in] DWORD      dwProcessId,  
    [in] BOOL       win32DebuggingEnabled  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02a6d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="02a6d-105">Parameters</span></span>  

 `dwProcessId`  
 <span data-ttu-id="02a6d-106">から既存のプロセスの ID。</span><span class="sxs-lookup"><span data-stu-id="02a6d-106">[in] The ID of an existing process.</span></span>  
  
 `win32DebuggingEnabled`  
 <span data-ttu-id="02a6d-107">からWin32 デバッグを有効にして `true` 起動する場合、または win32 デバッグを有効にしてアタッチする場合は、を渡します。それ以外の場合は、を渡し `false` ます。</span><span class="sxs-lookup"><span data-stu-id="02a6d-107">[in] Pass in `true` if you plan to launch with Win32 debugging enabled, or to attach with Win32 debugging enabled; otherwise, pass `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="02a6d-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="02a6d-108">Return Value</span></span>  

 <span data-ttu-id="02a6d-109">現在のコンピューターと実行時の構成に関する情報を指定して、デバッグサービスによって新しいプロセスの起動または特定のプロセスへのアタッチが可能かどうかを判断する場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="02a6d-109">S_OK if the debugging services determine that launching a new process or attaching to the given process is possible, given the information about the current machine and runtime configuration.</span></span> <span data-ttu-id="02a6d-110">使用できる HRESULT 値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="02a6d-110">Possible HRESULT values are:</span></span>  
  
- <span data-ttu-id="02a6d-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="02a6d-111">S_OK</span></span>  
  
- <span data-ttu-id="02a6d-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span><span class="sxs-lookup"><span data-stu-id="02a6d-112">CORDBG_E_DEBUGGING_NOT_POSSIBLE</span></span>  
  
- <span data-ttu-id="02a6d-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span><span class="sxs-lookup"><span data-stu-id="02a6d-113">CORDBG_E_KERNEL_DEBUGGER_PRESENT</span></span>  
  
- <span data-ttu-id="02a6d-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span><span class="sxs-lookup"><span data-stu-id="02a6d-114">CORDBG_E_KERNEL_DEBUGGER_ENABLED</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02a6d-115">注釈</span><span class="sxs-lookup"><span data-stu-id="02a6d-115">Remarks</span></span>  

 <span data-ttu-id="02a6d-116">このメソッドは純粋な情報です。</span><span class="sxs-lookup"><span data-stu-id="02a6d-116">This method is purely informational.</span></span> <span data-ttu-id="02a6d-117">インターフェイスは、によって返される値に関係なく、プロセスの起動やアタッチを停止することはありません `CanLaunchOrAttach` 。</span><span class="sxs-lookup"><span data-stu-id="02a6d-117">The interface will not stop you from launching or attaching to a process, regardless of the value returned by `CanLaunchOrAttach`.</span></span>  
  
 <span data-ttu-id="02a6d-118">Win32 デバッグが有効になっている状態で起動する場合、または Win32 デバッグを有効にしてアタッチする場合は、 `true` にを渡し `win32DebuggingEnabled` ます。</span><span class="sxs-lookup"><span data-stu-id="02a6d-118">If you plan to launch with Win32 debugging enabled or attach with Win32 debugging enabled, pass `true` for `win32DebuggingEnabled`.</span></span> <span data-ttu-id="02a6d-119">このオプションを使用すると、によって返される HRESULT が `CanLaunchOrAttach` 異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="02a6d-119">The HRESULT returned by `CanLaunchOrAttach` might differ if you use this option.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02a6d-120">要件</span><span class="sxs-lookup"><span data-stu-id="02a6d-120">Requirements</span></span>  

 <span data-ttu-id="02a6d-121">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="02a6d-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02a6d-122">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02a6d-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02a6d-123">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02a6d-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02a6d-124">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02a6d-124">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02a6d-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="02a6d-125">See also</span></span>

- [<span data-ttu-id="02a6d-126">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="02a6d-126">ICorDebug Interface</span></span>](icordebug-interface.md)
