---
title: ISymUnmanagedWriter4 インターフェイス
ms.date: 03/30/2017
ms.assetid: 4af5e8c0-987d-405e-b934-8b9e70fcae6e
ms.openlocfilehash: c2b57897e4f0e8b23337302f344065d79677e0c4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725808"
---
# <a name="isymunmanagedwriter4-interface"></a><span data-ttu-id="e6ff7-102">ISymUnmanagedWriter4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6ff7-102">ISymUnmanagedWriter4 Interface</span></span>

<span data-ttu-id="e6ff7-103">ISymUnmanagedWriter4 インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="e6ff7-103">ISymUnmanagedWriter4 interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6ff7-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e6ff7-104">Syntax</span></span>  
  
```idl  
[object,uuid(BC7E3F53-F458-4C23-9DBD-A189E6E96594),pointer_default(unique)]interface ISymUnmanagedWriter4 : ISymUnmanagedWriter3  
```  
  
## <a name="methods"></a><span data-ttu-id="e6ff7-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="e6ff7-105">Methods</span></span>  

 <span data-ttu-id="e6ff7-106">このインターフェイスには、次のメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e6ff7-106">This interface contains the following methods:</span></span>  
  
|<span data-ttu-id="e6ff7-107">メソッド</span><span class="sxs-lookup"><span data-stu-id="e6ff7-107">Method</span></span>|<span data-ttu-id="e6ff7-108">説明</span><span class="sxs-lookup"><span data-stu-id="e6ff7-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e6ff7-109">GetDebugInfoWithPadding メソッド</span><span class="sxs-lookup"><span data-stu-id="e6ff7-109">GetDebugInfoWithPadding Method</span></span>](isymunmanagedwriter4-getdebuginfowithpadding-method.md)|<span data-ttu-id="e6ff7-110">関数は [GetDebugInfo メソッド](isymunmanagedwriter-getdebuginfo-method.md) と同じですが、文字列データを固定サイズにするために、終端の null 文字の後にパス文字列がゼロで埋め込まれる点が異なり `MAX_PATH` ます。</span><span class="sxs-lookup"><span data-stu-id="e6ff7-110">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="e6ff7-111">埋め込みは、パス文字列の長さがより小さい場合にのみ指定 `MAX_PATH` します。</span><span class="sxs-lookup"><span data-stu-id="e6ff7-111">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span><br /><br /> <span data-ttu-id="e6ff7-112">これにより、PE ファイルを区別するツールを簡単に記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e6ff7-112">This makes it easier to write tools that difference PE files.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e6ff7-113">要件</span><span class="sxs-lookup"><span data-stu-id="e6ff7-113">Requirements</span></span>  

 <span data-ttu-id="e6ff7-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="e6ff7-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6ff7-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="e6ff7-115">See also</span></span>

- [<span data-ttu-id="e6ff7-116">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6ff7-116">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="e6ff7-117">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e6ff7-117">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
