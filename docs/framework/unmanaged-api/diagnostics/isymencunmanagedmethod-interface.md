---
title: ISymENCUnmanagedMethod インターフェイス
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod
helpviewer_keywords:
- ISymENCUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: faebf594-67d5-4abf-b9c1-547fd3a1ff87
topic_type:
- apiref
ms.openlocfilehash: acb8d48ed6314756e2c1a10fff314a303799fb24
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95707283"
---
# <a name="isymencunmanagedmethod-interface"></a><span data-ttu-id="65985-102">ISymENCUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="65985-102">ISymENCUnmanagedMethod Interface</span></span>

<span data-ttu-id="65985-103">エディットコンティニュ機能に関する情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="65985-103">Provides information for the Edit and Continue feature.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="65985-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="65985-104">Methods</span></span>  
  
|<span data-ttu-id="65985-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="65985-105">Method</span></span>|<span data-ttu-id="65985-106">説明</span><span class="sxs-lookup"><span data-stu-id="65985-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="65985-107">GetDocumentsForMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="65985-107">GetDocumentsForMethod Method</span></span>](isymencunmanagedmethod-getdocumentsformethod-method.md)|<span data-ttu-id="65985-108">このメソッドに行が含まれているドキュメントを取得します。</span><span class="sxs-lookup"><span data-stu-id="65985-108">Gets the documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="65985-109">GetDocumentsForMethodCount メソッド</span><span class="sxs-lookup"><span data-stu-id="65985-109">GetDocumentsForMethodCount Method</span></span>](isymencunmanagedmethod-getdocumentsformethodcount-method.md)|<span data-ttu-id="65985-110">このメソッドに行があるドキュメントの数を取得します。</span><span class="sxs-lookup"><span data-stu-id="65985-110">Gets the number of documents that this method has lines in.</span></span>|  
|[<span data-ttu-id="65985-111">GetFileNameFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="65985-111">GetFileNameFromOffset Method</span></span>](isymencunmanagedmethod-getfilenamefromoffset-method.md)|<span data-ttu-id="65985-112">オフセットに関連付けられた行のファイル名を取得します。</span><span class="sxs-lookup"><span data-stu-id="65985-112">Gets the file name for the line associated with an offset.</span></span>|  
|[<span data-ttu-id="65985-113">GetLineFromOffset メソッド</span><span class="sxs-lookup"><span data-stu-id="65985-113">GetLineFromOffset Method</span></span>](isymencunmanagedmethod-getlinefromoffset-method.md)|<span data-ttu-id="65985-114">オフセットに関連付けられている行情報を取得します。</span><span class="sxs-lookup"><span data-stu-id="65985-114">Gets the line information associated with an offset.</span></span>|  
|[<span data-ttu-id="65985-115">GetSourceExtentInDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="65985-115">GetSourceExtentInDocument Method</span></span>](isymencunmanagedmethod-getsourceextentindocument-method.md)|<span data-ttu-id="65985-116">特定のドキュメント内のメソッドの最小の開始行と最大の終了行を取得します。</span><span class="sxs-lookup"><span data-stu-id="65985-116">Gets the smallest start line and largest end line for the method in a specific document.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="65985-117">要件</span><span class="sxs-lookup"><span data-stu-id="65985-117">Requirements</span></span>  

 <span data-ttu-id="65985-118">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="65985-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65985-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="65985-119">See also</span></span>

- [<span data-ttu-id="65985-120">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="65985-120">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
