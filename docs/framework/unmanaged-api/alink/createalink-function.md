---
title: CreateALink 関数
ms.date: 03/30/2017
api_name:
- CreateALink
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- CreateALink
helpviewer_keywords:
- CreateALink function
- Alink API, CreateALink function
ms.assetid: fc73bcb9-6af6-44d8-bc39-2f4400325dae
topic_type:
- apiref
ms.openlocfilehash: 98c6ed4657dc69554a9fcca27145f65c621492f4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95683732"
---
# <a name="createalink-function"></a><span data-ttu-id="769d4-102">CreateALink 関数</span><span class="sxs-lookup"><span data-stu-id="769d4-102">CreateALink Function</span></span>

<span data-ttu-id="769d4-103">アセンブリリンカーのインスタンスを作成し、指定したインターフェイスへのポインターを設定します。</span><span class="sxs-lookup"><span data-stu-id="769d4-103">Creates an instance of the Assembly Linker and sets a pointer to the specified interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="769d4-104">構文</span><span class="sxs-lookup"><span data-stu-id="769d4-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateALink (  
   REFIID riid,  
   IUnknown **ppInterface  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="769d4-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="769d4-105">Parameters</span></span>  
  
|<span data-ttu-id="769d4-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="769d4-106">Parameter</span></span>|<span data-ttu-id="769d4-107">説明</span><span class="sxs-lookup"><span data-stu-id="769d4-107">Description</span></span>|  
|---------------|-----------------|  
|`riid`|<span data-ttu-id="769d4-108">アセンブリリンカーインターフェイスの1つの物理名。</span><span class="sxs-lookup"><span data-stu-id="769d4-108">The physical name of one of the Assembly Linker interfaces.</span></span>|  
|`ppInterface`|<span data-ttu-id="769d4-109">正常に完了した場所には、インターフェイスへのポインターが含まれてい `riid` ます。</span><span class="sxs-lookup"><span data-stu-id="769d4-109">The location that on successful completion contains a pointer to the `riid` interface.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="769d4-110">要件</span><span class="sxs-lookup"><span data-stu-id="769d4-110">Requirements</span></span>  

 <span data-ttu-id="769d4-111">**ライブラリ**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="769d4-111">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="769d4-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="769d4-112">See also</span></span>

- [<span data-ttu-id="769d4-113">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="769d4-113">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
