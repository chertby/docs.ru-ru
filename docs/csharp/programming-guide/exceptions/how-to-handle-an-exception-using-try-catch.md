---
title: Практическое руководство. Обработка исключений с помощью блока try-catch (руководство по программированию на C#)
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- exception handling [C#], try/catch blocks
- exceptions [C#], try/catch blocks
- try/catch blocks [C#]
ms.assetid: ca8e3773-980e-4767-8633-7408540e9818
ms.openlocfilehash: 0524248a0b82ddc115e82108f774e894f1dc2f26
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/01/2019
ms.locfileid: "57201616"
---
# <a name="how-to-handle-an-exception-using-trycatch-c-programming-guide"></a>Практическое руководство. Обработка исключений с помощью блока try-catch (руководство по программированию на C#)
Блок [try-catch-](../../../csharp/language-reference/keywords/try-catch.md) предназначен для перехвата и обработки исключений, происходящих в исполняемом коде. Некоторые исключения могут обрабатываться в блоке `catch`, и проблема решается без повторного создания исключения. Но в большинстве случаев на этом этапе можно только проверить, что создано подходящее исключение.  
  
## <a name="example"></a>Пример  
 В этом примере <xref:System.IndexOutOfRangeException> не является наиболее подходящим исключением. Для данного метода больше подходит исключение <xref:System.ArgumentOutOfRangeException>, поскольку ошибка вызвана переданным методу аргументом `index`.  
  
 [!code-csharp[csProgGuideExceptions#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideExceptions/CS/Exceptions.cs#5)]  
  
## <a name="comments"></a>Комментарии  
 Код, вызывающий исключение, находится в блоке `try`. Оператор `catch` добавляется сразу после него, чтобы обрабатывать исключение `IndexOutOfRangeException`, если оно происходит. Блок `catch` обрабатывает исключение `IndexOutOfRangeException` и вместо него вызывает более подходящее исключение `ArgumentOutOfRangeException`. Чтобы вызывающий объект получил максимально подробную информацию, рекомендуется указать исходное исключение в качестве значения <xref:System.Exception.InnerException%2A> нового исключения. Поскольку свойство <xref:System.Exception.InnerException%2A> [доступно только для чтения](../../../csharp/language-reference/keywords/readonly.md), его значение необходимо присваивать только в конструкторе нового исключения.  
  
## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../../../csharp/programming-guide/index.md)
- [Исключения и обработка исключений](../../../csharp/programming-guide/exceptions/index.md)
- [Обработка исключений](../../../csharp/programming-guide/exceptions/exception-handling.md)
