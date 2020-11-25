---
title: ICorDebugStaticFieldSymbol インターフェイス
ms.date: 03/30/2017
ms.assetid: c0b93609-631e-4b15-878a-189ede922631
ms.openlocfilehash: fcf3bb61ccd903f2dd375e638814247a98aaf7b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717566"
---
# <a name="icordebugstaticfieldsymbol-interface"></a><span data-ttu-id="8fe41-102">ICorDebugStaticFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8fe41-102">ICorDebugStaticFieldSymbol Interface</span></span>

<span data-ttu-id="8fe41-103">静的フィールドのデバッグ シンボル情報を表します。</span><span class="sxs-lookup"><span data-stu-id="8fe41-103">Represents the debug symbol information for a static field.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8fe41-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="8fe41-104">Methods</span></span>  
  
|<span data-ttu-id="8fe41-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="8fe41-105">Method</span></span>|<span data-ttu-id="8fe41-106">説明</span><span class="sxs-lookup"><span data-stu-id="8fe41-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8fe41-107">GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="8fe41-107">GetAddress Method</span></span>](icordebugstaticfieldsymbol-getaddress-method.md)|<span data-ttu-id="8fe41-108">静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="8fe41-108">Gets the address of the static field.</span></span>|  
|[<span data-ttu-id="8fe41-109">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="8fe41-109">GetName Method</span></span>](icordebugstaticfieldsymbol-getname-method.md)|<span data-ttu-id="8fe41-110">静的フィールドの名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="8fe41-110">Gets the name of the static field.</span></span>|  
|[<span data-ttu-id="8fe41-111">GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="8fe41-111">GetSize Method</span></span>](icordebugstaticfieldsymbol-getsize-method.md)|<span data-ttu-id="8fe41-112">静的フィールドのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="8fe41-112">Gets the size in bytes of the static field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8fe41-113">注釈</span><span class="sxs-lookup"><span data-stu-id="8fe41-113">Remarks</span></span>  

 <span data-ttu-id="8fe41-114">`ICorDebugStaticFieldSymbol` インターフェイスは、静的フィールドのデバッグ シンボル情報を取得するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="8fe41-114">The `ICorDebugStaticFieldSymbol` interface is used to retrieve the debug symbol information for a static field.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8fe41-115">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="8fe41-115">This interface is available with .NET Native only.</span></span> <span data-ttu-id="8fe41-116">.NET ネイティブの外部で ICorDebug シナリオについてこのインターフェイスを実装する場合は、共通言語ランタイムはこのインターフェイスを無視します。</span><span class="sxs-lookup"><span data-stu-id="8fe41-116">If you implement this interface for ICorDebug scenarios outside of .NET Native, the common language runtime will ignore this interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fe41-117">要件</span><span class="sxs-lookup"><span data-stu-id="8fe41-117">Requirements</span></span>  

 <span data-ttu-id="8fe41-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8fe41-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fe41-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8fe41-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8fe41-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8fe41-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fe41-121">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fe41-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fe41-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="8fe41-122">See also</span></span>

- [<span data-ttu-id="8fe41-123">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="8fe41-123">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="8fe41-124">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="8fe41-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="8fe41-125">デバッグ</span><span class="sxs-lookup"><span data-stu-id="8fe41-125">Debugging</span></span>](index.md)
