---
title: ICorDebugClass2::SetJMCStatus メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
ms.openlocfilehash: 1db2c9b5e65ae150f05242172f5ea16db433bbb5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95717826"
---
# <a name="icordebugclass2setjmcstatus-method"></a><span data-ttu-id="92da9-102">ICorDebugClass2::SetJMCStatus メソッド</span><span class="sxs-lookup"><span data-stu-id="92da9-102">ICorDebugClass2::SetJMCStatus Method</span></span>

<span data-ttu-id="92da9-103">クラスの各メソッドについて、メソッドがユーザー定義のコードかどうかを示す値を設定します。</span><span class="sxs-lookup"><span data-stu-id="92da9-103">For each method of the class, sets a value that indicates whether the method is user-defined code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92da9-104">構文</span><span class="sxs-lookup"><span data-stu-id="92da9-104">Syntax</span></span>  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92da9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="92da9-105">Parameters</span></span>  

 `bIsJustMyCode`  
 <span data-ttu-id="92da9-106">から `true` メソッドがユーザー定義コードであることを示す場合はに設定します。それ以外の場合はに設定 `false` します。</span><span class="sxs-lookup"><span data-stu-id="92da9-106">[in] Set to `true` to indicate that the method is user-defined code; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92da9-107">注釈</span><span class="sxs-lookup"><span data-stu-id="92da9-107">Remarks</span></span>  

 <span data-ttu-id="92da9-108">マイコードのみ (JMC) のステッパは、ユーザー定義ではないコードをスキップします。</span><span class="sxs-lookup"><span data-stu-id="92da9-108">A just-my-code (JMC) stepper will skip non-user-defined code.</span></span> <span data-ttu-id="92da9-109">ユーザー定義コードは、デバッグ可能なコードのサブセットである必要があります。</span><span class="sxs-lookup"><span data-stu-id="92da9-109">User-defined code must be a subset of debuggable code.</span></span>  
  
 <span data-ttu-id="92da9-110">`SetJMCStatus` は、他のすべてのメソッドの値が正常に設定された場合でも、メソッドの値の設定に失敗した場合に S_FALSE の HRESULT 値を返します。</span><span class="sxs-lookup"><span data-stu-id="92da9-110">`SetJMCStatus` returns an HRESULT value of S_FALSE if it fails to set the value for any method, even if it successfully sets the value for all other methods.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92da9-111">要件</span><span class="sxs-lookup"><span data-stu-id="92da9-111">Requirements</span></span>  

 <span data-ttu-id="92da9-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="92da9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92da9-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92da9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92da9-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92da9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92da9-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92da9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
