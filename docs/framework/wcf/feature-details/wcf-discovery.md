---
title: WCF Discovery
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
ms.openlocfilehash: 176e9760d98f9640bd9d1c7b059287dc29c0d666
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96289361"
---
# <a name="wcf-discovery"></a><span data-ttu-id="8a173-102">WCF Discovery</span><span class="sxs-lookup"><span data-stu-id="8a173-102">WCF Discovery</span></span>

<span data-ttu-id="8a173-103">Windows Communication Foundation (WCF) は、WS-Discovery プロトコルを使用して、相互運用可能な方法で実行時にサービスを探索可能にするためのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="8a173-103">Windows Communication Foundation (WCF) provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> <span data-ttu-id="8a173-104">WCF サービスは、マルチキャストメッセージまたは探索プロキシサーバーを使用して、ネットワークへの可用性をアナウンスできます。</span><span class="sxs-lookup"><span data-stu-id="8a173-104">WCF services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="8a173-105">クライアント アプリケーションは、ネットワークまたは探索プロキシ サーバーを検索して、一連の基準を満たすサービスを見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="8a173-105">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="8a173-106">このセクションのトピックでは、この機能の概要を示し、そのプログラミング モデルについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8a173-106">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="8a173-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="8a173-107">In This Section</span></span>  

 [<span data-ttu-id="8a173-108">WCF Discovery の概要</span><span class="sxs-lookup"><span data-stu-id="8a173-108">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)  
 <span data-ttu-id="8a173-109">WCF によって提供される WS-Discovery のサポートの概要について説明します。</span><span class="sxs-lookup"><span data-stu-id="8a173-109">Provides an overview of WS-Discovery support provided by WCF.</span></span>  
  
 [<span data-ttu-id="8a173-110">WCF Discovery オブジェクト モデル</span><span class="sxs-lookup"><span data-stu-id="8a173-110">WCF Discovery Object Model</span></span>](wcf-discovery-object-model.md)  
 <span data-ttu-id="8a173-111">オブジェクト モデルのクラスと WS-Discovery サポートの拡張性について説明します。</span><span class="sxs-lookup"><span data-stu-id="8a173-111">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="8a173-112">方法: プログラムを使用して探索可能性に WCF サービスとクライアントを追加する</span><span class="sxs-lookup"><span data-stu-id="8a173-112">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="8a173-113">Windows Communication Foundation (WCF) サービスを探索可能にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8a173-113">Shows how to make a Windows Communication Foundation (WCF) service discoverable.</span></span>  
  
 [<span data-ttu-id="8a173-114">探索プロキシの実装</span><span class="sxs-lookup"><span data-stu-id="8a173-114">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)  
 <span data-ttu-id="8a173-115">探索プロキシを実装するのに必要な手順、探索プロキシで登録される探索可能なサービス、および探索プロキシを使用して探索可能なサービスを検索するクライアントについて説明します。</span><span class="sxs-lookup"><span data-stu-id="8a173-115">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="8a173-116">探索機能のバージョン指定</span><span class="sxs-lookup"><span data-stu-id="8a173-116">Discovery Versioning</span></span>](discovery-versioning.md)  
 <span data-ttu-id="8a173-117">いくつかの新しい探索機能のプロトタイプ実装の概要を示します。</span><span class="sxs-lookup"><span data-stu-id="8a173-117">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="8a173-118">使用する探索バージョンを選択する方法の概要も示します。</span><span class="sxs-lookup"><span data-stu-id="8a173-118">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="8a173-119">構成ファイルにおける探索の構成</span><span class="sxs-lookup"><span data-stu-id="8a173-119">Configuring Discovery in a Configuration File</span></span>](configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="8a173-120">構成ファイルで探索を構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8a173-120">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="8a173-121">探索クライアント チャネルの使用</span><span class="sxs-lookup"><span data-stu-id="8a173-121">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)  
 <span data-ttu-id="8a173-122">WCF クライアントアプリケーションを記述するときに探索クライアントチャネルを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="8a173-122">Shows how to use a Discovery Client Channel when writing a WCF client application.</span></span>
