---
title: '方法: ChannelFactory を使用する'
description: WCF クライアントを使用してサービスにアクセスするために複数のチャネルを作成するチャネルファクトリを作成する方法について説明します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: d48f01b5-582b-4c8b-b547-8adddae7e371
ms.openlocfilehash: dd767443fefb16ebc02300bffa4264357f12c3ae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280586"
---
# <a name="how-to-use-the-channelfactory"></a><span data-ttu-id="14f2c-103">方法: ChannelFactory を使用する</span><span class="sxs-lookup"><span data-stu-id="14f2c-103">How to: Use the ChannelFactory</span></span>

<span data-ttu-id="14f2c-104"><xref:System.ServiceModel.ChannelFactory%601> ジェネリック クラスは、複数チャネルの作成に使用できるチャネル ファクトリの作成を必要とする高度なシナリオで使用します。</span><span class="sxs-lookup"><span data-stu-id="14f2c-104">The generic <xref:System.ServiceModel.ChannelFactory%601> class is used in advanced scenarios that require the creation of a channel factory that can be used to create more than one channel.</span></span>  
  
### <a name="to-create-and-use-the-channelfactory-class"></a><span data-ttu-id="14f2c-105">ChannelFactory クラスの作成方法と使用方法</span><span class="sxs-lookup"><span data-stu-id="14f2c-105">To create and use the ChannelFactory class</span></span>  
  
1. <span data-ttu-id="14f2c-106">Windows Communication Foundation (WCF) サービスをビルドして実行します。</span><span class="sxs-lookup"><span data-stu-id="14f2c-106">Build and run an Windows Communication Foundation (WCF) service.</span></span> <span data-ttu-id="14f2c-107">詳細については、「 [サービスの設計と実装](../designing-and-implementing-services.md)」、「 [サービスの構成](../configuring-services.md)」、および「 [ホスティングサービス](../hosting-services.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="14f2c-107">For more information, see [Designing and Implementing Services](../designing-and-implementing-services.md), [Configuring Services](../configuring-services.md), and [Hosting Services](../hosting-services.md).</span></span>  
  
2. <span data-ttu-id="14f2c-108">[ServiceModel メタデータユーティリティツール (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md)を使用して、クライアントのコントラクト (インターフェイス) を生成します。</span><span class="sxs-lookup"><span data-stu-id="14f2c-108">Use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the contract (interface) for the client.</span></span>  
  
3. <span data-ttu-id="14f2c-109">クライアント コード内で、<xref:System.ServiceModel.ChannelFactory%601> クラスを使用して複数のエンドポイント リスナーを作成します。</span><span class="sxs-lookup"><span data-stu-id="14f2c-109">In the client code, use the <xref:System.ServiceModel.ChannelFactory%601> class to create multiple endpoint listeners.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14f2c-110">例</span><span class="sxs-lookup"><span data-stu-id="14f2c-110">Example</span></span>  

 [!code-csharp[c_HowToUseChannelFactory#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howtousechannelfactory/cs/source.cs#1)]
 [!code-vb[c_HowToUseChannelFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howtousechannelfactory/vb/source.vb#1)]
