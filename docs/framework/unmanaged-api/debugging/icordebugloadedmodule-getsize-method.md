---
title: ICorDebugLoadedModule::GetSize メソッド
ms.date: 03/30/2017
ms.assetid: aaa0e5c0-be9d-4fe1-8418-5295b9b184d6
ms.openlocfilehash: 2ed19cb4a190f2af7581a827e8bd11b748b3d4a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721323"
---
# <a name="icordebugloadedmodulegetsize-method"></a><span data-ttu-id="36bf9-102">ICorDebugLoadedModule::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="36bf9-102">ICorDebugLoadedModule::GetSize Method</span></span>

<span data-ttu-id="36bf9-103">読み込まれたモジュールのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="36bf9-103">Gets the size in bytes of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36bf9-104">構文</span><span class="sxs-lookup"><span data-stu-id="36bf9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="36bf9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="36bf9-105">Parameters</span></span>  

 `pcBytes`  
 <span data-ttu-id="36bf9-106">[out] 読み込まれたモジュールのバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="36bf9-106">[out] A pointer to the number of bytes in the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="36bf9-107">注釈</span><span class="sxs-lookup"><span data-stu-id="36bf9-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36bf9-108">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="36bf9-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="36bf9-109">要件</span><span class="sxs-lookup"><span data-stu-id="36bf9-109">Requirements</span></span>  

 <span data-ttu-id="36bf9-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="36bf9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="36bf9-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="36bf9-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="36bf9-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="36bf9-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="36bf9-113">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="36bf9-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="36bf9-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="36bf9-114">See also</span></span>

- [<span data-ttu-id="36bf9-115">ICorDebugLoadedModule インターフェイス</span><span class="sxs-lookup"><span data-stu-id="36bf9-115">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="36bf9-116">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="36bf9-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
