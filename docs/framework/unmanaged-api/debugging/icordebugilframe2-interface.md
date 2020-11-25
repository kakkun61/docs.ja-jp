---
title: ICorDebugILFrame2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugILFrame2
helpviewer_keywords:
- ICorDebugILFrame2 interface [.NET Framework debugging]
ms.assetid: f94b9d53-d8f8-4424-a95e-53a1bfd26e4a
topic_type:
- apiref
ms.openlocfilehash: 3ada9e19bb1a92b3bd7e41340b99bf81b651dd37
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725015"
---
# <a name="icordebugilframe2-interface"></a><span data-ttu-id="40285-102">ICorDebugILFrame2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="40285-102">ICorDebugILFrame2 Interface</span></span>

<span data-ttu-id="40285-103">モジュールの論理拡張機能インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="40285-103">A logical extension of the ICorDebugILFrame interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40285-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="40285-104">Methods</span></span>  
  
|<span data-ttu-id="40285-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="40285-105">Method</span></span>|<span data-ttu-id="40285-106">説明</span><span class="sxs-lookup"><span data-stu-id="40285-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40285-107">EnumerateTypeParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="40285-107">EnumerateTypeParameters Method</span></span>](icordebugilframe2-enumeratetypeparameters-method.md)|<span data-ttu-id="40285-108">このフレームのパラメーターを格納している、テキスト型の型の列挙体オブジェクトを取得し <xref:System.Type> ます。</span><span class="sxs-lookup"><span data-stu-id="40285-108">Gets an ICorDebugTypeEnum object that contains the <xref:System.Type> parameters in this frame.</span></span>|  
|[<span data-ttu-id="40285-109">RemapFunction メソッド</span><span class="sxs-lookup"><span data-stu-id="40285-109">RemapFunction Method</span></span>](icordebugilframe2-remapfunction-method.md)|<span data-ttu-id="40285-110">新しい MSIL オフセットを指定して、編集された関数を再マップします。</span><span class="sxs-lookup"><span data-stu-id="40285-110">Remaps an edited function by specifying the new MSIL offset.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40285-111">注釈</span><span class="sxs-lookup"><span data-stu-id="40285-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="40285-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="40285-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40285-113">要件</span><span class="sxs-lookup"><span data-stu-id="40285-113">Requirements</span></span>  

 <span data-ttu-id="40285-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="40285-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40285-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40285-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40285-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40285-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40285-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40285-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40285-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="40285-118">See also</span></span>

- [<span data-ttu-id="40285-119">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="40285-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
