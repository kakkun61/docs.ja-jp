---
title: ISymUnmanagedDocument::GetCheckSum メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocument::GetCheckSum method [.NET Framework debugging]
- GetCheckSum method [.NET Framework debugging]
ms.assetid: 9bc881b3-e2ce-48a7-ad69-17eaaa304120
topic_type:
- apiref
ms.openlocfilehash: 4030da31400b7075952d146e5d6740306863e9ad
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721089"
---
# <a name="isymunmanageddocumentgetchecksum-method"></a><span data-ttu-id="c80b4-102">ISymUnmanagedDocument::GetCheckSum メソッド</span><span class="sxs-lookup"><span data-stu-id="c80b4-102">ISymUnmanagedDocument::GetCheckSum Method</span></span>

<span data-ttu-id="c80b4-103">チェックサムを取得します。</span><span class="sxs-lookup"><span data-stu-id="c80b4-103">Gets the checksum.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c80b4-104">構文</span><span class="sxs-lookup"><span data-stu-id="c80b4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCheckSum(  
    [in]  ULONG32  cData,  
    [out] ULONG32  *pcData,  
    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c80b4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c80b4-105">Parameters</span></span>  

 `cData`  
 <span data-ttu-id="c80b4-106">からパラメーターによって指定されたバッファーの長さ `data`</span><span class="sxs-lookup"><span data-stu-id="c80b4-106">[in] The length of the buffer provided by the `data` parameter</span></span>  
  
 `pcData`  
 <span data-ttu-id="c80b4-107">入出力チェックサムのサイズと長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="c80b4-107">[out] The size and length of the checksum, in bytes.</span></span>  
  
 `data`  
 <span data-ttu-id="c80b4-108">入出力チェックサムを受け取るバッファー。</span><span class="sxs-lookup"><span data-stu-id="c80b4-108">[out] The buffer that receives the checksum.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c80b4-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="c80b4-109">Return Value</span></span>  

 <span data-ttu-id="c80b4-110">メソッドが成功した場合は S_OK。それ以外の場合は、エラーコード。</span><span class="sxs-lookup"><span data-stu-id="c80b4-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c80b4-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="c80b4-111">See also</span></span>

- [<span data-ttu-id="c80b4-112">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c80b4-112">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
