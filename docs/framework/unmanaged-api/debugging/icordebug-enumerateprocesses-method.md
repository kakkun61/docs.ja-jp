---
title: ICorDebug::EnumerateProcesses メソッド
ms.date: 03/30/2017
api_name:
- ICorDebug.EnumerateProcesses
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- EnumerateProcesses
helpviewer_keywords:
- EnumerateProcesses method [.NET Framework debugging]
- ICorDebug::EnumerateProcesses method [.NET Framework debugging]
ms.assetid: ba25d166-1d28-4f1d-aca2-de298bbca669
topic_type:
- apiref
ms.openlocfilehash: bf672c90cdbb9e9fb66105820a264a49601b38d7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723455"
---
# <a name="icordebugenumerateprocesses-method"></a><span data-ttu-id="1f725-102">ICorDebug::EnumerateProcesses メソッド</span><span class="sxs-lookup"><span data-stu-id="1f725-102">ICorDebug::EnumerateProcesses Method</span></span>

<span data-ttu-id="1f725-103">デバッグ中のプロセスの列挙子を取得します。</span><span class="sxs-lookup"><span data-stu-id="1f725-103">Gets an enumerator for the processes that are being debugged.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f725-104">構文</span><span class="sxs-lookup"><span data-stu-id="1f725-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateProcesses (  
    [out] ICorDebugProcessEnum      **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f725-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1f725-105">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="1f725-106">デバッグ中のプロセスの列挙子である、のオブジェクトのアドレスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="1f725-106">A pointer to the address of an ICorDebugProcessEnum object that is the enumerator for the processes being debugged.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f725-107">要件</span><span class="sxs-lookup"><span data-stu-id="1f725-107">Requirements</span></span>  

 <span data-ttu-id="1f725-108">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1f725-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f725-109">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f725-109">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f725-110">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f725-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f725-111">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f725-111">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f725-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f725-112">See also</span></span>

- [<span data-ttu-id="1f725-113">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f725-113">ICorDebug Interface</span></span>](icordebug-interface.md)
