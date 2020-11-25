---
title: ISymUnmanagedVariable::GetAddressField1 メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField1
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type:
- apiref
ms.openlocfilehash: e3ea3c0fd65750d52c0cfb10edbe18b1512f724b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95729019"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="d85e9-102">ISymUnmanagedVariable::GetAddressField1 メソッド</span><span class="sxs-lookup"><span data-stu-id="d85e9-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>

<span data-ttu-id="d85e9-103">この変数の最初のアドレスフィールドを取得します。</span><span class="sxs-lookup"><span data-stu-id="d85e9-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="d85e9-104">その意味は、アドレスの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="d85e9-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d85e9-105">構文</span><span class="sxs-lookup"><span data-stu-id="d85e9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d85e9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d85e9-106">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="d85e9-107">入出力最初のアドレスフィールドを受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="d85e9-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d85e9-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="d85e9-108">Return Value</span></span>  

 <span data-ttu-id="d85e9-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="d85e9-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d85e9-110">要件</span><span class="sxs-lookup"><span data-stu-id="d85e9-110">Requirements</span></span>  

 <span data-ttu-id="d85e9-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="d85e9-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d85e9-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="d85e9-112">See also</span></span>

- [<span data-ttu-id="d85e9-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d85e9-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="d85e9-114">GetAddressField2 メソッド</span><span class="sxs-lookup"><span data-stu-id="d85e9-114">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="d85e9-115">GetAddressField3 メソッド</span><span class="sxs-lookup"><span data-stu-id="d85e9-115">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="d85e9-116">GetAddressKind メソッド</span><span class="sxs-lookup"><span data-stu-id="d85e9-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
