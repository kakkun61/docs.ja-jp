---
title: ISymUnmanagedWriter::RemapToken メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.RemapToken
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::RemapToken
helpviewer_keywords:
- ISymUnmanagedWriter::RemapToken method [.NET Framework debugging]
- RemapToken method [.NET Framework debugging]
ms.assetid: bca92682-ee1e-467f-8fb0-d8d4617f82fe
topic_type:
- apiref
ms.openlocfilehash: 8799815f7c6c6aefc7081f3583e6fd174cd478f7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683558"
---
# <a name="isymunmanagedwriterremaptoken-method"></a><span data-ttu-id="84adb-102">ISymUnmanagedWriter::RemapToken メソッド</span><span class="sxs-lookup"><span data-stu-id="84adb-102">ISymUnmanagedWriter::RemapToken Method</span></span>

<span data-ttu-id="84adb-103">メタデータが生成されたときにメタデータトークンが再マップされたことをシンボルライターに通知します。</span><span class="sxs-lookup"><span data-stu-id="84adb-103">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span> <span data-ttu-id="84adb-104">シンボルライターがシンボルストア内に古いトークンを格納している場合は、格納されているトークンを新しい値で更新するか、読み取りフェーズ中に対応するシンボルリーダーがマップを再マップするようにマップを保存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="84adb-104">If the symbol writer has stored the old token within the symbol store, it must either update the stored token with the new value, or it must save the map for the corresponding symbol reader to remap during the read phase.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84adb-105">構文</span><span class="sxs-lookup"><span data-stu-id="84adb-105">Syntax</span></span>  
  
```cpp  
HRESULT RemapToken(  
    [in] mdToken  oldToken,  
    [in] mdToken  newToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84adb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="84adb-106">Parameters</span></span>  

 `oldToken`  
 <span data-ttu-id="84adb-107">から再マップされたメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="84adb-107">[in] The metadata token that was remapped.</span></span>  
  
 `newToken`  
 <span data-ttu-id="84adb-108">からが再マップされた新しいメタデータトークン `oldToken` 。</span><span class="sxs-lookup"><span data-stu-id="84adb-108">[in] The new metadata token to which `oldToken` was remapped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="84adb-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="84adb-109">Return Value</span></span>  

 <span data-ttu-id="84adb-110">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="84adb-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84adb-111">要件</span><span class="sxs-lookup"><span data-stu-id="84adb-111">Requirements</span></span>  

 <span data-ttu-id="84adb-112">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="84adb-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84adb-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="84adb-113">See also</span></span>

- [<span data-ttu-id="84adb-114">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="84adb-114">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
