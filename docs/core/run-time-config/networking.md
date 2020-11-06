---
title: ネットワークの構成設定
description: .NET Core アプリのネットワークを構成するランタイム設定について説明します。
ms.date: 11/27/2019
ms.topic: reference
ms.openlocfilehash: bda608e83bb1b093d7d9b860de9607f6734720aa
ms.sourcegitcommit: 7588b1f16b7608bc6833c05f91ae670c22ef56f8
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/02/2020
ms.locfileid: "93188303"
---
# <a name="run-time-configuration-options-for-networking"></a><span data-ttu-id="77bc7-103">ネットワークのランタイム構成オプション</span><span class="sxs-lookup"><span data-stu-id="77bc7-103">Run-time configuration options for networking</span></span>

## <a name="http2-protocol"></a><span data-ttu-id="77bc7-104">HTTP/2 プロトコル</span><span class="sxs-lookup"><span data-stu-id="77bc7-104">HTTP/2 protocol</span></span>

- <span data-ttu-id="77bc7-105">HTTP/2 プロトコルのサポートを有効にするかどうかを構成します。</span><span class="sxs-lookup"><span data-stu-id="77bc7-105">Configures whether support for the HTTP/2 protocol is enabled.</span></span>

- <span data-ttu-id="77bc7-106">.NET Core 3.0 で導入されました。</span><span class="sxs-lookup"><span data-stu-id="77bc7-106">Introduced in .NET Core 3.0.</span></span>

- <span data-ttu-id="77bc7-107">.NET Core 3.0 のみ:この設定を省略した場合、HTTP/2 プロトコルのサポートは無効になります。</span><span class="sxs-lookup"><span data-stu-id="77bc7-107">.NET Core 3.0 only: If you omit this setting, support for the HTTP/2 protocol is disabled.</span></span> <span data-ttu-id="77bc7-108">これは、値を `false` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="77bc7-108">This is equivalent to setting the value to `false`.</span></span>

- <span data-ttu-id="77bc7-109">.NET Core 3.1 および .NET 5+:この設定を省略した場合、HTTP/2 プロトコルのサポートは有効になります。</span><span class="sxs-lookup"><span data-stu-id="77bc7-109">.NET Core 3.1 and .NET 5+: If you omit this setting, support for the HTTP/2 protocol is enabled.</span></span> <span data-ttu-id="77bc7-110">これは、値を `true` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="77bc7-110">This is equivalent to setting the value to `true`.</span></span>

| | <span data-ttu-id="77bc7-111">設定の名前</span><span class="sxs-lookup"><span data-stu-id="77bc7-111">Setting name</span></span> | <span data-ttu-id="77bc7-112">値</span><span class="sxs-lookup"><span data-stu-id="77bc7-112">Values</span></span> |
| - | - | - |
| <span data-ttu-id="77bc7-113">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="77bc7-113">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.Http2Support` | <span data-ttu-id="77bc7-114">`false` - 無効</span><span class="sxs-lookup"><span data-stu-id="77bc7-114">`false` - disabled</span></span><br/><span data-ttu-id="77bc7-115">`true` - 有効</span><span class="sxs-lookup"><span data-stu-id="77bc7-115">`true` - enabled</span></span> |
| <span data-ttu-id="77bc7-116">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="77bc7-116">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2SUPPORT` | <span data-ttu-id="77bc7-117">`0` - 無効</span><span class="sxs-lookup"><span data-stu-id="77bc7-117">`0` - disabled</span></span><br/><span data-ttu-id="77bc7-118">`1` - 有効</span><span class="sxs-lookup"><span data-stu-id="77bc7-118">`1` - enabled</span></span> |

## <a name="usesocketshttphandler"></a><span data-ttu-id="77bc7-119">UseSocketsHttpHandler</span><span class="sxs-lookup"><span data-stu-id="77bc7-119">UseSocketsHttpHandler</span></span>

- <span data-ttu-id="77bc7-120"><xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> が <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> 以前の HTTP プロトコル スタック (Windows と `CurlHandler` では <xref:System.Net.Http.WinHttpHandler>、Linux では [libcurl](https://curl.haxx.se/libcurl/) の上位に実装された内部クラス) を使用するかどうかを構成します。</span><span class="sxs-lookup"><span data-stu-id="77bc7-120">Configures whether <xref:System.Net.Http.HttpClientHandler?displayProperty=nameWithType> uses <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType> or older HTTP protocol stacks (<xref:System.Net.Http.WinHttpHandler> on Windows and `CurlHandler`, an internal class implemented on top of [libcurl](https://curl.haxx.se/libcurl/), on Linux).</span></span>

  > [!NOTE]
  > <span data-ttu-id="77bc7-121"><xref:System.Net.Http.HttpClientHandler> クラスを直接インスタンス化するのではなく、高レベルのネットワーク API を使用している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="77bc7-121">You may be using high-level networking APIs instead of directly instantiating the <xref:System.Net.Http.HttpClientHandler> class.</span></span> <span data-ttu-id="77bc7-122">この設定は、<xref:System.Net.Http.HttpClient> や [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)) などの高レベル ネットワーク API で使用される HTTP プロトコル スタックにも影響します。</span><span class="sxs-lookup"><span data-stu-id="77bc7-122">This setting also affects which HTTP protocol stack is used by high-level networking APIs, including <xref:System.Net.Http.HttpClient> and [HttpClientFactory](/previous-versions/aspnet/hh995280(v=vs.118)).</span></span>

- <span data-ttu-id="77bc7-123">この設定を省略した場合、<xref:System.Net.Http.HttpClientHandler> では <xref:System.Net.Http.SocketsHttpHandler> が使用されます。</span><span class="sxs-lookup"><span data-stu-id="77bc7-123">If you omit this setting, <xref:System.Net.Http.HttpClientHandler> uses <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="77bc7-124">これは、値を `true` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="77bc7-124">This is equivalent to setting the value to `true`.</span></span>

- <span data-ttu-id="77bc7-125">この設定は、<xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> メソッドを呼び出すことによりプログラムで構成できます。</span><span class="sxs-lookup"><span data-stu-id="77bc7-125">You can configure this setting programmatically by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method.</span></span>

| | <span data-ttu-id="77bc7-126">設定の名前</span><span class="sxs-lookup"><span data-stu-id="77bc7-126">Setting name</span></span> | <span data-ttu-id="77bc7-127">値</span><span class="sxs-lookup"><span data-stu-id="77bc7-127">Values</span></span> |
| - | - | - |
| <span data-ttu-id="77bc7-128">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="77bc7-128">**runtimeconfig.json**</span></span> | `System.Net.Http.UseSocketsHttpHandler` | <span data-ttu-id="77bc7-129">`true` - <xref:System.Net.Http.SocketsHttpHandler> の使用を有効にする</span><span class="sxs-lookup"><span data-stu-id="77bc7-129">`true` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="77bc7-130">`false` - Windows では <xref:System.Net.Http.WinHttpHandler>、Linux では [libcurl](https://curl.haxx.se/libcurl/) の使用を有効にする</span><span class="sxs-lookup"><span data-stu-id="77bc7-130">`false` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |
| <span data-ttu-id="77bc7-131">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="77bc7-131">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` | <span data-ttu-id="77bc7-132">`1` - <xref:System.Net.Http.SocketsHttpHandler> の使用を有効にする</span><span class="sxs-lookup"><span data-stu-id="77bc7-132">`1` - enables the use of <xref:System.Net.Http.SocketsHttpHandler></span></span><br/><span data-ttu-id="77bc7-133">`0` - Windows では <xref:System.Net.Http.WinHttpHandler>、Linux では [libcurl](https://curl.haxx.se/libcurl/) の使用を有効にする</span><span class="sxs-lookup"><span data-stu-id="77bc7-133">`0` - enables the use of <xref:System.Net.Http.WinHttpHandler> on Windows or [libcurl](https://curl.haxx.se/libcurl/) on Linux</span></span> |

> [!NOTE]
> <span data-ttu-id="77bc7-134">.NET 5 以降では、`System.Net.Http.UseSocketsHttpHandler` 設定は使用できなくなりました。</span><span class="sxs-lookup"><span data-stu-id="77bc7-134">Starting in .NET 5, the `System.Net.Http.UseSocketsHttpHandler` setting is no longer available.</span></span>

## <a name="latin1-headers-net-core-31-only"></a><span data-ttu-id="77bc7-135">Latin1 ヘッダー (.NET Core 3.1 のみ)</span><span class="sxs-lookup"><span data-stu-id="77bc7-135">Latin1 headers (.NET Core 3.1 only)</span></span>

- <span data-ttu-id="77bc7-136">このスイッチによって HTTP ヘッダー検証の緩和が許可され、<xref:System.Net.Http.SocketsHttpHandler> では、ISO-8859-1 (Latin-1) でエンコードされた文字をヘッダーで送信できます。</span><span class="sxs-lookup"><span data-stu-id="77bc7-136">This switch allows relaxing the HTTP header validation, enabling <xref:System.Net.Http.SocketsHttpHandler> to send ISO-8859-1 (Latin-1) encoded characters in headers.</span></span>

- <span data-ttu-id="77bc7-137">この設定を省略した場合、ASCII 以外の文字を送信しようとすると <xref:System.Net.Http.HttpRequestException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="77bc7-137">If you omit this setting, an attempt to send a non-ASCII character will result in <xref:System.Net.Http.HttpRequestException>.</span></span> <span data-ttu-id="77bc7-138">これは、値を `false` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="77bc7-138">This is equivalent to setting the value to `false`.</span></span>

| | <span data-ttu-id="77bc7-139">設定の名前</span><span class="sxs-lookup"><span data-stu-id="77bc7-139">Setting name</span></span> | <span data-ttu-id="77bc7-140">値</span><span class="sxs-lookup"><span data-stu-id="77bc7-140">Values</span></span> |
| - | - | - |
| <span data-ttu-id="77bc7-141">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="77bc7-141">**runtimeconfig.json**</span></span> | `System.Net.Http.SocketsHttpHandler.AllowLatin1Headers` | <span data-ttu-id="77bc7-142">`false` - 無効</span><span class="sxs-lookup"><span data-stu-id="77bc7-142">`false` - disabled</span></span><br/><span data-ttu-id="77bc7-143">`true` - 有効</span><span class="sxs-lookup"><span data-stu-id="77bc7-143">`true` - enabled</span></span> |
| <span data-ttu-id="77bc7-144">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="77bc7-144">**Environment variable**</span></span> | `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_ALLOWLATIN1HEADERS` | <span data-ttu-id="77bc7-145">`0` - 無効</span><span class="sxs-lookup"><span data-stu-id="77bc7-145">`0` - disabled</span></span><br/><span data-ttu-id="77bc7-146">`1` - 有効</span><span class="sxs-lookup"><span data-stu-id="77bc7-146">`1` - enabled</span></span> |

> [!NOTE]
> <span data-ttu-id="77bc7-147">このオプションは .NET Core バージョン 3.1 9 以降の 3.1 でのみお使いになれます。それ以前またはそれ以降のバージョンでは利用できません。</span><span class="sxs-lookup"><span data-stu-id="77bc7-147">This option is only available in .NET Core 3.1 since version 3.1.9, and not in previous or later versions.</span></span> <span data-ttu-id="77bc7-148">.NET 5 では、<xref:System.Net.Http.SocketsHttpHandler.RequestHeaderEncodingSelector> の使用をお勧めします。</span><span class="sxs-lookup"><span data-stu-id="77bc7-148">In .NET 5 we recommend using <xref:System.Net.Http.SocketsHttpHandler.RequestHeaderEncodingSelector>.</span></span>
