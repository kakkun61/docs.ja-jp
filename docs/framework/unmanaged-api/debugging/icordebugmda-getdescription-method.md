---
title: ICorDebugMDA::GetDescription メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetDescription
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type:
- apiref
ms.openlocfilehash: cb1e0f2bc597b48496dc362c9d7a364421c68a87
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681848"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="59175-102">ICorDebugMDA::GetDescription メソッド</span><span class="sxs-lookup"><span data-stu-id="59175-102">ICorDebugMDA::GetDescription Method</span></span>

<span data-ttu-id="59175-103">によって表されるマネージデバッグアシスタント (MDA) の説明を含む文字列を [取得します](icordebugmda-interface.md)。</span><span class="sxs-lookup"><span data-stu-id="59175-103">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59175-104">構文</span><span class="sxs-lookup"><span data-stu-id="59175-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="59175-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="59175-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="59175-106">から説明を格納する文字列バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="59175-106">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="59175-107">入出力文字列バッファーで返されたバイト数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="59175-107">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="59175-108">入出力MDA の説明を格納している文字列バッファー。</span><span class="sxs-lookup"><span data-stu-id="59175-108">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59175-109">注釈</span><span class="sxs-lookup"><span data-stu-id="59175-109">Remarks</span></span>  

 <span data-ttu-id="59175-110">文字列の長さは0にすることができます。</span><span class="sxs-lookup"><span data-stu-id="59175-110">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="59175-111">要件</span><span class="sxs-lookup"><span data-stu-id="59175-111">Requirements</span></span>  

 <span data-ttu-id="59175-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="59175-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="59175-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="59175-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="59175-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="59175-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="59175-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="59175-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="59175-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="59175-116">See also</span></span>

- [<span data-ttu-id="59175-117">ICorDebugMDA インターフェイス</span><span class="sxs-lookup"><span data-stu-id="59175-117">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="59175-118">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="59175-118">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
