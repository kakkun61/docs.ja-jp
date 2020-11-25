---
title: ICorDebugAssembly::EnumerateModules メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugAssembly.EnumerateModules
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAssembly::EnumerateModules
helpviewer_keywords:
- ICorDebugAssembly::EnumerateModules method [.NET Framework debugging]
- EnumerateModules method [.NET Framework debugging]
ms.assetid: c7ba51a1-0dd5-4452-b471-232febe0f897
topic_type:
- apiref
ms.openlocfilehash: 6d00d17a5876dd7454b9f89ffa916bc62efb3d0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734128"
---
# <a name="icordebugassemblyenumeratemodules-method"></a><span data-ttu-id="f9a2c-102">ICorDebugAssembly::EnumerateModules メソッド</span><span class="sxs-lookup"><span data-stu-id="f9a2c-102">ICorDebugAssembly::EnumerateModules Method</span></span>

<span data-ttu-id="f9a2c-103">に格納されているモジュールの列挙子を取得し `ICorDebugAssembly` ます。</span><span class="sxs-lookup"><span data-stu-id="f9a2c-103">Gets an enumerator for the modules contained in the `ICorDebugAssembly`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9a2c-104">構文</span><span class="sxs-lookup"><span data-stu-id="f9a2c-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateModules (  
    [out] ICorDebugModuleEnum **ppModules  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9a2c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f9a2c-105">Parameters</span></span>  

 `ppModules`  
 <span data-ttu-id="f9a2c-106">入出力列挙子である、モジュールの列挙型インターフェイスのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="f9a2c-106">[out] A pointer to the address of the ICorDebugModuleEnum interface that is the enumerator.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9a2c-107">要件</span><span class="sxs-lookup"><span data-stu-id="f9a2c-107">Requirements</span></span>  

 <span data-ttu-id="f9a2c-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="f9a2c-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9a2c-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9a2c-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9a2c-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9a2c-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9a2c-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9a2c-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
