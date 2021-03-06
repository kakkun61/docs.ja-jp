---
title: DLL 読み込み時のエラーです。
ms.date: 07/20/2015
f1_keywords:
- vbrID48
ms.assetid: 4226cd1f-028c-477d-88a5-cb57f7e0cdc8
ms.openlocfilehash: 35733fe2e20d46207f6cfdaee32f6559fceed6eb
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/22/2020
ms.locfileid: "90874376"
---
# <a name="error-in-loading-dll-visual-basic"></a>DLL 読み込み時のエラーです。(Visual Basic)

ダイナミックリンク ライブラリ (DLL) は、`Declare` ステートメントの `Lib` 句で指定されたライブラリです。 このエラーには、次の原因が考えられます。  
  
- ファイルが DLL 実行可能ファイルではありません。  
  
- ファイルが Microsoft Windows DLL ではありません。  
  
- DLL が存在しない別の DLL を参照しています。  
  
- DLL または参照先の DLL が、パスで指定されたディレクトリにありません。  
  
## <a name="to-correct-this-error"></a>このエラーを解決するには  
  
- ファイルがソーステキスト ファイルであり、そのため DLL 実行可能ファイルでない場合は、コンパイルして DLL 実行可能形式にリンクする必要があります。  
  
- ファイルが Microsoft Windows DLL でない場合は、Microsoft Windows と同等のものを取得します。  
  
- DLL が存在しない別の DLL を参照している場合は、参照先の DLL を取得して、使用できるようにします。  
  
- DLL または参照先の DLL がパスによって指定されたディレクトリにない場合は、DLL を参照先のディレクトリに移動します。  
  
## <a name="see-also"></a>関連項目

- [Declare ステートメント](../statements/declare-statement.md)
