---
title: ICorDebugNativeFrame インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame
helpviewer_keywords:
- ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 04819c58-7246-4b32-befb-680cf1dbc436
topic_type:
- apiref
ms.openlocfilehash: 043dc0fdd5218d7bc6b80428d1eb891b3f01ee8c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695544"
---
# <a name="icordebugnativeframe-interface"></a><span data-ttu-id="080da-102">ICorDebugNativeFrame インターフェイス</span><span class="sxs-lookup"><span data-stu-id="080da-102">ICorDebugNativeFrame Interface</span></span>

<span data-ttu-id="080da-103">ネイティブフレームに使用される、特殊な実装のテキストフレーム。</span><span class="sxs-lookup"><span data-stu-id="080da-103">A specialized implementation of ICorDebugFrame used for native frames.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="080da-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="080da-104">Methods</span></span>  
  
|<span data-ttu-id="080da-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="080da-105">Method</span></span>|<span data-ttu-id="080da-106">説明</span><span class="sxs-lookup"><span data-stu-id="080da-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="080da-107">CanSetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="080da-107">CanSetIP Method</span></span>](icordebugnativeframe-cansetip-method.md)|<span data-ttu-id="080da-108">命令ポインターをネイティブコード内の指定したオフセット位置に安全に設定できるかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="080da-108">Gets a value that indicates whether it is safe to set the instruction pointer to the specified offset location in native code.</span></span>|  
|[<span data-ttu-id="080da-109">GetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="080da-109">GetIP Method</span></span>](icordebugnativeframe-getip-method.md)|<span data-ttu-id="080da-110">ネイティブコードへのスタックフレームのオフセットを取得します。</span><span class="sxs-lookup"><span data-stu-id="080da-110">Gets the stack frame's offset into native code.</span></span>|  
|[<span data-ttu-id="080da-111">GetLocalDoubleRegisterValue メソッド</span><span class="sxs-lookup"><span data-stu-id="080da-111">GetLocalDoubleRegisterValue Method</span></span>](icordebugnativeframe-getlocaldoubleregistervalue-method.md)|<span data-ttu-id="080da-112">ネイティブフレームの2つのメモリレジスタに格納されている引数またはローカル変数の値を表す ICorDebugValue へのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="080da-112">Gets a pointer to an ICorDebugValue that represents the value of an argument or local variable stored in two memory registers of a native frame.</span></span>|  
|[<span data-ttu-id="080da-113">GetLocalMemoryRegisterValue メソッド</span><span class="sxs-lookup"><span data-stu-id="080da-113">GetLocalMemoryRegisterValue Method</span></span>](icordebugnativeframe-getlocalmemoryregistervalue-method.md)|<span data-ttu-id="080da-114">指定した `ICorDebugValue` レジスタに下位ビットが格納されているローカル変数の値を表すへのポインターを取得します。上位ビットは、指定したメモリアドレスに格納されます。</span><span class="sxs-lookup"><span data-stu-id="080da-114">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the low bits are stored in the specified register and the high bits are stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="080da-115">GetLocalMemoryValue メソッド</span><span class="sxs-lookup"><span data-stu-id="080da-115">GetLocalMemoryValue Method</span></span>](icordebugnativeframe-getlocalmemoryvalue-method.md)|<span data-ttu-id="080da-116">`ICorDebugValue`指定したメモリアドレスに格納されているローカル変数の値を表すへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="080da-116">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable stored at the specified memory address.</span></span>|  
|[<span data-ttu-id="080da-117">GetLocalRegisterMemoryValue メソッド</span><span class="sxs-lookup"><span data-stu-id="080da-117">GetLocalRegisterMemoryValue Method</span></span>](icordebugnativeframe-getlocalregistermemoryvalue-method.md)|<span data-ttu-id="080da-118">指定した `ICorDebugValue` レジスタに上位ビットが格納され、下位ビットが指定したメモリアドレスに格納されているローカル変数の値を表すへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="080da-118">Gets a pointer to an `ICorDebugValue` that represents the value of a local variable, of which the high bits are stored in the specified register and the low bits are stored at the specified memory address</span></span>|  
|[<span data-ttu-id="080da-119">GetLocalRegisterValue メソッド</span><span class="sxs-lookup"><span data-stu-id="080da-119">GetLocalRegisterValue Method</span></span>](icordebugnativeframe-getlocalregistervalue-method.md)|<span data-ttu-id="080da-120">`ICorDebugValue`引数の値または指定したネイティブレジスタに格納されているローカル変数を表すへのポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="080da-120">Gets a pointer to an `ICorDebugValue` that represents the value of an argument or a local variable stored in the specified native register.</span></span>|  
|[<span data-ttu-id="080da-121">GetRegisterSet メソッド</span><span class="sxs-lookup"><span data-stu-id="080da-121">GetRegisterSet Method</span></span>](icordebugnativeframe-getregisterset-method.md)|<span data-ttu-id="080da-122">こののレジスタセットを表す、ツール [のセットへ](icordebugregisterset-interface.md) のポインターを取得し `ICorDebugNativeFrame` ます。</span><span class="sxs-lookup"><span data-stu-id="080da-122">Gets a pointer to an [ICorDebugRegisterSet](icordebugregisterset-interface.md) that represents the register set for this `ICorDebugNativeFrame`.</span></span>|  
|[<span data-ttu-id="080da-123">SetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="080da-123">SetIP Method</span></span>](icordebugnativeframe-setip-method.md)|<span data-ttu-id="080da-124">命令ポインターをネイティブコード内の指定されたオフセット位置に設定します。</span><span class="sxs-lookup"><span data-stu-id="080da-124">Sets the instruction pointer to the specified offset location in native code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="080da-125">注釈</span><span class="sxs-lookup"><span data-stu-id="080da-125">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="080da-126">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="080da-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="080da-127">要件</span><span class="sxs-lookup"><span data-stu-id="080da-127">Requirements</span></span>  

 <span data-ttu-id="080da-128">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="080da-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="080da-129">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="080da-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="080da-130">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="080da-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="080da-131">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="080da-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="080da-132">関連項目</span><span class="sxs-lookup"><span data-stu-id="080da-132">See also</span></span>

- [<span data-ttu-id="080da-133">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="080da-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
