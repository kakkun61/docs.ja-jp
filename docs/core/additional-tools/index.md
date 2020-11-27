---
title: その他のツール
description: .NET Core 機能をサポートおよび拡張する、インストール可能な追加ツールについての概要。
author: mlacouture
ms.date: 02/13/2020
ms.custom: mvc
ms.openlocfilehash: f563dff312442cbf068d52d08992621e3d6f1460
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95699002"
---
# <a name="net-core-additional-tools-overview"></a><span data-ttu-id="cfedd-103">.NET Core の追加ツールの概要</span><span class="sxs-lookup"><span data-stu-id="cfedd-103">.NET Core additional tools overview</span></span>

<span data-ttu-id="cfedd-104">このセクションでは、.NET Core CLI に加えて、.NET Core 機能をサポートおよび拡張するツールの一覧をまとめて説明します。</span><span class="sxs-lookup"><span data-stu-id="cfedd-104">This section compiles a list of tools that support and extend the .NET Core functionality, in addition to the .NET Core CLI.</span></span>

## <a name="net-core-uninstall-tool"></a><span data-ttu-id="cfedd-105">.NET Core アンインストール ツール</span><span class="sxs-lookup"><span data-stu-id="cfedd-105">.NET Core Uninstall Tool</span></span>

<span data-ttu-id="cfedd-106">[.NET Core アンインストール ツール](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) を使うと、システム上の .NET Core SDK とランタイムをクリーンアップし、指定したバージョンのみを残すことができます。</span><span class="sxs-lookup"><span data-stu-id="cfedd-106">The [.NET Core Uninstall Tool](https://github.com/dotnet/cli-lab/releases) (`dotnet-core-uninstall`) lets you clean up .NET Core SDKs and Runtimes on a system such that only the specified versions remain.</span></span> <span data-ttu-id="cfedd-107">一連のオプションを使用して、アンインストールするバージョンを指定できます。</span><span class="sxs-lookup"><span data-stu-id="cfedd-107">A collection of options is available to specify which versions are uninstalled.</span></span>

## <a name="net-core-diagnostic-tools"></a><span data-ttu-id="cfedd-108">.NET Core 診断ツール</span><span class="sxs-lookup"><span data-stu-id="cfedd-108">.NET Core diagnostic tools</span></span>

<span data-ttu-id="cfedd-109">[dotnet-カウンター](../diagnostics/dotnet-counters.md)は、第 1 レベルの正常性監視とパフォーマンス調査のためのパフォーマンス監視ツールです。</span><span class="sxs-lookup"><span data-stu-id="cfedd-109">[dotnet-counters](../diagnostics/dotnet-counters.md) is a performance monitoring tool for first-level health monitoring and performance investigation.</span></span>

<span data-ttu-id="cfedd-110">[dotnet-dump](../diagnostics/dotnet-dump.md) は、ネイティブ デバッガーを使用せずに Windows および Linux のコア ダンプを収集して分析する方法です。</span><span class="sxs-lookup"><span data-stu-id="cfedd-110">[dotnet-dump](../diagnostics/dotnet-dump.md) provides a way to collect and analyze Windows and Linux core dumps without a native debugger.</span></span>

<span data-ttu-id="cfedd-111">[dotnet-gcdump](../diagnostics/dotnet-gcdump.md) は、ライブ .NET プロセスの GC (ガベージコレクター) ダンプを収集する手段を提供します。</span><span class="sxs-lookup"><span data-stu-id="cfedd-111">[dotnet-gcdump](../diagnostics/dotnet-gcdump.md) provides a way to collect GC (Garbage Collector) dumps of live .NET processes.</span></span>

<span data-ttu-id="cfedd-112">[dotnet-trace](../diagnostics/dotnet-trace.md) では、自分のアプリからプロファイル データを収集できます。これは、アプリの実行速度が低下する原因を特定する必要があるシナリオで役立ちます。</span><span class="sxs-lookup"><span data-stu-id="cfedd-112">[dotnet-trace](../diagnostics/dotnet-trace.md) collects profiling data from your app that can help in scenarios where you need to find out what causes an app to run slow.</span></span>

## <a name="wcf-web-service-reference-tool"></a><span data-ttu-id="cfedd-113">WCF Web Service Reference ツール</span><span class="sxs-lookup"><span data-stu-id="cfedd-113">WCF Web Service Reference tool</span></span>

<span data-ttu-id="cfedd-114">WCF (Windows Communication Foundation) [Web Service Reference ツール](wcf-web-service-reference-guide.md)は、Visual Studio に接続されているサービス プロバイダーです。[Visual Studio 2017 バージョン 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools) から導入されました。</span><span class="sxs-lookup"><span data-stu-id="cfedd-114">The WCF (Windows Communication Foundation) [Web Service Reference tool](wcf-web-service-reference-guide.md) is a Visual Studio connected service provider that made its debut in [Visual Studio 2017 version 15.5](/visualstudio/releasenotes/vs2017-relnotes-v15.5#WCFTools).</span></span> <span data-ttu-id="cfedd-115">このツールを使うと、現在のソリューションの Web サービス、ネットワーク上の場所、または WSDL ファイルから、メタデータを取得できます。</span><span class="sxs-lookup"><span data-stu-id="cfedd-115">This tool retrieves metadata from a web service in the current solution, on a network location, or from a WSDL file.</span></span> <span data-ttu-id="cfedd-116">それにより、.NET Core と互換性のあるソース ファイルが生成され、Web サービス操作へのアクセスに使用できるメソッドを含む WCF プロキシ クラスが定義されます。</span><span class="sxs-lookup"><span data-stu-id="cfedd-116">It generates a source file compatible with .NET Core, defining a WCF proxy class with methods that you can use to access the web service operations.</span></span>

## <a name="wcf-dotnet-svcutil-tool"></a><span data-ttu-id="cfedd-117">WCF dotnet-svcutil ツール</span><span class="sxs-lookup"><span data-stu-id="cfedd-117">WCF dotnet-svcutil tool</span></span>

<span data-ttu-id="cfedd-118">WCF の [dotnet-svcutil ツール](dotnet-svcutil-guide.md)は、ネットワークの場所にある Web サービスまたは WSDL ファイルからメタデータを取得する .NET ツールです。</span><span class="sxs-lookup"><span data-stu-id="cfedd-118">The WCF [dotnet-svcutil tool](dotnet-svcutil-guide.md) is a .NET tool that retrieves metadata from a web service on a network location or from a WSDL file.</span></span> <span data-ttu-id="cfedd-119">それにより、.NET Core と互換性のあるソース ファイルが生成され、Web サービス操作へのアクセスに使用できるメソッドを含む WCF プロキシ クラスが定義されます。</span><span class="sxs-lookup"><span data-stu-id="cfedd-119">It generates a source file compatible with .NET Core, defining a WCF proxy class with methods that you can use to access the web service operations.</span></span>

<span data-ttu-id="cfedd-120">**dotnet-svcutil** ツールは、Visual Studio 2017 バージョン 15.5 で最初に用意された Visual Studio 接続済みサービス プロバイダーである、[**WCF Web Service Reference**](wcf-web-service-reference-guide.md) に代わる手段です。</span><span class="sxs-lookup"><span data-stu-id="cfedd-120">The **dotnet-svcutil** tool is an alternative to the [**WCF Web Service Reference**](wcf-web-service-reference-guide.md) Visual Studio connected service provider, which first shipped with Visual Studio 2017 version 15.5.</span></span> <span data-ttu-id="cfedd-121">**dotnet-svcutil** ツールは、.NET ツールとして、Linux、macOS、Windows 上で利用できます。</span><span class="sxs-lookup"><span data-stu-id="cfedd-121">The **dotnet-svcutil** tool, as a .NET tool, is available on Linux, macOS, and Windows.</span></span>

## <a name="wcf-dotnet-svcutilxmlserializer-tool"></a><span data-ttu-id="cfedd-122">WCF dotnet-svcutil.xmlserializer ツール</span><span class="sxs-lookup"><span data-stu-id="cfedd-122">WCF dotnet-svcutil.xmlserializer tool</span></span>

<span data-ttu-id="cfedd-123">.NET Framework 上で、svcutil ツールを使って事前にシリアル化アセンブリを生成することができます。</span><span class="sxs-lookup"><span data-stu-id="cfedd-123">On the .NET Framework, you can pre-generate a serialization assembly using the svcutil tool.</span></span> <span data-ttu-id="cfedd-124">WCF [dotnet-svcutil.xmlserializer ツール](dotnet-svcutil.xmlserializer-guide.md)には、.NET Core に対して同様の機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="cfedd-124">The WCF [dotnet-svcutil.xmlserializer tool](dotnet-svcutil.xmlserializer-guide.md) provides similar functionality on .NET Core.</span></span> <span data-ttu-id="cfedd-125">これは、クライアント アプリケーション内の型で、WCF サービス コントラクトによって使われ <xref:System.Xml.Serialization.XmlSerializer> によってシリアル化できるものに対して、C# のシリアル化コードを事前に生成します。</span><span class="sxs-lookup"><span data-stu-id="cfedd-125">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="cfedd-126">これにより、それらの型のオブジェクトをシリアル化または逆シリアル化するときに XML シリアル化の起動時のパフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="cfedd-126">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="xml-serializer-generator"></a><span data-ttu-id="cfedd-127">XML シリアライザー ジェネレーター</span><span class="sxs-lookup"><span data-stu-id="cfedd-127">XML Serializer Generator</span></span>

<span data-ttu-id="cfedd-128">.NET Framework の [Xml シリアライザー ジェネレーター (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) と同様に、[Microsoft.XmlSerializer.Generator NuGet パッケージ](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator)は .NET Core および .NET Standard ライブラリのソリューションです。</span><span class="sxs-lookup"><span data-stu-id="cfedd-128">Like the [Xml Serializer Generator (sgen.exe)](../../standard/serialization/xml-serializer-generator-tool-sgen-exe.md) for the .NET Framework, the [Microsoft.XmlSerializer.Generator NuGet package](https://www.nuget.org/packages/Microsoft.XmlSerializer.Generator) is the solution for .NET Core and .NET Standard libraries.</span></span> <span data-ttu-id="cfedd-129">アセンブリに含まれる型の XML シリアル化アセンブリを作成することで、<xref:System.Xml.Serialization.XmlSerializer> を使用してその型のオブジェクトをシリアル化または逆シリアル化するときの XML シリアル化の起動パフォーマンスを改善します。</span><span class="sxs-lookup"><span data-stu-id="cfedd-129">It creates an XML serialization assembly for types contained in an assembly to improve the startup performance of XML serialization when serializing or de-serializing objects of those types using <xref:System.Xml.Serialization.XmlSerializer>.</span></span>

## <a name="generating-self-signed-certificates"></a><span data-ttu-id="cfedd-130">自己署名証明書の生成</span><span class="sxs-lookup"><span data-stu-id="cfedd-130">Generating Self-Signed Certificates</span></span>

<span data-ttu-id="cfedd-131">[dotnet dev-cert](self-signed-certificates-guide.md) を使用して、開発およびテストのシナリオ用の自己署名証明書を作成することができます。</span><span class="sxs-lookup"><span data-stu-id="cfedd-131">You can use [dotnet dev-certs](self-signed-certificates-guide.md) to create self-signed certificates for development and testing scenarios.</span></span>
