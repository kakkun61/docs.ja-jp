---
title: ISymUnmanagedWriter::Abort メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.Abort
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::Abort
helpviewer_keywords:
- ISymUnmanagedWriter::Abort method [.NET Framework debugging]
- Abort method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 416b220f-38d4-48e0-bb49-d2faa7366702
topic_type:
- apiref
ms.openlocfilehash: 2136eb32f147b8928e6ac90b99bbdf66804f244d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95733270"
---
# <a name="isymunmanagedwriterabort-method"></a><span data-ttu-id="ecaed-102">ISymUnmanagedWriter::Abort メソッド</span><span class="sxs-lookup"><span data-stu-id="ecaed-102">ISymUnmanagedWriter::Abort Method</span></span>

<span data-ttu-id="ecaed-103">シンボルストアにシンボルをコミットせずにシンボルライターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="ecaed-103">Closes the symbol writer without committing the symbols to the symbol store.</span></span> <span data-ttu-id="ecaed-104">この呼び出しの後、シンボルライターは、さらに更新するために無効になります。</span><span class="sxs-lookup"><span data-stu-id="ecaed-104">After this call, the symbol writer becomes invalid for further updates.</span></span> <span data-ttu-id="ecaed-105">シンボルをコミットし、シンボルライターを閉じるには、代わりに [ISymUnmanagedWriter:: close](isymunmanagedwriter-close-method.md) メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="ecaed-105">To commit the symbols and close the symbol writer, use the [ISymUnmanagedWriter::Close](isymunmanagedwriter-close-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecaed-106">構文</span><span class="sxs-lookup"><span data-stu-id="ecaed-106">Syntax</span></span>  
  
```cpp  
HRESULT Abort();  
```  
  
## <a name="return-value"></a><span data-ttu-id="ecaed-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="ecaed-107">Return Value</span></span>  

 <span data-ttu-id="ecaed-108">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="ecaed-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecaed-109">要件</span><span class="sxs-lookup"><span data-stu-id="ecaed-109">Requirements</span></span>  

 <span data-ttu-id="ecaed-110">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="ecaed-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecaed-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="ecaed-111">See also</span></span>

- [<span data-ttu-id="ecaed-112">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ecaed-112">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
