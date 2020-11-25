---
title: ISymUnmanagedConstant::GetName メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetName
helpviewer_keywords:
- ISymUnmanagedConstant::GetName method [.NET Framework debugging]
- GetName method, ISymUnmanagedConstant interface [.NET Framework debugging]
ms.assetid: cbaca4e1-4473-459b-ba34-f1f59ce7c0ba
topic_type:
- apiref
ms.openlocfilehash: fca7b11a83b5a695feae82fe5f25218f87afbce2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732893"
---
# <a name="isymunmanagedconstantgetname-method"></a><span data-ttu-id="40c5e-102">ISymUnmanagedConstant::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="40c5e-102">ISymUnmanagedConstant::GetName Method</span></span>

<span data-ttu-id="40c5e-103">定数の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="40c5e-103">Gets the name of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40c5e-104">構文</span><span class="sxs-lookup"><span data-stu-id="40c5e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40c5e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="40c5e-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="40c5e-106">からパラメーターが指すバッファーの長さ `szName` 。</span><span class="sxs-lookup"><span data-stu-id="40c5e-106">[in] The length of the buffer that the `szName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="40c5e-107">入出力 `ULONG32` Null 終了を含む、名前を格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="40c5e-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="40c5e-108">入出力名前を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="40c5e-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40c5e-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="40c5e-109">Return Value</span></span>  

 <span data-ttu-id="40c5e-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="40c5e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40c5e-111">要件</span><span class="sxs-lookup"><span data-stu-id="40c5e-111">Requirements</span></span>  

 <span data-ttu-id="40c5e-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="40c5e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40c5e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="40c5e-113">See also</span></span>

- [<span data-ttu-id="40c5e-114">ISymUnmanagedConstant インターフェイス</span><span class="sxs-lookup"><span data-stu-id="40c5e-114">ISymUnmanagedConstant Interface</span></span>](isymunmanagedconstant-interface.md)
- [<span data-ttu-id="40c5e-115">GetSignature メソッド</span><span class="sxs-lookup"><span data-stu-id="40c5e-115">GetSignature Method</span></span>](isymunmanagedconstant-getsignature-method.md)
- [<span data-ttu-id="40c5e-116">GetValue メソッド</span><span class="sxs-lookup"><span data-stu-id="40c5e-116">GetValue Method</span></span>](isymunmanagedconstant-getvalue-method.md)
