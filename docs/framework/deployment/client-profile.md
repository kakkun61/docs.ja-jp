---
title: .NET Framework Client Profile
description: .NET のバージョン 4 以前のエディションで提供されていた .NET のサブセットだった .NET Client Profile について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- WPF [.NET Framework Client Profile]
- WCF [.NET Framework Client Profile]
- Windows Forms [.NET Framework Client Profile]
- client profile [.NET Framework Client Profile]
- profile [.NET Framework Client Profile]
- .NET Framework Client Profile
ms.assetid: f0219919-1f02-4588-8704-327a62fd91f1
ms.openlocfilehash: 92ade654b20c5971482464ce1cb9619c434679b6
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96236391"
---
# <a name="net-framework-client-profile"></a><span data-ttu-id="27372-103">.NET Framework Client Profile</span><span class="sxs-lookup"><span data-stu-id="27372-103">.NET Framework Client Profile</span></span>

<span data-ttu-id="27372-104">.NET Client Profile は、.NET Framework のサブセットで、.NET Framework 4 以前のバージョンに含まれ、クライアント アプリケーション用に最適化されていました。</span><span class="sxs-lookup"><span data-stu-id="27372-104">The .NET Client Profile is a subset of the .NET Framework, which was provided with .NET Framework 4 and earlier versions and was optimized for client applications.</span></span> <span data-ttu-id="27372-105">.NET Framework は、Windows、Windows Phone、および Microsoft Azure 用の開発プラットフォームであり、マネージド アプリの実行環境と .NET Framework クラス ライブラリを提供します。</span><span class="sxs-lookup"><span data-stu-id="27372-105">The .NET Framework is a development platform for Windows, Windows Phone and Microsoft Azure and provides a managed app execution environment and the .NET Framework class library.</span></span> <span data-ttu-id="27372-106">.NET Framework 4 以前のバージョンでは、2 種類の配置オプション (完全な .NET Framework と Client Profile) が用意されていました。</span><span class="sxs-lookup"><span data-stu-id="27372-106">The .NET Framework 4 and earlier versions provided two deployment options: the full .NET Framework and the Client Profile.</span></span> <span data-ttu-id="27372-107">完全な .NET Framework に比べて、Client Profile では、配置の迅速化とアプリ インストール パッケージの小型化が実現されました。</span><span class="sxs-lookup"><span data-stu-id="27372-107">The Client Profile enabled faster deployment and smaller app installation packages than the full .NET Framework.</span></span>  
  
 <span data-ttu-id="27372-108">.NET Framework 4.5 以降では、Client Profile が中止され、完全な再頒布可能パッケージのみが使用できます。</span><span class="sxs-lookup"><span data-stu-id="27372-108">Starting with the .NET Framework 4.5, the Client Profile has been discontinued and only the full redistributable package is available.</span></span> <span data-ttu-id="27372-109">より小さいダウンロード サイズや高速化された配置などの .NET Framework 4.5 の最適化により、別の配置パッケージが不要になりました。</span><span class="sxs-lookup"><span data-stu-id="27372-109">Optimizations provided by the .NET Framework 4.5, such as smaller download size and faster deployment, have eliminated the need for a separate deployment package.</span></span> <span data-ttu-id="27372-110">単一の再頒布可能パッケージにより、インストール プロセスが効率化され、アプリケーションの配置オプションが簡略化されます。</span><span class="sxs-lookup"><span data-stu-id="27372-110">The single redistributable streamlines the installation process and simplifies your app's deployment options.</span></span>  
  
 <span data-ttu-id="27372-111">ただし、.NET Framework 4 または 3.5 を対象とする場合、Client Profile の概要と用途については、.NET Framework 4 ドキュメントの「[.NET Framework Client Profile](/previous-versions/dotnet/netframework-4.0/cc656912(v=vs.100))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27372-111">However, if you are targeting the .NET Framework 4 or 3.5 and want to learn more about the Client Profile and when to use it, see [.NET Framework Client Profile](/previous-versions/dotnet/netframework-4.0/cc656912(v=vs.100)) in the .NET Framework 4 documentation.</span></span>  
  
 <span data-ttu-id="27372-112">.NET Framework 4.5 をインストールすると、.NET Framework 4 Client Profile は .NET Framework の完全バージョンに更新されます。</span><span class="sxs-lookup"><span data-stu-id="27372-112">When you install the .NET Framework 4.5, the .NET Framework 4 Client Profile is updated to the full version of the .NET Framework.</span></span> <span data-ttu-id="27372-113">.NET Framework 4.5 のインストールの詳細については、「[開発者向けの .NET Framework のインストール](../install/guide-for-developers.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="27372-113">For information about installing the .NET Framework 4.5, see [Install the .NET Framework for developers](../install/guide-for-developers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27372-114">関連項目</span><span class="sxs-lookup"><span data-stu-id="27372-114">See also</span></span>

- <span data-ttu-id="27372-115">[.NET Framework Client Profile (.NET Framework 4)](/previous-versions/dotnet/netframework-4.0/cc656912(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="27372-115">[.NET Framework Client Profile (.NET Framework 4)](/previous-versions/dotnet/netframework-4.0/cc656912(v=vs.100))</span></span>
- [<span data-ttu-id="27372-116">Visual Studio のマルチ ターゲットの概要</span><span class="sxs-lookup"><span data-stu-id="27372-116">Visual Studio Multi-Targeting Overview</span></span>](/visualstudio/ide/visual-studio-multi-targeting-overview)
- [<span data-ttu-id="27372-117">.NET Framework を対象とするエラーのトラブルシューティング</span><span class="sxs-lookup"><span data-stu-id="27372-117">Troubleshooting .NET Framework Targeting Errors</span></span>](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors)
- [<span data-ttu-id="27372-118">方法: .NET Framework のバージョンをターゲットにする</span><span class="sxs-lookup"><span data-stu-id="27372-118">How to: Target a Version of the .NET Framework</span></span>](/visualstudio/ide/visual-studio-multi-targeting-overview)
