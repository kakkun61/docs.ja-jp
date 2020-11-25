---
title: ICorDebugStringValue::GetString メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetString
helpviewer_keywords:
- ICorDebugStringValue::GetString method [.NET Framework debugging]
- GetString method, ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: 2b94bda7-09ee-435d-91b9-c4e31af1896c
topic_type:
- apiref
ms.openlocfilehash: 9051fa612bef3fbd817ff7bdadbd52c96ade5b7f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95697104"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="ae5b3-102">ICorDebugStringValue::GetString メソッド</span><span class="sxs-lookup"><span data-stu-id="ae5b3-102">ICorDebugStringValue::GetString Method</span></span>

<span data-ttu-id="ae5b3-103">このによって参照される文字列を取得します。</span><span class="sxs-lookup"><span data-stu-id="ae5b3-103">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ae5b3-104">構文</span><span class="sxs-lookup"><span data-stu-id="ae5b3-104">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]
        WCHAR       szString[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ae5b3-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ae5b3-105">Parameters</span></span>  

 `cchString`  
 <span data-ttu-id="ae5b3-106">[in] `szString` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="ae5b3-106">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="ae5b3-107">入出力配列で返された文字数へのポインター `szString` 。</span><span class="sxs-lookup"><span data-stu-id="ae5b3-107">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="ae5b3-108">入出力取得した文字列を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="ae5b3-108">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ae5b3-109">要件</span><span class="sxs-lookup"><span data-stu-id="ae5b3-109">Requirements</span></span>  

 <span data-ttu-id="ae5b3-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ae5b3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ae5b3-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ae5b3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ae5b3-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ae5b3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ae5b3-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ae5b3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
