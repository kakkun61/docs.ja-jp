---
title: ISymENCUnmanagedMethod::GetFileNameFromOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetFileNameFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetFileNameFromOffset
helpviewer_keywords:
- GetFileNameFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetFileNameFromOffset method [.NET Framework debugging]
ms.assetid: 00e2e194-12f5-436e-a997-2b9d3e844d4f
topic_type:
- apiref
ms.openlocfilehash: ad9631039c8d032e7ffdba1e6098b66398f82277
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707387"
---
# <a name="isymencunmanagedmethodgetfilenamefromoffset-method"></a><span data-ttu-id="5b393-102">ISymENCUnmanagedMethod::GetFileNameFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="5b393-102">ISymENCUnmanagedMethod::GetFileNameFromOffset Method</span></span>

<span data-ttu-id="5b393-103">オフセットに関連付けられた行のファイル名を取得します。</span><span class="sxs-lookup"><span data-stu-id="5b393-103">Gets the file name for the line associated with an offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b393-104">構文</span><span class="sxs-lookup"><span data-stu-id="5b393-104">Syntax</span></span>  
  
```cpp  
HRESULT GetFileNameFromOffset(  
    [in]  ULONG32  dwOffset,  
    [in]  ULONG32  cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName),  
       length_is(*pcchName)] WCHAR szName[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b393-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5b393-105">Parameters</span></span>  

 `dwOffset`  
 <span data-ttu-id="5b393-106">から `ULONG32` オフセットを格納している。</span><span class="sxs-lookup"><span data-stu-id="5b393-106">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `cchName`  
 <span data-ttu-id="5b393-107">から `ULONG32` バッファーのサイズを示す `szName` 。</span><span class="sxs-lookup"><span data-stu-id="5b393-107">[in] A `ULONG32` that indicates the size of the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="5b393-108">入出力 `ULONG32` ファイル名を格納するために必要なバッファーのサイズ (文字数) を受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5b393-108">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the file names.</span></span>  
  
 `szName`  
 <span data-ttu-id="5b393-109">入出力ファイル名を格納しているバッファー。</span><span class="sxs-lookup"><span data-stu-id="5b393-109">[out] The buffer that contains the file names.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="5b393-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="5b393-110">Return Value</span></span>  

 <span data-ttu-id="5b393-111">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="5b393-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5b393-112">要件</span><span class="sxs-lookup"><span data-stu-id="5b393-112">Requirements</span></span>  

 <span data-ttu-id="5b393-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="5b393-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5b393-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="5b393-114">See also</span></span>

- [<span data-ttu-id="5b393-115">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="5b393-115">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
