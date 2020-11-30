---
description: csc.exe を使用したコマンド ラインからのビルド
title: csc.exe を使用したコマンド ラインからのビルド
ms.date: 04/19/2017
helpviewer_keywords:
- builds [C#]
- command line [C#]
ms.assetid: 66e70056-dd20-453c-a9b3-507e0478b015
ms.openlocfilehash: 9ffd164602862fce7f5e4f0982d3eda7cb403e60
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "89125931"
---
# <a name="command-line-build-with-cscexe"></a><span data-ttu-id="81424-103">csc.exe を使用したコマンド ラインからのビルド</span><span class="sxs-lookup"><span data-stu-id="81424-103">Command-line build with csc.exe</span></span>

<span data-ttu-id="81424-104">C# コンパイラは、その実行可能ファイルの名前 (*csc.exe*) をコマンド プロンプトに入力することによって呼び出します。</span><span class="sxs-lookup"><span data-stu-id="81424-104">You can invoke the C# compiler by typing the name of its executable file (*csc.exe*) at a command prompt.</span></span>

<span data-ttu-id="81424-105">**Visual Studio 用開発者コマンド プロンプト** ウィンドウを使用した場合、必要なすべての環境変数が設定されます。</span><span class="sxs-lookup"><span data-stu-id="81424-105">If you use the **Developer Command Prompt for Visual Studio** window, all the necessary environment variables are set for you.</span></span> <span data-ttu-id="81424-106">このツールを表示する方法については、「[Visual Studio 用開発者コマンド プロンプト](../../../framework/tools/developer-command-prompt-for-vs.md)」トピックをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="81424-106">For information on how to access this tool, see the [Developer Command Prompt for Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md) topic.</span></span>

<span data-ttu-id="81424-107">標準のコマンド プロンプト ウィンドウを使用する場合は、コンピューター上の任意のサブディレクトリから *csc.exe* を呼び出すことができるようにパスを修正する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81424-107">If you use a standard Command Prompt window, you must adjust your path before you can invoke *csc.exe* from any subdirectory on your computer.</span></span> <span data-ttu-id="81424-108">また、*VsDevCmd.bat* を実行して、コマンド ライン ビルドをサポートするための適切な環境変数を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="81424-108">You also must run *VsDevCmd.bat* to set the appropriate environment variables to support command-line builds.</span></span> <span data-ttu-id="81424-109">検索して実行する方法の手順など、*VsDevCmd.bat* の詳細については、「[Visual Studio のコマンドラインのための環境変数を設定する方法](./how-to-set-environment-variables-for-the-visual-studio-command-line.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81424-109">For more information about *VsDevCmd.bat*, including instructions for how to find and run it, see [How to set environment variables for the Visual Studio Command Line](./how-to-set-environment-variables-for-the-visual-studio-command-line.md).</span></span>

<span data-ttu-id="81424-110">Windows Software Development Kit (SDK) のみがインストールされているコンピューターでは、**SDK コマンド プロンプト** (**[Microsoft .NET Framework SDK]** メニュー オプションから開くことができます) で C# コンパイラを使用できます。</span><span class="sxs-lookup"><span data-stu-id="81424-110">If you're working on a computer that has only the Windows Software Development Kit (SDK), you can use the C# compiler at the **SDK Command Prompt**, which you open from the **Microsoft .NET Framework SDK** menu option.</span></span>

<span data-ttu-id="81424-111">MSBuild を使用して、プログラムによって C# プログラムをビルドすることもできます。</span><span class="sxs-lookup"><span data-stu-id="81424-111">You can also use MSBuild to build C# programs programmatically.</span></span> <span data-ttu-id="81424-112">詳細については、「[MSBuild](/visualstudio/msbuild/msbuild)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81424-112">For more information, see [MSBuild](/visualstudio/msbuild/msbuild).</span></span>

<span data-ttu-id="81424-113">通常、実行可能ファイル *csc.exe* は、*Windows* ディレクトリの Microsoft.NET\Framework\\ *\<Version>* フォルダーに配置されています。</span><span class="sxs-lookup"><span data-stu-id="81424-113">The *csc.exe* executable file usually is located in the Microsoft.NET\Framework\\*\<Version>* folder under the *Windows* directory.</span></span> <span data-ttu-id="81424-114">ただし、この格納場所は、特定のコンピューターの構成によって異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="81424-114">Its location might vary depending on the exact configuration of a particular computer.</span></span> <span data-ttu-id="81424-115">複数のバージョンの .NET Framework がコンピューターにインストールされている場合、このファイルのバージョンが複数見つかります。</span><span class="sxs-lookup"><span data-stu-id="81424-115">If more than one version of the .NET Framework is installed on your computer, you'll find multiple versions of this file.</span></span> <span data-ttu-id="81424-116">このようなインストールの詳細については、「[方法: インストールされている .NET Framework バージョンを確認する](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="81424-116">For more information about such installations, see [How to: determine which versions of the .NET Framework are installed](../../../framework/migration-guide/how-to-determine-which-versions-are-installed.md).</span></span>

> [!TIP]
> <span data-ttu-id="81424-117">Visual Studio IDE を使用してプロジェクトをビルドすると、**csc** コマンドとその関連するコンパイラ オプションが **出力** ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="81424-117">When you build a project by using the Visual Studio IDE, you can display the **csc** command and its associated compiler options in the **Output** window.</span></span> <span data-ttu-id="81424-118">この情報を表示するには、「[方法: ビルド ログ ファイルを表示、保存、および構成する](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log)」の手順に従って、ログ データの詳細レベルを **[標準]** または **[詳細]** に変更します。</span><span class="sxs-lookup"><span data-stu-id="81424-118">To display this information, follow the instructions in [How to: View, Save, and Configure Build Log Files](/visualstudio/ide/how-to-view-save-and-configure-build-log-files#to-change-the-amount-of-information-included-in-the-build-log) to change the verbosity level of the log data to **Normal** or **Detailed**.</span></span> <span data-ttu-id="81424-119">プロジェクトをリビルドした後、C# コンパイラの呼び出しを見つけるために **出力** ウィンドウで **csc** を検索します。</span><span class="sxs-lookup"><span data-stu-id="81424-119">After you rebuild your project, search the **Output** window for **csc** to find the invocation of the C# compiler.</span></span>

 <span data-ttu-id="81424-120">**このトピックの内容**</span><span class="sxs-lookup"><span data-stu-id="81424-120">**In this topic**</span></span>

- [<span data-ttu-id="81424-121">コマンド ライン構文の規則</span><span class="sxs-lookup"><span data-stu-id="81424-121">Rules for command-line syntax</span></span>](#rules-for-command-line-syntax-for-the-c-compiler)

- [<span data-ttu-id="81424-122">サンプル コマンド ライン</span><span class="sxs-lookup"><span data-stu-id="81424-122">Sample command lines</span></span>](#sample-command-lines-for-the-c-compiler)

- [<span data-ttu-id="81424-123">C# コンパイラと C++ コンパイラの出力の相違点</span><span class="sxs-lookup"><span data-stu-id="81424-123">Differences between C# compiler and C++ compiler output</span></span>](#differences-between-c-compiler-and-c-compiler-output)

## <a name="rules-for-command-line-syntax-for-the-c-compiler"></a><span data-ttu-id="81424-124">C# コンパイラのコマンド ライン構文の規則</span><span class="sxs-lookup"><span data-stu-id="81424-124">Rules for command-line syntax for the C# compiler</span></span>

<span data-ttu-id="81424-125">C# コンパイラは、オペレーティング システムのコマンド ラインで指定された引数を次の規則に従って解釈します。</span><span class="sxs-lookup"><span data-stu-id="81424-125">The C# compiler uses the following rules when it interprets arguments given on the operating system command line:</span></span>

- <span data-ttu-id="81424-126">引数は、空白 (スペースまたはタブ) で区切ります。</span><span class="sxs-lookup"><span data-stu-id="81424-126">Arguments are delimited by white space, which is either a space or a tab.</span></span>

- <span data-ttu-id="81424-127">キャレット (^) は、エスケープ文字やデリミターとしては認識されません。</span><span class="sxs-lookup"><span data-stu-id="81424-127">The caret character (^) is not recognized as an escape character or delimiter.</span></span> <span data-ttu-id="81424-128">キャレットは、オペレーティング システムのコマンド ライン パーサーによって処理されてからプログラムの `argv` 配列に渡されます。</span><span class="sxs-lookup"><span data-stu-id="81424-128">The character is handled by the command-line parser in the operating system before it's passed to the `argv` array in the program.</span></span>

- <span data-ttu-id="81424-129">二重引用符で囲まれた文字列 ("string") は、空白を含む場合でも、単一の引数と見なされます。</span><span class="sxs-lookup"><span data-stu-id="81424-129">A string enclosed in double quotation marks ("string") is interpreted as a single argument, regardless of white space that is contained within.</span></span> <span data-ttu-id="81424-130">二重引用符で囲んだ文字列を引数に埋め込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="81424-130">A quoted string can be embedded in an argument.</span></span>

- <span data-ttu-id="81424-131">円記号を前に付けた二重引用符 (\\") は、リテラル二重引用符文字 (") として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="81424-131">A double quotation mark preceded by a backslash (\\") is interpreted as a literal double quotation mark character (").</span></span>

- <span data-ttu-id="81424-132">二重引用符の直前にある円記号以外は、円記号 (\) として解釈されます。</span><span class="sxs-lookup"><span data-stu-id="81424-132">Backslashes are interpreted literally, unless they immediately precede a double quotation mark.</span></span>

- <span data-ttu-id="81424-133">二重引用符の直前に円記号が偶数個 (0 個は含まない) あると、円記号のペアごとに 1 個の円記号が `argv` 配列に格納されます。この場合、二重引用符は文字列のデリミターとして解釈されます。</span><span class="sxs-lookup"><span data-stu-id="81424-133">If an even number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is interpreted as a string delimiter.</span></span>

- <span data-ttu-id="81424-134">二重引用符の直前に円記号が奇数個 (3 個以上) あると、円記号のペアごとに 1 個の円記号が `argv` 配列に格納されます。この場合、二重引用符は残った円記号によりエスケープ シーケンスになります。</span><span class="sxs-lookup"><span data-stu-id="81424-134">If an odd number of backslashes is followed by a double quotation mark, one backslash is put in the `argv` array for every pair of backslashes, and the double quotation mark is "escaped" by the remaining backslash.</span></span> <span data-ttu-id="81424-135">これにより、リテラル二重引用符 (") が `argv` に追加されます。</span><span class="sxs-lookup"><span data-stu-id="81424-135">This causes a literal double quotation mark (") to be added in `argv`.</span></span>

## <a name="sample-command-lines-for-the-c-compiler"></a><span data-ttu-id="81424-136">C# コンパイラのコマンド ラインのサンプル</span><span class="sxs-lookup"><span data-stu-id="81424-136">Sample command lines for the C# compiler</span></span>

- <span data-ttu-id="81424-137">*File.cs* をコンパイルして *File.exe* を作成します。</span><span class="sxs-lookup"><span data-stu-id="81424-137">Compiles *File.cs* producing *File.exe*:</span></span>

  ```console
  csc File.cs
  ```

- <span data-ttu-id="81424-138">*File.cs* をコンパイルして *File.dll* を作成します。</span><span class="sxs-lookup"><span data-stu-id="81424-138">Compiles *File.cs* producing *File.dll*:</span></span>

  ```console
  csc -target:library File.cs
  ```

- <span data-ttu-id="81424-139">*File.cs* をコンパイルして *My.exe* を作成します。</span><span class="sxs-lookup"><span data-stu-id="81424-139">Compiles *File.cs* and creates *My.exe*:</span></span>

  ```console
  csc -out:My.exe File.cs
  ```

- <span data-ttu-id="81424-140">最適化を有効にし、DEBUG シンボルを定義して、現在のディレクトリにあるすべての C# ファイルをコンパイルします。</span><span class="sxs-lookup"><span data-stu-id="81424-140">Compiles all the C# files in the current directory with optimizations enabled and defines the DEBUG symbol.</span></span> <span data-ttu-id="81424-141">*File2.exe* が出力されます。</span><span class="sxs-lookup"><span data-stu-id="81424-141">The output is *File2.exe*:</span></span>

  ```console
  csc -define:DEBUG -optimize -out:File2.exe *.cs
  ```

- <span data-ttu-id="81424-142">現在のディレクトリにあるすべての C# ファイルをコンパイルして、デバッグ バージョンの *File2.dll* を作成します。</span><span class="sxs-lookup"><span data-stu-id="81424-142">Compiles all the C# files in the current directory producing a debug version of *File2.dll*.</span></span> <span data-ttu-id="81424-143">ロゴや警告は表示されません。</span><span class="sxs-lookup"><span data-stu-id="81424-143">No logo and no warnings are displayed:</span></span>

  ```console
  csc -target:library -out:File2.dll -warn:0 -nologo -debug *.cs
  ```

- <span data-ttu-id="81424-144">現在のディレクトリにあるすべての C# ファイルをコンパイルして、*Something.xyz* (DLL) に出力します。</span><span class="sxs-lookup"><span data-stu-id="81424-144">Compiles all the C# files in the current directory to *Something.xyz* (a DLL):</span></span>

  ```console
  csc -target:library -out:Something.xyz *.cs
  ```

## <a name="differences-between-c-compiler-and-c-compiler-output"></a><span data-ttu-id="81424-145">C# コンパイラと C++ コンパイラの出力の相違点</span><span class="sxs-lookup"><span data-stu-id="81424-145">Differences between C# compiler and C++ compiler output</span></span>

<span data-ttu-id="81424-146">C# コンパイラを起動してもオブジェクト ( *.obj*) ファイルは作成されず、出力ファイルが直接作成されます。</span><span class="sxs-lookup"><span data-stu-id="81424-146">There are no object (*.obj*) files created as a result of invoking the C# compiler; output files are created directly.</span></span> <span data-ttu-id="81424-147">このため、C# コンパイラにはリンカーが不要です。</span><span class="sxs-lookup"><span data-stu-id="81424-147">As a result of this, the C# compiler does not need a linker.</span></span>

## <a name="see-also"></a><span data-ttu-id="81424-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="81424-148">See also</span></span>

- [<span data-ttu-id="81424-149">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="81424-149">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="81424-150">アルファベット順の C# コンパイラ オプションの一覧</span><span class="sxs-lookup"><span data-stu-id="81424-150">C# Compiler Options Listed Alphabetically</span></span>](./listed-alphabetically.md)
- [<span data-ttu-id="81424-151">カテゴリ別の C# コンパイラ オプションの一覧</span><span class="sxs-lookup"><span data-stu-id="81424-151">C# Compiler Options Listed by Category</span></span>](./listed-by-category.md)
- [<span data-ttu-id="81424-152">Main() とコマンドライン引数</span><span class="sxs-lookup"><span data-stu-id="81424-152">Main() and Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/index.md)
- [<span data-ttu-id="81424-153">コマンド ライン引数</span><span class="sxs-lookup"><span data-stu-id="81424-153">Command-Line Arguments</span></span>](../../programming-guide/main-and-command-args/command-line-arguments.md)
- [<span data-ttu-id="81424-154">コマンド ライン引数を表示する方法</span><span class="sxs-lookup"><span data-stu-id="81424-154">How to display command-line arguments</span></span>](../../programming-guide/main-and-command-args/how-to-display-command-line-arguments.md)
- [<span data-ttu-id="81424-155">Main() の戻り値</span><span class="sxs-lookup"><span data-stu-id="81424-155">Main() Return Values</span></span>](../../programming-guide/main-and-command-args/main-return-values.md)
