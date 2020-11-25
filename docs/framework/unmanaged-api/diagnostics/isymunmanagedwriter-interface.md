---
title: ISymUnmanagedWriter インターフェイス
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter
helpviewer_keywords:
- ISymUnmanagedWriter interface [.NET Framework debugging]
ms.assetid: 7d6733ec-f081-4166-bc17-de09e16dc304
topic_type:
- apiref
ms.openlocfilehash: fddfd2a163f6e6513b648ee0b724c0b5bd54c81a
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/24/2020
ms.locfileid: "95722935"
---
# <a name="isymunmanagedwriter-interface"></a><span data-ttu-id="d0e2d-102">ISymUnmanagedWriter インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d0e2d-102">ISymUnmanagedWriter Interface</span></span>

<span data-ttu-id="d0e2d-103">シンボル ライターを表し、ドキュメント、シーケンス ポイント、構文スコープ、変数を定義するメソッドを提供します。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-103">Represents a symbol writer, and provides methods to define documents, sequence points, lexical scopes, and variables.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d0e2d-104">メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-104">Methods</span></span>  
  
|<span data-ttu-id="d0e2d-105">メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-105">Method</span></span>|<span data-ttu-id="d0e2d-106">説明</span><span class="sxs-lookup"><span data-stu-id="d0e2d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d0e2d-107">Abort メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-107">Abort Method</span></span>](isymunmanagedwriter-abort-method.md)|<span data-ttu-id="d0e2d-108">シンボルストアにシンボルをコミットせずにシンボルライターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-108">Closes the symbol writer without committing the symbols to the symbol store.</span></span>|  
|[<span data-ttu-id="d0e2d-109">Close メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-109">Close Method</span></span>](isymunmanagedwriter-close-method.md)|<span data-ttu-id="d0e2d-110">シンボルをシンボルストアにコミットした後、シンボルライターを閉じます。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-110">Closes the symbol writer after committing the symbols to the symbol store.</span></span>|  
|[<span data-ttu-id="d0e2d-111">CloseMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-111">CloseMethod Method</span></span>](isymunmanagedwriter-closemethod-method.md)|<span data-ttu-id="d0e2d-112">現在のメソッドを閉じます。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-112">Closes the current method.</span></span> <span data-ttu-id="d0e2d-113">メソッドを閉じると、それ以上シンボルを定義することはできません。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-113">Once a method is closed, no more symbols can be defined within it.</span></span>|  
|[<span data-ttu-id="d0e2d-114">CloseNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-114">CloseNamespace Method</span></span>](isymunmanagedwriter-closenamespace-method.md)|<span data-ttu-id="d0e2d-115">最近開いた名前空間を閉じます。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-115">Closes the most recently opened namespace.</span></span>|  
|[<span data-ttu-id="d0e2d-116">CloseScope メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-116">CloseScope Method</span></span>](isymunmanagedwriter-closescope-method.md)|<span data-ttu-id="d0e2d-117">現在の構文のスコープを閉じます。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-117">Closes the current lexical scope.</span></span>|  
|[<span data-ttu-id="d0e2d-118">DefineConstant メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-118">DefineConstant Method</span></span>](isymunmanagedwriter-defineconstant-method.md)|<span data-ttu-id="d0e2d-119">定数値の名前を定義します。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-119">Defines a name for a constant value.</span></span>|  
|[<span data-ttu-id="d0e2d-120">DefineDocument メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-120">DefineDocument Method</span></span>](isymunmanagedwriter-definedocument-method.md)|<span data-ttu-id="d0e2d-121">ソース ドキュメントを定義します。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-121">Defines a source document.</span></span>|  
|[<span data-ttu-id="d0e2d-122">DefineField メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-122">DefineField Method</span></span>](isymunmanagedwriter-definefield-method.md)|<span data-ttu-id="d0e2d-123">メソッド内にない単一の変数を定義します。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-123">Defines a single variable that is not within a method.</span></span>|  
|[<span data-ttu-id="d0e2d-124">DefineGlobalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-124">DefineGlobalVariable Method</span></span>](isymunmanagedwriter-defineglobalvariable-method.md)|<span data-ttu-id="d0e2d-125">グローバル変数を 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-125">Defines a single global variable.</span></span>|  
|[<span data-ttu-id="d0e2d-126">DefineLocalVariable メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-126">DefineLocalVariable Method</span></span>](isymunmanagedwriter-definelocalvariable-method.md)|<span data-ttu-id="d0e2d-127">現在の構文のスコープの変数を 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-127">Defines a single variable in the current lexical scope.</span></span>|  
|[<span data-ttu-id="d0e2d-128">DefineParameter メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-128">DefineParameter Method</span></span>](isymunmanagedwriter-defineparameter-method.md)|<span data-ttu-id="d0e2d-129">現在のメソッドのパラメーターを 1 つ定義します。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-129">Defines a single parameter in the current method.</span></span>|  
|[<span data-ttu-id="d0e2d-130">DefineSequencePoints メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-130">DefineSequencePoints Method</span></span>](isymunmanagedwriter-definesequencepoints-method.md)|<span data-ttu-id="d0e2d-131">現在のメソッド内のシーケンス ポイントのグループを定義します。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-131">Defines a group of sequence points within the current method.</span></span>|  
|[<span data-ttu-id="d0e2d-132">GetDebugInfo メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-132">GetDebugInfo Method</span></span>](isymunmanagedwriter-getdebuginfo-method.md)|<span data-ttu-id="d0e2d-133">コンパイラがポータブル実行可能 (PE) ファイルヘッダーにデバッグディレクトリエントリを書き込むために必要な情報を返します。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-133">Returns the information necessary for a compiler to write the debug directory entry in the portable executable (PE) file header.</span></span>|  
|[<span data-ttu-id="d0e2d-134">Initialize メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-134">Initialize Method</span></span>](isymunmanagedwriter-initialize-method.md)|<span data-ttu-id="d0e2d-135">このライターが関連付けられるメタデータエミッタインターフェイスを設定し、デバッグシンボルの書き込み先となる出力ファイル名を設定します。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-135">Sets the metadata emitter interface with which this writer will be associated, and sets the output file name to which the debugging symbols will be written.</span></span>|  
|[<span data-ttu-id="d0e2d-136">Initialize2 メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-136">Initialize2 Method</span></span>](isymunmanagedwriter-initialize2-method.md)|<span data-ttu-id="d0e2d-137">このライターが関連付けられるメタデータエミッタインターフェイスを設定し、デバッグシンボルの書き込み先となる出力ファイル名を設定し、プログラムデータベース (PDB) ファイルの最終的な場所を設定します。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-137">Sets the metadata emitter interface with which this writer will be associated, sets the output file name to which the debugging symbols will be written, and sets the final location of the program database (PDB) file.</span></span>|  
|[<span data-ttu-id="d0e2d-138">OpenMethod メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-138">OpenMethod Method</span></span>](isymunmanagedwriter-openmethod-method.md)|<span data-ttu-id="d0e2d-139">シンボル情報を出力するメソッドを開きます。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-139">Opens a method into which symbol information is emitted.</span></span>|  
|[<span data-ttu-id="d0e2d-140">OpenNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-140">OpenNamespace Method</span></span>](isymunmanagedwriter-opennamespace-method.md)|<span data-ttu-id="d0e2d-141">新しい名前空間を開きます。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-141">Opens a new namespace.</span></span>|  
|[<span data-ttu-id="d0e2d-142">OpenScope メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-142">OpenScope Method</span></span>](isymunmanagedwriter-openscope-method.md)|<span data-ttu-id="d0e2d-143">現在のメソッドの構文の新しいスコープを開きます。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-143">Opens a new lexical scope in the current method.</span></span>|  
|[<span data-ttu-id="d0e2d-144">RemapToken メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-144">RemapToken Method</span></span>](isymunmanagedwriter-remaptoken-method.md)|<span data-ttu-id="d0e2d-145">メタデータが生成されたときにメタデータトークンが再マップされたことをシンボルライターに通知します。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-145">Notifies the symbol writer that a metadata token has been remapped as the metadata was emitted.</span></span>|  
|[<span data-ttu-id="d0e2d-146">SetMethodSourceRange メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-146">SetMethodSourceRange Method</span></span>](isymunmanagedwriter-setmethodsourcerange-method.md)|<span data-ttu-id="d0e2d-147">ソース ファイル内にメソッドの実際の先頭と末尾を指定します。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-147">Specifies the true start and end of a method within a source file.</span></span>|  
|[<span data-ttu-id="d0e2d-148">SetScopeRange メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-148">SetScopeRange Method</span></span>](isymunmanagedwriter-setscoperange-method.md)|<span data-ttu-id="d0e2d-149">指定した構文のスコープのオフセット範囲を定義します。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-149">Defines the offset range for the specified lexical scope.</span></span>|  
|[<span data-ttu-id="d0e2d-150">SetSymAttribute メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-150">SetSymAttribute Method</span></span>](isymunmanagedwriter-setsymattribute-method.md)|<span data-ttu-id="d0e2d-151">名前に基づいてカスタム属性を定義します。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-151">Defines a custom attribute based upon its name.</span></span>|  
|[<span data-ttu-id="d0e2d-152">SetUserEntryPoint メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-152">SetUserEntryPoint Method</span></span>](isymunmanagedwriter-setuserentrypoint-method.md)|<span data-ttu-id="d0e2d-153">このモジュールのエントリポイントであるユーザー定義メソッドを指定します。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-153">Specifies the user-defined method that is the entry point for this module.</span></span>|  
|[<span data-ttu-id="d0e2d-154">UsingNamespace メソッド</span><span class="sxs-lookup"><span data-stu-id="d0e2d-154">UsingNamespace Method</span></span>](isymunmanagedwriter-usingnamespace-method.md)|<span data-ttu-id="d0e2d-155">現在開いている構文のスコープ内で、指定された完全修飾名前空間名が使用されていることを指定します。</span><span class="sxs-lookup"><span data-stu-id="d0e2d-155">Specifies that the given fully qualified namespace name is being used within the currently open lexical scope.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d0e2d-156">要件</span><span class="sxs-lookup"><span data-stu-id="d0e2d-156">Requirements</span></span>  

 <span data-ttu-id="d0e2d-157">**ヘッダー:** CorSym .idl、CorSym .h</span><span class="sxs-lookup"><span data-stu-id="d0e2d-157">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0e2d-158">関連項目</span><span class="sxs-lookup"><span data-stu-id="d0e2d-158">See also</span></span>

- [<span data-ttu-id="d0e2d-159">シンボル ストア診断インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d0e2d-159">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
- [<span data-ttu-id="d0e2d-160">ISymUnmanagedWriter2 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d0e2d-160">ISymUnmanagedWriter2 Interface</span></span>](isymunmanagedwriter2-interface.md)
- [<span data-ttu-id="d0e2d-161">ISymUnmanagedWriter3 インターフェイス</span><span class="sxs-lookup"><span data-stu-id="d0e2d-161">ISymUnmanagedWriter3 Interface</span></span>](isymunmanagedwriter3-interface.md)
