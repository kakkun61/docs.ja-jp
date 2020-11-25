---
title: ICorDebugNativeFrame::GetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.GetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::GetIP
helpviewer_keywords:
- GetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
- ICorDebugNativeFrame::GetIP method [.NET Framework debugging]
ms.assetid: 99f693f3-d3b9-4fd8-9d09-b8efd03f7b67
topic_type:
- apiref
ms.openlocfilehash: c9c0598f8e7b3e8654124f50663c912f3cd61659
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709305"
---
# <a name="icordebugnativeframegetip-method"></a><span data-ttu-id="0471d-102">ICorDebugNativeFrame::GetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="0471d-102">ICorDebugNativeFrame::GetIP Method</span></span>

<span data-ttu-id="0471d-103">命令ポインターが現在設定されているネイティブコードのオフセット位置を取得します。</span><span class="sxs-lookup"><span data-stu-id="0471d-103">Gets the native code offset location to which the instruction pointer is currently set.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0471d-104">構文</span><span class="sxs-lookup"><span data-stu-id="0471d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetIP (  
    [out] ULONG32           *pnOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0471d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0471d-105">Parameters</span></span>  

 `pnOffset`  
 <span data-ttu-id="0471d-106">入出力ネイティブコード内のオフセット位置を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="0471d-106">[out] A pointer to the offset location in the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0471d-107">注釈</span><span class="sxs-lookup"><span data-stu-id="0471d-107">Remarks</span></span>  

 <span data-ttu-id="0471d-108">この "テキストフレーム" によって表されるスタックフレームがアクティブな場合、オフセットは次に実行される命令のアドレスになります。</span><span class="sxs-lookup"><span data-stu-id="0471d-108">If the stack frame that is represented by this "ICorDebugNativeFrame" is active, the offset is the address of the next instruction to be executed.</span></span> <span data-ttu-id="0471d-109">このスタックフレームがアクティブでない場合、オフセットは、スタックフレームが再アクティブ化されたときに実行される次の命令のアドレスになります。</span><span class="sxs-lookup"><span data-stu-id="0471d-109">If this stack frame is not active, the offset is the address of the next instruction to be executed when the stack frame is reactivated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0471d-110">要件</span><span class="sxs-lookup"><span data-stu-id="0471d-110">Requirements</span></span>  

 <span data-ttu-id="0471d-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0471d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0471d-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0471d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0471d-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0471d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0471d-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0471d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0471d-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="0471d-115">See also</span></span>
