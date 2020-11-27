---
title: '方法: WebSockets 上で通信する WCF サービスを作成する'
ms.date: 03/30/2017
ms.assetid: bafbbd89-eab8-4e9a-b4c3-b7b0178e12d8
ms.openlocfilehash: 64f856bcce1234c8e833cc9be723b4af91c4569c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96286163"
---
# <a name="how-to-create-a-wcf-service-that-communicates-over-websockets"></a><span data-ttu-id="3c8e1-102">方法: WebSockets 上で通信する WCF サービスを作成する</span><span class="sxs-lookup"><span data-stu-id="3c8e1-102">How to: Create a WCF Service that Communicates over WebSockets</span></span>

<span data-ttu-id="3c8e1-103">WCF サービスと WCF クライアントは、<xref:System.ServiceModel.NetHttpBinding> バインディングを使用することにより、WebSocket 経由で通信できます。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-103">WCF services and clients can use the <xref:System.ServiceModel.NetHttpBinding> binding to communicate over WebSockets.</span></span>  <span data-ttu-id="3c8e1-104">WebSocket が使用されるのは、サービス コントラクトによってコールバック コントラクトが定義されていると <xref:System.ServiceModel.NetHttpBinding> によって判断された場合です。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-104">WebSockets will be used when the <xref:System.ServiceModel.NetHttpBinding> determines the service contract defines a callback contract.</span></span> <span data-ttu-id="3c8e1-105">ここでは、<xref:System.ServiceModel.NetHttpBinding> を使用して WebSocket 経由で通信する WCF サービスと WCF クライアントの実装方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-105">This topic describes how to implement a WCF service and client that uses the <xref:System.ServiceModel.NetHttpBinding> to communicate over WebSockets.</span></span>  
  
### <a name="define-the-service"></a><span data-ttu-id="3c8e1-106">サービスの定義</span><span class="sxs-lookup"><span data-stu-id="3c8e1-106">Define the Service</span></span>  
  
1. <span data-ttu-id="3c8e1-107">コールバック コントラクトを定義します。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-107">Define a callback contract</span></span>  
  
    ```csharp  
    [ServiceContract]  
        public interface IStockQuoteCallback  
        {  
            [OperationContract(IsOneWay = true)]  
            Task SendQuote(string code, double value);  
        }  
    ```  
  
     <span data-ttu-id="3c8e1-108">このコントラクトは、サービス側からクライアントにメッセージを返すことができるようにクライアント アプリケーションで実装されます。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-108">This contract will be implemented by the client application to allow the service to send messages back to the client.</span></span>  
  
2. <span data-ttu-id="3c8e1-109">サービス コントラクトを定義し、コールバック コントラクトとして `IStockQuoteCallback` インターフェイスを指定します。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-109">Define the service contract and specify the `IStockQuoteCallback` interface as the callback contract.</span></span>  
  
    ```csharp  
    [ServiceContract(CallbackContract = typeof(IStockQuoteCallback))]  
        public interface IStockQuoteService  
        {  
            [OperationContract(IsOneWay = true)]  
            Task StartSendingQuotes();  
        }  
    ```  
  
3. <span data-ttu-id="3c8e1-110">サービス コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-110">Implement the service contract.</span></span>  
  
    ```csharp
    public class StockQuoteService : IStockQuoteService  
    {  
        public async Task StartSendingQuotes()  
        {  
            var callback = OperationContext.Current.GetCallbackChannel<IStockQuoteCallback>();  
            var random = new Random();  
            double price = 29.00;  

            while (((IChannel)callback).State == CommunicationState.Opened)  
            {  
                await callback.SendQuote("MSFT", price);  
                price += random.NextDouble();  
                await Task.Delay(1000);  
            }  
        }  
    }  
    ```  
  
     <span data-ttu-id="3c8e1-111">サービス操作 `StartSendingQuotes` は、非同期呼び出しとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-111">The service operation `StartSendingQuotes` is implemented as an asynchronous call.</span></span> <span data-ttu-id="3c8e1-112">`OperationContext` を使ってコールバック チャネルを取得します。チャネルが開いている場合は、コールバック チャネルで非同期呼び出しを行います。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-112">We retrieve the callback channel using the `OperationContext` and if the channel is open, we make an async call on the callback channel.</span></span>  
  
4. <span data-ttu-id="3c8e1-113">サービスの構成</span><span class="sxs-lookup"><span data-stu-id="3c8e1-113">Configure the service</span></span>  
  
    ```xml  
    <configuration>  
        <appSettings>  
          <add key="aspnet:UseTaskFriendlySynchronizationContext" value="true" />
        </appSettings>  
        <system.web>  
          <compilation debug="true" targetFramework="4.5" />
        </system.web>  
        <system.serviceModel>  
            <protocolMapping>  
              <add scheme="http" binding="netHttpBinding"/>  
              <add scheme="https" binding="netHttpsBinding"/>  
            </protocolMapping>  
            <behaviors>  
                <serviceBehaviors>  
                    <behavior name="">  
                        <serviceMetadata httpGetEnabled="true" httpsGetEnabled="true" />  
                        <serviceDebug includeExceptionDetailInFaults="false" />  
                    </behavior>  
                </serviceBehaviors>  
            </behaviors>  
            <serviceHostingEnvironment aspNetCompatibilityEnabled="true"  
                multipleSiteBindingsEnabled="true" />  
        </system.serviceModel>  
    </configuration>  
    ```  
  
     <span data-ttu-id="3c8e1-114">サービスの構成ファイルは WCF の既定のエンドポイントに依存しています。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-114">The service’s configuration file relies on WCF’s default endpoints.</span></span> <span data-ttu-id="3c8e1-115">作成された既定のエンドポイントに `<protocolMapping>` を使用するように、`NetHttpBinding` セクションを使用して指定しています。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-115">The `<protocolMapping>` section is used to specify that the `NetHttpBinding` should be used for the default endpoints created.</span></span>  
  
### <a name="define-the-client"></a><span data-ttu-id="3c8e1-116">クライアントの定義</span><span class="sxs-lookup"><span data-stu-id="3c8e1-116">Define the Client</span></span>  
  
1. <span data-ttu-id="3c8e1-117">コールバック コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-117">Implement the callback contract.</span></span>  
  
    ```csharp  
    private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
            {  
                public async Task SendQuoteAsync(string code, double value)  
                {  
                    Console.WriteLine("{0}: {1:f2}", code, value);  
                }  
            }  
    ```  
  
     <span data-ttu-id="3c8e1-118">コールバック コントラクト操作は、非同期メソッドとして実装されます。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-118">The callback contract operation is implemented as an asynchronous method.</span></span>  
  
    1. <span data-ttu-id="3c8e1-119">クライアント コードを実装します。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-119">Implement the client code.</span></span>  
  
        ```csharp  
        class Program  
        {  
            static void Main(string[] args)  
            {  
                var context = new InstanceContext(new CallbackHandler());  
                var client = new StockQuoteServiceReference.StockQuoteServiceClient(context);  
                client.StartSendingQuotes();
                Console.ReadLine();  
            }  
  
            private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
            {  
                public async Task SendQuoteAsync(string code, double value)  
                {  
                    Console.WriteLine("{0}: {1:f2}", code, value);  
                }  
            }  
        }  
        ```  
  
         <span data-ttu-id="3c8e1-120">ここでは、わかりやすいように CallbackHandler を繰り返しています。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-120">The CallbackHandler is repeated here for clarity.</span></span> <span data-ttu-id="3c8e1-121">クライアント アプリケーションは、新しい InstanceContext を作成し、コールバック インターフェイスの実装を指定します。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-121">The client application creates a new InstanceContext and specifies the implementation of the callback interface.</span></span> <span data-ttu-id="3c8e1-122">次に、新しく作成された InstanceContext への参照を送信するプロキシ クラスのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-122">Next it creates an instance of the proxy class sending a reference to the newly created InstanceContext.</span></span> <span data-ttu-id="3c8e1-123">クライアントがサービスを呼び出すと、サービスは、指定されたコールバック コントラクトを使用してクライアントを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-123">When the client calls the service, the service will call the client using the callback contract specified.</span></span>  
  
    2. <span data-ttu-id="3c8e1-124">クライアントの構成</span><span class="sxs-lookup"><span data-stu-id="3c8e1-124">Configure the client</span></span>  
  
        ```xml  
        <?xml version="1.0" encoding="utf-8" ?>  
        <configuration>  
            <startup>
                <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />  
            </startup>  
            <system.serviceModel>  
                <bindings>  
                    <netHttpBinding>  
                        <binding name="NetHttpBinding_IStockQuoteService">  
                            <webSocketSettings transportUsage="Always" />  
                        </binding>  
                    </netHttpBinding>  
                </bindings>  
                <client>  
                    <endpoint address="ws://localhost/NetHttpSampleServer/StockQuoteService.svc"  
                        binding="netHttpBinding" bindingConfiguration="NetHttpBinding_IStockQuoteService"  
                        contract="StockQuoteServiceReference.IStockQuoteService" name="NetHttpBinding_IStockQuoteService" />  
                </client>  
            </system.serviceModel>  
        </configuration>  
        ```  
  
         <span data-ttu-id="3c8e1-125">クライアント構成では特別な操作を実行する必要はありません。`NetHttpBinding` を使用して、クライアント側のエンドポイントを指定するだけです。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-125">There is nothing special you need to do in the client configuration, just specify the client side endpoint using the `NetHttpBinding`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3c8e1-126">例</span><span class="sxs-lookup"><span data-stu-id="3c8e1-126">Example</span></span>  

 <span data-ttu-id="3c8e1-127">このトピックで使用されているコード全体を次に示します。</span><span class="sxs-lookup"><span data-stu-id="3c8e1-127">The following is the complete code used in this topic.</span></span>  
  
```csharp  
// IStockQuoteService.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Server  
{  
    [ServiceContract(CallbackContract = typeof(IStockQuoteCallback))]  
    public interface IStockQuoteService  
    {  
        [OperationContract(IsOneWay = true)]  
        Task StartSendingQuotes();  
    }  
  
    [ServiceContract]  
    public interface IStockQuoteCallback  
    {  
        [OperationContract(IsOneWay = true)]  
        Task SendQuote(string code, double value);  
    }  
}  
```  
  
```csharp
// StockQuoteService.svc.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.Runtime.Serialization;  
using System.ServiceModel;  
using System.ServiceModel.Channels;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Server  
{  
    public class StockQuoteService : IStockQuoteService  
    {  
        public async Task StartSendingQuotes()  
        {  
            var callback = OperationContext.Current.GetCallbackChannel<IStockQuoteCallback>();  
            var random = new Random();  
            double price = 29.00;  
  
            while (((IChannel)callback).State == CommunicationState.Opened)  
            {  
                await callback.SendQuote("MSFT", price);  
                price += random.NextDouble();  
                await Task.Delay(1000);  
            }  
        }  
    }  
}  
```  
  
```xml  
<?xml version="1.0"?>  
  
<!--  
  For more information on how to configure your ASP.NET application, please visit  
  https://go.microsoft.com/fwlink/?LinkId=169433  
  -->  
  
<configuration>  
    <appSettings>  
      <add key="aspnet:UseTaskFriendlySynchronizationContext" value="true" />
    </appSettings>  
    <system.web>  
      <compilation debug="true" targetFramework="4.5" />
    </system.web>  
    <system.serviceModel>  
        <protocolMapping>  
          <add scheme="http" binding="netHttpBinding"/>  
          <add scheme="https" binding="netHttpsBinding"/>  
        </protocolMapping>  
        <behaviors>  
            <serviceBehaviors>  
                <behavior name="">  
                    <serviceMetadata httpGetEnabled="true" httpsGetEnabled="true" />  
                    <serviceDebug includeExceptionDetailInFaults="false" />  
                </behavior>  
            </serviceBehaviors>  
        </behaviors>  
        <serviceHostingEnvironment aspNetCompatibilityEnabled="true"  
            multipleSiteBindingsEnabled="true" />  
    </system.serviceModel>  
</configuration>  
```  
  
```aspx-csharp
<!-- StockQuoteService.svc -->  
<%@ ServiceHost Language="C#" Debug="true" Service="Server.StockQuoteService" CodeBehind="StockQuoteService.svc.cs" %>  
```  
  
```csharp  
// Client.cs  
using System;  
using System.Collections.Generic;  
using System.Linq;  
using System.ServiceModel;  
using System.Text;  
using System.Threading.Tasks;  
  
namespace Client  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            var context = new InstanceContext(new CallbackHandler());  
            var client = new StockQuoteServiceReference.StockQuoteServiceClient(context);  
            client.StartSendingQuotes();
            Console.ReadLine();  
        }  
  
        private class CallbackHandler : StockQuoteServiceReference.IStockQuoteServiceCallback  
        {  
            public async Task SendQuoteAsync(string code, double value)  
            {  
                Console.WriteLine("{0}: {1:f2}", code, value);  
            }  
        }  
    }  
}  
```  
  
```xml  
<!--App.config -->  
<?xml version="1.0" encoding="utf-8" ?>  
<configuration>  
    <startup>
        <supportedRuntime version="v4.0" sku=".NETFramework,Version=v4.5" />  
    </startup>  
    <system.serviceModel>  
        <bindings>  
            <netHttpBinding>  
                <binding name="NetHttpBinding_IStockQuoteService">  
                    <webSocketSettings transportUsage="Always" />  
                </binding>  
            </netHttpBinding>  
        </bindings>  
        <client>  
            <endpoint address="ws://localhost/NetHttpSampleServer/StockQuoteService.svc"  
                binding="netHttpBinding" bindingConfiguration="NetHttpBinding_IStockQuoteService"  
                contract="StockQuoteServiceReference.IStockQuoteService" name="NetHttpBinding_IStockQuoteService" />  
        </client>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="3c8e1-128">関連項目</span><span class="sxs-lookup"><span data-stu-id="3c8e1-128">See also</span></span>

- [<span data-ttu-id="3c8e1-129">同期操作と非同期操作</span><span class="sxs-lookup"><span data-stu-id="3c8e1-129">Synchronous and Asynchronous Operations</span></span>](../synchronous-and-asynchronous-operations.md)
- [<span data-ttu-id="3c8e1-130">NetHttpBinding の使用</span><span class="sxs-lookup"><span data-stu-id="3c8e1-130">Using the NetHttpBinding</span></span>](using-the-nethttpbinding.md)
