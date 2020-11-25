---
title: ICorDebugEval::NewString メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
ms.openlocfilehash: c2d29a0cc344539bf515793c071fe839aa441ebc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729721"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="d53fa-102">ICorDebugEval::NewString メソッド</span><span class="sxs-lookup"><span data-stu-id="d53fa-102">ICorDebugEval::NewString Method</span></span>

<span data-ttu-id="d53fa-103">指定された内容を持つ新しい文字列インスタンスを割り当てます。</span><span class="sxs-lookup"><span data-stu-id="d53fa-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d53fa-104">構文</span><span class="sxs-lookup"><span data-stu-id="d53fa-104">Syntax</span></span>  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d53fa-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d53fa-105">Parameters</span></span>  

 `string`  
 <span data-ttu-id="d53fa-106">から文字列のコンテンツへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d53fa-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d53fa-107">注釈</span><span class="sxs-lookup"><span data-stu-id="d53fa-107">Remarks</span></span>  

 <span data-ttu-id="d53fa-108">文字列は常に、スレッドが現在実行されているアプリケーションドメインで作成されます。</span><span class="sxs-lookup"><span data-stu-id="d53fa-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d53fa-109">要件</span><span class="sxs-lookup"><span data-stu-id="d53fa-109">Requirements</span></span>  

 <span data-ttu-id="d53fa-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d53fa-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d53fa-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d53fa-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d53fa-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d53fa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d53fa-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d53fa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
