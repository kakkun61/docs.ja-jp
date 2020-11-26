---
title: 手続き型ワークフロー
description: Workflow Foundation では、手続き型ワークフローは、手続き型言語と同様のフロー制御メソッドを使用します。
ms.date: 03/30/2017
ms.assetid: 52401de9-9115-472d-8fd9-047af6a072b9
ms.openlocfilehash: 13d1b5e55b84687e2a78db1a94317b8b1e33328c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96246031"
---
# <a name="procedural-workflows"></a><span data-ttu-id="17cb4-103">手続き型ワークフロー</span><span class="sxs-lookup"><span data-stu-id="17cb4-103">Procedural Workflows</span></span>

<span data-ttu-id="17cb4-104">手続き型ワークフローでは、手続き型言語と似たフロー制御方法を使用します。</span><span class="sxs-lookup"><span data-stu-id="17cb4-104">Procedural workflows use flow-control methods similar to those found in procedural languages.</span></span> <span data-ttu-id="17cb4-105">これらの構造には `While` と `If` が含まれます。</span><span class="sxs-lookup"><span data-stu-id="17cb4-105">These constructs include `While` and `If`.</span></span> <span data-ttu-id="17cb4-106">これらのワークフローは、<xref:System.Activities.Statements.Flowchart> や <xref:System.Activities.Statements.Sequence> など、他のフロー制御アクティビティを使用して自由に構成できます。</span><span class="sxs-lookup"><span data-stu-id="17cb4-106">These workflows can be freely composed using other flow control activities such as <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Sequence>.</span></span>  
  
## <a name="controlling-execution-flow"></a><span data-ttu-id="17cb4-107">実行フローの制御</span><span class="sxs-lookup"><span data-stu-id="17cb4-107">Controlling Execution Flow</span></span>  

 <span data-ttu-id="17cb4-108">ワークフロー アクティビティ ライブラリには、手続き型言語で使用されるほとんどのフロー制御方法をモデル化するアクティビティがあります。</span><span class="sxs-lookup"><span data-stu-id="17cb4-108">The workflow activity library has activities for modeling most flow-control methods used in procedural languages.</span></span> <span data-ttu-id="17cb4-109">これには以下が含まれます。</span><span class="sxs-lookup"><span data-stu-id="17cb4-109">These include:</span></span>  
  
- <xref:System.Activities.Statements.While>  
  
- <xref:System.Activities.Statements.DoWhile>  
  
- <xref:System.Activities.Statements.ForEach%601>  
  
- <xref:System.Activities.Statements.Parallel>  
  
- <xref:System.Activities.Statements.ParallelForEach%601>  
  
- <xref:System.Activities.Statements.If>  
  
- <xref:System.Activities.Statements.Switch%601>  
  
- <xref:System.Activities.Statements.Pick>  
  
 <span data-ttu-id="17cb4-110">フロー制御アクティビティを使用するには、[ **アクティビティ** ] ツールボックスからデザイナーウィンドウ内の複合アクティビティにドラッグアンドドロップします。</span><span class="sxs-lookup"><span data-stu-id="17cb4-110">To use flow control activities, drag and drop them from the **Activity** toolbox into a composite activity inside the designer window.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17cb4-111">Windows Server AppFabric のホスト機能を使用して Web ファームでワークフローをホストしている場合、AppFabric は異なる AppFabric サーバー間でインスタンスを移動します。</span><span class="sxs-lookup"><span data-stu-id="17cb4-111">If using the hosting features of Windows Server AppFabric to host workflows on a Web farm, AppFabric will move instances between different AppFabric servers.</span></span> <span data-ttu-id="17cb4-112">この機能を利用するには、リソースがすべてのノード間で共有可能になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="17cb4-112">This requires that the resources are able to be shared between all nodes.</span></span>  <span data-ttu-id="17cb4-113">既定の NET 4 ワークフロー アクティビティには、ローカル リソースにアクセスする操作は含まれていません。</span><span class="sxs-lookup"><span data-stu-id="17cb4-113">None of the default NET 4 workflow activities contain any operations that access local resources.</span></span> <span data-ttu-id="17cb4-114">AppFabric には特定のワークフローを不変に設定するメカニズムがないため、ワークフローが移動されるとエラーが発生するようなカスタム アクティビティは絶対に作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="17cb4-114">Since AppFabric does not offer any mechanism to mark a workflow as immovable, a developer must not create custom activities that fail when a workflow is moved.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17cb4-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="17cb4-115">See also</span></span>

- [<span data-ttu-id="17cb4-116">Flowchart のワークフロー</span><span class="sxs-lookup"><span data-stu-id="17cb4-116">Flowchart Workflows</span></span>](flowchart-workflows.md)
