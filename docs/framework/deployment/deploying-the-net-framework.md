---
title: .NET Framework の配置
description: アプリケーションと共に .NET をインストールする開発者、およびネットワーク経由で .NET を配置する管理者を対象に、.NET を配置する方法について説明します。
ms.date: 03/30/2017
helpviewer_keywords:
- .NET Framework, deploying
- deployment [.NET Framework]
ms.assetid: 19df26c5-4008-461d-a7d7-18f4506312d2
ms.openlocfilehash: b42646b60fab91fe761a8fdef59d67be6ffa884b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96242046"
---
# <a name="deploying-the-net-framework"></a><span data-ttu-id="d269b-103">.NET Framework の配置</span><span class="sxs-lookup"><span data-stu-id="d269b-103">Deploying the .NET Framework</span></span>

<span data-ttu-id="d269b-104">.NET Framework ドキュメントのこのセクションでは、アプリケーションとともに .NET Framework をインストールする開発者、およびネットワーク上で .NET Framework を展開する管理者に対して情報を提供します。</span><span class="sxs-lookup"><span data-stu-id="d269b-104">This section of the .NET Framework documentation provides information for developers who want to install the .NET Framework with their applications, and administrators who want to deploy the .NET Framework across a network.</span></span> <span data-ttu-id="d269b-105">また、アクティベーション、配置に伴う再起動の問題、.NET Framework のインストールの進捗を監視する方法についても説明します。</span><span class="sxs-lookup"><span data-stu-id="d269b-105">It also discusses activation and restart issues associated with deployment, and how to monitor the progress of your .NET Framework installation.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d269b-106">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="d269b-106">In This Section</span></span>  

 [<span data-ttu-id="d269b-107">配置ガイド (開発者向け)</span><span class="sxs-lookup"><span data-stu-id="d269b-107">Deployment Guide for Developers</span></span>](deployment-guide-for-developers.md)  
 <span data-ttu-id="d269b-108">開発者による .NET Framework とアプリケーションのユーザーのコンピューターへのインストール方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d269b-108">Explains how developers can install .NET Framework on their users' computers with their applications.</span></span>  
  
 [<span data-ttu-id="d269b-109">配置ガイド (管理者向け)</span><span class="sxs-lookup"><span data-stu-id="d269b-109">Deployment Guide for Administrators</span></span>](guide-for-administrators.md)  
 <span data-ttu-id="d269b-110">システム管理者が、Microsoft Endpoint Configuration Manager を使用して、ネットワーク全体に .NET Framework とその依存関係を配置する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d269b-110">Explains how a system administrator can deploy the .NET Framework and its system dependencies across a network by using Microsoft Endpoint Configuration Manager.</span></span>  
  
 [<span data-ttu-id="d269b-111">.NET Framework 4.5 のインストール中のシステム再起動の削減</span><span class="sxs-lookup"><span data-stu-id="d269b-111">Reducing System Restarts During .NET Framework 4.5 Installations</span></span>](reducing-system-restarts.md)  
 <span data-ttu-id="d269b-112">再起動をできる限り回避する再起動マネージャーと、.NET Framework をインストールするアプリケーションがそれをどのように利用できるかを説明しています。</span><span class="sxs-lookup"><span data-stu-id="d269b-112">Describes the Restart Manager, which prevents reboots whenever possible, and explains how applications that install the .NET Framework can take advantage of it.</span></span>  
  
 [<span data-ttu-id="d269b-113">方法: .NET Framework 4.5 インストーラーの進行状況を表示する</span><span class="sxs-lookup"><span data-stu-id="d269b-113">How to: Get Progress from the .NET Framework 4.5 Installer</span></span>](how-to-get-progress-from-the-dotnet-installer.md)  
 <span data-ttu-id="d269b-114">進行状況のビューを独自に表示する一方で、.NET Framework セットアップ プロセスをサイレントで起動および追跡する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="d269b-114">Describes how to silently launch and track the .NET Framework setup process while showing your own view of the setup progress.</span></span>  
  
 [<span data-ttu-id="d269b-115">.NET Framework の初期化エラー: ユーザー エクスペリエンスの管理</span><span class="sxs-lookup"><span data-stu-id="d269b-115">.NET Framework Initialization Errors: Managing the User Experience</span></span>](initialization-errors-managing-the-user-experience.md)  
 <span data-ttu-id="d269b-116">ユーザーのコンピューターで無効な、またはインストールされていない CLR バージョンが .NET Framework アプリケーションで必要になると何が起きるか、そしてこのようなエラーの解決方法と、ユーザーに表示されるエラー メッセージの制御方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d269b-116">Explains what happens when a .NET Framework application requires a CLR version that's invalid or not installed on the user's computer, how to resolve these errors, and how to control the error message displayed to the user.</span></span>  
  
 [<span data-ttu-id="d269b-117">方法: CLR のアクティブ化に関する問題をデバッグする</span><span class="sxs-lookup"><span data-stu-id="d269b-117">How to: Debug CLR Activation Issues</span></span>](how-to-debug-clr-activation-issues.md)  
 <span data-ttu-id="d269b-118">正しいバージョンの CLR でアプリケーションを実行して発生した問題を解決するために、どのようにして CLR アクティベーション ログを表示し、デバッグするかを説明します。</span><span class="sxs-lookup"><span data-stu-id="d269b-118">Explains how you can view and debug CLR activation logs to resolve issues you may encounter in getting your application to run with the correct version of the CLR.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d269b-119">関連項目</span><span class="sxs-lookup"><span data-stu-id="d269b-119">See also</span></span>

- [<span data-ttu-id="d269b-120">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="d269b-120">Development Guide</span></span>](../development-guide.md)
