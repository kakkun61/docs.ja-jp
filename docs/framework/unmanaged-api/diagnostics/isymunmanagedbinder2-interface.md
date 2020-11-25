---
title: ISymUnmanagedBinder2 インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedBinder2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedBinder2 Interface
helpviewer_keywords:
- ISymUnmanagedBinder2 interface [.NET Framework debugging]
ms.assetid: 7a59f405-73e8-4434-8bcc-a9dc45ea08e6
topic_type:
- apiref
ms.openlocfilehash: c5a43f6c277f582f9f14cefe5bfba6f5300c09d8
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95727355"
---
# <a name="isymunmanagedbinder2-interface"></a><span data-ttu-id="94d8e-102">ISymUnmanagedBinder2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94d8e-102">ISymUnmanagedBinder2 Interface</span></span>

<span data-ttu-id="94d8e-103">アンマネージコードのシンボルバインダーを表し、 [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) インターフェイスを拡張します。</span><span class="sxs-lookup"><span data-stu-id="94d8e-103">Represents a symbol binder for unmanaged code, and extends the [ISymUnmanagedBinder](isymunmanagedbinder-interface.md) interface.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="94d8e-104">信頼されていないソースからプログラムデータベース (PDB) ファイルを開くと、セキュリティ上の危険があります。</span><span class="sxs-lookup"><span data-stu-id="94d8e-104">It is a security risk to open a program database (PDB) file from an untrusted source.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="94d8e-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="94d8e-105">Methods</span></span>  
  
|<span data-ttu-id="94d8e-106">メソッド</span><span class="sxs-lookup"><span data-stu-id="94d8e-106">Method</span></span>|<span data-ttu-id="94d8e-107">説明</span><span class="sxs-lookup"><span data-stu-id="94d8e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="94d8e-108">GetReaderForFile2 メソッド</span><span class="sxs-lookup"><span data-stu-id="94d8e-108">GetReaderForFile2 Method</span></span>](isymunmanagedbinder2-getreaderforfile2-method.md)|<span data-ttu-id="94d8e-109">メタデータインターフェイスとファイル名を指定すると、モジュールに関連付けられているデバッグシンボルを読み取る正しい [ISymUnmanagedReader](isymunmanagedreader-interface.md) インターフェイスが返されます。</span><span class="sxs-lookup"><span data-stu-id="94d8e-109">Given a metadata interface and a file name, returns the correct [ISymUnmanagedReader](isymunmanagedreader-interface.md) interface that will read the debugging symbols associated with the module.</span></span> <span data-ttu-id="94d8e-110">[ISymUnmanagedBinder:: GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md)メソッドよりも広範な検索を提供します。</span><span class="sxs-lookup"><span data-stu-id="94d8e-110">Provides a more extensive search than the [ISymUnmanagedBinder::GetReaderForFile](isymunmanagedbinder-getreaderforfile-method.md) method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="94d8e-111">要件</span><span class="sxs-lookup"><span data-stu-id="94d8e-111">Requirements</span></span>  

 <span data-ttu-id="94d8e-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="94d8e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94d8e-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="94d8e-113">See also</span></span>

- [<span data-ttu-id="94d8e-114">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94d8e-114">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="94d8e-115">ISymUnmanagedBinder インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94d8e-115">ISymUnmanagedBinder Interface</span></span>](isymunmanagedbinder-interface.md)
- [<span data-ttu-id="94d8e-116">ISymUnmanagedBinder3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="94d8e-116">ISymUnmanagedBinder3 Interface</span></span>](isymunmanagedbinder3-interface.md)
