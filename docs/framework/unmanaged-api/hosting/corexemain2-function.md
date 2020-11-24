---
title: _CorExeMain2 関数
ms.date: 03/30/2017
api_name:
- _CorExeMain2
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorExeMain2
helpviewer_keywords:
- _CorExeMain2 function [.NET Framework hosting]
ms.assetid: 72ea68b4-689f-4733-9416-9664b75e8892
topic_type:
- apiref
ms.openlocfilehash: a3fb9d87b6433d46dad081619e0692a42219408d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673624"
---
# <a name="_corexemain2-function"></a><span data-ttu-id="afdbb-102">_CorExeMain2 関数</span><span class="sxs-lookup"><span data-stu-id="afdbb-102">_CorExeMain2 Function</span></span>

<span data-ttu-id="afdbb-103">指定されたメモリ マップト コードのエントリ ポイントを実行します。</span><span class="sxs-lookup"><span data-stu-id="afdbb-103">Executes the entry point in the specified memory-mapped code.</span></span> <span data-ttu-id="afdbb-104">この関数は、オペレーティング システム ローダーによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="afdbb-104">This function is called by the operating system loader.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afdbb-105">構文</span><span class="sxs-lookup"><span data-stu-id="afdbb-105">Syntax</span></span>  
  
```cpp  
__int32 STDMETHODCALLTYPE _CorExeMain2 (  
   [in] PBYTE           pUnmappedPE,  
   [in] DWORD           cUnmappedPE,  
   [in] __in LPWSTR     pImageNameIn,  
   [in] __in LPWSTR     pLoadersFileName,  
   [in] __in LPWSTR     pCmdLine  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="afdbb-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="afdbb-106">Parameters</span></span>  

 `pUnmappedPE`  
 <span data-ttu-id="afdbb-107">からメモリマップトコードへのポインター。</span><span class="sxs-lookup"><span data-stu-id="afdbb-107">[in] A pointer to the memory-mapped code.</span></span>  
  
 `cUnmappedPE`  
 <span data-ttu-id="afdbb-108">から保持できる要素の数 `pUnmappedPE` 。</span><span class="sxs-lookup"><span data-stu-id="afdbb-108">[in] The number of elements `pUnmappedPE` can hold.</span></span>  
  
 `pImageNameIn`  
 <span data-ttu-id="afdbb-109">から実行可能イメージの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="afdbb-109">[in] A pointer to the name of the executable image.</span></span>  
  
 `pLoadersFileName`  
 <span data-ttu-id="afdbb-110">からローダーファイルの名前。</span><span class="sxs-lookup"><span data-stu-id="afdbb-110">[in] The name of the loader file.</span></span>  
  
 `pCmdLine`  
 <span data-ttu-id="afdbb-111">からコマンドラインパラメーター (存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="afdbb-111">[in] Command-line parameters, if any.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afdbb-112">要件</span><span class="sxs-lookup"><span data-stu-id="afdbb-112">Requirements</span></span>  

 <span data-ttu-id="afdbb-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="afdbb-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afdbb-114">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="afdbb-114">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="afdbb-115">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="afdbb-115">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="afdbb-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afdbb-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afdbb-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="afdbb-117">See also</span></span>

- [<span data-ttu-id="afdbb-118">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="afdbb-118">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
