---
title: CertFreeAuthenticodeTimestamperInfo 関数
ms.date: 03/30/2017
api_name:
- CertFreeAuthenticodeTimestamperInfo
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 3eb14c49-68c2-4516-ac89-e5bd7473831c
ms.openlocfilehash: 1ef71b14faf66c179030dff2a7d953e27463c1f7
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674165"
---
# <a name="certfreeauthenticodetimestamperinfo-function"></a><span data-ttu-id="0a45e-102">CertFreeAuthenticodeTimestamperInfo 関数</span><span class="sxs-lookup"><span data-stu-id="0a45e-102">CertFreeAuthenticodeTimestamperInfo Function</span></span>

<span data-ttu-id="0a45e-103">[AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md)構造に割り当てられたリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="0a45e-103">Frees resources allocated for the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a45e-104">構文</span><span class="sxs-lookup"><span data-stu-id="0a45e-104">Syntax</span></span>  
  
```cpp  
HRESULT CertFreeAuthenticodeTimestamperInfo (  
    [in, out]  PAXL_AUTHENTICODE_TIMESTAMPER_INFO   pTimestamperInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0a45e-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="0a45e-105">Parameters</span></span>  

 `pTimestamperInfo`  
 <span data-ttu-id="0a45e-106">[入力、出力] 解放されるタイム スタンパー情報。</span><span class="sxs-lookup"><span data-stu-id="0a45e-106">[in, out] The time stamper information to be released.</span></span> <span data-ttu-id="0a45e-107">[AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md)構造を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0a45e-107">See the [AXL_AUTHENTICODE_TIMESTAMPER_INFO](axl-authenticode-timestamper-info-structure.md) structure.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0a45e-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="0a45e-108">Return Value</span></span>  

 <span data-ttu-id="0a45e-109">関数が成功した場合は `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="0a45e-109">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="0a45e-110">それ以外の場合はエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="0a45e-110">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a45e-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a45e-111">See also</span></span>

- [<span data-ttu-id="0a45e-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="0a45e-112">Authenticode</span></span>](index.md)
