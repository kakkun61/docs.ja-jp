---
title: フェデレーションと発行済みトークン
ms.date: 03/30/2017
helpviewer_keywords:
- WCF, federation
- issued tokens [WCF]
- federation [WCF], issued tokens
ms.assetid: 4c31ee7d-a820-4067-8b84-a83049021bb6
ms.openlocfilehash: 0ab3d6bad717e71901b4d94c99f1c48f99d8675e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255521"
---
# <a name="federation-and-issued-tokens"></a><span data-ttu-id="3c411-102">フェデレーションと発行済みトークン</span><span class="sxs-lookup"><span data-stu-id="3c411-102">Federation and Issued Tokens</span></span>

<span data-ttu-id="3c411-103">Windows Communication Foundation (WCF) を使用すると、WS-Federation と WS-Trust の仕様を実装するサービスと安全に通信するクライアントを作成できます。</span><span class="sxs-lookup"><span data-stu-id="3c411-103">With Windows Communication Foundation (WCF), you can create clients that communicate securely with services that implement the WS-Federation and WS-Trust specifications.</span></span> <span data-ttu-id="3c411-104">これらの仕様では、異なる信頼領域間での認証と承認を可能にする機構を提供するために、XML、SOAP、および Web サービス記述言語 (WSDL: Web Services Description Language) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="3c411-104">The specifications use XML, SOAP, and Web Services Description Language (WSDL) to provide mechanisms that enable authentication and authorization across different trust realms.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3c411-105">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="3c411-105">In This Section</span></span>  

 [<span data-ttu-id="3c411-106">フェデレーション</span><span class="sxs-lookup"><span data-stu-id="3c411-106">Federation</span></span>](federation.md)  
 <span data-ttu-id="3c411-107">フェデレーションの概要を説明します。</span><span class="sxs-lookup"><span data-stu-id="3c411-107">Provides an overview of federation.</span></span>  
  
 [<span data-ttu-id="3c411-108">フェデレーションと信頼</span><span class="sxs-lookup"><span data-stu-id="3c411-108">Federation and Trust</span></span>](federation-and-trust.md)  
 <span data-ttu-id="3c411-109">フェデレーション サービスまたはクライアントを作成するときに注意する必要がある設計上の問題を示します。</span><span class="sxs-lookup"><span data-stu-id="3c411-109">Lists the design issues to be aware of when creating federated services or clients.</span></span>  
  
 [<span data-ttu-id="3c411-110">方法: フェデレーション クライアントを作成する</span><span class="sxs-lookup"><span data-stu-id="3c411-110">How to: Create a Federated Client</span></span>](how-to-create-a-federated-client.md)  
 <span data-ttu-id="3c411-111">WCF を使用したフェデレーションクライアントの作成の基本について説明します。</span><span class="sxs-lookup"><span data-stu-id="3c411-111">Describes the basics of creating a federated client with WCF.</span></span>  
  
 [<span data-ttu-id="3c411-112">方法: フェデレーション サービスで資格情報を設定する</span><span class="sxs-lookup"><span data-stu-id="3c411-112">How to: Configure Credentials on a Federation Service</span></span>](how-to-configure-credentials-on-a-federation-service.md)  
 <span data-ttu-id="3c411-113">フェデレーション サービスを作成する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="3c411-113">Describes the steps of creating a federated service.</span></span>  
  
 [<span data-ttu-id="3c411-114">方法: WSFederationHttpBinding を作成する</span><span class="sxs-lookup"><span data-stu-id="3c411-114">How to: Create a WSFederationHttpBinding</span></span>](how-to-create-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="3c411-115">`WSFederationHttpBinding` を使用するクライアントおよびサービスを構成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="3c411-115">Describes how to configure clients and services that use the `WSFederationHttpBinding`.</span></span>  
  
 [<span data-ttu-id="3c411-116">方法: セキュリティ トークン サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="3c411-116">How to: Create a Security Token Service</span></span>](how-to-create-a-security-token-service.md)  
 <span data-ttu-id="3c411-117">セキュリティ トークン サービスを作成する手順を説明します。</span><span class="sxs-lookup"><span data-stu-id="3c411-117">Describes the steps of creating a security token service.</span></span>  
  
 [<span data-ttu-id="3c411-118">SAML (Security Assertions Markup Language) トークンとクレーム</span><span class="sxs-lookup"><span data-stu-id="3c411-118">Security Assertions Markup Language (SAML) Tokens and Claims</span></span>](saml-tokens-and-claims.md)  
 <span data-ttu-id="3c411-119">多様なクレームの種類を作成できる拡張可能な SAML (Security Assertions Markup Language) トークンについて説明します。</span><span class="sxs-lookup"><span data-stu-id="3c411-119">Describes Security Assertions Markup Language (SAML) tokens, which are extensible and enable you to create rich claim types.</span></span>  
  
 [<span data-ttu-id="3c411-120">方法: ローカル発行者を設定する</span><span class="sxs-lookup"><span data-stu-id="3c411-120">How to: Configure a Local Issuer</span></span>](how-to-configure-a-local-issuer.md)  
 <span data-ttu-id="3c411-121">セキュリティ トークンのローカル発行者の作成方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="3c411-121">Describes how to create a local issuer of security tokens.</span></span>  
  
 [<span data-ttu-id="3c411-122">方法: WSFederationHttpBinding のセキュリティで保護されたセッションを無効にする</span><span class="sxs-lookup"><span data-stu-id="3c411-122">How to: Disable Secure Sessions on a WSFederationHttpBinding</span></span>](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)  
 <span data-ttu-id="3c411-123">`WSFederationHttpBinding` のセキュリティで保護されたセッションを無効にする方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="3c411-123">Describes how to disable secure sessions on a `WSFederationHttpBinding`.</span></span> <span data-ttu-id="3c411-124">クライアントごとにセッションが必要になる Web ファームを作成する場合には、セキュリティで保護されたセッションを無効化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="3c411-124">Disabling secure sessions is necessary when creating a Web farm that requires a session for each client.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3c411-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c411-125">Reference</span></span>  

 <xref:System.IdentityModel.Claims>  
  
 <xref:System.ServiceModel.ServiceAuthorizationManager>  
  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenProvider>  
  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
  
## <a name="see-also"></a><span data-ttu-id="3c411-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c411-126">See also</span></span>

- [<span data-ttu-id="3c411-127">承認</span><span class="sxs-lookup"><span data-stu-id="3c411-127">Authorization</span></span>](authorization-in-wcf.md)
- [<span data-ttu-id="3c411-128">カスタム トークン</span><span class="sxs-lookup"><span data-stu-id="3c411-128">Custom Tokens</span></span>](../extending/custom-tokens.md)
- <span data-ttu-id="3c411-129">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="3c411-129">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
