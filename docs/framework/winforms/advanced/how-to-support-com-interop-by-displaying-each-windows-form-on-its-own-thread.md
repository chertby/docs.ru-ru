---
title: Практическое руководство. Поддержка COM-взаимодействия путем отображения каждой формы Windows Forms в отдельном потоке
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: f158cf71f69ed3221dcaf7d3abbe495cf818638b
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593189"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>Практическое руководство. Поддержка COM-взаимодействия путем отображения каждой формы Windows Forms в отдельном потоке
Проблемы COM-взаимодействия можно устранить путем отображения формы в цикл обработки сообщений .NET Framework, которую можно создать с помощью <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> метод.  
  
 Чтобы исправить работу формы Windows Forms из клиентского приложения COM, необходимо запустить форму в цикле обработки сообщений Windows Forms. Для этого воспользуйтесь одним из перечисленных ниже подходов.  
  
- Используйте метод <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> для отображения Windows Form. Дополнительные сведения см. в разделе [Практическое руководство. Поддержка COM-взаимодействия путем отображения формы Windows Forms с помощью метода ShowDialog](com-interop-by-displaying-a-windows-form-shadow.md).  
  
- Отображайте каждую форму Windows Forms в отдельном потоке.  
  
 Имеется широкая поддержка этой возможности в Visual Studio.  
  
 Также см. в разделе [Пошаговое руководство: Поддержка COM-взаимодействия путем отображения каждой формы Windows Forms в отдельном потоке](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100)).  
  
## <a name="example"></a>Пример  
 В следующем примере кода демонстрируется отображение формы в отдельном потоке и вызов метода <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> для запуска загрузки сообщений Windows Forms в этом потоке. Чтобы использовать этот подход, необходимо выполнять маршалинг всех обращений к форме из приложения неуправляемого кода с помощью метода <xref:System.Windows.Forms.Control.Invoke%2A> .  
  
 Этот подход требует, что каждый экземпляр формы выполнялся в своем собственном потоке с использованием собственного цикла обработки сообщений. В каждом потоке не может быть более одного цикла обработки сообщений. Таким образом, изменить цикл обработки сообщений клиентского приложения нельзя. Тем не менее можно изменить компонент .NET Framework для запуска нового потока, использующего собственный цикл обработки сообщений.  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
  
- Скомпилируйте типы `COMForm`, `Form1`и `FormManager` в сборку и назовите ее `COMWinform.dll`. Зарегистрируйте сборку для COM-взаимодействия с помощью одного из методов, описанных в разделе [Packaging an Assembly for COM](../../interop/packaging-an-assembly-for-com.md). Теперь можно использовать сборку и соответствующий ей файл библиотеки типов (с расширением TLB) в неуправляемых приложениях. Например, можно использовать библиотеку типов как ссылку в проекте исполняемого файла Visual Basic 6.0.  
  
## <a name="see-also"></a>См. также

- [Предоставление компонентов .NET Framework клиентам COM](../../interop/exposing-dotnet-components-to-com.md)
- [Упаковка сборки для модели COM](../../interop/packaging-an-assembly-for-com.md)
- [Регистрация сборок в COM](../../interop/registering-assemblies-with-com.md)
- [Практическое руководство. Поддержка COM-взаимодействия путем отображения формы Windows Forms с помощью метода ShowDialog](com-interop-by-displaying-a-windows-form-shadow.md)
- [Общие сведения о Windows Forms и неуправляемых приложениях](windows-forms-and-unmanaged-applications-overview.md)
