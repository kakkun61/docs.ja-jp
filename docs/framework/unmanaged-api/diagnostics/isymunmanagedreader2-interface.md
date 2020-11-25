---
title: ISymUnmanagedReader2 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2
helpviewer_keywords:
- ISymUnmanagedReader2 interface [.NET Framework debugging]
ms.assetid: a01a881b-82a3-4b3e-a3a9-9dc305c2e5f7
topic_type:
- apiref
ms.openlocfilehash: 3f34be833d3ccb5c636d2c5f18ccb6e216ef2c49
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709077"
---
# <a name="isymunmanagedreader2-interface"></a><span data-ttu-id="03e3c-102">ISymUnmanagedReader2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="03e3c-102">ISymUnmanagedReader2 Interface</span></span>

<span data-ttu-id="03e3c-103">シンボル ストア内のドキュメント、メソッド、および変数へのアクセスを提供するシンボル リーダーを表します。</span><span class="sxs-lookup"><span data-stu-id="03e3c-103">Represents a symbol reader that provides access to documents, methods, and variables within a symbol store.</span></span> <span data-ttu-id="03e3c-104">このインターフェイスは、 [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="03e3c-104">This interface extends the [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="03e3c-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="03e3c-105">Methods</span></span>  
  
|<span data-ttu-id="03e3c-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="03e3c-106">Method</span></span>|<span data-ttu-id="03e3c-107">説明</span><span class="sxs-lookup"><span data-stu-id="03e3c-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="03e3c-108">GetMethodByVersionPreRemap メソッド</span><span class="sxs-lookup"><span data-stu-id="03e3c-108">GetMethodByVersionPreRemap Method</span></span>](isymunmanagedreader2-getmethodbyversionpreremap-method.md)|<span data-ttu-id="03e3c-109">メソッドトークンとエディットコンティニュバージョン番号を指定して、シンボルリーダーメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="03e3c-109">Get a symbol reader method, given a method token and an edit-and-continue version number.</span></span>|  
|[<span data-ttu-id="03e3c-110">GetMethodsInDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="03e3c-110">GetMethodsInDocument Method</span></span>](isymunmanagedreader2-getmethodsindocument-method.md)|<span data-ttu-id="03e3c-111">指定されたドキュメントに行情報が含まれるすべてのメソッドを取得します。</span><span class="sxs-lookup"><span data-stu-id="03e3c-111">Gets every method that has line information in the provided document.</span></span>|  
|[<span data-ttu-id="03e3c-112">GetSymAttributePreRemap メソッド</span><span class="sxs-lookup"><span data-stu-id="03e3c-112">GetSymAttributePreRemap Method</span></span>](isymunmanagedreader2-getsymattributepreremap-method.md)|<span data-ttu-id="03e3c-113">名前に基づいてカスタム属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="03e3c-113">Gets a custom attribute based upon its name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="03e3c-114">要件</span><span class="sxs-lookup"><span data-stu-id="03e3c-114">Requirements</span></span>  

 <span data-ttu-id="03e3c-115">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="03e3c-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03e3c-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="03e3c-116">See also</span></span>

- [<span data-ttu-id="03e3c-117">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="03e3c-117">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="03e3c-118">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="03e3c-118">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
