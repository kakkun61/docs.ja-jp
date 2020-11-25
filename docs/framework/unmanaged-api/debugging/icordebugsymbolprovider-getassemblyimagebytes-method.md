---
title: ICorDebugSymbolProvider::GetAssemblyImageBytes メソッド
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: b52614065d599edf8e556524c33e8bc50b4924ef
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709181"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="bab10-102">ICorDebugSymbolProvider::GetAssemblyImageBytes メソッド</span><span class="sxs-lookup"><span data-stu-id="bab10-102">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>

<span data-ttu-id="bab10-103">マージされたアセンブリ内の指定の相対仮想アドレス (RVA: relative virtual address) で、マージされたアセンブリのデータを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="bab10-103">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bab10-104">構文</span><span class="sxs-lookup"><span data-stu-id="bab10-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bab10-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bab10-105">Parameters</span></span>  

 `rva`  
 <span data-ttu-id="bab10-106">[in] マージされたアセンブリ内の相対仮想アドレス (RVA)。</span><span class="sxs-lookup"><span data-stu-id="bab10-106">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="bab10-107">マージされたアセンブリから読み取るバイト数。</span><span class="sxs-lookup"><span data-stu-id="bab10-107">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="bab10-108">マージされたアセンブリメタデータを持つメモリバッファーに関する情報を格納している、 [のオブジェクトの](icordebugmemorybuffer-interface.md) アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="bab10-108">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bab10-109">注釈</span><span class="sxs-lookup"><span data-stu-id="bab10-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bab10-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="bab10-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bab10-111">要件</span><span class="sxs-lookup"><span data-stu-id="bab10-111">Requirements</span></span>  

 <span data-ttu-id="bab10-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bab10-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bab10-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bab10-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bab10-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bab10-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bab10-115">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bab10-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bab10-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="bab10-116">See also</span></span>

- [<span data-ttu-id="bab10-117">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bab10-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="bab10-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="bab10-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
