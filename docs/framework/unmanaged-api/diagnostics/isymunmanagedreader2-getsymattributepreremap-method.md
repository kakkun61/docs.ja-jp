---
title: ISymUnmanagedReader2::GetSymAttributePreRemap メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedReader2.GetSymAttributePreRemap
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedReader2::GetSymAttributePreRemap
helpviewer_keywords:
- GetSymAttributePreRemap method [.NET Framework debugging]
- ISymUnmanagedReader2::GetSymAttributePreRemap method [.NET Framework debugging]
ms.assetid: 7580d546-a709-40c5-ad02-aa70d774fd0b
topic_type:
- apiref
ms.openlocfilehash: 812c0d08930efff9140c6e897d3f93c4909e8464
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95709090"
---
# <a name="isymunmanagedreader2getsymattributepreremap-method"></a><span data-ttu-id="0deb0-102">ISymUnmanagedReader2::GetSymAttributePreRemap メソッド</span><span class="sxs-lookup"><span data-stu-id="0deb0-102">ISymUnmanagedReader2::GetSymAttributePreRemap Method</span></span>

<span data-ttu-id="0deb0-103">名前に基づいてカスタム属性を取得します。</span><span class="sxs-lookup"><span data-stu-id="0deb0-103">Gets a custom attribute based upon its name.</span></span> <span data-ttu-id="0deb0-104">メタデータのカスタム属性とは異なり、これらの属性はシンボルストアに保持されます。</span><span class="sxs-lookup"><span data-stu-id="0deb0-104">Unlike metadata custom attributes, these attributes are held in the symbol store.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0deb0-105">構文</span><span class="sxs-lookup"><span data-stu-id="0deb0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymAttributePreRemap(  
    [in]  mdToken  parent,  
    [in]  WCHAR    *name,  
    [in]  ULONG32  cBuffer,  
    [out] ULONG32  *pcBuffer,  
    [out, size_is(cBuffer),  
        length_is(*pcBuffer)] BYTE buffer[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0deb0-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0deb0-106">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="0deb0-107">から親のメタデータトークン。</span><span class="sxs-lookup"><span data-stu-id="0deb0-107">[in] The metadata token of the parent.</span></span>  
  
 `name`  
 <span data-ttu-id="0deb0-108">から名前を格納し `WCHAR` ているへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0deb0-108">[in] A pointer to a `WCHAR` that contains the name.</span></span>  
  
 `cBuffer`  
 <span data-ttu-id="0deb0-109">から `ULONG32` 配列のサイズを示す `buffer` 。</span><span class="sxs-lookup"><span data-stu-id="0deb0-109">[in] A `ULONG32` that indicates the size of the `buffer` array.</span></span>  
  
 `pcBuffer`  
 <span data-ttu-id="0deb0-110">入出力 `ULONG32` 属性バイトを格納するために必要なバッファーのサイズを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0deb0-110">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the attribute bytes.</span></span>  
  
 `buffer`  
 <span data-ttu-id="0deb0-111">入出力属性バイトを受け取るバッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="0deb0-111">[out] A pointer to the buffer that receives the attribute bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0deb0-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="0deb0-112">Return Value</span></span>  

 <span data-ttu-id="0deb0-113">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="0deb0-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0deb0-114">要件</span><span class="sxs-lookup"><span data-stu-id="0deb0-114">Requirements</span></span>  

 <span data-ttu-id="0deb0-115">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="0deb0-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0deb0-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="0deb0-116">See also</span></span>

- [<span data-ttu-id="0deb0-117">ISymUnmanagedReader2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="0deb0-117">ISymUnmanagedReader2 Interface</span></span>](isymunmanagedreader2-interface.md)
