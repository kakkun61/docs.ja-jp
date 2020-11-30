---
title: 拡張された厳密な名前付け
description: .NET Framework でのアセンブリのための従来の厳密な名前の署名には制限があります。 拡張された厳密な名前付けについて説明します。
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies
- strong naming [.NET Framework], enhanced
ms.assetid: 6cf17a82-62a1-4f6d-8d5a-d7d06dec2bb5
ms.openlocfilehash: b9c690c77dafc247f7282c3f56384481efe53399
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95731528"
---
# <a name="enhanced-strong-naming"></a><span data-ttu-id="1d7cc-104">拡張された厳密な名前付け</span><span class="sxs-lookup"><span data-stu-id="1d7cc-104">Enhanced strong naming</span></span>

<span data-ttu-id="1d7cc-105">厳密な名前の署名は、アセンブリを識別するための .NET Framework の識別機構です。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-105">A strong name signature is an identity mechanism in the .NET Framework for identifying assemblies.</span></span> <span data-ttu-id="1d7cc-106">これは通常、発行元 (署名者) から受取人 (検証者) に対して渡されるデータの整合性を検証するために使用される、公開キーによるデジタル署名です。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-106">It is a public-key digital signature that is typically used to verify the integrity of data being passed from an originator (signer) to a recipient (verifier).</span></span> <span data-ttu-id="1d7cc-107">この署名はアセンブリに対する一意の ID として使用され、これによりアセンブリへの参照のあいまいさをなくします。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-107">This signature is used as a unique identity for an assembly and ensures that references to the assembly are not ambiguous.</span></span> <span data-ttu-id="1d7cc-108">アセンブリはビルド プロセスの一部として署名され、読み込まれるときに検証されます。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-108">The assembly is signed as part of the build process and then verified when it is loaded.</span></span>  
  
 <span data-ttu-id="1d7cc-109">厳密な名前の署名により、悪意のあるユーザーがアセンブリを不正に変更して、元の署名者のキーでアセンブリを再署名することを防ぐことができます。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-109">Strong name signatures help prevent malicious parties from tampering with an assembly and then re-signing the assembly with the original signer’s key.</span></span> <span data-ttu-id="1d7cc-110">ただし、厳密な名前キーには、発行者に関する信頼できる情報も、証明書の階層構造も含まれていません。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-110">However, strong name keys don’t contain any reliable information about the publisher, nor do they contain a certificate hierarchy.</span></span> <span data-ttu-id="1d7cc-111">厳密な名前の署名は、アセンブリの署名者の信頼性を保証するものではなく、またその署名者がキーの正当な所有者であることを示すものでもありません。厳密な名前の署名は、キーの所有者がアセンブリに署名したことのみを示しています。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-111">A strong name signature does not guarantee the trustworthiness of the person who signed the assembly or indicate whether that person was a legitimate owner of the key; it indicates only that the owner of the key signed the assembly.</span></span> <span data-ttu-id="1d7cc-112">したがって、信頼できるサードパーティのコードのためのセキュリティの検証コントロールとして、厳密な名前の署名を使用することはお勧めしません。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-112">Therefore, we do not recommend using a strong name signature as a security validator for trusting third-party code.</span></span> <span data-ttu-id="1d7cc-113">コードを認証するために推奨される方法は、Microsoft Authenticode です。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-113">Microsoft Authenticode is the recommended way to authenticate code.</span></span>  
  
## <a name="limitations-of-conventional-strong-names"></a><span data-ttu-id="1d7cc-114">従来の厳密な名前の制限</span><span class="sxs-lookup"><span data-stu-id="1d7cc-114">Limitations of conventional strong names</span></span>  

 <span data-ttu-id="1d7cc-115">.NET Framework 4.5 以前のバージョンで使用されている厳密な名前付けのテクノロジには次の欠点があります。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-115">The strong naming technology used in versions before the .NET Framework 4.5 has the following shortcomings:</span></span>  
  
- <span data-ttu-id="1d7cc-116">キーが常に攻撃を受ける状態に置かれています。テクノロジとハードウェアの向上により、公開キーから秘密キーを推測することが容易になっています。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-116">Keys are constantly under attack, and improved techniques and hardware make it easier to infer a private key from a public key.</span></span> <span data-ttu-id="1d7cc-117">攻撃からの保護には、より大きなキーが必要です。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-117">To guard against attacks, larger keys are necessary.</span></span> <span data-ttu-id="1d7cc-118">.NET Framework 4.5 より前の .NET Framework バージョンでは任意のサイズのキー (既定のサイズは 1024 ビット) で署名する機能を提供していますが、新しいキーでアセンブリを署名すると、アセンブリの古い ID を参照しているすべてのバイナリが動作しなくなります。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-118">.NET Framework versions before the .NET Framework 4.5 provide the ability to sign with any size key (the default size is 1024 bits), but signing an assembly with a new key breaks all binaries that reference the older identity of the assembly.</span></span> <span data-ttu-id="1d7cc-119">したがって、互換性を維持する場合には、署名キーのサイズの更新は非常に困難です。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-119">Therefore, it is extremely difficult to upgrade the size of a signing key if you want to maintain compatibility.</span></span>  
  
- <span data-ttu-id="1d7cc-120">厳密な名前の署名は SHA-1 アルゴリズムのみをサポートします。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-120">Strong name signing supports only the SHA-1 algorithm.</span></span> <span data-ttu-id="1d7cc-121">SHA-1 は、最近、セキュリティが強化されたハッシュ アプリケーションのためには不十分であることがわかりました。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-121">SHA-1 has recently been found to be inadequate for secure hashing applications.</span></span> <span data-ttu-id="1d7cc-122">したがって、より強力なアルゴリズム (SHA-256 以上) が必要です。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-122">Therefore, a stronger algorithm (SHA-256 or greater) is necessary.</span></span> <span data-ttu-id="1d7cc-123">SHA-1 は FIPS 準拠の地位を失う可能性があり、これによって FIPS 準拠のソフトウェアとアルゴリズムのみを選択して使用しているユーザーには問題が生じることになります。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-123">It is possible that SHA-1 will lose its FIPS-compliant standing, which would present problems for those who choose to use only FIPS-compliant software and algorithms.</span></span>  
  
## <a name="advantages-of-enhanced-strong-names"></a><span data-ttu-id="1d7cc-124">強化された厳密な名前の利点</span><span class="sxs-lookup"><span data-stu-id="1d7cc-124">Advantages of enhanced strong names</span></span>  

 <span data-ttu-id="1d7cc-125">強化された厳密な名前の主な利点は、既存の厳密な名前との互換性と、ある ID が別の ID と等価であることを指定できる機能です。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-125">The main advantages of enhanced strong names are compatibility with pre-existing strong names and the ability to claim that one identity is equivalent to another:</span></span>  
  
- <span data-ttu-id="1d7cc-126">既存の署名付きアセンブリを持つ開発者は、以前の ID を参照するアセンブリとの互換性を保ちながら、それらのアセンブリの ID を SHA-2 アルゴリズムに移行できます。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-126">Developers who have pre-existing signed assemblies can migrate their identities to the SHA-2 algorithms while maintaining compatibility with assemblies that reference the old identities.</span></span>  
  
- <span data-ttu-id="1d7cc-127">新しいアセンブリを作成する際に、既存の厳密な名前の署名を考慮する必要のない開発者は、より安全な SHA-2 アルゴリズムを使用して、今までどおりにアセンブリに署名できます。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-127">Developers who create new assemblies and are not concerned with pre-existing strong name signatures can use the more secure SHA-2 algorithms and sign the assemblies as they always have.</span></span>  
  
## <a name="use-enhanced-strong-names"></a><span data-ttu-id="1d7cc-128">強化された厳密な名前を使用する</span><span class="sxs-lookup"><span data-stu-id="1d7cc-128">Use enhanced strong names</span></span>  

 <span data-ttu-id="1d7cc-129">厳密な名前のキーは署名キーと ID のキーで構成されます。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-129">Strong name keys consist of a signature key and an identity key.</span></span> <span data-ttu-id="1d7cc-130">アセンブリは署名キーで署名され、ID キーで識別されます。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-130">The assembly is signed with the signature key and is identified by the identity key.</span></span> <span data-ttu-id="1d7cc-131">.NET Framework 4.5 より前では、これらの 2 つのキーは同一です。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-131">Prior to the .NET Framework 4.5, these two keys were identical.</span></span> <span data-ttu-id="1d7cc-132">.NET Framework 4.5 以降では、ID キーは、.NET Framework の以前のバージョンと同じですが、署名キーは、より強力なハッシュ アルゴリズムを備えて強化されています。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-132">Starting with the .NET Framework 4.5, the identity key remains the same as in earlier .NET Framework versions, but the signature key is enhanced with a stronger hash algorithm.</span></span> <span data-ttu-id="1d7cc-133">さらに、副署名を作成するために、署名キーは ID キーで署名されます。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-133">In addition, the signature key is signed with the identity key to create a counter-signature.</span></span>  
  
 <span data-ttu-id="1d7cc-134"><xref:System.Reflection.AssemblySignatureKeyAttribute> 属性によって、アセンブリのメタデータはアセンブリの ID に既存の公開キーを使用することができ、これによって、古いアセンブリ参照は引き続き動作します。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-134">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute enables the assembly metadata to use the pre-existing public key for assembly identity, which allows old assembly references to continue to work.</span></span>  <span data-ttu-id="1d7cc-135"><xref:System.Reflection.AssemblySignatureKeyAttribute> の属性は副署名を使用して、新しい署名キーの所有者が古い ID キーの所有者にもなるようにします。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-135">The <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute uses the counter-signature to ensure that the owner of the new signature key is also the owner of the old identity key.</span></span>  
  
### <a name="sign-with-sha-2-without-key-migration"></a><span data-ttu-id="1d7cc-136">キー移行を伴わない SHA-2 による署名</span><span class="sxs-lookup"><span data-stu-id="1d7cc-136">Sign with SHA-2, without key migration</span></span>  

 <span data-ttu-id="1d7cc-137">厳密な名前の署名を移行せずにアセンブリに署名するには、コマンド プロンプトから次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-137">Run the following commands from a command prompt to sign an assembly without migrating a strong name signature:</span></span>  
  
1. <span data-ttu-id="1d7cc-138">新しい ID キーを生成します (必要な場合)。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-138">Generate the new identity key (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    ```  
  
2. <span data-ttu-id="1d7cc-139">ID の公開キーを抽出し、このキーで署名する場合に SHA-2 アルゴリズムを使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-139">Extract the identity public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="1d7cc-140">ID 公開キー ファイルで、アセンブリに遅延署名します。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-140">Delay-sign the assembly with the identity public key file.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
4. <span data-ttu-id="1d7cc-141">完全な ID キーのペアでアセンブリに再署名します。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-141">Re-sign the assembly with the full identity key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe IdentityKey.snk  
    ```  
  
### <a name="sign-with-sha-2-with-key-migration"></a><span data-ttu-id="1d7cc-142">キー移行を伴う SHA-2 による署名</span><span class="sxs-lookup"><span data-stu-id="1d7cc-142">Sign with SHA-2, with key migration</span></span>  

 <span data-ttu-id="1d7cc-143">移行した厳密な名前の署名でアセンブリに署名するには、コマンド プロンプトで次のコマンドを実行します。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-143">Run the following commands from a command prompt to sign an assembly with a migrated strong name signature.</span></span>  
  
1. <span data-ttu-id="1d7cc-144">ID キーと署名キーのペアを生成します (必要な場合)。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-144">Generate an identity and signature key pair (if necessary).</span></span>  
  
    ```console  
    sn -k IdentityKey.snk  
    sn -k SignatureKey.snk  
    ```  
  
2. <span data-ttu-id="1d7cc-145">署名の公開キーを抽出し、このキーで署名する場合に SHA-2 アルゴリズムを使用するように指定します。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-145">Extract the signature public key, and specify that a SHA-2 algorithm should be used when signing with this key.</span></span>  
  
    ```console  
    sn -p SignatureKey.snk SignaturePubKey.snk sha256  
    ```  
  
3. <span data-ttu-id="1d7cc-146">副署名を生成するハッシュ アルゴリズムを決定する ID の公開キーを抽出します。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-146">Extract the identity public key, which determines the hash algorithm that generates a counter-signature.</span></span>  
  
    ```console  
    sn -p IdentityKey.snk IdentityPubKey.snk  
    ```  
  
4. <span data-ttu-id="1d7cc-147"><xref:System.Reflection.AssemblySignatureKeyAttribute> の属性のパラメーターを生成し、アセンブリに属性を追加します。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-147">Generate the parameters for a <xref:System.Reflection.AssemblySignatureKeyAttribute> attribute, and attach the attribute to the assembly.</span></span>  
  
    ```console  
    sn -a IdentityPubKey.snk IdentityKey.snk SignaturePubKey.snk  
    ```  

    <span data-ttu-id="1d7cc-148">これにより、次のような出力が生成されます。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-148">This produces output similar to the following.</span></span>

    ```output
    Information for key migration attribute.
    (System.Reflection.AssemblySignatureKeyAttribute):
    publicKey=
    002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519
    d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936
    e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b4
    3893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a3
    4d153cdd

    counterSignature=
    e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91eb
    e1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8
    ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3
    ae5fec2c682e57b7442738
    ```

    <span data-ttu-id="1d7cc-149">この出力は AssemblySignatureKeyAttribute に変換できます。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-149">This output can then be transformed into an AssemblySignatureKeyAttribute.</span></span>

    ```csharp
    [assembly:System.Reflection.AssemblySignatureKeyAttribute(
    "002400000c80000094000000060200000024000052534131000400000100010005a3a81ac0a519d96244a9c589fc147c7d403e40ccf184fc290bdd06c7339389a76b738e255a2bce1d56c3e7e936e4fc87d45adc82ca94c716b50a65d39d373eea033919a613e4341c66863cb2dc622bcb541762b43893434d219d1c43f07e9c83fada2aed400b9f6e44ff05e3ecde6c2827830b8f43f7ac8e3270a34d153cdd",
    "e3cf7c211678c4d1a7b8fb20276c894ab74c29f0b5a34de4d61e63d4a997222f78cdcbfe4c91ebe1ddf9f3505a32edcb2a76f34df0450c4f61e376b70fa3cdeb7374b1b8e2078b121e2ee6e8c6a8ed661cc35621b4af53ac29c9e41738f199a81240e8fd478c887d1a30729d34e954a97cddce66e3ae5fec2c682e57b7442738"
    )]
    ```
  
5. <span data-ttu-id="1d7cc-150">ID 公開キーでアセンブリに遅延署名します。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-150">Delay-sign the assembly with the identity public key.</span></span>  
  
    ```console  
    csc MyAssembly.cs /keyfile:IdentityPubKey.snk /delaySign+  
    ```  
  
6. <span data-ttu-id="1d7cc-151">完全な署名キーのペアでアセンブリに署名します。</span><span class="sxs-lookup"><span data-stu-id="1d7cc-151">Fully sign the assembly with the signature key pair.</span></span>  
  
    ```console  
    sn -Ra MyAssembly.exe SignatureKey.snk  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1d7cc-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="1d7cc-152">See also</span></span>

- [<span data-ttu-id="1d7cc-153">厳密な名前付きアセンブリの作成と使用</span><span class="sxs-lookup"><span data-stu-id="1d7cc-153">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
