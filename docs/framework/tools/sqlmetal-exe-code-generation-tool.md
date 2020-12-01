---
title: SqlMetal.exe (コード生成ツール)
description: SqlMetal.exe (コード生成ツール) について理解します。 このツールを使用して、.NET の LINQ to SQL コンポーネント用のコードとマッピングを生成します。
ms.date: 03/30/2017
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
ms.openlocfilehash: 4edf11315892ed8267bee17d69a70033348eca5c
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96272567"
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="a4d51-104">SqlMetal.exe (コード生成ツール)</span><span class="sxs-lookup"><span data-stu-id="a4d51-104">SqlMetal.exe (Code Generation Tool)</span></span>

<span data-ttu-id="a4d51-105">SqlMetal コマンドライン ツールは、.NET Framework の [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] コンポーネント用のコードとマッピングを生成します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-105">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the .NET Framework.</span></span> <span data-ttu-id="a4d51-106">このトピックで後述するオプションを適用することにより、次のようなアクションを SqlMetal で実行できます。</span><span class="sxs-lookup"><span data-stu-id="a4d51-106">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
- <span data-ttu-id="a4d51-107">データベースから、ソース コードとマッピング属性またはマッピング ファイルを生成する。</span><span class="sxs-lookup"><span data-stu-id="a4d51-107">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
- <span data-ttu-id="a4d51-108">データベースから、カスタマイズ用の中間的なデータベース マークアップ言語 (.dbml) ファイルを生成する。</span><span class="sxs-lookup"><span data-stu-id="a4d51-108">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
- <span data-ttu-id="a4d51-109">.dbml ファイルから、コードとマッピング属性またはマッピング ファイルを生成する。</span><span class="sxs-lookup"><span data-stu-id="a4d51-109">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="a4d51-110">このツールは、Visual Studio と共に自動的にインストールされます。</span><span class="sxs-lookup"><span data-stu-id="a4d51-110">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="a4d51-111">既定では、このファイルは `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin にあります。</span><span class="sxs-lookup"><span data-stu-id="a4d51-111">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="a4d51-112">Visual Studio をインストールしない場合は、 [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225)をダウンロードすることによって SQLMetal ファイルを入手することもできます。</span><span class="sxs-lookup"><span data-stu-id="a4d51-112">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](https://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4d51-113">Visual Studio を使用する開発者は、オブジェクト リレーショナル デザイナーを使用してエンティティ クラスを生成することもできます。</span><span class="sxs-lookup"><span data-stu-id="a4d51-113">Developers who use Visual Studio can also use the Object Relational Designer to generate entity classes.</span></span> <span data-ttu-id="a4d51-114">コマンド ライン方式は、大きなデータベースにも適切に対応できます。</span><span class="sxs-lookup"><span data-stu-id="a4d51-114">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="a4d51-115">SqlMetal はコマンド ライン ツールであるため、ビルド プロセスでこれを使用できます。</span><span class="sxs-lookup"><span data-stu-id="a4d51-115">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="a4d51-116">このツールを実行するには、Visual Studio 用開発者コマンド プロンプト (または Windows 7 の Visual Studio コマンド プロンプト) を使用します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-116">To run the tool, use the Developer Command Prompt for Visual Studio (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="a4d51-117">詳細については、「[Visual Studio 用開発者コマンド プロンプト](developer-command-prompt-for-vs.md)」を参照してください。コマンド プロンプトで、次のように入力します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-117">For more information, see [Command Prompts](developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4d51-118">構文</span><span class="sxs-lookup"><span data-stu-id="a4d51-118">Syntax</span></span>  
  
```console  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="a4d51-119">Options</span><span class="sxs-lookup"><span data-stu-id="a4d51-119">Options</span></span>  

 <span data-ttu-id="a4d51-120">最新のオプションの一覧を確認するには、コマンド プロンプトでインストール場所に移動し、「 `sqlmetal /?` 」と入力します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-120">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="a4d51-121">**接続オプション**</span><span class="sxs-lookup"><span data-stu-id="a4d51-121">**Connection Options**</span></span>  
  
|<span data-ttu-id="a4d51-122">オプション</span><span class="sxs-lookup"><span data-stu-id="a4d51-122">Option</span></span>|<span data-ttu-id="a4d51-123">説明</span><span class="sxs-lookup"><span data-stu-id="a4d51-123">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a4d51-124">**/server:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="a4d51-124">**/server:** *\<name>*</span></span>|<span data-ttu-id="a4d51-125">データベース サーバーの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-125">Specifies database server name.</span></span>|  
|<span data-ttu-id="a4d51-126">**/database:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="a4d51-126">**/database:** *\<name>*</span></span>|<span data-ttu-id="a4d51-127">サーバー上のデータベース カタログを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-127">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="a4d51-128">**/user:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="a4d51-128">**/user:** *\<name>*</span></span>|<span data-ttu-id="a4d51-129">ログオン ユーザー ID を指定します。既定値:Windows 認証の使用。</span><span class="sxs-lookup"><span data-stu-id="a4d51-129">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="a4d51-130">**/password:** *\<password>*</span><span class="sxs-lookup"><span data-stu-id="a4d51-130">**/password:** *\<password>*</span></span>|<span data-ttu-id="a4d51-131">ログオン パスワードを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-131">Specifies logon password.</span></span> <span data-ttu-id="a4d51-132">既定値:Windows 認証の使用。</span><span class="sxs-lookup"><span data-stu-id="a4d51-132">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="a4d51-133">**/conn:** *\<connection string>*</span><span class="sxs-lookup"><span data-stu-id="a4d51-133">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="a4d51-134">データベース接続文字列を指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-134">Specifies database connection string.</span></span> <span data-ttu-id="a4d51-135">**/server**、 **/database**、 **/user**、または **/password** オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a4d51-135">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="a4d51-136">接続文字列にファイル名は含めないでください。</span><span class="sxs-lookup"><span data-stu-id="a4d51-136">Do not include the file name in the connection string.</span></span> <span data-ttu-id="a4d51-137">代わりに、コマンド ラインにファイル名を入力ファイルとして追加します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-137">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="a4d51-138">たとえば、 **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"** というコマンド ラインは、入力ファイルとして "c:\northwnd.mdf" を指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-138">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="a4d51-139">**/timeout:** *\<seconds>*</span><span class="sxs-lookup"><span data-stu-id="a4d51-139">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="a4d51-140">SqlMetal がデータベースにアクセスする際のタイムアウト値を指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-140">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="a4d51-141">既定値:0 (時間制限なし)。</span><span class="sxs-lookup"><span data-stu-id="a4d51-141">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="a4d51-142">**抽出オプション**</span><span class="sxs-lookup"><span data-stu-id="a4d51-142">**Extraction options**</span></span>  
  
|<span data-ttu-id="a4d51-143">オプション</span><span class="sxs-lookup"><span data-stu-id="a4d51-143">Option</span></span>|<span data-ttu-id="a4d51-144">説明</span><span class="sxs-lookup"><span data-stu-id="a4d51-144">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a4d51-145">**/views**</span><span class="sxs-lookup"><span data-stu-id="a4d51-145">**/views**</span></span>|<span data-ttu-id="a4d51-146">データベース ビューを抽出します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-146">Extracts database views.</span></span>|  
|<span data-ttu-id="a4d51-147">**/functions**</span><span class="sxs-lookup"><span data-stu-id="a4d51-147">**/functions**</span></span>|<span data-ttu-id="a4d51-148">データベース関数を抽出します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-148">Extracts database functions.</span></span>|  
|<span data-ttu-id="a4d51-149">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="a4d51-149">**/sprocs**</span></span>|<span data-ttu-id="a4d51-150">ストアド プロシージャを抽出します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-150">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="a4d51-151">**出力オプション**</span><span class="sxs-lookup"><span data-stu-id="a4d51-151">**Output options**</span></span>  
  
|<span data-ttu-id="a4d51-152">オプション</span><span class="sxs-lookup"><span data-stu-id="a4d51-152">Option</span></span>|<span data-ttu-id="a4d51-153">説明</span><span class="sxs-lookup"><span data-stu-id="a4d51-153">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a4d51-154">**/dbml** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="a4d51-154">**/dbml** *[:file]*</span></span>|<span data-ttu-id="a4d51-155">出力を .dbml として送ります。</span><span class="sxs-lookup"><span data-stu-id="a4d51-155">Sends output as .dbml.</span></span> <span data-ttu-id="a4d51-156">**/map** オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a4d51-156">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="a4d51-157">**/code** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="a4d51-157">**/code** *[:file]*</span></span>|<span data-ttu-id="a4d51-158">出力をソース コードとして送ります。</span><span class="sxs-lookup"><span data-stu-id="a4d51-158">Sends output as source code.</span></span> <span data-ttu-id="a4d51-159">**/dbml** オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a4d51-159">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="a4d51-160">**/map** *[:file]*</span><span class="sxs-lookup"><span data-stu-id="a4d51-160">**/map** *[:file]*</span></span>|<span data-ttu-id="a4d51-161">属性ではなく XML マッピング ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-161">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="a4d51-162">**/dbml** オプションと共に使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="a4d51-162">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="a4d51-163">**その他**</span><span class="sxs-lookup"><span data-stu-id="a4d51-163">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="a4d51-164">オプション</span><span class="sxs-lookup"><span data-stu-id="a4d51-164">Option</span></span>|<span data-ttu-id="a4d51-165">説明</span><span class="sxs-lookup"><span data-stu-id="a4d51-165">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="a4d51-166">**/language:** *\<language>*</span><span class="sxs-lookup"><span data-stu-id="a4d51-166">**/language:** *\<language>*</span></span>|<span data-ttu-id="a4d51-167">ソース コードの言語を指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-167">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="a4d51-168">有効な *\<language>* : vb、csharp。</span><span class="sxs-lookup"><span data-stu-id="a4d51-168">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="a4d51-169">既定値:コード ファイル名の拡張子から派生します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-169">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="a4d51-170">**/namespace:** *\<name>*</span><span class="sxs-lookup"><span data-stu-id="a4d51-170">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="a4d51-171">生成されるコードの名前空間を指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-171">Specifies namespace of the generated code.</span></span> <span data-ttu-id="a4d51-172">既定値は、名前空間なしです。</span><span class="sxs-lookup"><span data-stu-id="a4d51-172">Default value: no namespace.</span></span>|  
|<span data-ttu-id="a4d51-173">**/context:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="a4d51-173">**/context:** *\<type>*</span></span>|<span data-ttu-id="a4d51-174">データ コンテキスト クラスの名前を指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-174">Specifies name of data context class.</span></span> <span data-ttu-id="a4d51-175">既定値:データベース名から派生します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-175">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="a4d51-176">**/entitybase:** *\<type>*</span><span class="sxs-lookup"><span data-stu-id="a4d51-176">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="a4d51-177">生成されるコード内のエンティティ クラスの基本クラスを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-177">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="a4d51-178">既定値:エンティティの基本クラスなしです。</span><span class="sxs-lookup"><span data-stu-id="a4d51-178">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="a4d51-179">**/pluralize**</span><span class="sxs-lookup"><span data-stu-id="a4d51-179">**/pluralize**</span></span>|<span data-ttu-id="a4d51-180">クラスとメンバーの名前を自動的に複数化または単数化します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-180">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="a4d51-181">このオプションは、米国英語バージョンでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="a4d51-181">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="a4d51-182">**/serialization:** *\<option>*</span><span class="sxs-lookup"><span data-stu-id="a4d51-182">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="a4d51-183">シリアル化可能なクラスを生成します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-183">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="a4d51-184">有効な *\<option>* :None と Unidirectional。</span><span class="sxs-lookup"><span data-stu-id="a4d51-184">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="a4d51-185">既定値:なし。</span><span class="sxs-lookup"><span data-stu-id="a4d51-185">Default value: None.</span></span><br /><br /> <span data-ttu-id="a4d51-186">詳細については、「[Serialization](../data/adonet/sql/linq/serialization.md)」 (シリアル化) を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a4d51-186">For more information, see [Serialization](../data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="a4d51-187">**入力ファイル**</span><span class="sxs-lookup"><span data-stu-id="a4d51-187">**Input File**</span></span>  
  
|<span data-ttu-id="a4d51-188">オプション</span><span class="sxs-lookup"><span data-stu-id="a4d51-188">Option</span></span>|<span data-ttu-id="a4d51-189">説明</span><span class="sxs-lookup"><span data-stu-id="a4d51-189">Description</span></span>|  
|------------|-----------------|  
|**\<input file>**|<span data-ttu-id="a4d51-190">SQL Server Express .mdf ファイル、SQL Server Compact 3.5 .sdf ファイル、または .dbml 中間ファイルを指定します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-190">Specifies a SQL Server Express .mdf file, a SQL Server Compact 3.5 .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a4d51-191">Remarks</span><span class="sxs-lookup"><span data-stu-id="a4d51-191">Remarks</span></span>  

 <span data-ttu-id="a4d51-192">SqlMetal の実際の機能には、次の 2 つの段階が含まれています。</span><span class="sxs-lookup"><span data-stu-id="a4d51-192">SqlMetal functionality actually involves two steps:</span></span>  
  
- <span data-ttu-id="a4d51-193">データベースのメタデータを .dbml ファイルに抽出する。</span><span class="sxs-lookup"><span data-stu-id="a4d51-193">Extracting the metadata of the database into a .dbml file.</span></span>  
  
- <span data-ttu-id="a4d51-194">コード出力ファイルを生成する。</span><span class="sxs-lookup"><span data-stu-id="a4d51-194">Generating a code output file.</span></span>  
  
     <span data-ttu-id="a4d51-195">適切なコマンド ライン オプションを使用することで、Visual Basic または C# ソース コードを生成するか、XML マッピング ファイルを生成できます。</span><span class="sxs-lookup"><span data-stu-id="a4d51-195">By using the appropriate command-line options, you can produce Visual Basic or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="a4d51-196">メタデータを .mdf ファイルから抽出するには、他のすべてのオプションの後に .mdf ファイルの名前を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a4d51-196">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="a4d51-197">**/server** を指定しない場合、 **localhost/sqlexpress** と見なされます。</span><span class="sxs-lookup"><span data-stu-id="a4d51-197">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 <span data-ttu-id="a4d51-198">Microsoft SQL Server 2005 は、次の条件が少なくとも 1 つ満たされる場合に例外をスローします。</span><span class="sxs-lookup"><span data-stu-id="a4d51-198">Microsoft SQL Server 2005 throws an exception if one or more of the following conditions are true:</span></span>  
  
- <span data-ttu-id="a4d51-199">自身を呼び出すストアド プロシージャを SqlMetal が抽出しようとした。</span><span class="sxs-lookup"><span data-stu-id="a4d51-199">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
- <span data-ttu-id="a4d51-200">ストアド プロシージャ、関数、またはビューの入れ子レベルが 32 を超える。</span><span class="sxs-lookup"><span data-stu-id="a4d51-200">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="a4d51-201">SqlMetal はこの例外をキャッチして、それを警告として報告します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-201">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="a4d51-202">入力ファイル名を指定するには、その名前をコマンド ラインに入力ファイルとして追加します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-202">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="a4d51-203">( **/conn** オプションを使用して) 接続文字列にファイル名を含める操作は、サポートされていません。</span><span class="sxs-lookup"><span data-stu-id="a4d51-203">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="a4d51-204">使用例</span><span class="sxs-lookup"><span data-stu-id="a4d51-204">Examples</span></span>  

 <span data-ttu-id="a4d51-205">抽出された SQL メタデータを格納する .dbml ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-205">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="a4d51-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="a4d51-206">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="a4d51-207">SQL Server Express を使用して .mdf ファイルから抽出された SQL メタデータを格納する .dbml ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-207">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="a4d51-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="a4d51-208">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="a4d51-209">SQL Server Express から抽出された SQL メタデータを格納する .dbml ファイルを生成します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-209">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="a4d51-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="a4d51-210">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="a4d51-211">.dbml メタデータ ファイルからソース コードを生成します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-211">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="a4d51-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="a4d51-212">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="a4d51-213">SQL メタデータからソース コードを直接生成します。</span><span class="sxs-lookup"><span data-stu-id="a4d51-213">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="a4d51-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="a4d51-214">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a4d51-215">サンプル データベース Northwind で **/pluralize** オプションを使用する場合には、注意を必要とする動作があります。</span><span class="sxs-lookup"><span data-stu-id="a4d51-215">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="a4d51-216">SqlMetal がテーブルのために行型の名前を生成するとき、テーブル名は単数形です。</span><span class="sxs-lookup"><span data-stu-id="a4d51-216">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="a4d51-217">テーブルに関する <xref:System.Data.Linq.DataContext> プロパティを生成するときには、テーブル名は複数形です。</span><span class="sxs-lookup"><span data-stu-id="a4d51-217">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="a4d51-218">偶然にも、サンプル データベース Northwind 内のテーブルには既に複数形が使われています。</span><span class="sxs-lookup"><span data-stu-id="a4d51-218">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="a4d51-219">このため、この部分はうまく機能しません。</span><span class="sxs-lookup"><span data-stu-id="a4d51-219">Therefore, you do not see that part working.</span></span> <span data-ttu-id="a4d51-220">データベース テーブルの名前は単数形にするのが一般的ですが、.NET では、コレクションの名前を複数形にすることも一般的です。</span><span class="sxs-lookup"><span data-stu-id="a4d51-220">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4d51-221">関連項目</span><span class="sxs-lookup"><span data-stu-id="a4d51-221">See also</span></span>

- [<span data-ttu-id="a4d51-222">方法: Visual Basic または C# でオブジェクト モデルを生成する</span><span class="sxs-lookup"><span data-stu-id="a4d51-222">How to: Generate the Object Model in Visual Basic or C#</span></span>](../data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)
- [<span data-ttu-id="a4d51-223">LINQ to SQL でのコード生成</span><span class="sxs-lookup"><span data-stu-id="a4d51-223">Code Generation in LINQ to SQL</span></span>](../data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="a4d51-224">外部マップ</span><span class="sxs-lookup"><span data-stu-id="a4d51-224">External Mapping</span></span>](../data/adonet/sql/linq/external-mapping.md)
