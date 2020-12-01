---
ms.openlocfilehash: 394f2daebad7b6af94bee4d7876796e87fe8ab19
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032069"
---
### <a name="handling-corrupted-state-exceptions-is-not-supported"></a><span data-ttu-id="9944c-101">破損状態例外の処理がサポートされない</span><span class="sxs-lookup"><span data-stu-id="9944c-101">Handling corrupted state exceptions is not supported</span></span>

<span data-ttu-id="9944c-102">.NET Core ではプロセス破損状態例外の処理はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="9944c-102">Handling corrupted-process-state exceptions in .NET Core is not supported.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9944c-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="9944c-103">Change description</span></span>

<span data-ttu-id="9944c-104">以前は、マネージド コード例外ハンドラーにより (たとえば、C# の [try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) ステートメントを使用して)、プロセス破損状態例外をキャッチして処理することができました。</span><span class="sxs-lookup"><span data-stu-id="9944c-104">Previously, corrupted-process-state exceptions could be caught and handled by managed code exception handlers, for example, by using a [try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) statement in C#.</span></span>

<span data-ttu-id="9944c-105">.NET Core 1.0 以降では、プロセス破損状態例外をマネージド コードで処理することはできません。</span><span class="sxs-lookup"><span data-stu-id="9944c-105">Starting in .NET Core 1.0, corrupted-process-state exceptions cannot be handled by managed code.</span></span> <span data-ttu-id="9944c-106">共通言語ランタイムでは、プロセス破損状態例外がマネージド コードに提供されません。</span><span class="sxs-lookup"><span data-stu-id="9944c-106">The common language runtime doesn't deliver corrupted-process-state exceptions to managed code.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="9944c-107">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="9944c-107">Version introduced</span></span>

<span data-ttu-id="9944c-108">1</span><span class="sxs-lookup"><span data-stu-id="9944c-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9944c-109">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="9944c-109">Recommended action</span></span>

<span data-ttu-id="9944c-110">代わりに、そのような例外をもたらした状況に対処することで、プロセス破損状態例外を処理する必要がないようにします。</span><span class="sxs-lookup"><span data-stu-id="9944c-110">Avoid the need to handle corrupted-process-state exceptions by addressing the situations that lead to them instead.</span></span> <span data-ttu-id="9944c-111">プロセス破損状態例外をどうしても処理する必要がある場合は、C または C++ のコードで例外ハンドラーを記述します。</span><span class="sxs-lookup"><span data-stu-id="9944c-111">If it's absolutely necessary to handle corrupted-process-state exceptions, write the exception handler in C or C++ code.</span></span>

#### <a name="category"></a><span data-ttu-id="9944c-112">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="9944c-112">Category</span></span>

<span data-ttu-id="9944c-113">Core .NET ライブラリ</span><span class="sxs-lookup"><span data-stu-id="9944c-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9944c-114">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="9944c-114">Affected APIs</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName>
- [<span data-ttu-id="9944c-115">legacyCorruptedStateExceptionsPolicy 要素</span><span class="sxs-lookup"><span data-stu-id="9944c-115">legacyCorruptedStateExceptionsPolicy element</span></span>](~/docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)

<!--

#### Affected APIs

- `T:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute`

-->
