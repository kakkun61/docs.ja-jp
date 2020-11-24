---
title: ICorDebugAssembly3 インターフェイス
ms.date: 03/30/2017
ms.assetid: 17fc5d76-75a9-4933-83f0-594de7f973f3
ms.openlocfilehash: 0260267a05a880fbb3ac48325e55deff326f5f87
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688368"
---
# <a name="icordebugassembly3-interface"></a><span data-ttu-id="0a0c5-102">ICorDebugAssembly3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a0c5-102">ICorDebugAssembly3 Interface</span></span>

<span data-ttu-id="0a0c5-103">コンテナーのアセンブリとそれらに含まれるアセンブリのサポートを提供するために、ICorDebugAssembly インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="0a0c5-103">Logically extends the ICorDebugAssembly interface to provide support for container assemblies and their contained assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0a0c5-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="0a0c5-104">Methods</span></span>  
  
|<span data-ttu-id="0a0c5-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="0a0c5-105">Method</span></span>|<span data-ttu-id="0a0c5-106">説明</span><span class="sxs-lookup"><span data-stu-id="0a0c5-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0a0c5-107">EnumerateContainedAssemblies メソッド</span><span class="sxs-lookup"><span data-stu-id="0a0c5-107">EnumerateContainedAssemblies Method</span></span>](icordebugassembly3-enumeratecontainedassemblies-method.md)|<span data-ttu-id="0a0c5-108">このアセンブリに含まれているアセンブリの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="0a0c5-108">Gets an enumerator for the assemblies contained in this assembly.</span></span>|  
|[<span data-ttu-id="0a0c5-109">GetContainerAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="0a0c5-109">GetContainerAssembly Method</span></span>](icordebugassembly3-getcontainerassembly-method.md)|<span data-ttu-id="0a0c5-110">この `ICorDebugAssembly3` オブジェクトのコンテナー アセンブリを返します。</span><span class="sxs-lookup"><span data-stu-id="0a0c5-110">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a0c5-111">注釈</span><span class="sxs-lookup"><span data-stu-id="0a0c5-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0a0c5-112">このインターフェイスは .NET ネイティブでのみ使用可能です。</span><span class="sxs-lookup"><span data-stu-id="0a0c5-112">The interface is available with .NET Native only.</span></span> <span data-ttu-id="0a0c5-113">インターフェイス ポインターを取得するために `QueryInterface` を呼び出そうとすると、.NET ネイティブ外の ICorDebug シナリオに対して `E_NOINTERFACE` が返されます。</span><span class="sxs-lookup"><span data-stu-id="0a0c5-113">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0a0c5-114">要件</span><span class="sxs-lookup"><span data-stu-id="0a0c5-114">Requirements</span></span>  

 <span data-ttu-id="0a0c5-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a0c5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0a0c5-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0a0c5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0a0c5-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0a0c5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0a0c5-118">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0a0c5-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a0c5-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a0c5-119">See also</span></span>

- [<span data-ttu-id="0a0c5-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="0a0c5-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="0a0c5-121">デバッグ</span><span class="sxs-lookup"><span data-stu-id="0a0c5-121">Debugging</span></span>](index.md)
