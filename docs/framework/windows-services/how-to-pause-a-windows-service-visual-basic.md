---
title: '方法: Windows サービスを一時中断する (Visual Basic)'
description: ServiceController コンポーネントを使用して、ローカルコンピューター上の Windows サービス (IIS 管理サービスなど) を Visual Basic で一時停止する方法を確認します。
ms.date: 03/30/2017
dev_langs:
- vb
f1_keywords:
- ServiceController.Pause
helpviewer_keywords:
- Windows Service applications, pausing
- pausing Windows Service applications
ms.assetid: eddb9409-942b-46b6-a2ce-fbd4c65f2790
ms.openlocfilehash: a8c3074fdbf8d7b948b00def4e6a664310fc6ec2
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96270590"
---
# <a name="how-to-pause-a-windows-service-visual-basic"></a><span data-ttu-id="12ab5-103">方法: Windows サービスを一時中断する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12ab5-103">How to: Pause a Windows Service (Visual Basic)</span></span>

<span data-ttu-id="12ab5-104">この例では、<xref:System.ServiceProcess.ServiceController> コンポーネントを使って、ローカル コンピューター上の IIS 管理サービスを一時停止します。</span><span class="sxs-lookup"><span data-stu-id="12ab5-104">This example uses the <xref:System.ServiceProcess.ServiceController> component to pause the IIS Admin service on the local computer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12ab5-105">例</span><span class="sxs-lookup"><span data-stu-id="12ab5-105">Example</span></span>  

 [!code-vb[VbRadconService#11](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#11)]  
[!code-vb[VbRadconService#12](../../../samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbRadconService/VB/MyNewService.vb#12)]  
  
 <span data-ttu-id="12ab5-106">このコード例は、IntelliSense コード スニペットとしても利用できます。</span><span class="sxs-lookup"><span data-stu-id="12ab5-106">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="12ab5-107">コード スニペット ピッカーでは、これは **[Windows オペレーティング システム] > [Windows サービス]** に配置されます。</span><span class="sxs-lookup"><span data-stu-id="12ab5-107">In the code snippet picker, it is located in **Windows Operating System > Windows Services**.</span></span> <span data-ttu-id="12ab5-108">詳細については、「[Code Snippets](/visualstudio/ide/code-snippets)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12ab5-108">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="12ab5-109">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="12ab5-109">Compiling the Code</span></span>  

 <span data-ttu-id="12ab5-110">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="12ab5-110">This example requires:</span></span>  
  
- <span data-ttu-id="12ab5-111">System.serviceprocess.dll へのプロジェクト参照が必要です。</span><span class="sxs-lookup"><span data-stu-id="12ab5-111">A project reference to System.serviceprocess.dll.</span></span>  
  
- <span data-ttu-id="12ab5-112"><xref:System.ServiceProcess> 名前空間のメンバーへのアクセス許可。</span><span class="sxs-lookup"><span data-stu-id="12ab5-112">Access to the members of the <xref:System.ServiceProcess> namespace.</span></span> <span data-ttu-id="12ab5-113">コード内でメンバー名を完全修飾していない場合は、`Imports` ステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="12ab5-113">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="12ab5-114">詳細については、「[Imports ステートメント (.NET 名前空間および型)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="12ab5-114">For more information, see [Imports Statement (.NET Namespace and Type)](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="12ab5-115">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="12ab5-115">Robust Programming</span></span>  

 <span data-ttu-id="12ab5-116"><xref:System.ServiceProcess.ServiceController> クラスの <xref:System.ServiceProcess.ServiceController.MachineName%2A> プロパティは、既定ではローカル コンピューターです。</span><span class="sxs-lookup"><span data-stu-id="12ab5-116">The <xref:System.ServiceProcess.ServiceController.MachineName%2A> property of the <xref:System.ServiceProcess.ServiceController> class is the local computer by default.</span></span> <span data-ttu-id="12ab5-117">別のコンピューター上の Windows サービスを参照するには、<xref:System.ServiceProcess.ServiceController.MachineName%2A> プロパティをそのコンピューターの名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="12ab5-117">To reference Windows services on another computer, change the <xref:System.ServiceProcess.ServiceController.MachineName%2A> property to the name of that computer.</span></span>  
  
 <span data-ttu-id="12ab5-118">次の条件を満たす場合は、例外が発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="12ab5-118">The following conditions may cause an exception:</span></span>  
  
- <span data-ttu-id="12ab5-119">サービスを一時停止できません。</span><span class="sxs-lookup"><span data-stu-id="12ab5-119">The service cannot be paused.</span></span> <span data-ttu-id="12ab5-120">(<xref:System.InvalidOperationException>)</span><span class="sxs-lookup"><span data-stu-id="12ab5-120">(<xref:System.InvalidOperationException>)</span></span>  
  
- <span data-ttu-id="12ab5-121">システム API にアクセス中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="12ab5-121">An error occurred when accessing a system API.</span></span> <span data-ttu-id="12ab5-122">(<xref:System.ComponentModel.Win32Exception>)</span><span class="sxs-lookup"><span data-stu-id="12ab5-122">(<xref:System.ComponentModel.Win32Exception>)</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="12ab5-123">.NET Framework セキュリティ</span><span class="sxs-lookup"><span data-stu-id="12ab5-123">.NET Framework Security</span></span>  

 <span data-ttu-id="12ab5-124">コンピューター上のサービスの制御は、<xref:System.ServiceProcess.ServiceControllerPermissionAccess> を使って <xref:System.ServiceProcess.ServiceControllerPermission> のアクセス許可を設定することにより制限できます。</span><span class="sxs-lookup"><span data-stu-id="12ab5-124">Control of services on the computer may be restricted by using the <xref:System.ServiceProcess.ServiceControllerPermissionAccess> to set permissions in the <xref:System.ServiceProcess.ServiceControllerPermission>.</span></span>  
  
 <span data-ttu-id="12ab5-125">サービス情報へのアクセスは、<xref:System.Security.Permissions.PermissionState> を使って <xref:System.Security.Permissions.SecurityPermission> のアクセス許可を設定することにより制限できます。</span><span class="sxs-lookup"><span data-stu-id="12ab5-125">Access to service information may be restricted by using the <xref:System.Security.Permissions.PermissionState> to set permissions in the <xref:System.Security.Permissions.SecurityPermission>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12ab5-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="12ab5-126">See also</span></span>

- <xref:System.ServiceProcess.ServiceController>
- <xref:System.ServiceProcess.ServiceControllerStatus>
- <xref:System.ServiceProcess.ServiceController.WaitForStatus%2A>
- [<span data-ttu-id="12ab5-127">方法: Windows サービスを続行する (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="12ab5-127">How to: Continue a Windows Service (Visual Basic)</span></span>](how-to-continue-a-windows-service-visual-basic.md)
