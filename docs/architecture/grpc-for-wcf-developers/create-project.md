---
title: WCF 開発者向けの新しい ASP.NET Core gRPC プロジェクト-gRPC を作成する
description: Visual Studio またはコマンドラインを使用して gRPC プロジェクトを作成する方法について説明します。
ms.date: 12/15/2020
ms.openlocfilehash: 960725a9507797f43b2c15283e384b0ad827c2b1
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938658"
---
# <a name="create-a-new-aspnet-core-grpc-project"></a><span data-ttu-id="a9bef-103">新しい ASP.NET Core gRPC プロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="a9bef-103">Create a new ASP.NET Core gRPC project</span></span>

<span data-ttu-id="a9bef-104">.NET SDK には、強力な CLI ツールであるが付属しています。このツールを使用すると、 `dotnet` コマンドラインからプロジェクトとソリューションを作成および管理できます。</span><span class="sxs-lookup"><span data-stu-id="a9bef-104">The .NET SDK comes with a powerful CLI tool, `dotnet`, which enables you to create and manage projects and solutions from the command line.</span></span> <span data-ttu-id="a9bef-105">SDK は Visual Studio と密接に統合されているので、使い慣れたグラフィカルユーザーインターフェイスを使用してすべてを利用できます。</span><span class="sxs-lookup"><span data-stu-id="a9bef-105">The SDK is closely integrated with Visual Studio, so everything is also available through the familiar graphical user interface.</span></span> <span data-ttu-id="a9bef-106">この章では、新しい ASP.NET Core gRPC プロジェクトを作成する両方の方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="a9bef-106">This chapter shows both ways to create a new ASP.NET Core gRPC project.</span></span>

## <a name="create-the-project-by-using-visual-studio"></a><span data-ttu-id="a9bef-107">Visual Studio を使用してプロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="a9bef-107">Create the project by using Visual Studio</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a9bef-108">ASP.NET Core 5.0 アプリを開発するには、 **ASP.NET と web 開発** ワークロードがインストールされた Visual Studio 2019 バージョン16.3 以降が必要です。</span><span class="sxs-lookup"><span data-stu-id="a9bef-108">To develop any ASP.NET Core 5.0 app, you need Visual Studio 2019 version 16.3 or later, with the **ASP.NET and web development** workload installed.</span></span>

<span data-ttu-id="a9bef-109">空の *ソリューション* テンプレートから、 **TraderSys** という名前の空のソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="a9bef-109">Create an empty solution called **TraderSys** from the *Blank Solution* template.</span></span> <span data-ttu-id="a9bef-110">という名前のソリューションフォルダーを追加 `src` します。</span><span class="sxs-lookup"><span data-stu-id="a9bef-110">Add a solution folder called `src`.</span></span> <span data-ttu-id="a9bef-111">次に、フォルダーを右クリックし、[   >  **新しいプロジェクト** の追加] を選択します。</span><span class="sxs-lookup"><span data-stu-id="a9bef-111">Then, right-click on the folder and choose **Add** > **New Project**.</span></span> <span data-ttu-id="a9bef-112">[ `grpc` テンプレート検索] ボックスに「」と入力すると、という名前のプロジェクトテンプレートが表示され `gRPC Service` ます。</span><span class="sxs-lookup"><span data-stu-id="a9bef-112">Enter `grpc` in the template search box, and you should see a project template called `gRPC Service`.</span></span>

![[新しいプロジェクトの追加] ダイアログボックスのスクリーンショット](media/create-project/new-grpc-project.png)

<span data-ttu-id="a9bef-114">[ **次** へ] を選択して、[ **新しいプロジェクトの構成** ] ダイアログボックスに進みます。</span><span class="sxs-lookup"><span data-stu-id="a9bef-114">Select **Next** to continue to the **Configure your new project** dialog box.</span></span> <span data-ttu-id="a9bef-115">プロジェクトに名前 `TraderSys.Portfolios` を指定し `src` 、その **場所** にサブディレクトリを追加します。</span><span class="sxs-lookup"><span data-stu-id="a9bef-115">Name the project `TraderSys.Portfolios` and add an `src` subdirectory to the **Location**.</span></span>

![[新しいプロジェクトの構成] ダイアログボックスのスクリーンショット](media/create-project/configure-project.png)

<span data-ttu-id="a9bef-117">[ **次** へ] を選択して、[ **新しい Grpc サービスの作成** ] ダイアログボックスに進みます。</span><span class="sxs-lookup"><span data-stu-id="a9bef-117">Select **Next** to continue to the **Create a new gRPC service** dialog box.</span></span>

![[新しい gRPC サービスの作成] ダイアログボックスのスクリーンショット](media/create-project/create-new-grpc-service-v2.png)

<span data-ttu-id="a9bef-119">現時点では、サービス作成のオプションは限られています。</span><span class="sxs-lookup"><span data-stu-id="a9bef-119">At present, you have limited options for the service creation.</span></span> <span data-ttu-id="a9bef-120">Docker は後で導入されるため、このオプションをオフのままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="a9bef-120">Docker will be introduced later, so for now, leave that option unselected.</span></span> <span data-ttu-id="a9bef-121">[作成] を選択 **する** だけです。</span><span class="sxs-lookup"><span data-stu-id="a9bef-121">Just select **Create**.</span></span> <span data-ttu-id="a9bef-122">最初の ASP.NET Core 5.0 gRPC プロジェクトが生成され、ソリューションに追加されます。</span><span class="sxs-lookup"><span data-stu-id="a9bef-122">Your first ASP.NET Core 5.0 gRPC project is generated and added to the solution.</span></span> <span data-ttu-id="a9bef-123">の使用について知りたくない場合は、 `dotnet CLI` 「 [コード例のクリーンアップ](#clean-up-the-example-code) 」のセクションに進んでください。</span><span class="sxs-lookup"><span data-stu-id="a9bef-123">If you don't want to know about working with the `dotnet CLI`, skip to the [Clean up the example code](#clean-up-the-example-code) section.</span></span>

## <a name="create-the-project-by-using-the-net-cli"></a><span data-ttu-id="a9bef-124">.NET CLI を使用してプロジェクトを作成する</span><span class="sxs-lookup"><span data-stu-id="a9bef-124">Create the project by using the .NET CLI</span></span>

<span data-ttu-id="a9bef-125">ここでは、コマンドラインからのソリューションとプロジェクトの作成について説明します。</span><span class="sxs-lookup"><span data-stu-id="a9bef-125">This section covers the creation of solutions and projects from the command line.</span></span>

<span data-ttu-id="a9bef-126">次のコマンドに示すように、ソリューションを作成します。</span><span class="sxs-lookup"><span data-stu-id="a9bef-126">Create the solution as shown in the following command.</span></span> <span data-ttu-id="a9bef-127">`-o`(または `--output` ) フラグは、現在のディレクトリに作成されている出力ディレクトリを指定します (まだ存在しない場合)。</span><span class="sxs-lookup"><span data-stu-id="a9bef-127">The `-o` (or `--output`) flag specifies the output directory, which is created in the current directory if it doesn't already exist.</span></span> <span data-ttu-id="a9bef-128">ソリューションには、ディレクトリと同じ名前が付けられてい `TraderSys.sln` ます。</span><span class="sxs-lookup"><span data-stu-id="a9bef-128">The solution has the same name as the directory: `TraderSys.sln`.</span></span> <span data-ttu-id="a9bef-129">`-n`(または) フラグを使用して、別の名前を指定でき `--name` ます。</span><span class="sxs-lookup"><span data-stu-id="a9bef-129">You can provide a different name by using the `-n` (or `--name`) flag.</span></span>

```dotnetcli
dotnet new sln -o TraderSys
cd TraderSys
```

<span data-ttu-id="a9bef-130">ASP.NET Core 5.0 には、gRPC サービス用の CLI テンプレートが付属しています。</span><span class="sxs-lookup"><span data-stu-id="a9bef-130">ASP.NET Core 5.0 comes with a CLI template for gRPC services.</span></span> <span data-ttu-id="a9bef-131">このテンプレートを使用して新しいプロジェクトを作成し、 `src` ASP.NET Core プロジェクトの従来のようにサブディレクトリに配置します。</span><span class="sxs-lookup"><span data-stu-id="a9bef-131">Create the new project by using this template, putting it into an `src` subdirectory as is conventional for ASP.NET Core projects.</span></span> <span data-ttu-id="a9bef-132">フラグを使用して別の名前を指定しない限り、プロジェクトにはディレクトリ () の後に名前が付けられ `TraderSys.Portfolios.csproj` `-n` ます。</span><span class="sxs-lookup"><span data-stu-id="a9bef-132">The project is named after the directory (`TraderSys.Portfolios.csproj`), unless you specify a different name with the `-n` flag.</span></span>

```dotnetcli
dotnet new grpc -o src/TraderSys.Portfolios
```

<span data-ttu-id="a9bef-133">最後に、コマンドを使用して、ソリューションにプロジェクトを追加し `dotnet sln` ます。</span><span class="sxs-lookup"><span data-stu-id="a9bef-133">Finally, add the project to the solution by using the `dotnet sln` command:</span></span>

```dotnetcli
dotnet sln add src/TraderSys.Portfolios
```

> [!TIP]
> <span data-ttu-id="a9bef-134">特定のディレクトリにはファイルが1つしか含まれていないため、 `.csproj` ディレクトリだけを指定して入力を保存できます。</span><span class="sxs-lookup"><span data-stu-id="a9bef-134">Because the particular directory only contains a single `.csproj` file, you can specify just the directory, to save typing.</span></span>

<span data-ttu-id="a9bef-135">このソリューションは、Visual Studio 2019、Visual Studio Code、または任意のエディターで開くことができるようになりました。</span><span class="sxs-lookup"><span data-stu-id="a9bef-135">You can now open this solution in Visual Studio 2019, Visual Studio Code, or whatever editor you prefer.</span></span>

## <a name="clean-up-the-example-code"></a><span data-ttu-id="a9bef-136">コード例をクリーンアップする</span><span class="sxs-lookup"><span data-stu-id="a9bef-136">Clean up the example code</span></span>

<span data-ttu-id="a9bef-137">これで、このブックで既に確認されている gRPC テンプレートを使用して、サンプルサービスを作成できました。</span><span class="sxs-lookup"><span data-stu-id="a9bef-137">You've now created an example service by using the gRPC template, which was reviewed earlier in the book.</span></span> <span data-ttu-id="a9bef-138">このコードは、株式取引のコンテキストでは役に立たないので、最初のプロジェクトのために編集します。</span><span class="sxs-lookup"><span data-stu-id="a9bef-138">This code isn't useful in our stock trading context, so we'll edit things for our first project.</span></span>

### <a name="rename-and-edit-the-proto-file"></a><span data-ttu-id="a9bef-139">プロトコルファイルの名前を変更して編集する</span><span class="sxs-lookup"><span data-stu-id="a9bef-139">Rename and edit the proto file</span></span>

<span data-ttu-id="a9bef-140">ファイルの名前 `Protos/greet.proto` をに変更し `Protos/portfolios.proto` 、エディターで開きます。</span><span class="sxs-lookup"><span data-stu-id="a9bef-140">Go ahead and rename the `Protos/greet.proto` file to `Protos/portfolios.proto`, and open it in your editor.</span></span> <span data-ttu-id="a9bef-141">行の後のすべてを削除 `package` します。</span><span class="sxs-lookup"><span data-stu-id="a9bef-141">Delete everything after the `package` line.</span></span> <span data-ttu-id="a9bef-142">次に、 `option csharp_namespace` 、、 `package` およびの `service` 名前を変更し、既定のサービスを削除し `SayHello` ます。</span><span class="sxs-lookup"><span data-stu-id="a9bef-142">Then change the `option csharp_namespace`, `package` and `service` names, and remove the default `SayHello` service.</span></span> <span data-ttu-id="a9bef-143">コードは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="a9bef-143">The code now looks like the following:</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

> [!TIP]
> <span data-ttu-id="a9bef-144">既定では、このテンプレートでは名前空間の部分は追加されません `Protos` が、追加すると、gRPC によって生成されたクラスと独自のクラスをコード内で明確に区別しやすくなります。</span><span class="sxs-lookup"><span data-stu-id="a9bef-144">The template doesn't add the `Protos` namespace part by default, but adding it makes it easier to keep gRPC-generated classes and your own classes clearly separated in your code.</span></span>

<span data-ttu-id="a9bef-145">`greet.proto`Visual Studio などの統合開発環境 (IDE) でファイルの名前を変更すると、このファイルへの参照がファイルで自動的に更新され `.csproj` ます。</span><span class="sxs-lookup"><span data-stu-id="a9bef-145">If you rename the `greet.proto` file in an integrated development environment (IDE) like Visual Studio, a reference to this file is automatically updated in the `.csproj` file.</span></span> <span data-ttu-id="a9bef-146">ただし、Visual Studio Code などの他のエディターでは、この参照は自動的に更新されないため、プロジェクトファイルを手動で編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9bef-146">But in some other editor, such as Visual Studio Code, this reference isn't updated automatically, so you need to edit the project file manually.</span></span>

<span data-ttu-id="a9bef-147">GRPC ビルドターゲットには、どのファイルをコンパイルするかを `Protobuf` 指定できる item 要素 `.proto` と、どのような形式のコード生成が必要か (つまり、"サーバー" または "クライアント") があります。</span><span class="sxs-lookup"><span data-stu-id="a9bef-147">In the gRPC build targets, there's a `Protobuf` item element that lets you specify which `.proto` files should be compiled, and which form of code generation is required (that is, "Server" or "Client").</span></span>

```xml
<ItemGroup>
  <Protobuf Include="Protos\portfolios.proto" GrpcServices="Server" />
</ItemGroup>
```

### <a name="rename-the-greeterservice-class"></a><span data-ttu-id="a9bef-148">クラスの名前を変更する `GreeterService`</span><span class="sxs-lookup"><span data-stu-id="a9bef-148">Rename the `GreeterService` class</span></span>

<span data-ttu-id="a9bef-149">`GreeterService`クラスはフォルダー内に `Services` あり、から継承され `Greeter.GreeterBase` ます。</span><span class="sxs-lookup"><span data-stu-id="a9bef-149">The `GreeterService` class is in the `Services` folder and inherits from `Greeter.GreeterBase`.</span></span> <span data-ttu-id="a9bef-150">名前をに変更 `PortfolioService` し、基本クラスをに変更し `Portfolios.PortfoliosBase` ます。</span><span class="sxs-lookup"><span data-stu-id="a9bef-150">Rename it to `PortfolioService`, and change the base class to `Portfolios.PortfoliosBase`.</span></span> <span data-ttu-id="a9bef-151">メソッドを削除 `override` します。</span><span class="sxs-lookup"><span data-stu-id="a9bef-151">Delete the `override` methods.</span></span>

```csharp
public class PortfolioService : Portfolios.PortfoliosBase
{
}
```

<span data-ttu-id="a9bef-152">クラスのメソッドに、クラスへの参照がありました `GreeterService` `Configure` `Startup` 。</span><span class="sxs-lookup"><span data-stu-id="a9bef-152">There was a reference to the `GreeterService` class in the `Configure` method in the `Startup` class.</span></span> <span data-ttu-id="a9bef-153">リファクタリングを使用してクラスの名前を変更した場合は、この参照が自動的に更新されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9bef-153">If you used refactoring to rename the class, this reference should have been updated automatically.</span></span> <span data-ttu-id="a9bef-154">ただし、使用していない場合は、手動で編集する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9bef-154">However, if you didn't, you need to edit it manually.</span></span>

```csharp
public void Configure(IApplicationBuilder app, IWebHostEnvironment env)
{
    if (env.IsDevelopment())
    {
        app.UseDeveloperExceptionPage();
    }

    app.UseRouting();

    app.UseEndpoints(endpoints =>
    {
        endpoints.MapGrpcService<PortfolioService>();
    });
}
```

<span data-ttu-id="a9bef-155">次のセクションでは、この新しいサービスに機能を追加します。</span><span class="sxs-lookup"><span data-stu-id="a9bef-155">In the next section, we'll add functionality to this new service.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a9bef-156">[前へ](migrate-wcf-to-grpc.md)
>[次へ](migrate-request-reply.md)</span><span class="sxs-lookup"><span data-stu-id="a9bef-156">[Previous](migrate-wcf-to-grpc.md)
[Next](migrate-request-reply.md)</span></span>
