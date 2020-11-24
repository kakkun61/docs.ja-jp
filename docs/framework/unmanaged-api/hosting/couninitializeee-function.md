---
title: CoUninitializeEE 関数
ms.date: 03/30/2017
api_name:
- CoUninitializeEE
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeEE
helpviewer_keywords:
- CoUninitializeEE function [.NET Framework hosting]
ms.assetid: 5f5a311a-839a-465f-89d9-ff1c74da9736
topic_type:
- apiref
ms.openlocfilehash: e6616392eaa23f8ba40247c5aabd12e4d530cea1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687848"
---
# <a name="couninitializeee-function"></a><span data-ttu-id="c07f3-102">CoUninitializeEE 関数</span><span class="sxs-lookup"><span data-stu-id="c07f3-102">CoUninitializeEE Function</span></span>

<span data-ttu-id="c07f3-103">`CoUninitializeEE` は互換性のために残されており、機能を提供しません。</span><span class="sxs-lookup"><span data-stu-id="c07f3-103">`CoUninitializeEE` is obsolete and provides no functionality.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c07f3-104">構文</span><span class="sxs-lookup"><span data-stu-id="c07f3-104">Syntax</span></span>  
  
```cpp  
void CoUninitializeEE (  
    BOOL fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="c07f3-105">解説</span><span class="sxs-lookup"><span data-stu-id="c07f3-105">Remarks</span></span>  

 <span data-ttu-id="c07f3-106">共通言語ランタイムの実行エンジンをプロセスからアンロードできません。</span><span class="sxs-lookup"><span data-stu-id="c07f3-106">The common language runtime execution engine cannot be unloaded from a process.</span></span> <span data-ttu-id="c07f3-107">実行エンジンをシャットダウンするには、 [CorExitProcess](corexitprocess-function.md)を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="c07f3-107">To shut down the execution engine call [CorExitProcess](corexitprocess-function.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c07f3-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="c07f3-108">See also</span></span>

- [<span data-ttu-id="c07f3-109">CoInitializeEE 関数</span><span class="sxs-lookup"><span data-stu-id="c07f3-109">CoInitializeEE Function</span></span>](coinitializeee-function.md)
- [<span data-ttu-id="c07f3-110">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="c07f3-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
