---
ms.openlocfilehash: eb3fa768a491f6c0ff4b15479beabd71b0670338
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032511"
---
### <a name="hosting-https-redirection-enabled-for-iis-out-of-process-apps"></a><span data-ttu-id="e68ca-101">ホスティング:IIS アウトプロセス アプリ用に HTTPS リダイレクトを有効化</span><span class="sxs-lookup"><span data-stu-id="e68ca-101">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>

<span data-ttu-id="e68ca-102">IIS アウトプロセスでホストするための [ASP.NET Core モジュール (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) のバージョン 13.0.19218.0 により、ASP.NET Core 3.0 および 2.2 アプリに既存の HTTPS リダイレクト機能が有効になります。</span><span class="sxs-lookup"><span data-stu-id="e68ca-102">Version 13.0.19218.0 of the [ASP.NET Core Module (ANCM)](/aspnet/core/host-and-deploy/aspnet-core-module) for hosting via IIS out-of-process enables an existing HTTPS redirection feature for ASP.NET Core 3.0 and 2.2 apps.</span></span>

<span data-ttu-id="e68ca-103">ディスカッションについては、[dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e68ca-103">For discussion, see [dotnet/AspNetCore#15243](https://github.com/dotnet/AspNetCore/issues/15243).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="e68ca-104">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="e68ca-104">Version introduced</span></span>

<span data-ttu-id="e68ca-105">3.0</span><span class="sxs-lookup"><span data-stu-id="e68ca-105">3.0</span></span>

#### <a name="old-behavior"></a><span data-ttu-id="e68ca-106">以前の動作</span><span class="sxs-lookup"><span data-stu-id="e68ca-106">Old behavior</span></span>

<span data-ttu-id="e68ca-107">ASP.NET Core 2.1 プロジェクト テンプレートで、<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> や <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A> などの HTTPS ミドルウェア メソッドのサポートが初めて導入されました。</span><span class="sxs-lookup"><span data-stu-id="e68ca-107">The ASP.NET Core 2.1 project template first introduced support for HTTPS middleware methods like <xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection%2A> and <xref:Microsoft.AspNetCore.Builder.HstsBuilderExtensions.UseHsts%2A>.</span></span> <span data-ttu-id="e68ca-108">開発中のアプリでは既定のポート 443 が使用されないため、HTTPS リダイレクトを有効にするには構成を追加する必要がありました。</span><span class="sxs-lookup"><span data-stu-id="e68ca-108">Enabling HTTPS redirection required the addition of configuration, since apps in development don't use the default port of 443.</span></span> <span data-ttu-id="e68ca-109">[HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) は、要求で既に HTTPS が使用されている場合にのみアクティブになります。</span><span class="sxs-lookup"><span data-stu-id="e68ca-109">[HTTP Strict Transport Security (HSTS)](https://cheatsheetseries.owasp.org/cheatsheets/HTTP_Strict_Transport_Security_Cheat_Sheet.html) is active only if the request is already using HTTPS.</span></span> <span data-ttu-id="e68ca-110">localhost は既定ではスキップされます。</span><span class="sxs-lookup"><span data-stu-id="e68ca-110">Localhost is skipped by default.</span></span>

#### <a name="new-behavior"></a><span data-ttu-id="e68ca-111">新しい動作</span><span class="sxs-lookup"><span data-stu-id="e68ca-111">New behavior</span></span>

<span data-ttu-id="e68ca-112">ASP.NET Core 3.0 では、IIS HTTPS シナリオが[強化](https://github.com/dotnet/AspNetCore/pull/4685)されました。</span><span class="sxs-lookup"><span data-stu-id="e68ca-112">In ASP.NET Core 3.0, the IIS HTTPS scenario was [enhanced](https://github.com/dotnet/AspNetCore/pull/4685).</span></span> <span data-ttu-id="e68ca-113">この強化により、アプリがサーバーの HTTPS ポートを検出し、既定で `UseHttpsRedirection` を動作させることができました。</span><span class="sxs-lookup"><span data-stu-id="e68ca-113">With the enhancement, an app could discover the server's HTTPS ports and make `UseHttpsRedirection` work by default.</span></span> <span data-ttu-id="e68ca-114">インプロセス コンポーネントでは、`IServerAddresses` 機能を使用してポート検出が行われていました。この機能は、インプロセス ライブラリがフレームワークでバージョン管理されているため、ASP.NET Core 3.0 アプリにのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="e68ca-114">The in-process component accomplished port discovery with the `IServerAddresses` feature, which only affects ASP.NET Core 3.0 apps because the in-process library is versioned with the framework.</span></span> <span data-ttu-id="e68ca-115">アウトプロセス コンポーネントが、`ASPNETCORE_HTTPS_PORT` 環境変数を自動的に追加するように変更されました。</span><span class="sxs-lookup"><span data-stu-id="e68ca-115">The out-of-process component changed to automatically add the `ASPNETCORE_HTTPS_PORT` environment variable.</span></span> <span data-ttu-id="e68ca-116">アプトプロセス コンポーネントはグローバルに共有されるため、この変更によって ASP.NET Core 2.2 と 3.0 の両方のアプリが影響を受けました。</span><span class="sxs-lookup"><span data-stu-id="e68ca-116">This change affected both ASP.NET Core 2.2 and 3.0 apps because the out-of-process component is shared globally.</span></span> <span data-ttu-id="e68ca-117">ASP.NET Core 2.1 アプリは、既定で以前のバージョンの ANCM を使用しているため、響を受けません。</span><span class="sxs-lookup"><span data-stu-id="e68ca-117">ASP.NET Core 2.1 apps aren't affected because they use a prior version of ANCM by default.</span></span>

<span data-ttu-id="e68ca-118">上記の動作は、ASP.NET Core 2.x での動作の変更を元に戻すために ASP.NET Core 3.0.1 および 3.1.0 Preview 3 で変更されました。</span><span class="sxs-lookup"><span data-stu-id="e68ca-118">The preceding behavior was modified in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 to reverse the behavior changes in ASP.NET Core 2.x.</span></span> <span data-ttu-id="e68ca-119">これらの変更は、IIS アウトプロセス アプリにのみ影響します。</span><span class="sxs-lookup"><span data-stu-id="e68ca-119">These changes only affect IIS out-of-process apps.</span></span>

<span data-ttu-id="e68ca-120">前に説明したように、ASP.NET Core 3.0.0 をインストールすると、ASP.NET Core 2.x アプリで `UseHttpsRedirection` ミドルウェアもアクティブになるという副作用がありました。</span><span class="sxs-lookup"><span data-stu-id="e68ca-120">As detailed above, installing ASP.NET Core 3.0.0 had the side effect of also activating the `UseHttpsRedirection` middleware in ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="e68ca-121">ASP.NET Core 3.0.1 と 3.1.0 Preview 3 では、インストールによって ASP.NET Core 2.x アプリに影響を及ぼさないよう、ANCM に変更が加えられました。</span><span class="sxs-lookup"><span data-stu-id="e68ca-121">A change was made to ANCM in ASP.NET Core 3.0.1 and 3.1.0 Preview 3 such that installing them no longer has this effect on ASP.NET Core 2.x apps.</span></span> <span data-ttu-id="e68ca-122">ANCM が ASP.NET Core 3.0.0 で設定した `ASPNETCORE_HTTPS_PORT` 環境変数は、ASP.NET Core 3.0.1 および 3.1.0 Preview 3 で `ASPNETCORE_ANCM_HTTPS_PORT` に変更されました。</span><span class="sxs-lookup"><span data-stu-id="e68ca-122">The `ASPNETCORE_HTTPS_PORT` environment variable that ANCM populated in ASP.NET Core 3.0.0 was changed to `ASPNETCORE_ANCM_HTTPS_PORT` in ASP.NET Core 3.0.1 and 3.1.0 Preview 3.</span></span> <span data-ttu-id="e68ca-123">これらのリリースでは、新しい変数と古い変数の両方を理解するように `UseHttpsRedirection` も更新されました。</span><span class="sxs-lookup"><span data-stu-id="e68ca-123">`UseHttpsRedirection` was also updated in these releases to understand both the new and old variables.</span></span> <span data-ttu-id="e68ca-124">ASP.NET Core 2.x は更新されません。</span><span class="sxs-lookup"><span data-stu-id="e68ca-124">ASP.NET Core 2.x won't be updated.</span></span> <span data-ttu-id="e68ca-125">その結果、既定で無効になっている前の動作に戻ります。</span><span class="sxs-lookup"><span data-stu-id="e68ca-125">As a result, it reverts to the previous behavior of being disabled by default.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="e68ca-126">変更理由</span><span class="sxs-lookup"><span data-stu-id="e68ca-126">Reason for change</span></span>

<span data-ttu-id="e68ca-127">ASP.NET Core 3.0 の機能を向上するため。</span><span class="sxs-lookup"><span data-stu-id="e68ca-127">Improved ASP.NET Core 3.0 functionality.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="e68ca-128">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="e68ca-128">Recommended action</span></span>

<span data-ttu-id="e68ca-129">すべてのクライアントで HTTPS を使用する場合は、アクションは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="e68ca-129">No action is required if you want all clients to use HTTPS.</span></span> <span data-ttu-id="e68ca-130">一部のクライアントに HTTP の使用を許可するには、次のいずれかの手順を行います。</span><span class="sxs-lookup"><span data-stu-id="e68ca-130">To allow some clients to use HTTP, take one of the following steps:</span></span>

* <span data-ttu-id="e68ca-131">プロジェクトの `Startup.Configure` メソッドから `UseHttpsRedirection` と `UseHsts` への呼び出しを削除し、アプリを再デプロイします。</span><span class="sxs-lookup"><span data-stu-id="e68ca-131">Remove the calls to `UseHttpsRedirection` and `UseHsts` from your project's `Startup.Configure` method, and redeploy the app.</span></span>
* <span data-ttu-id="e68ca-132">*web.config* ファイルで、`ASPNETCORE_HTTPS_PORT` 環境変数を空の文字列に設定します。</span><span class="sxs-lookup"><span data-stu-id="e68ca-132">In your *web.config* file, set the `ASPNETCORE_HTTPS_PORT` environment variable to an empty string.</span></span> <span data-ttu-id="e68ca-133">この変更は、アプリを再デプロイしなくても、サーバー上で直接行うことができます。</span><span class="sxs-lookup"><span data-stu-id="e68ca-133">This change can occur directly on the server without redeploying the app.</span></span> <span data-ttu-id="e68ca-134">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="e68ca-134">For example:</span></span>

    ```xml
    <aspNetCore processPath="dotnet" arguments=".\WebApplication3.dll" stdoutLogEnabled="false" stdoutLogFile="\\?\%home%\LogFiles\stdout" >
        <environmentVariables>
        <environmentVariable name="ASPNETCORE_HTTPS_PORT" value="" />
        </environmentVariables>
    </aspNetCore>
    ```

<span data-ttu-id="e68ca-135">`UseHttpsRedirection` は引き続き次のことができます。</span><span class="sxs-lookup"><span data-stu-id="e68ca-135">`UseHttpsRedirection` can still be:</span></span>

* <span data-ttu-id="e68ca-136">`ASPNETCORE_HTTPS_PORT` 環境変数を適切なポート番号 (ほとんどの運用シナリオでは 443) に設定することによって ASP.NET Core 2.x で手動でアクティブ化する。</span><span class="sxs-lookup"><span data-stu-id="e68ca-136">Activated manually in ASP.NET Core 2.x by setting the `ASPNETCORE_HTTPS_PORT` environment variable to the appropriate port number (443 in most production scenarios).</span></span>
* <span data-ttu-id="e68ca-137">空の文字列値を使用して `ASPNETCORE_ANCM_HTTPS_PORT` を定義することで、ASP.NET Core 3.x で非アクティブ化する。</span><span class="sxs-lookup"><span data-stu-id="e68ca-137">Deactivated in ASP.NET Core 3.x by defining `ASPNETCORE_ANCM_HTTPS_PORT` with an empty string value.</span></span> <span data-ttu-id="e68ca-138">この値は、前の `ASPNETCORE_HTTPS_PORT` の例と同じ方法で設定されます。</span><span class="sxs-lookup"><span data-stu-id="e68ca-138">This value is set in the same fashion as the preceding `ASPNETCORE_HTTPS_PORT` example.</span></span>

<span data-ttu-id="e68ca-139">ASP.NET Core 3.0.0 アプリを実行しているマシンでは、ASP.NET Core 3.1.0 Preview 3 ANCM をインストールする前に、ASP.NET Core 3.0.1 ランタイムをインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="e68ca-139">Machines running ASP.NET Core 3.0.0 apps should install the ASP.NET Core 3.0.1 runtime before installing the ASP.NET Core 3.1.0 Preview 3 ANCM.</span></span> <span data-ttu-id="e68ca-140">これにより、ASP.NET Core 3.0 アプリで引き続き `UseHttpsRedirection` を期待どおりに動作させることができます。</span><span class="sxs-lookup"><span data-stu-id="e68ca-140">Doing so ensures that `UseHttpsRedirection` continues to operate as expected for the ASP.NET Core 3.0 apps.</span></span>

<span data-ttu-id="e68ca-141">Azure App Service では、ANCM はそのグローバルな性質のため、ランタイムとは別のスケジュールでデプロイされます。</span><span class="sxs-lookup"><span data-stu-id="e68ca-141">In Azure App Service, ANCM deploys on a separate schedule from the runtime because of its global nature.</span></span> <span data-ttu-id="e68ca-142">ANCM は、ASP.NET Core3.0.1 と 3.1.0 がデプロイされた後に、これらの変更とともに Azure にデプロイされました。</span><span class="sxs-lookup"><span data-stu-id="e68ca-142">ANCM was deployed to Azure with these changes after ASP.NET Core 3.0.1 and 3.1.0 were deployed.</span></span>

#### <a name="category"></a><span data-ttu-id="e68ca-143">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="e68ca-143">Category</span></span>

<span data-ttu-id="e68ca-144">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e68ca-144">ASP.NET Core</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="e68ca-145">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="e68ca-145">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)?displayProperty=nameWithType>

<!-- 

#### Affected APIs

`M:Microsoft.AspNetCore.Builder.HttpsPolicyBuilderExtensions.UseHttpsRedirection(Microsoft.AspNetCore.Builder.IApplicationBuilder)`

-->
