---
title: CodeChunkInfo 構造体
ms.date: 03/30/2017
api_name:
- CodeChunkInfo
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CodeChunkInfo
helpviewer_keywords:
- CodeChunkInfo structure [.NET Framework debugging]
ms.assetid: 0f482454-8517-48de-ba7a-d7aedab13bb5
topic_type:
- apiref
ms.openlocfilehash: 11197246662a93f6a8b57c6e61e49505a9999d00
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727433"
---
# <a name="codechunkinfo-structure"></a><span data-ttu-id="aa7f1-102">CodeChunkInfo 構造体</span><span class="sxs-lookup"><span data-stu-id="aa7f1-102">CodeChunkInfo Structure</span></span>

<span data-ttu-id="aa7f1-103">メモリ内のコードの単一のチャンクを表しています。</span><span class="sxs-lookup"><span data-stu-id="aa7f1-103">Represents a single chunk of code in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa7f1-104">構文</span><span class="sxs-lookup"><span data-stu-id="aa7f1-104">Syntax</span></span>  
  
```cpp  
typedef struct _CodeChunkInfo {  
    CORDB_ADDRESS startAddr;  
    ULONG32       length;  
} CodeChunkInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="aa7f1-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="aa7f1-105">Members</span></span>  
  
|<span data-ttu-id="aa7f1-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="aa7f1-106">Member</span></span>|<span data-ttu-id="aa7f1-107">説明</span><span class="sxs-lookup"><span data-stu-id="aa7f1-107">Description</span></span>|  
|------------|-----------------|  
|`startAddr`|<span data-ttu-id="aa7f1-108">`CORDB_ADDRESS`チャンクの開始アドレスを示す値です。</span><span class="sxs-lookup"><span data-stu-id="aa7f1-108">A `CORDB_ADDRESS` value that specifies the starting address of the chunk.</span></span>|  
|`length`|<span data-ttu-id="aa7f1-109">チャンクのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="aa7f1-109">The size, in bytes, of the chunk.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aa7f1-110">注釈</span><span class="sxs-lookup"><span data-stu-id="aa7f1-110">Remarks</span></span>  

 <span data-ttu-id="aa7f1-111">コードの1つのチャンクは、関数などのコードオブジェクトの一部であるネイティブコードの領域です。</span><span class="sxs-lookup"><span data-stu-id="aa7f1-111">The single chunk of code is a region of native code that is part of a code object such as a function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa7f1-112">要件</span><span class="sxs-lookup"><span data-stu-id="aa7f1-112">Requirements</span></span>  

 <span data-ttu-id="aa7f1-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa7f1-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa7f1-114">**ヘッダー:** CorDebug .idl</span><span class="sxs-lookup"><span data-stu-id="aa7f1-114">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="aa7f1-115">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa7f1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa7f1-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa7f1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa7f1-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa7f1-117">See also</span></span>

- [<span data-ttu-id="aa7f1-118">GetCodeChunks メソッド</span><span class="sxs-lookup"><span data-stu-id="aa7f1-118">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
- [<span data-ttu-id="aa7f1-119">デバッグ構造体</span><span class="sxs-lookup"><span data-stu-id="aa7f1-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="aa7f1-120">デバッグ</span><span class="sxs-lookup"><span data-stu-id="aa7f1-120">Debugging</span></span>](index.md)
