---
title: Общие сведения об элементе управления BindingNavigator (Windows Forms)
ms.date: 03/30/2017
f1_keywords:
- DataNavigator
helpviewer_keywords:
- BindingNavigator control [Windows Forms], about BindingNavigator control
- records [Windows Forms], navigating on a form
- data [Windows Forms], navigating
- data navigation
ms.assetid: 4423eede-f8d1-4d02-822f-5bf8432680d0
ms.openlocfilehash: ad63f622aae55cb4175eddc93ab5e086965a8fe8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/23/2019
ms.locfileid: "62011786"
---
# <a name="bindingnavigator-control-overview-windows-forms"></a>Общие сведения об элементе управления BindingNavigator (Windows Forms)
Элемент управления <xref:System.Windows.Forms.BindingNavigator> можно использовать для создания стандартных средств поиска и изменения данных в форме Windows Forms. Элемент управления <xref:System.Windows.Forms.BindingNavigator> часто используется с компонентом <xref:System.Windows.Forms.BindingSource>, позволяя пользователям переходить по записям данных в форме и взаимодействовать с ними.  
  
## <a name="how-the-bindingnavigator-works"></a>Как работает элемент управления BindingNavigator  

 Элемент управления <xref:System.Windows.Forms.BindingNavigator> состоит из элемента <xref:System.Windows.Forms.ToolStrip> с набором объектов <xref:System.Windows.Forms.ToolStripItem> для большинства обычных действий с данными: их добавления, удаления и перемещения по ним. По умолчанию элемент управления <xref:System.Windows.Forms.BindingNavigator> содержит эти стандартные кнопки. На следующем снимке экрана показан <xref:System.Windows.Forms.BindingNavigator> элемента управления в форме:
  
 ![Снимок экрана, показывающий элемент управления BindingNavigator.](./media/bindingnavigator-control-overview-windows-forms/bindingnavigator-control-form.gif)  
  
 В таблице ниже перечислены элементы управления и их функции.  
  
|Элемент управления|Функция|  
|-------------|--------------|  
|<xref:System.Windows.Forms.BindingNavigator.AddNewItem%2A> Кнопка|Вставляет новую строку в базовый источник данных.|  
|<xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> Кнопка|Удаляет текущую строку из базового источника данных.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> Кнопка|Переход к первому элементу базового источника данных.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveLastItem%2A> Кнопка|Переход к последнему элементу базового источника данных.|  
|<xref:System.Windows.Forms.BindingNavigator.MoveNextItem%2A> Кнопка|Переход к следующему элементу базового источника данных.|  
|<xref:System.Windows.Forms.BindingNavigator.MovePreviousItem%2A> Кнопка|Переход к предыдущему элементу базового источника данных.|  
|Текстовое поле <xref:System.Windows.Forms.BindingNavigator.PositionItem%2A>|Возвращает текущую позицию в базовом источнике данных.|  
|Текстовое поле <xref:System.Windows.Forms.BindingNavigator.CountItem%2A>|Возвращает общее число элементов в базовом источнике данных.|  
  
 Каждому элементу управления этой коллекции соответствует член компонента <xref:System.Windows.Forms.BindingSource>, обеспечивающий ту же функциональность программным путем. Например, кнопка <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> соответствует методу <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> компонента <xref:System.Windows.Forms.BindingSource>, кнопка <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> соответствует методу <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> и т. д.  
  
 Если кнопки по умолчанию не удовлетворяют требованиям приложения или необходимо использовать дополнительные кнопки с иной функциональностью, можно создать собственные кнопки <xref:System.Windows.Forms.ToolStrip>. Также см. раздел [Как Добавление загрузки, сохранения и кнопки "Отмена" для Windows Forms элемента управления BindingNavigator](load-save-and-cancel-bindingnavigator.md).  
  
## <a name="see-also"></a>См. также

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.BindingSource>
- [Элемент управления BindingNavigator](bindingnavigator-control-windows-forms.md)
