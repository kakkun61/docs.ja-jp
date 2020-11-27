---
title: カスタム ストリームのアップグレード
ms.date: 03/30/2017
ms.assetid: e3da85c8-57f3-4e32-a4cb-50123f30fea6
ms.openlocfilehash: 3ef0f59a5d63c24188b29cb7a38db2d6323d80ee
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96295582"
---
# <a name="custom-stream-upgrades"></a><span data-ttu-id="e74b2-102">カスタム ストリームのアップグレード</span><span class="sxs-lookup"><span data-stu-id="e74b2-102">Custom Stream Upgrades</span></span>

<span data-ttu-id="e74b2-103">TCP、名前付きパイプなど、ストリーム指向のデータ伝送機構 (トランスポート) が扱うのは、クライアントとサーバーの間を流れる、連続的なバイト ストリームです。</span><span class="sxs-lookup"><span data-stu-id="e74b2-103">Stream-oriented transports such as TCP and Named Pipes operate on a continuous stream of bytes between the client and server.</span></span> <span data-ttu-id="e74b2-104">このストリームを実際に作り出すのは <xref:System.IO.Stream> オブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="e74b2-104">This stream is realized by a  <xref:System.IO.Stream> object.</span></span> <span data-ttu-id="e74b2-105">ストリーム アップグレードでは、クライアントは、オプションのプロトコル階層をチャネル スタックに追加する場合に、相手側の通信チャネルにも同じことをするよう要求します。</span><span class="sxs-lookup"><span data-stu-id="e74b2-105">In a stream upgrade, the client wants to add an optional protocol layer to the channel stack, and asks the other end of the communication channel to do so.</span></span> <span data-ttu-id="e74b2-106">ストリーム アップグレードは、<xref:System.IO.Stream> オブジェクトをアップグレードされたものに置き換える形で実施します。</span><span class="sxs-lookup"><span data-stu-id="e74b2-106">The stream upgrade consists in replacing the original <xref:System.IO.Stream> object with an upgraded one.</span></span>  
  
 <span data-ttu-id="e74b2-107">たとえば、トランスポート ストリームのすぐ上に圧縮ストリームを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="e74b2-107">For example, you can build a compression stream directly on top of the transport stream.</span></span> <span data-ttu-id="e74b2-108">この場合、元のトランスポート <xref:System.IO.Stream> を、それを圧縮 <xref:System.IO.Stream> でラップしたものに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e74b2-108">In this case the original transport <xref:System.IO.Stream> is replaced with one that wraps the compression <xref:System.IO.Stream> around the original one.</span></span>  
  
 <span data-ttu-id="e74b2-109">オブジェクトを順にラップしていくことにより、ストリーム アップグレードを多重に適用できます。</span><span class="sxs-lookup"><span data-stu-id="e74b2-109">You can apply multiple stream upgrades, each wrapping the preceding one.</span></span>  
  
## <a name="how-stream-upgrades-work"></a><span data-ttu-id="e74b2-110">ストリーム アップグレードの動作</span><span class="sxs-lookup"><span data-stu-id="e74b2-110">How Stream Upgrades Work</span></span>  

 <span data-ttu-id="e74b2-111">ストリーム アップグレード処理には 4 つのコンポーネントが関与します。</span><span class="sxs-lookup"><span data-stu-id="e74b2-111">There are four components to the stream upgrade process.</span></span>  
  
1. <span data-ttu-id="e74b2-112">アップグレードストリームの *イニシエーター* は、プロセスを開始します。実行時には、接続の相手側に要求を開始してチャネルトランスポート層をアップグレードできます。</span><span class="sxs-lookup"><span data-stu-id="e74b2-112">An upgrade stream *Initiator* begins the process: at run-time it can initiate a request to the other end of its connection to upgrade the channel transport layer.</span></span>  
  
2. <span data-ttu-id="e74b2-113">アップグレードストリーム *アクセプタ* は、アップグレードを実行するときに、他のコンピューターからのアップグレード要求を受信します。可能な場合は、アップグレードを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="e74b2-113">An upgrade stream *Acceptor* carries out the upgrade: at run-time it receives the upgrade request from the other machine, and if possible, accepts the upgrade.</span></span>  
  
3. <span data-ttu-id="e74b2-114">アップグレード *プロバイダー* によって、クライアント上の *イニシエーター* と、サーバー上の *アクセプタ* が作成されます。</span><span class="sxs-lookup"><span data-stu-id="e74b2-114">An upgrade *Provider* creates the *Initiator* on the client and the *Acceptor* on the server.</span></span>  
  
4. <span data-ttu-id="e74b2-115">ストリームアップグレードの *バインド要素* がサービスとクライアントのバインディングに追加され、実行時にプロバイダーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e74b2-115">A stream upgrade *Binding Element* is added to the bindings on the service and the client, and creates the provider at runtime.</span></span>  
  
 <span data-ttu-id="e74b2-116">なお、多重にアップグレードを適用する場合、イニシエーターとアクセプタはステート マシンをカプセル化して、適切な適用順序になるようにします。</span><span class="sxs-lookup"><span data-stu-id="e74b2-116">Note that in the case of multiple upgrades, the Initiator and Acceptor encapsulate state machines to enforce which upgrade transitions are valid for each Initiation.</span></span>  
  
## <a name="how-to-implement-a-stream-upgrade"></a><span data-ttu-id="e74b2-117">ストリーム アップグレードの実装方法</span><span class="sxs-lookup"><span data-stu-id="e74b2-117">How to Implement a Stream Upgrade</span></span>  

 <span data-ttu-id="e74b2-118">Windows Communication Foundation (WCF) には、実装できる4つのクラスが用意され `abstract` ています。</span><span class="sxs-lookup"><span data-stu-id="e74b2-118">Windows Communication Foundation (WCF) provides four `abstract` classes that you can implement:</span></span>  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeInitiator?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeProvider?displayProperty=nameWithType>  
  
- <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement?displayProperty=nameWithType>  
  
 <span data-ttu-id="e74b2-119">カスタム ストリーム アップグレードを実装する手順を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="e74b2-119">To implement a custom stream upgrade, do the following.</span></span> <span data-ttu-id="e74b2-120">これは、クライアント側、サーバー側双方に、ごく単純なストリーム アップグレード処理を組み込む場合の手順です。</span><span class="sxs-lookup"><span data-stu-id="e74b2-120">This procedure implements a minimal stream upgrade process on both the client and server machines.</span></span>  
  
1. <span data-ttu-id="e74b2-121"><xref:System.ServiceModel.Channels.StreamUpgradeInitiator> を実装するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e74b2-121">Create a class that implements <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>.</span></span>  
  
    1. <span data-ttu-id="e74b2-122"><xref:System.ServiceModel.Channels.StreamUpgradeInitiator.InitiateUpgrade%2A> メソッドをオーバーライドして、ストリームを入力すると、それをアップグレードしたストリームが返されるようにします。</span><span class="sxs-lookup"><span data-stu-id="e74b2-122">Override the <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.InitiateUpgrade%2A> method to take in the stream to be upgraded, and return the upgraded stream.</span></span> <span data-ttu-id="e74b2-123">これは同期型のメソッドですが、これに似た非同期型のメソッドもあります。</span><span class="sxs-lookup"><span data-stu-id="e74b2-123">This method works synchronously; there are analogous methods to initiate the upgrade asynchronously.</span></span>  
  
    2. <span data-ttu-id="e74b2-124"><xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> メソッドをオーバーライドして、追加のアップグレードがないか確認するようにします。</span><span class="sxs-lookup"><span data-stu-id="e74b2-124">Override the <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> method to check for additional upgrades.</span></span>  
  
2. <span data-ttu-id="e74b2-125"><xref:System.ServiceModel.Channels.StreamUpgradeAcceptor> を実装するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e74b2-125">Create a class that implements <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>.</span></span>  
  
    1. <span data-ttu-id="e74b2-126"><xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.AcceptUpgrade%2A> メソッドをオーバーライドして、ストリームを入力すると、それをアップグレードしたストリームが返されるようにします。</span><span class="sxs-lookup"><span data-stu-id="e74b2-126">Override the <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.AcceptUpgrade%2A> method to take in the stream to be upgraded, and return the upgraded stream.</span></span> <span data-ttu-id="e74b2-127">これは同期型のメソッドですが、これに似た非同期型のメソッドもあります。</span><span class="sxs-lookup"><span data-stu-id="e74b2-127">This method works synchronously; there are analogous methods to accept the upgrade asynchronously.</span></span>  
  
    2. <span data-ttu-id="e74b2-128"><xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> メソッドをオーバーライドして、アップグレード処理中のこの時点で、このアップグレード アクセプタがアップグレード要求に応じることができるかどうかを判断するようにします。</span><span class="sxs-lookup"><span data-stu-id="e74b2-128">Override the <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> method to determine if the upgrade requested is supported by this upgrade acceptor at this point in the upgrade process.</span></span>  
  
3. <span data-ttu-id="e74b2-129"><xref:System.ServiceModel.Channels.StreamUpgradeProvider> を実装するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e74b2-129">Create a class the implements <xref:System.ServiceModel.Channels.StreamUpgradeProvider>.</span></span> <span data-ttu-id="e74b2-130"><xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeAcceptor%2A> メソッドおよび <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeInitiator%2A> メソッドをオーバーライドして、手順 1. および 2. で定義したアクセプタとイニシエーターのインスタンスをそれぞれ返すようにします。</span><span class="sxs-lookup"><span data-stu-id="e74b2-130">Override the <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeAcceptor%2A> and the <xref:System.ServiceModel.Channels.StreamUpgradeProvider.CreateUpgradeInitiator%2A> methods to return instances of the acceptor and initiator defined in steps 2 and 1.</span></span>  
  
4. <span data-ttu-id="e74b2-131"><xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> を実装するクラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e74b2-131">Create a class that implements <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>.</span></span>  
  
    1. <span data-ttu-id="e74b2-132">クライアント側の <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildClientStreamUpgradeProvider%2A> メソッドとサービス側の <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildServerStreamUpgradeProvider%2A> メソッドをオーバーライドします。</span><span class="sxs-lookup"><span data-stu-id="e74b2-132">Override the <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildClientStreamUpgradeProvider%2A> method on the client and the <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement.BuildServerStreamUpgradeProvider%2A> method on the service.</span></span>  
  
    2. <span data-ttu-id="e74b2-133">クライアント側の <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> メソッドとサービス側の <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> メソッドをオーバーライドして、アップグレード バインド要素を <xref:System.ServiceModel.Channels.BindingContext.BindingParameters%2A> に追加するようにします。</span><span class="sxs-lookup"><span data-stu-id="e74b2-133">Override the <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> method on the client and the <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> method on the service to add the upgrade Binding Element to <xref:System.ServiceModel.Channels.BindingContext.BindingParameters%2A>.</span></span>  
  
5. <span data-ttu-id="e74b2-134">サーバー側とクライアント側のバインディングに、新しいストリーム アップグレード バインド要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="e74b2-134">Add the new stream upgrade binding element to bindings on the server and client machines.</span></span>  
  
## <a name="security-upgrades"></a><span data-ttu-id="e74b2-135">セキュリティ アップグレード</span><span class="sxs-lookup"><span data-stu-id="e74b2-135">Security Upgrades</span></span>  

 <span data-ttu-id="e74b2-136">ストリーム アップグレードの特別な場合として、セキュリティ アップグレードがあります。</span><span class="sxs-lookup"><span data-stu-id="e74b2-136">Adding a security upgrade is a specialized version of the general stream upgrade process.</span></span>  
  
 <span data-ttu-id="e74b2-137">WCF には、ストリームセキュリティをアップグレードするためのバインド要素が既に2つ用意されています。</span><span class="sxs-lookup"><span data-stu-id="e74b2-137">WCF already provides two binding elements for upgrading stream security.</span></span> <span data-ttu-id="e74b2-138">トランスポート レベルのセキュリティ構成は、<xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> および <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement> にカプセル化されており、これらの要素を構成して、カスタム バインドに追加することができます。</span><span class="sxs-lookup"><span data-stu-id="e74b2-138">The configuration of transport-level security is encapsulated by the <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement> and the <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement> which can be configured and added to a custom binding.</span></span> <span data-ttu-id="e74b2-139">この 2 つのバインド要素は、クライアント側およびサーバー側のストリーム アップグレード プロバイダーを構築する <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> クラスを拡張したものです。</span><span class="sxs-lookup"><span data-stu-id="e74b2-139">These binding elements extend the <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement> class that builds the client and server stream upgrade providers.</span></span> <span data-ttu-id="e74b2-140">これらのバインド要素には、セキュリティ ストリーム アップグレード専用のプロバイダー クラスを作成するメソッドが定義されています。これらのメソッドは `public` ではないので、いずれの場合もバインド要素をバインディングに追加するだけでセキュリティ アップグレードが可能です。</span><span class="sxs-lookup"><span data-stu-id="e74b2-140">These binding elements have methods that create the specialized security stream upgrade provider classes, which are not `public`, so for these two cases all you need to do is to add the binding element to the binding.</span></span>  
  
 <span data-ttu-id="e74b2-141">上記の 2 つのバインド要素では対応できないセキュリティ上の要求に備え、既述のイニシエーター、アクセプタ、プロバイダーの各基底クラスから派生した `abstract` クラスが 3 つ定義されています。</span><span class="sxs-lookup"><span data-stu-id="e74b2-141">For security scenarios not met by the above two binding elements, three security-related `abstract` classes are derived from the above initiator, acceptor and provider base classes:</span></span>  
  
1. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator?displayProperty=nameWithType>  
  
2. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor?displayProperty=nameWithType>  
  
3. <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider?displayProperty=nameWithType>  
  
 <span data-ttu-id="e74b2-142">セキュリティ ストリーム アップグレードを実装する手順も、以上 3 つのクラスから派生することを除き、一般のストリーム アップグレードと同様です。</span><span class="sxs-lookup"><span data-stu-id="e74b2-142">The process of implementing a security stream upgrade is the same as before, with the difference that you would derive from these three classes.</span></span> <span data-ttu-id="e74b2-143">これらのクラスには実行時にセキュリティ情報をやり取りするためのプロパティが追加されているので、これをオーバーライドしてください。</span><span class="sxs-lookup"><span data-stu-id="e74b2-143">Override the additional properties in these classes to supply security information to the runtime.</span></span>  
  
## <a name="multiple-upgrades"></a><span data-ttu-id="e74b2-144">多重アップグレード</span><span class="sxs-lookup"><span data-stu-id="e74b2-144">Multiple Upgrades</span></span>  

 <span data-ttu-id="e74b2-145">追加のアップグレード要求を作成するには、前述の手順を繰り返して、追加の <xref:System.ServiceModel.Channels.StreamUpgradeProvider> およびバインド要素の拡張を作成し、</span><span class="sxs-lookup"><span data-stu-id="e74b2-145">To create additional upgrade requests repeat the above process: create additional extensions of <xref:System.ServiceModel.Channels.StreamUpgradeProvider> and binding elements.</span></span> <span data-ttu-id="e74b2-146">これをバインディングに追加します。</span><span class="sxs-lookup"><span data-stu-id="e74b2-146">Add the binding elements to the binding.</span></span> <span data-ttu-id="e74b2-147">各バインド要素は、バインディングに追加した順に処理されます。</span><span class="sxs-lookup"><span data-stu-id="e74b2-147">The additional binding elements are processed sequentially, starting with the first binding element added to the binding.</span></span> <span data-ttu-id="e74b2-148">各アップグレード プロバイダーは、<xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> および <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> で、既存のアップグレード バインディング パラメーターに、どのように自分自身を積み重ねるかを指定できます。</span><span class="sxs-lookup"><span data-stu-id="e74b2-148">In <xref:System.ServiceModel.Channels.BindingElement.BuildChannelFactory%2A> and <xref:System.ServiceModel.Channels.BindingElement.BuildChannelListener%2A> each upgrade provider can determine how to layer itself on any pre-existing upgrade binding parameters.</span></span> <span data-ttu-id="e74b2-149">次に、既存のアップグレード バインディング パラメーターを、新しい複合アップグレード バインディング パラメーターに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="e74b2-149">It should then replace the existing upgrade binding parameter with a new composite upgrade binding parameter.</span></span>  
  
 <span data-ttu-id="e74b2-150">あるいは、単一のアップグレード プロバイダーで、多重のアップグレードに対応することも可能です。</span><span class="sxs-lookup"><span data-stu-id="e74b2-150">Alternatively, one upgrade provider can support multiple upgrades.</span></span> <span data-ttu-id="e74b2-151">たとえば、セキュリティと圧縮の両方に対応するカスタム ストリーム アップグレード プロバイダーを実装できます。</span><span class="sxs-lookup"><span data-stu-id="e74b2-151">For example, you might want to implement a custom stream upgrade provider that supports both security and compression.</span></span> <span data-ttu-id="e74b2-152">手順は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e74b2-152">Do the following steps:</span></span>  
  
1. <span data-ttu-id="e74b2-153"><xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider> のサブクラスとして、イニシエーターおよびアクセプタを生成するプロバイダー クラスを作成します。</span><span class="sxs-lookup"><span data-stu-id="e74b2-153">Subclass <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider> to write the provider class that creates the Initiator and Acceptor.</span></span>  
  
2. <span data-ttu-id="e74b2-154"><xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator> のサブクラスを作成し、<xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> メソッドをオーバーライドして、圧縮ストリーム、セキュリティ ストリームの順にコンテンツ タイプを返すようにします。</span><span class="sxs-lookup"><span data-stu-id="e74b2-154">Subclass the <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator> making sure to override the <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> method to return the content types for the compression stream and the secure stream in order.</span></span>  
  
3. <span data-ttu-id="e74b2-155"><xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor> のサブクラスを作成し、<xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> メソッドをオーバーライドして、独自のコンテンツ タイプに応じた処理をするようにします。</span><span class="sxs-lookup"><span data-stu-id="e74b2-155">Subclass the <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor> that understands the custom content types in its <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> method.</span></span>  
  
4. <span data-ttu-id="e74b2-156">ストリームは、<xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> および <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A> をそれぞれ呼び出した後にアップグレードされます。</span><span class="sxs-lookup"><span data-stu-id="e74b2-156">The stream will be upgraded after each call to <xref:System.ServiceModel.Channels.StreamUpgradeInitiator.GetNextUpgrade%2A> and <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor.CanUpgrade%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e74b2-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="e74b2-157">See also</span></span>

- <xref:System.ServiceModel.Channels.StreamUpgradeInitiator>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeInitiator>
- <xref:System.ServiceModel.Channels.StreamUpgradeAcceptor>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeAcceptor>
- <xref:System.ServiceModel.Channels.StreamUpgradeProvider>
- <xref:System.ServiceModel.Channels.StreamSecurityUpgradeProvider>
- <xref:System.ServiceModel.Channels.StreamUpgradeBindingElement>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>
