---
title: 破壊的変更:HttpSys:既定で無効になっているクライアント証明書の再ネゴシエーション
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: HttpSys:既定で無効になっているクライアント証明書の再ネゴシエーション'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: 796989e1a21e3cb206d081e4fe8f79630121dc84
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759331"
---
# <a name="httpsys-client-certificate-renegotiation-disabled-by-default"></a><span data-ttu-id="a155a-103">HttpSys:既定で無効になっているクライアント証明書の再ネゴシエーション</span><span class="sxs-lookup"><span data-stu-id="a155a-103">HttpSys: Client certificate renegotiation disabled by default</span></span>

<span data-ttu-id="a155a-104">接続を再ネゴシエートし、クライアント証明書を要求するオプションは既定で無効になっています。</span><span class="sxs-lookup"><span data-stu-id="a155a-104">The option to renegotiate a connection and request a client certificate has been disabled by default.</span></span> <span data-ttu-id="a155a-105">ディスカッションについては、イシュー [dotnet/aspnetcore#23181](https://github.com/dotnet/aspnetcore/issues/23181) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a155a-105">For discussion, see issue [dotnet/aspnetcore#23181](https://github.com/dotnet/aspnetcore/issues/23181).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="a155a-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="a155a-106">Version introduced</span></span>

<span data-ttu-id="a155a-107">ASP.NET Core 5.0</span><span class="sxs-lookup"><span data-stu-id="a155a-107">ASP.NET Core 5.0</span></span>

## <a name="old-behavior"></a><span data-ttu-id="a155a-108">以前の動作</span><span class="sxs-lookup"><span data-stu-id="a155a-108">Old behavior</span></span>

<span data-ttu-id="a155a-109">接続を再ネゴシエートし、クライアント証明書を要求できます。</span><span class="sxs-lookup"><span data-stu-id="a155a-109">The connection can be renegotiated to request a client certificate.</span></span>

## <a name="new-behavior"></a><span data-ttu-id="a155a-110">新しい動作</span><span class="sxs-lookup"><span data-stu-id="a155a-110">New behavior</span></span>

<span data-ttu-id="a155a-111">クライアント証明書は、初回接続ハンドシェイク中にのみ要求できます。</span><span class="sxs-lookup"><span data-stu-id="a155a-111">Client certificates can only be requested during the initial connection handshake.</span></span> <span data-ttu-id="a155a-112">詳細については、pull request [dotnet/aspnetcore#23162](https://github.com/dotnet/aspnetcore/pull/23162) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a155a-112">For more information, see pull request [dotnet/aspnetcore#23162](https://github.com/dotnet/aspnetcore/pull/23162).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="a155a-113">変更理由</span><span class="sxs-lookup"><span data-stu-id="a155a-113">Reason for change</span></span>

<span data-ttu-id="a155a-114">再ネゴシエーションによって、パフォーマンスとデッドロックのさまざまな問題が発生しました。</span><span class="sxs-lookup"><span data-stu-id="a155a-114">Renegotiation caused a number of performance and deadlock issues.</span></span> <span data-ttu-id="a155a-115">また、HTTP/2 でサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a155a-115">It's also not supported in HTTP/2.</span></span> <span data-ttu-id="a155a-116">この動作を制御するオプションが ASP.NET Core 3.1 で導入されて以降の追加コンテキストについては、イシュー [dotnet/aspnetcore#14806](https://github.com/dotnet/aspnetcore/issues/14806) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a155a-116">For additional context from when the option to control this behavior was introduced in ASP.NET Core 3.1, see issue [dotnet/aspnetcore#14806](https://github.com/dotnet/aspnetcore/issues/14806).</span></span>

## <a name="recommended-action"></a><span data-ttu-id="a155a-117">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="a155a-117">Recommended action</span></span>

<span data-ttu-id="a155a-118">クライアント証明書を必要とするアプリでは *netsh.exe* を使用し、`clientcertnegotiation` オプションを `enabled` に設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a155a-118">Apps that require client certificates should use *netsh.exe* to set the `clientcertnegotiation` option to `enabled`.</span></span> <span data-ttu-id="a155a-119">詳細については、「[netsh http コマンド](/windows-server/networking/technologies/netsh/netsh-http)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a155a-119">For more information, see [netsh http commands](/windows-server/networking/technologies/netsh/netsh-http).</span></span>

<span data-ttu-id="a155a-120">クライアント証明書をアプリの一部のみで有効にする場合、「[オプションのクライアント証明書](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates)」にあるガイダンスをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="a155a-120">If you want client certificates enabled for only some parts of your app, see the guidance at [Optional client certificates](/aspnet/core/security/authentication/certauth?view=aspnetcore-3.1#optional-client-certificates).</span></span>

<span data-ttu-id="a155a-121">以前の再ネゴシエート動作が必要な場合、以前の値である `ClientCertificateMethod.AllowRenegotiate` に `HttpSysOptions.ClientCertificateMethod` を設定してください。</span><span class="sxs-lookup"><span data-stu-id="a155a-121">If you need the old renegotiate behavior, set `HttpSysOptions.ClientCertificateMethod` to the old value `ClientCertificateMethod.AllowRenegotiate`.</span></span> <span data-ttu-id="a155a-122">これは上述の理由から推奨されておらず、リンク先のガイダンスで推奨されていません。</span><span class="sxs-lookup"><span data-stu-id="a155a-122">This isn't recommended for the reasons outlined above and in the linked guidance.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="a155a-123">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="a155a-123">Affected APIs</span></span>

- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.ClientCertificate`
- `Overload:Microsoft.AspNetCore.Http.ConnectionInfo.GetClientCertificateAsync`
- `Overload:Microsoft.AspNetCore.Server.HttpSys.HttpSysOptions.ClientCertificateMethod`

-->
