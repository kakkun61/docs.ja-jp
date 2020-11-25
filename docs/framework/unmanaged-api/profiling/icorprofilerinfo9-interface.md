---
title: ICorProfilerInfo9 インターフェイス
ms.date: 08/06/2019
author: davmason
ms.author: davmason
ms.openlocfilehash: 3d1cdfa56e6bb20f08370aa76b87d516f7b51cda
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732958"
---
# <a name="icorprofilerinfo9-interface"></a><span data-ttu-id="6dc42-102">ICorProfilerInfo9 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6dc42-102">ICorProfilerInfo9 Interface</span></span>

<span data-ttu-id="6dc42-103">複数のネイティブコードバージョンを持つ関数に関する情報を照会するメソッドを提供する [ICorProfilerInfo8](icorprofilerinfo8-interface.md) のサブクラス。</span><span class="sxs-lookup"><span data-stu-id="6dc42-103">A subclass of [ICorProfilerInfo8](icorprofilerinfo8-interface.md) that provides methods to query information about functions with multiple native code versions.</span></span>  

## <a name="methods"></a><span data-ttu-id="6dc42-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="6dc42-104">Methods</span></span>  

| <span data-ttu-id="6dc42-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="6dc42-105">Method</span></span>|<span data-ttu-id="6dc42-106">説明</span><span class="sxs-lookup"><span data-stu-id="6dc42-106">Description</span></span>|  
| ------------|-----------------|  
|[<span data-ttu-id="6dc42-107">GetNativeCodeStartAddresses メソッド</span><span class="sxs-lookup"><span data-stu-id="6dc42-107">GetNativeCodeStartAddresses Method</span></span>](icorprofilerinfo9-getnativecodestartaddresses-method.md)| <span data-ttu-id="6dc42-108">指定された functionId と rejitId は、現在存在する、このコードのすべての just-in-time バージョンのネイティブコードの開始アドレスを列挙します。</span><span class="sxs-lookup"><span data-stu-id="6dc42-108">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span> |
|[<span data-ttu-id="6dc42-109">GetILToNativeMapping3 メソッド</span><span class="sxs-lookup"><span data-stu-id="6dc42-109">GetILToNativeMapping3 Method</span></span>](icorprofilerinfo9-getiltonativemapping3-method.md)| <span data-ttu-id="6dc42-110">ネイティブコードの開始アドレスが指定されている場合、この just-in-time バージョンのコードのネイティブから IL へのマッピング情報を返します。</span><span class="sxs-lookup"><span data-stu-id="6dc42-110">Given the native code start address, returns the native to IL mapping information for this jitted version of the code.</span></span> |
|[<span data-ttu-id="6dc42-111">GetCodeInfo4 メソッド</span><span class="sxs-lookup"><span data-stu-id="6dc42-111">GetCodeInfo4 Method</span></span>](icorprofilerinfo9-getcodeinfo4-method.md)| <span data-ttu-id="6dc42-112">ネイティブコードの開始アドレスを指定すると、このコードを格納する仮想メモリのブロックが返されます。</span><span class="sxs-lookup"><span data-stu-id="6dc42-112">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span> |

## <a name="requirements"></a><span data-ttu-id="6dc42-113">要件</span><span class="sxs-lookup"><span data-stu-id="6dc42-113">Requirements</span></span>  

<span data-ttu-id="6dc42-114">**プラットフォーム:** 「 [.Net Core でサポートされるオペレーティングシステム](../../../core/install/windows.md?pivots=os-windows)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6dc42-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/windows.md?pivots=os-windows).</span></span>  
<span data-ttu-id="6dc42-115">**ヘッダー** : CorProf.idl、CorProf.h</span><span class="sxs-lookup"><span data-stu-id="6dc42-115">**Header:** CorProf.idl, CorProf.h</span></span>  
<span data-ttu-id="6dc42-116">**.Net のバージョン:**[!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6dc42-116">**.NET Versions:** [!INCLUDE[net_core](../../../../includes/net-core-22-md.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="6dc42-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="6dc42-117">See also</span></span>

- [<span data-ttu-id="6dc42-118">プロファイリングのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="6dc42-118">Profiling Interfaces</span></span>](profiling-interfaces.md)
