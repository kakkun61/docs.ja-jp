---
title: ISymUnmanagedVariable::GetAddressField3 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type:
- apiref
ms.openlocfilehash: 13746c4ac6322a401e547c1c7acc99c0eda9accf
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95723338"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="bea6e-102">ISymUnmanagedVariable::GetAddressField3 メソッド</span><span class="sxs-lookup"><span data-stu-id="bea6e-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>

<span data-ttu-id="bea6e-103">この変数の3番目のアドレスフィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="bea6e-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="bea6e-104">その意味は、アドレスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="bea6e-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bea6e-105">構文</span><span class="sxs-lookup"><span data-stu-id="bea6e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bea6e-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="bea6e-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="bea6e-107">入出力 `ULONG32` 3 番目のアドレスフィールドを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="bea6e-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bea6e-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="bea6e-108">Return Value</span></span>  

 <span data-ttu-id="bea6e-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="bea6e-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bea6e-110">要件</span><span class="sxs-lookup"><span data-stu-id="bea6e-110">Requirements</span></span>  

 <span data-ttu-id="bea6e-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="bea6e-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bea6e-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="bea6e-112">See also</span></span>

- [<span data-ttu-id="bea6e-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="bea6e-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="bea6e-114">GetAddressField1 メソッド</span><span class="sxs-lookup"><span data-stu-id="bea6e-114">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="bea6e-115">GetAddressField2 メソッド</span><span class="sxs-lookup"><span data-stu-id="bea6e-115">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="bea6e-116">GetAddressKind メソッド</span><span class="sxs-lookup"><span data-stu-id="bea6e-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
