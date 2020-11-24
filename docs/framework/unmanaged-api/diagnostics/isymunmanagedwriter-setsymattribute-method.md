---
title: ISymUnmanagedWriter::SetSymAttribute メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetSymAttribute
helpviewer_keywords:
- SetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedWriter::SetSymAttribute method [.NET Framework debugging]
ms.assetid: 64d9b80e-b883-4539-89c7-03573185a1eb
topic_type:
- apiref
ms.openlocfilehash: 484affb2ca87ca50a805d1bb46b7749d294d09f2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683512"
---
# <a name="isymunmanagedwritersetsymattribute-method"></a><span data-ttu-id="20f73-102">ISymUnmanagedWriter::SetSymAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="20f73-102">ISymUnmanagedWriter::SetSymAttribute Method</span></span>

<span data-ttu-id="20f73-103">名前に基づいてカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="20f73-103">Defines a custom attribute based upon its name.</span></span> <span data-ttu-id="20f73-104">これらの属性は、メタデータのカスタム属性とは異なり、シンボルストアに保持されます。</span><span class="sxs-lookup"><span data-stu-id="20f73-104">These attributes are held in the symbol store, unlike metadata custom attributes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="20f73-105">構文</span><span class="sxs-lookup"><span data-stu-id="20f73-105">Syntax</span></span>  
  
```cpp  
HRESULT SetSymAttribute(  
    [in] mdToken parent,  
    [in] const WCHAR *name,  
    [in] ULONG32 cData,  
    [in, size_is(cData)] unsigned char data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="20f73-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="20f73-106">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="20f73-107">から属性を定義するメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="20f73-107">[in] The metadata token for which the attribute is being defined.</span></span>  
  
 `name`  
 <span data-ttu-id="20f73-108">から `WCHAR` 属性名を格納しているへのポインター。</span><span class="sxs-lookup"><span data-stu-id="20f73-108">[in] A pointer to a `WCHAR` that contains the attribute name.</span></span>  
  
 `cData`  
 <span data-ttu-id="20f73-109">から `ULONG32` 配列のサイズを示す `data` 。</span><span class="sxs-lookup"><span data-stu-id="20f73-109">[in] A `ULONG32` that indicates the size of the `data` array.</span></span>  
  
 `data`  
 <span data-ttu-id="20f73-110">から属性値。</span><span class="sxs-lookup"><span data-stu-id="20f73-110">[in] The attribute value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="20f73-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="20f73-111">Return Value</span></span>  

 <span data-ttu-id="20f73-112">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="20f73-112">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="20f73-113">要件</span><span class="sxs-lookup"><span data-stu-id="20f73-113">Requirements</span></span>  

 <span data-ttu-id="20f73-114">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="20f73-114">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20f73-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="20f73-115">See also</span></span>

- [<span data-ttu-id="20f73-116">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="20f73-116">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
