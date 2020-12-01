---
title: インターネット認証
description: .NET Framework でアプリケーションに対して System.Net クラスがサポートする、さまざまなクライアント認証メカニズムについて学習します。
ms.date: 03/30/2017
helpviewer_keywords:
- authentication [.NET Framework], classes
- IAuthenticationModule interface
- ICredentialLookup interface
- CredentialCache class, about CredentialCache class
- receiving data, authentication
- AuthenticationManager class, about AuthenticationManager class
- Internet, authentication
- sending data, authentication
- network resources, authentication
- user authentication, classes for authentication
- NetworkCredential class, about NetworkCredential class
- client authentication, classes for authentication
ms.assetid: d342e87c-f672-4660-a513-41a2f2b80c4a
ms.openlocfilehash: 085ca27dd0cfedc90211b21c10cc8bc5cf1ecd21
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96241591"
---
# <a name="internet-authentication"></a><span data-ttu-id="8af97-103">インターネット認証</span><span class="sxs-lookup"><span data-stu-id="8af97-103">Internet Authentication</span></span>

<span data-ttu-id="8af97-104"><xref:System.Net> クラスは、さまざまなクライアント認証メカニズムをサポートしています。これには、基本、ダイジェスト、ネゴシエート、NTLM、および Kerberos の標準のインターネット認証方法の他に、ユーザーが作成できるカスタム メソッドも含まれます。</span><span class="sxs-lookup"><span data-stu-id="8af97-104">The <xref:System.Net> classes support a variety of client authentication mechanisms, including the standard Internet authentication methods basic, digest, negotiate, NTLM, and Kerberos authentication, as well as custom methods that you can create.</span></span>  
  
 <span data-ttu-id="8af97-105">認証の資格情報は、<xref:System.Net.ICredentials> インターフェイスを実装する <xref:System.Net.NetworkCredential> クラスと <xref:System.Net.CredentialCache> クラスに格納されています。</span><span class="sxs-lookup"><span data-stu-id="8af97-105">Authentication credentials are stored in the <xref:System.Net.NetworkCredential> and <xref:System.Net.CredentialCache> classes, which implement the <xref:System.Net.ICredentials> interface.</span></span> <span data-ttu-id="8af97-106">資格情報についてこれらのいずれかのクラスが照会されると、そのクラスが **NetworkCredential** クラスのインスタンスを返します。</span><span class="sxs-lookup"><span data-stu-id="8af97-106">When one of these classes is queried for credentials, it returns an instance of the **NetworkCredential** class.</span></span> <span data-ttu-id="8af97-107">認証プロセスは <xref:System.Net.AuthenticationManager> クラスで管理され、実際の認証プロセスは <xref:System.Net.IAuthenticationModule> インターフェイスを実装する認証モジュール クラスによって実行されます。</span><span class="sxs-lookup"><span data-stu-id="8af97-107">The authentication process is managed by the <xref:System.Net.AuthenticationManager> class, and the actual authentication process is performed by an authentication module class that implements the <xref:System.Net.IAuthenticationModule> interface.</span></span> <span data-ttu-id="8af97-108">カスタム認証モジュールは、**AuthenticationManager** に登録してから使用する必要があります。基本、ダイジェスト、ネゴシエート、NTLM、および Kerberos の各認証方法は、既定で登録されています。</span><span class="sxs-lookup"><span data-stu-id="8af97-108">You must register a custom authentication module with the **AuthenticationManager** before it can be used; modules for the basic, digest, negotiate, NTLM, and Kerberos authentication methods are registered by default.</span></span>  
  
 <span data-ttu-id="8af97-109">**NetworkCredential** は、URI で識別される 1 つのインターネット リソースに関連付けられている一連の資格情報を格納し、<xref:System.Net.NetworkCredential.GetCredential%2A> メソッドへの任意の呼び出しに応答してそれらを返します。</span><span class="sxs-lookup"><span data-stu-id="8af97-109">**NetworkCredential** stores a set of credentials associated with a single Internet resource identified by a URI and returns them in response to any call to the <xref:System.Net.NetworkCredential.GetCredential%2A> method.</span></span> <span data-ttu-id="8af97-110">**NetworkCredential** クラスは通常、限定された数のインターネット リソースにアクセスするアプリケーション、またはどんな場合でも同じ資格情報のセットを使用するアプリケーションで使用されます。</span><span class="sxs-lookup"><span data-stu-id="8af97-110">The **NetworkCredential** class is typically used by applications that access a limited number of Internet resources or by applications that use the same set of credentials in all cases.</span></span>  
  
 <span data-ttu-id="8af97-111">**CredentialCache** クラスは、さまざまな Web リソースの資格情報のコレクションを格納します。</span><span class="sxs-lookup"><span data-stu-id="8af97-111">The **CredentialCache** class stores a collection of credentials for various Web resources.</span></span> <span data-ttu-id="8af97-112"><xref:System.Net.CredentialCache.GetCredential%2A> メソッドが呼び出されると、**CredentialCache** は、適切な資格情報のセットを返します。これは Web リソースの URI と要求された認証スキームによって決まります。</span><span class="sxs-lookup"><span data-stu-id="8af97-112">When the <xref:System.Net.CredentialCache.GetCredential%2A> method is called, **CredentialCache** returns the proper set of credentials, as determined by the URI of the Web resource and the requested authentication scheme.</span></span> <span data-ttu-id="8af97-113">異なる認証スキームでさまざまなインターネット リソースを使用するアプリケーションは、**CredentialCache** クラスを使用することでメリットが得られます。それは、このクラスがすべての資格情報を格納し、要求に応じてそれらを提供するからです。</span><span class="sxs-lookup"><span data-stu-id="8af97-113">Applications that use a variety of Internet resources with different authentication schemes benefit from using the **CredentialCache** class, since it stores all the credentials and provides them as requested.</span></span>  
  
 <span data-ttu-id="8af97-114">インターネット リソースが認証を要求すると、<xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> メソッドは資格情報の要求と共に <xref:System.Net.WebRequest> を **AuthenticationManager** に送信します。</span><span class="sxs-lookup"><span data-stu-id="8af97-114">When an Internet resource requests authentication, the <xref:System.Net.WebRequest.GetResponse%2A?displayProperty=nameWithType> method sends the <xref:System.Net.WebRequest> to the **AuthenticationManager** along with the request for credentials.</span></span> <span data-ttu-id="8af97-115">そして要求は、次のプロセスに従って認証されます。</span><span class="sxs-lookup"><span data-stu-id="8af97-115">The request is then authenticated according to the following process:</span></span>  
  
1. <span data-ttu-id="8af97-116">**AuthenticationManager** が登録済みの各認証モジュールで、登録された順番で <xref:System.Net.IAuthenticationModule.Authenticate%2A> メソッドを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="8af97-116">The **AuthenticationManager** calls the <xref:System.Net.IAuthenticationModule.Authenticate%2A> method on each of the registered authentication modules in the order they were registered.</span></span> <span data-ttu-id="8af97-117">**AuthenticationManager** は **null** を返さない 1 つ目のモジュールを使用して認証プロセスを実行します。</span><span class="sxs-lookup"><span data-stu-id="8af97-117">The **AuthenticationManager** uses the first module that does not return **null** to carry out the authentication process.</span></span> <span data-ttu-id="8af97-118">プロセスの詳細は、使用する認証モジュールの種類によって異なります。</span><span class="sxs-lookup"><span data-stu-id="8af97-118">The details of the process vary depending on the type of authentication module involved.</span></span>  
  
2. <span data-ttu-id="8af97-119">認証プロセスが完了すると、認証モジュールが <xref:System.Net.Authorization> をインターネット リソースにアクセスするために必要な情報を含む **WebRequest** に返します。</span><span class="sxs-lookup"><span data-stu-id="8af97-119">When the authentication process is complete, the authentication module returns an <xref:System.Net.Authorization> to the **WebRequest** that contains the information needed to access the Internet resource.</span></span>  
  
 <span data-ttu-id="8af97-120">一部の認証スキームでは、最初にリソースの要求を作成しなくても、ユーザーを認証することができます。</span><span class="sxs-lookup"><span data-stu-id="8af97-120">Some authentication schemes can authenticate a user without first making a request for a resource.</span></span> <span data-ttu-id="8af97-121">リソースでユーザーを事前認証することで、サーバーへのラウンド トリップを少なくとも 1 回減らせるため、アプリケーションが時間を節約できます。</span><span class="sxs-lookup"><span data-stu-id="8af97-121">An application can save time by preauthenticating the user with the resource, thus eliminating at least one round trip to the server.</span></span> <span data-ttu-id="8af97-122">または、後でユーザーへの応答性を高めるため、プログラムの起動中に認証を実行できます。</span><span class="sxs-lookup"><span data-stu-id="8af97-122">Or, it can perform authentication during program startup in order to be more responsive to the user later.</span></span> <span data-ttu-id="8af97-123">事前認証を使用できる認証スキームで <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> プロパティを **true** に設定します。</span><span class="sxs-lookup"><span data-stu-id="8af97-123">Authentication schemes that can use preauthentication set the <xref:System.Net.IAuthenticationModule.PreAuthenticate%2A> property to **true**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8af97-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="8af97-124">See also</span></span>

- [<span data-ttu-id="8af97-125">基本認証とダイジェスト認証</span><span class="sxs-lookup"><span data-stu-id="8af97-125">Basic and Digest Authentication</span></span>](basic-and-digest-authentication.md)
- [<span data-ttu-id="8af97-126">NTLM 認証および Kerberos 認証</span><span class="sxs-lookup"><span data-stu-id="8af97-126">NTLM and Kerberos Authentication</span></span>](ntlm-and-kerberos-authentication.md)
- [<span data-ttu-id="8af97-127">ネットワーク プログラミングにおけるセキュリティ</span><span class="sxs-lookup"><span data-stu-id="8af97-127">Security in Network Programming</span></span>](security-in-network-programming.md)
