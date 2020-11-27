---
title: ワークフロー実行プロパティ
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: be9ae5924786ea1e23cc649034d927789c64e405
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293794"
---
# <a name="workflow-execution-properties"></a><span data-ttu-id="df059-102">ワークフロー実行プロパティ</span><span class="sxs-lookup"><span data-stu-id="df059-102">Workflow Execution Properties</span></span>

<span data-ttu-id="df059-103">CLR は、スレッド ローカル ストレージ (TLS) を介して各スレッドの実行コンテキストを維持します。</span><span class="sxs-lookup"><span data-stu-id="df059-103">Through thread local storage (TLS), the CLR maintains an execution context for each thread.</span></span> <span data-ttu-id="df059-104">この実行コンテキストは、スレッド ID、アンビエント トランザクション、現在のアクセス許可セットなど、既知のスレッド プロパティに加えて、名前付きスロットのようなユーザー定義のスレッド プロパティを制御します。</span><span class="sxs-lookup"><span data-stu-id="df059-104">This execution context governs well-known thread properties such as the thread identity, the ambient transaction, and the current permission set in addition to user-defined thread properties like named slots.</span></span>  
  
 <span data-ttu-id="df059-105">CLR を直接対象にするプログラムとは異なり、ワークフロー プログラムは、スレッド非依存環境で実行されるアクティビティのツリーへ階層的にスコープ設定されます。</span><span class="sxs-lookup"><span data-stu-id="df059-105">Unlike programs directly targeting the CLR, workflow programs are hierarchically scoped trees of activities that execute in a thread-agnostic environment.</span></span> <span data-ttu-id="df059-106">つまり、特定の作業項目のスコープに含まれるコンテキストを判断するために、標準の TLS 機構を直接使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="df059-106">This implies that the standard TLS mechanisms cannot directly be used to determine what context is in scope for a given work item.</span></span> <span data-ttu-id="df059-107">たとえば、2 つの並行する実行の分岐で異なるトランザクションを使用していても、スケジューラは同じ CLR スレッド上でそれらの実行をインターリーブすることがあります。</span><span class="sxs-lookup"><span data-stu-id="df059-107">For example, two parallel branches of execution might use different transactions, yet the scheduler might interleave their execution on the same CLR thread.</span></span>  
  
 <span data-ttu-id="df059-108">ワークフローの実行プロパティには、アクティビティの環境にコンテキスト特有のプロパティを追加する機構が用意されています。</span><span class="sxs-lookup"><span data-stu-id="df059-108">Workflow execution properties provide a mechanism to add context specific properties to an activity’s environment.</span></span> <span data-ttu-id="df059-109">そのため、サブツリーのスコープに含まれるプロパティをアクティビティで宣言することができ、CLR オブジェクトと適切に相互作用するように TLS の設定および設定解除を行うフックの実現もできます。</span><span class="sxs-lookup"><span data-stu-id="df059-109">This allows an activity to declare which properties are in scope for its sub-tree and also provides hooks for setting up and tearing down TLS to properly interoperate with CLR objects.</span></span>  
  
## <a name="creating-and-using-workflow-execution-properties"></a><span data-ttu-id="df059-110">ワークフロー実行プロパティの作成と使用</span><span class="sxs-lookup"><span data-stu-id="df059-110">Creating and Using Workflow Execution Properties</span></span>  

 <span data-ttu-id="df059-111">ワークフロー実行プロパティは、通常、<xref:System.Activities.IExecutionProperty> インターフェイスを実装します。ただし、メッセージングに重点を置いたプロパティが代わりに <xref:System.ServiceModel.Activities.ISendMessageCallback> と <xref:System.ServiceModel.Activities.IReceiveMessageCallback> を実装することもあります。</span><span class="sxs-lookup"><span data-stu-id="df059-111">Workflow execution properties usually implement the <xref:System.Activities.IExecutionProperty> interface, though properties focused on messaging may implement <xref:System.ServiceModel.Activities.ISendMessageCallback> and <xref:System.ServiceModel.Activities.IReceiveMessageCallback> instead.</span></span> <span data-ttu-id="df059-112">ワークフロー実行プロパティを作成するには、<xref:System.Activities.IExecutionProperty> インターフェイスを実装するクラスを作成し、メンバーの <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> および <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> を実装します。</span><span class="sxs-lookup"><span data-stu-id="df059-112">To create a workflow execution property, create a class that implements the <xref:System.Activities.IExecutionProperty> interface and implement the members <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> and <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span></span> <span data-ttu-id="df059-113">これらのメンバーには、プロパティを含むアクティビティ (すべての子アクティビティを含む) の作業の各パルス中に、スレッド ローカル ストレージを適切に設定および設定解除できる実行プロパティがあります。</span><span class="sxs-lookup"><span data-stu-id="df059-113">These members provide the execution property with an opportunity to properly set up and tear down the thread local storage during each pulse of work of the activity that contains the property, including any child activities.</span></span> <span data-ttu-id="df059-114">この例では、`ConsoleColorProperty` を設定する `Console.ForegroundColor` を作成します。</span><span class="sxs-lookup"><span data-stu-id="df059-114">In this example, a `ConsoleColorProperty` is created that sets the `Console.ForegroundColor`.</span></span>  
  
```csharp  
class ConsoleColorProperty : IExecutionProperty  
{  
    public const string Name = "ConsoleColorProperty";  
  
    ConsoleColor original;  
    ConsoleColor color;  
  
    public ConsoleColorProperty(ConsoleColor color)  
    {  
        this.color = color;  
    }  
  
    void IExecutionProperty.SetupWorkflowThread()  
    {  
        original = Console.ForegroundColor;  
        Console.ForegroundColor = color;  
    }  
  
    void IExecutionProperty.CleanupWorkflowThread()  
    {  
        Console.ForegroundColor = original;  
    }  
}  
```  
  
 <span data-ttu-id="df059-115">アクティビティ作成者がこのプロパティを使用するには、アクティビティの実行オーバーライドに登録します。</span><span class="sxs-lookup"><span data-stu-id="df059-115">Activity authors can use this property by registering it in the activity’s execute override.</span></span> <span data-ttu-id="df059-116">この例では、現在の <xref:System.Activities.NativeActivityContext> の <xref:System.Activities.NativeActivityContext.Properties%2A> コレクションに追加することで、`ConsoleColorProperty` を登録する `ConsoleColorScope` アクティビティが定義されています。</span><span class="sxs-lookup"><span data-stu-id="df059-116">In this example, a `ConsoleColorScope` activity is defined that registers the `ConsoleColorProperty` by adding it to the <xref:System.Activities.NativeActivityContext.Properties%2A> collection of the current <xref:System.Activities.NativeActivityContext>.</span></span>  
  
```csharp  
public sealed class ConsoleColorScope : NativeActivity  
{  
    public ConsoleColorScope()  
        : base()  
    {  
    }  
  
    public ConsoleColor Color { get; set; }  
    public Activity Body { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        context.Properties.Add(ConsoleColorProperty.Name, new ConsoleColorProperty(this.Color));  
  
        if (this.Body != null)  
        {  
            context.ScheduleActivity(this.Body);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="df059-117">アクティビティの本体が作業のパルスを開始すると、プロパティの <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> メソッドが呼び出されます。作業のパルスが完了すると、<xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="df059-117">When the activity’s body starts a pulse of work, the <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> method of the property is called, and when the pulse of work is complete, the <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> is called.</span></span> <span data-ttu-id="df059-118">この例では、3 つの分岐がある <xref:System.Activities.Statements.Parallel> アクティビティを使用するワークフローが作成されます。</span><span class="sxs-lookup"><span data-stu-id="df059-118">In this example, a workflow is created that uses a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="df059-119">最初の 2 つの分岐では `ConsoleColorScope` アクティビティを使用しますが、3 つ目の分岐は使用しません。</span><span class="sxs-lookup"><span data-stu-id="df059-119">The first two branches use the `ConsoleColorScope` activity and the third branch does not.</span></span> <span data-ttu-id="df059-120">3 つの分岐にはいずれも 2 つの <xref:System.Activities.Statements.WriteLine> アクティビティと 1 つの <xref:System.Activities.Statements.Delay> アクティビティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="df059-120">All three branches contain two <xref:System.Activities.Statements.WriteLine> activities and a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="df059-121"><xref:System.Activities.Statements.Parallel> アクティビティが実行されると、その分岐に含まれるアクティビティはインターリーブ形式で実行されますが、それぞれの子アクティビティが実行されるため、`ConsoleColorProperty` によって適切なコンソールの色が適用されます。</span><span class="sxs-lookup"><span data-stu-id="df059-121">When the <xref:System.Activities.Statements.Parallel> activity executes, the activities that are contained in the branches execute in an interleaved manner, but as each child activity executes the correct console color is applied by the `ConsoleColorProperty`.</span></span>  
  
```csharp  
Activity wf = new Parallel  
{  
    Branches =
    {  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Blue,  
            Body = new Sequence  
            {  
                Activities =
                {  
                    new WriteLine  
                    {  
                        Text = "Start blue text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End blue text."  
                    }  
                }  
            }  
        },  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Red,  
            Body = new Sequence  
            {  
                Activities =
                {  
                    new WriteLine  
                    {  
                        Text = "Start red text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End red text."  
                    }  
                }  
            }  
        },  
        new Sequence  
        {  
            Activities =
            {  
                new WriteLine  
                {  
                    Text = "Start default text."  
                },  
                new Delay  
                {  
                    Duration = TimeSpan.FromSeconds(1)  
                },  
                new WriteLine  
                {  
                    Text = "End default text."  
                }  
            }  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 <span data-ttu-id="df059-122">このワークフローを呼び出すと、次の出力がコンソール ウィンドウに書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="df059-122">When the workflow is invoked, the following output is written to the console window.</span></span>  
  
```console  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
> <span data-ttu-id="df059-123">前の出力には示していませんが、コンソール ウィンドウの各テキスト行は、指定した色で表示されます。</span><span class="sxs-lookup"><span data-stu-id="df059-123">Although it is not shown in the previous output, each line of text in the console window is displayed in the indicated color.</span></span>  
  
 <span data-ttu-id="df059-124">ワークフロー実行プロパティは、カスタム アクティビティ作成者が使用できます。また、このプロパティには、<xref:System.ServiceModel.Activities.CorrelationScope> や <xref:System.Activities.Statements.TransactionScope> などのアクティビティ向けにハンドル管理の機構も用意されています。</span><span class="sxs-lookup"><span data-stu-id="df059-124">Workflow execution properties can be used by custom activity authors, and they also provide the mechanism for handle management for activities such as the <xref:System.ServiceModel.Activities.CorrelationScope> and <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df059-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="df059-125">See also</span></span>

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
