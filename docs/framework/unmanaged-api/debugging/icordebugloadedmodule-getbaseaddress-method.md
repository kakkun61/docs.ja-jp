---
title: ICorDebugLoadedModule::GetBaseAddress メソッド
ms.date: 03/30/2017
ms.assetid: 7c036772-d58a-47f1-a5fa-31779898ef0d
ms.openlocfilehash: 29153da86812583a0ea789da0c0816f08e0a6b43
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95698079"
---
# <a name="icordebugloadedmodulegetbaseaddress-method"></a><span data-ttu-id="ed515-102">ICorDebugLoadedModule::GetBaseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="ed515-102">ICorDebugLoadedModule::GetBaseAddress Method</span></span>

<span data-ttu-id="ed515-103">読み込まれたモジュールのベース アドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="ed515-103">Gets the base address of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed515-104">構文</span><span class="sxs-lookup"><span data-stu-id="ed515-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
   [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ed515-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ed515-105">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="ed515-106">[out] 読み込まれたモジュールのベース アドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="ed515-106">[out] A pointer to the base address of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ed515-107">注釈</span><span class="sxs-lookup"><span data-stu-id="ed515-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ed515-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="ed515-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ed515-109">要件</span><span class="sxs-lookup"><span data-stu-id="ed515-109">Requirements</span></span>  

 <span data-ttu-id="ed515-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ed515-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ed515-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ed515-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ed515-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ed515-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ed515-113">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ed515-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed515-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="ed515-114">See also</span></span>

- [<span data-ttu-id="ed515-115">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ed515-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="ed515-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="ed515-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
