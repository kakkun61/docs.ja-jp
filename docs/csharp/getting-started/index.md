---
title: 作業開始 - C# 言語と .NET の概要"
description: C# と .NET の基本を説明します。 C# 言語および .NET エコシステムの概要をご確認ください。
ms.date: 10/13/2020
ms.openlocfilehash: 94d49be28fbdba8f58ca16e959a10643d6467c63
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92160959"
---
# <a name="introduction-to-the-c-language-and-net"></a>C# 言語と .NET の概要

C# は、洗練されたタイプ セーフなオブジェクト指向言語です。 C# を使用すると、.NET エコシステムで稼働する、安全で信頼性の高い多くの種類のアプリケーションを構築できます。

## <a name="c-language"></a>C# 言語

C# の構文は表現力が豊かですが、単純ですぐに覚えることができます。 C、C++、Java、または JavaScript に慣れていれば、C# の中かっこ ({}) 構文をすぐに理解できます。 これらの言語のいずれかを理解している開発者は、一般に、短期間で C# で生産的に作業できるようになります。 C# には、null 許容型、デリゲート、ラムダ式、パターン マッチング、安全なダイレクト メモリ アクセスなどの強力な機能が実装されています。 C# は、タイプ セーフとパフォーマンスの向上を実現するジェネリック メソッドと型をサポートします。 C# は反復子もサポートしているため、クライアント コードのカスタム動作をコレクション クラスの実装側が定義できます。 統合言語クエリ (LINQ) 式により、厳密に型指定されたクエリは高度な言語構成要素になります。

C# は、オブジェクト指向言語として、カプセル化、継承、およびポリモーフィズムの概念をサポートしています。 親クラスから直接継承できるクラスは 1 つのみですが、クラスで実装できるインターフェイスの数は任意です。 親クラスの仮想メソッドをオーバーライドする場合、誤って再定義しないように、`override` キーワードを指定する必要があります。 C# の構造体はコンパクトなクラスのようなものです。インターフェイスを実装できるスタック割り当て型ですが、継承はサポートされていません。 C# には、主にデータ値を格納する目的を持つクラス型であるレコードも用意されています。

C# には、次のような革新的な言語構成要素がいくつか用意されているため、ソフトウェア コンポーネントの開発が容易になります。

- メソッドのシグネチャをカプセル化する "*デリゲート*"。タイプ セーフなイベント通知を実行できます。
- プロパティ。プライベート メンバー変数へのアクセサーとして機能します。
- 属性。実行時に型に関する宣言のメタデータを提供します。
- インライン XML ドキュメントのコメント。
- 統合言語クエリ (LINQ)。さまざまな種類のデータ ソースを対象とする組み込みのクエリ機能を提供します。
- パターンマッチング。データ型と値を調べることによって制御フローを有効にします。

ネイティブ コンポーネントと対話するには、"相互運用" というプロセスを使用します。 C# プログラムで相互運用機能を使用すると、ネイティブの C++ アプリケーションで実行できる機能をほぼすべて実行できます。 さらに、ダイレクト メモリ アクセスがクリティカルの場合でも、ポインターと "unsafe" コードの概念がサポートされます。

C# のビルド処理は、C や C++ よりも単純で Java よりも柔軟です。 ヘッダー ファイルは分かれていません。また、メソッドや型を特定の順序で宣言する必要はありません。 C# のソース ファイルでは、クラス、構造体、インターフェイス、およびイベントをいくつでも定義できます。

その他に、C# の参照ドキュメントを紹介します。

- 言語の概略については、[C# 言語のツアー](../tour-of-csharp/index.md)に関する記事を参照してください。
- C# 言語の具体的な側面の詳細については、「[C# リファレンス](../language-reference/index.md)」を参照してください。
- LINQ の詳細については、「[統合言語クエリ (LINQ)](../programming-guide/concepts/linq/index.md)」を参照してください。

## <a name="net-platform-architecture"></a>.NET プラットフォーム アーキテクチャ

C# プログラムは、.NET で実行されます。これは、共通言語ランタイム (CLR) と呼ばれる仮想実行システムであり、クラス ライブラリの統合されたセットです。 CLR は、国際規格である共通言語基盤 (CLI) の Microsoft による商用実装です。 CLI は、言語やライブラリをシームレスに連携する実行および開発環境を構築するための基盤です。

C# で記述したソース コードは、CLI 仕様に準拠する[中間言語 (IL)](../../standard/managed-code.md) にコンパイルされます。 IL コードおよびリソース (ビットマップや文字列など) は、アセンブリに保存されます。拡張子は一般的には .dll です。 アセンブリに含まれるマニフェストには、アセンブリの種類、バージョン、およびカルチャに関する情報が規定されています。

C# プログラムを実行すると、アセンブリが CLR に読み込まれます。 CLR によって Just-In-Time (JIT) コンパイルが実行され、IL コードはネイティブのマシン語命令に変換されます。 CLR には、自動的なガベージ コレクション、例外処理、およびリソース管理に関する他のサービスが用意されています。 CLR で実行されるコードは、"マネージド コード" と呼ばれることがあります。反対に、特定のシステムを対象にしたネイティブのマシン語にコンパイルされたコードは、"アンマネージド コード" と呼ばれることがあります。

言語の相互運用性は、.NET の主要機能です。 C# コンパイラによって生成された IL コードは、共通型の仕様 (CTS) に準拠しています。 C# から生成された IL コードは、F#、Visual Basic、C++ の .NET バージョンの他、20 を超える CTS 準拠言語で生成されたコードと相互運用性があります。 1 つのアセンブリには、異なる .NET 言語で記述されたモジュールを複数含めることができます。また、同じ言語で記述されている場合と同様に、型を参照することもできます。

.NET には、実行時のサービス以外にも、広範なライブラリが用意されています。 これらのライブラリは、さまざまなワークロードをサポートします。 これらは、ファイルの入出力、XML 解析のための文字列操作、Web アプリケーションのフレームワーク、Windows フォーム コントロールなど、役に立つさまざまな機能を備えた名前空間に構成されています。 C# アプリケーションでは、一般に、.NET クラス ライブラリを広範囲に使用して、一般的な "配管工事" のような作業を処理しています。

.NET の詳細については、[.NET の概要](../../core/introduction.md)に関する記事を参照してください。
