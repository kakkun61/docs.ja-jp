---
title: プロパティ
description: C# のプロパティについて説明します。C# のプロパティには、検証、計算値、遅延評価、プロパティ変更通知の機能があります。
ms.technology: csharp-fundamentals
ms.date: 04/25/2018
ms.openlocfilehash: 5306650a10a3de0ff208f7c72c0ba520a527e746
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437941"
---
# <a name="properties"></a><span data-ttu-id="4bdd2-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="4bdd2-103">Properties</span></span>

<span data-ttu-id="4bdd2-104">C# のプロパティは、非常に優れた機能です。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-104">Properties are first class citizens in C#.</span></span> <span data-ttu-id="4bdd2-105">開発者は C# で定義されている構文を使用して、設計の意図を正確に表すコードを記述できます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-105">The language defines syntax that enables developers to write code that accurately expresses their design intent.</span></span>

<span data-ttu-id="4bdd2-106">プロパティは、アクセスされたときにはフィールドのように振る舞います。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-106">Properties behave like fields when they are accessed.</span></span>
<span data-ttu-id="4bdd2-107">ただし、フィールドとは異なり、プロパティの実装ではアクセサーを使用します。プロパティがアクセスされたときや値を割り当てられたときに実行されるステートメントをアクセサーで定義します。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-107">However, unlike fields, properties are implemented with accessors that define the statements executed when a property is accessed or assigned.</span></span>

## <a name="property-syntax"></a><span data-ttu-id="4bdd2-108">プロパティの構文</span><span class="sxs-lookup"><span data-stu-id="4bdd2-108">Property syntax</span></span>

<span data-ttu-id="4bdd2-109">プロパティの構文は、フィールドを自然に拡張したものです。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-109">The syntax for properties is a natural extension to fields.</span></span> <span data-ttu-id="4bdd2-110">フィールドで格納場所を定義します。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-110">A field defines a storage location:</span></span>

[!code-csharp[Person class with public fields](../../samples/snippets/csharp/properties/Person.cs#1)]

<span data-ttu-id="4bdd2-111">プロパティの定義には、プロパティの値を取得する `get` アクセサーとプロパティに値を割り当てる `set` アクセサーの宣言が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-111">A property definition contains declarations for a `get` and `set` accessor that retrieves and assigns the value of that property:</span></span>

[!code-csharp[Person class with public properties](../../samples/snippets/csharp/properties/Person.cs#2)]

<span data-ttu-id="4bdd2-112">上記の構文は "*自動プロパティ*" の構文です。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-112">The syntax shown above is the *auto property* syntax.</span></span> <span data-ttu-id="4bdd2-113">コンパイラによって、プロパティをバックアップするフィールドの格納場所が生成されます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-113">The compiler generates the storage location for the field that backs up the property.</span></span> <span data-ttu-id="4bdd2-114">また、`get` アクセサーと `set` アクセサーの本体もコンパイラによって実装されます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-114">The compiler also implements the body of the `get` and `set` accessors.</span></span>

<span data-ttu-id="4bdd2-115">場合によっては、その型の既定以外の値にプロパティを初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-115">Sometimes, you need to initialize a property to a value other than the default for its type.</span></span>  <span data-ttu-id="4bdd2-116">C# では、プロパティの右中かっこの後で値を設定することにより可能です。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-116">C# enables that by setting a value after the closing brace for the property.</span></span> <span data-ttu-id="4bdd2-117">`FirstName` プロパティの初期値は `null` より空の文字列の方がよい場合があります。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-117">You may prefer the initial value for the `FirstName` property to be the empty string rather than `null`.</span></span> <span data-ttu-id="4bdd2-118">その場合は次に示すように指定します。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-118">You would specify that as shown below:</span></span>

[!code-csharp[Person class with properties and initializer](../../samples/snippets/csharp/properties/Person.cs#3)]

<span data-ttu-id="4bdd2-119">この記事で後述するように、特定の初期化は読み取り専用プロパティに最も役に立ちます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-119">Specific initialization is most useful for read-only properties, as you'll see later in this article.</span></span>

<span data-ttu-id="4bdd2-120">格納場所は、下に示すように、開発者が定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-120">You can also define the storage yourself, as shown below:</span></span>

[!code-csharp[Person class with properties and backing field](../../samples/snippets/csharp/properties/Person.cs#4)]

<span data-ttu-id="4bdd2-121">プロパティの実装が 1 つの式の場合は、*式形式のメンバー* を get アクセス操作子または set アクセス操作子に使用できます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-121">When a property implementation is a single expression, you can use *expression-bodied members* for the getter or setter:</span></span>

[!code-csharp[Person class with properties and expression bodied getters and setters](../../samples/snippets/csharp/properties/Person.cs#5)]

<span data-ttu-id="4bdd2-122">この記事では、該当する箇所ではこの簡単な構文を使います。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-122">This simplified syntax will be used where applicable throughout this article.</span></span>

<span data-ttu-id="4bdd2-123">上に示したプロパティの定義は、読み取り/書き込みプロパティです。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-123">The property definition shown above is a read-write property.</span></span> <span data-ttu-id="4bdd2-124">set アクセサーの `value` に注目してください。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-124">Notice the keyword `value` in the set accessor.</span></span> <span data-ttu-id="4bdd2-125">`set` アクセサーには常に、`value` という名前のパラメーターが 1 つあります。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-125">The `set` accessor always has a single parameter named `value`.</span></span> <span data-ttu-id="4bdd2-126">`get` アクセサーは、プロパティの型に変換可能な値を返す必要があります (この例では `string`)。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-126">The `get` accessor must return a value that is convertible to the type of the property (`string` in this example).</span></span>

<span data-ttu-id="4bdd2-127">これが構文の基本です。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-127">That's the basics of the syntax.</span></span> <span data-ttu-id="4bdd2-128">さまざまな設計手法をサポートするバリエーションが多数あります。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-128">There are many different variations that support a variety of different design idioms.</span></span> <span data-ttu-id="4bdd2-129">これらを詳しく確認しながら、各種シナリオに応じた構文の選択肢を見てみましょう。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-129">Let's explore, and learn the syntax options for each.</span></span>

## <a name="scenarios"></a><span data-ttu-id="4bdd2-130">シナリオ</span><span class="sxs-lookup"><span data-stu-id="4bdd2-130">Scenarios</span></span>

<span data-ttu-id="4bdd2-131">ここまでに示した例は、検証が行われない読み取り/書き込みプロパティという、プロパティ定義の中でも単純なものでした。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-131">The examples above showed one of the simplest cases of property definition: a read-write property with no validation.</span></span> <span data-ttu-id="4bdd2-132">目的のコードを `get` アクセサーと `set` アクセサーで記述することで、さまざまなシナリオに対応できます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-132">By writing the code you want in the `get` and `set` accessors, you can create many different scenarios.</span></span>

### <a name="validation"></a><span data-ttu-id="4bdd2-133">検証</span><span class="sxs-lookup"><span data-stu-id="4bdd2-133">Validation</span></span>

<span data-ttu-id="4bdd2-134">`set` アクセサーにコードを記述すると、プロパティが表す値を常に有効な値にすることができます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-134">You can write code in the `set` accessor to ensure that the values represented by a property are always valid.</span></span> <span data-ttu-id="4bdd2-135">たとえば、`Person` クラスに設定されているルールの 1 つに、名前は無指定または空白文字にできないというものがあるとします。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-135">For example, suppose one rule for the `Person` class is that the name cannot be blank or white space.</span></span> <span data-ttu-id="4bdd2-136">これは次のように記述できます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-136">You would write that as follows:</span></span>

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#6)]

<span data-ttu-id="4bdd2-137">上記の例は、プロパティ セッターの検証の一部として `throw` 式を使用して簡略化できます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-137">The preceding example can be simplified by using a `throw` expression as part of the property setter validation:</span></span>

[!code-csharp[Validating property setters](../../samples/snippets/csharp/properties/Person.cs#7)]

<span data-ttu-id="4bdd2-138">上記の例では、名前を無指定または空白文字にしてはいけないというルールが強制的に適用されます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-138">The example above enforces the rule that the first name must not be blank or white space.</span></span> <span data-ttu-id="4bdd2-139">もし開発者が下のように指定すると、</span><span class="sxs-lookup"><span data-stu-id="4bdd2-139">If a developer writes</span></span>

```csharp
hero.FirstName = "";
```

<span data-ttu-id="4bdd2-140">この割り当てに対して `ArgumentException` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-140">That assignment throws an `ArgumentException`.</span></span> <span data-ttu-id="4bdd2-141">プロパティの set アクセサーの戻り値は void でなければならないため、例外をスローすることで set アクセサーにエラーを報告します。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-141">Because a property set accessor must have a void return type, you report errors in the set accessor by throwing an exception.</span></span>

<span data-ttu-id="4bdd2-142">この構文を拡張して、シナリオに必要なあらゆる要素に対応できます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-142">You can extend this same syntax to anything needed in your scenario.</span></span> <span data-ttu-id="4bdd2-143">たとえば、各種プロパティ間の関係をチェックしたり、外部条件に対して検証したりできます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-143">You can check the relationships between different properties, or validate against any external conditions.</span></span> <span data-ttu-id="4bdd2-144">C# で有効なステートメントは、すべてプロパティ アクセサーでも有効です。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-144">Any valid C# statements are valid in a property accessor.</span></span>

### <a name="read-only"></a><span data-ttu-id="4bdd2-145">読み取り専用</span><span class="sxs-lookup"><span data-stu-id="4bdd2-145">Read-only</span></span>

<span data-ttu-id="4bdd2-146">ここまでのプロパティ定義はすべて、パブリック アクセサーを持つ読み取り/書き込みプロパティでした。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-146">Up to this point, all the property definitions you have seen are read/write properties with public accessors.</span></span> <span data-ttu-id="4bdd2-147">これ以外にも、プロパティに有効なアクセシビリティがあります。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-147">That's not the only valid accessibility for properties.</span></span>
<span data-ttu-id="4bdd2-148">たとえば、読み取り専用プロパティを作成したり、set アクセサーと get アクセサーに異なるアクセシビリティを設定したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-148">You can create read-only properties, or give different accessibility to the set and get accessors.</span></span> <span data-ttu-id="4bdd2-149">具体例として、`Person` クラスで、クラス内の他のメソッドからのみ `FirstName` プロパティの値を変更できるようにしたい場合は、</span><span class="sxs-lookup"><span data-stu-id="4bdd2-149">Suppose that your `Person` class should only enable changing the value of the `FirstName` property from other methods in that class.</span></span> <span data-ttu-id="4bdd2-150">set アクセサーのアクセシビリティを `public` ではなく `private` に設定します。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-150">You could give the set accessor `private` accessibility instead of `public`:</span></span>

[!code-csharp[Using a private setter for a publicly readonly property](../../samples/snippets/csharp/properties/Person.cs#8)]

<span data-ttu-id="4bdd2-151">これで、`FirstName` プロパティにはどのコードからもアクセスできる一方で、値の割り当ては `Person` クラス内の他のコードからしかできなくなります。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-151">Now, the `FirstName` property can be accessed from any code, but it can only be assigned from other code in the `Person` class.</span></span>

<span data-ttu-id="4bdd2-152">制限を設定するアクセス修飾子を set アクセサーと get アクセサーのどちらか 1 つに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-152">You can add any restrictive access modifier to either the set or get accessors.</span></span> <span data-ttu-id="4bdd2-153">個々のアクセサーには、プロパティ定義のアクセス修飾子よりも制限が強いアクセス修飾子を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-153">Any access modifier you place on the individual accessor must be more limited than the access modifier on the property definition.</span></span> <span data-ttu-id="4bdd2-154">上記は、`FirstName` プロパティが `public` ですが set アクセサーが `private` であるため、有効です。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-154">The above is legal because the `FirstName` property is `public`, but the set accessor is `private`.</span></span> <span data-ttu-id="4bdd2-155">`public` なアクセサーを持つ `private` なプロパティを宣言することはできません。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-155">You could not declare a `private` property with a `public` accessor.</span></span> <span data-ttu-id="4bdd2-156">プロパティの宣言では、`protected`、`internal`、`protected internal`、`private` を宣言することもできます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-156">Property declarations can also be declared `protected`, `internal`, `protected internal`, or, even `private`.</span></span>

<span data-ttu-id="4bdd2-157">`get` アクセサーに制限の高い修飾子を設定することも有効です。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-157">It is also legal to place the more restrictive modifier on the `get` accessor.</span></span> <span data-ttu-id="4bdd2-158">たとえば、`public` なプロパティで、`get` アクセサーを `private` に制限できます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-158">For example, you could have a `public` property, but restrict the `get` accessor to `private`.</span></span> <span data-ttu-id="4bdd2-159">ただし、このようなシナリオは実際にはほとんどありません。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-159">That scenario is rarely done in practice.</span></span>

<span data-ttu-id="4bdd2-160">また、コンストラクターやプロパティの初期化子でのみ設定できるように、プロパティに対する変更を制限することもできます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-160">You can also restrict modifications to a property so that it can only be set in a constructor or a property initializer.</span></span> <span data-ttu-id="4bdd2-161">`Person` クラスを次のように変更することができます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-161">You can modify the `Person` class so as follows:</span></span>

[!code-csharp[A readonly auto implemented property](../../samples/snippets/csharp/properties/Person.cs#9)]

<span data-ttu-id="4bdd2-162">この機能は、読み取り専用プロパティとして公開されるコレクションを初期化する場合に最もよく使われます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-162">This feature is most commonly used for initializing collections that are exposed as read-only properties:</span></span>

```csharp
public class Measurements
{
    public ICollection<DataPoint> points { get; } = new List<DataPoint>();
}
```

### <a name="computed-properties"></a><span data-ttu-id="4bdd2-163">計算されたプロパティ</span><span class="sxs-lookup"><span data-stu-id="4bdd2-163">Computed properties</span></span>

<span data-ttu-id="4bdd2-164">プロパティが返す値は、メンバー フィールドの値でなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-164">A property does not need to simply return the value of a member field.</span></span> <span data-ttu-id="4bdd2-165">計算された値を返すプロパティを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-165">You can create properties that return a computed value.</span></span> <span data-ttu-id="4bdd2-166">姓と名を連結する計算をしてフルネームを返すように `Person` オブジェクトを拡張してみましょう。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-166">Let's expand the `Person` object to return the full name, computed by concatenating the first and last names:</span></span>

[!code-csharp[A computed property](../../samples/snippets/csharp/properties/Person.cs#10)]

<span data-ttu-id="4bdd2-167">上の例では、"[文字列補間](./language-reference/tokens/interpolated.md)" 機能を使用して、フルネームを表す書式設定された文字列を作成しています。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-167">The example above uses the [string interpolation](./language-reference/tokens/interpolated.md) feature to create the formatted string for the full name.</span></span>

<span data-ttu-id="4bdd2-168">*式形式のメンバー* を使用することもできます。式形式のメンバーを使用すると、計算された `FullName` プロパティを簡潔な方法で作成できます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-168">You can also use an *expression-bodied member*, which provides a more succinct way to create the computed `FullName` property:</span></span>

[!code-csharp[A computed property using an expression bodied member](../../samples/snippets/csharp/properties/Person.cs#11)]

<span data-ttu-id="4bdd2-169">*式形式のメンバー* では、式が 1 つだけ含まれたメソッドを定義する *ラムダ式* 構文を使用します。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-169">*Expression-bodied members* use the *lambda expression* syntax to define methods that contain a single expression.</span></span> <span data-ttu-id="4bdd2-170">ここでは、その式が Person オブジェクトのフルネームを返しています。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-170">Here, that expression returns the full name for the person object.</span></span>

### <a name="cached-evaluated-properties"></a><span data-ttu-id="4bdd2-171">キャッシュ済みの評価されたプロパティ</span><span class="sxs-lookup"><span data-stu-id="4bdd2-171">Cached evaluated properties</span></span>

<span data-ttu-id="4bdd2-172">計算されたプロパティの概念をストレージと組み合わせて、*キャッシュ済みの評価されたプロパティ* を作成できます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-172">You can mix the concept of a computed property with storage and create a *cached evaluated property*.</span></span>  <span data-ttu-id="4bdd2-173">たとえば、`FullName` プロパティを更新して、プロパティが最初にアクセスされたときに文字列が書式設定されるようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-173">For example, you could update the `FullName` property so that the string formatting only happened the first time it was accessed:</span></span>

[!code-csharp[Caching the value of a computed property](../../samples/snippets/csharp/properties/Person.cs#12)]

<span data-ttu-id="4bdd2-174">ただし、上記のコードにはバグが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-174">The above code contains a bug though.</span></span> <span data-ttu-id="4bdd2-175">コードによって `FirstName` プロパティと `LastName` プロパティのいずれかの値が更新されると、以前に評価された `fullName` フィールドは無効になります。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-175">If code updates the value of either the `FirstName` or `LastName` property, the previously evaluated `fullName` field is invalid.</span></span> <span data-ttu-id="4bdd2-176">`fullName` フィールドが再計算されるように、`FirstName` プロパティと `LastName` プロパティの `set` アクセサーを変更します。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-176">You modify the `set` accessors of the `FirstName` and `LastName` property so that the `fullName` field is calculated again:</span></span>

[!code-csharp[Invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#13)]

<span data-ttu-id="4bdd2-177">上の最終版では、必要になった場合にのみ `FullName` プロパティが評価されます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-177">This final version evaluates the `FullName` property only when needed.</span></span>
<span data-ttu-id="4bdd2-178">以前に計算されたものが有効であれば、それが使用されます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-178">If the previously calculated version is valid, it's used.</span></span> <span data-ttu-id="4bdd2-179">状態が変化したことで、以前に計算されたバージョンが無効になると、再計算が行われます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-179">If another state change invalidates the previously calculated version, it will be recalculated.</span></span> <span data-ttu-id="4bdd2-180">このクラスを使用するにあたって、開発者は実装の詳細を知っている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-180">Developers that use this class do not need to know the details of the implementation.</span></span> <span data-ttu-id="4bdd2-181">内部で変化があっても Person オブジェクトの使用には影響しません。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-181">None of these internal changes affect the use of the Person object.</span></span> <span data-ttu-id="4bdd2-182">これが、プロパティを使用してオブジェクトのデータ メンバーを公開するする重要な利点です。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-182">That's the key reason for using Properties to expose data members of an object.</span></span>

### <a name="attaching-attributes-to-auto-implemented-properties"></a><span data-ttu-id="4bdd2-183">自動実装プロパティに属性をアタッチする</span><span class="sxs-lookup"><span data-stu-id="4bdd2-183">Attaching attributes to auto-implemented properties</span></span>

<span data-ttu-id="4bdd2-184">C# 7.3 以降、自動実装プロパティのコンパイラの生成したバッキング フィールドにフィールド属性をアタッチできるようになりました。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-184">Beginning with C# 7.3, field attributes can be attached to the compiler generated backing field in auto-implemented properties.</span></span> <span data-ttu-id="4bdd2-185">たとえば、一意の整数 `Id` プロパティを追加する `Person` クラスのリビジョンについて考えてみましょう。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-185">For example, consider a revision to the `Person` class that adds a unique integer `Id` property.</span></span>
<span data-ttu-id="4bdd2-186">自動実装プロパティを使用して `Id` プロパティを記述しますが、この設計では `Id` プロパティの永続化を呼び出しません。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-186">You write the `Id` property using an auto-implemented property, but your design does not call for persisting the `Id` property.</span></span> <span data-ttu-id="4bdd2-187"><xref:System.NonSerializedAttribute> は、プロパティではなく、フィールドにのみアタッチすることができます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-187">The <xref:System.NonSerializedAttribute> can only be attached to fields, not properties.</span></span> <span data-ttu-id="4bdd2-188">次の例のように、属性に対して `field:` 指定子を使用して `Id` プロパティのバッキング フィールドに <xref:System.NonSerializedAttribute> をアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-188">You can attach the <xref:System.NonSerializedAttribute> to the backing field for the `Id` property by using the `field:` specifier on the attribute, as shown in the following example:</span></span>

[!code-csharp[Attaching attributes to a backing field](../../samples/snippets/csharp/properties/Person.cs#14)]

<span data-ttu-id="4bdd2-189">この手法は、自動実装プロパティのバッキング フィールドにアタッチする任意の属性に利用できます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-189">This technique works for any attribute you attach to the backing field on the auto-implemented property.</span></span>

### <a name="implementing-inotifypropertychanged"></a><span data-ttu-id="4bdd2-190">INotifyPropertyChanged を実装する</span><span class="sxs-lookup"><span data-stu-id="4bdd2-190">Implementing INotifyPropertyChanged</span></span>

<span data-ttu-id="4bdd2-191">プロパティ アクセサーでコードを記述する必要があるシナリオとして、値が変更されたことをデータ バインディング クライアントに通知するための <xref:System.ComponentModel.INotifyPropertyChanged> インターフェイスのサポートというものもあります。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-191">A final scenario where you need to write code in a property accessor is to support the <xref:System.ComponentModel.INotifyPropertyChanged> interface used to notify data binding clients that a value has changed.</span></span> <span data-ttu-id="4bdd2-192">プロパティの値が変更されると、オブジェクトはその変更を示す <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> イベントを発生させます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-192">When the value of a property changes, the object raises the <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged?displayProperty=nameWithType> event to indicate the change.</span></span> <span data-ttu-id="4bdd2-193">データ バインディング ライブラリは、その変更に基づいて表示要素を更新します。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-193">The data binding libraries, in turn, update display elements based on that change.</span></span> <span data-ttu-id="4bdd2-194">下のコードは、この Person クラスの `FirstName` プロパティに `INotifyPropertyChanged` を実装する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-194">The code below shows how you would implement `INotifyPropertyChanged` for the `FirstName` property of this person class.</span></span>

[!code-csharp[invalidating the cache correctly](../../samples/snippets/csharp/properties/Person.cs#15)]

<span data-ttu-id="4bdd2-195">`?.` は "*null 条件演算子*" と呼ばれる演算子です。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-195">The `?.` operator is called the *null conditional operator*.</span></span> <span data-ttu-id="4bdd2-196">演算子の右側を評価する前に、null 参照がないかをチェックします。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-196">It checks for a null reference before evaluating the right side of the operator.</span></span> <span data-ttu-id="4bdd2-197">チェックの結果、`PropertyChanged` イベントに対するサブスクライバーがない場合は、イベントを発生させるコードは実行されません。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-197">The end result is that if there are no subscribers to the `PropertyChanged` event, the code to raise the event doesn't execute.</span></span> <span data-ttu-id="4bdd2-198">その場合、評価は行われず `NullReferenceException` がスローされます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-198">It would throw a `NullReferenceException` without this check in that case.</span></span> <span data-ttu-id="4bdd2-199">詳細については、「[`events`](events-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-199">For more information, see [`events`](events-overview.md).</span></span> <span data-ttu-id="4bdd2-200">上記の例では、新たに `nameof` という演算子を使用して、記号としてのプロパティ名を文字列に変換しています。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-200">This example also uses the new `nameof` operator to convert from the property name symbol to its text representation.</span></span>
<span data-ttu-id="4bdd2-201">`nameof` を使用すると、プロパティ名にタイプミスが含まれるというエラーを減らすことができます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-201">Using `nameof` can reduce errors where you have mistyped the name of the property.</span></span>

<span data-ttu-id="4bdd2-202"><xref:System.ComponentModel.INotifyPropertyChanged> の実装も、アクセサーでコードを記述することで目的のシナリオをサポートできるケースの一例です。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-202">Again, implementing <xref:System.ComponentModel.INotifyPropertyChanged> is an example of a case where you can write code in your accessors to support the scenarios you need.</span></span>

## <a name="summing-up"></a><span data-ttu-id="4bdd2-203">要約</span><span class="sxs-lookup"><span data-stu-id="4bdd2-203">Summing up</span></span>

<span data-ttu-id="4bdd2-204">プロパティは、クラスまたはオブジェクトに含まれた一種のスマート フィールドです。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-204">Properties are a form of smart fields in a class or object.</span></span> <span data-ttu-id="4bdd2-205">オブジェクトの外部からは、オブジェクト内にあるフィールドのように見えます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-205">From outside the object, they appear like fields in the object.</span></span> <span data-ttu-id="4bdd2-206">一方、プロパティは、C# の機能をどれでも自由に使用して実装できます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-206">However, properties can be implemented using the full palette of C# functionality.</span></span>
<span data-ttu-id="4bdd2-207">検証、各種アクセシビリティ、遅延評価など、目的のシナリオで必要となる要素はすべて提供できます。</span><span class="sxs-lookup"><span data-stu-id="4bdd2-207">You can provide validation, different accessibility, lazy evaluation, or any requirements your scenarios need.</span></span>
