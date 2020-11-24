---
title: 自動実装するプロパティを使用して簡易クラスを実装する方法 - C# プログラミング ガイド
description: 自動実装プロパティのカプセル化を行う、変更できない簡易クラスを C# で作成する方法について説明します。 実装方法は 2 つあります。
ms.date: 07/20/2015
helpviewer_keywords:
- auto-implemented properties [C#]
- properties [C#], auto-implemented
ms.topic: how-to
ms.custom: contperfq2
ms.assetid: 1dc5a8ad-a4f7-4f32-8506-3fc6d8c8bfed
ms.openlocfilehash: 39e191ce3b113b483fe93d70a0cadf02a7bee915
ms.sourcegitcommit: 30e9e11dfd90112b8eec6406186ba3533f21eba1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2020
ms.locfileid: "95099375"
---
# <a name="how-to-implement-a-lightweight-class-with-auto-implemented-properties-c-programming-guide"></a><span data-ttu-id="62eea-104">自動実装するプロパティを使用して簡易クラスを実装する方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="62eea-104">How to implement a lightweight class with auto-implemented properties (C# Programming Guide)</span></span>

<span data-ttu-id="62eea-105">この例では、一連の自動実装プロパティのカプセル化のみを行う、変更できない簡易クラスの作成方法を示します。</span><span class="sxs-lookup"><span data-stu-id="62eea-105">This example shows how to create an immutable lightweight class that serves only to encapsulate a set of auto-implemented properties.</span></span> <span data-ttu-id="62eea-106">参照型のセマンティクスを使用する必要がある場合は、構造体ではなく次のようなコンストラクトを使用します。</span><span class="sxs-lookup"><span data-stu-id="62eea-106">Use this kind of construct instead of a struct when you must use reference type semantics.</span></span>

<span data-ttu-id="62eea-107">変更できないプロパティの作成方法は 2 つあります。</span><span class="sxs-lookup"><span data-stu-id="62eea-107">You can make an immutable property in two ways:</span></span>

- <span data-ttu-id="62eea-108">[set](../../language-reference/keywords/set.md) アクセサーは、[private](../../language-reference/keywords/private.md) として宣言することができます。</span><span class="sxs-lookup"><span data-stu-id="62eea-108">You can declare the [set](../../language-reference/keywords/set.md) accessor to be [private](../../language-reference/keywords/private.md).</span></span>  <span data-ttu-id="62eea-109">プロパティは型の中のみで設定可能で、コンシューマーは変更できません。</span><span class="sxs-lookup"><span data-stu-id="62eea-109">The property is only settable within the type, but it is immutable to consumers.</span></span>

  <span data-ttu-id="62eea-110">`set` アクセサーを private で宣言した場合、オブジェクト初期化子を使用してプロパティを初期化することはできません。</span><span class="sxs-lookup"><span data-stu-id="62eea-110">When you declare a private `set` accessor, you cannot use an object initializer to initialize the property.</span></span> <span data-ttu-id="62eea-111">コンストラクターまたはファクトリ メソッドを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="62eea-111">You must use a constructor or a factory method.</span></span>
- <span data-ttu-id="62eea-112">[get](../../language-reference/keywords/get.md) アクセサーのみを宣言し、その型のコンストラクターを除くすべての場所でプロパティを変更できないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="62eea-112">You can declare only the [get](../../language-reference/keywords/get.md) accessor, which makes the property immutable everywhere except in the type's constructor.</span></span>

<span data-ttu-id="62eea-113">次の例では、get アクセサーのみを持つプロパティが、get と private set を持つプロパティとどのように異なるかを示しています。</span><span class="sxs-lookup"><span data-stu-id="62eea-113">The following example shows how a property with only get accessor differs than one with get and private set.</span></span>

```csharp
class Contact
{
    public string Name { get; }
    public string Address { get; private set; }

    public Contact(string contactName, string contactAddress)
    {
        // Both properties are accessible in the constructor.
        Name = contactName;
        Address = contactAddress;
    }

    // Name isn't assignable here. This will generate a compile error.
    //public void ChangeName(string newName) => Name = newName;

    // Address is assignable here.
    public void ChangeAddress(string newAddress) => Address = newAddress
}
```

## <a name="example"></a><span data-ttu-id="62eea-114">例</span><span class="sxs-lookup"><span data-stu-id="62eea-114">Example</span></span>

<span data-ttu-id="62eea-115">次の例は、自動実装プロパティを持つ変更できないクラスを実装する 2 つの方法を示します。</span><span class="sxs-lookup"><span data-stu-id="62eea-115">The following example shows two ways to implement an immutable class that has auto-implemented properties.</span></span> <span data-ttu-id="62eea-116">それぞれの方法では、プロパティの 1 つを private `set` で、1 つを `get` のみで宣言します。</span><span class="sxs-lookup"><span data-stu-id="62eea-116">Each way declares one of the properties with a private `set` and one of the properties with a `get` only.</span></span>  <span data-ttu-id="62eea-117">最初のクラスはプロパティの初期化にコンストラクターのみを使用しますが、2 番目のクラスは、コンストラクターを呼び出す静的ファクトリ メソッドを使用します。</span><span class="sxs-lookup"><span data-stu-id="62eea-117">The first class uses a constructor only to initialize the properties, and the second class uses a static factory method that calls a constructor.</span></span>

```csharp
// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// constructor to initialize its properties.
class Contact
{
    // Read-only property.
    public string Name { get; }

    // Read-write property with a private set accessor.
    public string Address { get; private set; }

    // Public constructor.
    public Contact(string contactName, string contactAddress)
    {
        Name = contactName;
        Address = contactAddress;
    }
}

// This class is immutable. After an object is created,
// it cannot be modified from outside the class. It uses a
// static method and private constructor to initialize its properties.
public class Contact2
{
    // Read-write property with a private set accessor.
    public string Name { get; private set; }

    // Read-only property.
    public string Address { get; }

    // Private constructor.
    private Contact2(string contactName, string contactAddress)
    {
        Name = contactName;
        Address = contactAddress;
    }

    // Public factory method.
    public static Contact2 CreateContact(string name, string address)
    {
        return new Contact2(name, address);
    }
}

public class Program
{
    static void Main()
    {
        // Some simple data sources.
        string[] names = {"Terry Adams","Fadi Fakhouri", "Hanying Feng",
                            "Cesar Garcia", "Debra Garcia"};
        string[] addresses = {"123 Main St.", "345 Cypress Ave.", "678 1st Ave",
                                "12 108th St.", "89 E. 42nd St."};

        // Simple query to demonstrate object creation in select clause.
        // Create Contact objects by using a constructor.
        var query1 = from i in Enumerable.Range(0, 5)
                    select new Contact(names[i], addresses[i]);

        // List elements cannot be modified by client code.
        var list = query1.ToList();
        foreach (var contact in list)
        {
            Console.WriteLine("{0}, {1}", contact.Name, contact.Address);
        }

        // Create Contact2 objects by using a static factory method.
        var query2 = from i in Enumerable.Range(0, 5)
                        select Contact2.CreateContact(names[i], addresses[i]);

        // Console output is identical to query1.
        var list2 = query2.ToList();

        // List elements cannot be modified by client code.
        // CS0272:
        // list2[0].Name = "Eugene Zabokritski";

        // Keep the console open in debug mode.
        Console.WriteLine("Press any key to exit.");
        Console.ReadKey();
    }
}

/* Output:
    Terry Adams, 123 Main St.
    Fadi Fakhouri, 345 Cypress Ave.
    Hanying Feng, 678 1st Ave
    Cesar Garcia, 12 108th St.
    Debra Garcia, 89 E. 42nd St.
*/
```

<span data-ttu-id="62eea-118">コンパイラによって、各自動実装プロパティにバッキング フィールドが作成されます。</span><span class="sxs-lookup"><span data-stu-id="62eea-118">The compiler creates backing fields for each auto-implemented property.</span></span> <span data-ttu-id="62eea-119">このフィールドは、ソース コードから直接アクセスできません。</span><span class="sxs-lookup"><span data-stu-id="62eea-119">The fields are not accessible directly from source code.</span></span>

## <a name="see-also"></a><span data-ttu-id="62eea-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="62eea-120">See also</span></span>

- [<span data-ttu-id="62eea-121">プロパティ</span><span class="sxs-lookup"><span data-stu-id="62eea-121">Properties</span></span>](./properties.md)
- [<span data-ttu-id="62eea-122">struct</span><span class="sxs-lookup"><span data-stu-id="62eea-122">struct</span></span>](../../language-reference/builtin-types/struct.md)
- [<span data-ttu-id="62eea-123">オブジェクト初期化子とコレクション初期化子</span><span class="sxs-lookup"><span data-stu-id="62eea-123">Object and Collection Initializers</span></span>](./object-and-collection-initializers.md)
