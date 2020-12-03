---
title: 破壊的変更:ConsoleLoggerOptions の古いプロパティ
description: Core .NET ライブラリにおける .NET 5.0 の破壊的変更について学習します。ConsoleLoggerFormat 型と ConsoleLoggerOptions のいくつかのプロパティは、古くなりました。
ms.date: 11/01/2020
ms.openlocfilehash: e38ba3bda371c713a8b2cb4cda8b4c585dac29f5
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95759926"
---
# <a name="obsolete-properties-on-consoleloggeroptions"></a><span data-ttu-id="bc91f-103">ConsoleLoggerOptions の古いプロパティ</span><span class="sxs-lookup"><span data-stu-id="bc91f-103">Obsolete properties on ConsoleLoggerOptions</span></span>

<span data-ttu-id="bc91f-104"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> 型および <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> のいくつかのプロパティは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="bc91f-104">The <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type and some properties on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> are now obsolete.</span></span>

## <a name="change-description"></a><span data-ttu-id="bc91f-105">変更内容</span><span class="sxs-lookup"><span data-stu-id="bc91f-105">Change description</span></span>

<span data-ttu-id="bc91f-106">.NET 5.0 以降では、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> 型および <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> のいくつかのプロパティは、互換性のために残されています。</span><span class="sxs-lookup"><span data-stu-id="bc91f-106">Starting in .NET 5.0, the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerFormat?displayProperty=nameWithType> type and several properties on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> are obsolete.</span></span> <span data-ttu-id="bc91f-107">互換性のために残されているプロパティは、次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="bc91f-107">The obsolete properties are:</span></span>

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType>

<span data-ttu-id="bc91f-108">新しいフォーマッタの導入により、これらのプロパティを個々のフォーマッタで使用できるようになりました。</span><span class="sxs-lookup"><span data-stu-id="bc91f-108">With the introduction of new formatters, these properties are now available on the individual formatters.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="bc91f-109">変更理由</span><span class="sxs-lookup"><span data-stu-id="bc91f-109">Reason for change</span></span>

<span data-ttu-id="bc91f-110"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> プロパティは列挙型であり、カスタム フォーマッタを表すことはできません。</span><span class="sxs-lookup"><span data-stu-id="bc91f-110">The <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> property is an enumeration type, which cannot represent a custom formatter.</span></span>

<span data-ttu-id="bc91f-111">残りのプロパティは、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> に設定され、コンソール ログ用の組み込みの書式の両方に適用されていました。</span><span class="sxs-lookup"><span data-stu-id="bc91f-111">The remaining properties were set on <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions> and applied to both of the built-in formats for console logs.</span></span> <span data-ttu-id="bc91f-112">ただし、新しいフォーマッタ API を導入することで、フォーマッタ固有のオプションでの書式設定がよりわかりやすくなります。</span><span class="sxs-lookup"><span data-stu-id="bc91f-112">However, with the introduction of a new formatter API, it makes more sense for formatting to be represented on the formatter-specific options.</span></span> <span data-ttu-id="bc91f-113">この変更により、ロガーとロガー フォーマッタの分離が改善されます。</span><span class="sxs-lookup"><span data-stu-id="bc91f-113">This change provides better separation between the logger and logger formatters.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="bc91f-114">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="bc91f-114">Version introduced</span></span>

<span data-ttu-id="bc91f-115">5.0</span><span class="sxs-lookup"><span data-stu-id="bc91f-115">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="bc91f-116">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="bc91f-116">Recommended action</span></span>

- <span data-ttu-id="bc91f-117"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> プロパティの代わりに、新しい <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> プロパティを使用します。</span><span class="sxs-lookup"><span data-stu-id="bc91f-117">Use the new <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName?displayProperty=nameWithType> property in place of the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="bc91f-118">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="bc91f-118">For example:</span></span>

  ```csharp
  loggingBuilder.AddConsole(options =>
  {
    options.FormatterName = ConsoleFormatterNames.Systemd;
  });
  ```

  <span data-ttu-id="bc91f-119"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> と <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> にはいくつかの違いがあります。</span><span class="sxs-lookup"><span data-stu-id="bc91f-119">There are several differences between <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> and <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format>:</span></span>

  - <span data-ttu-id="bc91f-120"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> には、`Default` と `Systemd` の 2 つのオプションがあるのみです。</span><span class="sxs-lookup"><span data-stu-id="bc91f-120"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format> has only two possible options: `Default` and `Systemd`.</span></span>
  - <span data-ttu-id="bc91f-121"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> では、大文字と小文字は区別されず、任意の文字列を指定できます。</span><span class="sxs-lookup"><span data-stu-id="bc91f-121"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.FormatterName> is case insensitive and can be any string.</span></span> <span data-ttu-id="bc91f-122">予約された組み込みの名前は、`Simple`、`Systemd`、`Json` (.NET 5.0 以降) です。</span><span class="sxs-lookup"><span data-stu-id="bc91f-122">The reserved, built-in names are `Simple`, `Systemd`, and `Json` (.NET 5.0 and later).</span></span>
  - <span data-ttu-id="bc91f-123">`"Format": "Systemd"` は `"FormatterName": "Systemd"` にマップされます。</span><span class="sxs-lookup"><span data-stu-id="bc91f-123">`"Format": "Systemd"` maps to `"FormatterName": "Systemd"`.</span></span>
  - <span data-ttu-id="bc91f-124">`"Format": "Default"` は `"FormatterName": "Simple"` にマップされます。</span><span class="sxs-lookup"><span data-stu-id="bc91f-124">`"Format": "Default"` maps to `"FormatterName": "Simple"`.</span></span>

- <span data-ttu-id="bc91f-125"><xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors>、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes>、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat>、<xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> の各プロパティについては、新しい <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions> 型、<xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions> 型、または <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> 型の対応するプロパティを代わりに使用します。</span><span class="sxs-lookup"><span data-stu-id="bc91f-125">For the <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes>, <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat>, and <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp> properties, use the corresponding property on the new <xref:Microsoft.Extensions.Logging.Console.ConsoleFormatterOptions>, <xref:Microsoft.Extensions.Logging.Console.JsonConsoleFormatterOptions>, or <xref:Microsoft.Extensions.Logging.Console.SimpleConsoleFormatterOptions> types instead.</span></span> <span data-ttu-id="bc91f-126">次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="bc91f-126">For example:</span></span>

  ```csharp
  loggingBuilder.AddSimpleConsole(options =>
  {
      options.DisableColors = true;
  });
  ```

<span data-ttu-id="bc91f-127">次の 2 つの JSON スニペットは、構成ファイルがどのように変更されているかを示しています。</span><span class="sxs-lookup"><span data-stu-id="bc91f-127">The following two JSON snippets show how the configuration file changes.</span></span> <span data-ttu-id="bc91f-128">古い構成ファイル:</span><span class="sxs-lookup"><span data-stu-id="bc91f-128">Old configuration file:</span></span>

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "None",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    },

    "Console": {
      "LogLevel": {
        "Default": "Information"
      },
      "Format": "Systemd",
      "IncludeScopes": true,
      "TimestampFormat": "HH:mm:ss",
      "UseUtcTimestamp": true
    }
  },
  "AllowedHosts": "*"
}
```

<span data-ttu-id="bc91f-129">新しい構成ファイル:</span><span class="sxs-lookup"><span data-stu-id="bc91f-129">New configuration file:</span></span>

```json
{
  "Logging": {
    "LogLevel": {
      "Default": "None",
      "Microsoft": "Warning",
      "Microsoft.Hosting.Lifetime": "Information"
    },

    "Console": {
      "LogLevel": {
        "Default": "Information"
      },
      "FormatterName": "Systemd",
      "FormatterOptions": {
        "IncludeScopes": true,
        "TimestampFormat": "HH:mm:ss",
        "UseUtcTimestamp": true
      }
    }
  },
  "AllowedHosts": "*"
}
```

## <a name="affected-apis"></a><span data-ttu-id="bc91f-130">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="bc91f-130">Affected APIs</span></span>

- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp?displayProperty=fullName>
- <xref:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format?displayProperty=fullName>

<!--

#### Category

- Core .NET libraries
- ASP.NET

### Affected APIs

- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.DisableColors`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.IncludeScopes`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.TimestampFormat`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.UseUtcTimestamp`
- `P:Microsoft.Extensions.Logging.Console.ConsoleLoggerOptions.Format`

-->
