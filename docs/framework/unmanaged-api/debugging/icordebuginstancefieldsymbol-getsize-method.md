---
title: ICorDebugInstanceFieldSymbol::GetSize メソッド
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: c4b193b45e30b0eba3367f18cb1e4c2b4e108fa8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724911"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="3fc23-102">ICorDebugInstanceFieldSymbol::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="3fc23-102">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>

<span data-ttu-id="3fc23-103">インスタンス フィールドのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="3fc23-103">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fc23-104">構文</span><span class="sxs-lookup"><span data-stu-id="3fc23-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fc23-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3fc23-105">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="3fc23-106">[out] フィールドの長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="3fc23-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fc23-107">注釈</span><span class="sxs-lookup"><span data-stu-id="3fc23-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3fc23-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3fc23-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fc23-109">要件</span><span class="sxs-lookup"><span data-stu-id="3fc23-109">Requirements</span></span>  

 <span data-ttu-id="3fc23-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3fc23-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fc23-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fc23-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fc23-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fc23-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fc23-113">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fc23-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fc23-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="3fc23-114">See also</span></span>

- [<span data-ttu-id="3fc23-115">ICorDebugInstanceFieldSymbol インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3fc23-115">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="3fc23-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3fc23-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
