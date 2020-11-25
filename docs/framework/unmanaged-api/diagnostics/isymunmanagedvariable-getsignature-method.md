---
title: ISymUnmanagedVariable::GetSignature メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetSignature method [.NET Framework debugging]
ms.assetid: 78c1ba28-a410-4360-805c-23a95408964a
topic_type:
- apiref
ms.openlocfilehash: 791b92c30fc2bf3d506113620b59ba20015e077e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95725821"
---
# <a name="isymunmanagedvariablegetsignature-method"></a><span data-ttu-id="6d350-102">ISymUnmanagedVariable::GetSignature メソッド</span><span class="sxs-lookup"><span data-stu-id="6d350-102">ISymUnmanagedVariable::GetSignature Method</span></span>

<span data-ttu-id="6d350-103">この変数のシグネチャを取得します。</span><span class="sxs-lookup"><span data-stu-id="6d350-103">Gets the signature of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d350-104">構文</span><span class="sxs-lookup"><span data-stu-id="6d350-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d350-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6d350-105">Parameters</span></span>  

 `cSig`  
 <span data-ttu-id="6d350-106">からパラメーターが指すバッファーの長さ `sig` 。</span><span class="sxs-lookup"><span data-stu-id="6d350-106">[in] The length of the buffer pointed to by the `sig` parameter.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="6d350-107">入出力 `ULONG32` 署名を格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6d350-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="6d350-108">入出力署名を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="6d350-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d350-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="6d350-109">Return Value</span></span>  

 <span data-ttu-id="6d350-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="6d350-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d350-111">要件</span><span class="sxs-lookup"><span data-stu-id="6d350-111">Requirements</span></span>  

 <span data-ttu-id="6d350-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="6d350-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d350-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="6d350-113">See also</span></span>

- [<span data-ttu-id="6d350-114">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6d350-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
