---
title: ラップされていないメッセージ
ms.date: 03/30/2017
ms.assetid: 019657bd-1f9b-4315-ad74-eaa4e7551ff6
ms.openlocfilehash: edecbc953cd3ade6135b4c76725e65d317d83132
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294980"
---
# <a name="unwrapped-messages"></a><span data-ttu-id="3d047-102">ラップされていないメッセージ</span><span class="sxs-lookup"><span data-stu-id="3d047-102">Unwrapped Messages</span></span>

<span data-ttu-id="3d047-103">このサンプルでは、ラップされていないメッセージを示します。</span><span class="sxs-lookup"><span data-stu-id="3d047-103">This sample demonstrates unwrapped messages.</span></span> <span data-ttu-id="3d047-104">既定では、メッセージの本文は、サービス操作に渡されるパラメーターがラップされるように書式設定されます。</span><span class="sxs-lookup"><span data-stu-id="3d047-104">By default, the message body is formatted such that the parameters to a service operation are wrapped.</span></span> <span data-ttu-id="3d047-105">ラップされたモードでの `Add` サービスへの `ICalculator` 要求メッセージのサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3d047-105">The following sample shows an `Add` request message to the `ICalculator` service in wrapped mode.</span></span>  
  
```xml  
<s:Envelope
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"  
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        …  
    </s:Header>  
    <s:Body>  
      <Add xmlns="http://Microsoft.ServiceModel.Samples">  
        <n1>100</n1>  
        <n2>15.99</n2>  
      </Add>  
    </s:Body>  
</s:Envelope>  
```  
  
 <span data-ttu-id="3d047-106">メッセージ本文の `<Add>` 要素は、`n1` パラメータおよび `n2` パラメータをラップします。</span><span class="sxs-lookup"><span data-stu-id="3d047-106">The `<Add>` element in the message body wraps the `n1` and `n2` parameters.</span></span> <span data-ttu-id="3d047-107">これに対して、ラップされていないモードでの同様のメッセージのサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="3d047-107">In contrast, the following sample shows the equivalent message in the unwrapped mode.</span></span>  
  
```xml  
<s:Envelope
    xmlns:s="http://www.w3.org/2003/05/soap-envelope"
    xmlns:a="http://schemas.xmlsoap.org/ws/2005/08/addressing">  
    <s:Header>  
        ….  
    </s:Header>  
    <s:Body>  
      <n1 xmlns="http://Microsoft.ServiceModel.Samples">100</n1>  
      <n2 xmlns="http://Microsoft.ServiceModel.Samples">15.99</n2>  
    </s:Body>  
  </s:Envelope>  
```  
  
 <span data-ttu-id="3d047-108">ラップされていないメッセージは、格納要素内の `n1` パラメータおよび `n2` パラメータをラップしません。これらのパラメータは、SOAP 本文要素の直接の子になります。</span><span class="sxs-lookup"><span data-stu-id="3d047-108">The unwrapped message does not wrap the `n1` and `n2` parameters in a containing element, they are direct children of the soap body element.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3d047-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d047-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3d047-110">このサンプルでは、ラップされていないメッセージは、サービス操作のパラメータ型に <xref:System.ServiceModel.MessageContractAttribute> を適用して値型を返すことによって作成されます。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="3d047-110">In this sample, an unwrapped message is created by applying the <xref:System.ServiceModel.MessageContractAttribute> to the service operation parameter type and return value type as shown in the following sample code.</span></span>  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface ICalculator  
{  
    [OperationContract]  
    ResponseMessage Add(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Subtract(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Multiply(RequestMessage request);  
    [OperationContract]  
    ResponseMessage Divide(RequestMessage request);  
}  
  
//setting IsWrapped to false means the n1 and n2  
//members will be direct children of the soap body element  
[MessageContract(IsWrapped = false)]  
public class RequestMessage  
{  
    [MessageBodyMember]  
    private double n1;  
    [MessageBodyMember]  
    private double n2;  
    //…  
}  
  
//setting IsWrapped to false means the result  
//member will be a direct child of the soap body element  
[MessageContract(IsWrapped = false)]  
public class ResponseMessage  
{  
    [MessageBodyMember]  
    private double result;  
    //…  
}  
```  
  
 <span data-ttu-id="3d047-111">送受信されたメッセージを表示できるようにするため、このサンプルではトレースを使用します。</span><span class="sxs-lookup"><span data-stu-id="3d047-111">To allow you to see the messages being sent and received, this sample uses tracing.</span></span> <span data-ttu-id="3d047-112">さらに、<xref:System.ServiceModel.WSHttpBinding> は、記録されるメッセージ数を減らす目的で、セキュリティを無効にして構成されています。</span><span class="sxs-lookup"><span data-stu-id="3d047-112">In addition, the <xref:System.ServiceModel.WSHttpBinding> has been configured without security, to reduce the number of messages it logs.</span></span>  
  
 <span data-ttu-id="3d047-113">生成されたトレースログ (c:\logs\Message.log) は、 [サービストレースビューアーツール (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)を使用して表示できます。</span><span class="sxs-lookup"><span data-stu-id="3d047-113">The resulting trace log (c:\logs\Message.log) can be viewed by using the [Service Trace Viewer Tool (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md).</span></span> <span data-ttu-id="3d047-114">メッセージの内容を表示するには、サービストレースビューアーツールの左側と右側の両方のウィンドウで [ **メッセージ** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="3d047-114">To view message contents, select **Messages** in both the left and the right panes of the Service Trace Viewer tool.</span></span> <span data-ttu-id="3d047-115">このサンプルのトレース ログは、C:\LOGS フォルダに生成されるように構成されています。</span><span class="sxs-lookup"><span data-stu-id="3d047-115">Trace logs in this sample are configured to be generated into the C:\LOGS folder.</span></span> <span data-ttu-id="3d047-116">サンプルの実行前にこのフォルダを作成し、ユーザー Network Service にそのディレクトリへの書き込み権限を与えます。</span><span class="sxs-lookup"><span data-stu-id="3d047-116">Create this folder before running the sample and give the user Network Service write permissions for this directory.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3d047-117">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="3d047-117">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3d047-118">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="3d047-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3d047-119">メッセージのログ記録用に C:\LOGS ディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="3d047-119">Create a C:\LOGS directory for logging messages.</span></span> <span data-ttu-id="3d047-120">ユーザー Network Service にそのディレクトリの書き込み権限を与えます。</span><span class="sxs-lookup"><span data-stu-id="3d047-120">Give the user Network Service write permissions for this directory.</span></span>  
  
3. <span data-ttu-id="3d047-121">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3d047-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="3d047-122">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="3d047-122">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="3d047-123">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="3d047-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="3d047-124">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="3d047-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="3d047-125">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="3d047-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="3d047-126">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="3d047-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Message\Unwrapped`  
