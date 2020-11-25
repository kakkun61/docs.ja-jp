---
title: ISymENCUnmanagedMethod::GetSourceExtentInDocument メソッド
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetSourceExtentInDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetSourceExtentInDocument
helpviewer_keywords:
- GetSourceExtentInDocument method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetSourceExtentInDocument method [.NET Framework debugging]
ms.assetid: 9c5566ab-4ec7-4b61-9753-839bb90ae78c
topic_type:
- apiref
ms.openlocfilehash: 2cd362279f5c5ff281b9674fe3d1e293ddbab5f1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707296"
---
# <a name="isymencunmanagedmethodgetsourceextentindocument-method"></a><span data-ttu-id="6c945-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="6c945-102">ISymENCUnmanagedMethod::GetSourceExtentInDocument Method</span></span>

<span data-ttu-id="6c945-103">特定のドキュメント内のメソッドの最小の開始行と最大の終了行を取得します。</span><span class="sxs-lookup"><span data-stu-id="6c945-103">Gets the smallest start line and largest end line for the method in a specific document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6c945-104">構文</span><span class="sxs-lookup"><span data-stu-id="6c945-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSourceExtentInDocument(  
    [in]  ISymUnmanagedDocument *document,  
    [out] ULONG32* pstartLine,  
    [out] ULONG32* pendLine);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6c945-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6c945-105">Parameters</span></span>  

 `document`  
 <span data-ttu-id="6c945-106">からドキュメントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="6c945-106">[in] A pointer to the document.</span></span>  
  
 `pstartLine`  
 <span data-ttu-id="6c945-107">入出力開始行を受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="6c945-107">[out] A pointer to a `ULONG32` that receives the start line.</span></span>  
  
 `pendLine`  
 <span data-ttu-id="6c945-108">入出力終了行を受け取るへのポインター `ULONG32` 。</span><span class="sxs-lookup"><span data-stu-id="6c945-108">[out] A pointer to a `ULONG32` that receives the end line.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6c945-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="6c945-109">Return Value</span></span>  

 <span data-ttu-id="6c945-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="6c945-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6c945-111">要件</span><span class="sxs-lookup"><span data-stu-id="6c945-111">Requirements</span></span>  

 <span data-ttu-id="6c945-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="6c945-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c945-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="6c945-113">See also</span></span>

- [<span data-ttu-id="6c945-114">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="6c945-114">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
