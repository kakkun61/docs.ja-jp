---
title: ISymUnmanagedMethod::GetNamespace メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type:
- apiref
ms.openlocfilehash: 7e26c272ee1ecf03f7d2a347cf7ca2cc3efa2122
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699561"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="f1e89-102">ISymUnmanagedMethod::GetNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="f1e89-102">ISymUnmanagedMethod::GetNamespace Method</span></span>

<span data-ttu-id="f1e89-103">このメソッドが定義されている名前空間を取得します。</span><span class="sxs-lookup"><span data-stu-id="f1e89-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1e89-104">構文</span><span class="sxs-lookup"><span data-stu-id="f1e89-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f1e89-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f1e89-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="f1e89-106">入出力返された [ISymUnmanagedNamespace](isymunmanagednamespace-interface.md) インターフェイスに設定されたポインター。</span><span class="sxs-lookup"><span data-stu-id="f1e89-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f1e89-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="f1e89-107">Return Value</span></span>  

 <span data-ttu-id="f1e89-108">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="f1e89-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f1e89-109">要件</span><span class="sxs-lookup"><span data-stu-id="f1e89-109">Requirements</span></span>  

 <span data-ttu-id="f1e89-110">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="f1e89-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1e89-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="f1e89-111">See also</span></span>

- [<span data-ttu-id="f1e89-112">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f1e89-112">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
