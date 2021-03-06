---
title: Общие сведения о компоненте FolderBrowserDialog (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- FolderBrowserDialog
helpviewer_keywords:
- FolderBrowserDialog component [Windows Forms], about FolderBrowserDialog
- directories [Windows Forms], enabling browsing in applications
- folders [Windows Forms], enabling browsing in applications
ms.assetid: 796b622c-3ba9-4356-93bb-e217fc52f2c7
ms.openlocfilehash: cd89980ccad7e6c73094c1fb462d93cee8094959
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2019
ms.locfileid: "65210399"
---
# <a name="folderbrowserdialog-component-overview-windows-forms"></a>Общие сведения о компоненте FolderBrowserDialog (Windows Forms)

Windows Forms <xref:System.Windows.Forms.FolderBrowserDialog> компонент — это модальное диалоговое окно, которое используется для просмотра и выбора папки. Новые папки можно также создать изнутри <xref:System.Windows.Forms.FolderBrowserDialog> компонента.

> [!NOTE]
> Чтобы выбрать файлы, а не папки, используйте [OpenFileDialog](openfiledialog-component-windows-forms.md) компонента.

<xref:System.Windows.Forms.FolderBrowserDialog> Компонент отображается во время выполнения с помощью <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> метод. Задать <xref:System.Windows.Forms.FolderBrowserDialog.RootFolder%2A> свойства, чтобы определить самую верхнюю папку и все вложенные папки, которые будут отображаться в представлении в виде дерева диалогового окна. После отображения диалоговое окно можно использовать <xref:System.Windows.Forms.FolderBrowserDialog.SelectedPath%2A> свойство, чтобы получить путь к папке, которая была выбрана.

При добавлении в форму, <xref:System.Windows.Forms.FolderBrowserDialog> компонент появится в области в нижней части конструктора Windows Forms в Visual Studio.

## <a name="see-also"></a>См. также

- <xref:System.Windows.Forms.FolderBrowserDialog>
- [Практическое руководство. Выберите папки с помощью компонента FolderBrowserDialog в Windows Forms](how-to-choose-folders-with-the-windows-forms-folderbrowserdialog-component.md)
- [Компонент FolderBrowserDialog](folderbrowserdialog-component-windows-forms.md)
