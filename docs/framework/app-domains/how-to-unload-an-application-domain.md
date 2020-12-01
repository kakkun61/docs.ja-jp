---
title: '方法: アプリケーション ドメインをアンロードする'
description: 指定されたアプリケーション ドメインを適切にシャットダウンするために AppDomain.Unload メソッドを使用して .NET のアプリケーション ドメインをアンロードする方法について確認します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Unload method
- application domains, unloading
- unloading application domains
ms.assetid: f356116d-e415-4f7c-a332-6e6a60227192
ms.openlocfilehash: 23a63bf69fab94b890f35b19b45d29f8f22218a3
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96268938"
---
# <a name="how-to-unload-an-application-domain"></a><span data-ttu-id="bbd05-103">方法: アプリケーション ドメインをアンロードする</span><span class="sxs-lookup"><span data-stu-id="bbd05-103">How to: Unload an Application Domain</span></span>

<span data-ttu-id="bbd05-104">アプリケーション ドメインの使用が完了したら、<xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> メソッドを使用してアプリケーション ドメインをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="bbd05-104">When you have finished using an application domain, unload it using the <xref:System.AppDomain.Unload%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="bbd05-105">**Unload** メソッドは、指定したアプリケーション ドメインを正常にシャットダウンします。</span><span class="sxs-lookup"><span data-stu-id="bbd05-105">The **Unload** method gracefully shuts down the specified application domain.</span></span> <span data-ttu-id="bbd05-106">アンロード プロセス中は、新たなスレッドがアプリケーション ドメインにアクセスすることはできません。また、アプリケーション ドメイン固有のデータ構造はすべて解放されます。</span><span class="sxs-lookup"><span data-stu-id="bbd05-106">During the unloading process, no new threads can access the application domain, and all application domain–specific data structures are freed.</span></span>  
  
 <span data-ttu-id="bbd05-107">アプリケーション ドメインに読み込まれたアセンブリは、削除され、以後は使用できません。</span><span class="sxs-lookup"><span data-stu-id="bbd05-107">Assemblies loaded into the application domain are removed and are no longer available.</span></span> <span data-ttu-id="bbd05-108">アプリケーション ドメイン内のアセンブリが、ドメインに中立である場合、アセンブリのデータは、プロセス全体がシャットダウンされるまでメモリに残ります。</span><span class="sxs-lookup"><span data-stu-id="bbd05-108">If an assembly in the application domain is domain-neutral, data for the assembly remains in memory until the entire process is shut down.</span></span> <span data-ttu-id="bbd05-109">プロセス全体をシャットダウンする以外に、ドメインに中立なアセンブリをアンロードする機構はありません。</span><span class="sxs-lookup"><span data-stu-id="bbd05-109">There is no mechanism to unload a domain-neutral assembly other than shutting down the entire process.</span></span> <span data-ttu-id="bbd05-110">アプリケーション ドメインのアンロード要求が機能しない場合は、<xref:System.CannotUnloadAppDomainException> が生成されます。</span><span class="sxs-lookup"><span data-stu-id="bbd05-110">There are situations where the request to unload an application domain does not work and results in a <xref:System.CannotUnloadAppDomainException>.</span></span>  
  
 <span data-ttu-id="bbd05-111">次の例では、`MyDomain` という新しいアプリケーション ドメインを作成し、情報をコンソールに出力してから、アプリケーション ドメインをアンロードします。</span><span class="sxs-lookup"><span data-stu-id="bbd05-111">The following example creates a new application domain called `MyDomain`, prints some information to the console, and then unloads the application domain.</span></span> <span data-ttu-id="bbd05-112">このコードは、アンロードされたアプリケーション ドメインのフレンドリ名をコンソールに出力しようとすることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="bbd05-112">Note that the code then attempts to print the friendly name of the unloaded application domain to the console.</span></span> <span data-ttu-id="bbd05-113">このアクションでは、例外が生成されます。この例外は、プログラムの最後の try ステートメントまたは catch ステートメントで処理されます。</span><span class="sxs-lookup"><span data-stu-id="bbd05-113">This action generates an exception that is handled by the try/catch statements at the end of the program.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bbd05-114">例</span><span class="sxs-lookup"><span data-stu-id="bbd05-114">Example</span></span>  

 [!code-cpp[System.AppDomain.Load#3](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.appdomain.load/cpp/source3.cpp#3)]
 [!code-csharp[System.AppDomain.Load#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.appdomain.load/cs/source3.cs#3)]
 [!code-vb[System.AppDomain.Load#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.appdomain.load/vb/source3.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="bbd05-115">関連項目</span><span class="sxs-lookup"><span data-stu-id="bbd05-115">See also</span></span>

- [<span data-ttu-id="bbd05-116">アプリケーション ドメインを使用したプログラミング</span><span class="sxs-lookup"><span data-stu-id="bbd05-116">Programming with Application Domains</span></span>](application-domains.md#programming-with-application-domains)
- [<span data-ttu-id="bbd05-117">方法: アプリケーション ドメインを作成する</span><span class="sxs-lookup"><span data-stu-id="bbd05-117">How to: Create an Application Domain</span></span>](how-to-create-an-application-domain.md)
- [<span data-ttu-id="bbd05-118">アプリケーション ドメインの使用</span><span class="sxs-lookup"><span data-stu-id="bbd05-118">Using Application Domains</span></span>](use.md)
