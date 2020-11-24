---
title: ISymUnmanagedWriter::UsingNamespace メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.UsingNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::UsingNamespace
helpviewer_keywords:
- UsingNamespace method [.NET Framework debugging]
- ISymUnmanagedWriter::UsingNamespace method [.NET Framework debugging]
ms.assetid: 8d746e0a-d158-4983-88da-db0a0856bc0b
topic_type:
- apiref
ms.openlocfilehash: 6404252f2c1eb14f0cd723451beb82b4c65960fd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683486"
---
# <a name="isymunmanagedwriterusingnamespace-method"></a><span data-ttu-id="0feba-102">ISymUnmanagedWriter::UsingNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="0feba-102">ISymUnmanagedWriter::UsingNamespace Method</span></span>

<span data-ttu-id="0feba-103">現在開いている構文のスコープ内で、指定された完全修飾名前空間名が使用されていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="0feba-103">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span> <span data-ttu-id="0feba-104">名前空間は、現在開いているスコープから継承されるすべてのスコープ内で使用されます。</span><span class="sxs-lookup"><span data-stu-id="0feba-104">The namespace will be used within all scopes that inherit from the currently open scope.</span></span> <span data-ttu-id="0feba-105">現在のスコープを終了すると、名前空間も使用できなくなります。</span><span class="sxs-lookup"><span data-stu-id="0feba-105">Closing the current scope will also stop the use of the namespace.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0feba-106">構文</span><span class="sxs-lookup"><span data-stu-id="0feba-106">Syntax</span></span>  
  
```cpp  
HRESULT UsingNamespace(  
    [in] const WCHAR *fullName);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0feba-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0feba-107">Parameters</span></span>  

 `fullName`  
 <span data-ttu-id="0feba-108">から名前空間の完全修飾名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="0feba-108">[in] A pointer to the fully qualified name of the namespace.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0feba-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="0feba-109">Return Value</span></span>  

 <span data-ttu-id="0feba-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="0feba-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0feba-111">要件</span><span class="sxs-lookup"><span data-stu-id="0feba-111">Requirements</span></span>  

 <span data-ttu-id="0feba-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="0feba-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0feba-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="0feba-113">See also</span></span>

- [<span data-ttu-id="0feba-114">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0feba-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
