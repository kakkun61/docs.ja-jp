---
title: ISymUnmanagedWriter::CloseNamespace メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.CloseNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::CloseNamespace
helpviewer_keywords:
- ISymUnmanagedWriter::CloseNamespace method [.NET Framework debugging]
- CloseNamespace method [.NET Framework debugging]
ms.assetid: 7f74d9c5-1377-4958-b842-6306d611cbd5
topic_type:
- apiref
ms.openlocfilehash: 13a433157e0c92653edf234f1f1f885270196ffd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95686411"
---
# <a name="isymunmanagedwriterclosenamespace-method"></a><span data-ttu-id="1f4e6-102">ISymUnmanagedWriter::CloseNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="1f4e6-102">ISymUnmanagedWriter::CloseNamespace Method</span></span>

<span data-ttu-id="1f4e6-103">最近開いた名前空間を閉じます。</span><span class="sxs-lookup"><span data-stu-id="1f4e6-103">Closes the most recently opened namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f4e6-104">構文</span><span class="sxs-lookup"><span data-stu-id="1f4e6-104">Syntax</span></span>  
  
```cpp  
HRESULT CloseNamespace();  
```  
  
## <a name="return-value"></a><span data-ttu-id="1f4e6-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="1f4e6-105">Return Value</span></span>  

 <span data-ttu-id="1f4e6-106">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="1f4e6-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f4e6-107">要件</span><span class="sxs-lookup"><span data-stu-id="1f4e6-107">Requirements</span></span>  

 <span data-ttu-id="1f4e6-108">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="1f4e6-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f4e6-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="1f4e6-109">See also</span></span>

- [<span data-ttu-id="1f4e6-110">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1f4e6-110">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="1f4e6-111">OpenNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="1f4e6-111">OpenNamespace Method</span></span>](isymunmanagedwriter-opennamespace-method.md)
