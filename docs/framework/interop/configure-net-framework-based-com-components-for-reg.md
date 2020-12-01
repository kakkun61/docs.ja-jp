---
title: '方法: 登録を必要としないアクティベーション用の .NET Framework ベースの COM コンポーネントを構成する'
description: 登録を必要としないアクティベーション用の .NET ベースの COM コンポーネントを構成します。 セットアップには、Win32 スタイルのアプリケーション マニフェストと .NET コンポーネント マニフェストが必要です。
ms.date: 03/30/2017
helpviewer_keywords:
- components [.NET Framework], manifest
- application manifests [.NET Framework]
- manifests [.NET Framework]
- registration-free COM interop, configuring .NET-based components
- activation, registration-free
ms.assetid: 32f8b7c6-3f73-455d-8e13-9846895bd43b
ms.openlocfilehash: ffeb342f286663ee7fe733ee617741e0ab30d0d8
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96282874"
---
# <a name="how-to-configure-net-framework-based-com-components-for-registration-free-activation"></a><span data-ttu-id="d4998-104">方法: 登録を必要としないアクティベーション用の .NET Framework ベースの COM コンポーネントを構成する</span><span class="sxs-lookup"><span data-stu-id="d4998-104">How to: Configure .NET Framework-Based COM Components for Registration-Free Activation</span></span>

<span data-ttu-id="d4998-105">.NET Framework ベースのコンポーネントの登録を必要としないアクティベーションは、COM コンポーネントの場合よりも少しだけ複雑です。</span><span class="sxs-lookup"><span data-stu-id="d4998-105">Registration-free activation for .NET Framework-based components is only slightly more complicated than it is for COM components.</span></span> <span data-ttu-id="d4998-106">セットアップには 2 つのマニフェストが必要です。</span><span class="sxs-lookup"><span data-stu-id="d4998-106">The setup requires two manifests:</span></span>  
  
- <span data-ttu-id="d4998-107">COM アプリケーションには、マネージド コンポーネントを識別するための Win32 スタイルのアプリケーション マニフェストが必要です。</span><span class="sxs-lookup"><span data-stu-id="d4998-107">COM applications must have a Win32-style application manifest to identify the managed component.</span></span>  
  
- <span data-ttu-id="d4998-108">.NET Framework ベースのコンポーネントには、実行時に必要なアクティベーション情報のコンポーネント マニフェストが必要です。</span><span class="sxs-lookup"><span data-stu-id="d4998-108">.NET Framework-based components must have a component manifest for activation information needed at run time.</span></span>  
  
 <span data-ttu-id="d4998-109">このトピックでは、アプリケーション マニフェストをアプリケーションに関連付ける方法、コンポーネント マニフェストをコンポーネントに関連付ける方法、およびコンポーネント マニフェストをアセンブリに埋め込む方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="d4998-109">This topic describes how to associate an application manifest with an application; associate a component manifest with a component; and embed a component manifest in an assembly.</span></span>  
  
## <a name="create-an-application-manifest"></a><span data-ttu-id="d4998-110">アプリケーション マニフェストを作成する</span><span class="sxs-lookup"><span data-stu-id="d4998-110">Create an application manifest</span></span>  
  
1. <span data-ttu-id="d4998-111">XML エディターを使用して、1 つ以上のマネージド コンポーネントと相互運用する COM アプリケーションによって所有されるアプリケーション マニフェストを作成または編集します。</span><span class="sxs-lookup"><span data-stu-id="d4998-111">Using an XML editor, create (or modify) the application manifest owned by the COM application that is interoperating with one or more managed components.</span></span>  
  
2. <span data-ttu-id="d4998-112">ファイルの先頭に次の標準ヘッダーを挿入します。</span><span class="sxs-lookup"><span data-stu-id="d4998-112">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
     <span data-ttu-id="d4998-113">マニフェストの要素とその属性については、「[Application Manifests](/windows/desktop/SbsCs/application-manifests)」(アプリケーション マニフェスト) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d4998-113">For information about manifest elements and their attributes, see [Application Manifests](/windows/desktop/SbsCs/application-manifests).</span></span>  
  
3. <span data-ttu-id="d4998-114">マニフェストの所有者を指定します。</span><span class="sxs-lookup"><span data-stu-id="d4998-114">Identify the owner of the manifest.</span></span> <span data-ttu-id="d4998-115">次の例では、`myComApp` バージョン 1 がマニフェスト ファイルを所有しています。</span><span class="sxs-lookup"><span data-stu-id="d4998-115">In the following example, `myComApp` version 1 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="msil"
      />
    </assembly>  
    ```  
  
4. <span data-ttu-id="d4998-116">依存アセンブリを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4998-116">Identify dependent assemblies.</span></span> <span data-ttu-id="d4998-117">`myComApp` が `myManagedComp` に依存する例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d4998-117">In the following example, `myComApp` depends on `myManagedComp`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
      <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myComApp"
                        version="1.0.0.0"
                        processorArchitecture="x86"
                        publicKeyToken="8275b28176rcbbef"  
      />  
      <dependency>  
        <dependentAssembly>  
          <assemblyIdentity type="win32"
                        name="myOrganization.myDivision.myManagedComp"
                        version="6.0.0.0"
                        processorArchitecture="X86"
                        publicKeyToken="8275b28176rcbbef"  
          />  
        </dependentAssembly>  
      </dependency>  
    </assembly>  
    ```  
  
5. <span data-ttu-id="d4998-118">マニフェスト ファイルに名前を付けて保存します。</span><span class="sxs-lookup"><span data-stu-id="d4998-118">Save and name the manifest file.</span></span> <span data-ttu-id="d4998-119">アプリケーション マニフェストの名前は、アセンブリ実行可能ファイルの名前に拡張子 .manifest が付いたものです。</span><span class="sxs-lookup"><span data-stu-id="d4998-119">The name of an application manifest is the name of the assembly executable followed by the .manifest extension.</span></span> <span data-ttu-id="d4998-120">たとえば、myComApp.exe のアプリケーション マニフェスト ファイル名は myComApp.exe.manifest です。</span><span class="sxs-lookup"><span data-stu-id="d4998-120">For example, the application manifest file name for myComApp.exe is myComApp.exe.manifest.</span></span>  
  
<span data-ttu-id="d4998-121">アプリケーション マニフェストは、COM アプリケーションと同じディレクトリにインストールできます。</span><span class="sxs-lookup"><span data-stu-id="d4998-121">You can install an application manifest in the same directory as the COM application.</span></span> <span data-ttu-id="d4998-122">また、アプリケーションの .exe ファイルにリソースとして追加することもできます。</span><span class="sxs-lookup"><span data-stu-id="d4998-122">Alternatively, you can add it as a resource to the application's .exe file.</span></span> <span data-ttu-id="d4998-123">詳しくは、「[side-by-side アセンブリについて](/windows/desktop/SbsCs/about-side-by-side-assemblies-)」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="d4998-123">For more information, see [About Side-by-Side Assemblies](/windows/desktop/SbsCs/about-side-by-side-assemblies-).</span></span>  
  
## <a name="create-a-component-manifest"></a><span data-ttu-id="d4998-124">コンポーネント マニフェストを作成する</span><span class="sxs-lookup"><span data-stu-id="d4998-124">Create a component manifest</span></span>  
  
1. <span data-ttu-id="d4998-125">XML エディターを使用して、マネージド アセンブリを記述するコンポーネント マニフェストを作成します。</span><span class="sxs-lookup"><span data-stu-id="d4998-125">Using an XML editor, create a component manifest to describe the managed assembly.</span></span>  
  
2. <span data-ttu-id="d4998-126">ファイルの先頭に次の標準ヘッダーを挿入します。</span><span class="sxs-lookup"><span data-stu-id="d4998-126">Insert the following standard header at the beginning of the file:</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
    </assembly>
    ```  
  
3. <span data-ttu-id="d4998-127">ファイルの所有者を指定します。</span><span class="sxs-lookup"><span data-stu-id="d4998-127">Identify the owner of the file.</span></span> <span data-ttu-id="d4998-128">アプリケーション マニフェスト ファイル内の `<assemblyIdentity>` 要素の `<dependentAssembly>` 要素は、コンポーネント マニフェスト内の要素と一致している必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4998-128">The `<assemblyIdentity>` element of the `<dependentAssembly>` element in application manifest file must match the one in the component manifest.</span></span> <span data-ttu-id="d4998-129">次の例では、`myManagedComp` バージョン 1.2.3.4 がマニフェスト ファイルを所有しています。</span><span class="sxs-lookup"><span data-stu-id="d4998-129">In the following example, `myManagedComp` version 1.2.3.4 owns the manifest file.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"  
                        publicKeyToken="8275b28176rcbbef"  
                        processorArchitecture="msil"  
           />
    </assembly>
    ```  
  
4. <span data-ttu-id="d4998-130">アセンブリ内の各クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4998-130">Identify each class in the assembly.</span></span> <span data-ttu-id="d4998-131">マネージド アセンブリ内の各クラスを一意に識別するには `<clrClass>` 要素を使用します。</span><span class="sxs-lookup"><span data-stu-id="d4998-131">Use the `<clrClass>` element to uniquely identify each class in the managed assembly.</span></span> <span data-ttu-id="d4998-132">この要素は、`<assembly>` 要素のサブ要素であり、次の表に示す属性を持っています。</span><span class="sxs-lookup"><span data-stu-id="d4998-132">The element, which is a subelement of the `<assembly>` element, has the attributes described in the following table.</span></span>  
  
    |<span data-ttu-id="d4998-133">属性</span><span class="sxs-lookup"><span data-stu-id="d4998-133">Attribute</span></span>|<span data-ttu-id="d4998-134">説明</span><span class="sxs-lookup"><span data-stu-id="d4998-134">Description</span></span>|<span data-ttu-id="d4998-135">必須</span><span class="sxs-lookup"><span data-stu-id="d4998-135">Required</span></span>|  
    |---------------|-----------------|--------------|  
    |`clsid`|<span data-ttu-id="d4998-136">アクティブにするクラスを指定する識別子。</span><span class="sxs-lookup"><span data-stu-id="d4998-136">The identifier that specifies the class to be activated.</span></span>|<span data-ttu-id="d4998-137">はい</span><span class="sxs-lookup"><span data-stu-id="d4998-137">Yes</span></span>|  
    |`description`|<span data-ttu-id="d4998-138">ユーザーにコンポーネントを説明する文字列。</span><span class="sxs-lookup"><span data-stu-id="d4998-138">A string that informs the user about the component.</span></span> <span data-ttu-id="d4998-139">既定では文字列は空です。</span><span class="sxs-lookup"><span data-stu-id="d4998-139">An empty string is the default.</span></span>|<span data-ttu-id="d4998-140">いいえ</span><span class="sxs-lookup"><span data-stu-id="d4998-140">No</span></span>|  
    |`name`|<span data-ttu-id="d4998-141">マネージド クラスを表す文字列。</span><span class="sxs-lookup"><span data-stu-id="d4998-141">A string that represents the managed class.</span></span>|<span data-ttu-id="d4998-142">はい</span><span class="sxs-lookup"><span data-stu-id="d4998-142">Yes</span></span>|  
    |`progid`|<span data-ttu-id="d4998-143">遅延バインディングによるアクティベーションで使用される識別子。</span><span class="sxs-lookup"><span data-stu-id="d4998-143">The identifier to be used for late-bound activation.</span></span>|<span data-ttu-id="d4998-144">いいえ</span><span class="sxs-lookup"><span data-stu-id="d4998-144">No</span></span>|  
    |`threadingModel`|<span data-ttu-id="d4998-145">COM スレッド モデル。</span><span class="sxs-lookup"><span data-stu-id="d4998-145">The COM threading model.</span></span> <span data-ttu-id="d4998-146">"Both" が既定値です。</span><span class="sxs-lookup"><span data-stu-id="d4998-146">"Both" is the default value.</span></span>|<span data-ttu-id="d4998-147">いいえ</span><span class="sxs-lookup"><span data-stu-id="d4998-147">No</span></span>|  
    |`runtimeVersion`|<span data-ttu-id="d4998-148">使用する共通言語ランタイム (CLR: Common Language Runtime) のバージョンを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4998-148">Specifies the common language runtime (CLR) version to use.</span></span> <span data-ttu-id="d4998-149">この属性を指定せず、CLR がまだ読み込まれていない場合は、インストールされている最新の CLR (CLR Version 4 よりも前のバージョン) でコンポーネントが読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="d4998-149">If you do not specify this attribute, and the CLR is not already loaded, the component is loaded with the latest installed CLR prior to CLR version 4.</span></span> <span data-ttu-id="d4998-150">v1.0.3705、v1.1.4322、または v2.0.50727 を指定すると、インストールされている最新の CLR バージョン (CLR Version 4 よりも前のバージョン。通常は v2.0.50727) に自動的にロールフォワードされます。</span><span class="sxs-lookup"><span data-stu-id="d4998-150">If you specify v1.0.3705, v1.1.4322, or v2.0.50727, the version automatically rolls forward to the latest installed CLR version prior to CLR version 4 (usually v2.0.50727).</span></span> <span data-ttu-id="d4998-151">別のバージョンの CLR が既に読み込まれていて、指定されたバージョンをインプロセスで並行して (side-by-side で) 読み込むことができる場合は、指定されたバージョンが読み込まれます。それ以外の場合は、読み込まれた CLR が使用されます。</span><span class="sxs-lookup"><span data-stu-id="d4998-151">If another version of the CLR is already loaded and the specified version can be loaded side-by-side in-process, the specified version is loaded; otherwise, the loaded CLR is used.</span></span> <span data-ttu-id="d4998-152">これにより、読み込みエラーが発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="d4998-152">This might cause a load failure.</span></span>|<span data-ttu-id="d4998-153">いいえ</span><span class="sxs-lookup"><span data-stu-id="d4998-153">No</span></span>|  
    |`tlbid`|<span data-ttu-id="d4998-154">クラスに関する型情報を格納するタイプ ライブラリの識別子。</span><span class="sxs-lookup"><span data-stu-id="d4998-154">The identifier of the type library that contains type information about the class.</span></span>|<span data-ttu-id="d4998-155">いいえ</span><span class="sxs-lookup"><span data-stu-id="d4998-155">No</span></span>|  
  
     <span data-ttu-id="d4998-156">属性タグはすべて大文字と小文字が区別されます。</span><span class="sxs-lookup"><span data-stu-id="d4998-156">All attribute tags are case-sensitive.</span></span> <span data-ttu-id="d4998-157">OLE/COM オブジェクト ビューアー (Oleview.exe) で、エクスポートされたアセンブリのタイプ ライブラリを表示することによって、CLSID、ProgID、スレッド モデル、およびランタイムのバージョンを取得できます。</span><span class="sxs-lookup"><span data-stu-id="d4998-157">You can obtain CLSIDs, ProgIDs, threading models, and the runtime version by viewing the exported type library for the assembly with the OLE/COM ObjectViewer (Oleview.exe).</span></span>  
  
     <span data-ttu-id="d4998-158">`testClass1` および `testClass2` という 2 つのクラスを識別するコンポーネント マニフェストを次に示します。</span><span class="sxs-lookup"><span data-stu-id="d4998-158">The following component manifest identifies two classes, `testClass1` and `testClass2`.</span></span>  
  
    ```xml  
    <?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
    <assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
           <assemblyIdentity  
                        name="myOrganization.myDivision.myManagedComp"  
                        version="1.2.3.4"
                        publicKeyToken="8275b28176rcbbef"  
           />  
           <clrClass  
                        clsid="{65722BE6-3449-4628-ABD3-74B6864F9739}"  
                        progid="myManagedComp.testClass1"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass1"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <clrClass  
                        clsid="{367221D6-3559-3328-ABD3-45B6825F9732}"  
                        progid="myManagedComp.testClass2"  
                        threadingModel="Both"  
                        name="myManagedComp.testClass2"  
                        runtimeVersion="v1.0.3705">  
           </clrClass>  
           <file name="MyManagedComp.dll">  
           </file>  
    </assembly>  
    ```  
  
5. <span data-ttu-id="d4998-159">マニフェスト ファイルに名前を付けて保存します。</span><span class="sxs-lookup"><span data-stu-id="d4998-159">Save and name the manifest file.</span></span> <span data-ttu-id="d4998-160">コンポーネント マニフェストの名前は、アセンブリ ライブラリの名前に拡張子 .manifest が付いたものです。</span><span class="sxs-lookup"><span data-stu-id="d4998-160">The name of a component manifest is the name of the assembly library followed by the .manifest extension.</span></span> <span data-ttu-id="d4998-161">たとえば、myManagedComp.dll の場合は、myManagedComp.manifest になります。</span><span class="sxs-lookup"><span data-stu-id="d4998-161">For example, the myManagedComp.dll is myManagedComp.manifest.</span></span>  
  
 <span data-ttu-id="d4998-162">コンポーネント マニフェストはリソースとしてアセンブリに埋め込む必要があります。</span><span class="sxs-lookup"><span data-stu-id="d4998-162">You must embed the component manifest as a resource in the assembly.</span></span>  
  
#### <a name="to-embed-a-component-manifest-in-a-managed-assembly"></a><span data-ttu-id="d4998-163">コンポーネント マニフェストをマネージド アセンブリに埋め込むには</span><span class="sxs-lookup"><span data-stu-id="d4998-163">To embed a component manifest in a managed assembly</span></span>  
  
1. <span data-ttu-id="d4998-164">次のステートメントを含むリソース スクリプトを作成します。</span><span class="sxs-lookup"><span data-stu-id="d4998-164">Create a resource script that contains the following statement:</span></span>  
  
     `RT_MANIFEST 1 myManagedComp.manifest`  
  
     <span data-ttu-id="d4998-165">このステートメントで、`myManagedComp.manifest` は埋め込むコンポーネント マニフェストの名前です。</span><span class="sxs-lookup"><span data-stu-id="d4998-165">In this statement, `myManagedComp.manifest` is the name of the component manifest being embedded.</span></span> <span data-ttu-id="d4998-166">この例では、スクリプト ファイル名は `myresource.rc` です。</span><span class="sxs-lookup"><span data-stu-id="d4998-166">For this example, the script file name is `myresource.rc`.</span></span>  
  
2. <span data-ttu-id="d4998-167">Microsoft Windows リソース コンパイラ (Rc.exe) を使用してスクリプトをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="d4998-167">Compile the script using the Microsoft Windows Resource Compiler (Rc.exe).</span></span> <span data-ttu-id="d4998-168">コマンド プロンプトに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="d4998-168">At the command prompt, type the following command:</span></span>  
  
     `rc myresource.rc`  
  
     <span data-ttu-id="d4998-169">Rc.exe は `myresource.res` リソース ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="d4998-169">Rc.exe produces the `myresource.res` resource file.</span></span>  
  
3. <span data-ttu-id="d4998-170">もう一度アセンブリのソース ファイルをコンパイルし、 **/win32res** オプションを使用してリソース ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="d4998-170">Compile the assembly's source file again and specify the resource file by using the **/win32res** option:</span></span>  
  
    `/win32res:myresource.res`  
  
     <span data-ttu-id="d4998-171">ここでも、`myresource.res` は埋め込むリソースを含むリソース ファイルの名前です。</span><span class="sxs-lookup"><span data-stu-id="d4998-171">Again, `myresource.res` is the name of the resource file containing embedded resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4998-172">関連項目</span><span class="sxs-lookup"><span data-stu-id="d4998-172">See also</span></span>

- [<span data-ttu-id="d4998-173">登録を必要としない COM 相互運用機能</span><span class="sxs-lookup"><span data-stu-id="d4998-173">Registration-Free COM Interop</span></span>](registration-free-com-interop.md)
- <span data-ttu-id="d4998-174">[登録を必要としない COM 相互運用機能の要件](/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d4998-174">[Requirements for Registration-Free COM Interop](/previous-versions/dotnet/netframework-4.0/f8h7012w(v=vs.100))</span></span>
- <span data-ttu-id="d4998-175">[登録を必要としないアクティベーション用の COM コンポーネントの構成](/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d4998-175">[Configuring COM Components for Registration-Free Activation](/previous-versions/dotnet/netframework-4.0/x65a421a(v=vs.100))</span></span>
- <span data-ttu-id="d4998-176">[.NET ベースのコンポーネントの登録を必要としないアクティベーション: チュートリアル](/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span><span class="sxs-lookup"><span data-stu-id="d4998-176">[Registration-Free Activation of .NET-Based Components: A Walkthrough](/previous-versions/dotnet/articles/ms973915(v=msdn.10))</span></span>
