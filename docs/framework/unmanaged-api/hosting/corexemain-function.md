---
title: _CorExeMain 関数
ms.date: 03/30/2017
api_name:
- _CorExeMain
api_location:
- mscoree.dll
- clr.dll
- mscorwks.dll
- mscoreei.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain
helpviewer_keywords:
- _CorExeMain function [.NET Framework hosting]
ms.assetid: 898f76e2-16f4-4a63-b7d9-dad2d3824d8a
topic_type:
- apiref
ms.openlocfilehash: af1d0e2039024a51341e30bec497c581a0bcacb3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673671"
---
# <a name="_corexemain-function"></a><span data-ttu-id="a89f4-102">_CorExeMain 関数</span><span class="sxs-lookup"><span data-stu-id="a89f4-102">_CorExeMain Function</span></span>

<span data-ttu-id="a89f4-103">共通言語ランタイム (CLR) を初期化し、実行可能アセンブリの CLR ヘッダーでマネージエントリポイントを検索して、実行を開始します。</span><span class="sxs-lookup"><span data-stu-id="a89f4-103">Initializes the common language runtime (CLR), locates the managed entry point in the executable assembly's CLR header, and begins execution.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a89f4-104">構文</span><span class="sxs-lookup"><span data-stu-id="a89f4-104">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="a89f4-105">解説</span><span class="sxs-lookup"><span data-stu-id="a89f4-105">Remarks</span></span>  

 <span data-ttu-id="a89f4-106">この関数は、マネージ実行可能アセンブリから作成されたプロセスでローダーによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a89f4-106">This function is called by the loader in processes created from managed executable assemblies.</span></span> <span data-ttu-id="a89f4-107">DLL アセンブリの場合、ローダーは代わりに [_CorDllMain](cordllmain-function.md) 関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a89f4-107">For DLL assemblies, the loader calls the [_CorDllMain](cordllmain-function.md) function instead.</span></span>  
  
 <span data-ttu-id="a89f4-108">オペレーティングシステムローダーは、イメージファイルで指定されたエントリポイントに関係なく、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="a89f4-108">The operating system loader calls this method regardless of the entry point specified in the image file.</span></span>  
  
 <span data-ttu-id="a89f4-109">Windows 98、Windows ME、Windows NT、および Windows 2000 では、 `_CorExeMain` 関数はオペレーティングシステムローダーの修正によって間接的に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a89f4-109">In Windows 98, Windows ME, Windows NT, and Windows 2000, the `_CorExeMain` function is called indirectly through a fixup in the operating system loader.</span></span> <span data-ttu-id="a89f4-110">それ以外のすべてのバージョンの Windows では、オペレーティングシステムローダーによって直接呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="a89f4-110">In all other versions of Windows, it is called directly by the operating system loader.</span></span>  
  
 <span data-ttu-id="a89f4-111">詳細については、「 [_CorValidateImage](corvalidateimage-function.md) 」トピックの「解説」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a89f4-111">For additional information, see the Remarks section in the [_CorValidateImage](corvalidateimage-function.md) topic.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a89f4-112">要件</span><span class="sxs-lookup"><span data-stu-id="a89f4-112">Requirements</span></span>  

 <span data-ttu-id="a89f4-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a89f4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a89f4-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="a89f4-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a89f4-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="a89f4-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a89f4-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a89f4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a89f4-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="a89f4-117">See also</span></span>

- [<span data-ttu-id="a89f4-118">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="a89f4-118">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
