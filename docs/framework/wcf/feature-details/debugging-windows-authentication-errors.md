---
title: Windows 認証エラーのデバッグ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, authentication
- WCF, Windows authentication
ms.assetid: 181be4bd-79b1-4a66-aee2-931887a6d7cc
ms.openlocfilehash: c8aa87bdbf9488bce8e1a62f6d1a3898f923d349
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96291662"
---
# <a name="debug-windows-authentication-errors"></a><span data-ttu-id="1493d-102">Windows 認証エラーのデバッグ</span><span class="sxs-lookup"><span data-stu-id="1493d-102">Debug Windows authentication errors</span></span>

<span data-ttu-id="1493d-103">セキュリティ機構として Windows 認証を使用する場合、セキュリティ サポート プロバイダー インターフェイス (SSPI: Security Support Provider Interface) がセキュリティ プロセスを処理します。</span><span class="sxs-lookup"><span data-stu-id="1493d-103">When using Windows authentication as a security mechanism, the Security Support Provider Interface (SSPI) handles security processes.</span></span> <span data-ttu-id="1493d-104">SSPI 層でセキュリティエラーが発生すると、Windows Communication Foundation (WCF) によって表示されます。</span><span class="sxs-lookup"><span data-stu-id="1493d-104">When security errors occur at the SSPI layer, they are surfaced by Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="1493d-105">このトピックでは、エラーの診断に役立つフレームワークと一連の質問を示します。</span><span class="sxs-lookup"><span data-stu-id="1493d-105">This topic provides a framework and set of questions to help diagnose the errors.</span></span>  
  
 <span data-ttu-id="1493d-106">Kerberos プロトコルの概要については、 [kerberos の説明](/previous-versions/windows/it-pro/windows-2000-server/bb742516(v=technet.10))を参照してください。SSPI の概要については、「 [sspi](/windows/win32/secauthn/sspi)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1493d-106">For an overview of the Kerberos protocol, see [Kerberos Explained](/previous-versions/windows/it-pro/windows-2000-server/bb742516(v=technet.10)); for an overview of SSPI, see [SSPI](/windows/win32/secauthn/sspi).</span></span>  
  
 <span data-ttu-id="1493d-107">Windows 認証の場合、WCF は通常、クライアントとサービスの間で Kerberos 相互認証を実行する *ネゴシエート* セキュリティサポートプロバイダー (SSP) を使用します。</span><span class="sxs-lookup"><span data-stu-id="1493d-107">For Windows authentication, WCF typically uses the *Negotiate* Security Support Provider (SSP), which performs Kerberos mutual authentication between the client and service.</span></span> <span data-ttu-id="1493d-108">Kerberos プロトコルが使用できない場合、既定では、WCF は NT LAN Manager (NTLM) にフォールバックします。</span><span class="sxs-lookup"><span data-stu-id="1493d-108">If the Kerberos protocol is not available, by default WCF falls back to NT LAN Manager (NTLM).</span></span> <span data-ttu-id="1493d-109">ただし、Kerberos プロトコルのみを使用するように WCF を構成することができます (および Kerberos が使用できない場合は例外をスローします)。</span><span class="sxs-lookup"><span data-stu-id="1493d-109">However, you can configure WCF to use only the Kerberos protocol (and to throw an exception if Kerberos is not available).</span></span> <span data-ttu-id="1493d-110">Kerberos プロトコルの制限付き形式を使用するように WCF を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="1493d-110">You can also configure WCF to use restricted forms of the Kerberos protocol.</span></span>  
  
## <a name="debugging-methodology"></a><span data-ttu-id="1493d-111">デバッグ方法</span><span class="sxs-lookup"><span data-stu-id="1493d-111">Debugging Methodology</span></span>  

 <span data-ttu-id="1493d-112">基本的な方法は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="1493d-112">The basic method is as follows:</span></span>  
  
1. <span data-ttu-id="1493d-113">Windows 認証を使用しているかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="1493d-113">Determine whether you are using Windows authentication.</span></span> <span data-ttu-id="1493d-114">他の方式を使用している場合には、このトピックは該当しません。</span><span class="sxs-lookup"><span data-stu-id="1493d-114">If you are using any other scheme, this topic does not apply.</span></span>  
  
2. <span data-ttu-id="1493d-115">Windows 認証を使用していることがわかっている場合は、WCF 構成で Kerberos 直接またはネゴシエートのどちらを使用するかを決定します。</span><span class="sxs-lookup"><span data-stu-id="1493d-115">If you are sure you are using Windows authentication, determine whether your WCF configuration uses Kerberos direct or Negotiate.</span></span>  
  
3. <span data-ttu-id="1493d-116">構成で Kerberos プロトコルと NTLM のどちらを使用しているかを確認した後は、現在のコンテキストでのエラー メッセージを理解できます。</span><span class="sxs-lookup"><span data-stu-id="1493d-116">Once you have determined whether your configuration is using the Kerberos protocol or NTLM, you can understand error messages in the correct context.</span></span>  
  
### <a name="availability-of-the-kerberos-protocol-and-ntlm"></a><span data-ttu-id="1493d-117">Kerberos プロトコルと NTLM の可用性</span><span class="sxs-lookup"><span data-stu-id="1493d-117">Availability of the Kerberos Protocol and NTLM</span></span>  

 <span data-ttu-id="1493d-118">Kerberos SSP は、Kerberos キー配布センター (KDC: Key Distribution Center) として機能するドメイン コントローラーを必要とします。</span><span class="sxs-lookup"><span data-stu-id="1493d-118">The Kerberos SSP requires a domain controller to act as the Kerberos Key Distribution Center (KDC).</span></span> <span data-ttu-id="1493d-119">Kerberos プロトコルを使用できるのは、クライアントとサービスの両方がドメイン ID を使用している場合だけです。</span><span class="sxs-lookup"><span data-stu-id="1493d-119">The Kerberos protocol is available only when both the client and service are using domain identities.</span></span> <span data-ttu-id="1493d-120">次の表に示すように、アカウントの他の組み合わせでは NTLM が使用されます。</span><span class="sxs-lookup"><span data-stu-id="1493d-120">In other account combinations, NTLM is used, as summarized in the following table.</span></span>  
  
 <span data-ttu-id="1493d-121">この表の列見出しは、サーバーが使用すると考えられるアカウントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="1493d-121">The table headers show possible account types used by the server.</span></span> <span data-ttu-id="1493d-122">左の列は、クライアントが使用すると考えられるアカウントの種類を示します。</span><span class="sxs-lookup"><span data-stu-id="1493d-122">The left column shows possible account types used by the client.</span></span>  
  
||<span data-ttu-id="1493d-123">Local User</span><span class="sxs-lookup"><span data-stu-id="1493d-123">Local User</span></span>|<span data-ttu-id="1493d-124">[ローカル システム]</span><span class="sxs-lookup"><span data-stu-id="1493d-124">Local System</span></span>|<span data-ttu-id="1493d-125">Domain User</span><span class="sxs-lookup"><span data-stu-id="1493d-125">Domain User</span></span>|<span data-ttu-id="1493d-126">Domain Machine</span><span class="sxs-lookup"><span data-stu-id="1493d-126">Domain Machine</span></span>|  
|-|----------------|------------------|-----------------|--------------------|  
|<span data-ttu-id="1493d-127">Local User</span><span class="sxs-lookup"><span data-stu-id="1493d-127">Local User</span></span>|<span data-ttu-id="1493d-128">NTLM</span><span class="sxs-lookup"><span data-stu-id="1493d-128">NTLM</span></span>|<span data-ttu-id="1493d-129">NTLM</span><span class="sxs-lookup"><span data-stu-id="1493d-129">NTLM</span></span>|<span data-ttu-id="1493d-130">NTLM</span><span class="sxs-lookup"><span data-stu-id="1493d-130">NTLM</span></span>|<span data-ttu-id="1493d-131">NTLM</span><span class="sxs-lookup"><span data-stu-id="1493d-131">NTLM</span></span>|  
|<span data-ttu-id="1493d-132">[ローカル システム]</span><span class="sxs-lookup"><span data-stu-id="1493d-132">Local System</span></span>|<span data-ttu-id="1493d-133">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="1493d-133">Anonymous NTLM</span></span>|<span data-ttu-id="1493d-134">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="1493d-134">Anonymous NTLM</span></span>|<span data-ttu-id="1493d-135">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="1493d-135">Anonymous NTLM</span></span>|<span data-ttu-id="1493d-136">匿名 NTLM</span><span class="sxs-lookup"><span data-stu-id="1493d-136">Anonymous NTLM</span></span>|  
|<span data-ttu-id="1493d-137">Domain User</span><span class="sxs-lookup"><span data-stu-id="1493d-137">Domain User</span></span>|<span data-ttu-id="1493d-138">NTLM</span><span class="sxs-lookup"><span data-stu-id="1493d-138">NTLM</span></span>|<span data-ttu-id="1493d-139">NTLM</span><span class="sxs-lookup"><span data-stu-id="1493d-139">NTLM</span></span>|<span data-ttu-id="1493d-140">Kerberos</span><span class="sxs-lookup"><span data-stu-id="1493d-140">Kerberos</span></span>|<span data-ttu-id="1493d-141">Kerberos</span><span class="sxs-lookup"><span data-stu-id="1493d-141">Kerberos</span></span>|  
|<span data-ttu-id="1493d-142">Domain Machine</span><span class="sxs-lookup"><span data-stu-id="1493d-142">Domain Machine</span></span>|<span data-ttu-id="1493d-143">NTLM</span><span class="sxs-lookup"><span data-stu-id="1493d-143">NTLM</span></span>|<span data-ttu-id="1493d-144">NTLM</span><span class="sxs-lookup"><span data-stu-id="1493d-144">NTLM</span></span>|<span data-ttu-id="1493d-145">Kerberos</span><span class="sxs-lookup"><span data-stu-id="1493d-145">Kerberos</span></span>|<span data-ttu-id="1493d-146">Kerberos</span><span class="sxs-lookup"><span data-stu-id="1493d-146">Kerberos</span></span>|  
  
 <span data-ttu-id="1493d-147">具体的には、次の 4 種類のアカウントがあります。</span><span class="sxs-lookup"><span data-stu-id="1493d-147">Specifically, the four account types include:</span></span>  
  
- <span data-ttu-id="1493d-148">Local User : コンピューター専用のユーザー プロファイル。</span><span class="sxs-lookup"><span data-stu-id="1493d-148">Local User: Machine-only user profile.</span></span> <span data-ttu-id="1493d-149">たとえば、`MachineName\Administrator` や `MachineName\ProfileName` などです。</span><span class="sxs-lookup"><span data-stu-id="1493d-149">For example: `MachineName\Administrator` or `MachineName\ProfileName`.</span></span>  
  
- <span data-ttu-id="1493d-150">Local System : ドメインに参加していないコンピューターの SYSTEM ビルトイン アカウント。</span><span class="sxs-lookup"><span data-stu-id="1493d-150">Local System: The built-in account SYSTEM on a machine that is not joined to a domain.</span></span>  
  
- <span data-ttu-id="1493d-151">Domain User : Windows ドメインのユーザー アカウント。</span><span class="sxs-lookup"><span data-stu-id="1493d-151">Domain User: A user account on a Windows domain.</span></span> <span data-ttu-id="1493d-152">例: `DomainName\ProfileName`。</span><span class="sxs-lookup"><span data-stu-id="1493d-152">For example: `DomainName\ProfileName`.</span></span>  
  
- <span data-ttu-id="1493d-153">Domain Machine : Windows ドメインに参加しているコンピューターで実行されている、コンピューター ID を使用するプロセス。</span><span class="sxs-lookup"><span data-stu-id="1493d-153">Domain Machine: A process with machine identity running on a machine joined to a Windows domain.</span></span> <span data-ttu-id="1493d-154">例: `MachineName\Network Service`。</span><span class="sxs-lookup"><span data-stu-id="1493d-154">For example: `MachineName\Network Service`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1493d-155">サービス資格情報は、<xref:System.ServiceModel.ICommunicationObject.Open%2A> クラスの <xref:System.ServiceModel.ServiceHost> メソッドが呼び出されたときにキャプチャされます。</span><span class="sxs-lookup"><span data-stu-id="1493d-155">The service credential is captured when the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method of the <xref:System.ServiceModel.ServiceHost> class is called.</span></span> <span data-ttu-id="1493d-156">クライアント資格情報は、クライアントがメッセージを送信するたびに読み取られます。</span><span class="sxs-lookup"><span data-stu-id="1493d-156">The client credential is read whenever the client sends a message.</span></span>  
  
## <a name="common-windows-authentication-problems"></a><span data-ttu-id="1493d-157">Windows 認証の一般的な問題</span><span class="sxs-lookup"><span data-stu-id="1493d-157">Common Windows Authentication Problems</span></span>  

 <span data-ttu-id="1493d-158">ここでは、Windows 認証に関するいくつかの一般的な問題と、考えられる解決策について説明します。</span><span class="sxs-lookup"><span data-stu-id="1493d-158">This section discusses some common Windows authentication problems and possible remedies.</span></span>  
  
### <a name="kerberos-protocol"></a><span data-ttu-id="1493d-159">Kerberos プロトコル</span><span class="sxs-lookup"><span data-stu-id="1493d-159">Kerberos Protocol</span></span>  
  
#### <a name="spnupn-problems-with-the-kerberos-protocol"></a><span data-ttu-id="1493d-160">Kerberos プロトコルでの SPN と UPN の問題</span><span class="sxs-lookup"><span data-stu-id="1493d-160">SPN/UPN Problems with the Kerberos Protocol</span></span>  

 <span data-ttu-id="1493d-161">Windows 認証を使用し、SSPI が Kerberos プロトコルを使用またはネゴシエートする場合、クライアント エンドポイントが使用する URL には、サービス URL 内のサービスのホストの完全修飾ドメイン名が含まれている必要があります。</span><span class="sxs-lookup"><span data-stu-id="1493d-161">When using Windows authentication, and the Kerberos protocol is used or negotiated by SSPI, the URL the client endpoint uses must include the fully qualified domain name of the service's host inside the service URL.</span></span> <span data-ttu-id="1493d-162">これは、サービスを実行しているアカウントがコンピューターの (既定の) サービス プリンシパル名 (SPN: Service Principal Name) キーにアクセスできることを前提としています。このキーは、コンピューターを Active Directory ドメインに追加したときに作成されます。コンピューターの SPN キーにアクセスできるようにするには、Network Service アカウントでサービスを実行するのが最も一般的な方法です。</span><span class="sxs-lookup"><span data-stu-id="1493d-162">This assumes that the account under which the service is running has access to the machine (default) service principal name (SPN) key that is created when the computer is added to the Active Directory domain, which is most commonly done by running the service under the Network Service account.</span></span> <span data-ttu-id="1493d-163">サービスがコンピューターの SPN キーにアクセスできない場合は、クライアントのエンドポイント ID でサービスを実行しているアカウントの正しい SPN またはユーザー プリンシパル名 (UPN: User Principal Name) を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1493d-163">If the service does not have access to the machine SPN key, you must supply the correct SPN or user principal name (UPN) of the account under which the service is running in the client's endpoint identity.</span></span> <span data-ttu-id="1493d-164">WCF での SPN と UPN の使用方法の詳細については、「 [サービス id と認証](service-identity-and-authentication.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1493d-164">For more information about how WCF works with SPN and UPN, see [Service Identity and Authentication](service-identity-and-authentication.md).</span></span>  
  
 <span data-ttu-id="1493d-165">Web ファームや Web ガーデンなどの負荷分散シナリオでは、各アプリケーションに一意のアカウントを定義し、そのアカウントに SPN を割り当て、アプリケーションのサービスすべてがそのアカウントで実行されるようにするのが一般的です。</span><span class="sxs-lookup"><span data-stu-id="1493d-165">In load-balancing scenarios, such as Web farms or Web gardens, a common practice is to define a unique account for each application, assign an SPN to that account, and ensure that all of the application's services run in that account.</span></span>  
  
 <span data-ttu-id="1493d-166">サービスのアカウント用の SPN を取得するには、Active Directory ドメイン管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="1493d-166">To obtain an SPN for your service's account, you need to be an Active Directory domain administrator.</span></span> <span data-ttu-id="1493d-167">詳細については、「 [Windows 用の Kerberos テクニカル補完](/previous-versions/msp-n-p/ff649429(v=pandp.10))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1493d-167">For more information, see [Kerberos Technical Supplement for Windows](/previous-versions/msp-n-p/ff649429(v=pandp.10)).</span></span>  
  
#### <a name="kerberos-protocol-direct-requires-the-service-to-run-under-a-domain-machine-account"></a><span data-ttu-id="1493d-168">Kerberos プロトコル ダイレクトでは Domain Machine アカウントでサービスを実行する必要がある</span><span class="sxs-lookup"><span data-stu-id="1493d-168">Kerberos Protocol Direct Requires the Service to Run Under a Domain Machine Account</span></span>  

 <span data-ttu-id="1493d-169">この状況は、次のコードに示すように、`ClientCredentialType` プロパティが `Windows` に設定され、<xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> プロパティが `false` に設定されている場合に発生します。</span><span class="sxs-lookup"><span data-stu-id="1493d-169">This occurs when the `ClientCredentialType` property is set to `Windows` and the <xref:System.ServiceModel.MessageSecurityOverHttp.NegotiateServiceCredential%2A> property is set to `false`, as shown in the following code.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#1)]
 [!code-vb[C_DebuggingWindowsAuth#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#1)]  
  
 <span data-ttu-id="1493d-170">これを解決するには、ドメインに参加しているコンピューターで、Domain Machine アカウント (Network Service など) を使用してサービスを実行します。</span><span class="sxs-lookup"><span data-stu-id="1493d-170">To remedy, run the service using a Domain Machine account, such as Network Service, on a domain joined machine.</span></span>  
  
### <a name="delegation-requires-credential-negotiation"></a><span data-ttu-id="1493d-171">委任には資格情報ネゴシエーションが必要</span><span class="sxs-lookup"><span data-stu-id="1493d-171">Delegation Requires Credential Negotiation</span></span>  

 <span data-ttu-id="1493d-172">委任で Kerberos 認証プロトコルを使用するには、資格情報ネゴシエーションを使用する Kerberos プロトコル ("マルチレッグ" Kerberos または "マルチステップ" Kerberos とも呼ばれます) を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1493d-172">To use the Kerberos authentication protocol with delegation, you must implement the Kerberos protocol with credential negotiation (sometimes called "multi-leg" or "multi-step" Kerberos).</span></span> <span data-ttu-id="1493d-173">資格情報ネゴシエーションを使用しない Kerberos 認証 ("ワンショット" Kerberos または "シングルレッグ" Kerberos とも呼ばれます) を実装した場合は、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="1493d-173">If you implement Kerberos authentication without credential negotiation (sometimes called "one-shot" or "single-leg" Kerberos), an exception will be thrown.</span></span>  
  
 <span data-ttu-id="1493d-174">資格情報ネゴシエーションを使用する Kerberos を実装するには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="1493d-174">To implement Kerberos with credential negotiation, do the following steps:</span></span>  
  
1. <span data-ttu-id="1493d-175"><xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> を <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> に設定して委任を実装します。</span><span class="sxs-lookup"><span data-stu-id="1493d-175">Implement delegation by setting <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> to <xref:System.Security.Principal.TokenImpersonationLevel.Delegation>.</span></span>  
  
2. <span data-ttu-id="1493d-176">次のような SSPI ネゴシエーションが必要です。</span><span class="sxs-lookup"><span data-stu-id="1493d-176">Require SSPI negotiation:</span></span>  
  
    1. <span data-ttu-id="1493d-177">標準バインディングを使用する場合は、`NegotiateServiceCredential` プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="1493d-177">If you are using standard bindings, set the `NegotiateServiceCredential` property to `true`.</span></span>  
  
    2. <span data-ttu-id="1493d-178">カスタム バインドを使用する場合は、`AuthenticationMode` 要素の `Security` 属性を `SspiNegotiated` に設定します。</span><span class="sxs-lookup"><span data-stu-id="1493d-178">If you are using custom bindings, set the `AuthenticationMode` attribute of the `Security` element to `SspiNegotiated`.</span></span>  
  
3. <span data-ttu-id="1493d-179">次のように、NTLM を使用できないようにすることで、SSPI ネゴシエーションで Kerberos を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="1493d-179">Require the SSPI negotiation to use Kerberos by disallowing the use of NTLM:</span></span>  
  
    1. <span data-ttu-id="1493d-180">NTLM を使用できないようにするには、コードで `ChannelFactory.Credentials.Windows.AllowNtlm = false` ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="1493d-180">Do this in code, with the following statement: `ChannelFactory.Credentials.Windows.AllowNtlm = false`</span></span>  
  
    2. <span data-ttu-id="1493d-181">構成ファイルで `allowNtlm` 属性を `false` に設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="1493d-181">Or you can do this in the configuration file by setting the `allowNtlm` attribute to `false`.</span></span> <span data-ttu-id="1493d-182">この属性は、に含まれてい [\<windows>](../../configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md) ます。</span><span class="sxs-lookup"><span data-stu-id="1493d-182">This attribute is contained in the [\<windows>](../../configure-apps/file-schema/wcf/windows-of-clientcredentials-element.md).</span></span>  
  
### <a name="ntlm-protocol"></a><span data-ttu-id="1493d-183">NTLM プロトコル</span><span class="sxs-lookup"><span data-stu-id="1493d-183">NTLM Protocol</span></span>  
  
#### <a name="negotiate-ssp-falls-back-to-ntlm-but-ntlm-is-disabled"></a><span data-ttu-id="1493d-184">ネゴシエート SSP は NTLM にフォールバックするが、NTLM が無効になっている</span><span class="sxs-lookup"><span data-stu-id="1493d-184">Negotiate SSP Falls Back to NTLM, but NTLM Is Disabled</span></span>  

 <span data-ttu-id="1493d-185"><xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A>プロパティがに設定されている `false` 場合、NTLM が使用されている場合、WINDOWS COMMUNICATION FOUNDATION (WCF) がベストエフォートで例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="1493d-185">The <xref:System.ServiceModel.Security.WindowsClientCredential.AllowNtlm%2A> property is set to `false`, which causes Windows Communication Foundation (WCF) to make a best-effort to throw an exception if NTLM is used.</span></span> <span data-ttu-id="1493d-186">このプロパティをに設定すると `false` 、NTLM 資格情報がネットワーク経由で送信されるのを防ぐことができません。</span><span class="sxs-lookup"><span data-stu-id="1493d-186">Setting this property to `false` may not prevent NTLM credentials from being sent over the wire.</span></span>  
  
 <span data-ttu-id="1493d-187">NTLM へのフォールバックを無効にする方法を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1493d-187">The following shows how to disable fallback to NTLM.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#4)]
 [!code-vb[C_DebuggingWindowsAuth#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#4)]  
  
#### <a name="ntlm-logon-fails"></a><span data-ttu-id="1493d-188">NTLM ログオンが失敗する</span><span class="sxs-lookup"><span data-stu-id="1493d-188">NTLM Logon Fails</span></span>  

 <span data-ttu-id="1493d-189">サービスで、クライアント資格情報が無効です。</span><span class="sxs-lookup"><span data-stu-id="1493d-189">The client credentials are not valid on the service.</span></span> <span data-ttu-id="1493d-190">ユーザー名とパスワードが正しく設定されており、サービスを実行しているコンピューターに認識されているアカウントに対応していることを確認します。</span><span class="sxs-lookup"><span data-stu-id="1493d-190">Check that the user name and password are correctly set and correspond to an account that is known to the computer where the service is running.</span></span> <span data-ttu-id="1493d-191">NTLM では、指定された資格情報を使用してサービスのコンピューターにログオンします。</span><span class="sxs-lookup"><span data-stu-id="1493d-191">NTLM uses the specified credentials to log on to the service's computer.</span></span> <span data-ttu-id="1493d-192">資格情報がクライアントを実行しているコンピューターで有効であっても、サービスのコンピューターでは無効な場合、このログオンは失敗します。</span><span class="sxs-lookup"><span data-stu-id="1493d-192">While the credentials may be valid on the computer where the client is running, this logon will fail if the credentials are not valid on the service's computer.</span></span>  
  
#### <a name="anonymous-ntlm-logon-occurs-but-anonymous-logons-are-disabled-by-default"></a><span data-ttu-id="1493d-193">匿名 NTLM ログオンが発生するが、既定では匿名ログオンが無効になっている</span><span class="sxs-lookup"><span data-stu-id="1493d-193">Anonymous NTLM Logon Occurs, but Anonymous Logons Are Disabled by Default</span></span>  

 <span data-ttu-id="1493d-194">次の例に示すように、クライアントの作成時に、<xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> プロパティを <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> に設定します。ただし、既定では、サーバーは匿名ログオンを許可しません。</span><span class="sxs-lookup"><span data-stu-id="1493d-194">When creating a client, the <xref:System.ServiceModel.Security.WindowsClientCredential.AllowedImpersonationLevel%2A> property is set to <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous>, as shown in the following example, but by default the server disallows anonymous logons.</span></span> <span data-ttu-id="1493d-195">これは、<xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> クラスの <xref:System.ServiceModel.Security.WindowsServiceCredential> プロパティの既定値が `false` であるためです。</span><span class="sxs-lookup"><span data-stu-id="1493d-195">This occurs because the default value of the <xref:System.ServiceModel.Security.WindowsServiceCredential.AllowAnonymousLogons%2A> property of the <xref:System.ServiceModel.Security.WindowsServiceCredential> class is `false`.</span></span>  
  
 <span data-ttu-id="1493d-196">匿名ログオンを有効にすることを試みるクライアント コードを次に示します (既定のプロパティは `Identification` です)。</span><span class="sxs-lookup"><span data-stu-id="1493d-196">The following client code attempts to enable anonymous logons (note that the default property is `Identification`).</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#5)]
 [!code-vb[C_DebuggingWindowsAuth#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#5)]  
  
 <span data-ttu-id="1493d-197">サーバーによって匿名ログオンを有効にするように既定値を変更するサービス コードを次に示します。</span><span class="sxs-lookup"><span data-stu-id="1493d-197">The following service code changes the default to enable anonymous logons by the server.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#6)]
 [!code-vb[C_DebuggingWindowsAuth#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#6)]  
  
 <span data-ttu-id="1493d-198">権限借用の詳細については、「 [委任と偽装](delegation-and-impersonation-with-wcf.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="1493d-198">For more information about impersonation, see [Delegation and Impersonation](delegation-and-impersonation-with-wcf.md).</span></span>  
  
 <span data-ttu-id="1493d-199">もう 1 つの方法として、SYSTEM ビルトイン アカウントを使用する Windows サービスとしてクライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="1493d-199">Alternatively, the client is running as a Windows service, using the built-in account SYSTEM.</span></span>  
  
### <a name="other-problems"></a><span data-ttu-id="1493d-200">その他の問題</span><span class="sxs-lookup"><span data-stu-id="1493d-200">Other Problems</span></span>  
  
#### <a name="client-credentials-are-not-set-correctly"></a><span data-ttu-id="1493d-201">クライアント資格情報が正しく設定されていない</span><span class="sxs-lookup"><span data-stu-id="1493d-201">Client Credentials Are Not Set Correctly</span></span>  

 <span data-ttu-id="1493d-202">Windows 認証では、<xref:System.ServiceModel.Security.WindowsClientCredential> ではなく、<xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> クラスの <xref:System.ServiceModel.ClientBase%601> プロパティによって返された <xref:System.ServiceModel.Security.UserNamePasswordClientCredential> インスタンスを使用します。</span><span class="sxs-lookup"><span data-stu-id="1493d-202">Windows authentication uses the <xref:System.ServiceModel.Security.WindowsClientCredential> instance returned by the <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> property of the <xref:System.ServiceModel.ClientBase%601> class, not the <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>.</span></span> <span data-ttu-id="1493d-203">誤りのあるコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1493d-203">The following shows an incorrect example.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#2)]
 [!code-vb[C_DebuggingWindowsAuth#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#2)]  
  
 <span data-ttu-id="1493d-204">正しいコード例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="1493d-204">The following shows the correct example.</span></span>  
  
 [!code-csharp[C_DebuggingWindowsAuth#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_debuggingwindowsauth/cs/source.cs#3)]
 [!code-vb[C_DebuggingWindowsAuth#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_debuggingwindowsauth/vb/source.vb#3)]  
  
#### <a name="sspi-is-not-available"></a><span data-ttu-id="1493d-205">SSPI を使用できない</span><span class="sxs-lookup"><span data-stu-id="1493d-205">SSPI Is Not Available</span></span>  

 <span data-ttu-id="1493d-206">サーバーとして使用する場合、次のオペレーティングシステムは Windows 認証をサポートしていません: Windows XP Home Edition、Windows XP Media Center Edition、および Windows Vista Home エディション。</span><span class="sxs-lookup"><span data-stu-id="1493d-206">The following operating systems do not support Windows authentication when used as a server: Windows XP Home Edition, Windows XP Media Center Edition, and Windows Vista Home editions.</span></span>  
  
#### <a name="developing-and-deploying-with-different-identities"></a><span data-ttu-id="1493d-207">異なる ID を使用した開発と展開</span><span class="sxs-lookup"><span data-stu-id="1493d-207">Developing and Deploying with Different Identities</span></span>  

 <span data-ttu-id="1493d-208">アプリケーションを 1 台のコンピューターで開発し、別のコンピューターに展開し、異なるアカウントの種類を使用して各コンピューターで認証を行う場合、動作の違いが発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="1493d-208">If you develop your application on one machine, and deploy on another, and use different account types to authenticate on each machine, you may experience different behavior.</span></span> <span data-ttu-id="1493d-209">たとえば、`SSPI Negotiated` 認証モードを使用して Windows XP Professional コンピューターでアプリケーションを開発するとします。</span><span class="sxs-lookup"><span data-stu-id="1493d-209">For example, suppose you develop your application on a Windows XP Pro machine using the `SSPI Negotiated` authentication mode.</span></span> <span data-ttu-id="1493d-210">ローカル ユーザー アカウントを使用して認証する場合は、NTLM プロトコルが使用されます。</span><span class="sxs-lookup"><span data-stu-id="1493d-210">If you use a local user account to authenticate with, then NTLM protocol will be used.</span></span> <span data-ttu-id="1493d-211">アプリケーションを開発した後は、ドメイン アカウントで実行されるサービスを Windows Server 2003 コンピューターに展開します。</span><span class="sxs-lookup"><span data-stu-id="1493d-211">Once the application is developed, you deploy the service to a Windows Server 2003 machine where it runs under a domain account.</span></span> <span data-ttu-id="1493d-212">この時点では、クライアントは Kerberos およびドメインコントローラーを使用するため、サービスを認証できません。</span><span class="sxs-lookup"><span data-stu-id="1493d-212">At this point, the client will not be able to authenticate the service because it will be using Kerberos and a domain controller.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1493d-213">関連項目</span><span class="sxs-lookup"><span data-stu-id="1493d-213">See also</span></span>

- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.Security.WindowsServiceCredential>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- <xref:System.ServiceModel.ClientBase%601>
- [<span data-ttu-id="1493d-214">委任と偽装</span><span class="sxs-lookup"><span data-stu-id="1493d-214">Delegation and Impersonation</span></span>](delegation-and-impersonation-with-wcf.md)
- [<span data-ttu-id="1493d-215">サポートされていないシナリオ</span><span class="sxs-lookup"><span data-stu-id="1493d-215">Unsupported Scenarios</span></span>](unsupported-scenarios.md)
