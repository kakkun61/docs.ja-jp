---
title: ISymUnmanagedReader::GetMethodByVersion メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetMethodByVersion
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetMethodByVersion
helpviewer_keywords:
- ISymUnmanagedReader::GetMethodByVersion method [.NET Framework debugging]
- GetMethodByVersion method [.NET Framework debugging]
ms.assetid: 6ddb0631-4569-41b3-93e4-50fdfaa486dc
topic_type:
- apiref
ms.openlocfilehash: 64e6b9a1942e9a69e43de3d2f09564814328ec08
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95689616"
---
# <a name="isymunmanagedreadergetmethodbyversion-method"></a><span data-ttu-id="be8e1-102">ISymUnmanagedReader::GetMethodByVersion メソッド</span><span class="sxs-lookup"><span data-stu-id="be8e1-102">ISymUnmanagedReader::GetMethodByVersion Method</span></span>

<span data-ttu-id="be8e1-103">メソッドトークンと編集およびコピーバージョン番号を指定して、シンボルリーダーメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="be8e1-103">Gets a symbol reader method, given a method token and an edit-and-copy version number.</span></span> <span data-ttu-id="be8e1-104">バージョン番号は1から始まり、編集とコピー操作の結果としてメソッドが変更されるたびに増分されます。</span><span class="sxs-lookup"><span data-stu-id="be8e1-104">Version numbers start at 1 and are incremented each time the method is changed as a result of an edit-and-copy operation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be8e1-105">構文</span><span class="sxs-lookup"><span data-stu-id="be8e1-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodByVersion (  
    [in]  mdMethodDef  token,  
    [in]  int  version,  
    [out, retval] ISymUnmanagedMethod** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be8e1-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="be8e1-106">Parameters</span></span>  

 `token`  
 <span data-ttu-id="be8e1-107">からメソッドトークン。</span><span class="sxs-lookup"><span data-stu-id="be8e1-107">[in] The method token.</span></span>  
  
 `version`  
 <span data-ttu-id="be8e1-108">からメソッドのバージョン。</span><span class="sxs-lookup"><span data-stu-id="be8e1-108">[in] The method version.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="be8e1-109">入出力返されたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="be8e1-109">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be8e1-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="be8e1-110">Return Value</span></span>  

 <span data-ttu-id="be8e1-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="be8e1-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be8e1-112">要件</span><span class="sxs-lookup"><span data-stu-id="be8e1-112">Requirements</span></span>  

 <span data-ttu-id="be8e1-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="be8e1-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be8e1-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="be8e1-114">See also</span></span>

- [<span data-ttu-id="be8e1-115">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="be8e1-115">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
