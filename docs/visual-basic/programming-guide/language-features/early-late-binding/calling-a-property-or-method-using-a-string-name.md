---
title: "Вызов свойства или метода с помощью строкового имени (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "CallByName - функция"
  - "вызов методов, имена строк"
  - "вызовы метода, строки"
  - "методы [Visual Basic], вызов при помощи имен строк"
  - "объекты [Visual Basic], задание свойств"
  - "передача операторам"
  - "свойства [Visual Basic], установка во время выполнения"
  - "задание свойств, свойства объекта во время выполнения"
  - "строки [Visual Basic], передача новых операторов как"
ms.assetid: 79a7b8b4-b8c7-4ad8-aca8-12a9a2b32f03
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# Вызов свойства или метода с помощью строкового имени (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

В большинстве случаев во время разработки имеется доступ к свойствам и методам объекта и можно писать код для их обработки.  Однако в некоторых случаях свойства и методы объекта заранее не известны, или конечному пользователю необходима гибкость для указания свойств или методов во время выполнения.  
  
## Функция CallByName  
 Рассмотрим, например, клиентское приложение, вычисляющее выражения, введенные пользователем с помощью передачи оператора COM\-компоненту.  Предположим, что в компонент постоянно добавляются новые функции, которым необходимы новые операторы.  При использовании стандартных методов доступа к объекту может возникнуть необходимость повторной компиляции и переустановки клиентского приложения прежде чем можно будет использовать.  Чтобы этого избежать, используется функция `CallByName` для передачи новых операторов в виде строк без изменения приложения.  
  
 Функция `CallByName` позволяет использовать строку для указания свойства или метода во время выполнения.  Сигнатура функции `CallByName` выглядит следующим образом:  
  
 *Результат* \= `CallByName`\(*Объект*, *Имя процедуры*, *Тип вызова*, *Аргументы*\(\)\)  
  
 Первый аргумент, *Объект*, принимает имя объекта, над которым совершаются действия.  Аргумент *Имя процедуры* принимает строку, содержащую имя метода или свойства вызываемой процедуры.  Аргумент *CallType* принимает константу, являющейся типом вызываемой процедуры: метода \(`Microsoft.VisualBasic.CallType.Method`\), считанного свойства \(`Microsoft.VisualBasic.CallType.Get`\) или заданного свойства \(`Microsoft.VisualBasic.CallType.Set`\).  Необязательный аргумент *Аргументы* содержит массив типа `Object`, содержащий любые аргументы для процедуры.  
  
 `CallByName` можно использовать с классами используемого решения, но наиболее часто она используется для получения доступа к COM\-объектам или объектам из [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)] сборок.  
  
 Предположим, что была добавлена ссылка на сборку, содержащую класс с именем `MathClass`, который имеет новую функцию с именем `SquareRoot`, как показано в следующем коде:  
  
 [!code-vb[VbVbalrOOP#53](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_1.vb)]  
  
 В приложении могут использоваться элементы управления текстовыми полями для управления вызываемыми методами и их аргументами.  Например, если `TextBox1` содержит выражение для вычисления, и `TextBox2` используется для ввода имени функции, можно использовать следующий код для вызова функции `SquareRoot` для выражения в `TextBox1`:  
  
 [!code-vb[VbVbalrOOP#54](../../../../visual-basic/misc/codesnippet/VisualBasic/calling-a-property-or-method-using-a-string-name_2.vb)]  
  
 Если ввести "64" в `TextBox1`, "SquareRoot" в `TextBox2` и затем вызвать процедуру `CallMath`, то будет вычислен квадратный корень из числа в `TextBox1`.  Код в примере вызывает функцию `SquareRoot` \(которая принимает в качестве необходимого аргумента строку, содержащую выражение для оценки\) и возвращает "8" в элементе `TextBox1` \(квадратный корень из 64\).  Конечно, если пользователь вводит в элемент `TextBox2` недопустимую строку, если строка содержит имя свойства вместо метода или если методу требовался дополнительный аргумент, то возникает ошибка во время выполнения.  Необходимо добавить надлежащий код обработки ошибки, если используется `CallByName`, чтобы реагировать на эти или другие ошибки.  
  
> [!NOTE]
>  Хотя функция `CallByName` может быть полезна в некоторых случаях, необходимо учитывать ее влияние на производительность — использование `CallByName` для вызова процедуры немного медленнее, чем вызов с поздним связыванием.  При повторяющихся вызовах функции, например в цикле, `CallByName` может существенно повлиять на производительность.  
  
## См. также  
 <xref:Microsoft.VisualBasic.Interaction.CallByName%2A>   
 [Определение типа объекта](../../../../visual-basic/programming-guide/language-features/early-late-binding/determining-object-type.md)