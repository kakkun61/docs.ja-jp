---
title: ICorDebugModuleBreakpoint インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugModuleBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleBreakpoint
helpviewer_keywords:
- ICorDebugModuleBreakpoint interface [.NET Framework debugging]
ms.assetid: 34667162-f314-475f-ae1b-ce9cb0fcbb83
topic_type:
- apiref
ms.openlocfilehash: 14f2b6822744070e649cf9a6722272992c0bf1c8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709519"
---
# <a name="icordebugmodulebreakpoint-interface"></a><span data-ttu-id="99bec-102">ICorDebugModuleBreakpoint インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99bec-102">ICorDebugModuleBreakpoint Interface</span></span>

<span data-ttu-id="99bec-103">特定のモジュールへのアクセスを提供します。</span><span class="sxs-lookup"><span data-stu-id="99bec-103">Provides access to specific modules.</span></span> <span data-ttu-id="99bec-104">このインターフェイスは、ICorDebugBreakpoint インターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="99bec-104">This interface is a subclass of the ICorDebugBreakpoint interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="99bec-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="99bec-105">Methods</span></span>  
  
|<span data-ttu-id="99bec-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="99bec-106">Method</span></span>|<span data-ttu-id="99bec-107">説明</span><span class="sxs-lookup"><span data-stu-id="99bec-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="99bec-108">GetModule メソッド</span><span class="sxs-lookup"><span data-stu-id="99bec-108">GetModule Method</span></span>](icordebugmodulebreakpoint-getmodule-method.md)|<span data-ttu-id="99bec-109">このブレークポイントが設定されているモジュールを参照するモジュールへのインターフェイスポインターを取得します。</span><span class="sxs-lookup"><span data-stu-id="99bec-109">Gets an interface pointer to an ICorDebugModule that references the module where this breakpoint is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99bec-110">注釈</span><span class="sxs-lookup"><span data-stu-id="99bec-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="99bec-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="99bec-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99bec-112">要件</span><span class="sxs-lookup"><span data-stu-id="99bec-112">Requirements</span></span>  

 <span data-ttu-id="99bec-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="99bec-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99bec-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99bec-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99bec-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99bec-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99bec-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99bec-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99bec-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="99bec-117">See also</span></span>

- [<span data-ttu-id="99bec-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="99bec-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
