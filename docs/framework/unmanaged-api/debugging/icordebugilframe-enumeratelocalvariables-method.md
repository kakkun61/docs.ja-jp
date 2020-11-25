---
title: ICorDebugILFrame::EnumerateLocalVariables メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame.EnumerateLocalVariables
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame::EnumerateLocalVariables
helpviewer_keywords:
- EnumerateLocalVariables method [.NET Framework debugging]
- ICorDebugILFrame::EnumerateLocalVariables method [.NET Framework debugging]
ms.assetid: 1a67fa1b-2419-4cd0-aad4-6f46a0719b4b
topic_type:
- apiref
ms.openlocfilehash: 968ceec53aade3d04c500c8247d397ffb71382c1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95703201"
---
# <a name="icordebugilframeenumeratelocalvariables-method"></a><span data-ttu-id="f027f-102">ICorDebugILFrame::EnumerateLocalVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="f027f-102">ICorDebugILFrame::EnumerateLocalVariables Method</span></span>

<span data-ttu-id="f027f-103">このフレーム内のローカル変数の列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="f027f-103">Gets an enumerator for the local variables in this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f027f-104">構文</span><span class="sxs-lookup"><span data-stu-id="f027f-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateLocalVariables(
    [out] ICorDebugValueEnum    **ppValueEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f027f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f027f-105">Parameters</span></span>  

 `ppValueEnum`  
 <span data-ttu-id="f027f-106">[出力] このフレームのローカル変数の列挙子である ICorDebugValueEnum オブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f027f-106">[out] A pointer to the address of an ICorDebugValueEnum object that is the enumerator for the local variables in this frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f027f-107">注釈</span><span class="sxs-lookup"><span data-stu-id="f027f-107">Remarks</span></span>  

 <span data-ttu-id="f027f-108">`EnumerateLocalVariables` このテキストボックスオブジェクトで表される呼び出しフレームで使用可能なローカル変数を一覧表示できる列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="f027f-108">`EnumerateLocalVariables` gets an enumerator that can list the local variables available in the call frame that is represented by this ICorDebugILFrame object.</span></span> <span data-ttu-id="f027f-109">この一覧には、一部のローカル変数がアクティブでない可能性があるため、実行中の関数のすべてのローカル変数を含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="f027f-109">The list may not include all of the local variables in the running function, because some of them may not be active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f027f-110">要件</span><span class="sxs-lookup"><span data-stu-id="f027f-110">Requirements</span></span>  

 <span data-ttu-id="f027f-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f027f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f027f-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f027f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f027f-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f027f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f027f-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f027f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
