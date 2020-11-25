---
title: ISymUnmanagedVariable::GetName メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetName
helpviewer_keywords:
- GetName method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetName method [.NET Framework debugging]
ms.assetid: eedf1ef0-9d4a-4847-a201-4e99572dfe5e
topic_type:
- apiref
ms.openlocfilehash: f9da3ca8684da3bbc87146b3b52effdc4f91393d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95726887"
---
# <a name="isymunmanagedvariablegetname-method"></a><span data-ttu-id="c7d0d-102">ISymUnmanagedVariable::GetName メソッド</span><span class="sxs-lookup"><span data-stu-id="c7d0d-102">ISymUnmanagedVariable::GetName Method</span></span>

<span data-ttu-id="c7d0d-103">この変数の名前を取得します。</span><span class="sxs-lookup"><span data-stu-id="c7d0d-103">Gets the name of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7d0d-104">構文</span><span class="sxs-lookup"><span data-stu-id="c7d0d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
        length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7d0d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c7d0d-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="c7d0d-106">からパラメーターが指すバッファーの長さ `pcchName` 。</span><span class="sxs-lookup"><span data-stu-id="c7d0d-106">[in] The length of the buffer that the `pcchName` parameter points to.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="c7d0d-107">入出力 `ULONG32` Null 終了を含む、名前を格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="c7d0d-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the name, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="c7d0d-108">入出力名前を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="c7d0d-108">[out] The buffer that stores the name.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c7d0d-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="c7d0d-109">Return Value</span></span>  

 <span data-ttu-id="c7d0d-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="c7d0d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7d0d-111">要件</span><span class="sxs-lookup"><span data-stu-id="c7d0d-111">Requirements</span></span>  

 <span data-ttu-id="c7d0d-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="c7d0d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c7d0d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="c7d0d-113">See also</span></span>

- [<span data-ttu-id="c7d0d-114">ISymUnmanagedVariable インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c7d0d-114">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
