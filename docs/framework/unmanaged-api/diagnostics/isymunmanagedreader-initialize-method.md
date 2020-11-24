---
title: ISymUnmanagedReader::Initialize メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.Initialize
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::Initialize
helpviewer_keywords:
- ISymUnmanagedReader::Initialize method [.NET Framework debugging]
- Initialize method, ISymUnmanagedReader interface [.NET Framework debugging]
ms.assetid: 8f0dd2fe-7df7-464e-91f4-5518c586bb5f
topic_type:
- apiref
ms.openlocfilehash: 6193d91c8cbe0efa7cd68b97b9262acf72c9ea0b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675881"
---
# <a name="isymunmanagedreaderinitialize-method"></a><span data-ttu-id="ceae9-102">ISymUnmanagedReader::Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="ceae9-102">ISymUnmanagedReader::Initialize Method</span></span>

<span data-ttu-id="ceae9-103">このリーダーが関連付けられるメタデータインポーターインターフェイスと、モジュールのファイル名を使用して、シンボルリーダーを初期化します。</span><span class="sxs-lookup"><span data-stu-id="ceae9-103">Initializes the symbol reader with the metadata importer interface that this reader will be associated with, along with the file name of the module.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ceae9-104">このメソッドを呼び出すことができるのは1回だけです。他のリーダーメソッドの前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="ceae9-104">This method can be called only once, and must be called before any other reader methods.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ceae9-105">構文</span><span class="sxs-lookup"><span data-stu-id="ceae9-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize (  
    [in]  IUnknown     *importer,  
    [in]  const WCHAR  *filename,  
    [in]  const WCHAR  *searchPath,  
    [in]  IStream      *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ceae9-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ceae9-106">Parameters</span></span>  

 `importer`  
 <span data-ttu-id="ceae9-107">からこのリーダーが関連付けられるメタデータインポーターインターフェイス。</span><span class="sxs-lookup"><span data-stu-id="ceae9-107">[in] The metadata importer interface with which this reader will be associated.</span></span>  
  
 `filename`  
 <span data-ttu-id="ceae9-108">からモジュールのファイル名。</span><span class="sxs-lookup"><span data-stu-id="ceae9-108">[in] The file name of the module.</span></span> <span data-ttu-id="ceae9-109">代わりに、パラメーターを使用でき `pIStream` ます。</span><span class="sxs-lookup"><span data-stu-id="ceae9-109">You can use the `pIStream` parameter instead.</span></span>  
  
 `searchPath`  
 <span data-ttu-id="ceae9-110">から検索するパス。</span><span class="sxs-lookup"><span data-stu-id="ceae9-110">[in] The path to search.</span></span> <span data-ttu-id="ceae9-111">このパラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="ceae9-111">This parameter is optional.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="ceae9-112">からファイルストリーム。 filename パラメーターの代わりに使用されます。</span><span class="sxs-lookup"><span data-stu-id="ceae9-112">[in] The file stream, used as an alternative to the filename parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ceae9-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="ceae9-113">Return Value</span></span>  

 <span data-ttu-id="ceae9-114">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="ceae9-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ceae9-115">注釈</span><span class="sxs-lookup"><span data-stu-id="ceae9-115">Remarks</span></span>  

 <span data-ttu-id="ceae9-116">またはパラメーターのいずれか1つだけを指定する必要があります。両方を指定すること `filename` はでき `pIStream` ません。</span><span class="sxs-lookup"><span data-stu-id="ceae9-116">You need to specify only one of the `filename` or the `pIStream` parameters, not both.</span></span> <span data-ttu-id="ceae9-117">`searchPath` パラメーターは省略可能です。</span><span class="sxs-lookup"><span data-stu-id="ceae9-117">The `searchPath` parameter is optional.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ceae9-118">要件</span><span class="sxs-lookup"><span data-stu-id="ceae9-118">Requirements</span></span>  

 <span data-ttu-id="ceae9-119">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="ceae9-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceae9-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="ceae9-120">See also</span></span>

- [<span data-ttu-id="ceae9-121">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ceae9-121">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
