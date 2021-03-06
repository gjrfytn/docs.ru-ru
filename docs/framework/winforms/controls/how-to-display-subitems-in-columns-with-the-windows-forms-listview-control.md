---
title: Практическое руководство. Отображение дополнительных данных в столбцах элемента управления ListView в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- list items
- Details view
- ListView control [Windows Forms], adding ListSubItems
- subitems
ms.assetid: e465f044-cde7-4fd9-a687-788a73a0f554
ms.openlocfilehash: efee926301bc358bb7645ba67826f412c0d0dbbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-subitems-in-columns-with-the-windows-forms-listview-control"></a>Практическое руководство. Отображение дополнительных данных в столбцах элемента управления ListView в Windows Forms
Windows Forms <xref:System.Windows.Forms.ListView> элемент управления может отображать дополнительный текст или подэлементы, для каждого элемента в представлении Details. В первом столбце отображается текст элемента, например номер сотрудника. Второй, третий и последующих столбцах отображаются первый, второй и последующие связанные подэлементы.  
  
### <a name="to-add-subitems-to-a-list-item"></a>Чтобы добавить дополнительные элементы в элемент списка  
  
1.  Добавьте все необходимые столбцы. Так как в первом столбце будет отображаться элемент <xref:System.Windows.Forms.ListView.Text%2A> свойства, необходимо один столбец больше, чем количество дополнительных элементов. Дополнительные сведения о добавлении столбцов см. в разделе [как: Добавление столбцов в элемент управления Windows Forms ListView](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md).  
  
2.  Вызовите <xref:System.Windows.Forms.ListViewItem.ListViewSubItemCollection.Add%2A> метод в коллекцию, возвращаемую <xref:System.Windows.Forms.ListViewItem.SubItems%2A> свойство элемента. В примере кода задает имя сотрудника и отдел для элемента списка.  
  
     [!code-csharp[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/CS/Class1.cs#61)]
     [!code-vb[System.Windows.Forms.ListViewLegacyTopics#61](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListViewLegacyTopics/VB/Class1.vb#61)]  
  
## <a name="see-also"></a>См. также  
 [Общие сведения об элементе управления ListView](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Практическое руководство. Добавление и удаление элементов с помощью элемента управления ListView в Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-and-remove-items-with-the-windows-forms-listview-control.md)  
 [Практическое руководство. Добавление столбцов в элемент управления ListView в Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-columns-to-the-windows-forms-listview-control.md)  
 [Практическое руководство. Отображение значков в элементе управления ListView в Windows Forms](../../../../docs/framework/winforms/controls/how-to-display-icons-for-the-windows-forms-listview-control.md)  
 [Практическое руководство. Добавление пользовательских данных в элемент управления TreeView или ListView (Windows Forms)](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)
