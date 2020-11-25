---
title: ICorDebugRegisterSet::GetRegistersAvailable メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
ms.openlocfilehash: d28c130e55cbebf29348752780c03b03c1b8f358
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716994"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="06aad-102">ICorDebugRegisterSet::GetRegistersAvailable メソッド</span><span class="sxs-lookup"><span data-stu-id="06aad-102">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>

<span data-ttu-id="06aad-103">[このは、この](icordebugregisterset-interface.md)"この" のどのレジスタが現在使用可能であるかを示すビットマスクを取得します。</span><span class="sxs-lookup"><span data-stu-id="06aad-103">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06aad-104">構文</span><span class="sxs-lookup"><span data-stu-id="06aad-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="06aad-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="06aad-105">Parameters</span></span>  

 `pAvailable`  
 <span data-ttu-id="06aad-106">入出力現在使用できるレジスタを示すビットマスク。</span><span class="sxs-lookup"><span data-stu-id="06aad-106">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06aad-107">注釈</span><span class="sxs-lookup"><span data-stu-id="06aad-107">Remarks</span></span>  

 <span data-ttu-id="06aad-108">特定の状況でその値を特定できない場合は、レジスタを使用できない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="06aad-108">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="06aad-109">返されるマスクには、レジスタごとにビットが含まれています (1 << レジスタインデックス)。</span><span class="sxs-lookup"><span data-stu-id="06aad-109">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="06aad-110">レジスタが使用可能な場合、ビット値は1です。使用できない場合は0です。</span><span class="sxs-lookup"><span data-stu-id="06aad-110">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06aad-111">要件</span><span class="sxs-lookup"><span data-stu-id="06aad-111">Requirements</span></span>  

 <span data-ttu-id="06aad-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="06aad-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06aad-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="06aad-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="06aad-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06aad-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06aad-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06aad-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06aad-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="06aad-116">See also</span></span>

- [<span data-ttu-id="06aad-117">ICorDebugRegisterSet インターフェイス</span><span class="sxs-lookup"><span data-stu-id="06aad-117">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="06aad-118">ICorDebugRegisterSet2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="06aad-118">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
