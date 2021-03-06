---
title: Трассировка и ведение журнала сообщений
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 55fdb31310c62c5d0ac7e5d963309cb1b3fe2da4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/28/2019
ms.locfileid: "64617531"
---
# <a name="tracing-and-message-logging"></a>Трассировка и ведение журнала сообщений
В этом образце показано, как включить трассировку и ведение журнала сообщений. Получаемые трассировки и журналы сообщений можно просмотреть с помощью [программа Service Trace Viewer (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Этот образец основан на [Приступая к работе](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Процедура настройки и инструкции по построению для данного образца приведены в конце этого раздела.  
  
## <a name="tracing"></a>Трассировка  
 Windows Communication Foundation (WCF) использует механизм трассировки, определенный в <xref:System.Diagnostics> пространства имен. В этой модели трассировки данные трассировки создаются источниками трассировки, реализуемыми приложениями. Каждый источник определяется именем. Потребители трассировки создают прослушиватели трассировки для источников трассировки, для которых необходимо извлечь информацию. Чтобы получить данные трассировки, необходимо создать прослушиватель для источника трассировки. В WCF, это можно сделать, добавив следующий код в файл конфигурации службы или клиента, установив источник трассировки модели службы `switchValue`:  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 Дополнительные сведения об источниках трассировки см. в разделе источника трассировки в [Настройка трассировки](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) раздела.  
  
## <a name="activity-tracing-and-propagation"></a>Трассировка и распространение действий  
 Наличие `ActivityTracing` включен и `propagateActivity` присвоено `true` в `system.ServiceModel` источники трассировки клиента и службы обеспечить корреляцию трассировок в логических единицах обработки (действиях), между действиями в конечных точек () путем перенаправления действий) и между действиями с охватом нескольких конечных точек (путем распространения идентификатора действия).  
  
 Эти три механизма (действия, перенаправление и распространение) могут помочь быстрее найти первопричину ошибки с использованием программы Service Trace Viewer. Дополнительные сведения см. в разделе [с помощью программы Service Trace Viewer для просмотра корреляцию трассировок и устранения неполадок](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Возможно расширить трассировку, предоставляемую ServiceModel, создав пользовательские трассировки действий. Пользовательская трассировка действий позволяет пользователю создавать действия трассировки для следующих целей.  
  
- Группирование трассировок в логические блоки обработки.  
  
- Корреляция действий путем перенаправления и распространения.  
  
- Снижение расходов производительности, трассировки WCF (например, дисковое пространство, занимаемое файлом журнала).  
  
 Дополнительные сведения о трассировке пользовательского действия, см. в разделе [расширение трассировки](../../../../docs/framework/wcf/samples/extending-tracing.md) образца.  
  
## <a name="message-logging"></a>Ведение журналов сообщений  
 Можно включить ведение журнала сообщений, и на стороне клиента и службы любого приложения WCF. Чтобы включить ведение журнала сообщений, необходимо добавить следующий код в клиент или службу.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels -->  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 При записи сообщения тип трассировки зависит от того, трассируется оно на стороне клиента или сервера. Например, сообщение "Добавить", отправленное клиенту, трассируется в категории "TransportWrite" на стороне клиента, в то время как то же сообщение трассируется в категории "TransportRead" на стороне службы.  
  
 Настройте прослушиватель трассировки, добавив следующий код в раздел <xref:System.Diagnostics> файла App.config клиента или файла Web.config службы.  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 Сообщения записываются в журнал в формате XML в целевом каталоге, указанном в файле конфигурации.  
  
> [!NOTE]
>  Файлы трассировки невозможно создать, если не создан каталог журнала. Убедитесь, что каталог C:\logs\ существует или укажите альтернативный каталог ведения журнала в конфигурации прослушивателя. Дополнительные сведения см. в первоначальных инструкциях по настройке, приведенных в конце данного документа.  
  
 Дополнительные сведения о ведении журнала сообщений см. в разделе [Настройка ведения журнала сообщений](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) раздела.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Настройка, сборка и выполнение образца  
  
1. Убедитесь, что вы выполнили [выполняемая однократно процедура настройки для образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Перед выполнением образца трассировки и ведения журнала сообщений создайте каталог C:\logs\, чтобы служба записывала данные в файлы с расширением SVCLOG. Имя этого каталога определяется в файле конфигурации как путь для трассировок и сообщений для записи в журнал, и его можно изменить. Предоставьте сетевой службе пользователя доступ к записи в каталог журналов.  
  
3. Чтобы создать выпуск решения на C#, C++ или Visual Basic .NET, следуйте инструкциям в [сборка образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Чтобы запустить образец в конфигурации с одной или нескольких компьютерах, следуйте инструкциям в [выполнение образцов Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] примеры. Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>См. также

- [Трассировка](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Образцы наблюдения за AppFabric](https://go.microsoft.com/fwlink/?LinkId=193959)
