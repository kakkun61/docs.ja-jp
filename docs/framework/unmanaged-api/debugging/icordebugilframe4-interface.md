---
title: ICorDebugILFrame4 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame4
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1e739183-3e05-49e5-846f-4075256e41de
topic_type:
- apiref
ms.openlocfilehash: 7d0f3661c7941c5f2f85fa5b0b67af213de75f05
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724950"
---
# <a name="icordebugilframe4-interface"></a><span data-ttu-id="f9713-102">ICorDebugILFrame4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9713-102">ICorDebugILFrame4 Interface</span></span>

<span data-ttu-id="f9713-103">[.NET Framework 4.5.2 以降のバージョンでのみでサポート]</span><span class="sxs-lookup"><span data-stu-id="f9713-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="f9713-104">ローカル変数にアクセスできるようにするメソッドおよび中間言語 (IL) コードのスタック フレームのコードを提供します。</span><span class="sxs-lookup"><span data-stu-id="f9713-104">Provides methods that allow you to access the local variables and code in a stack frame of intermediate language (IL) code.</span></span> <span data-ttu-id="f9713-105">パラメーターは、プロファイラーの ReJIT インストルメンテーションに追加される変数およびコードへデバッガーがアクセスできるかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="f9713-105">A parameter specifies whether the debugger has access to variables and code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f9713-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="f9713-106">Methods</span></span>  
  
|<span data-ttu-id="f9713-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="f9713-107">Method</span></span>|<span data-ttu-id="f9713-108">説明</span><span class="sxs-lookup"><span data-stu-id="f9713-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f9713-109">EnumerateLocalVariablesEx メソッド</span><span class="sxs-lookup"><span data-stu-id="f9713-109">EnumerateLocalVariablesEx Method</span></span>](icordebugilframe4-enumeratelocalvariablesex-method.md)|<span data-ttu-id="f9713-110">現在のフレームで使用可能なローカル変数の一覧を返します。</span><span class="sxs-lookup"><span data-stu-id="f9713-110">Returns a list of the local variables available in the current frame.</span></span>|  
|[<span data-ttu-id="f9713-111">GetCodeEx メソッド</span><span class="sxs-lookup"><span data-stu-id="f9713-111">GetCodeEx Method</span></span>](icordebugilframe4-getcodeex-method.md)|<span data-ttu-id="f9713-112">このスタック フレームが実行するコードを返します。</span><span class="sxs-lookup"><span data-stu-id="f9713-112">Returns the code that this stack frame is running.</span></span>|  
|[<span data-ttu-id="f9713-113">GetLocalVariableEx メソッド</span><span class="sxs-lookup"><span data-stu-id="f9713-113">GetLocalVariableEx Method</span></span>](icordebugilframe4-getlocalvariableex-method.md)|<span data-ttu-id="f9713-114">IL フレーム内のローカル変数の値を返します。</span><span class="sxs-lookup"><span data-stu-id="f9713-114">Returns the value of a local variable in the IL frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9713-115">注釈</span><span class="sxs-lookup"><span data-stu-id="f9713-115">Remarks</span></span>  

 <span data-ttu-id="f9713-116">これらのメソッドは、 [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md)、 [GetCode](icordebugframe-getcode-method.md)、および [getlocalvariable](icordebugilframe-getlocalvariable-method.md) の各メソッドによって提供される機能に加えて機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="f9713-116">These methods offer functionality in addition to that provided by the [EnumerateLocalVariables](icordebugilframe-enumeratelocalvariables-method.md), [GetCode](icordebugframe-getcode-method.md), and [GetLocalVariable](icordebugilframe-getlocalvariable-method.md) methods.</span></span> <span data-ttu-id="f9713-117">各メソッドには、追加のローカル変数またはプロファイラーの ReJIT 要求によって定義されているコードが参照可能かどうかを指定する `flags` パラメーターが含まれます。</span><span class="sxs-lookup"><span data-stu-id="f9713-117">Each method includes a `flags` parameter that specifies whether additional local variables or code defined by a profiler's ReJIT request are visible.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9713-118">要件</span><span class="sxs-lookup"><span data-stu-id="f9713-118">Requirements</span></span>  

 <span data-ttu-id="f9713-119">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9713-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9713-120">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9713-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9713-121">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9713-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9713-122">**.NET Framework のバージョン:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9713-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9713-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="f9713-123">See also</span></span>

- [<span data-ttu-id="f9713-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="f9713-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="f9713-125">デバッグ</span><span class="sxs-lookup"><span data-stu-id="f9713-125">Debugging</span></span>](index.md)
