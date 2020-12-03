---
title: ASP.NET Core の破壊的変更
titleSuffix: ''
description: ASP.NET Core 3.0 および 3.1 における破壊的変更を挙げます。
ms.date: 11/03/2020
author: scottaddie
ms.author: scaddie
ms.openlocfilehash: 40dfda77dd51ed46366ec6cd8f6598070e8ce846
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "96032442"
---
# <a name="aspnet-core-breaking-changes-for-versions-30-and-31"></a><span data-ttu-id="381e7-103">ASP.NET Core バージョン 3.0 および 3.1 における破壊的変更</span><span class="sxs-lookup"><span data-stu-id="381e7-103">ASP.NET Core breaking changes for versions 3.0 and 3.1</span></span>

<span data-ttu-id="381e7-104">ASP.NET Core からは、.NET Core で使用される Web アプリ開発機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="381e7-104">ASP.NET Core provides the web app development features used by .NET Core.</span></span>

<span data-ttu-id="381e7-105">特定のバージョンの破壊的変更については、次のリンクのいずれかを選択します。</span><span class="sxs-lookup"><span data-stu-id="381e7-105">Select one of the following links for breaking changes in a specific version:</span></span>

* [<span data-ttu-id="381e7-106">ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="381e7-106">ASP.NET Core 3.1</span></span>](#aspnet-core-31)
* [<span data-ttu-id="381e7-107">ASP.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="381e7-107">ASP.NET Core 3.0</span></span>](#aspnet-core-30)

<span data-ttu-id="381e7-108">このページでは、ASP.NET Core 3.0 および 3.1 の次の破壊的変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="381e7-108">The following breaking changes in ASP.NET Core 3.0 and 3.1 are documented on this page:</span></span>

- [<span data-ttu-id="381e7-109">Antiforgery、CORS、Diagnostics、MVC、Routing の古い API の削除</span><span class="sxs-lookup"><span data-stu-id="381e7-109">Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed</span></span>](#obsolete-antiforgery-cors-diagnostics-mvc-and-routing-apis-removed)
- [<span data-ttu-id="381e7-110">認証:Google+ の非推奨</span><span class="sxs-lookup"><span data-stu-id="381e7-110">Authentication: Google+ deprecation</span></span>](#authentication-google-deprecated-and-replaced)
- [<span data-ttu-id="381e7-111">認証:HttpContext.Authentication プロパティの削除</span><span class="sxs-lookup"><span data-stu-id="381e7-111">Authentication: HttpContext.Authentication property removed</span></span>](#authentication-httpcontextauthentication-property-removed)
- [<span data-ttu-id="381e7-112">認証:Newtonsoft.Json 型の置き換え</span><span class="sxs-lookup"><span data-stu-id="381e7-112">Authentication: Newtonsoft.Json types replaced</span></span>](#authentication-newtonsoftjson-types-replaced)
- [<span data-ttu-id="381e7-113">認証:OAuthHandler ExchangeCodeAsync 署名の変更</span><span class="sxs-lookup"><span data-stu-id="381e7-113">Authentication: OAuthHandler ExchangeCodeAsync signature changed</span></span>](#authentication-oauthhandler-exchangecodeasync-signature-changed)
- [<span data-ttu-id="381e7-114">承認:AddAuthorization のオーバーロードを別のアセンブリに移動</span><span class="sxs-lookup"><span data-stu-id="381e7-114">Authorization: AddAuthorization overload moved to different assembly</span></span>](#authorization-addauthorization-overload-moved-to-different-assembly)
- [<span data-ttu-id="381e7-115">承認:AuthorizationFilterContext.Filters から IAllowAnonymous を削除</span><span class="sxs-lookup"><span data-stu-id="381e7-115">Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters</span></span>](#authorization-iallowanonymous-removed-from-authorizationfiltercontextfilters)
- [<span data-ttu-id="381e7-116">承認:IAuthorizationPolicyProvider の実装に新しいメソッドが必要</span><span class="sxs-lookup"><span data-stu-id="381e7-116">Authorization: IAuthorizationPolicyProvider implementations require new method</span></span>](#authorization-iauthorizationpolicyprovider-implementations-require-new-method)
- [<span data-ttu-id="381e7-117">キャッシュ:CompactOnMemoryPressure プロパティの削除</span><span class="sxs-lookup"><span data-stu-id="381e7-117">Caching: CompactOnMemoryPressure property removed</span></span>](#caching-compactonmemorypressure-property-removed)
- [<span data-ttu-id="381e7-118">キャッシュ:Microsoft.Extensions.Caching.SqlServer で新しい SqlClient パッケージを使用</span><span class="sxs-lookup"><span data-stu-id="381e7-118">Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package</span></span>](#caching-microsoftextensionscachingsqlserver-uses-new-sqlclient-package)
- [<span data-ttu-id="381e7-119">データ保護:DataProtection.Blobs では新しい Azure Storage API が使用されます</span><span class="sxs-lookup"><span data-stu-id="381e7-119">Data Protection: DataProtection.Blobs uses new Azure Storage APIs</span></span>](#data-protection-dataprotectionblobs-uses-new-azure-storage-apis)
- [<span data-ttu-id="381e7-120">ホスティング:Windows ホスティング バンドルから AspNetCoreModule V1 を削除</span><span class="sxs-lookup"><span data-stu-id="381e7-120">Hosting: AspNetCoreModule V1 removed from Windows Hosting Bundle</span></span>](#hosting-aspnetcoremodule-v1-removed-from-windows-hosting-bundle)
- [<span data-ttu-id="381e7-121">ホスティング:汎用ホストによる Startup コンストラクター挿入の制限</span><span class="sxs-lookup"><span data-stu-id="381e7-121">Hosting: Generic host restricts Startup constructor injection</span></span>](#hosting-generic-host-restricts-startup-constructor-injection)
- [<span data-ttu-id="381e7-122">ホスティング:IIS アウトプロセス アプリ用に HTTPS リダイレクトを有効化</span><span class="sxs-lookup"><span data-stu-id="381e7-122">Hosting: HTTPS redirection enabled for IIS out-of-process apps</span></span>](#hosting-https-redirection-enabled-for-iis-out-of-process-apps)
- [<span data-ttu-id="381e7-123">ホスティング:IHostingEnvironment と IApplicationLifetime の型を置き換え</span><span class="sxs-lookup"><span data-stu-id="381e7-123">Hosting: IHostingEnvironment and IApplicationLifetime types replaced</span></span>](#hosting-ihostingenvironment-and-iapplicationlifetime-types-marked-obsolete-and-replaced)
- [<span data-ttu-id="381e7-124">ホスティング:WebHostBuilder 依存関係から ObjectPoolProvider を削除</span><span class="sxs-lookup"><span data-stu-id="381e7-124">Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies</span></span>](#hosting-objectpoolprovider-removed-from-webhostbuilder-dependencies)
- [<span data-ttu-id="381e7-125">HTTP:ブラウザー SameSite の変更による認証への影響</span><span class="sxs-lookup"><span data-stu-id="381e7-125">HTTP: Browser SameSite changes impact authentication</span></span>](#http-browser-samesite-changes-impact-authentication)
- [<span data-ttu-id="381e7-126">HTTP:DefaultHttpContext の機能拡張の削除</span><span class="sxs-lookup"><span data-stu-id="381e7-126">HTTP: DefaultHttpContext extensibility removed</span></span>](#http-defaulthttpcontext-extensibility-removed)
- [<span data-ttu-id="381e7-127">HTTP:HeaderNames フィールドを静的読み取り専用に変更</span><span class="sxs-lookup"><span data-stu-id="381e7-127">HTTP: HeaderNames fields changed to static readonly</span></span>](#http-headernames-constants-changed-to-static-readonly)
- [<span data-ttu-id="381e7-128">HTTP:応答本文のインフラストラクチャの変更</span><span class="sxs-lookup"><span data-stu-id="381e7-128">HTTP: Response body infrastructure changes</span></span>](#http-response-body-infrastructure-changes)
- [<span data-ttu-id="381e7-129">HTTP:一部の cookie SameSite の既定値の変更</span><span class="sxs-lookup"><span data-stu-id="381e7-129">HTTP: Some cookie SameSite default values changed</span></span>](#http-some-cookie-samesite-defaults-changed-to-none)
- [<span data-ttu-id="381e7-130">HTTP:同期 IO を既定で無効化</span><span class="sxs-lookup"><span data-stu-id="381e7-130">HTTP: Synchronous IO disabled by default</span></span>](#http-synchronous-io-disabled-in-all-servers)
- [<span data-ttu-id="381e7-131">ID:AddDefaultUI メソッド オーバーロードの削除</span><span class="sxs-lookup"><span data-stu-id="381e7-131">Identity: AddDefaultUI method overload removed</span></span>](#identity-adddefaultui-method-overload-removed)
- [<span data-ttu-id="381e7-132">ID:UI ブートストラップ バージョンの変更</span><span class="sxs-lookup"><span data-stu-id="381e7-132">Identity: UI Bootstrap version change</span></span>](#identity-default-bootstrap-version-of-ui-changed)
- [<span data-ttu-id="381e7-133">ID:SignInAsync が認証されていない ID に対して例外をスロー</span><span class="sxs-lookup"><span data-stu-id="381e7-133">Identity: SignInAsync throws exception for unauthenticated identity</span></span>](#identity-signinasync-throws-exception-for-unauthenticated-identity)
- [<span data-ttu-id="381e7-134">ID:SignInManager コンストラクターで新しいパラメーターの受け入れ</span><span class="sxs-lookup"><span data-stu-id="381e7-134">Identity: SignInManager constructor accepts new parameter</span></span>](#identity-signinmanager-constructor-accepts-new-parameter)
- [<span data-ttu-id="381e7-135">ID:UI で静的な Web 資産機能を使用</span><span class="sxs-lookup"><span data-stu-id="381e7-135">Identity: UI uses static web assets feature</span></span>](#identity-ui-uses-static-web-assets-feature)
- [<span data-ttu-id="381e7-136">Kestrel:接続アダプターを削除</span><span class="sxs-lookup"><span data-stu-id="381e7-136">Kestrel: Connection adapters removed</span></span>](#kestrel-connection-adapters-removed)
- [<span data-ttu-id="381e7-137">Kestrel:空の HTTPS アセンブリを削除</span><span class="sxs-lookup"><span data-stu-id="381e7-137">Kestrel: Empty HTTPS assembly removed</span></span>](#kestrel-empty-https-assembly-removed)
- [<span data-ttu-id="381e7-138">Kestrel:要求トレーラー ヘッダーを新しいコレクションに移動</span><span class="sxs-lookup"><span data-stu-id="381e7-138">Kestrel: Request trailer headers moved to new collection</span></span>](#kestrel-request-trailer-headers-moved-to-new-collection)
- [<span data-ttu-id="381e7-139">Kestrel:トランスポート抽象化レイヤーの変更</span><span class="sxs-lookup"><span data-stu-id="381e7-139">Kestrel: Transport abstraction layer changes</span></span>](#kestrel-transport-abstractions-removed-and-made-public)
- [<span data-ttu-id="381e7-140">ローカリゼーション:API を古いとしてマーク</span><span class="sxs-lookup"><span data-stu-id="381e7-140">Localization: APIs marked obsolete</span></span>](#localization-resourcemanagerwithculturestringlocalizer-and-withculture-marked-obsolete)
- [<span data-ttu-id="381e7-141">ログ:internal になった DebugLogger クラス</span><span class="sxs-lookup"><span data-stu-id="381e7-141">Logging: DebugLogger class made internal</span></span>](#logging-debuglogger-class-made-internal)
- [<span data-ttu-id="381e7-142">MVC:コントローラー アクション Async サフィックスを削除</span><span class="sxs-lookup"><span data-stu-id="381e7-142">MVC: Controller action Async suffix removed</span></span>](#mvc-async-suffix-trimmed-from-controller-action-names)
- [<span data-ttu-id="381e7-143">MVC:JsonResult を Microsoft.AspNetCore.Mvc.Core に移動</span><span class="sxs-lookup"><span data-stu-id="381e7-143">MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core</span></span>](#mvc-jsonresult-moved-to-microsoftaspnetcoremvccore)
- [<span data-ttu-id="381e7-144">MVC:プリコンパイル ツールを非推奨</span><span class="sxs-lookup"><span data-stu-id="381e7-144">MVC: Precompilation tool deprecated</span></span>](#mvc-precompilation-tool-deprecated)
- [<span data-ttu-id="381e7-145">MVC:型を internal に変更</span><span class="sxs-lookup"><span data-stu-id="381e7-145">MVC: Types changed to internal</span></span>](#mvc-pubternal-types-changed-to-internal)
- [<span data-ttu-id="381e7-146">MVC:Web API 互換性 shim を削除</span><span class="sxs-lookup"><span data-stu-id="381e7-146">MVC: Web API compatibility shim removed</span></span>](#mvc-web-api-compatibility-shim-removed)
- [<span data-ttu-id="381e7-147">Razor:RazorTemplateEngine API が削除されました</span><span class="sxs-lookup"><span data-stu-id="381e7-147">Razor: RazorTemplateEngine API removed</span></span>](#razor-razortemplateengine-api-removed)
- [<span data-ttu-id="381e7-148">Razor:実行時コンパイルをパッケージに移動</span><span class="sxs-lookup"><span data-stu-id="381e7-148">Razor: Runtime compilation moved to a package</span></span>](#razor-runtime-compilation-moved-to-a-package)
- [<span data-ttu-id="381e7-149">セッション状態:古い API を削除</span><span class="sxs-lookup"><span data-stu-id="381e7-149">Session state: Obsolete APIs removed</span></span>](#session-state-obsolete-apis-removed)
- [<span data-ttu-id="381e7-150">共有フレームワーク:Microsoft.AspNetCore.App からアセンブリの削除</span><span class="sxs-lookup"><span data-stu-id="381e7-150">Shared framework: Assembly removal from Microsoft.AspNetCore.App</span></span>](#shared-framework-assemblies-removed-from-microsoftaspnetcoreapp)
- [<span data-ttu-id="381e7-151">共有フレームワーク:Microsoft.AspNetCore.All を削除</span><span class="sxs-lookup"><span data-stu-id="381e7-151">Shared framework: Microsoft.AspNetCore.All removed</span></span>](#shared-framework-removed-microsoftaspnetcoreall)
- [<span data-ttu-id="381e7-152">SignalR:HandshakeProtocol.SuccessHandshakeData を置き換え</span><span class="sxs-lookup"><span data-stu-id="381e7-152">SignalR: HandshakeProtocol.SuccessHandshakeData replaced</span></span>](#signalr-handshakeprotocolsuccesshandshakedata-replaced)
- [<span data-ttu-id="381e7-153">SignalR:HubConnection メソッドを削除</span><span class="sxs-lookup"><span data-stu-id="381e7-153">SignalR: HubConnection methods removed</span></span>](#signalr-hubconnection-resetsendping-and-resettimeout-methods-removed)
- [<span data-ttu-id="381e7-154">SignalR:HubConnectionContext コンストラクターを変更</span><span class="sxs-lookup"><span data-stu-id="381e7-154">SignalR: HubConnectionContext constructors changed</span></span>](#signalr-hubconnectioncontext-constructors-changed)
- [<span data-ttu-id="381e7-155">SignalR:JavaScript クライアント パッケージ名を変更</span><span class="sxs-lookup"><span data-stu-id="381e7-155">SignalR: JavaScript client package name change</span></span>](#signalr-javascript-client-package-name-changed)
- [<span data-ttu-id="381e7-156">SignalR:古い API</span><span class="sxs-lookup"><span data-stu-id="381e7-156">SignalR: Obsolete APIs</span></span>](#signalr-usesignalr-and-useconnections-methods-marked-obsolete)
- [<span data-ttu-id="381e7-157">SPA:SpaServices および NodeServices コンソール ロガー フォールバックの既定値を変更</span><span class="sxs-lookup"><span data-stu-id="381e7-157">SPAs: SpaServices and NodeServices console logger fallback default change</span></span>](#spas-spaservices-and-nodeservices-no-longer-fall-back-to-console-logger)
- [<span data-ttu-id="381e7-158">SPA:SpaServices および NodeServices を古いとしてマーク</span><span class="sxs-lookup"><span data-stu-id="381e7-158">SPAs: SpaServices and NodeServices marked obsolete</span></span>](#spas-spaservices-and-nodeservices-marked-obsolete)
- [<span data-ttu-id="381e7-159">ターゲット フレームワーク: .NET Framework がサポートされない</span><span class="sxs-lookup"><span data-stu-id="381e7-159">Target framework: .NET Framework not supported</span></span>](#target-framework-net-framework-support-dropped)

## <a name="aspnet-core-31"></a><span data-ttu-id="381e7-160">ASP.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="381e7-160">ASP.NET Core 3.1</span></span>

[!INCLUDE[HTTP: Browser SameSite changes impact authentication](~/includes/core-changes/aspnetcore/3.1/http-cookie-samesite-authn-impacts.md)]

***

## <a name="aspnet-core-30"></a><span data-ttu-id="381e7-161">ASP.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="381e7-161">ASP.NET Core 3.0</span></span>

[!INCLUDE[Obsolete Antiforgery, CORS, Diagnostics, MVC, and Routing APIs removed](~/includes/core-changes/aspnetcore/3.0/obsolete-apis-removed.md)]

<span data-ttu-id="381e7-162">\*\*_</span><span class="sxs-lookup"><span data-stu-id="381e7-162">\*\*_</span></span>

[!INCLUDE[Authentication: Google+ deprecation](~/includes/core-changes/aspnetcore/3.0/authn-google-plus-authn-changes.md)]

_*_

[!INCLUDE[Authentication: HttpContext.Authentication property removed](~/includes/core-changes/aspnetcore/3.0/authn-httpcontext-property-removed.md)]

_*_

[!INCLUDE[Authentication: Newtonsoft.Json types replaced](~/includes/core-changes/aspnetcore/3.0/authn-apis-json-types.md)]

_*_

[!INCLUDE[Authentication: OAuthHandler ExchangeCodeAsync signature changed](~/includes/core-changes/aspnetcore/3.0/authn-exchangecodeasync-signature-change.md)]

_*_

[!INCLUDE[Authorization: AddAuthorization overload assembly change](~/includes/core-changes/aspnetcore/3.0/authz-assembly-change.md)]

_*_

[!INCLUDE[Authorization: IAllowAnonymous removed from AuthorizationFilterContext.Filters](~/includes/core-changes/aspnetcore/3.0/authz-iallowanonymous-removed-from-collection.md)]

_*_

[!INCLUDE[Authorization: IAuthorizationPolicyProvider implementations require new method](~/includes/core-changes/aspnetcore/3.0/authz-iauthzpolicyprovider-new-method.md)]

_*_

[!INCLUDE[Caching: CompactOnMemoryPressure property removed](~/includes/core-changes/aspnetcore/3.0/caching-memory-property-removed.md)]

_*_

[!INCLUDE[Caching: Microsoft.Extensions.Caching.SqlServer uses new SqlClient package](~/includes/core-changes/aspnetcore/3.0/caching-new-sqlclient-package.md)]

_*_

[!INCLUDE[Caching: ResponseCaching types changed to internal](~/includes/core-changes/aspnetcore/3.0/caching-response-pubternal-to-internal.md)]

_*_

[!INCLUDE[Data Protection: DataProtection.AzureStorage uses new Azure Storage APIs](~/includes/core-changes/aspnetcore/3.0/dataprotection-azstorage-using-azstorage-apis.md)]

_*_

[!INCLUDE[Hosting: ANCM version 1 removed from hosting bundle](~/includes/core-changes/aspnetcore/3.0/hosting-ancmv1-hosting-bundle-removal.md)]

_*_

[!INCLUDE[Hosting: Generic host restriction on Startup constructor injection](~/includes/core-changes/aspnetcore/3.0/hosting-generic-host-startup-ctor-restriction.md)]

_*_

[!INCLUDE[Hosting: HTTPS redirection enabled for IIS OutOfProcess](~/includes/core-changes/aspnetcore/3.0/hosting-https-redirection-iis-outofprocess.md)]

_*_

[!INCLUDE[Hosting: IHostingEnvironment and IApplicationLifetime types replaced](~/includes/core-changes/aspnetcore/3.0/hosting-ihostingenv-iapplifetime-types-replaced.md)]

_*_

[!INCLUDE[Hosting: ObjectPoolProvider removed from WebHostBuilder dependencies](~/includes/core-changes/aspnetcore/3.0/hosting-objectpoolprovider-webhostbuilder-dependencies.md)]

_*_

[!INCLUDE[HTTP: DefaultHttpContext extensibility removed](~/includes/core-changes/aspnetcore/3.0/http-defaulthttpcontext-extensibility-removed.md)]

_*_

[!INCLUDE[HTTP: HeaderNames fields changed to static readonly](~/includes/core-changes/aspnetcore/3.0/http-headernames-constants-staticreadonly.md)]

_*_

[!INCLUDE[HTTP: Response body infrastructure changes](~/includes/core-changes/aspnetcore/3.0/http-response-body-changes.md)]

_*_

[!INCLUDE[HTTP: Some cookie SameSite default values changed](~/includes/core-changes/aspnetcore/3.0/http-cookie-samesite-defaults-change.md)]

_*_

[!INCLUDE[HTTP: Synchronous IO disabled by default](~/includes/core-changes/aspnetcore/3.0/http-synchronous-io-disabled.md)]

_*_

[!INCLUDE[Identity: AddDefaultUI method overload removed](~/includes/core-changes/aspnetcore/3.0/identity-ui-adddefaultui-overload-removed.md)]

_*_

[!INCLUDE[Identity: UI Bootstrap version change](~/includes/core-changes/aspnetcore/3.0/identity-ui-bootstrap-version.md)]

_*_

[!INCLUDE[Identity: SignInAsync throws exception for unauthenticated identity](~/includes/core-changes/aspnetcore/3.0/identity-signinasync-throws-exception.md)]

_*_

[!INCLUDE[Identity: SignInManager constructor accepts new parameter](~/includes/core-changes/aspnetcore/3.0/identity-signinmanager-ctor-parameter.md)]

_*_

[!INCLUDE[Identity: UI uses static web assets feature](~/includes/core-changes/aspnetcore/3.0/identity-ui-static-web-assets.md)]

_*_

[!INCLUDE[Kestrel: Connection adapters removed](~/includes/core-changes/aspnetcore/3.0/kestrel-connection-adapters-removed.md)]

_*_

[!INCLUDE[Kestrel: Empty HTTPS assembly removed](~/includes/core-changes/aspnetcore/3.0/kestrel-empty-assembly-removed.md)]

_*_

[!INCLUDE[Kestrel: Request trailer headers moved to new collection](~/includes/core-changes/aspnetcore/3.0/kestrel-request-trailer-headers.md)]

_*_

[!INCLUDE[Kestrel: Transport abstraction layer changes](~/includes/core-changes/aspnetcore/3.0/kestrel-transport-abstractions.md)]

_*_

[!INCLUDE[Localization: APIs marked obsolete](~/includes/core-changes/aspnetcore/3.0/localization-apis-marked-obsolete.md)]

_*_

[!INCLUDE[Logging: DebugLogger class made internal](~/includes/core-changes/aspnetcore/3.0/logging-debuglogger-to-internal.md)]

_*_

[!INCLUDE[MVC: Controller action Async suffix removed](~/includes/core-changes/aspnetcore/3.0/mvc-action-async-suffix-trimmed.md)]

_*_

[!INCLUDE[MVC: JsonResult moved to Microsoft.AspNetCore.Mvc.Core](~/includes/core-changes/aspnetcore/3.0/mvc-jsonresult-moved.md)]

_*_

[!INCLUDE[MVC: Precompilation tool deprecated](~/includes/core-changes/aspnetcore/3.0/mvc-precompilation-tool-deprecated.md)]

_*_

[!INCLUDE[MVC: Types changed to internal](~/includes/core-changes/aspnetcore/3.0/mvc-pubternal-to-internal.md)]

_*_

[!INCLUDE[MVC: Web API compatibility shim removed](~/includes/core-changes/aspnetcore/3.0/mvc-webapi-compat-shim-removed.md)]

_*_

[!INCLUDE[Razor: RazorTemplatEengine API removed](~/includes/core-changes/aspnetcore/3.0/razor-razortemplateengine-api-removed.md)]

_*_

[!INCLUDE[Razor: Runtime compilation moved to a package](~/includes/core-changes/aspnetcore/3.0/razor-runtime-compilation-package.md)]

_*_

[!INCLUDE[Session state: Obsolete APIs removed](~/includes/core-changes/aspnetcore/3.0/session-obsolete-apis-removed.md)]

_*_

[!INCLUDE[Shared framework: Assembly removal from Microsoft.AspNetCore.App](~/includes/core-changes/aspnetcore/3.0/sharedfx-app-shared-framework-assemblies.md)]

_*_

[!INCLUDE[Shared framework: Microsoft.AspNetCore.All removed](~/includes/core-changes/aspnetcore/3.0/sharedfx-all-framework-removed.md)]

_*_

[!INCLUDE[SignalR: HandshakeProtocol.SuccessHandshakeData replaced](~/includes/core-changes/aspnetcore/3.0/signalr-successhandshakedata-replaced.md)]

_*_

[!INCLUDE[SignalR: HubConnection methods removed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnection-methods-removed.md)]

_*_

[!INCLUDE[SignalR: HubConnectionContext constructors changed](~/includes/core-changes/aspnetcore/3.0/signalr-hubconnectioncontext-ctors.md)]

_*_

[!INCLUDE[SignalR: JavaScript client package name change](~/includes/core-changes/aspnetcore/3.0/signalr-js-client-package-name.md)]

_*_

[!INCLUDE[SignalR: Obsolete APIs](~/includes/core-changes/aspnetcore/3.0/signalr-obsolete-apis.md)]

_*_

[!INCLUDE[SPAs: SpaServices and NodeServices marked obsolete](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-obsolete.md)]

_*_

[!INCLUDE[SPAs: SpaServices and NodeServices console logger fallback default change](~/includes/core-changes/aspnetcore/3.0/spas-spaservices-nodeservices-fallback.md)]

_*_

[!INCLUDE[Target framework: .NET Framework not supported](~/includes/core-changes/aspnetcore/3.0/targetfx-netfx-tfm-support.md)]

<span data-ttu-id="381e7-163">_\*\*</span><span class="sxs-lookup"><span data-stu-id="381e7-163">_\*\*</span></span>
