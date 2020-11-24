---
title: DestroyICeeFileGen 関数
ms.date: 03/30/2017
api_name:
- DestroyICeeFileGen
api_location:
- mscoree.dll
- mscorpehost.dll
- mscorpe.dll
api_type:
- COM
f1_keywords:
- DestroyICeeFileGen
helpviewer_keywords:
- DestroyICeeFileGen function [.NET Framework hosting]
ms.assetid: dc1e2235-e721-4cb2-a0b8-6b0c030d7bab
topic_type:
- apiref
ms.openlocfilehash: 495d84470c559df13ea64b63dd00582f4335d4e3
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95673194"
---
# <a name="destroyiceefilegen-function"></a><span data-ttu-id="d7ec6-102">DestroyICeeFileGen 関数</span><span class="sxs-lookup"><span data-stu-id="d7ec6-102">DestroyICeeFileGen Function</span></span>

<span data-ttu-id="d7ec6-103">[ICeeFileGen](iceefilegen-class.md)オブジェクトを破棄します。</span><span class="sxs-lookup"><span data-stu-id="d7ec6-103">Destroys an [ICeeFileGen](iceefilegen-class.md) object.</span></span>  
  
 <span data-ttu-id="d7ec6-104">この関数は .NET Framework 4 で非推奨とされました。</span><span class="sxs-lookup"><span data-stu-id="d7ec6-104">This function has been deprecated in the .NET Framework 4.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7ec6-105">構文</span><span class="sxs-lookup"><span data-stu-id="d7ec6-105">Syntax</span></span>  
  
```cpp  
HRESULT DestroyICeeFileGen (  
    [in] ICeeFileGen  **ceeFileGen  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d7ec6-106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d7ec6-106">Parameters</span></span>  

 `ceeFileGen`  
 <span data-ttu-id="d7ec6-107">から `ICeeFileGen` 破棄するオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="d7ec6-107">[in] The `ICeeFileGen` object to destroy.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d7ec6-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="d7ec6-108">Return Value</span></span>  

 <span data-ttu-id="d7ec6-109">このメソッドは、標準の COM エラーコードを返します。</span><span class="sxs-lookup"><span data-stu-id="d7ec6-109">This method returns standard COM error codes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d7ec6-110">注釈</span><span class="sxs-lookup"><span data-stu-id="d7ec6-110">Remarks</span></span>  

 <span data-ttu-id="d7ec6-111">`DestroyICeeFileGen``ICeeFileGen` [CreateICeeFileGen](createiceefilegen-function.md)関数によって作成されたオブジェクトを破棄します。</span><span class="sxs-lookup"><span data-stu-id="d7ec6-111">`DestroyICeeFileGen` destroys the `ICeeFileGen` object created by the [CreateICeeFileGen](createiceefilegen-function.md) function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7ec6-112">要件</span><span class="sxs-lookup"><span data-stu-id="d7ec6-112">Requirements</span></span>  

 <span data-ttu-id="d7ec6-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7ec6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7ec6-114">**ヘッダー:** ICeeFileGen</span><span class="sxs-lookup"><span data-stu-id="d7ec6-114">**Header:** ICeeFileGen.h</span></span>  
  
 <span data-ttu-id="d7ec6-115">**ライブラリ:** MSCorPE.dll</span><span class="sxs-lookup"><span data-stu-id="d7ec6-115">**Library:** MSCorPE.dll</span></span>  
  
 <span data-ttu-id="d7ec6-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7ec6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7ec6-117">関連項目</span><span class="sxs-lookup"><span data-stu-id="d7ec6-117">See also</span></span>

- [<span data-ttu-id="d7ec6-118">非推奨の CLR ホスト関数</span><span class="sxs-lookup"><span data-stu-id="d7ec6-118">Deprecated CLR Hosting Functions</span></span>](deprecated-clr-hosting-functions.md)
