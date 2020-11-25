---
title: ICorDebugThread::GetUserState メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type:
- apiref
ms.openlocfilehash: dd3936656ce1c9482b7f07a5780fcf651356b4be
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727966"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="bbfe4-102">ICorDebugThread::GetUserState メソッド</span><span class="sxs-lookup"><span data-stu-id="bbfe4-102">ICorDebugThread::GetUserState Method</span></span>

<span data-ttu-id="bbfe4-103">このスレッドの現在のユーザー状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="bbfe4-103">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbfe4-104">構文</span><span class="sxs-lookup"><span data-stu-id="bbfe4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbfe4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bbfe4-105">Parameters</span></span>  

 `pState`  
 <span data-ttu-id="bbfe4-106">入出力このスレッドの現在のユーザー状態を示す CorDebugUserState 列挙値のビットごとの組み合わせへのポインター。</span><span class="sxs-lookup"><span data-stu-id="bbfe4-106">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbfe4-107">注釈</span><span class="sxs-lookup"><span data-stu-id="bbfe4-107">Remarks</span></span>  

 <span data-ttu-id="bbfe4-108">スレッドのユーザー状態は、デバッグ中のプログラムによって検査されるときのスレッドの状態です。</span><span class="sxs-lookup"><span data-stu-id="bbfe4-108">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="bbfe4-109">スレッドに複数の状態ビットが設定されている可能性があります。</span><span class="sxs-lookup"><span data-stu-id="bbfe4-109">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbfe4-110">要件</span><span class="sxs-lookup"><span data-stu-id="bbfe4-110">Requirements</span></span>  

 <span data-ttu-id="bbfe4-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbfe4-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbfe4-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bbfe4-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbfe4-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbfe4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbfe4-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbfe4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
