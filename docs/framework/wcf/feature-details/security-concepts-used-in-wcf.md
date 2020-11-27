---
title: WCF で使用されるセキュリティの概要
ms.date: 03/30/2017
ms.assetid: 3b9dfcf5-4bf1-4f35-9070-723171c823a1
ms.openlocfilehash: 2c7bc01ba45c02be4a1d40c2600fde62e94afe32
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251387"
---
# <a name="security-concepts-used-in-wcf"></a><span data-ttu-id="c5aba-102">WCF で使用されるセキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="c5aba-102">Security Concepts Used in WCF</span></span>

<span data-ttu-id="c5aba-103">Windows Communication Foundation (WCF) セキュリティは、さまざまなセキュリティインフラストラクチャで既に使用および展開されている概念に基づいて構築されています。</span><span class="sxs-lookup"><span data-stu-id="c5aba-103">Windows Communication Foundation (WCF) security is built upon concepts already in use and deployed in various security infrastructures.</span></span>  
  
 <span data-ttu-id="c5aba-104">WCF は、Secure Sockets Layer (SSL) over HTTP (HTTPS) などの一部のインフラストラクチャをサポートします。</span><span class="sxs-lookup"><span data-stu-id="c5aba-104">WCF supports some of those infrastructures, such as Secure Sockets Layer (SSL) over HTTP (HTTPS).</span></span> <span data-ttu-id="c5aba-105">ただし、WCF は、SOAP でエンコードされたメッセージに対して、より新しい相互運用可能なセキュリティ標準 (WS-SECURITY など) を実装することで、既存のセキュリティインフラストラクチャをサポートすることを超えています。</span><span class="sxs-lookup"><span data-stu-id="c5aba-105">However, WCF goes beyond supporting existing security infrastructures by implementing newer interoperable security standards (such as WS-Security) over SOAP-encoded messages.</span></span> <span data-ttu-id="c5aba-106">既存の機構と新規の相互運用可能な標準のどちらを使用する場合でも、背後にあるセキュリティ概念に変わりはありません。</span><span class="sxs-lookup"><span data-stu-id="c5aba-106">Whether you are using existing mechanisms or new interoperable standards, the security concepts behind both are the same.</span></span> <span data-ttu-id="c5aba-107">既存のインフラストラクチャおよび新しい標準を支える概念を理解することが、アプリケーションにとって最善のセキュリティ モデルを実装するための要になります。</span><span class="sxs-lookup"><span data-stu-id="c5aba-107">Understanding the concepts behind existing infrastructures and the newer standards is central to implementing the best security model for an application.</span></span>  
  
## <a name="introduction-to-security-for-wcf-web-services"></a><span data-ttu-id="c5aba-108">WCF Web サービスのセキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="c5aba-108">Introduction to Security for WCF Web Services</span></span>  

<span data-ttu-id="c5aba-109">Microsoft のパターンとプラクティスグループでは、 [WCF セキュリティガイド](https://archive.codeplex.com/?p=wcfsecurityguide)と呼ばれる詳細なホワイトペーパーを作成しました。</span><span class="sxs-lookup"><span data-stu-id="c5aba-109">The Microsoft Patterns and Practices group wrote an in-depth white paper called [WCF Security Guide](https://archive.codeplex.com/?p=wcfsecurityguide).</span></span> <span data-ttu-id="c5aba-110">このホワイトペーパーでは、web サービス、主要な WCF セキュリティの概念、イントラネットアプリケーションのシナリオ、およびインターネットアプリケーションのシナリオに関連する基本的なセキュリティの概念について説明します。</span><span class="sxs-lookup"><span data-stu-id="c5aba-110">This white paper describes the fundamental security concepts as they relate to web services, key WCF security concepts, intranet application scenarios, and internet application scenarios.</span></span>  
  
## <a name="industry-wide-security-specifications"></a><span data-ttu-id="c5aba-111">業界標準のセキュリティ仕様</span><span class="sxs-lookup"><span data-stu-id="c5aba-111">Industry-Wide Security Specifications</span></span>  
  
### <a name="public-key-infrastructure"></a><span data-ttu-id="c5aba-112">公開キー基盤</span><span class="sxs-lookup"><span data-stu-id="c5aba-112">Public Key Infrastructure</span></span>  

<span data-ttu-id="c5aba-113">公開キー基盤 (PKI) は、デジタル証明書、証明機関、およびその他の登録機関のシステムであり、公開キー暗号化を使用して、電子取引に関連する各パーティを検証および認証します。</span><span class="sxs-lookup"><span data-stu-id="c5aba-113">Public Key Infrastructure (PKI) is a system of digital certificates, certification authorities, and other registration authorities that verify and authenticate each party involved in an electronic transaction through the use of public-key cryptography.</span></span>
  
### <a name="kerberos-protocol"></a><span data-ttu-id="c5aba-114">Kerberos プロトコル</span><span class="sxs-lookup"><span data-stu-id="c5aba-114">Kerberos Protocol</span></span>  

 <span data-ttu-id="c5aba-115">*Kerberos プロトコル* は、Windows ドメインでユーザーを認証するセキュリティメカニズムを作成するための仕様です。</span><span class="sxs-lookup"><span data-stu-id="c5aba-115">The *Kerberos protocol* is a specification for creating a security mechanism that authenticates users on a Windows domain.</span></span> <span data-ttu-id="c5aba-116">ユーザーはドメイン内の他のエンティティと、セキュリティで保護されたコンテキストを確立できます。</span><span class="sxs-lookup"><span data-stu-id="c5aba-116">It allows a user to establish a secure context with other entities within a domain.</span></span> <span data-ttu-id="c5aba-117">Windows 2000 以降のプラットフォームでは、Kerberos プロトコルが既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="c5aba-117">Windows 2000 and later platforms use the Kerberos protocol by default.</span></span> <span data-ttu-id="c5aba-118">システムの機構を理解することは、イントラネット クライアントと対話するサービスを作成する場合に役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c5aba-118">Understanding the mechanisms of the system is useful when creating a service that will interact with intranet clients.</span></span> <span data-ttu-id="c5aba-119">さらに、 *Web Services Security Kerberos バインド* が広く公開されているため、kerberos プロトコルを使用してインターネットクライアントと通信できます (つまり、kerberos プロトコルは相互運用可能です)。</span><span class="sxs-lookup"><span data-stu-id="c5aba-119">In addition, since the *Web Services Security Kerberos Binding* is widely published, you can use the Kerberos protocol to communicate with Internet clients (that is, the Kerberos protocol is interoperable).</span></span> <span data-ttu-id="c5aba-120">Windows で Kerberos プロトコルを実装する方法の詳細については、「  [Microsoft kerberos](/windows/win32/secauthn/microsoft-kerberos)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5aba-120">For more information about how the Kerberos protocol is implemented in Windows, see  [Microsoft Kerberos](/windows/win32/secauthn/microsoft-kerberos).</span></span>  
  
### <a name="x509-certificates"></a><span data-ttu-id="c5aba-121">X.509 証明書</span><span class="sxs-lookup"><span data-stu-id="c5aba-121">X.509 Certificates</span></span>  

 <span data-ttu-id="c5aba-122">X.509 証明書は、セキュリティ アプリケーションで使用される主要な資格情報の形式です。</span><span class="sxs-lookup"><span data-stu-id="c5aba-122">X.509 certificates are a primary credential form used in security applications.</span></span> <span data-ttu-id="c5aba-123">X.509 証明書の詳細については、「 [X.509 公開キー証明書](/windows/win32/seccertenroll/about-x-509-public-key-certificates)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5aba-123">For more information on X.509 certificates see [X.509 Public Key Certificates](/windows/win32/seccertenroll/about-x-509-public-key-certificates).</span></span> <span data-ttu-id="c5aba-124">X.509 証明書は証明書ストア内に格納されます。</span><span class="sxs-lookup"><span data-stu-id="c5aba-124">X.509 certificates are stored within a certificate store.</span></span> <span data-ttu-id="c5aba-125">Windows を実行しているコンピューターには、それぞれ目的が異なる数種類の証明書ストアがあります。</span><span class="sxs-lookup"><span data-stu-id="c5aba-125">A computer running Windows has several kinds of certificate stores, each with a different purpose.</span></span> <span data-ttu-id="c5aba-126">さまざまなストアの詳細については、「 [証明書ストア](/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5aba-126">For more information about the different stores, see [Certificate Stores](/previous-versions/windows/it-pro/windows-server-2003/cc757138(v=ws.10)).</span></span>  
  
## <a name="web-services-security-specifications"></a><span data-ttu-id="c5aba-127">Web サービスのセキュリティ仕様</span><span class="sxs-lookup"><span data-stu-id="c5aba-127">Web Services Security Specifications</span></span>  

 <span data-ttu-id="c5aba-128">システム定義のバインディングでは、一般に使用されるさまざまな Web サービスのセキュリティ仕様をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c5aba-128">The system-defined bindings support many commonly used web services security specifications.</span></span> <span data-ttu-id="c5aba-129">システム指定のバインディングとそれらがサポートする web サービスの仕様の完全な一覧については、「 [System-Provided 相互運用性バインドでサポートされる Web サービスプロトコル](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5aba-129">For a complete list of system-provided bindings and the web services specifications they support see: [Web Services Protocols Supported by System-Provided Interoperability Bindings](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)</span></span>  
  
## <a name="access-control-mechanisms"></a><span data-ttu-id="c5aba-130">アクセス制御機構</span><span class="sxs-lookup"><span data-stu-id="c5aba-130">Access Control Mechanisms</span></span>  

 <span data-ttu-id="c5aba-131">WCF には、サービスや操作へのアクセスを制御するさまざまな方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="c5aba-131">WCF provides a number of ways to control access to a service or operation.</span></span> <span data-ttu-id="c5aba-132">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="c5aba-132">Among them are</span></span>  
  
1. <xref:System.Security.Permissions.PrincipalPermissionAttribute>  
  
2. <span data-ttu-id="c5aba-133">ASP.NET メンバーシップ プロバイダー</span><span class="sxs-lookup"><span data-stu-id="c5aba-133">ASP.NET Membership Provider</span></span>  
  
3. <span data-ttu-id="c5aba-134">ASP.NET ロール プロバイダー</span><span class="sxs-lookup"><span data-stu-id="c5aba-134">ASP.NET Role Provider</span></span>  
  
4. <span data-ttu-id="c5aba-135">承認マネージャー</span><span class="sxs-lookup"><span data-stu-id="c5aba-135">Authorization Manager</span></span>  
  
5. <span data-ttu-id="c5aba-136">ID モデル</span><span class="sxs-lookup"><span data-stu-id="c5aba-136">Identity Model</span></span>  
  
 <span data-ttu-id="c5aba-137">これらのトピックの詳細については、「」、「 [Access Control メカニズム](access-control-mechanisms.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c5aba-137">For more information on these topics see, [Access Control Mechanisms](access-control-mechanisms.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5aba-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="c5aba-138">See also</span></span>

- [<span data-ttu-id="c5aba-139">セキュリティの概要</span><span class="sxs-lookup"><span data-stu-id="c5aba-139">Security Overview</span></span>](security-overview.md)
- <span data-ttu-id="c5aba-140">[Windows Server AppFabric のセキュリティ モデル](/previous-versions/appfabric/ee677202(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="c5aba-140">[Security Model for Windows Server App Fabric](/previous-versions/appfabric/ee677202(v=azure.10))</span></span>
