---
title: .NET Framework を使用した Windows ベースのクライアント アプリケーションの開発
description: .NET を使用して Windows ベースのアプリケーションを開発します。 ユニバーサル Windows プラットフォーム (UWP)、Windows Presentation Foundation (WPF)、または Windows フォームを使用できます。
ms.date: 01/09/2018
helpviewer_keywords:
- client application services
- applications [Windows Forms]
- Windows Presentation Foundation, in Visual Studio
- WPF, in Visual Studio
- Windows applications
- rich client applications
- .NET applications, Windows applications
- Visual Basic code, creating applications
- Visual C#, creating applications
- client/server applications, Windows applications
ms.assetid: 2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68
ms.openlocfilehash: e8d3a95b58cd2cabc41be31b7a4b66b1a79317d6
ms.sourcegitcommit: 30a686fd4377fe6472aa04e215c0de711bc1c322
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/10/2020
ms.locfileid: "94439431"
---
# <a name="develop-client-applications-with-net-framework"></a><span data-ttu-id="ddcee-104">.NET Framework を使用したクライアント アプリケーションの開発</span><span class="sxs-lookup"><span data-stu-id="ddcee-104">Develop client applications with .NET Framework</span></span>

<span data-ttu-id="ddcee-105">.NET Framework で Windows ベースのアプリケーションを開発する方法は複数あります。</span><span class="sxs-lookup"><span data-stu-id="ddcee-105">There are several ways to develop Windows-based applications with .NET Framework.</span></span> <span data-ttu-id="ddcee-106">次のツールおよびフレームワークのいずれかを使用することができます。</span><span class="sxs-lookup"><span data-stu-id="ddcee-106">You can use any of these tools and frameworks:</span></span>

- [<span data-ttu-id="ddcee-107">ユニバーサル Windows プラットフォーム (UWP)</span><span class="sxs-lookup"><span data-stu-id="ddcee-107">Universal Windows Platform (UWP)</span></span>](/windows/uwp/)
- [<span data-ttu-id="ddcee-108">Windows Presentation Foundation (WPF)</span><span class="sxs-lookup"><span data-stu-id="ddcee-108">Windows Presentation Foundation (WPF)</span></span>](/dotnet/desktop/wpf/)
- [<span data-ttu-id="ddcee-109">Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="ddcee-109">Windows Forms</span></span>](/dotnet/desktop/winforms/)

<span data-ttu-id="ddcee-110">このセクションには、Windows Presentation Foundation または Windows Forms を使用して Windows ベースのアプリケーションを作成する方法について説明している記事があります。</span><span class="sxs-lookup"><span data-stu-id="ddcee-110">This section contains articles that describe how to create Windows-based applications by using Windows Presentation Foundation or Windows Forms.</span></span> <span data-ttu-id="ddcee-111">ただし、.NET Framework を使用して Web アプリケーションを作成したり、コンピューターやデバイス向けのクライアント アプリケーションを作成したりして、Microsoft Store (UWP アプリ) で公開することもできます。</span><span class="sxs-lookup"><span data-stu-id="ddcee-111">However, you can also create web applications using .NET Framework and client applications for computers or devices that you make available through Microsoft Store (UWP apps).</span></span>

## <a name="related-sections"></a><span data-ttu-id="ddcee-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="ddcee-112">Related sections</span></span>

<span data-ttu-id="ddcee-113">[ユニバーサル Windows プラットフォーム](/windows/uwp/)</span><span class="sxs-lookup"><span data-stu-id="ddcee-113">[Universal Windows Platform](/windows/uwp/)</span></span>\
<span data-ttu-id="ddcee-114">Microsoft Store を通じてユーザーが入手できる UWP アプリケーションを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ddcee-114">Describes how to create UWP applications that you can make available to users through Microsoft Store.</span></span>

<span data-ttu-id="ddcee-115">[UWP アプリ用 .NET API](../../api/index.md?view=dotnet-uwp-10.0)</span><span class="sxs-lookup"><span data-stu-id="ddcee-115">[.NET API for UWP apps](../../api/index.md?view=dotnet-uwp-10.0)</span></span>\
<span data-ttu-id="ddcee-116">UWP アプリをサポートする .NET 型のリファレンス。</span><span class="sxs-lookup"><span data-stu-id="ddcee-116">Reference for .NET types that support UWP apps.</span></span>
  
<span data-ttu-id="ddcee-117">[複数のプラットフォーム向けの開発](./cross-platform/index.md)</span><span class="sxs-lookup"><span data-stu-id="ddcee-117">[Develop for Multiple Platforms](./cross-platform/index.md)</span></span>\
<span data-ttu-id="ddcee-118">複数の種類のクライアント アプリを対象にするために .NET Framework を使用できるさまざまな方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ddcee-118">Describes the different methods you can use .NET Framework to target multiple client app types.</span></span>

<span data-ttu-id="ddcee-119">[ASP.NET Web サイト入門](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span><span class="sxs-lookup"><span data-stu-id="ddcee-119">[Get Started with ASP.NET Web Sites](https://dotnet.microsoft.com/apps/aspnet/web-apps)</span></span>\
<span data-ttu-id="ddcee-120">ASP.NET を使用して Web アプリを開発する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="ddcee-120">Describes the ways you can develop web apps using ASP.NET.</span></span>

<span data-ttu-id="ddcee-121">[Windows Phone Silverlight 用の .NET API](/previous-versions/windows/apps/jj207211\(v=vs.105\))</span><span class="sxs-lookup"><span data-stu-id="ddcee-121">[.NET API for Windows Phone Silverlight](/previous-versions/windows/apps/jj207211\(v=vs.105\))</span></span>\
<span data-ttu-id="ddcee-122">Windows Phone Silverlight を使用したアプリを構築するために利用できる .NET Framework API の一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="ddcee-122">Lists .NET Framework APIs you can use for building apps with Windows Phone Silverlight.</span></span>

## <a name="see-also"></a><span data-ttu-id="ddcee-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="ddcee-123">See also</span></span>

- [<span data-ttu-id="ddcee-124">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="ddcee-124">.NET Standard</span></span>](../standard/net-standard.md)
- [<span data-ttu-id="ddcee-125">概要</span><span class="sxs-lookup"><span data-stu-id="ddcee-125">Overview</span></span>](./get-started/overview.md)
- [<span data-ttu-id="ddcee-126">開発ガイド</span><span class="sxs-lookup"><span data-stu-id="ddcee-126">Development Guide</span></span>](./development-guide.md)
- [<span data-ttu-id="ddcee-127">Windows サービス アプリケーション</span><span class="sxs-lookup"><span data-stu-id="ddcee-127">Windows Service Applications</span></span>](./windows-services/index.md)
