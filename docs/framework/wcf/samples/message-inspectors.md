---
title: メッセージ インスペクター
description: メッセージ検証メカニズムを提供する WCF クライアントおよびサービスメッセージインスペクターを実装して構成する方法について説明します。
ms.date: 03/30/2017
ms.assetid: 9bd1f305-ad03-4dd7-971f-fa1014b97c9b
ms.openlocfilehash: 4b2f7b97d0895e3cb7550217f64a2b0b14545abf
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240707"
---
# <a name="message-inspectors"></a><span data-ttu-id="b4349-103">メッセージ インスペクター</span><span class="sxs-lookup"><span data-stu-id="b4349-103">Message Inspectors</span></span>

<span data-ttu-id="b4349-104">このサンプルでは、クライアントとサービスのメッセージ インスペクタを実装して構成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b4349-104">This sample demonstrates how to implement and configure client and service message inspectors.</span></span>  
  
 <span data-ttu-id="b4349-105">メッセージ インスペクタは拡張オブジェクトで、サービス モデルのクライアント ランタイムで使用し、プログラムまたは構成を使用してランタイムをディスパッチします。それにより、受信後または送信前にメッセージの検査および変更を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b4349-105">A message inspector is an extensibility object that can be used in the service model's client runtime and dispatch runtime programmatically or through configuration and that can inspect and alter messages after they are received or before they are sent.</span></span>  
  
 <span data-ttu-id="b4349-106">このサンプルでは、クライアントとサービスの基本的なメッセージ検証機構を実装します。この機構は、構成可能な XML スキーマ ドキュメント セットに照らして受信メッセージを検証します。</span><span class="sxs-lookup"><span data-stu-id="b4349-106">This sample implements a basic client and service message validation mechanism that validates incoming messages against a set of configurable XML Schema documents.</span></span> <span data-ttu-id="b4349-107">このサンプルでのメッセージ検証は、操作ごとに行われません。</span><span class="sxs-lookup"><span data-stu-id="b4349-107">Note that this sample does not validate messages for each operation.</span></span> <span data-ttu-id="b4349-108">これは意図的に単純化されたサンプルであるためです。</span><span class="sxs-lookup"><span data-stu-id="b4349-108">This is an intentional simplification.</span></span>  
  
## <a name="message-inspector"></a><span data-ttu-id="b4349-109">Message Inspector</span><span class="sxs-lookup"><span data-stu-id="b4349-109">Message Inspector</span></span>  

 <span data-ttu-id="b4349-110">クライアント メッセージ インスペクタには、<xref:System.ServiceModel.Dispatcher.IClientMessageInspector> インターフェイスが実装され、サービス メッセージ インスペクタには <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> インターフェイスが実装されます。</span><span class="sxs-lookup"><span data-stu-id="b4349-110">Client message inspectors implement the <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> interface and service message inspectors implement the <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> interface.</span></span> <span data-ttu-id="b4349-111">こうした実装を 1 つのクラスに結合すると、クライアントとサービスの両方で使用できるメッセージ インスペクタとして設定できます。</span><span class="sxs-lookup"><span data-stu-id="b4349-111">The implementations can be combined into a single class to form a message inspector that works for both sides.</span></span> <span data-ttu-id="b4349-112">このサンプルでは、このように結合されたメッセージ インスペクタを実装します。</span><span class="sxs-lookup"><span data-stu-id="b4349-112">This sample implements such a combined message inspector.</span></span> <span data-ttu-id="b4349-113">このインスペクタは、受信メッセージと送信メッセージが検証されるスキーマ セットを渡すように構築されます。開発者はインスペクタを使用して、受信メッセージまたは送信メッセージを検証するかどうか、およびインスペクタをディスパッチ モードとクライアント モードのどちらにするかを指定できます。この指定内容は、このトピックで後述するようにエラー処理に影響します。</span><span class="sxs-lookup"><span data-stu-id="b4349-113">The inspector is constructed passing in a set of schemas against which incoming and outgoing messages are validated and allows the developer to specify whether incoming or outgoing messages are validated and whether the inspector is in dispatch or client mode, which affects the error handling as discussed later in this topic.</span></span>  
  
```csharp
public class SchemaValidationMessageInspector : IClientMessageInspector, IDispatchMessageInspector  
{  
    XmlSchemaSet schemaSet;  
    bool validateRequest;  
    bool validateReply;  
    bool isClientSide;  
    [ThreadStatic]  
    bool isRequest;  
  
    public SchemaValidationMessageInspector(XmlSchemaSet schemaSet,  
         bool validateRequest, bool validateReply, bool isClientSide)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = validateReply;  
        this.validateRequest = validateRequest;  
        this.isClientSide = isClientSide;  
    }  
```  
  
 <span data-ttu-id="b4349-114">サービス (ディスパッチャ) メッセージ インスペクタには、<xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> と <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> の、2 つの <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> メソッドを実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4349-114">Any service (dispatcher) message inspector must implement the two <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector> methods <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> and <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29>.</span></span>  
  
 <span data-ttu-id="b4349-115"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> がディスパッチャによって呼び出されるのは、メッセージが到着してチャネル スタックで処理され、サービスに割り当てられたときですが、メッセージが逆シリアル化されて操作にディスパッチされる前です。</span><span class="sxs-lookup"><span data-stu-id="b4349-115"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> is invoked by the dispatcher when a message has been received, processed by the channel stack and assigned to a service, but before it is deserialized and dispatched to an operation.</span></span> <span data-ttu-id="b4349-116">受信メッセージが暗号化されていた場合、そのメッセージはメッセージ インスペクタに到着するときには既に復号化されています。</span><span class="sxs-lookup"><span data-stu-id="b4349-116">If the incoming message was encrypted, the message is already decrypted when it reaches the message inspector.</span></span> <span data-ttu-id="b4349-117">このメソッドは、参照パラメータとして渡された `request` メッセージを取得します。これにより、必要に応じてメッセージを調査、操作または置き換えることができます。</span><span class="sxs-lookup"><span data-stu-id="b4349-117">The method gets the `request` message passed as a reference parameter, which allows the message to be inspected, manipulated or replaced as required.</span></span> <span data-ttu-id="b4349-118">戻り値は任意のオブジェクトで、サービスが現在のメッセージに応答を返すときに <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> に渡される相関状態オブジェクトとして使用されます。</span><span class="sxs-lookup"><span data-stu-id="b4349-118">The return value can be any object and is used as a correlation state object that is passed to <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> when the service returns a reply to the current message.</span></span> <span data-ttu-id="b4349-119">サンプルでは、<xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> はメッセージの検査 (検証) をプライベートでローカルのメソッド `ValidateMessageBody` に代行させ、相関状態オブジェクトを返しません。</span><span class="sxs-lookup"><span data-stu-id="b4349-119">In this sample, <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> delegates the inspection (validation) of the message to the private, local method `ValidateMessageBody` and returns no correlation state object.</span></span> <span data-ttu-id="b4349-120">このメソッドは、無効なメッセージがサービスに渡されないようにします。</span><span class="sxs-lookup"><span data-stu-id="b4349-120">This method ensures that no invalid messages pass into the service.</span></span>  
  
```csharp  
object IDispatchMessageInspector.AfterReceiveRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel, System.ServiceModel.InstanceContext instanceContext)  
{  
    if (validateRequest)  
    {  
        // inspect the message. If a validation error occurs,  
        // the thrown fault exception bubbles up.  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 <span data-ttu-id="b4349-121"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> は、応答がクライアントに返送される準備が完了するたびに呼び出されます。一方向メッセージの場合は、受信メッセージが処理されるときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b4349-121"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%28System.ServiceModel.Channels.Message%40%2CSystem.Object%29> is invoked whenever a reply is ready to be sent back to a client, or in the case of one-way messages, when the incoming message has been processed.</span></span> <span data-ttu-id="b4349-122">これにより、この拡張機能は MEP に関係なく対称的に呼び出されるものと想定できます。</span><span class="sxs-lookup"><span data-stu-id="b4349-122">This allows extensions to count on being called symmetrically, regardless of MEP.</span></span> <span data-ttu-id="b4349-123"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> と同様に、メッセージは参照パラメータとして渡され、検査、変更、または置き換えを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="b4349-123">As with <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, the message is passed as a reference parameter and can be inspected, modified or replaced.</span></span> <span data-ttu-id="b4349-124">このサンプルで実行されるメッセージの検証も、同様に `ValidMessageBody` メソッドで代行されますが、この場合、検証エラーの処理は若干異なります。</span><span class="sxs-lookup"><span data-stu-id="b4349-124">The validation of the message that is performed in this sample is again delegated to the `ValidMessageBody` method, but the handling of validation errors is slightly different in this case.</span></span>  
  
 <span data-ttu-id="b4349-125">サービスで検証エラーが発生すると、`ValidateMessageBody` メソッドは <xref:System.ServiceModel.FaultException> から派生した例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="b4349-125">If a validation error occurs on the service, the `ValidateMessageBody` method throws <xref:System.ServiceModel.FaultException>-derived exceptions.</span></span> <span data-ttu-id="b4349-126"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A> では、これらの例外をサービス モデル インフラストラクチャに格納できます。例外はここで自動的に SOAP エラーに変換され、クライアントに転送されます。</span><span class="sxs-lookup"><span data-stu-id="b4349-126">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.AfterReceiveRequest%2A>, these exceptions can be put into the service model infrastructure where they are automatically transformed into SOAP faults and relayed to the client.</span></span> <span data-ttu-id="b4349-127"><xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A> では、<xref:System.ServiceModel.FaultException> 例外はインフラストラクチャに格納できません。メッセージ インスペクタが呼び出される前に、サービスによってスローされたエラー例外が変換されるためです。</span><span class="sxs-lookup"><span data-stu-id="b4349-127">In <xref:System.ServiceModel.Dispatcher.IDispatchMessageInspector.BeforeSendReply%2A>, <xref:System.ServiceModel.FaultException> exceptions must not be put into the infrastructure, because the transformation of fault exceptions thrown by the service occurs before the message inspector is called.</span></span> <span data-ttu-id="b4349-128">したがって、次の実装では、既知の `ReplyValidationFault` 例外がキャッチされ、応答メッセージが明示的なエラー メッセージに置き換えられます。</span><span class="sxs-lookup"><span data-stu-id="b4349-128">Therefore the following implementation catches the known `ReplyValidationFault` exception and replaces the reply message with an explicit fault message.</span></span> <span data-ttu-id="b4349-129">このメソッドは、無効なメッセージがサービス実装によって返されないようにします。</span><span class="sxs-lookup"><span data-stu-id="b4349-129">This method ensures that no invalid messages are returned by the service implementation.</span></span>  
  
```csharp  
void IDispatchMessageInspector.BeforeSendReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        // Inspect the reply, catch a possible validation error
        try  
        {  
            ValidateMessageBody(ref reply, false);  
        }  
        catch (ReplyValidationFault fault)  
        {  
            // if a validation error occurred, the message is replaced  
            // with the validation fault.  
            reply = Message.CreateMessage(reply.Version,
                    fault.CreateMessageFault(), reply.Headers.Action);  
        }  
    }  
```  
  
 <span data-ttu-id="b4349-130">クライアント メッセージ インスペクタも、これとよく似ています。</span><span class="sxs-lookup"><span data-stu-id="b4349-130">The client message inspector is very similar.</span></span> <span data-ttu-id="b4349-131"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector> からは、<xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> および <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> の 2 つのメソッドが実装される必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4349-131">The two methods that must be implemented from <xref:System.ServiceModel.Dispatcher.IClientMessageInspector> are <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.AfterReceiveReply%2A> and <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A>.</span></span>  
  
 <span data-ttu-id="b4349-132"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> は、クライアント アプリケーションまたは操作フォーマッタのどちらかでメッセージが作成されたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b4349-132"><xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> is invoked when the message has been composed either by the client application or by the operation formatter.</span></span> <span data-ttu-id="b4349-133">ディスパッチャ メッセージ インスペクタと同様、メッセージを検査することも、または完全に置き換えることもできます。</span><span class="sxs-lookup"><span data-stu-id="b4349-133">As with the dispatcher message inspectors, the message can just be inspected or entirely replaced.</span></span> <span data-ttu-id="b4349-134">このサンプルのインスペクタは、ディスパッチ メッセージ インスペクタにも使用されている、同じローカルの `ValidateMessageBody` ヘルパー メソッドに代行させます。</span><span class="sxs-lookup"><span data-stu-id="b4349-134">In this sample, the inspector delegates to the same local `ValidateMessageBody` helper method that is also used for the dispatch message inspectors.</span></span>  
  
 <span data-ttu-id="b4349-135">(コンストラクタで指定される) クライアント検証とサービス検証間の動作上の違いは、クライアント検証はユーザー コードに格納するローカル例外をスローする点です。この例外はローカルに発生するもので、サービス エラーではないためです。</span><span class="sxs-lookup"><span data-stu-id="b4349-135">The behavioral difference between the client and service validation (as specified in the constructor) is that the client validation throws local exceptions that are put into the user code because they occur locally and not because of a service failure.</span></span> <span data-ttu-id="b4349-136">通常のルールでは、サービス ディスパッチャ インスペクタがエラーをスローするのに対し、クライアント インスペクタは例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="b4349-136">Generally, the rule is that service dispatcher inspectors throw faults and that client inspectors throw exceptions.</span></span>  
  
 <span data-ttu-id="b4349-137">この <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> の実装は、無効なメッセージがサービスに送信されないようにします。</span><span class="sxs-lookup"><span data-stu-id="b4349-137">This <xref:System.ServiceModel.Dispatcher.IClientMessageInspector.BeforeSendRequest%2A> implementation ensures that no invalid messages are sent to the service.</span></span>  
  
```csharp  
object IClientMessageInspector.BeforeSendRequest(ref System.ServiceModel.Channels.Message request, System.ServiceModel.IClientChannel channel)  
{  
    if (validateRequest)  
    {  
        ValidateMessageBody(ref request, true);  
    }  
    return null;  
}  
```  
  
 <span data-ttu-id="b4349-138">`AfterReceiveReply` の実装は、サービスから受信された無効なメッセージがクライアント ユーザー コードに転送されないようにします。</span><span class="sxs-lookup"><span data-stu-id="b4349-138">The `AfterReceiveReply` implementation ensures that no invalid messages received from the service are relayed to the client user code.</span></span>  
  
```csharp  
void IClientMessageInspector.AfterReceiveReply(ref System.ServiceModel.Channels.Message reply, object correlationState)  
{  
    if (validateReply)  
    {  
        ValidateMessageBody(ref reply, false);  
    }  
}  
```  
  
 <span data-ttu-id="b4349-139">この特定のメッセージ インスペクタの中心となるのが `ValidateMessageBody` メソッドです。</span><span class="sxs-lookup"><span data-stu-id="b4349-139">The heart of this particular message inspector is the `ValidateMessageBody` method.</span></span> <span data-ttu-id="b4349-140">この動作を実行するには、渡されるメッセージ本文のコンテンツのサブツリーを、<xref:System.Xml.XmlReader> 検証でラップします。</span><span class="sxs-lookup"><span data-stu-id="b4349-140">To perform its work, it wraps a validating <xref:System.Xml.XmlReader> around the body content sub-tree of the passed message.</span></span> <span data-ttu-id="b4349-141">リーダーには、メッセージ インスペクタが保持するスキーマ セットが設定され、検証コールバックは、このメソッドと共に定義される `InspectionValidationHandler` を参照するデリゲートに設定されます。</span><span class="sxs-lookup"><span data-stu-id="b4349-141">The reader is populated with the set of schemas that the message inspector holds and the validation callback is set to a delegate referring to the `InspectionValidationHandler` that is defined alongside this method.</span></span> <span data-ttu-id="b4349-142">この検証を実行するためにメッセージが読み取られ、メモリ ストリームを基にする <xref:System.Xml.XmlDictionaryWriter> にスプールされます。</span><span class="sxs-lookup"><span data-stu-id="b4349-142">To perform the validation, the message is then read and spooled into a memory stream-backed <xref:System.Xml.XmlDictionaryWriter>.</span></span> <span data-ttu-id="b4349-143">この処理中に検証エラーまたは警告が発生した場合は、コールバック メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b4349-143">If a validation error or warning occurs in the process, the callback method is invoked.</span></span>  
  
 <span data-ttu-id="b4349-144">エラーが発生しない場合、プロパティとヘッダーが元のメッセージからコピーされた、新しいメッセージが作成されます。このメッセージにはメモリ ストリーム内の現在検証した Infoset が使用され、<xref:System.Xml.XmlDictionaryReader> でラップされて置換メッセージに追加されます。</span><span class="sxs-lookup"><span data-stu-id="b4349-144">If no error occurs, a new message is constructed that copies the properties and headers from the original message and uses the now-validated infoset in the memory stream, which is wrapped by an <xref:System.Xml.XmlDictionaryReader> and added to the replacement message.</span></span>  
  
```csharp  
void ValidateMessageBody(ref System.ServiceModel.Channels.Message message, bool isRequest)  
{  
    if (!message.IsFault)  
    {  
        XmlDictionaryReaderQuotas quotas =
                new XmlDictionaryReaderQuotas();  
        XmlReader bodyReader =
            message.GetReaderAtBodyContents().ReadSubtree();  
        XmlReaderSettings wrapperSettings =
                              new XmlReaderSettings();  
        wrapperSettings.CloseInput = true;  
        wrapperSettings.Schemas = schemaSet;  
        wrapperSettings.ValidationFlags =
                                XmlSchemaValidationFlags.None;  
        wrapperSettings.ValidationType = ValidationType.Schema;  
        wrapperSettings.ValidationEventHandler += new
           ValidationEventHandler(InspectionValidationHandler);  
        XmlReader wrappedReader = XmlReader.Create(bodyReader,
                                            wrapperSettings);  
  
        // pull body into a memory backed writer to validate  
        this.isRequest = isRequest;  
        MemoryStream memStream = new MemoryStream();  
        XmlDictionaryWriter xdw =  
              XmlDictionaryWriter.CreateBinaryWriter(memStream);  
        xdw.WriteNode(wrappedReader, false);  
        xdw.Flush(); memStream.Position = 0;  
        XmlDictionaryReader xdr =
        XmlDictionaryReader.CreateBinaryReader(memStream, quotas);  
  
        // reconstruct the message with the validated body  
        Message replacedMessage =
            Message.CreateMessage(message.Version, null, xdr);  
        replacedMessage.Headers.CopyHeadersFrom(message.Headers);  
        replacedMessage.Properties.CopyProperties(message.Properties);  
        message = replacedMessage;  
    }  
}  
```  
  
 <span data-ttu-id="b4349-145">`InspectionValidationHandler` メソッドは、スキーマの検証エラーまたは警告が発生するたびに、<xref:System.Xml.XmlReader> 検証によって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="b4349-145">The `InspectionValidationHandler` method is called by the validating <xref:System.Xml.XmlReader> whenever a schema validation error or warning occurs.</span></span> <span data-ttu-id="b4349-146">次の実装はエラーにのみ対応し、すべての警告を無視します。</span><span class="sxs-lookup"><span data-stu-id="b4349-146">The following implementation only works with errors and ignores all warnings.</span></span>  
  
 <span data-ttu-id="b4349-147">最初は、<xref:System.Xml.XmlReader> 検証をメッセージ インスペクタを使用してメッセージに挿入し、メッセージの処理時にメッセージをバッファ処理することなく検証できるように思えます。</span><span class="sxs-lookup"><span data-stu-id="b4349-147">On first consideration, it might seem possible to inject a validating <xref:System.Xml.XmlReader> into the message with the message inspector and let the validation happen as the message is processed and without buffering the message.</span></span> <span data-ttu-id="b4349-148">ただし、この場合、このコールバックがサービス モデル インフラストラクチャの任意の場所に検証例外をスローするか、またはユーザー コードが無効な XML ノードとして検出され、その結果、予測不可能な動作になります。</span><span class="sxs-lookup"><span data-stu-id="b4349-148">That, however, means that this callback throws the validation exceptions somewhere into the service model infrastructure or the user code as invalid XML nodes are detected, resulting in unpredictable behavior.</span></span> <span data-ttu-id="b4349-149">バッファ処理の方法により、ユーザー コードは無効なメッセージから完全にシールドされます。</span><span class="sxs-lookup"><span data-stu-id="b4349-149">The buffering approach shields the user code from invalid messages, entirely.</span></span>  
  
 <span data-ttu-id="b4349-150">これまでに説明したように、ハンドラによってスローされる例外は、クライアントとサービスとでは異なります。</span><span class="sxs-lookup"><span data-stu-id="b4349-150">As previously discussed, the exceptions thrown by the handler differ between the client and the service.</span></span> <span data-ttu-id="b4349-151">サービスでの例外は <xref:System.ServiceModel.FaultException> から派生し、クライアントでの例外は標準のカスタム例外です。</span><span class="sxs-lookup"><span data-stu-id="b4349-151">On the service, the exceptions are derived from <xref:System.ServiceModel.FaultException>, on the client the exceptions are regular custom exceptions.</span></span>  
  
```csharp  
        void InspectionValidationHandler(object sender, ValidationEventArgs e)  
{  
    if (e.Severity == XmlSeverityType.Error)  
    {  
        // We are treating client and service side validation errors  
        // differently here. Client side errors cause exceptions  
        // and are thrown straight up to the user code. Service side  
        // validations cause faults.  
        if (isClientSide)  
        {  
            if (isRequest)  
            {  
                throw new RequestClientValidationException(e.Message);  
            }  
            else  
            {  
                throw new ReplyClientValidationException(e.Message);  
            }  
        }  
        else  
        {  
            if (isRequest)  
            {  
                // this fault is caught by the ServiceModel
                // infrastructure and turned into a fault reply.  
                throw new RequestValidationFault(e.Message);  
             }  
             else  
             {  
                // this fault is caught and turned into a fault message  
                // in BeforeSendReply in this class  
                throw new ReplyValidationFault(e.Message);  
              }  
          }  
      }  
    }  
```  
  
## <a name="behavior"></a><span data-ttu-id="b4349-152">動作</span><span class="sxs-lookup"><span data-stu-id="b4349-152">Behavior</span></span>  

 <span data-ttu-id="b4349-153">メッセージ インスペクタは、クライアント ランタイムまたはディスパッチ ランタイムに対する拡張機能です。</span><span class="sxs-lookup"><span data-stu-id="b4349-153">Message inspectors are extensions to the client runtime or the dispatch runtime.</span></span> <span data-ttu-id="b4349-154">このような拡張機能は、 *ビヘイビアー* を使用して構成されます。</span><span class="sxs-lookup"><span data-stu-id="b4349-154">Such extensions are configured using *behaviors*.</span></span> <span data-ttu-id="b4349-155">動作はサービス モデル ランタイムの動作を変更するクラスです。この変更は、既定の構成を変更するか、または拡張機能 (メッセージ インスペクタなど) を追加したりすることによって行われます。</span><span class="sxs-lookup"><span data-stu-id="b4349-155">A behavior is a class that changes the behavior of the service model runtime by changing the default configuration or adding extensions (such as message inspectors) to it.</span></span>  
  
 <span data-ttu-id="b4349-156">次の `SchemaValidationBehavior` クラスは、このサンプルのメッセージ インスペクタをクライアント ランタイムまたはディスパッチ ランタイムに追加するときに使用される動作です。</span><span class="sxs-lookup"><span data-stu-id="b4349-156">The following `SchemaValidationBehavior` class is the behavior used to add this sample's message inspector to the client or dispatch runtime.</span></span> <span data-ttu-id="b4349-157">この実装は、どちらの場合でも基本的な実装です。</span><span class="sxs-lookup"><span data-stu-id="b4349-157">The implementation is rather basic in both cases.</span></span> <span data-ttu-id="b4349-158"><xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> と <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A> ではメッセージ インスペクタが作成され、それぞれのランタイムの <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> コレクションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="b4349-158">In <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyClientBehavior%2A> and <xref:System.ServiceModel.Description.IEndpointBehavior.ApplyDispatchBehavior%2A>, the message inspector is created and added to the <xref:System.ServiceModel.Dispatcher.ClientRuntime.MessageInspectors%2A> collection of the respective runtime.</span></span>  
  
```csharp
public class SchemaValidationBehavior : IEndpointBehavior  
{  
    XmlSchemaSet schemaSet;
    bool validateRequest;
    bool validateReply;  
  
    public SchemaValidationBehavior(XmlSchemaSet schemaSet, bool
                           inspectRequest, bool inspectReply)  
    {  
        this.schemaSet = schemaSet;  
        this.validateReply = inspectReply;  
        this.validateRequest = inspectRequest;  
    }  
    #region IEndpointBehavior Members  
  
    public void AddBindingParameters(ServiceEndpoint endpoint,
       System.ServiceModel.Channels.BindingParameterCollection
                                            bindingParameters)  
    {  
    }  
  
    public void ApplyClientBehavior(ServiceEndpoint endpoint,
            System.ServiceModel.Dispatcher.ClientRuntime clientRuntime)  
    {  
        SchemaValidationMessageInspector inspector =
           new SchemaValidationMessageInspector(schemaSet,
                      validateRequest, validateReply, true);  
            clientRuntime.MessageInspectors.Add(inspector);  
    }  
  
    public void ApplyDispatchBehavior(ServiceEndpoint endpoint,
         System.ServiceModel.Dispatcher.EndpointDispatcher
                                          endpointDispatcher)  
    {  
        SchemaValidationMessageInspector inspector =
           new SchemaValidationMessageInspector(schemaSet,
                        validateRequest, validateReply, false);  
   endpointDispatcher.DispatchRuntime.MessageInspectors.Add(inspector);  
    }  
  
   public void Validate(ServiceEndpoint endpoint)  
   {  
   }  
  
    #endregion  
}  
```  
  
> [!NOTE]
> <span data-ttu-id="b4349-159">この特定の動作は属性の代わりにはなりません。したがって、サービス型のコントラクト型に宣言して追加することはできません。</span><span class="sxs-lookup"><span data-stu-id="b4349-159">This particular behavior does not double as an attribute and therefore cannot be added declaratively onto a contract type of a service type.</span></span> <span data-ttu-id="b4349-160">これは設計上の判断です。スキーマ コレクションを属性の宣言で読み込むことはできず、この属性で他の構成場所 (アプリケーション設定など) を参照することによって、残りのサービス モデル構成と一貫性を持たない構成要素が作成されるからです。</span><span class="sxs-lookup"><span data-stu-id="b4349-160">This is a by-design decision made because the schema collection cannot be loaded in an attribute declaration and referring to an extra configuration location (for instance to the application settings) in this attribute means creating a configuration element that is not consistent with the rest of the service model configuration.</span></span> <span data-ttu-id="b4349-161">したがって、この動作は、強制的にコードおよびサービス モデル構成の拡張を使用してのみ追加できます。</span><span class="sxs-lookup"><span data-stu-id="b4349-161">Therefore, this behavior can only be added imperatively through code and through a service model configuration extension.</span></span>  
  
## <a name="adding-the-message-inspector-through-configuration"></a><span data-ttu-id="b4349-162">構成を使用したメッセージ インスペクタの追加</span><span class="sxs-lookup"><span data-stu-id="b4349-162">Adding the Message Inspector through Configuration</span></span>  

 <span data-ttu-id="b4349-163">アプリケーション構成ファイルのエンドポイントでカスタム動作を構成するには、サービスモデルで、から派生したクラスによって表される構成 *拡張要素* を作成する実装が必要です <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> 。</span><span class="sxs-lookup"><span data-stu-id="b4349-163">For configuring a custom behavior on an endpoint in the application configuration file, the service model requires implementers to create a configuration *extension element* represented by a class derived from <xref:System.ServiceModel.Configuration.BehaviorExtensionElement>.</span></span> <span data-ttu-id="b4349-164">次に、この拡張機能を拡張用のサービス モデルの構成セクションに追加する必要があります。このセクションで説明する拡張機能を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b4349-164">This extension must then be added to the service model's configuration section for extensions as shown for the following extension discussed in this section.</span></span>  
  
```xml  
<system.serviceModel>  
…  
   <extensions>  
      <behaviorExtensions>  
        <add name="schemaValidator" type="Microsoft.ServiceModel.Samples.SchemaValidationBehaviorExtensionElement, MessageInspectors, Version=1.0.0.0, Culture=neutral, PublicKeyToken=null"/>  
      </behaviorExtensions>  
    </extensions>  
…  
</system.serviceModel>  
```  
  
 <span data-ttu-id="b4349-165">拡張機能は、アプリケーションまたは ASP.NET の構成ファイルに追加できます。これが最も一般的な選択肢ですが、コンピュータ上の構成ファイルに追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="b4349-165">Extensions can be added in the application or ASP.NET configuration file, which is the most common choice, or in the machine configuration file.</span></span>  
  
 <span data-ttu-id="b4349-166">拡張機能を構成範囲に追加すると、次のコードに示すように、動作を動作の構成に追加できるようになります。</span><span class="sxs-lookup"><span data-stu-id="b4349-166">When the extension is added to a configuration scope, the behavior can be added to a behavior configuration as it is shown in the following code.</span></span> <span data-ttu-id="b4349-167">動作の構成は再使用可能な要素で、必要に応じて複数のエンドポイントに適用できます。</span><span class="sxs-lookup"><span data-stu-id="b4349-167">Behavior configurations are reusable elements that can be applied to multiple endpoints as required.</span></span> <span data-ttu-id="b4349-168">ここで構成される特定の動作は <xref:System.ServiceModel.Description.IEndpointBehavior> を実装するので、構成ファイルの各構成セクションでのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="b4349-168">Because the particular behavior to be configured here implements <xref:System.ServiceModel.Description.IEndpointBehavior>, it is only valid in the respective configuration section in the configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
   <behaviors>  
      …  
     <endpointBehaviors>  
        <behavior name="HelloServiceEndpointBehavior">  
          <schemaValidator validateRequest="True" validateReply="True">  
            <schemas>  
              <add location="messages.xsd" />
            </schemas>  
          </schemaValidator>  
        </behavior>  
      </endpointBehaviors>  
      …  
    </behaviors>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="b4349-169">メッセージ インスペクタを構成する `<schemaValidator>` 要素は、`SchemaValidationBehaviorExtensionElement` クラスによってサポートされます。</span><span class="sxs-lookup"><span data-stu-id="b4349-169">The `<schemaValidator>` element that configures the message inspector is backed by the `SchemaValidationBehaviorExtensionElement` class.</span></span> <span data-ttu-id="b4349-170">このクラスは、`ValidateRequest` と `ValidateReply` という 2 つのブール型パブリック プロパティを公開します。</span><span class="sxs-lookup"><span data-stu-id="b4349-170">The class exposes two Boolean public properties named `ValidateRequest` and `ValidateReply`.</span></span> <span data-ttu-id="b4349-171">これらのプロパティは、どちらも <xref:System.Configuration.ConfigurationPropertyAttribute> でマークされます。</span><span class="sxs-lookup"><span data-stu-id="b4349-171">Both of these are marked with a <xref:System.Configuration.ConfigurationPropertyAttribute>.</span></span> <span data-ttu-id="b4349-172">この属性は、コードのプロパティと XML 属性との間のリンクを構成するもので、前の XML 構成要素に含まれています。</span><span class="sxs-lookup"><span data-stu-id="b4349-172">This attribute constitutes the link between the code properties and the XML attributes that can be seen on the preceding XML configuration element.</span></span> <span data-ttu-id="b4349-173">このクラスには、追加で `Schemas` でマークされる、<xref:System.Configuration.ConfigurationCollectionAttribute> 型のプロパティ `SchemaCollection` もあります。これもこのサンプルに含まれていますが、このドキュメントでは簡略化のために省略されています。</span><span class="sxs-lookup"><span data-stu-id="b4349-173">The class also has a property `Schemas` that is additionally marked with the <xref:System.Configuration.ConfigurationCollectionAttribute> and is of the type `SchemaCollection`, which is also part of this sample but omitted from this document for brevity.</span></span> <span data-ttu-id="b4349-174">このプロパティは、コレクションおよびコレクション要素クラス `SchemaConfigElement` と共に、前の構成スニペット内の `<schemas>` 要素を補足し、スキーマのコレクションを検証セットに追加できるようにします。</span><span class="sxs-lookup"><span data-stu-id="b4349-174">This property along with the collection and the collection element class `SchemaConfigElement` backs the `<schemas>` element in the preceding configuration snippet and allows adding a collection of schemas to the validation set.</span></span>  
  
 <span data-ttu-id="b4349-175">ランタイムがクライアントまたはエンドポイントを構築するときにその構成データを評価する場合、オーバーライドされた `CreateBehavior` メソッドにより、構成データは動作オブジェクトになります。</span><span class="sxs-lookup"><span data-stu-id="b4349-175">The overridden `CreateBehavior` method turns the configuration data into a behavior object when the runtime evaluates the configuration data as it builds a client or an endpoint.</span></span>  
  
```csharp
public class SchemaValidationBehaviorExtensionElement : BehaviorExtensionElement  
{  
    public SchemaValidationBehaviorExtensionElement()  
    {  
    }  
  
    public override Type BehaviorType
    {
        get  
        {  
            return typeof(SchemaValidationBehavior);  
        }
    }  
  
    protected override object CreateBehavior()  
    {  
        XmlSchemaSet schemaSet = new XmlSchemaSet();  
        foreach (SchemaConfigElement schemaCfg in this.Schemas)  
        {  
            Uri baseSchema = new
                Uri(AppDomain.CurrentDomain.BaseDirectory);  
            string location = new
                Uri(baseSchema,schemaCfg.Location).ToString();  
            XmlSchema schema =
                XmlSchema.Read(new XmlTextReader(location), null);  
            schemaSet.Add(schema);  
        }  
     return new
     SchemaValidationBehavior(schemaSet,ValidateRequest,ValidateReply);  
    }  
  
[ConfigurationProperty("validateRequest",DefaultValue=false,IsRequired=false)]  
public bool ValidateRequest  
{  
    get { return (bool)base["validateRequest"]; }  
    set { base["validateRequest"] = value; }  
}  
  
[ConfigurationProperty("validateReply", DefaultValue = false, IsRequired = false)]  
        public bool ValidateReply  
        {  
            get { return (bool)base["validateReply"]; }  
            set { base["validateReply"] = value; }  
        }  
  
     //Declare the Schema collection property.  
     //Note: the "IsDefaultCollection = false" instructs
     //.NET Framework to build a nested section of
     //the kind <Schema> ...</Schema>.  
    [ConfigurationProperty("schemas", IsDefaultCollection = true)]  
    [ConfigurationCollection(typeof(SchemasCollection),  
        AddItemName = "add",  
        ClearItemsName = "clear",  
        RemoveItemName = "remove")]  
    public SchemasCollection Schemas  
    {  
        get  
        {  
            SchemasCollection SchemasCollection =  
            (SchemasCollection)base["schemas"];  
            return SchemasCollection;  
        }  
    }  
}  
```  
  
## <a name="adding-message-inspectors-imperatively"></a><span data-ttu-id="b4349-176">メッセージ インスペクタの強制的な追加</span><span class="sxs-lookup"><span data-stu-id="b4349-176">Adding Message Inspectors Imperatively</span></span>  

 <span data-ttu-id="b4349-177">属性 (このサンプルでは前の理由により未サポート) と構成を使用せず、極力簡単に動作をクライアント ランタイムとサービス ランタイムに追加するには、強制コードを使用できます。</span><span class="sxs-lookup"><span data-stu-id="b4349-177">Except through attributes (which is not supported in this sample for the reason cited previously) and configuration, behaviors can quite easily be added to a client and service runtime using imperative code.</span></span> <span data-ttu-id="b4349-178">このサンプルでは、クライアント アプリケーションで強制コードを使用して、クライアント メッセージ インスペクタをテストします。</span><span class="sxs-lookup"><span data-stu-id="b4349-178">In this sample, this is done in the client application to test the client message inspector.</span></span> <span data-ttu-id="b4349-179">`GenericClient` クラスは、エンドポイント構成をユーザー コードに対して公開する <xref:System.ServiceModel.ClientBase%601> から派生しています。</span><span class="sxs-lookup"><span data-stu-id="b4349-179">The `GenericClient` class is derived from <xref:System.ServiceModel.ClientBase%601>, which exposes the endpoint configuration to the user code.</span></span> <span data-ttu-id="b4349-180">クライアントが暗黙に開かれる前に、エンドポイント構成は変更できます。たとえば、次のコードで示すように動作を追加します。</span><span class="sxs-lookup"><span data-stu-id="b4349-180">Before the client is implicitly opened the endpoint configuration can be changed, for instance by adding behaviors as shown in the following code.</span></span> <span data-ttu-id="b4349-181">サービスに動作を追加する方法は、ここで示すクライアントの手法と非常に似ており、サービス ホストが開かれる前に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b4349-181">Adding the behavior on the service is largely equivalent to the client technique shown here and must be performed before the service host is opened.</span></span>  
  
```csharp  
try  
{  
    Console.WriteLine("*** Call 'Hello' with generic client, with client behavior");  
    GenericClient client = new GenericClient();  
  
    // Configure client programmatically, adding behavior  
    XmlSchema schema = XmlSchema.Read(new StreamReader("messages.xsd"),
                                                          null);  
    XmlSchemaSet schemaSet = new XmlSchemaSet();  
    schemaSet.Add(schema);  
    client.Endpoint.Behaviors.Add(new
                SchemaValidationBehavior(schemaSet, true, true));  
  
    Console.WriteLine("--- Sending valid client request:");  
    GenericCallValid(client, helloAction);  
    Console.WriteLine("--- Sending invalid client request:");  
    GenericCallInvalid(client, helloAction);  
  
    client.Close();  
}  
catch (Exception e)  
{  
    DumpException(e);  
}  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b4349-182">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="b4349-182">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="b4349-183">[Windows Communication Foundation サンプルの1回限りのセットアップ手順](one-time-setup-procedure-for-the-wcf-samples.md)を実行したことを確認します。</span><span class="sxs-lookup"><span data-stu-id="b4349-183">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="b4349-184">ソリューションをビルドするには、「 [Windows Communication Foundation サンプルのビルド](building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b4349-184">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="b4349-185">サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「 [Windows Communication Foundation サンプルの実行](running-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b4349-185">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="b4349-186">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b4349-186">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b4349-187">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b4349-187">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="b4349-188">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="b4349-188">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b4349-189">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b4349-189">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\MessageInspectors`  
