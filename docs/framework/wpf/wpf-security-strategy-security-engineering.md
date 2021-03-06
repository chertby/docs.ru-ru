---
title: Стратегия безопасности WPF — проектирование безопасности
ms.date: 03/30/2017
helpviewer_keywords:
- security [WPF], testing techniques
- Security Development Lifecycle (SDL), security analysis [WPF]
- Security Development Lifecycle (SDL), threat modeling
- Security Development Lifecycle (SDL), testing techniques
- Security Development Lifecycle (SDL), source analysis tools
- Security Development Lifecycle (SDL), critical code management
- threat modeling [WPF]
ms.assetid: 0fc04394-4e47-49ca-b0cf-8cd1161d95b9
ms.openlocfilehash: d5bcd5b06f6d922b29c2a494f1f63da1217e2b2d
ms.sourcegitcommit: 10736f243dd2296212e677e207102c463e5f143e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 08/06/2019
ms.locfileid: "68817872"
---
# <a name="wpf-security-strategy---security-engineering"></a>Стратегия безопасности WPF — проектирование безопасности
Trustworthy Computing (защищенные информационные системы) — это инициатива корпорации Майкрософт по созданию безопасного кода. Ключевым элементом для создания защищенных информационных систем является [!INCLUDE[TLA#tla_sdl](../../../includes/tlasharptla-sdl-md.md)]. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] является технической практикой, которая используется в сочетании со стандартными инженерными процессами для облегчения доставки безопасного кода. [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] состоит из десяти этапов, которые объединяют рекомендации с формализацией, измеряемостью и дополнительными структурами, включая:  
  
- анализ разработки безопасности;  
  
- проверки качества на основе инструментов;  
  
- тестирование уязвимости;  
  
- окончательный анализ безопасности;  
  
- управление безопасностью после выпуска продукта.  
  
## <a name="wpf-specifics"></a>Особенности WPF  
 Группа разработки [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] применяет и расширяет [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)], сочетание которых включает следующие ключевые аспекты.  
  
 [Моделирование угроз](#threat_modeling)  
  
 [Анализ безопасности и средства редактирования](#tools)  
  
 [Способы тестирования](#techniques)  
  
 [Управление критическим кодом](#critical_code)  
  
<a name="threat_modeling"></a>   
### <a name="threat-modeling"></a>Моделирование угроз  
 Моделирование угроз является основным компонентом [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] и используется для профилирования системы, чтобы определить потенциальные уязвимости системы безопасности. После обнаружения уязвимостей моделирование угроз также гарантирует принятие соответствующих мер по снижению уязвимости.  
  
 На высоком уровне моделирование угроз включает следующие основные этапы, если использовать в качестве примера продуктовый магазин.  
  
1. **Идентификация активов**. Активы продуктового магазина могут включать сотрудников, сейф, кассовые аппараты и склад.  
  
2. **Перечисление точек входа**. Точки входа продуктового магазина могут включать переднюю и заднюю двери, окна, погрузочный док и установки для кондиционирования воздуха.  
  
3. **Изучение атак на активы с использованием точек входа**. Одна из возможных атак может быть предпринята на *сейф* продуктового магазина через *установку для кондиционирования воздуха*; эта установка может быть выкручена, чтобы вытянуть через нее сейф и покинуть магазин.  
  
 Моделирование угроз применяется во всем [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] и включает следующее.  
  
- Как средство синтаксического анализа [!INCLUDE[TLA2#tla_xaml](../../../includes/tla2sharptla-xaml-md.md)] читает файлы, сопоставляет текст с соответствующими классами объектной модели и создает фактический код.  
  
- Как дескриптор окна (hWnd) создается, отправляет сообщения и используется для отображения содержимого окна.  
  
- Как привязка данных получает ресурсы и взаимодействует с системой.  
  
 Эти модели угроз важны для идентификации требований к разработке системы безопасности и снижения угроз в процессе разработки.  
  
<a name="tools"></a>   
### <a name="source-analysis-and-editing-tools"></a>Анализ безопасности и средства редактирования  
 В дополнение к ручному анализу кода безопасности элементов [!INCLUDE[TLA2#tla_sdl](../../../includes/tla2sharptla-sdl-md.md)] группа  [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] использует несколько средств для анализа источника и связанных правок для уменьшения уязвимости системы безопасности. Используются широкий диапазон средств, который включает следующее.  
  
- **FxCop**: Находит распространенные проблемы безопасности в управляемом коде, начиная от правил наследования до использования управления доступом для кода, чтобы безопасно взаимодействовать с неуправляемым кодом. См. раздел [FXCop](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.0/bb429476%28v=vs.80%29).  
  
- **Префикс/с быстрой скоростью**: Находит уязвимости системы безопасности и распространенные проблемы безопасности в неуправляемом коде, такие как переполнение буфера, проблемы форматирования строк и проверка ошибок.  
  
- **Запрещенные API**: Поиск в исходном коде для обнаружения случайного использования функций, которые хорошо известны для обеспечения безопасности, например `strcpy`. После идентификации эти функции заменяются альтернативными вариантами, которые являются более безопасными.  
  
<a name="techniques"></a>   
### <a name="testing-techniques"></a>Способы тестирования  
 [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] использует различные методы тестирования безопасности, включая следующие.  
  
- **Тестирование методом белого ящика**: Тестеры просматривают исходный код, а затем создают проверки эксплойтов.
  
- **Тестирование блаккбокс**: Тестировщики пытаются найти эксплойты безопасности, изучив API и функции, а затем попытаемся атаковать продукт.  
  
- **Регрессия проблем безопасности из других продуктов**: Если это уместно, проверяются проблемы безопасности из связанных продуктов. Например, соответствующие варианты примерно 60 проблем безопасности для обозревателя Internet Explorer были идентифицированы и предпринимали попытку их [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)]применения к.  
  
- **Средства тестирования уязвимости на основе инструментов благодаря нечеткому тестированию файлов**: Нечеткие файлы — это использование входного диапазона модуля чтения файлов с помощью различных входных данных. Одним из примеров в [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)], где используется этот способ, является проверка неисправности в коде декодирования изображения.  
  
<a name="critical_code"></a>   
### <a name="critical-code-management"></a>Управление критическим кодом  
 Для [!INCLUDE[TLA#tla_xbap#plural](../../../includes/tlasharptla-xbapsharpplural-md.md)]создает песочницу безопасности, используя поддержку .NET Framework для маркировки и отслеживания критического для безопасности кода, который повышает привилегии (см. статью **методология критической безопасности** в стратегии безопасности WPF — платформа). [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] [ Безопасность](wpf-security-strategy-platform-security.md)). Учитывая требования к высокому качеству безопасности при защите важного кода, такой код получает дополнительный уровень управления источником и аудита безопасности. Приблизительно от 5 % до 10 % [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] состоит из кода, критического с точки зрения безопасности, который анализируется выделенной группой анализа. Исходный код и постановка кода на учет управляются путем отслеживания кода, критического с точки зрения безопасности, и сопоставления каждой критической сущности (например, метода, содержащего критический код) с ее утвержденным состоянием. Утвержденное состояние содержит имена одного или нескольких рецензентов. Каждая ежедневная сборка [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] сравнивает критически важный код с этим кодом в предыдущих сборках для проверки неутвержденных изменений. Если инженер изменяет критически важный код без получения утверждения от группы рецензирования, он немедленно обнаруживается и фиксируется. Этот процесс обеспечивает применение и обслуживание особенно высокого уровня безопасности через код песочницы [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)].  
  
## <a name="see-also"></a>См. также

- [Безопасность](security-wpf.md)
- [Безопасность частичного доверия в WPF](wpf-partial-trust-security.md)
- [Стратегия безопасности WPF — безопасность платформы](wpf-security-strategy-platform-security.md)
- [Надежные вычисления](https://www.microsoft.com/mscorp/twc/default.mspx)
- [Безопасность в .NET](../../standard/security/index.md)
