---
title: -out
ms.date: 07/20/2015
helpviewer_keywords:
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
ms.openlocfilehash: 7c013270c8a6b7c2b28f02766df7437b43075dd2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/23/2020
ms.locfileid: "91098905"
---
# <a name="-out-visual-basic"></a>-out (Visual Basic)

出力ファイルの名前を指定します。  
  
## <a name="syntax"></a>構文  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>引数  
  
|期間|定義|  
|---|---|  
|`filename`|必須です。 コンパイラによって作成される出力ファイルの名前。 ファイル名に空白が含まれている場合は、名前を二重引用符 (" ") で囲みます。|  
  
## <a name="remarks"></a>Remarks  

 作成するファイルの完全な名前と拡張子を指定します。 そうしない場合、.exe ファイル名は `Sub Main` プロシージャを含むソースコード ファイルの名前になり、.dll ファイル名は最初のソースコード ファイルの名前になります。  
  
 .exe または .dll 拡張子のないファイル名を指定すると、コンパイラによって、`-target` コンパイラ オプションに指定された値に応じて、自動的に拡張子が追加されます。  
  
|Visual Studio 統合開発環境で -out を設定するには|  
|---|  
|1.**ソリューション エクスプローラー**でプロジェクトを選択します。 **[プロジェクト]** メニューの **[プロパティ]** をクリックします。 <br />2. **[アプリケーション]** タブをクリックします。<br />3. **[アセンブリ名]** ボックスで値を変更します。|  
  
## <a name="example"></a>例  

 次のコードでは `T2.vb` をコンパイルし、出力ファイル `T2.exe` を作成します。  
  
```console
vbc t2.vb -out:t3.exe  
```  
  
## <a name="see-also"></a>関連項目

- [Visual Basic のコマンド ライン コンパイラ](index.md)
- [-target (Visual Basic)](target.md)
- [コンパイル コマンド ラインのサンプル](sample-compilation-command-lines.md)
