---
title: 自己ホスト型 gRPC アプリケーション-WCF 開発者向け gRPC
description: ASP.NET Core gRPC アプリケーションを自己ホスト型サービスとして展開する。
ms.date: 12/15/2020
ms.openlocfilehash: a5e2316b8d76593f4eb53760d2609b5bbbc9d2c5
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938534"
---
# <a name="self-hosted-grpc-applications"></a><span data-ttu-id="b42cc-103">自己ホスト型 gRPC アプリケーション</span><span class="sxs-lookup"><span data-stu-id="b42cc-103">Self-hosted gRPC applications</span></span>

<span data-ttu-id="b42cc-104">ASP.NET Core 5.0 アプリケーションは Windows Server の IIS でホストできますが、HTTP/2 機能の一部がサポートされていないため、現在、IIS で gRPC アプリケーションをホストすることはできません。</span><span class="sxs-lookup"><span data-stu-id="b42cc-104">Although ASP.NET Core 5.0 applications can be hosted in IIS on Windows Server, currently it isn't possible to host a gRPC application in IIS because some of the HTTP/2 functionality isn't supported.</span></span> <span data-ttu-id="b42cc-105">この機能は、Windows Server の今後の更新プログラムの目的です。</span><span class="sxs-lookup"><span data-stu-id="b42cc-105">This functionality is a goal for a future update to Windows Server.</span></span>

<span data-ttu-id="b42cc-106">アプリケーションを Windows サービスとして実行できます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-106">You can run your application as a Windows service.</span></span> <span data-ttu-id="b42cc-107">または、.NET 5.0 ホスト拡張機能の新機能により、 [systemd](https://en.wikipedia.org/wiki/Systemd)によって制御される Linux サービスとして実行できます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-107">Or you can run it as a Linux service controlled by [systemd](https://en.wikipedia.org/wiki/Systemd), because of new features in the .NET 5.0 hosting extensions.</span></span>

## <a name="run-your-app-as-a-windows-service"></a><span data-ttu-id="b42cc-108">Windows サービスとしてのアプリの実行</span><span class="sxs-lookup"><span data-stu-id="b42cc-108">Run your app as a Windows service</span></span>

<span data-ttu-id="b42cc-109">Windows サービスとして実行するように ASP.NET Core アプリケーションを構成する [には、NuGet からパッケージを](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) インストールします。</span><span class="sxs-lookup"><span data-stu-id="b42cc-109">To configure your ASP.NET Core application to run as a Windows service, install the [Microsoft.Extensions.Hosting.WindowsServices](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.WindowsServices) package from NuGet.</span></span> <span data-ttu-id="b42cc-110">次に、 `UseWindowsService` のメソッドにの呼び出しを追加し `CreateHostBuilder` `Program.cs` ます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-110">Then add a call to `UseWindowsService` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseWindowsService() // Enable running as a Windows service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> <span data-ttu-id="b42cc-111">アプリケーションが Windows サービスとして実行されていない場合、 `UseWindowsService` メソッドは何も実行しません。</span><span class="sxs-lookup"><span data-stu-id="b42cc-111">If the application isn't running as a Windows service, the `UseWindowsService` method doesn't do anything.</span></span>

<span data-ttu-id="b42cc-112">ここで、次のいずれかの方法を使用してアプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-112">Now publish your application by using one of these methods:</span></span>

* <span data-ttu-id="b42cc-113">Visual Studio で、プロジェクトを右クリックし、ショートカットメニューの [ **発行** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-113">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="b42cc-114">.NET CLI から。</span><span class="sxs-lookup"><span data-stu-id="b42cc-114">From the .NET CLI.</span></span>

<span data-ttu-id="b42cc-115">.NET アプリケーションを発行するときに、 *フレームワークに依存* する展開と *自己完結* 型の展開のどちらを作成するかを選択できます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-115">When you publish a .NET application, you can choose to create a *framework-dependent* deployment or a *self-contained* deployment.</span></span> <span data-ttu-id="b42cc-116">フレームワークに依存する展開では、.NET 共有ランタイムが実行されているホストにインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="b42cc-116">Framework-dependent deployments require the .NET Shared Runtime to be installed on the host where they are run.</span></span> <span data-ttu-id="b42cc-117">自己完結型の展開は、.NET ランタイムとフレームワークの完全なコピーを使用して発行され、任意のホストで実行できます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-117">Self-contained deployments are published with a complete copy of the .NET runtime and framework and can be run on any host.</span></span> <span data-ttu-id="b42cc-118">各方法の長所と短所を含む詳細については、 [.net アプリケーションのデプロイ](../../core/deploying/index.md) に関するドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b42cc-118">For more information, including the advantages and disadvantages of each approach, see the [.NET application deployment](../../core/deploying/index.md) documentation.</span></span>

<span data-ttu-id="b42cc-119">.NET 5.0 ランタイムをホストにインストールする必要がないアプリケーションの自己完結型のビルドを発行するには、アプリケーションに含めるランタイムを指定します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-119">To publish a self-contained build of the application that does not require the .NET 5.0 runtime to be installed on the host, specify the runtime to be included with the application.</span></span> <span data-ttu-id="b42cc-120">`-r`(または) フラグを使用し `--runtime` ます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-120">Use the `-r` (or `--runtime`) flag.</span></span>

```dotnetcli
dotnet publish -c Release -r win-x64 -o ./publish
```

<span data-ttu-id="b42cc-121">フレームワークに依存するビルドを発行するには、フラグを省略し `-r` ます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-121">To publish a framework-dependent build, omit the `-r` flag.</span></span>

```dotnetcli
dotnet publish -c Release -o ./publish
```

<span data-ttu-id="b42cc-122">ディレクトリの完全な内容 `publish` をインストールフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b42cc-122">Copy the complete contents of the `publish` directory to an installation folder.</span></span> <span data-ttu-id="b42cc-123">次に、 [sc ツール](/windows/desktop/services/controlling-a-service-using-sc) を使用して、実行可能ファイルの Windows サービスを作成します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-123">Then, use the [sc tool](/windows/desktop/services/controlling-a-service-using-sc) to create a Windows service for the executable file.</span></span>

```console
sc create MyService binPath=C:\MyService\MyService.exe
```

### <a name="log-to-the-windows-event-log"></a><span data-ttu-id="b42cc-124">Windows イベントログにログを記録する</span><span class="sxs-lookup"><span data-stu-id="b42cc-124">Log to the Windows event log</span></span>

<span data-ttu-id="b42cc-125">メソッドは、 `UseWindowsService` ログメッセージを Windows イベントログに書き込むログ [記録](/aspnet/core/fundamentals/logging/) プロバイダーを自動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-125">The `UseWindowsService` method automatically adds a [logging](/aspnet/core/fundamentals/logging/) provider that writes log messages to the Windows event log.</span></span> <span data-ttu-id="b42cc-126">このプロバイダーのログ記録を構成するに `EventLog` `Logging` は、のセクション `appsettings.json` または別の構成ソースにエントリを追加します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-126">You can configure logging for this provider by adding an `EventLog` entry to the `Logging` section of `appsettings.json` or another configuration source.</span></span>

<span data-ttu-id="b42cc-127">イベントログで使用されるソース名を上書きするには、 `SourceName` これらの設定でプロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-127">You can override the source name used in the event log by setting a `SourceName` property in these settings.</span></span> <span data-ttu-id="b42cc-128">名前を指定しない場合は、既定のアプリケーション名 (通常は実行可能アセンブリ名) が使用されます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-128">If you don't specify a name, the default application name (normally the executable assembly name) will be used.</span></span>

<span data-ttu-id="b42cc-129">ログ記録の詳細については、この章の最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b42cc-129">More information on logging is at the end of this chapter.</span></span>

## <a name="run-your-app-as-a-linux-service-with-systemd"></a><span data-ttu-id="b42cc-130">Systemd を使用してアプリを Linux サービスとして実行する</span><span class="sxs-lookup"><span data-stu-id="b42cc-130">Run your app as a Linux service with systemd</span></span>

<span data-ttu-id="b42cc-131">Linux サービス (Linux 用語の *デーモン* ) として実行するように ASP.NET Core アプリケーションを構成するには、NuGet から [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) パッケージをインストールします。</span><span class="sxs-lookup"><span data-stu-id="b42cc-131">To configure your ASP.NET Core application to run as a Linux service (or *daemon* in Linux parlance), install the [Microsoft.Extensions.Hosting.Systemd](https://www.nuget.org/packages/Microsoft.Extensions.Hosting.Systemd) package from NuGet.</span></span> <span data-ttu-id="b42cc-132">次に、 `UseSystemd` のメソッドにの呼び出しを追加し `CreateHostBuilder` `Program.cs` ます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-132">Then add a call to `UseSystemd` to the `CreateHostBuilder` method in `Program.cs`.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .UseSystemd() // Enable running as a Systemd service
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
        });
```

> [!NOTE]
> <span data-ttu-id="b42cc-133">アプリケーションが Linux サービスとして実行されていない場合、 `UseSystemd` メソッドは何も実行しません。</span><span class="sxs-lookup"><span data-stu-id="b42cc-133">If the application isn't running as a Linux service, the `UseSystemd` method doesn't do anything.</span></span>

<span data-ttu-id="b42cc-134">次に、アプリケーションを発行します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-134">Now publish your application.</span></span> <span data-ttu-id="b42cc-135">アプリケーションは、フレームワークに依存するか、関連する Linux ランタイムに自己完結します (たとえば、 `linux-x64` )。</span><span class="sxs-lookup"><span data-stu-id="b42cc-135">The application can be either framework dependent or self-contained for the relevant Linux runtime (for example, `linux-x64`).</span></span> <span data-ttu-id="b42cc-136">次のいずれかの方法を使用して発行できます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-136">You can publish by using one of these methods:</span></span>

* <span data-ttu-id="b42cc-137">Visual Studio で、プロジェクトを右クリックし、ショートカットメニューの [ **発行** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-137">From Visual Studio by right-clicking the project and selecting **Publish** on the shortcut menu.</span></span>
* <span data-ttu-id="b42cc-138">.NET CLI から、次のコマンドを使用します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-138">From the .NET CLI, by using the following command:</span></span>

  ```dotnetcli
  dotnet publish -c Release -r linux-x64 -o ./publish
  ```
  
<span data-ttu-id="b42cc-139">ディレクトリの完全な内容 `publish` を、Linux ホストのインストールフォルダーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="b42cc-139">Copy the complete contents of the `publish` directory to an installation folder on the Linux host.</span></span> <span data-ttu-id="b42cc-140">サービスを登録するには、 *ユニットファイル* と呼ばれる特殊なファイルをディレクトリに追加する必要があり `/etc/systemd/system` ます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-140">Registering the service requires a special file, called a *unit file*, to be added to the `/etc/systemd/system` directory.</span></span> <span data-ttu-id="b42cc-141">このフォルダーにファイルを作成するには、ルートアクセス許可が必要です。</span><span class="sxs-lookup"><span data-stu-id="b42cc-141">You'll need root permission to create a file in this folder.</span></span> <span data-ttu-id="b42cc-142">使用する識別子と拡張子をファイルに付け `systemd` `.service` ます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-142">Name the file with the identifier that you want `systemd` to use and the `.service` extension.</span></span> <span data-ttu-id="b42cc-143">たとえば、 `/etc/systemd/system/myapp.service`を使用します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-143">For example, use `/etc/systemd/system/myapp.service`.</span></span>

<span data-ttu-id="b42cc-144">次の例に示すように、サービスファイルは INI 形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-144">The service file uses INI format, as shown in this example:</span></span>

```ini
[Unit]
Description=My gRPC Application

[Service]
Type=notify
ExecStart=/usr/sbin/myapp

[Install]
WantedBy=multi-user.target
```

<span data-ttu-id="b42cc-145">`Type=notify`プロパティは、 `systemd` アプリケーションが起動時およびシャットダウン時に通知することを示します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-145">The `Type=notify` property tells `systemd` that the application will notify it on startup and shutdown.</span></span> <span data-ttu-id="b42cc-146">この設定により、 `WantedBy=multi-user.target` Linux システムが "ランダウン 2" に達したときにサービスが開始されます。これは、グラフィカルでないマルチユーザーシェルがアクティブであることを意味します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-146">The `WantedBy=multi-user.target` setting will cause the service to start when the Linux system reaches "runlevel 2," which means a non-graphical, multi-user shell is active.</span></span>

<span data-ttu-id="b42cc-147">はサービスを認識する前に、 `systemd` 構成を再読み込みする必要があります。</span><span class="sxs-lookup"><span data-stu-id="b42cc-147">Before `systemd` will recognize the service, it needs to reload its configuration.</span></span> <span data-ttu-id="b42cc-148">を制御する `systemd` には、コマンドを使用し `systemctl` ます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-148">You control `systemd` by using the `systemctl` command.</span></span> <span data-ttu-id="b42cc-149">再読み込みが完了したら、サブコマンドを使用して、 `status` アプリケーションが正常に登録されたことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-149">After reloading, use the `status` subcommand to confirm that the application has registered successfully.</span></span>

```console
sudo systemctl daemon-reload
sudo systemctl status myapp
```

<span data-ttu-id="b42cc-150">サービスが正しく構成されている場合は、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-150">If you've configured the service correctly, you'll get the following output:</span></span>

```text
myapp.service - My gRPC Application
 Loaded: loaded (/etc/systemd/system/myapp.service; disabled; vendor preset: enabled)
 Active: inactive (dead)
```

<span data-ttu-id="b42cc-151">`start`コマンドを使用してサービスを開始します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-151">Use the `start` command to start the service.</span></span>

```console
sudo systemctl start myapp.service
```

> [!TIP]
> <span data-ttu-id="b42cc-152">`.service`拡張機能は、を使用している場合は省略可能です `systemctl start` 。</span><span class="sxs-lookup"><span data-stu-id="b42cc-152">The `.service` extension is optional when you're using `systemctl start`.</span></span>

<span data-ttu-id="b42cc-153">システムの起動時にサービスを自動的に開始するように指定するには、 `systemd` コマンドを使用し `enable` ます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-153">To tell `systemd` to start the service automatically on system startup, use the `enable` command.</span></span>

```console
sudo systemctl enable myapp
```

### <a name="log-to-journald"></a><span data-ttu-id="b42cc-154">Journald にログを記録する</span><span class="sxs-lookup"><span data-stu-id="b42cc-154">Log to journald</span></span>

<span data-ttu-id="b42cc-155">Linux と同等の Windows イベントログは `journald` 、の一部である構造化されたログ記録システムサービスです `systemd` 。</span><span class="sxs-lookup"><span data-stu-id="b42cc-155">The Linux equivalent of the Windows event log is `journald`, a structured logging system service that's part of `systemd`.</span></span> <span data-ttu-id="b42cc-156">Linux デーモンによって標準出力に書き込まれたログメッセージは、自動的にに書き込まれ `journald` ます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-156">Log messages written to the standard output by a Linux daemon are automatically written to `journald`.</span></span> <span data-ttu-id="b42cc-157">ログ記録レベルを構成するには、 `Console` ログ構成のセクションを使用します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-157">To configure logging levels, use the `Console` section of the logging configuration.</span></span> <span data-ttu-id="b42cc-158">`UseSystemd`Host builder メソッドは、journal に合わせてコンソールの出力形式を自動的に構成します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-158">The `UseSystemd` host builder method automatically configures the console output format to suit the journal.</span></span>

<span data-ttu-id="b42cc-159">`journald`は Linux ログの標準であるため、さまざまなツールが統合されています。</span><span class="sxs-lookup"><span data-stu-id="b42cc-159">Because `journald` is the standard for Linux logs, a variety of tools integrate with it.</span></span> <span data-ttu-id="b42cc-160">から外部ログシステムにログを簡単にルーティングでき `journald` ます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-160">You can easily route logs from `journald` to an external logging system.</span></span> <span data-ttu-id="b42cc-161">ホストでローカルに作業している場合は、コマンドを使用して `journalctl` コマンドラインからのログを表示できます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-161">Working locally on the host, you can use the `journalctl` command to view logs from the command line.</span></span>

```console
sudo journalctl -u myapp
```

> [!TIP]
> <span data-ttu-id="b42cc-162">ホストで使用できる GUI 環境がある場合は、 *QJournalctl* や *gnome ログ* など、Linux で使用できるグラフィカルなログビューアーがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="b42cc-162">If you have a GUI environment available on your host, a few graphical log viewers are available for Linux, such as *QJournalctl* and *gnome-logs*.</span></span>

<span data-ttu-id="b42cc-163">を使用してコマンドラインからジャーナルにクエリを実行する方法の詳細については `systemd` `journalctl` 、 [manpages](https://manpages.debian.org/buster/systemd/journalctl.1)を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b42cc-163">To learn more about querying the `systemd` journal from the command line by using `journalctl`, see [the manpages](https://manpages.debian.org/buster/systemd/journalctl.1).</span></span>

## <a name="https-certificates-for-self-hosted-applications"></a><span data-ttu-id="b42cc-164">自己ホスト型アプリケーションの HTTPS 証明書</span><span class="sxs-lookup"><span data-stu-id="b42cc-164">HTTPS certificates for self-hosted applications</span></span>

<span data-ttu-id="b42cc-165">運用環境で gRPC アプリケーションを実行している場合は、信頼された証明機関 (CA) からの TLS 証明書を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b42cc-165">When you're running a gRPC application in production, you should use a TLS certificate from a trusted certificate authority (CA).</span></span> <span data-ttu-id="b42cc-166">この CA は、パブリック CA である場合もあれば、組織の内部の ca である場合もあります。</span><span class="sxs-lookup"><span data-stu-id="b42cc-166">This CA might be a public CA, or an internal one for your organization.</span></span>

<span data-ttu-id="b42cc-167">Windows ホストでは、クラスを使用して、セキュリティで保護された [証明書ストア](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) から証明書を読み込むことができ <xref:System.Security.Cryptography.X509Certificates.X509Store> ます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-167">On Windows hosts, you can load the certificate from a secure [certificate store](/windows/win32/seccrypto/managing-certificates-with-certificate-stores) by using the <xref:System.Security.Cryptography.X509Certificates.X509Store> class.</span></span> <span data-ttu-id="b42cc-168">また、 `X509Store` 一部の Linux ホストでは、OpenSSL キーストアでクラスを使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-168">You can also use the `X509Store` class with the OpenSSL key store on some Linux hosts.</span></span>

<span data-ttu-id="b42cc-169">また、いずれかの [X509Certificate2 コンストラクター](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A)を使用して証明書を作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-169">You can also create certificates by using one of the [X509Certificate2 constructors](xref:System.Security.Cryptography.X509Certificates.X509Certificate2.%23ctor%2A), from either:</span></span>

* <span data-ttu-id="b42cc-170">ファイル ( `.pfx` 強力なパスワードで保護されたファイルなど)</span><span class="sxs-lookup"><span data-stu-id="b42cc-170">A file, such as a `.pfx` file protected by a strong password</span></span>
* <span data-ttu-id="b42cc-171">[Azure Key Vault](https://azure.microsoft.com/services/key-vault/)などのセキュリティで保護されたストレージサービスから取得したバイナリデータ</span><span class="sxs-lookup"><span data-stu-id="b42cc-171">Binary data retrieved from a secure storage service such as [Azure Key Vault](https://azure.microsoft.com/services/key-vault/)</span></span>

<span data-ttu-id="b42cc-172">証明書を使用するように Kestrel を構成するには、構成とコードの2つの方法があります。</span><span class="sxs-lookup"><span data-stu-id="b42cc-172">You can configure Kestrel to use a certificate in two ways: from configuration or in code.</span></span>

### <a name="set-https-certificates-by-using-configuration"></a><span data-ttu-id="b42cc-173">構成を使用して HTTPS 証明書を設定する</span><span class="sxs-lookup"><span data-stu-id="b42cc-173">Set HTTPS certificates by using configuration</span></span>

<span data-ttu-id="b42cc-174">構成方法では、 `.pfx` Kestrel 構成セクションで証明書ファイルへのパスとパスワードを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b42cc-174">The configuration approach requires setting the path to the certificate `.pfx` file and the password in the Kestrel configuration section.</span></span> <span data-ttu-id="b42cc-175">で `appsettings.json` は、これは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="b42cc-175">In `appsettings.json`, that would look like this:</span></span>

```json
{
  "Kestrel": {
    "Certificates": {
      "Default": {
        "Path": "cert.pfx",
        "Password": "DO NOT STORE PLAINTEXT PASSWORDS IN APPSETTINGS FILES"
      }
    }
  }
}
```

<span data-ttu-id="b42cc-176">Azure Key Vault または Hashicorp Vault などのセキュリティで保護された構成ソースを使用して、パスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="b42cc-176">Provide the password by using a secure configuration source such as Azure Key Vault or Hashicorp Vault.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b42cc-177">暗号化されていないパスワードを構成ファイルに保存しないでください。</span><span class="sxs-lookup"><span data-stu-id="b42cc-177">Don't store unencrypted passwords in configuration files.</span></span>

### <a name="set-https-certificates-in-code"></a><span data-ttu-id="b42cc-178">コードでの HTTPS 証明書の設定</span><span class="sxs-lookup"><span data-stu-id="b42cc-178">Set HTTPS certificates in code</span></span>

<span data-ttu-id="b42cc-179">コードで Kestrel の HTTPS を構成するには、クラスのでメソッドを使用し `ConfigureKestrel` `IWebHostBuilder` `Program` ます。</span><span class="sxs-lookup"><span data-stu-id="b42cc-179">To configure HTTPS on Kestrel in code, use the `ConfigureKestrel` method on `IWebHostBuilder` in the `Program` class.</span></span>

```csharp
public static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureWebHostDefaults(webBuilder =>
        {
            webBuilder.UseStartup<Startup>();
            webBuilder.ConfigureKestrel(kestrel =>
            {
                kestrel.ConfigureHttpsDefaults(https =>
                {
                    https.ServerCertificate = new X509Certificate2("mycert.pfx", "password");
                });
            });
        });
```

<span data-ttu-id="b42cc-180">ここでも、ファイルのパスワードをに保存 `.pfx` し、セキュリティで保護された構成ソースから取得するようにしてください。</span><span class="sxs-lookup"><span data-stu-id="b42cc-180">Again, be sure to store the password for the `.pfx` file in, and retrieve it from, a secure configuration source.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="b42cc-181">[前へ](grpc-in-production.md)
>[次へ](docker.md)</span><span class="sxs-lookup"><span data-stu-id="b42cc-181">[Previous](grpc-in-production.md)
[Next](docker.md)</span></span>
