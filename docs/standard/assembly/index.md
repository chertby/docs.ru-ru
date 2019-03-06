---
title: Сборки в .NET
ms.date: 07/10/2018
ms.assetid: 149f5ca5-5b34-4746-9542-1ae43b2d0256
---
# <a name="assemblies-in-net"></a>Сборки в .NET

Сборки представляют собой базовый элемент развертывания, управления версиями, повторного использования, назначения областей активации и прав доступа для приложения на основе платформы .NET. Сборки создаются в виде исполняемого файла (.exe) или файла библиотеки динамической компоновки (.dll) и являются составными частями приложений .NET. Они предоставляют сведения для среды CLR, которые нужны для распознавания реализаций типов. Сборку можно представить как коллекцию типов и ресурсов, которые предназначены для совместной работы и формируют логическую единицу функциональности.  
  
 В .NET Core и .NET Framework сборку можно создать из одного или нескольких файлов исходного кода. В .NET Framework сборки могут содержать один или несколько модулей. Благодаря этому в крупных проектах несколько разработчиков могут работать с отдельными файлами или модулями исходного кода, которые вместе образуют единую сборку. Дополнительные сведения см. в статье [Как выполнить создании многофайловой сборки](../../framework/app-domains/how-to-build-a-multifile-assembly.md).
  
 Сборки имеют следующие свойства.  
  
-   Сборки реализованы как файлы .exe или .dll.  
  
-   Для библиотек, предназначенных для .NET Framework, сборку можно совместно использовать в нескольких приложениях, поместив ее в [глобальный кэш сборок](../../framework/app-domains/gac.md). Сборки должны получить строгие имена, чтобы их можно было включить в глобальный кэш сборок. Подробнее см. в статье [Сборки со строгими именами](../../framework/app-domains/strong-named-assemblies.md).  
  
-   Сборки загружаются в память только в том случае, если они реально используются. Если сборка не используется, она не загружается. Благодаря этому свойству сборки могут быть эффективным средством для управления ресурсами в крупных проектах.  
  
-   Сведения о сборке можно получить программным путем с помощью отражения. Дополнительные сведения см. в статьях [Отражение (C#)](../../csharp/programming-guide/concepts/reflection.md) и [Отражение (Visual Basic)](../../visual-basic/programming-guide/concepts/reflection.md).   
  
-   Сборку можно загрузить только для ее проверки. Для этого вызовите метод <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A?displayProperty=nameWithType>.  
  
## <a name="assembly-manifest"></a>Манифест сборки  
 Каждая сборка содержит *манифест сборки*. Манифест сборки выполняет роль оглавления и содержит следующую информацию.  
  
-   Идентификатор сборки (ее имя и версию).  
  
-   Таблица с описанием всех файлов, входящих в сборку. Например, сюда относятся другие ваши сборки, от которых зависит файл с расширением .exe или .dll, а также растровые изображения или файлы сведений.  
  
-   *Список ссылок сборки*, то есть список всех внешних зависимостей — библиотек DLL или других файлов, созданных другими разработчиками, которые требуются для работы вашего приложения. Ссылки на сборки содержат ссылки на глобальные и частные объекты. Глобальные объекты доступны для всех других приложений. В .NET Core они связаны с определенной средой выполнения. В .NET Framework они расположены в глобальном кэше сборок. Пространство имен <xref:System.IO?displayProperty=nameWithType> служит примером сборки в глобальном кэше сборок. Закрытые объекты должны находиться в каталоге установки приложения или в одном из его подкаталогов.  
  
 Так как сборки содержат сведения о содержимом, версиях и зависимостях, работа связанных с ними приложений не зависит от значений в реестре Windows. Сборки снижают риск конфликта библиотек DLL, а также повышают надежность и простоту развертывания приложений. Во многих случаях для установки приложения на базе .NET достаточно просто скопировать его файлы на целевой компьютер. Дополнительные сведения см. в статье [Манифест сборки](../../framework/app-domains/assembly-manifest.md).  
  
## <a name="adding-a-reference-to-an-assembly"></a>Добавление ссылки на сборку  
 Чтобы использовать сборку, нужно добавить ссылку на нее. Затем с помощью [директивы using](../../csharp/language-reference/keywords/using-directive.md) для C# или [оператора Imports](../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) для Visual Basic можно выбрать пространство имен для элементов, которые вы хотите использовать. Когда вы добавите ссылку на сборку и импортируете ее, в вашем приложении станут доступны все предоставленные в сборке типы, свойства, методы и другие члены пространств имен, как если бы их код являлся частью файла с исходным кодом вашего приложения.  
 
> [!NOTE]
> Ссылки на большинство сборок из библиотеки классов .NET создаются автоматически. Но в некоторых случаях ссылки на системные сборки не создаются автоматически. В .NET Core можно добавить ссылку на пакет NuGet, который содержит сборку, используя диспетчер пакетов NuGet в Visual Studio или добавив элемент [<PackageReference>](../../core/tools/dependencies.md#the-new-packagereference-element) для сборки в файл проекта с расширением *.csproj или *.vbproj. В .NET Framework можно добавить ссылку на сборку с помощью диалогового окна **Добавить ссылку** в Visual Studio или параметра командной строки `-reference` для компиляторов [C#](../../csharp/language-reference/compiler-options/reference-compiler-option.md) или [Visual Basic](../../visual-basic/reference/command-line-compiler/reference.md).
 
 На C# вы также можете использовать две версии одной и той же сборки в одном приложении. Дополнительные сведения см. в разделе [Псевдоним extern](../../csharp/language-reference/keywords/extern-alias.md).  
  
## <a name="creating-an-assembly"></a>Создание сборки  
 Скомпилируйте приложение. Для этого выполните компиляцию в Visual Studio, из командной строки с помощью средств интерфейса командной строки .NET Core или скомпилируйте сборки .NET Framework с помощью компилятора командной строки. Дополнительные сведения о компиляции сборок с помощью средств интерфейса командной строки .NET см. в [этой статье](../../core/tools/index.md). Дополнительные сведения о компиляции сборок с помощью компиляторов командной строки см. в статьях [Построение из командной строки с помощью csc.exe](../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md) для C# и [Построение из командной строки](../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) для Visual Basic.  
  
> [!NOTE]
>  Чтобы создать сборку в Visual Studio, выберите пункт **Сборка** из меню **Сборка**.  

## <a name="see-also"></a>См. также

 - [Формат файла сборки .NET](file-format.md)
 - [Сборки в среде CLR](../../framework/app-domains/assemblies-in-the-common-language-runtime.md)  
 - [Дружественные сборки](friend-assemblies.md)  
 - [Практическое руководство. Загрузка и выгрузка сборок (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)  
 - [Практическое руководство. Загрузка и выгрузка сборок (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-load-and-unload-assemblies.md)  
 - [Практическое руководство. Использование и отладка сборок с возможностью выгрузки в .NET Core](unloadability-howto.md)
 - [Практическое руководство. Определение того, является ли файл сборкой (C#)](../../csharp/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md)  
 - [Практическое руководство. Determine If a File Is an Assembly (Visual Basic)](../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-determine-if-a-file-is-an-assembly.md) (Практическое руководство. Как определить, является ли файл сборкой (Visual Basic))  