---
title: ISymUnmanagedConstant::GetSignature メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
ms.openlocfilehash: 4436e4528c1dc486eb5c443c5a9467ac69a26c7d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95706932"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="9c1ad-102">ISymUnmanagedConstant::GetSignature メソッド</span><span class="sxs-lookup"><span data-stu-id="9c1ad-102">ISymUnmanagedConstant::GetSignature Method</span></span>

<span data-ttu-id="9c1ad-103">定数の署名を取得します。</span><span class="sxs-lookup"><span data-stu-id="9c1ad-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c1ad-104">構文</span><span class="sxs-lookup"><span data-stu-id="9c1ad-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9c1ad-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="9c1ad-105">Parameters</span></span>  

 `cSig`  
 <span data-ttu-id="9c1ad-106">からパラメーターが指すバッファーの長さ `pcSig` 。</span><span class="sxs-lookup"><span data-stu-id="9c1ad-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="9c1ad-107">入出力 `ULONG32` 署名を格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="9c1ad-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="9c1ad-108">入出力署名を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="9c1ad-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9c1ad-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="9c1ad-109">Return Value</span></span>  

 <span data-ttu-id="9c1ad-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="9c1ad-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9c1ad-111">要件</span><span class="sxs-lookup"><span data-stu-id="9c1ad-111">Requirements</span></span>  

 <span data-ttu-id="9c1ad-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="9c1ad-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c1ad-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c1ad-113">See also</span></span>

- [<span data-ttu-id="9c1ad-114">ISymUnmanagedConstant インターフェイス</span><span class="sxs-lookup"><span data-stu-id="9c1ad-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="9c1ad-115">GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="9c1ad-115">GetName Method</span></span>](isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="9c1ad-116">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="9c1ad-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
