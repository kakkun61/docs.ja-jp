---
title: Windows コンテナーを展開しない状況
description: Azure Cloud と Windows コンテナーで既存の .NET アプリケーションを最新化する | Windows コンテナーをデプロイしない状況
ms.date: 12/21/2020
ms.openlocfilehash: 4eea24ab8deb3719c778b45b3ddc1309277a3f50
ms.sourcegitcommit: 5d9cee27d9ffe8f5670e5f663434511e81b8ac38
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2021
ms.locfileid: "98025174"
---
# <a name="when-not-to-deploy-to-windows-containers"></a><span data-ttu-id="c466f-103">Windows コンテナーを展開しない状況</span><span class="sxs-lookup"><span data-stu-id="c466f-103">When not to deploy to Windows Containers</span></span>

<span data-ttu-id="c466f-104">一部の Windows テクノロジは、Windows コンテナーでサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c466f-104">Some Windows technologies are not supported by Windows Containers.</span></span> <span data-ttu-id="c466f-105">そのような場合でも、通常は Windows と IIS だけを使用して標準 VM に移行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c466f-105">In those cases, you still need to migrate to the standards VMs, usually with just Windows and IIS.</span></span>

<span data-ttu-id="c466f-106">Windows コンテナーでサポートされていないケース (2018 年 5 月):</span><span class="sxs-lookup"><span data-stu-id="c466f-106">Cases not supported in Windows Containers, as of May 2018:</span></span>

- <span data-ttu-id="c466f-107">Microsoft メッセージ キュー (MSMQ) は現在のところ、Windows Server v1803 リリースをベースとする Windows コンテナーでのみ利用できます。それ以前のリリースでは利用できません。</span><span class="sxs-lookup"><span data-stu-id="c466f-107">Microsoft Message Queuing (MSMQ) currently is only available in Windows Containers based on Windows Server v1803 release, but not in any other prior releases.</span></span>

  - [<span data-ttu-id="c466f-108">UserVoice リクエスト フォーラム</span><span class="sxs-lookup"><span data-stu-id="c466f-108">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/15719031-create-base-container-image-with-msmq-server)

  - [<span data-ttu-id="c466f-109">ディスカッション フォーラム</span><span class="sxs-lookup"><span data-stu-id="c466f-109">Discussion forum</span></span>](https://social.msdn.microsoft.com/Forums/bce99a7d-aa60-44fa-a348-450855650810/msmqserver-is-it-supported?forum=windowscontainers)

- <span data-ttu-id="c466f-110">Microsoft 分散トランザクション コーディネーター (MSDTC) は現在のところ、Windows コンテナーでサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c466f-110">Microsoft Distributed Transaction Coordinator (MSDTC) currently is not supported in Windows Containers.</span></span>

  - [<span data-ttu-id="c466f-111">GitHub の問題</span><span class="sxs-lookup"><span data-stu-id="c466f-111">GitHub issue</span></span>](https://github.com/MicrosoftDocs/Virtualization-Documentation/issues/494)

- <span data-ttu-id="c466f-112">Microsoft Office では現在、コンテナーがサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="c466f-112">Microsoft Office currently does not support containers.</span></span>

  - [<span data-ttu-id="c466f-113">UserVoice リクエスト フォーラム</span><span class="sxs-lookup"><span data-stu-id="c466f-113">UserVoice request forum</span></span>](https://windowsserver.uservoice.com/forums/304624-containers/suggestions/19686220-provide-office-support-for-containers)

- <span data-ttu-id="c466f-114">UI アプリ (ビジュアル ユーザー インターフェイスのあるクライアント アプリ) は、サポートされていないシナリオです。</span><span class="sxs-lookup"><span data-stu-id="c466f-114">UI apps (client apps with a visual user interface) are not supported scenarios.</span></span>

- <span data-ttu-id="c466f-115">Windows インフラストラクチャの役割 (DNS、DHCP、DC、NTP、PRINT、ファイル サーバー、IAM など) は、サポートされていないシナリオです。</span><span class="sxs-lookup"><span data-stu-id="c466f-115">Windows infrastructure roles (DNS, DHCP, DC, NTP, PRINT, File server, IAM etc.) are not supported scenarios.</span></span>

<span data-ttu-id="c466f-116">他の未サポート シナリオやコミュニティからのリクエストについては、Windows コンテナーの UserVoice フォーラム <https://windowsserver.uservoice.com/forums/304624-containers> を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c466f-116">For other nonsupported scenarios and requests from the community, see the UserVoice forum for Windows Containers: <https://windowsserver.uservoice.com/forums/304624-containers>.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c466f-117">その他のリソース</span><span class="sxs-lookup"><span data-stu-id="c466f-117">Additional resources</span></span>

- <span data-ttu-id="c466f-118">**Azure 内の仮想マシンとコンテナー**</span><span class="sxs-lookup"><span data-stu-id="c466f-118">**Virtual machines and containers in Azure**</span></span>

    <https://azure.microsoft.com/overview/containers/>

> [!div class="step-by-step"]
> <span data-ttu-id="c466f-119">[前へ](deploy-existing-net-apps-as-windows-containers.md)
> [次へ](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="c466f-119">[Previous](deploy-existing-net-apps-as-windows-containers.md)
[Next](when-to-deploy-windows-containers-in-your-on-premises-iaas-vm-infrastructure.md)</span></span>
