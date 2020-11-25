---
title: ISymUnmanagedVariable::GetAttributes メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAttributes
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAttributes
helpviewer_keywords:
- GetAttributes method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAttributes method [.NET Framework debugging]
ms.assetid: 80f168af-a6a6-4c8f-b9e6-8a82dc834ed5
topic_type:
- apiref
ms.openlocfilehash: 1142dbb83693f6104ba6e22e174ce02fb92997a6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726900"
---
# <a name="isymunmanagedvariablegetattributes-method"></a><span data-ttu-id="74b74-102">ISymUnmanagedVariable::GetAttributes メソッド</span><span class="sxs-lookup"><span data-stu-id="74b74-102">ISymUnmanagedVariable::GetAttributes Method</span></span>

<span data-ttu-id="74b74-103">この変数の属性フラグを取得します。</span><span class="sxs-lookup"><span data-stu-id="74b74-103">Gets the attribute flags for this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74b74-104">構文</span><span class="sxs-lookup"><span data-stu-id="74b74-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAttributes(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="74b74-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="74b74-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="74b74-106">入出力属性を受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="74b74-106">[out] A pointer to a `ULONG32` that receives the attributes.</span></span> <span data-ttu-id="74b74-107">返される値は、 [Corsymvarflag](corsymvarflag-enumeration.md) 列挙で定義されている値のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="74b74-107">The returned value will be one of the values defined in the [CorSymVarFlag](corsymvarflag-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74b74-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="74b74-108">Return Value</span></span>  

 <span data-ttu-id="74b74-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="74b74-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74b74-110">要件</span><span class="sxs-lookup"><span data-stu-id="74b74-110">Requirements</span></span>  

 <span data-ttu-id="74b74-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="74b74-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74b74-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="74b74-112">See also</span></span>

- [<span data-ttu-id="74b74-113">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="74b74-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
