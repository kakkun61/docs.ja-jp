---
title: ICorDebugClass::GetStaticFieldValue メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetStaticFieldValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetStaticFieldValue
helpviewer_keywords:
- GetStaticFieldValue method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetStaticFieldValue method [.NET Framework debugging]
ms.assetid: 56e718b4-fabd-418b-a5b3-3cc33c745683
topic_type:
- apiref
ms.openlocfilehash: dd1608badf553650b05b7de98d9bbcd76b2f3edf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728434"
---
# <a name="icordebugclassgetstaticfieldvalue-method"></a><span data-ttu-id="aae8d-102">ICorDebugClass::GetStaticFieldValue メソッド</span><span class="sxs-lookup"><span data-stu-id="aae8d-102">ICorDebugClass::GetStaticFieldValue Method</span></span>

<span data-ttu-id="aae8d-103">指定された静的フィールドの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="aae8d-103">Gets the value of the specified static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aae8d-104">構文</span><span class="sxs-lookup"><span data-stu-id="aae8d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldValue (  
    [in]  mdFieldDef         fieldDef,  
    [in]  ICorDebugFrame     *pFrame,  
    [out] ICorDebugValue     **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aae8d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aae8d-105">Parameters</span></span>  

 `fieldDef`  
 <span data-ttu-id="aae8d-106">から `Def` 取得するフィールドを参照するフィールドトークン。</span><span class="sxs-lookup"><span data-stu-id="aae8d-106">[in] A field `Def` token that references the field to be retrieved.</span></span>  
  
 `pFrame`  
 <span data-ttu-id="aae8d-107">からスレッド、コンテキスト、またはアプリケーションドメインの静的を区別するために使用されるフレームを表す、テキストフレームオブジェクトへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aae8d-107">[in] A pointer to an ICorDebugFrame object that represents the frame to be used to disambiguate among thread, context, or application domain statics.</span></span>  
  
 <span data-ttu-id="aae8d-108">静的フィールドがスレッド、コンテキスト、またはアプリケーションドメインに対する相対パスである場合、フレームによって適切な値が決定されます。</span><span class="sxs-lookup"><span data-stu-id="aae8d-108">If the static field is relative to a thread, a context, or an application domain, the frame will determine the proper value.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="aae8d-109">入出力静的フィールドの値を表す ICorDebugValue オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aae8d-109">[out] A pointer to the address of an ICorDebugValue object that represents the value of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="aae8d-110">注釈</span><span class="sxs-lookup"><span data-stu-id="aae8d-110">Remarks</span></span>  

 <span data-ttu-id="aae8d-111">パラメーター化された型の場合、静的フィールドの値は、特定のインスタンス化に対する相対値になります。</span><span class="sxs-lookup"><span data-stu-id="aae8d-111">For parameterized types, the value of a static field is relative to the particular instantiation.</span></span> <span data-ttu-id="aae8d-112">したがって、クラスコンストラクターが型のパラメーターを受け取る場合は、では <xref:System.Type> なく、の [型](icordebugtype-getstaticfieldvalue-method.md) を呼び出す必要があり `ICorDebugClass::GetStaticFieldValue` ます。</span><span class="sxs-lookup"><span data-stu-id="aae8d-112">Therefore, if the class constructor takes parameters of type <xref:System.Type>, call [ICorDebugType::GetStaticFieldValue](icordebugtype-getstaticfieldvalue-method.md) instead of `ICorDebugClass::GetStaticFieldValue`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aae8d-113">要件</span><span class="sxs-lookup"><span data-stu-id="aae8d-113">Requirements</span></span>  

 <span data-ttu-id="aae8d-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aae8d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aae8d-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aae8d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aae8d-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aae8d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aae8d-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aae8d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
