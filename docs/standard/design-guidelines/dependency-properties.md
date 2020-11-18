---
title: 依存関係プロパティ
ms.date: 10/22/2008
ms.assetid: 212cfb1e-cec4-4047-94a6-47209b387f6f
ms.openlocfilehash: c6cebd7c6c630af6a1a439b48faccad2aea74a91
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94821373"
---
# <a name="dependency-properties"></a><span data-ttu-id="5d56e-102">依存関係プロパティ</span><span class="sxs-lookup"><span data-stu-id="5d56e-102">Dependency Properties</span></span>
<span data-ttu-id="5d56e-103">依存関係プロパティ (DP) は、など、型の変数 (field) に格納するのではなく、プロパティストアにその値を格納する通常のプロパティです。</span><span class="sxs-lookup"><span data-stu-id="5d56e-103">A dependency property (DP) is a regular property that stores its value in a property store instead of storing it in a type variable (field), for example.</span></span>

 <span data-ttu-id="5d56e-104">アタッチされる依存関係プロパティは、静的な Get および Set メソッドとしてモデル化された依存関係プロパティの一種で、オブジェクトとそのコンテナーの間のリレーションシップ (コンテナー上のオブジェクトの位置など) を表す "プロパティ" を表し `Button` `Panel` ます。</span><span class="sxs-lookup"><span data-stu-id="5d56e-104">An attached dependency property is a kind of dependency property modeled as static Get and Set methods representing "properties" describing relationships between objects and their containers (e.g., the position of a `Button` object on a `Panel` container).</span></span>

 <span data-ttu-id="5d56e-105">スタイル設定、トリガー、データバインディング、アニメーション、動的リソース、継承などの WPF 機能をサポートするためにプロパティが必要な場合は、依存関係プロパティを指定✔️ます。</span><span class="sxs-lookup"><span data-stu-id="5d56e-105">✔️ DO provide the dependency properties, if you need the properties to support WPF features such as styling, triggers, data binding, animations, dynamic resources, and inheritance.</span></span>

## <a name="dependency-property-design"></a><span data-ttu-id="5d56e-106">依存関係プロパティのデザイン</span><span class="sxs-lookup"><span data-stu-id="5d56e-106">Dependency Property Design</span></span>
 <span data-ttu-id="5d56e-107"><xref:System.Windows.DependencyObject>依存関係プロパティを実装するときに、✔️、またはそのサブタイプの1つを継承します。</span><span class="sxs-lookup"><span data-stu-id="5d56e-107">✔️ DO inherit from <xref:System.Windows.DependencyObject>, or one of its subtypes, when implementing dependency properties.</span></span> <span data-ttu-id="5d56e-108">型は、プロパティストアの非常に効率的な実装を提供し、WPF のデータバインディングを自動的にサポートします。</span><span class="sxs-lookup"><span data-stu-id="5d56e-108">The type provides a very efficient implementation of a property store and automatically supports WPF data binding.</span></span>

 <span data-ttu-id="5d56e-109">✔️は、 <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> 依存関係プロパティごとにのインスタンスを格納する通常の CLR プロパティとパブリックの静的読み取り専用フィールドを提供します。</span><span class="sxs-lookup"><span data-stu-id="5d56e-109">✔️ DO provide a regular CLR property and public static read-only field storing an instance of <xref:System.Windows.DependencyProperty?displayProperty=nameWithType> for each dependency property.</span></span>

 <span data-ttu-id="5d56e-110">インスタンスメソッドとを呼び出すことによって、依存関係プロパティを実装✔️ <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="5d56e-110">✔️ DO implement dependency properties by calling instance methods <xref:System.Windows.DependencyObject.GetValue%2A?displayProperty=nameWithType> and <xref:System.Windows.DependencyObject.SetValue%2A?displayProperty=nameWithType>.</span></span>

 <span data-ttu-id="5d56e-111">✔️プロパティの名前を "suffixing" にして、依存関係プロパティの静的フィールドに名前を付けます。</span><span class="sxs-lookup"><span data-stu-id="5d56e-111">✔️ DO name the dependency property static field by suffixing the name of the property with "Property."</span></span>

 <span data-ttu-id="5d56e-112">❌ コードで依存関係プロパティの既定値を明示的に設定しないでください。代わりに、メタデータに設定します。</span><span class="sxs-lookup"><span data-stu-id="5d56e-112">❌ DO NOT set default values of dependency properties explicitly in code; set them in metadata instead.</span></span>

 <span data-ttu-id="5d56e-113">プロパティの既定値を明示的に設定した場合、スタイル設定などのいくつかの暗黙的な方法によってそのプロパティが設定されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="5d56e-113">If you set a property default explicitly, you might prevent that property from being set by some implicit means, such as a styling.</span></span>

 <span data-ttu-id="5d56e-114">❌ 静的フィールドにアクセスするために、標準コード以外のプロパティアクセサーにコードを配置しないでください。</span><span class="sxs-lookup"><span data-stu-id="5d56e-114">❌ DO NOT put code in the property accessors other than the standard code to access the static field.</span></span>

 <span data-ttu-id="5d56e-115">スタイル設定などの暗黙的な方法によってプロパティが設定されている場合、そのコードは実行されません。これは、スタイルが静的フィールドを直接使用するためです。</span><span class="sxs-lookup"><span data-stu-id="5d56e-115">That code won’t execute if the property is set by implicit means, such as a styling, because styling uses the static field directly.</span></span>

 <span data-ttu-id="5d56e-116">❌ セキュリティで保護されたデータを格納するために依存関係プロパティを使用しないでください。</span><span class="sxs-lookup"><span data-stu-id="5d56e-116">❌ DO NOT use dependency properties to store secure data.</span></span> <span data-ttu-id="5d56e-117">プライベート依存関係プロパティも、パブリックにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="5d56e-117">Even private dependency properties can be accessed publicly.</span></span>

## <a name="attached-dependency-property-design"></a><span data-ttu-id="5d56e-118">アタッチされた依存関係プロパティのデザイン</span><span class="sxs-lookup"><span data-stu-id="5d56e-118">Attached Dependency Property Design</span></span>
 <span data-ttu-id="5d56e-119">前のセクションで説明した依存関係プロパティは、宣言する型の組み込みプロパティを表します。たとえば、プロパティは、を `Text` 宣言するのプロパティです `TextButton` 。</span><span class="sxs-lookup"><span data-stu-id="5d56e-119">Dependency properties described in the preceding section represent intrinsic properties of the declaring type; for example, the `Text` property is a property of `TextButton`, which declares it.</span></span> <span data-ttu-id="5d56e-120">特別な種類の依存関係プロパティは、アタッチされる依存関係プロパティです。</span><span class="sxs-lookup"><span data-stu-id="5d56e-120">A special kind of dependency property is the attached dependency property.</span></span>

 <span data-ttu-id="5d56e-121">添付プロパティの従来の例として、 <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="5d56e-121">A classic example of an attached property is the <xref:System.Windows.Controls.Grid.Column%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="5d56e-122">プロパティは、ボタンの (グリッドではなく) 列の位置を表しますが、グリッドにボタンが含まれている場合にのみ関連し、グリッドによってボタンに "アタッチ" されます。</span><span class="sxs-lookup"><span data-stu-id="5d56e-122">The property represents Button’s (not Grid’s) column position, but it is only relevant if the Button is contained in a Grid, and so it's "attached" to Buttons by Grids.</span></span>

```xaml
<Grid>
    <Grid.ColumnDefinitions>
        <ColumnDefinition />
        <ColumnDefinition />
    </Grid.ColumnDefinitions>

    <Button Grid.Column="0">Click</Button>
    <Button Grid.Column="1">Clack</Button>
</Grid>
```

 <span data-ttu-id="5d56e-123">添付プロパティの定義は、通常の依存関係プロパティとほとんど同じように見えますが、アクセサーは静的な Get メソッドと Set メソッドによって表される点が異なります。</span><span class="sxs-lookup"><span data-stu-id="5d56e-123">The definition of an attached property looks mostly like that of a regular dependency property, except that the accessors are represented by static Get and Set methods:</span></span>

```csharp
public class Grid {

    public static int GetColumn(DependencyObject obj) {
        return (int)obj.GetValue(ColumnProperty);
    }

    public static void SetColumn(DependencyObject obj, int value) {
        obj.SetValue(ColumnProperty,value);
    }

    public static readonly DependencyProperty ColumnProperty =
        DependencyProperty.RegisterAttached(
            "Column",
            typeof(int),
            typeof(Grid)
    );
}
```

## <a name="dependency-property-validation"></a><span data-ttu-id="5d56e-124">依存関係プロパティの検証</span><span class="sxs-lookup"><span data-stu-id="5d56e-124">Dependency Property Validation</span></span>
 <span data-ttu-id="5d56e-125">プロパティは、多くの場合、検証と呼ばれるものを実装します。</span><span class="sxs-lookup"><span data-stu-id="5d56e-125">Properties often implement what is called validation.</span></span> <span data-ttu-id="5d56e-126">検証ロジックは、プロパティの値を変更しようとしたときに実行されます。</span><span class="sxs-lookup"><span data-stu-id="5d56e-126">Validation logic executes when an attempt is made to change the value of a property.</span></span>

 <span data-ttu-id="5d56e-127">残念ながら、依存関係プロパティのアクセサーに任意の検証コードを含めることはできません。</span><span class="sxs-lookup"><span data-stu-id="5d56e-127">Unfortunately dependency property accessors cannot contain arbitrary validation code.</span></span> <span data-ttu-id="5d56e-128">代わりに、プロパティの登録時に依存関係プロパティの検証ロジックを指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5d56e-128">Instead, dependency property validation logic needs to be specified during property registration.</span></span>

 <span data-ttu-id="5d56e-129">❌ プロパティのアクセサーに依存関係プロパティの検証ロジックを配置しないでください。</span><span class="sxs-lookup"><span data-stu-id="5d56e-129">❌ DO NOT put dependency property validation logic in the property’s accessors.</span></span> <span data-ttu-id="5d56e-130">代わりに、検証コールバックをメソッドに渡し `DependencyProperty.Register` ます。</span><span class="sxs-lookup"><span data-stu-id="5d56e-130">Instead, pass a validation callback to `DependencyProperty.Register` method.</span></span>

## <a name="dependency-property-change-notifications"></a><span data-ttu-id="5d56e-131">依存関係プロパティの変更通知</span><span class="sxs-lookup"><span data-stu-id="5d56e-131">Dependency Property Change Notifications</span></span>
 <span data-ttu-id="5d56e-132">❌ 依存関係プロパティのアクセサーには、変更通知ロジックを実装しないでください。</span><span class="sxs-lookup"><span data-stu-id="5d56e-132">❌ DO NOT implement change notification logic in dependency property accessors.</span></span> <span data-ttu-id="5d56e-133">依存関係プロパティには、に変更通知コールバックを提供することによって使用する必要がある、組み込みの変更通知機能があり <xref:System.Windows.PropertyMetadata> ます。</span><span class="sxs-lookup"><span data-stu-id="5d56e-133">Dependency properties have a built-in change notifications feature that must be used by supplying a change notification callback to the <xref:System.Windows.PropertyMetadata>.</span></span>

## <a name="dependency-property-value-coercion"></a><span data-ttu-id="5d56e-134">依存関係プロパティ値の強制変換</span><span class="sxs-lookup"><span data-stu-id="5d56e-134">Dependency Property Value Coercion</span></span>
 <span data-ttu-id="5d56e-135">プロパティの強制変換は、プロパティの set アクセス操作子に渡された値が setter によって変更されたときに、プロパティストアが実際に変更される前に行われます。</span><span class="sxs-lookup"><span data-stu-id="5d56e-135">Property coercion takes place when the value given to a property setter is modified by the setter before the property store is actually modified.</span></span>

 <span data-ttu-id="5d56e-136">❌ 依存関係プロパティアクセサーに強制型変換ロジックを実装しないでください。</span><span class="sxs-lookup"><span data-stu-id="5d56e-136">❌ DO NOT implement coercion logic in dependency property accessors.</span></span>

 <span data-ttu-id="5d56e-137">依存関係プロパティには組み込みの強制型変換機能があり、への強制変換コールバックを提供することによって使用でき `PropertyMetadata` ます。</span><span class="sxs-lookup"><span data-stu-id="5d56e-137">Dependency properties have a built-in coercion feature, and it can be used by supplying a coercion callback to the `PropertyMetadata`.</span></span>

 <span data-ttu-id="5d56e-138">*©2005、2009 Microsoft Corporation の部分。すべての権限が予約されています。*</span><span class="sxs-lookup"><span data-stu-id="5d56e-138">*Portions © 2005, 2009 Microsoft Corporation. All rights reserved.*</span></span>

 <span data-ttu-id="5d56e-139">*2008 年 10 月 22 日に Microsoft Windows Development シリーズの一部として、Addison-Wesley Professional によって発行された、Krzysztof Cwalina および Brad Abrams による「[Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)」 (フレームワーク デザイン ガイドライン: 再利用可能な .NET ライブラリの規則、用法、パターン、第 2 版) から Pearson Education, Inc. の許可を得て再印刷されています。*</span><span class="sxs-lookup"><span data-stu-id="5d56e-139">*Reprinted by permission of Pearson Education, Inc. from [Framework Design Guidelines: Conventions, Idioms, and Patterns for Reusable .NET Libraries, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) by Krzysztof Cwalina and Brad Abrams, published Oct 22, 2008 by Addison-Wesley Professional as part of the Microsoft Windows Development Series.*</span></span>

## <a name="see-also"></a><span data-ttu-id="5d56e-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="5d56e-140">See also</span></span>

- [<span data-ttu-id="5d56e-141">フレームワークデザインのガイドライン</span><span class="sxs-lookup"><span data-stu-id="5d56e-141">Framework Design Guidelines</span></span>](index.md)
- [<span data-ttu-id="5d56e-142">一般的なデザインパターン</span><span class="sxs-lookup"><span data-stu-id="5d56e-142">Common Design Patterns</span></span>](common-design-patterns.md)
