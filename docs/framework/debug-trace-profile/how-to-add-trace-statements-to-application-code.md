---
title: '方法: アプリケーション コードにトレース ステートメントを追加する'
description: .NET のアプリケーションコードにトレースステートメントを追加する方法について説明します。 トレースで最も頻繁に使用されるメソッドは、出力をリスナーに書き込むためのメソッドです。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tracing [.NET Framework], conditional writes based on switches
- trace statements
- WriteLineIf method
- tracing [.NET Framework], adding trace statements
- Assert method, tracing code
- trace switches, conditional writes based on switches
- WriteIf method
ms.assetid: f3a93fa7-1717-467d-aaff-393e5c9828b4
ms.openlocfilehash: 6beecf39d4372a194a9110ed8942b998443934d4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244211"
---
# <a name="how-to-add-trace-statements-to-application-code"></a><span data-ttu-id="2e0c7-104">方法: アプリケーション コードにトレース ステートメントを追加する</span><span class="sxs-lookup"><span data-stu-id="2e0c7-104">How to: Add Trace Statements to Application Code</span></span>

<span data-ttu-id="2e0c7-105">トレースで最も使用頻度の高いメソッドは、出力をリスナーに書き込むメソッドである **Write**、**WriteIf**、**WriteLine**、**WriteLineIf**、**Assert**、および **Fail** です。</span><span class="sxs-lookup"><span data-stu-id="2e0c7-105">The methods used most often for tracing are the methods for writing output to listeners: **Write**, **WriteIf**, **WriteLine**, **WriteLineIf**, **Assert**, and **Fail**.</span></span> <span data-ttu-id="2e0c7-106">これらのメソッドは、次の 2 つのカテゴリに分類できます。**Write**、**WriteLine**、および **Fail** はすべて出力を無条件に生成します。それに対して、**WriteIf**、**WriteLineIf**、および **Assert** はブール条件をテストし、条件の値に基づいて書き込みを行ったり行わなかったりします。</span><span class="sxs-lookup"><span data-stu-id="2e0c7-106">These methods can be divided into two categories: **Write**, **WriteLine**, and **Fail** all emit output unconditionally, whereas **WriteIf**, **WriteLineIf**, and **Assert** test a Boolean condition, and write or do not write based on the value of the condition.</span></span> <span data-ttu-id="2e0c7-107">**WriteIf** と **WriteLineIf** は条件が `true` の場合に出力を生成し、**Assert** は条件が `false` の場合に出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="2e0c7-107">**WriteIf** and **WriteLineIf** emit output if the condition is `true`, and **Assert** emits output if the condition is `false`.</span></span>  
  
 <span data-ttu-id="2e0c7-108">トレースおよびデバッグの方法をデザインするときは、出力の表示方法について検討する必要があります。</span><span class="sxs-lookup"><span data-stu-id="2e0c7-108">When designing your tracing and debugging strategy, you should think about how you want the output to look.</span></span> <span data-ttu-id="2e0c7-109">複数の **Write** ステートメントが関連付けられていない情報でいっぱいになると、読み取りにくいログが作成されます。</span><span class="sxs-lookup"><span data-stu-id="2e0c7-109">Multiple **Write** statements filled with unrelated information will create a log that is difficult to read.</span></span> <span data-ttu-id="2e0c7-110">一方、 **WriteLine** を使用して関連するステートメントを別々の行に配置すると、どの情報が一緒に属しているかを区別するのが困難になる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="2e0c7-110">On the other hand, using **WriteLine** to put related statements on separate lines may make it difficult to distinguish what information belongs together.</span></span> <span data-ttu-id="2e0c7-111">一般に **、複数の** ソースの情報を結合して1つの情報メッセージを作成し、1つの完全なメッセージを作成する場合は、 **WriteLine** ステートメントを使用します。</span><span class="sxs-lookup"><span data-stu-id="2e0c7-111">In general, use multiple **Write** statements when you want to combine information from multiple sources to create a single informative message, and use the **WriteLine** statement when you want to create a single, complete message.</span></span>  
  
### <a name="to-write-a-complete-line"></a><span data-ttu-id="2e0c7-112">完結した行を書き込むには</span><span class="sxs-lookup"><span data-stu-id="2e0c7-112">To write a complete line</span></span>  
  
1. <span data-ttu-id="2e0c7-113"><xref:System.Diagnostics.Trace.WriteLine%2A> メソッドまたは <xref:System.Diagnostics.Trace.WriteLineIf%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2e0c7-113">Call the <xref:System.Diagnostics.Trace.WriteLine%2A> or <xref:System.Diagnostics.Trace.WriteLineIf%2A> method.</span></span>  
  
     <span data-ttu-id="2e0c7-114">このメソッドが返すメッセージの末尾には、キャリッジ リターンが追加されます。したがって、次回の **Write**、**WriteIf**、**WriteLine**、または **WriteLineIf** が返すメッセージは、次の行から開始されます。</span><span class="sxs-lookup"><span data-stu-id="2e0c7-114">A carriage return is appended to the end of the message this method returns, so that the next message returned by **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the following line:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteLine("Error in AppendData procedure.")  
    Trace.WriteLineIf(errorFlag, "Error in AppendData procedure.")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteLine ("Error in AppendData procedure.");  
    System.Diagnostics.Trace.WriteLineIf(errorFlag,
       "Error in AppendData procedure.");  
    ```  
  
### <a name="to-write-a-partial-line"></a><span data-ttu-id="2e0c7-115">完結しない行を書き込むには</span><span class="sxs-lookup"><span data-stu-id="2e0c7-115">To write a partial line</span></span>  
  
1. <span data-ttu-id="2e0c7-116"><xref:System.Diagnostics.Trace.Write%2A> メソッドまたは <xref:System.Diagnostics.Trace.WriteIf%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2e0c7-116">Call the <xref:System.Diagnostics.Trace.Write%2A> or <xref:System.Diagnostics.Trace.WriteIf%2A> method.</span></span>  
  
     <span data-ttu-id="2e0c7-117">**Write**、**WriteIf**、**WriteLine** または **WriteLineIf** によって次に書き込まれるメッセージは、今回の **Write** または **WriteIf** ステートメントによって書き込まれるメッセージと同じ行から開始されます。</span><span class="sxs-lookup"><span data-stu-id="2e0c7-117">The next message put out by a **Write**, **WriteIf**, **WriteLine**, or **WriteLineIf** will begin on the same line as the message put out by the **Write** or **WriteIf** statement:</span></span>  
  
    ```vb  
    Dim errorFlag As Boolean = False  
    Trace.WriteIf(errorFlag, "Error in AppendData procedure.")  
    Debug.WriteIf(errorFlag, "Transaction abandoned.")  
    Trace.Write("Invalid value for data request")  
    ```  
  
    ```csharp  
    bool errorFlag = false;  
    System.Diagnostics.Trace.WriteIf(errorFlag,
       "Error in AppendData procedure.");  
    System.Diagnostics.Debug.WriteIf(errorFlag, "Transaction abandoned.");  
    Trace.Write("Invalid value for data request");  
    ```  
  
### <a name="to-verify-that-certain-conditions-exist-either-before-or-after-you-execute-a-method"></a><span data-ttu-id="2e0c7-118">メソッドの実行前または実行後に特定の条件が存在するかどうかを確認するには</span><span class="sxs-lookup"><span data-stu-id="2e0c7-118">To verify that certain conditions exist either before or after you execute a method</span></span>  
  
1. <span data-ttu-id="2e0c7-119"><xref:System.Diagnostics.Trace.Assert%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="2e0c7-119">Call the <xref:System.Diagnostics.Trace.Assert%2A> method.</span></span>  
  
    ```vb  
    Dim i As Integer = 4  
    Trace.Assert(i = 5, "i is not equal to 5.")  
    ```  
  
    ```csharp  
    int i = 4;  
    System.Diagnostics.Trace.Assert(i == 5, "i is not equal to 5.");  
    ```  
  
    > [!NOTE]
    > <span data-ttu-id="2e0c7-120">**Assert** は、トレースとデバッグの両方で使用できます。</span><span class="sxs-lookup"><span data-stu-id="2e0c7-120">You can use **Assert** with both tracing and debugging.</span></span> <span data-ttu-id="2e0c7-121">この例では、呼び出し履歴を **Listeners** コレクションのリスナーに出力しています。</span><span class="sxs-lookup"><span data-stu-id="2e0c7-121">This example outputs the call stack to any listener in the **Listeners** collection.</span></span> <span data-ttu-id="2e0c7-122">詳細については、「[マネージド コードのアサーション](/visualstudio/debugger/assertions-in-managed-code)」および「<xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2e0c7-122">For more information, see [Assertions in Managed Code](/visualstudio/debugger/assertions-in-managed-code) and <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e0c7-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="2e0c7-123">See also</span></span>

- <xref:System.Diagnostics.Debug.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Debug.WriteLineIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteIf%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.Trace.WriteLineIf%2A?displayProperty=nameWithType>
- [<span data-ttu-id="2e0c7-124">アプリケーションのトレースとインストルメント</span><span class="sxs-lookup"><span data-stu-id="2e0c7-124">Tracing and Instrumenting Applications</span></span>](tracing-and-instrumenting-applications.md)
- [<span data-ttu-id="2e0c7-125">方法: トレース スイッチを作成、初期化、および構成する</span><span class="sxs-lookup"><span data-stu-id="2e0c7-125">How to: Create, Initialize and Configure Trace Switches</span></span>](how-to-create-initialize-and-configure-trace-switches.md)
- [<span data-ttu-id="2e0c7-126">トレース スイッチ</span><span class="sxs-lookup"><span data-stu-id="2e0c7-126">Trace Switches</span></span>](trace-switches.md)
- [<span data-ttu-id="2e0c7-127">トレース リスナー</span><span class="sxs-lookup"><span data-stu-id="2e0c7-127">Trace Listeners</span></span>](trace-listeners.md)
