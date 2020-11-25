---
title: ICorDebugNativeFrame::CanSetIP メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugNativeFrame.CanSetIP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugNativeFrame::CanSetIP
helpviewer_keywords:
- ICorDebugNativeFrame::CanSetIP method [.NET Framework debugging]
- CanSetIP method, ICorDebugNativeFrame interface [.NET Framework debugging]
ms.assetid: 13258ac6-f4e4-4f66-8fc3-f1244417a3c3
topic_type:
- apiref
ms.openlocfilehash: 194065e53d550c9bbd0486de54462309a4d9ffa1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695739"
---
# <a name="icordebugnativeframecansetip-method"></a><span data-ttu-id="4e512-102">ICorDebugNativeFrame::CanSetIP メソッド</span><span class="sxs-lookup"><span data-stu-id="4e512-102">ICorDebugNativeFrame::CanSetIP Method</span></span>

<span data-ttu-id="4e512-103">命令ポインター (IP) をネイティブコード内の指定されたオフセット位置に安全に設定できるかどうかを示す HRESULT を取得します。</span><span class="sxs-lookup"><span data-stu-id="4e512-103">Gets an HRESULT that indicates whether it is safe to set the instruction pointer (IP) to the specified offset location in native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4e512-104">構文</span><span class="sxs-lookup"><span data-stu-id="4e512-104">Syntax</span></span>  
  
```cpp  
HRESULT CanSetIP (  
    [in] ULONG32            nOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4e512-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4e512-105">Parameters</span></span>  

 `nOffset`  
 <span data-ttu-id="4e512-106">から命令ポインターに必要な設定。</span><span class="sxs-lookup"><span data-stu-id="4e512-106">[in] The desired setting for the instruction pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4e512-107">注釈</span><span class="sxs-lookup"><span data-stu-id="4e512-107">Remarks</span></span>  

 <span data-ttu-id="4e512-108">次のメソッドを使用して、 `CanSetIP` [テキストボックス:: SetIP](icordebugnativeframe-setip-method.md) メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4e512-108">Use the `CanSetIP` method prior to calling the [ICorDebugNativeFrame::SetIP](icordebugnativeframe-setip-method.md) method.</span></span> <span data-ttu-id="4e512-109">が `CanSetIP` S_OK 以外の HRESULT を返した場合でもを呼び出すことはでき `ICorDebugNativeFrame::SetIP` ますが、デバッガーがデバッグ中のコードの安全かつ適切な実行を継続する保証はありません。</span><span class="sxs-lookup"><span data-stu-id="4e512-109">If `CanSetIP` returns any HRESULT other than S_OK, you can still invoke `ICorDebugNativeFrame::SetIP`, but there is no guarantee that the debugger will continue the safe and correct execution of the code being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4e512-110">要件</span><span class="sxs-lookup"><span data-stu-id="4e512-110">Requirements</span></span>  

 <span data-ttu-id="4e512-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4e512-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4e512-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4e512-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4e512-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4e512-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4e512-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4e512-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4e512-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="4e512-115">See also</span></span>
