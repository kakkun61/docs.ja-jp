---
title: 非ジェネリックの ForEach
ms.date: 03/30/2017
ms.assetid: 576cd07a-d58d-4536-b514-77bad60bff38
ms.openlocfilehash: 9678d929375857a76d01f575e637a069b0911ae5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283576"
---
# <a name="non-generic-foreach"></a><span data-ttu-id="a08bf-102">非ジェネリックの ForEach</span><span class="sxs-lookup"><span data-stu-id="a08bf-102">Non-Generic ForEach</span></span>

[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] <span data-ttu-id="a08bf-103">のツールボックスには、制御フロー アクティビティのセットが用意されています。これには、<xref:System.Activities.Statements.ForEach%601> コレクションを反復処理できる <xref:System.Collections.Generic.IEnumerable%601> が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a08bf-103">ships in its toolbox a set of Control Flow activities, including <xref:System.Activities.Statements.ForEach%601>, which allows iterating through <xref:System.Collections.Generic.IEnumerable%601> collections.</span></span>  
  
 <span data-ttu-id="a08bf-104"><xref:System.Activities.Statements.ForEach%601> では、その <xref:System.Activities.Statements.ForEach%601.Values%2A> プロパティを <xref:System.Collections.Generic.IEnumerable%601> 型にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="a08bf-104"><xref:System.Activities.Statements.ForEach%601> requires its <xref:System.Activities.Statements.ForEach%601.Values%2A> property to be of type <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="a08bf-105">このため、ユーザーは、<xref:System.Collections.Generic.IEnumerable%601> インターフェイス (<xref:System.Collections.ArrayList> など) を実装するデータ構造を反復処理できません。</span><span class="sxs-lookup"><span data-stu-id="a08bf-105">This precludes users from iterating over data structures that implement <xref:System.Collections.Generic.IEnumerable%601> interface (for example, <xref:System.Collections.ArrayList>).</span></span> <span data-ttu-id="a08bf-106"><xref:System.Activities.Statements.ForEach%601> の非ジェネリック バージョンにはこの要件はありませんが、コレクション内の値の型の互換性を確保するために実行時の複雑さが増します。</span><span class="sxs-lookup"><span data-stu-id="a08bf-106">The non-generic version of <xref:System.Activities.Statements.ForEach%601> overcomes this requirement, at the expense of more run-time complexity for ensuring the compatibility of the types of the values in the collection.</span></span>  
  
 <span data-ttu-id="a08bf-107">このサンプルでは、非ジェネリックの <xref:System.Activities.Statements.ForEach%601> アクティビティとそのデザイナーを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a08bf-107">This sample shows how to implement a non-generic <xref:System.Activities.Statements.ForEach%601> activity and its designer.</span></span> <span data-ttu-id="a08bf-108">このアクティビティは、<xref:System.Collections.ArrayList> の反復処理に使用できます。</span><span class="sxs-lookup"><span data-stu-id="a08bf-108">This activity can be used to iterate through <xref:System.Collections.ArrayList>.</span></span>  
  
## <a name="foreach-activity"></a><span data-ttu-id="a08bf-109">ForEach アクティビティ</span><span class="sxs-lookup"><span data-stu-id="a08bf-109">ForEach Activity</span></span>  

 <span data-ttu-id="a08bf-110">C#/Visual Basic のステートメントは、コレクションの要素を `foreach` 列挙し、コレクションの各要素に対して埋め込みステートメントを実行します。</span><span class="sxs-lookup"><span data-stu-id="a08bf-110">The C#/Visual Basic `foreach` statement enumerates the elements of a collection, executing an embedded statement for each element of the collection.</span></span> <span data-ttu-id="a08bf-111">[!INCLUDE[wf1](../../../../includes/wf1-md.md)] に相当する `foreach` のアクティビティは、<xref:System.Activities.Statements.ForEach%601> および <xref:System.Activities.Statements.ParallelForEach%601> です。</span><span class="sxs-lookup"><span data-stu-id="a08bf-111">The [!INCLUDE[wf1](../../../../includes/wf1-md.md)] equivalent activities of `foreach` are <xref:System.Activities.Statements.ForEach%601> and <xref:System.Activities.Statements.ParallelForEach%601>.</span></span> <span data-ttu-id="a08bf-112"><xref:System.Activities.Statements.ForEach%601> アクティビティには、値のリストと本体が含まれます。</span><span class="sxs-lookup"><span data-stu-id="a08bf-112">The <xref:System.Activities.Statements.ForEach%601> activity contains a list of values and a body.</span></span> <span data-ttu-id="a08bf-113">実行時に、リストが反復処理されて、リスト内の値ごとに本体が実行されます。</span><span class="sxs-lookup"><span data-stu-id="a08bf-113">At runtime, the list is iterated and the body is executed for each value in the list.</span></span>  
  
 <span data-ttu-id="a08bf-114">ほとんどの場合、ジェネリック バージョンのアクティビティを使用することをお勧めします。ジェネリック バージョンのアクティビティは、そのアクティビティを使用するシナリオの大半に対応し、コンパイル時の型チェックが実現するためです。</span><span class="sxs-lookup"><span data-stu-id="a08bf-114">For most cases, the generic version of the activity should be the preferred solution, because it covers most of the scenarios in which it would be used, and provides type checking at compile time.</span></span> <span data-ttu-id="a08bf-115">非ジェネリック バージョンは、非ジェネリックの <xref:System.Collections.IEnumerable> インターフェイスを実装する型を反復処理するために使用できます。</span><span class="sxs-lookup"><span data-stu-id="a08bf-115">The non-generic version can be used for iterating through types that implement the non-generic <xref:System.Collections.IEnumerable> interface.</span></span>  
  
## <a name="class-definition"></a><span data-ttu-id="a08bf-116">クラス定義</span><span class="sxs-lookup"><span data-stu-id="a08bf-116">Class Definition</span></span>  

 <span data-ttu-id="a08bf-117">次のコード例は、非ジェネリックの `ForEach` アクティビティの定義を示しています。</span><span class="sxs-lookup"><span data-stu-id="a08bf-117">The following code example shows the definition of a non-generic `ForEach` activity.</span></span>  
  
```csharp  
[ContentProperty("Body")]  
public class ForEach : NativeActivity  
{  
    [RequiredArgument]  
    [DefaultValue(null)]  
    InArgument<IEnumerable> Values { get; set; }  
  
    [DefaultValue(null)]  
    [DependsOn("Values")]  
    ActivityAction<object> Body { get; set; }
}  
```  
  
 <span data-ttu-id="a08bf-118">Body (省略可能)</span><span class="sxs-lookup"><span data-stu-id="a08bf-118">Body (optional)</span></span>  
 <span data-ttu-id="a08bf-119">コレクション内の要素ごとに実行される <xref:System.Activities.ActivityAction> 型の <xref:System.Object>。</span><span class="sxs-lookup"><span data-stu-id="a08bf-119">The <xref:System.Activities.ActivityAction> of type <xref:System.Object>, which is executed for each element in the collection.</span></span> <span data-ttu-id="a08bf-120">各要素は、`Argument` プロパティを使用して Body に渡されます。</span><span class="sxs-lookup"><span data-stu-id="a08bf-120">Each individual element is passed into the Body through its `Argument` property.</span></span>  
  
 <span data-ttu-id="a08bf-121">Values (省略可能)</span><span class="sxs-lookup"><span data-stu-id="a08bf-121">Values (optional)</span></span>  
 <span data-ttu-id="a08bf-122">反復処理される要素のコレクション。</span><span class="sxs-lookup"><span data-stu-id="a08bf-122">The collection of elements that are iterated over.</span></span> <span data-ttu-id="a08bf-123">コレクションのすべての要素の型が互換性のある型であることが実行時に確認されます。</span><span class="sxs-lookup"><span data-stu-id="a08bf-123">Ensuring that all elements of the collection are of compatible types is done at run-time.</span></span>  
  
## <a name="example-of-using-foreach"></a><span data-ttu-id="a08bf-124">ForEach の使用例</span><span class="sxs-lookup"><span data-stu-id="a08bf-124">Example of Using ForEach</span></span>  

 <span data-ttu-id="a08bf-125">アプリケーションでの ForEach アクティビティの使用方法を次のコードに示します。</span><span class="sxs-lookup"><span data-stu-id="a08bf-125">The following code demonstrates how to use the ForEach activity in an application.</span></span>  
  
```csharp  
string[] names = { "bill", "steve", "ray" };  
  
DelegateInArgument<object> iterationVariable = new DelegateInArgument<object>() { Name = "iterationVariable" };  
  
Activity sampleUsage =  
    new ForEach  
    {  
       Values = new InArgument<IEnumerable>(c=> names),  
       Body = new ActivityAction<object>
       {
           Argument = iterationVariable,  
           Handler = new WriteLine  
           {  
               Text = new InArgument<string>(env => string.Format("Hello {0}",                                                               iterationVariable.Get(env)))  
           }  
       }  
   };  
```  
  
|<span data-ttu-id="a08bf-126">条件</span><span class="sxs-lookup"><span data-stu-id="a08bf-126">Condition</span></span>|<span data-ttu-id="a08bf-127">Message</span><span class="sxs-lookup"><span data-stu-id="a08bf-127">Message</span></span>|<span data-ttu-id="a08bf-128">重大度</span><span class="sxs-lookup"><span data-stu-id="a08bf-128">Severity</span></span>|<span data-ttu-id="a08bf-129">例外の種類</span><span class="sxs-lookup"><span data-stu-id="a08bf-129">Exception Type</span></span>|  
|---------------|-------------|--------------|--------------------|  
|<span data-ttu-id="a08bf-130">値が `null` である</span><span class="sxs-lookup"><span data-stu-id="a08bf-130">Values is `null`</span></span>|<span data-ttu-id="a08bf-131">必須のアクティビティ引数 'Values' の値が指定されませんでした。</span><span class="sxs-lookup"><span data-stu-id="a08bf-131">Value for a required activity argument 'Values' was not supplied.</span></span>|<span data-ttu-id="a08bf-132">エラー</span><span class="sxs-lookup"><span data-stu-id="a08bf-132">Error</span></span>|<xref:System.InvalidOperationException>|  
  
## <a name="foreach-designer"></a><span data-ttu-id="a08bf-133">ForEach デザイナー</span><span class="sxs-lookup"><span data-stu-id="a08bf-133">ForEach Designer</span></span>  

 <span data-ttu-id="a08bf-134">サンプルのアクティビティ デザイナーは、組み込みの <xref:System.Activities.Statements.ForEach%601> アクティビティ用に提供されているデザイナーに外観が似ています。</span><span class="sxs-lookup"><span data-stu-id="a08bf-134">The activity designer for the sample is similar in appearance to the designer provided for the built-in <xref:System.Activities.Statements.ForEach%601> activity.</span></span> <span data-ttu-id="a08bf-135">デザイナーは、[ **サンプル** の **非ジェネリックアクティビティ** ] カテゴリの [ツールボックス] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="a08bf-135">The designer appears in the toolbox in the **Samples**, **Non-Generic Activities** category.</span></span> <span data-ttu-id="a08bf-136">デザイナーのツールボックスには **ForEachWithBodyFactory** という名前が付けられます。これは、アクティビティがツールボックスでを公開するためです。これにより、 <xref:System.Activities.Presentation.IActivityTemplateFactory> 適切に構成されたを持つアクティビティが作成され <xref:System.Activities.ActivityAction> ます。</span><span class="sxs-lookup"><span data-stu-id="a08bf-136">The designer is named **ForEachWithBodyFactory** in the toolbox, because the activity exposes an <xref:System.Activities.Presentation.IActivityTemplateFactory> in the toolbox, which creates the activity with a properly configured <xref:System.Activities.ActivityAction>.</span></span>  
  
```csharp  
public sealed class ForEachWithBodyFactory : IActivityTemplateFactory  
{  
    public Activity Create(DependencyObject target)  
    {  
        return new Microsoft.Samples.Activities.Statements.ForEach()  
        {  
            Body = new ActivityAction<object>()  
            {  
                Argument = new DelegateInArgument<object>()  
                {  
                    Name = "item"  
                }  
            }  
        };  
    }  
}  
```  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="a08bf-137">このサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="a08bf-137">To run this sample</span></span>  
  
1. <span data-ttu-id="a08bf-138">選択したプロジェクトをソリューションのスタートアップ プロジェクトに設定します。</span><span class="sxs-lookup"><span data-stu-id="a08bf-138">Set the project of your choice as the start-up project of the solution:</span></span>  
  
    1. <span data-ttu-id="a08bf-139">**Codetestclient** は、コードを使用してアクティビティを使用する方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="a08bf-139">**CodeTestClient** shows how to use the activity using code.</span></span>  
  
    2. <span data-ttu-id="a08bf-140">**デザイナ Testclient** デザイナー内でアクティビティを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a08bf-140">**DesignerTestClient** shows how to use the activity within the designer.</span></span>  
  
2. <span data-ttu-id="a08bf-141">プロジェクトをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="a08bf-141">Build and run the project.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="a08bf-142">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a08bf-142">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a08bf-143">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a08bf-143">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="a08bf-144">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="a08bf-144">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a08bf-145">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a08bf-145">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\NonGenericForEach`
