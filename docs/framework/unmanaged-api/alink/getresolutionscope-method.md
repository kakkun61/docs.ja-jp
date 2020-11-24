---
title: GetResolutionScope メソッド
ms.date: 03/30/2017
api_name:
- IALink.GetResolutionScope
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetResolutionScope
helpviewer_keywords:
- GetResolutionScope method
ms.assetid: 5b48ca60-dacd-44b2-9979-4a5122f00812
topic_type:
- apiref
ms.openlocfilehash: 6318890dd6f0259d8d6a7675380684a129c14c8b
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95684677"
---
# <a name="getresolutionscope-method"></a><span data-ttu-id="49f19-102">GetResolutionScope メソッド</span><span class="sxs-lookup"><span data-stu-id="49f19-102">GetResolutionScope Method</span></span>

<span data-ttu-id="49f19-103">指定された型のスコープを取得します。</span><span class="sxs-lookup"><span data-stu-id="49f19-103">Retrieves the scope of a given type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49f19-104">構文</span><span class="sxs-lookup"><span data-stu-id="49f19-104">Syntax</span></span>  
  
```cpp  
HRESULT GetResolutionScope(  
    mdAssembly  AssemblyID,  
    mdToken     FileToken,  
    mdToken     TargetFile,  
    mdToken*    pScope  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="49f19-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="49f19-105">Parameters</span></span>  

 `AssemblyID`  
 <span data-ttu-id="49f19-106">アセンブリの ID。</span><span class="sxs-lookup"><span data-stu-id="49f19-106">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="49f19-107">参照が必要なファイル。</span><span class="sxs-lookup"><span data-stu-id="49f19-107">File that is in need of a reference.</span></span>  
  
 `TargetFile`  
 <span data-ttu-id="49f19-108">型が定義されているファイルのトークン。通常は、 [Importfile メソッド](importfile-method.md)を使用して取得されます。</span><span class="sxs-lookup"><span data-stu-id="49f19-108">Token of file that type is defined in, usually retrieved with [ImportFile Method](importfile-method.md).</span></span>  
  
 `pScope`  
 <span data-ttu-id="49f19-109">アセンブリまたはモジュール参照を受け取ります。</span><span class="sxs-lookup"><span data-stu-id="49f19-109">Receives the assembly or module reference.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49f19-110">戻り値</span><span class="sxs-lookup"><span data-stu-id="49f19-110">Return Value</span></span>  

 <span data-ttu-id="49f19-111">メソッドが成功した場合は S_OK を返します。</span><span class="sxs-lookup"><span data-stu-id="49f19-111">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49f19-112">要件</span><span class="sxs-lookup"><span data-stu-id="49f19-112">Requirements</span></span>  

 <span data-ttu-id="49f19-113">Alink. h が必要です。</span><span class="sxs-lookup"><span data-stu-id="49f19-113">Requires alink.h.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49f19-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="49f19-114">See also</span></span>

- [<span data-ttu-id="49f19-115">IALink インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49f19-115">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="49f19-116">IALink2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="49f19-116">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="49f19-117">ALink API</span><span class="sxs-lookup"><span data-stu-id="49f19-117">ALink API</span></span>](index.md)
