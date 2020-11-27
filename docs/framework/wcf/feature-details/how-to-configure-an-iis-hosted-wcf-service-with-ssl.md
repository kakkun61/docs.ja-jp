---
title: '方法: IIS でホストされる WCF サービスに SSL を構成する'
description: Iis でホストされる WCF サービスで HTTP トランスポートセキュリティを使用するように設定する方法について説明します。これには、IIS に登録されている証明書が必要です。
ms.date: 03/30/2017
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
ms.openlocfilehash: 960005761d3bed917142141976e9f9094094b34c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96257653"
---
# <a name="how-to-configure-an-iis-hosted-wcf-service-with-ssl"></a><span data-ttu-id="e244f-103">方法: IIS でホストされる WCF サービスに SSL を構成する</span><span class="sxs-lookup"><span data-stu-id="e244f-103">How to: Configure an IIS-hosted WCF service with SSL</span></span>

<span data-ttu-id="e244f-104">ここでは、HTTP トランスポート セキュリティを使用するように IIS でホストされる WCF サービスをセットアップする方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="e244f-104">This topic describes how to set up an IIS-hosted WCF service to use HTTP transport security.</span></span> <span data-ttu-id="e244f-105">HTTP トランスポート セキュリティを使用するには、SSL 証明書が IIS に登録されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e244f-105">HTTP transport security requires an SSL certificate to be registered with IIS.</span></span> <span data-ttu-id="e244f-106">SSL 証明書がない場合は、IIS を使用してテスト証明書を生成できます。</span><span class="sxs-lookup"><span data-stu-id="e244f-106">If you do not have an SSL certificate you can use IIS to generate a test certificate.</span></span> <span data-ttu-id="e244f-107">次に、Web サイトに SSL バインディングを追加し、Web サイトの認証プロパティを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e244f-107">Next you must add an SSL binding to the web site and configure the web site’s authentication properties.</span></span> <span data-ttu-id="e244f-108">最後に、HTTPS を使用するように WCF サービスを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e244f-108">Finally you need to configure the WCF service to use HTTPS.</span></span>  
  
### <a name="creating-a-self-signed-certificate"></a><span data-ttu-id="e244f-109">自己署名証明書の作成</span><span class="sxs-lookup"><span data-stu-id="e244f-109">Creating a Self-Signed Certificate</span></span>  
  
1. <span data-ttu-id="e244f-110">インターネット インフォメーション サービス マネージャー (inetmgr.exe) を開き、左側のツリー ビューでコンピューター名を選択します。</span><span class="sxs-lookup"><span data-stu-id="e244f-110">Open Internet Information Services Manager (inetmgr.exe), and select your computer name in the left-hand tree view.</span></span> <span data-ttu-id="e244f-111">画面の右側で [サーバー証明書] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e244f-111">On the right-hand side of the screen select Server Certificates</span></span>  
  
     <span data-ttu-id="e244f-112">![IIS マネージャー ホーム画面](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span><span class="sxs-lookup"><span data-stu-id="e244f-112">![IIS Manager Home Screen](media/mg-inetmgrhome.jpg "mg_INetMgrHome")</span></span>  
  
2. <span data-ttu-id="e244f-113">[サーバー証明書] ウィンドウで、[ **Create Self-Signed Certificate...** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e244f-113">In the Server Certificates window click the **Create Self-Signed Certificate….**</span></span> <span data-ttu-id="e244f-114">リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e244f-114">Link.</span></span>  
  
     <span data-ttu-id="e244f-115">![IIS での自己&#45;署名入り証明書の作成](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span><span class="sxs-lookup"><span data-stu-id="e244f-115">![Creating a self&#45;signed certificate with IIS](media/mg-createselfsignedcert.jpg "mg_CreateSelfSignedCert")</span></span>  
  
3. <span data-ttu-id="e244f-116">自己署名証明書のフレンドリ名を入力し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e244f-116">Enter a friendly name for the self-signed certificate and click **OK**.</span></span>  
  
     <span data-ttu-id="e244f-117">![自己&#45;署名入り証明書の作成ダイアログ](media/mg-mycert.jpg "mg_MyCert")</span><span class="sxs-lookup"><span data-stu-id="e244f-117">![Create Self&#45;Signed Certificate Dialog](media/mg-mycert.jpg "mg_MyCert")</span></span>  
  
     <span data-ttu-id="e244f-118">新しく作成された自己署名証明書の詳細が [ **サーバー証明書** ] ウィンドウに表示されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e244f-118">The newly created self-signed certificate details are now shown in the **Server Certificates** window.</span></span>  
  
     <span data-ttu-id="e244f-119">![[サーバー証明書] ウィンドウ](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span><span class="sxs-lookup"><span data-stu-id="e244f-119">![Server Certificate Window](media/mg-servercertificatewindow.jpg "mg_ServerCertificateWindow")</span></span>  
  
     <span data-ttu-id="e244f-120">生成された証明書が、信頼されたルート証明機関ストアにインストールされます。</span><span class="sxs-lookup"><span data-stu-id="e244f-120">The generated certificate is installed in the Trusted Root Certification Authorities store.</span></span>  
  
### <a name="add-ssl-binding"></a><span data-ttu-id="e244f-121">SSL バインドの追加</span><span class="sxs-lookup"><span data-stu-id="e244f-121">Add SSL Binding</span></span>  
  
1. <span data-ttu-id="e244f-122">引き続きインターネットインフォメーションサービスマネージャーで、[ **サイト** ] フォルダーを展開し、画面の左側にあるツリービューの [ **既定の Web サイト** ] フォルダーを展開します。</span><span class="sxs-lookup"><span data-stu-id="e244f-122">Still in Internet Information Services Manager, expand the **Sites** folder and then the **Default Web Site** folder in the tree view on the left-hand side of the screen.</span></span>  
  
2. <span data-ttu-id="e244f-123">[**バインド...** ] をクリックします。</span><span class="sxs-lookup"><span data-stu-id="e244f-123">Click the **Bindings….**</span></span> <span data-ttu-id="e244f-124">ウィンドウの右上隅にある [ **アクション** ] セクションのリンク。</span><span class="sxs-lookup"><span data-stu-id="e244f-124">Link in the **Actions** section in the upper right hand portion of the window.</span></span>  
  
     <span data-ttu-id="e244f-125">![SSL バインディングの追加](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span><span class="sxs-lookup"><span data-stu-id="e244f-125">![Adding an SSL binding](media/mg-addsslbinding.jpg "mg_AddSSLBinding")</span></span>  
  
3. <span data-ttu-id="e244f-126">[サイトバインド] ウィンドウで、[ **追加** ] ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e244f-126">In the Site Bindings window click the **Add** button.</span></span>  
  
     <span data-ttu-id="e244f-127">![[サイト バインド] ダイアログ](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span><span class="sxs-lookup"><span data-stu-id="e244f-127">![Site Bindings Dialog](media/mg-sitebindingsdialog.jpg "mg_SiteBindingsDialog")</span></span>  
  
4. <span data-ttu-id="e244f-128">[ **サイトバインドの追加** ] ダイアログで、[種類] に [https] を、先ほど作成した自己署名証明書のフレンドリ名を選択します。</span><span class="sxs-lookup"><span data-stu-id="e244f-128">In the **Add Site Binding** dialog, select https for the type and the friendly name of the self-signed certificate you just created.</span></span>  
  
     <span data-ttu-id="e244f-129">![サイト バインディングの例](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span><span class="sxs-lookup"><span data-stu-id="e244f-129">![Site binding example](media/mg-mycertbinding.jpg "mg_MyCertBinding")</span></span>  
  
### <a name="configure-virtual-directory-for-ssl"></a><span data-ttu-id="e244f-130">SSL の仮想ディレクトリの構成</span><span class="sxs-lookup"><span data-stu-id="e244f-130">Configure Virtual Directory for SSL</span></span>  
  
1. <span data-ttu-id="e244f-131">インターネット インフォメーション サービス マネージャーで、WCF のセキュリティで保護されたサービスが含まれている仮想ディレクトリを選択します。</span><span class="sxs-lookup"><span data-stu-id="e244f-131">Still in Internet Information Services Manager, select the virtual directory that contains your WCF secure service.</span></span>  
  
2. <span data-ttu-id="e244f-132">ウィンドウの中央のウィンドウで、[IIS] セクションの [ **SSL 設定** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="e244f-132">In the center pane of the window, select **SSL Settings** in the IIS section.</span></span>  
  
     <span data-ttu-id="e244f-133">![仮想ディレクトリの SSL 設定](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span><span class="sxs-lookup"><span data-stu-id="e244f-133">![SSL Settings for virtual directory](media/mg-sslsettingsforvdir.jpg "mg_SSLSettingsForVDir")</span></span>  
  
3. <span data-ttu-id="e244f-134">[SSL 設定] ウィンドウで、[ **Ssl が必要**] チェックボックスをオンにし、画面の右側の [**アクション**] セクションの [**適用**] リンクをクリックします。</span><span class="sxs-lookup"><span data-stu-id="e244f-134">In the SSL Settings pane, select the **Require SSL** checkbox and click the **Apply** link in the **Actions** section on the right hand side of the screen.</span></span>  
  
     <span data-ttu-id="e244f-135">![仮想ディレクトリの SSL 設定](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span><span class="sxs-lookup"><span data-stu-id="e244f-135">![Virtual directory SSL settings](media/mg-vdirsslsettings.JPG "mg_VDirSSLSettings")</span></span>  
  
### <a name="configure-wcf-service-for-http-transport-security"></a><span data-ttu-id="e244f-136">HTTP トランスポート セキュリティのための WCF サービスの構成</span><span class="sxs-lookup"><span data-stu-id="e244f-136">Configure WCF Service for HTTP Transport Security</span></span>  
  
1. <span data-ttu-id="e244f-137">WCF サービスの Web.config で、次の XML に示すように、トランスポート セキュリティを使用するよう HTTP バインドを構成します。</span><span class="sxs-lookup"><span data-stu-id="e244f-137">In the WCF service’s web.config configure the HTTP binding to use transport security as shown in the following XML.</span></span>  
  
    ```xml  
    <bindings>  
          <basicHttpBinding>  
            <binding name="secureHttpBinding">  
              <security mode="Transport">  
                <transport clientCredentialType="None"/>  
              </security>  
            </binding>  
          </basicHttpBinding>  
    </bindings>  
    ```  
  
2. <span data-ttu-id="e244f-138">次の XML に示すように、サービスとサービス エンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="e244f-138">Specify your service and service endpoint as shown in the following XML.</span></span>  
  
    ```xml  
    <services>  
          <service name="MySecureWCFService.Service1">  
            <endpoint address=""  
                      binding="basicHttpBinding"  
                      bindingConfiguration="secureHttpBinding"  
                      contract="MySecureWCFService.IService1"/>  
  
            <endpoint address="mex"  
                      binding="mexHttpsBinding"  
                      contract="IMetadataExchange" />  
          </service>  
    </services>  
    ```  
  
## <a name="example"></a><span data-ttu-id="e244f-139">例</span><span class="sxs-lookup"><span data-stu-id="e244f-139">Example</span></span>  

 <span data-ttu-id="e244f-140">次は、HTTP トランスポート セキュリティを使用した WCF サービスの web.config ファイルの詳細な例です。</span><span class="sxs-lookup"><span data-stu-id="e244f-140">The following is a complete example of a web.config file for a WCF service using HTTP transport security</span></span>  
  
```xml  
<?xml version="1.0"?>  
<configuration>  
  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <services>  
      <service name="MySecureWCFService.Service1">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="secureHttpBinding"  
                  contract="MySecureWCFService.IService1"/>  
  
        <endpoint address="mex"  
                  binding="mexHttpsBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="secureHttpBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <!-- To avoid disclosing metadata information, set the value below to false and remove the metadata endpoint above before deployment -->  
          <serviceMetadata httpsGetEnabled="true"/>  
          <!-- To receive exception details in faults for debugging purposes, set the value below to true.  Set to false before deployment to avoid disclosing exception information -->  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
  </system.serviceModel>  
  <system.webServer>  
    <modules runAllManagedModulesForAllRequests="true"/>  
  </system.webServer>  
  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e244f-141">関連項目</span><span class="sxs-lookup"><span data-stu-id="e244f-141">See also</span></span>

- [<span data-ttu-id="e244f-142">インターネット インフォメーション サービスでのホスティング</span><span class="sxs-lookup"><span data-stu-id="e244f-142">Hosting in Internet Information Services</span></span>](hosting-in-internet-information-services.md)
- [<span data-ttu-id="e244f-143">インターネット インフォメーション サービスのホスティング手順</span><span class="sxs-lookup"><span data-stu-id="e244f-143">Internet Information Service Hosting Instructions</span></span>](../samples/internet-information-service-hosting-instructions.md)
- [<span data-ttu-id="e244f-144">インターネット インフォメーション サービス ホスティングのベスト プラクティス</span><span class="sxs-lookup"><span data-stu-id="e244f-144">Internet Information Services Hosting Best Practices</span></span>](internet-information-services-hosting-best-practices.md)
- [<span data-ttu-id="e244f-145">インライン コードを使用した IIS ホスティング</span><span class="sxs-lookup"><span data-stu-id="e244f-145">IIS Hosting Using Inline Code</span></span>](../samples/iis-hosting-using-inline-code.md)
