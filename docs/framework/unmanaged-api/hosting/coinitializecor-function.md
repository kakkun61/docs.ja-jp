---
title: CoInitializeCor 関数
ms.date: 03/30/2017
api_name:
- CoInitializeCor
api_location:
- mscoree.dll
- mscorsvr.dll
api_type:
- DLLExport
f1_keywords:
- CoInitializeCor
helpviewer_keywords:
- CoInitializeCor function [.NET Framework hosting]
ms.assetid: 9b9079fb-579e-4141-b3f0-791072dd40dc
topic_type:
- apiref
ms.openlocfilehash: 9d077d5c5a414568b5643cad0171e101d7bb06f9
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731710"
---
# <a name="coinitializecor-function"></a><span data-ttu-id="00ab3-102">CoInitializeCor 関数</span><span class="sxs-lookup"><span data-stu-id="00ab3-102">CoInitializeCor Function</span></span>

<span data-ttu-id="00ab3-103">`CoInitializeCor` は互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="00ab3-103">`CoInitializeCor` is obsolete.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00ab3-104">構文</span><span class="sxs-lookup"><span data-stu-id="00ab3-104">Syntax</span></span>  
  
```cpp  
STDAPI CoInitializeCor (  
    DWORD fFlags  
);  
```  
  
## <a name="remarks"></a><span data-ttu-id="00ab3-105">解説</span><span class="sxs-lookup"><span data-stu-id="00ab3-105">Remarks</span></span>  

 <span data-ttu-id="00ab3-106">共通言語ランタイムを初期化するには、 [Corbindtoruntimeex](corbindtoruntimeex-function.md) または [Corbindtoの entruntime](corbindtocurrentruntime-function.md)を使用します。</span><span class="sxs-lookup"><span data-stu-id="00ab3-106">To initialize the common language runtime, use either [CorBindToRuntimeEx](corbindtoruntimeex-function.md) or [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00ab3-107">要件</span><span class="sxs-lookup"><span data-stu-id="00ab3-107">Requirements</span></span>  

 <span data-ttu-id="00ab3-108">**ヘッダー:** Cor</span><span class="sxs-lookup"><span data-stu-id="00ab3-108">**Header:** Cor.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00ab3-109">関連項目</span><span class="sxs-lookup"><span data-stu-id="00ab3-109">See also</span></span>

- [<span data-ttu-id="00ab3-110">メタデータ グローバル静的関数</span><span class="sxs-lookup"><span data-stu-id="00ab3-110">Metadata Global Static Functions</span></span>](../metadata/metadata-global-static-functions.md)
