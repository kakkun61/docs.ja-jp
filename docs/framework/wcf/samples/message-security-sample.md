---
title: メッセージ セキュリティ サンプル
ms.date: 03/30/2017
ms.assetid: 82444166-6288-493a-85d4-85f43f134d19
ms.openlocfilehash: 267073d22d3b1b311e0de90454e0f2ec3744cf66
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96294392"
---
# <a name="message-security-sample"></a><span data-ttu-id="78c6d-102">メッセージ セキュリティ サンプル</span><span class="sxs-lookup"><span data-stu-id="78c6d-102">Message Security Sample</span></span>

<span data-ttu-id="78c6d-103">このサンプルでは、`basicHttpBinding` とメッセージ セキュリティを使用するアプリケーションを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-103">This sample demonstrates how to implement an application that uses the `basicHttpBinding` and message security.</span></span> <span data-ttu-id="78c6d-104">このサンプルは、電卓サービスを実装する [はじめに](getting-started-sample.md) に基づいています。</span><span class="sxs-lookup"><span data-stu-id="78c6d-104">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78c6d-105">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78c6d-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="78c6d-106">`basicHttpBinding` のセキュリティ モードの値は、`Message`、`Transport`、`TransportWithMessageCredential`、`TransportCredentialOnly`、および `None` に設定できます。</span><span class="sxs-lookup"><span data-stu-id="78c6d-106">The security mode of `basicHttpBinding` can be set to the following values: `Message`, `Transport`, `TransportWithMessageCredential`, `TransportCredentialOnly` and `None`.</span></span> <span data-ttu-id="78c6d-107">サービスのサンプルの App.config ファイルでは、エンドポイント定義によって `basicHttpBinding` が指定され、`Binding1` という名前のバインディング構成が参照されます。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78c6d-107">In the following sample service App.config file, the endpoint definition specifies the `basicHttpBinding` and references a binding configuration named `Binding1`, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
     <!-- This endpoint is exposed at the base address provided by -->  
     <!-- host: http://localhost:8000/ServiceModelSamples/service.-->  
     <endpoint address=""  
               binding="basicHttpBinding"  
               bindingConfiguration="Binding1"
               contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    </service>  
  </services>  
  ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="78c6d-108">バインディング構成は、の `mode` 属性を [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) に設定 `Message` し、 `clientCredentialType` の属性をに設定し [\<message>](../../configure-apps/file-schema/wcf/message-of-basichttpbinding.md) `Certificate` ます。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78c6d-108">The binding configuration sets the `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-basichttpbinding.md) to `Message` and sets the `clientCredentialType` attribute of the [\<message>](../../configure-apps/file-schema/wcf/message-of-basichttpbinding.md) to `Certificate` as shown in the following sample configuration:</span></span>  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
    <binding name="Binding1" >  
      <security mode = "Message">  
        <message clientCredentialType="Certificate"/>  
      </security>  
    </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="78c6d-109">サービスがクライアントに対してサービス自体を認証するために使用する証明書は、`serviceCredentials` 要素の下にある構成ファイルの behaviors セクションで設定されます。</span><span class="sxs-lookup"><span data-stu-id="78c6d-109">The certificate that the service uses to authenticate itself to the client is set in the behaviors section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="78c6d-110">クライアントがサービスに対してクライアント自体を認証するために使用する証明書に適用される検証モードも、`clientCertificate` 要素の下にある behaviors セクションで設定されます。</span><span class="sxs-lookup"><span data-stu-id="78c6d-110">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the behaviors section under the `clientCertificate` element.</span></span>  
  
```xml  
<!--For debugging purposes, set the includeExceptionDetailInFaults attribute to true.-->  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <!--The serviceCredentials behavior allows one to define a -->  
      <!--service certificate. A service certificate is used by a -->  
      <!--client to authenticate the service and provide message -->  
      <!-- protection. This configuration references the "localhost"-->  
      <!--certificate installed during the setup instructions. -->  
      <serviceCredentials>  
        <serviceCertificate findValue="localhost"  
               storeLocation="LocalMachine"
               storeName="My" x509FindType="FindBySubjectName" />  
        <clientCertificate>  
          <!-- Setting the certificateValidationMode to -->  
          <!-- PeerOrChainTrust means that if the certificate -->  
          <!--is in the user's Trusted People store, then it is -->  
          <!-- trusted without performing a validation of the -->  
          <!-- certificate's issuer chain. This setting is used -->  
          <!-- here for convenience so that the sample can be run -->  
          <!-- without having to have certificates issued by a -->  
          <!-- certification authority (CA). -->  
          <!-- This setting is less secure than the default, -->  
          <!-- ChainTrust. The security implications of this -->  
          <!-- setting should be carefully considered before using -->  
          <!-- PeerOrChainTrust in production code. -->  
          <authentication
                       certificateValidationMode="PeerOrChainTrust" />  
        </clientCertificate>  
      </serviceCredentials>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="78c6d-111">同じバインディングとセキュリティの詳細が、クライアントの構成ファイルで指定されます。</span><span class="sxs-lookup"><span data-stu-id="78c6d-111">The same binding and security details are specified in the client configuration file.</span></span>  
  
 <span data-ttu-id="78c6d-112">次のコードを使用すると、呼び出し元の ID がサービス コンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="78c6d-112">The identity of the caller is displayed in the service console window by using the following code:</span></span>  

```csharp
Console.WriteLine("Called by {0}", ServiceSecurityContext.Current.PrimaryIdentity.Name);  
```

 <span data-ttu-id="78c6d-113">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="78c6d-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="78c6d-114">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-114">Press ENTER in the client window to shut down the client.</span></span>  
  
```console
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-and-build-the-sample"></a><span data-ttu-id="78c6d-115">サンプルをセットアップしてビルドするには</span><span class="sxs-lookup"><span data-stu-id="78c6d-115">To set up and build the sample</span></span>  
  
1. <span data-ttu-id="78c6d-116">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="78c6d-117">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="78c6d-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-on-the-same-machine"></a><span data-ttu-id="78c6d-118">サンプルを同じコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="78c6d-118">To run the sample on the same machine</span></span>  
  
1. <span data-ttu-id="78c6d-119">Setup.bat をサンプルのインストール フォルダーで実行します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-119">Run Setup.bat from the sample install folder.</span></span> <span data-ttu-id="78c6d-120">これにより、サンプルの実行に必要なすべての証明書がインストールされます。</span><span class="sxs-lookup"><span data-stu-id="78c6d-120">This installs all the certificates required for running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="78c6d-121">Setup.bat バッチ ファイルは、Windows SDK コマンド プロンプトから実行します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-121">The Setup.bat batch file is designed to be run from a Windows SDK Command Prompt.</span></span> <span data-ttu-id="78c6d-122">MSSDK 環境変数が SDK のインストール ディレクトリを指している必要があります。</span><span class="sxs-lookup"><span data-stu-id="78c6d-122">It requires that the MSSDK environment variable point to the directory where the SDK is installed.</span></span> <span data-ttu-id="78c6d-123">この環境変数は、Windows SDK コマンド プロンプトで自動設定されます。</span><span class="sxs-lookup"><span data-stu-id="78c6d-123">This environment variable is automatically set within a Windows SDK Command Prompt.</span></span>  
  
2. <span data-ttu-id="78c6d-124">サービス アプリケーションを \service\bin で実行します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-124">Run the service application from \service\bin.</span></span>  
  
3. <span data-ttu-id="78c6d-125">クライアント アプリケーションを \client\bin で実行します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-125">Run the client application from \client\bin.</span></span> <span data-ttu-id="78c6d-126">クライアント アクティビティがクライアントのコンソール アプリケーションに表示されます。</span><span class="sxs-lookup"><span data-stu-id="78c6d-126">Client activity is displayed on the client console application.</span></span>  
  
4. <span data-ttu-id="78c6d-127">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78c6d-127">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
5. <span data-ttu-id="78c6d-128">サンプルの使用が終わったら、Cleanup.bat を実行して証明書を削除してください。</span><span class="sxs-lookup"><span data-stu-id="78c6d-128">Remove the certificates by running Cleanup.bat when you have finished with the sample.</span></span> <span data-ttu-id="78c6d-129">他のセキュリティ サンプルでも同じ証明書を使用します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-129">Other security samples use the same certificates.</span></span>  
  
### <a name="to-run-the-sample-across-machines"></a><span data-ttu-id="78c6d-130">サンプルを複数コンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="78c6d-130">To run the sample across machines</span></span>  
  
1. <span data-ttu-id="78c6d-131">サービス コンピューターにサービス バイナリ用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-131">Create a directory on the service machine for the service binaries.</span></span>  
  
2. <span data-ttu-id="78c6d-132">サービス プログラム ファイルを、サーバーのサービス ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="78c6d-132">Copy the service program files to the service directory on the server.</span></span> <span data-ttu-id="78c6d-133">Setup.bat、Cleanup.bat、ImportClientCert.bat の各ファイルもサーバーにコピーします。</span><span class="sxs-lookup"><span data-stu-id="78c6d-133">Also copy the Setup.bat, Cleanup.bat, and ImportClientCert.bat files to the server.</span></span>  
  
3. <span data-ttu-id="78c6d-134">クライアント コンピューターにクライアント バイナリ用のディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-134">Create a directory on the client machine for the client binaries.</span></span>  
  
4. <span data-ttu-id="78c6d-135">クライアント プログラム ファイルを、クライアント コンピュータに作成したクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="78c6d-135">Copy the client program files to the client directory on the client machine.</span></span> <span data-ttu-id="78c6d-136">Setup.bat、Cleanup.bat、ImportServiceCert.bat の各ファイルもクライアントにコピーします。</span><span class="sxs-lookup"><span data-stu-id="78c6d-136">Also copy the Setup.bat, Cleanup.bat, and ImportServiceCert.bat files to the client.</span></span>  
  
5. <span data-ttu-id="78c6d-137">サーバーで `setup.bat service` を実行します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-137">On the server, run `setup.bat service`.</span></span> <span data-ttu-id="78c6d-138">引数を指定してを実行する `setup.bat` `service` と、コンピューターの完全修飾ドメイン名を使用してサービス証明書が作成され、service .cer という名前のファイルにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="78c6d-138">Running `setup.bat` with the `service` argument creates a service certificate with the fully-qualified domain name of the machine and exports the service certificate to a file named Service.cer.</span></span>  
  
6. <span data-ttu-id="78c6d-139">Service.exe.config を編集して、新しい証明書名 ( `findValue` 要素の属性) を反映し [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) ます。これは、コンピューターの完全修飾ドメイン名と同じです。</span><span class="sxs-lookup"><span data-stu-id="78c6d-139">Edit Service.exe.config to reflect the new certificate name (in the `findValue` attribute in the [\<serviceCertificate>](../../configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md) element) which is the same as the fully-qualified domain name of the machine.</span></span> <span data-ttu-id="78c6d-140">さらに、ベース アドレスの値を `.` から完全修飾コンピュータ名に変更します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-140">Also change the value of the base address to specify a fully-qualified machine name instead of localhost`.`</span></span>  
  
7. <span data-ttu-id="78c6d-141">Service.cer ファイルを、サービス ディレクトリからクライアント コンピューターのクライアント ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="78c6d-141">Copy the Service.cer file from the service directory to the client directory on the client machine.</span></span>  
  
8. <span data-ttu-id="78c6d-142">クライアントで `setup.bat client` を実行します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-142">On the client, run `setup.bat client`.</span></span> <span data-ttu-id="78c6d-143">`setup.bat`に `client` 引数を指定して実行すると、client.com というクライアント証明書が作成され、Client.cer というファイルにエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="78c6d-143">Running `setup.bat` with the `client` argument creates a client certificate named client.com and exports the client certificate to a file named Client.cer.</span></span>  
  
9. <span data-ttu-id="78c6d-144">クライアント コンピューターの Client.exe.config ファイルで、エンドポイントのアドレス値をサービスの新しいアドレスに合わせます。</span><span class="sxs-lookup"><span data-stu-id="78c6d-144">In the Client.exe.config file on the client machine, change the address value of the endpoint to match the new address of your service.</span></span> <span data-ttu-id="78c6d-145">そのためには、localhost をサーバーの完全修飾ドメイン名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="78c6d-145">You do this by replacing localhost with the fully-qualified domain name of the server.</span></span> <span data-ttu-id="78c6d-146">また `findValue` 、の属性を、 [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) サーバーの完全修飾ドメイン名である新しいサービス証明書の名前に変更します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-146">Also change the `findValue` attribute of the [\<defaultCertificate>](../../configure-apps/file-schema/wcf/defaultcertificate-element.md) to the new service certificate name which is the fully-qualified domain name of the server.</span></span>  
  
10. <span data-ttu-id="78c6d-147">Client.cer ファイルを、クライアント ディレクトリからサーバーのサービス ディレクトリにコピーします。</span><span class="sxs-lookup"><span data-stu-id="78c6d-147">Copy the Client.cer file from the client directory to the service directory on the server.</span></span>  
  
11. <span data-ttu-id="78c6d-148">クライアントで ImportServiceCert.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-148">On the client, run ImportServiceCert.bat.</span></span> <span data-ttu-id="78c6d-149">これにより、サービス証明書が Service.cer ファイルから CurrentUser - TrustedPeople ストアにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="78c6d-149">This imports the service certificate from the Service.cer file into the CurrentUser - TrustedPeople store.</span></span>  
  
12. <span data-ttu-id="78c6d-150">サーバーで ImportClientCert.bat を実行します。これにより、クライアント証明書が Client.cer ファイルから LocalMachine - TrustedPeople ストアにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="78c6d-150">On the server, run ImportClientCert.bat, This imports the client certificate from the Client.cer file into the LocalMachine - TrustedPeople store.</span></span>  
  
13. <span data-ttu-id="78c6d-151">サービス コンピューターで、コマンド プロンプトから Service.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-151">On the service machine, run Service.exe from a command prompt.</span></span>  
  
14. <span data-ttu-id="78c6d-152">クライアント コンピューターで、コマンド プロンプト ウィンドウから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-152">On the client machine, launch Client.exe from a command prompt window.</span></span>  
  
    1. <span data-ttu-id="78c6d-153">クライアントとサービスが通信できない場合は、「 [WCF サンプルのトラブルシューティングのヒント](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90))」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="78c6d-153">If the client and service are not able to communicate, see [Troubleshooting Tips for WCF Samples](/previous-versions/dotnet/netframework-3.5/ms751511(v=vs.90)).</span></span>  
  
### <a name="to-clean-up-after-the-sample"></a><span data-ttu-id="78c6d-154">サンプルの実行後にクリーンアップするには</span><span class="sxs-lookup"><span data-stu-id="78c6d-154">To clean up after the sample</span></span>  
  
- <span data-ttu-id="78c6d-155">サンプルの実行が終わったら、サンプル フォルダーにある Cleanup.bat を実行します。</span><span class="sxs-lookup"><span data-stu-id="78c6d-155">Run Cleanup.bat in the samples folder once you have finished running the sample.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="78c6d-156">このサンプルを別のマシンで実行している場合、このスクリプトはサービス証明書をクライアントから削除しません。</span><span class="sxs-lookup"><span data-stu-id="78c6d-156">This script does not remove service certificates on a client when running this sample across machines.</span></span> <span data-ttu-id="78c6d-157">コンピューター間で証明書を使用する Windows Communication Foundation (WCF) サンプルを実行した場合は、CurrentUser-TrustedPeople ストアにインストールされているサービス証明書を必ずオフにしてください。</span><span class="sxs-lookup"><span data-stu-id="78c6d-157">If you have run Windows Communication Foundation (WCF) samples that use certificates across machines, be sure to clear the service certificates that have been installed in the CurrentUser - TrustedPeople store.</span></span> <span data-ttu-id="78c6d-158">削除するには、コマンド `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` を実行します。たとえば、`certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com` となります。</span><span class="sxs-lookup"><span data-stu-id="78c6d-158">To do this, use the following command: `certmgr -del -r CurrentUser -s TrustedPeople -c -n <Fully Qualified Server Machine Name>` For example: `certmgr -del -r CurrentUser -s TrustedPeople -c -n server1.contoso.com`</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="78c6d-159">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="78c6d-159">The samples may already be installed on your machine.</span></span> <span data-ttu-id="78c6d-160">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="78c6d-160">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="78c6d-161">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="78c6d-161">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="78c6d-162">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="78c6d-162">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Basic\MessageSecurity`
