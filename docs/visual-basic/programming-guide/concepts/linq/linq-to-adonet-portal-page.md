---
title: LINQ to ADO.NET (Страница портала)
ms.date: 07/20/2015
ms.assetid: bbbd7c76-2981-4b91-b8d2-437547181f52
ms.openlocfilehash: 850e154b40e69cc655ee1b59161351b0b2898033
ms.sourcegitcommit: b5c59eaaf8bf48ef3ec259f228cb328d6d4c0ceb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/03/2019
ms.locfileid: "67539385"
---
# <a name="linq-to-adonet-portal-page"></a>LINQ to ADO.NET (Страница портала)
LINQ to ADO.NET позволяет запрашивать любой перечисляемый объект, в ADO.NET с помощью [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)] модель программирования.  
  
> [!NOTE]
>  LINQ to ADO.NET документации находится в разделе ADO.NET пакета SDK для .NET Framework: [LINQ и ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md).
  
 Существуют три отдельные технологии ADO.NET [!INCLUDE[vbteclinqext](~/includes/vbteclinqext-md.md)]: LINQ to DataSet, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)]и LINQ to Entities. LINQ to DataSet предоставляет расширенные и оптимизированные запросы к <xref:System.Data.DataSet>, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] включает возможность запрашивать непосредственно схемы базы данных SQL Server и LINQ to Entities позволяет выполнять запросы к модели EDM.  
  
## <a name="linq-to-dataset"></a>LINQ to DataSet  
 <xref:System.Data.DataSet> является одним из наиболее широко используемых компонентов в ADO.NET и ключевым элементом модели автономного программирования, на основе которой создан ADO.NET. Несмотря на все это, объект <xref:System.Data.DataSet> имеет ограниченные возможности запросов.  
  
 LINQ to DataSet позволяет использовать расширенные возможности запросов в <xref:System.Data.DataSet> с помощью той же функциональности, которая доступна для многих других источников данных.  
  
 Дополнительные сведения см. в разделе [LINQ to DataSet](../../../../framework/data/adonet/linq-to-dataset.md).  
  
## <a name="linq-to-sql"></a>LINQ to SQL  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] предоставляет инфраструктуру времени выполнения для управления реляционными данными в виде объектов. В [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] модель данных реляционной базы данных сопоставляется объектной модели, выраженной в языке программирования разработчика. При выполнении приложения [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] преобразует интегрированные в язык запросы из объектной модели в SQL и отправляет их в базу данных для выполнения. Когда база данных возвращает результаты, [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] переводит их обратно в объекты, которыми можно управлять.  
  
 [!INCLUDE[vbtecdlinq](~/includes/vbtecdlinq-md.md)] включает поддержку хранимых процедур, определяемых пользователем функций в базе данных и наследования в объектной модели.  
  
 Дополнительные сведения см. в разделе [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md).  
  
## <a name="linq-to-entities"></a>LINQ to Entities  
 В модели EDM реляционные данные представлены в виде объектов в среде .NET. Благодаря этому поддержка [!INCLUDE[vbteclinq](~/includes/vbteclinq-md.md)] эффективно реализуется на уровне объектов, что позволяет составлять запросы баз данных на языке, используемом для сборки бизнес-логики. Эта возможность называется LINQ to Entities. Дополнительные сведения см. в разделе [LINQ to Entities](../../../../framework/data/adonet/ef/language-reference/linq-to-entities.md).  
  
## <a name="see-also"></a>См. также

- [LINQ и ADO.NET](../../../../framework/data/adonet/linq-and-ado-net.md)
- [Синтаксис LINQ (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/index.md)
