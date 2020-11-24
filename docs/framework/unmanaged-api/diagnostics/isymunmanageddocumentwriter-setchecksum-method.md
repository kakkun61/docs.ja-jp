---
title: ISymUnmanagedDocumentWriter::SetCheckSum メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetCheckSum
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetCheckSum method [.NET Framework debugging]
- SetCheckSum method [.NET Framework debugging]
ms.assetid: c7e99879-421f-43ce-b193-34733cf30085
topic_type:
- apiref
ms.openlocfilehash: 58055d9ea56d7928729d289198965752985d8e0c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95688901"
---
# <a name="isymunmanageddocumentwritersetchecksum-method"></a><span data-ttu-id="f5b3e-102">ISymUnmanagedDocumentWriter::SetCheckSum メソッド</span><span class="sxs-lookup"><span data-stu-id="f5b3e-102">ISymUnmanagedDocumentWriter::SetCheckSum Method</span></span>

<span data-ttu-id="f5b3e-103">チェックサム情報を設定します。</span><span class="sxs-lookup"><span data-stu-id="f5b3e-103">Sets checksum information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5b3e-104">構文</span><span class="sxs-lookup"><span data-stu-id="f5b3e-104">Syntax</span></span>  
  
```cpp  
HRESULT SetCheckSum(  
    [in]  GUID     algorithmId,  
    [in]  ULONG32  checkSumSize,  
    [in, size_is(checkSumSize)]  BYTE checkSum[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5b3e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="f5b3e-105">Parameters</span></span>  

 `algorithmId`  
 <span data-ttu-id="f5b3e-106">からアルゴリズム識別子を表す GUID。</span><span class="sxs-lookup"><span data-stu-id="f5b3e-106">[in] The GUID that represents the algorithm identifier.</span></span>  
  
 `checkSumSize`  
 <span data-ttu-id="f5b3e-107">から `ULONG32` バッファーのサイズ (バイト単位) を示す `checkSum` 。</span><span class="sxs-lookup"><span data-stu-id="f5b3e-107">[in] A `ULONG32` that indicates the size, in bytes, of the `checkSum` buffer.</span></span>  
  
 `checkSum`  
 <span data-ttu-id="f5b3e-108">からチェックサム情報を格納するバッファー。</span><span class="sxs-lookup"><span data-stu-id="f5b3e-108">[in] The buffer that stores the checksum information.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f5b3e-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="f5b3e-109">Return Value</span></span>  

 <span data-ttu-id="f5b3e-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="f5b3e-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5b3e-111">要件</span><span class="sxs-lookup"><span data-stu-id="f5b3e-111">Requirements</span></span>  

 <span data-ttu-id="f5b3e-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="f5b3e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5b3e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5b3e-113">See also</span></span>

- [<span data-ttu-id="f5b3e-114">ISymUnmanagedDocumentWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="f5b3e-114">ISymUnmanagedDocumentWriter Interface</span></span>](isymunmanageddocumentwriter-interface.md)
