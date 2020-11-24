---
title: _AxlRSAKeyValueToPublicKeyToken 関数
ms.date: 03/30/2017
api_name:
- _AxlRSAKeyValueToPublicKeyToken
api_location:
- clr.dll
api_type:
- DLLExport
ms.assetid: d60f19fe-7bec-47ba-b60e-ba9ce66abf8c
ms.openlocfilehash: 5c1e2bfc7fd55e807af68744e28faa473daea772
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674217"
---
# <a name="_axlrsakeyvaluetopublickeytoken-function"></a><span data-ttu-id="aa2ec-102">\_AxlRSAKeyValueToPublicKeyToken 関数</span><span class="sxs-lookup"><span data-stu-id="aa2ec-102">\_AxlRSAKeyValueToPublicKeyToken function</span></span>

<span data-ttu-id="aa2ec-103">Modulus および Exponent を、厳密な名前の公開キー トークンに変換します。</span><span class="sxs-lookup"><span data-stu-id="aa2ec-103">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa2ec-104">構文</span><span class="sxs-lookup"><span data-stu-id="aa2ec-104">Syntax</span></span>  
  
```cpp  
HRESULT _AxlRSAKeyValueToPublicKeyToken (  
    [in]  PCRYPT_DATA_BLOB pModulusBlob,  
    [in]  PCRYPT_DATA_BLOB pExponentBlob,  
    [out] LPWSTR           *ppwszPublicKeyToken  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa2ec-105">パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa2ec-105">Parameters</span></span>  

 `pModulusBlob`  
 <span data-ttu-id="aa2ec-106">からBase64 でエンコードされた剰余 blob ( \<Modulus> 要素から)。</span><span class="sxs-lookup"><span data-stu-id="aa2ec-106">[in] The base64-encoded Modulus blob (from the \<Modulus> element).</span></span>  <span data-ttu-id="aa2ec-107">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob)構造を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa2ec-107">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `pExponentBlob`  
 <span data-ttu-id="aa2ec-108">からBase64 でエンコードされた指数 (要素からの \<Exponent> ) blob。</span><span class="sxs-lookup"><span data-stu-id="aa2ec-108">[in] The base64-encoded Exponent blob (from the \<Exponent> element).</span></span> <span data-ttu-id="aa2ec-109">[CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob)構造を参照してください。</span><span class="sxs-lookup"><span data-stu-id="aa2ec-109">See the [CRYPTOAPI_BLOB](/windows/win32/api/dpapi/ns-dpapi-crypt_integer_blob) structure.</span></span>  
  
 `ppwszPublicKeyToken`  
 <span data-ttu-id="aa2ec-110">[out] 16 進エンコードされた公開キー トークンを受け取るための WCHAR \* へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa2ec-110">[out] A pointer to WCHAR \* to receive the hex-encoded public key token.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aa2ec-111">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa2ec-111">Return Value</span></span>  

 <span data-ttu-id="aa2ec-112">関数が成功した場合は `S_OK`。</span><span class="sxs-lookup"><span data-stu-id="aa2ec-112">`S_OK` if the function succeeds.</span></span> <span data-ttu-id="aa2ec-113">それ以外の場合はエラー コードを返します。</span><span class="sxs-lookup"><span data-stu-id="aa2ec-113">Otherwise, returns an error code.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa2ec-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="aa2ec-114">See also</span></span>

- [<span data-ttu-id="aa2ec-115">Authenticode</span><span class="sxs-lookup"><span data-stu-id="aa2ec-115">Authenticode</span></span>](index.md)
