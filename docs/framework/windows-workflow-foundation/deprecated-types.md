---
title: Windows Workflow Foundation で非推奨の型
ms.date: 03/30/2017
ms.assetid: 4aebe928-a964-4c1c-abf7-0dbbd3604b13
ms.openlocfilehash: 011f13a56695efdd9e964ef1e6c1099b0acc2710
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95713341"
---
# <a name="deprecated-types-in-windows-workflow-foundation"></a><span data-ttu-id="df9a7-102">Windows Workflow Foundation で非推奨の型</span><span class="sxs-lookup"><span data-stu-id="df9a7-102">Deprecated types in Windows Workflow Foundation</span></span>
<span data-ttu-id="df9a7-103">.NET 4 の段階で、ワークフロー チームは、<xref:System.Activities> 名前空間のまったく新しいワークフロー エンジンをリリースしました。</span><span class="sxs-lookup"><span data-stu-id="df9a7-103">In .NET 4 the Workflow Team released an all new Workflow engine in the <xref:System.Activities> namespace.</span></span> <span data-ttu-id="df9a7-104">.NET Framework 4.5 Beta のリリースでは、"WF 3"、、および名前空間のほとんどの型を <xref:System.Workflow.Activities> <xref:System.Workflow.ComponentModel>  <xref:System.Workflow.Runtime> 廃止としてマークしています。</span><span class="sxs-lookup"><span data-stu-id="df9a7-104">With the release of .NET Framework 4.5 Beta we are marking most of the types in the "WF 3" <xref:System.Workflow.Activities>, <xref:System.Workflow.ComponentModel>, and  <xref:System.Workflow.Runtime> namespaces as obsolete.</span></span>

## <a name="obsolete-namespaces-and-tools"></a><span data-ttu-id="df9a7-105">旧式の名前空間とツール</span><span class="sxs-lookup"><span data-stu-id="df9a7-105">Obsolete namespaces and tools</span></span>
 <span data-ttu-id="df9a7-106">次のアセンブリには、今後非推奨とされるパブリック型が 1 つ以上含まれています：</span><span class="sxs-lookup"><span data-stu-id="df9a7-106">The following assemblies have one or more public types that will be deprecated:</span></span>

- <span data-ttu-id="df9a7-107">System.Workflow.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="df9a7-107">System.Workflow.Activities.dll</span></span>

- <span data-ttu-id="df9a7-108">System.Workflow.ComponentModel.dll</span><span class="sxs-lookup"><span data-stu-id="df9a7-108">System.Workflow.ComponentModel.dll</span></span>

- <span data-ttu-id="df9a7-109">System.Workflow.Runtime.dll</span><span class="sxs-lookup"><span data-stu-id="df9a7-109">System.Workflow.Runtime.dll</span></span>

- <span data-ttu-id="df9a7-110">System.WorkflowServices.dll</span><span class="sxs-lookup"><span data-stu-id="df9a7-110">System.WorkflowServices.dll</span></span>

- <span data-ttu-id="df9a7-111">Microsoft.Workflow.DebugController.dll</span><span class="sxs-lookup"><span data-stu-id="df9a7-111">Microsoft.Workflow.DebugController.dll</span></span>

- <span data-ttu-id="df9a7-112">Microsoft.Workflow.Compiler.exe</span><span class="sxs-lookup"><span data-stu-id="df9a7-112">Microsoft.Workflow.Compiler.exe</span></span>

- <span data-ttu-id="df9a7-113">Wfc.exe</span><span class="sxs-lookup"><span data-stu-id="df9a7-113">Wfc.exe</span></span>

 <span data-ttu-id="df9a7-114">その結果、非推奨とされた WF 3 API を今後使用すると、ビルド時に警告が発生し、次のようなメッセージが表示されます：</span><span class="sxs-lookup"><span data-stu-id="df9a7-114">As a result, customers who are using the deprecated WF 3 APIs will encounter build warnings with a message similar to the following:</span></span>

 <span data-ttu-id="df9a7-115">**警告 BC40000: X は互換性のために残されています: WF 3 の型は非推奨とされます。代わりに、WF 4 を使用してください。**</span><span class="sxs-lookup"><span data-stu-id="df9a7-115">**Warning BC40000: X is obsolete: WF 3 types are deprecated. Please use WF 4 instead.**</span></span> <span data-ttu-id="df9a7-116">WF 3 の型は .NET Framework の将来のリリースで削除されますが、実際の削除時期はまだ未定です (4.5 では行われません)。</span><span class="sxs-lookup"><span data-stu-id="df9a7-116">We will remove the types from the .NET Framework in a future release, but we have not yet determined that timeframe (not in 4.5).</span></span> <span data-ttu-id="df9a7-117">この段階的な変更は、今後の方向性を示し、お客様が WF 4 モデルに余裕をもって移行するための期間を確保するためのものです。</span><span class="sxs-lookup"><span data-stu-id="df9a7-117">This current step allows us to communicate our direction to our customers and allow them plenty of time to move to the new WF4 model.</span></span> <span data-ttu-id="df9a7-118">もちろん、 [Microsoft サポートライフサイクルポリシー](/lifecycle/)では、これらの WF 3 の種類を引き続きサポートします。</span><span class="sxs-lookup"><span data-stu-id="df9a7-118">We will, of course, continue to support these WF 3 types under the [Microsoft Support Lifecycle Policy](/lifecycle/).</span></span> <span data-ttu-id="df9a7-119">既存の WF3 アプリケーションは .NET Framework 4.5 では問題なく実行され、Visual Studio 2012 は新規および既存の WF3 ベースのソリューションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="df9a7-119">Existing WF3 applications will run without issue on .NET Framework 4.5, and Visual Studio 2012 will support new and existing WF3-based solutions.</span></span>

 <span data-ttu-id="df9a7-120"><xref:System.Workflow.Activities.Rules> 名前空間に含まれるルール関連の型については、WF 4.5 には相当する型がないため、非推奨扱いにはなりません。</span><span class="sxs-lookup"><span data-stu-id="df9a7-120">Rules related types in the <xref:System.Workflow.Activities.Rules> namespace, which do not have a replacement in WF 4.5, have not been deprecated.</span></span>

 <span data-ttu-id="df9a7-121">WF 4 にアプリケーションを移行するお客様は、 [ワークフロー4の移行](migration-guidance.md)に関するガイダンスのヘルプを参照してください。</span><span class="sxs-lookup"><span data-stu-id="df9a7-121">Customers who want to migrate their applications to WF 4 will find help in the [Workflow 4 Migration Guidance](migration-guidance.md).</span></span>
