---
title: ISymUnmanagedWriter::SetScopeRange メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.SetScopeRange
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::SetScopeRange
helpviewer_keywords:
- SetScopeRange method [.NET Framework debugging]
- ISymUnmanagedWriter::SetScopeRange method [.NET Framework debugging]
ms.assetid: d4d98676-444b-46ca-bfe6-0d827385cd22
topic_type:
- apiref
ms.openlocfilehash: 06dff4847ec3d15f446f1c89219b10eddb8eec4f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683525"
---
# <a name="isymunmanagedwritersetscoperange-method"></a><span data-ttu-id="19560-102">ISymUnmanagedWriter::SetScopeRange メソッド</span><span class="sxs-lookup"><span data-stu-id="19560-102">ISymUnmanagedWriter::SetScopeRange Method</span></span>

<span data-ttu-id="19560-103">指定した構文のスコープのオフセット範囲を定義します。</span><span class="sxs-lookup"><span data-stu-id="19560-103">Defines the offset range for the specified lexical scope.</span></span> <span data-ttu-id="19560-104">スコープは新しい現在のスコープになり、スコープのスタックにプッシュされます。</span><span class="sxs-lookup"><span data-stu-id="19560-104">The scope becomes the new current scope and is pushed onto a stack of scopes.</span></span> <span data-ttu-id="19560-105">スコープは階層を形成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="19560-105">Scopes must form a hierarchy.</span></span> <span data-ttu-id="19560-106">兄弟を重ねることはできません。</span><span class="sxs-lookup"><span data-stu-id="19560-106">Siblings are not allowed to overlap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19560-107">構文</span><span class="sxs-lookup"><span data-stu-id="19560-107">Syntax</span></span>  
  
```cpp  
HRESULT OpenScope(  
    [in] ULONG32  scopeID,  
    [in] ULONG32  startOffset,  
    [in] ULONG32  endOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="19560-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="19560-108">Parameters</span></span>  

 `scopeId`  
 <span data-ttu-id="19560-109">からスコープのスコープ識別子。</span><span class="sxs-lookup"><span data-stu-id="19560-109">[in] The scope identifier for the scope.</span></span>  
  
 `startOffset`  
 <span data-ttu-id="19560-110">からメソッドの先頭からの構文のスコープの最初の命令のオフセット (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="19560-110">[in] The offset, in bytes, of the first instruction in the lexical scope from the beginning of the method.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="19560-111">からメソッドの先頭からの構文のスコープの最後の命令のオフセット (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="19560-111">[in] The offset, in bytes, of the last instruction in the lexical scope from the beginning of the method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="19560-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="19560-112">Return Value</span></span>  

 <span data-ttu-id="19560-113">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="19560-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19560-114">注釈</span><span class="sxs-lookup"><span data-stu-id="19560-114">Remarks</span></span>  

 <span data-ttu-id="19560-115">[ISymUnmanagedWriter:: OpenScope](isymunmanagedwriter-openscope-method.md) は、 `ISymUnmanagedWriter::SetScopeRange` 後でスコープの開始オフセットと終了オフセットを定義するためにと共に使用できる非透過スコープ識別子を返します。</span><span class="sxs-lookup"><span data-stu-id="19560-115">[ISymUnmanagedWriter::OpenScope](isymunmanagedwriter-openscope-method.md) returns an opaque scope identifier that can be used with `ISymUnmanagedWriter::SetScopeRange` to define a scope's starting and ending offset at a later time.</span></span> <span data-ttu-id="19560-116">この場合、 `ISymUnmanagedWriter::OpenScope` と [ISymUnmanagedWriter:: cloに](isymunmanagedwriter-closescope-method.md) 渡されるオフセットは無視されます。</span><span class="sxs-lookup"><span data-stu-id="19560-116">In this case, the offsets passed to `ISymUnmanagedWriter::OpenScope` and [ISymUnmanagedWriter::CloseScope](isymunmanagedwriter-closescope-method.md) are ignored.</span></span> <span data-ttu-id="19560-117">スコープ識別子は、現在のメソッドでのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="19560-117">Scope identifiers are only valid in the current method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19560-118">要件</span><span class="sxs-lookup"><span data-stu-id="19560-118">Requirements</span></span>  

 <span data-ttu-id="19560-119">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="19560-119">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19560-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="19560-120">See also</span></span>

- [<span data-ttu-id="19560-121">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="19560-121">ISymUnmanagedWriter Interface</span></span>](isymunmanagedwriter-interface.md)
