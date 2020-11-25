---
title: ICorDebugVirtualUnwinder::Next メソッド
ms.date: 03/30/2017
ms.assetid: 790e0426-e5cd-49fd-a792-f8c8635d72fe
ms.openlocfilehash: bfc827a1503b0367a442e3f3ca0915bd2aaeb01e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725951"
---
# <a name="icordebugvirtualunwindernext-method"></a><span data-ttu-id="3d399-102">ICorDebugVirtualUnwinder::Next メソッド</span><span class="sxs-lookup"><span data-stu-id="3d399-102">ICorDebugVirtualUnwinder::Next Method</span></span>

<span data-ttu-id="3d399-103">呼び出し元のコンテキストに進みます。</span><span class="sxs-lookup"><span data-stu-id="3d399-103">Advances to the caller's context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d399-104">構文</span><span class="sxs-lookup"><span data-stu-id="3d399-104">Syntax</span></span>  
  
```cpp  
HRESULT Next();  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d399-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3d399-105">Parameters</span></span>  

 <span data-ttu-id="3d399-106">[なし] :</span><span class="sxs-lookup"><span data-stu-id="3d399-106">None.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3d399-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="3d399-107">Return Value</span></span>  

 <span data-ttu-id="3d399-108">アンワインドが正常に発生した場合は `S_OK`、フレームがないためにアンワインドが完了できなかった場合は `CORDBG_S_AT_END_OF_STACK`。</span><span class="sxs-lookup"><span data-stu-id="3d399-108">`S_OK` if the unwind occurred successfully, or `CORDBG_S_AT_END_OF_STACK` if the unwind cannot be completed because there are no more frames.</span></span>  
  
 <span data-ttu-id="3d399-109">失敗を示す HRESULT が返される場合、ICorDebug API は `CORDBG_E_DATA_TARGET_ERROR` を返します。</span><span class="sxs-lookup"><span data-stu-id="3d399-109">If a failing HRESULT is returned, ICorDebug APIs will return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d399-110">注釈</span><span class="sxs-lookup"><span data-stu-id="3d399-110">Remarks</span></span>  

 <span data-ttu-id="3d399-111">スタック ウォーカーにより、前へ進んでいることが確認されます。これにより、最終的に `Next` の呼び出しによって、失敗を示す HRESULT または `CORDBG_S_AT_END_OF_STACK` が返されます。</span><span class="sxs-lookup"><span data-stu-id="3d399-111">The stack walker should ensure that it makes forward progress, so that eventually a call to `Next` will return a failing HRESULT or `CORDBG_S_AT_END_OF_STACK`.</span></span> <span data-ttu-id="3d399-112">無制限 `S_OK` に戻ると、無限ループが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="3d399-112">Returning `S_OK` indefinitely may cause an infinite loop.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d399-113">このメソッドは .NET ネイティブでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="3d399-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d399-114">要件</span><span class="sxs-lookup"><span data-stu-id="3d399-114">Requirements</span></span>  

 <span data-ttu-id="3d399-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d399-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d399-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d399-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d399-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d399-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d399-118">**.NET Framework のバージョン:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d399-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d399-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="3d399-119">See also</span></span>

- [<span data-ttu-id="3d399-120">ICorDebugMemoryBuffer インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d399-120">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="3d399-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="3d399-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
