---
title: ICorDebugModule::GetSize メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetSize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetSize
helpviewer_keywords:
- GetSize method, ICorDebugModule interface [.NET Framework debugging]
- ICorDebugModule::GetSize method [.NET Framework debugging]
ms.assetid: 5c68375d-145d-46ef-a7c8-2dc4257472de
topic_type:
- apiref
ms.openlocfilehash: 0cfc31839b263c2e8cf44d15439b44ffacccf5bf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709896"
---
# <a name="icordebugmodulegetsize-method"></a><span data-ttu-id="6aba4-102">ICorDebugModule::GetSize メソッド</span><span class="sxs-lookup"><span data-stu-id="6aba4-102">ICorDebugModule::GetSize Method</span></span>

<span data-ttu-id="6aba4-103">モジュールのサイズ (バイト単位) を取得します。</span><span class="sxs-lookup"><span data-stu-id="6aba4-103">Gets the size, in bytes, of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6aba4-104">構文</span><span class="sxs-lookup"><span data-stu-id="6aba4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
    [out] ULONG32 *pcBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6aba4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6aba4-105">Parameters</span></span>  

 `pcBytes`  
 <span data-ttu-id="6aba4-106">入出力モジュールのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="6aba4-106">[out] The size of the module in bytes.</span></span>  
  
 <span data-ttu-id="6aba4-107">モジュールがネイティブイメージジェネレーター (NGen.exe) から生成された場合、モジュールのサイズはゼロになります。</span><span class="sxs-lookup"><span data-stu-id="6aba4-107">If the module was produced from the native image generator (NGen.exe), the size of the module will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6aba4-108">要件</span><span class="sxs-lookup"><span data-stu-id="6aba4-108">Requirements</span></span>  

 <span data-ttu-id="6aba4-109">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6aba4-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6aba4-110">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6aba4-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6aba4-111">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6aba4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6aba4-112">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6aba4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
