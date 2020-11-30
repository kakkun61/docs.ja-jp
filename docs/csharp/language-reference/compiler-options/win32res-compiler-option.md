---
description: -win32res (C# コンパイラ オプション)
title: -win32res (C# コンパイラ オプション)
ms.date: 07/20/2015
f1_keywords:
- /win32res
helpviewer_keywords:
- win32res compiler option
- /win32res compiler option [C#]
- -win32res compiler option [C#]
- win32res compiler option [C#]
ms.assetid: 3c33f750-6948-4c7e-a27e-bef98f77255b
ms.openlocfilehash: 442c788595a01db9c0a1196d9e13b2a98963a38c
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "91204347"
---
# <a name="-win32res-c-compiler-options"></a><span data-ttu-id="75851-103">-win32res (C# コンパイラ オプション)</span><span class="sxs-lookup"><span data-stu-id="75851-103">-win32res (C# Compiler Options)</span></span>

<span data-ttu-id="75851-104">**-win32res** オプションは、Win32 リソースを出力ファイルに挿入します。</span><span class="sxs-lookup"><span data-stu-id="75851-104">The **-win32res** option inserts a Win32 resource in the output file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75851-105">構文</span><span class="sxs-lookup"><span data-stu-id="75851-105">Syntax</span></span>  
  
```console  
-win32res:filename  
```  
  
## <a name="arguments"></a><span data-ttu-id="75851-106">引数</span><span class="sxs-lookup"><span data-stu-id="75851-106">Arguments</span></span>  

 `filename`  
 <span data-ttu-id="75851-107">出力ファイルに追加するリソース ファイル。</span><span class="sxs-lookup"><span data-stu-id="75851-107">The resource file that you want to add to your output file.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75851-108">注釈</span><span class="sxs-lookup"><span data-stu-id="75851-108">Remarks</span></span>  

 <span data-ttu-id="75851-109">Win32 リソース ファイルは、[リソース コンパイラ](resource-compiler-option.md)を使用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="75851-109">A Win32 resource file can be created with the [Resource Compiler](resource-compiler-option.md).</span></span> <span data-ttu-id="75851-110">リソース コンパイラは、Visual C++ プログラムをコンパイルするときに呼び出されます。 .res ファイルは .rc ファイルから作成されます。</span><span class="sxs-lookup"><span data-stu-id="75851-110">The Resource Compiler is invoked when you compile a Visual C++ program; a .res file is created from the .rc file.</span></span>  
  
 <span data-ttu-id="75851-111">Win32 リソースは、バージョンまたはビットマップ (アイコン) 情報を格納できます。エクスプローラーでアプリケーションを識別するのに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="75851-111">A Win32 resource can contain version or bitmap (icon) information that would help identify your application in the File Explorer.</span></span> <span data-ttu-id="75851-112">**-win32res** を指定しない場合、コンパイラはアセンブリ バージョンに基づいてバージョン情報を生成します。</span><span class="sxs-lookup"><span data-stu-id="75851-112">If you do not specify **-win32res**, the compiler will generate version information based on the assembly version.</span></span>  
  
 <span data-ttu-id="75851-113">.NET Framework リソース ファイルの [-linkresource](./linkresource-compiler-option.md) (参照) または [-resource](./resource-compiler-option.md) (アタッチ) をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="75851-113">See [-linkresource](./linkresource-compiler-option.md) (to reference) or [-resource](./resource-compiler-option.md) (to attach) a .NET Framework resource file.</span></span>  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a><span data-ttu-id="75851-114">Visual Studio 開発環境でこのコンパイラ オプションを設定するには</span><span class="sxs-lookup"><span data-stu-id="75851-114">To set this compiler option in the Visual Studio development environment</span></span>  
  
1. <span data-ttu-id="75851-115">プロジェクトの **[プロパティ]** ページを開きます。</span><span class="sxs-lookup"><span data-stu-id="75851-115">Open the project's **Properties** page.</span></span>  
  
2. <span data-ttu-id="75851-116">**[アプリケーション]** プロパティ ページをクリックします。</span><span class="sxs-lookup"><span data-stu-id="75851-116">Click the **Application** property page.</span></span>  
  
3. <span data-ttu-id="75851-117">**[リソース ファイル]** ボタンをクリックし、コンボ ボックスを利用してファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="75851-117">Click on the **Resource File** button and choose a file by using the combo box.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75851-118">例</span><span class="sxs-lookup"><span data-stu-id="75851-118">Example</span></span>  

 <span data-ttu-id="75851-119">`in.cs` をコンパイルし、Win32 リソース ファイル `rf.res` をアタッチし、`in.exe` を作成します。</span><span class="sxs-lookup"><span data-stu-id="75851-119">Compile `in.cs` and attach a Win32 resource file `rf.res` to produce `in.exe`:</span></span>  
  
```console  
csc -win32res:rf.res in.cs  
```  
  
## <a name="see-also"></a><span data-ttu-id="75851-120">関連項目</span><span class="sxs-lookup"><span data-stu-id="75851-120">See also</span></span>

- [<span data-ttu-id="75851-121">C# コンパイラ オプション</span><span class="sxs-lookup"><span data-stu-id="75851-121">C# Compiler Options</span></span>](./index.md)
- [<span data-ttu-id="75851-122">プロジェクトおよびソリューションのプロパティの管理</span><span class="sxs-lookup"><span data-stu-id="75851-122">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
