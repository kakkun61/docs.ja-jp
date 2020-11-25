---
title: ICorDebugAssembly2::IsFullyTrusted メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly2.IsFullyTrusted
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly2::IsFullyTrusted
helpviewer_keywords:
- ICorDebugAssembly2::IsFullyTrusted method [.NET Framework debugging]
- IsFullyTrusted method [.NET Framework debugging]
ms.assetid: 26cbd27d-12bf-444a-8197-ccd14d37dda3
topic_type:
- apiref
ms.openlocfilehash: 8a2a6be0db76f5ee2c7fa67c2038e0a5c845bd0f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719711"
---
# <a name="icordebugassembly2isfullytrusted-method"></a><span data-ttu-id="9b196-102">ICorDebugAssembly2::IsFullyTrusted メソッド</span><span class="sxs-lookup"><span data-stu-id="9b196-102">ICorDebugAssembly2::IsFullyTrusted Method</span></span>

<span data-ttu-id="9b196-103">アセンブリにランタイムセキュリティシステムによる完全信頼が付与されているかどうかを示す値を取得します。</span><span class="sxs-lookup"><span data-stu-id="9b196-103">Gets a value that indicates whether the assembly has been granted full trust by the runtime security system.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b196-104">構文</span><span class="sxs-lookup"><span data-stu-id="9b196-104">Syntax</span></span>  
  
```cpp  
HRESULT IsFullyTrusted(  
    [out] BOOL *pbFullyTrusted  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b196-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9b196-105">Parameters</span></span>  

 `pbFullyTrusted`  
 <span data-ttu-id="9b196-106">[出力] `true` アセンブリにランタイムセキュリティシステムによる完全信頼が付与されている場合は。それ以外の場合は `false` 。</span><span class="sxs-lookup"><span data-stu-id="9b196-106">[out] `true` if the assembly has been granted full trust by the runtime security system; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b196-107">注釈</span><span class="sxs-lookup"><span data-stu-id="9b196-107">Remarks</span></span>  

 <span data-ttu-id="9b196-108">このメソッドは、アセンブリのセキュリティポリシーがまだ解決されていない場合、つまりアセンブリ内のコードがまだ実行されていない場合に、CORDBG_E_NOTREADY の HRESULT を返します。</span><span class="sxs-lookup"><span data-stu-id="9b196-108">This method returns an HRESULT of CORDBG_E_NOTREADY if the security policy for the assembly has not yet been resolved, that is, if no code in the assembly has been run yet.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b196-109">要件</span><span class="sxs-lookup"><span data-stu-id="9b196-109">Requirements</span></span>  

 <span data-ttu-id="9b196-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9b196-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b196-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b196-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b196-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b196-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b196-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b196-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
