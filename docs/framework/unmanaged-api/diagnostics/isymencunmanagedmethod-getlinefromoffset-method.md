---
title: ISymENCUnmanagedMethod::GetLineFromOffset メソッド
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetLineFromOffset
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetLineFromOffset
helpviewer_keywords:
- GetLineFromOffset method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetLineFromOffset method [.NET Framework debugging]
ms.assetid: cc09bad2-fb34-4d13-a521-6ec7b1a1d915
topic_type:
- apiref
ms.openlocfilehash: 196993df9058d3eb8167e0144255c5fe366c54f8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707361"
---
# <a name="isymencunmanagedmethodgetlinefromoffset-method"></a><span data-ttu-id="71787-102">ISymENCUnmanagedMethod::GetLineFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="71787-102">ISymENCUnmanagedMethod::GetLineFromOffset Method</span></span>

<span data-ttu-id="71787-103">オフセットに関連付けられている行情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="71787-103">Gets the line information associated with an offset.</span></span> <span data-ttu-id="71787-104">オフセットパラメーター ( `dwOffset` ) がシーケンスポイントでない場合、このメソッドは、前のオフセットに関連付けられている行情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="71787-104">If the offset parameter (`dwOffset`) is not a sequence point, this method gets the line information associated with the previous offset.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71787-105">構文</span><span class="sxs-lookup"><span data-stu-id="71787-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLineFromOffset(  
     [in]  ULONG32   dwOffset,  
     [out] ULONG32*  pline,  
     [out] ULONG32*  pcolumn,  
     [out] ULONG32*  pendLine,  
     [out] ULONG32*  pendColumn,  
     [out] ULONG32*  pdwStartOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="71787-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="71787-106">Parameters</span></span>  

 `dwOffset`  
 <span data-ttu-id="71787-107">から `ULONG32` オフセットを格納している。</span><span class="sxs-lookup"><span data-stu-id="71787-107">[in] A `ULONG32` that contains the offset.</span></span>  
  
 `pline`  
 <span data-ttu-id="71787-108">入出力行を受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="71787-108">[out] A pointer to a `ULONG32` that receives the line.</span></span>  
  
 `pcolumn`  
 <span data-ttu-id="71787-109">入出力列を受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="71787-109">[out] A pointer to a `ULONG32` that receives the column.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="71787-110">入出力終了行を受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="71787-110">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
 `pendColumn`  
 <span data-ttu-id="71787-111">入出力終了列を受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="71787-111">[out] A pointer to a `ULONG32` that receives the end column.</span></span>  
  
 `pdwStartOffset`  
 <span data-ttu-id="71787-112">入出力 `ULONG32` 関連付けられたシーケンスポイントを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="71787-112">[out] A pointer to a `ULONG32` that receives the associated sequence point.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="71787-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="71787-113">Return Value</span></span>  

 <span data-ttu-id="71787-114">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="71787-114">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="71787-115">要件</span><span class="sxs-lookup"><span data-stu-id="71787-115">Requirements</span></span>  

 <span data-ttu-id="71787-116">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="71787-116">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="71787-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="71787-117">See also</span></span>

- [<span data-ttu-id="71787-118">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="71787-118">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
