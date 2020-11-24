---
title: _AxlPublicKeyBlobToPublicKeyToken 関数
ms.date: 03/30/2017
api_name:
- _AxlPublicKeyBlobToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: 2d92a746-d68c-4f53-a16e-727f071a2d80
ms.openlocfilehash: 989e99198efd1519f607a2e3164ff4de584e88af
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679885"
---
# <a name="_axlpublickeyblobtopublickeytoken-function"></a><span data-ttu-id="011bb-102">\_AxlPublicKeyBlobToPublicKeyToken 関数</span><span class="sxs-lookup"><span data-stu-id="011bb-102">\_AxlPublicKeyBlobToPublicKeyToken Function</span></span>

<span data-ttu-id="011bb-103">CSP PUBLICKEYBLOB 形式から厳密な名前の公開キー トークンを算出します。</span><span class="sxs-lookup"><span data-stu-id="011bb-103">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="011bb-104">構文</span><span class="sxs-lookup"><span data-stu-id="011bb-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlPublicKeyBlobToPublicKeyToken (  
    [in]  PCCERT_CHAIN_CONTEXT   pCspPublicKeyBlob,  
    [out] LPWSTR                 *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="011bb-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="011bb-105">Parameters</span></span>  

 `pCspPublicKeyBlob`  
 <span data-ttu-id="011bb-106">[in] CSP 公開キー BLOB。</span><span class="sxs-lookup"><span data-stu-id="011bb-106">[in] The CSP public key blob.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="011bb-107">[out] 16 進エンコードされた公開キー ハッシュを受け取るための WCHAR \* へのポインター。</span><span class="sxs-lookup"><span data-stu-id="011bb-107">[out] A pointer to WCHAR \* to receive the hex-encoded public key hash.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="011bb-108">戻り値</span><span class="sxs-lookup"><span data-stu-id="011bb-108">Return Value</span></span>  

 <span data-ttu-id="011bb-109">関数が成功した場合は `S_OK`、それ以外の場合は `S_FALSE`。</span><span class="sxs-lookup"><span data-stu-id="011bb-109">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="011bb-110">関連項目</span><span class="sxs-lookup"><span data-stu-id="011bb-110">See also</span></span>

- [<span data-ttu-id="011bb-111">Authenticode</span><span class="sxs-lookup"><span data-stu-id="011bb-111">Authenticode</span></span>](index.md)
