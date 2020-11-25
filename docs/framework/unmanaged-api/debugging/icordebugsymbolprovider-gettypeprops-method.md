---
title: ICorDebugSymbolProvider::GetTypeProps メソッド
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: 4738d35aabbc2197c796405e0657607f75ff685d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694504"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="79034-102">ICorDebugSymbolProvider::GetTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="79034-102">ICorDebugSymbolProvider::GetTypeProps Method</span></span>

<span data-ttu-id="79034-103">Vtable の指定の相対仮想アドレス (RVA) における、ジェネリック パラメーターのシグネチャの数などの型のプロパティに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="79034-103">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79034-104">構文</span><span class="sxs-lookup"><span data-stu-id="79034-104">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="79034-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="79034-105">Parameters</span></span>  

 `tableRva`  
 <span data-ttu-id="79034-106">[in] vtable の相対仮想アドレス (RVA)。</span><span class="sxs-lookup"><span data-stu-id="79034-106">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="79034-107">[in] `signature` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="79034-107">[in] The size of the `signature` array.</span></span> <span data-ttu-id="79034-108">「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79034-108">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="79034-109">[out] [out] 返される `signature` 配列のサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="79034-109">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="79034-110">[out] すべてのジェネリック パラメーターの typespec シグネチャを保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="79034-110">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="79034-111">注釈</span><span class="sxs-lookup"><span data-stu-id="79034-111">Remarks</span></span>  

 <span data-ttu-id="79034-112">型の配列の必要なサイズを取得するには `signature` 、 `cbSignature` 引数を0に設定し、 `signature` を **null** に設定します。</span><span class="sxs-lookup"><span data-stu-id="79034-112">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="79034-113">このメソッドから制御が戻ると、`pcbSignature` には `signature` 配列の必要なバイト数が格納されます。</span><span class="sxs-lookup"><span data-stu-id="79034-113">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="79034-114">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="79034-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="79034-115">要件</span><span class="sxs-lookup"><span data-stu-id="79034-115">Requirements</span></span>  

 <span data-ttu-id="79034-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="79034-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="79034-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="79034-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="79034-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="79034-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="79034-119">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="79034-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79034-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="79034-120">See also</span></span>

- [<span data-ttu-id="79034-121">GetMethodProps メソッド</span><span class="sxs-lookup"><span data-stu-id="79034-121">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="79034-122">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="79034-122">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="79034-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="79034-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
