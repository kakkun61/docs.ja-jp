---
title: .NET Framework およびアプリケーションの配置
description: .NET とアプリケーションのデプロイすることから始めます。 .NET には、ゼロインパクト アプリケーション、プライベート コンポーネント (既定で)、制御コードの共有などが用意されています。
ms.date: 03/30/2017
helpviewer_keywords:
- deploying applications [.NET Framework], packaging
- deploying applications [.NET Framework]
- deploying applications [.NET Framework], features
- deploying applications [.NET Framework], distribution
- .NET Framework, deploying
- .NET Framework application deployment
ms.assetid: 238d8284-6042-4a38-a7f6-1ee8efd719da
ms.openlocfilehash: 9948d5313c5168965f3ff991b26a4bc913f7d7ee
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94817030"
---
# <a name="deploying-the-net-framework-and-applications"></a><span data-ttu-id="413a4-104">.NET Framework およびアプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="413a4-104">Deploying the .NET Framework and Applications</span></span>

<span data-ttu-id="413a4-105">ここでは、アプリケーションと共に .NET Framework を配置する方法についての概要を示します。</span><span class="sxs-lookup"><span data-stu-id="413a4-105">This article helps you get started deploying the .NET Framework with your application.</span></span> <span data-ttu-id="413a4-106">情報のほとんどは、開発者、OEM、およびエンタープライズ管理者を対象としています。</span><span class="sxs-lookup"><span data-stu-id="413a4-106">Most of the information is intended for developers, OEMs, and enterprise administrators.</span></span> <span data-ttu-id="413a4-107">コンピュータに .NET Framework をインストールするユーザーは、「[.NET Framework のインストール](../install/index.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="413a4-107">Users who want to install the .NET Framework on their computers should read [Installing the .NET Framework](../install/index.md).</span></span>

## <a name="key-deployment-resources"></a><span data-ttu-id="413a4-108">主な配置リソース</span><span class="sxs-lookup"><span data-stu-id="413a4-108">Key Deployment Resources</span></span>

<span data-ttu-id="413a4-109">.NET Framework の配置とサービスの詳細については、次に示す他の MSDN トピックへのリンク先を参照してください。</span><span class="sxs-lookup"><span data-stu-id="413a4-109">Use the following links to other MSDN topics for specific information about deploying and servicing the .NET Framework.</span></span>

<span data-ttu-id="413a4-110">**セットアップと配置**</span><span class="sxs-lookup"><span data-stu-id="413a4-110">**Setup and deployment**</span></span>

- <span data-ttu-id="413a4-111">インストーラーと配置についての一般的な情報:</span><span class="sxs-lookup"><span data-stu-id="413a4-111">General installer and deployment information:</span></span>

  - <span data-ttu-id="413a4-112">インストーラー オプション:</span><span class="sxs-lookup"><span data-stu-id="413a4-112">Installer options:</span></span>

    - [<span data-ttu-id="413a4-113">Web インストーラー</span><span class="sxs-lookup"><span data-stu-id="413a4-113">Web installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

    - [<span data-ttu-id="413a4-114">オフライン インストーラー</span><span class="sxs-lookup"><span data-stu-id="413a4-114">Offline installer</span></span>](../install/guide-for-developers.md#to-install-or-download-the-net-framework-redistributable)

  - <span data-ttu-id="413a4-115">インストール モード:</span><span class="sxs-lookup"><span data-stu-id="413a4-115">Installation modes:</span></span>

    - [<span data-ttu-id="413a4-116">サイレント インストール</span><span class="sxs-lookup"><span data-stu-id="413a4-116">Silent installation</span></span>](deployment-guide-for-developers.md#chaining_custom)

    - [<span data-ttu-id="413a4-117">UI の表示</span><span class="sxs-lookup"><span data-stu-id="413a4-117">Displaying a UI</span></span>](deployment-guide-for-developers.md#chaining_default)

  - [<span data-ttu-id="413a4-118">.NET Framework 4.5 のインストール中のシステム再起動の削減</span><span class="sxs-lookup"><span data-stu-id="413a4-118">Reducing system restarts during .NET Framework 4.5 installations</span></span>](reducing-system-restarts.md)

  - [<span data-ttu-id="413a4-119">.NET Framework のインストールおよびアンインストールのブロックのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="413a4-119">Troubleshoot blocked .NET Framework installations and uninstallations</span></span>](../install/troubleshoot-blocked-installations-and-uninstallations.md)

- <span data-ttu-id="413a4-120">.NET Framework とクライアント アプリケーションの配置 (開発者向け):</span><span class="sxs-lookup"><span data-stu-id="413a4-120">Deploying the .NET Framework with a client application (for developers):</span></span>

  - <span data-ttu-id="413a4-121">セットアップと配置プロジェクトでの [InstallShield の使用](deployment-guide-for-developers.md#installshield-deployment)</span><span class="sxs-lookup"><span data-stu-id="413a4-121">[Using InstallShield](deployment-guide-for-developers.md#installshield-deployment) in a setup and deployment project</span></span>

  - [<span data-ttu-id="413a4-122">Visual Studio の ClickOnce アプリケーションの使用</span><span class="sxs-lookup"><span data-stu-id="413a4-122">Using a Visual Studio ClickOnce application</span></span>](deployment-guide-for-developers.md#clickonce-deployment)

  - [<span data-ttu-id="413a4-123">WiX インストール パッケージの作成</span><span class="sxs-lookup"><span data-stu-id="413a4-123">Creating a WiX installation package</span></span>](deployment-guide-for-developers.md#wix)

  - [<span data-ttu-id="413a4-124">カスタム インストーラーの使用</span><span class="sxs-lookup"><span data-stu-id="413a4-124">Using a custom installer</span></span>](deployment-guide-for-developers.md#chaining)

  - <span data-ttu-id="413a4-125">開発者向けの[追加情報](deployment-guide-for-developers.md)</span><span class="sxs-lookup"><span data-stu-id="413a4-125">[Additional information](deployment-guide-for-developers.md) for developers</span></span>

- <span data-ttu-id="413a4-126">.NET Framework の配置 (OEM と管理者向け):</span><span class="sxs-lookup"><span data-stu-id="413a4-126">Deploying the .NET Framework (for OEMs and administrators):</span></span>

  - [<span data-ttu-id="413a4-127">Windows アセスメント & デプロイメント キット (ADK)</span><span class="sxs-lookup"><span data-stu-id="413a4-127">Windows Assessment and Deployment Kit (ADK)</span></span>](/windows-hardware/get-started/adk-install)

  - [<span data-ttu-id="413a4-128">管理者ガイド</span><span class="sxs-lookup"><span data-stu-id="413a4-128">Administrator's guide</span></span>](guide-for-administrators.md)

<span data-ttu-id="413a4-129">**サービス**</span><span class="sxs-lookup"><span data-stu-id="413a4-129">**Servicing**</span></span>

- <span data-ttu-id="413a4-130">一般的な情報については、[.NET Framework に関するブログ](https://devblogs.microsoft.com/dotnet/)をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="413a4-130">For general information, see the [.NET Framework blog](https://devblogs.microsoft.com/dotnet/).</span></span>

- [<span data-ttu-id="413a4-131">バージョンの検出</span><span class="sxs-lookup"><span data-stu-id="413a4-131">Detecting versions</span></span>](../migration-guide/how-to-determine-which-versions-are-installed.md)

- [<span data-ttu-id="413a4-132">Service Pack と更新プログラムの検出</span><span class="sxs-lookup"><span data-stu-id="413a4-132">Detecting service packs and updates</span></span>](../migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)

## <a name="features-that-simplify-deployment"></a><span data-ttu-id="413a4-133">配置を簡素化する機能</span><span class="sxs-lookup"><span data-stu-id="413a4-133">Features That Simplify Deployment</span></span>

<span data-ttu-id="413a4-134">.NET Framework には、アプリケーションを簡単に配置できるようにするための基本機能が数多く用意されています。</span><span class="sxs-lookup"><span data-stu-id="413a4-134">The .NET Framework provides a number of basic features that make it easier to deploy your applications:</span></span>

- <span data-ttu-id="413a4-135">ゼロインパクト アプリケーション</span><span class="sxs-lookup"><span data-stu-id="413a4-135">No-impact applications.</span></span>

     <span data-ttu-id="413a4-136">この機能は、アプリケーションを分離し、DLL の競合を解消します。</span><span class="sxs-lookup"><span data-stu-id="413a4-136">This feature provides application isolation and eliminates DLL conflicts.</span></span> <span data-ttu-id="413a4-137">既定では、コンポーネントはほかのアプリケーションに影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="413a4-137">By default, components do not affect other applications.</span></span>

- <span data-ttu-id="413a4-138">プライベート コンポーネント (既定)</span><span class="sxs-lookup"><span data-stu-id="413a4-138">Private components by default.</span></span>

     <span data-ttu-id="413a4-139">既定では、コンポーネントはアプリケーション ディレクトリに配置され、コンテナー アプリケーションだけで参照できます。</span><span class="sxs-lookup"><span data-stu-id="413a4-139">By default, components are deployed to the application directory and are visible only to the containing application.</span></span>

- <span data-ttu-id="413a4-140">制御コードの共有</span><span class="sxs-lookup"><span data-stu-id="413a4-140">Controlled code sharing.</span></span>

     <span data-ttu-id="413a4-141">コードを共有するには、既定の動作を実行する代わりに、共有するためのコードを明示的に作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="413a4-141">Code sharing requires you to explicitly make code available for sharing instead of being the default behavior.</span></span>

- <span data-ttu-id="413a4-142">side-by-side でのバージョン管理。</span><span class="sxs-lookup"><span data-stu-id="413a4-142">Side-by-side versioning.</span></span>

     <span data-ttu-id="413a4-143">コンポーネントまたはアプリケーションの複数のバージョンを共存させ、使用するバージョンを選択できます。共通言語ランタイムによって、バージョン管理ポリシーが適用されます。</span><span class="sxs-lookup"><span data-stu-id="413a4-143">Multiple versions of a component or application can coexist, you can choose which versions to use, and the common language runtime enforces versioning policy.</span></span>

- <span data-ttu-id="413a4-144">XCOPY による配置およびレプリケーション</span><span class="sxs-lookup"><span data-stu-id="413a4-144">XCOPY deployment and replication.</span></span>

     <span data-ttu-id="413a4-145">自己言及的な、単体で使用できるコンポーネントやアプリケーションは、レジストリ エントリや依存関係を設定せずに配置できます。</span><span class="sxs-lookup"><span data-stu-id="413a4-145">Self-described and self-contained components and applications can be deployed without registry entries or dependencies.</span></span>

- <span data-ttu-id="413a4-146">実行時更新</span><span class="sxs-lookup"><span data-stu-id="413a4-146">On-the-fly updates.</span></span>

     <span data-ttu-id="413a4-147">管理者は、ASP.NET などのホストを使用してプログラムの DLL を更新できます。リモート コンピューター上の DLL も更新できます。</span><span class="sxs-lookup"><span data-stu-id="413a4-147">Administrators can use hosts, such as ASP.NET, to update program DLLs, even on remote computers.</span></span>

- <span data-ttu-id="413a4-148">Windows インストーラーとの統合</span><span class="sxs-lookup"><span data-stu-id="413a4-148">Integration with the Windows Installer.</span></span>

     <span data-ttu-id="413a4-149">アプリケーションを配置するときに、通知、発行、修復、およびオンデマンド インストールのすべてを使用できます。</span><span class="sxs-lookup"><span data-stu-id="413a4-149">Advertisement, publishing, repair, and install-on-demand are all available when deploying your application.</span></span>

- <span data-ttu-id="413a4-150">エンタープライズ配置</span><span class="sxs-lookup"><span data-stu-id="413a4-150">Enterprise deployment.</span></span>

     <span data-ttu-id="413a4-151">この機能を使用すると、Active Directory を使用する場合など、ソフトウェアの配布を簡単に行うことができます。</span><span class="sxs-lookup"><span data-stu-id="413a4-151">This feature provides easy software distribution, including using Active Directory.</span></span>

- <span data-ttu-id="413a4-152">ダウンロードとキャッシュ</span><span class="sxs-lookup"><span data-stu-id="413a4-152">Downloading and caching.</span></span>

     <span data-ttu-id="413a4-153">インクリメンタル ダウンロードにより、ダウンロードのサイズを小さくすることができます。また、コンポーネントを分離して、そのアプリケーションだけで使用されるようにし、配置の影響を抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="413a4-153">Incremental downloads keep downloads smaller, and components can be isolated for use only by the application for low-impact deployment.</span></span>

- <span data-ttu-id="413a4-154">完全な権利を与えられていないコード</span><span class="sxs-lookup"><span data-stu-id="413a4-154">Partially trusted code.</span></span>

     <span data-ttu-id="413a4-155">ID は、ユーザーではなく、コードに基づきます。証明書関連のダイアログ ボックスは表示されません。</span><span class="sxs-lookup"><span data-stu-id="413a4-155">Identity is based on the code instead of the user, and no certificate dialog boxes appear.</span></span>

## <a name="packaging-and-distributing-net-framework-applications"></a><span data-ttu-id="413a4-156">.NET Framework アプリケーションのパッケージ化と配布</span><span class="sxs-lookup"><span data-stu-id="413a4-156">Packaging and Distributing .NET Framework Applications</span></span>

<span data-ttu-id="413a4-157">.NET Framework でのパッケージ化および配置についての情報の一部は、ドキュメントの別のトピックで説明します。</span><span class="sxs-lookup"><span data-stu-id="413a4-157">Some of the packaging and deployment information for the .NET Framework is described in other sections of the documentation.</span></span> <span data-ttu-id="413a4-158">それらのトピックでは、レジストリ エントリを必要としない[アセンブリ](../../standard/assembly/index.md)と呼ばれる自己言及的な単位、名前の一意性を保証し、名前の悪用を防止する[厳密な名前付きアセンブリ](../../standard/assembly/strong-named.md)、DLL 競合に関連した問題の多くを解決する[アセンブリのバージョン管理](../../standard/assembly/versioning.md)についての情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="413a4-158">Those sections provide information about the self-describing units called [assemblies](../../standard/assembly/index.md), which require no registry entries, [strong-named assemblies](../../standard/assembly/strong-named.md), which ensure name uniqueness and prevent name spoofing, and [assembly versioning](../../standard/assembly/versioning.md), which addresses many of the problems associated with DLL conflicts.</span></span> <span data-ttu-id="413a4-159">以下のセクションでは、.NET Framework アプリケーションのパッケージ化および配布について説明します。</span><span class="sxs-lookup"><span data-stu-id="413a4-159">The following sections provide information about packaging and distributing .NET Framework applications.</span></span>

### <a name="packaging"></a><span data-ttu-id="413a4-160">パッケージ化</span><span class="sxs-lookup"><span data-stu-id="413a4-160">Packaging</span></span>

<span data-ttu-id="413a4-161">.NET Framework は、アプリケーション パッケージ化のために、次のオプションを提供します。</span><span class="sxs-lookup"><span data-stu-id="413a4-161">The .NET Framework provides the following options for packaging applications:</span></span>

- <span data-ttu-id="413a4-162">単一のアセンブリまたはアセンブリのコレクションとしてパッケージ化する。</span><span class="sxs-lookup"><span data-stu-id="413a4-162">As a single assembly or as a collection of assemblies.</span></span>

     <span data-ttu-id="413a4-163">このオプションでは、.dll ファイルまたは .exe ファイルは既に作成されているため、単に使用するだけです。</span><span class="sxs-lookup"><span data-stu-id="413a4-163">With this option, you simply use the .dll or .exe files as they were built.</span></span>

- <span data-ttu-id="413a4-164">キャビネット (CAB) ファイルとしてパッケージ化する。</span><span class="sxs-lookup"><span data-stu-id="413a4-164">As cabinet (CAB) files.</span></span>

     <span data-ttu-id="413a4-165">このオプションでは、配布やダウンロードの時間を短縮するために、ファイルを .cab ファイルに圧縮します。</span><span class="sxs-lookup"><span data-stu-id="413a4-165">With this option, you compress files into .cab files to make distribution or download less time consuming.</span></span>

- <span data-ttu-id="413a4-166">Windows インストーラー パッケージとして、またはその他のインストーラー フォーマットでパッケージ化する。</span><span class="sxs-lookup"><span data-stu-id="413a4-166">As a Windows Installer package or in other installer formats.</span></span>

     <span data-ttu-id="413a4-167">このオプションでは、Windows インストーラーで使用する .msi ファイルを作成するか、または他のインストーラー用としてアプリケーションをパッケージ化します。</span><span class="sxs-lookup"><span data-stu-id="413a4-167">With this option, you create .msi files for use with the Windows Installer, or you package your application for use with some other installer.</span></span>

### <a name="distribution"></a><span data-ttu-id="413a4-168">配布</span><span class="sxs-lookup"><span data-stu-id="413a4-168">Distribution</span></span>

<span data-ttu-id="413a4-169">.NET Framework には、アプリケーション配布のために、次のオプションが用意されています。</span><span class="sxs-lookup"><span data-stu-id="413a4-169">The .NET Framework provides the following options for distributing applications:</span></span>

- <span data-ttu-id="413a4-170">XCOPY または FTP を使用する。</span><span class="sxs-lookup"><span data-stu-id="413a4-170">Use XCOPY or FTP.</span></span>

     <span data-ttu-id="413a4-171">共通言語ランタイム アプリケーションは、自己言及的で、レジストリ エントリを必要としないため、XCOPY または FTP を使用して適切なディレクトリに単純にコピーできます。</span><span class="sxs-lookup"><span data-stu-id="413a4-171">Because common language runtime applications are self-describing and require no registry entries, you can use XCOPY or FTP to simply copy the application to an appropriate directory.</span></span> <span data-ttu-id="413a4-172">その後、そのディレクトリでアプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="413a4-172">The application can then be run from that directory.</span></span>

- <span data-ttu-id="413a4-173">コードのダウンロードを使用する。</span><span class="sxs-lookup"><span data-stu-id="413a4-173">Use code download.</span></span>

     <span data-ttu-id="413a4-174">アプリケーションをインターネットや企業のイントラネットに配布する場合は、コードをコンピューターにダウンロードし、そこでアプリケーションを実行できます。</span><span class="sxs-lookup"><span data-stu-id="413a4-174">If you are distributing your application over the Internet or through a corporate intranet, you can simply download the code to a computer and run the application there.</span></span>

- <span data-ttu-id="413a4-175">Windows Installer 2.0 などのインストーラー プログラムを使用する。</span><span class="sxs-lookup"><span data-stu-id="413a4-175">Use an installer program such as Windows Installer 2.0.</span></span>

     <span data-ttu-id="413a4-176">Windows インストーラー 2.0 を使用して、グローバル アセンブリ キャッシュおよびプライベート ディレクトリへの .NET Framework アセンブリのインストール、修復、または削除を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="413a4-176">Windows Installer 2.0 can install, repair, or remove .NET Framework assemblies in the global assembly cache and in private directories.</span></span>

### <a name="installation-location"></a><span data-ttu-id="413a4-177">インストール場所</span><span class="sxs-lookup"><span data-stu-id="413a4-177">Installation Location</span></span>

<span data-ttu-id="413a4-178">ランタイムがアプリケーションのアセンブリを検索できるようなアセンブリの配置先については、「[ランタイムがアセンブリを検索する方法](how-the-runtime-locates-assemblies.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="413a4-178">To determine where to deploy your application's assemblies so they can be found by the runtime, see [How the Runtime Locates Assemblies](how-the-runtime-locates-assemblies.md).</span></span>

<span data-ttu-id="413a4-179">アプリケーションの配置方法には、セキュリティの考慮事項も関係します。</span><span class="sxs-lookup"><span data-stu-id="413a4-179">Security considerations can also affect how you deploy your application.</span></span> <span data-ttu-id="413a4-180">コードが存在する場所に基づいて、マネージド コードにセキュリティ アクセス許可が付与されます。</span><span class="sxs-lookup"><span data-stu-id="413a4-180">Security permissions are granted to managed code according to where the code is located.</span></span> <span data-ttu-id="413a4-181">インターネットなど、信頼度の低い場所にアプリケーションやコンポーネントを配置すると、そのアプリケーションやコンポーネントが実行できることは制限されます。</span><span class="sxs-lookup"><span data-stu-id="413a4-181">Deploying an application or component to a location where it receives little trust, such as the Internet, limits what the application or component can do.</span></span> <span data-ttu-id="413a4-182">配置とセキュリティ上の考慮事項については、「[コード アクセス セキュリティの基礎](../misc/code-access-security-basics.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="413a4-182">For more information about deployment and security considerations, see [Code Access Security Basics](../misc/code-access-security-basics.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="413a4-183">関連トピック</span><span class="sxs-lookup"><span data-stu-id="413a4-183">Related Topics</span></span>

|<span data-ttu-id="413a4-184">Title</span><span class="sxs-lookup"><span data-stu-id="413a4-184">Title</span></span>|<span data-ttu-id="413a4-185">説明</span><span class="sxs-lookup"><span data-stu-id="413a4-185">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="413a4-186">ランタイムがアセンブリを検索する方法</span><span class="sxs-lookup"><span data-stu-id="413a4-186">How the Runtime Locates Assemblies</span></span>](how-the-runtime-locates-assemblies.md)|<span data-ttu-id="413a4-187">共通言語ランタイムが、バインド要求を満たすために、使用するアセンブリをどのように特定するかを説明します。</span><span class="sxs-lookup"><span data-stu-id="413a4-187">Describes how the common language runtime determines which assembly to use to fulfill a binding request.</span></span>|
|[<span data-ttu-id="413a4-188">アセンブリの読み込みのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="413a4-188">Best Practices for Assembly Loading</span></span>](best-practices-for-assembly-loading.md)|<span data-ttu-id="413a4-189"><xref:System.InvalidCastException>、<xref:System.MissingMethodException>、およびその他のエラーの原因となることがある型 ID の問題を回避する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="413a4-189">Discusses ways to avoid problems of type identity that can lead to <xref:System.InvalidCastException>, <xref:System.MissingMethodException>, and other errors.</span></span>|
|[<span data-ttu-id="413a4-190">.NET Framework 4.5 のインストール中のシステム再起動の削減</span><span class="sxs-lookup"><span data-stu-id="413a4-190">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)|<span data-ttu-id="413a4-191">再起動をできる限り回避する再起動マネージャーと、.NET Framework をインストールするアプリケーションがそれをどのように利用できるかを説明しています。</span><span class="sxs-lookup"><span data-stu-id="413a4-191">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>|
|[<span data-ttu-id="413a4-192">配置ガイド (管理者向け)</span><span class="sxs-lookup"><span data-stu-id="413a4-192">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)|<span data-ttu-id="413a4-193">システム管理者が、Microsoft Endpoint Configuration Manager を使用して、ネットワーク全体に .NET Framework とその依存関係を配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="413a4-193">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>|
|[<span data-ttu-id="413a4-194">配置ガイド (開発者向け)</span><span class="sxs-lookup"><span data-stu-id="413a4-194">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)|<span data-ttu-id="413a4-195">開発者による .NET Framework とアプリケーションのユーザーのコンピューターへのインストール方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="413a4-195">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>|
|[<span data-ttu-id="413a4-196">アプリケーション、サービス、およびコンポーネントの配置</span><span class="sxs-lookup"><span data-stu-id="413a4-196">Deploying Applications, Services, and Components</span></span>](/visualstudio/deployment/deploying-applications-services-and-components)|<span data-ttu-id="413a4-197">ClickOnce を使用したアプリケーションの発行手順や、Windows インストーラー テクノロジなど、Visual Studio の配置オプションについて説明します。</span><span class="sxs-lookup"><span data-stu-id="413a4-197">Discusses deployment options in Visual Studio, including instructions for publishing an application using the ClickOnce and Windows Installer technologies.</span></span>|
|[<span data-ttu-id="413a4-198">ClickOnce アプリケーションの発行</span><span class="sxs-lookup"><span data-stu-id="413a4-198">Publishing ClickOnce Applications</span></span>](/visualstudio/deployment/publishing-clickonce-applications)|<span data-ttu-id="413a4-199">Windows フォーム アプリケーションをパッケージ化し、これを ClickOnce でネットワーク上のクライアント コンピューターに配置する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="413a4-199">Describes how to package a Windows Forms application and deploy it with ClickOnce to client computers on a network.</span></span>|
|[<span data-ttu-id="413a4-200">リソースのパッケージ化と配置</span><span class="sxs-lookup"><span data-stu-id="413a4-200">Packaging and Deploying Resources</span></span>](../resources/packaging-and-deploying-resources-in-desktop-apps.md)|<span data-ttu-id="413a4-201">.NET Framework でリソースのパッケージ化と配置に使用する、ハブ アンド スポーク モデルについて説明します。リソースの名前付け規則、フォールバック プロセス、およびパッケージ化の代替策についても説明します。</span><span class="sxs-lookup"><span data-stu-id="413a4-201">Describes the hub and spoke model that the .NET Framework uses to package and deploy resources; covers resource naming conventions, fallback process, and packaging alternatives.</span></span>|
|[<span data-ttu-id="413a4-202">相互運用アプリケーションの配置</span><span class="sxs-lookup"><span data-stu-id="413a4-202">Deploying an Interop Application</span></span>](../interop/deploying-an-interop-application.md)|<span data-ttu-id="413a4-203">相互運用アプリケーションの出荷方法とインストール方法について説明します。通常、相互運用アプリケーションには、.NET Framework クライアント アセンブリ、個別の COM タイプ ライブラリを表す 1 つ以上の相互運用機能アセンブリ、および 1 つ以上の登録済み COM コンポーネントが含まれています。</span><span class="sxs-lookup"><span data-stu-id="413a4-203">Explains how to ship and install interop applications, which typically include a .NET Framework client assembly, one or more interop assemblies representing distinct COM type libraries, and one or more registered COM components.</span></span>|
|[<span data-ttu-id="413a4-204">方法: .NET Framework 4.5 インストーラーの進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="413a4-204">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)|<span data-ttu-id="413a4-205">進行状況のビューを独自に表示する一方で、.NET Framework セットアップ プロセスをサイレントで起動および追跡する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="413a4-205">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>|

## <a name="see-also"></a><span data-ttu-id="413a4-206">関連項目</span><span class="sxs-lookup"><span data-stu-id="413a4-206">See also</span></span>

- [<span data-ttu-id="413a4-207">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="413a4-207">Development Guide</span></span>](../development-guide.md)
