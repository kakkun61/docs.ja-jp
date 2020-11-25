---
title: PreCloseAssembly メソッド
ms.date: 03/30/2017
api_name:
- IALink.PreCloseAssembly
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- PreCloseAssembly
helpviewer_keywords:
- PreCloseAssembly method
ms.assetid: 6d23ac54-15ea-4027-a172-9ebef43e8f56
topic_type:
- apiref
ms.openlocfilehash: 31c0c5e23d1a985c2005693e25ca91379037482a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95728681"
---
# <a name="precloseassembly-method"></a><span data-ttu-id="74643-102">PreCloseAssembly メソッド</span><span class="sxs-lookup"><span data-stu-id="74643-102">PreCloseAssembly Method</span></span>

<span data-ttu-id="74643-103">アセンブリファイルを閉じます。</span><span class="sxs-lookup"><span data-stu-id="74643-103">Closes the assembly file.</span></span> <span data-ttu-id="74643-104">他のすべてのファイルを閉じた後、アセンブリファイルを閉じる前に、このメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="74643-104">Call this method after closing all other files, but before closing the assembly file.</span></span> <span data-ttu-id="74643-105">バインドされていないモジュールに対しては、このメソッドを呼び出さないでください。</span><span class="sxs-lookup"><span data-stu-id="74643-105">Do not call this method for unbound modules.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="74643-106">構文</span><span class="sxs-lookup"><span data-stu-id="74643-106">Syntax</span></span>  
  
```cpp  
HRESULT PreCloseAssembly(  
    mdAssembly AssemblyID  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="74643-107">パラメーター</span><span class="sxs-lookup"><span data-stu-id="74643-107">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="74643-108">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="74643-108">ID of the assembly.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="74643-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="74643-109">Return Value</span></span>  

 <span data-ttu-id="74643-110">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="74643-110">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74643-111">要件</span><span class="sxs-lookup"><span data-stu-id="74643-111">Requirements</span></span>  

 <span data-ttu-id="74643-112">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="74643-112">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74643-113">関連項目</span><span class="sxs-lookup"><span data-stu-id="74643-113">See also</span></span>

- [<span data-ttu-id="74643-114">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="74643-114">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="74643-115">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="74643-115">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="74643-116">ALink API</span><span class="sxs-lookup"><span data-stu-id="74643-116">ALink API</span></span>](index.md)
