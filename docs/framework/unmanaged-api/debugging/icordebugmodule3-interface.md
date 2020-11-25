---
title: ICorDebugModule3 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugModule3
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3
helpviewer_keywords:
- ICorDebugModule3 interface [.NET Framework debugging]
ms.assetid: 0b69f945-263a-4e11-8512-89d27f6ea296
topic_type:
- apiref
ms.openlocfilehash: 543a1a3c79b6cf3eb799da5844f35286dfa91940
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709558"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="e8db7-102">ICorDebugModule3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e8db7-102">ICorDebugModule3 Interface</span></span>

<span data-ttu-id="e8db7-103">動的モジュールのシンボル リーダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="e8db7-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8db7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e8db7-104">Syntax</span></span>  
  
```cpp  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e8db7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e8db7-105">Methods</span></span>  
  
|<span data-ttu-id="e8db7-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="e8db7-106">Method</span></span>|<span data-ttu-id="e8db7-107">説明</span><span class="sxs-lookup"><span data-stu-id="e8db7-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e8db7-108">ICorDebugModule3::CreateReaderForInMemorySymbols メソッド</span><span class="sxs-lookup"><span data-stu-id="e8db7-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="e8db7-109">動的モジュールのシンボルリーダー (通常は [ISymUnmanagedReader インターフェイス](../diagnostics/isymunmanagedreader-interface.md)) を作成します。</span><span class="sxs-lookup"><span data-stu-id="e8db7-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8db7-110">注釈</span><span class="sxs-lookup"><span data-stu-id="e8db7-110">Remarks</span></span>  

 <span data-ttu-id="e8db7-111">このインターフェイスは、"ICorDebugModule2" インターフェイスと "" インターフェイスを論理的に拡張します。</span><span class="sxs-lookup"><span data-stu-id="e8db7-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8db7-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="e8db7-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8db7-113">要件</span><span class="sxs-lookup"><span data-stu-id="e8db7-113">Requirements</span></span>  

 <span data-ttu-id="e8db7-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e8db7-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8db7-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e8db7-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8db7-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e8db7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8db7-117">**.NET Framework のバージョン:** 4.5、4、3.5 SP1</span><span class="sxs-lookup"><span data-stu-id="e8db7-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="e8db7-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="e8db7-118">See also</span></span>

- [<span data-ttu-id="e8db7-119">ICorDebugRemoteTarget インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e8db7-119">ICorDebugRemoteTarget Interface</span></span>](icordebugremotetarget-interface.md)
- [<span data-ttu-id="e8db7-120">ICorDebug インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e8db7-120">ICorDebug Interface</span></span>](icordebug-interface.md)

- [<span data-ttu-id="e8db7-121">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="e8db7-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
