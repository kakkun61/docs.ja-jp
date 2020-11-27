---
title: DataContractSerializer と DataContractResolver を使用した NetDataContractSerializer 機能の提供
ms.date: 03/30/2017
ms.assetid: 1376658f-f695-45f7-a7e0-94664e9619ff
ms.openlocfilehash: 002cd101ddf760e28a71ded0d6a7f4ee29a56c3b
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96253614"
---
# <a name="using-datacontractserializer-and-datacontractresolver-to-provide-the-functionality-of-netdatacontractserializer"></a><span data-ttu-id="27263-102">DataContractSerializer と DataContractResolver を使用した NetDataContractSerializer 機能の提供</span><span class="sxs-lookup"><span data-stu-id="27263-102">Using DataContractSerializer and DataContractResolver to Provide the Functionality of NetDataContractSerializer</span></span>

<span data-ttu-id="27263-103">このサンプルでは、<xref:System.Runtime.Serialization.DataContractSerializer> を適切な <xref:System.Runtime.Serialization.DataContractResolver> と共に使用して、<xref:System.Runtime.Serialization.NetDataContractSerializer> と同じ機能を提供する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="27263-103">This sample demonstrates how the use of <xref:System.Runtime.Serialization.DataContractSerializer> with an appropriate <xref:System.Runtime.Serialization.DataContractResolver> provides the same functionality as <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="27263-104">このサンプルで示すのは、<xref:System.Runtime.Serialization.DataContractResolver> を作成して <xref:System.Runtime.Serialization.DataContractSerializer> に追加する方法です。</span><span class="sxs-lookup"><span data-stu-id="27263-104">This sample shows how to create the appropriate <xref:System.Runtime.Serialization.DataContractResolver> and how to add it to the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>

## <a name="sample-details"></a><span data-ttu-id="27263-105">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="27263-105">Sample details</span></span>

 <span data-ttu-id="27263-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> は、1 つの重要な点で <xref:System.Runtime.Serialization.DataContractSerializer> とは異なります。<xref:System.Runtime.Serialization.NetDataContractSerializer> はシリアル化された XML の中に CLR 型情報を含みますが、<xref:System.Runtime.Serialization.DataContractSerializer> にはこの情報は含まれません。</span><span class="sxs-lookup"><span data-stu-id="27263-106"><xref:System.Runtime.Serialization.NetDataContractSerializer> differs from <xref:System.Runtime.Serialization.DataContractSerializer> in one important way: <xref:System.Runtime.Serialization.NetDataContractSerializer> includes CLR type information in the serialized XML, whereas <xref:System.Runtime.Serialization.DataContractSerializer> does not.</span></span> <span data-ttu-id="27263-107">したがって、<xref:System.Runtime.Serialization.NetDataContractSerializer> は、シリアル化と逆シリアル化の両方で、同一の CLR 型を共有する結果になる場合のみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="27263-107">Therefore, <xref:System.Runtime.Serialization.NetDataContractSerializer> can be used only if both the serializing and deserializing ends share the same CLR types.</span></span> <span data-ttu-id="27263-108">ただし、<xref:System.Runtime.Serialization.DataContractSerializer> よりも優れたパフォーマンスが得られるため、<xref:System.Runtime.Serialization.NetDataContractSerializer> を使用することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="27263-108">However, it is recommended to use <xref:System.Runtime.Serialization.DataContractSerializer> because its performance is better than <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span></span> <span data-ttu-id="27263-109"><xref:System.Runtime.Serialization.DataContractSerializer> を追加することによって、<xref:System.Runtime.Serialization.DataContractResolver> でシリアル化される情報を変更することができます。</span><span class="sxs-lookup"><span data-stu-id="27263-109">You can change the information that is serialized in <xref:System.Runtime.Serialization.DataContractSerializer> by adding a <xref:System.Runtime.Serialization.DataContractResolver> to it.</span></span>

 <span data-ttu-id="27263-110">このサンプルは、2 つのプロジェクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="27263-110">This sample consists of two projects.</span></span> <span data-ttu-id="27263-111">最初のプロジェクトでは、<xref:System.Runtime.Serialization.NetDataContractSerializer> を使用してオブジェクトをシリアル化します。</span><span class="sxs-lookup"><span data-stu-id="27263-111">The first project uses <xref:System.Runtime.Serialization.NetDataContractSerializer> to serialize an object.</span></span> <span data-ttu-id="27263-112">2 番目のプロジェクトでは、<xref:System.Runtime.Serialization.DataContractSerializer> を <xref:System.Runtime.Serialization.DataContractResolver> と共に使用して、最初のプロジェクトと同じ機能を提供します。</span><span class="sxs-lookup"><span data-stu-id="27263-112">The second project uses <xref:System.Runtime.Serialization.DataContractSerializer> with a <xref:System.Runtime.Serialization.DataContractResolver> to provide the same functionality as the first project.</span></span>

 <span data-ttu-id="27263-113">次のコード例では、DCSwithDCR プロジェクトの <xref:System.Runtime.Serialization.DataContractResolver> に追加される `MyDataContractResolver` という名前のカスタム <xref:System.Runtime.Serialization.DataContractSerializer> の実装を示します。</span><span class="sxs-lookup"><span data-stu-id="27263-113">The following code example shows the implementation of a custom <xref:System.Runtime.Serialization.DataContractResolver> named `MyDataContractResolver` that is added to the <xref:System.Runtime.Serialization.DataContractSerializer> in the DCSwithDCR project.</span></span>

```csharp
class MyDataContractResolver : DataContractResolver
{
    private XmlDictionary dictionary = new XmlDictionary();

    public MyDataContractResolver()
    {
    }

    // Used at deserialization
    // Allows users to map xsi:type name to any Type
    public override Type ResolveName(string typeName, string typeNamespace, DataContractResolver knownTypeResolver)
    {
        Type type = knownTypeResolver.ResolveName(typeName, typeNamespace, null);
        type ??= Type.GetType(typeName + ", " + typeNamespace);
        return type;
    }

    // Used at serialization
    // Maps any Type to a new xsi:type representation
    public override void ResolveType(Type dataContractType, DataContractResolver knownTypeResolver, out XmlDictionaryString typeName, out XmlDictionaryString typeNamespace)
    {
        knownTypeResolver.ResolveType(dataContractType, null, out typeName, out typeNamespace);
        if (typeName == null || typeNamespace == null)
        {
            XmlDictionary dictionary = new XmlDictionary();
            typeName = dictionary.Add(dataContractType.FullName);
            typeNamespace = dictionary.Add(dataContractType.Assembly.FullName);
        }
    }
}
```

#### <a name="to-use-this-sample"></a><span data-ttu-id="27263-114">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="27263-114">To use this sample</span></span>

1. <span data-ttu-id="27263-115">Visual Studio 2012 を使用して、DCRSample .sln ソリューションファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="27263-115">Using Visual Studio 2012, open the DCRSample.sln solution file.</span></span>

2. <span data-ttu-id="27263-116">ソリューションファイルを右クリックし、[ **プロパティ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="27263-116">Right-click the solution file and choose **Properties**.</span></span>

3. <span data-ttu-id="27263-117">[ **ソリューションプロパティページ** ] ダイアログボックスの **[共通プロパティ**] の [ **スタートアッププロジェクト**] で、[ **マルチスタートアッププロジェクト:**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="27263-117">In the **Solution Property Pages** dialog, under **Common Properties**, **Startup Project**, select **Multiple startup projects:**.</span></span>

4. <span data-ttu-id="27263-118">**DCSwithDCR** プロジェクトの横にある [**アクション**] ドロップダウンから [**開始**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="27263-118">Next to the **DCSwithDCR** project, select **Start** from the **Action** dropdown.</span></span>

5. <span data-ttu-id="27263-119">**Netdcs** プロジェクトの横にある [**アクション**] ドロップダウンから [**開始**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="27263-119">Next to the **NetDCS** project, select **Start** from the **Action** dropdown.</span></span>

6. <span data-ttu-id="27263-120">[**OK**] をクリックしてダイアログ ボックスを閉じます。</span><span class="sxs-lookup"><span data-stu-id="27263-120">Click **OK** to close the dialog.</span></span>

7. <span data-ttu-id="27263-121">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="27263-121">To build the solution, press CTRL+SHIFT+B.</span></span>

8. <span data-ttu-id="27263-122">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="27263-122">To run the solution, press CTRL+F5.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="27263-123">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="27263-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="27263-124">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="27263-124">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="27263-125">このディレクトリが存在しない場合は、 [Windows Communication Foundation (wcf) および Windows Workflow Foundation (WF) のサンプルの .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) にアクセスして、すべての WINDOWS COMMUNICATION FOUNDATION (wcf) とサンプルをダウンロードして [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ください。</span><span class="sxs-lookup"><span data-stu-id="27263-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="27263-126">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="27263-126">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Data\NetDcSasDcSwithDCR`  
