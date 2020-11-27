---
title: セキュリティ検証と認証エラー
ms.date: 03/30/2017
ms.assetid: 0d4e3666-dfc6-421c-baf8-9479c22f7050
ms.openlocfilehash: 3bcc6111f322a3bd8169567e8f436871eb19f879
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253051"
---
# <a name="security-validation-and-authentication-failures"></a><span data-ttu-id="c146e-102">セキュリティ検証と認証エラー</span><span class="sxs-lookup"><span data-stu-id="c146e-102">Security Validation and Authentication Failures</span></span>

<span data-ttu-id="c146e-103">カウンター名 : セキュリティ検証と認証エラー</span><span class="sxs-lookup"><span data-stu-id="c146e-103">Counter name: Security Validation and Authentication Failures</span></span>  
  
## <a name="description"></a><span data-ttu-id="c146e-104">Description</span><span class="sxs-lookup"><span data-stu-id="c146e-104">Description</span></span>  

 <span data-ttu-id="c146e-105">このカウンターは、"承認されていないセキュリティ呼び出し" カウンターでカウントの対象とならないセキュリティ上の問題が原因でメッセージが拒否されるたびにインクリメントされます。</span><span class="sxs-lookup"><span data-stu-id="c146e-105">This counter is incremented whenever a message is rejected due to a security problem not covered by the "Security Calls Not Authorized" counter.</span></span> <span data-ttu-id="c146e-106">この問題には、次のようなものがあります。</span><span class="sxs-lookup"><span data-stu-id="c146e-106">Such problems include:</span></span>  
  
- <span data-ttu-id="c146e-107">メッセージからクライアント トークンを読み取ることができない。</span><span class="sxs-lookup"><span data-stu-id="c146e-107">Client token cannot be read from the message.</span></span>  
  
- <span data-ttu-id="c146e-108">クライアント トークンが認証に失敗した (例 : 無効なパスワード)。</span><span class="sxs-lookup"><span data-stu-id="c146e-108">Client token has failed authentication (for example, bad password).</span></span>  
  
- <span data-ttu-id="c146e-109">署名の検証に失敗した (例 : メッセージが改ざんされた)。</span><span class="sxs-lookup"><span data-stu-id="c146e-109">Signature verification has failed (for example, the message has been tampered).</span></span>  
  
- <span data-ttu-id="c146e-110">メッセージが以前のメッセージと重複する。この現象はリプレイ攻撃中に発生することがあります。</span><span class="sxs-lookup"><span data-stu-id="c146e-110">The message is a duplicate from a previous one, which can happen during a replay attack.</span></span>  
  
- <span data-ttu-id="c146e-111">復号化に失敗した。</span><span class="sxs-lookup"><span data-stu-id="c146e-111">A decryption failure has occurred.</span></span>  
  
- <span data-ttu-id="c146e-112">一部の必須要素 (タイムスタンプ、暗号化データ ブロックなど) がメッセージにない。</span><span class="sxs-lookup"><span data-stu-id="c146e-112">Some required elements (for example, missing timestamp or encrypted data block) are missing from the message.</span></span>  
  
- <span data-ttu-id="c146e-113">TLSNEGO/SPNEGO ハンドシェイク中にエラーが発生した。</span><span class="sxs-lookup"><span data-stu-id="c146e-113">Errors have occurred during TLSNEGO/SPNEGO handshake.</span></span>
