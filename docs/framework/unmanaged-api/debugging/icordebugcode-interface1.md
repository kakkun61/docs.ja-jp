---
title: ICorDebugCode インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode
helpviewer_keywords:
- ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7bd14fb6-8b54-4484-a891-e3c21859c019
topic_type:
- apiref
ms.openlocfilehash: 03cbc1a598ba6c0166f72ff404c239763956c996
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687607"
---
# <a name="icordebugcode-interface"></a><span data-ttu-id="a4e41-102">ICorDebugCode インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4e41-102">ICorDebugCode Interface</span></span>

<span data-ttu-id="a4e41-103">Microsoft Intermediate Language (MSIL) コードまたはネイティブ コードのセグメントを表します。</span><span class="sxs-lookup"><span data-stu-id="a4e41-103">Represents a segment of either Microsoft intermediate language (MSIL) code or native code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a4e41-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="a4e41-104">Methods</span></span>  
  
|<span data-ttu-id="a4e41-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="a4e41-105">Method</span></span>|<span data-ttu-id="a4e41-106">説明</span><span class="sxs-lookup"><span data-stu-id="a4e41-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a4e41-107">CreateBreakpoint メソッド</span><span class="sxs-lookup"><span data-stu-id="a4e41-107">CreateBreakpoint Method</span></span>](icordebugcode-createbreakpoint-method.md)|<span data-ttu-id="a4e41-108">指定したオフセット位置にブレークポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="a4e41-108">Creates a breakpoint at the specified offset.</span></span>|  
|[<span data-ttu-id="a4e41-109">GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="a4e41-109">GetAddress Method</span></span>](icordebugcode-getaddress-method.md)|<span data-ttu-id="a4e41-110">この `ICorDebugCode` が表すコード セグメントの RVA (Relative Virtual Address) を取得します。</span><span class="sxs-lookup"><span data-stu-id="a4e41-110">Gets the relative virtual address (RVA) of the code segment that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="a4e41-111">GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="a4e41-111">GetCode Method</span></span>](icordebugcode-getcode-method.md)|<span data-ttu-id="a4e41-112">指定した関数のすべてのコードを取得し、逆アセンブリ用に書式設定します。</span><span class="sxs-lookup"><span data-stu-id="a4e41-112">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="a4e41-113">このメソッドは非推奨とされました。代わりに [ICorDebugCode2:: GetCodeChunks](icordebugcode2-getcodechunks-method.md) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="a4e41-113">This method has been deprecated; use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>|  
|[<span data-ttu-id="a4e41-114">GetEnCRemapSequencePoints メソッド</span><span class="sxs-lookup"><span data-stu-id="a4e41-114">GetEnCRemapSequencePoints Method</span></span>](icordebugcode-getencremapsequencepoints-method.md)|<span data-ttu-id="a4e41-115">実装されていません。</span><span class="sxs-lookup"><span data-stu-id="a4e41-115">Not implemented.</span></span>|  
|[<span data-ttu-id="a4e41-116">GetFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="a4e41-116">GetFunction Method</span></span>](icordebugcode-getfunction-method.md)|<span data-ttu-id="a4e41-117">このに関連付けられている "の関数" を取得し `ICorDebugCode` ます。</span><span class="sxs-lookup"><span data-stu-id="a4e41-117">Gets the "ICorDebugFunction" associated with this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="a4e41-118">GetILToNativeMapping メソッド</span><span class="sxs-lookup"><span data-stu-id="a4e41-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)|<span data-ttu-id="a4e41-119">MSIL オフセットからネイティブオフセットへのマッピングを表す "COR_DEBUG_IL_TO_NATIVE_MAP" インスタンスの配列を取得します。</span><span class="sxs-lookup"><span data-stu-id="a4e41-119">Gets an array of "COR_DEBUG_IL_TO_NATIVE_MAP" instances that represent mappings from MSIL offsets to native offsets.</span></span>|  
|[<span data-ttu-id="a4e41-120">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="a4e41-120">GetSize Method</span></span>](icordebugcode-getsize-method.md)|<span data-ttu-id="a4e41-121">この `ICorDebugCode` で表されるバイナリ コードのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="a4e41-121">Gets the size, in bytes, of the binary code represented by this `ICorDebugCode`.</span></span>|  
|[<span data-ttu-id="a4e41-122">GetVersionNumber メソッド</span><span class="sxs-lookup"><span data-stu-id="a4e41-122">GetVersionNumber Method</span></span>](icordebugcode-getversionnumber-method.md)|<span data-ttu-id="a4e41-123">この `ICorDebugCode` が表すコードのバージョンを識別する、1 から始まる数字を取得します。</span><span class="sxs-lookup"><span data-stu-id="a4e41-123">Gets the one-based number that identifies the version of the code that this `ICorDebugCode` represents.</span></span>|  
|[<span data-ttu-id="a4e41-124">IsIL メソッド</span><span class="sxs-lookup"><span data-stu-id="a4e41-124">IsIL Method</span></span>](icordebugcode-isil-method.md)|<span data-ttu-id="a4e41-125">この `ICorDebugCode` が MSIL でコンパイルされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="a4e41-125">Gets a value that indicates whether this `ICorDebugCode` is compiled in MSIL.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4e41-126">注釈</span><span class="sxs-lookup"><span data-stu-id="a4e41-126">Remarks</span></span>  

 <span data-ttu-id="a4e41-127">`ICorDebugCode` は、MSIL またはネイティブ コードを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="a4e41-127">`ICorDebugCode` can represent either MSIL or native code.</span></span> <span data-ttu-id="a4e41-128">MSIL コードを表す "の関数" オブジェクトは、0個または1個 `ICorDebugCode` のオブジェクトを関連付けることができます。</span><span class="sxs-lookup"><span data-stu-id="a4e41-128">An "ICorDebugFunction" object that represents MSIL code can have either zero or one `ICorDebugCode` objects associated with it.</span></span> <span data-ttu-id="a4e41-129">ネイティブコードを表す "表示関数" オブジェクトには、任意の数のオブジェクトを関連付けることができ `ICorDebugCode` ます。</span><span class="sxs-lookup"><span data-stu-id="a4e41-129">An "ICorDebugFunction" object that represents native code can have any number of `ICorDebugCode` objects associated with it.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4e41-130">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="a4e41-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4e41-131">要件</span><span class="sxs-lookup"><span data-stu-id="a4e41-131">Requirements</span></span>  

 <span data-ttu-id="a4e41-132">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4e41-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a4e41-133">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a4e41-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a4e41-134">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a4e41-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a4e41-135">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a4e41-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4e41-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4e41-136">See also</span></span>

- [<span data-ttu-id="a4e41-137">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4e41-137">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="a4e41-138">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="a4e41-138">Debugging Interfaces</span></span>](debugging-interfaces.md)
