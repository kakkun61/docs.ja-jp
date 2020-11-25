---
title: ICorDebugExceptionDebugEvent::GetFlags メソッド
ms.date: 03/30/2017
ms.assetid: 73225303-8852-487e-9a0e-9f0cb95e99d9
ms.openlocfilehash: 02a20b54b7fecc711bda010c6916fe036cf20dd9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729604"
---
# <a name="icordebugexceptiondebugeventgetflags-method"></a><span data-ttu-id="06c8d-102">ICorDebugExceptionDebugEvent::GetFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="06c8d-102">ICorDebugExceptionDebugEvent::GetFlags Method</span></span>

<span data-ttu-id="06c8d-103">例外をインターセプトできるかどうかを示すフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="06c8d-103">Gets a flag that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06c8d-104">構文</span><span class="sxs-lookup"><span data-stu-id="06c8d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFlags(  
   [out] CorDebugExceptionFlags *pdwFlags  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06c8d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="06c8d-105">Parameters</span></span>  

 `pdwFlags`  
 <span data-ttu-id="06c8d-106">入出力例外をインターセプトできるかどうかを示す [Cordebugexceptionflags](cordebugexceptionflags-enumeration.md) 値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="06c8d-106">[out] A pointer to a [CorDebugExceptionFlags](cordebugexceptionflags-enumeration.md) value that indicates whether the exception can be intercepted.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06c8d-107">注釈</span><span class="sxs-lookup"><span data-stu-id="06c8d-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="06c8d-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="06c8d-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06c8d-109">要件</span><span class="sxs-lookup"><span data-stu-id="06c8d-109">Requirements</span></span>  

 <span data-ttu-id="06c8d-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06c8d-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06c8d-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06c8d-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06c8d-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06c8d-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06c8d-113">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06c8d-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06c8d-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="06c8d-114">See also</span></span>

- [<span data-ttu-id="06c8d-115">ICorDebugExceptionDebugEvent インターフェイス</span><span class="sxs-lookup"><span data-stu-id="06c8d-115">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="06c8d-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="06c8d-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
