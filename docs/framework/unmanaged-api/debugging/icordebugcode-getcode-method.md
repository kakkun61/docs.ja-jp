---
title: ICorDebugCode::GetCode メソッド
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
ms.openlocfilehash: 20eac75a1f1d13b6a30267d56ff66024725e6f33
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674776"
---
# <a name="icordebugcodegetcode-method"></a><span data-ttu-id="6e496-102">ICorDebugCode::GetCode メソッド</span><span class="sxs-lookup"><span data-stu-id="6e496-102">ICorDebugCode::GetCode Method</span></span>

<span data-ttu-id="6e496-103">指定した関数のすべてのコードを取得し、逆アセンブリ用に書式設定します。</span><span class="sxs-lookup"><span data-stu-id="6e496-103">Gets all the code for the specified function, formatted for disassembly.</span></span> <span data-ttu-id="6e496-104">このメソッドは .NET Framework バージョン2.0 では非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="6e496-104">This method has been deprecated in the .NET Framework version 2.0.</span></span> <span data-ttu-id="6e496-105">代わりに [ICorDebugCode2:: GetCodeChunks](icordebugcode2-getcodechunks-method.md) を使用してください。</span><span class="sxs-lookup"><span data-stu-id="6e496-105">Use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6e496-106">構文</span><span class="sxs-lookup"><span data-stu-id="6e496-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCode (  
    [in] ULONG32     startOffset,
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6e496-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="6e496-107">Parameters</span></span>  

 `startOffset`  
 <span data-ttu-id="6e496-108">から関数の開始位置のオフセット。</span><span class="sxs-lookup"><span data-stu-id="6e496-108">[in] The offset of the beginning of the function.</span></span>  
  
 `endOffset`  
 <span data-ttu-id="6e496-109">から関数の終了位置のオフセット。</span><span class="sxs-lookup"><span data-stu-id="6e496-109">[in] The offset of the end of the function.</span></span>  
  
 `cBufferAlloc`  
 <span data-ttu-id="6e496-110">からコードが返される `buffer` 配列のサイズ。</span><span class="sxs-lookup"><span data-stu-id="6e496-110">[in] The size of the `buffer` array into which the code will be returned.</span></span>  
  
 `buffer`  
 <span data-ttu-id="6e496-111">入出力コードが返される配列。</span><span class="sxs-lookup"><span data-stu-id="6e496-111">[out] The array into which the code will be returned.</span></span>  
  
 `pcBufferSize`  
 <span data-ttu-id="6e496-112">入出力返されたバイト数。</span><span class="sxs-lookup"><span data-stu-id="6e496-112">[out] The number of bytes returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e496-113">注釈</span><span class="sxs-lookup"><span data-stu-id="6e496-113">Remarks</span></span>  

 <span data-ttu-id="6e496-114">関数のコードが複数のチャンクに分割されている場合は、ネイティブオフセットが増加する順序で連結されます。</span><span class="sxs-lookup"><span data-stu-id="6e496-114">If the function's code has been divided into multiple chunks, they are concatenated in order of increasing native offset.</span></span> <span data-ttu-id="6e496-115">命令の境界はチェックされません。</span><span class="sxs-lookup"><span data-stu-id="6e496-115">Instruction boundaries are not checked.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6e496-116">要件</span><span class="sxs-lookup"><span data-stu-id="6e496-116">Requirements</span></span>  

 <span data-ttu-id="6e496-117">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="6e496-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6e496-118">**ヘッダー:** CorDebug.idl、CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6e496-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6e496-119">**ライブラリ:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6e496-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6e496-120">**.NET Framework のバージョン:** 1.1、1.0</span><span class="sxs-lookup"><span data-stu-id="6e496-120">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6e496-121">関連項目</span><span class="sxs-lookup"><span data-stu-id="6e496-121">See also</span></span>

- [<span data-ttu-id="6e496-122">GetCodeChunks メソッド</span><span class="sxs-lookup"><span data-stu-id="6e496-122">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)
