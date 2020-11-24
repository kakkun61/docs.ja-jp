---
title: _AxlGetIssuerPublicKeyHash 関数
ms.date: 03/30/2017
api_name:
- _AxlGetIssuerPublicKeyHash
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: fb626b41-b888-4625-84c3-2c02b5e3866f
ms.openlocfilehash: 49674e43109108e41b135cecbec061ad61e14865
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679963"
---
# <a name="_axlgetissuerpublickeyhash-function"></a><span data-ttu-id="50c78-102">\_AxlGetIssuerPublicKeyHash 関数</span><span class="sxs-lookup"><span data-stu-id="50c78-102">\_AxlGetIssuerPublicKeyHash Function</span></span>

<span data-ttu-id="50c78-103">指定された証明書の署名に使用する秘密キーに関連付けられている公開キーの SHA-1 ハッシュを取得します。</span><span class="sxs-lookup"><span data-stu-id="50c78-103">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50c78-104">構文</span><span class="sxs-lookup"><span data-stu-id="50c78-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlGetIssuerPublicKeyHash (  
    [in]  IN PCRYPT_DATA_BLOB   pChainContext,  
    [out] LPWSTR                *ppwszPublicKeyHash  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="50c78-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="50c78-105">Parameters</span></span>  

 `pChainContext`  
 <span data-ttu-id="50c78-106">[in] CSP 公開キー BLOB。</span><span class="sxs-lookup"><span data-stu-id="50c78-106">[in] The CSP public key blob.</span></span> <span data-ttu-id="50c78-107">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob)構造を参照してください。</span><span class="sxs-lookup"><span data-stu-id="50c78-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyHash`  
 <span data-ttu-id="50c78-108">[out] 16 進エンコードされた公開キー トークンを受け取るための WCHAR \* へのポインター。</span><span class="sxs-lookup"><span data-stu-id="50c78-108">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="50c78-109">戻り値</span><span class="sxs-lookup"><span data-stu-id="50c78-109">Return Value</span></span>  

 <span data-ttu-id="50c78-110">関数が成功した場合は `S_OK`、それ以外の場合は `S_FALSE`。</span><span class="sxs-lookup"><span data-stu-id="50c78-110">`S_OK` if the function succeeds; otherwise `S_FALSE`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50c78-111">関連項目</span><span class="sxs-lookup"><span data-stu-id="50c78-111">See also</span></span>

- [<span data-ttu-id="50c78-112">Authenticode</span><span class="sxs-lookup"><span data-stu-id="50c78-112">Authenticode</span></span>](index.md)
