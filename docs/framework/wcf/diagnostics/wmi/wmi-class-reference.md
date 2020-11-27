---
title: WMI クラスの参照
ms.date: 03/30/2017
ms.assetid: b95a51f5-8251-4619-ae05-7de88cb90f9a
ms.openlocfilehash: 9830fbf50e8df625e3d3077a66c66e0370204acb
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96262256"
---
# <a name="wmi-class-reference"></a><span data-ttu-id="9df2b-102">WMI クラスの参照</span><span class="sxs-lookup"><span data-stu-id="9df2b-102">WMI Class Reference</span></span>

<span data-ttu-id="9df2b-103">ここでは、Windows Communication Foundation (WCF) WMI プロバイダーによって公開されるすべての WMI クラスの一覧を示します。</span><span class="sxs-lookup"><span data-stu-id="9df2b-103">This section lists all the WMI classes exposed by the Windows Communication Foundation (WCF) WMI provider.</span></span>  
  
## <a name="accessing-wmi-instances"></a><span data-ttu-id="9df2b-104">WMI インスタンスへのアクセス</span><span class="sxs-lookup"><span data-stu-id="9df2b-104">Accessing WMI Instances</span></span>  

 <span data-ttu-id="9df2b-105">WMI オブジェクト リファレンスに記載されているクラスはすべて、インスタンスを直接生成することはできません。ただし Service、AppDomain、Contract、ServiceAppDomain、ServiceToEndpointAssociation、Endpoint の各クラスを除きます。</span><span class="sxs-lookup"><span data-stu-id="9df2b-105">All the classes listed in the WMI Object Reference cannot be directly instantiated, except for Service, AppDomain, Contract, ServiceAppDomain, ServiceToEndpointAssociation and Endpoint.</span></span> <span data-ttu-id="9df2b-106">他のインスタンスには、これらのトップ レベル クラスのプロパティからアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9df2b-106">To access other instances, you can access the properties of the previously mentioned top level classes.</span></span> <span data-ttu-id="9df2b-107">たとえば、TransportBindingElement インスタンスにアクセスするには、エンドポイントインスタンスから > バインド > BindingElements を使用します。</span><span class="sxs-lookup"><span data-stu-id="9df2b-107">For example, you can access the TransportBindingElement instance from the Endpoint instance -> Binding -> BindingElements.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9df2b-108">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="9df2b-108">In This Section</span></span>  

 [<span data-ttu-id="9df2b-109">ActivityTransfer</span><span class="sxs-lookup"><span data-stu-id="9df2b-109">ActivityTransfer</span></span>](activitytransfer.md)  
  
 [<span data-ttu-id="9df2b-110">AppDomainInfo</span><span class="sxs-lookup"><span data-stu-id="9df2b-110">AppDomainInfo</span></span>](appdomaininfo.md)  
  
 [<span data-ttu-id="9df2b-111">AspNetCompatibilityRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="9df2b-111">AspNetCompatibilityRequirementsAttribute</span></span>](aspnetcompatibilityrequirementsattribute.md)  
  
 [<span data-ttu-id="9df2b-112">AsymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-112">AsymmetricSecurityBindingElement</span></span>](asymmetricsecuritybindingelement.md)  
  
 <span data-ttu-id="9df2b-113">"Behavior クラス"</span><span class="sxs-lookup"><span data-stu-id="9df2b-113">"Behavior class"</span></span>  
  
 [<span data-ttu-id="9df2b-114">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-114">BinaryMessageEncodingBindingElement</span></span>](binarymessageencodingbindingelement.md)  
  
 [<span data-ttu-id="9df2b-115">Binding</span><span class="sxs-lookup"><span data-stu-id="9df2b-115">Binding</span></span>](binding.md)  
  
 [<span data-ttu-id="9df2b-116">BindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-116">BindingElement</span></span>](bindingelement.md)  
  
 [<span data-ttu-id="9df2b-117">CallbackBehavior</span><span class="sxs-lookup"><span data-stu-id="9df2b-117">CallbackBehavior</span></span>](callbackbehavior.md)  
  
 [<span data-ttu-id="9df2b-118">チャネル クラス</span><span class="sxs-lookup"><span data-stu-id="9df2b-118">Channel class</span></span>](channel-class.md)  
  
 [<span data-ttu-id="9df2b-119">ChannelPoolSettings</span><span class="sxs-lookup"><span data-stu-id="9df2b-119">ChannelPoolSettings</span></span>](channelpoolsettings.md)  
  
 [<span data-ttu-id="9df2b-120">ClientCredentials</span><span class="sxs-lookup"><span data-stu-id="9df2b-120">ClientCredentials</span></span>](clientcredentials.md)  
  
 [<span data-ttu-id="9df2b-121">ClientViaBehavior</span><span class="sxs-lookup"><span data-stu-id="9df2b-121">ClientViaBehavior</span></span>](clientviabehavior.md)  
  
 [<span data-ttu-id="9df2b-122">CompositeDuplexBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-122">CompositeDuplexBindingElement</span></span>](compositeduplexbindingelement.md)  
  
 [<span data-ttu-id="9df2b-123">ConnectionOrientedTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-123">ConnectionOrientedTransportBindingElement</span></span>](connectionorientedtransportbindingelement.md)  
  
 [<span data-ttu-id="9df2b-124">決め</span><span class="sxs-lookup"><span data-stu-id="9df2b-124">Contract</span></span>](contract.md)  
  
 [<span data-ttu-id="9df2b-125">CustomBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-125">CustomBindingElement</span></span>](custombindingelement.md)  
  
 [<span data-ttu-id="9df2b-126">DeliveryRequirementsAttribute</span><span class="sxs-lookup"><span data-stu-id="9df2b-126">DeliveryRequirementsAttribute</span></span>](deliveryrequirementsattribute.md)  
  
 [<span data-ttu-id="9df2b-127">エンドポイント</span><span class="sxs-lookup"><span data-stu-id="9df2b-127">Endpoint</span></span>](endpoint.md)  
  
 [<span data-ttu-id="9df2b-128">HttpsTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-128">HttpsTransportBindingElement</span></span>](httpstransportbindingelement.md)  
  
 [<span data-ttu-id="9df2b-129">HttpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-129">HttpTransportBindingElement</span></span>](httptransportbindingelement.md)  
  
 [<span data-ttu-id="9df2b-130">LocalServiceSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="9df2b-130">LocalServiceSecuritySettings</span></span>](localservicesecuritysettings.md)  
  
 [<span data-ttu-id="9df2b-131">MatchAllEndpointBehavior</span><span class="sxs-lookup"><span data-stu-id="9df2b-131">MatchAllEndpointBehavior</span></span>](matchallendpointbehavior.md)  
  
 [<span data-ttu-id="9df2b-132">MessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-132">MessageEncodingBindingElement</span></span>](messageencodingbindingelement.md)  
  
 [<span data-ttu-id="9df2b-133">MsmqBindingElementBase</span><span class="sxs-lookup"><span data-stu-id="9df2b-133">MsmqBindingElementBase</span></span>](msmqbindingelementbase.md)  
  
 [<span data-ttu-id="9df2b-134">MsmqIntegrationBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-134">MsmqIntegrationBindingElement</span></span>](msmqintegrationbindingelement.md)  
  
 [<span data-ttu-id="9df2b-135">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-135">MsmqTransportBindingElement</span></span>](msmqtransportbindingelement.md)  
  
 [<span data-ttu-id="9df2b-136">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-136">MtomMessageEncodingBindingElement</span></span>](mtommessageencodingbindingelement.md)  
  
 [<span data-ttu-id="9df2b-137">MustUnderstandBehavior</span><span class="sxs-lookup"><span data-stu-id="9df2b-137">MustUnderstandBehavior</span></span>](mustunderstandbehavior.md)  
  
 [<span data-ttu-id="9df2b-138">NamedPipeConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="9df2b-138">NamedPipeConnectionPoolSettings</span></span>](namedpipeconnectionpoolsettings.md)  
  
 [<span data-ttu-id="9df2b-139">NamedPipeTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-139">NamedPipeTransportBindingElement</span></span>](namedpipetransportbindingelement.md)  
  
 [<span data-ttu-id="9df2b-140">OneWayBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-140">OneWayBindingElement</span></span>](onewaybindingelement.md)  
  
 <span data-ttu-id="9df2b-141">"Operation クラス"</span><span class="sxs-lookup"><span data-stu-id="9df2b-141">"Operation class"</span></span>  
  
 [<span data-ttu-id="9df2b-142">OperationBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="9df2b-142">OperationBehaviorAttribute</span></span>](operationbehaviorattribute.md)  
  
 [<span data-ttu-id="9df2b-143">PeerCustomResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-143">PeerCustomResolverBindingElement</span></span>](peercustomresolverbindingelement.md)  
  
 [<span data-ttu-id="9df2b-144">PeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-144">PeerResolverBindingElement</span></span>](peerresolverbindingelement.md)  
  
 [<span data-ttu-id="9df2b-145">PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="9df2b-145">PeerSecuritySettings</span></span>](peersecuritysettings.md)  
  
 [<span data-ttu-id="9df2b-146">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-146">PeerTransportBindingElement</span></span>](peertransportbindingelement.md)  
  
 [<span data-ttu-id="9df2b-147">PeerTransportSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="9df2b-147">PeerTransportSecuritySettings</span></span>](peertransportsecuritysettings.md)  
  
 [<span data-ttu-id="9df2b-148">PnrpPeerResolverBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-148">PnrpPeerResolverBindingElement</span></span>](pnrppeerresolverbindingelement.md)  
  
 [<span data-ttu-id="9df2b-149">PrivacyNoticeBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-149">PrivacyNoticeBindingElement</span></span>](privacynoticebindingelement.md)  
  
 [<span data-ttu-id="9df2b-150">ReliableSessionBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-150">ReliableSessionBindingElement</span></span>](reliablesessionbindingelement.md)  
  
 [<span data-ttu-id="9df2b-151">SecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-151">SecurityBindingElement</span></span>](securitybindingelement.md)  
  
 [<span data-ttu-id="9df2b-152">サービス</span><span class="sxs-lookup"><span data-stu-id="9df2b-152">Service</span></span>](service.md)  
  
 [<span data-ttu-id="9df2b-153">ServiceAppDomain</span><span class="sxs-lookup"><span data-stu-id="9df2b-153">ServiceAppDomain</span></span>](serviceappdomain.md)  
  
 [<span data-ttu-id="9df2b-154">ServiceAuthorizationBehavior</span><span class="sxs-lookup"><span data-stu-id="9df2b-154">ServiceAuthorizationBehavior</span></span>](serviceauthorizationbehavior.md)  
  
 [<span data-ttu-id="9df2b-155">ServiceBehaviorAttribute</span><span class="sxs-lookup"><span data-stu-id="9df2b-155">ServiceBehaviorAttribute</span></span>](servicebehaviorattribute.md)  
  
 [<span data-ttu-id="9df2b-156">ServiceCredentials</span><span class="sxs-lookup"><span data-stu-id="9df2b-156">ServiceCredentials</span></span>](servicecredentials.md)  
  
 [<span data-ttu-id="9df2b-157">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="9df2b-157">ServiceDebugBehavior</span></span>](servicedebugbehavior.md)  
  
 [<span data-ttu-id="9df2b-158">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="9df2b-158">ServiceMetadataBehavior</span></span>](servicemetadatabehavior.md)  
  
 [<span data-ttu-id="9df2b-159">ServiceSecurityAuditBehavior</span><span class="sxs-lookup"><span data-stu-id="9df2b-159">ServiceSecurityAuditBehavior</span></span>](servicesecurityauditbehavior.md)  
  
 [<span data-ttu-id="9df2b-160">ServiceThrottlingBehavior</span><span class="sxs-lookup"><span data-stu-id="9df2b-160">ServiceThrottlingBehavior</span></span>](servicethrottlingbehavior.md)  
  
 [<span data-ttu-id="9df2b-161">ServiceTimeoutsBehavior</span><span class="sxs-lookup"><span data-stu-id="9df2b-161">ServiceTimeoutsBehavior</span></span>](servicetimeoutsbehavior.md)  
  
 [<span data-ttu-id="9df2b-162">ServiceToEndpointAssociation</span><span class="sxs-lookup"><span data-stu-id="9df2b-162">ServiceToEndpointAssociation</span></span>](servicetoendpointassociation.md)  
  
 [<span data-ttu-id="9df2b-163">SslStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-163">SslStreamSecurityBindingElement</span></span>](sslstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="9df2b-164">SymmetricSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-164">SymmetricSecurityBindingElement</span></span>](symmetricsecuritybindingelement.md)  
  
 [<span data-ttu-id="9df2b-165">SynchronousReceiveBehavior</span><span class="sxs-lookup"><span data-stu-id="9df2b-165">SynchronousReceiveBehavior</span></span>](synchronousreceivebehavior.md)  
  
 [<span data-ttu-id="9df2b-166">TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="9df2b-166">TcpConnectionPoolSettings</span></span>](tcpconnectionpoolsettings.md)  
  
 [<span data-ttu-id="9df2b-167">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-167">TcpTransportBindingElement</span></span>](tcptransportbindingelement.md)  
  
 [<span data-ttu-id="9df2b-168">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-168">TextMessageEncodingBindingElement</span></span>](textmessageencodingbindingelement.md)  
  
 [<span data-ttu-id="9df2b-169">TraceListener</span><span class="sxs-lookup"><span data-stu-id="9df2b-169">TraceListener</span></span>](tracelistener.md)  
  
 [<span data-ttu-id="9df2b-170">TraceListenerArgument</span><span class="sxs-lookup"><span data-stu-id="9df2b-170">TraceListenerArgument</span></span>](tracelistenerargument.md)  
  
 [<span data-ttu-id="9df2b-171">TransactedBatchingBehavior</span><span class="sxs-lookup"><span data-stu-id="9df2b-171">TransactedBatchingBehavior</span></span>](transactedbatchingbehavior.md)  
  
 [<span data-ttu-id="9df2b-172">TransactionFlowAttribute</span><span class="sxs-lookup"><span data-stu-id="9df2b-172">TransactionFlowAttribute</span></span>](transactionflowattribute.md)  
  
 [<span data-ttu-id="9df2b-173">TransactionFlowBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-173">TransactionFlowBindingElement</span></span>](transactionflowbindingelement.md)  
  
 [<span data-ttu-id="9df2b-174">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-174">TransportBindingElement</span></span>](transportbindingelement.md)  
  
 [<span data-ttu-id="9df2b-175">TransportSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-175">TransportSecurityBindingElement</span></span>](transportsecuritybindingelement.md)  
  
 [<span data-ttu-id="9df2b-176">UseManagedPresentationBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-176">UseManagedPresentationBindingElement</span></span>](usemanagedpresentationbindingelement.md)  
  
 [<span data-ttu-id="9df2b-177">WindowsStreamSecurityBindingElement</span><span class="sxs-lookup"><span data-stu-id="9df2b-177">WindowsStreamSecurityBindingElement</span></span>](windowsstreamsecuritybindingelement.md)  
  
 [<span data-ttu-id="9df2b-178">WSAT_TraceEvent</span><span class="sxs-lookup"><span data-stu-id="9df2b-178">WSAT_TraceEvent</span></span>](wsat-traceevent.md)  
  
 [<span data-ttu-id="9df2b-179">WSAT_TraceProvider</span><span class="sxs-lookup"><span data-stu-id="9df2b-179">WSAT_TraceProvider</span></span>](wsat-traceprovider.md)  
  
 [<span data-ttu-id="9df2b-180">WSAT_TraceRecord</span><span class="sxs-lookup"><span data-stu-id="9df2b-180">WSAT_TraceRecord</span></span>](wsat-tracerecord.md)  
  
 [<span data-ttu-id="9df2b-181">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="9df2b-181">XmlDictionaryReaderQuotas</span></span>](xmldictionaryreaderquotas.md)  
  
 [<span data-ttu-id="9df2b-182">XmlSerializerOperationBehavior</span><span class="sxs-lookup"><span data-stu-id="9df2b-182">XmlSerializerOperationBehavior</span></span>](xmlserializeroperationbehavior.md)
