---
title: ICorDebugEval2::NewParameterizedObject メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewParameterizedObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewParameterizedObject
helpviewer_keywords:
- NewParameterizedObject method [.NET Framework debugging]
- ICorDebugEval2::NewParameterizedObject method [.NET Framework debugging]
ms.assetid: 3d705463-e640-4249-8036-4e8206d03cfe
topic_type:
- apiref
ms.openlocfilehash: 8c91296bd4185fd98962d49f611a3cdcb5f0ad28
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729659"
---
# <a name="icordebugeval2newparameterizedobject-method"></a><span data-ttu-id="86d2e-102">ICorDebugEval2::NewParameterizedObject メソッド</span><span class="sxs-lookup"><span data-stu-id="86d2e-102">ICorDebugEval2::NewParameterizedObject Method</span></span>

<span data-ttu-id="86d2e-103">新しいパラメーター化された型オブジェクトをインスタンス化し、オブジェクトのコンストラクターメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="86d2e-103">Instantiates a new parameterized type object and calls the object's constructor method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86d2e-104">構文</span><span class="sxs-lookup"><span data-stu-id="86d2e-104">Syntax</span></span>  
  
```cpp  
HRESULT NewParameterizedObject (  
    [in] ICorDebugFunction     *pConstructor,  
    [in] ULONG32               nTypeArgs,  
    [in, size_is(nTypeArgs)] ICorDebugType *ppTypeArgs[],  
    [in] ULONG32               nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="86d2e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="86d2e-105">Parameters</span></span>  

 `pConstructor`  
 <span data-ttu-id="86d2e-106">からインスタンス化するオブジェクトのコンストラクターを表す、のオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="86d2e-106">[in] A pointer to an ICorDebugFunction object that represents the constructor of the object to be instantiated.</span></span>  
  
 `nTypeArgs`  
 <span data-ttu-id="86d2e-107">から渡された型引数の数。</span><span class="sxs-lookup"><span data-stu-id="86d2e-107">[in] The number of type arguments passed.</span></span>  
  
 `ppTypeArgs`  
 <span data-ttu-id="86d2e-108">からポインターの配列。各ポインターは、インスタンス化されているオブジェクトの型引数を表す、テキスト型のオブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="86d2e-108">[in] An array of pointers, each of which points to an ICorDebugType object that represents a type argument for the object that is being instantiated.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="86d2e-109">からコンストラクターに渡された引数の数。</span><span class="sxs-lookup"><span data-stu-id="86d2e-109">[in] The number of arguments passed to the constructor.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="86d2e-110">からポインターの配列。各ポインターは、コンストラクターに渡される引数値を表す ICorDebugValue オブジェクトを指します。</span><span class="sxs-lookup"><span data-stu-id="86d2e-110">[in] An array of pointers, each of which points to an ICorDebugValue object that represents an argument value that is passed to the constructor.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="86d2e-111">注釈</span><span class="sxs-lookup"><span data-stu-id="86d2e-111">Remarks</span></span>  

 <span data-ttu-id="86d2e-112">オブジェクトのコンストラクターは、パラメーターを受け取ることができ <xref:System.Type> ます。</span><span class="sxs-lookup"><span data-stu-id="86d2e-112">The object's constructor may take <xref:System.Type> parameters.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86d2e-113">要件</span><span class="sxs-lookup"><span data-stu-id="86d2e-113">Requirements</span></span>  

 <span data-ttu-id="86d2e-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="86d2e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86d2e-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="86d2e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="86d2e-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86d2e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86d2e-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86d2e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
