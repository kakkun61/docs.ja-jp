---
title: COM へのアセンブリの登録
description: クラスに関する情報をシステム レジストリに追加するアセンブリ登録ツール (Regasm.exe) を使用して、アセンブリを COM に登録または登録解除します。
ms.date: 03/30/2017
helpviewer_keywords:
- COM interop, registering assemblies
- unregistering assemblies
- interoperation with unmanaged code, registering assemblies
- registering assemblies
ms.assetid: 87925795-a3ae-4833-b138-125413478551
ms.openlocfilehash: 525e3724aec82a74f5b0339296808b41f30d0ddc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96266377"
---
# <a name="registering-assemblies-with-com"></a><span data-ttu-id="155d1-103">COM へのアセンブリの登録</span><span class="sxs-lookup"><span data-stu-id="155d1-103">Registering Assemblies with COM</span></span>

<span data-ttu-id="155d1-104">[アセンブリ登録ツール (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) というコマンドライン ツールを実行して、COM で使うアセンブリを登録または登録解除できます。</span><span class="sxs-lookup"><span data-stu-id="155d1-104">You can run a command-line tool called the [Assembly Registration Tool (Regasm.exe)](../tools/regasm-exe-assembly-registration-tool.md) to register or unregister an assembly for use with COM.</span></span> <span data-ttu-id="155d1-105">Regasm.exe は、COM クライアントが .NET Framework のクラスを透過的に使うことができるように、クラスについての情報をシステム レジストリに追加します。</span><span class="sxs-lookup"><span data-stu-id="155d1-105">Regasm.exe adds information about the class to the system registry so COM clients can use the .NET Framework class transparently.</span></span> <span data-ttu-id="155d1-106"><xref:System.Runtime.InteropServices.RegistrationServices> クラスには、同等の機能が用意されています。</span><span class="sxs-lookup"><span data-stu-id="155d1-106">The <xref:System.Runtime.InteropServices.RegistrationServices> class provides the equivalent functionality.</span></span>  
  
 <span data-ttu-id="155d1-107">マネージド コンポーネントを COM クライアントからアクティブ化するには、先にマネージド コンポーネントを Windows レジストリに登録しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="155d1-107">A managed component must be registered in the Windows registry before it can be activated from a COM client.</span></span> <span data-ttu-id="155d1-108">次の表では、Regasm.exe が通常、Windows レジストリに追加するキーを示します</span><span class="sxs-lookup"><span data-stu-id="155d1-108">The following table shows the keys that Regasm.exe typically adds to the Windows registry.</span></span> <span data-ttu-id="155d1-109">(000000 は実際の GUID の値を示します)。</span><span class="sxs-lookup"><span data-stu-id="155d1-109">(000000 indicates the actual GUID value.)</span></span>  
  
|<span data-ttu-id="155d1-110">GUID</span><span class="sxs-lookup"><span data-stu-id="155d1-110">GUID</span></span>|<span data-ttu-id="155d1-111">説明</span><span class="sxs-lookup"><span data-stu-id="155d1-111">Description</span></span>|<span data-ttu-id="155d1-112">レジストリ キー</span><span class="sxs-lookup"><span data-stu-id="155d1-112">Registry key</span></span>|  
|----------|-----------------|------------------|  
|<span data-ttu-id="155d1-113">CLSID</span><span class="sxs-lookup"><span data-stu-id="155d1-113">CLSID</span></span>|<span data-ttu-id="155d1-114">クラス識別子</span><span class="sxs-lookup"><span data-stu-id="155d1-114">Class identifier</span></span>|<span data-ttu-id="155d1-115">HKEY_CLASSES_ROOT\CLSID\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="155d1-115">HKEY_CLASSES_ROOT\CLSID\\{000…000}</span></span>|  
|<span data-ttu-id="155d1-116">IID</span><span class="sxs-lookup"><span data-stu-id="155d1-116">IID</span></span>|<span data-ttu-id="155d1-117">インターフェイス識別子</span><span class="sxs-lookup"><span data-stu-id="155d1-117">Interface identifier</span></span>|<span data-ttu-id="155d1-118">HKEY_CLASSES_ROOT\Interface\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="155d1-118">HKEY_CLASSES_ROOT\Interface\\{000…000}</span></span>|  
|<span data-ttu-id="155d1-119">LIBID</span><span class="sxs-lookup"><span data-stu-id="155d1-119">LIBID</span></span>|<span data-ttu-id="155d1-120">ライブラリ識別子</span><span class="sxs-lookup"><span data-stu-id="155d1-120">Library identifier</span></span>|<span data-ttu-id="155d1-121">HKEY_CLASSES_ROOT\TypeLib\\{000…000}</span><span class="sxs-lookup"><span data-stu-id="155d1-121">HKEY_CLASSES_ROOT\TypeLib\\{000…000}</span></span>|  
|<span data-ttu-id="155d1-122">ProgID</span><span class="sxs-lookup"><span data-stu-id="155d1-122">ProgID</span></span>|<span data-ttu-id="155d1-123">プログラム識別子</span><span class="sxs-lookup"><span data-stu-id="155d1-123">Programmatic identifier</span></span>|<span data-ttu-id="155d1-124">HKEY_CLASSES_ROOT\000…000</span><span class="sxs-lookup"><span data-stu-id="155d1-124">HKEY_CLASSES_ROOT\000…000</span></span>|  
  
 <span data-ttu-id="155d1-125">HKCR\CLSID\\{0000…0000} キーの下では、既定値がクラスの ProgID に設定され、Class と Assembly という 2 つの新しい名前付きの値が追加されます。</span><span class="sxs-lookup"><span data-stu-id="155d1-125">Under the HKCR\CLSID\\{0000…0000} key, the default value is set to the ProgID of the class, and two new named values, Class and Assembly, are added.</span></span> <span data-ttu-id="155d1-126">ランタイムは、レジストリから Assembly の値を読み取り、ランタイム アセンブリ リゾルバーに渡します。</span><span class="sxs-lookup"><span data-stu-id="155d1-126">The runtime reads the Assembly value from the registry and passes it on to the runtime assembly resolver.</span></span> <span data-ttu-id="155d1-127">アセンブリ リゾルバーは、名前やバージョン番号などのアセンブリの情報に基づいて、アセンブリの特定を試みます。</span><span class="sxs-lookup"><span data-stu-id="155d1-127">The assembly resolver attempts to locate the assembly, based on assembly information such as the name and version number.</span></span> <span data-ttu-id="155d1-128">アセンブリ リゾルバーがアセンブリを特定するには、アセンブリが次のいずれかの場所に存在する必要があります。</span><span class="sxs-lookup"><span data-stu-id="155d1-128">For the assembly resolver to locate an assembly, the assembly has to be in one of the following locations:</span></span>  
  
- <span data-ttu-id="155d1-129">グローバル アセンブリ キャッシュ (厳密な名前付きアセンブリである必要があります)。</span><span class="sxs-lookup"><span data-stu-id="155d1-129">The global assembly cache (must be a strong-named assembly).</span></span>  
  
- <span data-ttu-id="155d1-130">アプリケーション ディレクトリ内。</span><span class="sxs-lookup"><span data-stu-id="155d1-130">In the application directory.</span></span> <span data-ttu-id="155d1-131">アプリケーション パスから読み込まれたアセンブリは、そのアプリケーションからのみアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="155d1-131">Assemblies loaded from the application path are only accessible from that application.</span></span>  
  
- <span data-ttu-id="155d1-132">Regasm.exe に対する **/codebase** オプションで指定されたファイル パス上。</span><span class="sxs-lookup"><span data-stu-id="155d1-132">Along an file path specified with the **/codebase** option to Regasm.exe.</span></span>  
  
 <span data-ttu-id="155d1-133">Regasm.exe は、HKCR\CLSID\\{0000…0000} キーの下に InProcServer32 キーも作成します。</span><span class="sxs-lookup"><span data-stu-id="155d1-133">Regasm.exe also creates the InProcServer32 key under the HKCR\CLSID\\{0000…0000} key.</span></span> <span data-ttu-id="155d1-134">このキーの既定値は、共通言語ランタイム (Mscoree.dll) を初期化する DLL の名前に設定されます。</span><span class="sxs-lookup"><span data-stu-id="155d1-134">The default value for the key is set to the name of the DLL that initializes the common language runtime (Mscoree.dll).</span></span>  
  
## <a name="examining-registry-entries"></a><span data-ttu-id="155d1-135">レジストリ エントリを調べる</span><span class="sxs-lookup"><span data-stu-id="155d1-135">Examining Registry Entries</span></span>  

 <span data-ttu-id="155d1-136">COM 相互運用は、.NET Framework クラスのインスタンスを作成するための標準のクラス ファクトリの実装を提供します。</span><span class="sxs-lookup"><span data-stu-id="155d1-136">COM interop provides a standard class factory implementation to create an instance of any .NET Framework class.</span></span> <span data-ttu-id="155d1-137">クライアントは、他の COM コンポーネントと同様に、マネージド DLL で **DllGetClassObject** を呼び出してクラス ファクトリを取得し、オブジェクトを作成することができます。</span><span class="sxs-lookup"><span data-stu-id="155d1-137">Clients can call **DllGetClassObject** on the managed DLL to get a class factory and create objects, just as they would with any other COM component.</span></span>  
  
 <span data-ttu-id="155d1-138">`InprocServer32` サブキーには、従来の COM タイプ ライブラリの代わりに Mscoree.dll への参照が表示され、共通言語ランタイムがマネージド オブジェクトを作成することを示します。</span><span class="sxs-lookup"><span data-stu-id="155d1-138">For the `InprocServer32` subkey, a reference to Mscoree.dll appears in place of a traditional COM type library to indicate that the common language runtime creates the managed object.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="155d1-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="155d1-139">See also</span></span>

- [<span data-ttu-id="155d1-140">COM への .NET Framework コンポーネントの公開</span><span class="sxs-lookup"><span data-stu-id="155d1-140">Exposing .NET Framework Components to COM</span></span>](exposing-dotnet-components-to-com.md)
- [<span data-ttu-id="155d1-141">方法: COM から .NET 型を参照する</span><span class="sxs-lookup"><span data-stu-id="155d1-141">How to: Reference .NET Types from COM</span></span>](how-to-reference-net-types-from-com.md)
- <span data-ttu-id="155d1-142">[.NET オブジェクトの呼び出し](/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="155d1-142">[Calling a .NET Object](/previous-versions/dotnet/netframework-4.0/8hw8h46b(v=vs.100))</span></span>
- <span data-ttu-id="155d1-143">[COM アクセスに対するアプリケーションの配置](/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="155d1-143">[Deploying an Application for COM Access](/previous-versions/dotnet/netframework-4.0/c2850st8(v=vs.100))</span></span>
