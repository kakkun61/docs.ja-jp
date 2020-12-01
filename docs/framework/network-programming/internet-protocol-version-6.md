---
title: インターネット プロトコル バージョン 6
description: IPv6 プロトコルと IPv4 との違いについて学習します。 .NET Framework アプリケーションでは IPv6 をサポートしますが、構成が必要になる場合があります。
ms.date: 03/30/2017
helpviewer_keywords:
- IPv6, improvements
- IPv4
- IPv6
- Internet Protocol version 6, improvements
- Internet Protocol version 6
ms.assetid: e6fa8ebd-010a-4c48-a5ec-a5102c53c06f
ms.openlocfilehash: f5b74674ba4144f75d125267f2458394bb74fab1
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96283953"
---
# <a name="internet-protocol-version-6"></a><span data-ttu-id="c0079-104">インターネット プロトコル バージョン 6</span><span class="sxs-lookup"><span data-stu-id="c0079-104">Internet Protocol Version 6</span></span>

<span data-ttu-id="c0079-105">インターネット プロトコル バージョン 6 (IPv6) は、インターネットのネットワーク層の標準プロトコルの新しいスイートです。</span><span class="sxs-lookup"><span data-stu-id="c0079-105">The Internet Protocol version 6 (IPv6) is a new suite of standard protocols for the network layer of the Internet.</span></span> <span data-ttu-id="c0079-106">IPv6 は、アドレスの不足、セキュリティ、自動構成、拡張性などに関して、インターネット プロトコル スイートの現在のバージョン (IPv4) が抱える多くの問題を解決するために設計されています。</span><span class="sxs-lookup"><span data-stu-id="c0079-106">IPv6 is designed to solve many of the problems of the current version of the Internet Protocol suite (known as IPv4) with regard to address depletion, security, auto-configuration, extensibility, and so on.</span></span> <span data-ttu-id="c0079-107">IPv6 は、インターネットの機能を拡張して、ピア ツー ピア アプリケーションやモバイル アプリケーションなどの新しい種類のアプリケーションを有効にします。</span><span class="sxs-lookup"><span data-stu-id="c0079-107">IPv6 expands the capabilities of the Internet to enable new kinds of applications, including peer-to-peer and mobile applications.</span></span> <span data-ttu-id="c0079-108">現在の IPv4 プロトコルの主な問題を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c0079-108">The following are the main issues of the current IPv4 protocol:</span></span>  
  
- <span data-ttu-id="c0079-109">アドレス空間の急減。</span><span class="sxs-lookup"><span data-stu-id="c0079-109">Rapid depletion of the address space.</span></span>  
  
     <span data-ttu-id="c0079-110">これが、複数のプライベート アドレスを 1 つのパブリック IP アドレスにマップするネットワーク アドレス変換器 (NAT) の使用につながってきました。</span><span class="sxs-lookup"><span data-stu-id="c0079-110">This has led to the use of Network Address Translators (NATs) that map multiple private addresses to a single public IP address.</span></span> <span data-ttu-id="c0079-111">このメカニズムによって生じた主な問題は、処理オーバーヘッドとエンド ツー エンドの接続の欠如です。</span><span class="sxs-lookup"><span data-stu-id="c0079-111">The main problems created by this mechanism are processing overhead and lack of end-to-end connectivity.</span></span>  
  
- <span data-ttu-id="c0079-112">階層サポートの不足。</span><span class="sxs-lookup"><span data-stu-id="c0079-112">Lack of hierarchy support.</span></span>  
  
     <span data-ttu-id="c0079-113">IPv4 固有の定義済みクラス組織により、IPv4 には真の階層サポートが不足しています。</span><span class="sxs-lookup"><span data-stu-id="c0079-113">Because of its inherent predefined class organization, IPv4 lacks true hierarchical support.</span></span> <span data-ttu-id="c0079-114">真にネットワーク トポロジをマップする方法で IP アドレスを構成することはできません。</span><span class="sxs-lookup"><span data-stu-id="c0079-114">It is impossible to structure the IP addresses in a way that truly maps the network topology.</span></span> <span data-ttu-id="c0079-115">この重大な設計上の欠陥により、IPv4 パケットをインターネット上の任意の場所に配信するために大規模なルーティング テーブルが必要となっています。</span><span class="sxs-lookup"><span data-stu-id="c0079-115">This crucial design flaw creates the need for large routing tables to deliver IPv4 packets to any location on the Internet.</span></span>  
  
- <span data-ttu-id="c0079-116">複雑なネットワーク構成。</span><span class="sxs-lookup"><span data-stu-id="c0079-116">Complex network configuration.</span></span>  
  
     <span data-ttu-id="c0079-117">IPv4 では、アドレスを静的に、または DHCP などの構成プロトコルを使用して割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0079-117">With IPv4, addresses must be assigned statically or using a configuration protocol such as DHCP.</span></span> <span data-ttu-id="c0079-118">理想的な状況では、ホストは DHCP インフラストラクチャの管理に依存する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="c0079-118">In an ideal situation, hosts would not have to rely on the administration of a DHCP infrastructure.</span></span> <span data-ttu-id="c0079-119">代わりに、ホストが配置されているネットワーク セグメントに基づいてホスト自身で構成できます。</span><span class="sxs-lookup"><span data-stu-id="c0079-119">Instead, they would be able to configure themselves based on the network segment in which they are located.</span></span>  
  
- <span data-ttu-id="c0079-120">組み込み認証と機密性の不足。</span><span class="sxs-lookup"><span data-stu-id="c0079-120">Lack of built-in authentication and confidentiality.</span></span>  
  
     <span data-ttu-id="c0079-121">IPv4 では、交換されるデータの認証または暗号化を提供する任意のメカニズムのサポートは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="c0079-121">IPv4 does not require the support for any mechanism that provides authentication or encryption of the exchanged data.</span></span> <span data-ttu-id="c0079-122">IPv6 ではこれが変わります。</span><span class="sxs-lookup"><span data-stu-id="c0079-122">This changes with IPv6.</span></span> <span data-ttu-id="c0079-123">インターネット プロトコル セキュリティ (IPSec) は、IPv6 のサポート要件です。</span><span class="sxs-lookup"><span data-stu-id="c0079-123">Internet Protocol security (IPSec) is an IPv6 support requirement.</span></span>  
  
 <span data-ttu-id="c0079-124">新しいプロトコル スイートは、次の基本的な要件を満たす必要があります。</span><span class="sxs-lookup"><span data-stu-id="c0079-124">A new protocol suite must satisfy the following basic requirements:</span></span>  
  
- <span data-ttu-id="c0079-125">大規模なルーティングと低いオーバーヘッドでのアドレス指定。</span><span class="sxs-lookup"><span data-stu-id="c0079-125">Large-scale routing and addressing with low overhead.</span></span>  
  
- <span data-ttu-id="c0079-126">さまざまな接続状況の自動構成。</span><span class="sxs-lookup"><span data-stu-id="c0079-126">Auto-configuration for various connecting situations.</span></span>  
  
- <span data-ttu-id="c0079-127">組み込み認証と機密性。</span><span class="sxs-lookup"><span data-stu-id="c0079-127">Built-in authentication and confidentiality.</span></span>  
  
 <span data-ttu-id="c0079-128">詳細については、「[IPv6 アドレス指定](ipv6-addressing.md)」、「[IPv6 のルーティング](ipv6-routing.md)」、「[IPv6 の自動構成](ipv6-auto-configuration.md)」、「[IPv6 の有効化と無効化](enabling-and-disabling-ipv6.md)」、および「[方法:IPv6 のサポートを有効にするようにコンピューター構成ファイルを変更する](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c0079-128">For more information, see [IPv6 Addressing](ipv6-addressing.md), [IPv6 Routing](ipv6-routing.md), [IPv6 Auto-Configuration](ipv6-auto-configuration.md), [Enabling and Disabling IPv6](enabling-and-disabling-ipv6.md), and [How to: Modify the Computer Configuration File to Enable IPv6 Support](how-to-modify-the-computer-configuration-file-to-enable-ipv6-support.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="c0079-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0079-129">References</span></span>  

 <span data-ttu-id="c0079-130">[インターネット技術標準化委員会 (IETF)](https://www.ietf.org/) Web サイトで検索できる厳選した RFC ドキュメントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="c0079-130">The following are selected RFC documents that you can find at the [Internet Engineering Task Force (IETF)](https://www.ietf.org/) website:</span></span>  
  
- <span data-ttu-id="c0079-131">RFC 1287、Towards the Future Internet Architecture (将来のインターネットアーキテクチャに向けて)</span><span class="sxs-lookup"><span data-stu-id="c0079-131">RFC 1287, Towards the Future Internet Architecture.</span></span>  
  
- <span data-ttu-id="c0079-132">RFC 1454、Comparison of Proposals for Next Version of IP (IP の次のバージョンのための提案の比較)</span><span class="sxs-lookup"><span data-stu-id="c0079-132">RFC 1454, Comparison of Proposals for Next Version of IP.</span></span>  
  
- <span data-ttu-id="c0079-133">RFC 2373、IP Version 6 Addressing Architecture (IP バージョン 6 のアドレス指定アーキテクチャ)</span><span class="sxs-lookup"><span data-stu-id="c0079-133">RFC 2373, IP Version 6 Addressing Architecture.</span></span>  
  
- <span data-ttu-id="c0079-134">RFC 2374、An IPv6 Aggregatable Global Unicast Address Format (IPv6 の集約可能なグローバル ユニキャスト アドレス形式)</span><span class="sxs-lookup"><span data-stu-id="c0079-134">RFC 2374, An IPv6 Aggregatable Global Unicast Address Format.</span></span>  
  
 <span data-ttu-id="c0079-135">[IP バージョン 6 (IPv6)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498(v=ws.10)) でも IPv6 関連の情報を見つけることができます。</span><span class="sxs-lookup"><span data-stu-id="c0079-135">You can also find IPv6-related information on the [IP Version 6 (IPv6)](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/dd379498(v=ws.10)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0079-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="c0079-136">See also</span></span>

- <span data-ttu-id="c0079-137">[IPv6 ソケットのサンプル](/previous-versions/dotnet/netframework-3.0/ms180981(v=vs.85))</span><span class="sxs-lookup"><span data-stu-id="c0079-137">[IPv6 Sockets Sample](/previous-versions/dotnet/netframework-3.0/ms180981(v=vs.85))</span></span>
- [<span data-ttu-id="c0079-138">ネットワーク プログラミングのサンプル</span><span class="sxs-lookup"><span data-stu-id="c0079-138">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="c0079-139">ソケット</span><span class="sxs-lookup"><span data-stu-id="c0079-139">Sockets</span></span>](sockets.md)
