---
title: Authenticode (アンマネージ API リファレンス)
ms.date: 03/30/2017
ms.assetid: 7e8cc303-6e77-4116-aa8b-7ea297a3a467
ms.openlocfilehash: 9b3e1585278bda82dedf7542e866a551867b9c9f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95674048"
---
# <a name="authenticode-unmanaged-api-reference"></a><span data-ttu-id="0a2e3-102">Authenticode (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="0a2e3-102">Authenticode (Unmanaged API Reference)</span></span>

<span data-ttu-id="0a2e3-103">Authenticode XrML ライセンスの作成および検証モジュールをサポートします。</span><span class="sxs-lookup"><span data-stu-id="0a2e3-103">Supports the Authenticode XrML license creation and verification module.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0a2e3-104">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="0a2e3-104">In This Section</span></span>  

 [<span data-ttu-id="0a2e3-105">_AxlGetIssuerPublicKeyHash 関数</span><span class="sxs-lookup"><span data-stu-id="0a2e3-105">_AxlGetIssuerPublicKeyHash Function</span></span>](axlgetissuerpublickeyhash-function.md)  
 <span data-ttu-id="0a2e3-106">指定された証明書の署名に使用する秘密キーに関連付けられている公開キーの SHA-1 ハッシュを取得します。</span><span class="sxs-lookup"><span data-stu-id="0a2e3-106">Retrieves the SHA-1 hash of the public key associated with the private key that is used to sign the specified certificate.</span></span>  
  
 [<span data-ttu-id="0a2e3-107">_AxlPublicKeyBlobToPublicKeyToken 関数</span><span class="sxs-lookup"><span data-stu-id="0a2e3-107">_AxlPublicKeyBlobToPublicKeyToken Function</span></span>](axlpublickeyblobtopublickeytoken-function.md)  
 <span data-ttu-id="0a2e3-108">CSP PUBLICKEYBLOB 形式から厳密な名前の公開キー トークンを算出します。</span><span class="sxs-lookup"><span data-stu-id="0a2e3-108">Computes the strong name public key token from a CSP PUBLICKEYBLOB format.</span></span>  
  
 [<span data-ttu-id="0a2e3-109">_AxlRSAKeyValueToPublicKeyToken 関数</span><span class="sxs-lookup"><span data-stu-id="0a2e3-109">_AxlRSAKeyValueToPublicKeyToken Function</span></span>](axlrsakeyvaluetopublickeytoken-function.md)  
 <span data-ttu-id="0a2e3-110">Modulus および Exponent を、厳密な名前の公開キー トークンに変換します。</span><span class="sxs-lookup"><span data-stu-id="0a2e3-110">Converts a Modulus and Exponent to a strong name public key token.</span></span>  
  
 [<span data-ttu-id="0a2e3-111">CertFreeAuthenticodeSignerInfo 関数</span><span class="sxs-lookup"><span data-stu-id="0a2e3-111">CertFreeAuthenticodeSignerInfo Function</span></span>](certfreeauthenticodesignerinfo-function.md)  
 <span data-ttu-id="0a2e3-112">AXL_AUTHENTICODE_SIGNER_INFO 構造に割り当てられているリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="0a2e3-112">Frees resources allocated for the AXL_AUTHENTICODE_SIGNER_INFO structure.</span></span>  
  
 [<span data-ttu-id="0a2e3-113">CertFreeAuthenticodeTimestamperInfo 関数</span><span class="sxs-lookup"><span data-stu-id="0a2e3-113">CertFreeAuthenticodeTimestamperInfo Function</span></span>](certfreeauthenticodetimestamperinfo-function.md)  
 <span data-ttu-id="0a2e3-114">AXL_AUTHENTICODE_TIMESTAMPER_INFO 構造に割り当てられているリソースを開放します。</span><span class="sxs-lookup"><span data-stu-id="0a2e3-114">Frees resources allocated for the AXL_AUTHENTICODE_TIMESTAMPER_INFO structure.</span></span>  
  
 [<span data-ttu-id="0a2e3-115">CertTimestampAuthenticodeLicense 関数</span><span class="sxs-lookup"><span data-stu-id="0a2e3-115">CertTimestampAuthenticodeLicense Function</span></span>](certtimestampauthenticodelicense-function.md)  
 <span data-ttu-id="0a2e3-116">CertCreateAuthenticodeLicense で作成された Authenticode XrML ライセンスにタイム スタンプを付けます。</span><span class="sxs-lookup"><span data-stu-id="0a2e3-116">Time stamps an Authenticode XrML license created by CertCreateAuthenticodeLicense.</span></span>  
  
 [<span data-ttu-id="0a2e3-117">CertVerifyAuthenticodeLicense 関数</span><span class="sxs-lookup"><span data-stu-id="0a2e3-117">CertVerifyAuthenticodeLicense Function</span></span>](certverifyauthenticodelicense-function.md)  
 <span data-ttu-id="0a2e3-118">Authenticode XrML ライセンスの有効性を検証します。</span><span class="sxs-lookup"><span data-stu-id="0a2e3-118">Verifies the validity of an Authenticode XrML license.</span></span>  
  
 [<span data-ttu-id="0a2e3-119">AXL_AUTHENTICODE_SIGNER_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="0a2e3-119">AXL_AUTHENTICODE_SIGNER_INFO Structure</span></span>](axl-authenticode-signer-info-structure.md)  
 <span data-ttu-id="0a2e3-120">Authenticode の署名者情報を定義します。</span><span class="sxs-lookup"><span data-stu-id="0a2e3-120">Defines the Authenticode signer information.</span></span>  
  
 [<span data-ttu-id="0a2e3-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="0a2e3-121">AXL_AUTHENTICODE_TIMESTAMPER_INFO Structure</span></span>](axl-authenticode-timestamper-info-structure.md)  
 <span data-ttu-id="0a2e3-122">Authenticode のタイム スタンパー情報を定義します。</span><span class="sxs-lookup"><span data-stu-id="0a2e3-122">Defines the Authenticode time stamper information.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0a2e3-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="0a2e3-123">See also</span></span>

- [<span data-ttu-id="0a2e3-124">アンマネージ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="0a2e3-124">Unmanaged API Reference</span></span>](../index.md)
