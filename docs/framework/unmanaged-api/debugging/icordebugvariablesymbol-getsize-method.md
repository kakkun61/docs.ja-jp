---
title: ICorDebugVariableSymbol::GetSize メソッド
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
ms.openlocfilehash: 1079351e75ec9c48a9657f514ee56e2e6a4b0920
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731372"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="667be-102">ICorDebugVariableSymbol::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="667be-102">ICorDebugVariableSymbol::GetSize Method</span></span>

<span data-ttu-id="667be-103">変数のサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="667be-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="667be-104">構文</span><span class="sxs-lookup"><span data-stu-id="667be-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="667be-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="667be-105">Parameters</span></span>  

 `pcbValue`  
 <span data-ttu-id="667be-106">変数のサイズが格納されている 32 ビットの符号なし整数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="667be-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="667be-107">注釈</span><span class="sxs-lookup"><span data-stu-id="667be-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="667be-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="667be-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="667be-109">要件</span><span class="sxs-lookup"><span data-stu-id="667be-109">Requirements</span></span>  

 <span data-ttu-id="667be-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="667be-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="667be-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="667be-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="667be-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="667be-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="667be-113">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="667be-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="667be-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="667be-114">See also</span></span>

- [<span data-ttu-id="667be-115">ICorDebugVariableSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="667be-115">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="667be-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="667be-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
