---
title: ICorDebugInternalFrame::GetFrameType メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame.GetFrameType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame::GetFrameType
helpviewer_keywords:
- GetFrameType method [.NET Framework debugging]
- ICorDebugInternalFrame::GetFrameType method [.NET Framework debugging]
ms.assetid: da278a29-dc2e-4bf7-96ce-801bdc4d7025
topic_type:
- apiref
ms.openlocfilehash: c675ba4b56cecd1990184cd2f0e805250c3dfeb7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95724885"
---
# <a name="icordebuginternalframegetframetype-method"></a><span data-ttu-id="bbfa2-102">ICorDebugInternalFrame::GetFrameType メソッド</span><span class="sxs-lookup"><span data-stu-id="bbfa2-102">ICorDebugInternalFrame::GetFrameType Method</span></span>

<span data-ttu-id="bbfa2-103">この内部フレームの型を取得します。</span><span class="sxs-lookup"><span data-stu-id="bbfa2-103">Gets the type of this internal frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbfa2-104">構文</span><span class="sxs-lookup"><span data-stu-id="bbfa2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameType (  
    [out] CorDebugInternalFrameType  *pType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bbfa2-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bbfa2-105">Parameters</span></span>  

 `pType`  
 <span data-ttu-id="bbfa2-106">入出力このオブジェクトによって表される内部フレームの種類を示す CorDebugInternalFrameType 列挙値へのポインター `ICorDebugInternalFrame` 。</span><span class="sxs-lookup"><span data-stu-id="bbfa2-106">[out] A pointer to a value of the CorDebugInternalFrameType enumeration that indicates the type of internal frame represented by this `ICorDebugInternalFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bbfa2-107">注釈</span><span class="sxs-lookup"><span data-stu-id="bbfa2-107">Remarks</span></span>  

 <span data-ttu-id="bbfa2-108">内部フレームの種類は STUBFRAME_NONE されません。</span><span class="sxs-lookup"><span data-stu-id="bbfa2-108">The internal frame type will never be STUBFRAME_NONE.</span></span> <span data-ttu-id="bbfa2-109">デバッガーは、認識されない内部フレーム型を正常に無視する必要があります。</span><span class="sxs-lookup"><span data-stu-id="bbfa2-109">Debuggers should gracefully ignore unrecognized internal frame types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbfa2-110">要件</span><span class="sxs-lookup"><span data-stu-id="bbfa2-110">Requirements</span></span>  

 <span data-ttu-id="bbfa2-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="bbfa2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bbfa2-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bbfa2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bbfa2-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bbfa2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bbfa2-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bbfa2-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
