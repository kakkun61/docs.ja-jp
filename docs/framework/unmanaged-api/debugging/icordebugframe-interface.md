---
title: ICorDebugFrame インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame
helpviewer_keywords:
- ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 0c48f764-3c64-4602-b2f4-4ffc60eb2c65
topic_type:
- apiref
ms.openlocfilehash: bdc17e2c6c63deae1420fe738eac51153f6b368e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726341"
---
# <a name="icordebugframe-interface"></a><span data-ttu-id="c3028-102">ICorDebugFrame インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c3028-102">ICorDebugFrame Interface</span></span>

<span data-ttu-id="c3028-103">現在のスタックのフレームを表します。</span><span class="sxs-lookup"><span data-stu-id="c3028-103">Represents a frame on the current stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c3028-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="c3028-104">Methods</span></span>  
  
|<span data-ttu-id="c3028-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c3028-105">Method</span></span>|<span data-ttu-id="c3028-106">説明</span><span class="sxs-lookup"><span data-stu-id="c3028-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c3028-107">CreateStepper メソッド</span><span class="sxs-lookup"><span data-stu-id="c3028-107">CreateStepper Method</span></span>](icordebugframe-createstepper-method.md)|<span data-ttu-id="c3028-108">このに対して相対的なステップ実行操作を実行する ICorDebugStepper を取得し `ICorDebugFrame` ます。</span><span class="sxs-lookup"><span data-stu-id="c3028-108">Gets an ICorDebugStepper to perform stepping operations relative to this `ICorDebugFrame`.</span></span>|  
|[<span data-ttu-id="c3028-109">GetCallee メソッド</span><span class="sxs-lookup"><span data-stu-id="c3028-109">GetCallee Method</span></span>](icordebugframe-getcallee-method.md)|<span data-ttu-id="c3028-110">このフレームが呼び出された現在のチェーン内のへのポインターを取得し `ICorDebugFrame` ます。または、このがチェーン内の最も内側のフレームである場合は null を返します。</span><span class="sxs-lookup"><span data-stu-id="c3028-110">Gets a pointer to the `ICorDebugFrame` in the current chain that this frame called, or returns null if this is the innermost frame in the chain.</span></span>|  
|[<span data-ttu-id="c3028-111">GetCaller メソッド</span><span class="sxs-lookup"><span data-stu-id="c3028-111">GetCaller Method</span></span>](icordebugframe-getcaller-method.md)|<span data-ttu-id="c3028-112">このフレームを呼び出した現在のチェーン内のへのポインターを取得し `ICorDebugFrame` ます。これがチェーンの最も外側のフレームである場合は null を返します。</span><span class="sxs-lookup"><span data-stu-id="c3028-112">Gets a pointer to the `ICorDebugFrame` in the current chain that called this frame, or returns null if this is the outermost frame in the chain.</span></span>|  
|[<span data-ttu-id="c3028-113">GetChain メソッド</span><span class="sxs-lookup"><span data-stu-id="c3028-113">GetChain Method</span></span>](icordebugframe-getchain-method.md)|<span data-ttu-id="c3028-114">このが含まれている、ツールチェーンへのポインターを取得し `ICorDebugFrame` ます。</span><span class="sxs-lookup"><span data-stu-id="c3028-114">Gets a pointer to the ICorDebugChain this `ICorDebugFrame` is a part of.</span></span>|  
|[<span data-ttu-id="c3028-115">GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="c3028-115">GetCode Method</span></span>](icordebugframe-getcode-method.md)|<span data-ttu-id="c3028-116">このスタックフレームに関連付けられているテキストコードへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c3028-116">Gets a pointer to the ICorDebugCode associated with this stack frame.</span></span>|  
|[<span data-ttu-id="c3028-117">GetFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="c3028-117">GetFunction Method</span></span>](icordebugframe-getfunction-method.md)|<span data-ttu-id="c3028-118">このスタックフレームに関連付けられているコードを格納しているコードを指すポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="c3028-118">Gets a pointer to the ICorDebugFunction that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="c3028-119">GetFunctionToken メソッド</span><span class="sxs-lookup"><span data-stu-id="c3028-119">GetFunctionToken Method</span></span>](icordebugframe-getfunctiontoken-method.md)|<span data-ttu-id="c3028-120">このスタックフレームに関連付けられているコードを含む関数のメタデータトークンを取得します。</span><span class="sxs-lookup"><span data-stu-id="c3028-120">Gets the metadata token for the function that contains the code associated with this stack frame.</span></span>|  
|[<span data-ttu-id="c3028-121">GetStackRange メソッド</span><span class="sxs-lookup"><span data-stu-id="c3028-121">GetStackRange Method</span></span>](icordebugframe-getstackrange-method.md)|<span data-ttu-id="c3028-122">このによって表されるスタックフレームの絶対アドレス範囲を取得し `ICorDebugFrame` ます。</span><span class="sxs-lookup"><span data-stu-id="c3028-122">Gets the absolute address range of the stack frame represented by this `ICorDebugFrame`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c3028-123">注釈</span><span class="sxs-lookup"><span data-stu-id="c3028-123">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c3028-124">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="c3028-124">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3028-125">要件</span><span class="sxs-lookup"><span data-stu-id="c3028-125">Requirements</span></span>  

 <span data-ttu-id="c3028-126">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c3028-126">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3028-127">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3028-127">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3028-128">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3028-128">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3028-129">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3028-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3028-130">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3028-130">See also</span></span>

- [<span data-ttu-id="c3028-131">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c3028-131">Debugging Interfaces</span></span>](debugging-interfaces.md)
