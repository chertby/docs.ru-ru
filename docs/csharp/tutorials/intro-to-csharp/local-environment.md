---
title: Знакомство со средствами разработки. Вводное руководство по C#
description: Эта статья содержит базовое описание средств разработки, которые вы будете использовать для создания приложений C# и .NET на локальном компьютере.
ms.date: 10/23/2018
ms.openlocfilehash: db0b3228272a17feaa11ec754fa0aa4952a0d1ee
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/18/2019
ms.locfileid: "58920666"
---
# <a name="become-familiar-with-the-net-development-tools"></a>Знакомство со средствами разработки для .NET

Для выполнения этого руководства прежде всего нужно настроить на компьютере среду разработки.
В руководстве по [началу работы с .NET за 10 минут](https://www.microsoft.com/net/core) содержатся инструкции по настройке локальной среды разработки на компьютерах Mac, Windows или Linux.

Кроме того, вы можете установить [пакет SDK для .NET Core](https://www.microsoft.com/net/download) и [Visual Studio Code](https://code.visualstudio.com/).

## <a name="basic-application-development-flow"></a>Базовый поток разработки приложения

Чтобы создать приложения, выполните команду [`dotnet new`](../../../core/tools/dotnet-new.md). Эта команда создает файлы и ресурсы, необходимые для приложения. Во всех ознакомительных руководствах по C# используется тип приложения `console`. Освоив описанные здесь основы, вы сможете перейти и к другим типам приложений.

Выполните команду [`dotnet build`](../../../core/tools/dotnet-build.md), чтобы создать исполняемый файл. Затем запустите исполняемый файла с помощью команды [`dotnet run`](../../../core/tools/dotnet-run.md).

## <a name="pick-your-tutorial"></a>Выбор руководства

Вы можете начать изучение с любого из следующих руководств:

## <a name="numbers-in-cnumbers-in-csharp-localmd"></a>[Числа в C#](numbers-in-csharp-local.md)

Из руководства [Числа в C#](numbers-in-csharp-local.md) вы узнаете, как на компьютере хранятся числа и как выполнять вычисления с разными числовыми типами. Вы ознакомитесь с основами округления и научитесь выполнять математические вычисления с помощью C#.

В этом руководстве предполагается, что вы уже прошли занятие [Hello World](hello-world.yml).

## <a name="branches-and-loopsbranches-and-loops-localmd"></a>[Ветви и циклы](branches-and-loops-local.md)

В руководстве [Ветви и циклы](branches-and-loops-local.md) представлены общие принципы организации ветвления кода в зависимости от значений, хранящихся в переменных. Вы узнаете, что такое поток управления, являющийся основой принятия решений и выбора различных действий в программах.

В этом руководстве предполагается, что вы уже прошли занятия [Hello World](hello-world.yml) и [Числа в C#](numbers-in-csharp-local.md).

## <a name="list-collectionarrays-and-collectionsmd"></a>[Коллекция списков](arrays-and-collections.md)

Занятие [Коллекция списков](arrays-and-collections.md) содержит обзор типа "Коллекция списков", в котором хранятся последовательности данных. Вы узнаете, как добавлять и удалять элементы, выполнять их поиск и сортировать списки. Вы ознакомитесь с различными типами списков. 

В этом руководстве предполагается, что вы уже прошли перечисленные выше занятия.

## <a name="introduction-to-classesintroduction-to-classesmd"></a>[Общие сведения о классах](introduction-to-classes.md)

Это заключительное ознакомительное руководство по C# можно изучить только на локальном компьютере, используя настроенную среду разработки и .NET Core.
Вы создадите консольное приложение и изучите основные объектно-ориентированные функции языка C#.
