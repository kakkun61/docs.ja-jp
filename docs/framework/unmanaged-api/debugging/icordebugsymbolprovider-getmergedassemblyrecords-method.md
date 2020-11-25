---
title: ICorDebugSymbolProvider::GetMergedAssemblyRecords メソッド
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: 10bbcf2e6a536eeb4ab8141c10c177a53faa1c95
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730878"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="3bf63-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords メソッド</span><span class="sxs-lookup"><span data-stu-id="3bf63-102">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>

<span data-ttu-id="3bf63-103">すべてのマージされたアセンブリのシンボル レコードを取得します。</span><span class="sxs-lookup"><span data-stu-id="3bf63-103">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bf63-104">構文</span><span class="sxs-lookup"><span data-stu-id="3bf63-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3bf63-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3bf63-105">Parameters</span></span>  

 `cRequestedRecords`  
 <span data-ttu-id="3bf63-106">[in] 要求されるシンボル レコードの数。</span><span class="sxs-lookup"><span data-stu-id="3bf63-106">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="3bf63-107">[out] メソッドによって取得されたシンボル レコード数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="3bf63-107">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="3bf63-108">[ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md)オブジェクトの配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="3bf63-108">A pointer to an array of [ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3bf63-109">注釈</span><span class="sxs-lookup"><span data-stu-id="3bf63-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3bf63-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3bf63-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3bf63-111">要件</span><span class="sxs-lookup"><span data-stu-id="3bf63-111">Requirements</span></span>  

 <span data-ttu-id="3bf63-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3bf63-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bf63-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3bf63-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3bf63-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3bf63-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3bf63-115">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bf63-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bf63-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="3bf63-116">See also</span></span>

- [<span data-ttu-id="3bf63-117">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3bf63-117">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="3bf63-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3bf63-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
