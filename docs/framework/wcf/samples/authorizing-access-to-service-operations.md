---
title: サービス操作へのアクセスの承認
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: 68e6d53b656cb6327487598f65fa4f04c2495292
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96255456"
---
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="e31cc-102">サービス操作へのアクセスの承認</span><span class="sxs-lookup"><span data-stu-id="e31cc-102">Authorizing Access to Service Operations</span></span>

<span data-ttu-id="e31cc-103">このサンプルでは、を使用して、 [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) サービス操作へのアクセスを承認するために属性を使用できるようにする方法を示し <xref:System.Security.Permissions.PrincipalPermissionAttribute> ます。</span><span class="sxs-lookup"><span data-stu-id="e31cc-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="e31cc-104">このサンプルは、 [はじめに](getting-started-sample.md) のサンプルに基づいています。</span><span class="sxs-lookup"><span data-stu-id="e31cc-104">This sample is based on the [Getting Started](getting-started-sample.md) sample.</span></span> <span data-ttu-id="e31cc-105">サービスとクライアントは、を使用して構成され [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) ます。</span><span class="sxs-lookup"><span data-stu-id="e31cc-105">The service and client are configured using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="e31cc-106">`mode`の属性 [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) がに設定され、 `Message` `clientCredentialType` がに設定されてい `Windows` ます。</span><span class="sxs-lookup"><span data-stu-id="e31cc-106">The `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="e31cc-107"><xref:System.Security.Permissions.PrincipalPermissionAttribute> は各サービス メソッドに適用され、各操作へのアクセスを制限するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e31cc-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="e31cc-108">呼び出し元は、各操作にアクセスできる Windows 管理者である必要があります。</span><span class="sxs-lookup"><span data-stu-id="e31cc-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="e31cc-109">この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="e31cc-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e31cc-110">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e31cc-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e31cc-111">サービス構成ファイルでは、を使用して [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) 属性を設定し `principalPermissionMode` ます。</span><span class="sxs-lookup"><span data-stu-id="e31cc-111">The service configuration file uses the [\<serviceAuthorization>](../../configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="e31cc-112">`principalPermissionMode` を `UseWindowsGroups` に設定すると、Windows グループ名に基づいて <xref:System.Security.Permissions.PrincipalPermissionAttribute> を使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="e31cc-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="e31cc-113">呼び出し元が Windows 管理者グループのメンバーであることを要求するため、<xref:System.Security.Permissions.PrincipalPermissionAttribute> が各操作に適用されます。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="e31cc-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="e31cc-114">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="e31cc-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e31cc-115">クライアントが管理者グループのメンバーであるアカウントで実行される場合、クライアントは各操作と正常に通信できます。それ以外のアカウントで実行される場合、アクセスは拒否されます。</span><span class="sxs-lookup"><span data-stu-id="e31cc-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="e31cc-116">承認エラーを試すには、管理グループのメンバーではないアカウントでクライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="e31cc-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="e31cc-117">クライアントをシャットダウンするには、コンソール ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="e31cc-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="e31cc-118"><xref:System.ServiceModel.Dispatcher.IErrorHandler> を実装すると、サービスに承認エラーを通知することができます。</span><span class="sxs-lookup"><span data-stu-id="e31cc-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="e31cc-119">の実装の詳細については [、「エラー処理およびレポートに対する制御の拡張](extending-control-over-error-handling-and-reporting.md) 」を参照してください `IErrorHandler` 。</span><span class="sxs-lookup"><span data-stu-id="e31cc-119">See [Extending Control Over Error Handling and Reporting](extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e31cc-120">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="e31cc-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e31cc-121">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="e31cc-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e31cc-122">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e31cc-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e31cc-123">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="e31cc-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
