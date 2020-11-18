---
title: '方法: キーコンテナーに非対称キーを格納する'
description: .NET のキーコンテナーに非対称キーを格納する方法について説明します。 非対称キーを作成し、キーコンテナーに保存し、キーを取得して削除する方法について説明します。
ms.date: 05/26/2020
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cryptography [.NET], asymmetric keys
- storing asymmetric keys
- keys, asymmetric
- encryption keys
- keys, storing in key containers
- asymmetric keys [.NET]
- encryption [.NET], asymmetric keys
- decryption keys
ms.assetid: 0dbcbd8d-0dcf-40e9-9f0c-e3f162d35ccc
ms.openlocfilehash: 946657f0c96aa80705575d8203ff158c63a72780
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2020
ms.locfileid: "94820151"
---
# <a name="store-asymmetric-keys-in-a-key-container"></a><span data-ttu-id="28b6b-104">キーコンテナーに非対称キーを格納する</span><span class="sxs-lookup"><span data-stu-id="28b6b-104">Store asymmetric keys in a key container</span></span>

<span data-ttu-id="28b6b-105">非対称秘密キーは、ローカル コンピューターにそのまま平文として保存しないでください。</span><span class="sxs-lookup"><span data-stu-id="28b6b-105">Asymmetric private keys should never be stored verbatim or in plain text on the local computer.</span></span> <span data-ttu-id="28b6b-106">秘密キーを保存する必要がある場合は、キーコンテナーを使用します。</span><span class="sxs-lookup"><span data-stu-id="28b6b-106">If you need to store a private key, use a key container.</span></span> <span data-ttu-id="28b6b-107">キーコンテナーの詳細については、「 [コンピューターレベルおよびユーザーレベルの RSA キーコンテナー](/previous-versions/aspnet/f5cs0acs(v=vs.100))について」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28b6b-107">For more information on key containers, see [Understanding machine-level and user-level RSA key containers](/previous-versions/aspnet/f5cs0acs(v=vs.100)).</span></span>

> [!NOTE]
> <span data-ttu-id="28b6b-108">この記事のコードは Windows に適用され、.NET Core 2.2 以前のバージョンでは使用できない機能を使用します。</span><span class="sxs-lookup"><span data-stu-id="28b6b-108">The code in this article applies to Windows and uses features not available in .NET Core 2.2 and earlier versions.</span></span> <span data-ttu-id="28b6b-109">詳細については、「 [dotnet/runtime # 23391](https://github.com/dotnet/runtime/issues/23391)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="28b6b-109">For more information, see [dotnet/runtime#23391](https://github.com/dotnet/runtime/issues/23391).</span></span>

## <a name="create-an-asymmetric-key-and-save-it-in-a-key-container"></a><span data-ttu-id="28b6b-110">非対称キーを作成してキーコンテナーに保存する</span><span class="sxs-lookup"><span data-stu-id="28b6b-110">Create an asymmetric key and save it in a key container</span></span>

1. <span data-ttu-id="28b6b-111">クラスの新しいインスタンスを作成 <xref:System.Security.Cryptography.CspParameters> し、キーコンテナーを呼び出す名前をフィールドに渡し <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="28b6b-111">Create a new instance of a <xref:System.Security.Cryptography.CspParameters> class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>

1. <span data-ttu-id="28b6b-112">クラス (通常はまたは) から派生したクラスの新しいインスタンスを作成 <xref:System.Security.Cryptography.AsymmetricAlgorithm> <xref:System.Security.Cryptography.RSACryptoServiceProvider> し、 <xref:System.Security.Cryptography.DSACryptoServiceProvider> 以前に作成したオブジェクトを `CspParameters` そのコンストラクターに渡します。</span><span class="sxs-lookup"><span data-stu-id="28b6b-112">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually <xref:System.Security.Cryptography.RSACryptoServiceProvider> or <xref:System.Security.Cryptography.DSACryptoServiceProvider>) and pass the previously created `CspParameters` object to its constructor.</span></span>

> [!NOTE]
> <span data-ttu-id="28b6b-113">非対称キーの作成と取得は1つの操作です。</span><span class="sxs-lookup"><span data-stu-id="28b6b-113">The creation and retrieval of an asymmetric key is one operation.</span></span> <span data-ttu-id="28b6b-114">キーがコンテナーにまだ存在しない場合は、返される前に作成されます。</span><span class="sxs-lookup"><span data-stu-id="28b6b-114">If a key is not already in the container, it's created before being returned.</span></span>
>
> - <xref:System.Security.Cryptography.RSA.ToXmlString%2A?displayProperty=nameWithType>
> - <xref:System.Security.Cryptography.DSA.ToXmlString%2A?displayProperty=nameWithType>

## <a name="delete-the-key-from-the-key-container"></a><span data-ttu-id="28b6b-115">キーコンテナーからキーを削除します。</span><span class="sxs-lookup"><span data-stu-id="28b6b-115">Delete the key from the key container</span></span>

1. <span data-ttu-id="28b6b-116">クラスの新しいインスタンスを作成 `CspParameters` し、キーコンテナーを呼び出す名前をフィールドに渡し <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> ます。</span><span class="sxs-lookup"><span data-stu-id="28b6b-116">Create a new instance of a `CspParameters` class and pass the name that you want to call the key container to the <xref:System.Security.Cryptography.CspParameters.KeyContainerName?displayProperty=nameWithType> field.</span></span>

1. <span data-ttu-id="28b6b-117">クラス (通常はまたは) から派生したクラスの新しいインスタンスを作成 <xref:System.Security.Cryptography.AsymmetricAlgorithm> `RSACryptoServiceProvider` し、 `DSACryptoServiceProvider` 以前に作成したオブジェクトを `CspParameters` そのコンストラクターに渡します。</span><span class="sxs-lookup"><span data-stu-id="28b6b-117">Create a new instance of a class that derives from the <xref:System.Security.Cryptography.AsymmetricAlgorithm> class (usually `RSACryptoServiceProvider` or `DSACryptoServiceProvider`) and pass the previously created `CspParameters` object to its constructor.</span></span>

1. <span data-ttu-id="28b6b-118"><xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> から派生するクラスのまたはのプロパティ `AsymmetricAlgorithm` を `false` (Visual Basic) に設定し `False` ます。</span><span class="sxs-lookup"><span data-stu-id="28b6b-118">Set the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> or the <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp?displayProperty=nameWithType> property of the class that derives from `AsymmetricAlgorithm` to `false` (`False` in Visual Basic).</span></span>

1. <span data-ttu-id="28b6b-119">`Clear`から派生したクラスのメソッドを呼び出し `AsymmetricAlgorithm` ます。</span><span class="sxs-lookup"><span data-stu-id="28b6b-119">Call the `Clear` method of the class that derives from `AsymmetricAlgorithm`.</span></span> <span data-ttu-id="28b6b-120">このメソッドは、クラスのすべてのリソースを解放し、キー コンテナーを消去します。 </span><span class="sxs-lookup"><span data-stu-id="28b6b-120">This method releases all resources of the class and clears the key container.</span></span>

## <a name="example"></a><span data-ttu-id="28b6b-121">例</span><span class="sxs-lookup"><span data-stu-id="28b6b-121">Example</span></span>

<span data-ttu-id="28b6b-122">非対称キーを作成し、それをキー コンテナーへ格納し、後でキーを取得し、最後にキー コンテナーからキーを削除する方法の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="28b6b-122">The following example demonstrates how to create an asymmetric key, save it in a key container, retrieve the key at a later time, and delete the key from the container.</span></span>

<span data-ttu-id="28b6b-123">`GenKey_SaveInContainer` メソッドと `GetKeyFromContainer` メソッドのコードは類似していることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="28b6b-123">Notice that code in the `GenKey_SaveInContainer` method and the `GetKeyFromContainer` method is similar.</span></span> <span data-ttu-id="28b6b-124">オブジェクトのキーコンテナー名を指定し、 <xref:System.Security.Cryptography.CspParameters> <xref:System.Security.Cryptography.AsymmetricAlgorithm> <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> プロパティまたはプロパティがに設定されたオブジェクトに渡すと <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> `true` 、の動作は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="28b6b-124">When you specify a key container name for a <xref:System.Security.Cryptography.CspParameters> object and pass it to an <xref:System.Security.Cryptography.AsymmetricAlgorithm> object with the <xref:System.Security.Cryptography.RSACryptoServiceProvider.PersistKeyInCsp%2A> property or <xref:System.Security.Cryptography.DSACryptoServiceProvider.PersistKeyInCsp%2A> property set to `true`, the behavior is as follows:</span></span>

- <span data-ttu-id="28b6b-125">指定した名前のキー コンテナーが存在しない場合、コンテナーが作成されてキーが保持されます。</span><span class="sxs-lookup"><span data-stu-id="28b6b-125">If a key container with the specified name does not exist, then one is created and the key is persisted.</span></span>
- <span data-ttu-id="28b6b-126">指定した名前のキー コンテナーが存在する場合、そのコンテナー内のキーが現在の <xref:System.Security.Cryptography.AsymmetricAlgorithm> オブジェクトに自動的に読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="28b6b-126">If a key container with the specified name does exist, then the key in the container is automatically loaded into the current <xref:System.Security.Cryptography.AsymmetricAlgorithm> object.</span></span>

<span data-ttu-id="28b6b-127">このため、メソッドのコードは `GenKey_SaveInContainer` 最初に実行されるので、キーを永続化します。一方、メソッドのコードは、 `GetKeyFromContainer` 2 番目に実行されるため、キーを読み込みます。</span><span class="sxs-lookup"><span data-stu-id="28b6b-127">Therefore, the code in the `GenKey_SaveInContainer` method persists the key because it is run first, while the code in the `GetKeyFromContainer` method loads the key because it's run second.</span></span>

```vb
Imports System
Imports System.Security.Cryptography

Public Class StoreKey

    Public Shared Sub Main()
        Try
            ' Create a key and save it in a container.
            GenKey_SaveInContainer("MyKeyContainer")

            ' Retrieve the key from the container.
            GetKeyFromContainer("MyKeyContainer")

            ' Delete the key from the container.
            DeleteKeyFromContainer("MyKeyContainer")

            ' Create a key and save it in a container.
            GenKey_SaveInContainer("MyKeyContainer")

            ' Delete the key from the container.
            DeleteKeyFromContainer("MyKeyContainer")
        Catch e As CryptographicException
            Console.WriteLine(e.Message)
        End Try
    End Sub

    Private Shared Sub GenKey_SaveInContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        ' name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container MyKeyContainerName.
        Using rsa As New RSACryptoServiceProvider(parameters)
            ' Display the key information to the console.
            Console.WriteLine($"Key added to container:  {rsa.ToXmlString(True)}")
        End Using
    End Sub

    Private Shared Sub GetKeyFromContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        '  name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container MyKeyContainerName.
        Using rsa As New RSACryptoServiceProvider(parameters)
            ' Display the key information to the console.
            Console.WriteLine($"Key retrieved from container : {rsa.ToXmlString(True)}")
        End Using
    End Sub

    Private Shared Sub DeleteKeyFromContainer(ByVal ContainerName As String)
        ' Create the CspParameters object and set the key container
        '  name used to store the RSA key pair.
        Dim parameters As New CspParameters With {
            .KeyContainerName = ContainerName
        }

        ' Create a new instance of RSACryptoServiceProvider that accesses
        ' the key container.
        ' Delete the key entry in the container.
        Dim rsa As New RSACryptoServiceProvider(parameters) With {
            .PersistKeyInCsp = False
        }

        ' Call Clear to release resources and delete the key from the container.
        rsa.Clear()

        Console.WriteLine("Key deleted.")
    End Sub
End Class
```

```csharp
using System;
using System.Security.Cryptography;

public class StoreKey
{
    public static void Main()
    {
        try
        {
            // Create a key and save it in a container.
            GenKey_SaveInContainer("MyKeyContainer");

            // Retrieve the key from the container.
            GetKeyFromContainer("MyKeyContainer");

            // Delete the key from the container.
            DeleteKeyFromContainer("MyKeyContainer");

            // Create a key and save it in a container.
            GenKey_SaveInContainer("MyKeyContainer");

            // Delete the key from the container.
            DeleteKeyFromContainer("MyKeyContainer");
        }
        catch (CryptographicException e)
        {
            Console.WriteLine(e.Message);
        }
    }

    private static void GenKey_SaveInContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container MyKeyContainerName.
        using var rsa = new RSACryptoServiceProvider(parameters);

        // Display the key information to the console.
        Console.WriteLine($"Key added to container: \n  {rsa.ToXmlString(true)}");
    }

    private static void GetKeyFromContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container MyKeyContainerName.
        using var rsa = new RSACryptoServiceProvider(parameters);

        // Display the key information to the console.
        Console.WriteLine($"Key retrieved from container : \n {rsa.ToXmlString(true)}");
    }

    private static void DeleteKeyFromContainer(string containerName)
    {
        // Create the CspParameters object and set the key container
        // name used to store the RSA key pair.
        var parameters = new CspParameters
        {
            KeyContainerName = containerName
        };

        // Create a new instance of RSACryptoServiceProvider that accesses
        // the key container.
        using var rsa = new RSACryptoServiceProvider(parameters)
        {
            // Delete the key entry in the container.
            PersistKeyInCsp = false
        };

        // Call Clear to release resources and delete the key from the container.
        rsa.Clear();

        Console.WriteLine("Key deleted.");
    }
}
```

<span data-ttu-id="28b6b-128">出力は次のようになります。</span><span class="sxs-lookup"><span data-stu-id="28b6b-128">The output is as follows:</span></span>

```console
Key added to container:
<RSAKeyValue> Key Information A</RSAKeyValue>
Key retrieved from container :
<RSAKeyValue> Key Information A</RSAKeyValue>
Key deleted.
Key added to container:
<RSAKeyValue> Key Information B</RSAKeyValue>
Key deleted.
```

## <a name="see-also"></a><span data-ttu-id="28b6b-129">関連項目</span><span class="sxs-lookup"><span data-stu-id="28b6b-129">See also</span></span>

- [<span data-ttu-id="28b6b-130">暗号モデル</span><span class="sxs-lookup"><span data-stu-id="28b6b-130">Cryptography Model</span></span>](cryptography-model.md)
- [<span data-ttu-id="28b6b-131">Cryptographic Services</span><span class="sxs-lookup"><span data-stu-id="28b6b-131">Cryptographic Services</span></span>](cryptographic-services.md)
- [<span data-ttu-id="28b6b-132">クロスプラットフォーム暗号化</span><span class="sxs-lookup"><span data-stu-id="28b6b-132">Cross-Platform Cryptography</span></span>](cross-platform-cryptography.md)
- [<span data-ttu-id="28b6b-133">暗号化と復号化のためのキーの生成</span><span class="sxs-lookup"><span data-stu-id="28b6b-133">Generating keys for encryption and decryption</span></span>](generating-keys-for-encryption-and-decryption.md)
- [<span data-ttu-id="28b6b-134">データの暗号化</span><span class="sxs-lookup"><span data-stu-id="28b6b-134">Encrypting data</span></span>](encrypting-data.md)
- [<span data-ttu-id="28b6b-135">データの復号化</span><span class="sxs-lookup"><span data-stu-id="28b6b-135">Decrypting data</span></span>](decrypting-data.md)
- [<span data-ttu-id="28b6b-136">データ保護の ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="28b6b-136">ASP.NET Core Data Protection</span></span>](/aspnet/core/security/data-protection/introduction)
