---
title: ICorDebugCode2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICorDebugCode2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2
helpviewer_keywords:
- ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type:
- apiref
ms.openlocfilehash: 1e5b92d99d8ae52c88f1517f9c3d7db8e70598ac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720803"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="1bf94-102">ICorDebugCode2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1bf94-102">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="1bf94-103">"コード例" の機能を拡張するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="1bf94-103">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1bf94-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="1bf94-104">Methods</span></span>  
  
|<span data-ttu-id="1bf94-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="1bf94-105">Method</span></span>|<span data-ttu-id="1bf94-106">説明</span><span class="sxs-lookup"><span data-stu-id="1bf94-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1bf94-107">GetCodeChunks メソッド</span><span class="sxs-lookup"><span data-stu-id="1bf94-107">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="1bf94-108">このコード オブジェクトを構成しているコード チャンクを取得します。</span><span class="sxs-lookup"><span data-stu-id="1bf94-108">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="1bf94-109">GetCompilerFlags メソッド</span><span class="sxs-lookup"><span data-stu-id="1bf94-109">GetCompilerFlags Method</span></span>](icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="1bf94-110">このコード オブジェクトが Just-In-Time (JIT) コンパイルされたとき、またはネイティブ イメージ ジェネレーター (Ngen.exe) を使用して生成されたときの条件を指定するフラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="1bf94-110">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1bf94-111">注釈</span><span class="sxs-lookup"><span data-stu-id="1bf94-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1bf94-112">このインターフェイスは、コンピューター間またはプロセス間でのリモート呼び出しをサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="1bf94-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1bf94-113">要件</span><span class="sxs-lookup"><span data-stu-id="1bf94-113">Requirements</span></span>  

 <span data-ttu-id="1bf94-114">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1bf94-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1bf94-115">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1bf94-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1bf94-116">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1bf94-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1bf94-117">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1bf94-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bf94-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="1bf94-118">See also</span></span>

- [<span data-ttu-id="1bf94-119">ICorDebugCode3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1bf94-119">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="1bf94-120">デバッグのインターフェイス</span><span class="sxs-lookup"><span data-stu-id="1bf94-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
