---
title: プロパティ
description: 'オブジェクトに関連付けられている値を表すメンバーである F # プロパティについて説明します。'
ms.date: 05/16/2016
ms.openlocfilehash: a2a4fbfc88831dcb5cad7a2da701969b2e98b2e3
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2020
ms.locfileid: "96740199"
---
# <a name="properties"></a><span data-ttu-id="89386-103">プロパティ</span><span class="sxs-lookup"><span data-stu-id="89386-103">Properties</span></span>

<span data-ttu-id="89386-104">*プロパティ* は、オブジェクトに関連付けられた値を表すメンバーです。</span><span class="sxs-lookup"><span data-stu-id="89386-104">*Properties* are members that represent values associated with an object.</span></span>

## <a name="syntax"></a><span data-ttu-id="89386-105">構文</span><span class="sxs-lookup"><span data-stu-id="89386-105">Syntax</span></span>

```fsharp
// Property that has both get and set defined.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with [accessibility-modifier] get() =
    get-function-body
and [accessibility-modifier] set parameter =
    set-function-body

// Alternative syntax for a property that has get and set.
[ attributes-for-get ]
[ static ] member [accessibility-modifier-for-get] [self-identifier.]PropertyName =
    get-function-body
[ attributes-for-set ]
[ static ] member [accessibility-modifier-for-set] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName =
    get-function-body

// Alternative syntax for property that has get only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with get() =
    get-function-body

// Property that has set only.
[ attributes ]
[ static ] member [accessibility-modifier] [self-identifier.]PropertyName
with set parameter =
    set-function-body

// Automatically implemented properties.
[ attributes ]
[ static ] member val [accessibility-modifier] PropertyName = initialization-expression [ with get, set ]
```

## <a name="remarks"></a><span data-ttu-id="89386-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="89386-106">Remarks</span></span>

<span data-ttu-id="89386-107">プロパティは、オブジェクト指向プログラミングにおける "has a" リレーションシップを表します。これは、オブジェクトインスタンスに関連付けられているデータ、または静的なプロパティの場合は型を表します。</span><span class="sxs-lookup"><span data-stu-id="89386-107">Properties represent the "has a" relationship in object-oriented programming, representing data that is associated with object instances or, for static properties, with the type.</span></span>

<span data-ttu-id="89386-108">プロパティは、基になる値 (バッキングストアとも呼ばれます) を明示的に指定するかどうか、またはコンパイラがバッキングストアを自動的に生成できるようにするかどうかに応じて、2つの方法で宣言できます。</span><span class="sxs-lookup"><span data-stu-id="89386-108">You can declare properties in two ways, depending on whether you want to explicitly specify the underlying value (also called the backing store) for the property, or if you want to allow the compiler to automatically generate the backing store for you.</span></span> <span data-ttu-id="89386-109">一般に、プロパティが単純な実装であり、プロパティが値または変数の単純なラッパーである場合は、プロパティの自動的な方法を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="89386-109">Generally, you should use the more explicit way if the property has a non-trivial implementation and the automatic way when the property is just a simple wrapper for a value or variable.</span></span> <span data-ttu-id="89386-110">プロパティを明示的に宣言するには、キーワードを使用し `member` ます。</span><span class="sxs-lookup"><span data-stu-id="89386-110">To declare a property explicitly, use the `member` keyword.</span></span> <span data-ttu-id="89386-111">この宣言型の構文の後に、 `get` メソッドとメソッドを指定する構文、およびアクセサーを指定する構文が続き `set` ます。 *accessors*</span><span class="sxs-lookup"><span data-stu-id="89386-111">This declarative syntax is followed by the syntax that specifies the `get` and `set` methods, also named *accessors*.</span></span> <span data-ttu-id="89386-112">構文セクションに示されている明示的な構文のさまざまな形式は、読み取り/書き込み、読み取り専用、および書き込み専用のプロパティに使用されます。</span><span class="sxs-lookup"><span data-stu-id="89386-112">The various forms of the explicit syntax shown in the syntax section are used for read/write, read-only, and write-only properties.</span></span> <span data-ttu-id="89386-113">読み取り専用プロパティの場合は、メソッドのみを定義します `get` 。書き込み専用プロパティの場合は、メソッドのみを定義し `set` ます。</span><span class="sxs-lookup"><span data-stu-id="89386-113">For read-only properties, you define only a `get` method; for write-only properties, define only a `set` method.</span></span> <span data-ttu-id="89386-114">プロパティにアクセサーとアクセサーの両方がある場合は、 `get` `set` 次のコードに示すように、アクセサーごとに異なる属性とアクセシビリティ修飾子を指定できます。</span><span class="sxs-lookup"><span data-stu-id="89386-114">Note that when a property has both `get` and `set` accessors, the alternative syntax enables you to specify attributes and accessibility modifiers that are different for each accessor, as is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3201.fs)]

<span data-ttu-id="89386-115">メソッドとメソッドの両方を含む読み取り/書き込みプロパティの場合 `get` `set` 、との順序を逆にする `get` `set` ことができます。</span><span class="sxs-lookup"><span data-stu-id="89386-115">For read/write properties, which have both a `get` and `set` method, the order of `get` and `set` can be reversed.</span></span> <span data-ttu-id="89386-116">また、に対してのみ表示される構文と、を `get` 組み合わせた構文を使用する代わりに、に対してのみ表示される構文を指定することもでき `set` ます。</span><span class="sxs-lookup"><span data-stu-id="89386-116">Alternatively, you can provide the syntax shown for `get` only and the syntax shown for `set` only instead of using the combined syntax.</span></span> <span data-ttu-id="89386-117">これにより、個々の `get` またはメソッドが必要になることがある場合に、コメントを簡単にコメントアウトでき `set` ます。</span><span class="sxs-lookup"><span data-stu-id="89386-117">Doing this makes it easier to comment out the individual `get` or `set` method, if that is something you might need to do.</span></span> <span data-ttu-id="89386-118">この組み合わせの構文を使用する代わりに、次のコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="89386-118">This alternative to using the combined syntax is shown in the following code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3203.fs)]

<span data-ttu-id="89386-119">プロパティのデータを保持するプライベート値は、 *バッキングストア* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="89386-119">Private values that hold the data for properties are called *backing stores*.</span></span> <span data-ttu-id="89386-120">コンパイラによってバッキングストアが自動的に作成されるようにするには、キーワードを使用して `member val` 自己識別子を省略し、プロパティを初期化する式を指定します。</span><span class="sxs-lookup"><span data-stu-id="89386-120">To have the compiler create the backing store automatically, use the keywords `member val`, omit the self-identifier, then provide an expression to initialize the property.</span></span> <span data-ttu-id="89386-121">プロパティが変更可能である場合は、を含め `with get, set` ます。</span><span class="sxs-lookup"><span data-stu-id="89386-121">If the property is to be mutable, include `with get, set`.</span></span> <span data-ttu-id="89386-122">たとえば、次のクラス型には、自動的に実装される2つのプロパティが含まれています。</span><span class="sxs-lookup"><span data-stu-id="89386-122">For example, the following class type includes two automatically implemented properties.</span></span> <span data-ttu-id="89386-123">`Property1` は読み取り専用で、プライマリコンストラクターに指定された引数に初期化され、空の文字列に初期化される設定可能 `Property2` なプロパティです。</span><span class="sxs-lookup"><span data-stu-id="89386-123">`Property1` is read-only and is initialized to the argument provided to the primary constructor, and `Property2` is a settable property initialized to an empty string:</span></span>

```fsharp
type MyClass(property1 : int) =
member val Property1 = property1
member val Property2 = "" with get, set
```

<span data-ttu-id="89386-124">自動的に実装されるプロパティは、型の初期化の一部であるため、 `let` 型定義のバインディングやバインドと同様に、他のメンバー定義の前に含める必要があり `do` ます。</span><span class="sxs-lookup"><span data-stu-id="89386-124">Automatically implemented properties are part of the initialization of a type, so they must be included before any other member definitions, just like `let` bindings and `do` bindings in a type definition.</span></span> <span data-ttu-id="89386-125">自動的に実装されるプロパティを初期化する式は、初期化時にのみ評価され、プロパティがアクセスされるたびには評価されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="89386-125">Note that the expression that initializes an automatically implemented property is only evaluated upon initialization, and not every time the property is accessed.</span></span> <span data-ttu-id="89386-126">この動作は、明示的に実装されたプロパティの動作とは対照的です。</span><span class="sxs-lookup"><span data-stu-id="89386-126">This behavior is in contrast to the behavior of an explicitly implemented property.</span></span> <span data-ttu-id="89386-127">実際には、これらのプロパティを初期化するコードは、クラスのコンストラクターに追加されます。</span><span class="sxs-lookup"><span data-stu-id="89386-127">What this effectively means is that the code to initialize these properties is added to the constructor of a class.</span></span> <span data-ttu-id="89386-128">この違いを示す次のコードについて考えてみます。</span><span class="sxs-lookup"><span data-stu-id="89386-128">Consider the following code that shows this difference:</span></span>

```fsharp
type MyClass() =
    let random  = new System.Random()
    member val AutoProperty = random.Next() with get, set
    member this.ExplicitProperty = random.Next()

let class1 = new MyClass()

printfn $"class1.AutoProperty = %d{class1.AutoProperty}"
printfn $"class1.ExplicitProperty = %d{class1.ExplicitProperty}"
```

<span data-ttu-id="89386-129">**出力**</span><span class="sxs-lookup"><span data-stu-id="89386-129">**Output**</span></span>

```console
class1.AutoProperty = 1853799794
class1.AutoProperty = 1853799794
class1.ExplicitProperty = 978922705
class1.ExplicitProperty = 1131210765
```

<span data-ttu-id="89386-130">前のコードの出力は、AutoProperty の値が繰り返し呼び出されたときに変更されないことを示しています。一方、ExplicitProperty は、呼び出されるたびに変わります。</span><span class="sxs-lookup"><span data-stu-id="89386-130">The output of the preceding code shows that the value of AutoProperty is unchanged when called repeatedly, whereas the ExplicitProperty changes each time it is called.</span></span> <span data-ttu-id="89386-131">これは、明示的なプロパティの getter メソッドと同様に、自動的に実装されるプロパティの式は毎回評価されないことを示しています。</span><span class="sxs-lookup"><span data-stu-id="89386-131">This demonstrates that the expression for an automatically implemented property is not evaluated each time, as is the getter method for the explicit property.</span></span>

>[!WARNING]
><span data-ttu-id="89386-132">`System.Data.Entity`自動的に実装されるプロパティの初期化には適していない基底クラスのコンストラクターでカスタム操作を実行する Entity Framework () など、いくつかのライブラリがあります。</span><span class="sxs-lookup"><span data-stu-id="89386-132">There are some libraries, such as the Entity Framework (`System.Data.Entity`) that perform custom operations in base class constructors that don't work well with the initialization of automatically implemented properties.</span></span> <span data-ttu-id="89386-133">そのような場合は、明示的なプロパティを使用してみてください。</span><span class="sxs-lookup"><span data-stu-id="89386-133">In those cases, try using explicit properties.</span></span>

<span data-ttu-id="89386-134">プロパティは、クラス、構造体、判別共用体、レコード、インターフェイス、および型拡張のメンバーにすることができ、オブジェクト式で定義することもできます。</span><span class="sxs-lookup"><span data-stu-id="89386-134">Properties can be members of classes, structures, discriminated unions, records, interfaces, and type extensions and can also be defined in object expressions.</span></span>

<span data-ttu-id="89386-135">属性をプロパティに適用できます。</span><span class="sxs-lookup"><span data-stu-id="89386-135">Attributes can be applied to properties.</span></span> <span data-ttu-id="89386-136">属性をプロパティに適用するには、プロパティの前に別の行に属性を記述します。</span><span class="sxs-lookup"><span data-stu-id="89386-136">To apply an attribute to a property, write the attribute on a separate line before the property.</span></span> <span data-ttu-id="89386-137">詳細については、「[属性](../attributes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89386-137">For more information, see [Attributes](../attributes.md).</span></span>

<span data-ttu-id="89386-138">既定では、プロパティはパブリックです。</span><span class="sxs-lookup"><span data-stu-id="89386-138">By default, properties are public.</span></span> <span data-ttu-id="89386-139">アクセシビリティ修飾子は、プロパティにも適用できます。</span><span class="sxs-lookup"><span data-stu-id="89386-139">Accessibility modifiers can also be applied to properties.</span></span> <span data-ttu-id="89386-140">アクセシビリティ修飾子を適用するには、メソッドとメソッドの両方に適用することを意図している場合は、プロパティの名前の直前に追加します `get` `set` 。 `get` `set` 各アクセサーに異なるアクセシビリティが必要な場合は、キーワードとキーワードの前に追加します。</span><span class="sxs-lookup"><span data-stu-id="89386-140">To apply an accessibility modifier, add it immediately before the name of the property if it is meant to apply to both the `get` and `set` methods; add it before the `get` and `set` keywords if different accessibility is required for each accessor.</span></span> <span data-ttu-id="89386-141">*アクセシビリティ修飾子* は、、、のいずれかにすることができます `public` `private` `internal` 。</span><span class="sxs-lookup"><span data-stu-id="89386-141">The *accessibility-modifier* can be one of the following: `public`, `private`, `internal`.</span></span> <span data-ttu-id="89386-142">詳しくは、「[アクセス制御](../access-control.md)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="89386-142">For more information, see [Access Control](../access-control.md).</span></span>

<span data-ttu-id="89386-143">プロパティの実装は、プロパティがアクセスされるたびに実行されます。</span><span class="sxs-lookup"><span data-stu-id="89386-143">Property implementations are executed each time a property is accessed.</span></span>

## <a name="static-and-instance-properties"></a><span data-ttu-id="89386-144">静的プロパティとインスタンスプロパティ</span><span class="sxs-lookup"><span data-stu-id="89386-144">Static and Instance Properties</span></span>

<span data-ttu-id="89386-145">プロパティは、静的プロパティまたはインスタンスプロパティにすることができます。</span><span class="sxs-lookup"><span data-stu-id="89386-145">Properties can be static or instance properties.</span></span> <span data-ttu-id="89386-146">静的プロパティは、インスタンスなしで呼び出すことができ、個々のオブジェクトではなく、型に関連付けられている値に使用されます。</span><span class="sxs-lookup"><span data-stu-id="89386-146">Static properties can be invoked without an instance and are used for values associated with the type, not with individual objects.</span></span> <span data-ttu-id="89386-147">静的プロパティの場合は、自己識別子を省略します。</span><span class="sxs-lookup"><span data-stu-id="89386-147">For static properties, omit the self-identifier.</span></span> <span data-ttu-id="89386-148">インスタンスプロパティには、自己識別子が必要です。</span><span class="sxs-lookup"><span data-stu-id="89386-148">The self-identifier is required for instance properties.</span></span>

<span data-ttu-id="89386-149">次の静的プロパティ定義は、プロパティのバッキングストアである静的フィールドがあるシナリオに基づいてい `myStaticValue` ます。</span><span class="sxs-lookup"><span data-stu-id="89386-149">The following static property definition is based on a scenario in which you have a static field `myStaticValue` that is the backing store for the property.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3204.fs)]

<span data-ttu-id="89386-150">プロパティは配列に似ていますが、その場合は *インデックス付きプロパティ* と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="89386-150">Properties can also be array-like, in which case they are called *indexed properties*.</span></span> <span data-ttu-id="89386-151">詳細については、「 [インデックス付きプロパティ](indexed-properties.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89386-151">For more information, see [Indexed Properties](indexed-properties.md).</span></span>

## <a name="type-annotation-for-properties"></a><span data-ttu-id="89386-152">プロパティの型の注釈</span><span class="sxs-lookup"><span data-stu-id="89386-152">Type Annotation for Properties</span></span>

<span data-ttu-id="89386-153">多くの場合、コンパイラには、バッキングストアの型からプロパティの型を推論するのに十分な情報がありますが、型の注釈を追加することによって型を明示的に設定できます。</span><span class="sxs-lookup"><span data-stu-id="89386-153">In many cases, the compiler has enough information to infer the type of a property from the type of the backing store, but you can set the type explicitly by adding a type annotation.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3205.fs)]

## <a name="using-property-set-accessors"></a><span data-ttu-id="89386-154">プロパティセットアクセサーの使用</span><span class="sxs-lookup"><span data-stu-id="89386-154">Using Property set Accessors</span></span>

<span data-ttu-id="89386-155">アクセサーを提供するプロパティを設定する `set` には、演算子を使用し `<-` ます。</span><span class="sxs-lookup"><span data-stu-id="89386-155">You can set properties that provide `set` accessors by using the `<-` operator.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3206.fs)]

<span data-ttu-id="89386-156">出力は **20** です。</span><span class="sxs-lookup"><span data-stu-id="89386-156">The output is **20**.</span></span>

## <a name="abstract-properties"></a><span data-ttu-id="89386-157">抽象プロパティ</span><span class="sxs-lookup"><span data-stu-id="89386-157">Abstract Properties</span></span>

<span data-ttu-id="89386-158">プロパティは抽象にすることができます。</span><span class="sxs-lookup"><span data-stu-id="89386-158">Properties can be abstract.</span></span> <span data-ttu-id="89386-159">メソッドと同様に、は、 `abstract` プロパティに関連付けられた仮想ディスパッチがあることを意味します。</span><span class="sxs-lookup"><span data-stu-id="89386-159">As with methods, `abstract` just means that there is a virtual dispatch associated with the property.</span></span> <span data-ttu-id="89386-160">抽象プロパティは、完全に抽象的なものにすることができます。つまり、同じクラスに定義を指定する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="89386-160">Abstract properties can be truly abstract, that is, without a definition in the same class.</span></span> <span data-ttu-id="89386-161">そのため、このようなプロパティを含むクラスは抽象クラスです。</span><span class="sxs-lookup"><span data-stu-id="89386-161">The class that contains such a property is therefore an abstract class.</span></span> <span data-ttu-id="89386-162">また、抽象は、プロパティが仮想であることを示すだけで、その場合は定義が同じクラスに存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="89386-162">Alternatively, abstract can just mean that a property is virtual, and in that case, a definition must be present in the same class.</span></span> <span data-ttu-id="89386-163">抽象プロパティをプライベートにすることはできません。また、1つのアクセサーが抽象型である場合は、もう一方も abstract である必要があります。</span><span class="sxs-lookup"><span data-stu-id="89386-163">Note that abstract properties must not be private, and if one accessor is abstract, the other must also be abstract.</span></span> <span data-ttu-id="89386-164">抽象クラスの詳細については、「 [抽象クラス](../abstract-classes.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89386-164">For more information about abstract classes, see [Abstract Classes](../abstract-classes.md).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet3207.fs)]

## <a name="see-also"></a><span data-ttu-id="89386-165">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="89386-165">See also</span></span>

- [<span data-ttu-id="89386-166">メンバー</span><span class="sxs-lookup"><span data-stu-id="89386-166">Members</span></span>](index.md)
- [<span data-ttu-id="89386-167">メソッド</span><span class="sxs-lookup"><span data-stu-id="89386-167">Methods</span></span>](methods.md)
