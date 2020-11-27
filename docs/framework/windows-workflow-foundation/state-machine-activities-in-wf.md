---
title: WF のステート マシン アクティビティ
ms.date: 03/30/2017
ms.assetid: 93312eaf-07e0-4a55-b4f7-4cdbbc4dee2d
ms.openlocfilehash: dd0bfae1f24ecd9f98c0a2f04265581f880202a7
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96261723"
---
# <a name="state-machine-activities-in-wf"></a><span data-ttu-id="fc5c0-102">WF のステート マシン アクティビティ</span><span class="sxs-lookup"><span data-stu-id="fc5c0-102">State Machine Activities in WF</span></span>

<span data-ttu-id="fc5c0-103">.NET Framework 4.5 には、システムによって提供されるアクティビティと、ステートマシンワークフローを作成するためのアクティビティデザイナーが用意されています。</span><span class="sxs-lookup"><span data-stu-id="fc5c0-103">.NET Framework 4.5 provides several system-provided activities and activity designers for creating state machine workflows.</span></span>  
  
|||  
|-|-|  
|<xref:System.Activities.Statements.StateMachine>|<span data-ttu-id="fc5c0-104">使い慣れたステート マシン パラダイムを使用して、含まれているアクティビティを実行します。</span><span class="sxs-lookup"><span data-stu-id="fc5c0-104">Executes contained activities using the familiar state machine paradigm.</span></span>|  
|<xref:System.Activities.Statements.State>|<span data-ttu-id="fc5c0-105">ステート マシンの状態を表します。</span><span class="sxs-lookup"><span data-stu-id="fc5c0-105">Represents a state in a state machine.</span></span>|  
|<xref:System.Activities.Core.Presentation.FinalState>|<span data-ttu-id="fc5c0-106">ステート マシンの最終状態を表します。</span><span class="sxs-lookup"><span data-stu-id="fc5c0-106">Represents a terminating state in a state machine.</span></span> <span data-ttu-id="fc5c0-107"><xref:System.Activities.Core.Presentation.FinalState> は、使用すると、最終状態として事前に構成済みの <xref:System.Activities.Statements.State> を作成するアクティビティ デザイナーです。</span><span class="sxs-lookup"><span data-stu-id="fc5c0-107"><xref:System.Activities.Core.Presentation.FinalState> is an activity designer that when used creates a <xref:System.Activities.Statements.State> preconfigured as a terminating state.</span></span> <span data-ttu-id="fc5c0-108">詳細については、「 [Finalstate アクティビティデザイナー](/visualstudio/workflow-designer/finalstate-activity-designer)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc5c0-108">For more information, see [FinalState Activity Designer](/visualstudio/workflow-designer/finalstate-activity-designer).</span></span>|  
|<xref:System.Activities.Statements.Transition>|<span data-ttu-id="fc5c0-109">2 つの状態間の遷移を表します。</span><span class="sxs-lookup"><span data-stu-id="fc5c0-109">Represents the transition between two states.</span></span> <span data-ttu-id="fc5c0-110">用の **ツールボックス** アイテムはありません <xref:System.Activities.Statements.Transition> 。遷移は、ワークフローデザイナーで2つの状態の間の線をドラッグアンドドロップするか、ある状態を別の状態に移動したときに表示される三角形の状態を削除することによって作成されます。</span><span class="sxs-lookup"><span data-stu-id="fc5c0-110">There is no **Toolbox** item for <xref:System.Activities.Statements.Transition>; transitions are created on the workflow designer by dragging and dropping a line between two states, or by dropping a state on the triangles that appear when one state is hovered over another.</span></span> <span data-ttu-id="fc5c0-111">詳細については、「 [Transition アクティビティデザイナー](/visualstudio/workflow-designer/transition-activity-designer)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fc5c0-111">For more information, see [Transition Activity Designer](/visualstudio/workflow-designer/transition-activity-designer).</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fc5c0-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="fc5c0-112">See also</span></span>

- [<span data-ttu-id="fc5c0-113">チュートリアル入門</span><span class="sxs-lookup"><span data-stu-id="fc5c0-113">Getting Started Tutorial</span></span>](getting-started-tutorial.md)
