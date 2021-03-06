---
title: Оператор TypeOf (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: e5cb1ddc130a8b1913f30b0d20d27941005dd9d3
ms.sourcegitcommit: ca2ca60e6f5ea327f164be7ce26d9599e0f85fe4
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/06/2019
ms.locfileid: "65063250"
---
# <a name="typeof-operator-visual-basic"></a>Оператор TypeOf (Visual Basic)
Проверяет, является ли тип среды выполнения результата выражения совместимый с типом с указанным типом.
  
## <a name="syntax"></a>Синтаксис  
  
```  
result = TypeOf objectexpression Is typename  
```  
  
```  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a>Части  
 `result`  
 Возвращено. Значение `Boolean`.  
  
 `objectexpression`  
 Обязательный. Любое выражение, результатом которого является тип ссылки.  
  
 `typename`  
 Обязательный. Любое имя типа данных.  
  
## <a name="remarks"></a>Примечания  
 Оператор `TypeOf` определяет, совместим ли тип времени выполнения `objectexpression` с `typename`. Совместимость зависит от категории типа `typename`. В следующей таблице показано, как определяется совместимость.  
  
|Категория типа `typename`|Критерий совместимости|  
|---------------------------------|-----------------------------|  
|Класс|`objectexpression` типа `typename` или наследует от `typename`|  
|Структура|`objectexpression` типа `typename`|  
|Интерфейс|`objectexpression` реализует `typename` или наследует от класса, реализующего `typename`|  
  
 Если тип времени выполнения `objectexpression` удовлетворяет критерию совместимости, `result` является `True`. В противном случае `result` является `False`.  Если `objectexpression` имеет значение null, то `TypeOf`...`Is` возвращает `False`, а ...`IsNot` возвращает `True`.  
  
 `TypeOf` всегда используется с ключевым словом `Is` для создания выражения `TypeOf`...`Is` или с ключевым словом `IsNot` для создания выражения `TypeOf`...`IsNot`.  
  
## <a name="example"></a>Пример  
 В следующем примере выражение `TypeOf`...`Is` используется для проверки на совместимость типов двух переменных ссылок на объекты с различными типами данных.  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 Переменная `refInteger` имеет тип времени выполнения `Integer`. Она совместима с `Integer`, но не с `Double`. Переменная `refForm` имеет тип времени выполнения <xref:System.Windows.Forms.Form>. Она совместима с <xref:System.Windows.Forms.Form>, так как это ее тип, с <xref:System.Windows.Forms.Control>, так как <xref:System.Windows.Forms.Form> наследует от <xref:System.Windows.Forms.Control>, и с <xref:System.ComponentModel.IComponent>, так как <xref:System.Windows.Forms.Form> наследует от <xref:System.ComponentModel.Component>, который реализует <xref:System.ComponentModel.IComponent>. Однако `refForm` несовместима с <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>См. также

- [Оператор Is](../../../visual-basic/language-reference/operators/is-operator.md)
- [Оператор IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Операторы сравнения в Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Порядок применения операторов в Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Список операторов, сгруппированных по функциональному назначению](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Операторы и выражения](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
