---
title: SendMail カスタム アクティビティ
ms.date: 03/30/2017
ms.assetid: 947a9ae6-379c-43a3-9cd5-87f573a5739f
ms.openlocfilehash: f518beebe336080853e4dec3bca6f8539bbec304
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96267591"
---
# <a name="sendmail-custom-activity"></a><span data-ttu-id="d0751-102">SendMail カスタム アクティビティ</span><span class="sxs-lookup"><span data-stu-id="d0751-102">SendMail Custom Activity</span></span>

<span data-ttu-id="d0751-103">このサンプルでは、<xref:System.Activities.AsyncCodeActivity> から派生するカスタム アクティビティを作成して、SMTP を使用して電子メールを送信し、ワークフロー アプリケーション内で使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d0751-103">This sample demonstrates how to create a custom activity that derives from <xref:System.Activities.AsyncCodeActivity> to send mail using SMTP for use within a workflow application.</span></span> <span data-ttu-id="d0751-104">カスタムアクティビティでは、の機能を使用して、 <xref:System.Net.Mail.SmtpClient> 電子メールを非同期的に送信し、認証を使用してメールを送信します。</span><span class="sxs-lookup"><span data-stu-id="d0751-104">The custom activity uses the capabilities of <xref:System.Net.Mail.SmtpClient> to send email asynchronously and to send mail with authentication.</span></span> <span data-ttu-id="d0751-105">また、テスト モード、トークン置換、ファイル テンプレート、テスト ドロップ パスなどのエンドユーザーの機能も提供しています。</span><span class="sxs-lookup"><span data-stu-id="d0751-105">It also provides some end-user features like test mode, token replacement, file templates, and test drop path.</span></span>  
  
 <span data-ttu-id="d0751-106">次の表で、`SendMail` アクティビティの引数の詳細を説明します。</span><span class="sxs-lookup"><span data-stu-id="d0751-106">The following table details the arguments for the `SendMail` activity.</span></span>  
  
|<span data-ttu-id="d0751-107">名前</span><span class="sxs-lookup"><span data-stu-id="d0751-107">Name</span></span>|<span data-ttu-id="d0751-108">Type</span><span class="sxs-lookup"><span data-stu-id="d0751-108">Type</span></span>|<span data-ttu-id="d0751-109">説明</span><span class="sxs-lookup"><span data-stu-id="d0751-109">Description</span></span>|  
|-|-|-|  
|<span data-ttu-id="d0751-110">Host</span><span class="sxs-lookup"><span data-stu-id="d0751-110">Host</span></span>|<span data-ttu-id="d0751-111">文字列型</span><span class="sxs-lookup"><span data-stu-id="d0751-111">String</span></span>|<span data-ttu-id="d0751-112">SMTP サーバー ホストのアドレス。</span><span class="sxs-lookup"><span data-stu-id="d0751-112">Address of the SMTP server host.</span></span>|  
|<span data-ttu-id="d0751-113">Port</span><span class="sxs-lookup"><span data-stu-id="d0751-113">Port</span></span>|<span data-ttu-id="d0751-114">文字列型</span><span class="sxs-lookup"><span data-stu-id="d0751-114">String</span></span>|<span data-ttu-id="d0751-115">ホストの SMTP サービスのポート。</span><span class="sxs-lookup"><span data-stu-id="d0751-115">Port of the SMTP service in the host.</span></span>|  
|<span data-ttu-id="d0751-116">EnableSsl</span><span class="sxs-lookup"><span data-stu-id="d0751-116">EnableSsl</span></span>|<span data-ttu-id="d0751-117">[bool]</span><span class="sxs-lookup"><span data-stu-id="d0751-117">bool</span></span>|<span data-ttu-id="d0751-118"><xref:System.Net.Mail.SmtpClient> が、接続を暗号化するために SSL (Secure Sockets Layer) を使用するかどうかを指定します。</span><span class="sxs-lookup"><span data-stu-id="d0751-118">Specifies whether the <xref:System.Net.Mail.SmtpClient> uses Secure Sockets Layer (SSL) to encrypt the connection.</span></span>|  
|<span data-ttu-id="d0751-119">UserName</span><span class="sxs-lookup"><span data-stu-id="d0751-119">UserName</span></span>|<span data-ttu-id="d0751-120">文字列型</span><span class="sxs-lookup"><span data-stu-id="d0751-120">String</span></span>|<span data-ttu-id="d0751-121">差出人の <xref:System.Net.Mail.SmtpClient.Credentials%2A> プロパティを認証する資格情報を設定するユーザー名。</span><span class="sxs-lookup"><span data-stu-id="d0751-121">Username to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="d0751-122">パスワード</span><span class="sxs-lookup"><span data-stu-id="d0751-122">Password</span></span>|<span data-ttu-id="d0751-123">文字列型</span><span class="sxs-lookup"><span data-stu-id="d0751-123">String</span></span>|<span data-ttu-id="d0751-124">差出人の <xref:System.Net.Mail.SmtpClient.Credentials%2A> プロパティを認証する資格情報を設定するパスワード。</span><span class="sxs-lookup"><span data-stu-id="d0751-124">Password to set up the credentials to authenticate the sender <xref:System.Net.Mail.SmtpClient.Credentials%2A> property.</span></span>|  
|<span data-ttu-id="d0751-125">サブジェクト</span><span class="sxs-lookup"><span data-stu-id="d0751-125">Subject</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="d0751-126">メッセージの件名。</span><span class="sxs-lookup"><span data-stu-id="d0751-126">Subject of the message.</span></span>|  
|<span data-ttu-id="d0751-127">本文</span><span class="sxs-lookup"><span data-stu-id="d0751-127">Body</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="d0751-128">メッセージの本文。</span><span class="sxs-lookup"><span data-stu-id="d0751-128">Body of the message.</span></span>|  
|<span data-ttu-id="d0751-129">[Attachments]</span><span class="sxs-lookup"><span data-stu-id="d0751-129">Attachments</span></span>|<xref:System.Activities.InArgument%601>\<string>|<span data-ttu-id="d0751-130">この電子メールメッセージに添付されたデータを格納するために使用される添付ファイルのコレクションです。</span><span class="sxs-lookup"><span data-stu-id="d0751-130">Attachment collection used to store data attached to this email message.</span></span>|  
|<span data-ttu-id="d0751-131">ソース</span><span class="sxs-lookup"><span data-stu-id="d0751-131">From</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="d0751-132">この電子メールメッセージの差出人アドレス。</span><span class="sxs-lookup"><span data-stu-id="d0751-132">From address for this email message.</span></span>|  
|<span data-ttu-id="d0751-133">終了</span><span class="sxs-lookup"><span data-stu-id="d0751-133">To</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="d0751-134">この電子メールメッセージの受信者を含むアドレスコレクション。</span><span class="sxs-lookup"><span data-stu-id="d0751-134">Address collection that contains the recipients of this email message.</span></span>|  
|<span data-ttu-id="d0751-135">CC</span><span class="sxs-lookup"><span data-stu-id="d0751-135">CC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="d0751-136">この電子メールメッセージのカーボンコピー (CC) 受信者を格納するアドレスのコレクション。</span><span class="sxs-lookup"><span data-stu-id="d0751-136">Address collection that contains the carbon copy (CC) recipients for this email message.</span></span>|  
|<span data-ttu-id="d0751-137">BCC</span><span class="sxs-lookup"><span data-stu-id="d0751-137">BCC</span></span>|<xref:System.Activities.InArgument%601>\<<xref:System.Net.Mail.MailAddressCollection>>|<span data-ttu-id="d0751-138">この電子メールメッセージの BCC (ブラインドカーボンコピー) 受信者を含むアドレスコレクション。</span><span class="sxs-lookup"><span data-stu-id="d0751-138">Address collection that contains the blind carbon copy (BCC) recipients for this email message.</span></span>|  
|<span data-ttu-id="d0751-139">トークン</span><span class="sxs-lookup"><span data-stu-id="d0751-139">Tokens</span></span>|<span data-ttu-id="d0751-140"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span><span class="sxs-lookup"><span data-stu-id="d0751-140"><xref:System.Activities.InArgument%601><IDictionary\<string, string>></span></span>|<span data-ttu-id="d0751-141">本文で置換するトークン。</span><span class="sxs-lookup"><span data-stu-id="d0751-141">Tokens to replace in the body.</span></span> <span data-ttu-id="d0751-142">この機能を使用すると、本文にいくつかの値を指定した後、このプロパティを使用して提供されるトークンで置換できます。</span><span class="sxs-lookup"><span data-stu-id="d0751-142">This feature allows users to specify some values in the body than can be replaced later by the tokens provided using this property.</span></span>|  
|<span data-ttu-id="d0751-143">BodyTemplateFilePath</span><span class="sxs-lookup"><span data-stu-id="d0751-143">BodyTemplateFilePath</span></span>|<span data-ttu-id="d0751-144">文字列型</span><span class="sxs-lookup"><span data-stu-id="d0751-144">String</span></span>|<span data-ttu-id="d0751-145">本文のテンプレートのパス。</span><span class="sxs-lookup"><span data-stu-id="d0751-145">Path of a template for the body.</span></span> <span data-ttu-id="d0751-146">`SendMail` アクティビティは、このファイルの内容をその body プロパティにコピーします。</span><span class="sxs-lookup"><span data-stu-id="d0751-146">The `SendMail` activity copies the contents of this file to its body property.</span></span><br /><br /> <span data-ttu-id="d0751-147">テンプレートは、tokens プロパティの内容によって置き換えられるトークンを含めることができます。</span><span class="sxs-lookup"><span data-stu-id="d0751-147">The template can contain tokens that are replaced by the contents of the tokens property.</span></span>|  
|<span data-ttu-id="d0751-148">TestMailTo</span><span class="sxs-lookup"><span data-stu-id="d0751-148">TestMailTo</span></span>|<xref:System.Net.Mail.MailAddress>|<span data-ttu-id="d0751-149">このプロパティを設定すると、すべての電子メールが、その中に指定されたアドレスに送信されます。</span><span class="sxs-lookup"><span data-stu-id="d0751-149">When this property is set, all emails are sent to the address specified in it.</span></span><br /><br /> <span data-ttu-id="d0751-150">このプロパティは、ワークフローをテストするときに使用するためのものです。</span><span class="sxs-lookup"><span data-stu-id="d0751-150">This property is intended to be used when testing workflows.</span></span> <span data-ttu-id="d0751-151">たとえば、すべての電子メールが実際の受信者に送信されることなく送信されるようにする場合です。</span><span class="sxs-lookup"><span data-stu-id="d0751-151">For example, when you want to make sure that all emails are sent without sending them to the actual recipients.</span></span>|  
|<span data-ttu-id="d0751-152">TestDropPath</span><span class="sxs-lookup"><span data-stu-id="d0751-152">TestDropPath</span></span>|<span data-ttu-id="d0751-153">文字列型</span><span class="sxs-lookup"><span data-stu-id="d0751-153">String</span></span>|<span data-ttu-id="d0751-154">このプロパティが設定されている場合、すべての電子メールも指定したファイルに保存されます。</span><span class="sxs-lookup"><span data-stu-id="d0751-154">When this property is set, all emails are also saved in the specified file.</span></span><br /><br /> <span data-ttu-id="d0751-155">このプロパティは、ワークフローをテストまたはデバッグするときに使用することを目的としており、送信メールの形式と内容が適切であることを確認します。</span><span class="sxs-lookup"><span data-stu-id="d0751-155">This property is intended to be used when you are testing or debugging workflows, to make sure that the format and contents of the outgoing emails is appropriate.</span></span>|  
  
## <a name="solution-contents"></a><span data-ttu-id="d0751-156">ソリューションのコンテンツ</span><span class="sxs-lookup"><span data-stu-id="d0751-156">Solution Contents</span></span>  

 <span data-ttu-id="d0751-157">ソリューションには、次の 2 つのプロジェクトが含まれています。</span><span class="sxs-lookup"><span data-stu-id="d0751-157">The solution contains two projects.</span></span>  
  
|<span data-ttu-id="d0751-158">プロジェクト</span><span class="sxs-lookup"><span data-stu-id="d0751-158">Project</span></span>|<span data-ttu-id="d0751-159">説明</span><span class="sxs-lookup"><span data-stu-id="d0751-159">Description</span></span>|<span data-ttu-id="d0751-160">重要なファイル</span><span class="sxs-lookup"><span data-stu-id="d0751-160">Important Files</span></span>|  
|-------------|-----------------|---------------------|  
|<span data-ttu-id="d0751-161">SendMail</span><span class="sxs-lookup"><span data-stu-id="d0751-161">SendMail</span></span>|<span data-ttu-id="d0751-162">SendMail アクティビティ</span><span class="sxs-lookup"><span data-stu-id="d0751-162">The SendMail activity</span></span>|<span data-ttu-id="d0751-163">1. SendMail.cs: メインアクティビティの実装</span><span class="sxs-lookup"><span data-stu-id="d0751-163">1.  SendMail.cs: implementation for the main activity</span></span><br /><span data-ttu-id="d0751-164">2. SendMailDesigner .xaml and SendMailDesigner.xaml.cs: SendMail アクティビティのデザイナー</span><span class="sxs-lookup"><span data-stu-id="d0751-164">2.  SendMailDesigner.xaml and SendMailDesigner.xaml.cs: designer for the SendMail activity</span></span><br /><span data-ttu-id="d0751-165">3. MailTemplateBody.htm: 送信する電子メールのテンプレート。</span><span class="sxs-lookup"><span data-stu-id="d0751-165">3.  MailTemplateBody.htm: template for the email to be sent out.</span></span>|  
|<span data-ttu-id="d0751-166">SendMailTestClient</span><span class="sxs-lookup"><span data-stu-id="d0751-166">SendMailTestClient</span></span>|<span data-ttu-id="d0751-167">SendMail アクティビティをテストするクライアント。</span><span class="sxs-lookup"><span data-stu-id="d0751-167">Client to test the SendMail activity.</span></span>  <span data-ttu-id="d0751-168">このプロジェクトでは、SendMail アクティビティを宣言的に起動する方法とプログラムで起動する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d0751-168">This project demonstrates two ways of invoking the SendMail activity: declaratively, and programmatically.</span></span>|<span data-ttu-id="d0751-169">1. Sequence1: SendMail アクティビティを呼び出すワークフロー。</span><span class="sxs-lookup"><span data-stu-id="d0751-169">1.  Sequence1.xaml: workflow that invokes the SendMail activity.</span></span><br /><span data-ttu-id="d0751-170">2. Program.cs: Sequence1 を呼び出し、SendMail を使用するプログラムによってワークフローを作成します。</span><span class="sxs-lookup"><span data-stu-id="d0751-170">2.  Program.cs: invokes Sequence1 and also creates a workflow programmatically that uses SendMail.</span></span>|  
  
## <a name="further-configuration-of-the-sendmail-activity"></a><span data-ttu-id="d0751-171">SendMail アクティビティの追加構成</span><span class="sxs-lookup"><span data-stu-id="d0751-171">Further configuration of the SendMail activity</span></span>  

 <span data-ttu-id="d0751-172">サンプルには表示されませんが、SendMail アクティビティの追加構成を実行できます。</span><span class="sxs-lookup"><span data-stu-id="d0751-172">Although not shown in the sample, users can perform addition configuration of the SendMail activity.</span></span> <span data-ttu-id="d0751-173">次の 3 つのセクションは、その方法を示しています。</span><span class="sxs-lookup"><span data-stu-id="d0751-173">The next three sections demonstrate how this is done.</span></span>  
  
### <a name="sending-an-email-using-tokens-specified-in-the-body"></a><span data-ttu-id="d0751-174">本文で指定されたトークンを使用した電子メールの送信</span><span class="sxs-lookup"><span data-stu-id="d0751-174">Sending an email using tokens specified in the body</span></span>  

 <span data-ttu-id="d0751-175">次のコード スニペットでは、本文のトークンを使用して電子メールを送信する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d0751-175">This code snippet demonstrates how you can send email with tokens in the body.</span></span> <span data-ttu-id="d0751-176">トークンが body プロパティに指定されていることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="d0751-176">Notice how the tokens are provided in the body property.</span></span> <span data-ttu-id="d0751-177">それらのトークンの値は、tokens プロパティに指定されています。</span><span class="sxs-lookup"><span data-stu-id="d0751-177">Values for those tokens are provided to the tokens property.</span></span>  
  
```csharp  
IDictionary<string, string> tokens = new Dictionary<string, string>();  
tokens.Add("@name", "John Doe");  
tokens.Add("@date", DateTime.Now.ToString());  
tokens.Add("@server", "localhost");  
  
new SendMail  
{  
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Body = "Hello @name. This is a test email sent from @server. Current date is @date",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens)  
};  
```  
  
### <a name="sending-an-email-using-a-template"></a><span data-ttu-id="d0751-178">テンプレートを使用した電子メールの送信</span><span class="sxs-lookup"><span data-stu-id="d0751-178">Sending an email using a template</span></span>  

 <span data-ttu-id="d0751-179">次のスニペットでは、本文のテンプレート トークンを使用して電子メールを送信する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="d0751-179">This snippet shows how to send an email using a template tokens in the body.</span></span> <span data-ttu-id="d0751-180">`BodyTemplateFilePath` プロパティを設定するときに、Body プロパティの値を指定する必要がないことに注目してください (テンプレート ファイルのコンテンツは本文にコピーされます)。</span><span class="sxs-lookup"><span data-stu-id="d0751-180">Notice that when setting the `BodyTemplateFilePath` property we don’t need to provide the value for Body property (the contents of the template file will be copied to the body).</span></span>  
  
```csharp  
new SendMail  
{
    From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
    To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
    Subject = "Test email",  
    Host = "localhost",  
    Port = 25,  
    Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
    BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",
};  
```  
  
### <a name="sending-mails-in-testing-mode"></a><span data-ttu-id="d0751-181">テスト モードでの電子メールの送信</span><span class="sxs-lookup"><span data-stu-id="d0751-181">Sending Mails in Testing Mode</span></span>  

 <span data-ttu-id="d0751-182">このコードスニペットは、2つのテストプロパティを設定する方法を示しています。をに設定すると `TestMailTo` 、すべてのメッセージがに送信されます `john.doe@contoso.con` (To、Cc、Bcc の値には関係ありません)。</span><span class="sxs-lookup"><span data-stu-id="d0751-182">This code snippet shows how to set the two testing properties: by setting `TestMailTo` to all messages will be sent to `john.doe@contoso.con` (without regard of the values of To, Cc, Bcc).</span></span> <span data-ttu-id="d0751-183">TestDropPath を設定すると、送信するすべての電子メールは、指定したパスにも記録されます。</span><span class="sxs-lookup"><span data-stu-id="d0751-183">By setting TestDropPath all outgoing emails will be also recorded in the provided path.</span></span> <span data-ttu-id="d0751-184">これらのプロパティは、個別に設定できます (関連していません)。</span><span class="sxs-lookup"><span data-stu-id="d0751-184">These properties can be set independently (they are not related).</span></span>  
  
```csharp  
new SendMail  
{
   From = new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   To = new LambdaValue<MailAddressCollection>(  
                    ctx => new MailAddressCollection() { new MailAddress("someone@microsoft.com") }),  
   Subject = "Test email",  
   Host = "localhost",  
   Port = 25,  
   Tokens = new LambdaValue<IDictionary<string, string>>(ctx => tokens),  
   BodyTemplateFilePath = @"..\..\..\SendMail\Templates\MailTemplateBody.htm",  
   TestMailTo= new LambdaValue<MailAddress>(ctx => new MailAddress("john.doe@contoso.com")),  
   TestDropPath = @"c:\Samples\SendMail\TestDropPath\",  
};  
```  
  
## <a name="set-up-instructions"></a><span data-ttu-id="d0751-185">セットアップ手順</span><span class="sxs-lookup"><span data-stu-id="d0751-185">Set-Up Instructions</span></span>  

 <span data-ttu-id="d0751-186">このサンプルでは SMTP サーバーにアクセスする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0751-186">Access to a SMTP server is required for this sample.</span></span>  
  
 <span data-ttu-id="d0751-187">SMTP サーバーの設定の詳細については、次のリンクを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0751-187">For more information about setting up a SMTP server, see the following links.</span></span>  
  
- <span data-ttu-id="d0751-188">[SMTP サービス (IIS 6.0) の構成](/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="d0751-188">[Configuring the SMTP Service (IIS 6.0)](/previous-versions/windows/it-pro/windows-server-2003/cc784968(v=ws.10))</span></span>  
  
- <span data-ttu-id="d0751-189">[IIS 7.0: SMTP 電子メールの構成](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span><span class="sxs-lookup"><span data-stu-id="d0751-189">[IIS 7.0: Configure SMTP E-Mail](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772058(v=ws.10))</span></span>  
  
- <span data-ttu-id="d0751-190">[SMTP サービスをインストールする方法](/previous-versions/tn-archive/aa997480(v=exchg.65))</span><span class="sxs-lookup"><span data-stu-id="d0751-190">[How to Install the SMTP Service](/previous-versions/tn-archive/aa997480(v=exchg.65))</span></span>  
  
 <span data-ttu-id="d0751-191">ダウンロードには、サードパーティで提供されている SMTP エミュレーターを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d0751-191">SMTP emulators provided by third parties are available for download.</span></span>  
  
##### <a name="to-run-this-sample"></a><span data-ttu-id="d0751-192">このサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="d0751-192">To run this sample</span></span>  
  
1. <span data-ttu-id="d0751-193">Visual Studio 2010 を使用して、SendMail のソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="d0751-193">Using Visual Studio 2010, open the SendMail.sln solution file.</span></span>  
  
2. <span data-ttu-id="d0751-194">有効な SMTP サーバーへのアクセス権があることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d0751-194">Ensure that you have access to a valid SMTP server.</span></span> <span data-ttu-id="d0751-195">セットアップ手順を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d0751-195">See the set-up instructions.</span></span>  
  
3. <span data-ttu-id="d0751-196">サーバーアドレス、差出人、および宛先の電子メールアドレスを使用して、プログラムを構成します。</span><span class="sxs-lookup"><span data-stu-id="d0751-196">Configure the program with your server address, and From and To email addresses.</span></span>  
  
     <span data-ttu-id="d0751-197">このサンプルを正しく実行するには、From および To 電子メールアドレスの値と Program.cs の SMTP サーバーのアドレスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0751-197">To correctly run this sample, you may need to configure the value of From and To email addresses and the address of the SMTP server in  Program.cs and in Sequence.xaml.</span></span> <span data-ttu-id="d0751-198">プログラムでは電子メールが 2 つの方法で送信されるため、両方の場所でアドレスを変更する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d0751-198">You will need to change the address in both locations since the program sends mail in two different ways</span></span>  
  
4. <span data-ttu-id="d0751-199">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d0751-199">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
5. <span data-ttu-id="d0751-200">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="d0751-200">To run the solution, press CTRL+F5.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d0751-201">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="d0751-201">The samples may already be installed on your machine.</span></span> <span data-ttu-id="d0751-202">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="d0751-202">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="d0751-203">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="d0751-203">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="d0751-204">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="d0751-204">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\ActivityLibrary\SendMail`
