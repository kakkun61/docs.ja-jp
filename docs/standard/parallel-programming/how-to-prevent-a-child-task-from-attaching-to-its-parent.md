---
title: '方法: 子タスクがその親にアタッチしないようにする'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- tasks, preventing attachments
ms.assetid: c0fb85d4-9e80-4905-9f65-29acc54201c4
ms.openlocfilehash: 5874f07d48f99573af78c07a6ab6a0f386e6bc9a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95705905"
---
# <a name="how-to-prevent-a-child-task-from-attaching-to-its-parent"></a><span data-ttu-id="13860-102">方法: 子タスクがその親にアタッチしないようにする</span><span class="sxs-lookup"><span data-stu-id="13860-102">How to: Prevent a Child Task from Attaching to its Parent</span></span>

<span data-ttu-id="13860-103">このドキュメントでは、子タスクが親タスクにアタッチしないようにする方法を紹介します。</span><span class="sxs-lookup"><span data-stu-id="13860-103">This document demonstrates how to prevent a child task from attaching to the parent task.</span></span> <span data-ttu-id="13860-104">サード パーティによって書き込まれ、タスクも使用するコンポーネントを呼び出す場合は、子タスクがその親にアタッチしないようにすると便利です。</span><span class="sxs-lookup"><span data-stu-id="13860-104">Preventing a child task from attaching to its parent is useful when you call a component that is written by a third party and that also uses tasks.</span></span> <span data-ttu-id="13860-105">たとえば、<xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> オプションを使用して <xref:System.Threading.Tasks.Task> または <xref:System.Threading.Tasks.Task%601> オブジェクトを作成するサード パーティ コンポーネントが長時間実行されているか、ハンドルされない例外をスローする場合、コードで問題が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="13860-105">For example, a third-party component that uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent?displayProperty=nameWithType> option to create a <xref:System.Threading.Tasks.Task> or <xref:System.Threading.Tasks.Task%601> object can cause problems in your code if it is long-running or throws an unhandled exception.</span></span>  
  
## <a name="example"></a><span data-ttu-id="13860-106">例</span><span class="sxs-lookup"><span data-stu-id="13860-106">Example</span></span>  

 <span data-ttu-id="13860-107">次の例では、子タスクが親にアタッチしないようにする効果と、既定のオプションを使用する効果を比較します。</span><span class="sxs-lookup"><span data-stu-id="13860-107">The following example compares the effects of using the default options to the effects of preventing a child task from attaching to the parent.</span></span> <span data-ttu-id="13860-108">この例では、<xref:System.Threading.Tasks.Task> オブジェクトも使用する、サード パーティ ライブラリを呼び出す、<xref:System.Threading.Tasks.Task> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="13860-108">The example creates a <xref:System.Threading.Tasks.Task> object that calls into a third-party library that also uses a <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="13860-109">サード パーティ ライブラリでは <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> オプションを使用して、<xref:System.Threading.Tasks.Task> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="13860-109">The third-party library uses the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> option to create the <xref:System.Threading.Tasks.Task> object.</span></span> <span data-ttu-id="13860-110">アプリケーションでは <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> オプションを使用して、親タスクを作成します。</span><span class="sxs-lookup"><span data-stu-id="13860-110">The application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option to create the parent task.</span></span> <span data-ttu-id="13860-111">このオプションは、子タスクの <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> 指定を削除するようにランタイムに指示します。</span><span class="sxs-lookup"><span data-stu-id="13860-111">This option instructs the runtime to remove the <xref:System.Threading.Tasks.TaskCreationOptions.AttachedToParent> specification in child tasks.</span></span>  
  
 [!code-csharp[TPL_DenyChildAttach#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpl_denychildattach/cs/denychildattach.cs#1)]
 [!code-vb[TPL_DenyChildAttach#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpl_denychildattach/vb/denychildattach.vb#1)]  
  
 <span data-ttu-id="13860-112">親タスクはすべての子タスクが終了するまで終了しないため、長時間実行される子タスクによって、アプリケーション全体のパフォーマンスが低下する場合があります。</span><span class="sxs-lookup"><span data-stu-id="13860-112">Because a parent task does not finish until all child tasks finish, a long-running child task can cause the overall application to perform poorly.</span></span> <span data-ttu-id="13860-113">この例では、アプリケーションが既定のオプションを使用して親タスクを作成する場合に、親タスクが終了する前に子タスクが終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="13860-113">In this example, when the application uses the default options to create the parent task, the child task must finish before the parent task finishes.</span></span> <span data-ttu-id="13860-114">アプリケーションで <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> オプションを使用する場合、子は親にアタッチされません。</span><span class="sxs-lookup"><span data-stu-id="13860-114">When the application uses the <xref:System.Threading.Tasks.TaskCreationOptions.DenyChildAttach?displayProperty=nameWithType> option, the child is not attached to the parent.</span></span> <span data-ttu-id="13860-115">そのため、アプリケーションは、親タスクの終了後、子タスクが終了するのを待機する前に、追加の作業を実行できます。</span><span class="sxs-lookup"><span data-stu-id="13860-115">Therefore, the application can perform additional work after the parent task finishes and before it must wait for the child task to finish.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13860-116">参照</span><span class="sxs-lookup"><span data-stu-id="13860-116">See also</span></span>

- [<span data-ttu-id="13860-117">タスク ベースの非同期プログラミング</span><span class="sxs-lookup"><span data-stu-id="13860-117">Task-based Asynchronous Programming</span></span>](task-based-asynchronous-programming.md)
