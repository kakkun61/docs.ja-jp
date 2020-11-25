---
title: ISymUnmanagedReader::GetDocument メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type:
- apiref
ms.openlocfilehash: 4604d78f66b872a30457c51bf65890caf613c4fa
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707634"
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="56fb4-102">ISymUnmanagedReader::GetDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="56fb4-102">ISymUnmanagedReader::GetDocument Method</span></span>

<span data-ttu-id="56fb4-103">ドキュメントを検索します。</span><span class="sxs-lookup"><span data-stu-id="56fb4-103">Finds a document.</span></span> <span data-ttu-id="56fb4-104">ドキュメントの言語、ベンダ、および種類はオプションです。</span><span class="sxs-lookup"><span data-stu-id="56fb4-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56fb4-105">構文</span><span class="sxs-lookup"><span data-stu-id="56fb4-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="56fb4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="56fb4-106">Parameters</span></span>  

 `url`  
 <span data-ttu-id="56fb4-107">からドキュメントを識別する URL。</span><span class="sxs-lookup"><span data-stu-id="56fb4-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="56fb4-108">からドキュメントの言語。</span><span class="sxs-lookup"><span data-stu-id="56fb4-108">[in] The document language.</span></span> <span data-ttu-id="56fb4-109">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="56fb4-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="56fb4-110">からドキュメント言語のベンダの id。</span><span class="sxs-lookup"><span data-stu-id="56fb4-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="56fb4-111">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="56fb4-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="56fb4-112">からドキュメントの種類。</span><span class="sxs-lookup"><span data-stu-id="56fb4-112">[in] The type of the document.</span></span> <span data-ttu-id="56fb4-113">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="56fb4-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="56fb4-114">入出力返されたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="56fb4-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="56fb4-115">戻り値</span><span class="sxs-lookup"><span data-stu-id="56fb4-115">Return Value</span></span>  

 <span data-ttu-id="56fb4-116">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="56fb4-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="56fb4-117">要件</span><span class="sxs-lookup"><span data-stu-id="56fb4-117">Requirements</span></span>  

 <span data-ttu-id="56fb4-118">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="56fb4-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56fb4-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="56fb4-119">See also</span></span>

- [<span data-ttu-id="56fb4-120">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="56fb4-120">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
