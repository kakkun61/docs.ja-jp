---
title: ICorDebugILFrame::GetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugILFrame interface [.NET Framework debugging]
- ICorDebugILFrame::GetIP method [.NET Framework debugging]
ms.assetid: 18217ba1-1776-4297-a3b9-f77e64b0fead
topic_type:
- apiref
ms.openlocfilehash: 314d2a06c8e246a42b315690dc9fe4b507db285a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703175"
---
# <a name="icordebugilframegetip-method"></a><span data-ttu-id="0fe07-102">ICorDebugILFrame::GetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="0fe07-102">ICorDebugILFrame::GetIP Method</span></span>

<span data-ttu-id="0fe07-103">命令ポインターの値と、命令ポインターの値が取得された方法を示すビットごとの組み合わせ値を取得します。</span><span class="sxs-lookup"><span data-stu-id="0fe07-103">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fe07-104">構文</span><span class="sxs-lookup"><span data-stu-id="0fe07-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32               *pnOffset,
    [out] CorDebugMappingResult *pMappingResult  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fe07-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0fe07-105">Parameters</span></span>  

 `pnOffset`  
 <span data-ttu-id="0fe07-106">入出力命令ポインターの値。</span><span class="sxs-lookup"><span data-stu-id="0fe07-106">[out] The value of the instruction pointer.</span></span>  
  
 `pMappingResult`  
 <span data-ttu-id="0fe07-107">入出力命令ポインターの値の取得方法を示す CorDebugMappingResult 列挙値のビットごとの組み合わせへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0fe07-107">[out] A pointer to a bitwise combination of the CorDebugMappingResult enumeration values that describe how the value of the instruction pointer was obtained.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fe07-108">注釈</span><span class="sxs-lookup"><span data-stu-id="0fe07-108">Remarks</span></span>  

 <span data-ttu-id="0fe07-109">命令ポインターの値は、関数の MSIL (Microsoft 中間言語) コードへのスタックフレームのオフセットです。</span><span class="sxs-lookup"><span data-stu-id="0fe07-109">The value of the instruction pointer is the stack frame's offset into the function's Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="0fe07-110">スタックフレームがアクティブな場合、このアドレスは次に実行する命令になります。</span><span class="sxs-lookup"><span data-stu-id="0fe07-110">If the stack frame is active, this address is the next instruction to execute.</span></span> <span data-ttu-id="0fe07-111">スタックフレームがアクティブでない場合、このアドレスはスタックフレームが再アクティブ化されたときに次に実行される命令になります。</span><span class="sxs-lookup"><span data-stu-id="0fe07-111">If the stack frame is not active, this address is the next instruction to execute when the stack frame is reactivated.</span></span>  
  
 <span data-ttu-id="0fe07-112">このフレームが just-in-time (JIT) でコンパイルされたフレームである場合、命令ポインターの値は、実際のネイティブ命令ポインターから逆方向にマッピングすることによって決定されます。したがって、値は概数にすぎない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0fe07-112">If this frame is a just-in-time (JIT) compiled frame, the value of the instruction pointer will be determined by mapping backwards from the actual native instruction pointer, so the value may be only approximate.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fe07-113">要件</span><span class="sxs-lookup"><span data-stu-id="0fe07-113">Requirements</span></span>  

 <span data-ttu-id="0fe07-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0fe07-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fe07-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0fe07-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0fe07-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fe07-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fe07-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fe07-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
