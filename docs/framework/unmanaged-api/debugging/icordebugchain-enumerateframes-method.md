---
title: ICorDebugChain::EnumerateFrames メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugChain.EnumerateFrames
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain::EnumerateFrames method
helpviewer_keywords:
- EnumerateFrames method [.NET Framework debugging]
- ICorDebugChain::EnumerateFrames method [.NET Framework debugging]
ms.assetid: 9fcefa98-750d-4168-8915-8173a43accf2
topic_type:
- apiref
ms.openlocfilehash: ae6d81e6fdab0f8e3346d8a08a3b5ebc329a542a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95730150"
---
# <a name="icordebugchainenumerateframes-method"></a><span data-ttu-id="49bc0-102">ICorDebugChain::EnumerateFrames メソッド</span><span class="sxs-lookup"><span data-stu-id="49bc0-102">ICorDebugChain::EnumerateFrames Method</span></span>

<span data-ttu-id="49bc0-103">チェーン内のすべてのマネージスタックフレームが格納された列挙子を取得します。これは、最新のフレームから始まります。</span><span class="sxs-lookup"><span data-stu-id="49bc0-103">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49bc0-104">構文</span><span class="sxs-lookup"><span data-stu-id="49bc0-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateFrames (  
    [out] ICorDebugFrameEnum **ppFrames  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49bc0-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="49bc0-105">Parameters</span></span>  

 `ppFrames`  
 <span data-ttu-id="49bc0-106">入出力スタックフレームの列挙子である、テキストフレームの列挙型オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="49bc0-106">[out] A pointer to the address of an ICorDebugFrameEnum object that is the enumerator for the stack frames.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49bc0-107">注釈</span><span class="sxs-lookup"><span data-stu-id="49bc0-107">Remarks</span></span>  

 <span data-ttu-id="49bc0-108">チェーンは、スレッドの物理呼び出し履歴を表します。</span><span class="sxs-lookup"><span data-stu-id="49bc0-108">The chain represents the physical call stack for the thread.</span></span>  
  
 <span data-ttu-id="49bc0-109">メソッドは、 `EnumerateFrames` マネージドチェーンに対してのみ呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="49bc0-109">The `EnumerateFrames` method should be called only for managed chains.</span></span> <span data-ttu-id="49bc0-110">デバッグ API には、アンマネージチェーンに含まれるフレームを取得するためのメソッドが用意されていません。</span><span class="sxs-lookup"><span data-stu-id="49bc0-110">The debugging API does not provide methods for obtaining frames contained in unmanaged chains.</span></span> <span data-ttu-id="49bc0-111">デバッガーは、この情報を取得するために他の手段を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="49bc0-111">The debugger must use other means to obtain this information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49bc0-112">要件</span><span class="sxs-lookup"><span data-stu-id="49bc0-112">Requirements</span></span>  

 <span data-ttu-id="49bc0-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="49bc0-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49bc0-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49bc0-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49bc0-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49bc0-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49bc0-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49bc0-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
