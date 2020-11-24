---
title: ISymUnmanagedWriter3 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter3
helpviewer_keywords:
- ISymUnmanagedWriter3 interface [.NET Framework debugging]
ms.assetid: a034c21e-e371-4360-b470-29e88288948f
topic_type:
- apiref
ms.openlocfilehash: dfc2e39a6a39e7386bd7358d422d5c6978ec42ec
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683291"
---
# <a name="isymunmanagedwriter3-interface"></a><span data-ttu-id="9d924-102">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9d924-102">ISymUnmanagedWriter3 Interface</span></span>

<span data-ttu-id="9d924-103">シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文スコープ、変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="9d924-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span> <span data-ttu-id="9d924-104">このインターフェイスは、 [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="9d924-104">This interface extends the [ISymUnmanagedWriter](isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d924-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="9d924-105">Methods</span></span>  
  
|<span data-ttu-id="9d924-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="9d924-106">Method</span></span>|<span data-ttu-id="9d924-107">説明</span><span class="sxs-lookup"><span data-stu-id="9d924-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d924-108">Commit メソッド</span><span class="sxs-lookup"><span data-stu-id="9d924-108">Commit Method</span></span>](isymunmanagedwriter3-commit-method.md)|<span data-ttu-id="9d924-109">これまでに書き込まれた変更をストリームにコミットします。</span><span class="sxs-lookup"><span data-stu-id="9d924-109">Commits the changes written so far to the stream.</span></span>|  
|[<span data-ttu-id="9d924-110">OpenMethod2 メソッド</span><span class="sxs-lookup"><span data-stu-id="9d924-110">OpenMethod2 Method</span></span>](isymunmanagedwriter3-openmethod2-method.md)|<span data-ttu-id="9d924-111">メソッドを開き、イメージ内の実際のセクションオフセットを提供します。</span><span class="sxs-lookup"><span data-stu-id="9d924-111">Opens a method and provides its real section offset in the image.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9d924-112">要件</span><span class="sxs-lookup"><span data-stu-id="9d924-112">Requirements</span></span>  

 <span data-ttu-id="9d924-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="9d924-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d924-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d924-114">See also</span></span>

- [<span data-ttu-id="9d924-115">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9d924-115">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="9d924-116">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9d924-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="9d924-117">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9d924-117">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
