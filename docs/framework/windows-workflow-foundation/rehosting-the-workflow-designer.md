---
title: ワークフロー デザイナーのホスト変更
description: Windows ワークフローデザイナーは、ワークフローを作成、変更、および監視するために、Visual Studio の外部の環境で再ホストできます。
ms.date: 03/30/2017
ms.assetid: bec1fc28-f902-4edb-86c5-436cec802c2b
ms.openlocfilehash: 8c3a67d0beecdfcf4f99580bb6ec25fea6473718
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245901"
---
# <a name="rehosting-the-workflow-designer"></a><span data-ttu-id="4c755-103">ワークフロー デザイナーのホスト変更</span><span class="sxs-lookup"><span data-stu-id="4c755-103">Rehosting the Workflow Designer</span></span>

<span data-ttu-id="4c755-104">Windows ワークフローデザイナーは、ワークフローを作成、変更、および監視するために、Visual Studio 2012 の外部の環境で再ホストできます。</span><span class="sxs-lookup"><span data-stu-id="4c755-104">The Windows Workflow Designer can be rehosted in environments outside of Visual Studio 2012 for the purposes of creating, modifying, and monitoring workflows.</span></span>

 <span data-ttu-id="4c755-105"><xref:System.Activities.Presentation.WorkflowDesigner> 型はキャンバス、プロパティ グリッド、および他の要素のラッパーであり、デザイナーのホスト変更シナリオの多くに対応する基本的なプログラミング モデルを公開しています。</span><span class="sxs-lookup"><span data-stu-id="4c755-105">The <xref:System.Activities.Presentation.WorkflowDesigner> type is a wrapper of the canvas, property grid, and other elements, and exposes a basic programming model to handle the majority of designer rehosting scenarios.</span></span> <span data-ttu-id="4c755-106"><xref:System.Activities.Presentation.WorkflowDesigner>Windows Presentation Foundation (WPF) アプリケーション内でをホストすることは、ワークフローデザイナーの一般的な再ホスティングシナリオです。</span><span class="sxs-lookup"><span data-stu-id="4c755-106">Hosting the <xref:System.Activities.Presentation.WorkflowDesigner> inside a Windows Presentation Foundation (WPF) application is a common rehosting scenario for Workflow Designer.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="4c755-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="4c755-107">In This Section</span></span>

 [<span data-ttu-id="4c755-108">タスク 1:新しい Windows Presentation Foundation アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="4c755-108">Task 1: Create a New Windows Presentation Foundation Application</span></span>](task-1-create-a-new-wpf-app.md)

 [<span data-ttu-id="4c755-109">タスク 2:ワークフロー デザイナーのホスティング</span><span class="sxs-lookup"><span data-stu-id="4c755-109">Task 2: Host the Workflow Designer</span></span>](task-2-host-the-workflow-designer.md)

 [<span data-ttu-id="4c755-110">タスク 3:ツールボックス ペインと PropertyGrid ペインの作成</span><span class="sxs-lookup"><span data-stu-id="4c755-110">Task 3: Create the Toolbox and PropertyGrid Panes</span></span>](task-3-create-the-toolbox-and-propertygrid-panes.md)

 [<span data-ttu-id="4c755-111">再ホストされたワークフロー デザイナーにおける Workflow Foundation 4.5 の新機能のサポート</span><span class="sxs-lookup"><span data-stu-id="4c755-111">Support for New Workflow Foundation 4.5 Features in the Rehosted Workflow Designer</span></span>](wf-features-in-the-rehosted-workflow-designer.md)

## <a name="see-also"></a><span data-ttu-id="4c755-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="4c755-112">See also</span></span>

- [<span data-ttu-id="4c755-113">ワークフロー デザイン操作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="4c755-113">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
