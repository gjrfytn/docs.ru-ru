---
title: "Лучшие методики обработки исключений | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "исключения, рекомендации"
ms.assetid: f06da765-235b-427a-bfb6-47cd219af539
caps.latest.revision: 28
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 28
---
# Лучшие методики обработки исключений
Хорошо спроектированное приложение обрабатывает исключения и ошибки, чтобы предотвратить сбои приложения.  В этом разделе описываются рекомендации по обработке и созданию исключений.  
  
## Обработка исключений  
 В следующем списке приведены некоторые общие рекомендации по обработке исключений в приложении.  
  
-   Используйте код обработки исключений \(блоки `try`\/`catch`\) надлежащим образом.  Можно также программным путем проверять условие, которое с большой вероятностью может возникать без обработки исключений.  
  
     **Программные проверки**.  В следующем примере показано использование оператора `if` для проверки закрытия подключения.  Если подключение не закрыто, пример закрывает подключение вместо выдачи исключения.  
  
     [!code-cpp[Conceptual.Exception.Handling#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#2)]
     [!code-csharp[Conceptual.Exception.Handling#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#2)]
     [!code-vb[Conceptual.Exception.Handling#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#2)]  
  
     **Обработка исключений**.  В следующем примере используется блок `try`\/`catch`, который проверяет подключение и вызывает исключение, если подключение не закрыто.  
  
     [!code-cpp[Conceptual.Exception.Handling#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#3)]
     [!code-csharp[Conceptual.Exception.Handling#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#3)]
     [!code-vb[Conceptual.Exception.Handling#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#3)]  
  
     Выбираемый метод зависит от того, насколько часто ожидается возникновение данного события.  
  
    -   Используйте обработку исключений, если событие не происходит очень часто, то есть если событие носит действительно исключительный характер и указывает на ошибку \(например, в случае неожиданного конца файла\).  При использовании обработки исключений в обычных условиях выполняется меньше кода.  
  
    -   Если событие происходит регулярно в рамках нормальной работы программы, используйте программный метод проверки на наличие ошибок.  В случае программной проверки на наличие ошибок при возникновении исключения выполняется больше кода.  
  
-   Используйте блоки `try`\/`catch` выделив с их помощью тот код, который потенциально может вызвать исключение, и используйте блок `finally` для очистки ресурсов, если это необходимо.  При таком способе оператор `try` создает исключение, оператор `catch` обрабатывает исключение, а оператор `finally` закрывает или освобождает ресурсы.  
  
-   В блоках `catch` следует всегда упорядочивать исключения от более конкретных к более общим.  При таком методе определенное исключение обрабатывается до его передачи в блок `catch` более общего исключения.  
  
## Создание и вызов исключений  
 В следующем списке описываются рекомендации по созданию собственных исключений и ситуации, при которых они должны вызываться.  Дополнительные сведения см. в разделе [Правила разработки исключений](../../../docs/standard/design-guidelines/exceptions.md).  
  
-   Разрабатывайте классы таким образом, чтобы исключение никогда не создавалось при нормальном использовании.  Например, класс <xref:System.IO.FileStream> содержит методы, позволяющие определить, достигнут ли конец файла.  Это позволяет избежать создания исключения, создаваемого в случае выполнения чтения после окончания файла.  В следующем примере показан способ чтения до конца файла.  
  
     [!code-cpp[Conceptual.Exception.Handling#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#5)]
     [!code-csharp[Conceptual.Exception.Handling#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#5)]
     [!code-vb[Conceptual.Exception.Handling#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#5)]  
  
-   Вместо возврата кода ошибки или HRESULT следует создавать исключения.  
  
-   Для наиболее общих и часто встречающихся ошибок следует возвращать значение null.  Такие ошибки могут относиться к обычному потоку управления.  Возвращая значение null в таких случаях, можно сократить влияние на производительность приложения.  
  
-   В большинстве случаев следует использовать предопределенные типы исключений .NET Framework.  Создавайте новый класс исключений, только если предопределенное исключение не подходит.  
  
-   Вызывайте исключение <xref:System.InvalidOperationException>, если значение свойства или вызов метода не соответствуют текущему состоянию объекта.  
  
-   Вызывайте исключение <xref:System.ArgumentException> или класс, производный от <xref:System.ArgumentException>, если передаются недопустимые параметры.  
  
-   Для большинства приложений следует наследовать особые исключения от класса <xref:System.Exception>.  Наследование от класса <xref:System.ApplicationException> не имеет особого значения.  
  
-   Имена классов исключений завершайте словом "Exception".  Например:  
  
     [!code-cpp[Conceptual.Exception.Handling#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#4)]
     [!code-csharp[Conceptual.Exception.Handling#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#4)]
     [!code-vb[Conceptual.Exception.Handling#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#4)]  
  
-   В C\# и C\+\+ при создании собственных классов исключений можно использовать по меньшей мере три общих конструктора: конструктор по умолчанию, конструктор, принимающий строковое сообщение, и конструктор, принимающий строковое сообщение и внутреннее исключение.  Пример см. в разделе [Практическое руководство. Создание пользовательских исключений](../../../docs/standard/exceptions/how-to-create-user-defined-exceptions.md).  
  
    1.  <xref:System.Exception.%23ctor>, использующий значения по умолчанию.  
  
    2.  <xref:System.Exception.%23ctor%28System.String%29>, принимающий строковое сообщение.  
  
    3.  <xref:System.Exception.%23ctor%28System.String%2CSystem.Exception%29>, принимающий строковое сообщение и внутреннее исключение.  
  
-   При создании пользовательских исключений необходимо обеспечить доступность метаданных исключений для удаленно исполняемого кода, включая и те исключения, которые возникают между доменами приложений.  Например, предположим, что домен приложения А создает домен приложения В, который выполняет код, порождающий исключение.  Чтобы домен приложения A правильно перехватил и обработал это исключение, он должен иметь возможность найти сборку, содержащую исключение, вызванное доменом приложения B.  Если домен приложения B вызывает исключение, содержащееся в его базе приложения, но не в базе домена приложения A, то домен приложения A не сможет найти исключение и среда CLR вызовет исключение <xref:System.IO.FileNotFoundException>.  Чтобы избежать такой ситуации, можно развернуть сборку, содержащую сведения об исключении, двумя способами:  
  
    -   Поместите эту сборку в общую базу приложения, совместно используемую обоими доменами приложений.  
  
         \-или\-  
  
    -   Если у этих доменов нет общей базы приложения, то подпишите сборку, содержащую сведения об исключении, строгим именем и разверните ее в глобальном кэше сборок.  
  
-   В каждое исключение включайте локализованную строку описания.  Сообщение об ошибке, показываемое пользователю, извлекается из строки описания созданного исключения, а не из класса исключения.  
  
-   Используйте грамматически правильные сообщения об ошибке с соответствующей пунктуацией.  Каждое предложение в строке описания должно заканчиваться точкой.  Например, можно использовать строку описания "Переполнение таблицы журнала".  
  
-   Обеспечьте программный доступ к свойствам <xref:System.Exception>.  Дополнительные сведения \(кроме строки описания\) включайте в исключение только в тех случаях, когда в соответствии со сценарием программирования такие дополнительные сведения могут оказаться полезными.  Например, исключение <xref:System.IO.FileNotFoundException> предоставляет свойство <xref:System.IO.FileNotFoundException.FileName%2A>.  
  
-   Трассировка стека начинается в операторе, породившем исключение, и завершается оператором `catch`, перехватывающим это исключение.  Не забывайте об этом, принимая решение о месте расположения оператора `throw`.  
  
-   Используйте методы построителя исключений.  Обычно класс генерирует одно и то же исключение из различных мест своей реализации.  Чтобы избежать повторения кода, используйте вспомогательные методы, создающие исключение и затем возвращающие его.  Например:  
  
     [!code-cpp[Conceptual.Exception.Handling#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.exception.handling/cpp/source.cpp#6)]
     [!code-csharp[Conceptual.Exception.Handling#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.exception.handling/cs/source.cs#6)]
     [!code-vb[Conceptual.Exception.Handling#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.exception.handling/vb/source.vb#6)]  
  
     Другой вариант — воспользуйтесь конструктором для построения исключения.  Это больше подходит для глобальных классов исключений, таких как <xref:System.ArgumentException>.  
  
-   Устраняйте промежуточные результаты при порождении исключения.  Вызывающие объекты должны предполагать, что при создании исключения из метода не возникают побочные эффекты.  
  
## См. также  
 [Исключения](../../../docs/standard/exceptions/index.md)