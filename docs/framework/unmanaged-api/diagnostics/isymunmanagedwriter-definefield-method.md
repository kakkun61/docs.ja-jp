---
title: ISymUnmanagedWriter::DefineField メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineField
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineField
helpviewer_keywords:
- ISymUnmanagedWriter::DefineField method [.NET Framework debugging]
- DefineField method, ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: c6a1f797-dbf4-40f5-ab99-d9b4bfb26148
topic_type:
- apiref
ms.openlocfilehash: 5683c10938873821cbe998dbf13937a6a7d24d7c
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95675088"
---
# <a name="isymunmanagedwriterdefinefield-method"></a><span data-ttu-id="99961-102">ISymUnmanagedWriter::DefineField メソッド</span><span class="sxs-lookup"><span data-stu-id="99961-102">ISymUnmanagedWriter::DefineField Method</span></span>

<span data-ttu-id="99961-103">メソッド内にない単一の変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="99961-103">Defines a single variable that is not within a method.</span></span> <span data-ttu-id="99961-104">このメソッドは、クラス、ビットフィールドなどの特定のフィールドに対して使用されます。</span><span class="sxs-lookup"><span data-stu-id="99961-104">This method is used for certain fields in classes, bit fields, and so on.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99961-105">構文</span><span class="sxs-lookup"><span data-stu-id="99961-105">Syntax</span></span>  
  
```cpp  
HRESULT DefineField(  
    [in] mdTypeDef    parent,  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="99961-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="99961-106">Parameters</span></span>  

 `parent`  
 <span data-ttu-id="99961-107">からメタデータ型またはメソッドトークン。</span><span class="sxs-lookup"><span data-stu-id="99961-107">[in] The metadata type or method token.</span></span>  
  
 `name`  
 <span data-ttu-id="99961-108">からフィールド名。</span><span class="sxs-lookup"><span data-stu-id="99961-108">[in] The field name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="99961-109">からフィールド属性。</span><span class="sxs-lookup"><span data-stu-id="99961-109">[in] The field attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="99961-110">から `ULONG32` フィールドシグネチャを格納するために必要なバッファーのサイズ (文字数) を表す。</span><span class="sxs-lookup"><span data-stu-id="99961-110">[in] A `ULONG32` that is the size, in characters, of the buffer required to contain the field signature.</span></span>  
  
 `signature`  
 <span data-ttu-id="99961-111">からフィールドシグネチャの配列。</span><span class="sxs-lookup"><span data-stu-id="99961-111">[in] The array of field signatures.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="99961-112">からアドレスの種類。</span><span class="sxs-lookup"><span data-stu-id="99961-112">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="99961-113">からフィールド指定の最初のアドレス。</span><span class="sxs-lookup"><span data-stu-id="99961-113">[in] The first address for the field specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="99961-114">からフィールド指定の2番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="99961-114">[in] The second address for the field specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="99961-115">からフィールド指定の3番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="99961-115">[in] The third address for the field specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="99961-116">戻り値</span><span class="sxs-lookup"><span data-stu-id="99961-116">Return Value</span></span>  

 <span data-ttu-id="99961-117">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="99961-117">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99961-118">要件</span><span class="sxs-lookup"><span data-stu-id="99961-118">Requirements</span></span>  

 <span data-ttu-id="99961-119">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="99961-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99961-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="99961-120">See also</span></span>

- [<span data-ttu-id="99961-121">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="99961-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
