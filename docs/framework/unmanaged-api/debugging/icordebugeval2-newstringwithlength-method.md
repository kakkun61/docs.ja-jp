---
title: ICorDebugEval2::NewStringWithLength メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
ms.openlocfilehash: e5bab32f6d18c87b030f484a47bc3f1d525d2338
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729630"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="cacdc-102">ICorDebugEval2::NewStringWithLength メソッド</span><span class="sxs-lookup"><span data-stu-id="cacdc-102">ICorDebugEval2::NewStringWithLength Method</span></span>

<span data-ttu-id="cacdc-103">指定したコンテンツを使用して、指定した長さの文字列を作成します。</span><span class="sxs-lookup"><span data-stu-id="cacdc-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cacdc-104">構文</span><span class="sxs-lookup"><span data-stu-id="cacdc-104">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cacdc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="cacdc-105">Parameters</span></span>  

 `string`  
 <span data-ttu-id="cacdc-106">から文字列値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="cacdc-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="cacdc-107">から文字列の長さ。</span><span class="sxs-lookup"><span data-stu-id="cacdc-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cacdc-108">注釈</span><span class="sxs-lookup"><span data-stu-id="cacdc-108">Remarks</span></span>  

 <span data-ttu-id="cacdc-109">文字列の末尾の null 文字がマネージ文字列に含まれると想定される場合、メソッドの呼び出し元は、 `NewStringWithLength` 文字列の長さに末尾の null 文字が含まれていることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="cacdc-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="cacdc-110">文字列は常に、スレッドが現在実行されているアプリケーションドメインで作成されます。</span><span class="sxs-lookup"><span data-stu-id="cacdc-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cacdc-111">要件</span><span class="sxs-lookup"><span data-stu-id="cacdc-111">Requirements</span></span>  

 <span data-ttu-id="cacdc-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="cacdc-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cacdc-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cacdc-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cacdc-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cacdc-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cacdc-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cacdc-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
