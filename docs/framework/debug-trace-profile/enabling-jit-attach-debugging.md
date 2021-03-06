---
title: JIT アタッチ デバッグの有効化
description: エラーが発生したときにデバッガーをプロセスにアタッチするには、just-in-time (JIT) アタッチデバッグを有効にします。 特定のメソッドまたは関数によってトリガーされる場合があります。
ms.date: 03/30/2017
helpviewer_keywords:
- JIT-attach debugging
- debugging [.NET Framework], JIT-attach debugging
ms.assetid: f91fc5f7-de5a-4f23-b6ac-f450e63c662e
ms.openlocfilehash: dc1c8608b0d16e618b5ad6144d492db3302532dc
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2020
ms.locfileid: "96273504"
---
# <a name="enabling-jit-attach-debugging"></a>JIT アタッチ デバッグの有効化

JIT アタッチ デバッグとは、エラーが発生したとき、または特定のメソッドまたは関数によってトリガーすることで、プロセスにデバッガーをアタッチすることを表すために使用される語句です。  
  
 JIT アタッチ デバッグは、次のエラー状態で使用されます。  
  
- 未処理の例外 (ネイティブ コードとマネージド コードの両方)。  
  
- <xref:System.Environment.FailFast%2A?displayProperty=nameWithType> メソッドまたは [RaiseFailFastException](/windows/win32/api/errhandlingapi/nf-errhandlingapi-raisefailfastexception) 関数 (Windows 7 ファミリ)。  
  
- 実行時の致命的なエラー。  
  
 JIT アタッチ デバッグは、次のメソッドや関数への呼び出しによってもトリガーされます。  
  
- <xref:System.Diagnostics.Debugger.Launch%2A?displayProperty=nameWithType> メソッド  
  
- <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> メソッド  
  
- [DebugBreak](/windows/win32/api/debugapi/nf-debugapi-debugbreak) 関数 (Win32)。  
  
 .NET Framework 4 より前の .NET Framework では、ネイティブデバッガーとマネージデバッガーの動作を制御するために個別のレジストリキーが提供されていました。 .NET Framework 4 以降では、コントロールは単一のレジストリキー (HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\Current Version\AeDebug) の下に統合されます。 このキーに設定できる値により、デバッガーを呼び出すかどうか、呼び出す場合は、ユーザーの操作を必要とするダイアログ ボックスによって呼び出すかどうかが決まります。 このレジストリキーの設定の詳細については、「 [自動デバッグの構成](/windows/win32/debug/configuring-automatic-debugging)」を参照してください。  
  
## <a name="see-also"></a>関連項目

- [デバッグ、トレース、およびプロファイリング](index.md)
- [イメージのデバッグの簡略化](making-an-image-easier-to-debug.md)
