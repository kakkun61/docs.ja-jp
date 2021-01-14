---
title: '方法: ワークフローを作成する'
description: このセクションの3つのオプションのいずれかを実行して、この Workflow Foundation チュートリアルの一部としてワークフローを作成します。
ms.date: 03/30/2017
ms.assetid: 87234108-8e21-4cb3-9340-4a1a13f3f98c
ms.openlocfilehash: ea9fd023ba15ae23a10f5b8cf6f82c49ca9af6c8
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/14/2021
ms.locfileid: "98190443"
---
# <a name="how-to-create-a-workflow"></a><span data-ttu-id="6366b-103">方法: ワークフローを作成する</span><span class="sxs-lookup"><span data-stu-id="6366b-103">How to: Create a Workflow</span></span>

<span data-ttu-id="6366b-104">ワークフローは、ビルトイン アクティビティおよびカスタム アクティビティから構築できます。</span><span class="sxs-lookup"><span data-stu-id="6366b-104">Workflows can be constructed from built-in activities as well as from custom activities.</span></span> <span data-ttu-id="6366b-105">このセクションのトピックでは、アクティビティなどの組み込みのアクティビティ <xref:System.Activities.Statements.Flowchart> と、前の「 [How To: Create a activity](how-to-create-an-activity.md) 」トピックのカスタムアクティビティの両方を使用するワークフローを作成する手順について説明します。</span><span class="sxs-lookup"><span data-stu-id="6366b-105">The topics in this section step through creating a workflow that uses both built-in activities such as the <xref:System.Activities.Statements.Flowchart> activity, and the custom activities from the previous [How to: Create an Activity](how-to-create-an-activity.md) topic.</span></span> <span data-ttu-id="6366b-106">このワークフローは、数値推測ゲームをモデル化しています。</span><span class="sxs-lookup"><span data-stu-id="6366b-106">The workflow models a number guessing game.</span></span> <span data-ttu-id="6366b-107">このセクションのトピックの 1 つだけでチュートリアルを終わることができます。目的のスタイルを選択し、手順に従ってください。</span><span class="sxs-lookup"><span data-stu-id="6366b-107">Only one of the topics in this section is required to complete the tutorial; you should pick the style that interests you and follow that step.</span></span> <span data-ttu-id="6366b-108">ただし、必要に応じて、すべてのトピックを修了することができます。</span><span class="sxs-lookup"><span data-stu-id="6366b-108">However, you may complete all of the topics if desired.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6366b-109">チュートリアル入門の各トピックは、前のトピックに応じて異なります。</span><span class="sxs-lookup"><span data-stu-id="6366b-109">Each topic in the Getting Started tutorial depends on the previous topics.</span></span> <span data-ttu-id="6366b-110">このトピックを完了するには、まず「 [方法: アクティビティを作成](how-to-create-an-activity.md)する」を完了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="6366b-110">To complete this topic, you must first complete [How to: Create an Activity](how-to-create-an-activity.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="6366b-111">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="6366b-111">In This Section</span></span>  

 [<span data-ttu-id="6366b-112">方法: シーケンシャル ワークフローを作成する</span><span class="sxs-lookup"><span data-stu-id="6366b-112">How to: Create a Sequential Workflow</span></span>](how-to-create-a-sequential-workflow.md)  
 <span data-ttu-id="6366b-113"><xref:System.Activities.Statements.Sequence> アクティビティを使用してシーケンシャルなワークフローを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6366b-113">Describes how to create a sequential workflow using the <xref:System.Activities.Statements.Sequence> activity.</span></span>  
  
 [<span data-ttu-id="6366b-114">方法: フローチャート ワークフローを作成する</span><span class="sxs-lookup"><span data-stu-id="6366b-114">How to: Create a Flowchart Workflow</span></span>](how-to-create-a-flowchart-workflow.md)  
 <span data-ttu-id="6366b-115"><xref:System.Activities.Statements.Flowchart> アクティビティを使用してフローチャート ワークフローを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6366b-115">Describes how to create a flowchart workflow using the <xref:System.Activities.Statements.Flowchart> activity.</span></span>  
  
 [<span data-ttu-id="6366b-116">方法: ステート マシン ワークフローを作成する</span><span class="sxs-lookup"><span data-stu-id="6366b-116">How to: Create a State Machine Workflow</span></span>](how-to-create-a-state-machine-workflow.md)  
 <span data-ttu-id="6366b-117"><xref:System.Activities.Statements.StateMachine> アクティビティを使用してステート マシン ワークフローを作成する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="6366b-117">Describes how to create a state machine workflow using the <xref:System.Activities.Statements.StateMachine> activity.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6366b-118">こちらもご覧ください</span><span class="sxs-lookup"><span data-stu-id="6366b-118">See also</span></span>

- [<span data-ttu-id="6366b-119">Windows Workflow Foundation プログラミングの新機能</span><span class="sxs-lookup"><span data-stu-id="6366b-119">Windows Workflow Foundation Programming</span></span>](programming.md)
