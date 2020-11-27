---
title: UriTemplate テーブル ディスパッチャーのサンプル
ms.date: 03/30/2017
ms.assetid: 3b32975d-ba90-4c5c-83bc-2fbb48f11c0c
ms.openlocfilehash: 57489264de62b6adbca1c98230a0f90735b3918a
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294951"
---
# <a name="uritemplate-table-dispatcher-sample"></a><span data-ttu-id="18553-102">UriTemplate テーブル ディスパッチャーのサンプル</span><span class="sxs-lookup"><span data-stu-id="18553-102">UriTemplate Table Dispatcher Sample</span></span>

<span data-ttu-id="18553-103"><xref:System.UriTemplateTable> クラスには、<xref:System.UriTemplate> インスタンスのセットを使用するための、ディクショナリに似た結合テーブル構造が用意されています。</span><span class="sxs-lookup"><span data-stu-id="18553-103">The <xref:System.UriTemplateTable> class provides a dictionary-like associative table structure for working with a set of <xref:System.UriTemplate> instances.</span></span> <span data-ttu-id="18553-104">このサンプルでは、`UriTemplateTable` クラスの一般的な使用シナリオとして、`UriTemplateTable` を使用してビルドされた基本的なディスパッチ エンジンを示します。</span><span class="sxs-lookup"><span data-stu-id="18553-104">This sample demonstrates a basic dispatching engine built using `UriTemplateTable`, a common usage scenario for the `UriTemplateTable` class.</span></span>  
  
 <span data-ttu-id="18553-105">このサンプルでは、次の `UriTemplateTable` クラスに関連する重要な概念を示します。</span><span class="sxs-lookup"><span data-stu-id="18553-105">This sample demonstrates the following key concepts for the `UriTemplateTable` class:</span></span>  
  
- <span data-ttu-id="18553-106">`UriTemplates` の `UriTemplateTable` とのデリゲートの関連付け。</span><span class="sxs-lookup"><span data-stu-id="18553-106">Associating delegates with `UriTemplates` in a `UriTemplateTable`.</span></span>  
  
- <span data-ttu-id="18553-107"><xref:System.UriTemplateTable.MatchSingle%2A> を使用した特定の URI の正しいハンドラ デリゲートの取得。</span><span class="sxs-lookup"><span data-stu-id="18553-107">Using <xref:System.UriTemplateTable.MatchSingle%2A> to obtain the correct handler delegate for a particular URI.</span></span>  
  
- <span data-ttu-id="18553-108">要求を処理するためのハンドラー デリゲートの呼び出し。</span><span class="sxs-lookup"><span data-stu-id="18553-108">Invoking the handler delegate to process the request.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="18553-109">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="18553-109">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="18553-110">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="18553-110">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="18553-111">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="18553-111">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="18553-112">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="18553-112">The samples may already be installed on your machine.</span></span> <span data-ttu-id="18553-113">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="18553-113">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="18553-114">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="18553-114">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="18553-115">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="18553-115">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\UriTemplateDispatcher`  
  
## <a name="see-also"></a><span data-ttu-id="18553-116">関連項目</span><span class="sxs-lookup"><span data-stu-id="18553-116">See also</span></span>

- [<span data-ttu-id="18553-117">UriTemplate テーブル</span><span class="sxs-lookup"><span data-stu-id="18553-117">UriTemplate Table</span></span>](uritemplate-table-sample.md)
- [<span data-ttu-id="18553-118">UriTemplate</span><span class="sxs-lookup"><span data-stu-id="18553-118">UriTemplate</span></span>](uritemplate-sample.md)
