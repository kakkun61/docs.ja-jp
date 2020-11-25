---
title: ISymUnmanagedDispose::Destroy メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDispose.Destroy
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDispose::Destroy
helpviewer_keywords:
- ISymUnmanagedDispose::Destroy method [.NET Framework debugging]
- Destroy method [.NET Framework debugging]
ms.assetid: a854ab9f-d2ba-470e-867f-808c1e7bd07a
topic_type:
- apiref
ms.openlocfilehash: 6a31026f5b1669c0c29762048dc2c5c1c7bbb6a2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732828"
---
# <a name="isymunmanageddisposedestroy-method"></a><span data-ttu-id="0dc36-102">ISymUnmanagedDispose::Destroy メソッド</span><span class="sxs-lookup"><span data-stu-id="0dc36-102">ISymUnmanagedDispose::Destroy Method</span></span>

<span data-ttu-id="0dc36-103">基になるオブジェクトがすべての内部参照を解放し、後続のメソッド呼び出しの失敗を返します。</span><span class="sxs-lookup"><span data-stu-id="0dc36-103">Causes the underlying object to release all internal references and return failure on any subsequent method calls.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0dc36-104">構文</span><span class="sxs-lookup"><span data-stu-id="0dc36-104">Syntax</span></span>  
  
```cpp  
HRESULT Destroy();  
```  
  
## <a name="return-value"></a><span data-ttu-id="0dc36-105">戻り値</span><span class="sxs-lookup"><span data-stu-id="0dc36-105">Return Value</span></span>  

 <span data-ttu-id="0dc36-106">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="0dc36-106">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0dc36-107">要件</span><span class="sxs-lookup"><span data-stu-id="0dc36-107">Requirements</span></span>  

 <span data-ttu-id="0dc36-108">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="0dc36-108">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0dc36-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="0dc36-109">See also</span></span>

- [<span data-ttu-id="0dc36-110">ISymUnmanagedDispose インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0dc36-110">ISymUnmanagedDispose Interface</span></span>](isymunmanageddispose-interface.md)
