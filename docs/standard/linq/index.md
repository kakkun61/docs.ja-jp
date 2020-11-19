---
title: LINQ の概要 - .NET
description: 統合言語クエリ (LINQ) では、言語レベルのクエリ機能と、表現力豊かな宣言コードの記述を可能にする高階関数 API が C# および Visual Basic に提供されます。
author: cartermp
ms.author: wiwagn
ms.date: 06/20/2016
dev_langs:
- csharp
- vb
ms.openlocfilehash: ed78082c97511a8dbcc48d413a75a46c9da906a9
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94825833"
---
# <a name="linq-overview"></a><span data-ttu-id="d7e5b-103">LINQ の概要</span><span class="sxs-lookup"><span data-stu-id="d7e5b-103">LINQ overview</span></span>

<span data-ttu-id="d7e5b-104">統合言語クエリ (LINQ) では、言語レベルのクエリ機能と、表現力豊かな宣言コードの記述を可能にする[高階関数](https://en.wikipedia.org/wiki/Higher-order_function) API が C# および Visual Basic に提供されます。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-104">Language-Integrated Query (LINQ) provides language-level querying capabilities, and a [higher-order function](https://en.wikipedia.org/wiki/Higher-order_function) API to C# and Visual Basic, that enable you to write expressive declarative code.</span></span>

## <a name="language-level-query-syntax"></a><span data-ttu-id="d7e5b-105">言語レベルのクエリ構文</span><span class="sxs-lookup"><span data-stu-id="d7e5b-105">Language-level query syntax</span></span>

<span data-ttu-id="d7e5b-106">こちらが言語レベルのクエリ構文です:</span><span class="sxs-lookup"><span data-stu-id="d7e5b-106">This is the language-level query syntax:</span></span>

```csharp
var linqExperts = from p in programmers
                  where p.IsNewToLINQ
                  select new LINQExpert(p);
```

```vb
Dim linqExperts = From p in programmers
                  Where p.IsNewToLINQ
                  Select New LINQExpert(p)
```

<span data-ttu-id="d7e5b-107">こちらが `IEnumerable<T>` API を使用した同じ例です:</span><span class="sxs-lookup"><span data-stu-id="d7e5b-107">This is the same example using the `IEnumerable<T>` API:</span></span>

```csharp
var linqExperts = programmers.Where(p => p.IsNewToLINQ)
                             .Select(p => new LINQExpert(p));
```

```vb
Dim linqExperts = programmers.Where(Function(p) p.IsNewToLINQ).
                             Select(Function(p) New LINQExpert(p))
```

## <a name="linq-is-expressive"></a><span data-ttu-id="d7e5b-108">LINQ は表現力が豊か</span><span class="sxs-lookup"><span data-stu-id="d7e5b-108">LINQ is expressive</span></span>

<span data-ttu-id="d7e5b-109">たとえば、ペットのリストはあるが、`RFID` 値で直接ペットにアクセスできる辞書に変換する必要があるとします。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-109">Imagine you have a list of pets, but want to convert it into a dictionary where you can access a pet directly by its `RFID` value.</span></span>

<span data-ttu-id="d7e5b-110">こちらが従来の命令型コードです:</span><span class="sxs-lookup"><span data-stu-id="d7e5b-110">This is traditional imperative code:</span></span>

```csharp
var petLookup = new Dictionary<int, Pet>();

foreach (var pet in pets)
{
    petLookup.Add(pet.RFID, pet);
}
```

```vb
Dim petLookup = New Dictionary(Of Integer, Pet)()

For Each pet in pets
    petLookup.Add(pet.RFID, pet)
Next
```

<span data-ttu-id="d7e5b-111">コードの目的は、新しい `Dictionary<int, Pet>` を作成し、ループを使用して追加することではなく、既存のリストを辞書に変換することです。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-111">The intention behind the code isn't to create a new `Dictionary<int, Pet>` and add to it via a loop, it's to convert an existing list into a dictionary!</span></span> <span data-ttu-id="d7e5b-112">LINQ ではこの目的が維持されますが、命令型コードでは維持されません。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-112">LINQ preserves the intention whereas the imperative code doesn't.</span></span>

<span data-ttu-id="d7e5b-113">こちらが同等の LINQ 式です:</span><span class="sxs-lookup"><span data-stu-id="d7e5b-113">This is the equivalent LINQ expression:</span></span>

```csharp
var petLookup = pets.ToDictionary(pet => pet.RFID);
```

```vb
Dim petLookup = pets.ToDictionary(Function(pet) pet.RFID)
```

<span data-ttu-id="d7e5b-114">プログラマーとして考えると、目的とコードを同等にするため、LINQ を使用するコードのほうが有益です。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-114">The code using LINQ is valuable because it evens the playing field between intent and code when reasoning as a programmer.</span></span> <span data-ttu-id="d7e5b-115">また、コードが簡潔であるという利点があります。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-115">Another bonus is code brevity.</span></span> <span data-ttu-id="d7e5b-116">上記のように、コードベースの大部分を 3 分の 1 に減らせることを考えれば、</span><span class="sxs-lookup"><span data-stu-id="d7e5b-116">Imagine reducing large portions of a codebase by 1/3 as done above.</span></span> <span data-ttu-id="d7e5b-117">賢明な選択です。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-117">Sweet deal, right?</span></span>

## <a name="linq-providers-simplify-data-access"></a><span data-ttu-id="d7e5b-118">LINQ プロバイダーでデータ アクセスが簡単に</span><span class="sxs-lookup"><span data-stu-id="d7e5b-118">LINQ providers simplify data access</span></span>

<span data-ttu-id="d7e5b-119">実環境の非常に多くのソフトウェアでは、すべてのことが一部のソース (データベース、JSON、XML など) からのデータ処理を中心に展開されます。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-119">For a significant chunk of software out in the wild, everything revolves around dealing with data from some source (Databases, JSON, XML, and so on).</span></span> <span data-ttu-id="d7e5b-120">多くの場合、これには面倒なデータ ソースごとの新しい API の学習が含まれます。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-120">Often this involves learning a new API for each data source, which can be annoying.</span></span> <span data-ttu-id="d7e5b-121">LINQ は、データ アクセスの一般的な要素を、選択されたデータ ソースに関係なく同じようなクエリ構文に抽象化することで、これを簡略化します。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-121">LINQ simplifies this by abstracting common elements of data access into a query syntax that looks the same no matter which data source you pick.</span></span>

<span data-ttu-id="d7e5b-122">これにより、特定の属性値を持つ XML 要素がすべて検索されます。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-122">This finds all XML elements with a specific attribute value:</span></span>

```csharp
public static IEnumerable<XElement> FindAllElementsWithAttribute(XElement documentRoot, string elementName,
                                           string attributeName, string value)
{
    return from el in documentRoot.Elements(elementName)
           where (string)el.Element(attributeName) == value
           select el;
}
```

```vb
Public Shared Function FindAllElementsWithAttribute(documentRoot As XElement, elementName As String,
                                           attributeName As String, value As String) As IEnumerable(Of XElement)
    Return From el In documentRoot.Elements(elementName)
           Where el.Element(attributeName).ToString() = value
           Select el
End Function
```

<span data-ttu-id="d7e5b-123">コードを記述して XML ドキュメントを手動でスキャンし、このタスクを実行するのはとても難しいことです。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-123">Writing code to manually traverse the XML document to do this task would be far more challenging.</span></span>

<span data-ttu-id="d7e5b-124">XML との対話が、LINQ プロバイダーでできる唯一のことではありません。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-124">Interacting with XML isn't the only thing you can do with LINQ Providers.</span></span> <span data-ttu-id="d7e5b-125">[Linq to SQL](../../framework/data/adonet/sql/linq/index.md) は、MSSQL Server データベースの必要最低限のオブジェクト リレーショナル マッパー (ORM) です。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-125">[Linq to SQL](../../framework/data/adonet/sql/linq/index.md) is a fairly bare-bones Object-Relational Mapper (ORM) for an MSSQL Server Database.</span></span> <span data-ttu-id="d7e5b-126">[JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) ライブラリでは、LINQ を使用して効率的に JSON ドキュメントをトラバースできます。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-126">The [JSON.NET](https://www.newtonsoft.com/json/help/html/LINQtoJSON.htm) library provides efficient JSON Document traversal via LINQ.</span></span> <span data-ttu-id="d7e5b-127">さらに、必要な作業を行うライブラリがない場合は、[独自の LINQ プロバイダーを記述する](/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))こともできます。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-127">Furthermore, if there isn't a library that does what you need, you can also [write your own LINQ Provider](/previous-versions/visualstudio/visual-studio-2012/bb546158(v=vs.110))!</span></span>

## <a name="reasons-to-use-the-query-syntax"></a><span data-ttu-id="d7e5b-128">クエリ構文を使用する理由</span><span class="sxs-lookup"><span data-stu-id="d7e5b-128">Reasons to use the query syntax</span></span>

<span data-ttu-id="d7e5b-129">なぜクエリ構文を使用するのでしょうか?</span><span class="sxs-lookup"><span data-stu-id="d7e5b-129">Why use query syntax?</span></span> <span data-ttu-id="d7e5b-130">これはよくある質問です。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-130">This is a question that often comes up.</span></span> <span data-ttu-id="d7e5b-131">結論は、次のコードをご覧ください:</span><span class="sxs-lookup"><span data-stu-id="d7e5b-131">After all, the following code:</span></span>

```csharp
var filteredItems = myItems.Where(item => item.Foo);
```

```vb
Dim filteredItems = myItems.Where(Function(item) item.Foo)
```

<span data-ttu-id="d7e5b-132">上の構文は下の構文よりもずっと簡潔です。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-132">is a lot more concise than this:</span></span>

```csharp
var filteredItems = from item in myItems
                    where item.Foo
                    select item;
```

```vb
Dim filteredItems = From item In myItems
                    Where item.Foo
                    Select item
```

<span data-ttu-id="d7e5b-133">API 構文は単に、クエリ構文を実行するより簡潔な方法であるだけでしょうか?</span><span class="sxs-lookup"><span data-stu-id="d7e5b-133">Isn't the API syntax just a more concise way to do the query syntax?</span></span>

<span data-ttu-id="d7e5b-134">いいえ。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-134">No.</span></span> <span data-ttu-id="d7e5b-135">クエリ構文では **let** 句を使用できます。したがって、式の後ろの部分でこの句を使用すれば、式のスコープ内で変数を導入してバインドすることができます。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-135">The query syntax allows for the use of the **let** clause, which allows you to introduce and bind a variable within the scope of the expression, using it in subsequent pieces of the expression.</span></span> <span data-ttu-id="d7e5b-136">API 構文だけでも同じコードを再現できますが、コードが読み取りにくくなる可能性が高くなります。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-136">Reproducing the same code with only the API syntax can be done, but will most likely lead to code that's hard to read.</span></span>

<span data-ttu-id="d7e5b-137">そこで、**クエリ構文を使用する必要があるかどうか** ですが、</span><span class="sxs-lookup"><span data-stu-id="d7e5b-137">So this begs the question, **should you just use the query syntax?**</span></span>

<span data-ttu-id="d7e5b-138">次のような場合には、使用する必要が **あります**。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-138">The answer to this question is **yes** if:</span></span>

- <span data-ttu-id="d7e5b-139">既存のコードベースで既にクエリ構文を使用している。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-139">Your existing codebase already uses the query syntax.</span></span>
- <span data-ttu-id="d7e5b-140">複雑になるため、クエリ内で変数をスコープする必要がある。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-140">You need to scope variables within your queries because of complexity.</span></span>
- <span data-ttu-id="d7e5b-141">クエリ構文が好ましく、コードベースから注意がそれることはない。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-141">You prefer the query syntax and it won't distract from your codebase.</span></span>

<span data-ttu-id="d7e5b-142">次のような場合には、使用する必要は **ありません**。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-142">The answer to this question is **no** if...</span></span>

- <span data-ttu-id="d7e5b-143">既存のコードベースで既に API 構文を使用している。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-143">Your existing codebase already uses the API syntax</span></span>
- <span data-ttu-id="d7e5b-144">クエリ内で変数をスコープする必要はない。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-144">You have no need to scope variables within your queries</span></span>
- <span data-ttu-id="d7e5b-145">API 構文が好ましく、コードベースから注意がそれることはない</span><span class="sxs-lookup"><span data-stu-id="d7e5b-145">You prefer the API syntax and it won't distract from your codebase</span></span>

## <a name="essential-linq"></a><span data-ttu-id="d7e5b-146">重要な LINQ</span><span class="sxs-lookup"><span data-stu-id="d7e5b-146">Essential LINQ</span></span>

<span data-ttu-id="d7e5b-147">LINQ サンプルの一覧については、「[101 LINQ Samples](/samples/dotnet/try-samples/101-linq-samples/)」 (101 個の LINQ サンプル) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-147">For a truly comprehensive list of LINQ samples, visit [101 LINQ Samples](/samples/dotnet/try-samples/101-linq-samples/).</span></span>

<span data-ttu-id="d7e5b-148">以下の例は、LINQ の重要な要素の一部を簡単に示したものです。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-148">The following examples are a quick demonstration of some of the essential pieces of LINQ.</span></span> <span data-ttu-id="d7e5b-149">これは決して包括的なものではありません。LINQ ではここで紹介するものよりも多くの機能が提供されます。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-149">This is in no way comprehensive, as LINQ provides more functionality than what is showcased here.</span></span>

### <a name="the-bread-and-butter---where-select-and-aggregate"></a><span data-ttu-id="d7e5b-150">最も基本的かつ重要な要素 - `Where`、`Select`、および `Aggregate`</span><span class="sxs-lookup"><span data-stu-id="d7e5b-150">The bread and butter - `Where`, `Select`, and `Aggregate`</span></span>

```csharp
// Filtering a list.
var germanShepherds = dogs.Where(dog => dog.Breed == DogBreed.GermanShepherd);

// Using the query syntax.
var queryGermanShepherds = from dog in dogs
                          where dog.Breed == DogBreed.GermanShepherd
                          select dog;

// Mapping a list from type A to type B.
var cats = dogs.Select(dog => dog.TurnIntoACat());

// Using the query syntax.
var queryCats = from dog in dogs
                select dog.TurnIntoACat();

// Summing the lengths of a set of strings.
int seed = 0;
int sumOfStrings = strings.Aggregate(seed, (s1, s2) => s1.Length + s2.Length);
```

```vb
' Filtering a list.
Dim germanShepherds = dogs.Where(Function(dog) dog.Breed = DogBreed.GermanShepherd)

' Using the query syntax.
Dim queryGermanShepherds = From dog In dogs
                          Where dog.Breed = DogBreed.GermanShepherd
                          Select dog

' Mapping a list from type A to type B.
Dim cats = dogs.Select(Function(dog) dog.TurnIntoACat())

' Using the query syntax.
Dim queryCats = From dog In dogs
                Select dog.TurnIntoACat()

' Summing the lengths of a set of strings.
Dim seed As Integer = 0
Dim sumOfStrings As Integer = strings.Aggregate(seed, Function(s1, s2) s1.Length + s2.Length)
```

### <a name="flattening-a-list-of-lists"></a><span data-ttu-id="d7e5b-151">リストをまとめてフラット化する場合</span><span class="sxs-lookup"><span data-stu-id="d7e5b-151">Flattening a list of lists</span></span>

```csharp
// Transforms the list of kennels into a list of all their dogs.
var allDogsFromKennels = kennels.SelectMany(kennel => kennel.Dogs);
```

```vb
' Transforms the list of kennels into a list of all their dogs.
Dim allDogsFromKennels = kennels.SelectMany(Function(kennel) kennel.Dogs)
```

### <a name="union-between-two-sets-with-custom-comparator"></a><span data-ttu-id="d7e5b-152">2 つのセットの和集合 (カスタム比較子を含む)</span><span class="sxs-lookup"><span data-stu-id="d7e5b-152">Union between two sets (with custom comparator)</span></span>

```csharp
public class DogHairLengthComparer : IEqualityComparer<Dog>
{
    public bool Equals(Dog a, Dog b)
    {
        if (a == null && b == null)
        {
            return true;
        }
        else if ((a == null && b != null) ||
                 (a != null && b == null))
        {
            return false;
        }
        else
        {
            return a.HairLengthType == b.HairLengthType;
        }
    }

    public int GetHashCode(Dog d)
    {
        // Default hashcode is enough here, as these are simple objects.
        return d.GetHashCode();
    }
}
...

// Gets all the short-haired dogs between two different kennels.
var allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, new DogHairLengthComparer());

```

```vb
Public Class DogHairLengthComparer
  Inherits IEqualityComparer(Of Dog)

  Public Function Equals(a As Dog,b As Dog) As Boolean
      If a Is Nothing AndAlso b Is Nothing Then
          Return True
      ElseIf (a Is Nothing AndAlso b IsNot Nothing) OrElse (a IsNot Nothing AndAlso b Is Nothing) Then
          Return False
      Else
          Return a.HairLengthType = b.HairLengthType
      End If
  End Function

  Public Function GetHashCode(d As Dog) As Integer
      ' Default hashcode is enough here, as these are simple objects.
      Return d.GetHashCode()
  End Function
End Class

...

' Gets all the short-haired dogs between two different kennels.
Dim allShortHairedDogs = kennel1.Dogs.Union(kennel2.Dogs, New DogHairLengthComparer())
```

### <a name="intersection-between-two-sets"></a><span data-ttu-id="d7e5b-153">2 つのセットの積集合</span><span class="sxs-lookup"><span data-stu-id="d7e5b-153">Intersection between two sets</span></span>

```csharp
// Gets the volunteers who spend share time with two humane societies.
var volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     new VolunteerTimeComparer());
```

```vb
' Gets the volunteers who spend share time with two humane societies.
Dim volunteers = humaneSociety1.Volunteers.Intersect(humaneSociety2.Volunteers,
                                                     New VolunteerTimeComparer())
```

### <a name="ordering"></a><span data-ttu-id="d7e5b-154">順序</span><span class="sxs-lookup"><span data-stu-id="d7e5b-154">Ordering</span></span>

```csharp
// Get driving directions, ordering by if it's toll-free before estimated driving time.
var results = DirectionsProcessor.GetDirections(start, end)
              .OrderBy(direction => direction.HasNoTolls)
              .ThenBy(direction => direction.EstimatedTime);
```

```vb
' Get driving directions, ordering by if it's toll-free before estimated driving time.
Dim results = DirectionsProcessor.GetDirections(start, end).
                OrderBy(Function(direction) direction.HasNoTolls).
                ThenBy(Function(direction) direction.EstimatedTime)
```

### <a name="equality-of-instance-properties"></a><span data-ttu-id="d7e5b-155">インスタンスのプロパティの等価性</span><span class="sxs-lookup"><span data-stu-id="d7e5b-155">Equality of instance properties</span></span>

<span data-ttu-id="d7e5b-156">最後に、より高度なサンプルを以下に示します。同じ型の 2 つのインスタンスのプロパティ値が等しいかどうかを判断します ([この StackOverflow の投稿](https://stackoverflow.com/a/844855)から借用し、変更したもの)。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-156">Finally, a more advanced sample: determining if the values of the properties of two instances of the same type are equal (Borrowed and modified from [this StackOverflow post](https://stackoverflow.com/a/844855)):</span></span>

```csharp
public static bool PublicInstancePropertiesEqual<T>(this T self, T to, params string[] ignore) where T : class
{
    if (self == null || to == null)
    {
        return self == to;
    }

    // Selects the properties which have unequal values into a sequence of those properties.
    var unequalProperties = from property in typeof(T).GetProperties(BindingFlags.Public | BindingFlags.Instance)
                            where !ignore.Contains(property.Name)
                            let selfValue = property.GetValue(self, null)
                            let toValue = property.GetValue(to, null)
                            where !Equals(selfValue, toValue)
                            select property;
    return !unequalProperties.Any();
}
```

```vb
<System.Runtime.CompilerServices.Extension()>
Public Function PublicInstancePropertiesEqual(Of T As Class)(self As T, [to] As T, ParamArray ignore As String()) As Boolean
    If self Is Nothing OrElse [to] Is Nothing Then
        Return self Is [to]
    End If

    ' Selects the properties which have unequal values into a sequence of those properties.
    Dim unequalProperties = From [property] In GetType(T).GetProperties(BindingFlags.Public Or BindingFlags.Instance)
                            Where Not ignore.Contains([property].Name)
                            Let selfValue = [property].GetValue(self, Nothing)
                            Let toValue = [property].GetValue([to], Nothing)
                            Where Not Equals(selfValue, toValue) Select [property]
    Return Not unequalProperties.Any()
End Function
```

## <a name="plinq"></a><span data-ttu-id="d7e5b-157">PLINQ</span><span class="sxs-lookup"><span data-stu-id="d7e5b-157">PLINQ</span></span>

<span data-ttu-id="d7e5b-158">PLINQ (Parallel LINQ) は、LINQ 式の並列実行エンジンです。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-158">PLINQ, or Parallel LINQ, is a parallel execution engine for LINQ expressions.</span></span> <span data-ttu-id="d7e5b-159">つまり、LINQ の正規表現は、任意の数のスレッドで普通に並列化できます。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-159">In other words, a regular LINQ expression can be trivially parallelized across any number of threads.</span></span> <span data-ttu-id="d7e5b-160">これは、式の前に `AsParallel()` を指定して呼び出すことで実行できます。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-160">This is accomplished via a call to `AsParallel()` preceding the expression.</span></span>

<span data-ttu-id="d7e5b-161">以下、具体例に沿って説明します。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-161">Consider the following:</span></span>

```csharp
public static string GetAllFacebookUserLikesMessage(IEnumerable<FacebookUser> facebookUsers)
{
    var seed = default(UInt64);

    Func<UInt64, UInt64, UInt64> threadAccumulator = (t1, t2) => t1 + t2;
    Func<UInt64, UInt64, UInt64> threadResultAccumulator = (t1, t2) => t1 + t2;
    Func<Uint64, string> resultSelector = total => $"Facebook has {total} likes!";

    return facebookUsers.AsParallel()
                        .Aggregate(seed, threadAccumulator, threadResultAccumulator, resultSelector);
}
```

```vb
Public Shared GetAllFacebookUserLikesMessage(facebookUsers As IEnumerable(Of FacebookUser)) As String
{
    Dim seed As UInt64 = 0

    Dim threadAccumulator As Func(Of UInt64, UInt64, UInt64) = Function(t1, t2) t1 + t2
    Dim threadResultAccumulator As Func(Of UInt64, UInt64, UInt64) = Function(t1, t2) t1 + t2
    Dim resultSelector As Func(Of Uint64, string) = Function(total) $"Facebook has {total} likes!"

    Return facebookUsers.AsParallel().
                        Aggregate(seed, threadAccumulator, threadResultAccumulator, resultSelector)
}
```

<span data-ttu-id="d7e5b-162">このコードでは、必要に応じてシステム スレッドにまたがる `facebookUsers` をパーティション分割し、各スレッドの "いいね!" の数を合計し、スレッドごとの計算結果を合計して、その結果を適切な文字列に投影します。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-162">This code will partition `facebookUsers` across system threads as necessary, sum up the total likes on each thread in parallel, sum the results computed by each thread, and project that result into a nice string.</span></span>

<span data-ttu-id="d7e5b-163">図で表すと次のようになります。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-163">In diagram form:</span></span>

![PLINQ の図](media/index/plinq-diagram.png)

<span data-ttu-id="d7e5b-165">LINQ で簡単に表すことができる (つまり、純粋関数で副作用のない) 並列化可能な CPU 制約のあるジョブは、PLINQ の候補として最適です。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-165">Parallelizable CPU-bound jobs that can be easily expressed via LINQ (in other words, are pure functions and have no side effects) are a great candidate for PLINQ.</span></span> <span data-ttu-id="d7e5b-166">副作用の _ある_ ジョブの場合は、[タスク並列ライブラリ](../parallel-programming/task-parallel-library-tpl.md)の使用を検討してください。</span><span class="sxs-lookup"><span data-stu-id="d7e5b-166">For jobs that _do_ have a side effect, consider using the [Task Parallel Library](../parallel-programming/task-parallel-library-tpl.md).</span></span>

## <a name="more-resources"></a><span data-ttu-id="d7e5b-167">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="d7e5b-167">More resources</span></span>

* [<span data-ttu-id="d7e5b-168">101 個の LINQ サンプル</span><span class="sxs-lookup"><span data-stu-id="d7e5b-168">101 LINQ Samples</span></span>](/samples/dotnet/try-samples/101-linq-samples/)
* <span data-ttu-id="d7e5b-169">[Linqpad](https://www.linqpad.net/)。プレイグラウンド環境とデータベース クエリ エンジン (C#/F#/Visual Basic 用)</span><span class="sxs-lookup"><span data-stu-id="d7e5b-169">[Linqpad](https://www.linqpad.net/), a playground environment and Database querying engine for C#/F#/Visual Basic</span></span>
* <span data-ttu-id="d7e5b-170">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/)。LINQ to Objects の実装方法を学習するための電子書籍</span><span class="sxs-lookup"><span data-stu-id="d7e5b-170">[EduLinq](https://codeblog.jonskeet.uk/2011/02/23/reimplementing-linq-to-objects-part-45-conclusion-and-list-of-posts/), an e-book for learning how LINQ-to-objects is implemented</span></span>
