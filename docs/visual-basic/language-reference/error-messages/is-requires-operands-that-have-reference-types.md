---
title: "'Is' には参照型を持つオペランドが必要ですが、このオペランドの値型は '<typename>' です。"
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: 5c9f156272cd0c3cbaeadbc0e162129f41619cc6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163351"
---
# <a name="bc30020-is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a>BC30020:'Is' には参照型を持つオペランドが必要ですが、このオペランドの値型は '\<typename>' です。

`Is` 比較演算子は、2 つのオブジェクト変数が同じインスタンスを参照しているかどうかを判断します。 この比較は、値型に対して定義されていません。

 **エラー ID:** BC30020

## <a name="to-correct-this-error"></a>このエラーを解決するには

- 適切な算術比較演算子または `Like` 演算子を使用して、2 つの値の型を比較します。

## <a name="see-also"></a>関連項目

- [Is 演算子](../operators/is-operator.md)
- [Like 演算子](../operators/like-operator.md)
- [比較演算子](../operators/comparison-operators.md)
