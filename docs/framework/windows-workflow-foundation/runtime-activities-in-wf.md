---
title: WF のランタイム アクティビティ
ms.date: 03/30/2017
ms.assetid: e5ae8c31-19bc-4655-88b3-6b75cd6a1bd5
ms.openlocfilehash: b0472c669d69d9397843a004bee1bb2c15e139c4
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96245703"
---
# <a name="runtime-activities-in-wf"></a><span data-ttu-id="f7e7c-102">WF のランタイム アクティビティ</span><span class="sxs-lookup"><span data-stu-id="f7e7c-102">Runtime Activities in WF</span></span>

[!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="f7e7c-103">には、永続化や終了などのワークフロー ランタイムの機能にアクセスするために、システムによって提供されるアクティビティがいくつか用意されています。</span><span class="sxs-lookup"><span data-stu-id="f7e7c-103">provides several system-provided activities for accessing the features of the workflow runtime, such as persistence and termination.</span></span>  
  
|<span data-ttu-id="f7e7c-104">アクティビティ</span><span class="sxs-lookup"><span data-stu-id="f7e7c-104">Activity</span></span>|<span data-ttu-id="f7e7c-105">説明</span><span class="sxs-lookup"><span data-stu-id="f7e7c-105">Description</span></span>|  
|--------------|-----------------|  
|<xref:System.Activities.Statements.Persist>|<span data-ttu-id="f7e7c-106">ワークフローがその状態を永続化するように明示的に要求します。</span><span class="sxs-lookup"><span data-stu-id="f7e7c-106">Explicitly requests that the workflow persist its state.</span></span>|  
|<xref:System.Activities.Statements.TerminateWorkflow>|<span data-ttu-id="f7e7c-107">実行中のワークフロー インスタンスを終了します。</span><span class="sxs-lookup"><span data-stu-id="f7e7c-107">Terminates the running workflow instance.</span></span>|  
|<xref:System.Activities.Statements.NoPersistScope>|<span data-ttu-id="f7e7c-108">子アクティビティの永続化を防ぐコンテナー アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="f7e7c-108">A container activity that prevents child activities from persisting.</span></span>|
