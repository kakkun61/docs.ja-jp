---
title: ISymUnmanagedWriter4::GetDebugInfoWithPadding メソッド
ms.date: 03/30/2017
ms.assetid: 881e20ca-8131-4bd0-ba41-c2d6391b0fe2
ms.openlocfilehash: 4ac2cccfb17d82d8c62ad7db89161aa794825ae5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95678278"
---
# <a name="isymunmanagedwriter4getdebuginfowithpadding-method"></a><span data-ttu-id="c119e-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding メソッド</span><span class="sxs-lookup"><span data-stu-id="c119e-102">ISymUnmanagedWriter4::GetDebugInfoWithPadding Method</span></span>

<span data-ttu-id="c119e-103">関数は [GetDebugInfo メソッド](isymunmanagedwriter-getdebuginfo-method.md) と同じですが、文字列データを固定サイズにするために、終端の null 文字の後にパス文字列がゼロで埋め込まれる点が異なり `MAX_PATH` ます。</span><span class="sxs-lookup"><span data-stu-id="c119e-103">Functions the same as [GetDebugInfo Method](isymunmanagedwriter-getdebuginfo-method.md) except that the path string is padded with zeros following the terminating null character to make the string data a fixed size of `MAX_PATH`.</span></span> <span data-ttu-id="c119e-104">埋め込みは、パス文字列の長さがより小さい場合にのみ指定 `MAX_PATH` します。</span><span class="sxs-lookup"><span data-stu-id="c119e-104">Padding is only given if the path string length itself is less than `MAX_PATH`.</span></span>  
  
 <span data-ttu-id="c119e-105">これにより、PE ファイルを区別するツールを簡単に記述できるようになります。</span><span class="sxs-lookup"><span data-stu-id="c119e-105">This makes it easier to write tools that difference PE files.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c119e-106">構文</span><span class="sxs-lookup"><span data-stu-id="c119e-106">Syntax</span></span>  
  
```idl  
HRESULT GetDebugInfoWithPadding(    [in, out] IMAGE_DEBUG_DIRECTORY *pIDD,    [in] DWORD cData,    [out] DWORD *pcData,    [out, size_is(cData), length_is(*pcData)] BYTE data[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c119e-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c119e-107">Parameters</span></span>  
  
|<span data-ttu-id="c119e-108">パラメーター</span><span class="sxs-lookup"><span data-stu-id="c119e-108">Parameter</span></span>|<span data-ttu-id="c119e-109">説明</span><span class="sxs-lookup"><span data-stu-id="c119e-109">Description</span></span>|  
|---------------|-----------------|  
|`pIDD`||  
|`cData`||  
|`pcData`||  
|`data`||  
  
## <a name="return-value"></a><span data-ttu-id="c119e-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="c119e-110">Return Value</span></span>  

 <span data-ttu-id="c119e-111">`HRESULT` を返します。</span><span class="sxs-lookup"><span data-stu-id="c119e-111">Returns `HRESULT`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c119e-112">要件</span><span class="sxs-lookup"><span data-stu-id="c119e-112">Requirements</span></span>  

 <span data-ttu-id="c119e-113">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="c119e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c119e-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="c119e-114">See also</span></span>

- [<span data-ttu-id="c119e-115">ISymUnmanagedWriter4 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="c119e-115">ISymUnmanagedWriter4 Interface</span></span>](isymunmanagedwriter4-interface.md)
