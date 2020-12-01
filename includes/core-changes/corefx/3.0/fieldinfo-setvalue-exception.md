---
ms.openlocfilehash: 02c9305a36f47dfaf0b1fa8d19b07cd2d34badae
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/25/2020
ms.locfileid: "96032116"
---
### <a name="fieldinfosetvalue-throws-exception-for-static-init-only-fields"></a><span data-ttu-id="d90b8-101">FieldInfo.SetValue で、静的な初期化専用フィールドに対する例外がスローされる</span><span class="sxs-lookup"><span data-stu-id="d90b8-101">FieldInfo.SetValue throws exception for static, init-only fields</span></span>

<span data-ttu-id="d90b8-102">.NET Core 3.0 以降、<xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> を呼び出して静的な <xref:System.Reflection.FieldAttributes.InitOnly> フィールドに値を設定しようとすると、例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d90b8-102">Starting in .NET Core 3.0, an exception is thrown when you attempt to set a value on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d90b8-103">変更の説明</span><span class="sxs-lookup"><span data-stu-id="d90b8-103">Change description</span></span>

<span data-ttu-id="d90b8-104">.NET Framework と、3.0 より前のバージョンの .NET Core では、定数である静的フィールドの初期化 ([C# では読み取り専用に](~/docs/csharp/language-reference/keywords/readonly.md)) した後、<xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName> を呼び出すことで値を設定できました。</span><span class="sxs-lookup"><span data-stu-id="d90b8-104">In .NET Framework and versions of .NET Core prior to 3.0, you could set the value of a static field that's constant after it is initialized ([readonly in C#](~/docs/csharp/language-reference/keywords/readonly.md)) by calling <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=fullName>.</span></span> <span data-ttu-id="d90b8-105">ただし、この方法でこのようなフィールドを設定すると、ターゲット フレームワークと最適化の設定に基づく動作を予測できなくなります。</span><span class="sxs-lookup"><span data-stu-id="d90b8-105">However, setting such a field in this way resulted in unpredictable behavior based on the target framework and optimization settings.</span></span>

<span data-ttu-id="d90b8-106">.NET Core 3.0 以降のバージョンでは、静的な <xref:System.Reflection.FieldAttributes.InitOnly> フィールドに対して <xref:System.Reflection.FieldInfo.SetValue%2A> を呼び出すと、<xref:System.FieldAccessException?displayProperty=nameWithType> 例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="d90b8-106">In .NET Core 3.0 and later versions, when you call <xref:System.Reflection.FieldInfo.SetValue%2A> on a static, <xref:System.Reflection.FieldAttributes.InitOnly> field, a <xref:System.FieldAccessException?displayProperty=nameWithType> exception is thrown.</span></span>

> [!TIP]
> <span data-ttu-id="d90b8-107"><xref:System.Reflection.FieldAttributes.InitOnly> フィールドは、その宣言時またはそれを含んでいるクラスのコンストラクター内にのみ設定可能なフィールドです。</span><span class="sxs-lookup"><span data-stu-id="d90b8-107">An <xref:System.Reflection.FieldAttributes.InitOnly> field is one that can only be set at the time it's declared or in the constructor for the containing class.</span></span> <span data-ttu-id="d90b8-108">つまり、それは初期化された後は定数になります。</span><span class="sxs-lookup"><span data-stu-id="d90b8-108">In other words, it's constant after it is initialized.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d90b8-109">導入されたバージョン</span><span class="sxs-lookup"><span data-stu-id="d90b8-109">Version introduced</span></span>

<span data-ttu-id="d90b8-110">3.0</span><span class="sxs-lookup"><span data-stu-id="d90b8-110">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d90b8-111">推奨アクション</span><span class="sxs-lookup"><span data-stu-id="d90b8-111">Recommended action</span></span>

<span data-ttu-id="d90b8-112">静的コンストラクター内の静的な <xref:System.Reflection.FieldAttributes.InitOnly> フィールドを初期化します。</span><span class="sxs-lookup"><span data-stu-id="d90b8-112">Initialize static, <xref:System.Reflection.FieldAttributes.InitOnly> fields in a static constructor.</span></span> <span data-ttu-id="d90b8-113">これは、動的な型と非動的な型の両方に適用されます。</span><span class="sxs-lookup"><span data-stu-id="d90b8-113">This applies to both dynamic and non-dynamic types.</span></span>

<span data-ttu-id="d90b8-114">または、フィールドから <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> 属性を削除した後、<xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType> を呼び出すこともできます。</span><span class="sxs-lookup"><span data-stu-id="d90b8-114">Alternatively, you can remove the <xref:System.Reflection.FieldAttributes.InitOnly?displayProperty=nameWithType> attribute from the field, and then call <xref:System.Reflection.FieldInfo.SetValue%2A?displayProperty=nameWithType>.</span></span>

#### <a name="category"></a><span data-ttu-id="d90b8-115">カテゴリ</span><span class="sxs-lookup"><span data-stu-id="d90b8-115">Category</span></span>

<span data-ttu-id="d90b8-116">Core .NET ライブラリ</span><span class="sxs-lookup"><span data-stu-id="d90b8-116">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d90b8-117">影響を受ける API</span><span class="sxs-lookup"><span data-stu-id="d90b8-117">Affected APIs</span></span>

- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)?displayProperty=nameWithType>
- <xref:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object)`
- `M:System.Reflection.FieldInfo.SetValue(System.Object,System.Object,System.Reflection.BindingFlags,System.Reflection.Binder,System.Globalization.CultureInfo)`

-->
