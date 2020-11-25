---
title: ICorDebugEval::NewObjectNoConstructor メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type:
- apiref
ms.openlocfilehash: bb27ec755fb83dc71af7dd48b5ed6e7699436335
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729730"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="554cd-102">ICorDebugEval::NewObjectNoConstructor メソッド</span><span class="sxs-lookup"><span data-stu-id="554cd-102">ICorDebugEval::NewObjectNoConstructor Method</span></span>

<span data-ttu-id="554cd-103">コンストラクターメソッドを呼び出さずに、指定した型の新しいオブジェクトインスタンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="554cd-103">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="554cd-104">このメソッドは .NET Framework バージョン2.0 では廃止されています。</span><span class="sxs-lookup"><span data-stu-id="554cd-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="554cd-105">代わりに [ICorDebugEval2:: NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="554cd-105">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="554cd-106">構文</span><span class="sxs-lookup"><span data-stu-id="554cd-106">Syntax</span></span>  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="554cd-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="554cd-107">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="554cd-108">からインスタンス化するオブジェクトの型を表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="554cd-108">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="554cd-109">要件</span><span class="sxs-lookup"><span data-stu-id="554cd-109">Requirements</span></span>  

 <span data-ttu-id="554cd-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="554cd-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="554cd-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="554cd-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="554cd-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="554cd-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="554cd-113">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="554cd-113">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="554cd-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="554cd-114">See also</span></span>

- [<span data-ttu-id="554cd-115">NewParameterizedObjectNoConstructor メソッド</span><span class="sxs-lookup"><span data-stu-id="554cd-115">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)
