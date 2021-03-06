---
title: Общие сведения о безопасности модели автоматизации пользовательского интерфейса
ms.date: 03/30/2017
helpviewer_keywords:
- UI Automation, security model
- security model, UI Automation
ms.assetid: 1d853695-973c-48ae-b382-4132ae702805
ms.openlocfilehash: c74f770f917fc3b2a7d3a18c08270745dac68b12
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422434"
---
# <a name="ui-automation-security-overview"></a>Общие сведения о безопасности модели автоматизации пользовательского интерфейса

> [!NOTE]
> Эта документация предназначена для разработчиков .NET Framework, желающих использовать управляемые классы [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] , заданные в пространстве имен <xref:System.Windows.Automation> . Для получения последних сведений о [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], см. в разделе [API автоматизации Windows: Модели автоматизации пользовательского интерфейса](https://go.microsoft.com/fwlink/?LinkID=156746).

В этом обзоре описывается модель безопасности для [!INCLUDE[TLA#tla_uiautomation](../../../includes/tlasharptla-uiautomation-md.md)] в [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)].

<a name="User_Account_Control"></a>

## <a name="user-account-control"></a>контроль учетных записей

Безопасность является основным направлением [!INCLUDE[TLA#tla_winvista](../../../includes/tlasharptla-winvista-md.md)] , и среди нововведений можно отметить, что пользователи имеют возможность выполнять запуск от имени обычных пользователей (не администраторов) без обязательной блокировки запуска приложений и служб, которым требуются более высокие привилегии.

В [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)]большинство приложений предоставляется с помощью стандартного или административного токена. Если приложение не идентифицировано как административное приложение, оно запускается в качестве стандартного приложения по умолчанию. Прежде чем приложение, идентифицированное как административное, может быть запущено, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] запрашивает у пользователя разрешение на запуск приложения с повышенными привилегиями. Запрос на продолжение отображается по умолчанию, даже если пользователь является членом локальной группы администраторов, так как администраторы выполняют запуск как обычные пользователи, пока приложение или системный компонент, которому требуются административные учетные данные, не запросит разрешение на запуск.

<a name="Tasks_Requiring_Higher_Privileges"></a>

## <a name="tasks-requiring-higher-privileges"></a>Задачи, требующие повышенных привилегий

Когда пользователь пытается выполнить задачу, для которой требуются административные привилегии, [!INCLUDE[TLA2#tla_winvista](../../../includes/tla2sharptla-winvista-md.md)] выводит диалоговое окно с запросом на продолжение. Это диалоговое окно защищено от межпроцессного взаимодействия, чтобы вредоносные программы не могли имитировать ввод данных пользователем. Аналогичным образом экран входа в систему обычно недоступен для других процессов.

Клиенты автоматизации пользовательского интерфейса должны взаимодействовать с другими процессами, а некоторые из них могут запускаться с повышенным уровнем привилегий. Клиентам также может требоваться доступ к диалоговым окнам системы, которые обычно невидимы для других процессов. Таким образом, клиенты [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] должны быть доверенными для системы и должны запускаться со специальными привилегиями.

Чтобы быть доверенными для взаимодействия с приложениями, работающими на более высоком уровне привилегий, приложения должны быть подписаны.

<a name="Manifest_Files"></a>

## <a name="manifest-files"></a>Файлы манифеста

Чтобы получить доступ к защищенному системой пользовательского интерфейса, приложения должны быть построены с файлом манифеста, который включает в себя `uiAccess` атрибут в `requestedExecutionLevel` тег, следующим образом:

```xml
<trustInfo xmlns="urn:schemas-microsoft-com:asm.v3">
  <security>
    <requestedPrivileges>
      <requestedExecutionLevel
        level="highestAvailable"
        uiAccess="true" />
    </requestedPrivileges>
  </security>
</trustInfo>
```

Значение атрибута `level` в этом коде приводится только для примера.

`uiAccess` имеет значение «false» по умолчанию. то есть если этот атрибут указан или если отсутствует манифест сборки, приложение не будет сможет получить доступ к защищенным пользовательского интерфейса.

Дополнительные сведения о [!INCLUDE[TLA#tla_longhorn2](../../../includes/tlasharptla-longhorn2-md.md)] безопасности, подписи приложений и при создании манифестов сборки см. в разделе [передовые методики и рекомендации для приложений в среде с минимальными привилегиями](https://docs.microsoft.com/previous-versions/dotnet/articles/aa480150(v=msdn.10)).
