---
title: ICorDebugProcess::GetID メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetID
helpviewer_keywords:
- GetID method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetID method [.NET Framework debugging]
ms.assetid: b0ba8453-fa7e-4c14-93e5-335409cd4a47
topic_type:
- apiref
ms.openlocfilehash: 65d9c3688f3a41312a17e6058f73596fc2503dd4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95694985"
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="2f3a4-102">ICorDebugProcess::GetID メソッド</span><span class="sxs-lookup"><span data-stu-id="2f3a4-102">ICorDebugProcess::GetID Method</span></span>

<span data-ttu-id="2f3a4-103">プロセスのオペレーティングシステム (OS) ID を取得します。</span><span class="sxs-lookup"><span data-stu-id="2f3a4-103">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f3a4-104">構文</span><span class="sxs-lookup"><span data-stu-id="2f3a4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2f3a4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="2f3a4-105">Parameters</span></span>  

 `pdwProcessId`  
 <span data-ttu-id="2f3a4-106">入出力プロセスの一意の ID。</span><span class="sxs-lookup"><span data-stu-id="2f3a4-106">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f3a4-107">要件</span><span class="sxs-lookup"><span data-stu-id="2f3a4-107">Requirements</span></span>  

 <span data-ttu-id="2f3a4-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f3a4-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f3a4-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f3a4-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f3a4-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f3a4-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f3a4-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f3a4-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
