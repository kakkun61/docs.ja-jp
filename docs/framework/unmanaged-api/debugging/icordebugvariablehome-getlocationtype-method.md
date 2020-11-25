---
title: 'いい変数 Home:: GetLocationType メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type:
- apiref
ms.openlocfilehash: 3979ed19f8a61ac1fc045b83c52e23d7255ac364
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711872"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="77f17-102">いい変数 Home:: GetLocationType メソッド</span><span class="sxs-lookup"><span data-stu-id="77f17-102">ICorDebugVariableHome::GetLocationType Method</span></span>

<span data-ttu-id="77f17-103">変数のネイティブな場所の型を取得します。</span><span class="sxs-lookup"><span data-stu-id="77f17-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="77f17-104">構文</span><span class="sxs-lookup"><span data-stu-id="77f17-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="77f17-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="77f17-105">Parameters</span></span>  

 `pLocationType`  
 <span data-ttu-id="77f17-106">入出力変数のネイティブな場所の型へのポインター。</span><span class="sxs-lookup"><span data-stu-id="77f17-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="77f17-107">詳細については、 [VariableLocationType](variablelocationtype-enumeration.md) 列挙体を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77f17-107">See the [VariableLocationType](variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="77f17-108">要件</span><span class="sxs-lookup"><span data-stu-id="77f17-108">Requirements</span></span>  

 <span data-ttu-id="77f17-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="77f17-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="77f17-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="77f17-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="77f17-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="77f17-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="77f17-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="77f17-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77f17-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="77f17-113">See also</span></span>

- [<span data-ttu-id="77f17-114">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="77f17-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="77f17-115">VariableLocationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="77f17-115">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
