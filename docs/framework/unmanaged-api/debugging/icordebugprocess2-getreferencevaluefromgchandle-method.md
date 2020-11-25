---
title: ICorDebugProcess2::GetReferenceValueFromGCHandle メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetReferenceValueFromGCHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetReferenceValueFromGCHandle
helpviewer_keywords:
- GetReferenceValueFromGCHandle method [.NET Framework debugging]
- ICorDebugProcess2::GetReferenceValueFromGCHandle method [.NET Framework debugging]
ms.assetid: 8bdd7f4c-19f2-4ede-875e-603773e8c128
topic_type:
- apiref
ms.openlocfilehash: a5b9d57aab834ba3ca72a2ea8576ec70cd88eb77
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713575"
---
# <a name="icordebugprocess2getreferencevaluefromgchandle-method"></a><span data-ttu-id="15284-102">ICorDebugProcess2::GetReferenceValueFromGCHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="15284-102">ICorDebugProcess2::GetReferenceValueFromGCHandle Method</span></span>

<span data-ttu-id="15284-103">ガベージコレクションハンドルを持つ指定したマネージオブジェクトへの参照ポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="15284-103">Gets a reference pointer to the specified managed object that has a garbage collection handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15284-104">構文</span><span class="sxs-lookup"><span data-stu-id="15284-104">Syntax</span></span>  
  
```cpp  
HRESULT GetReferenceValueFromGCHandle (  
    [in]  UINT_PTR                 handle,  
    [out] ICorDebugReferenceValue  **pOutValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15284-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="15284-105">Parameters</span></span>  

 `handle`  
 <span data-ttu-id="15284-106">からガベージコレクションハンドルを持つマネージオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="15284-106">[in] A pointer to a managed object that has a garbage collection handle.</span></span> <span data-ttu-id="15284-107">この値はオブジェクトであり、 <xref:System.IntPtr> <xref:System.Runtime.InteropServices.GCHandle> マネージオブジェクトのから取得できます。</span><span class="sxs-lookup"><span data-stu-id="15284-107">This value is a <xref:System.IntPtr> object and can be retrieved from the <xref:System.Runtime.InteropServices.GCHandle> for the managed object.</span></span>  
  
 `pOutValue`  
 <span data-ttu-id="15284-108">入出力指定したマネージオブジェクトへの参照を表す、値オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="15284-108">[out] A pointer to the address of an ICorDebugReferenceValue object that represents a reference to the specified managed object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15284-109">注釈</span><span class="sxs-lookup"><span data-stu-id="15284-109">Remarks</span></span>  

 <span data-ttu-id="15284-110">返された参照値とガベージコレクション参照値を混同しないようにしてください。</span><span class="sxs-lookup"><span data-stu-id="15284-110">Do not confuse the returned reference value with a garbage collection reference value.</span></span>  
  
 <span data-ttu-id="15284-111">返される参照は、通常の参照のように動作します。</span><span class="sxs-lookup"><span data-stu-id="15284-111">The returned reference behaves like a normal reference.</span></span> <span data-ttu-id="15284-112">ブレークポイント後にコードの実行が続行される場合は無効になります。</span><span class="sxs-lookup"><span data-stu-id="15284-112">It is disabled when code execution continues after a breakpoint.</span></span> <span data-ttu-id="15284-113">ターゲットオブジェクトの有効期間は、参照値の有効期間の影響を受けません。</span><span class="sxs-lookup"><span data-stu-id="15284-113">The lifetime of the target object is not affected by the lifetime of the reference value.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="15284-114">メソッドでは `GetReferenceValueFromGCHandle` 、ハンドルは検証されません。</span><span class="sxs-lookup"><span data-stu-id="15284-114">The `GetReferenceValueFromGCHandle` method does not validate the handle.</span></span> <span data-ttu-id="15284-115">したがって、 `GetReferenceValueFromGCHandle` メソッドは、無効なハンドルが渡された場合に、デバッガーとデバッグされているコードの両方を破損する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="15284-115">Therefore, the `GetReferenceValueFromGCHandle` method can potentially corrupt both the debugger and the code being debugged if an invalid handle is passed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15284-116">要件</span><span class="sxs-lookup"><span data-stu-id="15284-116">Requirements</span></span>  

 <span data-ttu-id="15284-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="15284-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15284-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="15284-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15284-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15284-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15284-120">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15284-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
