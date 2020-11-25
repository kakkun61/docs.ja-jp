---
title: ICorDebugLoadedModule インターフェイス
ms.date: 03/30/2017
ms.assetid: 34be6369-2e75-4a95-a538-3b29ac97cf6d
ms.openlocfilehash: 6087411e8d23a9c3c97cb97ac8159d436e24759b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731830"
---
# <a name="icordebugloadedmodule-interface"></a><span data-ttu-id="ef84a-102">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ef84a-102">ICorDebugLoadedModule Interface</span></span>

<span data-ttu-id="ef84a-103">読み込まれたモジュールについての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="ef84a-103">Provides information about a loaded module.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ef84a-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="ef84a-104">Methods</span></span>  
  
|<span data-ttu-id="ef84a-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="ef84a-105">Method</span></span>|<span data-ttu-id="ef84a-106">説明</span><span class="sxs-lookup"><span data-stu-id="ef84a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ef84a-107">GetBaseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="ef84a-107">GetBaseAddress Method</span></span>](icordebugloadedmodule-getbaseaddress-method.md)|<span data-ttu-id="ef84a-108">読み込まれたモジュールのベース アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="ef84a-108">Gets the base address of the loaded module.</span></span>|  
|[<span data-ttu-id="ef84a-109">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="ef84a-109">GetName Method</span></span>](icordebugloadedmodule-getname-method.md)|<span data-ttu-id="ef84a-110">読み込まれたモジュールの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="ef84a-110">Gets the name of the loaded module.</span></span>|  
|[<span data-ttu-id="ef84a-111">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="ef84a-111">GetSize Method</span></span>](icordebugloadedmodule-getsize-method.md)|<span data-ttu-id="ef84a-112">読み込まれたモジュールのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="ef84a-112">Gets the size in bytes of the loaded module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ef84a-113">注釈</span><span class="sxs-lookup"><span data-stu-id="ef84a-113">Remarks</span></span>  

 <span data-ttu-id="ef84a-114">`ICorDebugLoadedModule` インターフェイスはデバッガーによって実装され、CLR デバッグ インターフェイスが、デバッガーから読み込まれたモジュールに関する情報を取得するために使用します。</span><span class="sxs-lookup"><span data-stu-id="ef84a-114">The `ICorDebugLoadedModule` interface is implemented by a debugger and is used by the CLR debugging interfaces to get information about the loaded module from the debugger.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ef84a-115">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="ef84a-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="ef84a-116">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="ef84a-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ef84a-117">要件</span><span class="sxs-lookup"><span data-stu-id="ef84a-117">Requirements</span></span>  

 <span data-ttu-id="ef84a-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ef84a-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ef84a-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ef84a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ef84a-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ef84a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ef84a-121">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ef84a-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ef84a-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="ef84a-122">See also</span></span>

- [<span data-ttu-id="ef84a-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ef84a-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="ef84a-124">デバッグ</span><span class="sxs-lookup"><span data-stu-id="ef84a-124">Debugging</span></span>](index.md)
