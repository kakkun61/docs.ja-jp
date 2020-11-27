---
title: '方法: カスタム アクティビティ テンプレートを作成する'
ms.date: 03/30/2017
ms.assetid: 6760a5cc-6eb8-465f-b4fa-f89b39539429
ms.openlocfilehash: 90a54806833ff66797fb7beaa6ac8a912665bddc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96280118"
---
# <a name="how-to-create-a-custom-activity-template"></a><span data-ttu-id="ffa41-102">方法: カスタム アクティビティ テンプレートを作成する</span><span class="sxs-lookup"><span data-stu-id="ffa41-102">How to: Create a Custom Activity Template</span></span>

<span data-ttu-id="ffa41-103">カスタム複合アクティビティなどのアクティビティの構成のカスタマイズには、カスタム アクティビティ テンプレートが使用されるため、手動で各アクティビティを個別に作成し、そのプロパティおよびその他の設定を構成する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="ffa41-103">Custom activity templates are used to customize the configuration of activities, including custom composite activities, so that users do not have to create each activity individually and configure their properties and other settings manually.</span></span> <span data-ttu-id="ffa41-104">これらのカスタムテンプレートは、Windows ワークフローデザイナーの **ツールボックス** 、または再ホストされたデザイナーから使用できます。ユーザーは、これらのテンプレートを使用して、構成済みのデザインサーフェイスにドラッグできます。</span><span class="sxs-lookup"><span data-stu-id="ffa41-104">These custom templates can be made available in the **Toolbox** on the Windows Workflow Designer or from a rehosted designer, from which users can drag them onto the preconfigured design surface.</span></span> <span data-ttu-id="ffa41-105">ワークフローデザイナーには、[[メッセージングアクティビティデザイナー](/visualstudio/workflow-designer/messaging-activity-designers) ] カテゴリの[sendandreceivereply テンプレートデザイナー](/visualstudio/workflow-designer/sendandreceivereply-template-designer)と[receiveandsendreply テンプレートデザイナー](/visualstudio/workflow-designer/receiveandsendreply-template-designer)の適切なテンプレートの例が付属しています。</span><span class="sxs-lookup"><span data-stu-id="ffa41-105">Workflow Designer ships with good examples of such templates: the [SendAndReceiveReply Template Designer](/visualstudio/workflow-designer/sendandreceivereply-template-designer) and the [ReceiveAndSendReply Template Designer](/visualstudio/workflow-designer/receiveandsendreply-template-designer) in the [Messaging Activity Designers](/visualstudio/workflow-designer/messaging-activity-designers) category.</span></span>

 <span data-ttu-id="ffa41-106">このトピックの最初の手順では、 **Delay** アクティビティ用のカスタムアクティビティテンプレートを作成する方法について説明します。2番目の手順では、カスタムテンプレートが動作するかどうかを確認するためにワークフローデザイナーで使用できるようにする方法について簡単に説明します。</span><span class="sxs-lookup"><span data-stu-id="ffa41-106">The first procedure in this topic describes how to create a custom activity template for a **Delay** activity and the second procedure describes briefly how to make it available in a Workflow Designer to verify that the custom template works.</span></span>

 <span data-ttu-id="ffa41-107">カスタム アクティビティ テンプレートに <xref:System.Activities.Presentation.IActivityTemplateFactory> を実装する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ffa41-107">Custom activity templates must implement the <xref:System.Activities.Presentation.IActivityTemplateFactory>.</span></span> <span data-ttu-id="ffa41-108">このインターフェイスには単一の <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> メソッドがあり、このメソッドを使用して、テンプレートで使用されるアクティビティ インスタンスを作成および構成できます。</span><span class="sxs-lookup"><span data-stu-id="ffa41-108">The interface has a single <xref:System.Activities.Presentation.IActivityTemplateFactory.Create%2A> method with which you can create and configure the activity instances used in the template.</span></span>

## <a name="to-create-a-template-for-the-delay-activity"></a><span data-ttu-id="ffa41-109">Delay アクティビティのテンプレートを作成するには</span><span class="sxs-lookup"><span data-stu-id="ffa41-109">To create a template for the Delay activity</span></span>

1. <span data-ttu-id="ffa41-110">Visual Studio 2010 を起動します。</span><span class="sxs-lookup"><span data-stu-id="ffa41-110">Start Visual Studio 2010.</span></span>

2. <span data-ttu-id="ffa41-111">**[ファイル]** メニューの **[新規作成]** をポイントし、 **[プロジェクト]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ffa41-111">On the **File** menu, point to **New**, and then select **Project**.</span></span>

     <span data-ttu-id="ffa41-112">**[新しいプロジェクト]** ダイアログ ボックスが表示されます。</span><span class="sxs-lookup"><span data-stu-id="ffa41-112">The **New Project** dialog box opens.</span></span>

3. <span data-ttu-id="ffa41-113">[**プロジェクトの種類**] ペインで、使用している言語に応じて、 **Visual C#** プロジェクトまたは **Visual Basic** グループから [**ワークフロー** ] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ffa41-113">In the **Project Types** pane, select **Workflow** from either the **Visual C#** projects or **Visual Basic** groupings depending on your language preference.</span></span>

4. <span data-ttu-id="ffa41-114">[ **テンプレート** ] ウィンドウで、[ **アクティビティライブラリ**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ffa41-114">In the **Templates** pane, select **Activity Library**.</span></span>

5. <span data-ttu-id="ffa41-115">**[名前]** ボックスに、「`DelayActivityTemplate`」と入力します。</span><span class="sxs-lookup"><span data-stu-id="ffa41-115">In the **Name** box, enter `DelayActivityTemplate`.</span></span>

6. <span data-ttu-id="ffa41-116">[ **場所** ] と [ **ソリューション名** ] のテキストボックスの既定値をそのまま使用し、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ffa41-116">Accept the defaults in the **Location** and **Solution name** text boxes, and then click **OK**.</span></span>

7. <span data-ttu-id="ffa41-117">**ソリューションエクスプローラー** で DelayActivityTemplate プロジェクトの References ディレクトリを右クリックし、[**参照の追加**] をクリックして [参照の **追加**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="ffa41-117">Right-click the References directory of the DelayActivityTemplate project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

8. <span data-ttu-id="ffa41-118">[ **.Net** ] タブに移動し、左側の [**コンポーネント名**] 列で [**プレゼンテーションフレームワーク**] を選択し、[ **OK** ] をクリックして PresentationFramework.dll ファイルへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="ffa41-118">Go to the **.NET** tab and select **PresentationFramework** from the **Component Name** column on the left and click **OK** to add a reference to the PresentationFramework.dll file.</span></span>

9. <span data-ttu-id="ffa41-119">この手順を繰り返して、System.Activities.Presentation.dll ファイルと WindowsBase.dll ファイルへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="ffa41-119">Repeat this procedure to add references to the System.Activities.Presentation.dll and the WindowsBase.dll files.</span></span>

10. <span data-ttu-id="ffa41-120">**ソリューションエクスプローラー** で DelayActivityTemplate プロジェクトを右クリックし、[**追加**]、[**新しい項目**] の順に選択して [**新しい項目の追加**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="ffa41-120">Right-click the DelayActivityTemplate project in **Solution Explorer** and choose **Add** and then **New Item** to open the **Add New Item** dialog box.</span></span>

11. <span data-ttu-id="ffa41-121">**クラス** テンプレートを選択し、MyDelayTemplate という名前を指定して、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ffa41-121">Select the **Class** template, name it MyDelayTemplate, and then click **OK**.</span></span>

12. <span data-ttu-id="ffa41-122">MyDelayTemplate.cs ファイルを開き、次のステートメントを追加します。</span><span class="sxs-lookup"><span data-stu-id="ffa41-122">Open the MyDelayTemplate.cs file and add the following statements.</span></span>

    ```csharp
    //Namespaces added
    using System.Activities;
    using System.Activities.Statements;
    using System.Activities.Presentation;
    using System.Windows;
    ```

13. <span data-ttu-id="ffa41-123">次のコードを使用して、<xref:System.Activities.Presentation.IActivityTemplateFactory> クラスを持つ `MyDelayActivity` を実装します。</span><span class="sxs-lookup"><span data-stu-id="ffa41-123">Implement the <xref:System.Activities.Presentation.IActivityTemplateFactory> with the `MyDelayActivity` class with the following code.</span></span> <span data-ttu-id="ffa41-124">これにより、10 秒間の遅延が構成されます。</span><span class="sxs-lookup"><span data-stu-id="ffa41-124">This configures the delay to have a duration of 10 seconds.</span></span>

    ```csharp
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
    ```

14. <span data-ttu-id="ffa41-125">[**ビルド**] メニューの [**ソリューションのビルド**] を選択して、DelayActivityTemplate.dll ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="ffa41-125">Select **Build Solution** from the **Build** menu to generate the DelayActivityTemplate.dll file.</span></span>

### <a name="to-make-the-template-available-in-a-workflow-designer"></a><span data-ttu-id="ffa41-126">ワークフロー デザイナーでテンプレートを利用できるようにするには</span><span class="sxs-lookup"><span data-stu-id="ffa41-126">To make the template available in a Workflow Designer</span></span>

1. <span data-ttu-id="ffa41-127">**ソリューションエクスプローラー** で DelayActivityTemplate ソリューションを右クリックし、[**追加**]、[**新しいプロジェクト**] の順に選択して [**新しいプロジェクトの追加**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="ffa41-127">Right-click the DelayActivityTemplate solution in **Solution Explorer** and choose **Add** and then **New Project** to open the **Add New Project** dialog box.</span></span>

2. <span data-ttu-id="ffa41-128">[ **ワークフローコンソールアプリケーション** ] テンプレートを選択し、という名前を指定して `CustomActivityTemplateApp` 、[ **OK]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="ffa41-128">Select the **Workflow Console Application** template, name it `CustomActivityTemplateApp`, and then click **OK**.</span></span>

3. <span data-ttu-id="ffa41-129">**ソリューションエクスプローラー** で CustomActivityTemplateApp プロジェクトの References ディレクトリを右クリックし、[**参照の追加**] をクリックして [参照の **追加**] ダイアログボックスを開きます。</span><span class="sxs-lookup"><span data-stu-id="ffa41-129">Right-click the References directory of the CustomActivityTemplateApp project in **Solution Explorer** and choose **Add Reference** to open the **Add Reference** dialog box.</span></span>

4. <span data-ttu-id="ffa41-130">[**プロジェクト**] タブに移動し、左側の [**プロジェクト名**] 列から [ **delayactivitytemplate** ] を選択し、[ **OK** ] をクリックして、最初の手順で作成した DelayActivityTemplate.dll ファイルへの参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="ffa41-130">Go to the **Projects** tab and select **DelayActivityTemplate** from the **Project Name** column on the left and click **OK** to add a reference to the DelayActivityTemplate.dll file that you created in the first procedure.</span></span>

5. <span data-ttu-id="ffa41-131">**ソリューションエクスプローラー** で CustomActivityTemplateApp プロジェクトを右クリックし、[**ビルド**] を選択してアプリケーションをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="ffa41-131">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Build** to compile the application.</span></span>

6. <span data-ttu-id="ffa41-132">**ソリューションエクスプローラー** で CustomActivityTemplateApp プロジェクトを右クリックし、[**スタートアッププロジェクトに設定**] を選択します。</span><span class="sxs-lookup"><span data-stu-id="ffa41-132">Right-click the CustomActivityTemplateApp project in **Solution Explorer** and choose **Set as Startup Project**.</span></span>

7. <span data-ttu-id="ffa41-133">[**デバッグ**] メニューの [**デバッグなしで開始**] を選択し、任意のキーを押して cmd.exe ウィンドウでメッセージが表示されたら操作を続行します。</span><span class="sxs-lookup"><span data-stu-id="ffa41-133">Select **Start Without Debugging** from the **Debug** menu and press any key to continue when prompted from the cmd.exe window.</span></span>

8. <span data-ttu-id="ffa41-134">Workflow1.xaml ファイルを開き、 **ツールボックス** を開きます。</span><span class="sxs-lookup"><span data-stu-id="ffa41-134">Open the Workflow1.xaml file and open the **Toolbox**.</span></span>

9. <span data-ttu-id="ffa41-135">**Delayactivitytemplate** カテゴリで **mydelayactivity** テンプレートを見つけます。</span><span class="sxs-lookup"><span data-stu-id="ffa41-135">Locate the **MyDelayActivity** template in the **DelayActivityTemplate** category.</span></span> <span data-ttu-id="ffa41-136">デザイン サーフェイスにドラッグします。</span><span class="sxs-lookup"><span data-stu-id="ffa41-136">Drag it onto the design surface.</span></span> <span data-ttu-id="ffa41-137">[ **プロパティ** ] ウィンドウで、 `Duration` プロパティが10秒に設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="ffa41-137">Confirm in the **Properties** window that the `Duration` property has been set to 10 seconds.</span></span>

## <a name="example"></a><span data-ttu-id="ffa41-138">例</span><span class="sxs-lookup"><span data-stu-id="ffa41-138">Example</span></span>

 <span data-ttu-id="ffa41-139">MyDelayActivity.cs ファイルには次のコードが含まれます。</span><span class="sxs-lookup"><span data-stu-id="ffa41-139">The MyDelayActivity.cs file should contain the following code.</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

//Namespaces added
using System.Activities;
using System.Activities.Statements;
using System.Activities.Presentation;
using System.Windows;

namespace DelayActivityTemplate
{
    public sealed class MyDelayActivity : IActivityTemplateFactory
    {
        public Activity Create(System.Windows.DependencyObject target)
        {
            return new System.Activities.Statements.Delay
            {
                DisplayName = "DelayActivityTemplate",
                Duration = new TimeSpan(0, 0, 10)

            };
        }
    }
}
```

## <a name="see-also"></a><span data-ttu-id="ffa41-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="ffa41-140">See also</span></span>

- <xref:System.Activities.Presentation.IActivityTemplateFactory>
- [<span data-ttu-id="ffa41-141">ワークフロー デザイン操作のカスタマイズ</span><span class="sxs-lookup"><span data-stu-id="ffa41-141">Customizing the Workflow Design Experience</span></span>](customizing-the-workflow-design-experience.md)
