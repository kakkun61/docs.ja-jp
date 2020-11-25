---
title: ICorDebugILFrame インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame
helpviewer_keywords:
- ICorDebugILFrame interface [.NET Framework debugging]
ms.assetid: d5cf5056-da4d-4629-914d-afe42a5393df
topic_type:
- apiref
ms.openlocfilehash: 4f34fdf9a0eeb47e027cc874afee5bd04f5bd9bc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95712392"
---
# <a name="icordebugilframe-interface"></a><span data-ttu-id="05d68-102">ICorDebugILFrame インターフェイス</span><span class="sxs-lookup"><span data-stu-id="05d68-102">ICorDebugILFrame Interface</span></span>

<span data-ttu-id="05d68-103">Microsoft 中間言語 (MSIL) コードのスタックフレームを表します。</span><span class="sxs-lookup"><span data-stu-id="05d68-103">Represents a stack frame of Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="05d68-104">このインターフェイスは、テキストボックスのインターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="05d68-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="05d68-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="05d68-105">Methods</span></span>  
  
|<span data-ttu-id="05d68-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="05d68-106">Method</span></span>|<span data-ttu-id="05d68-107">説明</span><span class="sxs-lookup"><span data-stu-id="05d68-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="05d68-108">CanSetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="05d68-108">CanSetIP Method</span></span>](icordebugilframe-cansetip-method.md)|<span data-ttu-id="05d68-109">命令ポインターを指定したオフセット位置に安全に設定できるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="05d68-109">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location.</span></span>|  
|[<span data-ttu-id="05d68-110">EnumerateArguments メソッド</span><span class="sxs-lookup"><span data-stu-id="05d68-110">EnumerateArguments Method</span></span>](icordebugilframe-enumeratearguments-method.md)|<span data-ttu-id="05d68-111">このフレーム内の引数の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="05d68-111">Gets an enumerator for the arguments in this frame.</span></span>|  
|[<span data-ttu-id="05d68-112">EnumerateLocalVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="05d68-112">EnumerateLocalVariables Method</span></span>](icordebugilframe-enumeratelocalvariables-method.md)|<span data-ttu-id="05d68-113">このフレーム内のローカル変数の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="05d68-113">Gets an enumerator for the local variables in this frame.</span></span>|  
|[<span data-ttu-id="05d68-114">GetArgument メソッド</span><span class="sxs-lookup"><span data-stu-id="05d68-114">GetArgument Method</span></span>](icordebugilframe-getargument-method.md)|<span data-ttu-id="05d68-115">この MSIL スタックフレーム内の指定された引数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="05d68-115">Gets the value of the specified argument in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="05d68-116">GetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="05d68-116">GetIP Method</span></span>](icordebugilframe-getip-method.md)|<span data-ttu-id="05d68-117">命令ポインターの値と、命令ポインターの値が取得された方法を示すビットごとの組み合わせ値を取得します。</span><span class="sxs-lookup"><span data-stu-id="05d68-117">Gets the value of the instruction pointer and a bitwise combination value that describes how the value of the instruction pointer was obtained.</span></span>|  
|[<span data-ttu-id="05d68-118">GetLocalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="05d68-118">GetLocalVariable Method</span></span>](icordebugilframe-getlocalvariable-method.md)|<span data-ttu-id="05d68-119">この MSIL スタックフレーム内の指定したローカル変数の値を取得します。</span><span class="sxs-lookup"><span data-stu-id="05d68-119">Gets the value of the specified local variable in this MSIL stack frame.</span></span>|  
|[<span data-ttu-id="05d68-120">GetStackDepth メソッド</span><span class="sxs-lookup"><span data-stu-id="05d68-120">GetStackDepth Method</span></span>](icordebugilframe-getstackdepth-method.md)|<span data-ttu-id="05d68-121">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="05d68-121">Not implemented.</span></span>|  
|[<span data-ttu-id="05d68-122">GetStackValue メソッド</span><span class="sxs-lookup"><span data-stu-id="05d68-122">GetStackValue Method</span></span>](icordebugilframe-getstackvalue-method.md)|<span data-ttu-id="05d68-123">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="05d68-123">Not implemented.</span></span>|  
|[<span data-ttu-id="05d68-124">SetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="05d68-124">SetIP Method</span></span>](icordebugilframe-setip-method.md)|<span data-ttu-id="05d68-125">命令ポインターを MSIL コード内の指定したオフセット位置に設定します。</span><span class="sxs-lookup"><span data-stu-id="05d68-125">Sets the instruction pointer to the specified offset location in the MSIL code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05d68-126">注釈</span><span class="sxs-lookup"><span data-stu-id="05d68-126">Remarks</span></span>  

 <span data-ttu-id="05d68-127">インターフェイスは、 `ICorDebugILFrame` 特別なテキストフレームインターフェイスです。</span><span class="sxs-lookup"><span data-stu-id="05d68-127">The `ICorDebugILFrame` interface is a specialized ICorDebugFrame interface.</span></span> <span data-ttu-id="05d68-128">これは、MSIL コードフレームまたは just-in-time (JIT) コンパイルフレームに対して使用されます。</span><span class="sxs-lookup"><span data-stu-id="05d68-128">It is used either for MSIL code frames or for just-in-time (JIT) compiled frames.</span></span> <span data-ttu-id="05d68-129">JIT でコンパイルされたフレームは、 `ICorDebugILFrame` インターフェイスとの両方のフレームインターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="05d68-129">The JIT-compiled frames implement both the `ICorDebugILFrame` interface and the ICorDebugNativeFrame interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05d68-130">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="05d68-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05d68-131">要件</span><span class="sxs-lookup"><span data-stu-id="05d68-131">Requirements</span></span>  

 <span data-ttu-id="05d68-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="05d68-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="05d68-133">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="05d68-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="05d68-134">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="05d68-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="05d68-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="05d68-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05d68-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="05d68-136">See also</span></span>

- [<span data-ttu-id="05d68-137">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="05d68-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
