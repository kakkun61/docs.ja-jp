---
title: ISymUnmanagedMethod::GetSequencePoints メソッド
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetSequencePoints
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetSequencePoints
helpviewer_keywords:
- ISymUnmanagedMethod::GetSequencePoints method [.NET Framework debugging]
- GetSequencePoints method [.NET Framework debugging]
ms.assetid: f909ac48-3d8f-49fb-a369-e3d9959151cd
topic_type:
- apiref
ms.openlocfilehash: 38763e687c66dcb038a874c9c17cb0d67e547816
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699353"
---
# <a name="isymunmanagedmethodgetsequencepoints-method"></a><span data-ttu-id="a2f69-102">ISymUnmanagedMethod::GetSequencePoints メソッド</span><span class="sxs-lookup"><span data-stu-id="a2f69-102">ISymUnmanagedMethod::GetSequencePoints Method</span></span>

<span data-ttu-id="a2f69-103">このメソッド内のすべてのシーケンスポイントを取得します。</span><span class="sxs-lookup"><span data-stu-id="a2f69-103">Gets all the sequence points within this method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2f69-104">構文</span><span class="sxs-lookup"><span data-stu-id="a2f69-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSequencePoints(  
    [in]  ULONG32  cPoints,  
    [out] ULONG32  *pcPoints,  
    [in, size_is(cPoints)] ULONG32  offsets[],  
    [in, size_is(cPoints)] ISymUnmanagedDocument* documents[],  
    [in, size_is(cPoints)] ULONG32  lines[],  
    [in, size_is(cPoints)] ULONG32  columns[],  
    [in, size_is(cPoints)] ULONG32  endLines[],  
    [in, size_is(cPoints)] ULONG32  endColumns[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2f69-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="a2f69-105">Parameters</span></span>  

 `cPoints`  
 <span data-ttu-id="a2f69-106">から、、、、、 `ULONG32` およびの各配列のサイズを受け取る `offsets` `documents` `lines` `columns` `endLines` `endColumns` 。</span><span class="sxs-lookup"><span data-stu-id="a2f69-106">[in] A `ULONG32` that receives the size of the `offsets`, `documents`, `lines`, `columns`, `endLines`, and `endColumns` arrays.</span></span>  
  
 `pcPoints`  
 <span data-ttu-id="a2f69-107">入出力 `ULONG32` シーケンスポイントを格納するために必要なバッファーの長さを受け取るへのポインター。</span><span class="sxs-lookup"><span data-stu-id="a2f69-107">[out] A pointer to a `ULONG32` that receives the length of the buffer required to contain the sequence points.</span></span>  
  
 `offsets`  
 <span data-ttu-id="a2f69-108">からシーケンスポイントのメソッドの先頭からの MSIL (Microsoft 中間言語) オフセットを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="a2f69-108">[in] An array in which to store the Microsoft intermediate language (MSIL) offsets from the beginning of the method for the sequence points.</span></span>  
  
 `documents`  
 <span data-ttu-id="a2f69-109">からシーケンスポイントが配置されているドキュメントを格納する配列。</span><span class="sxs-lookup"><span data-stu-id="a2f69-109">[in] An array in which to store the documents in which the sequence points are located.</span></span>  
  
 `lines`  
 <span data-ttu-id="a2f69-110">からシーケンスポイントが配置されているドキュメント内の行を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="a2f69-110">[in] An array in which to store the lines in the documents at which the sequence points are located.</span></span>  
  
 `columns`  
 <span data-ttu-id="a2f69-111">からシーケンスポイントが配置されているドキュメント内の列を格納する配列。</span><span class="sxs-lookup"><span data-stu-id="a2f69-111">[in] An array in which to store the columns in the documents at which the sequence points are located.</span></span>  
  
 `endLines`  
 <span data-ttu-id="a2f69-112">からシーケンスポイントが終了するドキュメント内の行の配列。</span><span class="sxs-lookup"><span data-stu-id="a2f69-112">[in] The array of lines in the documents at which the sequence points end.</span></span>  
  
 `endColumns`  
 <span data-ttu-id="a2f69-113">からシーケンスポイントが終了するドキュメント内の列の配列。</span><span class="sxs-lookup"><span data-stu-id="a2f69-113">[in] The array of columns in the documents at which the sequence points end.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a2f69-114">戻り値</span><span class="sxs-lookup"><span data-stu-id="a2f69-114">Return Value</span></span>  

 <span data-ttu-id="a2f69-115">メソッドが成功した場合は S_OK。それ以外の場合は、E_FAIL またはその他のエラーコードを指定します。</span><span class="sxs-lookup"><span data-stu-id="a2f69-115">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2f69-116">要件</span><span class="sxs-lookup"><span data-stu-id="a2f69-116">Requirements</span></span>  

 <span data-ttu-id="a2f69-117">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="a2f69-117">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2f69-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="a2f69-118">See also</span></span>

- [<span data-ttu-id="a2f69-119">ISymUnmanagedMethod インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a2f69-119">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
