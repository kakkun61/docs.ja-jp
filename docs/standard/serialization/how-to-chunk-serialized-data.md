---
title: '方法 : シリアル化されたデータをチャンクする'
description: データをチャンクして、大きなデータセットに関する問題を回避することができます。 IXmlSerializable インターフェイスを実装して、シリアル化と逆シリアル化を制御します。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- chunking serialized data
- data chunking
- binary serialization, chunking data
- large data set chunking
- serialization, chunking data
- serialization, examples
- binary serialization, examples
ms.assetid: 22f1b818-7e0d-428a-8680-f17d6ebdd185
ms.openlocfilehash: ee8bab4fe7659b1fe5b7edeabc81187d0a13e5bc
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95679001"
---
# <a name="how-to-chunk-serialized-data"></a><span data-ttu-id="c1404-104">方法 : シリアル化されたデータをチャンクする</span><span class="sxs-lookup"><span data-stu-id="c1404-104">How to: chunk serialized data</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="c1404-105">Web サービス メッセージ内で大きなデータ セットを送信すると、次の 2 つの問題が発生します。</span><span class="sxs-lookup"><span data-stu-id="c1404-105">Two issues that occur when sending large data sets in Web service messages are:</span></span>  
  
1. <span data-ttu-id="c1404-106">シリアル化エンジンのバッファリングによるワーキング セット (メモリ) の巨大化</span><span class="sxs-lookup"><span data-stu-id="c1404-106">A large working set (memory) due to buffering by the serialization engine.</span></span>  
  
2. <span data-ttu-id="c1404-107">Base64 エンコーディングの実行後はサイズが 33% 増大することによる、帯域幅の過剰消費</span><span class="sxs-lookup"><span data-stu-id="c1404-107">Inordinate bandwidth consumption due to 33 percent inflation after Base64 encoding.</span></span>  
  
 <span data-ttu-id="c1404-108">これらの問題を解決するには、シリアル化と逆シリアル化を制御する <xref:System.Xml.Serialization.IXmlSerializable> インターフェイスを実装します。</span><span class="sxs-lookup"><span data-stu-id="c1404-108">To solve these problems, implement the <xref:System.Xml.Serialization.IXmlSerializable> interface to control the serialization and deserialization.</span></span> <span data-ttu-id="c1404-109">特に、<xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> メソッドと <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> メソッドを実装することで、データをチャンクします。</span><span class="sxs-lookup"><span data-stu-id="c1404-109">Specifically, implement the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> and <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> methods to chunk the data.</span></span>  
  
### <a name="to-implement-server-side-chunking"></a><span data-ttu-id="c1404-110">サーバー側チャンク処理を実装するには</span><span class="sxs-lookup"><span data-stu-id="c1404-110">To implement server-side chunking</span></span>  
  
1. <span data-ttu-id="c1404-111">サーバー コンピューター上で、Web メソッドが ASP.NET バッファリングを無効にし、<xref:System.Xml.Serialization.IXmlSerializable> を実装する型を返す必要があります。</span><span class="sxs-lookup"><span data-stu-id="c1404-111">On the server machine, the Web method must turn off ASP.NET buffering and return a type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
2. <span data-ttu-id="c1404-112"><xref:System.Xml.Serialization.IXmlSerializable> を実装する型は、<xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> メソッド内でデータをチャンクします。</span><span class="sxs-lookup"><span data-stu-id="c1404-112">The type that implements <xref:System.Xml.Serialization.IXmlSerializable> chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
### <a name="to-implement-client-side-processing"></a><span data-ttu-id="c1404-113">クライアント側の処理を実装するには</span><span class="sxs-lookup"><span data-stu-id="c1404-113">To implement client-side processing</span></span>  
  
1. <span data-ttu-id="c1404-114">クライアント プロキシ上で <xref:System.Xml.Serialization.IXmlSerializable> を実装する型を返すように Web メソッドを変更します。</span><span class="sxs-lookup"><span data-stu-id="c1404-114">Alter the Web method on the client proxy to return the type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="c1404-115"><xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> を使用すると、この処理を自動化できますが、この方法はここでは説明しません。</span><span class="sxs-lookup"><span data-stu-id="c1404-115">You can use a <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> to do this automatically, but this isn't shown here.</span></span>  
  
2. <span data-ttu-id="c1404-116">チャンクされたデータ ストリームを読み込み、バイトをディスクに書き込むための <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="c1404-116">Implement the <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> method to read the chunked data stream and write the bytes to disk.</span></span> <span data-ttu-id="c1404-117">この実装により、進行状況イベントも発生します。これは、プログレス バーなどのグラフィック コントロールに使用できます。</span><span class="sxs-lookup"><span data-stu-id="c1404-117">This implementation also raises progress events that can be used by a graphic control, such as a progress bar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1404-118">例</span><span class="sxs-lookup"><span data-stu-id="c1404-118">Example</span></span>  

<span data-ttu-id="c1404-119">次のコード例では、クライアント上で ASP.NET バッファリングを無効にする Web メソッドを示します。</span><span class="sxs-lookup"><span data-stu-id="c1404-119">The following code example shows the Web method on the client that turns off ASP.NET buffering.</span></span> <span data-ttu-id="c1404-120">また、<xref:System.Xml.Serialization.IXmlSerializable> メソッドにおいてデータをチャンクする <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> インターフェイスをクライアント側で実装する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="c1404-120">It also shows the client-side implementation of the <xref:System.Xml.Serialization.IXmlSerializable> interface that chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)]
[!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]  
[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)]
[!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]  
[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)]
[!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c1404-121">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="c1404-121">Compiling the code</span></span>  
  
- <span data-ttu-id="c1404-122">このコードでは、<xref:System>、<xref:System.Runtime.Serialization>、<xref:System.Web.Services>、<xref:System.Web.Services.Protocols>、<xref:System.Xml>、<xref:System.Xml.Serialization>、および <xref:System.Xml.Schema> の各名前空間を使用しています。</span><span class="sxs-lookup"><span data-stu-id="c1404-122">The code uses the following namespaces: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, and <xref:System.Xml.Schema>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1404-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="c1404-123">See also</span></span>

- [<span data-ttu-id="c1404-124">カスタムのシリアル化</span><span class="sxs-lookup"><span data-stu-id="c1404-124">Custom Serialization</span></span>](custom-serialization.md)
