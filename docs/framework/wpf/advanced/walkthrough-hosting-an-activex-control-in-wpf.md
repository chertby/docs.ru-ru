---
title: Пошаговое руководство. Размещение элемента управления ActiveX в приложении WPF
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ActiveX controls [WPF interoperability]
- hosting ActiveX controls [WPF]
ms.assetid: 1931d292-0dd1-434f-963c-dcda7638d75a
ms.openlocfilehash: 0181093de1c40889110ab7eae75a3847a17845a9
ms.sourcegitcommit: 83ecdf731dc1920bca31f017b1556c917aafd7a0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 07/12/2019
ms.locfileid: "67859941"
---
# <a name="walkthrough-hosting-an-activex-control-in-wpf"></a>Пошаговое руководство. Размещение элемента управления ActiveX в приложении WPF
Для улучшенного взаимодействия с браузерами, можно использовать элементы управления ActiveX в вашей [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-приложения на основе. В этом пошаговом руководстве показано, как разместить [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] как элемент управления на [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] страницы.

 В данном пошаговом руководстве представлены следующие задачи.

- Создание проекта.

- Создание элемента управления ActiveX.

- Размещение элемента управления ActiveX на странице WPF.

 После завершения этого пошагового руководства вы узнаете, как использовать элементы управления ActiveX в вашей [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-приложения на основе.

## <a name="prerequisites"></a>Предварительные требования
 Ниже приведены компоненты, необходимые для выполнения данного пошагового руководства.

- [!INCLUDE[TLA#tla_wmp](../../../../includes/tlasharptla-wmp-md.md)] установлена на компьютере, где установлена среда Visual Studio.

- Visual Studio 2010.

## <a name="creating-the-project"></a>Создание проекта

### <a name="to-create-and-set-up-the-project"></a>Создание и настройка проекта

1. Создание проекта приложения WPF с именем `HostingAxInWpf`.

2. Добавить в решение проекта библиотеки элементов управления Windows Forms и назовите проект `WmpAxLib`.

3. В проекте WmpAxLib добавьте ссылку на сборку проигрывателя Windows Media, которая называется wmp.dll.

4. Откройте **элементов**.

5. Щелкните правой кнопкой мыши в **элементов**, а затем нажмите кнопку **Выбор элементов**.

6. Нажмите кнопку **COM-компоненты** выберите **проигрывателя Windows Media** управления, а затем нажмите кнопку **ОК**.

     Добавляемый элемент управления проигрывателя Windows Media **элементов**.

7. В обозревателе решений щелкните правой кнопкой мыши **UserControl1** файла и нажмите кнопку **Переименовать**.

8. Измените имя на `WmpAxControl.vb` или `WmpAxControl.cs`в зависимости от языка.

9. Если в ответ на приглашение переименовать все ссылки, нажмите кнопку **Да**.

## <a name="creating-the-activex-control"></a>Создание элемента управления ActiveX
 [!INCLUDE[TLA#tla_visualstu](../../../../includes/tlasharptla-visualstu-md.md)] автоматически создает <xref:System.Windows.Forms.AxHost> класс-оболочку для элемента управления Microsoft ActiveX, когда элемент управления добавляется в рабочую область конструирования. В следующей процедуре создается управляемая сборка с именем AxInterop.WMPLib.dll.

### <a name="to-create-the-activex-control"></a>Чтобы создать элемент управления ActiveX

1. Откройте WmpAxControl.vb или WmpAxControl.cs в конструкторе Windows Forms.

2. Из **элементов**, добавьте элемент управления проигрывателя Windows Media в область конструктора.

3. В окне свойств установите для параметра элемента управления проигрывателя Windows Media <xref:System.Windows.Forms.Control.Dock%2A> свойства <xref:System.Windows.Forms.DockStyle.Fill>.

4. Создание проекта библиотеки элементов управления WmpAxLib.

## <a name="hosting-the-activex-control-on-a-wpf-page"></a>Размещение элемента управления ActiveX в страницу WPF

### <a name="to-host-the-activex-control"></a>Размещение элемента управления ActiveX

1. В проекте HostingAxInWpf добавьте ссылку на созданную сборку взаимодействия ActiveX.

     Эта сборка называется AxInterop.WMPLib.dll и был добавлен в папку отладки проекта WmpAxLib при импорте элементом управления проигрывателя Windows Media.

2. Добавьте ссылку на сборку WindowsFormsIntegration с именем WindowsFormsIntegration.dll.

3. Добавьте ссылку на [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] сборку, которая называется System.Windows.Forms.dll.

4. Откройте файл MainWindow.xaml в конструкторе WPF.

5. Имя <xref:System.Windows.Controls.Grid> элемент `grid1`.

     [!code-xaml[HostingAxInWpf#1](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml#1)]

6. В представлении конструирования или XAML, выберите <xref:System.Windows.Window> элемент.

7. В окне «Свойства» щелкните **события** вкладки.

8. Дважды щелкните <xref:System.Windows.FrameworkElement.Loaded> событий.

9. Вставьте следующий код для обработки <xref:System.Windows.FrameworkElement.Loaded> событий.

     Этот код создает экземпляр класса <xref:System.Windows.Forms.Integration.WindowsFormsHost> управления и добавляет экземпляр `AxWindowsMediaPlayer` элемента управления в качестве дочернего.

     [!code-csharp[HostingAxInWpf#11](~/samples/snippets/csharp/VS_Snippets_Wpf/HostingAxInWpf/CSharp/HostingAxInWpf/window1.xaml.cs#11)]
     [!code-vb[HostingAxInWpf#11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HostingAxInWpf/VisualBasic/HostingAxInWpf/window1.xaml.vb#11)]  
  
10. Нажмите клавишу F5, чтобы выполнить сборку приложения и запустить его.  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Проектирование XAML в Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)
- [Пошаговое руководство: Размещение Windows Forms составного элемента управления в WPF](walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Пошаговое руководство: Размещение составного элемента управления WPF в Windows Forms](walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
