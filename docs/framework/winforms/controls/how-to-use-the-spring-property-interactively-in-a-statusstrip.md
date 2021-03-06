---
title: Практическое руководство. Интерактивное использование свойства Spring в элементе управления StatusStrip
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
- status bars [Windows Forms], examples
- Spring property [Windows Forms]
ms.assetid: 18bde842-a93c-48dd-9db3-15738a1775ce
ms.openlocfilehash: e3818beb96a7c005ea02bc04e9ea740b28a54707
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-spring-property-interactively-in-a-statusstrip"></a>Практическое руководство. Интерактивное использование свойства Spring в элементе управления StatusStrip
Для размещения элемента управления <xref:System.Windows.Forms.ToolStripStatusLabel> в элементе <xref:System.Windows.Forms.StatusStrip> можно использовать свойство <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>. Свойство <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> определяет, заполняет ли элемент управления <xref:System.Windows.Forms.ToolStripStatusLabel> доступное пространство в элементе управления <xref:System.Windows.Forms.StatusStrip> автоматически.  
  
## <a name="example"></a>Пример  
 В примере кода ниже показано использование свойства <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> для размещения элемента управления <xref:System.Windows.Forms.ToolStripStatusLabel> в элементе <xref:System.Windows.Forms.StatusStrip>. Для переключения значения свойства <xref:System.Windows.Forms.ToolStripItem.Click> обработчик событий <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> выполняет исключающую операцию ИЛИ (XOR).  
  
 Чтобы использовать этот пример кода, скомпилируйте и запустите приложение и нажмите кнопку **Middle (Spring)** на <xref:System.Windows.Forms.StatusStrip> переключите значение <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A> свойства.  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#50)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#50](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#50)]  
  
## <a name="compiling-the-code"></a>Компиляция кода  
 Для этого примера требуются:  
  
-   ссылки на сборки System.Design, System.Drawing и System.Windows.Forms.  
  
 Сведения о построении этого примера из командной строки для visual Basic или Visual C# см. в разделе [построение из командной строки](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) или [построение с командной строки csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Можно также построить этот пример, в Visual Studio, вставив код в новый проект.  См. также [Практическое руководство. Компиляция и выполнение откомпилированного примера кода формы Windows Forms с помощью Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>См. также  
 <xref:System.Windows.Forms.ToolStripStatusLabel>  
 <xref:System.Windows.Forms.StatusStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripItem>  
 <xref:System.Windows.Forms.ToolStripMenuItem>  
 [Элемент управления ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)
