---
title: ICorDebugDataTarget3::GetLoadedModules メソッド
ms.date: 03/30/2017
ms.assetid: 9a48c05b-1949-416e-933c-52549b6fcf5e
ms.openlocfilehash: efbada02b7a24e0a7ed613b86b8a4a1a0b5b051a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713751"
---
# <a name="icordebugdatatarget3getloadedmodules-method"></a><span data-ttu-id="90da3-102">ICorDebugDataTarget3::GetLoadedModules メソッド</span><span class="sxs-lookup"><span data-stu-id="90da3-102">ICorDebugDataTarget3::GetLoadedModules Method</span></span>

<span data-ttu-id="90da3-103">これまでに読み込まれたモジュールの一覧を取得します。</span><span class="sxs-lookup"><span data-stu-id="90da3-103">Gets a list of the modules that have been loaded so far.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90da3-104">構文</span><span class="sxs-lookup"><span data-stu-id="90da3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLoadedModules(  
   [in] ULONG32 cRequestedModules,  
   [out] ULONG32 *pcFetchedModules,  
   [out, size_is(cRequestedModules), length_is(*pcFetchedModules)] ICorDebugLoadedModule *pLoadedModules[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90da3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="90da3-105">Parameters</span></span>  

 `cRequestedModules`  
 <span data-ttu-id="90da3-106">[in] 情報を要求する対象のモジュールの数。</span><span class="sxs-lookup"><span data-stu-id="90da3-106">[in] The number of modules for which information is requested.</span></span>  
  
 `pcFetchedModules`  
 <span data-ttu-id="90da3-107">[out] 情報が返された対象モジュールの数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="90da3-107">[out] A pointer to the number of modules about which information was returned.</span></span>  
  
 `pLoadedModules`  
 <span data-ttu-id="90da3-108">入出力読み込まれたモジュールに関する情報を提供する [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) オブジェクトの配列へのポインター。</span><span class="sxs-lookup"><span data-stu-id="90da3-108">[out] A pointer to an array of [ICorDebugLoadedModule](icordebugloadedmodule-interface.md) objects that provide information about loaded modules.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="90da3-109">注釈</span><span class="sxs-lookup"><span data-stu-id="90da3-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="90da3-110">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="90da3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90da3-111">要件</span><span class="sxs-lookup"><span data-stu-id="90da3-111">Requirements</span></span>  

 <span data-ttu-id="90da3-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="90da3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90da3-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90da3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90da3-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90da3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90da3-115">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90da3-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90da3-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="90da3-116">See also</span></span>

- [<span data-ttu-id="90da3-117">ICorDebugDataTarget3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="90da3-117">ICorDebugDataTarget3 Interface</span></span>](icordebugdatatarget3-interface.md)
- [<span data-ttu-id="90da3-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="90da3-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
