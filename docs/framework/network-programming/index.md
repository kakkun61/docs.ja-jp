---
title: .NET Framework のネットワーク プログラミング
description: これらのリソースを使用して、.NET Framework によって提供されたインターネット サービスの、複数層の拡張可能なマネージド実装をアプリケーションに統合します。
ms.date: 03/30/2017
helpviewer_keywords:
- Networking
- Internet
- Internet, .NET Framework Internet services
- Network Resources
ms.assetid: 8d455610-67a0-4fa8-a62f-7747064a9256
ms.openlocfilehash: 50f23e1a343f969ad2cbb3422038921c710b2b1b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241682"
---
# <a name="network-programming-in-the-net-framework"></a><span data-ttu-id="912ee-103">.NET Framework のネットワーク プログラミング</span><span class="sxs-lookup"><span data-stu-id="912ee-103">Network Programming in the .NET Framework</span></span>

<span data-ttu-id="912ee-104">Microsoft .NET Framework は、アプリケーションにすばやく簡単に統合できる、複数層の拡張可能なインターネット サービスのマネージド実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="912ee-104">The Microsoft .NET Framework provides a layered, extensible, and managed implementation of Internet services that can be quickly and easily integrated into your applications.</span></span> <span data-ttu-id="912ee-105">ネットワーク アプリケーションは、プラグ可能なプロトコルを基に自動的に新しいインターネット プロトコルを使用するように作成することも、ソケット レベルでネットワークを使用できるように Windows ソケット インターフェイスのマネージド実装を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="912ee-105">Your network applications can build on pluggable protocols to automatically take advantage of new Internet protocols, or they can use a managed implementation of the Windows socket interface to work with the network on the socket level.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="912ee-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="912ee-106">In This Section</span></span>  

 [<span data-ttu-id="912ee-107">プラグ可能なプロトコルの概要</span><span class="sxs-lookup"><span data-stu-id="912ee-107">Introducing Pluggable Protocols</span></span>](introducing-pluggable-protocols.md)  
 <span data-ttu-id="912ee-108">必要なアクセス プロトコルに関係なく、インターネット リソースにアクセスする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-108">Describes how to access an Internet resource without regard to the access protocol that it requires.</span></span>  
  
 [<span data-ttu-id="912ee-109">データの要求</span><span class="sxs-lookup"><span data-stu-id="912ee-109">Requesting Data</span></span>](requesting-data.md)  
 <span data-ttu-id="912ee-110">プラグ可能なプロトコルを使用して、インターネット リソースにデータをアップロードしたり、ダウンロードしたりする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-110">Explains how to use pluggable protocols to upload and download data from Internet resources.</span></span>  
  
 [<span data-ttu-id="912ee-111">プラグ可能なプロトコルのプログラミング</span><span class="sxs-lookup"><span data-stu-id="912ee-111">Programming Pluggable Protocols</span></span>](programming-pluggable-protocols.md)  
 <span data-ttu-id="912ee-112">プロトコル固有のクラスを派生させて、プラグ可能なプロトコルを実装する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-112">Explains how to derive protocol-specific classes to implement pluggable protocols.</span></span>  
  
 [<span data-ttu-id="912ee-113">アプリケーション プロトコルの使用</span><span class="sxs-lookup"><span data-stu-id="912ee-113">Using Application Protocols</span></span>](using-application-protocols.md)  
 <span data-ttu-id="912ee-114">TCP、UDP、HTTP などのネットワーク プロトコルを利用するアプリケーションのプログラミングについて説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-114">Describes programming applications that take advantage of network protocols such as TCP, UDP, and HTTP.</span></span>  
  
 [<span data-ttu-id="912ee-115">インターネット プロトコル バージョン 6</span><span class="sxs-lookup"><span data-stu-id="912ee-115">Internet Protocol Version 6</span></span>](internet-protocol-version-6.md)  
 <span data-ttu-id="912ee-116">インターネット プロトコル スイート (IPv4) の現在のバージョンより優れたインターネット プロトコル Version 6 (IPv6) の利点について説明し、IPv6 のアドレス指定、ルーティングおよび自動構成、および IPv6 を有効/無効にする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-116">Describes the advantages of Internet Protocol version 6 (IPv6) over the current version of the Internet Protocol suite (IPv4), describes IPv6 addressing, routing and auto-configuration, and how to enable and disable IPv6.</span></span>  
  
 [<span data-ttu-id="912ee-117">インターネット アプリケーションの構成</span><span class="sxs-lookup"><span data-stu-id="912ee-117">Configuring Internet Applications</span></span>](configuring-internet-applications.md)  
 <span data-ttu-id="912ee-118">.NET Framework 構成ファイルを使用して、インターネット アプリケーションを構成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-118">Explains how to use the .NET Framework configuration files to configure Internet applications.</span></span>  
  
 [<span data-ttu-id="912ee-119">.NET Framework のネットワークのトレース</span><span class="sxs-lookup"><span data-stu-id="912ee-119">Network Tracing in the .NET Framework</span></span>](network-tracing.md)  
 <span data-ttu-id="912ee-120">.NET Framework のネットワークのトレースを使用して、メソッド呼び出しについての情報、およびマネージド アプリケーションによって生成されるネットワーク トラフィックについての情報を取得する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-120">Explains how to use network tracing to get information about method invocations and network traffic generated by a managed application.</span></span>  
  
 [<span data-ttu-id="912ee-121">ネットワーク アプリケーションのキャッシュ管理</span><span class="sxs-lookup"><span data-stu-id="912ee-121">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)  
 <span data-ttu-id="912ee-122"><xref:System.Net.WebClient?displayProperty=nameWithType>、 <xref:System.Net.WebRequest?displayProperty=nameWithType>、および <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> クラスを使用するアプリケーションでキャッシュを使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-122">Describes how to use caching for applications that use the <xref:System.Net.WebClient?displayProperty=nameWithType>, <xref:System.Net.WebRequest?displayProperty=nameWithType>, and <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> classes.</span></span>  
  
 [<span data-ttu-id="912ee-123">ネットワーク プログラミングにおけるセキュリティ</span><span class="sxs-lookup"><span data-stu-id="912ee-123">Security in Network Programming</span></span>](security-in-network-programming.md)  
 <span data-ttu-id="912ee-124">標準のインターネット セキュリティと認証の手法を使用する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-124">Describes how to use standard Internet security and authentication techniques.</span></span>  
  
 [<span data-ttu-id="912ee-125">System.Net クラスのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="912ee-125">Best Practices for System.Net Classes</span></span>](best-practices-for-system-net-classes.md)  
 <span data-ttu-id="912ee-126">インターネット アプリケーションを最大限に活用するためのヒントとテクニックを紹介します。</span><span class="sxs-lookup"><span data-stu-id="912ee-126">Provides tips and tricks for getting the most out of your Internet applications.</span></span>  
  
 [<span data-ttu-id="912ee-127">プロキシを介したインターネットへのアクセス</span><span class="sxs-lookup"><span data-stu-id="912ee-127">Accessing the Internet Through a Proxy</span></span>](accessing-the-internet-through-a-proxy.md)  
 <span data-ttu-id="912ee-128">プロキシの設定方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-128">Describes how to configure proxies.</span></span>  
  
 [<span data-ttu-id="912ee-129">ネットワーク情報</span><span class="sxs-lookup"><span data-stu-id="912ee-129">NetworkInformation</span></span>](networkinformation.md)  
 <span data-ttu-id="912ee-130">ネットワーク イベント、変更、統計、およびプロパティの情報を収集する方法について説明し、 <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> クラスを使用してリモート ホストに到達可能であるかどうかを判定する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-130">Describes how to gather information about network events, changes, statistics, and properties and also explains how to determine whether a remote host is reachable by using the <xref:System.Net.NetworkInformation.Ping?displayProperty=nameWithType> class.</span></span>  
  
 [<span data-ttu-id="912ee-131">バージョン 2.0 での System.Uri 名前空間の変更</span><span class="sxs-lookup"><span data-stu-id="912ee-131">Changes to the System.Uri namespace in Version 2.0</span></span>](changes-to-the-system-uri-namespace-in-version-2-0.md)  
 <span data-ttu-id="912ee-132">Version 2.0 で正しくない動作を修正し、使いやすさを改善し、セキュリティを強化するために <xref:System.Uri?displayProperty=nameWithType> クラスに加えられたいくつかの変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-132">Describes several changes made to the <xref:System.Uri?displayProperty=nameWithType> class in Version 2.0 to fixed incorrect behavior, enhance usability, and enhance security.</span></span>  
  
 [<span data-ttu-id="912ee-133">System.Uri での International Resource Identifier のサポート</span><span class="sxs-lookup"><span data-stu-id="912ee-133">International Resource Identifier Support in System.Uri</span></span>](international-resource-identifier-support-in-system-uri.md)  
 <span data-ttu-id="912ee-134">Version 3.5、3.0 SP1、および 2.0 SP1 で、International Resource Identifier (IRI) および国際化ドメイン名 (IDN) をサポートするために、 <xref:System.Uri?displayProperty=nameWithType> クラスに追加された強化機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-134">Describes enhancements to the <xref:System.Uri?displayProperty=nameWithType> class in Version 3.5, 3.0 SP1, and 2.0 SP1 for International Resource Identifier (IRI) and Internationalized Domain Name (IDN) support.</span></span>  
  
 [<span data-ttu-id="912ee-135">バージョン 3.5 のソケット パフォーマンスの強化</span><span class="sxs-lookup"><span data-stu-id="912ee-135">Socket Performance Enhancements in Version 3.5</span></span>](socket-performance-enhancements-in-version-3-5.md)  
 <span data-ttu-id="912ee-136">Version 3.5、3.0 SP1、および 2.0 SP1 で、 <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> クラスに追加された一連の強化機能について説明します。これらの機能によって、目的に特化した高パフォーマンスのソケット アプリケーションで使用できる代替非同期パターンが提供されます。</span><span class="sxs-lookup"><span data-stu-id="912ee-136">Describes a set of enhancements to the <xref:System.Net.Sockets.Socket?displayProperty=nameWithType> class in Version 3.5, 3.0 SP1, and 2.0 SP1 that provide an alternative asynchronous pattern that can be used by specialized high-performance socket applications.</span></span>  
  
 [<span data-ttu-id="912ee-137">ピア名解決プロトコル</span><span class="sxs-lookup"><span data-stu-id="912ee-137">Peer Name Resolution Protocol</span></span>](peer-name-resolution-protocol.md)  
 <span data-ttu-id="912ee-138">Version 3.5 で、ピア名解決プロトコル (PNRP)、サーバーを使用しない動的な名前登録、および名前解決プロトコルをサポートするために追加されたサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-138">Describes support added in Version 3.5 to support the Peer Name Resolution Protocol (PNRP), a serverless and dynamic name registration and name resolution protocol.</span></span> <span data-ttu-id="912ee-139">これらの新機能は、 <xref:System.Net.PeerToPeer?displayProperty=nameWithType> 名前空間によってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="912ee-139">These new features are supported by the <xref:System.Net.PeerToPeer?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="912ee-140">ピアツーピア コラボレーション</span><span class="sxs-lookup"><span data-stu-id="912ee-140">Peer-to-Peer Collaboration</span></span>](peer-to-peer-collaboration.md)  
 <span data-ttu-id="912ee-141">Version 3.5 で、PNRP に基づくピア ツー ピア コラボレーションをサポートするために追加されたサポートについて説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-141">Describes support added in Version 3.5 to support the Peer-to-Peer Collaboration that builds on PNRP.</span></span> <span data-ttu-id="912ee-142">これらの新機能は、 <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> 名前空間によってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="912ee-142">These new features are supported by the <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType> namespace.</span></span>  
  
 [<span data-ttu-id="912ee-143">バージョン 3.5 SP1 における HttpWebRequest の NTLM 認証への変更</span><span class="sxs-lookup"><span data-stu-id="912ee-143">Changes to NTLM authentication for HttpWebRequest in Version 3.5 SP1</span></span>](changes-to-ntlm-authentication-for-httpwebrequest-in-version-3-5-sp1.md)  
 <span data-ttu-id="912ee-144">System.Net 名前空間の <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>、 <xref:System.Net.HttpListener?displayProperty=nameWithType>、 <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>、および関連クラスによる統合 Windows 認証の処理方法に影響を与える、Version 3.5 SP1 で行われたセキュリティの変更について説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-144">Describes security changes made in Version 3.5 SP1 that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, and related classes in the System.Net namespace.</span></span>  
  
 [<span data-ttu-id="912ee-145">統合 Windows 認証と拡張保護</span><span class="sxs-lookup"><span data-stu-id="912ee-145">Integrated Windows Authentication with Extended Protection</span></span>](integrated-windows-authentication-with-extended-protection.md)  
 <span data-ttu-id="912ee-146"><xref:System.Net.HttpWebRequest?displayProperty=nameWithType>名前空間および関連名前空間の <xref:System.Net.HttpListener?displayProperty=nameWithType>、 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>、 <xref:System.Net.Security.SslStream?displayProperty=nameWithType>、 <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>、 <xref:System.Net?displayProperty=nameWithType> 、および関連クラスによる統合 Windows 認証の処理方法に影響を与える、拡張保護用の強化機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-146">Describes enhancements for extended protection that affect how integrated Windows authentication is handled by the <xref:System.Net.HttpWebRequest?displayProperty=nameWithType>, <xref:System.Net.HttpListener?displayProperty=nameWithType>, <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>, <xref:System.Net.Security.SslStream?displayProperty=nameWithType>, <xref:System.Net.Security.NegotiateStream?displayProperty=nameWithType>, and related classes in the <xref:System.Net?displayProperty=nameWithType> and related namespaces.</span></span>  
  
 [<span data-ttu-id="912ee-147">IPv6 および Teredo を使用した NAT トラバーサル</span><span class="sxs-lookup"><span data-stu-id="912ee-147">NAT Traversal using IPv6 and Teredo</span></span>](nat-traversal-using-ipv6-and-teredo.md)  
 <span data-ttu-id="912ee-148">IPv6 および Teredo を使用する NAT トラバースをサポートするために、 <xref:System.Net?displayProperty=nameWithType>、 <xref:System.Net.NetworkInformation?displayProperty=nameWithType>、および <xref:System.Net.Sockets?displayProperty=nameWithType> 名前空間に追加された強化機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-148">Describes enhancements added to the <xref:System.Net?displayProperty=nameWithType>, <xref:System.Net.NetworkInformation?displayProperty=nameWithType>, and <xref:System.Net.Sockets?displayProperty=nameWithType> namespaces to support NAT traversal using IPv6 and Teredo.</span></span>  
  
 [<span data-ttu-id="912ee-149">Windows ストア アプリのネットワーク分離</span><span class="sxs-lookup"><span data-stu-id="912ee-149">Network Isolation for Windows Store Apps</span></span>](network-isolation-for-windows-store-apps.md)  
 <span data-ttu-id="912ee-150"><xref:System.Net>、 <xref:System.Net.Http>、および <xref:System.Net.Http.Headers> 名前空間のクラスを Windows 8.x ストア アプリで使用したときのネットワーク分離の影響について説明します。</span><span class="sxs-lookup"><span data-stu-id="912ee-150">Describes the impact of network isolation when classes in the <xref:System.Net>, <xref:System.Net.Http>, and <xref:System.Net.Http.Headers> namespaces are used in Windows 8.x Store apps.</span></span>  
  
 [<span data-ttu-id="912ee-151">ネットワーク プログラミングのサンプル</span><span class="sxs-lookup"><span data-stu-id="912ee-151">Network Programming Samples</span></span>](network-programming-samples.md)  
 <span data-ttu-id="912ee-152"><xref:System.Net>、 <xref:System.Net.Cache>、 <xref:System.Net.Configuration>、 <xref:System.Net.Mail>、 <xref:System.Net.Mime>、 <xref:System.Net.NetworkInformation>、 <xref:System.Net.PeerToPeer>、 <xref:System.Net.Security>、 <xref:System.Net.Sockets> 名前空間のクラスを使用する、ダウンロード可能なネットワーク プログラミング サンプルへのリンク。</span><span class="sxs-lookup"><span data-stu-id="912ee-152">Links to downloadable network programming samples that use classes in the <xref:System.Net>, <xref:System.Net.Cache>, <xref:System.Net.Configuration>, <xref:System.Net.Mail>, <xref:System.Net.Mime>, <xref:System.Net.NetworkInformation>, <xref:System.Net.PeerToPeer>, <xref:System.Net.Security>, <xref:System.Net.Sockets> namespaces.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="912ee-153">関連項目</span><span class="sxs-lookup"><span data-stu-id="912ee-153">Reference</span></span>  

 <xref:System.Net?displayProperty=nameWithType>  
 <span data-ttu-id="912ee-154">最近のネットワークで使用されている多くのプロトコル用の単純なプログラミング インターフェイスを提供します。</span><span class="sxs-lookup"><span data-stu-id="912ee-154">Provides a simple programming interface for many of the protocols used on networks today.</span></span> <span data-ttu-id="912ee-155">この名前空間の <xref:System.Net.WebRequest?displayProperty=nameWithType> および <xref:System.Net.WebResponse?displayProperty=nameWithType> クラスは、プラグ可能なプロトコルの基礎です。</span><span class="sxs-lookup"><span data-stu-id="912ee-155">The <xref:System.Net.WebRequest?displayProperty=nameWithType> and <xref:System.Net.WebResponse?displayProperty=nameWithType> classes in this namespace are the basis for pluggable protocols.</span></span>  
  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 <span data-ttu-id="912ee-156">取得したリソースのキャッシュ ポリシーを <xref:System.Net.WebRequest?displayProperty=nameWithType> クラスおよび <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> クラスを使用して定義するために使用する型および列挙体を定義します。</span><span class="sxs-lookup"><span data-stu-id="912ee-156">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest?displayProperty=nameWithType> and <xref:System.Net.HttpWebRequest?displayProperty=nameWithType> classes.</span></span>  
  
 <xref:System.Net.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="912ee-157">アプリケーションが System.Net 名前空間の構成設定にプログラムでアクセスして更新するために使用するクラス。</span><span class="sxs-lookup"><span data-stu-id="912ee-157">Classes that applications use to programmatically access and update configuration settings for the System.Net namespaces.</span></span>  
  
 <xref:System.Net.Http?displayProperty=nameWithType>  
 <span data-ttu-id="912ee-158">最新の HTTP アプリケーション用のプログラミング インターフェイスを提供するクラス。</span><span class="sxs-lookup"><span data-stu-id="912ee-158">Classes that provides a programming interface for modern HTTP applications.</span></span>  
  
 <xref:System.Net.Http.Headers?displayProperty=nameWithType>  
 <span data-ttu-id="912ee-159"><xref:System.Net.Http?displayProperty=nameWithType> 名前空間で使用される HTTP ヘッダーのコレクションのサポートを提供します。</span><span class="sxs-lookup"><span data-stu-id="912ee-159">Provides support for collections of HTTP headers used by the <xref:System.Net.Http?displayProperty=nameWithType> namespace</span></span>  
  
 <xref:System.Net.Mail?displayProperty=nameWithType>  
 <span data-ttu-id="912ee-160">SMTP プロトコルを使用してメールを作成および送信するクラス。</span><span class="sxs-lookup"><span data-stu-id="912ee-160">Classes to compose and send mail using the SMTP protocol.</span></span>  
  
 <xref:System.Net.Mime?displayProperty=nameWithType>  
 <span data-ttu-id="912ee-161">Defines types that are used to represent Multipurpose Internet Mail Exchange (MIME) headers used by classes in the <xref:System.Net.Mail?displayProperty=nameWithType> 名前空間のクラスが、MIME (Multipurpose Internet Mail Exchange) ヘッダーを表すために使用する型を定義します。</span><span class="sxs-lookup"><span data-stu-id="912ee-161">Defines types that are used to represent Multipurpose Internet Mail Exchange (MIME) headers used by classes in the <xref:System.Net.Mail?displayProperty=nameWithType> namespace.</span></span>  
  
 <xref:System.Net.NetworkInformation?displayProperty=nameWithType>  
 <span data-ttu-id="912ee-162">ネットワーク イベント、変更、統計、およびプロパティについての情報をプログラムで収集するクラス。</span><span class="sxs-lookup"><span data-stu-id="912ee-162">Classes to programmatically gather information about network events, changes, statistics, and properties.</span></span>  
  
 <xref:System.Net.PeerToPeer?displayProperty=nameWithType>  
 <span data-ttu-id="912ee-163">ピア名前解決プロトコル (PNRP) のマネージド実装を開発者に提供します。</span><span class="sxs-lookup"><span data-stu-id="912ee-163">Provides a managed implementation of the Peer Name Resolution Protocol (PNRP) for developers.</span></span>  
  
 <xref:System.Net.PeerToPeer.Collaboration?displayProperty=nameWithType>  
 <span data-ttu-id="912ee-164">ピア ツー ピア コラボレーション インターフェイスのマネージド実装を開発者に提供します。</span><span class="sxs-lookup"><span data-stu-id="912ee-164">Provides a managed implementation of the Peer-to-Peer Collaboration interface for developers.</span></span>  
  
 <xref:System.Net.Security?displayProperty=nameWithType>  
 <span data-ttu-id="912ee-165">ホスト間の安全な通信のためのネットワーク ストリームを提供するクラス。</span><span class="sxs-lookup"><span data-stu-id="912ee-165">Classes to provide network streams for secure communications between hosts.</span></span>  
  
 <xref:System.Net.Sockets?displayProperty=nameWithType>  
 <span data-ttu-id="912ee-166">ネットワークへのアクセスの制御を支援する必要のある開発者のための、Windows ソケット (Winsock) インターフェイスのマネージド実装が用意されています。</span><span class="sxs-lookup"><span data-stu-id="912ee-166">Provides a managed implementation of the Windows Sockets (Winsock) interface for developers who need to help control access to the network.</span></span>  
  
 <xref:System.Net.WebSockets?displayProperty=nameWithType>  
 <span data-ttu-id="912ee-167">WebSocket インターフェイスのマネージド実装を開発者に提供します。</span><span class="sxs-lookup"><span data-stu-id="912ee-167">Provides a managed implementation of the WebSocket interface for developers.</span></span>  
  
 <xref:System.Uri?displayProperty=nameWithType>  
 <span data-ttu-id="912ee-168">URI (Uniform Resource Identifier) のオブジェクト表現を可能にし、URI の一部へ簡単にアクセスできるようにします。</span><span class="sxs-lookup"><span data-stu-id="912ee-168">Provides an object representation of a uniform resource identifier (URI) and easy access to the parts of the URI.</span></span>  
  
 <xref:System.Security.Authentication.ExtendedProtection?displayProperty=nameWithType>  
 <span data-ttu-id="912ee-169">アプリケーションの拡張保護を使用した認証をサポートします。</span><span class="sxs-lookup"><span data-stu-id="912ee-169">Provides support for authentication using extended protection for applications.</span></span>  
  
 <xref:System.Security.Authentication.ExtendedProtection.Configuration?displayProperty=nameWithType>  
 <span data-ttu-id="912ee-170">アプリケーションの拡張保護を使用した認証の構成をサポートします。</span><span class="sxs-lookup"><span data-stu-id="912ee-170">Provides support for configuration of authentication using extended protection for applications.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="912ee-171">関連項目</span><span class="sxs-lookup"><span data-stu-id="912ee-171">See also</span></span>

- [<span data-ttu-id="912ee-172">.NET Framework でのトランスポート層セキュリティ (TLS) のベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="912ee-172">Transport Layer Security (TLS) best practices with .NET Framework</span></span>](tls.md)
- [<span data-ttu-id="912ee-173">ネットワーク プログラミング方法のトピック</span><span class="sxs-lookup"><span data-stu-id="912ee-173">Network Programming How-to Topics</span></span>](network-programming-how-to-topics.md)
- [<span data-ttu-id="912ee-174">ネットワーク プログラミングのサンプル</span><span class="sxs-lookup"><span data-stu-id="912ee-174">Network Programming Samples</span></span>](network-programming-samples.md)
- [<span data-ttu-id="912ee-175">HttpClient のサンプル</span><span class="sxs-lookup"><span data-stu-id="912ee-175">HttpClient Sample</span></span>](https://code.msdn.microsoft.com/windowsapps/HttpClient-sample-55700664)
