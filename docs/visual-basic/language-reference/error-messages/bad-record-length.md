---
title: Недопустимая длина записи
ms.date: 07/20/2015
f1_keywords:
- vbrID59
ms.assetid: 0926a3a4-177b-4452-9b33-d8a01e24cc21
ms.openlocfilehash: 7ec0a8c27f425ec717bca5d45d5dfd2b601c11d5
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64665730"
---
# <a name="bad-record-length"></a>Недопустимая длина записи
Некоторые из возможных причин этой ошибки:  
  
- Длина переменной записи, указанной в `FileGet`, `FileGetObject`, `FilePut` или `FilePutObject` инструкция отличается от длины, указанной в соответствующем `FileOpen` инструкции.  
  
- Эту переменную в `FilePut` или `FilePutObject` инструкция или включает строку переменной длины.  
  
- Эту переменную в `FilePut` или `FilePutObject` является или включает `Variant` типа.  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
1. Убедитесь, что сумма размеров переменных фиксированной длины в определяемый пользователем тип, определяющий тип переменной записи совпадает со значением, заданным в `FileOpen` инструкции `Len` предложение.  
  
2. Если переменная в `FilePut` или `FilePutObject` инструкцию или включает строку переменной длины, то убедитесь, что строка переменной длины по крайней мере 2 символов, короче, чем длина записи, указанная в `Len` предложении `FileOpen` инструкция.  
  
3. Если переменная в `FilePut` или `FilePutObject` является или включает `Variant` убедитесь, что строка переменной длины по крайней мере 4 байта короче, чем длина записи, указанной в `Len` предложении `FileOpen` инструкции.  
  
## <a name="see-also"></a>См. также

- <xref:Microsoft.VisualBasic.FileSystem.FileGet%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FileGetObject%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePut%2A>
- <xref:Microsoft.VisualBasic.FileSystem.FilePutObject%2A>
