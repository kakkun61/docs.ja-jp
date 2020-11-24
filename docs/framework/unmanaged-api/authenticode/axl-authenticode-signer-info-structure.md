---
title: AXL_AUTHENTICODE_SIGNER_INFO 構造体
ms.date: 03/30/2017
ms.assetid: 81c0f8b4-ce35-4716-8651-b642d40648a2
ms.openlocfilehash: 1bb6df4aa82f8dfc367083732af2065aba9d07b1
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679989"
---
# <a name="axl_authenticode_signer_info-structure"></a><span data-ttu-id="95456-102">AXL_AUTHENTICODE_SIGNER_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="95456-102">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>

<span data-ttu-id="95456-103">Authenticode の署名者情報を定義します。</span><span class="sxs-lookup"><span data-stu-id="95456-103">Defines the Authenticode signer information.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95456-104">構文</span><span class="sxs-lookup"><span data-stu-id="95456-104">Syntax</span></span>  
  
```cpp  
typedef struct _AXL_AUTHENTICODE_SIGNER_INFO {  
    DWORD cbSize;  
    HRESULT dwError;  
    ALG_ID algHash;  
    LPCWSTR pwszHash  
    LPCWSTR pwszDescription;  
    LPCWSTR pwszDescriptionUrl;  
    PCCERT_CHAIN_CONTEXT pChainContext  
} AXL_AUTHENTICODE_SIGNER_INFO, * PAXL_AUTHENTICODE_SIGNER_INFO;  
```  
  
## <a name="members"></a><span data-ttu-id="95456-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="95456-105">Members</span></span>  
  
|<span data-ttu-id="95456-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="95456-106">Member</span></span>|<span data-ttu-id="95456-107">説明</span><span class="sxs-lookup"><span data-stu-id="95456-107">Description</span></span>|  
|------------|-----------------|  
|`cbSize`|<span data-ttu-id="95456-108">この構造のサイズ。</span><span class="sxs-lookup"><span data-stu-id="95456-108">The size of this structure.</span></span>|  
|`dwError`|<span data-ttu-id="95456-109">エラー コード。</span><span class="sxs-lookup"><span data-stu-id="95456-109">The error code.</span></span>|  
|`algHash`|<span data-ttu-id="95456-110">ハッシュアルゴリズム。</span><span class="sxs-lookup"><span data-stu-id="95456-110">The hash algorithm.</span></span>|  
|`pwszHash`|<span data-ttu-id="95456-111">ハッシュです。</span><span class="sxs-lookup"><span data-stu-id="95456-111">The hash.</span></span>|  
|`pwszDescription`|<span data-ttu-id="95456-112">説明です。</span><span class="sxs-lookup"><span data-stu-id="95456-112">The description.</span></span>|  
|`pwszDescriptionUrl`|<span data-ttu-id="95456-113">説明の URL。</span><span class="sxs-lookup"><span data-stu-id="95456-113">The URL of the description.</span></span>|  
|`pChainContext`|<span data-ttu-id="95456-114">署名者のチェーン コンテキスト。</span><span class="sxs-lookup"><span data-stu-id="95456-114">The chain context of the signer.</span></span> <span data-ttu-id="95456-115">[CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context)構造を参照してください。</span><span class="sxs-lookup"><span data-stu-id="95456-115">See the [CERT_CONTEXT](/windows/win32/api/wincrypt/ns-wincrypt-cert_context) structure.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95456-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="95456-116">See also</span></span>

- [<span data-ttu-id="95456-117">Authenticode</span><span class="sxs-lookup"><span data-stu-id="95456-117">Authenticode</span></span>](index.md)
