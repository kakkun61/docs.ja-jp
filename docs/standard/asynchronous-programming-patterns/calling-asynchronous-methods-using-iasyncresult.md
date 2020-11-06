---
title: IAsyncResult を使用した非同期メソッドの呼び出し
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- ending asynchronous operations
- waiting for asynchronous operations
- asynchronous method calling
- calling asynchronous methods
- asynchronous programming, calling asynchronous methods
- IAsyncResult interface, calling asynchronous methods
- stopping asynchronous operations
ms.assetid: 07fba116-045b-473c-a0b7-acdbeb49861f
ms.openlocfilehash: 8e11f734410e266aa4c175551e8a3fbf5d9236c9
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888907"
---
# <a name="calling-asynchronous-methods-using-iasyncresult"></a><span data-ttu-id="25a14-102">IAsyncResult を使用した非同期メソッドの呼び出し</span><span class="sxs-lookup"><span data-stu-id="25a14-102">Calling Asynchronous Methods Using IAsyncResult</span></span>

<span data-ttu-id="25a14-103">.NET ライブラリとサードパーティのクラス ライブラリの型では、アプリケーションのメイン スレッド以外のスレッドで非同期操作を実行しながら、アプリケーションを実行し続けることを許可するメソッドを提供できます。</span><span class="sxs-lookup"><span data-stu-id="25a14-103">Types in the .NET libraries and third-party class libraries can provide methods that allow an application to continue executing while performing asynchronous operations in threads other than the main application thread.</span></span> <span data-ttu-id="25a14-104">次のセクションでは、コード例を取り上げ、<xref:System.IAsyncResult> 設計パターンを使用する非同期メソッドをさまざまな方法で呼び出します。</span><span class="sxs-lookup"><span data-stu-id="25a14-104">The following sections describe and provide code examples that demonstrate the different ways you can call asynchronous methods that use the <xref:System.IAsyncResult> design pattern.</span></span>  
  
- <span data-ttu-id="25a14-105">[非同期操作の終了によるアプリケーション実行のブロック](blocking-application-execution-by-ending-an-async-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="25a14-105">[Blocking Application Execution by Ending an Async Operation](blocking-application-execution-by-ending-an-async-operation.md).</span></span>  
  
- <span data-ttu-id="25a14-106">[AsyncWaitHandle の使用によるアプリケーション実行のブロック](blocking-application-execution-using-an-asyncwaithandle.md)。</span><span class="sxs-lookup"><span data-stu-id="25a14-106">[Blocking Application Execution Using an AsyncWaitHandle](blocking-application-execution-using-an-asyncwaithandle.md).</span></span>  
  
- <span data-ttu-id="25a14-107">[非同期操作のステータスのポーリング](polling-for-the-status-of-an-asynchronous-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="25a14-107">[Polling for the Status of an Asynchronous Operation](polling-for-the-status-of-an-asynchronous-operation.md).</span></span>  
  
- <span data-ttu-id="25a14-108">[AsyncCallback デリゲートの使用による非同期操作の終了](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md)。</span><span class="sxs-lookup"><span data-stu-id="25a14-108">[Using an AsyncCallback Delegate to End an Asynchronous Operation](using-an-asynccallback-delegate-to-end-an-asynchronous-operation.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25a14-109">参照</span><span class="sxs-lookup"><span data-stu-id="25a14-109">See also</span></span>

- [<span data-ttu-id="25a14-110">イベント ベースの非同期パターン (EAP)</span><span class="sxs-lookup"><span data-stu-id="25a14-110">Event-based Asynchronous Pattern (EAP)</span></span>](event-based-asynchronous-pattern-eap.md)
- [<span data-ttu-id="25a14-111">イベントベースの非同期パターンの概要</span><span class="sxs-lookup"><span data-stu-id="25a14-111">Event-based Asynchronous Pattern Overview</span></span>](event-based-asynchronous-pattern-overview.md)
