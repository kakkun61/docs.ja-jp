---
title: ISymUnmanagedMethod::GetRootScope メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRootScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type:
- apiref
ms.openlocfilehash: 071738c8fb9b40457215e21172240aa7e77198cd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699470"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="d4af4-102">ISymUnmanagedMethod::GetRootScope メソッド</span><span class="sxs-lookup"><span data-stu-id="d4af4-102">ISymUnmanagedMethod::GetRootScope Method</span></span>

<span data-ttu-id="d4af4-103">このメソッド内のルート構文のスコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="d4af4-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="d4af4-104">このスコープはメソッド全体を囲みます。</span><span class="sxs-lookup"><span data-stu-id="d4af4-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4af4-105">構文</span><span class="sxs-lookup"><span data-stu-id="d4af4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4af4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d4af4-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="d4af4-107">入出力返された [ISymUnmanagedScope](isymunmanagedscope-interface.md) インターフェイスに設定されたポインター。</span><span class="sxs-lookup"><span data-stu-id="d4af4-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d4af4-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="d4af4-108">Return Value</span></span>  

 <span data-ttu-id="d4af4-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4af4-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4af4-110">要件</span><span class="sxs-lookup"><span data-stu-id="d4af4-110">Requirements</span></span>  

 <span data-ttu-id="d4af4-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="d4af4-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4af4-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4af4-112">See also</span></span>

- [<span data-ttu-id="d4af4-113">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d4af4-113">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
