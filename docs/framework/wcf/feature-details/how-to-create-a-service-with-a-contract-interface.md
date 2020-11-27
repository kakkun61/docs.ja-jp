---
title: '方法: コントラクト インターフェイスを使用してサービスを作成する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 7b6803f6-d6f9-4cc2-9f1b-6f4c920475d5
ms.openlocfilehash: 2234e6fe8d0ee2e0029a061ba96ef84f840f0c9b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286345"
---
# <a name="how-to-create-a-service-with-a-contract-interface"></a><span data-ttu-id="2f504-102">方法: コントラクト インターフェイスを使用してサービスを作成する</span><span class="sxs-lookup"><span data-stu-id="2f504-102">How to: Create a Service with a Contract Interface</span></span>

<span data-ttu-id="2f504-103">Windows Communication Foundation (WCF) コントラクトを作成するには、インターフェイスを使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="2f504-103">The preferred way to create a Windows Communication Foundation (WCF) contract is by using an interface.</span></span> <span data-ttu-id="2f504-104">このコントラクトでは、サービスが提供する操作にアクセスするために必要なメッセージのコレクションと構造を指定します。</span><span class="sxs-lookup"><span data-stu-id="2f504-104">This contract specifies the collection and structure of messages required to access the operations the service offers.</span></span> <span data-ttu-id="2f504-105">このインターフェイスでは、インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用し、公開するメソッドに <xref:System.ServiceModel.OperationContractAttribute> クラスを適用して、入力と出力の種類を定義します。</span><span class="sxs-lookup"><span data-stu-id="2f504-105">This interface defines the input and output types by applying the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface and the <xref:System.ServiceModel.OperationContractAttribute> class to the methods that you want to expose.</span></span>  
  
 <span data-ttu-id="2f504-106">サービスコントラクトの詳細については、「 [サービスコントラクトの設計](../designing-service-contracts.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f504-106">For more information about service contracts, see [Designing Service Contracts](../designing-service-contracts.md).</span></span>  
  
### <a name="creating-a-wcf-contract-with-an-interface"></a><span data-ttu-id="2f504-107">インターフェイスを使用した WCF コントラクトの作成</span><span class="sxs-lookup"><span data-stu-id="2f504-107">Creating a WCF contract with an interface</span></span>  
  
1. <span data-ttu-id="2f504-108">Visual Basic、C#、またはその他の共通言語ランタイム言語を使用して、新しいインターフェイスを作成します。</span><span class="sxs-lookup"><span data-stu-id="2f504-108">Create a new interface using Visual Basic, C#, or any other common language runtime language.</span></span>  
  
2. <span data-ttu-id="2f504-109">インターフェイスに <xref:System.ServiceModel.ServiceContractAttribute> クラスを適用します。</span><span class="sxs-lookup"><span data-stu-id="2f504-109">Apply the <xref:System.ServiceModel.ServiceContractAttribute> class to the interface.</span></span>  
  
3. <span data-ttu-id="2f504-110">インターフェイスのメソッドを定義します。</span><span class="sxs-lookup"><span data-stu-id="2f504-110">Define the methods in the interface.</span></span>  
  
4. <span data-ttu-id="2f504-111"><xref:System.ServiceModel.OperationContractAttribute>パブリック WCF コントラクトの一部として公開する必要がある各メソッドにクラスを適用します。</span><span class="sxs-lookup"><span data-stu-id="2f504-111">Apply the <xref:System.ServiceModel.OperationContractAttribute> class to each method that must be exposed as part of the public WCF contract.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2f504-112">例</span><span class="sxs-lookup"><span data-stu-id="2f504-112">Example</span></span>  

 <span data-ttu-id="2f504-113">次のコード例は、サービス コントラクトを定義するインターフェイスを示しています。</span><span class="sxs-lookup"><span data-stu-id="2f504-113">The following code example shows an interface that defines a service contract.</span></span>  
  
 [!code-csharp[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createcontractwithinterface/cs/source.cs#1)]
 [!code-vb[c_HowTo_CreateContractWithInterface#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_createcontractwithinterface/vb/source.vb#1)]  
  
 <span data-ttu-id="2f504-114"><xref:System.ServiceModel.OperationContractAttribute> クラスが適用されたメソッドは、既定で要求/応答メッセージ パターンを使用します。</span><span class="sxs-lookup"><span data-stu-id="2f504-114">The methods that have the <xref:System.ServiceModel.OperationContractAttribute> class applied use a request-reply message pattern by default.</span></span> <span data-ttu-id="2f504-115">このメッセージパターンの詳細については、「 [方法: Request-Reply コントラクトを作成](how-to-create-a-request-reply-contract.md)する」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f504-115">For more information about this message pattern, see [How to: Create a Request-Reply Contract](how-to-create-a-request-reply-contract.md).</span></span> <span data-ttu-id="2f504-116">属性のプロパティを設定することにより、他のメッセージ パターンを作成および使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="2f504-116">You can also create and use other message patterns by setting properties of the attribute.</span></span> <span data-ttu-id="2f504-117">その他の例については、「 [方法: One-Way コントラクトを作成](how-to-create-a-one-way-contract.md) する」および「 [方法: 双方向コントラクトを作成する](how-to-create-a-duplex-contract.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="2f504-117">For more examples, see [How to: Create a One-Way Contract](how-to-create-a-one-way-contract.md) and [How to: Create a Duplex Contract](how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f504-118">関連項目</span><span class="sxs-lookup"><span data-stu-id="2f504-118">See also</span></span>

- <xref:System.ServiceModel.ServiceContractAttribute>
- <xref:System.ServiceModel.OperationContractAttribute>
