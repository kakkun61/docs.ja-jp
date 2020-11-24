---
title: CoUninitializeCor 関数
ms.date: 03/30/2017
api_name:
- CoUninitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoUninitializeCor
helpviewer_keywords:
- CoUninitializeCor function [.NET Framework hosting]
ms.assetid: 50a95b8b-9766-470e-bb29-2c7ecddfd4a1
topic_type:
- apiref
ms.openlocfilehash: 7d39c6fda6f159bfc937f62dc45d0d7ce37657f3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95687882"
---
# <a name="couninitializecor-function"></a><span data-ttu-id="a3746-102">CoUninitializeCor 関数</span><span class="sxs-lookup"><span data-stu-id="a3746-102">CoUninitializeCor Function</span></span>

<span data-ttu-id="a3746-103">`CoUninitializeCor` は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="a3746-103">`CoUninitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a3746-104">構文</span><span class="sxs-lookup"><span data-stu-id="a3746-104">Syntax</span></span>  
  
```cpp  
STDAPI_(void) CoUninitializeCor(void);  
```  
  
## <a name="remarks"></a><span data-ttu-id="a3746-105">解説</span><span class="sxs-lookup"><span data-stu-id="a3746-105">Remarks</span></span>  

 <span data-ttu-id="a3746-106">共通言語ランタイムをプロセスからアンロードすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a3746-106">The common language runtime cannot be unloaded from a process.</span></span> <span data-ttu-id="a3746-107">実行中のプロセスからランタイムを完全に削除するには、そのプロセスをシャットダウンする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a3746-107">To completely remove the runtime from a running process, you must shut down that process.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3746-108">関連項目</span><span class="sxs-lookup"><span data-stu-id="a3746-108">See also</span></span>

- [<span data-ttu-id="a3746-109">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="a3746-109">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
