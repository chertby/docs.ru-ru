---
title: Безопасность (LINQ to DataSet)
ms.date: 03/30/2017
ms.assetid: 6116b2b8-75f4-4d8b-aea6-c13e55cda50b
ms.openlocfilehash: 33af2200c5d672dc63dc7be79833a174bfe31c20
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504255"
---
# <a name="security-linq-to-dataset"></a>Безопасность (LINQ to DataSet)
В этом разделе рассматриваются вопросы безопасности в LINQ to DataSet.  
  
## <a name="passing-a-query-to-an-untrusted-component"></a>Передача запроса недоверенному компоненту  
 LINQ запрос к набору данных может быть создан в одном месте программы и выполнена в другой. В месте своего создания запрос может ссылаться на любые элементы, видимые в этой точке, например закрытые элементы класса, которому принадлежит вызывающий метод, или символы, представляющие локальные переменные или аргументы. Во время выполнения запрос сможет получить доступ к элементам, на которые он ссылался при создании, даже если для вызывающего кода они невидимы. Код, выполняющий запросы, не имеет произвольно добавляемой видимости, то есть он не может выбирать, к каким элементам обращаться. Он сможет получить доступ только к тому, к чему обращается запрос, и только через сам запрос.  
  
 При этом подразумевается, что при передаче ссылки на запрос другому фрагменту кода компонент, получающий запрос, является доверенным и может получить доступ ко всем открытым и закрытым элементам класса, на которые ссылается запрос. Как правило LINQ для запросов набора данных должно не передаваться недоверенным компонентам, если запрос был составлен таким образом, чтобы он не предоставляет сведения, которые должны быть закрытыми.  
  
## <a name="external-input"></a>Внешние входные данные  
 Приложения часто получают внешние входные данные (от пользователя или другого внешнего агента) и выполняют действия над этими входными данными.  В случае LINQ to DataSet приложение может создать запрос определенным образом, на основе внешних входных данных или использовать внешние входные данные в запросе. LINQ to DataSet, запросы принимают параметры везде где допускаются литералы. Разработчикам приложений следует использовать параметризованные запросы, а не внедрять литералы из внешних агентов непосредственно в запрос.  
  
 Любые входные данные, прямо или косвенно полученные от пользователя или внешнего агента, могут иметь содержимое, использующее синтаксис целевого языка для выполнения несанкционированных действий. Это явление называется атакой путем внедрения кода SQL по названию схемы атаки, где целевым языком является Transact-SQL. Вводимые пользователем данные, внедренные непосредственно в запрос, используются для удаления таблицы базы данных, вызова отказа в обслуживании или других изменений выполняемой операции. Несмотря на то, что в LINQ to DataSet допустима композиция запросов, она выполняется через API объектной модели. LINQ для запросов к наборам данных не строятся с помощью манипулирования строками или объединения, как они находятся в Transact-SQL и не может быть уязвимо для атак путем внедрения кода SQL в традиционном понимании.  
  
## <a name="see-also"></a>См. также

- [Руководство по программированию](../../../../docs/framework/data/adonet/programming-guide-linq-to-dataset.md)
