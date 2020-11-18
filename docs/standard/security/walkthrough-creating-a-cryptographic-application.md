---
title: 'チュートリアル: 暗号化アプリケーションの作成'
description: 暗号化アプリケーションの作成について説明します。 Windows フォームアプリケーションでコンテンツを暗号化および復号化する方法について説明します。
ms.date: 07/14/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [NET], example
- cryptography [NET], cryptographic application example
- cryptography [NET], application example
ms.assetid: abf48c11-1e72-431d-9562-39cf23e1a8ff
ms.openlocfilehash: 70218d60abb336cdb35fc2e89e62a50b6bd79c67
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94830559"
---
# <a name="walkthrough-creating-a-cryptographic-application"></a><span data-ttu-id="af660-104">チュートリアル: 暗号化アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="af660-104">Walkthrough: Creating a Cryptographic Application</span></span>

> [!NOTE]
> <span data-ttu-id="af660-105">この記事は、Windows に適用されます。</span><span class="sxs-lookup"><span data-stu-id="af660-105">This article applies to Windows.</span></span>
>
> <span data-ttu-id="af660-106">ASP.NET Core の詳細については、「 [データ保護の ASP.NET Core](/aspnet/core/security/data-protection/introduction)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af660-106">For information about ASP.NET Core, see [ASP.NET Core Data Protection](/aspnet/core/security/data-protection/introduction).</span></span>

<span data-ttu-id="af660-107">このチュートリアルでは、コンテンツの暗号化および復号化の方法を示します。</span><span class="sxs-lookup"><span data-stu-id="af660-107">This walkthrough demonstrates how to encrypt and decrypt content.</span></span> <span data-ttu-id="af660-108">コード例は、Windows フォーム アプリケーション向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="af660-108">The code examples are designed for a Windows Forms application.</span></span> <span data-ttu-id="af660-109">このアプリケーションは、スマート カードを使用するなどの実際のシナリオは示していません。</span><span class="sxs-lookup"><span data-stu-id="af660-109">This application does not demonstrate real world scenarios, such as using smart cards.</span></span> <span data-ttu-id="af660-110">代わりに、暗号化と復号化の基礎を示しています。</span><span class="sxs-lookup"><span data-stu-id="af660-110">Instead, it demonstrates the fundamentals of encryption and decryption.</span></span>  
  
<span data-ttu-id="af660-111">このチュートリアルでは、次の暗号化のガイドラインを使用します。</span><span class="sxs-lookup"><span data-stu-id="af660-111">This walkthrough uses the following guidelines for encryption:</span></span>  
  
- <span data-ttu-id="af660-112">自動生成される <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> と <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A> を使用すると、対称アルゴリズムである <xref:System.Security.Cryptography.Aes> クラスでデータの暗号化と復号化を行えます。</span><span class="sxs-lookup"><span data-stu-id="af660-112">Use the <xref:System.Security.Cryptography.Aes> class, a symmetric algorithm, to encrypt and decrypt data by using its automatically generated <xref:System.Security.Cryptography.SymmetricAlgorithm.Key%2A> and <xref:System.Security.Cryptography.SymmetricAlgorithm.IV%2A>.</span></span>  
  
- <span data-ttu-id="af660-113">非対称アルゴリズムを使用し <xref:System.Security.Cryptography.RSA> て、によって暗号化されたデータに対してキーを暗号化および暗号化解除し <xref:System.Security.Cryptography.Aes> ます。</span><span class="sxs-lookup"><span data-stu-id="af660-113">Use the <xref:System.Security.Cryptography.RSA> asymmetric algorithm to encrypt and decrypt the key to the data encrypted by <xref:System.Security.Cryptography.Aes>.</span></span> <span data-ttu-id="af660-114">非対称アルゴリズムは、キーなどの少量のデータに最適です。</span><span class="sxs-lookup"><span data-stu-id="af660-114">Asymmetric algorithms are best used for smaller amounts of data, such as a key.</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="af660-115">暗号化されたコンテンツを他のユーザーと交換するのではなく、コンピューター上のデータを保護する場合は、クラスの使用を検討してください <xref:System.Security.Cryptography.ProtectedData> 。</span><span class="sxs-lookup"><span data-stu-id="af660-115">If you want to protect data on your computer instead of exchanging encrypted content with other people, consider using the <xref:System.Security.Cryptography.ProtectedData> class.</span></span>  
  
 <span data-ttu-id="af660-116">次の表は、このトピックの暗号化のタスクをまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="af660-116">The following table summarizes the cryptographic tasks in this topic.</span></span>  
  
|<span data-ttu-id="af660-117">タスク</span><span class="sxs-lookup"><span data-stu-id="af660-117">Task</span></span>|<span data-ttu-id="af660-118">説明</span><span class="sxs-lookup"><span data-stu-id="af660-118">Description</span></span>|  
|----------|-----------------|  
|<span data-ttu-id="af660-119">Windows フォーム アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="af660-119">Creating a Windows Forms application</span></span>|<span data-ttu-id="af660-120">アプリケーションを実行するために必要なコントロールの一覧を表示します。</span><span class="sxs-lookup"><span data-stu-id="af660-120">Lists the controls that are required to run the application.</span></span>|  
|<span data-ttu-id="af660-121">グローバル オブジェクトの宣言</span><span class="sxs-lookup"><span data-stu-id="af660-121">Declaring global objects</span></span>|<span data-ttu-id="af660-122">文字列のパスの変数、<xref:System.Security.Cryptography.CspParameters>、および <xref:System.Security.Cryptography.RSACryptoServiceProvider> を宣言して、<xref:System.Windows.Forms.Form> クラスのグローバル コンテキストを指定します。</span><span class="sxs-lookup"><span data-stu-id="af660-122">Declares string path variables, the <xref:System.Security.Cryptography.CspParameters>, and the <xref:System.Security.Cryptography.RSACryptoServiceProvider> to have global context of the <xref:System.Windows.Forms.Form> class.</span></span>|  
|<span data-ttu-id="af660-123">非対称キーを作成する</span><span class="sxs-lookup"><span data-stu-id="af660-123">Creating an asymmetric key</span></span>|<span data-ttu-id="af660-124">非対称の公開キーと秘密キーの値のペアを作成し、これにキー コンテナー名を割り当てます。</span><span class="sxs-lookup"><span data-stu-id="af660-124">Creates an asymmetric public and private key value pair and assigns it a key container name.</span></span>|  
|<span data-ttu-id="af660-125">ファイルの暗号化</span><span class="sxs-lookup"><span data-stu-id="af660-125">Encrypting a file</span></span>|<span data-ttu-id="af660-126">暗号化するファイルを選択するダイアログ ボックスを表示し、ファイルを暗号化します。</span><span class="sxs-lookup"><span data-stu-id="af660-126">Displays a dialog box to select a file for encryption and encrypts the file.</span></span>|  
|<span data-ttu-id="af660-127">ファイルの復号化</span><span class="sxs-lookup"><span data-stu-id="af660-127">Decrypting a file</span></span>|<span data-ttu-id="af660-128">復号化する暗号化されたファイルを選択するダイアログ ボックスを表示し、ファイルを復号化します。</span><span class="sxs-lookup"><span data-stu-id="af660-128">Displays a dialog box to select an encrypted file for decryption and decrypts the file.</span></span>|  
|<span data-ttu-id="af660-129">秘密キーの取得</span><span class="sxs-lookup"><span data-stu-id="af660-129">Getting a private key</span></span>|<span data-ttu-id="af660-130">キー コンテナー名を使用して、完全なキーのペアを取得します。</span><span class="sxs-lookup"><span data-stu-id="af660-130">Gets the full key pair using the key container name.</span></span>|  
|<span data-ttu-id="af660-131">公開キーのエクスポート</span><span class="sxs-lookup"><span data-stu-id="af660-131">Exporting a public key</span></span>|<span data-ttu-id="af660-132">パブリック パラメーターのみで XML ファイルにキーを保存します。</span><span class="sxs-lookup"><span data-stu-id="af660-132">Saves the key to an XML file with only public parameters.</span></span>|  
|<span data-ttu-id="af660-133">公開キーのインポート</span><span class="sxs-lookup"><span data-stu-id="af660-133">Importing a public key</span></span>|<span data-ttu-id="af660-134">キーを XML ファイルからキー コンテナーに読み込みます。</span><span class="sxs-lookup"><span data-stu-id="af660-134">Loads the key from an XML file into the key container.</span></span>|  
|<span data-ttu-id="af660-135">アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="af660-135">Testing the application</span></span>|<span data-ttu-id="af660-136">このアプリケーションをテストするための手順を一覧に示します。</span><span class="sxs-lookup"><span data-stu-id="af660-136">Lists procedures for testing this application.</span></span>|  
  
## <a name="prerequisites"></a><span data-ttu-id="af660-137">必須コンポーネント</span><span class="sxs-lookup"><span data-stu-id="af660-137">Prerequisites</span></span>  

<span data-ttu-id="af660-138">このチュートリアルを実行するには、次のコンポーネントが必要です。</span><span class="sxs-lookup"><span data-stu-id="af660-138">You need the following components to complete this walkthrough:</span></span>  
  
- <span data-ttu-id="af660-139"><xref:System.IO> 名前空間と <xref:System.Security.Cryptography> 名前空間への参照。</span><span class="sxs-lookup"><span data-stu-id="af660-139">References to the <xref:System.IO> and <xref:System.Security.Cryptography> namespaces.</span></span>  
  
## <a name="creating-a-windows-forms-application"></a><span data-ttu-id="af660-140">Windows フォーム アプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="af660-140">Creating a Windows Forms Application</span></span>  

<span data-ttu-id="af660-141">このチュートリアルにあるほとんどのコード例は、ボタン コントロールのイベント ハンドラーとして設計されています。</span><span class="sxs-lookup"><span data-stu-id="af660-141">Most of the code examples in this walkthrough are designed to be event handlers for button controls.</span></span> <span data-ttu-id="af660-142">次の表は、サンプル アプリケーションに必要なコントロールと、コード例に一致する必要な名前を示しています。</span><span class="sxs-lookup"><span data-stu-id="af660-142">The following table lists the controls required for the sample application and their required names to match the code examples.</span></span>  
  
|<span data-ttu-id="af660-143">Control</span><span class="sxs-lookup"><span data-stu-id="af660-143">Control</span></span>|<span data-ttu-id="af660-144">名前</span><span class="sxs-lookup"><span data-stu-id="af660-144">Name</span></span>|<span data-ttu-id="af660-145">テキストのプロパティ (必要に応じて)</span><span class="sxs-lookup"><span data-stu-id="af660-145">Text property (as needed)</span></span>|  
|-------------|----------|---------------------------------|  
|<xref:System.Windows.Forms.Button>|`buttonEncryptFile`|<span data-ttu-id="af660-146">ファイルの暗号化</span><span class="sxs-lookup"><span data-stu-id="af660-146">Encrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonDecryptFile`|<span data-ttu-id="af660-147">ファイルの復号化</span><span class="sxs-lookup"><span data-stu-id="af660-147">Decrypt File</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonCreateAsmKeys`|<span data-ttu-id="af660-148">キーの作成</span><span class="sxs-lookup"><span data-stu-id="af660-148">Create Keys</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonExportPublicKey`|<span data-ttu-id="af660-149">公開キーのエクスポート</span><span class="sxs-lookup"><span data-stu-id="af660-149">Export Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonImportPublicKey`|<span data-ttu-id="af660-150">公開キーのインポート</span><span class="sxs-lookup"><span data-stu-id="af660-150">Import Public Key</span></span>|  
|<xref:System.Windows.Forms.Button>|`buttonGetPrivateKey`|<span data-ttu-id="af660-151">秘密キーの取得</span><span class="sxs-lookup"><span data-stu-id="af660-151">Get Private Key</span></span>|  
|<xref:System.Windows.Forms.Label>|`label1`|<span data-ttu-id="af660-152">キーが設定されていません</span><span class="sxs-lookup"><span data-stu-id="af660-152">Key not set</span></span>|  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog1`||  
|<xref:System.Windows.Forms.OpenFileDialog>|`openFileDialog2`||  
  
 <span data-ttu-id="af660-153">イベントハンドラーを作成するには、Visual Studio デザイナーのボタンをダブルクリックします。</span><span class="sxs-lookup"><span data-stu-id="af660-153">Double-click the buttons in the Visual Studio designer to create their event handlers.</span></span>
  
## <a name="declaring-global-objects"></a><span data-ttu-id="af660-154">グローバル オブジェクトの宣言</span><span class="sxs-lookup"><span data-stu-id="af660-154">Declaring Global Objects</span></span>  

<span data-ttu-id="af660-155">次のコードをフォームのコンストラクターに追加します。</span><span class="sxs-lookup"><span data-stu-id="af660-155">Add the following code to the Form's constructor.</span></span> <span data-ttu-id="af660-156">環境とユーザー設定のための文字列変数を編集します。</span><span class="sxs-lookup"><span data-stu-id="af660-156">Edit the string variables for your environment and preferences.</span></span>  
  
[!code-csharp[CryptoWalkThru#1](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#1)]
[!code-vb[CryptoWalkThru#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#1)]  
  
## <a name="creating-an-asymmetric-key"></a><span data-ttu-id="af660-157">非対称キーの作成</span><span class="sxs-lookup"><span data-stu-id="af660-157">Creating an Asymmetric Key</span></span>  

<span data-ttu-id="af660-158">この作業では、<xref:System.Security.Cryptography.Aes> キーの暗号化と復号化を行う非対称キーを作成します。</span><span class="sxs-lookup"><span data-stu-id="af660-158">This task creates an asymmetric key that encrypts and decrypts the <xref:System.Security.Cryptography.Aes> key.</span></span> <span data-ttu-id="af660-159">このキーは、コンテンツの暗号化に使用されたもので、ラベル コントロールにキー コンテナー名を表示します。</span><span class="sxs-lookup"><span data-stu-id="af660-159">This key was used to encrypt the content and it displays the key container name on the label control.</span></span>  
  
 <span data-ttu-id="af660-160">次のコードを [`Create Keys`] ボタン (`buttonCreateAsmKeys_Click`) の `Click` イベント ハンドラーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="af660-160">Add the following code as the `Click` event handler for the `Create Keys` button (`buttonCreateAsmKeys_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#2)]
 [!code-vb[CryptoWalkThru#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#2)]  
  
## <a name="encrypting-a-file"></a><span data-ttu-id="af660-161">ファイルの暗号化</span><span class="sxs-lookup"><span data-stu-id="af660-161">Encrypting a File</span></span>  

<span data-ttu-id="af660-162">このタスクには、ボタン () のイベントハンドラーメソッド `Encrypt File` とメソッドの2つのメソッドが含ま `buttonEncryptFile_Click` れます。 `EncryptFile`</span><span class="sxs-lookup"><span data-stu-id="af660-162">This task involves two methods: the event handler method for the `Encrypt File` button (`buttonEncryptFile_Click`) and the `EncryptFile` method.</span></span> <span data-ttu-id="af660-163">最初のメソッドは、ファイルを選択するためのダイアログ ボックスを表示し、暗号化を実行する 2 番目のメソッドにファイル名を渡します。</span><span class="sxs-lookup"><span data-stu-id="af660-163">The first method displays a dialog box for selecting a file and passes the file name to the second method, which performs the encryption.</span></span>  
  
<span data-ttu-id="af660-164">暗号化されたコンテンツ、キー、および IV は、すべて 1 つの <xref:System.IO.FileStream> に保存されます。これを暗号化パッケージといいます。</span><span class="sxs-lookup"><span data-stu-id="af660-164">The encrypted content, key, and IV are all saved to one <xref:System.IO.FileStream>, which is referred to as the encryption package.</span></span>  
  
<span data-ttu-id="af660-165">`EncryptFile` メソッドは以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="af660-165">The `EncryptFile` method does the following:</span></span>  
  
1. <span data-ttu-id="af660-166">コンテンツを暗号化する <xref:System.Security.Cryptography.Aes> 対称アルゴリズムを作成します。</span><span class="sxs-lookup"><span data-stu-id="af660-166">Creates a <xref:System.Security.Cryptography.Aes> symmetric algorithm to encrypt the content.</span></span>  
  
2. <span data-ttu-id="af660-167"><xref:System.Security.Cryptography.Aes> キーを暗号化する <xref:System.Security.Cryptography.RSACryptoServiceProvider> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="af660-167">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to encrypt the <xref:System.Security.Cryptography.Aes> key.</span></span>  
  
3. <span data-ttu-id="af660-168">ソース ファイルの <xref:System.IO.FileStream> の読み取りと暗号化を行う <xref:System.Security.Cryptography.CryptoStream> オブジェクト (バイトのブロック) を使用して、暗号化ファイルの対象の <xref:System.IO.FileStream> オブジェクトにします。</span><span class="sxs-lookup"><span data-stu-id="af660-168">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and encrypt the <xref:System.IO.FileStream> of the source file, in blocks of bytes, into a destination <xref:System.IO.FileStream> object for the encrypted file.</span></span>  
  
4. <span data-ttu-id="af660-169">暗号化されたキーと IV の長さを決定し、長さの値のバイト配列を作成します。</span><span class="sxs-lookup"><span data-stu-id="af660-169">Determines the lengths of the encrypted key and IV, and creates byte arrays of their length values.</span></span>  
  
5. <span data-ttu-id="af660-170">暗号化されたパッケージにキー、IV、および長さの値を書き込みます。</span><span class="sxs-lookup"><span data-stu-id="af660-170">Writes the Key, IV, and their length values to the encrypted package.</span></span>  
  
 <span data-ttu-id="af660-171">暗号化パッケージでは、次の形式を使用します。</span><span class="sxs-lookup"><span data-stu-id="af660-171">The encryption package uses the following format:</span></span>  
  
- <span data-ttu-id="af660-172">キーの長さ: 0 - 3 バイト</span><span class="sxs-lookup"><span data-stu-id="af660-172">Key length, bytes 0 - 3</span></span>  
  
- <span data-ttu-id="af660-173">IV の長さ: 4 - 7 バイト</span><span class="sxs-lookup"><span data-stu-id="af660-173">IV length, bytes 4 - 7</span></span>  
  
- <span data-ttu-id="af660-174">暗号化されたキー</span><span class="sxs-lookup"><span data-stu-id="af660-174">Encrypted key</span></span>  
  
- <span data-ttu-id="af660-175">IV</span><span class="sxs-lookup"><span data-stu-id="af660-175">IV</span></span>  
  
- <span data-ttu-id="af660-176">暗号化テキスト</span><span class="sxs-lookup"><span data-stu-id="af660-176">Cipher text</span></span>  
  
 <span data-ttu-id="af660-177">キーと IV の長さを使用すると、暗号化パッケージのすべての部分の開始点と長さを決定することができます。これを使用してファイルを復号化します。</span><span class="sxs-lookup"><span data-stu-id="af660-177">You can use the lengths of the key and IV to determine the starting points and lengths of all parts of the encryption package, which can then be used to decrypt the file.</span></span>  
  
 <span data-ttu-id="af660-178">次のコードを [`Encrypt File`] ボタン (`buttonEncryptFile_Click`) の `Click` イベント ハンドラーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="af660-178">Add the following code as the `Click` event handler for the `Encrypt File` button (`buttonEncryptFile_Click`).</span></span>  
  
 [!code-csharp[CryptoWalkThru#3](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#3)]
 [!code-vb[CryptoWalkThru#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#3)]  
  
 <span data-ttu-id="af660-179">フォームに次の `EncryptFile` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="af660-179">Add the following `EncryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#5](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#5)]
 [!code-vb[CryptoWalkThru#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#5)]  
  
## <a name="decrypting-a-file"></a><span data-ttu-id="af660-180">ファイルの復号化</span><span class="sxs-lookup"><span data-stu-id="af660-180">Decrypting a File</span></span>  

<span data-ttu-id="af660-181">このタスクには、[`Decrypt File`] ボタン (`buttonDecryptFile_Click`) のイベント ハンドラー メソッドと `DecryptFile` メソッドという 2 つのメソッドが含まれています。</span><span class="sxs-lookup"><span data-stu-id="af660-181">This task involves two methods, the event handler method for the `Decrypt File` button (`buttonDecryptFile_Click`), and the `DecryptFile` method.</span></span> <span data-ttu-id="af660-182">最初のメソッドは、ファイルを選択するためのダイアログ ボックスを表示し、復号化を実行する 2 番目のメソッドにファイル名を渡します。</span><span class="sxs-lookup"><span data-stu-id="af660-182">The first method displays a dialog box for selecting a file and passes its file name to the second method, which performs the decryption.</span></span>  
  
<span data-ttu-id="af660-183">`Decrypt` メソッドは以下を実行します。</span><span class="sxs-lookup"><span data-stu-id="af660-183">The `Decrypt` method does the following:</span></span>  
  
1. <span data-ttu-id="af660-184"><xref:System.Security.Cryptography.Aes>コンテンツの暗号化を解除するための対称アルゴリズムを作成します。</span><span class="sxs-lookup"><span data-stu-id="af660-184">Creates an <xref:System.Security.Cryptography.Aes> symmetric algorithm to decrypt the content.</span></span>  
  
2. <span data-ttu-id="af660-185">暗号化されたキーと IV の長さを取得するには、暗号化パッケージの <xref:System.IO.FileStream> の最初の 8 バイトを読み取ってバイト配列にします。</span><span class="sxs-lookup"><span data-stu-id="af660-185">Reads the first eight bytes of the <xref:System.IO.FileStream> of the encrypted package into byte arrays to obtain the lengths of the encrypted key and the IV.</span></span>  
  
3. <span data-ttu-id="af660-186">キーと IV を暗号化パッケージから抽出してバイト配列にします。</span><span class="sxs-lookup"><span data-stu-id="af660-186">Extracts the key and IV from the encryption package into byte arrays.</span></span>  
  
4. <span data-ttu-id="af660-187"><xref:System.Security.Cryptography.Aes> キーを復号化する <xref:System.Security.Cryptography.RSACryptoServiceProvider> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="af660-187">Creates an <xref:System.Security.Cryptography.RSACryptoServiceProvider> object to decrypt the <xref:System.Security.Cryptography.Aes> key.</span></span>  
  
5. <span data-ttu-id="af660-188"><xref:System.Security.Cryptography.CryptoStream> オブジェクトを使用して、<xref:System.IO.FileStream> の暗号化パッケージの暗号テキスト セクションをバイトのブロックで読み取って復号化し、復号化されたファイルの <xref:System.IO.FileStream> オブジェクトにします。</span><span class="sxs-lookup"><span data-stu-id="af660-188">Uses a <xref:System.Security.Cryptography.CryptoStream> object to read and decrypt the cipher text section of the <xref:System.IO.FileStream> encryption package, in blocks of bytes, into the <xref:System.IO.FileStream> object for the decrypted file.</span></span> <span data-ttu-id="af660-189">これが終了すると、復号化は完了です。</span><span class="sxs-lookup"><span data-stu-id="af660-189">When this is finished, the decryption is completed.</span></span>  
  
 <span data-ttu-id="af660-190">次のコードを、[`Decrypt File`] ボタンの `Click` イベント ハンドラーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="af660-190">Add the following code as the `Click` event handler for the `Decrypt File` button.</span></span>  
  
 [!code-csharp[CryptoWalkThru#4](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#4)]
 [!code-vb[CryptoWalkThru#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#4)]  
  
 <span data-ttu-id="af660-191">フォームに次の `DecryptFile` メソッドを追加します。</span><span class="sxs-lookup"><span data-stu-id="af660-191">Add the following `DecryptFile` method to the form.</span></span>  
  
 [!code-csharp[CryptoWalkThru#6](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#6)]
 [!code-vb[CryptoWalkThru#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#6)]  
  
## <a name="exporting-a-public-key"></a><span data-ttu-id="af660-192">公開キーのエクスポート</span><span class="sxs-lookup"><span data-stu-id="af660-192">Exporting a Public Key</span></span>

<span data-ttu-id="af660-193">この作業では、[`Create Keys`] ボタンによって作成されたキーをファイルに保存します。</span><span class="sxs-lookup"><span data-stu-id="af660-193">This task saves the key created by the `Create Keys` button to a file.</span></span> <span data-ttu-id="af660-194">パブリック パラメーターのみがエクスポートされます。</span><span class="sxs-lookup"><span data-stu-id="af660-194">It exports only the public parameters.</span></span>  
  
<span data-ttu-id="af660-195">このタスクでは、アリスがボブに公開キーを与えるシナリオをシミュレーションします。そうすることで、ボブはアリスのファイルを暗号化できるようになります。</span><span class="sxs-lookup"><span data-stu-id="af660-195">This task simulates the scenario of Alice giving Bob her public key so that he can encrypt files for her.</span></span> <span data-ttu-id="af660-196">ボブとその公開キーを持つ他のユーザーはファイルを復号化できなくなります。彼らはプライベート パラメーターを持つ完全なキーのペアを持っていないためです。</span><span class="sxs-lookup"><span data-stu-id="af660-196">He and others who have that public key will not be able to decrypt them because they do not have the full key pair with private parameters.</span></span>  
  
<span data-ttu-id="af660-197">次のコードを [`Export Public Key`] ボタン (`buttonExportPublicKey_Click`) の `Click` イベント ハンドラーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="af660-197">Add the following code as the `Click` event handler for the `Export Public Key` button (`buttonExportPublicKey_Click`).</span></span>  
  
[!code-csharp[CryptoWalkThru#8](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#8)]
[!code-vb[CryptoWalkThru#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#8)]  
  
## <a name="importing-a-public-key"></a><span data-ttu-id="af660-198">公開キーのインポート</span><span class="sxs-lookup"><span data-stu-id="af660-198">Importing a Public Key</span></span>

<span data-ttu-id="af660-199">このタスクでは、[`Export Public Key`] ボタンによって作成されたパブリック パラメーターのみを持つキーを読み込み、キー コンテナー名として設定します。</span><span class="sxs-lookup"><span data-stu-id="af660-199">This task loads the key with only public parameters, as created by the `Export Public Key` button, and sets it as the key container name.</span></span>  
  
<span data-ttu-id="af660-200">この作業では、ボブがアリスのファイルを暗号化できるように、ボブがパブリック パラメーターのみを持つアリスのキーを読み込むシナリオをシミュレーションします。</span><span class="sxs-lookup"><span data-stu-id="af660-200">This task simulates the scenario of Bob loading Alice's key with only public parameters so he can encrypt files for her.</span></span>  
  
<span data-ttu-id="af660-201">次のコードを [`Import Public Key`] ボタン (`buttonImportPublicKey_Click`) の `Click` イベント ハンドラーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="af660-201">Add the following code as the `Click` event handler for the `Import Public Key` button (`buttonImportPublicKey_Click`).</span></span>  
  
[!code-csharp[CryptoWalkThru#9](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#9)]
[!code-vb[CryptoWalkThru#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#9)]  
  
## <a name="getting-a-private-key"></a><span data-ttu-id="af660-202">秘密キーの取得</span><span class="sxs-lookup"><span data-stu-id="af660-202">Getting a Private Key</span></span>  

<span data-ttu-id="af660-203">この作業では、[`Create Keys`] ボタンを使用して作成されたキーの名前にキー コンテナー名を設定します。</span><span class="sxs-lookup"><span data-stu-id="af660-203">This task sets the key container name to the name of the key created by using the `Create Keys` button.</span></span> <span data-ttu-id="af660-204">キー コンテナーには、プライベート パラメーターを持つ完全なキーのペアが格納されます。</span><span class="sxs-lookup"><span data-stu-id="af660-204">The key container will contain the full key pair with private parameters.</span></span>  
  
<span data-ttu-id="af660-205">この作業では、アリスが自分の秘密キーを使用してボブが暗号化したファイルを復号化するシナリオをシミュレーションします。</span><span class="sxs-lookup"><span data-stu-id="af660-205">This task simulates the scenario of Alice using her private key to decrypt files encrypted by Bob.</span></span>  
  
<span data-ttu-id="af660-206">次のコードを [`Get Private Key`] ボタン (`buttonGetPrivateKey_Click`) の `Click` イベント ハンドラーとして追加します。</span><span class="sxs-lookup"><span data-stu-id="af660-206">Add the following code as the `Click` event handler for the `Get Private Key` button (`buttonGetPrivateKey_Click`).</span></span>  
  
[!code-csharp[CryptoWalkThru#7](../../../samples/snippets/csharp/VS_Snippets_CLR/CryptoWalkThru/cs/Form1.cs#7)]
[!code-vb[CryptoWalkThru#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CryptoWalkThru/vb/Form1.vb#7)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="af660-207">アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="af660-207">Testing the Application</span></span>

<span data-ttu-id="af660-208">アプリケーションをビルドしたら、次のテスト シナリオを実行します。</span><span class="sxs-lookup"><span data-stu-id="af660-208">After you have built the application, perform the following testing scenarios.</span></span>  
  
#### <a name="to-create-keys-encrypt-and-decrypt"></a><span data-ttu-id="af660-209">キーの作成、暗号化、および復号化を行うには</span><span class="sxs-lookup"><span data-stu-id="af660-209">To create keys, encrypt, and decrypt</span></span>  
  
1. <span data-ttu-id="af660-210">`Create Keys` ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="af660-210">Click the `Create Keys` button.</span></span> <span data-ttu-id="af660-211">ラベルはキー名を表示し、完全なキーのペアであることを示します。</span><span class="sxs-lookup"><span data-stu-id="af660-211">The label displays the key name and shows that it is a full key pair.</span></span>  
  
2. <span data-ttu-id="af660-212">`Export Public Key` ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="af660-212">Click the `Export Public Key` button.</span></span> <span data-ttu-id="af660-213">公開キーのパラメーターのエクスポートにより現在のキーは変更されないことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="af660-213">Note that exporting the public key parameters does not change the current key.</span></span>  
  
3. <span data-ttu-id="af660-214">[`Encrypt File`] ボタンをクリックして、ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="af660-214">Click the `Encrypt File` button and select a file.</span></span>  
  
4. <span data-ttu-id="af660-215">[`Decrypt File`] ボタンをクリックし、暗号化したファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="af660-215">Click the `Decrypt File` button and select the file just encrypted.</span></span>  
  
5. <span data-ttu-id="af660-216">復号化したファイルを調べます。</span><span class="sxs-lookup"><span data-stu-id="af660-216">Examine the file just decrypted.</span></span>  
  
6. <span data-ttu-id="af660-217">次のシナリオで保持されたキー コンテナーを取得するテストを実行するには、アプリケーションを閉じて再起動します。</span><span class="sxs-lookup"><span data-stu-id="af660-217">Close the application and restart it to test retrieving persisted key containers in the next scenario.</span></span>  
  
#### <a name="to-encrypt-using-the-public-key"></a><span data-ttu-id="af660-218">公開キーを使用して暗号化するには</span><span class="sxs-lookup"><span data-stu-id="af660-218">To encrypt using the public key</span></span>  
  
1. <span data-ttu-id="af660-219">`Import Public Key` ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="af660-219">Click the `Import Public Key` button.</span></span> <span data-ttu-id="af660-220">ラベルはキー名を表示し、公開キーのみであることを示します。</span><span class="sxs-lookup"><span data-stu-id="af660-220">The label displays the key name and shows that it is public only.</span></span>  
  
2. <span data-ttu-id="af660-221">[`Encrypt File`] ボタンをクリックして、ファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="af660-221">Click the `Encrypt File` button and select a file.</span></span>  
  
3. <span data-ttu-id="af660-222">[`Decrypt File`] ボタンをクリックし、暗号化したファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="af660-222">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="af660-223">復号化するには秘密キーが必要であるため、これは失敗します。</span><span class="sxs-lookup"><span data-stu-id="af660-223">This will fail because you must have the private key to decrypt.</span></span>  
  
 <span data-ttu-id="af660-224">このシナリオでは、公開キーのみによる別のユーザーのファイルの暗号化をデモンストレーションします。</span><span class="sxs-lookup"><span data-stu-id="af660-224">This scenario demonstrates having only the public key to encrypt a file for another person.</span></span> <span data-ttu-id="af660-225">通常、そのユーザーは公開キーのみを与え、秘密キーは復号化のため与えないでおきます。</span><span class="sxs-lookup"><span data-stu-id="af660-225">Typically that person would give you only the public key and withhold the private key for decryption.</span></span>  
  
#### <a name="to-decrypt-using-the-private-key"></a><span data-ttu-id="af660-226">秘密キーを使用して復号化するには</span><span class="sxs-lookup"><span data-stu-id="af660-226">To decrypt using the private key</span></span>  
  
1. <span data-ttu-id="af660-227">`Get Private Key` ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="af660-227">Click the `Get Private Key` button.</span></span> <span data-ttu-id="af660-228">ラベルはキー名を表示し、完全なキーのペアであるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="af660-228">The label displays the key name and shows whether it is the full key pair.</span></span>  
  
2. <span data-ttu-id="af660-229">[`Decrypt File`] ボタンをクリックし、暗号化したファイルを選択します。</span><span class="sxs-lookup"><span data-stu-id="af660-229">Click the `Decrypt File` button and select the file just encrypted.</span></span> <span data-ttu-id="af660-230">復号化するための完全なキーのペアがあるため、これは成功します。</span><span class="sxs-lookup"><span data-stu-id="af660-230">This will be successful because you have the full key pair to decrypt.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af660-231">関連項目</span><span class="sxs-lookup"><span data-stu-id="af660-231">See also</span></span>

- <span data-ttu-id="af660-232">[暗号化モデル](cryptography-model.md) -基本クラスライブラリにおける暗号化の実装方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="af660-232">[Cryptography Model](cryptography-model.md) - Describes how cryptography is implemented in the base class library.</span></span>
- [<span data-ttu-id="af660-233">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="af660-233">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="af660-234">クロスプラットフォーム暗号化</span><span class="sxs-lookup"><span data-stu-id="af660-234">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="af660-235">データ保護の ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="af660-235">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
