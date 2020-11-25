---
title: ISymUnmanagedDocument::GetLanguageVendor メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguageVendor
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguageVendor
helpviewer_keywords:
- GetLanguageVendor method [.NET Framework debugging]
- ISymUnmanagedDocument::GetLanguageVendor method [.NET Framework debugging]
ms.assetid: 1d4b702e-4922-441d-8b44-03804284f70b
topic_type:
- apiref
ms.openlocfilehash: bac0f187409a191dda1ef635ec9b2da1aee25981
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95700952"
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="11f9f-102">ISymUnmanagedDocument::GetLanguageVendor メソッド</span><span class="sxs-lookup"><span data-stu-id="11f9f-102">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>

<span data-ttu-id="11f9f-103">このドキュメントの言語販売元を取得します。</span><span class="sxs-lookup"><span data-stu-id="11f9f-103">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11f9f-104">構文</span><span class="sxs-lookup"><span data-stu-id="11f9f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11f9f-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="11f9f-105">Parameters</span></span>  

 `pRetVal`  
 <span data-ttu-id="11f9f-106">入出力言語ベンダーを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="11f9f-106">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="11f9f-107">戻り値</span><span class="sxs-lookup"><span data-stu-id="11f9f-107">Return Value</span></span>  

 <span data-ttu-id="11f9f-108">メソッドが成功した場合は S_OK します。</span><span class="sxs-lookup"><span data-stu-id="11f9f-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11f9f-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="11f9f-109">See also</span></span>

- [<span data-ttu-id="11f9f-110">ISymUnmanagedDocument インターフェイス</span><span class="sxs-lookup"><span data-stu-id="11f9f-110">ISymUnmanagedDocument Interface</span></span>](isymunmanageddocument-interface.md)
