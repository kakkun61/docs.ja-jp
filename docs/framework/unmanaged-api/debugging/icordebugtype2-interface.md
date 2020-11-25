---
title: ICorDebugType2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugType2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType2
helpviewer_keywords:
- ICorDebugType2 interface
ms.assetid: 376fb03f-f1ef-4107-baa4-4d9d55884862
topic_type:
- apiref
ms.openlocfilehash: 0d5fffe4350cc1f58acf588f288db3bdb7e213d0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725669"
---
# <a name="icordebugtype2-interface"></a><span data-ttu-id="c66f1-102">ICorDebugType2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c66f1-102">ICorDebugType2 Interface</span></span>

<span data-ttu-id="c66f1-103">によって、テキスト型または複合型 (ユーザー定義型) の型識別子を取得するために、を拡張します。</span><span class="sxs-lookup"><span data-stu-id="c66f1-103">Extends the ICorDebugType interface to retrieve the type identifier  of a base type or complex (user-defined) type.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c66f1-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="c66f1-104">Methods</span></span>  
  
|<span data-ttu-id="c66f1-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="c66f1-105">Method</span></span>||  
|------------|-|  
|[<span data-ttu-id="c66f1-106">GetTypeID メソッド</span><span class="sxs-lookup"><span data-stu-id="c66f1-106">GetTypeID Method</span></span>](icordebugtype2-gettypeid-method.md)|<span data-ttu-id="c66f1-107">この型の [COR_TYPEID](cor-typeid-structure.md) を取得します。</span><span class="sxs-lookup"><span data-stu-id="c66f1-107">Gets a [COR_TYPEID](cor-typeid-structure.md) for this type.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c66f1-108">注釈</span><span class="sxs-lookup"><span data-stu-id="c66f1-108">Remarks</span></span>  

 <span data-ttu-id="c66f1-109">このインターフェイスは、テキストの型インターフェイスの論理上の拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="c66f1-109">This interface is a logical extension of the ICorDebugType interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c66f1-110">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="c66f1-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c66f1-111">例</span><span class="sxs-lookup"><span data-stu-id="c66f1-111">Example</span></span>  

 <span data-ttu-id="c66f1-112">次のコードフラグメントは、 [ICorDebugType2:: GetTypeID](icordebugtype2-gettypeid-method.md) メソッドの使用方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="c66f1-112">The following code fragment illustrates the use of the [ICorDebugType2::GetTypeID](icordebugtype2-gettypeid-method.md) method.</span></span>  
  
```cpp  
// (error checking omitted for brevity)  
// given an ICorDebugType *pType  
  
ICorDebugType2 *pType2 = NULL;  
pType->QueryInterface(IID_ICorDebugType2, &pType);  
  
COR_TYPEID id;  
pType2->GetTypeID(&id);  
  
// now we can use existing APIs to get information about this COR_TYPEID  
```  
  
## <a name="requirements"></a><span data-ttu-id="c66f1-113">要件</span><span class="sxs-lookup"><span data-stu-id="c66f1-113">Requirements</span></span>  

 <span data-ttu-id="c66f1-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c66f1-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c66f1-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c66f1-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c66f1-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c66f1-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c66f1-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c66f1-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c66f1-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="c66f1-118">See also</span></span>

- [<span data-ttu-id="c66f1-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="c66f1-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
