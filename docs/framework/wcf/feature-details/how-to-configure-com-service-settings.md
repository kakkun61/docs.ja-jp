---
title: '方法: COM+ サービス設定を構成する'
ms.date: 03/30/2017
helpviewer_keywords:
- COM+ [WCF], configuring service settings
ms.assetid: f42a55a8-3af8-4394-9fdd-bf12a93780eb
ms.openlocfilehash: b75f5c2a64b7184959e929439893b33193aa7bae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257471"
---
# <a name="how-to-configure-com-service-settings"></a><span data-ttu-id="4f5a3-102">方法: COM+ サービス設定を構成する</span><span class="sxs-lookup"><span data-stu-id="4f5a3-102">How to: Configure COM+ Service Settings</span></span>

<span data-ttu-id="4f5a3-103">COM+ サービス構成ツールを使用してアプリケーション インターフェイスを追加または削除すると、アプリケーション構成ファイル内の Web サービス構成が更新されます。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-103">When an application interface is added or removed by using the COM+ Service Configuration tool, the Web service configuration is updated within the application's configuration file.</span></span> <span data-ttu-id="4f5a3-104">COM + でホストされるモードでは、Application.config ファイルはアプリケーションのルートディレクトリに配置されます (%Programfiles%\complus applications\ Applications \\ {appid} が既定値です)。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-104">In the COM+ hosted mode, the Application.config file is placed in the Application Root Directory (%PROGRAMFILES%\ComPlus Applications\\{appid} is the default).</span></span> <span data-ttu-id="4f5a3-105">いずれの Web ホスト モードでも、Web.config ファイルは指定した vroot ディレクトリに配置されます。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-105">In either of the Web-hosted modes, the Web.config file is placed in the specified vroot directory.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f5a3-106">クライアントとサーバー間のメッセージの改ざんを防止するには、メッセージの署名を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-106">Message signing should be used to protect against tampering of messages between a client and a server.</span></span> <span data-ttu-id="4f5a3-107">また、クライアントとサーバー間のメッセージから情報が漏えいするのを防止するには、メッセージまたはトランスポート層の暗号化を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-107">Also, message or transport layer encryption should be used to protect against information disclosure from messages between a client and a server.</span></span> <span data-ttu-id="4f5a3-108">Windows Communication Foundation (WCF) サービスと同様に、同時呼び出し、接続、インスタンス、および保留中の操作の数を制限するには、調整を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-108">As with Windows Communication Foundation (WCF) services, you should use throttling to limit the number of concurrent calls, connections, instances, and pending operations.</span></span> <span data-ttu-id="4f5a3-109">これによりリソースの過剰消費を防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-109">This helps prevent over-consumption of resources.</span></span> <span data-ttu-id="4f5a3-110">調整の動作は、サービス構成ファイルの設定で指定します。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-110">Throttling behavior is specified through service configuration file settings.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f5a3-111">例</span><span class="sxs-lookup"><span data-stu-id="4f5a3-111">Example</span></span>  

 <span data-ttu-id="4f5a3-112">次のインターフェイスを実装するコンポーネントについて考えます。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-112">Consider a component that implements the following interface:</span></span>  
  
```csharp
[Guid("C551FBA9-E3AA-4272-8C2A-84BD8D290AC7")]  
public interface IFinances  
{  
    string Debit(string accountNo, double amount);  
    string Credit(string accountNo, double amount);  
}  
```  
  
 <span data-ttu-id="4f5a3-113">コンポーネントを Web サービスとして公開する場合、クライアントが準拠する必要のある対応の公開サービス コントラクトは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-113">If the component is exposed as a Web service, the corresponding service contract that is exposed, and that clients would need to conform to, is as follows:</span></span>  
  
```csharp
[ServiceContract(Session = true,  
Namespace = "http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7",  
Name = "IFinances")]  
public interface IFinancesContract : IDisposable  
{  
    [OperationContract]  
    string Debit(string accountNo, double amount);  
    [OperationContract]  
    string Credit(string accountNo, double amount);  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="4f5a3-114">IID はコントラクトの初期名前空間の一部です。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-114">IID forms part of the initial namespace for the contract.</span></span>  
  
 <span data-ttu-id="4f5a3-115">このサービスを使用するクライアント アプリケーションはこのコントラクトに準拠し、さらにアプリケーションの構成に指定したバインディングと互換性のあるバインディングを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-115">Client applications that use this service would need to conform to this contract, along with using a binding that is compatible with the one specified in the application configuration.</span></span>  
  
 <span data-ttu-id="4f5a3-116">次のコード例は、既定の構成ファイルの例を示しています。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-116">The following code example shows a default configuration file.</span></span> <span data-ttu-id="4f5a3-117">これは、Windows Communication Foundation (WCF) Web サービスであり、これは標準のサービスモデル構成スキーマに準拠しており、他の WCF サービス構成ファイルと同じ方法で編集できます。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-117">Being a Windows Communication Foundation (WCF) Web service, this conforms to the standard service model configuration schema and can be edited in the same way as other WCF services configuration files.</span></span>  
  
 <span data-ttu-id="4f5a3-118">通常、次のような変更を行います。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-118">Typical modifications would include:</span></span>  
  
- <span data-ttu-id="4f5a3-119">エンドポイント アドレスを既定の ApplicationName/ComponentName/InterfaceName という形式から、より利用しやすい形式に変更する。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-119">Changing the endpoint address from the default ApplicationName/ComponentName/InterfaceName form to a more usable form.</span></span>  
  
- <span data-ttu-id="4f5a3-120">サービスの名前空間を既定のフォームから `http://tempuri.org/InterfaceID` より適切な形式に変更します。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-120">Modifying the namespace of the service from the default `http://tempuri.org/InterfaceID` form to a more relevant form.</span></span>  
  
- <span data-ttu-id="4f5a3-121">異なるトランスポート バインディングを使用するようにエンドポイントを変更する。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-121">Changing the endpoint to use a different transport binding.</span></span>  
  
     <span data-ttu-id="4f5a3-122">COM+ ホスト モードの場合、既定では名前付きパイプ トランスポートが使用されますが、その代わりに TCP などのコンピューターに関係のないトランスポートも使用できます。</span><span class="sxs-lookup"><span data-stu-id="4f5a3-122">In the COM+-hosted case, the named pipes transport is used by default, but an off-machine transport like TCP can be used instead.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
    <system.serviceModel>  
        <bindings>  
            <netNamedPipeBinding>  
                <binding name="comNonTransactionalBinding" />  
                <binding name="comTransactionalBinding" transactionFlow="true" />  
            </netNamedPipeBinding>  
        </bindings>  
        <comContracts>  
            <comContract contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}"  
                name="IFinances" namespace="http://tempuri.org/C551FBA9-E3AA-4272-8C2A-84BD8D290AC7"  
                requiresSession="true">  
                <exposedMethods>  
                    <add exposedMethod="Debit" />  
                    <add exposedMethod="Credit" />  
                </exposedMethods>  
            </comContract>  
        </comContracts>  
        <services>  
            <service name="{DCDB24CC-0B19-4534-95CD-FBBFF4D67DD9},{C942B840-AD54-4A44-B5F7-928130980AB9}">  
                <endpoint address="IFinances" binding="netNamedPipeBinding" bindingConfiguration="comNonTransactionalBinding"  
                    contract="{C551FBA9-E3AA-4272-8C2A-84BD8D290AC7}" />  
                <host>  
                    <baseAddresses>  
                        <add baseAddress="net.pipe://localhost/ServiceModelDocSampleApp/ServiceModelDocSample.esFinance" />  
                    </baseAddresses>  
                </host>  
            </service>  
        </services>  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4f5a3-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="4f5a3-123">See also</span></span>

- [<span data-ttu-id="4f5a3-124">COM + アプリケーションとの統合</span><span class="sxs-lookup"><span data-stu-id="4f5a3-124">Integrating with COM+ Applications</span></span>](integrating-with-com-plus-applications.md)
