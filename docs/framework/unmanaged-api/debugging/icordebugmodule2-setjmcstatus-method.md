---
title: ICorDebugModule2::SetJMCStatus メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::SetJMCStatus
helpviewer_keywords:
- SetJMCStatus method, ICorDebugModule2 interface [.NET Framework debugging]
- ICorDebugModule2::SetJMCStatus method [.NET Framework debugging]
ms.assetid: 8c6d2089-4dbb-4715-b9e9-2a4491c8c9ce
topic_type:
- apiref
ms.openlocfilehash: cfa6df7a812559f05a4c57381a5007c9c90238e1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709649"
---
# <a name="icordebugmodule2setjmcstatus-method"></a><span data-ttu-id="42421-102">ICorDebugModule2::SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="42421-102">ICorDebugModule2::SetJMCStatus Method</span></span>

<span data-ttu-id="42421-103">この ICorDebugModule2 内のすべてのクラスのすべてのメソッドのマイコードのみ (JMC) の状態を、指定した値に設定し `pTokens` ます。ただし、逆の値に設定されている配列内のすべてのメソッドを除きます。</span><span class="sxs-lookup"><span data-stu-id="42421-103">Sets the Just My Code (JMC) status of all methods of all the classes in this ICorDebugModule2 to the specified value, except those in the `pTokens` array, which it sets to the opposite value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="42421-104">構文</span><span class="sxs-lookup"><span data-stu-id="42421-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL                        bIsJustMyCode,  
    [in] ULONG32                     cTokens,  
    [in, size_is(cTokens)] mdToken   pTokens[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="42421-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="42421-105">Parameters</span></span>  

 `bIsJustMycode`  
 <span data-ttu-id="42421-106">からコードを `true` デバッグする場合はに設定し、それ以外の場合はに設定 `false` します。</span><span class="sxs-lookup"><span data-stu-id="42421-106">[in] Set to `true` if the code is to be debugged; otherwise, set to `false`.</span></span>  
  
 `cTokens`  
 <span data-ttu-id="42421-107">[in] `pTokens` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="42421-107">[in] The size of the `pTokens` array.</span></span>  
  
 `pTokens`  
 <span data-ttu-id="42421-108">から値の配列 `mdToken` 。各値は、JMC の状態が! に設定されるメソッドを参照し `bIsJustMycode` ます。</span><span class="sxs-lookup"><span data-stu-id="42421-108">[in] An array of `mdToken` values, each of which refers to a method that will have its JMC status set to !`bIsJustMycode`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="42421-109">注釈</span><span class="sxs-lookup"><span data-stu-id="42421-109">Remarks</span></span>  

 <span data-ttu-id="42421-110">配列に指定されている各メソッドの JMC の状態 `pTokens` は、値の逆に設定され `bIsJustMycode` ます。</span><span class="sxs-lookup"><span data-stu-id="42421-110">The JMC status of each method that is specified in the `pTokens` array is set to the opposite of the `bIsJustMycode` value.</span></span> <span data-ttu-id="42421-111">このモジュール内の他のすべてのメソッドの状態は、値に設定され `bIsJustMycode` ます。</span><span class="sxs-lookup"><span data-stu-id="42421-111">The status of all other methods in this module is set to the `bIsJustMycode` value.</span></span>  
  
 <span data-ttu-id="42421-112">メソッドは、 `SetJMCStatus` このモジュール内の以前のすべての JMC 設定を消去します。</span><span class="sxs-lookup"><span data-stu-id="42421-112">The `SetJMCStatus` method erases all previous JMC settings in this module.</span></span>  
  
 <span data-ttu-id="42421-113">`SetJMCStatus`すべての関数が正常に設定されている場合、メソッドは S_OK HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="42421-113">The `SetJMCStatus` method returns an S_OK HRESULT if all functions were set successfully.</span></span> <span data-ttu-id="42421-114">マークされている一部の関数がデバッグ可能でない場合は、CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT が返され `true` ます。</span><span class="sxs-lookup"><span data-stu-id="42421-114">It returns a CORDBG_E_FUNCTION_NOT_DEBUGGABLE HRESULT if some functions that are marked `true` are not debuggable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="42421-115">要件</span><span class="sxs-lookup"><span data-stu-id="42421-115">Requirements</span></span>  

 <span data-ttu-id="42421-116">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="42421-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="42421-117">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="42421-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="42421-118">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="42421-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="42421-119">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="42421-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
