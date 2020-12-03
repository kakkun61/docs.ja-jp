---
title: '破壊的変更: SignalR:MessagePack ハブ プロトコル オプションの種類を変更'
description: 'ASP.NET Core 5.0 での破壊的変更について学習します。タイトル: SignalR:MessagePack ハブ プロトコル オプションの種類を変更'
author: scottaddie
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: b75dbec834699472f18b3058052274476bd9751d
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760028"
---
# <a name="signalr-messagepack-hub-protocol-options-type-changed"></a><span data-ttu-id="87442-103">SignalR:MessagePack ハブ プロトコル オプションの種類を変更</span><span class="sxs-lookup"><span data-stu-id="87442-103">SignalR: MessagePack Hub Protocol options type changed</span></span>

<span data-ttu-id="87442-104">ASP.NET Core SignalR MessagePack ハブ プロトコルのオプションの型が `IList<MessagePack.IFormatterResolver>` から [MessagePack](https://www.nuget.org/packages/MessagePack) ライブラリの `MessagePackSerializerOptions` 型に変更されました。</span><span class="sxs-lookup"><span data-stu-id="87442-104">The ASP.NET Core SignalR MessagePack Hub Protocol options type has changed from `IList<MessagePack.IFormatterResolver>` to the [MessagePack](https://www.nuget.org/packages/MessagePack) library's `MessagePackSerializerOptions` type.</span></span>

<span data-ttu-id="87442-105">この変更のディスカッションについては、[dotnet/aspnetcore#20506](https://github.com/dotnet/aspnetcore/issues/20506) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="87442-105">For discussion on this change, see [dotnet/aspnetcore#20506](https://github.com/dotnet/aspnetcore/issues/20506).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="87442-106">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="87442-106">Version introduced</span></span>

<span data-ttu-id="87442-107">5.0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="87442-107">5.0 Preview 4</span></span>

## <a name="old-behavior"></a><span data-ttu-id="87442-108">以前の動作</span><span class="sxs-lookup"><span data-stu-id="87442-108">Old behavior</span></span>

<span data-ttu-id="87442-109">次の例に示されているようにオプションを増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="87442-109">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers.Add(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="87442-110">次のようにオプションを置換してください。</span><span class="sxs-lookup"><span data-stu-id="87442-110">And replace the options as follows:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers = new List<MessagePack.IFormatterResolver>()
        {
            MessagePack.Resolvers.StandardResolver.Instance
        };
    });
```

## <a name="new-behavior"></a><span data-ttu-id="87442-111">新しい動作</span><span class="sxs-lookup"><span data-stu-id="87442-111">New behavior</span></span>

<span data-ttu-id="87442-112">次の例に示されているようにオプションを増やすことができます。</span><span class="sxs-lookup"><span data-stu-id="87442-112">You can add to the options as shown in the following example:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions =
            options.SerializeOptions.WithResolver(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

<span data-ttu-id="87442-113">次のようにオプションを置換してください。</span><span class="sxs-lookup"><span data-stu-id="87442-113">And replace the options as follows:</span></span>

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions = MessagePackSerializerOptions
                .Standard
                .WithResolver(MessagePack.Resolvers.StandardResolver.Instance)
                .WithSecurity(MessagePackSecurity.UntrustedData);
    });
```

## <a name="reason-for-change"></a><span data-ttu-id="87442-114">変更理由</span><span class="sxs-lookup"><span data-stu-id="87442-114">Reason for change</span></span>

<span data-ttu-id="87442-115">この変更は [aspnet/Announcements#404](https://github.com/aspnet/Announcements/issues/404) で告知した MessagePack v2.x への以降の一環です。</span><span class="sxs-lookup"><span data-stu-id="87442-115">This change is part of moving to MessagePack v2.x, which was announced in [aspnet/Announcements#404](https://github.com/aspnet/Announcements/issues/404).</span></span> <span data-ttu-id="87442-116">v2.x ライブラリで追加されたオプション API は使いやすく、以前に公開されていた `MessagePack.IFormatterResolver` のリストより機能が多くなっています。</span><span class="sxs-lookup"><span data-stu-id="87442-116">The v2.x library has added an options API that's easier to use and provides more features than the list of `MessagePack.IFormatterResolver` that was exposed before.</span></span>

## <a name="recommended-action"></a><span data-ttu-id="87442-117">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="87442-117">Recommended action</span></span>

<span data-ttu-id="87442-118">この重大な変更は、<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions> で値を構成しているユーザーに影響します。</span><span class="sxs-lookup"><span data-stu-id="87442-118">This breaking change affects anyone who is configuring values on <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>.</span></span> <span data-ttu-id="87442-119">ASP.NET Core SignalR MessagePack ハブ プロトコルを使用しているとき、このオプションを変更する場合、上の画像のように新しいオプション API を使用するように使用状況を更新します。</span><span class="sxs-lookup"><span data-stu-id="87442-119">If you're using the ASP.NET Core SignalR MessagePack Hub Protocol and modifying the options, update your usage to use the new options API as shown above.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="87442-120">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="87442-120">Affected APIs</span></span>

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
