---
title: ICorDebugProcess5::GetGCHeapInformation メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
ms.openlocfilehash: 43054a71445193bae7a74e0ed6785cccd1d02dc2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95670993"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="6d9df-102">ICorDebugProcess5::GetGCHeapInformation メソッド</span><span class="sxs-lookup"><span data-stu-id="6d9df-102">ICorDebugProcess5::GetGCHeapInformation Method</span></span>

<span data-ttu-id="6d9df-103">現在列挙可能であるかどうかなど、ガベージコレクションヒープに関する一般的な情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="6d9df-103">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d9df-104">構文</span><span class="sxs-lookup"><span data-stu-id="6d9df-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d9df-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6d9df-105">Parameters</span></span>  

 `pHeapInfo`  
 <span data-ttu-id="6d9df-106">入出力ガベージコレクションヒープに関する全般的な情報を提供する [COR_HEAPINFO](cor-heapinfo-structure.md) 値へのポインター。</span><span class="sxs-lookup"><span data-stu-id="6d9df-106">[out] A pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d9df-107">注釈</span><span class="sxs-lookup"><span data-stu-id="6d9df-107">Remarks</span></span>  

 <span data-ttu-id="6d9df-108">`ICorDebugProcess5::GetGCHeapInformation`プロセス内のガベージコレクション構造が現在有効であることを確認するには、ヒープまたは個々のヒープ領域を列挙する前に、メソッドを呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="6d9df-108">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="6d9df-109">コレクションの実行中にガベージコレクションヒープをウォークすることはできません。</span><span class="sxs-lookup"><span data-stu-id="6d9df-109">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="6d9df-110">それ以外の場合、列挙体は無効なガベージコレクション構造をキャプチャする可能性があります。</span><span class="sxs-lookup"><span data-stu-id="6d9df-110">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d9df-111">要件</span><span class="sxs-lookup"><span data-stu-id="6d9df-111">Requirements</span></span>  

 <span data-ttu-id="6d9df-112">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6d9df-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d9df-113">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d9df-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d9df-114">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d9df-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d9df-115">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d9df-115">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d9df-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d9df-116">See also</span></span>

- [<span data-ttu-id="6d9df-117">ICorDebugProcess5 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d9df-117">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="6d9df-118">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d9df-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
