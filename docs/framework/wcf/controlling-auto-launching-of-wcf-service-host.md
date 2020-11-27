---
title: WCF サービス ホストの自動起動の制御
ms.date: 03/30/2017
f1_keywords:
- WcfOptions
ms.assetid: 6abe5d34-519b-4cef-8f02-3c0a7f125585
ms.openlocfilehash: 2033e693003d0b50bcdada428e4a5f451b3ad67e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255079"
---
# <a name="controlling-auto-launching-of-wcf-service-host"></a><span data-ttu-id="9ea4c-102">WCF サービス ホストの自動起動の制御</span><span class="sxs-lookup"><span data-stu-id="9ea4c-102">Controlling Auto-launching of WCF Service Host</span></span>

<span data-ttu-id="9ea4c-103">複数のプロジェクトを含む同じ Visual Studio ソリューションで別のプロジェクトをデバッグするときに、WCF サービスライブラリプロジェクトの Windows Communication Foundation (WCF) サービスホスト (WcfSvcHost.exe) の自動起動機能を制御できます。</span><span class="sxs-lookup"><span data-stu-id="9ea4c-103">You can control the auto-launching capability of Windows Communication Foundation (WCF) Service Host (WcfSvcHost.exe) for a WCF Service Library project, when you debug another project in the same Visual Studio solution containing multiple projects.</span></span>  
  
 <span data-ttu-id="9ea4c-104">これを行うには、 **ソリューションエクスプローラー** で Wcf サービスプロジェクトを右クリックし、[ **プロパティ**] をクリックして、[ **wcf オプション** ] タブをクリックします。既定では、[ **同じソリューションで別のプロジェクトをデバッグするときに WCF サービスホストを開始する** ] チェックボックスがオンになっています。</span><span class="sxs-lookup"><span data-stu-id="9ea4c-104">To do so, right-click the WCF Service Project in **Solution Explorer**, choose **Properties**, and click **WCF Options** tab. The **Start WCF Service Host when debugging another project in the same solution** check box is enabled by default.</span></span> <span data-ttu-id="9ea4c-105">このチェックボックスをオフにすると、同じソリューションで別のプロジェクトがデバッグされるときに、この特定のプロジェクトの WCF サービスホストが起動されないようにすることができます。</span><span class="sxs-lookup"><span data-stu-id="9ea4c-105">You can clear the box so that WCF Service Host for this specific project is not launched when another project is debugged in the same solution.</span></span>  
  
 <span data-ttu-id="9ea4c-106">この動作は、F5 キーによるデバッグや、このプロジェクトへのサービス参照の追加の機能には影響を与えません。</span><span class="sxs-lookup"><span data-stu-id="9ea4c-106">This behavior does not affect the F5 debugging, or Add Service Reference functionalities for this project.</span></span>  
  
 <span data-ttu-id="9ea4c-107">このオプションは、次のプロジェクトで使用できます。</span><span class="sxs-lookup"><span data-stu-id="9ea4c-107">This option is available to the following projects:</span></span>  
  
- <span data-ttu-id="9ea4c-108">WCF サービスライブラリプロジェクト。</span><span class="sxs-lookup"><span data-stu-id="9ea4c-108">WCF Service Library Project.</span></span>  
  
- <span data-ttu-id="9ea4c-109">シーケンシャル ワークフロー サービス ライブラリ プロジェクト</span><span class="sxs-lookup"><span data-stu-id="9ea4c-109">Sequential Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="9ea4c-110">ステート マシン ワークフロー サービス ライブラリ プロジェクト</span><span class="sxs-lookup"><span data-stu-id="9ea4c-110">State Machine Workflow Service Library Project.</span></span>  
  
- <span data-ttu-id="9ea4c-111">配信サービス ライブラリ プロジェクト</span><span class="sxs-lookup"><span data-stu-id="9ea4c-111">Syndication Service Library Project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ea4c-112">関連項目</span><span class="sxs-lookup"><span data-stu-id="9ea4c-112">See also</span></span>

- [<span data-ttu-id="9ea4c-113">WCF サービス ホスト (WcfSvcHost.exe)</span><span class="sxs-lookup"><span data-stu-id="9ea4c-113">WCF Service Host (WcfSvcHost.exe)</span></span>](wcf-service-host-wcfsvchost-exe.md)
