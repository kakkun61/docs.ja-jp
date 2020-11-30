---
title: グローバリゼーションの構成設定
description: .NET Core アプリのグローバリゼーションの側面 (たとえば、日本語の日付の解析方法など) を構成するランタイム設定について説明します。
ms.date: 05/18/2020
ms.topic: reference
ms.openlocfilehash: fc98e965093c28b75b9b66e4f1c9f147abd4680e
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95721916"
---
# <a name="run-time-configuration-options-for-globalization"></a><span data-ttu-id="3b22c-103">グローバリゼーションのランタイム構成オプション</span><span class="sxs-lookup"><span data-stu-id="3b22c-103">Run-time configuration options for globalization</span></span>

## <a name="invariant-mode"></a><span data-ttu-id="3b22c-104">インバリアント モード</span><span class="sxs-lookup"><span data-stu-id="3b22c-104">Invariant mode</span></span>

- <span data-ttu-id="3b22c-105">.NET Core を、カルチャ固有のデータや動作にアクセスせずにグローバリゼーション インバリアント モードで実行するかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="3b22c-105">Determines whether a .NET Core app runs in globalization-invariant mode without access to culture-specific data and behavior.</span></span>
- <span data-ttu-id="3b22c-106">この設定を省略した場合、アプリはカルチャ データにアクセスできる状態で実行されます。</span><span class="sxs-lookup"><span data-stu-id="3b22c-106">If you omit this setting, the app runs with access to cultural data.</span></span> <span data-ttu-id="3b22c-107">これは、値を `false` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="3b22c-107">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="3b22c-108">詳細については、「[.NET Core のグローバリゼーション インバリアント モード](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b22c-108">For more information, see [.NET Core globalization invariant mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

| | <span data-ttu-id="3b22c-109">設定の名前</span><span class="sxs-lookup"><span data-stu-id="3b22c-109">Setting name</span></span> | <span data-ttu-id="3b22c-110">値</span><span class="sxs-lookup"><span data-stu-id="3b22c-110">Values</span></span> |
| - | - | - |
| <span data-ttu-id="3b22c-111">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="3b22c-111">**runtimeconfig.json**</span></span> | `System.Globalization.Invariant` | <span data-ttu-id="3b22c-112">`false` - カルチャ データにアクセスする</span><span class="sxs-lookup"><span data-stu-id="3b22c-112">`false` - access to cultural data</span></span><br/><span data-ttu-id="3b22c-113">`true` - インバリアント モードで実行する</span><span class="sxs-lookup"><span data-stu-id="3b22c-113">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="3b22c-114">**MSBuild のプロパティ**</span><span class="sxs-lookup"><span data-stu-id="3b22c-114">**MSBuild property**</span></span> | `InvariantGlobalization` | <span data-ttu-id="3b22c-115">`false` - カルチャ データにアクセスする</span><span class="sxs-lookup"><span data-stu-id="3b22c-115">`false` - access to cultural data</span></span><br/><span data-ttu-id="3b22c-116">`true` - インバリアント モードで実行する</span><span class="sxs-lookup"><span data-stu-id="3b22c-116">`true` - run in invariant mode</span></span> |
| <span data-ttu-id="3b22c-117">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="3b22c-117">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_INVARIANT` | <span data-ttu-id="3b22c-118">`0` - カルチャ データにアクセスする</span><span class="sxs-lookup"><span data-stu-id="3b22c-118">`0` - access to cultural data</span></span><br/><span data-ttu-id="3b22c-119">`1` - インバリアント モードで実行する</span><span class="sxs-lookup"><span data-stu-id="3b22c-119">`1` - run in invariant mode</span></span> |

### <a name="examples"></a><span data-ttu-id="3b22c-120">使用例</span><span class="sxs-lookup"><span data-stu-id="3b22c-120">Examples</span></span>

<span data-ttu-id="3b22c-121">*runtimeconfig.json* ファイル:</span><span class="sxs-lookup"><span data-stu-id="3b22c-121">*runtimeconfig.json* file:</span></span>

```json
{
   "runtimeOptions": {
      "configProperties": {
         "System.Globalization.Invariant": true
      }
   }
}
```

<span data-ttu-id="3b22c-122">プロジェクト ファイル:</span><span class="sxs-lookup"><span data-stu-id="3b22c-122">Project file:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <InvariantGlobalization>true</InvariantGlobalization>
  </PropertyGroup>

</Project>
```

## <a name="era-year-ranges"></a><span data-ttu-id="3b22c-123">年号の範囲</span><span class="sxs-lookup"><span data-stu-id="3b22c-123">Era year ranges</span></span>

- <span data-ttu-id="3b22c-124">複数の年号をサポートするカレンダーの範囲チェックを緩和するか、または日付が年号の日付範囲をオーバーフローした場合に <xref:System.ArgumentOutOfRangeException> をスローするかを決定します。</span><span class="sxs-lookup"><span data-stu-id="3b22c-124">Determines whether range checks for calendars that support multiple eras are relaxed or whether dates that overflow an era's date range throw an <xref:System.ArgumentOutOfRangeException>.</span></span>
- <span data-ttu-id="3b22c-125">この設定を省略した場合、範囲チェックは緩和されます。</span><span class="sxs-lookup"><span data-stu-id="3b22c-125">If you omit this setting, range checks are relaxed.</span></span> <span data-ttu-id="3b22c-126">これは、値を `false` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="3b22c-126">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="3b22c-127">詳細については、「[カレンダー、時代 (年号)、および日付範囲: 緩やかな範囲のチェック](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b22c-127">For more information, see [Calendars, eras, and date ranges: Relaxed range checks](../../standard/datetime/working-with-calendars.md#calendars-eras-and-date-ranges-relaxed-range-checks).</span></span>

| | <span data-ttu-id="3b22c-128">設定の名前</span><span class="sxs-lookup"><span data-stu-id="3b22c-128">Setting name</span></span> | <span data-ttu-id="3b22c-129">値</span><span class="sxs-lookup"><span data-stu-id="3b22c-129">Values</span></span> |
| - | - | - |
| <span data-ttu-id="3b22c-130">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="3b22c-130">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceJapaneseEraYearRanges` | <span data-ttu-id="3b22c-131">`false` - 緩和された範囲チェック</span><span class="sxs-lookup"><span data-stu-id="3b22c-131">`false` - relaxed range checks</span></span><br/><span data-ttu-id="3b22c-132">`true` - オーバーフローによって例外が発生する</span><span class="sxs-lookup"><span data-stu-id="3b22c-132">`true` - overflows cause an exception</span></span> |
| <span data-ttu-id="3b22c-133">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="3b22c-133">**Environment variable**</span></span> | <span data-ttu-id="3b22c-134">N/A</span><span class="sxs-lookup"><span data-stu-id="3b22c-134">N/A</span></span> | <span data-ttu-id="3b22c-135">N/A</span><span class="sxs-lookup"><span data-stu-id="3b22c-135">N/A</span></span> |

## <a name="japanese-date-parsing"></a><span data-ttu-id="3b22c-136">日本の日付の解析</span><span class="sxs-lookup"><span data-stu-id="3b22c-136">Japanese date parsing</span></span>

- <span data-ttu-id="3b22c-137">年として "1" または "元年" のいずれかを含む文字列を正しく解析するか、または "1" のみをサポートするかを決定します。</span><span class="sxs-lookup"><span data-stu-id="3b22c-137">Determines whether a string that contains either "1" or "Gannen" as the year parses successfully or whether only "1" is supported.</span></span>
- <span data-ttu-id="3b22c-138">この設定を省略した場合、年として "1" または "元年" が含まれる文字列は、正常に解析されます。</span><span class="sxs-lookup"><span data-stu-id="3b22c-138">If you omit this setting, strings that contain either "1" or "Gannen" as the year parse successfully.</span></span> <span data-ttu-id="3b22c-139">これは、値を `false` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="3b22c-139">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="3b22c-140">詳細については、「[複数の時代 (年号) のカレンダーで日付を表す](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b22c-140">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="3b22c-141">設定の名前</span><span class="sxs-lookup"><span data-stu-id="3b22c-141">Setting name</span></span> | <span data-ttu-id="3b22c-142">値</span><span class="sxs-lookup"><span data-stu-id="3b22c-142">Values</span></span> |
| - | - | - |
| <span data-ttu-id="3b22c-143">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="3b22c-143">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.EnforceLegacyJapaneseDateParsing` | <span data-ttu-id="3b22c-144">`false` - "元年" または "1" をサポートする</span><span class="sxs-lookup"><span data-stu-id="3b22c-144">`false` - "Gannen" or "1" is supported</span></span><br/><span data-ttu-id="3b22c-145">`true` - "1" のみをサポートする</span><span class="sxs-lookup"><span data-stu-id="3b22c-145">`true` - only "1" is supported</span></span> |
| <span data-ttu-id="3b22c-146">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="3b22c-146">**Environment variable**</span></span> | <span data-ttu-id="3b22c-147">N/A</span><span class="sxs-lookup"><span data-stu-id="3b22c-147">N/A</span></span> | <span data-ttu-id="3b22c-148">N/A</span><span class="sxs-lookup"><span data-stu-id="3b22c-148">N/A</span></span> |

## <a name="japanese-year-format"></a><span data-ttu-id="3b22c-149">日本の年の形式</span><span class="sxs-lookup"><span data-stu-id="3b22c-149">Japanese year format</span></span>

- <span data-ttu-id="3b22c-150">和暦の元年を "元年" または "1" のどちらで書式設定するかを決定します。</span><span class="sxs-lookup"><span data-stu-id="3b22c-150">Determines whether the first year of a Japanese calendar era is formatted as "Gannen" or as a number.</span></span>
- <span data-ttu-id="3b22c-151">この設定を省略した場合、最初の年は "元年" として書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="3b22c-151">If you omit this setting, the first year is formatted as "Gannen".</span></span> <span data-ttu-id="3b22c-152">これは、値を `false` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="3b22c-152">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="3b22c-153">詳細については、「[複数の時代 (年号) のカレンダーで日付を表す](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b22c-153">For more information, see [Represent dates in calendars with multiple eras](../../standard/datetime/working-with-calendars.md#represent-dates-in-calendars-with-multiple-eras).</span></span>

| | <span data-ttu-id="3b22c-154">設定の名前</span><span class="sxs-lookup"><span data-stu-id="3b22c-154">Setting name</span></span> | <span data-ttu-id="3b22c-155">値</span><span class="sxs-lookup"><span data-stu-id="3b22c-155">Values</span></span> |
| - | - | - |
| <span data-ttu-id="3b22c-156">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="3b22c-156">**runtimeconfig.json**</span></span> | `Switch.System.Globalization.FormatJapaneseFirstYearAsANumber` | <span data-ttu-id="3b22c-157">`false` - "元年" として書式設定する</span><span class="sxs-lookup"><span data-stu-id="3b22c-157">`false` - format as "Gannen"</span></span><br/><span data-ttu-id="3b22c-158">`true` - 数字として書式設定する</span><span class="sxs-lookup"><span data-stu-id="3b22c-158">`true` - format as number</span></span> |
| <span data-ttu-id="3b22c-159">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="3b22c-159">**Environment variable**</span></span> | <span data-ttu-id="3b22c-160">N/A</span><span class="sxs-lookup"><span data-stu-id="3b22c-160">N/A</span></span> | <span data-ttu-id="3b22c-161">N/A</span><span class="sxs-lookup"><span data-stu-id="3b22c-161">N/A</span></span> |

## <a name="nls"></a><span data-ttu-id="3b22c-162">NLS</span><span class="sxs-lookup"><span data-stu-id="3b22c-162">NLS</span></span>

- <span data-ttu-id="3b22c-163">.NET で Windows アプリ用に各国語サポート (NLS) または International Components for Unicode (ICU) のグローバリゼーション API が使用されるかどうかを決定します。</span><span class="sxs-lookup"><span data-stu-id="3b22c-163">Determines whether .NET uses National Language Support (NLS) or International Components for Unicode (ICU) globalization APIs for Windows apps.</span></span> <span data-ttu-id="3b22c-164">.NET 5.0 以降のバージョンの場合、Windows 10 May 2019 Update 以降のバージョンでは ICU グローバリゼーション API が既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="3b22c-164">.NET 5.0 and later versions use ICU globalization APIs by default on Windows 10 May 2019 Update and later versions.</span></span>
- <span data-ttu-id="3b22c-165">この設定を省略した場合、.NET では ICU グローバリゼーション API が既定で使用されます。</span><span class="sxs-lookup"><span data-stu-id="3b22c-165">If you omit this setting, .NET uses ICU globalization APIs by default.</span></span> <span data-ttu-id="3b22c-166">これは、値を `false` に設定した場合と同じです。</span><span class="sxs-lookup"><span data-stu-id="3b22c-166">This is equivalent to setting the value to `false`.</span></span>
- <span data-ttu-id="3b22c-167">詳細については、「[グローバリゼーション API では Windows 上の ICU ライブラリが使用される](../compatibility/globalization/5.0/icu-globalization-api.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3b22c-167">For more information, see [Globalization APIs use ICU libraries on Windows](../compatibility/globalization/5.0/icu-globalization-api.md).</span></span>

| | <span data-ttu-id="3b22c-168">設定の名前</span><span class="sxs-lookup"><span data-stu-id="3b22c-168">Setting name</span></span> | <span data-ttu-id="3b22c-169">値</span><span class="sxs-lookup"><span data-stu-id="3b22c-169">Values</span></span> | <span data-ttu-id="3b22c-170">導入時期</span><span class="sxs-lookup"><span data-stu-id="3b22c-170">Introduced</span></span> |
| - | - | - | - |
| <span data-ttu-id="3b22c-171">**runtimeconfig.json**</span><span class="sxs-lookup"><span data-stu-id="3b22c-171">**runtimeconfig.json**</span></span> | `System.Globalization.UseNls` | <span data-ttu-id="3b22c-172">`false` - ICU グローバリゼーション API を使用します</span><span class="sxs-lookup"><span data-stu-id="3b22c-172">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="3b22c-173">`true` - NLS グローバリゼーション API を使用します</span><span class="sxs-lookup"><span data-stu-id="3b22c-173">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="3b22c-174">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="3b22c-174">.NET 5.0</span></span> |
| <span data-ttu-id="3b22c-175">**環境変数**</span><span class="sxs-lookup"><span data-stu-id="3b22c-175">**Environment variable**</span></span> | `DOTNET_SYSTEM_GLOBALIZATION_USENLS` | <span data-ttu-id="3b22c-176">`false` - ICU グローバリゼーション API を使用します</span><span class="sxs-lookup"><span data-stu-id="3b22c-176">`false` - Use ICU globalization APIs</span></span><br/><span data-ttu-id="3b22c-177">`true` - NLS グローバリゼーション API を使用します</span><span class="sxs-lookup"><span data-stu-id="3b22c-177">`true` - Use NLS globalization APIs</span></span> | <span data-ttu-id="3b22c-178">.NET 5.0</span><span class="sxs-lookup"><span data-stu-id="3b22c-178">.NET 5.0</span></span> |
