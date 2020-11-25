---
title: ISymUnmanagedReader::GetSymAttribute メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader.GetSymAttribute
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader::GetSymAttribute
helpviewer_keywords:
- GetSymAttribute method [.NET Framework debugging]
- ISymUnmanagedReader::GetSymAttribute method [.NET Framework debugging]
ms.assetid: c675ce7e-76e7-45ff-8273-3b6489a2767c
topic_type:
- apiref
ms.openlocfilehash: aa3b742babe4a94a43e4e6168dea67c0a0245eb0
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95720582"
---
# <a name="isymunmanagedreadergetsymattribute-method"></a><span data-ttu-id="495c6-102">ISymUnmanagedReader::GetSymAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="495c6-102">ISymUnmanagedReader::GetSymAttribute Method</span></span>

<span data-ttu-id="495c6-103">名前に基づいてカスタム属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="495c6-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="495c6-104">メタデータのカスタム属性とは異なり、これらのカスタム属性はシンボルストアに保持されます。</span><span class="sxs-lookup"><span data-stu-id="495c6-104">Unlike metadata custom attributes, these custom attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="495c6-105">構文</span><span class="sxs-lookup"><span data-stu-id="495c6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttribute (  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is (cBuffer),  
        length_is (*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="495c6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="495c6-106">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="495c6-107">から属性を要求する対象のオブジェクトのメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="495c6-107">[in] The metadata token for the object for which the attribute is requested.</span></span>  
  
 `name`  
 <span data-ttu-id="495c6-108">から取得する属性を示す変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="495c6-108">[in] A pointer to the variable that indicates the attribute to retrieve.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="495c6-109">[in] `buffer` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="495c6-109">[in] The size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="495c6-110">入出力属性データの長さを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="495c6-110">[out] A pointer to the variable that receives the length of the attribute data.</span></span>  
  
 `buffer`  
 <span data-ttu-id="495c6-111">入出力属性データを受け取る変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="495c6-111">[out] A pointer to the variable that receives the attribute data.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="495c6-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="495c6-112">Return Value</span></span>  

 <span data-ttu-id="495c6-113">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="495c6-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="495c6-114">要件</span><span class="sxs-lookup"><span data-stu-id="495c6-114">Requirements</span></span>  

 <span data-ttu-id="495c6-115">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="495c6-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="495c6-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="495c6-116">See also</span></span>

- [<span data-ttu-id="495c6-117">ISymUnmanagedReader インターフェイス</span><span class="sxs-lookup"><span data-stu-id="495c6-117">ISymUnmanagedReader Interface</span></span>](isymunmanagedreader-interface.md)
