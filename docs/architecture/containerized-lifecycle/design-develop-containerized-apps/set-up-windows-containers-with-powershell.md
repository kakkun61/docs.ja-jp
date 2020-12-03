---
title: DockerFile で Windows PowerShell コマンドを使用して Windows コンテナー (Docker 標準ベース) を設定する
description: Windows コンテナーで Docker を操作する場合の PowerShell の使用方法について説明します
ms.date: 08/06/2020
ms.openlocfilehash: d65538c821a848d83915e715ee3a02990b40e836
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95681250"
---
# <a name="using-windows-powershell-commands-in-a-dockerfile-to-set-up-windows-containers-docker-standard-based"></a><span data-ttu-id="f7c09-103">DockerFile で Windows PowerShell コマンドを使用して Windows コンテナー (Docker 標準ベース) を設定する</span><span class="sxs-lookup"><span data-stu-id="f7c09-103">Using Windows PowerShell commands in a DockerFile to set up Windows Containers (Docker standard based)</span></span>

<span data-ttu-id="f7c09-104">[Windows コンテナー](/virtualization/windowscontainers/about/index)によって、既存の Windows アプリケーションを Docker イメージに変換して、その他の Docker エコシステムと同じツールでそれらをデプロイできます。</span><span class="sxs-lookup"><span data-stu-id="f7c09-104">With [Windows Containers](/virtualization/windowscontainers/about/index), you can convert your existing Windows applications to Docker images and deploy them with the same tools as the rest of the Docker ecosystem.</span></span>

<span data-ttu-id="f7c09-105">Windows コンテナーを使用するには、次の例に示すように、DockerFile で PowerShell コマンドを記述するだけです。</span><span class="sxs-lookup"><span data-stu-id="f7c09-105">To use Windows Containers, you just need to write Windows PowerShell commands in the DockerFile, as demonstrated in the following example:</span></span>

```dockerfile
FROM mcr.microsoft.com/windows/servercore:ltsc2019
LABEL Description="IIS" Vendor="Microsoft" Version="10"
RUN powershell -Command Add-WindowsFeature Web-Server
CMD [ "ping", "localhost", "-t" ]
```

<span data-ttu-id="f7c09-106">この例では、Windows PowerShell を使用して、Windows Server Core 基本イメージと IIS をインストールしています。</span><span class="sxs-lookup"><span data-stu-id="f7c09-106">In this case, we're using Windows PowerShell to install a Windows Server Core base image as well as IIS.</span></span>

<span data-ttu-id="f7c09-107">同様に、Windows PowerShell コマンドを使用して、次に示すように、従来の ASP.NET 4.x および .NET Framework 4.6 またはその他の任意の Windows ソフトウェアなどの追加コンポーネントを設定することもできます。</span><span class="sxs-lookup"><span data-stu-id="f7c09-107">In a similar way, you also could use Windows PowerShell commands to set up additional components like the traditional ASP.NET 4.x and .NET Framework 4.6 or any other Windows software, as shown here:</span></span>

```dockerfile
RUN powershell add-windowsfeature web-asp-net45
```

>[!div class="step-by-step"]
><span data-ttu-id="f7c09-108">[前へ](visual-studio-tools-for-docker.md)
>[次へ](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="f7c09-108">[Previous](visual-studio-tools-for-docker.md)
[Next](build-aspnet-core-applications-linux-containers-aks-kubernetes.md)</span></span>
