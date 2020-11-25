---
title: ICorDebugSymbolProvider::GetObjectSize メソッド
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
ms.openlocfilehash: 4937ff1be7736f98be9efb9b01bdb322bf33e037
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730809"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="3cc9e-102">ICorDebugSymbolProvider::GetObjectSize メソッド</span><span class="sxs-lookup"><span data-stu-id="3cc9e-102">ICorDebugSymbolProvider::GetObjectSize Method</span></span>

<span data-ttu-id="3cc9e-103">typespec シグネチャに基づいてオブジェクトのオブジェクト サイズを返します。</span><span class="sxs-lookup"><span data-stu-id="3cc9e-103">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3cc9e-104">構文</span><span class="sxs-lookup"><span data-stu-id="3cc9e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3cc9e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3cc9e-105">Parameters</span></span>  

 `cbSignature`  
 <span data-ttu-id="3cc9e-106">[in] typespec シグネチャのバイト数。</span><span class="sxs-lookup"><span data-stu-id="3cc9e-106">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="3cc9e-107">typeSig</span><span class="sxs-lookup"><span data-stu-id="3cc9e-107">typeSig</span></span>  
 <span data-ttu-id="3cc9e-108">[in] typespec シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="3cc9e-108">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="3cc9e-109">[out] オブジェクトのサイズへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3cc9e-109">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3cc9e-110">注釈</span><span class="sxs-lookup"><span data-stu-id="3cc9e-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3cc9e-111">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3cc9e-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3cc9e-112">要件</span><span class="sxs-lookup"><span data-stu-id="3cc9e-112">Requirements</span></span>  

 <span data-ttu-id="3cc9e-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3cc9e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3cc9e-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3cc9e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3cc9e-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3cc9e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3cc9e-116">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3cc9e-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3cc9e-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="3cc9e-117">See also</span></span>

- [<span data-ttu-id="3cc9e-118">ICorDebugSymbolProvider インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3cc9e-118">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="3cc9e-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3cc9e-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
