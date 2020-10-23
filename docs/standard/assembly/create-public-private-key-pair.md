---
title: '方法: 公開キーと秘密キーのキー ペアを作成する'
description: 厳密な名前が付いたアセンブリが作成するためにコンパイル時に利用される、公開キーと秘密キーからなる暗号鍵の組み合わせを作成する方法について説明します。
ms.date: 08/20/2019
helpviewer_keywords:
- key pairs for strong-named assemblies
- signing assemblies
- assemblies [.NET], signing
- cryptographic key pairs
- snk files (key pair files)
- public-private key pairs
- .snk files
- strong-named assemblies, key pairs
ms.assetid: 05026813-f3bd-4d7c-9e0b-fc588eb3d114
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: c42e98a7e27ded9a21445fae35ade843e834076a
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163494"
---
# <a name="how-to-create-a-public-private-key-pair"></a><span data-ttu-id="a0796-103">方法: 公開キーと秘密キーのキー ペアを作成する</span><span class="sxs-lookup"><span data-stu-id="a0796-103">How to: Create a public-private key pair</span></span>

<span data-ttu-id="a0796-104">アセンブリに厳密な名前で署名するには、公開/秘密キーの組み合わせが必要です。</span><span class="sxs-lookup"><span data-stu-id="a0796-104">To sign an assembly with a strong name, you must have a public/private key pair.</span></span> <span data-ttu-id="a0796-105">このような公開キーと秘密キーからなる暗号鍵の組み合わせがコンパイル時に利用され、厳密な名前が付いたアセンブリが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a0796-105">This public and private cryptographic key pair is used during compilation to create a strong-named assembly.</span></span> <span data-ttu-id="a0796-106">キーの組み合わせは[厳密名ツール (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) を利用して作成できます。</span><span class="sxs-lookup"><span data-stu-id="a0796-106">You can create a key pair using the [Strong Name tool (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md).</span></span> <span data-ttu-id="a0796-107">キー ペア ファイルには通常、 *.snk* 拡張子が与えられます。</span><span class="sxs-lookup"><span data-stu-id="a0796-107">Key pair files usually have an *.snk* extension.</span></span>

> [!NOTE]
> <span data-ttu-id="a0796-108">Visual Studio では、C# と Visual Basic のプロジェクト プロパティ ページに **[署名]** タブがあります。ここで、*Sn.exe* を使用することなく、既存のキー ファイルを選択したり、新しいキー ファイルを生成したりすることができます。</span><span class="sxs-lookup"><span data-stu-id="a0796-108">In Visual Studio, the C# and Visual Basic project property pages include a **Signing** tab that enables you to select existing key files or to generate new key files without using *Sn.exe*.</span></span> <span data-ttu-id="a0796-109">Visual C++ では、 **[プロパティ ページ]** ウィンドウの **[構成プロパティ]** セクションの **[リンカー]** セクションの **[詳細設定]** プロパティ ページで既存のキー ファイルの場所を指定できます。</span><span class="sxs-lookup"><span data-stu-id="a0796-109">In Visual C++, you can specify the location of an existing key file in the **Advanced** property page in the **Linker** section of the **Configuration Properties** section of the **Property Pages** window.</span></span> <span data-ttu-id="a0796-110">Visual Studio 2005 より、キー ファイル ペアを特定する <xref:System.Reflection.AssemblyKeyFileAttribute> 属性を使用できなくなりました。</span><span class="sxs-lookup"><span data-stu-id="a0796-110">The use of the <xref:System.Reflection.AssemblyKeyFileAttribute> attribute to identify key file pairs was made obsolete beginning with Visual Studio 2005.</span></span>

## <a name="create-a-key-pair"></a><span data-ttu-id="a0796-111">キー ペアを作成する</span><span class="sxs-lookup"><span data-stu-id="a0796-111">Create a key pair</span></span>

<span data-ttu-id="a0796-112">キー ペアを作成するには、コマンド プロンプトに次のコマンドを入力します。</span><span class="sxs-lookup"><span data-stu-id="a0796-112">To create a key pair, at a command prompt, type the following command:</span></span>

<span data-ttu-id="a0796-113">**sn –k** \<*file name*></span><span class="sxs-lookup"><span data-stu-id="a0796-113">**sn –k** \<*file name*></span></span>

<span data-ttu-id="a0796-114">このコマンドでは、*ファイル名*はキー ペアを含む出力ファイルの名前になります。</span><span class="sxs-lookup"><span data-stu-id="a0796-114">In this command, *file name* is the name of the output file containing the key pair.</span></span>

<span data-ttu-id="a0796-115">次の例では、*sgKey.snk* という名前のキー ペアが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a0796-115">The following example creates a key pair called *sgKey.snk*.</span></span>

```cmd
sn -k sgKey.snk
```

<span data-ttu-id="a0796-116">アセンブリに遅延署名する予定であり、キー ペア全体を制御する (テスト シナリオの範囲を超えることは予期されない) のであれば、次のコマンドを利用してキー ペアを生成し、それから個別ファイルに公開キーを抽出できます。</span><span class="sxs-lookup"><span data-stu-id="a0796-116">If you intend to delay sign an assembly and you control the whole key pair (which is unlikely outside test scenarios), you can use the following commands to generate a key pair and then extract the public key from it into a separate file.</span></span> <span data-ttu-id="a0796-117">最初に、キー ペアを作成します。</span><span class="sxs-lookup"><span data-stu-id="a0796-117">First, create the key pair:</span></span>

```cmd
sn -k keypair.snk
```

<span data-ttu-id="a0796-118">次に、キー ペアから公開キーを抽出し、それを個別ファイルにコピーします。</span><span class="sxs-lookup"><span data-stu-id="a0796-118">Next, extract the public key from the key pair and copy it to a separate file:</span></span>

```cmd
sn -p keypair.snk public.snk
```

<span data-ttu-id="a0796-119">キー ペアを作成したら、厳密な名前の署名ツールで見つけられる場所にファイルを置く必要があります。</span><span class="sxs-lookup"><span data-stu-id="a0796-119">Once you create the key pair, you must put the file where the strong name signing tools can find it.</span></span>

<span data-ttu-id="a0796-120">厳密な名前でアセンブリに署名すると、[アセンブリ リンカー (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) は、現在のディレクトリと出力ディレクトリを基準にしてキー ファイルを検索します。</span><span class="sxs-lookup"><span data-stu-id="a0796-120">When signing an assembly with a strong name, the [Assembly Linker (Al.exe)](../../framework/tools/al-exe-assembly-linker.md) looks for the key file relative to the current directory and to the output directory.</span></span> <span data-ttu-id="a0796-121">コマンド ライン コンパイラを使用する場合は、コード モジュールを格納する現在のディレクトリにキーをコピーするだけで十分です。</span><span class="sxs-lookup"><span data-stu-id="a0796-121">When using command-line compilers, you can simply copy the key to the current directory containing your code modules.</span></span>

<span data-ttu-id="a0796-122">プロジェクト プロパティに **[署名]** タブがない以前のバージョンの Visual Studio を利用している場合、キー ファイルの推奨場所はファイル属性が次のように指定されたプロジェクト ディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="a0796-122">If you are using an earlier version of Visual Studio that does not have a **Signing** tab in the project properties, the recommended key file location is the project directory with the file attribute specified as follows:</span></span>

```cpp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")];
```

```csharp
[assembly:AssemblyKeyFileAttribute("keyfile.snk")]
```

```vb
<Assembly:AssemblyKeyFileAttribute("keyfile.snk")>
```

## <a name="see-also"></a><span data-ttu-id="a0796-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="a0796-123">See also</span></span>

- [<span data-ttu-id="a0796-124">厳密な名前付きアセンブリの作成と使用</span><span class="sxs-lookup"><span data-stu-id="a0796-124">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
