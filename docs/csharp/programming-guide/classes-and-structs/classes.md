---
title: クラス - C# プログラミング ガイド
description: クラスの型と、クラスの型を作成する方法について説明します
ms.date: 08/21/2018
helpviewer_keywords:
- classes [C#]
- C# language, classes
ms.assetid: e8848524-7273-429f-8aba-c658d5eff5ad
ms.openlocfilehash: 8fa8d33ce9ece20a18c5c1542bc44cf569e9fa2e
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94440407"
---
# <a name="classes-c-programming-guide"></a><span data-ttu-id="4227f-103">クラス (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="4227f-103">Classes (C# Programming Guide)</span></span>

## <a name="reference-types"></a><span data-ttu-id="4227f-104">参照型</span><span class="sxs-lookup"><span data-stu-id="4227f-104">Reference types</span></span>  

<span data-ttu-id="4227f-105">[class](../../language-reference/keywords/class.md) として定義された型は、*参照型* です。</span><span class="sxs-lookup"><span data-stu-id="4227f-105">A type that is defined as a [class](../../language-reference/keywords/class.md) is a *reference type*.</span></span> <span data-ttu-id="4227f-106">実行時には、参照型の変数を宣言すると、[new](../../language-reference/operators/new-operator.md) 演算子を使用してクラスのインスタンスを明示的に作成するまで、変数には値 [null](../../language-reference/keywords/null.md) が格納されています。または、次の例に示すように、別の場所で作成された可能性がある、互換性のある型のオブジェクトを代入することもできます。</span><span class="sxs-lookup"><span data-stu-id="4227f-106">At run time, when you declare a variable of a reference type, the variable contains the value [null](../../language-reference/keywords/null.md) until you explicitly create an instance of the class by using the [new](../../language-reference/operators/new-operator.md) operator, or assign it an object of a compatible type that may have been created elsewhere, as shown in the following example:</span></span>

```csharp
//Declaring an object of type MyClass.
MyClass mc = new MyClass();

//Declaring another object of the same type, assigning it the value of the first object.
MyClass mc2 = mc;
```

<span data-ttu-id="4227f-107">オブジェクトが作成されると、その特定のオブジェクトに対してマネージド ヒープ上で十分なメモリが割り当てられ、変数にはそのオブジェクトの場所への参照のみが格納されます。</span><span class="sxs-lookup"><span data-stu-id="4227f-107">When the object is created, enough memory is allocated on the managed heap for that specific object, and the variable holds only a reference to the location of said object.</span></span> <span data-ttu-id="4227f-108">マネージド ヒープを使用する型では、メモリの割り当て時と、CLR の自動メモリ管理機能 ("*ガベージ コレクション*") による再要求時の両方についてオーバーヘッドが発生します。</span><span class="sxs-lookup"><span data-stu-id="4227f-108">Types on the managed heap require overhead both when they are allocated and when they are reclaimed by the automatic memory management functionality of the CLR, which is known as *garbage collection*.</span></span> <span data-ttu-id="4227f-109">しかし、ガベージ コレクションも高度に最適化されるため、ほとんどのシナリオでは、パフォーマンス上の問題が発生することはありません。</span><span class="sxs-lookup"><span data-stu-id="4227f-109">However, garbage collection is also highly optimized and in most scenarios, it does not create a performance issue.</span></span> <span data-ttu-id="4227f-110">ガベージ コレクションの詳細については、「[自動メモリ管理とガベージ コレクション](../../../standard/garbage-collection/fundamentals.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4227f-110">For more information about garbage collection, see [Automatic memory management and garbage collection](../../../standard/garbage-collection/fundamentals.md).</span></span>  
  
## <a name="declaring-classes"></a><span data-ttu-id="4227f-111">クラスの宣言</span><span class="sxs-lookup"><span data-stu-id="4227f-111">Declaring Classes</span></span>

 <span data-ttu-id="4227f-112">クラスは、次の例に示すように、[class](../../language-reference/keywords/class.md) キーワードと、その後に続ける一意の識別子を使用して宣言します。</span><span class="sxs-lookup"><span data-stu-id="4227f-112">Classes are declared by using the [class](../../language-reference/keywords/class.md) keyword followed by a unique identifier, as shown in the following example:</span></span>

 ```csharp
//[access modifier] - [class] - [identifier]
 public class Customer
 {
    // Fields, properties, methods and events go here...
 }
```

 <span data-ttu-id="4227f-113">`class` キーワードは、アクセス レベルの後に配置します。</span><span class="sxs-lookup"><span data-stu-id="4227f-113">The `class` keyword is preceded by the access level.</span></span> <span data-ttu-id="4227f-114">この例では、[public](../../language-reference/keywords/public.md) が使用されているため、誰でもこのクラスのインスタンスを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4227f-114">Because [public](../../language-reference/keywords/public.md) is used in this case, anyone can create instances of this class.</span></span> <span data-ttu-id="4227f-115">`class` キーワードの後にクラスの名前を記述します。</span><span class="sxs-lookup"><span data-stu-id="4227f-115">The name of the class follows the `class` keyword.</span></span> <span data-ttu-id="4227f-116">クラスの名前を、有効な C# の[識別子名](../inside-a-program/identifier-names.md)にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4227f-116">The name of the class must be a valid C# [identifier name](../inside-a-program/identifier-names.md).</span></span> <span data-ttu-id="4227f-117">定義の残りの部分がクラス本体で、そこで動作とデータを定義します。</span><span class="sxs-lookup"><span data-stu-id="4227f-117">The remainder of the definition is the class body, where the behavior and data are defined.</span></span> <span data-ttu-id="4227f-118">クラスのフィールド、プロパティ、メソッド、およびイベントは *クラス メンバー* と総称されます。</span><span class="sxs-lookup"><span data-stu-id="4227f-118">Fields, properties, methods, and events on a class are collectively referred to as *class members*.</span></span>  
  
## <a name="creating-objects"></a><span data-ttu-id="4227f-119">オブジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="4227f-119">Creating objects</span></span>

<span data-ttu-id="4227f-120">クラスとオブジェクトは、同義的に使用されることがありますが、これらは異なるものです。</span><span class="sxs-lookup"><span data-stu-id="4227f-120">Although they are sometimes used interchangeably, a class and an object are different things.</span></span> <span data-ttu-id="4227f-121">クラスはオブジェクトの型を定義しますが、オブジェクト自体ではありません。</span><span class="sxs-lookup"><span data-stu-id="4227f-121">A class defines a type of object, but it is not an object itself.</span></span> <span data-ttu-id="4227f-122">オブジェクトは、クラスに基づく具体的なエンティティであり、クラスのインスタンスと呼ばれることもあります。</span><span class="sxs-lookup"><span data-stu-id="4227f-122">An object is a concrete entity based on a class, and is sometimes referred to as an instance of a class.</span></span>  
  
 <span data-ttu-id="4227f-123">オブジェクトを作成するには、次のように、[new](../../language-reference/operators/new-operator.md) キーワードの後にオブジェクトの基になるクラスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="4227f-123">Objects can be created by using the [new](../../language-reference/operators/new-operator.md) keyword followed by the name of the class that the object will be based on, like this:</span></span>  

 ```csharp
 Customer object1 = new Customer();
 ```

 <span data-ttu-id="4227f-124">クラスのインスタンスを作成すると、そのオブジェクトへの参照が返されます。</span><span class="sxs-lookup"><span data-stu-id="4227f-124">When an instance of a class is created, a reference to the object is passed back to the programmer.</span></span> <span data-ttu-id="4227f-125">前の例の `object1` は、`Customer` に基づくオブジェクトへの参照です。</span><span class="sxs-lookup"><span data-stu-id="4227f-125">In the previous example, `object1` is a reference to an object that is based on `Customer`.</span></span> <span data-ttu-id="4227f-126">この参照は、新しいオブジェクトを参照しますが、オブジェクト データ自体を含みません。</span><span class="sxs-lookup"><span data-stu-id="4227f-126">This reference refers to the new object but does not contain the object data itself.</span></span> <span data-ttu-id="4227f-127">実際、オブジェクト参照は、オブジェクトを作成しなくても作成できます。</span><span class="sxs-lookup"><span data-stu-id="4227f-127">In fact, you can create an object reference without creating an object at all:</span></span>  

```csharp
 Customer object2;
```

 <span data-ttu-id="4227f-128">上のような、オブジェクトを参照しないオブジェクト参照を作成するのはお勧めしません。実行時にこのような参照を通じてオブジェクトへのアクセスを試みると失敗するからです。</span><span class="sxs-lookup"><span data-stu-id="4227f-128">We don't recommend creating object references such as this one that don't refer to an object because trying to access an object through such a reference will fail at run time.</span></span> <span data-ttu-id="4227f-129">ただし、新しいオブジェクトを作成するか、既存のオブジェクトを割り当てると、このような参照でオブジェクトを参照できるようになります。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4227f-129">However, such a reference can be made to refer to an object, either by creating a new object, or by assigning it an existing object, such as this:</span></span>  

 ```csharp
 Customer object3 = new Customer();
 Customer object4 = object3;
```
  
 <span data-ttu-id="4227f-130">上のコードでは、同じオブジェクトを参照する 2 つのオブジェクト参照が作成されます。</span><span class="sxs-lookup"><span data-stu-id="4227f-130">This code creates two object references that both refer to the same object.</span></span> <span data-ttu-id="4227f-131">そのため、`object3` を通じて行われたオブジェクトの変更は、後で `object4` を使用するときに反映されます。</span><span class="sxs-lookup"><span data-stu-id="4227f-131">Therefore, any changes to the object made through `object3` are reflected in subsequent uses of `object4`.</span></span> <span data-ttu-id="4227f-132">これは、クラスに基づくオブジェクトが参照によって参照されるからです。このためクラスは参照型と呼ばれています。</span><span class="sxs-lookup"><span data-stu-id="4227f-132">Because objects that are based on classes are referred to by reference, classes are known as reference types.</span></span>  
  
## <a name="class-inheritance"></a><span data-ttu-id="4227f-133">クラスの継承</span><span class="sxs-lookup"><span data-stu-id="4227f-133">Class inheritance</span></span>  

<span data-ttu-id="4227f-134">クラスは、オブジェクト指向プログラミングの基本的な特性である "*継承*" を完全にサポートします。</span><span class="sxs-lookup"><span data-stu-id="4227f-134">Classes fully support *inheritance*, a fundamental characteristic of object-oriented programming.</span></span> <span data-ttu-id="4227f-135">クラスを作成するときは、[sealed](../../language-reference/keywords/sealed.md) として定義されているものを除く、他のすべてのクラスから継承できます。また、作成したクラスから他のクラスを継承し、クラスの仮想メソッドをオーバーライドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="4227f-135">When you create a class, you can inherit from any other class that is not defined as [sealed](../../language-reference/keywords/sealed.md), and other classes can inherit from your class and override class virtual methods.</span></span> <span data-ttu-id="4227f-136">さらに、1 つまたは複数のインターフェイスを実装できます。</span><span class="sxs-lookup"><span data-stu-id="4227f-136">Furthermore, you can implement one or more interfaces.</span></span>

<span data-ttu-id="4227f-137">継承は、*派生* を使用して行われます。派生とは、データの動作の継承元である *基底クラス* を使用してクラスを宣言することを意味します。</span><span class="sxs-lookup"><span data-stu-id="4227f-137">Inheritance is accomplished by using a *derivation*, which means a class is declared by using a *base class* from which it inherits data and behavior.</span></span> <span data-ttu-id="4227f-138">基底クラスは、派生クラス名の後に、コロンと基底クラス名を追加して指定します。次に例を示します。</span><span class="sxs-lookup"><span data-stu-id="4227f-138">A base class is specified by appending a colon and the name of the base class following the derived class name, like this:</span></span>  

 ```csharp
 public class Manager : Employee
 {
     // Employee fields, properties, methods and events are inherited
     // New Manager fields, properties, methods and events go here...
 }
 ```

<span data-ttu-id="4227f-139">クラスで基底クラスを宣言している場合、基底クラスのすべてのメンバー (コンストラクター以外) が継承されます。</span><span class="sxs-lookup"><span data-stu-id="4227f-139">When a class declares a base class, it inherits all the members of the base class except the constructors.</span></span> <span data-ttu-id="4227f-140">詳細については、「[継承](inheritance.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4227f-140">For more information, see [Inheritance](inheritance.md).</span></span>
  
<span data-ttu-id="4227f-141">C++ と異なり、C# のクラスは 1 つの基底クラスから直接継承することしかできません。</span><span class="sxs-lookup"><span data-stu-id="4227f-141">Unlike C++, a class in C# can only directly inherit from one base class.</span></span> <span data-ttu-id="4227f-142">ただし、基底クラス自体が別のクラスを継承している場合があるため、1 つのクラスに複数の基底クラスが間接的に継承されることもあります。</span><span class="sxs-lookup"><span data-stu-id="4227f-142">However, because a base class may itself inherit from another class, a class may indirectly inherit multiple base classes.</span></span> <span data-ttu-id="4227f-143">さらに、クラスは 1 つまたは複数のインターフェイスを直接実装できます。</span><span class="sxs-lookup"><span data-stu-id="4227f-143">Furthermore, a class can directly implement one or more interfaces.</span></span> <span data-ttu-id="4227f-144">詳細については、「[インターフェイス](../interfaces/index.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4227f-144">For more information, see [Interfaces](../interfaces/index.md).</span></span>  
  
<span data-ttu-id="4227f-145">クラスは[抽象](../../language-reference/keywords/abstract.md)としても宣言できます。</span><span class="sxs-lookup"><span data-stu-id="4227f-145">A class can be declared [abstract](../../language-reference/keywords/abstract.md).</span></span> <span data-ttu-id="4227f-146">抽象クラスには、シグネチャ定義が存在し、実装は存在しない抽象メソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="4227f-146">An abstract class contains abstract methods that have a signature definition but no implementation.</span></span> <span data-ttu-id="4227f-147">抽象クラスはインスタンス化できません。</span><span class="sxs-lookup"><span data-stu-id="4227f-147">Abstract classes cannot be instantiated.</span></span> <span data-ttu-id="4227f-148">抽象クラスを使用するには、抽象メソッドを実装する派生クラスを介する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4227f-148">They can only be used through derived classes that implement the abstract methods.</span></span> <span data-ttu-id="4227f-149">これとは対照的に、[シール](../../language-reference/keywords/sealed.md) クラスは、他のクラスに派生させることはできません。</span><span class="sxs-lookup"><span data-stu-id="4227f-149">By contrast, a [sealed](../../language-reference/keywords/sealed.md) class does not allow other classes to derive from it.</span></span> <span data-ttu-id="4227f-150">詳細については、「[抽象クラスとシール クラス、およびクラス メンバー](abstract-and-sealed-classes-and-class-members.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4227f-150">For more information, see [Abstract and Sealed Classes and Class Members](abstract-and-sealed-classes-and-class-members.md).</span></span>  
  
<span data-ttu-id="4227f-151">クラス定義は、別々のソース ファイルに分割できます。</span><span class="sxs-lookup"><span data-stu-id="4227f-151">Class definitions can be split between different source files.</span></span> <span data-ttu-id="4227f-152">詳細については、「[部分クラスと部分メソッド](partial-classes-and-methods.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4227f-152">For more information, see [Partial Classes and Methods](partial-classes-and-methods.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4227f-153">例</span><span class="sxs-lookup"><span data-stu-id="4227f-153">Example</span></span>

<span data-ttu-id="4227f-154">次の例では、[自動実装プロパティ](auto-implemented-properties.md)、メソッド、およびコンストラクターという特殊なメソッドをそれぞれ 1 つずつ含むパブリック クラスを定義しています。</span><span class="sxs-lookup"><span data-stu-id="4227f-154">The following example defines a public class that contains an [auto-implemented property](auto-implemented-properties.md), a method, and a special method called a constructor.</span></span> <span data-ttu-id="4227f-155">詳しくは、[プロパティ](properties.md)、[メソッド](methods.md)、および[コンス トラクター](constructors.md)に関するトピックを参照してください。</span><span class="sxs-lookup"><span data-stu-id="4227f-155">For more information, see [Properties](properties.md), [Methods](methods.md), and [Constructors](constructors.md) topics.</span></span> <span data-ttu-id="4227f-156">このクラスのインスタンスは、`new` キーワードによってインスタンス化されます。</span><span class="sxs-lookup"><span data-stu-id="4227f-156">The instances of the class are then instantiated with the `new` keyword.</span></span>  
  
[!code-csharp[Class Example](~/samples/snippets/csharp/programming-guide/classes-and-structs/class-example.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="4227f-157">C# 言語仕様</span><span class="sxs-lookup"><span data-stu-id="4227f-157">C# Language Specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="4227f-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="4227f-158">See also</span></span>

- [<span data-ttu-id="4227f-159">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="4227f-159">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4227f-160">オブジェクト指向プログラミング</span><span class="sxs-lookup"><span data-stu-id="4227f-160">Object-Oriented Programming</span></span>](../../tutorials/intro-to-csharp/object-oriented-programming.md)
- [<span data-ttu-id="4227f-161">ポリモーフィズム</span><span class="sxs-lookup"><span data-stu-id="4227f-161">Polymorphism</span></span>](polymorphism.md)
- [<span data-ttu-id="4227f-162">識別子名</span><span class="sxs-lookup"><span data-stu-id="4227f-162">Identifier names</span></span>](../inside-a-program/identifier-names.md)
- [<span data-ttu-id="4227f-163">メンバー</span><span class="sxs-lookup"><span data-stu-id="4227f-163">Members</span></span>](members.md)
- [<span data-ttu-id="4227f-164">メソッド</span><span class="sxs-lookup"><span data-stu-id="4227f-164">Methods</span></span>](methods.md)
- [<span data-ttu-id="4227f-165">コンストラクター</span><span class="sxs-lookup"><span data-stu-id="4227f-165">Constructors</span></span>](constructors.md)
- [<span data-ttu-id="4227f-166">ファイナライザー</span><span class="sxs-lookup"><span data-stu-id="4227f-166">Finalizers</span></span>](destructors.md)
- [<span data-ttu-id="4227f-167">オブジェクト</span><span class="sxs-lookup"><span data-stu-id="4227f-167">Objects</span></span>](objects.md)
