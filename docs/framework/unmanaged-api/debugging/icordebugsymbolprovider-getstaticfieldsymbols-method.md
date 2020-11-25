---
title: ICorDebugSymbolProvider::GetStaticFieldSymbols メソッド
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
ms.openlocfilehash: 09e68c751da6500c5580f4945e8dd1c486a09217
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698664"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="17cb1-102">ICorDebugSymbolProvider::GetStaticFieldSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="17cb1-102">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>

<span data-ttu-id="17cb1-103">typespec シグネチャに対応する静的フィールド シンボルを取得します。</span><span class="sxs-lookup"><span data-stu-id="17cb1-103">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17cb1-104">構文</span><span class="sxs-lookup"><span data-stu-id="17cb1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17cb1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="17cb1-105">Parameters</span></span>  

 `cbSignature`  
 <span data-ttu-id="17cb1-106">[in] `typeSig` 配列のバイト数。</span><span class="sxs-lookup"><span data-stu-id="17cb1-106">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="17cb1-107">[in] `typespec` シグネチャを格納するバイト配列。</span><span class="sxs-lookup"><span data-stu-id="17cb1-107">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="17cb1-108">[in] 要求されるシンボルの数。</span><span class="sxs-lookup"><span data-stu-id="17cb1-108">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="17cb1-109">[out] メソッドによって取得されたシンボル数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="17cb1-109">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="17cb1-110">入出力要求された静的なフィールドシンボルが格納されている、表示名のある [シンボル](icordebugstaticfieldsymbol-interface.md) 配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="17cb1-110">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17cb1-111">注釈</span><span class="sxs-lookup"><span data-stu-id="17cb1-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17cb1-112">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="17cb1-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17cb1-113">要件</span><span class="sxs-lookup"><span data-stu-id="17cb1-113">Requirements</span></span>  

 <span data-ttu-id="17cb1-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="17cb1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17cb1-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17cb1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17cb1-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17cb1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17cb1-117">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17cb1-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17cb1-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="17cb1-118">See also</span></span>

- [<span data-ttu-id="17cb1-119">GetInstanceFieldSymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="17cb1-119">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="17cb1-120">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="17cb1-120">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="17cb1-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="17cb1-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
