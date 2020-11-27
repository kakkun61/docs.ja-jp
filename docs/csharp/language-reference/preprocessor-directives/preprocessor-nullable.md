---
description: '#Null 許容 - C# リファレンス'
title: '#Null 許容 - C# リファレンス'
ms.date: 11/18/2020
f1_keywords:
- '#nullable'
helpviewer_keywords:
- '#nullable directive [C#]'
ms.openlocfilehash: 4c114a09f29769fcc824bcdabdc1d523e33f199d
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099447"
---
# <a name="nullable-c-reference"></a><span data-ttu-id="a50eb-103">#nullable - C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="a50eb-103">#nullable (C# Reference)</span></span>

<span data-ttu-id="a50eb-104">`#nullable` プリプロセッサ ディレクティブは、"*Null 許容注釈コンテキスト*" と "*Null 許容警告コンテキスト*" を設定します。</span><span class="sxs-lookup"><span data-stu-id="a50eb-104">The `#nullable` preprocessor directive sets the *nullable annotation context* and *nullable warning context*.</span></span> <span data-ttu-id="a50eb-105">このディレクティブでは、Null 許容注釈の効果があるかどうか、および NULL 値の許容の警告が与えられるかどうかが制御されます。</span><span class="sxs-lookup"><span data-stu-id="a50eb-105">This directive controls whether nullable annotations have effect, and whether nullability warnings are given.</span></span> <span data-ttu-id="a50eb-106">各コンテキストは "*無効*" または "*有効*" になります。</span><span class="sxs-lookup"><span data-stu-id="a50eb-106">Each context is either *disabled* or *enabled*.</span></span>

<span data-ttu-id="a50eb-107">どちらのコンテキストもプロジェクト レベル (C# ソース コードの外部) で指定することができます。</span><span class="sxs-lookup"><span data-stu-id="a50eb-107">Both contexts can be specified at the project level (outside of C# source code).</span></span> <span data-ttu-id="a50eb-108">`#nullable` ディレクティブは、注釈と警告のコンテキストを制御し、プロジェクト レベルの設定よりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="a50eb-108">The `#nullable` directive controls the annotation and warning contexts and takes precedence over the project-level settings.</span></span> <span data-ttu-id="a50eb-109">ディレクティブは、別のディレクティブがそれをオーバーライドするか、ソース ファイルの末尾に達するまで、制御するコンテキストを設定します。</span><span class="sxs-lookup"><span data-stu-id="a50eb-109">A directive sets the context(s) it controls until another directive overrides it, or until the end of the source file.</span></span>

<span data-ttu-id="a50eb-110">ディレクティブの効果は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="a50eb-110">The effect of the directives is as follows:</span></span>

- <span data-ttu-id="a50eb-111">`#nullable disable`: Null 許容注釈および警告コンテキストを "*無効*" に設定します。</span><span class="sxs-lookup"><span data-stu-id="a50eb-111">`#nullable disable`: Sets the nullable annotation and warning contexts to *disabled*.</span></span>
- <span data-ttu-id="a50eb-112">`#nullable enable`: Null 許容注釈および警告コンテキストを "*有効*" に設定します。</span><span class="sxs-lookup"><span data-stu-id="a50eb-112">`#nullable enable`: Sets the nullable annotation and warning contexts to *enabled*.</span></span>
- <span data-ttu-id="a50eb-113">`#nullable restore`: Null 許容注釈および警告コンテキストを、プロジェクト設定に復元します。</span><span class="sxs-lookup"><span data-stu-id="a50eb-113">`#nullable restore`: Restores the nullable annotation and warning contexts to project settings.</span></span>
- <span data-ttu-id="a50eb-114">`#nullable disable annotations`: Null 許容注釈コンテキストを "*無効*" に設定します。</span><span class="sxs-lookup"><span data-stu-id="a50eb-114">`#nullable disable annotations`: Sets the nullable annotation context to *disabled*.</span></span>
- <span data-ttu-id="a50eb-115">`#nullable enable annotations`: Null 許容注釈コンテキストを "*有効*" に設定します。</span><span class="sxs-lookup"><span data-stu-id="a50eb-115">`#nullable enable annotations`: Sets the nullable annotation context to *enabled*.</span></span>
- <span data-ttu-id="a50eb-116">`#nullable restore annotations`: Null 許容注釈コンテキストを、プロジェクト設定に復元します。</span><span class="sxs-lookup"><span data-stu-id="a50eb-116">`#nullable restore annotations`: Restores the nullable annotation context to project settings.</span></span>
- <span data-ttu-id="a50eb-117">`#nullable disable warnings`: Null 許容警告コンテキストを "*無効*" に設定します。</span><span class="sxs-lookup"><span data-stu-id="a50eb-117">`#nullable disable warnings`: Sets the nullable warning context to *disabled*.</span></span>
- <span data-ttu-id="a50eb-118">`#nullable enable warnings`: Null 許容警告コンテキストを "*有効*" に設定します。</span><span class="sxs-lookup"><span data-stu-id="a50eb-118">`#nullable enable warnings`: Sets the nullable warning context to *enabled*.</span></span>
- <span data-ttu-id="a50eb-119">`#nullable restore warnings`: Null 許容警告コンテキストをプロジェクト設定に復元します。</span><span class="sxs-lookup"><span data-stu-id="a50eb-119">`#nullable restore warnings`: Restores the nullable warning context to project settings.</span></span>

## <a name="see-also"></a><span data-ttu-id="a50eb-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="a50eb-120">See also</span></span>

- [<span data-ttu-id="a50eb-121">C# リファレンス</span><span class="sxs-lookup"><span data-stu-id="a50eb-121">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a50eb-122">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="a50eb-122">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a50eb-123">C# プリプロセッサ ディレクティブ</span><span class="sxs-lookup"><span data-stu-id="a50eb-123">C# Preprocessor Directives</span></span>](./index.md)
