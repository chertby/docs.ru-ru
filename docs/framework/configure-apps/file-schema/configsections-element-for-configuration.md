---
title: Элемент <configSections> для <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: d522d004630dee942e24c39a936feae7dc957bd5
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300793"
---
# <a name="configsections-element-for-configuration"></a>\<configSections > элемент для \<configuration >

Содержит раздел конфигурации и пространства имен объявления.

[ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp; **\<configSections >**

## <a name="attributes"></a>Атрибуты

Нет

## <a name="parent-element"></a>Родительский элемент

|     | Описание |
| --- | ----------- |
| [ **\<configuration>** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework. |

## <a name="child-elements"></a>Дочерние элементы

|     | Описание |
| --- | ----------- |
| [ **\<раздел >** ](~/docs/framework/configure-apps/file-schema/section-element.md) | Содержит объявление раздела конфигурации. |
| [ **\<sectionGroup >** ](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Определяет пространство имен для разделов конфигурации. |
| [ **\<remove>** ](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | Удаляет предварительно определенный раздел или группу разделов. |
| [ **\<clear>** ](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | Удаляет все ранее определенные разделы и группы разделов. |

## <a name="remarks"></a>Примечания

Если этот элемент находится в файле конфигурации, его необходимо первый дочерний элемент элемента  **\<конфигурации >** элемент.

## <a name="example"></a>Пример

В следующем примере показано, как определения раздела конфигурации и его параметров:

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>файл конфигурации

Этот элемент может использоваться в файле конфигурации приложения, файл конфигурации компьютера (*Machine.config*), и *Web.config* файлы, которые не на уровне каталога приложения.

## <a name="see-also"></a>См. также

- [Схема файла конфигурации для .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
