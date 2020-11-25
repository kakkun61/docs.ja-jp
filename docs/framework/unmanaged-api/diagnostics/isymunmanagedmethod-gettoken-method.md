---
title: ISymUnmanagedMethod::GetToken メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetToken
helpviewer_keywords:
- ISymUnmanagedMethod::GetToken method [.NET Framework debugging]
- GetToken method, ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: 4effbe95-c36e-4a45-8b2a-ee21339415fb
topic_type:
- apiref
ms.openlocfilehash: 76134a2447cbc40b5c97304540d9907648bc89e8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95719919"
---
# <a name="isymunmanagedmethodgettoken-method"></a><span data-ttu-id="c3b26-102">ISymUnmanagedMethod::GetToken メソッド</span><span class="sxs-lookup"><span data-stu-id="c3b26-102">ISymUnmanagedMethod::GetToken Method</span></span>

<span data-ttu-id="c3b26-103">このメソッドのメタデータ トークンを返します。</span><span class="sxs-lookup"><span data-stu-id="c3b26-103">Returns the metadata token for this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3b26-104">構文</span><span class="sxs-lookup"><span data-stu-id="c3b26-104">Syntax</span></span>  
  
```cpp  
HRESULT GetToken(  
   [out, retval]  mdMethodDef  *pToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3b26-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c3b26-105">Parameters</span></span>  

 `pToken`  
 <span data-ttu-id="c3b26-106">入出力 `mdMethodDef` メタデータを格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c3b26-106">[out] A pointer to a `mdMethodDef` that receives the size, in characters, of the buffer required to contain the metadata.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c3b26-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="c3b26-107">Return Value</span></span>  

 <span data-ttu-id="c3b26-108">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="c3b26-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3b26-109">要件</span><span class="sxs-lookup"><span data-stu-id="c3b26-109">Requirements</span></span>  

 <span data-ttu-id="c3b26-110">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="c3b26-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c3b26-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="c3b26-111">See also</span></span>

- [<span data-ttu-id="c3b26-112">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c3b26-112">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
