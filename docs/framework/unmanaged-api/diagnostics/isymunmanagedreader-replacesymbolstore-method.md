---
title: ISymUnmanagedReader::ReplaceSymbolStore メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.ReplaceSymbolStore
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::ReplaceSymbolStore
helpviewer_keywords:
- ReplaceSymbolStore method [.NET Framework debugging]
- ISymUnmanagedReader::ReplaceSymbolStore method [.NET Framework debugging]
ms.assetid: 43257761-8cb1-4eaf-8fb5-1f3980cb66cd
topic_type:
- apiref
ms.openlocfilehash: 3fa94094ad066496cc8a1fc4dd2ccb0ee16b5aac
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675842"
---
# <a name="isymunmanagedreaderreplacesymbolstore-method"></a><span data-ttu-id="ecba8-102">ISymUnmanagedReader::ReplaceSymbolStore メソッド</span><span class="sxs-lookup"><span data-stu-id="ecba8-102">ISymUnmanagedReader::ReplaceSymbolStore Method</span></span>

<span data-ttu-id="ecba8-103">既存のシンボル ストアをデルタ シンボル ストアで置き換えます。</span><span class="sxs-lookup"><span data-stu-id="ecba8-103">Replaces the existing symbol store with a delta symbol store.</span></span> <span data-ttu-id="ecba8-104">このメソッドは、指定されたデルタが更新ではなく完全な置換として機能する点を除いて、"更新プログラム" [ストア](isymunmanagedreader-updatesymbolstore-method.md) メソッドに似ています。</span><span class="sxs-lookup"><span data-stu-id="ecba8-104">This method is similar to the [UpdateSymbolStore](isymunmanagedreader-updatesymbolstore-method.md) method, except that the given delta acts as a complete replacement rather than an update.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ecba8-105">またはパラメーターのいずれか1つだけを指定する必要があります。両方を指定すること `filename` はでき `pIStream` ません。</span><span class="sxs-lookup"><span data-stu-id="ecba8-105">You need specify only one of the `filename` or `pIStream` parameters, not both.</span></span> <span data-ttu-id="ecba8-106">を `filename` 指定した場合、シンボルストアはそのファイル内のシンボルで更新されます。</span><span class="sxs-lookup"><span data-stu-id="ecba8-106">If `filename` is specified, the symbol store will be updated with the symbols in that file.</span></span> <span data-ttu-id="ecba8-107">を指定した場合、 `pIStream` ストアはからのデータで更新され <xref:System.Runtime.InteropServices.ComTypes.IStream> ます。</span><span class="sxs-lookup"><span data-stu-id="ecba8-107">If `pIStream` is specified, the store will be updated with the data from the <xref:System.Runtime.InteropServices.ComTypes.IStream>.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecba8-108">構文</span><span class="sxs-lookup"><span data-stu-id="ecba8-108">Syntax</span></span>  
  
```cpp  
HRESULT ReplaceSymbolStore (  
    [in] const WCHAR *filename,  
    [in] IStream *pIStream);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ecba8-109">パラメーター</span><span class="sxs-lookup"><span data-stu-id="ecba8-109">Parameters</span></span>  

 `filename`  
 <span data-ttu-id="ecba8-110">からシンボルストアを格納しているファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="ecba8-110">[in] The name of the file containing the symbol store.</span></span>  
  
 `pIStream`  
 <span data-ttu-id="ecba8-111">からパラメーターの代わりに使用されるファイルストリーム `filename` 。</span><span class="sxs-lookup"><span data-stu-id="ecba8-111">[in] The file stream, used as an alternative to the `filename` parameter.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="ecba8-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="ecba8-112">Return Value</span></span>  

 <span data-ttu-id="ecba8-113">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="ecba8-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecba8-114">要件</span><span class="sxs-lookup"><span data-stu-id="ecba8-114">Requirements</span></span>  

 <span data-ttu-id="ecba8-115">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="ecba8-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecba8-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="ecba8-116">See also</span></span>

- [<span data-ttu-id="ecba8-117">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="ecba8-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
