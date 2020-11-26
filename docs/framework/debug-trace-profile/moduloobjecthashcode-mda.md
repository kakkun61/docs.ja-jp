---
title: moduloObjectHashcode MDA
description: ModuloObjectHashcode managed デバッグアシスタント (MDA) を確認します。これにより、GetHashCode メソッドの結果の剰余値を取得するようにオブジェクトクラスが変更されます。
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), hashcode modulus
- Modulo object hash code
- moduloObjectHashcode MDA
- hashcode modulus
- MDAs (managed debugging assistants), hashcode modulus
- GetHashCode method
- modulus of hashcodes
ms.assetid: b45366ff-2a7a-4b8e-ab01-537b72e9de68
ms.openlocfilehash: 6258d5df7be1923a69de3172dd4c7f32e0b51f35
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96240525"
---
# <a name="moduloobjecthashcode-mda"></a><span data-ttu-id="88dc5-103">moduloObjectHashcode MDA</span><span class="sxs-lookup"><span data-stu-id="88dc5-103">moduloObjectHashcode MDA</span></span>

<span data-ttu-id="88dc5-104">`moduloObjectHashcode` マネージド デバッグ アシスタント (MDA) は、<xref:System.Object.GetHashCode%2A> メソッドによって返されるハッシュ コードに対してモジュロ演算を実行するように、<xref:System.Object> クラスの動作を変更します。</span><span class="sxs-lookup"><span data-stu-id="88dc5-104">The `moduloObjectHashcode` managed debugging assistant (MDA) changes the behavior of the <xref:System.Object> class to perform a modulo operation on the hash code returned by the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="88dc5-105">この MDA の既定の係数は 1 であり、これにより <xref:System.Object.GetHashCode%2A> はすべてのオブジェクトに対して 0 を返すようになります。</span><span class="sxs-lookup"><span data-stu-id="88dc5-105">The default modulus for this MDA is 1, which causes <xref:System.Object.GetHashCode%2A> to return 0 for all objects.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="88dc5-106">現象</span><span class="sxs-lookup"><span data-stu-id="88dc5-106">Symptoms</span></span>  

 <span data-ttu-id="88dc5-107">新しいバージョンの共通言語ランタイム (CLR) に移行すると、プログラムが正しく動作しなくなります。</span><span class="sxs-lookup"><span data-stu-id="88dc5-107">After moving to a new version of the common language runtime (CLR), a program no longer executes properly:</span></span>  
  
- <span data-ttu-id="88dc5-108">プログラムは、<xref:System.Collections.Hashtable> から正しくないオブジェクトを取得します。</span><span class="sxs-lookup"><span data-stu-id="88dc5-108">The program is getting the wrong object from a <xref:System.Collections.Hashtable>.</span></span>  
  
- <span data-ttu-id="88dc5-109"><xref:System.Collections.Hashtable> からの列挙の順序に、プログラムが動作しなくなる変更があります。</span><span class="sxs-lookup"><span data-stu-id="88dc5-109">The order of enumeration from a <xref:System.Collections.Hashtable> has a change that breaks the program.</span></span>  
  
- <span data-ttu-id="88dc5-110">以前は等しかった 2 つのオブジェクトが、等しくなくなっています。</span><span class="sxs-lookup"><span data-stu-id="88dc5-110">Two objects that used to be equal are no longer equal.</span></span>  
  
- <span data-ttu-id="88dc5-111">以前は等しくなかった 2 つのオブジェクトが、等しくなっています。</span><span class="sxs-lookup"><span data-stu-id="88dc5-111">Two objects that used to not be equal are now equal.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="88dc5-112">原因</span><span class="sxs-lookup"><span data-stu-id="88dc5-112">Cause</span></span>  

 <span data-ttu-id="88dc5-113"><xref:System.Collections.Hashtable> へのキーに対するクラスの <xref:System.Object.Equals%2A> メソッドの実装は、<xref:System.Object.GetHashCode%2A> メソッドの呼び出しの結果を比較することによりオブジェクトの等価性をテストするため、プログラムが <xref:System.Collections.Hashtable> から正しくないオブジェクトを取得している可能性があります。</span><span class="sxs-lookup"><span data-stu-id="88dc5-113">Your program may be getting the wrong object from a <xref:System.Collections.Hashtable> because the implementation of the <xref:System.Object.Equals%2A> method on the class for the key into the <xref:System.Collections.Hashtable> tests for equality of objects by comparing the results of the call to the <xref:System.Object.GetHashCode%2A> method.</span></span> <span data-ttu-id="88dc5-114">それぞれのフィールドの値が異なる場合であっても、2 つのオブジェクトのハッシュ コードが同じになる場合があるので、オブジェクトの等価性のテストにハッシュ コードを使うことはできません。</span><span class="sxs-lookup"><span data-stu-id="88dc5-114">Hash codes should not be used to test for object equality because two objects may have the same hash code even if their respective fields have different values.</span></span> <span data-ttu-id="88dc5-115">実際にはまれなことですが、ハッシュ コードの衝突が発生します。</span><span class="sxs-lookup"><span data-stu-id="88dc5-115">These hash code collisions, although rare in practice, do occur.</span></span> <span data-ttu-id="88dc5-116">このことによる <xref:System.Collections.Hashtable> のルックアップへの影響としては、等しくない 2 つのキーが等しいものと見なされ、正しくないオブジェクトが <xref:System.Collections.Hashtable> から返されます。</span><span class="sxs-lookup"><span data-stu-id="88dc5-116">The effect this has on a <xref:System.Collections.Hashtable> lookup is that two keys which are not equal appear to be equal, and the wrong object is returned from the <xref:System.Collections.Hashtable>.</span></span> <span data-ttu-id="88dc5-117">パフォーマンス上の理由から、<xref:System.Object.GetHashCode%2A> の実装はランタイム バージョンによって変更される場合があり、あるバージョンでは発生しない競合が後のバージョンでは発生する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="88dc5-117">For performance reasons, the implementation of <xref:System.Object.GetHashCode%2A> can change between runtime versions, so collisions that might not occur on one version might occur on subsequent versions.</span></span> <span data-ttu-id="88dc5-118">ハッシュ コードが競合するときのバグがコードにあるかどうかをテストするには、この MDA を有効にします。</span><span class="sxs-lookup"><span data-stu-id="88dc5-118">Enable this MDA to test whether your code has bugs when hash codes collide.</span></span> <span data-ttu-id="88dc5-119">この MDA を有効にすると、<xref:System.Object.GetHashCode%2A> メソッドは 0 を返すようになり、結果としてすべてのハッシュ コードが競合します。</span><span class="sxs-lookup"><span data-stu-id="88dc5-119">When enabled, this MDA causes the <xref:System.Object.GetHashCode%2A> method to return 0, resulting in all hash codes colliding.</span></span> <span data-ttu-id="88dc5-120">この MDA を有効にすることによるプログラムへの唯一の影響は、プログラムの実行が遅くなることです。</span><span class="sxs-lookup"><span data-stu-id="88dc5-120">The only effect enabling this MDA should have on your program is that your program runs slower.</span></span>  
  
 <span data-ttu-id="88dc5-121">キー変更のハッシュ コードの計算に使われるアルゴリズムがランタイムのあるバージョンから別のバージョンに変更された場合、<xref:System.Collections.Hashtable> からの列挙の順序が変わる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="88dc5-121">The order of enumeration from a <xref:System.Collections.Hashtable> may change from one version of the runtime to another if the algorithm used to compute the hash codes for the key change.</span></span> <span data-ttu-id="88dc5-122">ハッシュ テーブルからのキーまたは値の列挙順序にプログラムが依存しているかどうかは、この MDA を有効にすることでテストできます。</span><span class="sxs-lookup"><span data-stu-id="88dc5-122">To test whether your program has taken a dependency on the order of enumeration of keys or values out of a hash table, you can enable this MDA.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="88dc5-123">解像度</span><span class="sxs-lookup"><span data-stu-id="88dc5-123">Resolution</span></span>  

 <span data-ttu-id="88dc5-124">オブジェクト ID の代わりに、ハッシュ コードを使わないでください。</span><span class="sxs-lookup"><span data-stu-id="88dc5-124">Never use hash codes as a substitute for object identity.</span></span> <span data-ttu-id="88dc5-125">ハッシュ コードを比較しないように、<xref:System.Object.Equals%2A?displayProperty=nameWithType> メソッドのオーバーライドを実装します。</span><span class="sxs-lookup"><span data-stu-id="88dc5-125">Implement the override of the <xref:System.Object.Equals%2A?displayProperty=nameWithType> method to not compare hash codes.</span></span>  
  
 <span data-ttu-id="88dc5-126">ハッシュ テーブル内のキーまたは値の列挙の順序への依存関係を作成しないでください。</span><span class="sxs-lookup"><span data-stu-id="88dc5-126">Do not create dependencies on the order of enumerations of keys or values in hash tables.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="88dc5-127">ランタイムへの影響</span><span class="sxs-lookup"><span data-stu-id="88dc5-127">Effect on the Runtime</span></span>  

 <span data-ttu-id="88dc5-128">この MDA を有効にすると、アプリケーションの速度が低下します。</span><span class="sxs-lookup"><span data-stu-id="88dc5-128">Applications run more slowly when this MDA is enabled.</span></span> <span data-ttu-id="88dc5-129">この MDA は、返されたハッシュ コードを取得し、代わりに係数で除算したときの余りを返します。</span><span class="sxs-lookup"><span data-stu-id="88dc5-129">This MDA simply takes the hash code that would have been returned and instead returns the remainder when divided by a modulus.</span></span>  
  
## <a name="output"></a><span data-ttu-id="88dc5-130">出力</span><span class="sxs-lookup"><span data-stu-id="88dc5-130">Output</span></span>  

 <span data-ttu-id="88dc5-131">この MDA に出力はありません。</span><span class="sxs-lookup"><span data-stu-id="88dc5-131">There is no output for this MDA.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="88dc5-132">構成</span><span class="sxs-lookup"><span data-stu-id="88dc5-132">Configuration</span></span>  

 <span data-ttu-id="88dc5-133">`modulus` 属性では、ハッシュ コードで使う係数を指定します。</span><span class="sxs-lookup"><span data-stu-id="88dc5-133">The `modulus` attribute specifies the modulus used on the hash code.</span></span> <span data-ttu-id="88dc5-134">既定値は 1 です。</span><span class="sxs-lookup"><span data-stu-id="88dc5-134">The default value is 1.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <moduloObjectHashcode modulus="1" />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a><span data-ttu-id="88dc5-135">関連項目</span><span class="sxs-lookup"><span data-stu-id="88dc5-135">See also</span></span>

- <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType>
- <xref:System.Object.Equals%2A?displayProperty=nameWithType>
- [<span data-ttu-id="88dc5-136">マネージド デバッグ アシスタントによるエラーの診断</span><span class="sxs-lookup"><span data-stu-id="88dc5-136">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
