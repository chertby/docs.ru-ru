---
title: Как выполнить Совместное использование сборки с другими приложениями (C#)
ms.date: 07/20/2015
ms.assetid: c30e972b-1693-4e05-b115-c31831fdf9f2
ms.openlocfilehash: 8bb36c2aded1144349b86b17a45eef4b48c8aabe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "59314793"
---
# <a name="how-to-share-an-assembly-with-other-applications-c"></a>Как выполнить Совместное использование сборки с другими приложениями (C#)
Сборки могут быть закрытыми или общими. По умолчанию большинство простых программ состоят из закрытой сборки, так как она не предназначена для использования другими приложениями.  
  
 Для совместного использования сборки с другими приложениями ее необходимо поместить в [глобальный кэш сборок](../../../../framework/app-domains/gac.md) (GAC).  
  
### <a name="sharing-an-assembly"></a>Предоставление общего доступа к сборке  
  
1. Создайте сборку. Дополнительные сведения см. в разделе [Создание сборок](../../../../framework/app-domains/create-assemblies.md).  
  
2. Назначьте сборке строгое имя. Дополнительные сведения см. в разделе [Как Подписание сборки строгим именем](../../../../framework/app-domains/how-to-sign-an-assembly-with-a-strong-name.md).  
  
3. Назначьте сведения о версии для сборки. Дополнительные сведения см. в разделе [Версии сборок](../../../../../docs/framework/app-domains/assembly-versioning.md).  
  
4. Добавьте сборку в глобальный кэш сборок. Дополнительные сведения см. в разделе [Как Установка сборки в глобальный кэш сборок](../../../../framework/app-domains/how-to-install-an-assembly-into-the-gac.md).  
  
5. Получите доступ к типам, содержащимся в сборке, из других приложений. Дополнительные сведения см. в разделе [Как Создание ссылки на сборку со строгим именем](../../../../framework/app-domains/how-to-reference-a-strong-named-assembly.md).  
  
## <a name="see-also"></a>См. также

- [Руководство по программированию на C#](../../../../csharp/programming-guide/index.md)
- [Программирование с использованием сборок](../../../../framework/app-domains/programming-with-assemblies.md)
