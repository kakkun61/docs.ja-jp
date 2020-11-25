---
title: ICorDebugFunction2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2
helpviewer_keywords:
- ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 2b936bef-9b75-48bf-859f-42e419c65f1c
topic_type:
- apiref
ms.openlocfilehash: d9e84a70d72db1338c80140ce3350774bfae4bca
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726276"
---
# <a name="icordebugfunction2-interface"></a><span data-ttu-id="10a4e-102">ICorDebugFunction2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="10a4e-102">ICorDebugFunction2 Interface</span></span>

<span data-ttu-id="10a4e-103">マイコードのみのステップスルーデバッグをサポートするように、この関数インターフェイスを論理的に拡張します。これにより、非ユーザーコードがスキップされます。</span><span class="sxs-lookup"><span data-stu-id="10a4e-103">Logically extends the ICorDebugFunction interface to provide support for Just My Code step-through debugging, which skips non-user code.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="10a4e-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="10a4e-104">Methods</span></span>  
  
|<span data-ttu-id="10a4e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="10a4e-105">Method</span></span>|<span data-ttu-id="10a4e-106">説明</span><span class="sxs-lookup"><span data-stu-id="10a4e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="10a4e-107">EnumerateNativeCode メソッド</span><span class="sxs-lookup"><span data-stu-id="10a4e-107">EnumerateNativeCode Method</span></span>](icordebugfunction2-enumeratenativecode-method.md)|<span data-ttu-id="10a4e-108">(実装されていません。)この ICorDebugFunction2 オブジェクトによって参照されている関数内のネイティブコードステートメントを含む、コードの型の列挙体へのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="10a4e-108">(Not yet implemented.) Gets an interface pointer to an ICorDebugCodeEnum that contains the native code statements in the function referenced by this ICorDebugFunction2 object.</span></span>|  
|[<span data-ttu-id="10a4e-109">GetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="10a4e-109">GetJMCStatus Method</span></span>](icordebugfunction2-getjmcstatus-method.md)|<span data-ttu-id="10a4e-110">この関数がユーザーコードとしてマークされているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="10a4e-110">Gets a value that indicates whether this function is marked as user code.</span></span>|  
|[<span data-ttu-id="10a4e-111">GetVersionNumber メソッド</span><span class="sxs-lookup"><span data-stu-id="10a4e-111">GetVersionNumber Method</span></span>](icordebugfunction2-getversionnumber-method.md)|<span data-ttu-id="10a4e-112">この関数のエディットコンティニュバージョンを取得します。</span><span class="sxs-lookup"><span data-stu-id="10a4e-112">Gets the Edit and Continue version of this function.</span></span>|  
|[<span data-ttu-id="10a4e-113">SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="10a4e-113">SetJMCStatus Method</span></span>](icordebugfunction2-setjmcstatus-method.md)|<span data-ttu-id="10a4e-114">マイコードのみのステップ実行のために、この関数をマークします。</span><span class="sxs-lookup"><span data-stu-id="10a4e-114">Marks this function for Just My Code stepping.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="10a4e-115">注釈</span><span class="sxs-lookup"><span data-stu-id="10a4e-115">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="10a4e-116">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="10a4e-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="10a4e-117">要件</span><span class="sxs-lookup"><span data-stu-id="10a4e-117">Requirements</span></span>  

 <span data-ttu-id="10a4e-118">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="10a4e-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="10a4e-119">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="10a4e-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="10a4e-120">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="10a4e-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="10a4e-121">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="10a4e-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="10a4e-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="10a4e-122">See also</span></span>

- [<span data-ttu-id="10a4e-123">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="10a4e-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
