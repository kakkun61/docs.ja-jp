---
title: クエリで要素のプロパティのサブセットを返す方法 - C# プログラミング ガイド
description: C# のクエリ式で匿名型を使用して、各ソース要素のプロパティの一部を取得する方法について説明します。
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [C#], for subsets of element properties
ms.topic: how-to
ms.custom: contperf-fy21q2
ms.assetid: fabdf349-f443-4e3f-8368-6c471be1dd7b
ms.openlocfilehash: 5784d6a288af374d357346e32535ebe9c1877bcc
ms.sourcegitcommit: d0990c1c1ab2f81908360f47eafa8db9aa165137
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/15/2020
ms.locfileid: "97512796"
---
# <a name="how-to-return-subsets-of-element-properties-in-a-query-c-programming-guide"></a><span data-ttu-id="133df-103">クエリで要素のプロパティのサブセットを返す方法 (C# プログラミング ガイド)</span><span class="sxs-lookup"><span data-stu-id="133df-103">How to return subsets of element properties in a query (C# Programming Guide)</span></span>

<span data-ttu-id="133df-104">次の両方の条件に当てはまる場合は、クエリ式に匿名型を使用します。</span><span class="sxs-lookup"><span data-stu-id="133df-104">Use an anonymous type in a query expression when both of these conditions apply:</span></span>  
  
- <span data-ttu-id="133df-105">各ソース要素のプロパティの一部のみを返したい。</span><span class="sxs-lookup"><span data-stu-id="133df-105">You want to return only some of the properties of each source element.</span></span>  
  
- <span data-ttu-id="133df-106">クエリを実行したメソッドのスコープ外のクエリ結果を保存する必要がない。</span><span class="sxs-lookup"><span data-stu-id="133df-106">You do not have to store the query results outside the scope of the method in which the query is executed.</span></span>  
  
 <span data-ttu-id="133df-107">各ソース要素の 1 つのプロパティまたはフィールドのみを返す場合は、`select` 句でドット演算子 (.) を使用します。</span><span class="sxs-lookup"><span data-stu-id="133df-107">If you only want to return one property or field from each source element, then you can just use the dot operator in the `select` clause.</span></span> <span data-ttu-id="133df-108">たとえば、各 `student` の `ID` のみを返すには、次のように `select` 句を記述します。</span><span class="sxs-lookup"><span data-stu-id="133df-108">For example, to return only the `ID` of each `student`, write the `select` clause as follows:</span></span>  
  
```csharp  
select student.ID;  
```  
  
## <a name="example"></a><span data-ttu-id="133df-109">例</span><span class="sxs-lookup"><span data-stu-id="133df-109">Example</span></span>  

 <span data-ttu-id="133df-110">次に、匿名型を使用して、各ソース要素のプロパティのうち、指定した条件に一致するプロパティのみを返す例を示します。</span><span class="sxs-lookup"><span data-stu-id="133df-110">The following example shows how to use an anonymous type to return only a subset of the properties of each source element that matches the specified condition.</span></span>  
  
 [!code-csharp[csProgGuideLINQ#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideLINQ/CS/csRef30LangFeatures_2.cs#31)]  
  
 <span data-ttu-id="133df-111">名前を指定しない場合、匿名型にはプロパティのソース要素名が使用されます。</span><span class="sxs-lookup"><span data-stu-id="133df-111">Note that the anonymous type uses the source element's names for its properties if no names are specified.</span></span> <span data-ttu-id="133df-112">匿名型のプロパティに新しい名前を付けるには、次のように `select` ステートメントを記述します。</span><span class="sxs-lookup"><span data-stu-id="133df-112">To give new names to the properties in the anonymous type, write the `select` statement as follows:</span></span>  
  
```csharp  
select new { First = student.FirstName, Last = student.LastName };  
```  
  
 <span data-ttu-id="133df-113">前の例でこの方法を試すには、`Console.WriteLine` ステートメントも次のように変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="133df-113">If you try this in the previous example, then the `Console.WriteLine` statement must also change:</span></span>  
  
```csharp  
Console.WriteLine(student.First + " " + student.Last);  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="133df-114">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="133df-114">Compiling the Code</span></span>  
  
<span data-ttu-id="133df-115">このコードを実行するには、クラスをコピーし、System.Linq に `using` ディレクティブを使用した C# コンソール アプリケーションに貼り付けます。</span><span class="sxs-lookup"><span data-stu-id="133df-115">To run this code, copy and paste the class into a C# console application  with a `using` directive for System.Linq.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="133df-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="133df-116">See also</span></span>

- [<span data-ttu-id="133df-117">C# プログラミング ガイド</span><span class="sxs-lookup"><span data-stu-id="133df-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="133df-118">匿名型</span><span class="sxs-lookup"><span data-stu-id="133df-118">Anonymous Types</span></span>](./anonymous-types.md)
- [<span data-ttu-id="133df-119">C# での LINQ</span><span class="sxs-lookup"><span data-stu-id="133df-119">LINQ in C#</span></span>](../../linq/index.md)
