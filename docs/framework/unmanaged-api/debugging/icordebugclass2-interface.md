---
title: ICorDebugClass2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugClass2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2
helpviewer_keywords:
- ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 5416de70-43f2-4cdf-a11f-d570759c9c0c
topic_type:
- apiref
ms.openlocfilehash: ce3f289ae914817071fad5274c45d1e5fae71a06
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717982"
---
# <a name="icordebugclass2-interface"></a><span data-ttu-id="21f51-102">ICorDebugClass2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="21f51-102">ICorDebugClass2 Interface</span></span>

<span data-ttu-id="21f51-103">ジェネリック、または <xref:System.Type> 型のメソッド パラメーターを持つクラスを表します。</span><span class="sxs-lookup"><span data-stu-id="21f51-103">Represents a generic class or a class with a method parameter of type <xref:System.Type>.</span></span> <span data-ttu-id="21f51-104">このインターフェイスは [、を](icordebugclass-interface.md)拡張します。</span><span class="sxs-lookup"><span data-stu-id="21f51-104">This interface extends [ICorDebugClass](icordebugclass-interface.md).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="21f51-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="21f51-105">Methods</span></span>  
  
|<span data-ttu-id="21f51-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="21f51-106">Method</span></span>|<span data-ttu-id="21f51-107">説明</span><span class="sxs-lookup"><span data-stu-id="21f51-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="21f51-108">GetParameterizedType メソッド</span><span class="sxs-lookup"><span data-stu-id="21f51-108">GetParameterizedType Method</span></span>](icordebugclass2-getparameterizedtype-method.md)|<span data-ttu-id="21f51-109">このクラスの型宣言を取得します。</span><span class="sxs-lookup"><span data-stu-id="21f51-109">Gets the type declaration for this class.</span></span>|  
|[<span data-ttu-id="21f51-110">SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="21f51-110">SetJMCStatus Method</span></span>](icordebugclass2-setjmcstatus-method.md)|<span data-ttu-id="21f51-111">このクラスの各メソッドについて、メソッドがユーザー定義のコードかどうかを示す値を設定します。</span><span class="sxs-lookup"><span data-stu-id="21f51-111">For each method of this class, sets a value that indicates whether the method is user-defined code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="21f51-112">注釈</span><span class="sxs-lookup"><span data-stu-id="21f51-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="21f51-113">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="21f51-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21f51-114">要件</span><span class="sxs-lookup"><span data-stu-id="21f51-114">Requirements</span></span>  

 <span data-ttu-id="21f51-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="21f51-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21f51-116">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21f51-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21f51-117">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21f51-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21f51-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21f51-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21f51-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="21f51-119">See also</span></span>

- [<span data-ttu-id="21f51-120">ICorDebugClass インターフェイス</span><span class="sxs-lookup"><span data-stu-id="21f51-120">ICorDebugClass Interface</span></span>](icordebugclass-interface.md)
- [<span data-ttu-id="21f51-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="21f51-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
