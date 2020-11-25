---
title: ISymUnmanagedVariable::GetAddressKind メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressKind
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type:
- apiref
ms.openlocfilehash: 6a7824949edc905a3edcd58f60d40f8b1a40c53c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726913"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="b160c-102">ISymUnmanagedVariable::GetAddressKind メソッド</span><span class="sxs-lookup"><span data-stu-id="b160c-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>

<span data-ttu-id="b160c-103">この変数のアドレスの種類を取得します。</span><span class="sxs-lookup"><span data-stu-id="b160c-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b160c-104">構文</span><span class="sxs-lookup"><span data-stu-id="b160c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b160c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="b160c-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="b160c-106">入出力値を受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="b160c-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="b160c-107">使用可能な値は、 [Corsymaddrkind](corsymaddrkind-enumeration.md) 列挙体で定義されています。</span><span class="sxs-lookup"><span data-stu-id="b160c-107">The possible values are defined in the [CorSymAddrKind](corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b160c-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="b160c-108">Return Value</span></span>  

 <span data-ttu-id="b160c-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="b160c-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b160c-110">要件</span><span class="sxs-lookup"><span data-stu-id="b160c-110">Requirements</span></span>  

 <span data-ttu-id="b160c-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="b160c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b160c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="b160c-112">See also</span></span>

- [<span data-ttu-id="b160c-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="b160c-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
