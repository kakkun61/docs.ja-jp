---
title: CertFreeAuthenticodeSignerInfo 関数
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeSignerInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 8029633c-b6e4-4665-a7c2-89607c3247ef
ms.openlocfilehash: dc6bb5a137a50ec07f89f292e5d9beac4349c3c7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674178"
---
# <a name="certfreeauthenticodesignerinfo-function"></a><span data-ttu-id="8cd6c-102">CertFreeAuthenticodeSignerInfo 関数</span><span class="sxs-lookup"><span data-stu-id="8cd6c-102">CertFreeAuthenticodeSignerInfo Function</span></span>

<span data-ttu-id="8cd6c-103">[AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md)構造に割り当てられたリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="8cd6c-103">Frees resources allocated for the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cd6c-104">構文</span><span class="sxs-lookup"><span data-stu-id="8cd6c-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeSignerInfo (  
    [in, out]  PAXL_AUTHENTICODE_SIGNER_INFO   pSignerInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8cd6c-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="8cd6c-105">Parameters</span></span>  

 `pSignerInfo`  
 <span data-ttu-id="8cd6c-106">[in, out] リリースされる署名者情報。</span><span class="sxs-lookup"><span data-stu-id="8cd6c-106">[in, out] Signer information to be released.</span></span> <span data-ttu-id="8cd6c-107">[AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md)構造を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8cd6c-107">See the [AXL_AUTHENTICODE_SIGNER_INFO](axl-authenticode-signer-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8cd6c-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="8cd6c-108">Return Value</span></span>  

 <span data-ttu-id="8cd6c-109">関数が成功した場合は `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="8cd6c-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="8cd6c-110">それ以外の場合はエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="8cd6c-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8cd6c-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="8cd6c-111">See also</span></span>

- [<span data-ttu-id="8cd6c-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="8cd6c-112">Authenticode</span></span>](index.md)
