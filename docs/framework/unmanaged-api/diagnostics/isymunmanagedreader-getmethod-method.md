---
title: ISymUnmanagedReader::GetMethod メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethod
helpviewer_keywords:
- GetMethod method, ISymUnmanagedReader interface [.NET Framework debugging]
- ISymUnmanagedReader::GetMethod method [.NET Framework debugging]
ms.assetid: ae6cfb29-bc2c-4606-af86-1d32ebd31020
topic_type:
- apiref
ms.openlocfilehash: 3f0d0e060bba832080dd8fbfab62f3115fec0aab
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689642"
---
# <a name="isymunmanagedreadergetmethod-method"></a><span data-ttu-id="e2bcd-102">ISymUnmanagedReader::GetMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="e2bcd-102">ISymUnmanagedReader::GetMethod Method</span></span>

<span data-ttu-id="e2bcd-103">メソッドトークンを指定して、シンボルリーダーメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="e2bcd-103">Gets a symbol reader method, given a method token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2bcd-104">構文</span><span class="sxs-lookup"><span data-stu-id="e2bcd-104">Syntax</span></span>  
  
```cpp  
HRESULT GetMethod (  
    [in]  mdMethodDef  token,  
    [out, retval] ISymUnmanagedMethod**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e2bcd-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="e2bcd-105">Parameters</span></span>  

 `token`  
 <span data-ttu-id="e2bcd-106">からメソッドトークン。</span><span class="sxs-lookup"><span data-stu-id="e2bcd-106">[in] The method token.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="e2bcd-107">入出力返されたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="e2bcd-107">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e2bcd-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="e2bcd-108">Return Value</span></span>  

 <span data-ttu-id="e2bcd-109">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="e2bcd-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e2bcd-110">要件</span><span class="sxs-lookup"><span data-stu-id="e2bcd-110">Requirements</span></span>  

 <span data-ttu-id="e2bcd-111">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="e2bcd-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e2bcd-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="e2bcd-112">See also</span></span>

- [<span data-ttu-id="e2bcd-113">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="e2bcd-113">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
