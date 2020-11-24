---
title: ICLRStrongName2 インターフェイス
ms.date: 03/30/2017
api_name:
- ICLRStrongName2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRStrongName2
helpviewer_keywords:
- ICLRStrongName2 interface [.NET Framework hosting]
ms.assetid: 9f098a74-201e-4628-a468-8dee9ab99b4a
topic_type:
- apiref
ms.openlocfilehash: df570f32d694ec21e9642e75b4965e169afaccfc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95677649"
---
# <a name="iclrstrongname2-interface"></a><span data-ttu-id="152ec-102">ICLRStrongName2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="152ec-102">ICLRStrongName2 Interface</span></span>

<span data-ttu-id="152ec-103">セキュリティで保護されたハッシュアルゴリズム (SHA-256、SHA-384、および SHA-512) の SHA-1 グループを使用して、厳密な名前を作成する機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="152ec-103">Provides the ability to create strong names using the SHA-2 group of Secure Hash Algorithms (SHA-256, SHA-384, and SHA-512).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="152ec-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="152ec-104">Methods</span></span>  
  
|<span data-ttu-id="152ec-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="152ec-105">Method</span></span>|<span data-ttu-id="152ec-106">説明</span><span class="sxs-lookup"><span data-stu-id="152ec-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="152ec-107">StrongNameGetPublicKeyEx メソッド</span><span class="sxs-lookup"><span data-stu-id="152ec-107">StrongNameGetPublicKeyEx Method</span></span>](strongnamegetpublickeyex-method.md)|<span data-ttu-id="152ec-108">公開キーと秘密キーのペアから公開キーを取得し、ハッシュアルゴリズムと署名アルゴリズムを指定します。</span><span class="sxs-lookup"><span data-stu-id="152ec-108">Gets the public key from a public/private key pair, and specifies a hash algorithm and a signature algorithm.</span></span>|  
|[<span data-ttu-id="152ec-109">StrongNameSignatureVerificationEx2 メソッド</span><span class="sxs-lookup"><span data-stu-id="152ec-109">StrongNameSignatureVerificationEx2 Method</span></span>](strongnamesignatureverificationex2-method.md)|<span data-ttu-id="152ec-110">厳密に名前が付けられたアセンブリの署名を検証し、ECMA キーから実際のキーへのマッピングを提供します。</span><span class="sxs-lookup"><span data-stu-id="152ec-110">Verifies the signature of a strongly named assembly, and provides a mapping from the ECMA key to a real key.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="152ec-111">解説</span><span class="sxs-lookup"><span data-stu-id="152ec-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="152ec-112">必要条件</span><span class="sxs-lookup"><span data-stu-id="152ec-112">Requirements</span></span>  

 <span data-ttu-id="152ec-113">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="152ec-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="152ec-114">**ヘッダー:** メタホスト .h</span><span class="sxs-lookup"><span data-stu-id="152ec-114">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="152ec-115">**ライブラリ:** MSCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="152ec-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="152ec-116">**.NET Framework のバージョン:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="152ec-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>
