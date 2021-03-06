---
title: Практическое руководство. Отключение объектов ToolStripMenuItem с помощью конструктора
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], disabling in designer
- MenuStrip control [Windows Forms], disabling menu items in designer
- menu items [Windows Forms], disabling
- menus [Windows Forms], disabling items
ms.assetid: 985e311e-7d67-4205-b5a3-d045b68a4a03
ms.openlocfilehash: 3ce18d40910145a076cc7084e2fba8ee0229c21f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-disable-toolstripmenuitems-using-the-designer"></a>Практическое руководство. Отключение объектов ToolStripMenuItem с помощью конструктора
Можно ограничить или расширить набор команд, которые может выбрать пользователь, включение и отключение элементов меню в ответ на действия пользователя. Пункты меню включены по умолчанию, если они были созданы, но это можно изменить с помощью <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> свойство. Можно изменить значение этого свойства во время разработки в **свойства** окна или программным путем установки его в код. Дополнительные сведения см. в разделе [как: отключение объектов ToolStripMenuItem](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems.md).  
  
> [!NOTE]
>  Отображаемые диалоговые окна и команды меню могут отличаться от описанных в справке в зависимости от текущих параметров или выпуска. Чтобы изменить параметры, выберите в меню **Сервис** пункт **Импорт и экспорт параметров** . Дополнительные сведения см. в статье [Настройка параметров разработки в Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-disable-a-menu-item-at-design-time"></a>Чтобы отключить пункт меню во время разработки  
  
1.  Выберите элемент меню в форме, установите <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A> свойства `false`.  
  
    > [!TIP]
    >  Отключение элемента меню первой или верхнего уровня в меню отключает всех пунктов меню. Аналогичным образом отключение пункта меню, который имеет вложенное отключает элементов вложенного меню. Если все команды конкретного меню недоступны пользователю, он считается хорошим стилем программирования, как скрыть и отключить всего меню, это представляет чистой пользовательского интерфейса. Как следует скрыть и отключить меню, как скрытие не запрещает доступ к командам меню с помощью сочетаний клавиш. Задать <xref:System.Windows.Forms.ToolStripItem.Visible%2A> свойства элемента меню верхнего уровня для `false` скрыть меню целиком.  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Практическое руководство. Скрытие объектов ToolStripMenuItem](../../../../docs/framework/winforms/controls/how-to-hide-toolstripmenuitems.md)  
 [Общие сведения об элементе управления MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)
