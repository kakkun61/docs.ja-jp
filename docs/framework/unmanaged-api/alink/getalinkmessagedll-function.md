---
title: GetALinkMessageDll 関数
ms.date: 03/30/2017
api_name:
- GetALinkMessageDll
api_location:
- alink.dll
api_type:
- DLLExport
f1_keywords:
- GetALinkMessageDll
helpviewer_keywords:
- Alink API, GetALinkMessageDll function
- GetALinkMessageDll function
ms.assetid: 67985a22-88a2-4c54-8d99-4bcde9d6213e
topic_type:
- apiref
ms.openlocfilehash: 554bd32ae965b21a88a09577749bbd7975f5ec7e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684747"
---
# <a name="getalinkmessagedll-function"></a><span data-ttu-id="3f5b2-102">GetALinkMessageDll 関数</span><span class="sxs-lookup"><span data-stu-id="3f5b2-102">GetALinkMessageDll Function</span></span>

<span data-ttu-id="3f5b2-103">メッセージ DLL を検索して読み込みます。</span><span class="sxs-lookup"><span data-stu-id="3f5b2-103">Finds and loads the message DLL.</span></span> <span data-ttu-id="3f5b2-104">メッセージ DLL が見つからないか、または読み込むことができなかった場合は0を返します。</span><span class="sxs-lookup"><span data-stu-id="3f5b2-104">Returns 0 if the message DLL could not be located or loaded.</span></span> <span data-ttu-id="3f5b2-105">メッセージ DLL は、名前が言語 ID または現在のディレクトリ内のサブディレクトリにある必要があります。</span><span class="sxs-lookup"><span data-stu-id="3f5b2-105">The message DLL should be either in a subdirectory whose name is a language ID, or in the current directory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f5b2-106">構文</span><span class="sxs-lookup"><span data-stu-id="3f5b2-106">Syntax</span></span>  
  
```cpp  
HINSTANCE WINAPI GetALinkMessageDll();  
```  
  
## <a name="requirements"></a><span data-ttu-id="3f5b2-107">必要条件</span><span class="sxs-lookup"><span data-stu-id="3f5b2-107">Requirements</span></span>  

 <span data-ttu-id="3f5b2-108">**ヘッダー:** alink</span><span class="sxs-lookup"><span data-stu-id="3f5b2-108">**Header:** alink.h</span></span>  
  
 <span data-ttu-id="3f5b2-109">**ライブラリ**: alink.dll</span><span class="sxs-lookup"><span data-stu-id="3f5b2-109">**Library**: alink.dll</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f5b2-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="3f5b2-110">See also</span></span>

- [<span data-ttu-id="3f5b2-111">Al.exe (アセンブリ リンカー)</span><span class="sxs-lookup"><span data-stu-id="3f5b2-111">Al.exe (Assembly Linker)</span></span>](../../tools/al-exe-assembly-linker.md)
