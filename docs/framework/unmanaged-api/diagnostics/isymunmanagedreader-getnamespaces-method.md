---
title: ISymUnmanagedReader::GetNamespaces メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetNamespaces
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetNamespaces
helpviewer_keywords:
- ISymUnmanagedReader::GetNamespaces method [.NET Framework debugging]
- GetNamespaces method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 3feb4796-2fab-45ce-beca-6f5bc530b971
topic_type:
- apiref
ms.openlocfilehash: c90cd0d21eca6875d3dae32e4ca80cf42e6140b2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720595"
---
# <a name="isymunmanagedreadergetnamespaces-method"></a><span data-ttu-id="63e7d-102">ISymUnmanagedReader::GetNamespaces メソッド</span><span class="sxs-lookup"><span data-stu-id="63e7d-102">ISymUnmanagedReader::GetNamespaces Method</span></span>

<span data-ttu-id="63e7d-103">このシンボルストア内のグローバルスコープで定義されている名前空間を取得します。</span><span class="sxs-lookup"><span data-stu-id="63e7d-103">Gets the namespaces defined at global scope within this symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63e7d-104">構文</span><span class="sxs-lookup"><span data-stu-id="63e7d-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNamespaces (  
    [in]  ULONG32  cNameSpaces,  
    [out] ULONG32  *pcNameSpaces,  
    [out, size_is (cNameSpaces),  
        length_is (*pcNameSpaces)]  
        ISymUnmanagedNamespace*  namespaces[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="63e7d-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="63e7d-105">Parameters</span></span>  

 `cNameSpaces`  
 <span data-ttu-id="63e7d-106">から名前空間配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="63e7d-106">[in] The size of the namespaces array.</span></span>  
  
 `pcNameSpaces`  
 <span data-ttu-id="63e7d-107">入出力名前空間リストの長さを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="63e7d-107">[out] A pointer to a variable that receives the length of the namespace list.</span></span>  
  
 `namespaces`  
 <span data-ttu-id="63e7d-108">入出力名前空間リストを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="63e7d-108">[out] A pointer to a variable that receives the namespace list.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63e7d-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="63e7d-109">Return Value</span></span>  

 <span data-ttu-id="63e7d-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="63e7d-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63e7d-111">要件</span><span class="sxs-lookup"><span data-stu-id="63e7d-111">Requirements</span></span>  

 <span data-ttu-id="63e7d-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="63e7d-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63e7d-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="63e7d-113">See also</span></span>

- [<span data-ttu-id="63e7d-114">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="63e7d-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
