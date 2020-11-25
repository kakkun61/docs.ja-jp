---
title: PublicKeyBlob 構造体
ms.date: 03/30/2017
api_name:
- PublicKeyBlob
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- PublicKeyBlob
helpviewer_keywords:
- PublicKeyBlob structure [.NET Framework strong naming]
ms.assetid: b9240712-829c-4c8d-9a09-a6e7aa63f63a
topic_type:
- apiref
ms.openlocfilehash: 42cd3cc22fbbb8eb3d5ac44544fce36650b6461f
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705931"
---
# <a name="publickeyblob-structure"></a><span data-ttu-id="58cda-102">PublicKeyBlob 構造体</span><span class="sxs-lookup"><span data-stu-id="58cda-102">PublicKeyBlob Structure</span></span>

<span data-ttu-id="58cda-103">公開キーと秘密キーのペアの公開キーをバイナリ形式で表します。</span><span class="sxs-lookup"><span data-stu-id="58cda-103">Represents, in binary format, the public key of a public/private key pair.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58cda-104">構文</span><span class="sxs-lookup"><span data-stu-id="58cda-104">Syntax</span></span>  
  
```cpp  
typedef struct {  
    unsigned int SigAlgId;  
    unsigned int HashAlgId;  
    ULONG cbPublicKey;  
    BYTE PublicKey[1]  
} PublicKeyBlob;
```  
  
## <a name="members"></a><span data-ttu-id="58cda-105">メンバー</span><span class="sxs-lookup"><span data-stu-id="58cda-105">Members</span></span>  
  
|<span data-ttu-id="58cda-106">メンバー</span><span class="sxs-lookup"><span data-stu-id="58cda-106">Member</span></span>|<span data-ttu-id="58cda-107">説明</span><span class="sxs-lookup"><span data-stu-id="58cda-107">Description</span></span>|  
|------------|-----------------|  
|`SigAlgId`|<span data-ttu-id="58cda-108">`ALG_ID`公開キーの署名アルゴリズム (WinCrypt .h で定義されている型の) の識別子。</span><span class="sxs-lookup"><span data-stu-id="58cda-108">The identifier for the signature algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`HashAlgId`|<span data-ttu-id="58cda-109">`ALG_ID`公開キーのハッシュアルゴリズム (WinCrypt .h で定義されている型の) の識別子。</span><span class="sxs-lookup"><span data-stu-id="58cda-109">The identifier for the hash algorithm (of type `ALG_ID`, as defined in WinCrypt.h) of the public key.</span></span>|  
|`cbPublicKey`|<span data-ttu-id="58cda-110">キーの長さ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="58cda-110">The length of the key in bytes.</span></span>|  
|`PublicKey`|<span data-ttu-id="58cda-111">CryptoAPI によって返される形式のキー値を格納する可変長バイト配列。</span><span class="sxs-lookup"><span data-stu-id="58cda-111">A variable-length byte array that contains the key value in the format returned by the CryptoAPI.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58cda-112">注釈</span><span class="sxs-lookup"><span data-stu-id="58cda-112">Remarks</span></span>  

 <span data-ttu-id="58cda-113">`PublicKeyBlob`構造体は、公開キーと秘密キーのペアの公開キーを表すために、 [StrongNameGetPublicKey](strongnamegetpublickey-function.md)、 [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md)、およびその他の厳密な名前関数によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="58cda-113">The `PublicKeyBlob` structure is used by [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md), and other strong name functions to represent the public key of a public/private key pair.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58cda-114">要件</span><span class="sxs-lookup"><span data-stu-id="58cda-114">Requirements</span></span>  

 <span data-ttu-id="58cda-115">**:**「[システム要件](../../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="58cda-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58cda-116">**ヘッダー:** StrongName</span><span class="sxs-lookup"><span data-stu-id="58cda-116">**Header:** StrongName.h</span></span>  
  
 <span data-ttu-id="58cda-117">**ライブラリ:** MsCorEE.dll にリソースとして含まれています</span><span class="sxs-lookup"><span data-stu-id="58cda-117">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="58cda-118">**.NET Framework のバージョン:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="58cda-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58cda-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="58cda-119">See also</span></span>

- [<span data-ttu-id="58cda-120">StrongNameGetPublicKey 関数</span><span class="sxs-lookup"><span data-stu-id="58cda-120">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)
- [<span data-ttu-id="58cda-121">StrongNameSignatureGeneration 関数</span><span class="sxs-lookup"><span data-stu-id="58cda-121">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)
