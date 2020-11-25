---
title: ICorDebugInternalFrame インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugInternalFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugInternalFrame
helpviewer_keywords:
- ICorDebugInternalFrame interface [.NET Framework debugging]
ms.assetid: bb4772ca-0d54-4185-b738-7a6ffe9ea85a
topic_type:
- apiref
ms.openlocfilehash: b7e738f06f9a9a06caedec2bdd0de4ab57f6d9b3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719724"
---
# <a name="icordebuginternalframe-interface"></a><span data-ttu-id="292d2-102">ICorDebugInternalFrame インターフェイス</span><span class="sxs-lookup"><span data-stu-id="292d2-102">ICorDebugInternalFrame Interface</span></span>

<span data-ttu-id="292d2-103">スタック上のランタイム内部フレームを表します。</span><span class="sxs-lookup"><span data-stu-id="292d2-103">Represents a runtime-internal frame on the stack.</span></span> <span data-ttu-id="292d2-104">このインターフェイスは、テキストボックスのインターフェイスのサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="292d2-104">This interface is a subclass of the ICorDebugFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="292d2-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="292d2-105">Methods</span></span>  
  
|<span data-ttu-id="292d2-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="292d2-106">Method</span></span>|<span data-ttu-id="292d2-107">説明</span><span class="sxs-lookup"><span data-stu-id="292d2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="292d2-108">GetFrameType メソッド</span><span class="sxs-lookup"><span data-stu-id="292d2-108">GetFrameType Method</span></span>](icordebuginternalframe-getframetype-method.md)|<span data-ttu-id="292d2-109">この内部フレームの型を取得します。</span><span class="sxs-lookup"><span data-stu-id="292d2-109">Gets the type of this internal frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="292d2-110">注釈</span><span class="sxs-lookup"><span data-stu-id="292d2-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="292d2-111">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="292d2-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="292d2-112">要件</span><span class="sxs-lookup"><span data-stu-id="292d2-112">Requirements</span></span>  

 <span data-ttu-id="292d2-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="292d2-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="292d2-114">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="292d2-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="292d2-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="292d2-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="292d2-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="292d2-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="292d2-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="292d2-117">See also</span></span>

- [<span data-ttu-id="292d2-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="292d2-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
