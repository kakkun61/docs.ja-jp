---
title: 'いい変数 Home:: GetRegister メソッド'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
ms.openlocfilehash: 7f912f4b13620b567f5aa097604e98112d85f02d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95711755"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="3441d-102">いい変数 Home:: GetRegister メソッド</span><span class="sxs-lookup"><span data-stu-id="3441d-102">ICorDebugVariableHome::GetRegister Method</span></span>

<span data-ttu-id="3441d-103">の場所の種類がである変数 `VLT_REGISTER` と、の場所の種類がの変数の基本レジスタを含むレジスタを取得し `VLT_REGISTER_RELATIVE` ます。</span><span class="sxs-lookup"><span data-stu-id="3441d-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3441d-104">構文</span><span class="sxs-lookup"><span data-stu-id="3441d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3441d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3441d-105">Parameters</span></span>  

 `pRegister`  
 <span data-ttu-id="3441d-106">入出力の場所の種類がである変数のレジスタ、 `VLT_REGISTER` およびの場所の種類がの変数の基本レジスタを示す CorDebugRegister 列挙値 `VLT_REGISTER_RELATIVE` 。</span><span class="sxs-lookup"><span data-stu-id="3441d-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3441d-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="3441d-107">Return Value</span></span>  

 <span data-ttu-id="3441d-108">メソッドは、次の値を返します。</span><span class="sxs-lookup"><span data-stu-id="3441d-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="3441d-109">値</span><span class="sxs-lookup"><span data-stu-id="3441d-109">Value</span></span>|<span data-ttu-id="3441d-110">説明</span><span class="sxs-lookup"><span data-stu-id="3441d-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="3441d-111">変数は、引数で指定されたレジスタにあり `pRegister` ます。</span><span class="sxs-lookup"><span data-stu-id="3441d-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="3441d-112">変数がレジスタまたはレジスタの相対位置にありません。</span><span class="sxs-lookup"><span data-stu-id="3441d-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3441d-113">要件</span><span class="sxs-lookup"><span data-stu-id="3441d-113">Requirements</span></span>  

 <span data-ttu-id="3441d-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3441d-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3441d-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3441d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3441d-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3441d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3441d-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3441d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3441d-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="3441d-118">See also</span></span>

- [<span data-ttu-id="3441d-119">VariableLocationType 列挙型</span><span class="sxs-lookup"><span data-stu-id="3441d-119">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
- [<span data-ttu-id="3441d-120">ICorDebugVariableHome インターフェイス</span><span class="sxs-lookup"><span data-stu-id="3441d-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
