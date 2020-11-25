---
title: ICorDebugSymbolProvider::GetMethodProps メソッド
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 5412b2f06445627c1240d6c8f4efb3ce6bbbec54
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730826"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="92c10-102">ICorDebugSymbolProvider::GetMethodProps メソッド</span><span class="sxs-lookup"><span data-stu-id="92c10-102">ICorDebugSymbolProvider::GetMethodProps Method</span></span>

<span data-ttu-id="92c10-103">メソッドの指定の相対仮想アドレス (RVA) で、そのメソッドのプロパティに関する情報 (メソッドのメタデータ トークンなど) と、そのジェネリック パラメーターに関する情報を返します。</span><span class="sxs-lookup"><span data-stu-id="92c10-103">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92c10-104">構文</span><span class="sxs-lookup"><span data-stu-id="92c10-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92c10-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="92c10-105">Parameters</span></span>  

 `codeRVA`  
 <span data-ttu-id="92c10-106">[in]情報を取得するメソッドでの相対仮想アドレス。</span><span class="sxs-lookup"><span data-stu-id="92c10-106">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="92c10-107">[out] メソッドのメタデータ トークンへのポインター。</span><span class="sxs-lookup"><span data-stu-id="92c10-107">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="92c10-108">[out] このメソッドに関連付けられているジェネリック パラメーターの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="92c10-108">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="92c10-109">[in] `signature` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="92c10-109">[in] The size of the `signature` array.</span></span> <span data-ttu-id="92c10-110">「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92c10-110">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="92c10-111">[out] 返される `signature` 配列のサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="92c10-111">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="92c10-112">[out] すべてのジェネリック パラメーターの typespec シグネチャを保持するバッファー。</span><span class="sxs-lookup"><span data-stu-id="92c10-112">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92c10-113">注釈</span><span class="sxs-lookup"><span data-stu-id="92c10-113">Remarks</span></span>  

 <span data-ttu-id="92c10-114">メソッドの配列の必要なサイズを取得するには `signature` 、 `cbSignature` 引数を0に設定し、 `signature` を **null** に設定します。</span><span class="sxs-lookup"><span data-stu-id="92c10-114">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="92c10-115">このメソッドから制御が戻ると、`pcbSignature` には `signature` 配列の必要なバイト数が格納されます。</span><span class="sxs-lookup"><span data-stu-id="92c10-115">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92c10-116">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="92c10-116">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92c10-117">要件</span><span class="sxs-lookup"><span data-stu-id="92c10-117">Requirements</span></span>  

 <span data-ttu-id="92c10-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92c10-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92c10-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92c10-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92c10-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92c10-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92c10-121">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92c10-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92c10-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="92c10-122">See also</span></span>

- [<span data-ttu-id="92c10-123">GetTypeProps メソッド</span><span class="sxs-lookup"><span data-stu-id="92c10-123">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="92c10-124">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="92c10-124">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="92c10-125">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="92c10-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
