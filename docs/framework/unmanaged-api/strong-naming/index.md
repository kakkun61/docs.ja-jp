---
title: 厳密な名前付け (アンマネージ API リファレンス)
ms.date: 03/30/2017
helpviewer_keywords:
- strong naming [.NET Framework], using the unmanaged API
- native API reference [.NET Framework], strong naming
- unmanaged API reference [.NET Framework], strong naming
ms.assetid: 428c68b6-a7b4-44be-b280-75905f46612c
ms.openlocfilehash: 7e431f3a41fadb7247f20d7ab9bb9120e827b0cd
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95732295"
---
# <a name="strong-naming-unmanaged-api-reference"></a><span data-ttu-id="a36b2-102">厳密な名前付け (アンマネージ API リファレンス)</span><span class="sxs-lookup"><span data-stu-id="a36b2-102">Strong Naming (Unmanaged API Reference)</span></span>

<span data-ttu-id="a36b2-103">厳密な名前付け API を使用すると、アセンブリに対する厳密な名前の署名をクライアントで管理できます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-103">The strong naming API enables a client to administer strong name signing for assemblies.</span></span>  
  
 <span data-ttu-id="a36b2-104">厳密な名前を使用してアセンブリに署名すると、アセンブリ マニフェストを格納しているファイルに公開キー暗号化が追加されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-104">Signing an assembly with a strong name adds a public key encryption to the file containing the assembly manifest.</span></span> <span data-ttu-id="a36b2-105">厳密な名前による署名では、名前の一意性の検証を支援し、名前の悪用を防止し、参照が解決されたときに呼び出し元に一意の ID を提供できます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-105">Strong name signing helps verify name uniqueness, prevents name spoofing, and provides callers with a unique identity when a reference is resolved.</span></span> <span data-ttu-id="a36b2-106">しかし、厳密な名前に信頼性のレベルは関連付けられていません。</span><span class="sxs-lookup"><span data-stu-id="a36b2-106">However, no level of trust is associated with a strong name.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a36b2-107">このセクションの内容</span><span class="sxs-lookup"><span data-stu-id="a36b2-107">In This Section</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a36b2-108">.NET Framework 4 以降、これらの関数すべてが非推奨となりました。</span><span class="sxs-lookup"><span data-stu-id="a36b2-108">All of these functions have been deprecated starting with the .NET Framework 4.</span></span> <span data-ttu-id="a36b2-109">推奨されている代わりの関数については、[ICLRStrongName](../hosting/iclrstrongname-interface.md) インターフェイスを参照してください。</span><span class="sxs-lookup"><span data-stu-id="a36b2-109">For suggested alternatives, see the [ICLRStrongName](../hosting/iclrstrongname-interface.md) interface.</span></span>  
  
 [<span data-ttu-id="a36b2-110">GetHashFromAssemblyFile 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-110">GetHashFromAssemblyFile Function</span></span>](gethashfromassemblyfile-function.md)  
 <span data-ttu-id="a36b2-111">指定したハッシュ アルゴリズムを使用して、指定したアセンブリ ファイルのハッシュ値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-111">Gets a hash of the specified assembly file, using the specified hash algorithm.</span></span> <span data-ttu-id="a36b2-112">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-112">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-113">GetHashFromAssemblyFileW 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-113">GetHashFromAssemblyFileW Function</span></span>](gethashfromassemblyfilew-function.md)  
 <span data-ttu-id="a36b2-114">指定したハッシュ アルゴリズムを使用して、Unicode 文字列として指定したアセンブリ ファイルのハッシュ値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-114">Gets a hash of the assembly file specified as a Unicode string, using the specified hash algorithm.</span></span> <span data-ttu-id="a36b2-115">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-115">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-116">GetHashFromBlob 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-116">GetHashFromBlob Function</span></span>](gethashfromblob-function.md)  
 <span data-ttu-id="a36b2-117">指定したハッシュ アルゴリズムを使用して、指定したメモリ アドレスにあるアセンブリのハッシュが取得されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-117">Gets a hash of the assembly at the specified memory address, using the specified hash algorithm.</span></span> <span data-ttu-id="a36b2-118">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-118">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-119">GetHashFromFile 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-119">GetHashFromFile Function</span></span>](gethashfromfile-function.md)  
 <span data-ttu-id="a36b2-120">指定したファイルの内容に対してハッシュが生成されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-120">Generates a hash over the contents of the specified file.</span></span>  <span data-ttu-id="a36b2-121">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-121">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-122">GetHashFromFileW 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-122">GetHashFromFileW Function</span></span>](gethashfromfilew-function.md)  
 <span data-ttu-id="a36b2-123">Unicode 文字列で指定されたファイルの内容に対してハッシュが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-123">Generates a hash over the contents of the file specified by a Unicode string.</span></span> <span data-ttu-id="a36b2-124">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-124">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-125">GetHashFromHandle 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-125">GetHashFromHandle Function</span></span>](gethashfromhandle-function.md)  
 <span data-ttu-id="a36b2-126">指定したハッシュ アルゴリズムを使用して、指定したファイル ハンドルを含むファイルの内容に対してハッシュが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-126">Generates a hash over the contents of the file with the specified file handle, using the specified hash algorithm.</span></span>  <span data-ttu-id="a36b2-127">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-127">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-128">StrongNameCompareAssemblies 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-128">StrongNameCompareAssemblies Function</span></span>](strongnamecompareassemblies-function.md)  
 <span data-ttu-id="a36b2-129">厳密な名前の署名に基づいて 2 つのアセンブリが異なるかどうかが判定されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-129">Determines whether two assemblies differ only by their strong name signatures.</span></span> <span data-ttu-id="a36b2-130">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-130">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-131">StrongNameErrorInfo 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-131">StrongNameErrorInfo Function</span></span>](strongnameerrorinfo-function.md)  
 <span data-ttu-id="a36b2-132">厳密な名前の関数のいずれかに基づいて最後に発生したエラー コードが取得されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-132">Gets the last error code that was raised by one of the strong name functions.</span></span>  
  
 [<span data-ttu-id="a36b2-133">StrongNameFreeBuffer 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-133">StrongNameFreeBuffer Function</span></span>](strongnamefreebuffer-function.md)  
 <span data-ttu-id="a36b2-134">[StrongNameGetPublicKey](strongnamegetpublickey-function.md)、[StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md)、または[StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md) などの厳密な名前の関数に対する前の呼び出しで割り当てられたメモリが解放されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-134">Frees memory that was allocated with a previous call to a strong name function such as [StrongNameGetPublicKey](strongnamegetpublickey-function.md), [StrongNameTokenFromPublicKey](strongnametokenfrompublickey-function.md), or [StrongNameSignatureGeneration](strongnamesignaturegeneration-function.md).</span></span>   <span data-ttu-id="a36b2-135">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-135">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-136">StrongNameGetBlob 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-136">StrongNameGetBlob Function</span></span>](strongnamegetblob-function.md)  
 <span data-ttu-id="a36b2-137">指定したアドレスにある実行可能ファイルのバイナリ表現が、指定したバッファーに入れられます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-137">Fills the specified buffer with the binary representation of the executable file at the specified address.</span></span> <span data-ttu-id="a36b2-138">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-138">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-139">StrongNameGetBlobFromImage 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-139">StrongNameGetBlobFromImage Function</span></span>](strongnamegetblobfromimage-function.md)  
 <span data-ttu-id="a36b2-140">指定したメモリ アドレスにあるアセンブリ イメージのバイナリ表現が取得されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-140">Gets a binary representation of the assembly image at the specified memory address.</span></span> <span data-ttu-id="a36b2-141">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-141">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-142">StrongNameGetPublicKey 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-142">StrongNameGetPublicKey Function</span></span>](strongnamegetpublickey-function.md)  
 <span data-ttu-id="a36b2-143">秘密/公開キーの組から公開キーが取得されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-143">Gets the public key from a private/public key pair.</span></span> <span data-ttu-id="a36b2-144">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-144">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-145">StrongNameHashSize 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-145">StrongNameHashSize Function</span></span>](strongnamehashsize-function.md)  
 <span data-ttu-id="a36b2-146">指定したハッシュ アルゴリズムを使用して、ハッシュに必須のバッファー サイズが取得されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-146">Gets the buffer size required for a hash, using the specified hash algorithm.</span></span>  <span data-ttu-id="a36b2-147">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-147">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-148">StrongNameKeyDelete 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-148">StrongNameKeyDelete Function</span></span>](strongnamekeydelete-function.md)  
 <span data-ttu-id="a36b2-149">指定したキー コンテナーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-149">Deletes the specified key container.</span></span> <span data-ttu-id="a36b2-150">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-150">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-151">StrongNameKeyGen 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-151">StrongNameKeyGen Function</span></span>](strongnamekeygen-function.md)  
 <span data-ttu-id="a36b2-152">厳密な名前を使用するために新しい公開/秘密キーの組が作成されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-152">Creates a new public/private key pair for strong name use.</span></span>  <span data-ttu-id="a36b2-153">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-153">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-154">StrongNameKeyGenEx 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-154">StrongNameKeyGenEx Function</span></span>](strongnamekeygenex-function.md)  
 <span data-ttu-id="a36b2-155">厳密な名前を使用するために、指定したキー サイズによって新しい公開/秘密キーの組が作成されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-155">Generates a new public/private key pair with the specified key size for strong name use.</span></span> <span data-ttu-id="a36b2-156">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-156">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-157">StrongNameKeyInstall 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-157">StrongNameKeyInstall Function</span></span>](strongnamekeyinstall-function.md)  
 <span data-ttu-id="a36b2-158">公開/秘密キーの組がコンテナーにインポートされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-158">Imports a public/private key pair into a container.</span></span>  <span data-ttu-id="a36b2-159">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-159">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-160">StrongNameSignatureGeneration 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-160">StrongNameSignatureGeneration Function</span></span>](strongnamesignaturegeneration-function.md)  
 <span data-ttu-id="a36b2-161">指定したアセンブリに対して厳密な名前の署名が生成されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-161">Generates a strong name signature for the specified assembly.</span></span>   <span data-ttu-id="a36b2-162">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-162">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-163">StrongNameSignatureGenerationEx 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-163">StrongNameSignatureGenerationEx Function</span></span>](strongnamesignaturegenerationex-function.md)  
 <span data-ttu-id="a36b2-164">指定したフラグに基づいて、指定したアセンブリに対する厳密な名前の署名が作成されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-164">Generates a strong name signature for the specified assembly, based on the specified flags.</span></span>    <span data-ttu-id="a36b2-165">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-165">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-166">StrongNameSignatureSize 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-166">StrongNameSignatureSize Function</span></span>](strongnamesignaturesize-function.md)  
 <span data-ttu-id="a36b2-167">厳密な名前の署名のサイズが返されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-167">Returns the size of the strong name signature.</span></span> <span data-ttu-id="a36b2-168">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-168">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-169">StrongNameSignatureVerification 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-169">StrongNameSignatureVerification Function</span></span>](strongnamesignatureverification-function.md)  
 <span data-ttu-id="a36b2-170">指定したパスにあるアセンブリ マニフェストに厳密な名前の署名が含まれるかどうかを示す値が取得されます。これは指定したフラグに従って確認されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-170">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature, which is verified according to the specified flags.</span></span> <span data-ttu-id="a36b2-171">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-171">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-172">StrongNameSignatureVerificationEx 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-172">StrongNameSignatureVerificationEx Function</span></span>](strongnamesignatureverificationex-function.md)  
 <span data-ttu-id="a36b2-173">指定したパスにあるアセンブリ マニフェストに厳密な名前の署名が含まれるかどうかを示す値が取得されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-173">Gets a value indicating whether the assembly manifest at the supplied path contains a strong name signature.</span></span>  <span data-ttu-id="a36b2-174">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-174">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-175">StrongNameSignatureVerificationFromImage 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-175">StrongNameSignatureVerificationFromImage Function</span></span>](strongnamesignatureverificationfromimage-function.md)  
 <span data-ttu-id="a36b2-176">メモリに既にマップされているアセンブリが、関連付けられている公開キーに対して有効であるかどうかが確認されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-176">Verifies that an assembly that has already been mapped to memory is valid for the associated public key.</span></span> <span data-ttu-id="a36b2-177">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-177">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-178">StrongNameTokenFromAssembly 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-178">StrongNameTokenFromAssembly Function</span></span>](strongnametokenfromassembly-function.md)  
 <span data-ttu-id="a36b2-179">指定したアセンブリ ファイルから、厳密な名前トークンが作成されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-179">Creates a strong name token from the specified assembly file.</span></span>  <span data-ttu-id="a36b2-180">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-180">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-181">StrongNameTokenFromAssemblyEx 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-181">StrongNameTokenFromAssemblyEx Function</span></span>](strongnametokenfromassemblyex-function.md)  
 <span data-ttu-id="a36b2-182">指定したアセンブリ ファイルから厳密な名前のトークンが作成され、公開キーが返されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-182">Creates a strong name token from the specified assembly file, and returns the public key.</span></span> <span data-ttu-id="a36b2-183">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-183">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-184">StrongNameTokenFromPublicKey 関数</span><span class="sxs-lookup"><span data-stu-id="a36b2-184">StrongNameTokenFromPublicKey Function</span></span>](strongnametokenfrompublickey-function.md)  
 <span data-ttu-id="a36b2-185">公開キーを表すトークンが取得されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-185">Gets a token representing a public key.</span></span> <span data-ttu-id="a36b2-186">.NET Framework 4 以降では非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-186">Deprecated starting with the .NET Framework 4.</span></span>  
  
 [<span data-ttu-id="a36b2-187">PublicKeyBlob 構造体</span><span class="sxs-lookup"><span data-stu-id="a36b2-187">PublicKeyBlob Structure</span></span>](publickeyblob-structure.md)  
 <span data-ttu-id="a36b2-188">公開/秘密キーの組の公開キーがバイナリ形式で表されます。</span><span class="sxs-lookup"><span data-stu-id="a36b2-188">Represents the public key of a public/private key pair in binary format.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a36b2-189">関連項目</span><span class="sxs-lookup"><span data-stu-id="a36b2-189">See also</span></span>

- [<span data-ttu-id="a36b2-190">ICLRStrongName インターフェイス</span><span class="sxs-lookup"><span data-stu-id="a36b2-190">ICLRStrongName Interface</span></span>](../hosting/iclrstrongname-interface.md)
- [<span data-ttu-id="a36b2-191">アンマネージ API リファレンス</span><span class="sxs-lookup"><span data-stu-id="a36b2-191">Unmanaged API Reference</span></span>](../index.md)
