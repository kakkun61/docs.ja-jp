---
title: ISymUnmanagedMethod::GetParameters メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetParameters
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetParameters
helpviewer_keywords:
- ISymUnmanagedMethod::GetParameters method [.NET Framework debugging]
- GetParameters method [.NET Framework debugging]
ms.assetid: 3a8074f1-facc-4a3f-bb9b-d6574fc2fc74
topic_type:
- apiref
ms.openlocfilehash: c66fd810ae4976bc0b5e04572b899465cebe4bbb
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699509"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="66e3e-102">ISymUnmanagedMethod::GetParameters メソッド</span><span class="sxs-lookup"><span data-stu-id="66e3e-102">ISymUnmanagedMethod::GetParameters Method</span></span>

<span data-ttu-id="66e3e-103">このメソッドのパラメーターを取得します。</span><span class="sxs-lookup"><span data-stu-id="66e3e-103">Gets the parameters for this method.</span></span> <span data-ttu-id="66e3e-104">パラメーターは、メソッドのシグネチャ内で定義されている順序で返されます。</span><span class="sxs-lookup"><span data-stu-id="66e3e-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66e3e-105">構文</span><span class="sxs-lookup"><span data-stu-id="66e3e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66e3e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="66e3e-106">Parameters</span></span>  

 `cParams`  
 <span data-ttu-id="66e3e-107">[in] `params` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="66e3e-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="66e3e-108">から `ULONG32` パラメーターを格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="66e3e-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="66e3e-109">入出力パラメーターを受け取るバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="66e3e-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66e3e-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="66e3e-110">Return Value</span></span>  

 <span data-ttu-id="66e3e-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="66e3e-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66e3e-112">要件</span><span class="sxs-lookup"><span data-stu-id="66e3e-112">Requirements</span></span>  

 <span data-ttu-id="66e3e-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="66e3e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66e3e-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="66e3e-114">See also</span></span>

- [<span data-ttu-id="66e3e-115">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="66e3e-115">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
