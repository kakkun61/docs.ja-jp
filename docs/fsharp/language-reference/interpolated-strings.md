---
title: 挿入文字列
description: '挿入文字列について説明します。これは、F # の式を直接埋め込むことができる特殊な形式の文字列です。'
ms.date: 11/12/2020
ms.openlocfilehash: 8c552b44cea7d6c51ec333b6bdd4d407c6f10da7
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94829688"
---
# <a name="interpolated-strings"></a><span data-ttu-id="c09c7-103">挿入文字列</span><span class="sxs-lookup"><span data-stu-id="c09c7-103">Interpolated strings</span></span>

<span data-ttu-id="c09c7-104">挿入文字列は、F # の式をその中に埋め込むことができる [文字列](strings.md) です。</span><span class="sxs-lookup"><span data-stu-id="c09c7-104">Interpolated strings are [strings](strings.md) that allow you to embed F# expressions into them.</span></span> <span data-ttu-id="c09c7-105">これらは、値または式の結果に基づいて文字列の値が変更される可能性があるさまざまなシナリオで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="c09c7-105">They are helpful in a wide range of scenarios where the value of a string may change based on the result of a value or expression.</span></span>

## <a name="syntax"></a><span data-ttu-id="c09c7-106">構文</span><span class="sxs-lookup"><span data-stu-id="c09c7-106">Syntax</span></span>

```fsharp
$"string-text {expr}"
$"string-text %format-specifier{expr}"
$"""string-text {"embedded string literal"}"""
```

## <a name="remarks"></a><span data-ttu-id="c09c7-107">解説</span><span class="sxs-lookup"><span data-stu-id="c09c7-107">Remarks</span></span>

<span data-ttu-id="c09c7-108">補間文字列を使用すると、文字列リテラルの内部にコードを "穴" で記述できます。</span><span class="sxs-lookup"><span data-stu-id="c09c7-108">Interpolated strings let you write code in "holes" inside of a string literal.</span></span> <span data-ttu-id="c09c7-109">基本的な例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c09c7-109">Here's a basic example:</span></span>

```fsharp
let name = "Phillip"
let age = 30
printfn $"Name: {name}, Age: {age}"

printfn $"I think {3.0 + 0.14} is close to {System.Math.PI}!"
```

<span data-ttu-id="c09c7-110">かっこで囲まれた各ペアの内容は、 `{}` 任意の F # 式にすることができます。</span><span class="sxs-lookup"><span data-stu-id="c09c7-110">The contents in between each `{}` brace pair can be any F# expression.</span></span>

<span data-ttu-id="c09c7-111">中かっこのペアをエスケープするには `{}` 、次のように2つのペアを記述します。</span><span class="sxs-lookup"><span data-stu-id="c09c7-111">To escape a `{}` brace pair, write two of them like so:</span></span>

```fsharp
let str = $"A pair of braces: {{}}"
// "A pair of braces: {}"
```

## <a name="typed-interpolated-strings"></a><span data-ttu-id="c09c7-112">型指定された挿入文字列</span><span class="sxs-lookup"><span data-stu-id="c09c7-112">Typed interpolated strings</span></span>

<span data-ttu-id="c09c7-113">挿入文字列には、タイプセーフを適用する F # 書式指定子を含めることもできます。</span><span class="sxs-lookup"><span data-stu-id="c09c7-113">Interpolated strings can also have F# format specifiers to enforce type safety.</span></span>

```fsharp
let name = "Phillip"
let age = 30

printfn $"Name: %s{name}, Age: %d{age}"

// Error: type mismatch
printfn $"Name: %s{age}, Age: %d{name}"
```

<span data-ttu-id="c09c7-114">前の例では、コードは、がである必要がある値を誤って渡して `age` `name` います。その逆も同様です。</span><span class="sxs-lookup"><span data-stu-id="c09c7-114">In the previous example, the code mistakenly passes the `age` value where `name` should be, and vice/versa.</span></span> <span data-ttu-id="c09c7-115">挿入文字列では書式指定子が使用されるため、これは微妙なランタイムバグではなくコンパイルエラーになります。</span><span class="sxs-lookup"><span data-stu-id="c09c7-115">Because the interpolated strings use format specifiers, this is a compile error instead of a subtle runtime bug.</span></span>

<span data-ttu-id="c09c7-116">[プレーンテキスト形式](plaintext-formatting.md)でカバーされるすべての書式指定子は、挿入文字列内で有効です。</span><span class="sxs-lookup"><span data-stu-id="c09c7-116">All format specifiers covered in [plaintext formatting](plaintext-formatting.md) are valid inside of an interpolated string.</span></span>

## <a name="verbatim-interpolated-strings"></a><span data-ttu-id="c09c7-117">逐語的補間文字列</span><span class="sxs-lookup"><span data-stu-id="c09c7-117">Verbatim interpolated strings</span></span>

<span data-ttu-id="c09c7-118">F # では、文字列リテラルを埋め込むことができるように、三重引用符で逐語的補間文字列をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="c09c7-118">F# supports verbatim interpolated strings with triple quotes so that you can embed string literals.</span></span>

```fsharp
let age = 30

printfn $"""Name: {"Phillip"}, Age: %d{age}"""
```

## <a name="aligning-expressions-in-interpolated-strings"></a><span data-ttu-id="c09c7-119">挿入文字列での式の配置</span><span class="sxs-lookup"><span data-stu-id="c09c7-119">Aligning expressions in interpolated strings</span></span>

<span data-ttu-id="c09c7-120">には、挿入文字列内の式を左揃えまたは右揃えにすることができます。また、スペースの数を指定することもでき `|` ます。</span><span class="sxs-lookup"><span data-stu-id="c09c7-120">You can left-align or right-align expressions inside interpolated strings with `|` and a specification of how many spaces.</span></span> <span data-ttu-id="c09c7-121">次の補間文字列は、左と右の式をそれぞれ7つのスペースで左右に配置します。</span><span class="sxs-lookup"><span data-stu-id="c09c7-121">The following interpolated string aligns the left and right expressions to the left and right, respectively, by seven spaces.</span></span>

```fsharp
printfn $"""|{"Left",-7}|{"Right",7}|"""
// |Left   |  Right|
```

## <a name="interpolated-strings-and-formattablestring-formatting"></a><span data-ttu-id="c09c7-122">挿入文字列と `FormattableString` 書式設定</span><span class="sxs-lookup"><span data-stu-id="c09c7-122">Interpolated strings and `FormattableString` formatting</span></span>

<span data-ttu-id="c09c7-123">次の規則に従って書式設定を適用することもでき <xref:System.FormattableString> ます。</span><span class="sxs-lookup"><span data-stu-id="c09c7-123">You can also apply formatting that adheres to the rules for <xref:System.FormattableString>:</span></span>

```fsharp
let speedOfLight = 299792.458
printfn $"The speed of light is {speedOfLight:N3} km/s."
// "The speed of light is 299,792.458 km/s."
```

<span data-ttu-id="c09c7-124">また、補間文字列は、型の注釈を使用してとしてチェックされる型にすることもでき <xref:System.FormattableString> ます。</span><span class="sxs-lookup"><span data-stu-id="c09c7-124">Additionally, an interpolated string can also be type checked as a <xref:System.FormattableString> via a type annotation:</span></span>

```fsharp
let frmtStr = $"The speed of light is {speedOfLight:N3} km/s." : FormattableString
// Type: FormattableString
// The speed of light is 299,792.458 km/s.
```

<span data-ttu-id="c09c7-125">型の注釈は、挿入文字列式自体に存在する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c09c7-125">Note that the type annotation must be on the interpolated string expression itself.</span></span> <span data-ttu-id="c09c7-126">F # は、補間文字列をに暗黙的に変換しません <xref:System.FormattableString> 。</span><span class="sxs-lookup"><span data-stu-id="c09c7-126">F# does not implicitly convert an interpolated string into a <xref:System.FormattableString>.</span></span>

## <a name="see-also"></a><span data-ttu-id="c09c7-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="c09c7-127">See also</span></span>

* [<span data-ttu-id="c09c7-128">文字列</span><span class="sxs-lookup"><span data-stu-id="c09c7-128">Strings</span></span>](strings.md)
