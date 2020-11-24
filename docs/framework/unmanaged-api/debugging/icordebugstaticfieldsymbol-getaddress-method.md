---
title: ICorDebugStaticFieldSymbol::GetAddress メソッド
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: e9404b429ad4507acb5132a86af5f287dbcf07b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677285"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="0ddf1-102">ICorDebugStaticFieldSymbol::GetAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="0ddf1-102">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>

<span data-ttu-id="0ddf1-103">静的フィールドのアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="0ddf1-103">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ddf1-104">構文</span><span class="sxs-lookup"><span data-stu-id="0ddf1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0ddf1-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0ddf1-105">Parameters</span></span>  

 <span data-ttu-id="0ddf1-106">pRVA</span><span class="sxs-lookup"><span data-stu-id="0ddf1-106">pRVA</span></span>  
 <span data-ttu-id="0ddf1-107">[out] 静的フィールドの相対仮想アドレス (RVA) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0ddf1-107">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0ddf1-108">注釈</span><span class="sxs-lookup"><span data-stu-id="0ddf1-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0ddf1-109">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="0ddf1-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0ddf1-110">要件</span><span class="sxs-lookup"><span data-stu-id="0ddf1-110">Requirements</span></span>  

 <span data-ttu-id="0ddf1-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0ddf1-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0ddf1-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0ddf1-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0ddf1-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0ddf1-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0ddf1-114">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0ddf1-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0ddf1-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0ddf1-115">See also</span></span>

- [<span data-ttu-id="0ddf1-116">ICorDebugStaticFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0ddf1-116">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="0ddf1-117">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="0ddf1-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
