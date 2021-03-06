---
title: Практическое руководство. Создание таблицы подстановки для элемента управления ComboBox, ListBox или CheckedListBox в Windows Forms
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- CheckedListBox control [Windows Forms], creating lookup tables
- lookup tables
- list boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], lookup tables
- ComboBox control [Windows Forms], lookup table
- lookup tables [Windows Forms], creating for controls
- combo boxes [Windows Forms], lookup tables
- ListBox control [Windows Forms], creating lookup tables
ms.assetid: 4ce35f12-1f4e-4317-92d1-af8686a8cfaa
ms.openlocfilehash: 212cc229d8a496be11c84e30dbf3a0eedb952006
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-lookup-table-for-a-windows-forms-combobox-listbox-or-checkedlistbox-control"></a>Практическое руководство. Создание таблицы подстановки для элемента управления ComboBox, ListBox или CheckedListBox в Windows Forms
Иногда полезно отображать данные в удобном для пользователя формате в форме Windows Forms и при этом сохранять их в формате, требуемом в используемой программе. Например, в бланке заказа продуктов питания могут отображаться элементы меню с названиями продуктов в списке. Однако таблица данных регистрации заказа будет содержать уникальные идентификаторы, представляющие продукты питания. В таблице ниже представлен пример хранения и отображения данных бланка заказа продуктов питания.  
  
### <a name="orderdetailstable"></a>OrderDetailsTable  
  
|OrderID|Код элемента|Количество|  
|-------------|------------|--------------|  
|4085|12|1|  
|4086|13|3|  
  
### <a name="itemtable"></a>ItemTable  
  
|ID|name|  
|--------|----------|  
|12|Картофель|  
|13|Цыпленок|  
  
 В этом сценарии одна таблица **OrderDetailsTable**, содержит фактические сведения, которые вас интересуют отображения и сохранения. Однако с целью экономии места они представлены в неудобном для восприятия виде. Другая таблица, **ItemTable**, содержит только связанные информацию о какой идентификатор номер эквивалентные какие название продукта и ничего о заказах на фактическое пищевых продуктов.  
  
 **ItemTable** подключен к <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox>, или <xref:System.Windows.Forms.CheckedListBox> управление с помощью трех свойств. `DataSource` Свойство содержит имя этой таблицы. `DisplayMember` Свойство содержит столбец данных таблицы, который будет отображаться в элементе управления (название продукта). `ValueMember` Свойство содержит столбец данных таблицы с сохраняемыми данными (идентификатор).  
  
 **OrderDetailsTable** подключен к элементу управления с помощью коллекции привязок, доступных через <xref:System.Windows.Forms.Control.DataBindings%2A> свойство. При добавлении объекта привязки в коллекцию свойство элемента управления подключиться к члену данных (столбцом кодов) в источнике данных ( **OrderDetailsTable**). Когда в элементе управления делается выбор, в этой таблице сохраняются вводимые данные.  
  
### <a name="to-create-a-lookup-table"></a>Создание таблицы подстановок  
  
1.  Добавьте на форму элемент управления <xref:System.Windows.Forms.ComboBox>, <xref:System.Windows.Forms.ListBox> или <xref:System.Windows.Forms.CheckedListBox>.  
  
2.  Произведите подключение к источнику данных.  
  
3.  Установите связь между данными в двух таблицах. В разделе [Знакомство с объектами DataRelation](http://msdn.microsoft.com/library/89d8a881-8265-41f2-a88b-61311ab06192).  
  
4.  Задайте перечисленные ниже свойства. Их можно задать в коде или в конструкторе.  
  
    |Свойство.|Параметр|  
    |--------------|-------------|  
    |<xref:System.Windows.Forms.ListControl.DataSource%2A>|Таблица, в которой содержатся сведения о том, какому коду соответствует тот или иной элемент. В приведенном выше сценарии это `ItemTable`.|  
    |<xref:System.Windows.Forms.ListControl.DisplayMember%2A>|Столбец таблицы источника данных, который необходимо отобразить в элементе управления. В приведенном выше сценарии это `"Name"` (для задания в коде используйте кавычки).|  
    |<xref:System.Windows.Forms.ListControl.ValueMember%2A>|Столбец таблицы источника данных, который содержит сохраняемую информацию. В приведенном выше сценарии это `"ID"` (для задания в коде используйте кавычки).|  
  
5.  В процедуре вызовите метод <xref:System.Windows.Forms.ControlBindingsCollection.Add%2A> класса <xref:System.Windows.Forms.ControlBindingsCollection> для привязки свойства <xref:System.Windows.Forms.ListControl.SelectedValue%2A> элемента управления к таблице, в которой регистрируются данные, вводимые в форме. Также это можно сделать в конструкторе, а не в коде, обратившись к элемента управления <xref:System.Windows.Forms.Control.DataBindings%2A> свойство в **свойства** окна. В приведенном выше сценарии это `OrderDetailsTable`, а столбец — `"ItemID"`.  
  
    ```vb  
    ListBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID")  
    ```  
  
    ```csharp  
    listBox1.DataBindings.Add("SelectedValue", OrderDetailsTable, "ItemID");  
    ```  
  
## <a name="see-also"></a>См. также  
 [Привязка данных и Windows Forms](../../../../docs/framework/winforms/data-binding-and-windows-forms.md)  
 [Общие сведения об элементе управления ListBox](../../../../docs/framework/winforms/controls/listbox-control-overview-windows-forms.md)  
 [Общие сведения об элементе управления ComboBox](../../../../docs/framework/winforms/controls/combobox-control-overview-windows-forms.md)  
 [Общие сведения об элементе управления CheckedListBox](../../../../docs/framework/winforms/controls/checkedlistbox-control-overview-windows-forms.md)  
 [Создание списка для выбора элементов в Windows Forms](../../../../docs/framework/winforms/controls/windows-forms-controls-used-to-list-options.md)
