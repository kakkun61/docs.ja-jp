---
title: ICorDebugProcess::GetHandle メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
ms.openlocfilehash: 87b7b7381ef53f7e2abebc053b5c9f87f94d96c2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95695063"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="d8b81-102">ICorDebugProcess::GetHandle メソッド</span><span class="sxs-lookup"><span data-stu-id="d8b81-102">ICorDebugProcess::GetHandle Method</span></span>

<span data-ttu-id="d8b81-103">プロセスを処理するハンドルを取得します。</span><span class="sxs-lookup"><span data-stu-id="d8b81-103">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8b81-104">構文</span><span class="sxs-lookup"><span data-stu-id="d8b81-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8b81-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d8b81-105">Parameters</span></span>  

 `phProcessHandle`  
 <span data-ttu-id="d8b81-106">入出力プロセスを指すハンドルであるへのポインター `HPROCESS` 。</span><span class="sxs-lookup"><span data-stu-id="d8b81-106">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8b81-107">注釈</span><span class="sxs-lookup"><span data-stu-id="d8b81-107">Remarks</span></span>  

 <span data-ttu-id="d8b81-108">取得したハンドルは、デバッグインターフェイスによって所有されています。</span><span class="sxs-lookup"><span data-stu-id="d8b81-108">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="d8b81-109">デバッガーは、使用する前にハンドルを複製する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d8b81-109">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8b81-110">要件</span><span class="sxs-lookup"><span data-stu-id="d8b81-110">Requirements</span></span>  

 <span data-ttu-id="d8b81-111">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d8b81-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8b81-112">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8b81-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8b81-113">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8b81-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8b81-114">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8b81-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
