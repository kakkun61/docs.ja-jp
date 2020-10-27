---
title: .NET Framework の新機能
description: .NET Framework のさまざまなバージョンの新機能を参照してください。 各バージョンでの主要な新機能と機能強化の概要を確認してください。
ms.date: 10/21/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- what's new [.NET Framework]
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
ms.openlocfilehash: 6bbadd05187946cfdc601f9c026d685609251193
ms.sourcegitcommit: 870bc4b4087510f6fba3c7b1c0d391f02bcc1f3e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/23/2020
ms.locfileid: "92471944"
---
# <a name="whats-new-in-net-framework"></a><span data-ttu-id="39b71-104">.NET Framework の新機能</span><span class="sxs-lookup"><span data-stu-id="39b71-104">What's new in .NET Framework</span></span>

[!INCLUDE [net-framework-future](../../../includes/net-framework-future.md)]

<span data-ttu-id="39b71-105">この記事では、.NET Framework の次のバージョンにおける主な新機能と機能強化の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="39b71-105">This article summarizes key new features and improvements in the following versions of .NET Framework:</span></span>

- [<span data-ttu-id="39b71-106">.NET Framework 4.8</span><span class="sxs-lookup"><span data-stu-id="39b71-106">.NET Framework 4.8</span></span>](#v48)
- [<span data-ttu-id="39b71-107">.NET Framework 4.7.2</span><span class="sxs-lookup"><span data-stu-id="39b71-107">.NET Framework 4.7.2</span></span>](#v472)
- [<span data-ttu-id="39b71-108">.NET Framework 4.7.1</span><span class="sxs-lookup"><span data-stu-id="39b71-108">.NET Framework 4.7.1</span></span>](#v471)
- [<span data-ttu-id="39b71-109">.NET Framework 4.7</span><span class="sxs-lookup"><span data-stu-id="39b71-109">.NET Framework 4.7</span></span>](#v47)
- [<span data-ttu-id="39b71-110">.NET Framework 4.6.2</span><span class="sxs-lookup"><span data-stu-id="39b71-110">.NET Framework 4.6.2</span></span>](#v462)
- [<span data-ttu-id="39b71-111">.NET Framework 4.6.1</span><span class="sxs-lookup"><span data-stu-id="39b71-111">.NET Framework 4.6.1</span></span>](#v461)
- [<span data-ttu-id="39b71-112">.NET 2015 と .NET Framework 4.6</span><span class="sxs-lookup"><span data-stu-id="39b71-112">.NET 2015 and .NET Framework 4.6</span></span>](#v46)
- [<span data-ttu-id="39b71-113">.NET Framework 4.5.2</span><span class="sxs-lookup"><span data-stu-id="39b71-113">.NET Framework 4.5.2</span></span>](#v452)
- [<span data-ttu-id="39b71-114">.NET Framework 4.5.1</span><span class="sxs-lookup"><span data-stu-id="39b71-114">.NET Framework 4.5.1</span></span>](#v451)
- [<span data-ttu-id="39b71-115">.NET Framework 4.5</span><span class="sxs-lookup"><span data-stu-id="39b71-115">.NET Framework 4.5</span></span>](#v45)

<span data-ttu-id="39b71-116">この記事は、各新機能の包括的な情報を説明するものではありません。また、この内容は変更される可能性があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-116">This article does not provide comprehensive information about each new feature and is subject to change.</span></span> <span data-ttu-id="39b71-117">.NET Framework の概要については、「[.NET Framework の概要](../get-started/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-117">For general information about .NET Framework, see [Getting Started](../get-started/index.md).</span></span> <span data-ttu-id="39b71-118">サポートされているプラットフォームについては、「[.NET Framework システム要件](../get-started/system-requirements.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-118">For supported platforms, see [System Requirements](../get-started/system-requirements.md).</span></span> <span data-ttu-id="39b71-119">ダウンロード リンクとインストール手順については、「[.NET Framework のインストール](../install/guide-for-developers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-119">For download links and installation instructions, see [Installation Guide](../install/guide-for-developers.md).</span></span>

> [!NOTE]
> <span data-ttu-id="39b71-120">また .NET Framework チームでは、プラットフォームのサポートの拡張と、新機能 (変更できないコレクションや SIMD 対応ベクター型など) を OOB で NuGet を使用してリリースしています。</span><span class="sxs-lookup"><span data-stu-id="39b71-120">The .NET Framework team also releases features out of band, using NuGet, to expand platform support and introduce new functionality, such as immutable collections and SIMD-enabled vector types.</span></span> <span data-ttu-id="39b71-121">詳細については、「[追加のクラス ライブラリと API](../additional-apis/index.md)」および「[.NET Framework および特別なリリース](../get-started/the-net-framework-and-out-of-band-releases.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-121">For more information, see [Additional Class Libraries and APIs](../additional-apis/index.md) and [.NET Framework and Out-of-Band Releases](../get-started/the-net-framework-and-out-of-band-releases.md).</span></span>
> <span data-ttu-id="39b71-122">.NET Framework 用の [NuGet パッケージの完全な一覧](https://www.nuget.org/profiles/dotnetframework)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-122">See a [complete list of NuGet packages](https://www.nuget.org/profiles/dotnetframework) for .NET Framework.</span></span>

<a name="v48"></a>

## <a name="introducing-net-framework-48"></a><span data-ttu-id="39b71-123">.NET Framework 4.8 の概要</span><span class="sxs-lookup"><span data-stu-id="39b71-123">Introducing .NET Framework 4.8</span></span>

<span data-ttu-id="39b71-124">.NET Framework 4.8 は、.NET Framework 4.x の以前のバージョンに、多数の新しい修正といくつかの新機能を追加した、これまでと同様の非常に安定した製品です。</span><span class="sxs-lookup"><span data-stu-id="39b71-124">.NET Framework 4.8 builds on previous versions of .NET Framework 4.x by adding many new fixes and several new features while remaining a very stable product.</span></span>

### <a name="download-and-install-net-framework-48"></a><span data-ttu-id="39b71-125">.NET Framework 4.8 のダウンロードとインストール</span><span class="sxs-lookup"><span data-stu-id="39b71-125">Download and install .NET Framework 4.8</span></span>

<span data-ttu-id="39b71-126">.NET Framework 4.8 は、次の場所からダウンロードできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-126">You can download .NET Framework 4.8 from the following locations:</span></span>

- [<span data-ttu-id="39b71-127">.NET Framework 4.8 の Web インストーラー</span><span class="sxs-lookup"><span data-stu-id="39b71-127">.NET Framework 4.8 Web Installer</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)

- [<span data-ttu-id="39b71-128">NET Framework 4.8 のオフライン インストーラー</span><span class="sxs-lookup"><span data-stu-id="39b71-128">NET Framework 4.8 Offline Installer</span></span>](https://dotnet.microsoft.com/download/dotnet-framework/net48)

<span data-ttu-id="39b71-129">.NET Framework 4.8 は、Windows 10、Windows 8.1、Windows 7 SP1、および Windows Server 2008 R2 SP1 以降に相当するサーバー プラットフォームにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-129">.NET Framework 4.8 can be installed on Windows 10, Windows 8.1, Windows 7 SP1, and the corresponding server platforms starting with Windows Server 2008 R2 SP1.</span></span> <span data-ttu-id="39b71-130">.NET Framework 4.8 は、Web インストーラーまたはオフライン インストーラーを使用してインストールできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-130">You can install .NET Framework 4.8 by using either the web installer or the offline installer.</span></span> <span data-ttu-id="39b71-131">ほとんどのユーザーにお勧めする方法は、Web インストーラーの使用です。</span><span class="sxs-lookup"><span data-stu-id="39b71-131">The recommended way for most users is to use the web installer.</span></span>

<span data-ttu-id="39b71-132">[.NET Framework 4.8 Developer Pack](https://go.microsoft.com/fwlink/?LinkId=2085167) をインストールすれば、Visual Studio 2012 以降で、.NET Framework 4.8 をインストール対象に設定できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-132">You can target .NET Framework 4.8 in Visual Studio 2012 or later by installing the [.NET Framework 4.8 Developer Pack](https://go.microsoft.com/fwlink/?LinkId=2085167).</span></span>

### <a name="whats-new-in-net-framework-48"></a><span data-ttu-id="39b71-133">.NET Framework 4.8 の新機能</span><span class="sxs-lookup"><span data-stu-id="39b71-133">What's new in .NET Framework 4.8</span></span>

<span data-ttu-id="39b71-134">.NET Framework 4.8 には、次の領域の新機能が導入されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-134">.NET Framework 4.8 introduces new features in the following areas:</span></span>

- [<span data-ttu-id="39b71-135">基底クラス</span><span class="sxs-lookup"><span data-stu-id="39b71-135">Base classes</span></span>](#core48)
- [<span data-ttu-id="39b71-136">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="39b71-136">Windows Communication Foundation (WCF)</span></span>](#wcf48)
- [<span data-ttu-id="39b71-137">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="39b71-137">Windows Presentation Foundation (WPF)</span></span>](#wpf48)
- [<span data-ttu-id="39b71-138">共通言語ランタイム</span><span class="sxs-lookup"><span data-stu-id="39b71-138">Common language runtime</span></span>](#clr48)

<span data-ttu-id="39b71-139">アプリケーションで支援技術のユーザーに適切なエクスペリエンスを提供できるようにするアクセシビリティ機能の向上は、.NET Framework 4.8 でも引き続き大きな注目点です。</span><span class="sxs-lookup"><span data-stu-id="39b71-139">Improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology, continues to be a major focus of .NET Framework 4.8.</span></span> <span data-ttu-id="39b71-140">.NET Framework 4.8 でのアクセシビリティ機能の改善について詳しくは、「[.NET Framework のアクセシビリティの新機能](whats-new-in-accessibility.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-140">For information on accessibility improvements in .NET Framework 4.8, see [What's new in accessibility in .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core48"></a>

#### <a name="base-classes"></a><span data-ttu-id="39b71-141">基底クラス</span><span class="sxs-lookup"><span data-stu-id="39b71-141">Base classes</span></span>

<span data-ttu-id="39b71-142">**暗号での FIPS への影響の低下** 。</span><span class="sxs-lookup"><span data-stu-id="39b71-142">**Reduced FIPS impact on Cryptography** .</span></span> <span data-ttu-id="39b71-143">以前のバージョンの .NET Framework では、システムの暗号化ライブラリが "FIPS モード" で構成されていると、<xref:System.Security.Cryptography.SHA256Managed> などのマネージド暗号化プロバイダー クラスで <xref:System.Security.Cryptography.CryptographicException> がスローされました。</span><span class="sxs-lookup"><span data-stu-id="39b71-143">In previous versions of .NET Framework, managed cryptographic provider classes such as <xref:System.Security.Cryptography.SHA256Managed> throw a <xref:System.Security.Cryptography.CryptographicException> when the system cryptographic libraries are configured in "FIPS mode".</span></span> <span data-ttu-id="39b71-144">これらの例外がスローされるのは、暗号化プロバイダー クラスのマネージド バージョンは、システムの暗号化ライブラリとは異なり、FIPS (Federal Information Processing Standards) 140-2 の認定を受けていないためです。</span><span class="sxs-lookup"><span data-stu-id="39b71-144">These exceptions are thrown because the managed versions of the cryptographic provider classes, unlike the system cryptographic libraries, have not undergone FIPS (Federal Information Processing Standards) 140-2 certification.</span></span> <span data-ttu-id="39b71-145">開発用コンピューターを FIPS モードにしている開発者はほとんどいないため、例外は一般に運用システムでスローされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-145">Because few developers have their development machines in FIPS mode, the exceptions are commonly thrown in production systems.</span></span>

<span data-ttu-id="39b71-146">.NET Framework 4.8 を対象とするアプリケーションの既定の設定では、この場合に次のマネージド暗号化クラスで <xref:System.Security.Cryptography.CryptographicException> がスローされることはなくなりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-146">By default in applications that target .NET Framework 4.8, the following managed cryptography classes no longer throw a <xref:System.Security.Cryptography.CryptographicException> in this case:</span></span>

- <xref:System.Security.Cryptography.MD5Cng>
- <xref:System.Security.Cryptography.MD5CryptoServiceProvider>
- <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
- <xref:System.Security.Cryptography.RijndaelManaged>
- <xref:System.Security.Cryptography.RIPEMD160Managed>
- <xref:System.Security.Cryptography.SHA256Managed>

<span data-ttu-id="39b71-147">代わりに、これらのクラスでは、暗号化操作はシステムの暗号化ライブラリにリダイレクトされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-147">Instead, these classes redirect cryptographic operations to a system cryptography library.</span></span> <span data-ttu-id="39b71-148">この変更により、開発者環境と運用環境での混乱を招く可能性のある違いは実質的になくなり、ネイティブ コンポーネントとマネージド コンポーネントは同じ暗号化ポリシーの下で動作するようになります。</span><span class="sxs-lookup"><span data-stu-id="39b71-148">This change effectively removes a potentially confusing difference between developer environments and production environments and makes native components and managed components operate under the same cryptographic policy.</span></span> <span data-ttu-id="39b71-149">これらの例外に依存するアプリケーションでは、AppContext スイッチ `Switch.System.Security.Cryptography.UseLegacyFipsThrow` を `true` に設定することで、以前の動作に戻すことができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-149">Applications that depend on these exceptions can restore the previous behavior by setting the AppContext switch `Switch.System.Security.Cryptography.UseLegacyFipsThrow` to `true`.</span></span> <span data-ttu-id="39b71-150">詳しくは、「[Managed cryptography classes do not throw a CryptographyException in FIPS mode (FIPS モードのマネージド暗号クラスで CryptographyException がスローされない)](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-150">For more information, see [Managed cryptography classes do not throw a CryptographyException in FIPS mode](../migration-guide/retargeting/4.7.2-4.8.md#managed-cryptography-classes-do-not-throw-a-cryptographyexception-in-fips-mode).</span></span>

<span data-ttu-id="39b71-151">**ZLib の更新バージョンの使用**</span><span class="sxs-lookup"><span data-stu-id="39b71-151">**Use of updated version of ZLib**</span></span>

<span data-ttu-id="39b71-152">.NET Framework 4.5 以降の clrcompression.dll アセンブリでは、deflate アルゴリズムの実装を提供するため、データ圧縮用のネイティブ外部ライブラリである [ZLib](https://www.zlib.net) が使われています。</span><span class="sxs-lookup"><span data-stu-id="39b71-152">Starting with .NET Framework 4.5, the clrcompression.dll assembly uses [ZLib](https://www.zlib.net), a native external library for data compression, in order to provide an implementation for the deflate algorithm.</span></span> <span data-ttu-id="39b71-153">.NET Framework 4.8 バージョンの clrcompression.dll は、いくつかの重要な機能強化と修正を含む ZLib バージョン 1.2.11 を使用するように更新されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-153">The .NET Framework 4.8 version of clrcompression.dll is updated to use ZLib Version 1.2.11, which includes several key improvements and fixes.</span></span>

<a name="wcf48"></a>

#### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="39b71-154">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="39b71-154">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="39b71-155">**ServiceHealthBehavior の導入**</span><span class="sxs-lookup"><span data-stu-id="39b71-155">**Introduction of ServiceHealthBehavior**</span></span>

<span data-ttu-id="39b71-156">正常性エンドポイントは、正常性の状態に基づいてサービスを管理するため、オーケストレーション ツールで広く使用されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-156">Health endpoints are widely used by orchestration tools to manage services based on their health status.</span></span> <span data-ttu-id="39b71-157">正常性チェックは、サービスの可用性とパフォーマンスを追跡して通知を提供するため、監視ツールでも使用できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-157">Health checks can also be used by monitoring tools to track and provide notifications about the availability and performance of a service.</span></span>

<span data-ttu-id="39b71-158">**ServiceHealthBehavior** は、<xref:System.ServiceModel.Description.IServiceBehavior> を拡張する WCF サービスの動作です。</span><span class="sxs-lookup"><span data-stu-id="39b71-158">**ServiceHealthBehavior** is a WCF service behavior that extends <xref:System.ServiceModel.Description.IServiceBehavior>.</span></span>  <span data-ttu-id="39b71-159"><xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> コレクションに追加すると、サービスの動作は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="39b71-159">When added to the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors?displayProperty=nameWithType> collection, a service behavior does the following:</span></span>

- <span data-ttu-id="39b71-160">HTTP 応答コードでサービスの正常性状態が返されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-160">Returns service health status with HTTP response codes.</span></span> <span data-ttu-id="39b71-161">HTTP/GET 正常性プローブ要求に対する HTTP 状態コードを、クエリ文字列で指定できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-161">You can specify in a query string the HTTP status code for a HTTP/GET health probe request.</span></span>

- <span data-ttu-id="39b71-162">サービスの正常性に関する情報が公開されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-162">Publishes information about service health.</span></span> <span data-ttu-id="39b71-163">サービスの状態、スロットルの数、容量などのサービス固有の詳細を、`?health` クエリ文字列を含む HTTP/GET 要求を使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-163">Service-specific details, including service state, throttle counts, and capacity can be displayed by using an HTTP/GET request with the `?health` query string.</span></span> <span data-ttu-id="39b71-164">動作がおかしい WCF サービスのトラブルシューティングを行うときは、このような情報に簡単にアクセスできることが重要です。</span><span class="sxs-lookup"><span data-stu-id="39b71-164">Ease of access to such information is important when troubleshooting a misbehaving WCF service.</span></span>

<span data-ttu-id="39b71-165">正常性エンドポイントを公開し、WCF サービスの正常性情報を公開するには、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-165">There are two ways to expose the health endpoint and publish WCF service health information:</span></span>

- <span data-ttu-id="39b71-166">コードの使用。</span><span class="sxs-lookup"><span data-stu-id="39b71-166">Through code.</span></span> <span data-ttu-id="39b71-167">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="39b71-167">For example:</span></span>

  ```csharp
  ServiceHost host = new ServiceHost(typeof(Service1),
                     new Uri("http://contoso:81/Service1"));
  ServiceHealthBehavior healthBehavior =
      host.Description.Behaviors.Find<ServiceHealthBehavior>();
  healthBehavior ??= new ServiceHealthBehavior();
  host.Description.Behaviors.Add(healthBehavior);
  ```

  ```vb
  Dim host As New ServiceHost(GetType(Service1),
              New Uri("http://contoso:81/Service1"))
  Dim healthBehavior As ServiceHealthBehavior =
     host.Description.Behaviors.Find(Of ServiceHealthBehavior)()
  If healthBehavior Is Nothing Then
     healthBehavior = New ServiceHealthBehavior()
  End If
  host.Description.Behaviors.Add(healthBehavior)
  ```

- <span data-ttu-id="39b71-168">構成ファイルの使用。</span><span class="sxs-lookup"><span data-stu-id="39b71-168">By using a configuration file.</span></span> <span data-ttu-id="39b71-169">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="39b71-169">For example:</span></span>

  ```xml
  <behaviors>
    <serviceBehaviors>
      <behavior name="DefaultBehavior">
        <serviceHealth httpsGetEnabled="true"/>
      </behavior>
    </serviceBehaviors>
  </behaviors>
  ```

<span data-ttu-id="39b71-170">`OnServiceFailure`、`OnDispatcherFailure`、`OnListenerFailure`、`OnThrottlePercentExceeded` などのクエリ パラメーターを使用して、サービスの正常性状態のクエリを実行することができ、各クエリ パラメーターに対して HTTP 応答コードを指定できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-170">A service's health status can be queried by using query parameters such as `OnServiceFailure`, `OnDispatcherFailure`, `OnListenerFailure`, `OnThrottlePercentExceeded`), and an HTTP response code can be specified for each query parameter.</span></span> <span data-ttu-id="39b71-171">クエリ パラメーターで HTTP 応答コードを省略すると、503 HTTP 応答コードが既定で使われます。</span><span class="sxs-lookup"><span data-stu-id="39b71-171">If the HTTP response code is omitted for a query parameter, a 503 HTTP response code is used by default.</span></span> <span data-ttu-id="39b71-172">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="39b71-172">For example:</span></span>

- <span data-ttu-id="39b71-173">OnServiceFailure: `https://contoso:81/Service1?health&OnServiceFailure=450`</span><span class="sxs-lookup"><span data-stu-id="39b71-173">OnServiceFailure: `https://contoso:81/Service1?health&OnServiceFailure=450`</span></span>

  <span data-ttu-id="39b71-174">[ServiceHost.State](xref:System.ServiceModel.Channels.CommunicationObject.State) が <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType> より大きい場合、450 HTTP 応答状態コードが返されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-174">A 450 HTTP response status code is returned when [ServiceHost.State](xref:System.ServiceModel.Channels.CommunicationObject.State) is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="39b71-175">クエリ パラメーターと例:</span><span class="sxs-lookup"><span data-stu-id="39b71-175">Query parameters and examples:</span></span>

- <span data-ttu-id="39b71-176">OnDispatcherFailure: `https://contoso:81/Service1?health&OnDispatcherFailure=455`</span><span class="sxs-lookup"><span data-stu-id="39b71-176">OnDispatcherFailure: `https://contoso:81/Service1?health&OnDispatcherFailure=455`</span></span>

  <span data-ttu-id="39b71-177">いずれかのチャネル ディスパッチャーの状態が <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType> より大きい場合、455 HTTP 応答状態コードが返されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-177">A 455 HTTP response status code is returned when the state of any of the channel dispatchers is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="39b71-178">OnListenerFailure: `https://contoso:81/Service1?health&OnListenerFailure=465`</span><span class="sxs-lookup"><span data-stu-id="39b71-178">OnListenerFailure: `https://contoso:81/Service1?health&OnListenerFailure=465`</span></span>

  <span data-ttu-id="39b71-179">いずれかのチャネル リスナーの状態が <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType> より大きい場合、465 HTTP 応答状態コードが返されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-179">A 465 HTTP response status code is returned when the state of any of the channel listeners is greater than <xref:System.ServiceModel.CommunicationState.Opened?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="39b71-180">OnThrottlePercentExceeded: `https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`</span><span class="sxs-lookup"><span data-stu-id="39b71-180">OnThrottlePercentExceeded: `https://contoso:81/Service1?health&OnThrottlePercentExceeded= 70:350,95:500`</span></span>

  <span data-ttu-id="39b71-181">応答をトリガーする割合 {1 – 100} とその HTTP 応答コード {200 – 599} を指定します。</span><span class="sxs-lookup"><span data-stu-id="39b71-181">Specifies the percentage {1 – 100} that triggers the response and its HTTP response code {200 – 599}.</span></span> <span data-ttu-id="39b71-182">この例では、次のように記述されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-182">In this example:</span></span>

  - <span data-ttu-id="39b71-183">割合が 95 より大きい場合、500 HTTP 応答コードが返されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-183">If the percentage is greater than 95, a 500 HTTP response code is returned.</span></span>

  - <span data-ttu-id="39b71-184">割合が 70 – 95 の場合は、350 が返されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-184">If the percentage or between 70 and 95, 350 is returned.</span></span>

  - <span data-ttu-id="39b71-185">それ以外の場合は、200 が返されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-185">Otherwise, 200 is returned.</span></span>

<span data-ttu-id="39b71-186">サービスの正常性状態は、HTML (`https://contoso:81/Service1?health` のようなクエリ文字列を指定) または XML (`https://contoso:81/Service1?health&Xml` のようなクエリ文字列を指定) で表示できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-186">The service health status can be displayed either in HTML by specifying a query string like `https://contoso:81/Service1?health` or in XML by specifying a query string like `https://contoso:81/Service1?health&Xml`.</span></span> <span data-ttu-id="39b71-187">`https://contoso:81/Service1?health&NoContent` のようなクエリ文字列では、空の HTML ページが返されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-187">A query string like `https://contoso:81/Service1?health&NoContent` returns an empty HTML page.</span></span>

<a name="wpf48"></a>

#### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="39b71-188">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="39b71-188">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="39b71-189">**高 DPI の機能強化**</span><span class="sxs-lookup"><span data-stu-id="39b71-189">**High DPI enhancements**</span></span>

<span data-ttu-id="39b71-190">.NET Framework 4.8 では、WPF でモニターごとの V2 DPI の認識および混合モードの DPI スケーリングのサポートが追加されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-190">In .NET Framework 4.8, WPF adds support for Per-Monitor V2 DPI Awareness and Mixed-Mode DPI scaling.</span></span> <span data-ttu-id="39b71-191">高 DPI の開発に関する追加情報については、「[High DPI Desktop Application Development on Windows (Windows での高 DPI デスクトップ アプリケーション開発)](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-191">See [High DPI Desktop Application Development on Windows](/windows/win32/hidpi/high-dpi-desktop-application-development-on-windows) for additional information about high DPI development.</span></span>

<span data-ttu-id="39b71-192">.NET framework 4.8 では、混合モードの DPI スケーリングをサポートするプラットフォーム上の高 DPI WPF アプリケーションでのホステッド HWND と Windows フォームの相互運用のためのサポートが向上しています (Windows 10 April 2018 Update 以降)。</span><span class="sxs-lookup"><span data-stu-id="39b71-192">.NET Framework 4.8 improves support for hosted HWNDs and Windows Forms interoperation in High-DPI WPF applications on platforms that support Mixed-Mode DPI scaling (starting with Windows 10 April 2018 Update).</span></span> <span data-ttu-id="39b71-193">[SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) および [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext) を呼び出すことによって、ホステッド HWND または Windows フォームのコントロールを混合モードの DPI スケーリングされたウィンドウとして作成すると、それらはモニターごとの V2 WPF アプリケーション内でホストでき、適切にサイズ設定およびスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-193">When hosted HWNDs or Windows Forms controls are created as Mixed-Mode DPI-scaled windows by calling [SetThreadDpiHostingBehavior](/windows/desktop/api/winuser/nf-winuser-setthreaddpihostingbehavior) and [SetThreadDpiAwarenessContext](/windows/desktop/api/winuser/nf-winuser-setthreaddpiawarenesscontext), they can be hosted in a Per-Monitor V2 WPF application and are sized and scaled appropriately.</span></span> <span data-ttu-id="39b71-194">そのようなホステッド コンテンツは、ネイティブ DPI ではレンダリングされず、代わりにオペレーティング システムによって適切なサイズにスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-194">Such hosted content is not rendered at the native DPI; instead, the operating system scales the hosted content to the appropriate size.</span></span> <span data-ttu-id="39b71-195">モニターごとの v2 DPI 認識モードのサポートにより、高 DPI アプリケーションのネイティブ ウィンドウで WPF コントロールをホストする (つまり、子にする) こともできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-195">The support for Per-Monitor v2 DPI awareness mode also allows WPF controls to be hosted (i.e., parented) in a native window in a high-DPI application.</span></span>

<span data-ttu-id="39b71-196">混合モードの高 DPI スケーリングのサポートを有効にするには、アプリケーション構成ファイルで次の [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) スイッチを設定します。</span><span class="sxs-lookup"><span data-stu-id="39b71-196">To enable support for Mixed-Mode High DPI scaling, you can set the following [AppContext](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) switches the application configuration file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value = "Switch.System.Windows.DoNotScaleForDpiChanges=false; Switch.System.Windows.DoNotUsePresentationDpiCapabilityTier2OrGreater=false"/>
</runtime>
```

<a name="clr48"></a>

#### <a name="common-language-runtime"></a><span data-ttu-id="39b71-197">共通言語ランタイム</span><span class="sxs-lookup"><span data-stu-id="39b71-197">Common language runtime</span></span>

<span data-ttu-id="39b71-198">NET Framework 4.8 のランタイムには、次の変更と強化が含まれます。</span><span class="sxs-lookup"><span data-stu-id="39b71-198">The runtime in .NET Framework 4.8 includes the following changes and improvements:</span></span>

<span data-ttu-id="39b71-199">**JIT コンパイラの機能強化** 。</span><span class="sxs-lookup"><span data-stu-id="39b71-199">**Improvements to the JIT compiler** .</span></span> <span data-ttu-id="39b71-200">.NET Framework 4.8 の Just-In-Time (JIT) コンパイラは、.NET Core 2.1 の JIT コンパイラが基になっていいます。</span><span class="sxs-lookup"><span data-stu-id="39b71-200">The Just-in-time (JIT) compiler in .NET Framework 4.8 is based on the JIT compiler in .NET Core 2.1.</span></span> <span data-ttu-id="39b71-201">.NET Core 2.1 の JIT コンパイラに対して行われた最適化の多くとすべてのバグ修正が、.NET Framework 4.8 の JIT コンパイラに含まれます。</span><span class="sxs-lookup"><span data-stu-id="39b71-201">Many of the optimizations and all of the bug fixes made to the .NET Core 2.1 JIT compiler are included in the .NET Framework 4.8 JIT compiler.</span></span>

<span data-ttu-id="39b71-202">**NGEN の機能強化** 。</span><span class="sxs-lookup"><span data-stu-id="39b71-202">**NGEN improvements** .</span></span> <span data-ttu-id="39b71-203">ランタイムでは、[ネイティブ イメージ ジェネレーター](../tools/ngen-exe-native-image-generator.md) (NGEN) のイメージに対するメモリ管理が改善され、NGEN イメージからマップされているデータがメモリに常駐しないようになっています。</span><span class="sxs-lookup"><span data-stu-id="39b71-203">The runtime has improved its memory management for [Native Image Generator](../tools/ngen-exe-native-image-generator.md) (NGEN) images so that data mapped from NGEN images are not memory-resident.</span></span> <span data-ttu-id="39b71-204">これにより、実行されるメモリを変更することによって任意のコードを実行しようとする攻撃に利用可能な領域が減ります。</span><span class="sxs-lookup"><span data-stu-id="39b71-204">This reduces the surface area available to attacks that attempt to execute arbitrary code by modifying memory that will be executed.</span></span>

<span data-ttu-id="39b71-205">**すべてのアセンブリに対するマルウェア対策スキャン** 。</span><span class="sxs-lookup"><span data-stu-id="39b71-205">**Antimalware scanning for all assemblies** .</span></span> <span data-ttu-id="39b71-206">以前のバージョンの .NET Framework のランタイムでは、Windows Defender またはサード パーティのマルウェア対策ソフトウェアを使用して、ディスクから読み込まれたすべてのアセンブリがスキャンされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-206">In previous versions of .NET Framework, the runtime scans all assemblies loaded from disk using either Windows Defender or third-party antimalware software.</span></span> <span data-ttu-id="39b71-207">しかし、<xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> メソッドなどの他のソースから読み込まれたアセンブリはスキャンされず、検出されていないマルウェアが含まれる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-207">However, assemblies loaded from other sources, such as by the <xref:System.Reflection.Assembly.Load(System.Byte[])?displayProperty=nameWithType> method, are not scanned and can potentially contain undetected malware.</span></span> <span data-ttu-id="39b71-208">Windows 10 で実行される .NET Framework 4.8 以降のランタイムでは、[Antimalware Scan Interface (AMSI)](/windows/desktop/AMSI/antimalware-scan-interface-portal) を実装するマルウェア対策ソリューションによるスキャンがトリガーされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-208">Starting with .NET Framework 4.8 running on Windows 10, the runtime triggers a scan by antimalware solutions that implement the [Antimalware Scan Interface (AMSI)](/windows/desktop/AMSI/antimalware-scan-interface-portal).</span></span>

<a name="v472"></a>

## <a name="whats-new-in-net-framework-472"></a><span data-ttu-id="39b71-209">.NET Framework 4.7.2 の新機能</span><span class="sxs-lookup"><span data-stu-id="39b71-209">What's new in .NET Framework 4.7.2</span></span>

<span data-ttu-id="39b71-210">.NET Framework 4.7.2 には、次の領域における新機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="39b71-210">.NET Framework 4.7.2 includes new features in the following areas:</span></span>

- [<span data-ttu-id="39b71-211">基底クラス</span><span class="sxs-lookup"><span data-stu-id="39b71-211">Base classes</span></span>](#core-472)
- [<span data-ttu-id="39b71-212">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="39b71-212">ASP.NET</span></span>](#asp-net472)
- [<span data-ttu-id="39b71-213">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="39b71-213">Networking</span></span>](#net472)
- [<span data-ttu-id="39b71-214">SQL</span><span class="sxs-lookup"><span data-stu-id="39b71-214">SQL</span></span>](#sql472)
- [<span data-ttu-id="39b71-215">WPF</span><span class="sxs-lookup"><span data-stu-id="39b71-215">WPF</span></span>](#wpf472)
- [<span data-ttu-id="39b71-216">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="39b71-216">ClickOnce</span></span>](#clickonce)

<span data-ttu-id="39b71-217">.NET Framework 4.7.2 では引き続きアクセシビリティ機能の向上が重視されており、それによりアプリケーションでは支援技術のユーザーに適切なエクスペリエンスを提供できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-217">A continuing focus in .NET Framework 4.7.2 is improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="39b71-218">.NET Framework 4.7.2 でのアクセシビリティ機能の改善について詳しくは、「[.NET Framework のアクセシビリティの新機能](whats-new-in-accessibility.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-218">For information on accessibility improvements in .NET Framework 4.7.2, see [What's new in accessibility in .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core-472"></a>

#### <a name="base-classes"></a><span data-ttu-id="39b71-219">基底クラス</span><span class="sxs-lookup"><span data-stu-id="39b71-219">Base classes</span></span>

<span data-ttu-id="39b71-220">.NET Framework 4.7.2 は、大量の暗号化の機能強化、ZIP アーカイブの圧縮解除サポートの向上、および追加のコレクションの API を備えています。</span><span class="sxs-lookup"><span data-stu-id="39b71-220">.NET Framework 4.7.2 features a large number of cryptographic enhancements, better decompression support for ZIP archives, and additional collection APIs.</span></span>

<span data-ttu-id="39b71-221">**RSA.Create および DSA.Create の新しいオーバーロード**</span><span class="sxs-lookup"><span data-stu-id="39b71-221">**New overloads of RSA.Create and DSA.Create**</span></span>

<span data-ttu-id="39b71-222"><xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> および <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> メソッドを使うと、新しい <xref:System.Security.Cryptography.DSA> または <xref:System.Security.Cryptography.RSA> キーをインスタンス化するときにキーのパラメーターを指定できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-222">The <xref:System.Security.Cryptography.DSA.Create(System.Security.Cryptography.DSAParameters)?displayProperty=nameWithType> and <xref:System.Security.Cryptography.RSA.Create(System.Security.Cryptography.RSAParameters)?displayProperty=nameWithType> methods let you supply key parameters when instantiating a new <xref:System.Security.Cryptography.DSA> or <xref:System.Security.Cryptography.RSA> key.</span></span> <span data-ttu-id="39b71-223">次のようなコードを置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-223">They allow you to replace code like the following:</span></span>

```csharp
// Before .NET Framework 4.7.2
using (RSA rsa = RSA.Create())
{
   rsa.ImportParameters(rsaParameters);
   // Other code to execute using the RSA instance.
}
```

```vb
' Before .NET Framework 4.7.2
Using rsa = RSA.Create()
   rsa.ImportParameters(rsaParameters)
   ' Other code to execute using the rsa instance.
End Using
```

<span data-ttu-id="39b71-224">次のようなコードに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="39b71-224">with code like this:</span></span>

```csharp
// Starting with .NET Framework 4.7.2
using (RSA rsa = RSA.Create(rsaParameters))
{
   // Other code to execute using the rsa instance.
}
```

```vb
' Starting with .NET Framework 4.7.2
Using rsa = RSA.Create(rsaParameters)
   ' Other code to execute using the rsa instance.
End Using
```

<span data-ttu-id="39b71-225"><xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> および <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> メソッドでは、特定のキー サイズを指定して、新しい <xref:System.Security.Cryptography.DSA> または <xref:System.Security.Cryptography.RSA> キーを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-225">The <xref:System.Security.Cryptography.DSA.Create(System.Int32)?displayProperty=nameWithType> and <xref:System.Security.Cryptography.RSA.Create(System.Int32)?displayProperty=nameWithType> methods let you generate new <xref:System.Security.Cryptography.DSA> or <xref:System.Security.Cryptography.RSA> keys with a specific key size.</span></span> <span data-ttu-id="39b71-226">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="39b71-226">For example:</span></span>

```csharp
using (DSA dsa = DSA.Create(2048))
{
   // Other code to execute using the dsa instance.
}
```

```vb
Using dsa = DSA.Create(2048)
   ' Other code to execute using the dsa instance.
End Using
```

<span data-ttu-id="39b71-227">**Rfc2898DeriveBytes コンストラクターは、ハッシュ アルゴリズムの名前を受け入れる**</span><span class="sxs-lookup"><span data-stu-id="39b71-227">**Rfc2898DeriveBytes constructors accept a hash algorithm name**</span></span>

<span data-ttu-id="39b71-228"><xref:System.Security.Cryptography.Rfc2898DeriveBytes> クラスには、3 つの新しいコンストラクターがあり、キーを派生するときに使用する HMAC アルゴリズムを識別する <xref:System.Security.Cryptography.HashAlgorithmName> パラメーターを使用します。</span><span class="sxs-lookup"><span data-stu-id="39b71-228">The <xref:System.Security.Cryptography.Rfc2898DeriveBytes> class has three new constructors with a <xref:System.Security.Cryptography.HashAlgorithmName> parameter that identifies the HMAC algorithm to use when deriving keys.</span></span> <span data-ttu-id="39b71-229">SHA-1 を使用する代わりに、開発者は、次の例に示すように SHA-256 などの SHA-2 ベースの HMAC を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-229">Instead of using SHA-1, developers should use a SHA-2-based HMAC like SHA-256, as shown in the following example:</span></span>

```csharp
private static byte[] DeriveKey(string password, out int iterations, out byte[] salt,
                                out HashAlgorithmName algorithm)
{
   iterations = 100000;
   algorithm = HashAlgorithmName.SHA256;

   const int SaltSize = 32;
   const int DerivedValueSize = 32;

   using (Rfc2898DeriveBytes pbkdf2 = new Rfc2898DeriveBytes(password, SaltSize,
                                                             iterations, algorithm))
   {
      salt = pbkdf2.Salt;
      return pbkdf2.GetBytes(DerivedValueSize);
   }
}
```

```vb
Private Shared Function DeriveKey(password As String, ByRef iterations As Integer,
                                  ByRef salt AS Byte(), ByRef algorithm As HashAlgorithmName) As Byte()
   iterations = 100000
   algorithm = HashAlgorithmName.SHA256

   Const SaltSize As Integer = 32
   Const  DerivedValueSize As Integer = 32

   Using pbkdf2 = New Rfc2898DeriveBytes(password, SaltSize, iterations, algorithm)
      salt = pbkdf2.Salt
      Return pbkdf2.GetBytes(DerivedValueSize)
   End Using
End Function
```

<span data-ttu-id="39b71-230">**一時的なキーのサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-230">**Support for ephemeral keys**</span></span>

<span data-ttu-id="39b71-231">PFX のインポートでは、必要に応じてハード ドライブをバイパスして、メモリから直接秘密キーを読み込むことができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-231">PFX import can optionally load private keys directly from memory, bypassing the hard drive.</span></span> <span data-ttu-id="39b71-232"> 新しい <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> フラグが、<xref:System.Security.Cryptography.X509Certificates.X509Certificate2> コンストラクターまたは <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> メソッドのいずれかのオーバーロードで指定されているときには、一時的なキーとして秘密キーが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="39b71-232">When the new <xref:System.Security.Cryptography.X509Certificates.X509KeyStorageFlags.EphemeralKeySet?displayProperty=nameWithType> flag is specified in an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> constructor or one of the overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.Import%2A?displayProperty=nameWithType> method, the private keys will be loaded as ephemeral keys.</span></span> <span data-ttu-id="39b71-233">これにより、キーがディスク上に表示されることを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="39b71-233">This prevents the keys from being visible on the disk.</span></span> <span data-ttu-id="39b71-234">ただし、</span><span class="sxs-lookup"><span data-stu-id="39b71-234">However:</span></span>

- <span data-ttu-id="39b71-235">キーは、ディスク上に持続しないので、このフラグで読み込まれた証明書は、X509Store に追加する適切な候補ではありません。</span><span class="sxs-lookup"><span data-stu-id="39b71-235">Since the keys are not persisted to disk, certificates loaded with this flag are not good candidates to add to an X509Store.</span></span>

- <span data-ttu-id="39b71-236">この方法で読み込まれたキーは、ほとんどの場合、Windows CNG を使用して読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="39b71-236">Keys loaded in this manner are almost always loaded via Windows CNG.</span></span> <span data-ttu-id="39b71-237">そのため呼び出し元は、[cert.GetRSAPrivateKey()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A) などの拡張メソッドを呼び出すことによって秘密キーにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-237">Therefore, callers must access the private key by calling extension methods, such as [cert.GetRSAPrivateKey()](xref:System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey%2A).</span></span> <span data-ttu-id="39b71-238"><xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> プロパティは機能しません。</span><span class="sxs-lookup"><span data-stu-id="39b71-238">The <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> property does not function.</span></span>

- <span data-ttu-id="39b71-239">従来の <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> プロパティは、証明書では機能しないので、開発者は、一時的なキーに切り替える前に厳格なテストを実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-239">Since the legacy <xref:System.Security.Cryptography.X509Certificates.X509Certificate2.PrivateKey?displayProperty=nameWithType> property does not work with certificates, developers should perform rigorous testing before switching to ephemeral keys.</span></span>

<span data-ttu-id="39b71-240">**PKCS #10 証明書署名要求と X.509 公開キー証明書のプログラムによる作成**</span><span class="sxs-lookup"><span data-stu-id="39b71-240">**Programmatic creation of PKCS#10 certification signing requests and X.509 public key certificates**</span></span>

<span data-ttu-id="39b71-241">.NET Framework 4.7.2 以降、ワークロードは、証明書署名要求 (CSR) を生成できるようになりました。これにより、証明書要求の生成を既存のツールにステージングすることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-241">Starting with .NET Framework 4.7.2, workloads can generate certificate signing requests (CSRs), which allows certificate request generation to be staged into existing tooling.</span></span> <span data-ttu-id="39b71-242">これは、テストのシナリオでよく役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="39b71-242">This is frequently useful in test scenarios.</span></span>

<span data-ttu-id="39b71-243">詳細およびコードの例については、[.NET ブログ](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/)の「Programmatic creation of PKCS#10 certification signing requests and X.509 public key certificates」(PKCS #10 証明書署名要求と X.509 公開キー証明書のプログラムによる作成) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-243">For more information and code examples, see "Programmatic creation of PKCS#10 certification signing requests and X.509 public key certificates" in the [.NET Blog](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span></span>

<span data-ttu-id="39b71-244">**新しい SignerInfo メンバー**</span><span class="sxs-lookup"><span data-stu-id="39b71-244">**New SignerInfo members**</span></span>

<span data-ttu-id="39b71-245">.NET Framework 4.7.2 以降、<xref:System.Security.Cryptography.Pkcs.SignerInfo> クラスでは署名についてさらに多くの詳細が公開されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-245">Starting with .NET Framework 4.7.2, the <xref:System.Security.Cryptography.Pkcs.SignerInfo> class exposes more information about the signature.</span></span> <span data-ttu-id="39b71-246"><xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> プロパティの値を取得して、署名者によって使用される署名アルゴリズムを判断することができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-246">You can retrieve the value of the <xref:System.Security.Cryptography.Pkcs.SignerInfo.SignatureAlgorithm?displayProperty=fullName> property to determine the signature algorithm used by the signer.</span></span> <span data-ttu-id="39b71-247"><xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType> を呼び出して、この署名者の暗号化署名のコピーを取得することができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-247"><xref:System.Security.Cryptography.Pkcs.SignerInfo.GetSignature%2A?displayProperty=nameWithType> can be called to get a copy of the cryptographic signature for this signer.</span></span>

<span data-ttu-id="39b71-248">**CryptoStream が破棄された後にラップされたストリームを開いたままにする**</span><span class="sxs-lookup"><span data-stu-id="39b71-248">**Leaving a wrapped stream open after CryptoStream is disposed**</span></span>

<span data-ttu-id="39b71-249">.NET Framework 4.7.2 以降、<xref:System.Security.Cryptography.CryptoStream> クラスの追加のコンストラクターを使用して、<xref:System.Security.Cryptography.CryptoStream.Dispose%2A> でラップされたストリームを開いたままにすることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-249">Starting with .NET Framework 4.7.2, the <xref:System.Security.Cryptography.CryptoStream> class has an additional constructor that allows <xref:System.Security.Cryptography.CryptoStream.Dispose%2A> to not close the wrapped stream.</span></span> <span data-ttu-id="39b71-250"> <xref:System.Security.Cryptography.CryptoStream> のインスタンスが破棄された後でラップされたストリームを開いたままにするには、次のように新しい <xref:System.Security.Cryptography.CryptoStream> コンストラクターを作成します。</span><span class="sxs-lookup"><span data-stu-id="39b71-250">To leave the wrapped stream open after the <xref:System.Security.Cryptography.CryptoStream> instance is disposed, call the new <xref:System.Security.Cryptography.CryptoStream> constructor as follows:</span></span>

```csharp
var cStream = new CryptoStream(stream, transform, mode, leaveOpen: true);
```

```vb
Dim cStream = New CryptoStream(stream, transform, mode, leaveOpen:=true)
```

<span data-ttu-id="39b71-251">**DeflateStream の圧縮解除の変更**</span><span class="sxs-lookup"><span data-stu-id="39b71-251">**Decompression changes in DeflateStream**</span></span>

<span data-ttu-id="39b71-252">.NET Framework 4.7.2 以降では、<xref:System.IO.Compression.DeflateStream> クラスの圧縮解除操作の実装の際に、既定でネイティブの Windows API を使用するように変更されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-252">Starting with .NET Framework 4.7.2, the implementation of decompression operations in the <xref:System.IO.Compression.DeflateStream> class has changed to use native Windows APIs by default.</span></span> <span data-ttu-id="39b71-253">通常は、これによりパフォーマンスが大幅に改善されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-253">Typically, this results in a substantial performance improvement.</span></span>

<span data-ttu-id="39b71-254">Windows API を使用した圧縮解除のサポートは .NET Framework 4.7.2 を対象とするアプリケーションで既定で有効です。</span><span class="sxs-lookup"><span data-stu-id="39b71-254">Support for decompression by using Windows APIs is enabled by default for applications that target .NET Framework 4.7.2.</span></span> <span data-ttu-id="39b71-255">以前のバージョンの .NET Framework を対象とするアプリケーションが .NET Framework 4.7.2 未満で実行される場合は、次の [AppContext スイッチ](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md)をアプリケーション構成ファイルに追加することで、この動作を選択できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-255">Applications that target earlier versions of .NET Framework but are running under .NET Framework 4.7.2 can opt into this behavior by adding the following [AppContext switch](../configure-apps/file-schema/runtime/appcontextswitchoverrides-element.md) to the application configuration file:</span></span>

```xml
<AppContextSwitchOverrides value="Switch.System.IO.Compression.DoNotUseNativeZipLibraryForDecompression=false" />
```

<span data-ttu-id="39b71-256">**追加のコレクション API**</span><span class="sxs-lookup"><span data-stu-id="39b71-256">**Additional collection APIs**</span></span>

<span data-ttu-id="39b71-257">.NET Framework 4.7.2 でいくつかの新しい API が <xref:System.Collections.Generic.SortedSet%601> および <xref:System.Collections.Generic.HashSet%601> 型に追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-257">.NET Framework 4.7.2 adds a number of new APIs to the <xref:System.Collections.Generic.SortedSet%601> and <xref:System.Collections.Generic.HashSet%601> types.</span></span> <span data-ttu-id="39b71-258">次の設定があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-258">These include:</span></span>

- <span data-ttu-id="39b71-259">`TryGetValue` メソッドは、他のコレクション型で使用する try パターンを次の 2 つの型に拡張します。</span><span class="sxs-lookup"><span data-stu-id="39b71-259">`TryGetValue` methods, which extend the try pattern used in other collection types to these two types.</span></span> <span data-ttu-id="39b71-260">これらのメソッドを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="39b71-260">The methods are:</span></span>

  - [<span data-ttu-id="39b71-261">public bool HashSet\<T>.TryGetValue(T equalValue, out T actualValue)</span><span class="sxs-lookup"><span data-stu-id="39b71-261">public bool HashSet\<T>.TryGetValue(T equalValue, out T actualValue)</span></span>](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)
  - [<span data-ttu-id="39b71-262">public bool SortedSet\<T>.TryGetValue(T equalValue, out T actualValue)</span><span class="sxs-lookup"><span data-stu-id="39b71-262">public bool SortedSet\<T>.TryGetValue(T equalValue, out T actualValue)</span></span>](xref:System.Collections.Generic.SortedSet%601.TryGetValue%2A)

- <span data-ttu-id="39b71-263"><xref:System.Collections.Generic.HashSet%601> 拡張メソッドは、コレクションを `Enumerable.To*` に変換します。</span><span class="sxs-lookup"><span data-stu-id="39b71-263">`Enumerable.To*` extension methods, which convert a collection to a <xref:System.Collections.Generic.HashSet%601>:</span></span>

  - [<span data-ttu-id="39b71-264">public static HashSet\<TSource> ToHashSet\<TSource>(this IEnumerable\<TSource> source)</span><span class="sxs-lookup"><span data-stu-id="39b71-264">public static HashSet\<TSource> ToHashSet\<TSource>(this IEnumerable\<TSource> source)</span></span>](xref:System.Linq.Enumerable.ToHashSet%2A)
  - [<span data-ttu-id="39b71-265">public static HashSet\<TSource> ToHashSet\<TSource>(this IEnumerable\<TSource> source, IEqualityComparer\<TSource> comparer)</span><span class="sxs-lookup"><span data-stu-id="39b71-265">public static HashSet\<TSource> ToHashSet\<TSource>(this IEnumerable\<TSource> source, IEqualityComparer\<TSource> comparer)</span></span>](xref:System.Linq.Enumerable.ToHashSet%2A)

- <span data-ttu-id="39b71-266">新しい <xref:System.Collections.Generic.HashSet%601> コンストラクターを使用して、<xref:System.Collections.Generic.HashSet%601> のサイズが事前にわかっている場合に、コレクションの容量を設定できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-266">New <xref:System.Collections.Generic.HashSet%601> constructors that let you set the collection's capacity, which yields a performance benefit when you know the size of the <xref:System.Collections.Generic.HashSet%601> in advance:</span></span>

  - <span data-ttu-id="39b71-267">[public HashSet(int capacity)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))</span><span class="sxs-lookup"><span data-stu-id="39b71-267">[public HashSet(int capacity)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32))</span></span>
  - <span data-ttu-id="39b71-268">[public HashSet(int capacity, IEqualityComparer\<T> comparer)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))</span><span class="sxs-lookup"><span data-stu-id="39b71-268">[public HashSet(int capacity, IEqualityComparer\<T> comparer)](xref:System.Collections.Generic.HashSet%601.%23ctor(System.Int32,System.Collections.Generic.IEqualityComparer%7B%600%7D))</span></span>

<span data-ttu-id="39b71-269"><xref:System.Collections.Concurrent.ConcurrentDictionary%602> クラスには、<xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> および <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> メソッドの新しいオーバーロードが含まれています、これにより、ディクショナリから値を取得したり、またはそれが見つからない場合にそれを追加したり、値が既に存在する場合に、値をディクショナリに追加するか更新したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-269">The <xref:System.Collections.Concurrent.ConcurrentDictionary%602> class includes new overloads of the <xref:System.Collections.Concurrent.ConcurrentDictionary%602.AddOrUpdate%2A> and <xref:System.Collections.Concurrent.ConcurrentDictionary%602.GetOrAdd%2A> methods to retrieve a value from the dictionary or to add it if it is not found, and to add a value to the dictionary or to update it if it already exists.</span></span>

```csharp
public TValue AddOrUpdate<TArg>(TKey key, Func<TKey, TArg, TValue> addValueFactory, Func<TKey, TValue, TArg, TValue> updateValueFactory, TArg factoryArgument)

public TValue GetOrAdd<TArg>(TKey key, Func<TKey, TArg, TValue> valueFactory, TArg factoryArgument)
```

```vb
Public AddOrUpdate(Of TArg)(key As TKey, addValueFactory As Func(Of TKey, TArg, TValue), updateValueFactory As Func(Of TKey, TValue, TArg, TValue), factoryArgument As TArg) As TValue

Public GetOrAdd(Of TArg)(key As TKey, valueFactory As Func(Of TKey, TArg, TValue), factoryArgument As TArg) As TValue
```

<a name="asp-net472"></a>

#### <a name="aspnet"></a><span data-ttu-id="39b71-270">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="39b71-270">ASP.NET</span></span>

<span data-ttu-id="39b71-271">**Web フォームでの依存関係挿入のサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-271">**Support for dependency injection in Web Forms**</span></span>

<span data-ttu-id="39b71-272">[依存性挿入 (DI)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) は、オブジェクトとその依存関係を分離し、依存関係の変更だけを理由としてオブジェクトのコードを変更する必要がないようにします。</span><span class="sxs-lookup"><span data-stu-id="39b71-272">[Dependency injection (DI)](/aspnet/core/fundamentals/dependency-injection#overview-of-dependency-injection) decouples objects and their dependencies so that an object's code no longer needs to be changed just because a dependency has changed.</span></span> <span data-ttu-id="39b71-273">.NET Framework 4.7.2 を対象とする ASP.NET アプリケーションを開発するときに次のことができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-273">When developing ASP.NET applications that target .NET Framework 4.7.2, you can:</span></span>

- <span data-ttu-id="39b71-274">ASP.NET Web アプリケーション プロジェクトの[ハンドラーとモジュール](/previous-versions/aspnet/bb398986(v=vs.100))、[ページ インスタンス](xref:System.Web.UI.Page)、および[ユーザー コントロール](/previous-versions/aspnet/y6wb1a0e(v=vs.100))でアクセス操作子ベース、インターフェイス ベース、およびコンストラクター ベースの挿入を使用します。</span><span class="sxs-lookup"><span data-stu-id="39b71-274">Use setter-based, interface-based, and constructor-based injection in [handlers and modules](/previous-versions/aspnet/bb398986(v=vs.100)), [Page instances](xref:System.Web.UI.Page), and [user controls](/previous-versions/aspnet/y6wb1a0e(v=vs.100)) of ASP.NET web application projects.</span></span>

- <span data-ttu-id="39b71-275">ASP.NET Web サイト プロジェクトの[ハンドラーとモジュール](/previous-versions/aspnet/bb398986(v=vs.100))、[ページ インスタンス](xref:System.Web.UI.Page)、および[ユーザー コントロール](/previous-versions/aspnet/y6wb1a0e(v=vs.100))でアクセス操作子ベースおよびインターフェイス ベースの挿入を使用します。</span><span class="sxs-lookup"><span data-stu-id="39b71-275">Use setter-based and interface-based injection in [handlers and modules](/previous-versions/aspnet/bb398986(v=vs.100)), [Page instances](xref:System.Web.UI.Page), and [user controls](/previous-versions/aspnet/y6wb1a0e(v=vs.100)) of ASP.NET web site projects.</span></span>

- <span data-ttu-id="39b71-276">別の依存関係の挿入のフレームワークにプラグインします。</span><span class="sxs-lookup"><span data-stu-id="39b71-276">Plug in different dependency injection frameworks.</span></span>

<span data-ttu-id="39b71-277">**同じサイトの cookie のサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-277">**Support for same-site cookies**</span></span>

<span data-ttu-id="39b71-278">[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) は、ブラウザーがサイト間の要求と共に cookie を送信するのを防ぎます。</span><span class="sxs-lookup"><span data-stu-id="39b71-278">[SameSite](https://tools.ietf.org/html/draft-west-first-party-cookies-07) prevents a browser from sending a cookie along with a cross-site request.</span></span> <span data-ttu-id="39b71-279">.NET Framework 4.7.2 では、<xref:System.Web.SameSiteMode?displayProperty=nameWithType> 列挙型のメンバーの値を持つ <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> プロパティが追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-279">.NET Framework 4.7.2 adds a <xref:System.Web.HttpCookie.SameSite?displayProperty=nameWithType> property whose value is a <xref:System.Web.SameSiteMode?displayProperty=nameWithType> enumeration member.</span></span> <span data-ttu-id="39b71-280">値が <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> または <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType> の場合、ASP.NET は `SameSite` 属性を set-cookie ヘッダーに追加します。</span><span class="sxs-lookup"><span data-stu-id="39b71-280">If its value is <xref:System.Web.SameSiteMode.Strict?displayProperty=nameWithType> or <xref:System.Web.SameSiteMode.Lax?displayProperty=nameWithType>, ASP.NET adds the `SameSite` attribute to the set-cookie header.</span></span> <span data-ttu-id="39b71-281">SameSite のサポートは、<xref:System.Web.HttpCookie> オブジェクト、および <xref:System.Web.Security.FormsAuthentication> と <xref:System.Web.SessionState> cookie に適用されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-281">SameSite support applies to <xref:System.Web.HttpCookie> objects, as well as to <xref:System.Web.Security.FormsAuthentication> and <xref:System.Web.SessionState> cookies.</span></span>

<span data-ttu-id="39b71-282"><xref:System.Web.HttpCookie> オブジェクトの SameSite を次のように設定できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-282">You can set SameSite for an <xref:System.Web.HttpCookie> object as follows:</span></span>

```csharp
var c = new HttpCookie("secureCookie", "same origin");
c.SameSite = SameSiteMode.Lax;
```

```vb
Dim c As New HttpCookie("secureCookie", "same origin")
c.SameSite = SameSiteMode.Lax
```

<span data-ttu-id="39b71-283">Web.config ファイルを変更して、アプリケーション レベルで SameSite cookie を構成することもできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-283">You can also configure SameSite cookies at the application level by modifying the web.config file:</span></span>

```xml
<system.web>
   <httpCookies sameSite="Strict" />
</system.web>
```

<span data-ttu-id="39b71-284">web config ファイルを変更することによって、<xref:System.Web.Security.FormsAuthentication> および <xref:System.Web.SessionState> cookie の SameSite を追加することができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-284">You can add SameSite for <xref:System.Web.Security.FormsAuthentication> and <xref:System.Web.SessionState> cookies by modifying the web config file:</span></span>

```xml
<system.web>
   <authentication mode="Forms">
      <forms cookieSameSite="Lax">
         <!-- ...   -->
      </forms>
   </authentication>
   <sessionState cookieSameSite="Lax"></sessionState>
</system.web>
```

<a name="net472"></a>

#### <a name="networking"></a><span data-ttu-id="39b71-285">ネットワーキング</span><span class="sxs-lookup"><span data-stu-id="39b71-285">Networking</span></span>

<span data-ttu-id="39b71-286">**HttpClientHandler プロパティの実装**</span><span class="sxs-lookup"><span data-stu-id="39b71-286">**Implementation of HttpClientHandler properties**</span></span>

<span data-ttu-id="39b71-287">.NET Framework 4.7.1 で 8 個のプロパティが、<xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> クラスに追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-287">.NET Framework 4.7.1 added eight properties to the <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="39b71-288">ただし、2 つは <xref:System.PlatformNotSupportedException> をスローしていました。</span><span class="sxs-lookup"><span data-stu-id="39b71-288">However, two threw a <xref:System.PlatformNotSupportedException>.</span></span> <span data-ttu-id="39b71-289">.NET Framework 4.7.2 では、それらのプロパティの実装が提供されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-289">.NET Framework 4.7.2 now provides an implementation for these properties.</span></span> <span data-ttu-id="39b71-290">次のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="39b71-290">The properties are:</span></span>

- <xref:System.Net.Http.HttpClientHandler.CheckCertificateRevocationList>
- <xref:System.Net.Http.HttpClientHandler.SslProtocols>

<a name="sql472"></a>

#### <a name="sqlclient"></a><span data-ttu-id="39b71-291">SQLClient</span><span class="sxs-lookup"><span data-stu-id="39b71-291">SQLClient</span></span>

<span data-ttu-id="39b71-292">**Azure Active Directory のユニバーサル認証と多要素認証のサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-292">**Support for Azure Active Directory Universal Authentication and Multi-Factor authentication**</span></span>

<span data-ttu-id="39b71-293">コンプライアンスとセキュリティのニーズが高まったために、多くのお客様が多要素認証 (MFA) を使用しています。</span><span class="sxs-lookup"><span data-stu-id="39b71-293">Growing compliance and security demands require that many customers use multi-factor authentication (MFA).</span></span> <span data-ttu-id="39b71-294">さらに、現在のベスト プラクティスでは、接続文字列内に直接ユーザーのパスワードを含めることは推奨されません。</span><span class="sxs-lookup"><span data-stu-id="39b71-294">In addition, current best practices discourage including user passwords directly in connection strings.</span></span> <span data-ttu-id="39b71-295">これらの変更をサポートするため、.NET Framework 4.7.2 では [SQLClient 接続文字列](xref:System.Data.SqlClient.SqlConnection.ConnectionString)が拡張され、MFA および [Azure AD Authentication](/azure/sql-database/sql-database-aad-authentication-configure) をサポートするための既存の "Authentication" キーワードに新しい値 "Active Directory Interactive" が追加されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-295">To support these changes, .NET Framework 4.7.2 extends [SQLClient connection strings](xref:System.Data.SqlClient.SqlConnection.ConnectionString) by adding a new value, "Active Directory Interactive", for the existing "Authentication" keyword to support MFA and [Azure AD Authentication](/azure/sql-database/sql-database-aad-authentication-configure).</span></span> <span data-ttu-id="39b71-296">新しい対話型メソッドでは、ネイティブおよびフェデレーションの Azure AD ユーザーだけでなく Azure AD ゲスト ユーザーをサポートします。</span><span class="sxs-lookup"><span data-stu-id="39b71-296">The new interactive method supports native and federated Azure AD users as well as Azure AD guest users.</span></span> <span data-ttu-id="39b71-297">このメソッドを使用する場合は、Azure AD によって課される MFA 認証が SQL データベースに対してサポートされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-297">When this method is used, the MFA authentication imposed by Azure AD is supported for SQL databases.</span></span> <span data-ttu-id="39b71-298">さらに、認証プロセスは、セキュリティのベスト プラクティスに準拠するためにユーザーのパスワードを要求します。</span><span class="sxs-lookup"><span data-stu-id="39b71-298">In addition, the authentication process requests a user password to adhere to security best practices.</span></span>

<span data-ttu-id="39b71-299">以前のバージョンの .NET Framework では、SQL 接続は、<xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> と <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> のオプションのみがサポートされていました。</span><span class="sxs-lookup"><span data-stu-id="39b71-299">In previous versions of .NET Framework, SQL connectivity supported only the <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryPassword?displayProperty=nameWithType> and <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryIntegrated?displayProperty=nameWithType> options.</span></span> <span data-ttu-id="39b71-300">これらはどちらも非対話型の [ADAL プロトコル](/azure/active-directory/develop/active-directory-authentication-libraries) の一部で、MFA はサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="39b71-300">Both of these are part of the non-interactive [ADAL protocol](/azure/active-directory/develop/active-directory-authentication-libraries), which does not support MFA.</span></span> <span data-ttu-id="39b71-301">新しい <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> オプションを使用して、SQL 接続は MFA および既存の認証方法 (パスワードや統合認証) をサポートします。これにより、ユーザーが接続文字列でパスワードを永続化せずに、対話形式でパスワードを入力することができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-301">With the new <xref:System.Data.SqlClient.SqlAuthenticationMethod.ActiveDirectoryInteractive?displayProperty=nameWithType> option, SQL connectivity supports MFA as well as existing authentication methods (password and integrated authentication), which allows users to enter user passwords interactively without persisting passwords in the connection string.</span></span>

<span data-ttu-id="39b71-302">詳細および例については、[.NET ブログ](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/)の「SQL -- Azure AD Universal and Multi-factor Authentication Support」(SQL--Azure AD ユニバーサルおよび多要素認証のサポート) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-302">For more information and an example, see "SQL -- Azure AD Universal and Multi-factor Authentication Support" in the [.NET Blog](https://devblogs.microsoft.com/dotnet/net-framework-4-7-2-developer-pack-early-access-build-3056-is-available/).</span></span>

<span data-ttu-id="39b71-303">**Always Encrypted バージョン 2 のサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-303">**Support for Always Encrypted version 2**</span></span>

<span data-ttu-id="39b71-304">NET Framework 4.7.2 では、エンクレーブ ベースの Always Encrypted のサポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-304">NET Framework 4.7.2 adds supports for enclave-based Always Encrypted.</span></span> <span data-ttu-id="39b71-305">Always Encrypted の元のバージョンは、暗号化キーがクライアントから離れないクライアント側暗号化テクノロジです。</span><span class="sxs-lookup"><span data-stu-id="39b71-305">The original version of Always Encrypted is a client-side encryption technology in which encryption keys never leave the client.</span></span> <span data-ttu-id="39b71-306">エンクレーブ ベースの Always Encrypted では、クライアントが、オプションで暗号化キーをセキュアなエンクレーブに送信することができます。エンクレーブは、SQL Server の一部と見なされても SQL Server のコードを改ざんできないセキュアなコンピューティング エンティティです。</span><span class="sxs-lookup"><span data-stu-id="39b71-306">In enclave-based Always Encrypted, the client can optionally send the encryption keys to a secure enclave, which is a secure computational entity that can be considered part of SQL Server but that SQL Server code cannot tamper with.</span></span> <span data-ttu-id="39b71-307">エンクレーブ ベースの Always Encrypted をサポートするために、.NET Framework 4.7.2 では、次の型とメンバーが <xref:System.Data.SqlClient> 名前空間に追加されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-307">To support enclave-based Always Encrypted, .NET Framework 4.7.2 adds the following types and members to the <xref:System.Data.SqlClient> namespace:</span></span>

- <span data-ttu-id="39b71-308"><xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>。エンクレーブ ベースの Always Encrypted の URI を指定します。</span><span class="sxs-lookup"><span data-stu-id="39b71-308"><xref:System.Data.SqlClient.SqlConnectionStringBuilder.EnclaveAttestationUrl?displayProperty=nameWithType>, which specifies the Uri for enclave-based Always Encrypted.</span></span>

- <span data-ttu-id="39b71-309"><xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>。すべてのエンクレーブ プロバイダーの派生元の抽象クラスです。</span><span class="sxs-lookup"><span data-stu-id="39b71-309"><xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider>, which is an abstract class from which all enclave providers are derived.</span></span>

- <span data-ttu-id="39b71-310"><xref:System.Data.SqlClient.SqlEnclaveSession>。指定されたエンクレーブ セッションの状態をカプセル化します。</span><span class="sxs-lookup"><span data-stu-id="39b71-310"><xref:System.Data.SqlClient.SqlEnclaveSession>, which encapsulates the state for a given enclave session.</span></span>

- <span data-ttu-id="39b71-311"><xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>。SQL Server によって、特定の構成証明プロトコルを実行するために必要な情報を取得するために使用される構成証明パラメーター。</span><span class="sxs-lookup"><span data-stu-id="39b71-311"><xref:System.Data.SqlClient.SqlEnclaveAttestationParameters>, which provides the attestation parameters used by SQL Server to get information required to execute a particular Attestation Protocol.</span></span>

<span data-ttu-id="39b71-312">アプリケーション構成ファイルで、エンクレーブ プロバイダーの機能を提供する抽象 <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> クラスの完全な実装を指定します。</span><span class="sxs-lookup"><span data-stu-id="39b71-312">The application configuration file then specifies a concrete implementation of the abstract <xref:System.Data.SqlClient.SqlColumnEncryptionEnclaveProvider?displayProperty=nameWithType> class that provides the functionality for the enclave provider.</span></span> <span data-ttu-id="39b71-313">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="39b71-313">For example:</span></span>

```xml
<configuration>
  <configSections>
    <section name="SqlColumnEncryptionEnclaveProviders" type="System.Data.SqlClient.SqlColumnEncryptionEnclaveProviderConfigurationSection,System.Data,Version=4.0.0.0,Culture=neutral,PublicKeyToken=b77a5c561934e089"/>
  </configSections>
  <SqlColumnEncryptionEnclaveProviders>
    <providers>
      <add name="Azure" type="Microsoft.SqlServer.Management.AlwaysEncrypted.AzureEnclaveProvider,MyApp"/>
      <add name="HGS" type="Microsoft.SqlServer.Management.AlwaysEncrypted.HGSEnclaveProvider,MyApp" />
    </providers>
  </SqlColumnEncryptionEnclaveProviders >
</configuration>
```

<span data-ttu-id="39b71-314">エンクレーブ ベースの Always Encrypted の基本的な流れを示します。</span><span class="sxs-lookup"><span data-stu-id="39b71-314">The basic flow of enclave-based Always Encrypted is:</span></span>

1. <span data-ttu-id="39b71-315">ユーザーが、エンクレーブ ベースの Always Encrypted をサポートしていた SQL Server への AlwaysEncrypted 接続を作成します。</span><span class="sxs-lookup"><span data-stu-id="39b71-315">The user creates an AlwaysEncrypted connection to SQL Server that supported enclave-based Always Encrypted.</span></span> <span data-ttu-id="39b71-316">ドライバーが、構成証明サービスにアクセスし、正しいエンクレーブに接続されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="39b71-316">The driver contacts the attestation service to ensure that it is connecting to right enclave.</span></span>

1. <span data-ttu-id="39b71-317">エンクレーブが証明されると、ドライバーが、SQL Server でホストされているセキュリティで保護されたエンクレーブとのセキュリティで保護されたチャネルを確立します。</span><span class="sxs-lookup"><span data-stu-id="39b71-317">Once the enclave has been attested, the driver establishes a secure channel with the secure enclave hosted on SQL Server.</span></span>

1. <span data-ttu-id="39b71-318">ドライバーは、SQL 接続の間にセキュリティで保護されたエンクレーブとクライアントによって承認された暗号化キーを共有します。</span><span class="sxs-lookup"><span data-stu-id="39b71-318">The driver shares encryption keys authorized by the client with the secure enclave for the duration of the SQL connection.</span></span>

<a name="wpf472"></a>

#### <a name="windows-presentation-foundation"></a><span data-ttu-id="39b71-319">Windows Presentation Foundation</span><span class="sxs-lookup"><span data-stu-id="39b71-319">Windows Presentation Foundation</span></span>

<span data-ttu-id="39b71-320">**ソースによる ResourceDictionaries の検索**</span><span class="sxs-lookup"><span data-stu-id="39b71-320">**Finding ResourceDictionaries by Source**</span></span>

<span data-ttu-id="39b71-321">.NET Framework 4.7.2 以降、特定のソース URI から作成された <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> を診断アシスタントが検出できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-321">Starting with .NET Framework 4.7.2, a diagnostic assistant can locate the <xref:System.Windows.Xps.Packaging.IXpsFixedPageReader.ResourceDictionaries> that have been created from a given source Uri.</span></span> <span data-ttu-id="39b71-322"> (この機能は、実稼働アプリケーションではなく診断アシスタントによって使用されます)。Visual Studio の "エディット コンティニュ" 機能などの診断アシスタントでは、ユーザーが、実行中のアプリケーションに変更を適用する目的で ResourceDictionary を編集できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-322">(This feature is for use by diagnostic assistants, not by production applications.) A diagnostic assistant such as Visual Studio's "Edit-and-Continue" facility lets its user edit a ResourceDictionary with the intent that the changes be applied to the running application.</span></span> <span data-ttu-id="39b71-323">これを実現するための 1 つの手順は、実行中のアプリケーションが編集されているディクショナリから作成したすべての ResourceDictionaries を見つけることです。</span><span class="sxs-lookup"><span data-stu-id="39b71-323">One step in achieving this is finding all the ResourceDictionaries that the running application has created from the dictionary that's being edited.</span></span> <span data-ttu-id="39b71-324">たとえば、アプリケーションは、コンテンツが特定のソース URI からコピーされる ResourceDictionary を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-324">For example, an application can declare a ResourceDictionary whose content is copied from a given source URI:</span></span>

```xml
<ResourceDictionary Source="MyRD.xaml" />
```

<span data-ttu-id="39b71-325">*MyRD.xaml* の元のマークアップを編集する診断アシスタントは、ディクショナリを検索する新しい機能を使用できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-325">A diagnostic assistant that edits the original markup in *MyRD.xaml* can use the new feature to locate the dictionary.</span></span> <span data-ttu-id="39b71-326"> この機能は、新しい静的メソッド <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType> によって実装されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-326">The feature is implemented by a new static method, <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetResourceDictionariesForSource%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="39b71-327">診断のアシスタントは、次のコードに示すように、元のマークアップを識別する絶対 URI を使用して新しいメソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="39b71-327">The diagnostic assistant calls the new method using an absolute Uri that identifies the original markup, as illustrated by the following code:</span></span>

```csharp
IEnumerable<ResourceDictionary> dictionaries = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(new Uri("pack://application:,,,/MyApp;component/MyRD.xaml"));
```

```vb
Dim dictionaries As IEnumerable(Of ResourceDictionary) = ResourceDictionaryDiagnostics.GetResourceDictionariesForSource(New Uri("pack://application:,,,/MyApp;component/MyRD.xaml"))
```

<span data-ttu-id="39b71-328">このメソッドは、<xref:System.Windows.Diagnostics.VisualDiagnostics> が有効になっていて、[`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) 環境変数が設定されていない限り、空白の列挙を返します。</span><span class="sxs-lookup"><span data-stu-id="39b71-328">The method returns an empty enumerable unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

<span data-ttu-id="39b71-329">**ResourceDictionary 所有者の検索**</span><span class="sxs-lookup"><span data-stu-id="39b71-329">**Finding ResourceDictionary owners**</span></span>

<span data-ttu-id="39b71-330">.NET Framework 4.7.2 以降、診断アシスタントでは、特定の <xref:Windows.UI.Xaml.ResourceDictionary> の所有者を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-330">Starting with .NET Framework 4.7.2, a diagnostic assistant can locate the owners of a given <xref:Windows.UI.Xaml.ResourceDictionary>.</span></span> <span data-ttu-id="39b71-331"> (この機能は、実稼働アプリケーションではなく診断アシスタントによって使用されます。)<xref:Windows.UI.Xaml.ResourceDictionary> の変更が行われたときに、WPF が、変更の影響を受ける可能性があるすべての [DynamicResource](/dotnet/desktop/wpf/advanced/dynamicresource-markup-extension) の参照を自動的に見つけます。</span><span class="sxs-lookup"><span data-stu-id="39b71-331">(The feature is for use by diagnostic assistants and not by production applications.) Whenever a change is made to a <xref:Windows.UI.Xaml.ResourceDictionary>, WPF automatically finds all [DynamicResource](/dotnet/desktop/wpf/advanced/dynamicresource-markup-extension) references that might be affected by the change.</span></span>

<span data-ttu-id="39b71-332">Visual Studio の "エディット コンティニュ" 機能などの診断アシスタントでは、場合によっては [StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) 参照を処理するためにこれを拡張する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-332">A diagnostic assistant such as Visual Studio's "Edit-and-Continue" facility may want to extend this to handle [StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) references.</span></span> <span data-ttu-id="39b71-333">このプロセスの最初の手順は、ディクショナリの所有者を検索することです。つまり、`Resources` プロパティがディクショナリを (直接または <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> プロパティを使用して間接的に) 参照しているすべてのオブジェクトを見つけます。</span><span class="sxs-lookup"><span data-stu-id="39b71-333">The first step in this process is to find the owners of the dictionary; that is, to find all the objects whose `Resources` property refers to the dictionary (either directly, or indirectly via the <xref:System.Windows.ResourceDictionary.MergedDictionaries?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="39b71-334"><xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> クラスに実装された 3 つの新しい静的メソッドは、`Resources` プロパティを持つ各基本データ型ごとに 1 つずつあり、次の手順をサポートします。</span><span class="sxs-lookup"><span data-stu-id="39b71-334">Three new static methods implemented on the <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics?displayProperty=nameWithType> class, one for each of the base types that has a `Resources` property, support this step:</span></span>

- [`public static IEnumerable<FrameworkElement> GetFrameworkElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkElementOwners%2A)

- [`public static IEnumerable<FrameworkContentElement> GetFrameworkContentElementOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetFrameworkContentElementOwners%2A)

- [`public static IEnumerable<Application> GetApplicationOwners(ResourceDictionary dictionary);`](xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.GetApplicationOwners%2A)

<span data-ttu-id="39b71-335">これらのメソッドは、<xref:System.Windows.Diagnostics.VisualDiagnostics> が有効になっていて、[`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) 環境変数が設定されていない限り、空白の列挙を返します。</span><span class="sxs-lookup"><span data-stu-id="39b71-335">These methods return an empty enumerable unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

<span data-ttu-id="39b71-336">**StaticResource 参照の検索**</span><span class="sxs-lookup"><span data-stu-id="39b71-336">**Finding StaticResource references**</span></span>

<span data-ttu-id="39b71-337">診断アシスタントで、[StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) 参照が解決されるたびに通知を受け取ることができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-337">A diagnostic assistant can now receive a notification whenever a [StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) reference is resolved.</span></span> <span data-ttu-id="39b71-338"> (この機能は、実稼働アプリケーションではなく診断アシスタントによって使用されます。)Visual Studio の "エディット コンティニュ" 機能などの診断アシスタントは、場合によっては <xref:Windows.UI.Xaml.ResourceDictionary> の値が変更されたときにリソースのすべての使用を更新する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-338">(The feature is for use by diagnostic assistants, not by production applications.) A diagnostic assistant such as Visual Studio's "Edit-and-Continue" facility may want to update all uses of a resource when its value in a <xref:Windows.UI.Xaml.ResourceDictionary> changes.</span></span> <span data-ttu-id="39b71-339">WPF は、[DynamicResource](/dotnet/desktop/wpf/advanced/dynamicresource-markup-extension) 参照に関してこれを自動的に実行しますが、[StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) 参照に関しては意図的に実行しません。</span><span class="sxs-lookup"><span data-stu-id="39b71-339">WPF does this automatically for [DynamicResource](/dotnet/desktop/wpf/advanced/dynamicresource-markup-extension) references, but it intentionally does not do so for [StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) references.</span></span> <span data-ttu-id="39b71-340">.NET Framework 4.7.2 以降、診断アシスタントは、静的リソースのそれらの使用を検索するのにこれらの通知を使用できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-340">Starting with .NET Framework 4.7.2, the diagnostic assistant can use these notifications to locate those uses of the static resource.</span></span>

<span data-ttu-id="39b71-341">通知は、新しい <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> イベントによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-341">The notification is implemented by the new <xref:System.Windows.Diagnostics.ResourceDictionaryDiagnostics.StaticResourceResolved?displayProperty=nameWithType> event:</span></span>

```csharp
public static event EventHandler<StaticResourceResolvedEventArgs> StaticResourceResolved;
```

```vb
Public Shared Event StaticResourceResolved As EventHandler(Of StaticResourceResolvedEventArgs)
```

<span data-ttu-id="39b71-342">このイベントは、ランタイムが [StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) 参照を解決するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="39b71-342">This event is raised whenever the runtime resolves a [StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) reference.</span></span> <span data-ttu-id="39b71-343"><xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> 引数は、解決を記述し、[StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) 参照をホストするオブジェクトとプロパティ、および解決に使用される <xref:Windows.UI.Xaml.ResourceDictionary> とキーを示します。</span><span class="sxs-lookup"><span data-stu-id="39b71-343">The <xref:System.Windows.Diagnostics.StaticResourceResolvedEventArgs> arguments describe the resolution, and indicate the object and property that host the [StaticResource](/dotnet/desktop/wpf/advanced/staticresource-markup-extension) reference and the <xref:Windows.UI.Xaml.ResourceDictionary> and key used for the resolution:</span></span>

```csharp
public class StaticResourceResolvedEventArgs : EventArgs
{
   public Object TargetObject { get; }

   public Object TargetProperty { get; }

   public ResourceDictionary ResourceDictionary { get; }

   public object ResourceKey { get; }
}
```

```vb
Public Class StaticResourceResolvedEventArgs : Inherits EventArgs
   Public ReadOnly Property TargetObject As Object
   Public ReadOnly Property TargetProperty As Object
   Public ReadOnly Property ResourceDictionary As ResourceDictionary
   Public ReadOnly Property ResourceKey As Object
End Class
```

<span data-ttu-id="39b71-344"><xref:System.Windows.Diagnostics.VisualDiagnostics> が有効になっていて [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) 環境変数が設定されていない限り、イベントを発生しません (その `add` アクセサーは無視されます)。</span><span class="sxs-lookup"><span data-stu-id="39b71-344">The event is not raised (and its `add` accessor is ignored) unless <xref:System.Windows.Diagnostics.VisualDiagnostics> is enabled and the [`ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO`](xref:System.Windows.Diagnostics.VisualDiagnostics.GetXamlSourceInfo%2A) environment variable is set.</span></span>

#### <a name="clickonce"></a><span data-ttu-id="39b71-345">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="39b71-345">ClickOnce</span></span>

<span data-ttu-id="39b71-346">ClickOnce を使用して、Windows フォームの HDPI 対応アプリケーション、Windows Presentation Foundation (WPF)、および Visual Studio Tools for Office (VSTO) のすべてを配置できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-346">HDPI-aware applications for Windows Forms, Windows Presentation Foundation (WPF), and Visual Studio Tools for Office (VSTO) can all be deployed by using ClickOnce.</span></span> <span data-ttu-id="39b71-347">次のエントリがアプリケーション マニフェストに見つかった場合、.NET Framework 4.7.2 で展開が成功します。</span><span class="sxs-lookup"><span data-stu-id="39b71-347">If the following entry is found in the application manifest, deployment will succeed under .NET Framework 4.7.2:</span></span>

```xml
<windowsSettings>
   <dpiAware xmlns="http://schemas.microsoft.com/SMI/2005/WindowsSettings">true</dpiAware>
</windowsSettings>
```

<span data-ttu-id="39b71-348">Windows フォーム アプリケーションの場合、DPI 認識をアプリケーション マニフェストではなくアプリケーション構成ファイルで設定するという以前の回避策は、ClickOnce 展開を成功させるために必要ではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-348">For Windows Forms application, the previous workaround of setting DPI awareness in the application configuration file rather than the application manifest is no longer necessary for ClickOnce deployment to succeed.</span></span>

<a name="v471"></a>

## <a name="whats-new-in-net-framework-471"></a><span data-ttu-id="39b71-349">.NET Framework 4.7.1 の新機能</span><span class="sxs-lookup"><span data-stu-id="39b71-349">What's new in .NET Framework 4.7.1</span></span>

<span data-ttu-id="39b71-350">.NET Framework 4.7.1 には、次の領域における新機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="39b71-350">.NET Framework 4.7.1 includes new features in the following areas:</span></span>

- [<span data-ttu-id="39b71-351">基底クラス</span><span class="sxs-lookup"><span data-stu-id="39b71-351">Base classes</span></span>](#core471)
- [<span data-ttu-id="39b71-352">共通言語ランタイム (CLR)</span><span class="sxs-lookup"><span data-stu-id="39b71-352">Common language runtime (CLR)</span></span>](#clr)
- [<span data-ttu-id="39b71-353">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="39b71-353">Networking</span></span>](#net471)
- [<span data-ttu-id="39b71-354">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="39b71-354">ASP.NET</span></span>](#asp-net471)

<span data-ttu-id="39b71-355">さらに、.NET Framework 4.7.1 ではアクセシビリティ機能の向上が重視されており、それによりアプリケーションでは支援技術のユーザーに適切なエクスペリエンスを提供できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-355">In addition, a major focus in .NET Framework 4.7.1 is improved accessibility, which allows an application to provide an appropriate experience for users of Assistive Technology.</span></span> <span data-ttu-id="39b71-356">.NET Framework 4.7.1 でのアクセシビリティ機能の改善について詳しくは、「[.NET Framework のアクセシビリティの新機能](whats-new-in-accessibility.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-356">For information on accessibility improvements in .NET Framework 4.7.1, see [What's new in accessibility in .NET Framework](whats-new-in-accessibility.md).</span></span>

<a name="core471"></a>

#### <a name="base-classes"></a><span data-ttu-id="39b71-357">基底クラス</span><span class="sxs-lookup"><span data-stu-id="39b71-357">Base classes</span></span>

<span data-ttu-id="39b71-358">**.NET Standard 2.0 のサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-358">**Support for .NET Standard 2.0**</span></span>

<span data-ttu-id="39b71-359">[.NET Standard](../../standard/net-standard.md) は、そのバージョンの標準をサポートする各 .NET 実装で使用する必要がある API のセットを定義します。</span><span class="sxs-lookup"><span data-stu-id="39b71-359">[.NET Standard](../../standard/net-standard.md) defines a set of APIs that must be available on each .NET implementation that supports that version of the standard.</span></span> <span data-ttu-id="39b71-360">.NET Framework 4.7.1 では、.NET Standard 2.0 が完全にサポートされており、.NET Standard 2.0 で定義されていて .NET Framework 4.6.1、4.6.2、および 4.7 にはなかった[約 200 の API](https://github.com/dotnet/standard/blob/master/src/netstandard/src/ApiCompatBaseline.net461.txt) が追加されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-360">.NET Framework 4.7.1 fully supports .NET Standard 2.0 and adds [about 200 APIs](https://github.com/dotnet/standard/blob/master/src/netstandard/src/ApiCompatBaseline.net461.txt) that are defined in .NET Standard 2.0 and are missing from .NET Framework 4.6.1, 4.6.2, and 4.7.</span></span> <span data-ttu-id="39b71-361">(これらのバージョンの .NET Framework では、.NET Standard の追加のサポート ファイルもターゲット システムに展開されている場合のみ .NET Standard 2.0 をサポートします)。詳細については、「[.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/)」(.NET Framework 4.7.1 ランタイムとコンパイラの機能) ブログ投稿の「BCL - .NET Standard 2.0 Support」(BCL - .NET Standard 2.0 のサポート) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-361">(Note that these versions of .NET Framework support .NET Standard 2.0 only if additional .NET Standard support files are also deployed on the target system.) For more information, see "BCL - .NET Standard 2.0 Support" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<span data-ttu-id="39b71-362">**構成ビルダーのサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-362">**Support for configuration builders**</span></span>

<span data-ttu-id="39b71-363">構成ビルダーを使用して、開発者が、実行時にアプリケーションの構成設定を動的に注入およびビルドすることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-363">Configuration builders allow developers to inject and build configuration settings for applications dynamically at run time.</span></span> <span data-ttu-id="39b71-364">カスタム構成ビルダーを使用して、構成セクションの既存のデータを変更したり、最初から完全に構成セクション全体をビルドしたりすることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-364">Custom configuration builders can be used to modify existing data in a configuration section or to build a configuration section entirely from scratch.</span></span> <span data-ttu-id="39b71-365">構成ビルダーを使用しない場合は、構成ファイルは静的であり、それらの設定はアプリケーションが起動されるしばらく前に定義されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-365">Without configuration builders, .config files are static, and their settings are defined some time before an application is launched.</span></span>

<span data-ttu-id="39b71-366">カスタム構成ビルダーを作成するには、抽象 <xref:System.Configuration.ConfigurationBuilder> クラスからビルダーを派生させ、その <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> と <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType> をオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="39b71-366">To create a custom configuration builder, you derive your builder from the abstract <xref:System.Configuration.ConfigurationBuilder> class and override its <xref:System.Configuration.ConfigurationBuilder.ProcessConfigurationSection%2A?displayProperty=nameWithType> and <xref:System.Configuration.ConfigurationBuilder.ProcessRawXml%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="39b71-367">また、.config ファイルでもビルダーを定義します。</span><span class="sxs-lookup"><span data-stu-id="39b71-367">You also define your builders in your .config file.</span></span> <span data-ttu-id="39b71-368">詳細については、「[.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) 」(.NET Framework 4.7.1 ASP.NET と構成機能) ブログ投稿の「Configuration Builders」(構成ビルダー) セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-368">For more information, see the "Configuration Builders" section in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="39b71-369">**実行時の機能の検出**</span><span class="sxs-lookup"><span data-stu-id="39b71-369">**Run-time feature detection**</span></span>

<span data-ttu-id="39b71-370"><xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> クラスは、コンパイル時または実行時に特定の .NET の実装上で事前に定義された機能がサポートされているかどうかを判断するためのメカニズムを提供します。</span><span class="sxs-lookup"><span data-stu-id="39b71-370">The <xref:System.Runtime.CompilerServices.RuntimeFeature?displayProperty=nameWithType> class provides a mechanism for determine whether a predefined feature is supported on a given .NET implementation at compile time or run time.</span></span> <span data-ttu-id="39b71-371">コンパイラは、コンパイル時に、指定されたフィールドが存在するかどうかを確認し、その機能がサポートされているかどうかを判断します。サポートされている場合は、その機能を利用するコードを生成できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-371">At compile time, a compiler can check whether a specified field exists to determine whether the feature is supported; if so, it can emit code that takes advantage of that feature.</span></span> <span data-ttu-id="39b71-372">実行時に、アプリケーションは、コードを生成する前に <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-372">At run time, an application can call the <xref:System.Runtime.CompilerServices.RuntimeFeature.IsSupported%2A?displayProperty=nameWithType> method before emitting code at runtime.</span></span> <span data-ttu-id="39b71-373">詳細については、「[Add helper method to describe features supported by the runtime](https://github.com/dotnet/corefx/issues/17116)」(ランタイムでサポートされる機能を記述するヘルパー メソッドを追加する) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-373">For more information, see [Add helper method to describe features supported by the runtime](https://github.com/dotnet/corefx/issues/17116).</span></span>

<span data-ttu-id="39b71-374">**値のタプル型はシリアル化できる**</span><span class="sxs-lookup"><span data-stu-id="39b71-374">**Value tuple types are serializable**</span></span>

<span data-ttu-id="39b71-375">.NET Framework 4.7.1 以降、<xref:System.ValueTuple?displayProperty=nameWithType> および関連するジェネリック型は、[Serializable](xref:System.SerializableAttribute) としてマークされ、バイナリのシリアル化ができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-375">Starting with .NET Framework 4.7.1, <xref:System.ValueTuple?displayProperty=nameWithType> and its associated generic types are marked as [Serializable](xref:System.SerializableAttribute), which allows binary serialization.</span></span> <span data-ttu-id="39b71-376">これにより、<xref:System.Tuple%603> や <xref:System.Tuple%604> などのタプル型を簡単に値のタプル型に移行できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-376">This should make migrating Tuple types, such as <xref:System.Tuple%603> and <xref:System.Tuple%604>, to value tuple types easier.</span></span> <span data-ttu-id="39b71-377">詳細については、「[.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/)」(.NET Framework 4.7.1 ランタイムとコンパイラの機能) ブログ投稿の「Compiler -- ValueTuple is Serializable」(コンパイラ -- 値タプルはシリアル化できる) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-377">For more information, see "Compiler -- ValueTuple is Serializable" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<span data-ttu-id="39b71-378">**読み取り専用の参照のサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-378">**Support for read-only references**</span></span>

<span data-ttu-id="39b71-379">.NET Framework 4.7.1 では、<xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType> が追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-379">.NET Framework 4.7.1 adds the <xref:System.Runtime.CompilerServices.IsReadOnlyAttribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="39b71-380">この属性は、読み取り専用の ref 戻り値型またはパラメーターを持つメンバーをマークする言語コンパイラで使用します。</span><span class="sxs-lookup"><span data-stu-id="39b71-380">This attribute is used by language compilers to mark members that have read-only ref return types or parameters.</span></span> <span data-ttu-id="39b71-381">詳細については、「[.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/)」(.NET Framework 4.7.1 ランタイムとコンパイラの機能) ブログ投稿の「Compiler - Support for ReadOnlyReferences」(コンパイラ - ReadOnlyReferences のサポート) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-381">For more information, see "Compiler -- Support for ReadOnlyReferences" in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span> <span data-ttu-id="39b71-382">参照戻り値の詳細については、[参照戻り値と参照ローカル変数 (C# Guide)](../../csharp/programming-guide/classes-and-structs/ref-returns.md)および[参照戻り値 (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-382">For information on ref return values, see [Ref return values and ref locals (C# Guide)](../../csharp/programming-guide/classes-and-structs/ref-returns.md) and [Ref return values (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/ref-return-values.md).</span></span>

<a name="clr"></a>

#### <a name="common-language-runtime-clr"></a><span data-ttu-id="39b71-383">共通言語ランタイム (CLR)</span><span class="sxs-lookup"><span data-stu-id="39b71-383">Common language runtime (CLR)</span></span>

<span data-ttu-id="39b71-384">**ガベージ コレクションのパフォーマンス改善**</span><span class="sxs-lookup"><span data-stu-id="39b71-384">**Garbage collection performance improvements**</span></span>

<span data-ttu-id="39b71-385">.NET Framework 4.7.1 でのガベージ コレクション (GC) に対する変更により、特に大きなオブジェクト ヒープ (LOH) の割り当ての場合に全体的なパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="39b71-385">Changes to garbage collection (GC) in .NET Framework 4.7.1 improve overall performance, especially for large object heap (LOH) allocations.</span></span> <span data-ttu-id="39b71-386">.NET Framework 4.7.1 では、小さなオブジェクト ヒープ (SOH) と LOH の割り当てに個別のロックが使用されます。これにより、バックグラウンド GC で SOH をスイープするときに、LOH を割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-386">In .NET Framework 4.7.1, separate locks are used for small object heap (SOH) and LOH allocations, which allows LOH allocations to occur when background GC is sweeping the SOH.</span></span> <span data-ttu-id="39b71-387">その結果、多数の LOH の割り当てを行うアプリケーションでは、割り当てのロックの競合が減少し、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="39b71-387">As a result, applications that make a large number of LOH allocations should see a reduction in allocation lock contention and improved performance.</span></span> <span data-ttu-id="39b71-388">詳細については、「[.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/)」(.NET Framework 4.7.1 ランタイムとコンパイラの機能) ブログ投稿の「Runtime -- GC Performance Improvements」(ランタイム - GC のパフォーマンスの向上) セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-388">For more information, see the "Runtime -- GC Performance Improvements" section in the [.NET Framework 4.7.1 Runtime and Compiler Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-runtime-and-compiler-features/) blog post.</span></span>

<a name="net471"/>

#### <a name="networking"></a><span data-ttu-id="39b71-389">ネットワーキング</span><span class="sxs-lookup"><span data-stu-id="39b71-389">Networking</span></span>

<span data-ttu-id="39b71-390">**Message.HashAlgorithm 用の SHA-2 のサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-390">**SHA-2 support for Message.HashAlgorithm**</span></span>

<span data-ttu-id="39b71-391">.NET Framework 4.7 およびそれ以前のバージョンの <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> プロパティでは、値 <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> および <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> のみがサポートされていました。</span><span class="sxs-lookup"><span data-stu-id="39b71-391">In .NET Framework 4.7 and earlier versions, the <xref:System.Messaging.Message.HashAlgorithm%2A?displayProperty=nameWithType> property supported values of <xref:System.Messaging.HashAlgorithm.Md5?displayProperty=nameWithType> and <xref:System.Messaging.HashAlgorithm.Sha?displayProperty=nameWithType> only.</span></span> <span data-ttu-id="39b71-392">.NET Framework 4.7.1 以降では、<xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>、<xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>、<xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> もサポートされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-392">Starting with .NET Framework 4.7.1, <xref:System.Messaging.HashAlgorithm.Sha256?displayProperty=nameWithType>, <xref:System.Messaging.HashAlgorithm.Sha384?displayProperty=nameWithType>, and <xref:System.Messaging.HashAlgorithm.Sha512?displayProperty=nameWithType> are also supported.</span></span> <span data-ttu-id="39b71-393"><xref:System.Messaging.Message> インスタンス自体は、ハッシュは行わず、MSMQ に値を渡すだけですなので、この値が実際に使用されるかどうかは MSMQ によって異なります。</span><span class="sxs-lookup"><span data-stu-id="39b71-393">Whether this value is actually used depends on MSMQ, since the <xref:System.Messaging.Message> instance itself does no hashing but simply passes on values to MSMQ.</span></span> <span data-ttu-id="39b71-394">詳細については、「[.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) 」(.NET Framework 4.7.1 ASP.NET と構成機能) ブログ投稿の「SHA-2 support for Message.HashAlgorithm」(Message.HashAlgorithm 用の SHA-2 のサポート) セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-394">For more information, see the "SHA-2 support for Message.HashAlgorithm" section in the [.NET Framework 4.7.1 ASP.NET and Configuration features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<a name="asp-net471"></a>

#### <a name="aspnet"></a><span data-ttu-id="39b71-395">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="39b71-395">ASP.NET</span></span>

<span data-ttu-id="39b71-396">**ASP.NET アプリケーションの実行ステップ**</span><span class="sxs-lookup"><span data-stu-id="39b71-396">**Execution steps in ASP.NET applications**</span></span>

<span data-ttu-id="39b71-397">ASP.NET は、23 のイベントを含む定義済みのパイプラインで要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="39b71-397">ASP.NET processes requests in a predefined pipeline that includes 23 events.</span></span> <span data-ttu-id="39b71-398">ASP.NET は、実行ステップとして、各イベント ハンドラーを実行します。</span><span class="sxs-lookup"><span data-stu-id="39b71-398">ASP.NET executes each event handler as an execution step.</span></span> <span data-ttu-id="39b71-399">.NET Framework 4.7 までの ASP.NET のバージョンでは、ASP.NET は、ネイティブ スレッドとマネージド スレッドの切り替えのために、実行コンテキストをフローすることはできません。</span><span class="sxs-lookup"><span data-stu-id="39b71-399">In versions of ASP.NET up to .NET Framework 4.7, ASP.NET can't flow the execution context due to switching between native and managed threads.</span></span> <span data-ttu-id="39b71-400">代わりに、ASP.NET は、<xref:System.Web.HttpContext> のみを選択的にフローします。</span><span class="sxs-lookup"><span data-stu-id="39b71-400">Instead, ASP.NET selectively flows only the <xref:System.Web.HttpContext>.</span></span> <span data-ttu-id="39b71-401">.NET Framework 4.7.1 以降、<xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> メソッドでは、モジュールがアンビエント データを復元することもできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-401">Starting with .NET Framework 4.7.1, the <xref:System.Web.HttpApplication.OnExecuteRequestStep(System.Action{System.Web.HttpContextBase,System.Action})?displayProperty=nameWithType> method also allows modules to restore ambient data.</span></span> <span data-ttu-id="39b71-402">この機能は、アプリケーションの実行フローを考慮する、トレース、プロファイリング、診断、トランザクションなどに関連するライブラリを対象とします。</span><span class="sxs-lookup"><span data-stu-id="39b71-402">This feature is targeted at libraries concerned with tracing, profiling, diagnostics, or transactions, for example, that care about the execution flow of the application.</span></span> <span data-ttu-id="39b71-403">詳細については、「[.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) 」(.NET Framework 4.7.1 ASP.NET と構成機能) ブログ投稿の「ASP.NET Execution Step Feature」(ASP.NET 実行ステップの機能) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-403">For more information, see the "ASP.NET Execution Step Feature" in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="39b71-404">**ASP.NET HttpCookie 解析**</span><span class="sxs-lookup"><span data-stu-id="39b71-404">**ASP.NET HttpCookie parsing**</span></span>

<span data-ttu-id="39b71-405">.NET Framework 4.7.1 には、新しいメソッド <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType> が含まれています。これは、文字列から <xref:System.Web.HttpCookie> オブジェクトを作成し、有効期限日やパスなどの cookie の値を正確に割り当てるための標準化された方法を提供します。</span><span class="sxs-lookup"><span data-stu-id="39b71-405">.NET Framework 4.7.1 includes a new method, <xref:System.Web.HttpCookie.TryParse%2A?displayProperty=nameWithType>, that provides a standardized way to create an <xref:System.Web.HttpCookie> object from a string and accurately assign cookie values such as expiration date and path.</span></span> <span data-ttu-id="39b71-406">詳細については、「[.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) 」(.NET Framework 4.7.1 ASP.NET と構成機能) ブログ投稿の「ASP.NET HttpCookie parsing」(ASP.NET HttpCookie の解析) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-406">For more information, see "ASP.NET HttpCookie parsing" in the [.NET Framework 4.7.1 ASP.NET and Configuration Features](https://devblogs.microsoft.com/dotnet/net-framework-4-7-1-asp-net-and-configuration-features/) blog post.</span></span>

<span data-ttu-id="39b71-407">**ASP.NET フォーム認証資格情報の SHA-2 ハッシュ オプション**</span><span class="sxs-lookup"><span data-stu-id="39b71-407">**SHA-2 hash options for ASP.NET forms authentication credentials**</span></span>

<span data-ttu-id="39b71-408">.NET Framework 4.7 およびそれ以前のバージョンの ASP.NET では、開発者は、MD5 または SHA1 を使用して、ユーザーの資格情報とハッシュされたパスワードを構成ファイルに格納できました。</span><span class="sxs-lookup"><span data-stu-id="39b71-408">In .NET Framework 4.7 and earlier versions, ASP.NET allowed developers to store user credentials with hashed passwords in configuration files using either MD5 or SHA1.</span></span> <span data-ttu-id="39b71-409">.NET Framework 4.7.1 以降の ASP.NET では、SHA256、SHA384、SHA512 などの新しい安全な SHA-2 ハッシュ オプションもサポートされるようになっています。</span><span class="sxs-lookup"><span data-stu-id="39b71-409">Starting with .NET Framework 4.7.1, ASP.NET also supports new secure SHA-2 hash options such as SHA256, SHA384, and SHA512.</span></span> <span data-ttu-id="39b71-410">SHA1 は既定のまま残り、Web 構成ファイルで既定以外のハッシュ アルゴリズムを定義することができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-410">SHA1 remains the default, and a non-default hash algorithm can be defined in the web configuration file.</span></span> <span data-ttu-id="39b71-411">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="39b71-411">For example:</span></span>

```xml
<system.web>
    <authentication mode="Forms">
        <forms loginUrl="~/login.aspx">
          <credentials passwordFormat="SHA512">
            <user name="jdoe" password="6D003E98EA1C7F04ABF8FCB375388907B7F3EE06F278DB966BE960E7CBBD103DF30CA6D61F7E7FD981B2E4E3A64D43C836A4BEDCA165C33B163E6BCDC538A664" />
          </credentials>
        </forms>
    </authentication>
</system.web>
```

<a name="v47"></a>

## <a name="whats-new-in-net-framework-47"></a><span data-ttu-id="39b71-412">.NET Framework 4.7 の新機能</span><span class="sxs-lookup"><span data-stu-id="39b71-412">What's new in .NET Framework 4.7</span></span>

<span data-ttu-id="39b71-413">.NET Framework 4.7 には、次の領域における新機能が含まれています。</span><span class="sxs-lookup"><span data-stu-id="39b71-413">.NET Framework 4.7 includes new features in the following areas:</span></span>

- [<span data-ttu-id="39b71-414">基底クラス</span><span class="sxs-lookup"><span data-stu-id="39b71-414">Base classes</span></span>](#Core47)
- [<span data-ttu-id="39b71-415">ネットワーク</span><span class="sxs-lookup"><span data-stu-id="39b71-415">Networking</span></span>](#net47)
- [<span data-ttu-id="39b71-416">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="39b71-416">ASP.NET</span></span>](#ASP-NET47)
- [<span data-ttu-id="39b71-417">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="39b71-417">Windows Communication Foundation (WCF)</span></span>](#wcf47)
- [<span data-ttu-id="39b71-418">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="39b71-418">Windows Forms</span></span>](#wf47)
- [<span data-ttu-id="39b71-419">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="39b71-419">Windows Presentation Foundation (WPF)</span></span>](#WPF47)

<span data-ttu-id="39b71-420">.NET Framework 4.7 に追加された新しい API の一覧については、GitHub で [.NET Framework 4.7 API の変更点](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md)に関するページをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-420">For a list of new APIs added to .NET Framework 4.7, see [.NET Framework 4.7 API Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-api-changes.md) on GitHub.</span></span> <span data-ttu-id="39b71-421">.NET Framework 4.7 における機能の改善とバグ修正の一覧については、GitHub で「[.NET Framework 4.7 List of Changes (.NET Framework 4.7 の変更点の一覧)](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-421">For a list of feature improvements and bug fixes in .NET Framework 4.7, see [.NET Framework 4.7 List of Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net47/dotnet47-changes.md) on GitHub.</span></span> <span data-ttu-id="39b71-422">詳細については、.NET のブログの [.NET Framework 4.7 の発表](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-422">For more information, see [Announcing .NET Framework 4.7](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-7/) in the .NET blog.</span></span>

<a name="Core47"></a>

#### <a name="base-classes"></a><span data-ttu-id="39b71-423">基底クラス</span><span class="sxs-lookup"><span data-stu-id="39b71-423">Base classes</span></span>

<span data-ttu-id="39b71-424">.NET Framework 4.7 では、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> によるシリアル化が改善されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-424">.NET Framework 4.7 improves serialization by the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:</span></span>

<span data-ttu-id="39b71-425">**楕円曲線暗号 (ECC) による機能強化** _</span><span class="sxs-lookup"><span data-stu-id="39b71-425">**Enhanced functionality with Elliptic Curve Cryptography (ECC)** _</span></span>

<span data-ttu-id="39b71-426">.NET Framework 4.7 では、`ImportParameters(ECParameters)` メソッドが <xref:System.Security.Cryptography.ECDsa> クラスと <xref:System.Security.Cryptography.ECDiffieHellman> クラスに追加され、既に確立されたキーをオブジェクトで表すことができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-426">In .NET Framework 4.7, `ImportParameters(ECParameters)` methods were added to the <xref:System.Security.Cryptography.ECDsa> and <xref:System.Security.Cryptography.ECDiffieHellman> classes to allow for an object to represent an already-established key.</span></span> <span data-ttu-id="39b71-427">明示的な曲線パラメーターを使ってキーをエクスポートするための `ExportParameters(Boolean)` メソッドも追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-427">An `ExportParameters(Boolean)` method was also added for exporting the key using explicit curve parameters.</span></span>

<span data-ttu-id="39b71-428">また、.NET Framework 4.7 では、その他の曲線 (Brainpool 曲線スイートなど) のサポートと、新しい <xref:System.Security.Cryptography.ECDsa.Create%2A> および <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> ファクトリ メソッドによる作成しやすい事前定義も追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-428">.NET Framework 4.7 also adds support for additional curves (including the Brainpool curve suite), and has added predefined definitions for ease-of-creation through the new <xref:System.Security.Cryptography.ECDsa.Create%2A> and <xref:System.Security.Cryptography.ECDiffieHellman.Create%2A> factory methods.</span></span>

<span data-ttu-id="39b71-429">GitHub で [.NET Framework 4.7 の暗号化の向上の例](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e)を見ることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-429">You can see an [example of .NET Framework 4.7 cryptography improvements](https://gist.github.com/richlander/5a182899895a87a296c21ada97f7a54e) on GitHub.</span></span>

<span data-ttu-id="39b71-430">_ *DataContractJsonSerializer による制御文字のサポートの向上*\*</span><span class="sxs-lookup"><span data-stu-id="39b71-430">_ *Better support for control characters by the DataContractJsonSerializer*\*</span></span>

<span data-ttu-id="39b71-431">.NET Framework 4.7 の <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> クラスでは、ECMAScript 6 標準に準拠して制御文字がシリアル化されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-431">In .NET Framework 4.7, the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> class serializes control characters in conformity with the ECMAScript 6 standard.</span></span> <span data-ttu-id="39b71-432">この動作は、.NET Framework 4.7 を対象とするアプリケーションでは既定で有効になり、.NET Framework 4.7 で実行していても対象が以前のバージョンの .NET Framework であるアプリケーションの場合はオプトイン機能です。</span><span class="sxs-lookup"><span data-stu-id="39b71-432">This behavior is enabled by default for applications that target .NET Framework 4.7, and is an opt-in feature for applications that are running under .NET Framework 4.7 but target a previous version of .NET Framework.</span></span> <span data-ttu-id="39b71-433">詳細については、「[アプリケーションの互換性](../migration-guide/application-compatibility.md)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-433">For more information, see the [Application compatibility](../migration-guide/application-compatibility.md) section.</span></span>

<a name="net47"></a>

#### <a name="networking"></a><span data-ttu-id="39b71-434">ネットワーキング</span><span class="sxs-lookup"><span data-stu-id="39b71-434">Networking</span></span>

<span data-ttu-id="39b71-435">.NET Framework 4.7 では、次のネットワーク関連機能が追加されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-435">.NET Framework 4.7 adds the following network-related feature:</span></span>

<span data-ttu-id="39b71-436">**TLS プロトコルの既定のオペレーティング システム サポート** _</span><span class="sxs-lookup"><span data-stu-id="39b71-436">**Default operating system support for TLS protocols** _</span></span>

<span data-ttu-id="39b71-437"><xref:System.Net.Security.SslStream?displayProperty=nameWithType> および HTTP、FTP、SMTP などの上位スタック コンポーネントによって使われる TLS スタックにより、開発者はオペレーティング システムによってサポートされる既定の TLS プロトコルを使うことができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-437">The TLS stack, which is used by <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and up-stack components such as HTTP, FTP, and SMTP, allows developers to use the default TLS protocols supported by the operating system.</span></span> <span data-ttu-id="39b71-438">TLS バージョンをハード コーディングする必要はなくなりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-438">Developers need no longer hard-code a TLS version.</span></span>

<a name="ASP-NET47"></a>

#### <a name="aspnet"></a><span data-ttu-id="39b71-439">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="39b71-439">ASP.NET</span></span>

<span data-ttu-id="39b71-440">.NET Framework 4.7 の ASP.NET には、次の新機能が含まれます。</span><span class="sxs-lookup"><span data-stu-id="39b71-440">In .NET Framework 4.7, ASP.NET includes the following new features:</span></span>

<span data-ttu-id="39b71-441">_ *オブジェクト キャッシュの拡張性*\*</span><span class="sxs-lookup"><span data-stu-id="39b71-441">_ *Object Cache Extensibility*\*</span></span>

<span data-ttu-id="39b71-442">.NET Framework 4.7 以降では、ASP.NET で追加された新しい API セットを使うことで、開発者は、メモリ内オブジェクト キャッシュとメモリ監視に関する既定の ASP.NET の実装を置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-442">Starting with .NET Framework 4.7, ASP.NET adds a new set of APIs that allow developers to replace the default ASP.NET implementations for in-memory object caching and memory monitoring.</span></span> <span data-ttu-id="39b71-443">ASP.NET の実装が適切ではない場合、次の 3 つのコンポーネントを置き換えることができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-443">Developers can now replace any of the following three components if the ASP.NET implementation is not adequate:</span></span>

- <span data-ttu-id="39b71-444">**オブジェクト キャッシュ ストア** 。</span><span class="sxs-lookup"><span data-stu-id="39b71-444">**Object Cache Store** .</span></span> <span data-ttu-id="39b71-445">新しいキャッシュ プロバイダー構成セクションを使うことで、開発者は、新しい **ICacheStoreProvider** インターフェイスを使って、ASP.NET アプリケーション用のオブジェクト キャッシュの新しい実装をプラグインできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-445">By using the new cache providers configuration section, developers can plug in new implementations of an object cache for an ASP.NET application by using the new **ICacheStoreProvider** interface.</span></span>

- <span data-ttu-id="39b71-446">**メモリ監視** 。</span><span class="sxs-lookup"><span data-stu-id="39b71-446">**Memory monitoring** .</span></span> <span data-ttu-id="39b71-447">ASP.NET の既定のメモリ モニターは、アプリケーションがプロセスに構成されているプライベート バイト制限に近づくと、またはコンピューターの使用可能な合計物理 RAM が低下すると、アプリケーションに通知します。</span><span class="sxs-lookup"><span data-stu-id="39b71-447">The default memory monitor in ASP.NET notifies applications when they are running close to the configured private bytes limit for the process, or when the machine is low on total available physical RAM.</span></span> <span data-ttu-id="39b71-448">これらの制限に近づくと、通知が発生します。</span><span class="sxs-lookup"><span data-stu-id="39b71-448">When these limits are near, notifications are fired.</span></span> <span data-ttu-id="39b71-449">一部のアプリケーションでは、通知の発生が構成されている制限に近すぎるため、有効な対応を取れません。</span><span class="sxs-lookup"><span data-stu-id="39b71-449">For some applications, notifications are fired too close to the configured limits to allow for useful reactions.</span></span> <span data-ttu-id="39b71-450">開発者は、<xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> プロパティを使用して既定値を置き換える独自のメモリ モニターを作成できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-450">Developers can now write their own memory monitors to replace the default by using the <xref:System.Web.Hosting.ApplicationMonitors.MemoryMonitor%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="39b71-451">**メモリ制限への対応** 。</span><span class="sxs-lookup"><span data-stu-id="39b71-451">**Memory Limit Reactions** .</span></span> <span data-ttu-id="39b71-452">既定では、プライベート バイト プロセス制限が近づくと、ASP.NET はオブジェクト キャッシュの削減を試み、<xref:System.GC.Collect%2A?displayProperty=nameWithType> を定期的に呼び出します。</span><span class="sxs-lookup"><span data-stu-id="39b71-452">By default, ASP.NET attempts to trim the object cache and periodically call <xref:System.GC.Collect%2A?displayProperty=nameWithType> when the private byte process limit is near.</span></span> <span data-ttu-id="39b71-453">アプリケーションによっては、<xref:System.GC.Collect%2A?displayProperty=nameWithType> の呼び出し頻度またはトリミングされるキャッシュ量が非効率になります。</span><span class="sxs-lookup"><span data-stu-id="39b71-453">For some applications, the frequency of calls to <xref:System.GC.Collect%2A?displayProperty=nameWithType> or the amount of cache that is trimmed are inefficient.</span></span> <span data-ttu-id="39b71-454">開発者は、アプリケーションのメモリ モニターに **IObserver** の実装をサブスクライブすることにより、既定の動作を置換または補完できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-454">Developers can now replace or supplement the default behavior by subscribing **IObserver** implementations to the application's memory monitor.</span></span>

<a name="wcf47"></a>

#### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="39b71-455">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="39b71-455">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="39b71-456">Windows Communication Foundation (WCF) では以下の機能が追加または変更されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-456">Windows Communication Foundation (WCF) adds the following features and changes:</span></span>

<span data-ttu-id="39b71-457">**既定のメッセージ セキュリティ設定を TLS1.1 または TLS1.2 に構成する機能。**</span><span class="sxs-lookup"><span data-stu-id="39b71-457">**Ability to configure the default message security settings to TLS 1.1 or TLS 1.2**</span></span>

<span data-ttu-id="39b71-458">.NET Framework 4.7 以降の WCF では、既定のメッセージ セキュリティ プロトコルとして、SSL 3.0 と TLS 1.0 に加えて、TLS 1.1 または TLS 1.2 を構成できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-458">Starting with .NET Framework 4.7, WCF allows you to configure TLS 1.1 or TLS 1.2 in addition to SSL 3.0 and TLS 1.0 as the default message security protocol.</span></span> <span data-ttu-id="39b71-459">これはオプトイン設定です。有効にするには、アプリケーション構成ファイルに次のエントリを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-459">This is an opt-in setting; to enable it, you must add the following entry to your application configuration file:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.ServiceModel.DisableUsingServicePointManagerSecurityProtocols=false;Switch.System.Net.DontEnableSchUseStrongCrypto=false" />
</runtime>
```

<span data-ttu-id="39b71-460">**WCF アプリケーションと WCF シリアル化の信頼性の向上**</span><span class="sxs-lookup"><span data-stu-id="39b71-460">**Improved reliability of WCF applications and WCF serialization**</span></span>

<span data-ttu-id="39b71-461">WCF に競合状態を除去する複数のコード変更が追加され、シリアル化オプションの信頼性とパフォーマンスが向上しています。</span><span class="sxs-lookup"><span data-stu-id="39b71-461">WCF includes a number of code changes that eliminate race conditions, thereby improving performance and the reliability of serialization options.</span></span> <span data-ttu-id="39b71-462">次の設定があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-462">These include:</span></span>

- <span data-ttu-id="39b71-463">**SocketConnection.BeginRead** および **SocketConnection.Read** の呼び出しでの非同期コードと同期コードの併用のサポートの向上。</span><span class="sxs-lookup"><span data-stu-id="39b71-463">Better support for mixing asynchronous and synchronous code in calls to **SocketConnection.BeginRead** and **SocketConnection.Read** .</span></span>
- <span data-ttu-id="39b71-464">**SharedConnectionListener** および **DuplexChannelBinder** で接続を中止するときの信頼性の向上。</span><span class="sxs-lookup"><span data-stu-id="39b71-464">Improved reliability when aborting a connection with **SharedConnectionListener** and **DuplexChannelBinder** .</span></span>
- <span data-ttu-id="39b71-465"><xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> メソッドの呼び出し時のシリアル化操作の信頼性を向上しました。</span><span class="sxs-lookup"><span data-stu-id="39b71-465">Improved reliability of serialization operations when calling the <xref:System.Runtime.Serialization.FormatterServices.GetSerializableMembers%28System.Type%29?displayProperty=nameWithType> method.</span></span>
- <span data-ttu-id="39b71-466">**ChannelSynchronizer.RemoveWaiter** メソッドを呼び出して待機を削除するときの信頼性の向上。</span><span class="sxs-lookup"><span data-stu-id="39b71-466">Improved reliability when removing a waiter by calling the **ChannelSynchronizer.RemoveWaiter** method.</span></span>

<a name="wf47"></a>

#### <a name="windows-forms"></a><span data-ttu-id="39b71-467">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="39b71-467">Windows Forms</span></span>

<span data-ttu-id="39b71-468">.NET Framework 4.7 では、Windows フォームによる高 DPI モニターのサポートが向上しました。</span><span class="sxs-lookup"><span data-stu-id="39b71-468">In .NET Framework 4.7, Windows Forms improves support for high DPI monitors.</span></span>

<span data-ttu-id="39b71-469">**高 DPI のサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-469">**High DPI support**</span></span>

<span data-ttu-id="39b71-470">.NET Framework 4.7 を対象とするアプリケーションで、Windows フォーム アプリケーションで高 DPI および動的 DPI がサポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-470">Starting with applications that target .NET Framework 4.7, .NET Framework features high DPI and dynamic DPI support for Windows Forms applications.</span></span> <span data-ttu-id="39b71-471">高 DPI のサポートにより、フォームのレイアウトと外観および高 DPI モニターでのコントロールが向上します。</span><span class="sxs-lookup"><span data-stu-id="39b71-471">High DPI support improves the layout and appearance of forms and controls on high DPI monitors.</span></span> <span data-ttu-id="39b71-472">動的 DPI は、ユーザーが実行中のアプリケーションの DPI または表示倍率を変更すると、フォームのレイアウトと外観およびコントロールを変更します。</span><span class="sxs-lookup"><span data-stu-id="39b71-472">Dynamic DPI changes the layout and appearance of forms and controls when the user changes the DPI or display scale factor of a running application.</span></span>

<span data-ttu-id="39b71-473">高 DPI のサポートはオプトイン機能であり、アプリケーション構成ファイルの [\<System.Windows.Forms.ConfigurationSection>](../configure-apps/file-schema/winforms/index.md) セクションを定義することで構成します。</span><span class="sxs-lookup"><span data-stu-id="39b71-473">High DPI support is an opt-in feature that you configure by defining a [\<System.Windows.Forms.ConfigurationSection>](../configure-apps/file-schema/winforms/index.md) section in your application configuration file.</span></span> <span data-ttu-id="39b71-474">Windows フォーム アプリケーションへの高 DPI サポートおよび動的 DPI サポート追加の詳細については、「[Windows フォームの高 DPI サポート](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-474">For more information on adding high DPI support and dynamic DPI support to your Windows Forms application, see [High DPI Support in Windows Forms](/dotnet/desktop/winforms/high-dpi-support-in-windows-forms).</span></span>

<a name="WPF47"></a>

#### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="39b71-475">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="39b71-475">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="39b71-476">.NET Framework 4.7 では、WPF の機能が次のように強化されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-476">In .NET Framework 4.7, WPF includes the following enhancements:</span></span>

<span data-ttu-id="39b71-477">**Windows WM_POINTER メッセージに基づくタッチ/スタイラス スタックのサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-477">**Support for a touch/stylus stack based on Windows WM_POINTER messages**</span></span>

<span data-ttu-id="39b71-478">Windows Ink Services Platform (WISP) の代わりに [WM_POINTER メッセージ](/previous-versions/windows/desktop/InputMsg/messages)に基づいてタッチ/スタイラス スタックを使うオプションが追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-478">You now have the option of using a touch/stylus stack based on [WM_POINTER messages](/previous-versions/windows/desktop/InputMsg/messages) instead of the Windows Ink Services Platform (WISP).</span></span> <span data-ttu-id="39b71-479">これは、.NET Framework のオプトイン機能です。</span><span class="sxs-lookup"><span data-stu-id="39b71-479">This is an opt-in feature in .NET Framework.</span></span> <span data-ttu-id="39b71-480">詳細については、「[アプリケーションの互換性](../migration-guide/application-compatibility.md)」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-480">For more information, see the [Application compatibility](../migration-guide/application-compatibility.md) section.</span></span>

<span data-ttu-id="39b71-481">**WPF 印刷 API の新しい実装**</span><span class="sxs-lookup"><span data-stu-id="39b71-481">**New implementation for WPF printing APIs**</span></span>

<span data-ttu-id="39b71-482"><xref:System.Printing.PrintQueue?displayProperty=nameWithType> クラスの WPF 印刷 API は、非推奨になった [XPS 印刷 API](/windows/desktop/printdocs/xps-printing) ではなく Windows [ドキュメント印刷パッケージ API](/windows/desktop/printdocs/tailored-app-printing-api) を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="39b71-482">WPF's printing APIs in the <xref:System.Printing.PrintQueue?displayProperty=nameWithType> class call the Windows [Print Document Package API](/windows/desktop/printdocs/tailored-app-printing-api) instead of the deprecated [XPS Print API](/windows/desktop/printdocs/xps-printing).</span></span> <span data-ttu-id="39b71-483">アプリケーションの互換性に対するこの変更の影響については、「[アプリケーションの互換性](../migration-guide/application-compatibility.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-483">For the impact of this change on application compatibility, see the [Application compatibility](../migration-guide/application-compatibility.md) section.</span></span>

<a name="v462"></a>

## <a name="whats-new-in-net-framework-462"></a><span data-ttu-id="39b71-484">.NET Framework 4.6.2 の新機能</span><span class="sxs-lookup"><span data-stu-id="39b71-484">What's new in .NET Framework 4.6.2</span></span>

<span data-ttu-id="39b71-485">.NET Framework 4.6.2 には、次の領域に新機能があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-485">.NET Framework 4.6.2 includes new features in the following areas:</span></span>

- [<span data-ttu-id="39b71-486">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="39b71-486">ASP.NET</span></span>](#ASPNET462)

- [<span data-ttu-id="39b71-487">文字カテゴリ</span><span class="sxs-lookup"><span data-stu-id="39b71-487">Character categories</span></span>](#Strings)

- [<span data-ttu-id="39b71-488">暗号</span><span class="sxs-lookup"><span data-stu-id="39b71-488">Cryptography</span></span>](#Crypto462)

- [<span data-ttu-id="39b71-489">SQLClient</span><span class="sxs-lookup"><span data-stu-id="39b71-489">SqlClient</span></span>](#SQLClient)

- [<span data-ttu-id="39b71-490">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="39b71-490">Windows Communication Foundation</span></span>](#WCF)

- [<span data-ttu-id="39b71-491">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="39b71-491">Windows Presentation Foundation (WPF)</span></span>](#WPF462)

- [<span data-ttu-id="39b71-492">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="39b71-492">Windows Workflow Foundation (WF)</span></span>](#WF462)

- [<span data-ttu-id="39b71-493">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="39b71-493">ClickOnce</span></span>](#clickonce-1)

- [<span data-ttu-id="39b71-494">Windows フォームおよび WPF アプリの UWP アプリへの変換</span><span class="sxs-lookup"><span data-stu-id="39b71-494">Converting Windows Forms and WPF apps to UWP apps</span></span>](#UWPConvert)

- [<span data-ttu-id="39b71-495">デバッグの機能強化</span><span class="sxs-lookup"><span data-stu-id="39b71-495">Debugging improvements</span></span>](#Debug462)

<span data-ttu-id="39b71-496">.NET Framework 4.6.2 に追加された新しい API の一覧については、GitHub で「[.NET Framework 4.6.2 API Changes (.NET Framework 4.6.2 API の変更点)](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-496">For a list of new APIs added to .NET Framework 4.6.2, see [.NET Framework 4.6.2 API Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) on GitHub.</span></span> <span data-ttu-id="39b71-497">.NET Framework 4.6.2 における機能の改善とバグ修正の一覧については、GitHub で「[.NET Framework 4.6.2 List of Changes (.NET Framework 4.6.2 の変更点の一覧)](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-changes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-497">For a list of feature improvements and bug fixes in .NET Framework 4.6.2, see [.NET Framework 4.6.2 List of Changes](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-changes.md) on GitHub.</span></span> <span data-ttu-id="39b71-498">詳細については、.NET ブログの「[.NET Framework 4.6.2 の発表](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-498">For more information, see [Announcing .NET Framework 4.6.2](https://devblogs.microsoft.com/dotnet/announcing-net-framework-4-6-2/) in the .NET blog.</span></span>

<a name="ASPNET462"></a>

### <a name="aspnet"></a><span data-ttu-id="39b71-499">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="39b71-499">ASP.NET</span></span>

<span data-ttu-id="39b71-500">.NET Framework 4.6.2 では、ASP.NET の機能が次のように強化されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-500">In  .NET Framework 4.6.2, ASP.NET includes the following enhancements:</span></span>

<span data-ttu-id="39b71-501">**データ注釈検証コントロールのローカライズされたエラー メッセージのサポート強化**</span><span class="sxs-lookup"><span data-stu-id="39b71-501">**Improved support for localized error messages in data annotation validators**</span></span>

<span data-ttu-id="39b71-502">データ注釈検証コントロールを使用して、1 つ以上の属性をクラス プロパティに追加して検証を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-502">Data annotation validators enable you to perform validation by adding one or more attributes to a class property.</span></span> <span data-ttu-id="39b71-503">属性の <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> 要素は、検証が失敗した場合にエラー メッセージのテキストを定義します。</span><span class="sxs-lookup"><span data-stu-id="39b71-503">The attribute's <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> element defines the text of the error message if validation fails.</span></span> <span data-ttu-id="39b71-504">.NET Framework 4.6.2 以降では、ASP.NET でエラー メッセージを簡単にローカライズできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-504">Starting with .NET Framework 4.6.2, ASP.NET makes it easy to localize error messages.</span></span> <span data-ttu-id="39b71-505">エラー メッセージは次のような場合にローカライズされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-505">Error messages will be localized if:</span></span>

1. <span data-ttu-id="39b71-506"><xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> が検証属性で指定されている。</span><span class="sxs-lookup"><span data-stu-id="39b71-506">The <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> is provided in the validation attribute.</span></span>

2. <span data-ttu-id="39b71-507">リソース ファイルが App_LocalResources フォルダーに格納されている。</span><span class="sxs-lookup"><span data-stu-id="39b71-507">The resource file is stored in the App_LocalResources folder.</span></span>

3. <span data-ttu-id="39b71-508">ローカライズされたリソース ファイル名の形式が `DataAnnotation.Localization.{`*名前*`}.resx` (この *名前* は、 *languageCode*`-`*country/regionCode* または *languageCode* 形式のカルチャ名) である。</span><span class="sxs-lookup"><span data-stu-id="39b71-508">The name of the localized resources file has the form `DataAnnotation.Localization.{`*name*`}.resx`, where *name* is a culture name in the format *languageCode*`-`*country/regionCode* or *languageCode* .</span></span>

4. <span data-ttu-id="39b71-509">リソースのキー名が <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> 属性に割り当てられている文字列で、その値がローカライズされたエラー メッセージである。</span><span class="sxs-lookup"><span data-stu-id="39b71-509">The key name of the resource is the string assigned to the <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=nameWithType> attribute,  and its value is the localized error message.</span></span>

<span data-ttu-id="39b71-510">たとえば、次のデータ注釈属性では、無効な評価の場合に表示する、既定のカルチャのエラー メッセージを定義します。</span><span class="sxs-lookup"><span data-stu-id="39b71-510">For example, the following data annotation attribute defines the default culture's error message for an invalid rating.</span></span>

```csharp
public class RatingInfo
{
   [Required(ErrorMessage = "The rating must be between 1 and 10.")]
   [Display(Name = "Your Rating")]
   public int Rating { get; set; }
}
```

```vb
Public Class RatingInfo
   <Required(ErrorMessage = "The rating must be between 1 and 10.")>
   <Display(Name = "Your Rating")>
   Public Property Rating As Integer = 1
End Class
```

<span data-ttu-id="39b71-511">キーがエラー メッセージ文字列であり、その値がローカライズされたエラー メッセージであるようにリソース ファイル DataAnnotation.Localization.fr.resx を作成します。</span><span class="sxs-lookup"><span data-stu-id="39b71-511">You can then create a resource file, DataAnnotation.Localization.fr.resx, whose key is the error message string and whose value is the localized error message.</span></span> <span data-ttu-id="39b71-512">ファイルは `App.LocalResources` フォルダーになければいけません。</span><span class="sxs-lookup"><span data-stu-id="39b71-512">The file must be found in the `App.LocalResources` folder.</span></span> <span data-ttu-id="39b71-513">たとえば下記は、キーとその値で、値はローカライズされたフランス語 (fr) のエラー メッセージです。</span><span class="sxs-lookup"><span data-stu-id="39b71-513">For example, the following is the key and its value in a localized French (fr) language error message:</span></span>

| <span data-ttu-id="39b71-514">名前</span><span class="sxs-lookup"><span data-stu-id="39b71-514">Name</span></span>                                 | <span data-ttu-id="39b71-515">[値]</span><span class="sxs-lookup"><span data-stu-id="39b71-515">Value</span></span>                                     |
| ------------------------------------ | ----------------------------------------- |
| <span data-ttu-id="39b71-516">評価は、1 から 10 の範囲である必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-516">The rating must be between 1 and 10.</span></span> | <span data-ttu-id="39b71-517">La note doit être comprise entre 1 et 10.</span><span class="sxs-lookup"><span data-stu-id="39b71-517">La note doit être comprise entre 1 et 10.</span></span> |

 <span data-ttu-id="39b71-518">また、データ注釈ローカリゼーションを拡張することができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-518">In addition, data annotation localization is extensible.</span></span> <span data-ttu-id="39b71-519">開発者は、<xref:System.Web.Globalization.IStringLocalizerProvider> インターフェイスを実装してリソース ファイル以外の場所にローカリゼーション文字列を格納することで、独自の文字列ローカライザー プロバイダーにプラグインできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-519">Developers can plug in their own string localizer provider by implementing the <xref:System.Web.Globalization.IStringLocalizerProvider> interface to store localization string somewhere other than in a resource file.</span></span>

 <span data-ttu-id="39b71-520">**セッション状態ストア プロバイダーでの非同期サポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-520">**Async support with session-state store providers**</span></span>

 <span data-ttu-id="39b71-521">ASP.NET では、セッション状態ストア プロバイダーでタスクを返すメソッドを使用できるようになりました。これにより、ASP.NET アプリで非同期のスケーラビリティのメリットが得られます。</span><span class="sxs-lookup"><span data-stu-id="39b71-521">ASP.NET now allows task-returning methods to be used with session-state store providers, thereby allowing ASP.NET apps to get the scalability benefits of async.</span></span> <span data-ttu-id="39b71-522">セッション状態ストア プロバイダーでの非同期操作をサポートするために、ASP.NET には新しいインターフェイスである <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType> が含まれています。これは <xref:System.Web.IHttpModule> から継承され、開発者はこれを使用して独自のセッション状態モジュールと非同期セッション ストア プロバイダーを実装することができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-522">To supports asynchronous operations with session state store providers, ASP.NET includes  a new interface, <xref:System.Web.SessionState.ISessionStateModule?displayProperty=nameWithType>, which inherits from <xref:System.Web.IHttpModule> and allows developers to implement their own session-state module and async session store providers.</span></span> <span data-ttu-id="39b71-523">このインターフェイスは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-523">The interface is defined as follows:</span></span>

```csharp
public interface ISessionStateModule : IHttpModule {
    void ReleaseSessionState(HttpContext context);
    Task ReleaseSessionStateAsync(HttpContext context);
}
```

```vb
Public Interface ISessionStateModule : Inherits IHttpModule
   Sub ReleaseSessionState(context As HttpContext)
   Function ReleaseSessionStateAsync(context As HttpContext) As Task
End Interface
```

 <span data-ttu-id="39b71-524">また、<xref:System.Web.SessionState.SessionStateUtility> クラスには <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> および <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A> という 2 つの新しいメソッドが含まれています。これらを使用して、非同期操作をサポートできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-524">In addition, the <xref:System.Web.SessionState.SessionStateUtility> class includes two new methods, <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A> and <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>, that can be used to support asynchronous operations.</span></span>

 <span data-ttu-id="39b71-525">**出力キャッシュ プロバイダーの非同期サポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-525">**Async support for output-cache providers**</span></span>

 <span data-ttu-id="39b71-526">.NET Framework 4.6.2 以降で、タスクを返すメソッドを出力キャッシュ プロバイダーで使って、非同期のスケーラビリティのメリットを得ることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-526">Starting with .NET Framework 4.6.2, task-returning methods can be used with output-cache providers to provide the scalability benefits of async.</span></span>  <span data-ttu-id="39b71-527">これらのメソッドを実装するプロバイダーは、Web サーバー上のスレッド ブロックを減らし、ASP.NET サービスのスケーラビリティを向上させます。</span><span class="sxs-lookup"><span data-stu-id="39b71-527">Providers that implement these methods reduce thread-blocking on a web server and improve the scalability of an ASP.NET service.</span></span>

 <span data-ttu-id="39b71-528">非同期出力キャッシュ プロバイダーをサポートするために、次の API が追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-528">The following APIs have been added to support asynchronous output-cache providers:</span></span>

- <span data-ttu-id="39b71-529"><xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> から継承される <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> クラス。これにより、開発者は非同期出力キャッシュ プロバイダーを実装できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-529">The <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=nameWithType> class, which inherits from <xref:System.Web.Caching.OutputCacheProvider?displayProperty=nameWithType> and allows developers to implement an asynchronous output-cache provider.</span></span>

- <span data-ttu-id="39b71-530"><xref:System.Web.Caching.OutputCacheUtility> クラス。出力キャッシュを構成するためのヘルパー メソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="39b71-530">The <xref:System.Web.Caching.OutputCacheUtility> class, which provides helper methods for configuring the output cache.</span></span>

- <span data-ttu-id="39b71-531"><xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> クラスの新しい 18 個のメソッド。</span><span class="sxs-lookup"><span data-stu-id="39b71-531">18 new methods in the <xref:System.Web.HttpCachePolicy?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="39b71-532">これらのメソッドには、<xref:System.Web.HttpCachePolicy.GetCacheability%2A>、<xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>、<xref:System.Web.HttpCachePolicy.GetETag%2A>、<xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>、<xref:System.Web.HttpCachePolicy.GetMaxAge%2A>、<xref:System.Web.HttpCachePolicy.GetMaxAge%2A>、<xref:System.Web.HttpCachePolicy.GetNoStore%2A>、<xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>、<xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>、<xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>、<xref:System.Web.HttpCachePolicy.GetRevalidation%2A>、<xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>、<xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>、<xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>、および <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A> が含まれます。</span><span class="sxs-lookup"><span data-stu-id="39b71-532">These include <xref:System.Web.HttpCachePolicy.GetCacheability%2A>, <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>, <xref:System.Web.HttpCachePolicy.GetETag%2A>, <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetNoStore%2A>, <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>, <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>, <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>, <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>, <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>, <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>, <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>, and <xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>.</span></span>

- <span data-ttu-id="39b71-533"><xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> クラスの新しい 2 つのメソッド (<xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> と <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>)。</span><span class="sxs-lookup"><span data-stu-id="39b71-533">2 new methods in the <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=nameWithType> class:  <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A> and <xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>.</span></span>

- <span data-ttu-id="39b71-534"><xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> クラスの新しい 2 つのメソッド (<xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> と <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>)。</span><span class="sxs-lookup"><span data-stu-id="39b71-534">2 new methods in the <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=nameWithType> class: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A> and <xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>.</span></span>

- <span data-ttu-id="39b71-535"><xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> クラスの新しい 2 つのメソッド (<xref:System.Web.HttpCacheVaryByParams.GetParams%2A> と <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>)。</span><span class="sxs-lookup"><span data-stu-id="39b71-535">2 new methods in the <xref:System.Web.HttpCacheVaryByParams?displayProperty=nameWithType> class: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A> and <xref:System.Web.HttpCacheVaryByParams.SetParams%2A>.</span></span>

- <span data-ttu-id="39b71-536"><xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> クラスの <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> メソッド。</span><span class="sxs-lookup"><span data-stu-id="39b71-536">In the <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=nameWithType> class, the <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A> method.</span></span>

- <span data-ttu-id="39b71-537"><xref:System.Web.Caching.CacheDependency> の <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> メソッド。</span><span class="sxs-lookup"><span data-stu-id="39b71-537">In the <xref:System.Web.Caching.CacheDependency>, the <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A> method.</span></span>

<a name="Strings"></a>

### <a name="character-categories"></a><span data-ttu-id="39b71-538">文字カテゴリ</span><span class="sxs-lookup"><span data-stu-id="39b71-538">Character categories</span></span>

<span data-ttu-id="39b71-539">.NET Framework 4.6.2 の文字は [Unicode Standard バージョン 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) に基づいて分類されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-539">Characters in .NET Framework 4.6.2 are classified based on the [Unicode Standard, Version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/).</span></span> <span data-ttu-id="39b71-540">.NET Framework 4.6 と .NET Framework 4.6.1 では、文字は Unicode 6.3 文字のカテゴリに基づいて分類されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-540">In .NET Framework 4.6 and .NET Framework 4.6.1, characters were classified based on Unicode 6.3 character categories.</span></span>

<span data-ttu-id="39b71-541">Unicode 8.0 のサポートは、<xref:System.Globalization.CharUnicodeInfo> クラスによる文字列の分類およびそれに依存する型とメソッドに限定されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-541">Support for Unicode 8.0 is limited to the classification of characters by the <xref:System.Globalization.CharUnicodeInfo> class and to types and methods that rely on it.</span></span> <span data-ttu-id="39b71-542">これらには、<xref:System.Globalization.StringInfo> クラス、オーバーロードされた <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> メソッド、および .NET Framework の正規表現エンジンによって認識される[文字クラス](../../standard/base-types/character-classes-in-regular-expressions.md)が含まれます。</span><span class="sxs-lookup"><span data-stu-id="39b71-542">These include the <xref:System.Globalization.StringInfo> class, the overloaded <xref:System.Char.GetUnicodeCategory%2A?displayProperty=nameWithType> method, and the [character classes](../../standard/base-types/character-classes-in-regular-expressions.md) recognized by the .NET Framework regular expression engine.</span></span>  <span data-ttu-id="39b71-543">文字や文字列の比較と並べ替えは、この変更の影響を受けず、.NET Framework で提供される文字データについては、引き続き基となるオペレーティング システム (Windows 7 システム) に依存します。</span><span class="sxs-lookup"><span data-stu-id="39b71-543">Character and string comparison and sorting is unaffected by this change and continues to rely on the underlying operating system or, on Windows 7 systems, on character data provided by .NET Framework.</span></span>

<span data-ttu-id="39b71-544">Unicode 6.0 から Unicode 7.0 への文字カテゴリの変更については、Unicode Consortium Web サイトの [Unicode Standard バージョン 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) に関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-544">For changes in character categories from Unicode 6.0 to Unicode 7.0, see [The Unicode Standard, Version 7.0.0](https://www.unicode.org/versions/Unicode7.0.0/) at The Unicode Consortium website.</span></span> <span data-ttu-id="39b71-545">Unicode 7.0 から Unicode 8.0 への変更については、Unicode Consortium の Web サイトの [Unicode Standard バージョン 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) に関する記述を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-545">For changes from Unicode 7.0 to Unicode 8.0, see [The Unicode Standard, Version 8.0.0](https://www.unicode.org/versions/Unicode8.0.0/) at The Unicode Consortium website.</span></span>

<a name="Crypto462"></a>

### <a name="cryptography"></a><span data-ttu-id="39b71-546">暗号</span><span class="sxs-lookup"><span data-stu-id="39b71-546">Cryptography</span></span>

<span data-ttu-id="39b71-547">**FIPS 186-3 DSA を含む X509 証明書のサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-547">**Support for X509 certificates containing FIPS 186-3 DSA**</span></span>

<span data-ttu-id="39b71-548">.NET Framework 4.6.2 で、FIPS 186-2 のキーに対する 1024 ビットの制限を超過するキーを使用できる DSA (Digital Signature Algorithm) X509 証明書をサポートするようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-548">.NET Framework 4.6.2 adds support for DSA (Digital Signature Algorithm) X509 certificates whose keys exceed the FIPS 186-2 1024-bit limit.</span></span>

<span data-ttu-id="39b71-549">.NET Framework 4.6.2 では、FIPS 186-3 のより大きなキー サイズを使用できることに加え、SHA-2 ファミリのハッシュ アルゴリズム (SHA256、SHA384、SHA512) によるシグネチャ計算も可能です。</span><span class="sxs-lookup"><span data-stu-id="39b71-549">In addition to supporting the larger key sizes of FIPS 186-3, .NET Framework 4.6.2 allows computing signatures with the SHA-2 family of hash algorithms (SHA256, SHA384, and SHA512).</span></span> <span data-ttu-id="39b71-550">FIPS 186-3 のサポートは新しい <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> クラスで提供されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-550">FIPS 186-3 support is provided by the new <xref:System.Security.Cryptography.DSACng?displayProperty=nameWithType> class.</span></span>

<span data-ttu-id="39b71-551">.NET Framework 4.6 の <xref:System.Security.Cryptography.RSA> クラスと .NET Framework 4.6.1 の <xref:System.Security.Cryptography.ECDsa> クラスの最近の変更に合わせて、.NET Framework 4.6.2 の <xref:System.Security.Cryptography.DSA> 抽象基本クラスには追加のメソッドがあり、これによって呼び出し元はこの機能をキャストせずに使用することができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-551">In keeping with recent changes to the <xref:System.Security.Cryptography.RSA> class in .NET Framework 4.6 and the <xref:System.Security.Cryptography.ECDsa> class in .NET Framework 4.6.1, the <xref:System.Security.Cryptography.DSA> abstract base class in .NET Framework 4.6.2 has additional methods to allow callers to use this functionality without casting.</span></span> <span data-ttu-id="39b71-552">データに署名する場合は、以下の例のように、<xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> 拡張メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-552">You can call the <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=nameWithType> extension method to sign data, as the following example shows.</span></span>

```csharp
public static byte[] SignDataDsaSha384(byte[] data, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPrivateKey())
    {
        return dsa.SignData(data, HashAlgorithmName.SHA384);
    }
}
```

```vb
Public Shared Function SignDataDsaSha384(data As Byte(), cert As X509Certificate2) As Byte()
    Using DSA As DSA = cert.GetDSAPrivateKey()
        Return DSA.SignData(data, HashAlgorithmName.SHA384)
    End Using
End Function
```

<span data-ttu-id="39b71-553">署名データを検証する場合は、以下の例のように、<xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> 拡張メソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-553">And you can call the <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=nameWithType> extension method to verify signed data, as the following example shows.</span></span>

```csharp
public static bool VerifyDataDsaSha384(byte[] data, byte[] signature, X509Certificate2 cert)
{
    using (DSA dsa = cert.GetDSAPublicKey())
    {
        return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384);
    }
}
```

```vb
 Public Shared Function VerifyDataDsaSha384(data As Byte(), signature As Byte(), cert As X509Certificate2) As Boolean
    Using dsa As DSA = cert.GetDSAPublicKey()
        Return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384)
    End Using
End Function
```

<span data-ttu-id="39b71-554">**ECDiffieHellman キー派生ルーチンへの入力をよりわかりやすく**</span><span class="sxs-lookup"><span data-stu-id="39b71-554">**Increased clarity for inputs to ECDiffieHellman key derivation routines**</span></span>

<span data-ttu-id="39b71-555">.NET Framework 3.5 では、3 種類の KDF (キー派生関数) ルーチンによる Elliptic Curve Diffie-Hellman キー承諾のサポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-555">.NET Framework 3.5 added support for Elliptic Curve Diffie-Hellman Key Agreement with three different Key Derivation Function (KDF) routines.</span></span> <span data-ttu-id="39b71-556">ルーチンへの入力、およびルーチン自体は <xref:System.Security.Cryptography.ECDiffieHellmanCng> オブジェクトのプロパティで構成されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-556">The inputs to the routines, and the routines themselves, were configured via properties on the <xref:System.Security.Cryptography.ECDiffieHellmanCng> object.</span></span> <span data-ttu-id="39b71-557">しかし、すべてのルーチンですべての入力プロパティが読み取られるわけではないため、これまで開発者がよく混乱することがありました。</span><span class="sxs-lookup"><span data-stu-id="39b71-557">But since not every routine read every input property, there was ample room for confusion on the past of the developer.</span></span>

<span data-ttu-id="39b71-558">.NET Framework 4.6.2 ではこれに対処するために、次の 3 つのメソッドが <xref:System.Security.Cryptography.ECDiffieHellman> 基底クラスに追加され、これらの KDF ルーチンとその入力がよりわかりやくなりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-558">To address this in .NET Framework 4.6.2, the following three methods have been added to the  <xref:System.Security.Cryptography.ECDiffieHellman> base class to more clearly represent these KDF routines and their inputs:</span></span>

|<span data-ttu-id="39b71-559">ECDiffieHellman メソッド</span><span class="sxs-lookup"><span data-stu-id="39b71-559">ECDiffieHellman method</span></span>|<span data-ttu-id="39b71-560">説明</span><span class="sxs-lookup"><span data-stu-id="39b71-560">Description</span></span>|
|----------------------------|-----------------|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="39b71-561">次の式を使用してキー マテリアルを派生させます。</span><span class="sxs-lookup"><span data-stu-id="39b71-561">Derives key material using the formula</span></span><br /><br /> <span data-ttu-id="39b71-562">HASH(secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span><span class="sxs-lookup"><span data-stu-id="39b71-562">HASH(secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span></span><br /><br /> <span data-ttu-id="39b71-563">HASH(secretPrepend OrElse *x* OrElse secretAppend)</span><span class="sxs-lookup"><span data-stu-id="39b71-563">HASH(secretPrepend OrElse *x* OrElse secretAppend)</span></span><br /><br /> <span data-ttu-id="39b71-564">ここで *x* は、EC Diffie-Hellman アルゴリズムの計算結果を表します。</span><span class="sxs-lookup"><span data-stu-id="39b71-564">where *x* is the computed result of the EC Diffie-Hellman algorithm.</span></span>|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="39b71-565">次の式を使用してキー マテリアルを派生させます。</span><span class="sxs-lookup"><span data-stu-id="39b71-565">Derives key material using the formula</span></span><br /><br /> <span data-ttu-id="39b71-566">HMAC(hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span><span class="sxs-lookup"><span data-stu-id="39b71-566">HMAC(hmacKey, secretPrepend &#124;&#124; *x* &#124;&#124; secretAppend)</span></span><br /><br /> <span data-ttu-id="39b71-567">HMAC(hmacKey, secretPrepend OrElse *x* OrElse secretAppend)</span><span class="sxs-lookup"><span data-stu-id="39b71-567">HMAC(hmacKey, secretPrepend OrElse *x* OrElse secretAppend)</span></span><br /><br /> <span data-ttu-id="39b71-568">ここで *x* は、EC Diffie-Hellman アルゴリズムの計算結果を表します。</span><span class="sxs-lookup"><span data-stu-id="39b71-568">where *x* is the computed result of the EC Diffie-Hellman algorithm.</span></span>|
|<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|<span data-ttu-id="39b71-569">TLS 擬似乱数関数 (PRF) 派生アルゴリズムを使用して、キー マテリアルを派生させます。</span><span class="sxs-lookup"><span data-stu-id="39b71-569">Derives key material using the TLS pseudo-random function (PRF) derivation algorithm.</span></span>|

<span data-ttu-id="39b71-570">**永続化されたキーによる対称暗号化のサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-570">**Support for persisted-key symmetric encryption**</span></span>

<span data-ttu-id="39b71-571">Windows の暗号化ライブラリ (CNG) では、永続化された対称キーの格納とハードウェアに格納された対称キーの使用ができるようになり、開発者がこの機能を .NET Framework 4.6.2 で利用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-571">The Windows cryptography library (CNG) added support for storing persisted symmetric keys and using hardware-stored symmetric keys, and .NET Framework 4.6.2 made it possible for developers to make use of this feature.</span></span>  <span data-ttu-id="39b71-572">キー名とキー プロバイダーの概念が実装に固有であるため、この機能を使用するには、推奨されるファクトリ手法 (`Aes.Create` の呼び出しなど) ではなく、具象実装型のコンストラクターを利用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-572">Since the notion of key names and key providers is implementation-specific, using this feature requires utilizing the constructor of the concrete implementation types instead of the preferred factory approach (such as calling `Aes.Create`).</span></span>

<span data-ttu-id="39b71-573">永続化されたキーによる対称暗号化は、AES (<xref:System.Security.Cryptography.AesCng>) と 3DES (<xref:System.Security.Cryptography.TripleDESCng>) アルゴリズムでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-573">Persisted-key symmetric encryption support exists for the AES (<xref:System.Security.Cryptography.AesCng>) and 3DES (<xref:System.Security.Cryptography.TripleDESCng>) algorithms.</span></span> <span data-ttu-id="39b71-574">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="39b71-574">For example:</span></span>

```csharp
public static byte[] EncryptDataWithPersistedKey(byte[] data, byte[] iv)
{
    using (Aes aes = new AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider))
    {
        aes.IV = iv;

        // Using the zero-argument overload is required to make use of the persisted key
        using (ICryptoTransform encryptor = aes.CreateEncryptor())
        {
            if (!encryptor.CanTransformMultipleBlocks)
            {
                throw new InvalidOperationException("This is a sample, this case wasn't handled...");
            }

            return encryptor.TransformFinalBlock(data, 0, data.Length);
        }
    }
}
```

```vb
Public Shared Function EncryptDataWithPersistedKey(data As Byte(), iv As Byte()) As Byte()
    Using Aes As Aes = New AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider)
        Aes.IV = iv

        ' Using the zero-argument overload Is required to make use of the persisted key
        Using encryptor As ICryptoTransform = Aes.CreateEncryptor()
            If Not encryptor.CanTransformMultipleBlocks Then
                Throw New InvalidOperationException("This is a sample, this case wasn't handled...")
            End If
            Return encryptor.TransformFinalBlock(data, 0, data.Length)
        End Using
    End Using
End Function
```

<span data-ttu-id="39b71-575">**SHA-2 ハッシュの SignedXml サポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-575">**SignedXml support for SHA-2 hashing**</span></span>

<span data-ttu-id="39b71-576">.NET Framework 4.6.2 の RSA-SHA256、RSA-SHA384、RSA-SHA512 の各 PKCS#1 署名メソッド、および SHA256、SHA384、SHA512 の各参照ダイジェスト アルゴリズムで、<xref:System.Security.Cryptography.Xml.SignedXml> クラスをさらに使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-576">.NET Framework 4.6.2 adds support to  the <xref:System.Security.Cryptography.Xml.SignedXml> class for RSA-SHA256, RSA-SHA384, and RSA-SHA512 PKCS#1 signature methods, and SHA256, SHA384, and SHA512 reference digest algorithms.</span></span>

<span data-ttu-id="39b71-577">以下のように、URI 定数はすべて <xref:System.Security.Cryptography.Xml.SignedXml> で示されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-577">The URI constants are all exposed on <xref:System.Security.Cryptography.Xml.SignedXml>:</span></span>

|<span data-ttu-id="39b71-578">SignedXml フィールド</span><span class="sxs-lookup"><span data-stu-id="39b71-578">SignedXml field</span></span>|<span data-ttu-id="39b71-579">定数</span><span class="sxs-lookup"><span data-stu-id="39b71-579">Constant</span></span>|
|---------------------|--------------|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|<span data-ttu-id="39b71-580">"http://www.w3.org/2001/04/xmlenc#sha256"</span><span class="sxs-lookup"><span data-stu-id="39b71-580">"http://www.w3.org/2001/04/xmlenc#sha256"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|<span data-ttu-id="39b71-581">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"</span><span class="sxs-lookup"><span data-stu-id="39b71-581">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|<span data-ttu-id="39b71-582">"http://www.w3.org/2001/04/xmldsig-more#sha384"</span><span class="sxs-lookup"><span data-stu-id="39b71-582">"http://www.w3.org/2001/04/xmldsig-more#sha384"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|<span data-ttu-id="39b71-583">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"</span><span class="sxs-lookup"><span data-stu-id="39b71-583">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|<span data-ttu-id="39b71-584">"http://www.w3.org/2001/04/xmlenc#sha512"</span><span class="sxs-lookup"><span data-stu-id="39b71-584">"http://www.w3.org/2001/04/xmlenc#sha512"</span></span>|
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|<span data-ttu-id="39b71-585">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"</span><span class="sxs-lookup"><span data-stu-id="39b71-585">"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"</span></span>|

 <span data-ttu-id="39b71-586">これらのアルゴリズムのサポートを追加するためにカスタムの <xref:System.Security.Cryptography.SignatureDescription> ハンドラーを <xref:System.Security.Cryptography.CryptoConfig> に登録していたプログラムはすべて従来どおり引き続き機能しますが、既定でプラットフォームでサポートされるようになったため、<xref:System.Security.Cryptography.CryptoConfig> への登録は不要になりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-586">Any programs that have registered a custom <xref:System.Security.Cryptography.SignatureDescription> handler into <xref:System.Security.Cryptography.CryptoConfig> to add support for these algorithms will continue to function as they did in the past, but since there are now platform defaults, the <xref:System.Security.Cryptography.CryptoConfig> registration is no longer necessary.</span></span>

<a name="SQLClient"></a>

### <a name="sqlclient"></a><span data-ttu-id="39b71-587">SqlClient</span><span class="sxs-lookup"><span data-stu-id="39b71-587">SqlClient</span></span>

<span data-ttu-id="39b71-588">.NET Framework 4.6.2 では、.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>) に次の新機能があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-588">.NET Framework Data Provider for SQL Server (<xref:System.Data.SqlClient?displayProperty=nameWithType>) includes the following new features in .NET Framework 4.6.2:</span></span>

<span data-ttu-id="39b71-589">**Azure SQL Database への接続プールとタイムアウト**</span><span class="sxs-lookup"><span data-stu-id="39b71-589">**Connection pooling and timeouts with Azure SQL databases**</span></span>

<span data-ttu-id="39b71-590">接続プールが有効な状態で、タイムアウトまたは他のログイン エラーが発生した場合は、例外がキャッシュされ、キャッシュされた例外は次の 5 秒から 1 分の間の後続の接続試行時にすべてスローされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-590">When connection pooling is enabled and a timeout or other login error occurs, an exception is cached, and the cached exception is thrown on any subsequent connection attempt for the next 5 seconds to 1 minute.</span></span> <span data-ttu-id="39b71-591">詳しくは、「[SQL Server の接続プール (ADO.NET)](../data/adonet/sql-server-connection-pooling.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-591">For more information, see [SQL Server Connection Pooling (ADO.NET)](../data/adonet/sql-server-connection-pooling.md).</span></span>

<span data-ttu-id="39b71-592">通常は迅速に復旧される一時的なエラーで接続試行が失敗する可能性があるため、Azure SQL Database への接続時のこの動作は望ましくありません。</span><span class="sxs-lookup"><span data-stu-id="39b71-592">This behavior is not desirable when connecting to Azure SQL Databases, since connection attempts can fail with transient errors that are typically recovered quickly.</span></span> <span data-ttu-id="39b71-593">接続試行操作をより最適化するため、Azure SQL Database への接続が失敗した場合は、接続プールのブロック期間の動作は削除されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-593">To better optimize the connection retry experience, the connection pool blocking period behavior is removed when connections to Azure SQL Databases fail.</span></span>

<span data-ttu-id="39b71-594">新しい `PoolBlockingPeriod` キーワードを追加することで、ご利用のアプリに最適なブロック期間を選択できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-594">The addition of the new `PoolBlockingPeriod` keyword lets you select the blocking period best suited for your app.</span></span> <span data-ttu-id="39b71-595">次の値が含まれます。</span><span class="sxs-lookup"><span data-stu-id="39b71-595">Values include:</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.Auto>

<span data-ttu-id="39b71-596">Azure SQL Database に接続しているアプリケーションの接続プールのブロック期間は無効になり、他のすべての SQL Server インスタンスに接続しているアプリケーションの接続プールのブロック期間が有効になります。</span><span class="sxs-lookup"><span data-stu-id="39b71-596">The connection pool blocking period for an application that connects to an Azure SQL Database is disabled, and the connection pool blocking period for an application that connects to any other SQL Server instance is enabled.</span></span> <span data-ttu-id="39b71-597">これが既定値です。</span><span class="sxs-lookup"><span data-stu-id="39b71-597">This is the default value.</span></span> <span data-ttu-id="39b71-598">サーバー エンドポイント名の末尾が以下のいずれかである場合は、Azure SQL Database と見なされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-598">If the Server endpoint name ends with any of the following, they are considered Azure SQL Databases:</span></span>

- <span data-ttu-id="39b71-599">.database.windows.net</span><span class="sxs-lookup"><span data-stu-id="39b71-599">.database.windows.net</span></span>

- <span data-ttu-id="39b71-600">.database.chinacloudapi.cn</span><span class="sxs-lookup"><span data-stu-id="39b71-600">.database.chinacloudapi.cn</span></span>

- <span data-ttu-id="39b71-601">.database.usgovcloudapi.net</span><span class="sxs-lookup"><span data-stu-id="39b71-601">.database.usgovcloudapi.net</span></span>

- <span data-ttu-id="39b71-602">.database.cloudapi.de</span><span class="sxs-lookup"><span data-stu-id="39b71-602">.database.cloudapi.de</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.AlwaysBlock>

<span data-ttu-id="39b71-603">接続プールのブロック期間は常に有効になります。</span><span class="sxs-lookup"><span data-stu-id="39b71-603">The connection pool blocking period is always enabled.</span></span>

<xref:System.Data.SqlClient.PoolBlockingPeriod.NeverBlock>

<span data-ttu-id="39b71-604">接続プールのブロック期間は常に無効になります。</span><span class="sxs-lookup"><span data-stu-id="39b71-604">The connection pool blocking period is always disabled.</span></span>

<span data-ttu-id="39b71-605">**Always Encrypted の強化**</span><span class="sxs-lookup"><span data-stu-id="39b71-605">**Enhancements for Always Encrypted**</span></span>

<span data-ttu-id="39b71-606">SQLClient では、Always Encrypted の以下の 2 つの機能が強化されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-606">SQLClient introduces two enhancements for Always Encrypted:</span></span>

- <span data-ttu-id="39b71-607">暗号化されたデータベースの列に対するパラメーター クエリのパフォーマンスを向上させるために、クエリ パラメーターの暗号化メタデータがキャッシュされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-607">To improve performance of parameterized queries against encrypted database columns, encryption metadata for query parameters is now cached.</span></span> <span data-ttu-id="39b71-608"><xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> プロパティが `true` (既定値) に設定されている状態で、同じクエリが複数回呼び出された場合、クライアントはサーバーからパラメーターのメタデータを 1 回だけ取得します。</span><span class="sxs-lookup"><span data-stu-id="39b71-608">With the <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=nameWithType> property set to `true` (which is the default value), if the same query is called multiple times, the client retrieves parameter metadata from the server only once.</span></span>

- <span data-ttu-id="39b71-609">キー キャッシュ内の列暗号化キー エントリは、<xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> プロパティを使用して設定された構成可能な時間間隔後に削除されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-609">Column encryption key entries in the key cache are now evicted after a configurable time interval, set using the <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=nameWithType> property.</span></span>

<a name="WCF"></a>

### <a name="windows-communication-foundation"></a><span data-ttu-id="39b71-610">Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="39b71-610">Windows Communication Foundation</span></span>

<span data-ttu-id="39b71-611">.NET Framework 4.6.2 では、Windows Communication Foundation の次の領域の機能が強化されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-611">In .NET Framework 4.6.2, Windows Communication Foundation has been enhanced in the following areas:</span></span>

<span data-ttu-id="39b71-612">**CNG を使用して格納される証明書の WCF トランスポート セキュリティ サポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-612">**WCF transport security support for certificates stored using CNG**</span></span>

<span data-ttu-id="39b71-613">WCF トランスポート セキュリティでは、Windows 暗号化ライブラリ (CNG) を使用して格納される証明書がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-613">WCF transport security supports certificates stored using the Windows cryptography library (CNG).</span></span> <span data-ttu-id="39b71-614">.NET Framework 4.6.2 では、このサポートは、指数の長さが 32 ビット以下の公開キーを持つ証明書を使う場合に限定されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-614">In .NET Framework 4.6.2, this support is limited to using certificates with a public key that has an exponent no more than 32 bits in length.</span></span> <span data-ttu-id="39b71-615">.NET Framework 4.6.2 を対象とするアプリケーションでは、この機能は既定で有効です。</span><span class="sxs-lookup"><span data-stu-id="39b71-615">When an application targets .NET Framework 4.6.2, this feature is on by default.</span></span>

<span data-ttu-id="39b71-616">.NET Framework 4.6.1 以前を対象とするアプリケーションが .NET Framework 4.6.2 で実行されている場合、app.config または web.config ファイルの [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) セクションに次の行を追加することで、この機能を有効にできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-616">For applications that target .NET Framework 4.6.1 and earlier but are running on .NET Framework 4.6.2, this feature can be enabled by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app.config or web.config file.</span></span>

```xml
<AppContextSwitchOverrides
    value="Switch.System.ServiceModel.DisableCngCertificates=false"
/>
```

<span data-ttu-id="39b71-617">以下のようなコードを使用してプログラムで行うこともできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-617">This can also be done programmatically with code like the following:</span></span>

```csharp
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";
AppContext.SetSwitch(disableCngCertificates, false);
```

```vb
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"
AppContext.SetSwitch(disableCngCertificates, False)
```

<span data-ttu-id="39b71-618">**DataContractJsonSerializer クラスによる複数の夏時間調整規則のサポート強化**</span><span class="sxs-lookup"><span data-stu-id="39b71-618">**Better support for multiple daylight saving time adjustment rules by the DataContractJsonSerializer class**</span></span>

<span data-ttu-id="39b71-619">お客様はアプリケーションの構成設定を使用して、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> クラスで 1 つのタイム ゾーンに対して複数の調整規則がサポートされているかどうかを判別することができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-619">Customers can use an application configuration setting to determine whether the <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> class supports multiple adjustment rules for a single time zone.</span></span> <span data-ttu-id="39b71-620">これはオプトイン機能です。</span><span class="sxs-lookup"><span data-stu-id="39b71-620">This is an opt-in feature.</span></span> <span data-ttu-id="39b71-621">これを有効にするには、app.config ファイルに次の設定を追加します。</span><span class="sxs-lookup"><span data-stu-id="39b71-621">To enable it, add the following setting to your app.config file:</span></span>

```xml
<runtime>
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />
</runtime>
```

<span data-ttu-id="39b71-622">この機能が有効な場合、<xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> オブジェクトは <xref:System.TimeZone> 型ではなく <xref:System.TimeZoneInfo> 型を使用して、日時データを逆シリアル化します。</span><span class="sxs-lookup"><span data-stu-id="39b71-622">When this feature is enabled, a <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> object uses the <xref:System.TimeZoneInfo> type instead of the <xref:System.TimeZone> type to deserialize date and time data.</span></span> <span data-ttu-id="39b71-623"><xref:System.TimeZoneInfo> では、<xref:System.TimeZone> でサポートされない複数の調整規則がサポートされるため、過去のタイム ゾーン データを操作できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-623"><xref:System.TimeZoneInfo> supports multiple adjustment rules, which makes it possible to work with historic time zone data;   <xref:System.TimeZone> does not.</span></span>

<span data-ttu-id="39b71-624"><xref:System.TimeZoneInfo> 構造体とタイム ゾーン調整の詳細については、「[タイム ゾーンの概要](../../standard/datetime/time-zone-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-624">For more information on the <xref:System.TimeZoneInfo> structure and time zone adjustments, see [Time Zone Overview](../../standard/datetime/time-zone-overview.md).</span></span>

<span data-ttu-id="39b71-625">**NetNamedPipeBinding の最適な一致**</span><span class="sxs-lookup"><span data-stu-id="39b71-625">**NetNamedPipeBinding best match**</span></span>

<span data-ttu-id="39b71-626">WCF には、クライアント アプリケーションで設定できる新しいアプリ設定があります。これにより、クライアント アプリケーションは常に、要求したものと最も一致する URI でリッスンしているサービスに接続できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-626">WCF has a new app setting that can be set on client applications to ensure they always connect to the service listening on the URI that best matches the one that they request.</span></span> <span data-ttu-id="39b71-627">このアプリ設定が `false` (既定値) に設定されている場合、クライアントは <xref:System.ServiceModel.NetNamedPipeBinding> を使用して、要求した URI の部分文字列である URI でリッスンしているサービスへの接続を試行できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-627">With this app setting set to `false` (the default), it is possible for clients using <xref:System.ServiceModel.NetNamedPipeBinding> to attempt to connect to a service listening on a URI that is a substring of the requested URI.</span></span>

<span data-ttu-id="39b71-628">たとえば、クライアントが `net.pipe://localhost/Service1` でリッスンしているサービスに接続しようとしているときに、管理者特権で実行しているコンピューター上の別のサービスが `net.pipe://localhost` でリッスンしているとします。</span><span class="sxs-lookup"><span data-stu-id="39b71-628">For example, a client tries to connect to a service listening at `net.pipe://localhost/Service1`, but a different service on that machine running with administrator privilege is listening at `net.pipe://localhost`.</span></span> <span data-ttu-id="39b71-629">このアプリ設定が `false` に設定されている場合、クライアントは間違ったサービスに接続しようとします。</span><span class="sxs-lookup"><span data-stu-id="39b71-629">With this app setting set to `false`, the client would attempt to connect to the wrong service.</span></span> <span data-ttu-id="39b71-630">アプリ設定を `true` に設定すれば、クライアントは常に最も一致するサービスに接続するようになります。</span><span class="sxs-lookup"><span data-stu-id="39b71-630">After setting the app setting to `true`, the client will always connect to the best matching service.</span></span>

> [!NOTE]
> <span data-ttu-id="39b71-631"><xref:System.ServiceModel.NetNamedPipeBinding> を使用するクライアントは、完全なエンドポイント アドレスではなく、サービスのベース アドレス (存在する場合) に基づいてサービスを検索します。</span><span class="sxs-lookup"><span data-stu-id="39b71-631">Clients using <xref:System.ServiceModel.NetNamedPipeBinding> find services based on the service's base address (if it exists) rather than the full endpoint address.</span></span> <span data-ttu-id="39b71-632">この設定が常に機能するようにするには、サービスは一意のベース アドレスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-632">To ensure this setting always works the service should use a unique base address.</span></span>

<span data-ttu-id="39b71-633">この変更を有効にするには、以下のアプリ設定をクライアント アプリケーションの App.config ファイルまたは Web.config ファイルに追加します。</span><span class="sxs-lookup"><span data-stu-id="39b71-633">To enable this change, add the following app setting to your client application's App.config or Web.config file:</span></span>

```xml
<configuration>
    <appSettings>
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />
    </appSettings>
</configuration>
```

<span data-ttu-id="39b71-634">**SSL 3.0 が既定のプロトコルではなくなった**</span><span class="sxs-lookup"><span data-stu-id="39b71-634">**SSL 3.0 is not a default protocol**</span></span>

<span data-ttu-id="39b71-635">トランスポート セキュリティで NetTcp を使用し、証明書の資格情報の種類を使用する場合、SSL 3.0 は、安全な接続のネゴシエーションに使用される既定のプロトコルではなくなりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-635">When using NetTcp with transport security and a credential type of certificate, SSL 3.0 is no longer a default protocol used for negotiating a secure connection.</span></span> <span data-ttu-id="39b71-636">TLS 1.0 が NetTcp のプロトコル一覧に含まれているため、ほとんどの場合、既存のアプリには影響はないと考えられます。</span><span class="sxs-lookup"><span data-stu-id="39b71-636">In most cases, there should be no impact to existing apps, because TLS 1.0 is included in the protocol list for NetTcp.</span></span> <span data-ttu-id="39b71-637">既存のすべてのクライアントは TLS 1.0 以降を使用して接続をネゴシエートできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-637">All existing clients should be able to negotiate a connection using at least TLS 1.0.</span></span> <span data-ttu-id="39b71-638">Ssl3 が必要な場合は、以下の構成メカニズムのいずれかを使用して、ネゴシエートされたプロトコルの一覧に追加します。</span><span class="sxs-lookup"><span data-stu-id="39b71-638">If Ssl3 is required, use one of the following configuration mechanisms to add it to the list of negotiated protocols.</span></span>

- <span data-ttu-id="39b71-639"><xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType> プロパティ</span><span class="sxs-lookup"><span data-stu-id="39b71-639">The <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=nameWithType> property</span></span>

- <span data-ttu-id="39b71-640"><xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> プロパティ</span><span class="sxs-lookup"><span data-stu-id="39b71-640">The <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=nameWithType> property</span></span>

- <span data-ttu-id="39b71-641">[\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md) セクションの [\<transport>](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) セクション</span><span class="sxs-lookup"><span data-stu-id="39b71-641">The [\<transport>](../configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) section of the [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md) section</span></span>

- <span data-ttu-id="39b71-642">[\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) セクションの [\<sslStreamSecurity>](../configure-apps/file-schema/wcf/sslstreamsecurity.md) セクション</span><span class="sxs-lookup"><span data-stu-id="39b71-642">The [\<sslStreamSecurity>](../configure-apps/file-schema/wcf/sslstreamsecurity.md) section of the [\<customBinding>](../configure-apps/file-schema/wcf/custombinding.md) section</span></span>

<a name="WPF462"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="39b71-643">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="39b71-643">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="39b71-644">.NET Framework 4.6.2 では、Windows Presentation Foundation の次の領域の機能が強化されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-644">In .NET Framework 4.6.2, Windows Presentation Foundation has been enhanced in the following areas:</span></span>

<span data-ttu-id="39b71-645">**グループの並べ替え**</span><span class="sxs-lookup"><span data-stu-id="39b71-645">**Group sorting**</span></span>

<span data-ttu-id="39b71-646"><xref:System.Windows.Data.CollectionView> オブジェクトを使用してデータをグループ化するアプリケーションは、グループを並べ替える方法を明示的に宣言できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-646">An application that uses a <xref:System.Windows.Data.CollectionView> object to group data can now explicitly declare how to  sort the groups.</span></span> <span data-ttu-id="39b71-647">明示的な並べ替えにより、アプリがグループを動的に追加または削除する場合や、グループ化に関連する項目のプロパティの値を変更する場合に発生する非直感的な順序付けの問題が解決されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-647">Explicit sorting addresses the problem of non-intuitive ordering that occurs when an app dynamically adds or removes groups, or when it changes the value of item properties involved in grouping.</span></span> <span data-ttu-id="39b71-648">また、グループ化プロパティの比較がコレクション全体の並べ替えからグループの並べ替えに変更されるため、グループ作成プロセスのパフォーマンスを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-648">It can also improve the performance of the group creation process by moving comparisons of the grouping properties from the sort of the full collection to the sort of the groups.</span></span>

<span data-ttu-id="39b71-649">グループの並べ替えをサポートするために、新しい <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> および <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> プロパティで、<xref:System.ComponentModel.GroupDescription> オブジェクトによって生成されるグループのコレクションを並べ替える方法が示されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-649">To support group sorting, the new <xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=nameWithType> and <xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=nameWithType> properties describe how to sort the collection of groups produced by the <xref:System.ComponentModel.GroupDescription> object.</span></span> <span data-ttu-id="39b71-650">これは、同じ名前の <xref:System.Windows.Data.ListCollectionView> プロパティでデータ項目を並べ替える方法を示すのと同様です。</span><span class="sxs-lookup"><span data-stu-id="39b71-650">This is analogous to the way the identically named <xref:System.Windows.Data.ListCollectionView> properties describe how to sort the data items.</span></span>

<span data-ttu-id="39b71-651"><xref:System.Windows.Data.PropertyGroupDescription> クラスの新しい 2 つの静的プロパティである <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> と <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A> は、最も一般的なケースで使用できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-651">Two new static properties of the <xref:System.Windows.Data.PropertyGroupDescription> class,  <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A> and <xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>, can be used for the most common cases.</span></span>

<span data-ttu-id="39b71-652">たとえば、次の XAML ではデータを年齢でグループ化し、年齢グループを昇順に並べ替え、各年齢グループ内の項目を姓でグループ化します。</span><span class="sxs-lookup"><span data-stu-id="39b71-652">For example, the following XAML groups data by age, sort the age groups in ascending order, and group the items within each age group by last name.</span></span>

```xaml
<GroupDescriptions>
     <PropertyGroupDescription
         PropertyName="Age"
         CustomSort=
              "{x:Static PropertyGroupDescription.CompareNamesAscending}"/>
     </PropertyGroupDescription>
</GroupDescriptions>

<SortDescriptions>
     <SortDescription PropertyName="LastName"/>
</SortDescriptions>
```

<span data-ttu-id="39b71-653">**タッチ キーボードのサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-653">**Touch keyboard support**</span></span>

<span data-ttu-id="39b71-654">タッチ キーボードのサポートにより、WPF アプリケーションでのフォーカス追跡が可能になります。テキスト入力が可能なコントロールによってタッチ入力が受信されると、Windows 10 の新しいタッチ キーボードが自動的に起動および終了します。</span><span class="sxs-lookup"><span data-stu-id="39b71-654">Touch keyboard support enables focus tracking in WPF applications by automatically invoking and dismissing the touch Keyboard in Windows 10 when the touch input is received by a control that can take textual input.</span></span>

<span data-ttu-id="39b71-655">.NET Framework の以前のバージョンでは、WPF アプリケーションで、WPF のペンまたはタッチ ジェスチャ サポートを無効にしないとフォーカス追跡を選択できません。</span><span class="sxs-lookup"><span data-stu-id="39b71-655">In previous versions of .NET Framework, WPF applications can't opt into the focus tracking without disabling WPF pen/touch gesture support.</span></span> <span data-ttu-id="39b71-656">そのため、WPF アプリケーションは完全な WPF タッチのフル サポートを選ぶか、Windows のマウス プロモーションに依存する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-656">As a result, WPF applications must choose between full WPF touch support or rely on Windows mouse promotion.</span></span>

<span data-ttu-id="39b71-657">**モニターごとの DPI**</span><span class="sxs-lookup"><span data-stu-id="39b71-657">**Per-monitor DPI**</span></span>

<span data-ttu-id="39b71-658">WPF アプリの最近の高 DPI とハイブリッド DPI 環境の急増に対応するため、.NET Framework 4.6.2 の WPF ではモニターごとの対応が可能になりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-658">To support the recent proliferation of high-DPI and hybrid-DPI environments for WPF apps, WPF in .NET Framework 4.6.2 enables per-monitor awareness.</span></span> <span data-ttu-id="39b71-659">ご使用の WPF アプリでモニターごとの DPI 対応を有効にする方法の詳細については、GitHub の[サンプルと開発者向けガイド](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-659">See the [samples and developer guide](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI) on GitHub for more information about how to enable your WPF app to become per-monitor DPI aware.</span></span>

<span data-ttu-id="39b71-660">.NET Framework の以前のバージョンでは、WPF アプリはシステム DPI 対応でした。</span><span class="sxs-lookup"><span data-stu-id="39b71-660">In previous versions of .NET Framework, WPF apps are system-DPI aware.</span></span> <span data-ttu-id="39b71-661">つまり、アプリケーションの UI は、アプリがレンダリングされるモニターの DPI に基づき、必要に応じて OS でスケーリングされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-661">In other words, the application's UI is scaled by the OS as appropriate, depending on the DPI of the monitor on which the app is rendered.</span></span>

<span data-ttu-id="39b71-662">.NET Framework 4.6.2 で実行されるアプリの場合、次のように、お使いのアプリケーションの構成ファイルの [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) セクションに構成ステートメントを追加して、WPF アプリでのモニターごとの DPI の変更を無効にできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-662">For apps running under .NET Framework 4.6.2, you can disable per-monitor DPI changes in WPF apps by adding a configuration statement to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of your application configuration file, as follows:</span></span>

```xml
<runtime>
   <AppContextSwitchOverrides value="Switch.System.Windows.DoNotScaleForDpiChanges=false"/>
</runtime>
```

<a name="WF462"></a>

### <a name="windows-workflow-foundation-wf"></a><span data-ttu-id="39b71-663">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="39b71-663">Windows Workflow Foundation (WF)</span></span>

<span data-ttu-id="39b71-664">.NET Framework 4.6.2 では、Windows Workflow Foundation の次領域の機能が強化されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-664">In .NET Framework 4.6.2, Windows Workflow Foundation has been enhanced in the following area:</span></span>

<span data-ttu-id="39b71-665">**再ホストされた WF デザイナーにおける C# 式と IntelliSense のサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-665">**Support for C# expressions and IntelliSense in the Rehosted WF Designer**</span></span>

<span data-ttu-id="39b71-666">.NET Framework 4.5 以降では、WF によって、Visual Studio デザイナーとコード ワークフローの両方で C# 式がサポートされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-666">Starting with .NET Framework 4.5, WF supports C# expressions in both the Visual Studio Designer and in code workflows.</span></span> <span data-ttu-id="39b71-667">再ホストされたワークフロー デザイナーは WF の主な機能です。これにより、ワークフロー デザイナーを Visual Studio の外部のアプリケーション (WPF など) で使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="39b71-667">The Rehosted Workflow Designer is a key feature of WF that allows for the Workflow Designer to be in an application outside Visual Studio (for example, in WPF).</span></span>  <span data-ttu-id="39b71-668">Windows Workflow Foundation は、再ホストされたワークフロー デザイナーで C# 式と IntelliSense をサポートできるようにします。</span><span class="sxs-lookup"><span data-stu-id="39b71-668">Windows Workflow Foundation provides the ability to support C# expressions and IntelliSense in the Rehosted Workflow Designer.</span></span> <span data-ttu-id="39b71-669">詳細については、[Windows Workflow Foundation のブログ](/archive/blogs/workflowteam/building-c-expressions-support-and-intellisense-in-the-rehosted-workflow-designer)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-669">For more information, see the [Windows Workflow Foundation blog](/archive/blogs/workflowteam/building-c-expressions-support-and-intellisense-in-the-rehosted-workflow-designer).</span></span>

<span data-ttu-id="39b71-670">`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio` 4.6.2 より前のバージョンの .NET Framework で、お客様が Visual Studio からワークフロー プロジェクトを再ビルドした場合、WF Designer IntelliSense は破損してしまいます。</span><span class="sxs-lookup"><span data-stu-id="39b71-670">`Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio` In versions of the .NET Framework prior to 4.6.2, WF Designer IntelliSense is broken when a customer rebuilds a workflow project from Visual Studio.</span></span> <span data-ttu-id="39b71-671">プロジェクトのビルドに成功しても、デザイナーでワークフローの種類が見つからず、 **[エラー一覧]** ウィンドウにワークフローの種類が欠落していることを示す IntelliSense からの警告が表示されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-671">While the project build is successful, the workflow types are not found on the designer, and warnings from IntelliSense for the missing workflow types appear in the **Error List** window.</span></span> <span data-ttu-id="39b71-672">.NET Framework 4.6.2 ではこのイシューに対処し、IntelliSense を使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="39b71-672">.NET Framework 4.6.2 addresses this issue and makes IntelliSense available.</span></span>

<span data-ttu-id="39b71-673">**ワークフロー追跡を有効にしたワークフロー V1 アプリケーションを FIPS モードで実行**</span><span class="sxs-lookup"><span data-stu-id="39b71-673">**Workflow V1 applications with Workflow Tracking on now run under FIPS-mode**</span></span>

<span data-ttu-id="39b71-674">FIPS コンプライアンス モードが有効なコンピューターで、ワークフロー追跡が有効なワークフロー バージョン 1 スタイルのアプリケーションを正常に実行できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-674">Machines with FIPS Compliance Mode enabled can now successfully run a workflow Version 1-style application with Workflow tracking on.</span></span> <span data-ttu-id="39b71-675">このシナリオを有効にするには、app.config ファイルを以下のように変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-675">To enable this scenario, you must make the following change to your app.config file:</span></span>

```xml
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />
```

<span data-ttu-id="39b71-676">このシナリオが有効でない場合、アプリケーションを実行すると、引き続き例外が生成され、"この実装は Windows プラットフォーム FIPS 検証暗号化アルゴリズムの一部ではありません" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-676">If this scenario is not enabled, running the application continues to generate an exception with the message, "This implementation is not part of the Windows Platform FIPS validated cryptographic algorithms."</span></span>

<span data-ttu-id="39b71-677">**Visual Studio ワークフロー デザイナーで動的更新を使用する場合のワークフローの改善**</span><span class="sxs-lookup"><span data-stu-id="39b71-677">**Workflow Improvements when using Dynamic Update with Visual Studio Workflow Designer**</span></span>

<span data-ttu-id="39b71-678">ワークフロー デザイナー、フローチャート アクティビティ デザイナー、およびその他のワークフロー アクティビティ デザイナーで、<xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> メソッドを呼び出した後に保存されたワークフローが正常に読み込まれ、表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-678">The Workflow Designer, FlowChart Activity Designer, and other Workflow Activity Designers now successfully load and display workflows that have been saved after calling  the <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="39b71-679">.NET Framework 4.6.2 より前のバージョンの .NET Framework では、<xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> を呼び出した後に保存されたワークフローの XAML ファイルを Visual Studio で読み込むと、以下の問題が発生する場合がありました。</span><span class="sxs-lookup"><span data-stu-id="39b71-679">In versions of the .NET Framework before .NET Framework 4.6.2, loading a XAML file in Visual Studio for a workflow that has been saved after calling <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=nameWithType> can result in the following issues:</span></span>

- <span data-ttu-id="39b71-680">ワークフロー デザイナーで XAML ファイルが正しく読み込めない (行の末尾に <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> がある場合)。</span><span class="sxs-lookup"><span data-stu-id="39b71-680">The Workflow Designer can't load the XAML file correctly (when the <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=nameWithType> is at the end of the line).</span></span>

- <span data-ttu-id="39b71-681">フローチャート アクティビティ デザイナーまたは他のワークフロー アクティビティ デザイナーで、アタッチされるプロパティの値ではなく既定の場所にすべてのオブジェクトが表示される場合がある。</span><span class="sxs-lookup"><span data-stu-id="39b71-681">Flowchart Activity Designer or other Workflow Activity Designers may display all objects in their default locations as opposed to attached property values.</span></span>

<a name="clickonce-1"></a>

### <a name="clickonce"></a><span data-ttu-id="39b71-682">ClickOnce</span><span class="sxs-lookup"><span data-stu-id="39b71-682">ClickOnce</span></span>

<span data-ttu-id="39b71-683">ClickOnce が更新され、既にサポートされている 1.0 プロトコルに加え、TLS 1.1 と TLS 1.2 がサポートがサポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-683">ClickOnce has been updated to support TLS 1.1 and TLS 1.2 in addition to the 1.0 protocol, which it already supports.</span></span> <span data-ttu-id="39b71-684">ClickOnce が必要なプロトコルを自動的に検出するため、TLS 1.1 と 1.2 のサポートを有効にするために、ClickOnce アプリケーション内での追加の手順は不要です。</span><span class="sxs-lookup"><span data-stu-id="39b71-684">ClickOnce automatically detects which protocol is required; no extra steps within the ClickOnce application are required to enable TLS 1.1 and 1.2 support.</span></span>

<a name="UWPConvert"></a>

### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a><span data-ttu-id="39b71-685">Windows フォームおよび WPF アプリの UWP アプリへの変換</span><span class="sxs-lookup"><span data-stu-id="39b71-685">Converting Windows Forms and WPF apps to  UWP apps</span></span>

<span data-ttu-id="39b71-686">Windows では、WPF および Windows フォーム アプリを含む、既存の Windows デスクトップ アプリを UWP (ユニバーサル Windows プラットフォーム) で使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-686">Windows now offers capabilities to bring existing Windows desktop apps, including WPF and Windows Forms apps, to the Universal Windows Platform (UWP).</span></span> <span data-ttu-id="39b71-687">このテクノロジはブリッジとして機能し、既存のコード ベースを段階的に UWP に移行し、アプリをすべての Windows 10 デバイスで使用できるようにします。</span><span class="sxs-lookup"><span data-stu-id="39b71-687">This technology acts as a bridge by enabling you to gradually migrate your existing code base to UWP, thereby bringing your app to all Windows 10 devices.</span></span>

<span data-ttu-id="39b71-688">変換後のデスクトップ アプリは UWP アプリのアプリ ID のようなアプリ ID を取得し、UWP API をアクセス可能にして、ライブ タイルや通知などの機能を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-688">Converted desktop apps gain an app identity similar to the app identity of UWP apps, which makes UWP APIs accessible to enable features such as Live Tiles and notifications.</span></span> <span data-ttu-id="39b71-689">アプリは引き続き従来どおり動作し、完全信頼アプリとして実行されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-689">The app continues to behave as before and runs as a full trust app.</span></span> <span data-ttu-id="39b71-690">アプリが変換されたら、アプリ コンテナー プロセスを既存の完全信頼プロセスに追加し、適応ユーザー インターフェイスを追加できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-690">Once the app is converted, an app container process can be added to the existing full trust process to add an adaptive user interface.</span></span> <span data-ttu-id="39b71-691">すべての機能がアプリ コンテナー プロセスに移行されたら、完全信頼プロセスを削除し、新しい UWP アプリをすべての Windows 10 デバイスで有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-691">When all functionality is moved to the app container process, the full trust process can be removed and the new UWP app can be made available to all Windows 10 devices.</span></span>

<a name="Debug462"></a>

### <a name="debugging-improvements"></a><span data-ttu-id="39b71-692">デバッグの機能強化</span><span class="sxs-lookup"><span data-stu-id="39b71-692">Debugging improvements</span></span>

<span data-ttu-id="39b71-693">.NET Framework 4.6.2 で *アンマネージ デバッグ API* が強化され、<xref:System.NullReferenceException> がスローされたときに、ソース コードの単一行でどの変数が `null` になっているかを判別できるように、さらに分析されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-693">The *unmanaged debugging API* has been enhanced in .NET Framework 4.6.2 to perform additional analysis when a <xref:System.NullReferenceException> is thrown so that it is possible to determine which variable in a single line of source code is `null`.</span></span>   <span data-ttu-id="39b71-694">このシナリオをサポートするために、次の API がアンマネージ デバッグ API に追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-694">To support this scenario, the following APIs have been added to the unmanaged debugging API.</span></span>

- <span data-ttu-id="39b71-695">[ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md)、[ICorDebugVariableHome](../unmanaged-api/debugging/icordebugvariablehome-interface.md)、および [ICorDebugVariableHomeEnum](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) インターフェイス。これらは管理対象変数の元のホームを公開します。</span><span class="sxs-lookup"><span data-stu-id="39b71-695">The [ICorDebugCode4](../unmanaged-api/debugging/icordebugcode4-interface.md), [ICorDebugVariableHome](../unmanaged-api/debugging/icordebugvariablehome-interface.md), and [ICorDebugVariableHomeEnum](../unmanaged-api/debugging/icordebugvariablehomeenum-interface.md) interfaces, which expose the native homes of managed variables.</span></span> <span data-ttu-id="39b71-696">これにより、デバッガーは、<xref:System.NullReferenceException> の発生時になんらかのコード フロー分析を行い、さかのぼって、`null` だった元の場所に対応する管理対象変数を判別できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-696">This enables debuggers to do some code flow analysis when a  <xref:System.NullReferenceException> occurs and to work backwards to determine the managed variable that corresponds to the native location that was `null`.</span></span>

- <span data-ttu-id="39b71-697">[ICorDebugType2::GetTypeID](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) メソッドでは ICorDebugType を [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) にマッピングできます。これにより、デバッガーは、ICorDebugType のインスタンスがなくても [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) を取得できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-697">The [ICorDebugType2::GetTypeID](../unmanaged-api/debugging/icordebugtype2-gettypeid-method.md) method provides a mapping for ICorDebugType to [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md), which allows the debugger to obtain a [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) without an instance of the ICorDebugType.</span></span> <span data-ttu-id="39b71-698">その後、[COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) で既存の API を使用して、型のクラス レイアウトを判別できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-698">Existing APIs on [COR_TYPEID](../unmanaged-api/debugging/cor-typeid-structure.md) can then be used to determine the class layout of the type.</span></span>

<a name="v461"></a>

## <a name="whats-new-in-net-framework-461"></a><span data-ttu-id="39b71-699">.NET Framework 4.6.1 の新機能</span><span class="sxs-lookup"><span data-stu-id="39b71-699">What's new in .NET Framework 4.6.1</span></span>

<span data-ttu-id="39b71-700">.NET Framework 4.6.1 には、次の領域に新機能があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-700">.NET Framework 4.6.1 includes new features in the following areas:</span></span>

- [<span data-ttu-id="39b71-701">暗号</span><span class="sxs-lookup"><span data-stu-id="39b71-701">Cryptography</span></span>](#Crypto)

- [<span data-ttu-id="39b71-702">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="39b71-702">ADO.NET</span></span>](#ADO.NET461)

- [<span data-ttu-id="39b71-703">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="39b71-703">Windows Presentation Foundation (WPF)</span></span>](#WPF461)

- [<span data-ttu-id="39b71-704">Windows Workflow Foundation</span><span class="sxs-lookup"><span data-stu-id="39b71-704">Windows Workflow Foundation</span></span>](#WWF461)

- [<span data-ttu-id="39b71-705">プロファイル</span><span class="sxs-lookup"><span data-stu-id="39b71-705">Profiling</span></span>](#Profile461)

- [<span data-ttu-id="39b71-706">NGen</span><span class="sxs-lookup"><span data-stu-id="39b71-706">NGen</span></span>](#NGEN461)

<span data-ttu-id="39b71-707">.NET Framework 4.6.1 の詳細については、次のトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-707">For more information on .NET Framework 4.6.1, see the following topics:</span></span>

- [<span data-ttu-id="39b71-708">.NET Framework 4.6.1 の変更の一覧</span><span class="sxs-lookup"><span data-stu-id="39b71-708">.NET Framework 4.6.1 list of changes</span></span>](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-changes.md)

- [<span data-ttu-id="39b71-709">4.6.1 でのアプリケーションの互換性</span><span class="sxs-lookup"><span data-stu-id="39b71-709">Application Compatibility in 4.6.1</span></span>](../migration-guide/application-compatibility.md)

- <span data-ttu-id="39b71-710">[.NET Framework API の diff (差分)](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-api-changes.md) (GitHub 上)</span><span class="sxs-lookup"><span data-stu-id="39b71-710">[.NET Framework API diff](https://github.com/Microsoft/dotnet/blob/master/releases/net461/dotnet461-api-changes.md) (on GitHub)</span></span>

<a name="Crypto"></a>

### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a><span data-ttu-id="39b71-711">暗号: ECDSA を含む X509 証明書のサポート</span><span class="sxs-lookup"><span data-stu-id="39b71-711">Cryptography: Support for X509 certificates containing ECDSA</span></span>

<span data-ttu-id="39b71-712">.NET Framework 4.6 では、X509 証明書の RSACng サポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-712">.NET Framework 4.6 added RSACng support for X509 certificates.</span></span> <span data-ttu-id="39b71-713">.NET Framework 4.6.1 に、ECDSA (Elliptic Curve Digital Signature Algorithm: 楕円曲線デジタル署名アルゴリズム) X509 証明書のサポートが追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-713">.NET Framework 4.6.1 adds support for ECDSA (Elliptic Curve Digital Signature Algorithm) X509 certificates.</span></span>

<span data-ttu-id="39b71-714">ECDSA は、RSA よりも安全な暗号化アルゴリズムで、パフォーマンスも向上するため、トランスポート層セキュリティ (TLS) のパフォーマンスとスケーラビリティが問題になる場合に最適な選択肢です。</span><span class="sxs-lookup"><span data-stu-id="39b71-714">ECDSA offers better performance and is a more secure cryptography algorithm than RSA, providing an excellent choice where Transport Layer Security (TLS) performance and scalability is a concern.</span></span> <span data-ttu-id="39b71-715">.NET Framework の実装では、既存の Windows 機能の呼び出しがラップされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-715">The .NET Framework implementation wraps calls into existing Windows functionality.</span></span>

<span data-ttu-id="39b71-716">次のサンプル コードは、.NET Framework 4.6.1 で新規にサポートされ含まれる ECDSA X509 証明書を使って、バイト ストリームの署名が簡単に生成できることを示しています。</span><span class="sxs-lookup"><span data-stu-id="39b71-716">The following example code shows how easy it is to generate a signature for a byte stream by using the new  support for ECDSA  X509 certificates included in .NET Framework 4.6.1.</span></span>

[!code-csharp[whatsnew.461.crypto#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
[!code-vb[whatsnew.461.crypto#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]

<span data-ttu-id="39b71-717">このコードは、.NET Framework 4.6 での署名の生成に必要な次のコードとは大きく異なっています。</span><span class="sxs-lookup"><span data-stu-id="39b71-717">This offers a marked contrast to the code needed to generate a signature in .NET Framework 4.6.</span></span>

[!code-csharp[whatsnew.461.crypto#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
[!code-vb[whatsnew.461.crypto#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]

<a name="ADO.NET461"></a>

### <a name="adonet"></a><span data-ttu-id="39b71-718">ADO.NET</span><span class="sxs-lookup"><span data-stu-id="39b71-718">ADO.NET</span></span>

<span data-ttu-id="39b71-719">次のものが ADO.NET に追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-719">The following have been added to ADO.NET:</span></span>

<span data-ttu-id="39b71-720">**ハードウェア保護キーに対する Always Encrypted のサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-720">**Always Encrypted support for hardware protected keys**</span></span>

<span data-ttu-id="39b71-721">ADO.NET では、Always Encrypted 列 (常に暗号化される列) のマスター キーをハードウェア セキュリティ モジュール (HSM) に格納することが、ネイティブでサポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-721">ADO.NET now supports storing Always Encrypted column master keys natively in Hardware Security Modules (HSMs).</span></span> <span data-ttu-id="39b71-722">このサポートによって、ユーザーは、HSM に格納された非対称キーを利用できます。カスタムの列マスター キー ストア プロバイダーを作成してからアプリケーションに登録する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="39b71-722">With this support, customers can leverage asymmetric keys stored in HSMs without having to write custom column master key store providers and registering them in applications.</span></span>

<span data-ttu-id="39b71-723">HSM に格納された列マスター キーで保護された Always Encrypted データにアクセスするには、HSM ベンダー提供の CSP プロバイダーまたは CNG キー ストア プロバイダーをアプリ サーバーまたはクライアント コンピューターにインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-723">Customers need to install the HSM vendor-provided CSP provider or CNG key store providers on the app servers or client computers in order to access Always Encrypted data protected with column master keys stored in a HSM.</span></span>

<span data-ttu-id="39b71-724">**AlwaysOn に対する <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> の接続動作の向上**</span><span class="sxs-lookup"><span data-stu-id="39b71-724">**Improved <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> connection behavior for AlwaysOn**</span></span>

<span data-ttu-id="39b71-725">SqlClient で、AlwaysOn 可用性グループ (AG) へのより高速な接続が自動的に提供されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-725">SqlClient now automatically provides faster connections to an AlwaysOn Availability Group (AG).</span></span> <span data-ttu-id="39b71-726">SqlClient では、アプリケーションが別のサブネット上の AlwaysOn 可用性グループ (AG) に接続しているかどうかを自動的に検出し、現在のアクティブなサーバーを迅速に探索し、そのサーバーへの接続を提供します。</span><span class="sxs-lookup"><span data-stu-id="39b71-726">It transparently detects whether your application is connecting to an AlwaysOn availability group (AG) on a different subnet and quickly discovers the current active server and provides a connection to the server.</span></span> <span data-ttu-id="39b71-727">このリリースよりも前は、アプリケーションで接続文字列を設定し、`"MultisubnetFailover=true"` を含め、AlwaysOn 可用性グループに接続されていることを示す必要がありました。</span><span class="sxs-lookup"><span data-stu-id="39b71-727">Prior to this release, an application had to set the connection string to include `"MultisubnetFailover=true"` to indicate that it was connecting to an AlwaysOn Availability Group.</span></span> <span data-ttu-id="39b71-728">`true` への接続キーワードを設定しないと、アプリケーションで AlwaysOn 可用性グループに接続中にタイムアウトが発生する可能性がありました。</span><span class="sxs-lookup"><span data-stu-id="39b71-728">Without setting the connection keyword to `true`, an application might experience a timeout while connecting to an AlwaysOn Availability Group.</span></span> <span data-ttu-id="39b71-729">このリリースを使用すれば、アプリケーションで <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> を `true` に設定する必要が *なくなり* ます。</span><span class="sxs-lookup"><span data-stu-id="39b71-729">With this release, an application does *not* need to set <xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> to `true` anymore.</span></span> <span data-ttu-id="39b71-730">Always On 可用性グループの SqlClient サポートの詳細については、「[高可用性障害復旧のための SqlClient サポート](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-730">For more information about SqlClient support for Always On Availability Groups, see [SqlClient Support for High Availability, Disaster Recovery](../data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md).</span></span>

<a name="WPF461"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="39b71-731">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="39b71-731">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="39b71-732">Windows Presentation Foundation には、さまざまな改善と変更が含まれています。</span><span class="sxs-lookup"><span data-stu-id="39b71-732">Windows Presentation Foundation includes a number of improvements and changes.</span></span>

<span data-ttu-id="39b71-733">**パフォーマンスの向上**</span><span class="sxs-lookup"><span data-stu-id="39b71-733">**Improved performance**</span></span>

<span data-ttu-id="39b71-734">.NET Framework 4.6.1 で、タッチ イベントの開始の遅延が修正されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-734">The delay in firing touch events has been fixed in .NET Framework 4.6.1.</span></span> <span data-ttu-id="39b71-735">また、<xref:System.Windows.Controls.RichTextBox> コントロールの入力が高速入力時のレンダーのスレッドを停止させなくなりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-735">In addition, typing in a <xref:System.Windows.Controls.RichTextBox> control no longer ties up the render thread during fast input.</span></span>

<span data-ttu-id="39b71-736">**スペル チェック機能の改善**</span><span class="sxs-lookup"><span data-stu-id="39b71-736">**Spell checking improvements**</span></span>

<span data-ttu-id="39b71-737">WPF のスペル チェック機能が、追加の言語のスペル チェックのためにオペレーティング システムのサポートを利用するように、Windows 8.1 以降のバージョンで更新されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-737">The spell checker in WPF has been updated on Windows 8.1 and later versions to leverage operating system support for spell-checking additional languages.</span></span>  <span data-ttu-id="39b71-738">Windows 8.1 よりも前の Windows バージョンの機能の変更はありません。</span><span class="sxs-lookup"><span data-stu-id="39b71-738">There is no change in functionality on Windows versions prior to Windows 8.1.</span></span>

<span data-ttu-id="39b71-739"><xref:System.Windows.Controls.TextBox> コントロールまたは <xref:System.Windows.Controls.RichTextBox> ブロックの言語は、以前のバージョンの .NET Framework と同様に、次の順序で情報を探し検出されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-739">As in previous versions of .NET Framework, the language for a <xref:System.Windows.Controls.TextBox> control ora <xref:System.Windows.Controls.RichTextBox> block is detected by looking for information in the following order:</span></span>

- <span data-ttu-id="39b71-740">`xml:lang` (存在する場合)。</span><span class="sxs-lookup"><span data-stu-id="39b71-740">`xml:lang`, if it is present.</span></span>

- <span data-ttu-id="39b71-741">現在の入力言語。</span><span class="sxs-lookup"><span data-stu-id="39b71-741">Current input language.</span></span>

- <span data-ttu-id="39b71-742">現在のスレッド カルチャ。</span><span class="sxs-lookup"><span data-stu-id="39b71-742">Current thread culture.</span></span>

<span data-ttu-id="39b71-743">WPF での言語サポートの詳細については、[.NET Framework 4.6.1 機能に関する WPF ブログの記事](https://devblogs.microsoft.com/wpf/wpf-in-net-4-6-1/)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-743">For more information on language support in WPF, see the [WPF blog post on .NET Framework 4.6.1 features](https://devblogs.microsoft.com/wpf/wpf-in-net-4-6-1/).</span></span>

<span data-ttu-id="39b71-744">**ユーザーごとのユーザー辞書の追加サポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-744">**Additional support for per-user custom dictionaries**</span></span>

<span data-ttu-id="39b71-745">.NET Framework 4.6.1 では、WPF で、グローバルに登録されているユーザー辞書が認識されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-745">In .NET Framework 4.6.1, WPF recognizes custom dictionaries that are registered globally.</span></span> <span data-ttu-id="39b71-746">この機能は、ユーザー辞書をコントロールごとに登録する機能に加えて使用できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-746">This capability is available in addition to the ability to register them per-control.</span></span>

<span data-ttu-id="39b71-747">以前のバージョンの WPF では、ユーザー辞書で除外された単語とオートコレクト リストが認識されませんでした。</span><span class="sxs-lookup"><span data-stu-id="39b71-747">In previous versions of WPF, custom dictionaries did not recognize Excluded Words and AutoCorrect lists.</span></span> <span data-ttu-id="39b71-748">`%AppData%\Microsoft\Spelling\<language tag>` ディレクトリに配置できるファイルの使用によって、これらが Windows 8.1 と Windows 10 でサポートされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-748">They are supported on Windows 8.1 and Windows 10 through the use of files that can be placed under the `%AppData%\Microsoft\Spelling\<language tag>` directory.</span></span>  <span data-ttu-id="39b71-749">これらのファイルには、次の規則が適用されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-749">The following rules apply to these files:</span></span>

- <span data-ttu-id="39b71-750">これらのファイルには、拡張子の .dic (追加された単語の場合)、.exc (除外された単語の場合)、または .acl (オートコレクトの場合) が付いている必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-750">The files should have extensions of .dic (for added words), .exc (for excluded words), or .acl (for AutoCorrect).</span></span>

- <span data-ttu-id="39b71-751">これらのファイルは、バイト オーダー マーク (BOM) で始まる UTF-16 LE プレーン テキストである必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-751">The files should be UTF-16 LE plaintext that starts with the Byte Order Mark (BOM).</span></span>

- <span data-ttu-id="39b71-752">それぞれの行は、1 つの単語 (追加および除外された単語の一覧内)、または単語が縦棒 ("&#124;") で区切られたオートコレクトのペア (オートコレクトの単語の一覧内) で構成される必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-752">Each line should consist of a word (in the added and excluded word lists), or an autocorrect pair with the words separated by a vertical bar ("&#124;") (in the AutoCorrect word list).</span></span>

- <span data-ttu-id="39b71-753">これらのファイルは読み取り専用と見なされ、システムによって変更されることはありません。</span><span class="sxs-lookup"><span data-stu-id="39b71-753">These files are considered read-only and are not modified by the system.</span></span>

> [!NOTE]
> <span data-ttu-id="39b71-754">これらの新しいファイル形式は、WPF スペル チェック API で直接サポートされるわけではありません。また、アプリケーションで WPF に提供されるユーザー辞書では以前と同様に .lex ファイルを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-754">These new file-formats are not directly supported by the WPF spell checking APIs, and the custom dictionaries supplied to WPF in applications should continue to use .lex files.</span></span>

<span data-ttu-id="39b71-755">**サンプル**</span><span class="sxs-lookup"><span data-stu-id="39b71-755">**Samples**</span></span>

<span data-ttu-id="39b71-756">WPF のサンプルは、[Microsoft/WPF サンプル](https://github.com/Microsoft/WPF-Samples) GitHub リポジトリにいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="39b71-756">There are a number of WPF samples on the [Microsoft/WPF-Samples](https://github.com/Microsoft/WPF-Samples) GitHub repository.</span></span> <span data-ttu-id="39b71-757">プル要求を送信するか、または[GitHub issue (GitHub の問題)](https://github.com/Microsoft/WPF-Samples/issues) を開いて、これらのサンプルの改善にご協力ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-757">Help us improve our samples by sending us a pull-request or opening a [GitHub issue](https://github.com/Microsoft/WPF-Samples/issues).</span></span>

<span data-ttu-id="39b71-758">**DirectX の拡張機能**</span><span class="sxs-lookup"><span data-stu-id="39b71-758">**DirectX extensions**</span></span>

<span data-ttu-id="39b71-759">WPF には、DX10 および Dx11 のコンテンツとの相互運用を容易にする、<xref:System.Windows.Interop.D3DImage> の新しい実装を提供する [NuGet パッケージ](https://www.nuget.org/packages/Microsoft.Wpf.Interop.DirectX-x86/)が含まれています。</span><span class="sxs-lookup"><span data-stu-id="39b71-759">WPF includes a [NuGet package](https://www.nuget.org/packages/Microsoft.Wpf.Interop.DirectX-x86/) that provides new implementations of <xref:System.Windows.Interop.D3DImage> that make it easy for you to interoperate with DX10 and Dx11 content.</span></span> <span data-ttu-id="39b71-760">このパッケージのコードはオープン ソース化されており、[GitHub で](https://github.com/Microsoft/WPFDXInterop)入手できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-760">The code for this package has been open sourced and is available [on GitHub](https://github.com/Microsoft/WPFDXInterop).</span></span>

<a name="WWF461"></a>

### <a name="windows-workflow-foundation-transactions"></a><span data-ttu-id="39b71-761">Windows Workflow Foundation: トランザクション</span><span class="sxs-lookup"><span data-stu-id="39b71-761">Windows Workflow Foundation: Transactions</span></span>

<span data-ttu-id="39b71-762"><xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> メソッドで、MSDTC 以外の分散トランザクション マネージャーを使用して、トランザクションをプロモート (昇格) できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-762">The <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> method can now use a distributed transaction manager other than MSDTC to promote the transaction.</span></span> <span data-ttu-id="39b71-763">このプロモートは、新しい <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> オーバーロードに GUID のトランザクション プロモーター識別子を指定することによって行います。</span><span class="sxs-lookup"><span data-stu-id="39b71-763">You do this by specifying a GUID transaction promoter identifier to the  new <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> overload .</span></span> <span data-ttu-id="39b71-764">この操作が成功すると、そのトランザクションの機能に制限が加えられます。</span><span class="sxs-lookup"><span data-stu-id="39b71-764">If this operation is successful, there are limitations placed on the capabilities of the transaction.</span></span> <span data-ttu-id="39b71-765">MSDTC 以外のトランザクション プロモーターが登録される (参加する) と、次の各メソッドで MSDTC へのプロモートが必要になるため、これらのメソッドで <xref:System.Transactions.TransactionPromotionException> がスローされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-765">Once a non-MSDTC transaction promoter is enlisted, the following methods throw a <xref:System.Transactions.TransactionPromotionException> because these methods require promotion to MSDTC:</span></span>

- <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=nameWithType>

- <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=nameWithType>

<span data-ttu-id="39b71-766">MSDTC 以外のトランザクション プロモーターが登録されると、そのプロモーターで定義するプロトコルを使用することで、そのプロモーターをその後の永続参加リストに使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-766">Once a non-MSDTC transaction promoter is enlisted, it must be used for future durable enlistments by using protocols that it defines.</span></span> <span data-ttu-id="39b71-767">トランザクション プロモーターの <xref:System.Guid> は、<xref:System.Transactions.Transaction.PromoterType%2A> プロパティを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-767">The <xref:System.Guid> of the transaction promoter can be obtained by using the <xref:System.Transactions.Transaction.PromoterType%2A> property.</span></span> <span data-ttu-id="39b71-768">トランザクションがプロモートする際、トランザクション プロモーターによって、プロモート済みトークンを表す <xref:System.Byte> 配列が提供されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-768">When the transaction promotes, the transaction promoter provides a <xref:System.Byte> array that represents the promoted token.</span></span> <span data-ttu-id="39b71-769">アプリケーションで、MSDTC 以外のプロモート済みトランザクションのプロモート済みトークンを <xref:System.Transactions.Transaction.GetPromotedToken%2A> メソッドを使用して取得できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-769">An application can obtain the promoted token for a non-MSDTC promoted transaction with the <xref:System.Transactions.Transaction.GetPromotedToken%2A> method.</span></span>

<span data-ttu-id="39b71-770">新しい <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> オーバーロードのユーザーは、プロモーション操作が正常に完了するように、特定の呼び出しシーケンスに従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-770">Users of the new <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=nameWithType> overload must follow a specific call sequence in order for the promotion operation to complete successfully.</span></span> <span data-ttu-id="39b71-771">これらの規則は、メソッドのドキュメントに記載されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-771">These rules are documented in the method's documentation.</span></span>

<a name="Profile461"></a>

### <a name="profiling"></a><span data-ttu-id="39b71-772">プロファイル</span><span class="sxs-lookup"><span data-stu-id="39b71-772">Profiling</span></span>

<span data-ttu-id="39b71-773">アンマネージド プロファイリング API が、次のように拡張されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-773">The unmanaged profiling API has been enhanced as follows:</span></span>

- <span data-ttu-id="39b71-774">[ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) インターフェイス内の PDB へのアクセスのサポートが向上。</span><span class="sxs-lookup"><span data-stu-id="39b71-774">Better support for accessing PDBs in the [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) interface.</span></span>

  <span data-ttu-id="39b71-775">ASP.NET Core では、アセンブリがメモリ内で Roslyn によってコンパイルされることがよりいっそう一般的になっています。</span><span class="sxs-lookup"><span data-stu-id="39b71-775">In ASP.NET Core, it is becoming much more common for assemblies to be compiled in-memory by Roslyn.</span></span> <span data-ttu-id="39b71-776">プロファイル ツールを作成する開発者にとって、これは従来ディスクにシリアル化されていた PDB が存在しなくなる可能性があることを意味しています。</span><span class="sxs-lookup"><span data-stu-id="39b71-776">For developers making profiling tools, this means that PDBs that historically were serialized on disk may no longer be present.</span></span> <span data-ttu-id="39b71-777">プロファイル ツールでは、多くの場合 PDB を使用して、コード カバレッジや 1 行単位のパフォーマンス分析などのタスクのソース行に、コードをマップし戻します。</span><span class="sxs-lookup"><span data-stu-id="39b71-777">Profiler tools often use PDBs to map code back to source lines for tasks such as code coverage or line-by-line performance analysis.</span></span> <span data-ttu-id="39b71-778">[ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) インターフェイスは、メモリ内の PDB データにアクセスして、これらのプロファイル ツールを提供する 2 つの新しいメソッド、[ICorProfilerInfo7::GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) と [ICorProfilerInfo7::ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md) を含むようになりました。これらの新しい API を使用すれば、プロファイラーでメモリ内の PDB の内容をバイト配列として取得してから、それを処理したり、ディスクにシリアル化したりできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-778">The [ICorProfilerInfo7](../unmanaged-api/profiling/icorprofilerinfo7-interface.md) interface now includes two new methods, [ICorProfilerInfo7::GetInMemorySymbolsLength](../unmanaged-api/profiling/icorprofilerinfo7-getinmemorysymbolslength-method.md) and [ICorProfilerInfo7::ReadInMemorySymbols](../unmanaged-api/profiling/icorprofilerinfo7-readinmemorysymbols.md), to provide these profiler tools with access to the in-memory PDB data, By using the new APIs, a profiler can obtain the contents of an in-memory PDB as a byte array and then process it or serialize it to disk.</span></span>

- <span data-ttu-id="39b71-779">ICorProfiler インターフェイスを使用したインストルメンテーションの改善。</span><span class="sxs-lookup"><span data-stu-id="39b71-779">Better instrumentation with the ICorProfiler interface.</span></span>

  <span data-ttu-id="39b71-780">動的インストルメンテーションに `ICorProfiler` API ReJit 機能を使用しているプロファイラーで、いくつかのメタデータを変更できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-780">Profilers that are using the `ICorProfiler` APIs ReJit functionality for dynamic instrumentation can now modify some metadata.</span></span> <span data-ttu-id="39b71-781">従来、このようなツールでは、いつでも IL をインストルメント化できましたが、メタデータを変更できるのはモジュールを読み込む時だけでした。</span><span class="sxs-lookup"><span data-stu-id="39b71-781">Previously such tools could instrument IL at any time, but metadata could only be modified at module load time.</span></span> <span data-ttu-id="39b71-782">IL はメタデータを参照するため、実行できるインストルメンテーションの種類が限られています。</span><span class="sxs-lookup"><span data-stu-id="39b71-782">Because IL refers to metadata, this limited the kinds of instrumentation that could be done.</span></span> <span data-ttu-id="39b71-783">モジュールの読み込み後のメタデータの編集のサブセットをサポートするために、[ICorProfilerInfo7::ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) メソッドを追加することで (特に新しい `AssemblyRef`、`TypeRef`、`TypeSpec`、`MemberRef`、`MemberSpec`、および `UserString` の各レコードを追加することで)、これらの制限の一部を解消しました。</span><span class="sxs-lookup"><span data-stu-id="39b71-783">We have lifted some of those limits by adding the [ICorProfilerInfo7::ApplyMetaData](../unmanaged-api/profiling/icorprofilerinfo7-applymetadata-method.md) method to support a subset of metadata edits after the module loads, in particular by adding new `AssemblyRef`, `TypeRef`, `TypeSpec`, `MemberRef`, `MemberSpec`, and `UserString` records.</span></span> <span data-ttu-id="39b71-784">この変更により、はるかに広範な実行時インストルメンテーションが可能になります。</span><span class="sxs-lookup"><span data-stu-id="39b71-784">This change makes a much broader range of on-the-fly instrumentation possible.</span></span>

<a name="NGEN461"></a>

### <a name="native-image-generator-ngen-pdbs"></a><span data-ttu-id="39b71-785">ネイティブ イメージ ジェネレーター (NGEN) PDB</span><span class="sxs-lookup"><span data-stu-id="39b71-785">Native Image Generator (NGEN) PDBs</span></span>

<span data-ttu-id="39b71-786">マシン間のイベント トレースを使用すれば、ユーザーはマシン A 上でプログラムをプロファイリングし、マシン B 上でソース行のマッピングを使用して、プロファイリング データを確認できます。以前のバージョンの .NET Framework で、ソースからネイティブへのマッピングを作成するには、ユーザーは、プロファイルされたコンピューターにあるすべてのモジュールとネイティブ イメージを、IL PDB が含まれた分析用コンピューターにコピーする必要がありました。</span><span class="sxs-lookup"><span data-stu-id="39b71-786">Cross-machine event tracing allows customers to profile a program on Machine A and look at the profiling data with source line mapping on Machine B. Using previous versions of .NET Framework, the user would copy all the modules and native images from the profiled machine to the analysis machine that contains the IL PDB to create the source-to-native mapping.</span></span> <span data-ttu-id="39b71-787">この処理は、Phone アプリケーションなどファイル サイズが比較的小さい場合には高速に実行されますが、これらのファイルのサイズがデスクトップ システム上で非常に大きくなる可能性があり、その場合コピーにかなりの時間を要する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-787">While this process may work well when the files are relatively small, such as for phone applications, the files can be very large on desktop systems and require significant time to copy.</span></span>

<span data-ttu-id="39b71-788">NGen PDB を使用すれば、IL PDB に依存することなく、NGen で IL からネイティブへのマッピングが含まれた PDB を作成できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-788">With Ngen PDBs, NGen can create a PDB that contains the IL-to-native mapping without a dependency on the IL PDB.</span></span> <span data-ttu-id="39b71-789">このマシン間のイベント トレース シナリオで必要なことは、コンピューター A で生成されたネイティブ イメージの PDB をコンピューター B にコピーすることと、[Debug Interface Access API](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) を使用して IL PDB のソースから IL へのマッピングとネイティブ イメージの PDB の IL からネイティブへのマッピングを読み取ることだけです。</span><span class="sxs-lookup"><span data-stu-id="39b71-789">In our cross-machine event tracing scenario, all that is needed is to copy the native image PDB that is generated by Machine A to Machine B and to use [Debug Interface Access APIs](/visualstudio/debugger/debug-interface-access/debug-interface-access-sdk-reference) to read the IL PDB's source-to-IL mapping and the native image PDB's IL-to-native mapping.</span></span> <span data-ttu-id="39b71-790">両方のマッピングを組み合わせることで、ソースからネイティブへのマッピングが実現します。</span><span class="sxs-lookup"><span data-stu-id="39b71-790">Combining both mappings provides a source-to-native mapping.</span></span> <span data-ttu-id="39b71-791">ネイティブ イメージの PDB は、どのモジュールとネイティブ イメージよりもはるかにサイズが小さいため、コンピューター A からコンピューター B へのコピーの処理は非常に高速になります。</span><span class="sxs-lookup"><span data-stu-id="39b71-791">Since the native image PDB is much smaller than all the modules and native images, the process of copying from Machine A to Machine B is much faster.</span></span>

<a name="v46"></a>

## <a name="whats-new-in-net-2015"></a><span data-ttu-id="39b71-792">.NET 2015 の新機能</span><span class="sxs-lookup"><span data-stu-id="39b71-792">What's new in .NET 2015</span></span>

<span data-ttu-id="39b71-793">.NET 2015 には、.NET Framework 4.6 と .NET Core が実装されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-793">.NET 2015 introduces .NET Framework 4.6 and .NET Core.</span></span> <span data-ttu-id="39b71-794">一部の新機能はその両方に適用され、その他の機能は .NET Framework 4.6 または .NET Core に固有です。</span><span class="sxs-lookup"><span data-stu-id="39b71-794">Some new features apply to both, and other features are specific to .NET Framework 4.6 or .NET Core.</span></span>

- <span data-ttu-id="39b71-795">**ASP.NET Core**</span><span class="sxs-lookup"><span data-stu-id="39b71-795">**ASP.NET Core**</span></span>

  <span data-ttu-id="39b71-796">.NET 2015 には、ASP.NET Core が含まれています。これは、最新のクラウド ベースのアプリを構築するのに効率的な .NET 実装です。</span><span class="sxs-lookup"><span data-stu-id="39b71-796">.NET 2015 includes ASP.NET Core, which is a lean .NET implementation for building modern cloud-based apps.</span></span> <span data-ttu-id="39b71-797">ASP.NET Core はモジュール形式であるため、ご利用のアプリケーションで必要な機能のみを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-797">ASP.NET Core is modular so you can include only those features that are needed in your application.</span></span> <span data-ttu-id="39b71-798">IIS でホストすることも、カスタムのプロセスでセルフホストすることもできます。さらに同じサーバー上のさまざまなバージョンの .NET Framework でアプリを実行することも可能です。</span><span class="sxs-lookup"><span data-stu-id="39b71-798">It can be hosted on IIS or self-hosted in a custom process, and you can run apps with different versions of the .NET Framework on the same server.</span></span> <span data-ttu-id="39b71-799">クラウド展開用に設計されている新たな環境構成システムが含まれています。</span><span class="sxs-lookup"><span data-stu-id="39b71-799">It includes a new environment configuration system that is designed for cloud deployment.</span></span>

  <span data-ttu-id="39b71-800">MVC、Web API、および Web ページは、MVC 6 と呼ばれる 1 つのフレームワークに統合されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-800">MVC, Web API, and Web Pages are unified into a single framework called MVC 6.</span></span> <span data-ttu-id="39b71-801">Visual Studio 2015 以降のツールで ASP.NET Core アプリをビルドします。</span><span class="sxs-lookup"><span data-stu-id="39b71-801">You build ASP.NET Core apps through tools in Visual Studio 2015 or later.</span></span> <span data-ttu-id="39b71-802">既存のアプリケーションは、この新しい .NET Framework で動作しますが、MVC 6 または SignalR 3 を使用するアプリをビルドするには Visual Studio 2015 以降のプロジェクト システムを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-802">Your existing applications will work on the new .NET Framework; however to build an app that uses MVC 6 or SignalR 3, you must use the project system in Visual Studio 2015 or later.</span></span>

  <span data-ttu-id="39b71-803">詳細については、[ASP.NET Core](/aspnet/core/) に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-803">For information, see [ASP.NET Core](/aspnet/core/).</span></span>

- <span data-ttu-id="39b71-804">**ASP.NET の更新プログラム**</span><span class="sxs-lookup"><span data-stu-id="39b71-804">**ASP.NET Updates**</span></span>

  - <span data-ttu-id="39b71-805">**非同期応答フラッシュ用のタスク ベース API**</span><span class="sxs-lookup"><span data-stu-id="39b71-805">**Task-based API for Asynchronous Response Flushing**</span></span>

    <span data-ttu-id="39b71-806">ASP.NET で、非同期応答フラッシュ用の単純なタスク ベース API である <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType> が提供されるようになりました。これにより、言語の `async/await` サポートを使用して非同期的に応答をフラッシュできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-806">ASP.NET now provides a simple task-based API for asynchronous response flushing, <xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=nameWithType>, that allows responses to be flushed asynchronously by using your language's `async/await` support.</span></span>

  - <span data-ttu-id="39b71-807">**モデル バインドによるタスクを返すメソッドのサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-807">**Model binding supports task-returning methods**</span></span>

    <span data-ttu-id="39b71-808">.NET Framework 4.5 の ASP.NET に、Web フォーム ページやユーザー コントロールでの CRUD ベースのデータ操作で、拡張可能なコード中心のアプローチを可能にするモデル バインド機能が追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-808">In .NET Framework 4.5, ASP.NET added the Model Binding feature that enabled an extensible, code-focused approach to CRUD-based data operations in Web Forms pages and user controls.</span></span> <span data-ttu-id="39b71-809">このモデル バインド システムで、<xref:System.Threading.Tasks.Task> を返すモデル バインド メソッドがサポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-809">The Model Binding system now supports <xref:System.Threading.Tasks.Task>-returning model binding methods.</span></span> <span data-ttu-id="39b71-810">この機能により、Web フォーム開発者は Entity Framework などの ORM の新しいバージョンを使用するときに、データ バインド システムのように簡単に非同期のスケーラビリティ上のメリットを得ることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-810">This feature allows Web Forms developers to get the scalability benefits of async with the ease of the data-binding system when using newer versions of ORMs, including the Entity Framework.</span></span>

    <span data-ttu-id="39b71-811">非同期モデル バインドは、`aspnet:EnableAsyncModelBinding` 構成設定によって制御されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-811">Async model binding is controlled by the `aspnet:EnableAsyncModelBinding` configuration setting.</span></span>

    ```xml
    <appSettings>
        <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />
    </appSettings>
    ```

    <span data-ttu-id="39b71-812">.NET Framework 4.6 を対象とするアプリでの既定は、`true` です。</span><span class="sxs-lookup"><span data-stu-id="39b71-812">On apps the target .NET Framework 4.6, it defaults to `true`.</span></span> <span data-ttu-id="39b71-813">.NET Framework 4.6 で実行され、.NET Framework の以前のバージョンを対象とするアプリでの既定は、`false` です。</span><span class="sxs-lookup"><span data-stu-id="39b71-813">On apps running on .NET Framework 4.6 that target an earlier version of .NET Framework, it is `false` by default.</span></span> <span data-ttu-id="39b71-814">有効にするには、この構成設定を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="39b71-814">It can be enabled by setting the configuration setting to `true`.</span></span>

  - <span data-ttu-id="39b71-815">**HTTP/2 のサポート (Windows 10)**</span><span class="sxs-lookup"><span data-stu-id="39b71-815">**HTTP/2 Support (Windows 10)**</span></span>

    <span data-ttu-id="39b71-816">[HTTP/2](https://www.wikipedia.org/wiki/HTTP/2) は HTTP プロトコルの新しいバージョンで、接続の使用状況が (クライアントとサーバー間のラウンド トリップ数の減少により) 大幅に改善されて、ユーザーが Web ページを読み込むときの遅延が軽減されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-816">[HTTP/2](https://www.wikipedia.org/wiki/HTTP/2) is a new version of the HTTP protocol that provides much better connection utilization (fewer round-trips between client and server), resulting in lower latency web page loading for users.</span></span>  <span data-ttu-id="39b71-817">このプロトコルは単一のエクスペリエンスの一部として要求さる複数の成果物のために最適化されているので、HTTP/2 が最も役立つのは (サービスではなく) web ページです。</span><span class="sxs-lookup"><span data-stu-id="39b71-817">Web pages (as opposed to services) benefit the most from HTTP/2, since the protocol optimizes for multiple artifacts being requested as part of a single experience.</span></span> <span data-ttu-id="39b71-818">.NET Framework 4.6 では、HTTP/2 のサポートが ASP.NET に追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-818">HTTP/2 support has been added to ASP.NET in .NET Framework 4.6.</span></span> <span data-ttu-id="39b71-819">ネットワーク機能は複数のレイヤーで存在するので、HTTP/2 を有効にするために、Windows、IIS、および ASP.NET で新機能が必要とされていました。</span><span class="sxs-lookup"><span data-stu-id="39b71-819">Because networking functionality exists at multiple layers, new features were required in Windows, in IIS, and in ASP.NET to enable HTTP/2.</span></span> <span data-ttu-id="39b71-820">ASP.NET で HTTP/2 を使用するには、Windows 10 を実行している必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-820">You must be running on Windows 10 to use HTTP/2 with ASP.NET.</span></span>

    <span data-ttu-id="39b71-821">HTTP/2 は、<xref:System.Net.Http.HttpClient?displayProperty=nameWithType> API を使用する Windows 10 ユニバーサル Windows プラットフォーム (UWP) アプリでもサポートされ、既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="39b71-821">HTTP/2 is also supported and on by default for Windows 10 Universal Windows Platform (UWP) apps that use the <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> API.</span></span>

    <span data-ttu-id="39b71-822">ASP.NET アプリケーションで [PUSH_PROMISE](https://httpwg.github.io/http2-spec/#PUSH_PROMISE) 機能を使用する手段を提供するために、<xref:System.Web.HttpResponse.PushPromise%28System.String%29> と <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29> の 2 つのオーバーロードを持つ新しいメソッドが <xref:System.Web.HttpResponse> クラスに追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-822">In order to provide a way to use the [PUSH_PROMISE](https://httpwg.github.io/http2-spec/#PUSH_PROMISE) feature in ASP.NET applications, a new method with two overloads, <xref:System.Web.HttpResponse.PushPromise%28System.String%29> and <xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>, has been added to the <xref:System.Web.HttpResponse> class.</span></span>

    > [!NOTE]
    > <span data-ttu-id="39b71-823">ASP.NET Core では HTTP/2 がサポートされますが、PUSH PROMISE 機能のサポートはまだ追加されていません。</span><span class="sxs-lookup"><span data-stu-id="39b71-823">While ASP.NET Core supports HTTP/2, support for the PUSH PROMISE feature has not yet been added.</span></span>

    <span data-ttu-id="39b71-824">ブラウザーと web サーバー (Windows 上の IIS) がすべての処理を実行します。</span><span class="sxs-lookup"><span data-stu-id="39b71-824">The browser and the web server (IIS on Windows) do all the work.</span></span> <span data-ttu-id="39b71-825">ユーザーの側で複雑な操作を実行する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="39b71-825">You don't have to do any heavy-lifting for your users.</span></span>

    <span data-ttu-id="39b71-826">[主要なブラウザーのほとんどは HTTP/2 をサポートしている](https://www.wikipedia.org/wiki/HTTP/2)ため、多くの場合、サーバーが HTTP/2 をサポートしていれば、ユーザーもそのメリットを得ることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-826">Most of the [major browsers support HTTP/2](https://www.wikipedia.org/wiki/HTTP/2), so it's likely that your users will benefit from HTTP/2 support if your server supports it.</span></span>

  - <span data-ttu-id="39b71-827">**トークン バインディング プロトコルのサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-827">**Support for the Token Binding Protocol**</span></span>

    <span data-ttu-id="39b71-828">Microsoft と Google は、[トークン バインディング プロトコル](https://github.com/TokenBinding/Internet-Drafts)と呼ばれる、認証のための新しいアプローチに共同で取り組んできました。</span><span class="sxs-lookup"><span data-stu-id="39b71-828">Microsoft and Google have been collaborating on a new approach to authentication, called the [Token Binding Protocol](https://github.com/TokenBinding/Internet-Drafts).</span></span> <span data-ttu-id="39b71-829">この前提となっているのは、犯罪者が (ブラウザー キャッシュ内の) 認証トークンを盗用することで、本来ならパスワードや他の特別な情報でセキュリティ保護されているリソース (銀行口座など) にアクセスできる可能性がある、ということです。</span><span class="sxs-lookup"><span data-stu-id="39b71-829">The premise is that authentication tokens (in your browser cache) can be stolen and used by criminals to access otherwise secure resources (for example, your bank account) without requiring your password or any other privileged knowledge.</span></span> <span data-ttu-id="39b71-830">新しいプロトコルは、この問題を軽減することを目指しています。</span><span class="sxs-lookup"><span data-stu-id="39b71-830">The new protocol aims to mitigate this problem.</span></span>

    <span data-ttu-id="39b71-831">トークン バインディング プロトコルは、Windows 10 でブラウザーの機能として実装されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-831">The Token Binding Protocol will be implemented in Windows 10 as a browser feature.</span></span> <span data-ttu-id="39b71-832">ASP.NET アプリは、認証トークンの正当性が検証されるように、このプロトコルに参加します。</span><span class="sxs-lookup"><span data-stu-id="39b71-832">ASP.NET apps will participate in the protocol, so that authentication tokens are validated to be legitimate.</span></span> <span data-ttu-id="39b71-833">クライアントとサーバーの実装は、プロトコルによって指定されるエンド ツー エンドの保護を確立します。</span><span class="sxs-lookup"><span data-stu-id="39b71-833">The client and the server implementations establish the end-to-end protection specified by the protocol.</span></span>

  - <span data-ttu-id="39b71-834">**ランダムな文字列のハッシュ アルゴリズム**</span><span class="sxs-lookup"><span data-stu-id="39b71-834">**Randomized string hash algorithms**</span></span>

    <span data-ttu-id="39b71-835">.NET Framework 4.5 で、[ランダム化された文字列のハッシュ アルゴリズム](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)が導入されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-835">.NET Framework 4.5 introduced a [randomized string hash algorithm](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span></span> <span data-ttu-id="39b71-836">しかし、ASP.NET の一部の機能は安定したハッシュ コードに依存していたため、この機能は ASP.NET ではサポートされませんでした。</span><span class="sxs-lookup"><span data-stu-id="39b71-836">However, it was not supported by ASP.NET because of some ASP.NET features depended on a stable hash code.</span></span> <span data-ttu-id="39b71-837">.NET Framework 4.6 では、ランダムな文字列のハッシュ アルゴリズムがサポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-837">In .NET Framework 4.6, randomized string hash algorithms are now supported.</span></span> <span data-ttu-id="39b71-838">この機能を有効にするには、`aspnet:UseRandomizedStringHashAlgorithm` 構成設定を使用します。</span><span class="sxs-lookup"><span data-stu-id="39b71-838">To enable this feature, use the `aspnet:UseRandomizedStringHashAlgorithm` config setting.</span></span>

    ```xml
    <appSettings>
        <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />
    </appSettings>
    ```

- <span data-ttu-id="39b71-839">**ADO.NET**</span><span class="sxs-lookup"><span data-stu-id="39b71-839">**ADO.NET**</span></span>

  <span data-ttu-id="39b71-840">ADO .NET では、SQL Server 2016 Community Technology Preview 2 (CTP2) で使用できる Always Encrypted 機能がサポートされました。</span><span class="sxs-lookup"><span data-stu-id="39b71-840">ADO .NET now supports the Always Encrypted feature available in SQL Server 2016 Community Technology Preview 2 (CTP2).</span></span> <span data-ttu-id="39b71-841">SQL Server は、Always Encrypted 機能を使用して、暗号化されたデータに対して操作を実行できます。特に、サーバー上ではなく、ユーザーが信頼している環境内にアプリケーションと共に暗号化キーを保存できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-841">With Always Encrypted, SQL Server can perform operations on encrypted data, and best of all the encryption key resides with the application inside the customer's trusted environment and not on the server.</span></span> <span data-ttu-id="39b71-842">Always Encrypted でユーザー データが保護されるので、DBA はプレーン テキスト データにアクセスできません。</span><span class="sxs-lookup"><span data-stu-id="39b71-842">Always Encrypted secures customer data so DBAs do not have access to plain text data.</span></span> <span data-ttu-id="39b71-843">データの暗号化と復号化は、ドライバー レベルで透過的に行われるので、既存のアプリケーションに対する変更が最小限に抑えられます。</span><span class="sxs-lookup"><span data-stu-id="39b71-843">Encryption and decryption of data happens transparently at the driver level, minimizing changes that have to be made to existing applications.</span></span> <span data-ttu-id="39b71-844">詳細については、「[Always Encrypted (データベース エンジン)](/sql/relational-databases/security/encryption/always-encrypted-database-engine)」および「[Always Encrypted (クライアント開発)](/sql/relational-databases/security/encryption/always-encrypted-client-development)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-844">For details, see [Always Encrypted (Database Engine)](/sql/relational-databases/security/encryption/always-encrypted-database-engine) and [Always Encrypted (client development)](/sql/relational-databases/security/encryption/always-encrypted-client-development).</span></span>

- <span data-ttu-id="39b71-845">**マネージド コードの JIT コンパイラ (64 ビット)**</span><span class="sxs-lookup"><span data-stu-id="39b71-845">**64-bit JIT Compiler for managed code**</span></span>

  <span data-ttu-id="39b71-846">.NET Framework 4.6 の特徴の 1 つとして、新しいバージョンの 64 ビット JIT コンパイラ (RyuJIT というコードネームで呼ばれていたもの) があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-846">.NET Framework 4.6 features a new version of the 64-bit JIT compiler (originally code-named RyuJIT).</span></span> <span data-ttu-id="39b71-847">この新しい 64 ビット コンパイラは、これまでの 64 ビット JIT コンパイラよりもパフォーマンスが大幅に向上しています。</span><span class="sxs-lookup"><span data-stu-id="39b71-847">The new 64-bit compiler provides significant performance improvements over the older 64-bit JIT compiler.</span></span> <span data-ttu-id="39b71-848">新しい 64 ビット コンパイラは、.NET Framework 4.6 上で実行される 64 ビット プロセスで有効になります。</span><span class="sxs-lookup"><span data-stu-id="39b71-848">The new 64-bit compiler is enabled for 64-bit processes running on top of .NET Framework 4.6.</span></span> <span data-ttu-id="39b71-849">64 ビットまたは AnyCPU としてコンパイルされ、64 ビット オペレーティング システム上で実行されるアプリは、64 ビットで動作します。</span><span class="sxs-lookup"><span data-stu-id="39b71-849">Your app will run in a 64-bit process if it is compiled as 64-bit or AnyCPU and is running on a 64-bit operating system.</span></span> <span data-ttu-id="39b71-850">新しいコンパイラへの移行をできる限り透過的に行うように注意を払いましたが、動作の変更が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-850">While care has been taken to make the transition to the new compiler as transparent as possible, changes in behavior are possible.</span></span>

  <span data-ttu-id="39b71-851">新しい 64 ビット JIT コンパイラには、ハードウェア SIMD アクセラレータ機能も含まれています。これを <xref:System.Numerics> 名前空間の SIMD 対応の型と組み合わせると、パフォーマンスが大幅に向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-851">The new 64-bit JIT compiler also includes hardware SIMD acceleration features when coupled with SIMD-enabled types in the <xref:System.Numerics> namespace, which can yield good performance improvements.</span></span>

- <span data-ttu-id="39b71-852">**アセンブリ ローダーの改善**</span><span class="sxs-lookup"><span data-stu-id="39b71-852">**Assembly loader improvements**</span></span>

  <span data-ttu-id="39b71-853">アセンブリ ローダーで、対応する NGEN イメージの読み込み後に IL アセンブリをアンロードすることにより、メモリがより効率的に使用されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-853">The assembly loader now uses memory more efficiently by unloading IL assemblies after a corresponding NGEN image is loaded.</span></span> <span data-ttu-id="39b71-854">この変更は、仮想メモリが減少するため、特に大規模な 32 ビット アプリ (Visual Studio など) で有益であり、物理メモリの節約にもなります。</span><span class="sxs-lookup"><span data-stu-id="39b71-854">This change decreases virtual memory, which is particularly beneficial for large 32-bit apps (such as Visual Studio), and also saves physical memory.</span></span>

- <span data-ttu-id="39b71-855">**基本クラス ライブラリの変更点**</span><span class="sxs-lookup"><span data-stu-id="39b71-855">**Base class library changes**</span></span>

  <span data-ttu-id="39b71-856">主なシナリオを利用できるようにするため、多くの新しい API が .NET Framework 4.6 に関連して追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-856">Many new APIs have been added around to .NET Framework 4.6 to enable key scenarios.</span></span> <span data-ttu-id="39b71-857">変更点と追加点を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="39b71-857">These include the following changes and additions:</span></span>

  - <span data-ttu-id="39b71-858">**IReadOnlyCollection\<T> implementations**</span><span class="sxs-lookup"><span data-stu-id="39b71-858">**IReadOnlyCollection\<T> implementations**</span></span>

    <span data-ttu-id="39b71-859">追加のコレクション <xref:System.Collections.Generic.IReadOnlyCollection%601> (<xref:System.Collections.Generic.Queue%601>、<xref:System.Collections.Generic.Stack%601> など) が実装されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-859">Additional collections implement <xref:System.Collections.Generic.IReadOnlyCollection%601> such as <xref:System.Collections.Generic.Queue%601> and <xref:System.Collections.Generic.Stack%601>.</span></span>

  - <span data-ttu-id="39b71-860">**CultureInfo.CurrentCulture と CultureInfo.CurrentUICulture**</span><span class="sxs-lookup"><span data-stu-id="39b71-860">**CultureInfo.CurrentCulture and CultureInfo.CurrentUICulture**</span></span>

    <span data-ttu-id="39b71-861"><xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> プロパティと <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> プロパティが読み取り専用ではなく、読み取り/書き込み可能になりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-861">The <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> and <xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=nameWithType> properties are now read-write rather than read-only.</span></span> <span data-ttu-id="39b71-862">新しい <xref:System.Globalization.CultureInfo> オブジェクトをこれらのプロパティに割り当てると、`Thread.CurrentThread.CurrentCulture` プロパティで現在定義されているスレッド カルチャと、`Thread.CurrentThread.CurrentUICulture` プロパティで現在定義されている UI スレッド カルチャも変更されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-862">If you assign a new <xref:System.Globalization.CultureInfo> object to these properties, the current thread culture defined by the `Thread.CurrentThread.CurrentCulture` property and the current UI thread culture defined by the `Thread.CurrentThread.CurrentUICulture` properties also change.</span></span>

  - <span data-ttu-id="39b71-863">**ガベージ コレクション (GC) の機能強化**</span><span class="sxs-lookup"><span data-stu-id="39b71-863">**Enhancements to garbage collection (GC)**</span></span>

    <span data-ttu-id="39b71-864"><xref:System.GC> クラスに <xref:System.GC.TryStartNoGCRegion%2A> メソッドと <xref:System.GC.EndNoGCRegion%2A> メソッドが含まれるようになりました。これらのメソッドを使用するとクリティカル パスの実行中にガベージ コレクションを不許可にできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-864">The <xref:System.GC> class now includes <xref:System.GC.TryStartNoGCRegion%2A> and <xref:System.GC.EndNoGCRegion%2A> methods that allow you to disallow garbage collection during the execution of a critical path.</span></span>

    <span data-ttu-id="39b71-865"><xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> メソッドの新しいオーバーロードを使用して、小さなオブジェクト ヒープと大きなオブジェクト ヒープの両方に関して、スイープして圧縮するのか、スイープのみを行うのかを制御できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-865">A new overload of the <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=nameWithType> method allows you to control whether both the small object heap and the large object heap are swept and compacted or swept only.</span></span>

  - <span data-ttu-id="39b71-866">**SIMD が有効な型**</span><span class="sxs-lookup"><span data-stu-id="39b71-866">**SIMD-enabled types**</span></span>

    <span data-ttu-id="39b71-867"><xref:System.Numerics> 名前空間には、<xref:System.Numerics.Matrix3x2>、<xref:System.Numerics.Matrix4x4>、<xref:System.Numerics.Plane>、<xref:System.Numerics.Quaternion>、<xref:System.Numerics.Vector2>、<xref:System.Numerics.Vector3>、<xref:System.Numerics.Vector4> など、いくつかの SIMD 対応の型が含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-867">The <xref:System.Numerics> namespace now includes a number of SIMD-enabled types, such as <xref:System.Numerics.Matrix3x2>, <xref:System.Numerics.Matrix4x4>, <xref:System.Numerics.Plane>, <xref:System.Numerics.Quaternion>, <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4>.</span></span>

    <span data-ttu-id="39b71-868">新しい 64 ビット JIT コンパイラにはハードウェア SIMD アクセラレータ機能も含まれているため、新しい 64 ビット JIT コンパイラで SIMD 対応の型を使用すると、パフォーマンスが大幅に向上します。</span><span class="sxs-lookup"><span data-stu-id="39b71-868">Because the new 64-bit JIT compiler also includes hardware SIMD acceleration features, there are especially significant performance improvements when using the SIMD-enabled types with the new 64-bit JIT compiler.</span></span>

  - <span data-ttu-id="39b71-869">**暗号の更新**</span><span class="sxs-lookup"><span data-stu-id="39b71-869">**Cryptography updates**</span></span>

    <span data-ttu-id="39b71-870"><xref:System.Security.Cryptography?displayProperty=nameWithType> API は、[Windows CNG 暗号化 API](/windows/desktop/SecCNG/cng-reference) をサポートするために更新中です。</span><span class="sxs-lookup"><span data-stu-id="39b71-870">The <xref:System.Security.Cryptography?displayProperty=nameWithType> API is being updated to support the [Windows CNG cryptography APIs](/windows/desktop/SecCNG/cng-reference).</span></span> <span data-ttu-id="39b71-871">以前のバージョンの .NET Framework は、<xref:System.Security.Cryptography?displayProperty=nameWithType> の実装の基礎として、[それより前のバージョンの Windows 暗号化 API](/windows/desktop/SecCrypto/cryptography-portal) に完全に依存していました。</span><span class="sxs-lookup"><span data-stu-id="39b71-871">Previous versions of the .NET Framework have relied entirely on an [earlier version of the Windows Cryptography APIs](/windows/desktop/SecCrypto/cryptography-portal) as the basis for the <xref:System.Security.Cryptography?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="39b71-872">CNG API は特定のカテゴリのアプリにとって重要な[最新の暗号アルゴリズム](/windows/desktop/SecCNG/cng-features#suite-b-support)をサポートするものであるため、CNG API をサポートしてほしいというリクエストが寄せられていました。</span><span class="sxs-lookup"><span data-stu-id="39b71-872">We have had requests to support the CNG API, since it supports [modern cryptography algorithms](/windows/desktop/SecCNG/cng-features#suite-b-support), which are important for certain categories of apps.</span></span>

    <span data-ttu-id="39b71-873">.NET Framework 4.6 には、Windows CNG 暗号化 API をサポートするために、次の新しい機能強化が含まれています。</span><span class="sxs-lookup"><span data-stu-id="39b71-873">.NET Framework 4.6 includes the following new enhancements to support the Windows CNG cryptography APIs:</span></span>

    - <span data-ttu-id="39b71-874">可能な場合に CAPI ベースの実装ではなく CNG ベースの実装を返す X509 証明書用の一連の拡張メソッド `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` および `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`</span><span class="sxs-lookup"><span data-stu-id="39b71-874">A set of extension methods for X509 Certificates, `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` and `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`, that return a CNG-based implementation rather than a CAPI-based implementation when possible.</span></span> <span data-ttu-id="39b71-875">(一部のスマート カードなどでは現在も CAPI が必要であり、API がフォールバックを処理します)。</span><span class="sxs-lookup"><span data-stu-id="39b71-875">(Some smartcards, etc., still require CAPI, and the APIs handle the fallback).</span></span>

    - <span data-ttu-id="39b71-876">RSA アルゴリズムの CNG 実装を提供する <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> クラス。</span><span class="sxs-lookup"><span data-stu-id="39b71-876">The <xref:System.Security.Cryptography.RSACng?displayProperty=nameWithType> class, which provides a CNG implementation of the RSA algorithm.</span></span>

    - <span data-ttu-id="39b71-877">一般的な操作でキャストを不要にする RSA API の機能強化。</span><span class="sxs-lookup"><span data-stu-id="39b71-877">Enhancements to the RSA API so that common actions no longer require casting.</span></span> <span data-ttu-id="39b71-878">たとえば、以前のバージョンの .NET Framework で <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> オブジェクトを使用してデータを暗号化するには、次のようなコードが必要です。</span><span class="sxs-lookup"><span data-stu-id="39b71-878">For example, encrypting data using an <xref:System.Security.Cryptography.X509Certificates.X509Certificate2> object requires code like the following in previous versions of .NET Framework.</span></span>

      [!code-csharp[WhatsNew.Casting#1](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
      [!code-vb[WhatsNew.Casting#1](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]

      <span data-ttu-id="39b71-879">.NET Framework 4.6 で新しい暗号化を使用するコードは、次のように書き換えてキャストを回避することができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-879">Code that uses the new cryptography APIs in .NET Framework 4.6 can be rewritten as follows to avoid the cast.</span></span>

      [!code-csharp[WhatsNew.Casting#2](~/samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
      [!code-vb[WhatsNew.Casting#2](~/samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]

  - <span data-ttu-id="39b71-880">**日付および時間と UNIX 時間の変換のサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-880">**Support for converting dates and times to or from Unix time**</span></span>

    <span data-ttu-id="39b71-881">日付値および時間値と UNIX 時間の変換をサポートするため、次の新しいメソッドが <xref:System.DateTimeOffset> 構造体に追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-881">The following new methods have been added to the <xref:System.DateTimeOffset> structure to support converting date and time values to or from Unix time:</span></span>

    - <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=nameWithType>

    - <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=nameWithType>

  - <span data-ttu-id="39b71-882">**互換性スイッチ**</span><span class="sxs-lookup"><span data-stu-id="39b71-882">**Compatibility switches**</span></span>

    <span data-ttu-id="39b71-883"><xref:System.AppContext> クラスでは、ライブラリの作成者が統一された新機能のオプトアウト メカニズムをユーザーに提供できるようにする、新しい互換性機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="39b71-883">The <xref:System.AppContext> class adds a new compatibility feature that enables library writers to provide a uniform opt-out mechanism for new functionality for their users.</span></span> <span data-ttu-id="39b71-884">これにより、オプトアウト要求を伝達するために、コンポーネント間に疎結合のコントラクトが確立されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-884">It establishes a loosely coupled contract between components in order to communicate an opt-out request.</span></span> <span data-ttu-id="39b71-885">通常、この機能は既存の機能が変更されるときに重要となります。</span><span class="sxs-lookup"><span data-stu-id="39b71-885">This capability is typically important when a change is made to existing functionality.</span></span> <span data-ttu-id="39b71-886">それに対して、新しい機能には暗黙のオプトインが既に存在しています。</span><span class="sxs-lookup"><span data-stu-id="39b71-886">Conversely, there is already an implicit opt-in for new functionality.</span></span>

    <span data-ttu-id="39b71-887"><xref:System.AppContext> によって、ライブラリは互換性スイッチを定義して公開します。また、それらに依存するコードは、それらのスイッチを設定してライブラリの動作に影響を与えることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-887">With <xref:System.AppContext>, libraries define and expose compatibility switches, while code that depends on them can set those switches to affect the library behavior.</span></span> <span data-ttu-id="39b71-888">ライブラリは、既定では新しい機能を提供し、スイッチが設定されている場合のみそれを変更する (つまり以前の機能を提供する) ことができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-888">By default, libraries provide the new functionality, and they only alter it (that is, they provide the previous functionality) if the switch is set.</span></span>

    <span data-ttu-id="39b71-889">アプリケーション (またはライブラリ) は、依存するライブラリが定義したスイッチの値 (常に <xref:System.Boolean> 値) を宣言できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-889">An application (or a library) can declare the value of a switch (which is always a <xref:System.Boolean> value) that a dependent library defines.</span></span> <span data-ttu-id="39b71-890">スイッチは常に暗黙的に `false` です。</span><span class="sxs-lookup"><span data-stu-id="39b71-890">The switch is always implicitly `false`.</span></span> <span data-ttu-id="39b71-891">スイッチを `true` に設定すると、それが有効になります。</span><span class="sxs-lookup"><span data-stu-id="39b71-891">Setting the switch to `true` enables it.</span></span> <span data-ttu-id="39b71-892">スイッチを明示的に `false` に設定すると、新しい動作が提供されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-892">Explicitly setting the switch to `false` provides the new behavior.</span></span>

    ```csharp
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);
    ```

    ```vb
    AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", True)
    ```

    <span data-ttu-id="39b71-893">ライブラリは、コンシューマーがスイッチの値を宣言したことを確認してから、それを適切に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-893">The library must check if a consumer has declared the value of the switch and then appropriately act on it.</span></span>

    ```csharp
    if (!AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", out shouldThrow))
    {
        // This is the case where the switch value was not set by the application.
        // The library can choose to get the value of shouldThrow by other means.
        // If no overrides nor default values are specified, the value should be 'false'.
        // A false value implies the latest behavior.
    }

    // The library can use the value of shouldThrow to throw exceptions or not.
    if (shouldThrow)
    {
        // old code
    }
    else
    {
        // new code
    }
    ```

    ```vb
    If Not AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", shouldThrow) Then
        ' This is the case where the switch value was not set by the application.
        ' The library can choose to get the value of shouldThrow by other means.
        ' If no overrides nor default values are specified, the value should be 'false'.
        ' A false value implies the latest behavior.
    End If

    ' The library can use the value of shouldThrow to throw exceptions or not.
    If shouldThrow Then
        ' old code
    Else
        ' new code
    End If
    ```

    <span data-ttu-id="39b71-894">スイッチは、ライブラリによって公開される正式なコントラクトであるため、一貫性のある形式を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="39b71-894">It's beneficial to use a consistent format for switches, since they are a formal contract exposed by a library.</span></span> <span data-ttu-id="39b71-895">2 つの明確な形式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="39b71-895">The following are two obvious formats.</span></span>

    - <span data-ttu-id="39b71-896">*Switch* . *namespace* . *switchname*</span><span class="sxs-lookup"><span data-stu-id="39b71-896">*Switch* . *namespace* . *switchname*</span></span>

    - <span data-ttu-id="39b71-897">*Switch* . *library* . *switchname*</span><span class="sxs-lookup"><span data-stu-id="39b71-897">*Switch* . *library* . *switchname*</span></span>

  - <span data-ttu-id="39b71-898">**タスク ベースの非同期パターン (TAP) の変更点**</span><span class="sxs-lookup"><span data-stu-id="39b71-898">**Changes to the task-based asynchronous pattern (TAP)**</span></span>

    <span data-ttu-id="39b71-899">.NET Framework 4.6 をターゲットとするアプリでは、<xref:System.Threading.Tasks.Task> および <xref:System.Threading.Tasks.Task%601> オブジェクトは、呼び出し元のスレッドのカルチャと UI カルチャを継承します。</span><span class="sxs-lookup"><span data-stu-id="39b71-899">For apps that target .NET Framework 4.6, <xref:System.Threading.Tasks.Task> and <xref:System.Threading.Tasks.Task%601> objects inherit the culture and UI culture of the calling thread.</span></span> <span data-ttu-id="39b71-900">以前のバージョンの .NET Framework をターゲットするとアプリまたは特定のバージョンの .NET Framework をターゲットとしないアプリの動作には影響はありません。</span><span class="sxs-lookup"><span data-stu-id="39b71-900">The behavior of apps that target previous versions of .NET Framework, or that do not target a specific version of .NET Framework, is unaffected.</span></span> <span data-ttu-id="39b71-901">詳細については、<xref:System.Globalization.CultureInfo> クラスのトピックの「カルチャとタスク ベースの非同期の操作」セクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-901">For more information, see the "Culture and task-based asynchronous operations" section of the <xref:System.Globalization.CultureInfo> class topic.</span></span>

    <span data-ttu-id="39b71-902"><xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> クラスを使用すると、`async` メソッドなど、特定の非同期制御フローに対してローカルなアンビエント データを表すことができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-902">The <xref:System.Threading.AsyncLocal%601?displayProperty=nameWithType> class allows you to represent ambient data that is local to a given asynchronous control flow, such as an `async` method.</span></span> <span data-ttu-id="39b71-903">これは、スレッド間でデータを保持するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-903">It can be used to persist data across threads.</span></span> <span data-ttu-id="39b71-904"><xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> プロパティの明示的な変更やスレッドでのコンテキスト変換の発生などによってアンビエント データが変更されるたびに通知されるコールバック メソッドを定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-904">You can also define a callback method that is notified whenever the ambient data changes either because the <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=nameWithType> property was explicitly changed, or because the thread encountered a context transition.</span></span>

    <span data-ttu-id="39b71-905">タスク ベースの非同期パターン (TAP) に、特定の状態で完了したタスクを返す 3 つの便利なメソッド <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>、<xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>、および <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType> が追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-905">Three convenience methods, <xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=nameWithType>, <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=nameWithType>, and <xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=nameWithType>, have been added to the task-based asynchronous pattern (TAP) to return completed tasks in a particular state.</span></span>

    <span data-ttu-id="39b71-906"><xref:System.IO.Pipes.NamedPipeClientStream> クラスで、新しい <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A> メソッドによる非同期通信がサポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-906">The <xref:System.IO.Pipes.NamedPipeClientStream> class now supports asynchronous communication with its new <xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>.</span></span> <span data-ttu-id="39b71-907">メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="39b71-907">method.</span></span>

  - <span data-ttu-id="39b71-908">**EventSource がイベント ログへの書き込みをサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-908">**EventSource now supports writing to the Event log**</span></span>

    <span data-ttu-id="39b71-909">コンピューター上で作成された既存の ETW セッションに加えて、<xref:System.Diagnostics.Tracing.EventSource> クラスを使用して管理または操作メッセージをイベント ログに記録できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-909">You now can use the <xref:System.Diagnostics.Tracing.EventSource> class to log administrative or operational messages to the event log, in addition to any existing ETW sessions created on the machine.</span></span> <span data-ttu-id="39b71-910">以前は、この機能のために Microsoft.Diagnostics.Tracing.EventSource NuGet パッケージを使用する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="39b71-910">In the past, you had to use the Microsoft.Diagnostics.Tracing.EventSource NuGet package for this functionality.</span></span> <span data-ttu-id="39b71-911">この機能は .NET Framework 4.6 に組み込まれました。</span><span class="sxs-lookup"><span data-stu-id="39b71-911">This functionality is now built-into .NET Framework 4.6.</span></span>

    <span data-ttu-id="39b71-912">NuGet パッケージと .NET Framework 4.6 は、どちらも次の機能によって更新されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-912">Both the NuGet package and .NET Framework 4.6 have been updated with the following features:</span></span>

    - <span data-ttu-id="39b71-913">**ダイナミック イベント**</span><span class="sxs-lookup"><span data-stu-id="39b71-913">**Dynamic events**</span></span>

      <span data-ttu-id="39b71-914">イベント メソッドを作成せずに、実行時にイベントを定義できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-914">Allows events defined "on the fly" without creating event methods.</span></span>

    - <span data-ttu-id="39b71-915">**リッチ ペイロード**</span><span class="sxs-lookup"><span data-stu-id="39b71-915">**Rich payloads**</span></span>

      <span data-ttu-id="39b71-916">特別な属性が指定されたクラスや配列に加えて、プリミティブ型もペイロードとして渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-916">Allows specially attributed classes and arrays as well as primitive types to be passed as a payload</span></span>

    - <span data-ttu-id="39b71-917">**アクティビティの追跡**</span><span class="sxs-lookup"><span data-stu-id="39b71-917">**Activity tracking**</span></span>

      <span data-ttu-id="39b71-918">Start イベントと Stop イベントの間のイベントに、現在アクティブなすべてのアクティビティを表す ID が付けられます。</span><span class="sxs-lookup"><span data-stu-id="39b71-918">Causes Start and Stop events to tag events between them with an ID that represents all currently active activities.</span></span>

    <span data-ttu-id="39b71-919">これらの機能をサポートするため、<xref:System.Diagnostics.Tracing.EventSource> クラスにオーバーロードされた <xref:System.Diagnostics.Tracing.EventSource.Write%2A> メソッドが追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-919">To support these features, the overloaded <xref:System.Diagnostics.Tracing.EventSource.Write%2A> method has been added to the <xref:System.Diagnostics.Tracing.EventSource> class.</span></span>

- <span data-ttu-id="39b71-920">**Windows Presentation Foundation (WPF)**</span><span class="sxs-lookup"><span data-stu-id="39b71-920">**Windows Presentation Foundation (WPF)**</span></span>

  - <span data-ttu-id="39b71-921">**HDPI の強化**</span><span class="sxs-lookup"><span data-stu-id="39b71-921">**HDPI improvements**</span></span>

    <span data-ttu-id="39b71-922">.NET Framework 4.6 の WPF で、HDPI のサポートが強化されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-922">HDPI support in WPF is now better in .NET Framework 4.6.</span></span> <span data-ttu-id="39b71-923">境界があるコントロールでのクリッピングの発生を減らすため、レイアウトの丸め処理が変更されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-923">Changes have been made to layout rounding to reduce instances of clipping in controls with borders.</span></span> <span data-ttu-id="39b71-924">既定では、<xref:System.Runtime.Versioning.TargetFrameworkAttribute> が .NET 4.6 に設定されている場合にのみ、この機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="39b71-924">By default, this feature is enabled only if your <xref:System.Runtime.Versioning.TargetFrameworkAttribute> is set to .NET 4.6.</span></span>  <span data-ttu-id="39b71-925">以前のバージョンの Framework を対象とするアプリケーションが .NET Framework 4.6 で実行される場合、app.config ファイルの [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) セクションに次の行を追加することで、新しい動作を選択できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-925">Applications that target earlier versions of the framework but are running on .NET Framework 4.6 can opt in to the new behavior by adding the following line to the [\<runtime>](../configure-apps/file-schema/runtime/runtime-element.md) section of the app.config file:</span></span>

    ```xml
    <AppContextSwitchOverrides
    value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"
    />
    ```

    <span data-ttu-id="39b71-926">異なる DPI 設定を持つ (マルチ DPI セットアップの) 複数のモニターにまたがる WPF ウィンドウは、ブラック アウト領域なしで完全にレンダリングされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-926">WPF windows straddling multiple monitors with different DPI settings (Multi-DPI setup) are now completely rendered without blacked-out regions.</span></span> <span data-ttu-id="39b71-927">この動作の選択を解除するには、app.config ファイルの `<appSettings>` セクションに次の行を追加して、この新しい動作を無効にします。</span><span class="sxs-lookup"><span data-stu-id="39b71-927">You can opt out of this behavior by adding the following line to the `<appSettings>` section of the app.config file to disable this new behavior:</span></span>

    ```xml
    <add key="EnableMultiMonitorDisplayClipping" value="true"/>
    ```

    <span data-ttu-id="39b71-928">DPI 設定に基づいて自動的に正しいカーソルを読み込む機能のサポートが <xref:System.Windows.Input.Cursor?displayProperty=nameWithType> に追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-928">Support for automatically loading the right cursor based on DPI setting has been added to  <xref:System.Windows.Input.Cursor?displayProperty=nameWithType>.</span></span>

  - <span data-ttu-id="39b71-929">**タッチの改善**</span><span class="sxs-lookup"><span data-stu-id="39b71-929">**Touch is better**</span></span>

    <span data-ttu-id="39b71-930">タッチで予期しない動作が発生するという、お客様から報告された [Connect](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) の問題が .NET Framework 4.6 で対処されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-930">Customer reports on [Connect](https://connect.microsoft.com/VisualStudio/feedback/details/903760/) that touch produces unpredictable behavior have been addressed in .NET Framework 4.6.</span></span> <span data-ttu-id="39b71-931">Windows 8.1 以降では、Windows ストア アプリケーションと WPF アプリケーションのダブルタップのしきい値が同じになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-931">The double tap threshold for Windows Store applications and WPF applications is now the same in Windows 8.1 and above.</span></span>

  - <span data-ttu-id="39b71-932">**透過的な子ウィンドウのサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-932">**Transparent child window support**</span></span>

    <span data-ttu-id="39b71-933">.NET Framework 4.6 の WPF は、Windows 8.1 以降で、透過的な子ウィンドウをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="39b71-933">WPF in .NET Framework 4.6 supports transparent child windows in Windows 8.1 and above.</span></span> <span data-ttu-id="39b71-934">これにより、最上位レベルのウィンドウ内に四角形でない透過的な子ウィンドウを作成できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-934">This allows you to create non-rectangular and transparent child windows in your top-level windows.</span></span> <span data-ttu-id="39b71-935">この機能を有効にするには、<xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="39b71-935">You can enable this feature by setting the <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=nameWithType> property to `true`.</span></span>

- <span data-ttu-id="39b71-936">**Windows Communication Foundation (WCF)**</span><span class="sxs-lookup"><span data-stu-id="39b71-936">**Windows Communication Foundation (WCF)**</span></span>

  - <span data-ttu-id="39b71-937">**SSL のサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-937">**SSL support**</span></span>

    <span data-ttu-id="39b71-938">WCF で、NetTcp をトランスポート セキュリティおよびクライアント認証と共に使用する場合に、SSL のバージョンとして SSL 3.0 および TLS 1.0 に加えて TLS 1.1 および TLS 1.2 がサポートされるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-938">WCF now supports SSL version TLS 1.1 and TLS 1.2, in addition to SSL 3.0 and TLS 1.0, when using NetTcp with transport security and client authentication.</span></span> <span data-ttu-id="39b71-939">使用するプロトコルを選択することも、安全性の低い古いプロトコルを無効化することもできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-939">It is now possible to select which protocol to use, or to disable old lesser secure protocols.</span></span> <span data-ttu-id="39b71-940">これを行うには、<xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> プロパティを設定するか、または構成ファイルに以下を追加します。</span><span class="sxs-lookup"><span data-stu-id="39b71-940">This can be done either by setting the <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A> property or by adding the following to a configuration file.</span></span>

    ```xml
    <netTcpBinding>
        <binding>
          <security mode= "None|Transport|Message|TransportWithMessageCredential" >
              <transport clientCredentialType="None|Windows|Certificate"
                        protectionLevel="None|Sign|EncryptAndSign"
                        sslProtocols="Ssl3|Tls1|Tls11|Tls12">
                </transport>
          </security>
        </binding>
    </netTcpBinding>
    ```

  - <span data-ttu-id="39b71-941">**異なる HTTP 接続によるメッセージの送信**</span><span class="sxs-lookup"><span data-stu-id="39b71-941">**Sending messages using different HTTP connections**</span></span>

    <span data-ttu-id="39b71-942">WCF で、ユーザーが別の基になる HTTP 接続を使用して特定のメッセージを送信できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-942">WCF now allows users to ensure certain messages are sent using different underlying HTTP connections.</span></span> <span data-ttu-id="39b71-943">これには、2 つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-943">There are two ways to do this:</span></span>

    - <span data-ttu-id="39b71-944">**接続グループ名プレフィックスの使用**</span><span class="sxs-lookup"><span data-stu-id="39b71-944">**Using a connection group name prefix**</span></span>

      <span data-ttu-id="39b71-945">ユーザーは、WCF で接続グループ名のプレフィックスとして使用される文字列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-945">Users can specify a string that WCF will use as a prefix for the connection group name.</span></span> <span data-ttu-id="39b71-946">異なるプレフィックスを持つ 2 つのメッセージは、別の基になる HTTP 接続を使用して送信されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-946">Two messages with different prefixes are sent using different underlying HTTP connections.</span></span> <span data-ttu-id="39b71-947">プレフィックスを設定するには、メッセージの <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> プロパティにキー/値のペアを追加します。</span><span class="sxs-lookup"><span data-stu-id="39b71-947">You set the prefix by adding a key/value pair to the message's <xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="39b71-948">キーは "HttpTransportConnectionGroupNamePrefix" で、値は使用するプレフィックスです。</span><span class="sxs-lookup"><span data-stu-id="39b71-948">The key is "HttpTransportConnectionGroupNamePrefix"; the value is the desired prefix.</span></span>

    - <span data-ttu-id="39b71-949">**異なるチャネル ファクトリの使用**</span><span class="sxs-lookup"><span data-stu-id="39b71-949">**Using different channel factories**</span></span>

      <span data-ttu-id="39b71-950">ユーザーは、異なるチャネル ファクトリによって作成されたチャネルを使用して送信されるメッセージで別の基になる HTTP 接続を使用する機能を有効にすることもできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-950">Users can also enable a feature that ensures that messages sent using channels created by different channel factories will use different underlying HTTP connections.</span></span> <span data-ttu-id="39b71-951">この機能を有効にするには、ユーザーが次の `appSetting` を `true` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-951">To enable this feature, users must set the following `appSetting` to `true`:</span></span>

      ```xml
      <appSettings>
          <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />
      </appSettings>
      ```

- <span data-ttu-id="39b71-952">**Windows Workflow Foundation (WWF)**</span><span class="sxs-lookup"><span data-stu-id="39b71-952">**Windows Workflow Foundation (WWF)**</span></span>

  <span data-ttu-id="39b71-953">順序不定の操作要求がタイムアウトする前に未処理の "非プロトコル" ブックマークが存在する場合に、ワークフロー サービスが要求を保持する秒数を指定できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-953">You can now specify the number of seconds a workflow service will hold on to an out-of-order operation request when there is an outstanding "non-protocol" bookmark before timing out the request.</span></span> <span data-ttu-id="39b71-954">"非プロトコル" ブックマークとは、未処理の Receive アクティビティに関連付けられていないブックマークです。</span><span class="sxs-lookup"><span data-stu-id="39b71-954">A "non-protocol" bookmark is a bookmark that is not related to outstanding Receive activities.</span></span> <span data-ttu-id="39b71-955">一部のアクティビティはその実装内で非プロトコル ブックマークを作成するため、必ずしも非プロトコル ブックマークの存在が明らかにわかるとは限りません。</span><span class="sxs-lookup"><span data-stu-id="39b71-955">Some activities create non-protocol bookmarks within their implementation, so it may not be obvious that a non-protocol bookmark exists.</span></span> <span data-ttu-id="39b71-956">例として State や Pick などがあります。</span><span class="sxs-lookup"><span data-stu-id="39b71-956">These include State and Pick.</span></span> <span data-ttu-id="39b71-957">ステート マシンを使用して実装されたワークフロー サービスや、Pick アクティビティを含むワークフロー サービスがある場合は、非プロトコル ブックマークが存在する可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="39b71-957">So if you have a workflow service implemented with a state machine or containing a Pick activity, you will most likely have non-protocol bookmarks.</span></span> <span data-ttu-id="39b71-958">この間隔を指定するには、app.config ファイルの `appSettings` セクションに次のような行を追加します。</span><span class="sxs-lookup"><span data-stu-id="39b71-958">You specify the interval by adding a line like the following to the `appSettings` section of your app.config file:</span></span>

  ```xml
  <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>
  ```

  <span data-ttu-id="39b71-959">既定値は 60 秒です。</span><span class="sxs-lookup"><span data-stu-id="39b71-959">The default value is 60 seconds.</span></span> <span data-ttu-id="39b71-960">`value` を 0 に設定すると、順序不定の要求はただちに拒否され、次のようなテキストを含むエラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-960">If `value` is set to 0, out-of-order requests are immediately rejected with a fault with text that looks like this:</span></span>

  ```console
  Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.
  ```

  <span data-ttu-id="39b71-961">これは、順序不定の操作メッセージを受信し、非プロトコル ブックマークが存在しない場合に受信するメッセージと同じです。</span><span class="sxs-lookup"><span data-stu-id="39b71-961">This is the same message that you receive if an out-of-order operation message is received and there are no non-protocol bookmarks.</span></span>

  <span data-ttu-id="39b71-962">`FilterResumeTimeoutInSeconds` 要素の値がゼロ以外で、非プロトコル ブックマークが存在し、タイムアウト間隔が終了した場合、その操作は失敗し、タイムアウト メッセージが発生します。</span><span class="sxs-lookup"><span data-stu-id="39b71-962">If the value of the `FilterResumeTimeoutInSeconds` element is non-zero, there are non-protocol bookmarks, and the timeout interval expires, the operation fails with a timeout message.</span></span>

- <span data-ttu-id="39b71-963">**トランザクション**</span><span class="sxs-lookup"><span data-stu-id="39b71-963">**Transactions**</span></span>

  <span data-ttu-id="39b71-964"><xref:System.Transactions.TransactionException> から派生した例外がスローされる原因となったトランザクションに、分散トランザクション識別子を含めることができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-964">You can now include the distributed transaction identifier for the transaction that has caused an exception derived from <xref:System.Transactions.TransactionException> to be thrown.</span></span> <span data-ttu-id="39b71-965">これを行うには、次のキーを app.config ファイルの `appSettings` セクションに追加します。</span><span class="sxs-lookup"><span data-stu-id="39b71-965">You do this by adding the following key to the `appSettings` section of your app.config file:</span></span>

  ```xml
  <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>
  ```

  <span data-ttu-id="39b71-966">既定値は `false` です。</span><span class="sxs-lookup"><span data-stu-id="39b71-966">The default value is `false`.</span></span>

- <span data-ttu-id="39b71-967">**ネットワーク**</span><span class="sxs-lookup"><span data-stu-id="39b71-967">**Networking**</span></span>

  - <span data-ttu-id="39b71-968">**ソケットの再利用**</span><span class="sxs-lookup"><span data-stu-id="39b71-968">**Socket reuse**</span></span>

    <span data-ttu-id="39b71-969">Windows 10 には、送信 TCP 接続のローカル ポートを再利用してコンピューターのリソースを効率的に使用する新しいスケーラビリティの高いネットワーク アルゴリズムが含まれています。</span><span class="sxs-lookup"><span data-stu-id="39b71-969">Windows 10 includes a new high-scalability networking algorithm that makes better use of machine resources by reusing local ports for outbound TCP connections.</span></span> <span data-ttu-id="39b71-970">.NET Framework 4.6 では、この新しいアルゴリズムがサポートされ、.NET アプリで新しい動作を利用できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-970">.NET Framework 4.6 supports the new algorithm, enabling .NET apps to take advantage of the new behavior.</span></span> <span data-ttu-id="39b71-971">以前のバージョンの Windows では、人工的なコンカレント接続の制限 (通常は動的なポート範囲の既定のサイズである 16,384) があったため、負荷がかかったときにポートが使い尽くされ、サービスのスケーラビリティが制限されることがありました。</span><span class="sxs-lookup"><span data-stu-id="39b71-971">In previous versions of Windows, there was an artificial concurrent connection limit (typically 16,384, the default size of the dynamic port range), which could limit the scalability of a service by causing port exhaustion when under load.</span></span>

    <span data-ttu-id="39b71-972">.NET Framework 4.6 では、ポートの再利用を有効にする次の 2 つの API が追加され、コンカレント接続に対する 64 KB の制限が実質的になくなりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-972">In .NET Framework 4.6, two APIs have been added to enable port reuse, which effectively removes the 64 KB limit on concurrent connections:</span></span>

    - <span data-ttu-id="39b71-973"><xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> 列挙型値。</span><span class="sxs-lookup"><span data-stu-id="39b71-973">The <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> enumeration value.</span></span>

    - <span data-ttu-id="39b71-974"><xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> プロパティ。</span><span class="sxs-lookup"><span data-stu-id="39b71-974">The <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property.</span></span>

    <span data-ttu-id="39b71-975">既定では、`HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` レジストリ キーの `HWRPortReuseOnSocketBind` の値が 0x1 に設定されないかぎり、<xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> プロパティは `false` になります。</span><span class="sxs-lookup"><span data-stu-id="39b71-975">By default, the <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property is `false` unless the `HWRPortReuseOnSocketBind` value of the `HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319` registry key is set to 0x1.</span></span> <span data-ttu-id="39b71-976">HTTP 接続でのローカル ポートの再利用を有効にするには、<xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="39b71-976">To enable local port reuse on HTTP connections, set the <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=nameWithType> property to `true`.</span></span> <span data-ttu-id="39b71-977">これにより、<xref:System.Net.Http.HttpClient> および <xref:System.Net.HttpWebRequest> からの外向きのすべての TCP ソケット接続で Windows 10 の新しいソケット オプション [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options) が使用されるようになるため、ローカル ポートの再利用が可能になります。</span><span class="sxs-lookup"><span data-stu-id="39b71-977">This causes all outgoing TCP socket connections from <xref:System.Net.Http.HttpClient> and <xref:System.Net.HttpWebRequest> to use a new Windows 10 socket option, [SO_REUSE_UNICASTPORT](/windows/desktop/WinSock/sol-socket-socket-options), that enables local port reuse.</span></span>

    <span data-ttu-id="39b71-978">ソケット専用のアプリケーションを作成する開発者は、<xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> などのメソッドを呼び出すときに <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> オプションを指定することにより、送信ソケットでバインド中にローカル ポートを再利用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="39b71-978">Developers writing a sockets-only application can specify the <xref:System.Net.Sockets.SocketOptionName?displayProperty=nameWithType> option when calling a method such as <xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=nameWithType> so that outbound sockets reuse local ports during binding.</span></span>

  - <span data-ttu-id="39b71-979">**国際ドメイン名と PunyCode のサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-979">**Support for international domain names and PunyCode**</span></span>

    <span data-ttu-id="39b71-980"><xref:System.Uri> クラスに新しいプロパティ <xref:System.Uri.IdnHost%2A> が追加され、国際ドメイン名と PunyCode のサポートが強化されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-980">A new property, <xref:System.Uri.IdnHost%2A>, has been added to the <xref:System.Uri> class to better support international domain names and PunyCode.</span></span>

- <span data-ttu-id="39b71-981">**Windows フォーム コントロールでのサイズ変更**</span><span class="sxs-lookup"><span data-stu-id="39b71-981">**Resizing in Windows Forms controls.**</span></span>

  <span data-ttu-id="39b71-982">この機能が .NET Framework 4.6 にも拡張されました。<xref:System.Windows.Forms.DomainUpDown>、<xref:System.Windows.Forms.NumericUpDown>、<xref:System.Windows.Forms.DataGridViewComboBoxColumn>、<xref:System.Windows.Forms.DataGridViewColumn>、<xref:System.Windows.Forms.ToolStripSplitButton> 型、および <xref:System.Drawing.Design.UITypeEditor> を描画するときに使用する <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> プロパティで指定される四角形も含まれるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-982">This feature has been expanded in .NET Framework 4.6 to include the <xref:System.Windows.Forms.DomainUpDown>, <xref:System.Windows.Forms.NumericUpDown>, <xref:System.Windows.Forms.DataGridViewComboBoxColumn>, <xref:System.Windows.Forms.DataGridViewColumn> and <xref:System.Windows.Forms.ToolStripSplitButton> types and the rectangle specified by the <xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A> property used when drawing a <xref:System.Drawing.Design.UITypeEditor>.</span></span>

  <span data-ttu-id="39b71-983">これはオプトイン機能です。</span><span class="sxs-lookup"><span data-stu-id="39b71-983">This is an opt-in feature.</span></span> <span data-ttu-id="39b71-984">この機能を有効にするには、アプリケーション構成 (app.config) ファイルで `EnableWindowsFormsHighDpiAutoResizing` 要素を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="39b71-984">To enable it, set the `EnableWindowsFormsHighDpiAutoResizing` element to `true` in the application configuration (app.config) file:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- <span data-ttu-id="39b71-985">**コード ページのエンコーディングのサポート**</span><span class="sxs-lookup"><span data-stu-id="39b71-985">**Support for code page encodings**</span></span>

  <span data-ttu-id="39b71-986">.NET Core は、本来 Unicode エンコードをサポートし、既定ではコード ページ エンコーディングに関するサポートは限定的です。</span><span class="sxs-lookup"><span data-stu-id="39b71-986">.NET Core primarily supports the Unicode encodings and by default provides limited support for code page encodings.</span></span> <span data-ttu-id="39b71-987"><xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> メソッドを使用してコード ページ エンコードを登録することで、.NET Framework では利用できるものの .NET Core ではサポートされていないコード ページ エンコードのサポートを追加できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-987">You can add support for code page encodings available in .NET Framework but unsupported in .NET Core by registering code page encodings with the <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="39b71-988">詳細については、「<xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-988">For more information, see <xref:System.Text.CodePagesEncodingProvider?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="39b71-989">**.NET ネイティブ**</span><span class="sxs-lookup"><span data-stu-id="39b71-989">**.NET Native**</span></span>

  <span data-ttu-id="39b71-990">.NET Core をターゲットとし、C# または Visual Basic で作成されている Windows 10 用の Windows アプリは、IL ではなくネイティブ コードにアプリをコンパイルする新しい技術を活用できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-990">Windows apps for Windows 10 that target .NET Core and are written in C# or Visual Basic can take advantage of a new technology that compiles apps to native code rather than IL.</span></span> <span data-ttu-id="39b71-991">これで、起動時間と実行時間がより速いアプリを生成できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-991">They produce apps characterized by faster startup and execution times.</span></span> <span data-ttu-id="39b71-992">詳しくは、「[.NET ネイティブによるアプリのコンパイル](../net-native/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-992">For more information, see [Compiling Apps with .NET Native](../net-native/index.md).</span></span> <span data-ttu-id="39b71-993">JIT コンパイルと NGEN による結果の違い、およびコードにおけるその影響の概要については、「[.NET ネイティブとコンパイル](../net-native/net-native-and-compilation.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-993">For an overview of .NET Native that examines how it differs from both JIT compilation and NGEN and what that means for your code, see [.NET Native and Compilation](../net-native/net-native-and-compilation.md).</span></span>

  <span data-ttu-id="39b71-994">ご利用のアプリは、Visual Studio 2015 以降でコンパイルするときに、既定でネイティブ コードにコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-994">Your apps are compiled to native code by default when you compile them with Visual Studio 2015 or later.</span></span> <span data-ttu-id="39b71-995">詳しくは、「[.NET ネイティブの概要](../net-native/getting-started-with-net-native.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-995">For more information, see [Getting Started with .NET Native](../net-native/getting-started-with-net-native.md).</span></span>

  <span data-ttu-id="39b71-996">.NET ネイティブ アプリのデバッグをサポートするため、アンマネージ デバッグ APIに対して数多くの新しいインターフェイスと列挙型が追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-996">To support debugging .NET Native apps, a number of new interfaces and enumerations have been added to the unmanaged debugging API.</span></span> <span data-ttu-id="39b71-997">詳しくは、「[デバッグ (アンマネージ API リファレンス)](../unmanaged-api/debugging/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-997">For more information, see the [Debugging (Unmanaged API Reference)](../unmanaged-api/debugging/index.md) topic.</span></span>

- <span data-ttu-id="39b71-998">**オープン ソースの .NET Framework パッケージ**</span><span class="sxs-lookup"><span data-stu-id="39b71-998">**Open-source .NET Framework packages**</span></span>

  <span data-ttu-id="39b71-999">.NET Core のパッケージ (変更できないコレクションなど)、[SIMD API](https://www.nuget.org/packages/Microsoft.Bcl.Simd)、およびネットワーク API (<xref:System.Net.Http> 名前空間に含まれるものなど) は、[GitHub](https://github.com/) でオープンソース パッケージとして入手できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-999">.NET Core packages such as the immutable collections, [SIMD APIs](https://www.nuget.org/packages/Microsoft.Bcl.Simd), and networking APIs such as those found in the <xref:System.Net.Http> namespace are now available as open-source packages on [GitHub](https://github.com/).</span></span> <span data-ttu-id="39b71-1000">このコードにアクセスするには、[GitHub 上の .NET](https://github.com/dotnet/runtime) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1000">To access the code, see [.NET on GitHub](https://github.com/dotnet/runtime).</span></span> <span data-ttu-id="39b71-1001">これらのパッケージの詳細、および投稿方法については、「[.NET Core とオープン ソース](../get-started/net-core-and-open-source.md)」および [GitHub の .NET ホーム ページ](https://github.com/dotnet/home)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1001">For more information and how to contribute to these packages, see [.NET Core and Open-Source](../get-started/net-core-and-open-source.md), [.NET Home Page on GitHub](https://github.com/dotnet/home).</span></span>

<a name="v452"></a>

## <a name="whats-new-in-net-framework-452"></a><span data-ttu-id="39b71-1002">.NET Framework 4.5.2 の新機能</span><span class="sxs-lookup"><span data-stu-id="39b71-1002">What's new in .NET Framework 4.5.2</span></span>

- <span data-ttu-id="39b71-1003">**ASP.NET アプリ用の新しい API。**</span><span class="sxs-lookup"><span data-stu-id="39b71-1003">**New APIs for ASP.NET apps.**</span></span> <span data-ttu-id="39b71-1004">新しい <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> メソッドと <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> メソッドにより、応答がクライアント アプリにフラッシュされる際の、応答ヘッダーと状態コードを確認および変更できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1004">The new <xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=nameWithType> and <xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=nameWithType> methods let you inspect and modify response headers and status code as the response is being flushed to the client app.</span></span> <span data-ttu-id="39b71-1005"><xref:System.Web.HttpApplication.PreSendRequestHeaders> イベントや <xref:System.Web.HttpApplication.PreSendRequestContent> イベントの代わりに、より効率的で信頼性の高いこれらのメソッドの使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1005">Consider using these methods instead of the <xref:System.Web.HttpApplication.PreSendRequestHeaders> and <xref:System.Web.HttpApplication.PreSendRequestContent> events; they are more efficient and reliable.</span></span>

  <span data-ttu-id="39b71-1006"><xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> メソッドにより、小さなバックグラウンド作業項目をスケジュールできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1006">The <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=nameWithType> method lets you schedule small background work items.</span></span> <span data-ttu-id="39b71-1007">ASP.NET はこれらの項目を追跡し、すべてのバックグラウンド作業項目が完了するまで IIS が突然ワーカー プロセスを終了しないようにします。</span><span class="sxs-lookup"><span data-stu-id="39b71-1007">ASP.NET tracks these items and prevents IIS from abruptly terminating the worker process until all background work items have completed.</span></span> <span data-ttu-id="39b71-1008">このメソッドは、ASP.NET マネージド アプリ ドメインの外部で呼び出すことはできません。</span><span class="sxs-lookup"><span data-stu-id="39b71-1008">This method can't be called outside an ASP.NET managed app domain.</span></span>

  <span data-ttu-id="39b71-1009">新しい <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> プロパティと <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> プロパティは、応答ヘッダーが書き込まれたかどうかを示すブール値を返します。</span><span class="sxs-lookup"><span data-stu-id="39b71-1009">The new <xref:System.Web.HttpResponse.HeadersWritten?displayProperty=nameWithType> and <xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=nameWithType> properties return Boolean values that indicate whether the response headers have been written.</span></span> <span data-ttu-id="39b71-1010">これらのプロパティを使用して、<xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> (ヘッダーが書き込まれた場合に例外をスローする) などの API への呼び出しが成功することを確認できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1010">You can use these properties to make sure that calls to APIs such as <xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=nameWithType> (which throw exceptions if the headers have been written) will succeed.</span></span>

- <span data-ttu-id="39b71-1011">**Windows フォーム コントロールでのサイズ変更**</span><span class="sxs-lookup"><span data-stu-id="39b71-1011">**Resizing in Windows Forms controls.**</span></span> <span data-ttu-id="39b71-1012">この機能が拡張されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-1012">This feature has been expanded.</span></span> <span data-ttu-id="39b71-1013">これにより、システム DPI 設定を使用して、次の追加コントロールのコンポーネント (例: コンボ ボックスのドロップダウン矢印) をサイズ変更できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1013">You can now use the system DPI setting to resize components of the following additional controls (for example, the drop-down arrow in combo boxes):</span></span>

  - <xref:System.Windows.Forms.ComboBox>
  - <xref:System.Windows.Forms.ToolStripComboBox>
  - <xref:System.Windows.Forms.ToolStripMenuItem>
  - <xref:System.Windows.Forms.Cursor>
  - <xref:System.Windows.Forms.DataGridView>
  - <xref:System.Windows.Forms.DataGridViewComboBoxColumn>

  <span data-ttu-id="39b71-1014">これはオプトイン機能です。</span><span class="sxs-lookup"><span data-stu-id="39b71-1014">This is an opt-in feature.</span></span> <span data-ttu-id="39b71-1015">この機能を有効にするには、アプリケーション構成 (app.config) ファイルで `EnableWindowsFormsHighDpiAutoResizing` 要素を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="39b71-1015">To enable it, set the `EnableWindowsFormsHighDpiAutoResizing` element to `true` in the application configuration (app.config) file:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

- <span data-ttu-id="39b71-1016">**新しいワークフロー機能。**</span><span class="sxs-lookup"><span data-stu-id="39b71-1016">**New workflow feature.**</span></span> <span data-ttu-id="39b71-1017"><xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> メソッドを使用している (および、結果として <xref:System.Transactions.IPromotableSinglePhaseNotification> インターフェイスを実装している) リソース マネージャーは、新しい <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> メソッドを使用して、次の事柄を要求できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1017">A resource manager that's using the <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A> method (and therefore implementing the <xref:System.Transactions.IPromotableSinglePhaseNotification> interface) can use the new <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> method to request the following:</span></span>

  - <span data-ttu-id="39b71-1018">トランザクションを Microsoft 分散トランザクション コーディネーター (MSDTC) トランザクションに昇格する。</span><span class="sxs-lookup"><span data-stu-id="39b71-1018">Promote the transaction to a Microsoft Distributed Transaction Coordinator (MSDTC) transaction.</span></span>

  - <span data-ttu-id="39b71-1019"><xref:System.Transactions.IPromotableSinglePhaseNotification> を <xref:System.Transactions.ISinglePhaseNotification> (単一フェーズのコミットをサポートする永続的登録リスト) に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1019">Replace <xref:System.Transactions.IPromotableSinglePhaseNotification> with an <xref:System.Transactions.ISinglePhaseNotification>, which is a durable enlistment that supports single phase commits.</span></span>

  <span data-ttu-id="39b71-1020">これは同じアプリ ドメイン内で実行でき、MSDTC とやり取りして昇格を実行するためにアンマネージ コードを追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="39b71-1020">This can be done within the same app domain, and doesn't require any extra unmanaged code to interact with MSDTC to perform the promotion.</span></span> <span data-ttu-id="39b71-1021"><xref:System.Transactions?displayProperty=nameWithType> から昇格可能な登録リストにより実装された <xref:System.Transactions.IPromotableSinglePhaseNotification>`Promote` メソッドへの未処理の呼び出しがある場合のみ、この新しいメソッドを呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1021">The new method can be called only when there's an outstanding call from <xref:System.Transactions?displayProperty=nameWithType> to the <xref:System.Transactions.IPromotableSinglePhaseNotification>`Promote` method that's implemented by the promotable enlistment.</span></span>

- <span data-ttu-id="39b71-1022">**プロファイリングの機能強化。**</span><span class="sxs-lookup"><span data-stu-id="39b71-1022">**Profiling improvements.**</span></span> <span data-ttu-id="39b71-1023">次の新しいアンマネージ プロファイリング API により、さらに信頼性の高いプロファイリングを提供します。</span><span class="sxs-lookup"><span data-stu-id="39b71-1023">The following new unmanaged profiling APIs provide more robust profiling:</span></span>

  - [<span data-ttu-id="39b71-1024">COR_PRF_ASSEMBLY_REFERENCE_INFO 構造体</span><span class="sxs-lookup"><span data-stu-id="39b71-1024">COR_PRF_ASSEMBLY_REFERENCE_INFO Structure</span></span>](../unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)
  - [<span data-ttu-id="39b71-1025">COR_PRF_HIGH_MONITOR 列挙型</span><span class="sxs-lookup"><span data-stu-id="39b71-1025">COR_PRF_HIGH_MONITOR Enumeration</span></span>](../unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)
  - [<span data-ttu-id="39b71-1026">GetAssemblyReferences メソッド</span><span class="sxs-lookup"><span data-stu-id="39b71-1026">GetAssemblyReferences Method</span></span>](../unmanaged-api/profiling/icorprofilercallback6-getassemblyreferences-method.md)
  - [<span data-ttu-id="39b71-1027">GetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="39b71-1027">GetEventMask2 Method</span></span>](../unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
  - [<span data-ttu-id="39b71-1028">SetEventMask2 メソッド</span><span class="sxs-lookup"><span data-stu-id="39b71-1028">SetEventMask2 Method</span></span>](../unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)
  - [<span data-ttu-id="39b71-1029">AddAssemblyReference メソッド</span><span class="sxs-lookup"><span data-stu-id="39b71-1029">AddAssemblyReference Method</span></span>](../unmanaged-api/profiling/icorprofilerassemblyreferenceprovider-addassemblyreference-method.md)

  <span data-ttu-id="39b71-1030">以前の `ICorProfiler` の実装は、依存アセンブリの遅延読み込みをサポートしていました。</span><span class="sxs-lookup"><span data-stu-id="39b71-1030">Previous `ICorProfiler` implementations supported lazy loading of dependent assemblies.</span></span> <span data-ttu-id="39b71-1031">新しいプロファイリング API では、プロファイラーにより挿入される依存アセンブリを、アプリの完全な初期化後に読み込むのではなく、すぐに読み込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-1031">The new profiling APIs require dependent assemblies that are injected by the profiler to be loadable immediately, instead of being loaded after the app is fully initialized.</span></span> <span data-ttu-id="39b71-1032">この変更は、既存の `ICorProfiler` API のユーザーには影響しません。</span><span class="sxs-lookup"><span data-stu-id="39b71-1032">This change doesn't affect users of the existing `ICorProfiler` APIs.</span></span>

- <span data-ttu-id="39b71-1033">**デバッグの機能強化。**</span><span class="sxs-lookup"><span data-stu-id="39b71-1033">**Debugging improvements.**</span></span> <span data-ttu-id="39b71-1034">次の新しいアンマネージド デバッグ API により、プロファイラーとの統合性が向上しました。</span><span class="sxs-lookup"><span data-stu-id="39b71-1034">The following new unmanaged debugging APIs provide better integration with a profiler.</span></span> <span data-ttu-id="39b71-1035">これにより、ダンプのデバッグ時にコンパイラ ReJIT 要求により作成されたローカル変数やコードだけでなく、プロファイラーにより挿入されたメタデータにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1035">You can now access metadata inserted by the profiler as well as local variables and code produced by compiler ReJIT requests when dump debugging.</span></span>

  - [<span data-ttu-id="39b71-1036">SetWriteableMetadataUpdateMode メソッド</span><span class="sxs-lookup"><span data-stu-id="39b71-1036">SetWriteableMetadataUpdateMode Method</span></span>](../unmanaged-api/debugging/icordebugprocess7-setwriteablemetadataupdatemode-method.md)
  - [<span data-ttu-id="39b71-1037">EnumerateLocalVariablesEx メソッド</span><span class="sxs-lookup"><span data-stu-id="39b71-1037">EnumerateLocalVariablesEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-enumeratelocalvariablesex-method.md)
  - [<span data-ttu-id="39b71-1038">GetLocalVariableEx メソッド</span><span class="sxs-lookup"><span data-stu-id="39b71-1038">GetLocalVariableEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-getlocalvariableex-method.md)
  - [<span data-ttu-id="39b71-1039">GetCodeEx メソッド</span><span class="sxs-lookup"><span data-stu-id="39b71-1039">GetCodeEx Method</span></span>](../unmanaged-api/debugging/icordebugilframe4-getcodeex-method.md)
  - [<span data-ttu-id="39b71-1040">GetActiveReJitRequestILCode メソッド</span><span class="sxs-lookup"><span data-stu-id="39b71-1040">GetActiveReJitRequestILCode Method</span></span>](../unmanaged-api/debugging/icordebugfunction3-getactiverejitrequestilcode-method.md)
  - [<span data-ttu-id="39b71-1041">GetInstrumentedILMap メソッド</span><span class="sxs-lookup"><span data-stu-id="39b71-1041">GetInstrumentedILMap Method</span></span>](../unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)

- <span data-ttu-id="39b71-1042">**イベント トレーシングの変更。**</span><span class="sxs-lookup"><span data-stu-id="39b71-1042">**Event tracing changes.**</span></span> <span data-ttu-id="39b71-1043">.NET Framework 4.5.2 では、より大きなサーフェイス領域において、アウトプロセスの Windows イベント トレーシング (ETW) に基づくアクティビティ トレーシングができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-1043">.NET Framework 4.5.2 enables out-of-process, Event Tracing for Windows (ETW)-based activity tracing for a larger surface area.</span></span> <span data-ttu-id="39b71-1044">これにより、アドバンスト パワー マネージメント (APM) ベンダーは、スレッドを越えた個々の要求とアクティビティのコストを正確に追跡する軽量ツールを提供できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1044">This enables Advanced Power Management (APM) vendors to provide lightweight tools that accurately track the costs of individual requests and activities that cross threads.</span></span>  <span data-ttu-id="39b71-1045">これらのイベントは、ETW コントローラーで有効にされた場合にのみ発生します。したがって、変更は以前に記述された ETW コードや ETW が無効な状態で実行されるコードには影響しません。</span><span class="sxs-lookup"><span data-stu-id="39b71-1045">These events are raised only when ETW controllers enable them; therefore, the changes don't affect previously written ETW code or code that runs with ETW disabled.</span></span>

- <span data-ttu-id="39b71-1046">**トランザクションの昇格と永続参加リストへの変換**</span><span class="sxs-lookup"><span data-stu-id="39b71-1046">**Promoting a transaction and converting it to a durable enlistment**</span></span>

  <span data-ttu-id="39b71-1047"><xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> は、.NET Framework 4.5.2 および 4.6 に追加された新しい API です。</span><span class="sxs-lookup"><span data-stu-id="39b71-1047"><xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=nameWithType> is a new API added to .NET Framework 4.5.2 and 4.6:</span></span>

  ```csharp
  [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]
  public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,
                                            IPromotableSinglePhaseNotification promotableNotification,
                                            ISinglePhaseNotification enlistmentNotification,
                                            EnlistmentOptions enlistmentOptions)
  ```

  ```vb
  <System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name:="FullTrust")>
  public Function PromoteAndEnlistDurable(resourceManagerIdentifier As Guid,
                                          promotableNotification As IPromotableSinglePhaseNotification,
                                          enlistmentNotification As ISinglePhaseNotification,
                                          enlistmentOptions As EnlistmentOptions) As Enlistment
  ```

  <span data-ttu-id="39b71-1048">このメソッドは、以前に <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> メソッドへの応答として <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> によって作成された参加リストで使用できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1048">The method may be used by an enlistment that was previously created by <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=nameWithType> in response to the <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="39b71-1049">これは、`System.Transactions` に対して、トランザクションを MSDTC トランザクションに昇格させ、昇格可能参加リストを永続参加リストに "変換" するように要求します。</span><span class="sxs-lookup"><span data-stu-id="39b71-1049">It asks `System.Transactions` to promote the transaction to an MSDTC transaction and to "convert" the promotable enlistment to a durable enlistment.</span></span> <span data-ttu-id="39b71-1050">このメソッドが正常に完了すると、<xref:System.Transactions.IPromotableSinglePhaseNotification> インターフェイスが `System.Transactions` から参照されなくなり、その後の通知は指定された <xref:System.Transactions.ISinglePhaseNotification> インターフェイスに到着します。</span><span class="sxs-lookup"><span data-stu-id="39b71-1050">After this method completes successfully, the <xref:System.Transactions.IPromotableSinglePhaseNotification> interface will no longer be referenced by `System.Transactions`, and any future notifications will arrive on the provided <xref:System.Transactions.ISinglePhaseNotification> interface.</span></span> <span data-ttu-id="39b71-1051">問題の参加リストは、永続参加リストとして機能し、トランザクションのログ記録と復旧をサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-1051">The enlistment in question must act as a durable enlistment, supporting transaction logging and recovery.</span></span> <span data-ttu-id="39b71-1052">詳細については、<xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1052">Refer to <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=nameWithType> for details.</span></span> <span data-ttu-id="39b71-1053">さらに、この参加リストは <xref:System.Transactions.ISinglePhaseNotification> もサポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-1053">In addition, the enlistment must support <xref:System.Transactions.ISinglePhaseNotification>.</span></span>  <span data-ttu-id="39b71-1054">このメソッドは、<xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> の呼び出しの処理中に *のみ* 呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1054">This method can *only* be called while processing an <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=nameWithType> call.</span></span> <span data-ttu-id="39b71-1055">そうでない場合は、<xref:System.Transactions.TransactionException> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1055">If that is not the case, a <xref:System.Transactions.TransactionException> exception is thrown.</span></span>

<a name="v451"></a>

## <a name="whats-new-in-net-framework-451"></a><span data-ttu-id="39b71-1056">.NET Framework 4.5.1 の新機能</span><span class="sxs-lookup"><span data-stu-id="39b71-1056">What's new in .NET Framework 4.5.1</span></span>

<span data-ttu-id="39b71-1057">**2014 年 4 月の更新** :</span><span class="sxs-lookup"><span data-stu-id="39b71-1057">**April 2014 updates** :</span></span>

- <span data-ttu-id="39b71-1058">[Visual Studio 2013 更新プログラム 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) には、次のシナリオをサポートするポータブル クラス ライブラリ テンプレートの更新が含まれています。</span><span class="sxs-lookup"><span data-stu-id="39b71-1058">[Visual Studio 2013 Update 2](https://go.microsoft.com/fwlink/p/?LinkId=393658) includes updates to the Portable Class Library templates to support these scenarios:</span></span>

  - <span data-ttu-id="39b71-1059">Windows 8.1、Windows Phone 8.1、および Windows Phone Silverlight 8.1 を対象とするポータブル ライブラリで Windows ランタイム API を使用できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1059">You can use Windows Runtime APIs in portable libraries that target Windows 8.1, Windows Phone 8.1, and Windows Phone Silverlight 8.1.</span></span>

  - <span data-ttu-id="39b71-1060">Windows 8.1 または Windows Phone 8.1 を対象とする場合、ポータブル ライブラリに XAML (Windows.UI.XAML 型) を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1060">You can include XAML (Windows.UI.XAML types) in portable libraries when you target Windows 8.1 or Windows Phone 8.1.</span></span> <span data-ttu-id="39b71-1061">次の XAML テンプレートがサポートされています: 空白のページ、リソース ディクショナリ、テンプレート コントロール、およびユーザー コントロール。</span><span class="sxs-lookup"><span data-stu-id="39b71-1061">The following XAML templates are supported:  Blank Page, Resource Dictionary, Templated Control, and User Control.</span></span>

  - <span data-ttu-id="39b71-1062">Windows 8.1 および Windows Phone 8.1 を対象とするストア アプリで使用するためにポータブル Windows ラインタイム コンポーネント (.winmd ファイル) を作成できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1062">You can create a portable Windows Runtime component (.winmd file) for use in Store apps that target Windows 8.1 and Windows Phone 8.1.</span></span>

  - <span data-ttu-id="39b71-1063">ポータブル クラス ライブラリのような Windows ストアまたは Windows Phone ストア クラス ライブラリを再ターゲットできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1063">You can retarget a Windows Store or Windows Phone Store class library like a Portable Class Library.</span></span>

  <span data-ttu-id="39b71-1064">これらの変更の詳細については、[ポータブル クラス ライブラリ](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1064">For more information about these changes, see [Portable Class Library](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).</span></span>

- <span data-ttu-id="39b71-1065">.NET Framework のコンテンツ セットには、Windows アプリをビルドして配置するためのプリコンパイル テクノロジである .NET Native のドキュメントが含まれます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1065">The .NET Framework content set now includes documentation for .NET Native, which is a precompilation technology for building and deploying Windows apps.</span></span> <span data-ttu-id="39b71-1066">.NET Native は、中間言語 (IL) ではなくネイティブ コードへアプリを直接コンパイルすることにより、パフォーマンスを向上させます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1066">.NET Native compiles your apps directly to native code, rather than to intermediate language (IL), for better performance.</span></span> <span data-ttu-id="39b71-1067">詳しくは、「[.NET ネイティブによるアプリのコンパイル](../net-native/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1067">For details, see [Compiling Apps with .NET Native](../net-native/index.md).</span></span>

- <span data-ttu-id="39b71-1068">[.NET Framework Reference Source](https://referencesource.microsoft.com/) で、新しい参照エクスペリエンスと強化された機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1068">The [.NET Framework Reference Source](https://referencesource.microsoft.com/) provides a new browsing experience and enhanced functionality.</span></span> <span data-ttu-id="39b71-1069">これにより、.NET Frameworkのソース コードをオンラインで参照したり、[リファレンスをダウンロード](https://referencesource.microsoft.com/download.html)してオフラインで表示したりできます。さらに、デバッグ中にソース (パッチや更新を含む) をステップ実行できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1069">You can now browse through the .NET Framework source code online, [download the reference](https://referencesource.microsoft.com/download.html) for offline viewing, and step through the sources (including patches and updates) during debugging.</span></span> <span data-ttu-id="39b71-1070">詳細については、ブログ記事「[A new look for .NET Reference Source (.NET Reference Source の新しい外観)](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1070">For more information, see the blog entry [A new look for .NET Reference Source](https://devblogs.microsoft.com/dotnet/a-new-look-for-net-reference-source/).</span></span>

<span data-ttu-id="39b71-1071">.NET Framework 4.5.1 の基底クラスの新機能と機能強化には次が含まれます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1071">New features and enhancements in the base classes in .NET Framework 4.5.1 include:</span></span>

- <span data-ttu-id="39b71-1072">アセンブリの自動バインディング リダイレクト。</span><span class="sxs-lookup"><span data-stu-id="39b71-1072">Automatic binding redirection for assemblies.</span></span> <span data-ttu-id="39b71-1073">.NET Framework 4.5.1 を対象とするアプリをコンパイルする場合、お使いのアプリまたはそのコンポーネントが同じアセンブリの複数バージョンを参照している場合、Visual Studio 2013 以降ではバインディング リダイレクトがアプリの構成ファイルに追加される場合があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-1073">Starting with Visual Studio 2013, when you compile an app that targets .NET Framework 4.5.1, binding redirects may be added to the app configuration file if your app or its components reference multiple versions of the same assembly.</span></span> <span data-ttu-id="39b71-1074">この機能は、.NET Framework の以前のバージョンを対象とするプロジェクトでも有効にできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1074">You can also enable this feature for projects that target older versions of .NET Framework.</span></span> <span data-ttu-id="39b71-1075">詳細については、「[方法:自動バインディング リダイレクトを有効/無効にする](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1075">For more information, see [How to: Enable and Disable Automatic Binding Redirection](../configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md).</span></span>

- <span data-ttu-id="39b71-1076">開発者がサーバーおよびクラウド アプリケーションのパフォーマンスを向上するために役立つ診断情報を収集する機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1076">Ability to collect diagnostics information to help developers improve the performance of server and cloud applications.</span></span> <span data-ttu-id="39b71-1077">詳細については、<xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> クラスの <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> メソッドと <xref:System.Diagnostics.Tracing.EventSource> メソッドを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1077">For more information, see the <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A> and <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A> methods in the <xref:System.Diagnostics.Tracing.EventSource> class.</span></span>

- <span data-ttu-id="39b71-1078">ガベージ コレクション中に大きなオブジェクト ヒープ (LOH) を圧縮する機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1078">Ability to explicitly compact the large object heap (LOH) during garbage collection.</span></span> <span data-ttu-id="39b71-1079">詳細については、<xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> プロパティを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1079">For more information, see the <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="39b71-1080">その他のパフォーマンス向上 (ASP.NET アプリの中断、マルチコア JIT の改良、.NET Framework 更新後のアプリ起動時間の短縮など)。</span><span class="sxs-lookup"><span data-stu-id="39b71-1080">Additional performance improvements such as ASP.NET app suspension, multi-core JIT improvements, and faster app startup after a .NET Framework update.</span></span> <span data-ttu-id="39b71-1081">詳細については、ブログ記事「[.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/)」(.NET Framework 4.5.1 についてのお知らせ) および「[ASP.NET app suspend](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/)」 (ASP.NET アプリケーションの中断) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1081">For details, see the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/) and the [ASP.NET app suspend](https://devblogs.microsoft.com/dotnet/asp-net-app-suspend-responsive-shared-net-web-hosting/) blog post.</span></span>

<span data-ttu-id="39b71-1082">Windows フォームの機能強化には次が含まれます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1082">Improvements to Windows Forms include:</span></span>

- <span data-ttu-id="39b71-1083">Windows フォーム コントロールでのサイズ変更。</span><span class="sxs-lookup"><span data-stu-id="39b71-1083">Resizing in Windows Forms controls.</span></span> <span data-ttu-id="39b71-1084">アプリのアプリケーション構成ファイル (app.config) 内のエントリで有効にすることにより、システム DIP 設定を使用してコントロールのコンポーネント (例: プロパティ グリッドに表示されるアイコン) をサイズ変更できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1084">You can use the system DPI setting to resize components of controls (for example, the icons that appear in a property grid) by opting in with an entry in the application configuration file (app.config) for your app.</span></span> <span data-ttu-id="39b71-1085">現在、この機能は次の Windows フォーム コントロールでサポートされています。</span><span class="sxs-lookup"><span data-stu-id="39b71-1085">This feature is currently supported in the following Windows Forms controls:</span></span>

  - <xref:System.Windows.Forms.PropertyGrid>
  - <xref:System.Windows.Forms.TreeView>
  - <span data-ttu-id="39b71-1086"><xref:System.Windows.Forms.DataGridView> の一部 (サポートされている追加コントロールについては、「[4.5.2 の新機能](#v452)」を参照してください)</span><span class="sxs-lookup"><span data-stu-id="39b71-1086">Some aspects of the <xref:System.Windows.Forms.DataGridView> (see [new features in 4.5.2](#v452) for additional controls supported)</span></span>

  <span data-ttu-id="39b71-1087">この機能を有効にするには、構成ファイル (app.config) に新しい \<appSettings> 要素を追加し、`EnableWindowsFormsHighDpiAutoResizing` 要素を `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="39b71-1087">To enable this feature, add a new \<appSettings> element to the configuration file (app.config) and set the `EnableWindowsFormsHighDpiAutoResizing` element to `true`:</span></span>

  ```xml
  <appSettings>
      <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />
  </appSettings>
  ```

<span data-ttu-id="39b71-1088">Visual Studio 2013 で .NET Framework アプリをデバッグするときの改善点は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="39b71-1088">Improvements when debugging your .NET Framework apps in Visual Studio 2013 include:</span></span>

- <span data-ttu-id="39b71-1089">Visual Studio デバッガーの戻り値。</span><span class="sxs-lookup"><span data-stu-id="39b71-1089">Return values in the Visual Studio debugger.</span></span> <span data-ttu-id="39b71-1090">Visual Studio 2013 でマネージド アプリをデバッグする場合、メソッドの戻り値の型と値が [自動変数] ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1090">When you debug a managed app in Visual Studio 2013, the Autos window displays return types and values for methods.</span></span> <span data-ttu-id="39b71-1091">デスクトップ アプリ、Windows ストア アプリ、Windows Phone アプリについて、この情報を使用できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1091">This information is available for desktop, Windows Store, and Windows Phone apps.</span></span> <span data-ttu-id="39b71-1092">詳細については、「[メソッド呼び出しの戻り値の調査](/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120))」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1092">For more information, see [Examine return values of method calls](/previous-versions/visualstudio/visual-studio-2013/dn323257(v=vs.120)).</span></span>

- <span data-ttu-id="39b71-1093">64 ビット アプリのエディット コンティニュ。</span><span class="sxs-lookup"><span data-stu-id="39b71-1093">Edit and Continue for 64-bit apps.</span></span> <span data-ttu-id="39b71-1094">Visual Studio 2013 では、デスクトップ、Windows ストア、Windows Phone 用の 64 ビット マネージド アプリについて、エディット コンティニュ機能がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="39b71-1094">Visual Studio 2013 supports the Edit and Continue feature for 64-bit managed apps for desktop, Windows Store, and Windows Phone.</span></span> <span data-ttu-id="39b71-1095">既存の制限は、32 ビット アプリと 64 ビット アプリの両方でまだ有効です (「[Supported Code Changes (C#)](/visualstudio/debugger/supported-code-changes-csharp)」(サポートされているコードの変更 (C#)) の記事の最後のセクションを参照してください)。</span><span class="sxs-lookup"><span data-stu-id="39b71-1095">The existing limitations remain in effect for both 32-bit and 64-bit apps (see the last section of the [Supported Code Changes (C#)](/visualstudio/debugger/supported-code-changes-csharp) article).</span></span>

- <span data-ttu-id="39b71-1096">非同期対応のデバッグ。</span><span class="sxs-lookup"><span data-stu-id="39b71-1096">Async-aware debugging.</span></span> <span data-ttu-id="39b71-1097">Visual Studio 2013 で非同期アプリを簡単にデバッグするために、呼び出し履歴には、非同期プログラミングをサポートするためにコンパイラに用意されているインフラストラクチャ コード、および論理上の親フレーム内のチェーンが表示されません。これにより、論理的なプログラムの実行をよりわかりやすく行うことができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1097">To make it easier to debug asynchronous apps in Visual Studio 2013, the call stack hides the infrastructure code provided by compilers to support asynchronous programming, and also chains in logical parent frames so you can follow logical program execution more clearly.</span></span> <span data-ttu-id="39b71-1098">[タスク] ウィンドウが [並列タスク] ウィンドウに代わって使用され、特定のブレークポイントに関連するタスクが表示されます。また、現在アクティブなタスクやアプリでスケジュールされているタスクなども表示されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1098">A Tasks window replaces the Parallel Tasks window and displays tasks that relate to a particular breakpoint, and also displays any other tasks that are currently active or scheduled in the app.</span></span> <span data-ttu-id="39b71-1099">この機能については、「[.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/)」(.NET Framework 4.5.1 についてのお知らせ) の「Async-aware debugging」(非同期対応のデバッグ) セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1099">You can read about this feature in the "Async-aware debugging" section of the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span></span>

- <span data-ttu-id="39b71-1100">Windows ランタイム コンポーネント向けのより適切な例外処理のサポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1100">Better exception support for Windows Runtime components.</span></span> <span data-ttu-id="39b71-1101">Windows 8.1 では、言語の種類に関係なく、Windows ストア アプリから発生する例外には、例外を発生させたエラーに関する情報が保持されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1101">In Windows 8.1, exceptions that arise from Windows Store apps preserve information about the error that caused the exception, even across language boundaries.</span></span> <span data-ttu-id="39b71-1102">この機能については、「[.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/)」(.NET Framework 4.5.1 についてのお知らせ) の「Windows Store app development」(Windows ストア アプリ開発) のセクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1102">You can read about this feature in the "Windows Store app development" section of the [.NET Framework 4.5.1 announcement](https://devblogs.microsoft.com/dotnet/announcing-the-net-framework-4-5-1-preview/).</span></span>

<span data-ttu-id="39b71-1103">Visual Studio 2013 以降では、[Mpgo.exe (マネージド プロファイル ガイド付き最適化ツール)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) を使って、Windows 8.x ストア アプリとデスクトップ アプリを最適化することができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1103">Starting with Visual Studio 2013, you can use the [Managed Profile Guided Optimization Tool (Mpgo.exe)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md) to optimize Windows 8.x Store apps as well as desktop apps.</span></span>

<span data-ttu-id="39b71-1104">ASP.NET 4.5.1 の新機能については、「[ASP.NET and Web Tools for Visual Studio 2013 のリリース ノート](/aspnet/visual-studio/overview/2013/release-notes)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1104">For new features in ASP.NET 4.5.1, see [ASP.NET and Web Tools for Visual Studio 2013 Release Notes](/aspnet/visual-studio/overview/2013/release-notes).</span></span>

<a name="v45"></a>

## <a name="whats-new-in-net-framework-45"></a><span data-ttu-id="39b71-1105">.NET Framework 4.5 の新機能</span><span class="sxs-lookup"><span data-stu-id="39b71-1105">What's new in .NET Framework 4.5</span></span>

### <a name="base-classes"></a><span data-ttu-id="39b71-1106">基底クラス</span><span class="sxs-lookup"><span data-stu-id="39b71-1106">Base classes</span></span>

- <span data-ttu-id="39b71-1107">配置時に .NET Framework 4 アプリケーションを検出して終了することにより、システムの再起動を減らす機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1107">Ability to reduce system restarts by detecting and closing .NET Framework 4 applications during deployment.</span></span> <span data-ttu-id="39b71-1108">「[.NET Framework 4.5 のインストール中のシステム再起動の削減](../deployment/reducing-system-restarts.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1108">See [Reducing System Restarts During .NET Framework 4.5 Installations](../deployment/reducing-system-restarts.md).</span></span>

- <span data-ttu-id="39b71-1109">64 ビット プラットフォームでの 2 ギガバイト (GB) を超える配列のサポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1109">Support for arrays that are larger than 2 gigabytes (GB) on 64-bit platforms.</span></span> <span data-ttu-id="39b71-1110">この機能は、アプリケーション構成ファイルで有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1110">This feature can be enabled in the application configuration file.</span></span> <span data-ttu-id="39b71-1111">「[\<gcAllowVeryLargeObjects> 要素](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)」も参照してください。オブジェクト サイズと配列サイズに関する他の制限も記載されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-1111">See the [\<gcAllowVeryLargeObjects> element](../configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md), which also lists other restrictions on object size and array size.</span></span>

- <span data-ttu-id="39b71-1112">サーバーのガベージ コレクションをバックグラウンドで行うことにより、パフォーマンスを改善します。</span><span class="sxs-lookup"><span data-stu-id="39b71-1112">Better performance through background garbage collection for servers.</span></span> <span data-ttu-id="39b71-1113">.NET Framework 4.5 でサーバーのガベージ コレクションを使うと、バックグラウンド ガベージ コレクションが自動的に有効になります。</span><span class="sxs-lookup"><span data-stu-id="39b71-1113">When you use server garbage collection in .NET Framework 4.5, background garbage collection is automatically enabled.</span></span> <span data-ttu-id="39b71-1114">「[ガベージ コレクションの基礎](../../standard/garbage-collection/fundamentals.md)」(ガベージ コレクションの基礎) トピックの「バックグラウンド サーバー ガベージ コレクション」というセクションをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1114">See the Background Server Garbage Collection section of the [Fundamentals of Garbage Collection](../../standard/garbage-collection/fundamentals.md) topic.</span></span>

- <span data-ttu-id="39b71-1115">マルチコア プロセッサでオプションで使用できるバックグラウンドの Just-in-time (JIT) コンパイルを使用すると、アプリケーションのパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="39b71-1115">Background just-in-time (JIT) compilation, which is optionally available on multi-core processors to improve application performance.</span></span> <span data-ttu-id="39b71-1116">「<xref:System.Runtime.ProfileOptimization>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1116">See <xref:System.Runtime.ProfileOptimization>.</span></span>

- <span data-ttu-id="39b71-1117">正規表現エンジンがタイムアウトする前に、正規表現の解決を試みる時間に制限を設ける機能。<xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> プロパティを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1117">Ability to limit how long the regular expression engine will attempt to resolve a regular expression before it times out. See the <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=nameWithType> property.</span></span>

- <span data-ttu-id="39b71-1118">アプリケーション ドメインの既定のカルチャを定義する機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1118">Ability to define the default culture for an application domain.</span></span> <span data-ttu-id="39b71-1119">詳細については、<xref:System.Globalization.CultureInfo> クラスのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1119">See the <xref:System.Globalization.CultureInfo> class.</span></span>

- <span data-ttu-id="39b71-1120">Unicode UTF-16 エンコードのコンソール サポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1120">Console support for Unicode (UTF-16) encoding.</span></span> <span data-ttu-id="39b71-1121">詳細については、<xref:System.Console> クラスのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1121">See the <xref:System.Console> class.</span></span>

- <span data-ttu-id="39b71-1122">カルチャに従った文字列の順序のバージョン指定と比較データのサポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1122">Support for versioning of cultural string ordering and comparison data.</span></span> <span data-ttu-id="39b71-1123">詳細については、<xref:System.Globalization.SortVersion> クラスのトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1123">See the <xref:System.Globalization.SortVersion> class.</span></span>

- <span data-ttu-id="39b71-1124">リソースを取得するときのパフォーマンスを改善します。</span><span class="sxs-lookup"><span data-stu-id="39b71-1124">Better performance when retrieving resources.</span></span> <span data-ttu-id="39b71-1125">「[リソースのパッケージ化と配置](../resources/packaging-and-deploying-resources-in-desktop-apps.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1125">See [Packaging and Deploying Resources](../resources/packaging-and-deploying-resources-in-desktop-apps.md).</span></span>

- <span data-ttu-id="39b71-1126">Zip 圧縮の機能強化により、圧縮ファイルのサイズが小さくなりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-1126">Zip compression improvements to reduce the size of a compressed file.</span></span> <span data-ttu-id="39b71-1127"><xref:System.IO.Compression?displayProperty=nameWithType> 名前空間を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1127">See the <xref:System.IO.Compression?displayProperty=nameWithType> namespace.</span></span>

- <span data-ttu-id="39b71-1128"><xref:System.Reflection.Context.CustomReflectionContext> クラスを使用して、既定のリフレクションの動作をオーバーライドするリフレクション コンテキストをカスタマイズできる機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1128">Ability to customize a reflection context to override default reflection behavior through the <xref:System.Reflection.Context.CustomReflectionContext> class.</span></span>

- <span data-ttu-id="39b71-1129"><xref:System.Globalization.IdnMapping?displayProperty=nameWithType> クラスを Windows 8 で使用した場合の IDNA (Internationalized Domain Names in Applications) 規格の 2008 バージョンのサポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1129">Support for the 2008 version of the Internationalized Domain Names in Applications (IDNA) standard when the <xref:System.Globalization.IdnMapping?displayProperty=nameWithType> class is used  on Windows 8.</span></span>

- <span data-ttu-id="39b71-1130">オペレーティング システムへの文字列比較の処理代行。 .NET Framework を Windows 8 で使ったときに、Unicode 6.0 が実装されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1130">Delegation of string comparison to the operating system, which implements Unicode 6.0, when the .NET Framework is used on Windows 8.</span></span> <span data-ttu-id="39b71-1131">他のプラットフォームで実行されている場合、.NET Framework には、Unicode 5.x. を実装する独自の文字列比較データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="39b71-1131">When running on other platforms, the .NET Framework includes its own string comparison data, which implements Unicode 5.x.</span></span> <span data-ttu-id="39b71-1132"><xref:System.String> クラスおよび <xref:System.Globalization.SortVersion> クラスの「コメント」セクションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1132">See the <xref:System.String> class and the Remarks section of the <xref:System.Globalization.SortVersion> class.</span></span>

- <span data-ttu-id="39b71-1133">アプリケーション ドメインごとに文字列のハッシュ コードを計算する機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1133">Ability to compute the hash codes for strings on a per application domain basis.</span></span> <span data-ttu-id="39b71-1134">「[\<UseRandomizedStringHashAlgorithm> 要素](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1134">See [\<UseRandomizedStringHashAlgorithm> Element](../configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).</span></span>

- <span data-ttu-id="39b71-1135"><xref:System.Type> クラスと <xref:System.Reflection.TypeInfo> クラスで、タイプ リフレクションのサポートが分割されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-1135">Type reflection support split between <xref:System.Type> and <xref:System.Reflection.TypeInfo> classes.</span></span> <span data-ttu-id="39b71-1136">「[Windows ストア アプリのための .NET Framework のリフレクション](../reflection-and-codedom/reflection-for-windows-store-apps.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1136">See [Reflection in the .NET Framework for Windows Store Apps](../reflection-and-codedom/reflection-for-windows-store-apps.md).</span></span>

### <a name="managed-extensibility-framework-mef"></a><span data-ttu-id="39b71-1137">MEF (Managed Extensibility Framework)</span><span class="sxs-lookup"><span data-stu-id="39b71-1137">Managed Extensibility Framework (MEF)</span></span>

<span data-ttu-id="39b71-1138">.NET Framework 4.5 の MEF (Managed Extensibility Framework) には、次の新機能があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-1138">In .NET Framework 4.5, the Managed Extensibility Framework (MEF) provides the following new features:</span></span>

- <span data-ttu-id="39b71-1139">ジェネリック型のサポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1139">Support for generic types.</span></span>

- <span data-ttu-id="39b71-1140">属性ではなく命名規則に基づいてパーツを作成できるようにする、規則ベースのプログラミング モデル。</span><span class="sxs-lookup"><span data-stu-id="39b71-1140">Convention-based programming model that enables you to create parts based on naming conventions rather than attributes.</span></span>

- <span data-ttu-id="39b71-1141">複数のスコープ。</span><span class="sxs-lookup"><span data-stu-id="39b71-1141">Multiple scopes.</span></span>

- <span data-ttu-id="39b71-1142">Windows 8.x ストア アプリを作成するときに使うことができる MEF のサブセット。</span><span class="sxs-lookup"><span data-stu-id="39b71-1142">A subset of MEF that you can use when you create Windows 8.x Store apps.</span></span> <span data-ttu-id="39b71-1143">このサブセットは、[ダウンロード可能パッケージ](https://www.nuget.org/packages/Microsoft.Composition)として NuGet ギャラリーから入手できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1143">This subset is available as a [downloadable package](https://www.nuget.org/packages/Microsoft.Composition) from the NuGet Gallery.</span></span> <span data-ttu-id="39b71-1144">パッケージをインストールするには、Visual Studio でプロジェクトを開き、 **[プロジェクト]** メニューの **[NuGet パッケージの管理]** をクリックし、`Microsoft.Composition` パッケージをオンラインで検索します。</span><span class="sxs-lookup"><span data-stu-id="39b71-1144">To install the package, open your project in Visual Studio, choose **Manage NuGet Packages** from the **Project** menu, and search online for the `Microsoft.Composition` package.</span></span>

<span data-ttu-id="39b71-1145">詳しくは、「[Managed Extensibility Framework (MEF)](../mef/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1145">For more information, see [Managed Extensibility Framework (MEF)](../mef/index.md).</span></span>

### <a name="asynchronous-file-operations"></a><span data-ttu-id="39b71-1146">非同期のファイル操作</span><span class="sxs-lookup"><span data-stu-id="39b71-1146">Asynchronous file operations</span></span>

<span data-ttu-id="39b71-1147">.NET Framework 4.5 の C# および Visual Basic 言語に、新しい非同期機能が追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-1147">In .NET Framework 4.5, new asynchronous features were added to the C# and Visual Basic languages.</span></span> <span data-ttu-id="39b71-1148">これらの機能は、非同期操作を実行するためのタスク ベースのモデルを追加します。</span><span class="sxs-lookup"><span data-stu-id="39b71-1148">These features add a task-based model for performing asynchronous operations.</span></span> <span data-ttu-id="39b71-1149">この新しいモデルを使用するには、I/O クラスで非同期メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="39b71-1149">To use this new model, use the asynchronous methods in the I/O classes.</span></span> <span data-ttu-id="39b71-1150">「[非同期ファイル I/O](../../standard/io/asynchronous-file-i-o.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1150">See [Asynchronous File I/O](../../standard/io/asynchronous-file-i-o.md).</span></span>

<a name="tools"></a>

### <a name="tools"></a><span data-ttu-id="39b71-1151">ツール</span><span class="sxs-lookup"><span data-stu-id="39b71-1151">Tools</span></span>

<span data-ttu-id="39b71-1152">.NET Framework 4.5 のリソース ファイル ジェネレーター (Resgen.exe) を使用すると、.NET Framework アセンブリに埋め込まれた .resources ファイルから Windows 8.x ストア アプリ用の .resw ファイルを作成できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1152">In .NET Framework 4.5, Resource File Generator (Resgen.exe) enables you to create a .resw file for use in Windows 8.x Store apps from a .resources file embedded in a .NET Framework assembly.</span></span> <span data-ttu-id="39b71-1153">詳しくは、「[Resgen.exe (リソース ファイル ジェネレーター)](../tools/resgen-exe-resource-file-generator.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1153">For more information, see [Resgen.exe (Resource File Generator)](../tools/resgen-exe-resource-file-generator.md).</span></span>

<span data-ttu-id="39b71-1154">マネージド プロファイル ガイド付き最適化ツール (Mpgo.exe) を使用すると、ネイティブ イメージ アセンブリを最適化することによって、アプリケーションの起動時間、メモリの使用率 (ワーキング セットのサイズ)、およびスループットを向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1154">Managed Profile Guided Optimization (Mpgo.exe) enables you to improve application startup time, memory utilization (working set size), and throughput by optimizing native image assemblies.</span></span> <span data-ttu-id="39b71-1155">このコマンド ライン ツールは、ネイティブ イメージ アプリケーション アセンブリ用のプロファイル データを生成します。</span><span class="sxs-lookup"><span data-stu-id="39b71-1155">The command-line tool generates profile data for native image application assemblies.</span></span> <span data-ttu-id="39b71-1156">「[Mpgo.exe (マネージド プロファイル ガイド付き最適化ツール)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1156">See [Mpgo.exe (Managed Profile Guided Optimization Tool)](../tools/mpgo-exe-managed-profile-guided-optimization-tool.md).</span></span> <span data-ttu-id="39b71-1157">Visual Studio 2013 以降では、Windows 8.x ストア アプリおよびデスクトップ アプリを最適化するために、Mpgo.exe を使うことができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1157">Starting with Visual Studio 2013, you can use Mpgo.exe to optimize Windows 8.x Store apps as well as desktop apps.</span></span>

<a name="parallel"></a>

### <a name="parallel-computing"></a><span data-ttu-id="39b71-1158">並列コンピューティング</span><span class="sxs-lookup"><span data-stu-id="39b71-1158">Parallel computing</span></span>

<span data-ttu-id="39b71-1159">.NET Framework 4.5 には、並列計算用の新機能と機能強化がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="39b71-1159">.NET Framework 4.5 provides several new features and improvements for parallel computing.</span></span> <span data-ttu-id="39b71-1160">パフォーマンスの向上、コントロールの強化、非同期プログラミングのサポートの改善、新しいデータフロー ライブラリ、並列デバッグとパフォーマンス分析のためのサポートの強化などが挙げられます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1160">These include improved performance, increased control, improved support for asynchronous programming, a new dataflow library, and improved support for parallel debugging and performance analysis.</span></span> <span data-ttu-id="39b71-1161">.NET での並列プログラミングに関するブログの「[What’s New for Parallelism in .NET 4.5](https://devblogs.microsoft.com/pfxteam/whats-new-for-parallelism-in-net-4-5/)」(.NET 4.5 での並列処理の新機能) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1161">See the entry [What's New for Parallelism in .NET 4.5](https://devblogs.microsoft.com/pfxteam/whats-new-for-parallelism-in-net-4-5/) in the Parallel Programming with .NET blog.</span></span>

<a name="web"></a>

### <a name="web"></a><span data-ttu-id="39b71-1162">Web</span><span class="sxs-lookup"><span data-stu-id="39b71-1162">Web</span></span>

<span data-ttu-id="39b71-1163">ASP.NET 4.5 および 4.5.1 では、Web フォーム モデルのバインディング、WebSocket のサポート、非同期ハンドラー、パフォーマンスの向上などの多くの機能が追加されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-1163">ASP.NET 4.5 and 4.5.1 add model binding for Web Forms, WebSocket support, asynchronous handlers, performance enhancements, and many other features.</span></span> <span data-ttu-id="39b71-1164">詳細については、次のリソースを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1164">For more information, see the following resources:</span></span>

- <span data-ttu-id="39b71-1165">[ASP.NET 4.5 と Visual Studio 2012](/previous-versions/aspnet/hh420390(v=vs.110))</span><span class="sxs-lookup"><span data-stu-id="39b71-1165">[ASP.NET 4.5 and Visual Studio 2012](/previous-versions/aspnet/hh420390(v=vs.110))</span></span>

- [<span data-ttu-id="39b71-1166">Visual Studio 2013 の ASP.NET と Web ツールのリリース ノート</span><span class="sxs-lookup"><span data-stu-id="39b71-1166">ASP.NET and Web Tools for Visual Studio 2013 Release Notes</span></span>](/aspnet/visual-studio/overview/2013/release-notes)

### <a name="networking"></a><span data-ttu-id="39b71-1167">ネットワーク <a name="networking"></a></span><span class="sxs-lookup"><span data-stu-id="39b71-1167">Networking <a name="networking"></a></span></span>

<span data-ttu-id="39b71-1168">.NET Framework 4.5 には、HTTP アプリケーション用の新しいプログラミング インターフェイスがあります。</span><span class="sxs-lookup"><span data-stu-id="39b71-1168">.NET Framework 4.5 provides a new programming interface for HTTP applications.</span></span> <span data-ttu-id="39b71-1169">詳細については、新しい <xref:System.Net.Http?displayProperty=nameWithType> 名前空間と <xref:System.Net.Http.Headers?displayProperty=nameWithType> 名前空間を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1169">For more information, see the new <xref:System.Net.Http?displayProperty=nameWithType> and <xref:System.Net.Http.Headers?displayProperty=nameWithType> namespaces.</span></span>

<span data-ttu-id="39b71-1170">既存の <xref:System.Net.HttpListener> と関連クラスを使用して WebSocket 接続を受け入れ、やり取りするための新しいプログラミング インターフェイスのサポートも含まれています。</span><span class="sxs-lookup"><span data-stu-id="39b71-1170">Support is also included for a new programming interface for accepting and interacting with a WebSocket connection by using the existing <xref:System.Net.HttpListener> and related classes.</span></span> <span data-ttu-id="39b71-1171">詳細については、新しい <xref:System.Net.WebSockets> 名前空間と <xref:System.Net.HttpListener> クラスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1171">For more information, see the new <xref:System.Net.WebSockets> namespace and the <xref:System.Net.HttpListener> class.</span></span>

<span data-ttu-id="39b71-1172">また .NET Framework 4.5 には、ネットワークの次の機能強化があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-1172">In addition, .NET Framework 4.5 includes the following networking improvements:</span></span>

- <span data-ttu-id="39b71-1173">RFC 準拠の URI サポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1173">RFC-compliant URI support.</span></span> <span data-ttu-id="39b71-1174">詳細については、<xref:System.Uri> および関連クラスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1174">For more information, see <xref:System.Uri> and related classes.</span></span>

- <span data-ttu-id="39b71-1175">国際化ドメイン名 (IDN: Internationalized Domain Name) による解析のサポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1175">Support for Internationalized Domain Name (IDN) parsing.</span></span> <span data-ttu-id="39b71-1176">詳細については、<xref:System.Uri> および関連クラスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1176">For more information, see <xref:System.Uri> and related classes.</span></span>

- <span data-ttu-id="39b71-1177">電子メール アドレスの国際化 (EAI) のサポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1177">Support for Email Address Internationalization (EAI).</span></span> <span data-ttu-id="39b71-1178">詳細については、「<xref:System.Net.Mail>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1178">For more information, see the <xref:System.Net.Mail> namespace.</span></span>

- <span data-ttu-id="39b71-1179">強化された IPv6 サポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1179">Improved IPv6 support.</span></span> <span data-ttu-id="39b71-1180">詳細については、「<xref:System.Net.NetworkInformation>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1180">For more information, see the <xref:System.Net.NetworkInformation> namespace.</span></span>

- <span data-ttu-id="39b71-1181">デュアル モードのソケットのサポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1181">Dual-mode socket support.</span></span> <span data-ttu-id="39b71-1182">詳細については、<xref:System.Net.Sockets.Socket> クラスおよび <xref:System.Net.Sockets.TcpListener> クラスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1182">For more information, see the <xref:System.Net.Sockets.Socket> and <xref:System.Net.Sockets.TcpListener> classes.</span></span>

<a name="client"></a>

### <a name="windows-presentation-foundation-wpf"></a><span data-ttu-id="39b71-1183">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="39b71-1183">Windows Presentation Foundation (WPF)</span></span>

<span data-ttu-id="39b71-1184">.NET Framework 4.5 の WPF (Windows Presentation Foundation) には、次の領域で機能変更および強化があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-1184">In .NET Framework 4.5, Windows Presentation Foundation (WPF) contains changes and improvements in the following areas:</span></span>

- <span data-ttu-id="39b71-1185">クイック アクセス ツール バー、アプリケーション メニューおよびタブをホストするリボン ユーザー インターフェイスを実装できる新しい <xref:System.Windows.Controls.Ribbon.Ribbon> コントロール。</span><span class="sxs-lookup"><span data-stu-id="39b71-1185">The new <xref:System.Windows.Controls.Ribbon.Ribbon> control, which enables you to implement a ribbon user interface that hosts a Quick Access Toolbar, Application Menu, and tabs.</span></span>

- <span data-ttu-id="39b71-1186">同期および非同期のデータ検証をサポートする新しい <xref:System.ComponentModel.INotifyDataErrorInfo> インターフェイス。</span><span class="sxs-lookup"><span data-stu-id="39b71-1186">The new <xref:System.ComponentModel.INotifyDataErrorInfo> interface, which supports synchronous and asynchronous data validation.</span></span>

- <span data-ttu-id="39b71-1187"><xref:System.Windows.Controls.VirtualizingPanel> および <xref:System.Windows.Threading.Dispatcher> クラスの新しい機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1187">New features for the <xref:System.Windows.Controls.VirtualizingPanel> and <xref:System.Windows.Threading.Dispatcher> classes.</span></span>

- <span data-ttu-id="39b71-1188">グループ化された大量のデータを表示するときに、非 UI スレッドのコレクションにアクセスすることによってパフォーマンスを向上。</span><span class="sxs-lookup"><span data-stu-id="39b71-1188">Improved performance when displaying large sets of grouped data, and by accessing collections on non-UI threads.</span></span>

- <span data-ttu-id="39b71-1189">静的プロパティへのデータ バインディング、<xref:System.Reflection.ICustomTypeProvider> インターフェイスを実装するカスタム型へのデータ バインディング、およびバインディング式からのデータ バインディング情報の取得。</span><span class="sxs-lookup"><span data-stu-id="39b71-1189">Data binding to static properties, data binding to custom types that implement the <xref:System.Reflection.ICustomTypeProvider> interface, and retrieval of data binding information from a binding expression.</span></span>

- <span data-ttu-id="39b71-1190">値の変更に伴うデータの再配置 (ライブ形成)。</span><span class="sxs-lookup"><span data-stu-id="39b71-1190">Repositioning of data as the values change (live shaping).</span></span>

- <span data-ttu-id="39b71-1191">項目コンテナーのデータ コンテキストを切断するかどうかをチェックする機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1191">Ability to check whether the data context for an item container is disconnected.</span></span>

- <span data-ttu-id="39b71-1192">プロパティの変更とデータ ソースの更新までの経過時間を設定する機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1192">Ability to set the amount of time that should elapse between property changes and data source updates.</span></span>

- <span data-ttu-id="39b71-1193">弱いイベント パターン実装時のサポートの強化。</span><span class="sxs-lookup"><span data-stu-id="39b71-1193">Improved support for implementing weak event patterns.</span></span> <span data-ttu-id="39b71-1194">また、イベントでマークアップ拡張機能を使用することもできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="39b71-1194">Also, events can now accept markup extensions.</span></span>

<a name="windows_communication_foundation"></a>

### <a name="windows-communication-foundation-wcf"></a><span data-ttu-id="39b71-1195">Windows Communication Foundation (WCF)</span><span class="sxs-lookup"><span data-stu-id="39b71-1195">Windows Communication Foundation (WCF)</span></span>

<span data-ttu-id="39b71-1196">.NET Framework 4.5 では、Windows Communication Foundation (WCF) アプリケーションの記述と保守を簡単にするため、次の機能が追加されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-1196">In .NET Framework 4.5, the following features have been added to make it simpler to write and maintain Windows Communication Foundation (WCF) applications:</span></span>

- <span data-ttu-id="39b71-1197">生成された構成ファイルの簡略化。</span><span class="sxs-lookup"><span data-stu-id="39b71-1197">Simplification of generated configuration files.</span></span>

- <span data-ttu-id="39b71-1198">コントラクト優先開発のサポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1198">Support for contract-first development.</span></span>

- <span data-ttu-id="39b71-1199">ASP.NET 互換モードをより簡単に構成できる機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1199">Ability to configure ASP.NET compatibility mode more easily.</span></span>

- <span data-ttu-id="39b71-1200">既定のトランスポート プロパティ値に変更を加え、設定しなければならない可能性を低減しました。</span><span class="sxs-lookup"><span data-stu-id="39b71-1200">Changes in default transport property values to reduce the likelihood that you will have to set them.</span></span>

- <span data-ttu-id="39b71-1201"><xref:System.Xml.XmlDictionaryReaderQuotas> クラスを更新して、XML ディクショナリ リーダーのクォータを手動で構成する手間を省けるようにしました。</span><span class="sxs-lookup"><span data-stu-id="39b71-1201">Updates to the <xref:System.Xml.XmlDictionaryReaderQuotas> class to reduce the likelihood that you will have to manually configure quotas for XML dictionary readers.</span></span>

- <span data-ttu-id="39b71-1202">ビルド処理の一部として Visual Studio による WCF 構成ファイルを検証することで、アプリケーションを実行する前に構成エラーを検出できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1202">Validation of WCF configuration files by Visual Studio as part of the build process, so you can detect configuration errors before you run your application.</span></span>

- <span data-ttu-id="39b71-1203">新しい非同期ストリーミングのサポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1203">New asynchronous streaming support.</span></span>

- <span data-ttu-id="39b71-1204">Internet Information Services (IIS) での HTTPS 上のエンドポイントを公開しやすくする新しい HTTPS プロトコル マッピング。</span><span class="sxs-lookup"><span data-stu-id="39b71-1204">New HTTPS protocol mapping to make it easier to expose an endpoint over HTTPS with Internet Information Services (IIS).</span></span>

- <span data-ttu-id="39b71-1205">`?singleWSDL` をサービス URL に追加して 1 つの WSDL ドキュメントのメタデータを生成する機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1205">Ability to generate metadata in a single WSDL document by appending `?singleWSDL` to the service URL.</span></span>

- <span data-ttu-id="39b71-1206">TCP トランスポートと同様のパフォーマンス特性を持つポート 80 と 443 で真の双方向通信を可能にする Websockets のサポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1206">Websockets support to enable true bidirectional communication over ports 80 and 443 with performance characteristics similar to the TCP transport.</span></span>

- <span data-ttu-id="39b71-1207">コード内の構成サービスのサポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1207">Support for configuring services in code.</span></span>

- <span data-ttu-id="39b71-1208">XML エディターのツール ヒント。</span><span class="sxs-lookup"><span data-stu-id="39b71-1208">XML Editor tooltips.</span></span>

- <span data-ttu-id="39b71-1209"><xref:System.ServiceModel.ChannelFactory> キャッシュのサポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1209"><xref:System.ServiceModel.ChannelFactory> caching support.</span></span>

- <span data-ttu-id="39b71-1210">バイナリ エンコーダーの圧縮サポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1210">Binary encoder compression support.</span></span>

- <span data-ttu-id="39b71-1211">開発者が「ファイア アンド フォーゲット (撃ち放し)」メッセージングを使用するサービスを作成できるようにする UDP トランスポートのサポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1211">Support for a UDP transport that enables developers to write services that use "fire and forget" messaging.</span></span> <span data-ttu-id="39b71-1212">クライアントは、サービスにメッセージを送信しますが、サービスからの応答を期待しません。</span><span class="sxs-lookup"><span data-stu-id="39b71-1212">A client sends a message to a service and expects no response from the service.</span></span>

- <span data-ttu-id="39b71-1213">HTTP トランスポートとトランスポート セキュリティを使用したときに、単一の WCF エンドポイントで複数の認証モードをサポートする機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1213">Ability to support multiple authentication modes on a single WCF endpoint when using the HTTP transport and transport security.</span></span>

- <span data-ttu-id="39b71-1214">国際化ドメイン名 (IDN: Internationalized Domain Name) を使用する WCF サービスのサポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1214">Support for WCF services that use internationalized domain names (IDNs).</span></span>

<span data-ttu-id="39b71-1215">詳細については、「[Windows Communication Foundation 4.5 の新機能](../wcf/whats-new.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1215">For more information, see [What's New in Windows Communication Foundation](../wcf/whats-new.md).</span></span>

<a name="windows_workflow_foundation"></a>

### <a name="windows-workflow-foundation-wf"></a><span data-ttu-id="39b71-1216">Windows Workflow Foundation (WF)</span><span class="sxs-lookup"><span data-stu-id="39b71-1216">Windows Workflow Foundation (WF)</span></span>

<span data-ttu-id="39b71-1217">.NET Framework 4.5 では、次に示すいくつかの新機能が Windows Workflow Foundation (WF) に追加されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-1217">In .NET Framework 4.5, several new features were added to Windows Workflow Foundation (WF), including:</span></span>

- <span data-ttu-id="39b71-1218">最初に .NET Framework 4.0.1 ([.NET Framework 4 Platform Update 1](/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)) の一部として導入された、ステート マシンのワークフロー。</span><span class="sxs-lookup"><span data-stu-id="39b71-1218">State machine workflows, which were first introduced as part of .NET Framework 4.0.1 ([.NET Framework 4 Platform Update 1](/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1)).</span></span> <span data-ttu-id="39b71-1219">この更新プログラムには、開発者がステート マシン ワークフローを作成できるようにする新しいクラスとアクティビティが複数含まれていました。</span><span class="sxs-lookup"><span data-stu-id="39b71-1219">This update included several new classes and activities that enabled developers to create state machine workflows.</span></span> <span data-ttu-id="39b71-1220">.NET Framework 4.5 では、これらのクラスとアクティビティが、次を含むように更新されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-1220">These classes and activities were updated for .NET Framework 4.5 to include:</span></span>

  - <span data-ttu-id="39b71-1221">状態でブレークポイントを設定する機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1221">The ability to set breakpoints on states.</span></span>

  - <span data-ttu-id="39b71-1222">ワークフロー デザイナーで遷移をコピーして貼り付ける機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1222">The ability to copy and paste transitions in the workflow designer.</span></span>

  - <span data-ttu-id="39b71-1223">共有されるトリガーの遷移作成のデザイナー サポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1223">Designer support for shared trigger transition creation.</span></span>

  - <span data-ttu-id="39b71-1224"><xref:System.Activities.Statements.StateMachine>、 <xref:System.Activities.Statements.State>、および <xref:System.Activities.Statements.Transition> などのようにステート マシン ワークフローを作成する機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1224">Activities for creating state machine workflows, including: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, and <xref:System.Activities.Statements.Transition>.</span></span>

- <span data-ttu-id="39b71-1225">次のようなワークフロー デザイナーの機能が強化されました。</span><span class="sxs-lookup"><span data-stu-id="39b71-1225">Enhanced Workflow Designer features such as the following:</span></span>

  - <span data-ttu-id="39b71-1226">**[クイック検索]** や **[フォルダーを指定して検索]** など、Visual Studio で強化されたワークフロー検索機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1226">Enhanced workflow search capabilities in Visual Studio, including **Quick Find** and **Find in Files** .</span></span>

  - <span data-ttu-id="39b71-1227">2 番目の子アクティビティがコンテナー アクティビティに追加されたときに、自動的にシーケンス アクティビティを作成し、両方のアクティビティをシーケンス アクティビティに含める機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1227">Ability to automatically create a Sequence activity when a second child activity is added to a container activity, and to include both activities in the Sequence activity.</span></span>

  - <span data-ttu-id="39b71-1228">スクロール バーを使用せずに変更されるワークフローの表示部分を変更できるようにするパン サポート。</span><span class="sxs-lookup"><span data-stu-id="39b71-1228">Panning support, which enables the visible portion of a workflow to be changed without using the scroll bars.</span></span>

  - <span data-ttu-id="39b71-1229">ツリー スタイルのアウトライン ビューでワークフローのコンポーネントを表示し、 **[ドキュメント アウトライン]** ビューでコンポーネントを選択できるようにする新しい **[ドキュメント アウトライン]** ビュー。</span><span class="sxs-lookup"><span data-stu-id="39b71-1229">A new **Document Outline** view that shows the components of a workflow in a tree-style outline view and lets you select a component in the **Document Outline** view.</span></span>

  - <span data-ttu-id="39b71-1230">アクティビティに注釈を追加できる機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1230">Ability to add annotations to activities.</span></span>

  - <span data-ttu-id="39b71-1231">ワークフロー デザイナーでアクティビティ デリゲートを定義および使用する機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1231">Ability to define and consume activity delegates by using the workflow designer.</span></span>

  - <span data-ttu-id="39b71-1232">ステート マシンのアクティビティと遷移、およびフローチャート ワークフローの自動接続と自動挿入。</span><span class="sxs-lookup"><span data-stu-id="39b71-1232">Auto-connect and auto-insert for activities and transitions in state machine and flowchart workflows.</span></span>

- <span data-ttu-id="39b71-1233">ワークフローのビュー状態情報を XAML ファイルの 1 つの要素に保管して、ビュー状態情報を簡単に見つけ、編集できるようにします。</span><span class="sxs-lookup"><span data-stu-id="39b71-1233">Storage of the view state information for a workflow in a single element in the XAML file, so you can easily locate and edit the view state information.</span></span>

- <span data-ttu-id="39b71-1234">子アクティビティの永続化を防ぐ NoPersistScope コンテナー アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="39b71-1234">A NoPersistScope container activity to prevent child activities from persisting.</span></span>

- <span data-ttu-id="39b71-1235">C# 式のサポート:</span><span class="sxs-lookup"><span data-stu-id="39b71-1235">Support for C# expressions:</span></span>

  - <span data-ttu-id="39b71-1236">Visual Basic を使用するワークフロー プロジェクトは、Visual Basic 式を使用し、C# ワークフロー プロジェクトは C# 式を使用します。</span><span class="sxs-lookup"><span data-stu-id="39b71-1236">Workflow projects that use Visual Basic will use Visual Basic expressions, and C# workflow projects will use C# expressions.</span></span>

  - <span data-ttu-id="39b71-1237">Visual Studio 2010 で作成され、Visual Basic 式が使用されている C# ワークフロー プロジェクトは、C# 式を使用する C# ワークフロー プロジェクトと互換性があります。</span><span class="sxs-lookup"><span data-stu-id="39b71-1237">C# workflow projects that were created in Visual Studio 2010 and that have Visual Basic expressions are compatible with C# workflow projects that use C# expressions.</span></span>

- <span data-ttu-id="39b71-1238">バージョン管理機能の強化</span><span class="sxs-lookup"><span data-stu-id="39b71-1238">Versioning enhancements:</span></span>

  - <span data-ttu-id="39b71-1239">永続化されたワークフロー インスタンスとワークフロー定義間のマッピングを提供する新しい <xref:System.Activities.WorkflowIdentity> クラス。</span><span class="sxs-lookup"><span data-stu-id="39b71-1239">The new  <xref:System.Activities.WorkflowIdentity> class, which provides a mapping between a persisted workflow instance and its workflow definition.</span></span>

  - <span data-ttu-id="39b71-1240"><xref:System.ServiceModel.Activities.WorkflowServiceHost> を含む同じホスト内の複数のワークフローのバージョンの並列実行。</span><span class="sxs-lookup"><span data-stu-id="39b71-1240">Side-by-side execution of multiple workflow versions in the same host, including <xref:System.ServiceModel.Activities.WorkflowServiceHost>.</span></span>

  - <span data-ttu-id="39b71-1241">動的更新プログラムで、永続化されたワークフロー インスタンスの定義を変更する機能。</span><span class="sxs-lookup"><span data-stu-id="39b71-1241">In Dynamic Update, the ability to modify the definition of a persisted workflow instance.</span></span>

- <span data-ttu-id="39b71-1242">既存のサービス コントラクトに合わせて自動的にアクティビティを生成するサポートが提供されるコントラクト優先のワークフロー サービス開発。</span><span class="sxs-lookup"><span data-stu-id="39b71-1242">Contract-first workflow service development, which provides support for automatically generating activities to match an existing service contract.</span></span>

<span data-ttu-id="39b71-1243">詳細については、「[.NET 4.5 での Windows Workflow Foundation の新機能](../windows-workflow-foundation/whats-new-in-wf-in-dotnet.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1243">For more information, see [What's New in Windows Workflow Foundation](../windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).</span></span>

<a name="tailored"></a>

### <a name="net-for-windows-8x-store-apps"></a><span data-ttu-id="39b71-1244">Windows 8.x ストア アプリ用 .NET</span><span class="sxs-lookup"><span data-stu-id="39b71-1244">.NET for Windows 8.x Store apps</span></span>

<span data-ttu-id="39b71-1245">Windows 8.x ストア アプリは、特定のフォーム ファクターに合わせて設計されており、Windows オペレーティング システムの機能を利用します。</span><span class="sxs-lookup"><span data-stu-id="39b71-1245">Windows 8.x Store apps are designed for specific form factors and leverage the power of the Windows operating system.</span></span> <span data-ttu-id="39b71-1246">.NET Framework 4.5 または 4.5.1 のサブセットで、C# または Visual Basic を使用して、Windows 用の Windows 8.x ストア アプリをビルドすることができます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1246">A subset of .NET Framework 4.5 or 4.5.1 is available for building Windows 8.x Store apps for Windows by using C# or Visual Basic.</span></span> <span data-ttu-id="39b71-1247">このサブセットは Windows 8.x ストア アプリ用 .NET と呼ばれ、[概要](/previous-versions/windows/apps/br230302(v=vs.140))のページで説明されています。</span><span class="sxs-lookup"><span data-stu-id="39b71-1247">This subset is called .NET for Windows 8.x Store apps and is discussed in an [overview](/previous-versions/windows/apps/br230302(v=vs.140)).</span></span>

### <a name="portable-class-libraries"></a><span data-ttu-id="39b71-1248">ポータブル クラス ライブラリ <a name="portable"></a></span><span class="sxs-lookup"><span data-stu-id="39b71-1248">Portable Class Libraries <a name="portable"></a></span></span>

<span data-ttu-id="39b71-1249">Visual Studio 2012 (および以降のバージョン) のポータブル クラス ライブラリ プロジェクトを使うと、複数の .NET Framework プラットフォームで動作するマネージド アセンブリを作成してビルドできます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1249">The Portable Class Library project in Visual Studio 2012 (and later versions) enables you to write and build managed assemblies that work on multiple .NET Framework platforms.</span></span> <span data-ttu-id="39b71-1250">ポータブル クラス ライブラリ プロジェクトを使って、対象とするプラットフォーム (Windows Phone や Windows 8.x ストア アプリ用 .NET など) を選択できます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1250">Using a Portable Class Library project, you choose the platforms (such as Windows Phone and .NET for Windows 8.x Store apps) to target.</span></span> <span data-ttu-id="39b71-1251">プロジェクトで使用できる型およびメンバーは、自動的にこれらのプラットフォーム間で共通の型とメンバーに制限されます。</span><span class="sxs-lookup"><span data-stu-id="39b71-1251">The available types and members in your project are automatically restricted to the common types and members across these platforms.</span></span> <span data-ttu-id="39b71-1252">詳細については、[ポータブル クラス ライブラリ](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)に関するページを参照してください。</span><span class="sxs-lookup"><span data-stu-id="39b71-1252">For more information, see [Portable Class Library](../../standard/cross-platform/cross-platform-development-with-the-portable-class-library.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="39b71-1253">関連項目</span><span class="sxs-lookup"><span data-stu-id="39b71-1253">See also</span></span>

- [<span data-ttu-id="39b71-1254">NET Framework および特別なリリース</span><span class="sxs-lookup"><span data-stu-id="39b71-1254">The .NET Framework and Out-of-Band Releases</span></span>](../get-started/the-net-framework-and-out-of-band-releases.md)
- [<span data-ttu-id="39b71-1255">.NET Framework のアクセシビリティの新機能</span><span class="sxs-lookup"><span data-stu-id="39b71-1255">What's new in accessibility in .NET Framework</span></span>](whats-new-in-accessibility.md)
- [<span data-ttu-id="39b71-1256">Visual Studio 2017 の新機能</span><span class="sxs-lookup"><span data-stu-id="39b71-1256">What's New in Visual Studio 2017</span></span>](/visualstudio/ide/whats-new-visual-studio-2017)
- [<span data-ttu-id="39b71-1257">Visual Studio 2019 の新機能</span><span class="sxs-lookup"><span data-stu-id="39b71-1257">What's New in Visual Studio 2019</span></span>](/visualstudio/ide/whats-new-visual-studio-2019)
- [<span data-ttu-id="39b71-1258">ASP.NET</span><span class="sxs-lookup"><span data-stu-id="39b71-1258">ASP.NET</span></span>](/aspnet)
- [<span data-ttu-id="39b71-1259">Visual Studio での C++ の新機能</span><span class="sxs-lookup"><span data-stu-id="39b71-1259">What's New for C++ in Visual Studio</span></span>](/cpp/what-s-new-for-visual-cpp-in-visual-studio)
