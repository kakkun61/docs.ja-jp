---
title: '方法: クライアントの資格情報の種類を指定する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security credentials, adding to SOAP messages
- WCF, security
ms.assetid: 10f51bee-5f92-4c1a-9126-fa5418535d8f
ms.openlocfilehash: b45d7b58d8a1fe79f9d7a8cff6e328b46633985c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96293677"
---
# <a name="how-to-specify-the-client-credential-type"></a><span data-ttu-id="74b6a-102">方法: クライアントの資格情報の種類を指定する</span><span class="sxs-lookup"><span data-stu-id="74b6a-102">How to: Specify the Client Credential Type</span></span>

<span data-ttu-id="74b6a-103">セキュリティ モード (トランスポートまたはメッセージ) を設定してから、クライアント資格情報の種類を指定することができます。</span><span class="sxs-lookup"><span data-stu-id="74b6a-103">After setting a security mode (either transport or message), you have the option of setting the client credential type.</span></span> <span data-ttu-id="74b6a-104">このプロパティでは、クライアントが認証時にサービスに提供する必要のある資格情報の種類を指定します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-104">This property specifies what type of credential the client must provide to the service for authentication.</span></span> <span data-ttu-id="74b6a-105">セキュリティモード (クライアント資格情報の種類を設定する前に必要な手順) の設定の詳細については、「 [方法: セキュリティモードを設定する](how-to-set-the-security-mode.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="74b6a-105">For more information about setting the security mode (a necessary step before setting the client credential type), see [How to: Set the Security Mode](how-to-set-the-security-mode.md).</span></span>  
  
### <a name="to-set-the-client-credential-type-in-code"></a><span data-ttu-id="74b6a-106">コードでクライアント資格情報の種類を設定するには</span><span class="sxs-lookup"><span data-stu-id="74b6a-106">To set the client credential type in code</span></span>  
  
1. <span data-ttu-id="74b6a-107">サービスで使用されるバインドのインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-107">Create an instance of the binding that the service will use.</span></span> <span data-ttu-id="74b6a-108">この例では、<xref:System.ServiceModel.WSHttpBinding> バインドを使用します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-108">This example uses the <xref:System.ServiceModel.WSHttpBinding> binding.</span></span>  
  
2. <span data-ttu-id="74b6a-109"><xref:System.ServiceModel.WSHttpSecurity.Mode%2A> プロパティに適切な値を設定します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-109">Set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to an appropriate value.</span></span> <span data-ttu-id="74b6a-110">この例では、メッセージ モードを使用します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-110">This example uses the Message mode.</span></span>  
  
3. <span data-ttu-id="74b6a-111"><xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> プロパティに適切な値を設定します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-111">Set the <xref:System.ServiceModel.MessageSecurityOverHttp.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="74b6a-112">この例では、Windows 認証 (<xref:System.ServiceModel.MessageCredentialType.Windows>) を使用するように設定します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-112">This example sets it to use Windows authentication (<xref:System.ServiceModel.MessageCredentialType.Windows>).</span></span>  
  
     [!code-csharp[c_ProgrammingSecurity#14](../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#14)]
     [!code-vb[c_ProgrammingSecurity#14](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#14)]  
  
### <a name="to-set-the-client-credential-type-in-configuration"></a><span data-ttu-id="74b6a-113">構成でクライアント資格情報の種類を設定するには</span><span class="sxs-lookup"><span data-stu-id="74b6a-113">To set the client credential type in configuration</span></span>  
  
1. <span data-ttu-id="74b6a-114">[\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md)構成ファイルに要素を追加します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-114">Add a [\<system.serviceModel>](../configure-apps/file-schema/wcf/system-servicemodel.md) element to the configuration file.</span></span>  
  
2. <span data-ttu-id="74b6a-115">子要素として、要素を追加し [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) ます。</span><span class="sxs-lookup"><span data-stu-id="74b6a-115">As a child element, add a [\<bindings>](../configure-apps/file-schema/wcf/bindings.md) element.</span></span>  
  
3. <span data-ttu-id="74b6a-116">適切なバインドを追加します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-116">Add an appropriate binding.</span></span> <span data-ttu-id="74b6a-117">この例では、要素を使用 [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-117">This example uses the [\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md) element.</span></span>  
  
4. <span data-ttu-id="74b6a-118">要素を追加 [\<binding>](../configure-apps/file-schema/wcf/bindings.md) し、 `name` 属性を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-118">Add a [\<binding>](../configure-apps/file-schema/wcf/bindings.md) element and set the `name` attribute to an appropriate value.</span></span> <span data-ttu-id="74b6a-119">この例では、"SecureBinding" という名前を使用します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-119">This example uses the name "SecureBinding".</span></span>  
  
5. <span data-ttu-id="74b6a-120">`<security>` バインドを追加します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-120">Add a `<security>` binding.</span></span> <span data-ttu-id="74b6a-121">`mode` 属性を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-121">Set the `mode` attribute to an appropriate value.</span></span> <span data-ttu-id="74b6a-122">この例では、`"Message"` に設定します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-122">This example sets it to `"Message"`.</span></span>  
  
6. <span data-ttu-id="74b6a-123">セキュリティ モードによって、`<message>` 要素と `<transport>` 要素のどちらかを追加します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-123">Add either a `<message>` or `<transport>` element, as determined by the security mode.</span></span> <span data-ttu-id="74b6a-124">`clientCredentialType` 属性を適切な値に設定します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-124">Set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="74b6a-125">この例では、`"Windows"` を使用します。</span><span class="sxs-lookup"><span data-stu-id="74b6a-125">This example uses `"Windows"`.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="SecureBinding">  
            <security mode="Message">  
                 <message clientCredentialType="Windows" />  
             </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
    </system.serviceModel>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="74b6a-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="74b6a-126">See also</span></span>

- [<span data-ttu-id="74b6a-127">サービスのセキュリティ保護</span><span class="sxs-lookup"><span data-stu-id="74b6a-127">Securing Services</span></span>](securing-services.md)
- [<span data-ttu-id="74b6a-128">方法: セキュリティ モードを設定する</span><span class="sxs-lookup"><span data-stu-id="74b6a-128">How to: Set the Security Mode</span></span>](how-to-set-the-security-mode.md)
