---
title: ISymUnmanagedWriter::DefineGlobalVariable メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineGlobalVariable
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable
helpviewer_keywords:
- ISymUnmanagedWriter::DefineGlobalVariable method [.NET Framework debugging]
- DefineGlobalVariable method [.NET Framework debugging]
ms.assetid: 843c904a-8176-4d8f-bd47-b4d4c29f4c5c
topic_type:
- apiref
ms.openlocfilehash: bc389b7247a6b1d6ce16cb3cf350f1672213b2e2
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95716422"
---
# <a name="isymunmanagedwriterdefineglobalvariable-method"></a><span data-ttu-id="45527-102">ISymUnmanagedWriter::DefineGlobalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="45527-102">ISymUnmanagedWriter::DefineGlobalVariable Method</span></span>

<span data-ttu-id="45527-103">グローバル変数を 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="45527-103">Defines a single global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45527-104">構文</span><span class="sxs-lookup"><span data-stu-id="45527-104">Syntax</span></span>  
  
```cpp  
HRESULT DefineGlobalVariable(  
    [in] const WCHAR  *name,  
    [in] ULONG32      attributes,  
    [in] ULONG32      cSig,  
    [in, size_is(cSig)] unsigned char signature[],  
    [in] ULONG32      addrKind,  
    [in] ULONG32      addr1,  
    [in] ULONG32      addr2,  
    [in] ULONG32      addr3);  
```  
  
## <a name="parameters"></a><span data-ttu-id="45527-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="45527-105">Parameters</span></span>  

 `name`  
 <span data-ttu-id="45527-106">から `WCHAR` グローバル変数名を定義するへのポインター。</span><span class="sxs-lookup"><span data-stu-id="45527-106">[in] A pointer to a `WCHAR` that defines the global variable name.</span></span>  
  
 `attributes`  
 <span data-ttu-id="45527-107">からグローバル変数属性。</span><span class="sxs-lookup"><span data-stu-id="45527-107">[in] The global variable attributes.</span></span>  
  
 `cSig`  
 <span data-ttu-id="45527-108">から `ULONG32` バッファーのサイズ (文字数) を示す `signature` 。</span><span class="sxs-lookup"><span data-stu-id="45527-108">[in] A `ULONG32` that indicates the size, in characters, of the `signature` buffer.</span></span>  
  
 `signature`  
 <span data-ttu-id="45527-109">からグローバル変数シグネチャ。</span><span class="sxs-lookup"><span data-stu-id="45527-109">[in] The global variable signature.</span></span>  
  
 `addrKind`  
 <span data-ttu-id="45527-110">からアドレスの種類。</span><span class="sxs-lookup"><span data-stu-id="45527-110">[in] The address type.</span></span>  
  
 `addr1`  
 <span data-ttu-id="45527-111">からパラメーター指定の最初のアドレス。</span><span class="sxs-lookup"><span data-stu-id="45527-111">[in] The first address for the parameter specification.</span></span>  
  
 `addr2`  
 <span data-ttu-id="45527-112">からパラメーター指定の2番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="45527-112">[in] The second address for the parameter specification.</span></span>  
  
 `addr3`  
 <span data-ttu-id="45527-113">からパラメーター指定の3番目のアドレス。</span><span class="sxs-lookup"><span data-stu-id="45527-113">[in] The third address for the parameter specification.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="45527-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="45527-114">Return Value</span></span>  

 <span data-ttu-id="45527-115">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="45527-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45527-116">要件</span><span class="sxs-lookup"><span data-stu-id="45527-116">Requirements</span></span>  

 <span data-ttu-id="45527-117">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="45527-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45527-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="45527-118">See also</span></span>

- [<span data-ttu-id="45527-119">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="45527-119">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
- [<span data-ttu-id="45527-120">DefineLocalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="45527-120">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)
- [<span data-ttu-id="45527-121">DefineGlobalVariable2 メソッド</span><span class="sxs-lookup"><span data-stu-id="45527-121">DefineGlobalVariable2 Method</span></span>](isymunmanagedwriter2-defineglobalvariable2-method.md)
