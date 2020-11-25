---
title: ISymUnmanagedReader::GetGlobalVariables メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetGlobalVariables
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetGlobalVariables
helpviewer_keywords:
- GetGlobalVariables method [.NET Framework debugging]
- ISymUnmanagedReader::GetGlobalVariables method [.NET Framework debugging]
ms.assetid: a2dd5098-3e58-4be5-b7a2-e4160b3b505a
topic_type:
- apiref
ms.openlocfilehash: 299787ea4eb8a5c25bdab64ad08445839c9f24d6
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707543"
---
# <a name="isymunmanagedreadergetglobalvariables-method"></a><span data-ttu-id="706fc-102">ISymUnmanagedReader::GetGlobalVariables メソッド</span><span class="sxs-lookup"><span data-stu-id="706fc-102">ISymUnmanagedReader::GetGlobalVariables Method</span></span>

<span data-ttu-id="706fc-103">すべてのグローバル変数を返します。</span><span class="sxs-lookup"><span data-stu-id="706fc-103">Returns all global variables.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="706fc-104">構文</span><span class="sxs-lookup"><span data-stu-id="706fc-104">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariables(  
    [in]  ULONG32  cVars,  
    [out] ULONG32  *pcVars,  
    [out, size_is(cVars),  
        length_is(*pcVars)] ISymUnmanagedVariable *pVars[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="706fc-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="706fc-105">Parameters</span></span>  

 `cVars`  
 <span data-ttu-id="706fc-106">からが指すバッファーの長さ `pcVars` 。</span><span class="sxs-lookup"><span data-stu-id="706fc-106">[in] The length of the buffer pointed to by `pcVars`.</span></span>  
  
 `pcVars`  
 <span data-ttu-id="706fc-107">入出力 `ULONG32` 変数を格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="706fc-107">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the variables.</span></span>  
  
 `pVars`  
 <span data-ttu-id="706fc-108">入出力変数を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="706fc-108">[out] A buffer that contains the variables.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="706fc-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="706fc-109">Return Value</span></span>  

 <span data-ttu-id="706fc-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="706fc-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="706fc-111">要件</span><span class="sxs-lookup"><span data-stu-id="706fc-111">Requirements</span></span>  

 <span data-ttu-id="706fc-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="706fc-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="706fc-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="706fc-113">See also</span></span>

- [<span data-ttu-id="706fc-114">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="706fc-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
