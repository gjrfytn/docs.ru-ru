---
title: "Установка режимов заполнения для столбцов элемента управления DataGridView в Windows Forms | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-winforms"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "jsharp"
helpviewer_keywords: 
  - "таблицы данных, автоматическое изменение размера столбцов"
  - "таблицы данных, режим заполнения столбцов"
  - "DataGridView - элемент управления [Windows Forms], режим заполнения столбцов"
ms.assetid: b4ef7411-ebf4-4e26-bb33-aecec90de80c
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# Установка режимов заполнения для столбцов элемента управления DataGridView в Windows Forms
В режиме заполнения столбцов элемент управления <xref:System.Windows.Forms.DataGridView> автоматически изменяет размер своих столбцов, чтобы они полностью заполняли доступную область отображения по ширине.  Элемент управления не отображает горизонтальную полосу прокрутки, за исключением случаев, когда необходимо сохранить ширину каждого столбца равной или большей, чем значение его свойства <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>.  
  
 Поведение каждого столбца при изменении размера зависит от его свойства <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A>.  Значение этого свойства наследуется от свойства <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> или свойства элемента управления <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A>, если значение столбца равно <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> \(значение по умолчанию\).  
  
 Каждый столбец может иметь свой режим определения размера, но все столбцы с режимом определения размера <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode> будут совместно использовать ту ширину области отображения, которая не занята другими столбцами.  Эта ширина распределяется между столбцами с заполнением пропорционально значениям их свойств <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>.  Например, если два столбца имеют значения <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, равные 100 и 200, то первый столбец будет иметь половину от ширины второго столбца.  
  
## Изменение размера пользователем в режиме заполнения  
 В отличие от режимов определения размера на основе содержимого ячейки, режим заполнения запрещает пользователям изменение размеров столбцов, имеющих значения свойства<xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A>, равные `true`.  При изменении пользователем размера столбца в режиме заполнения все столбцы с заполнением после столбца с измененным размером \(справа от него, если <xref:System.Windows.Forms.Control.RightToLeft%2A> равно `false`, в противном случае — слева\) также меняются, чтобы компенсировать изменение на доступную ширину.  Если после столбца с измененным размером нет столбцов с заполнением, то размеры всех остальных столбцов с заполнением в элементе управления изменяются для компенсации.  Если в элементе управления нет других столбцов с заполнением, то изменение размера игнорируется.  Если изменяется размер столбца, который не находится в режиме заполнения, то размеры всех столбцов с заполнением в элементе управления изменяются для компенсации.  
  
 После изменения размера столбца с заполнением значения <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> для всех измененных столбцов будут пропорционально скорректированы.  Например, если четыре столбца с заполнением имеют значения <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, равные 100, то уменьшение ширины второго столбца в два раза приведет к изменению значений <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> в 100, 50, 125 и 125.  Изменение размера столбца без заполнения не приведет к изменению значения <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, поскольку столбцы с заполнением просто компенсируют изменения, чтобы сохранить соотношения.  
  
## Коррекция на основе содержимого FillWeight  
 Для столбцов с заполнением можно инициализировать значения <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, используя методы автоматического изменения размера <xref:System.Windows.Forms.DataGridView>, такие как метод <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A>.  Этот метод сначала вычисляет ширину столбцов, необходимую для отображения их содержимого.  Затем элемент управления корректирует значения <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> для всех столбцов с заполнением, чтобы их соотношение соответствовало соотношению рассчитанных значений ширины.  И наконец, элемент управления изменяет размеры столбцов с заполнением с использованием нового соотношения <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, таким образом, чтобы все столбцы в элементе управления заполняли доступное пространство по горизонтали.  
  
## Пример  
  
### Описание  
 Поведение размеров столбцов для различных сценариев можно настроить, используя соответствующие значения для свойств <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> и <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A>.  
  
 В следующем примере кода можно поэкспериментировать с различными значениями для свойств <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A> и <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> различных столбцов.  В этом примере элемент управления <xref:System.Windows.Forms.DataGridView> привязан к собственной коллекции <xref:System.Windows.Forms.DataGridView.Columns%2A>, а один столбец связан с каждым из свойств <xref:System.Windows.Forms.DataGridViewColumn.HeaderText%2A>, <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A>, <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>, <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> и <xref:System.Windows.Forms.DataGridViewColumn.Width%2A>.  Каждый из столбцов также представлен строкой в элементе управления, и изменение значений в строке приведет к обновлению свойства соответствующего столбца, чтобы можно было увидеть взаимодействие значений.  
  
### Код  
 [!code-csharp[System.Windows.Forms.DataGridViewFillColumnsDemo#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/CS/fillcolumns.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewFillColumnsDemo#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewFillColumnsDemo/vb/fillcolumns.vb#00)]  
  
### Комментарии  
 Использование этого демонстрационного приложения.  
  
-   Измените размер формы.  Обратите внимание, как изменяется ширина столбцов и одновременно сохраняются пропорции, указанные значениями свойства <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>.  
  
-   Измените размеры столбцов, перетаскивая разделители столбцов с помощью мыши.  Обратите внимание, как изменяются значения <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A>.  
  
-   Измените значение <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> для одного столбца, а затем перетащите для изменения размеров формы.  Обратите внимание, что при достаточном уменьшении размера формы, значения <xref:System.Windows.Forms.DataGridViewColumn.Width%2A> не становятся меньше значений <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A>.  
  
-   Измените значения <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A> для всех столбцов на большие числа, чтобы суммарное значение было больше ширины элемента управления.  Обратите внимание, как появляется горизонтальная полоса прокрутки.  
  
-   Измените значения <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A> для некоторых столбцов.  Наблюдайте результат при изменении размера столбцов или формы.  
  
## Компиляция кода  
 Для этого примера требуются:  
  
-   ссылки на сборки System, System.Drawing и System.Windows.Forms.  
  
 Информацию о выполнении сборки этого примера из командной строки для [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] или [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)] можно найти в разделе [Построение из командной строки](../Topic/Building%20from%20the%20Command%20Line%20\(Visual%20Basic\).md) или [Построение из командной строки с помощью csc.exe](../../../../ocs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).  Вы можете выполнить сборку этого примера в [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)], вставив код в новый проект.  См. также [Практическое руководство. Компиляция и выполнение скомпилированного примера кода Windows Forms с помощью Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## См. также  
 <xref:System.Windows.Forms.DataGridView>   
 <xref:System.Windows.Forms.DataGridView.AutoResizeColumns%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridView.AutoSizeColumnsMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnsMode>   
 <xref:System.Windows.Forms.DataGridViewColumn>   
 <xref:System.Windows.Forms.DataGridViewColumn.InheritedAutoSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.AutoSizeMode%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewAutoSizeColumnMode>   
 <xref:System.Windows.Forms.DataGridViewColumn.FillWeight%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.MinimumWidth%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.Width%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.DataGridViewColumn.Resizable%2A?displayProperty=fullName>   
 <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName>   
 [Изменение размера столбцов и строк элемента управления DataGridView в Windows Forms](../../../../docs/framework/winforms/controls/resizing-columns-and-rows-in-the-windows-forms-datagridview-control.md)