---
title: сложный тип
ms.date: 03/30/2017
ms.assetid: 63efbd23-11d4-4871-bc88-ad01b9837553
ms.openlocfilehash: a6a7190a144280930d67f179373f29f6b19e98cc
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64583663"
---
# <a name="complex-type"></a>сложный тип
Объект *сложного типа* — это шаблон для определения расширенных структурированных свойств в [типы сущностей](../../../../docs/framework/data/adonet/entity-type.md) или на других сложных типов. Каждый шаблон содержит следующие сведения.  
  
- Уникальное имя. (Обязательный атрибут).  
  
    > [!NOTE]
    >  Имя сложного типа не может быть таким же, что и имя типа сущности внутри одного и того же пространства имени.  
  
- Данные в виде одного или нескольких [свойства](../../../../docs/framework/data/adonet/property.md). (Необязательно.)  
  
    > [!NOTE]
    >  Свойство сложного типа может быть другим сложным типом.  
  
 Сложный тип похож на тип сущности тем, что сложный тип может содержать полезные данные в форме свойств примитивного типа или других сложных типов. Однако между сложными типами и типами сущности существуют некоторые ключевые различия.  
  
- Сложные типы не имеют идентификаторов и поэтому не могут существовать независимо. Сложные типы могут существовать только как свойства типов сущностей или других сложных типов.  
  
- Сложные типы не могут участвовать в [ассоциации](../../../../docs/framework/data/adonet/association-type.md). Ни один конец ассоциации может быть сложным типом и поэтому [свойства навигации](../../../../docs/framework/data/adonet/navigation-property.md) нельзя определить для сложных типов.  
  
## <a name="example"></a>Пример  
 [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) использует доменный язык (DSL), называемый языком определения концептуальной схемы ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) для определения концептуальных моделей. Далее на языке CSDL определяется сложный тип, адрес со свойствами примитивного типа `StreetAddress`, `City`, `StateOrProvince`, `Country` и `PostalCode`.  
  
 [!code-xml[EDM_Example_Model#ComplexTypeExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books2.edmx#complextypeexample)]  
  
 Чтобы определить сложный тип `Address` (показанный выше) как свойство типа сущности, необходимо объявить тип свойства в определении типа сущности. Далее на языке CSDL объявляется свойство `Address` в виде сложного типа в типе сущности (издателе).  
  
 [!code-xml[EDM_Example_Model#EntityWithComplexType](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books3.edmx#entitywithcomplextype)]  
  
## <a name="see-also"></a>См. также

- [Основные понятия модели EDM](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [Сущностная модель данных](../../../../docs/framework/data/adonet/entity-data-model.md)
