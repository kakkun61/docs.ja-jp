---
title: ISymUnmanagedReader::GetSymbolStoreFileName メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymbolStoreFileName
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymbolStoreFileName
helpviewer_keywords:
- GetSymbolStoreFileName method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymbolStoreFileName method [.NET Framework debugging]
ms.assetid: c84f4846-9bc8-44a4-9a76-e39106d6d8b2
topic_type:
- apiref
ms.openlocfilehash: df503e44f20a0b1f02e2c609cc4b52712520faea
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720569"
---
# <a name="isymunmanagedreadergetsymbolstorefilename-method"></a><span data-ttu-id="1cee9-102">ISymUnmanagedReader::GetSymbolStoreFileName メソッド</span><span class="sxs-lookup"><span data-stu-id="1cee9-102">ISymUnmanagedReader::GetSymbolStoreFileName Method</span></span>

<span data-ttu-id="1cee9-103">シンボルストアのディスク上のファイル名を提供します。</span><span class="sxs-lookup"><span data-stu-id="1cee9-103">Provides the on-disk file name of the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cee9-104">構文</span><span class="sxs-lookup"><span data-stu-id="1cee9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolStoreFileName (  
    [in]  ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is (cchName),  
        length_is (*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1cee9-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="1cee9-105">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="1cee9-106">からバッファーのサイズ `szName` 。</span><span class="sxs-lookup"><span data-stu-id="1cee9-106">[in] The size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1cee9-107">入出力Null 終了を含む、で返された名前の長さを受け取る変数へのポインター `szName` 。</span><span class="sxs-lookup"><span data-stu-id="1cee9-107">[out] A pointer to the variable that receives the length of the name returned in `szName`, including the null termination.</span></span>  
  
 `szName`  
 <span data-ttu-id="1cee9-108">入出力シンボルストアのファイル名を受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="1cee9-108">[out] A pointer to the variable that receives the file name of the symbol store.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1cee9-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="1cee9-109">Return Value</span></span>  

 <span data-ttu-id="1cee9-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="1cee9-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cee9-111">要件</span><span class="sxs-lookup"><span data-stu-id="1cee9-111">Requirements</span></span>  

 <span data-ttu-id="1cee9-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="1cee9-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1cee9-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="1cee9-113">See also</span></span>

- [<span data-ttu-id="1cee9-114">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="1cee9-114">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
