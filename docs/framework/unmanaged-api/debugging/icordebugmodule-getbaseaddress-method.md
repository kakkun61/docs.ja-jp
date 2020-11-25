---
title: ICorDebugModule::GetBaseAddress メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetBaseAddress
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetBaseAddress
helpviewer_keywords:
- GetBaseAddress method [.NET Framework debugging]
- ICorDebugModule::GetBaseAddress method [.NET Framework debugging]
ms.assetid: 26a82815-1982-4eb7-92d1-5c3d318d5be4
topic_type:
- apiref
ms.openlocfilehash: 4562318c87b79fba5f3d99860ee438c0144e9aae
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95710247"
---
# <a name="icordebugmodulegetbaseaddress-method"></a><span data-ttu-id="3b7a5-102">ICorDebugModule::GetBaseAddress メソッド</span><span class="sxs-lookup"><span data-stu-id="3b7a5-102">ICorDebugModule::GetBaseAddress Method</span></span>

<span data-ttu-id="3b7a5-103">モジュールのベースアドレスを取得します。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-103">Gets the base address of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b7a5-104">構文</span><span class="sxs-lookup"><span data-stu-id="3b7a5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBaseAddress(  
    [out] CORDB_ADDRESS *pAddress  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b7a5-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="3b7a5-105">Parameters</span></span>  

 `pAddress`  
 <span data-ttu-id="3b7a5-106">入出力 `CORDB_ADDRESS` モジュールのベースアドレスを指定する。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-106">[out] A `CORDB_ADDRESS` that specifies the base address of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3b7a5-107">注釈</span><span class="sxs-lookup"><span data-stu-id="3b7a5-107">Remarks</span></span>  

 <span data-ttu-id="3b7a5-108">モジュールがネイティブイメージの場合 (つまり、モジュールがネイティブイメージジェネレーターによって生成された場合は、NGen.exe)、そのベースアドレスはゼロになります。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-108">If the module is a native image (that is, if the module was produced by the native image generator, NGen.exe), its base address will be zero.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b7a5-109">要件</span><span class="sxs-lookup"><span data-stu-id="3b7a5-109">Requirements</span></span>  

 <span data-ttu-id="3b7a5-110">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b7a5-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b7a5-111">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3b7a5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3b7a5-112">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3b7a5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3b7a5-113">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b7a5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b7a5-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="3b7a5-114">See also</span></span>
