---
title: Область подавления транзакции
ms.date: 03/30/2017
ms.assetid: 49fb6dd4-30d4-4067-925c-c5de44c8c740
ms.openlocfilehash: b38d168e7da4510b75ebeda7f4984c26fb68898d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="suppress-transaction-scope"></a>Область подавления транзакции
В этом образце показывается создание пользовательского действия `SuppressTransactionScope`, блокирующего внешнюю транзакцию среды выполнения при ее наличии.  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] образцов. Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`  
  
## <a name="sample-details"></a>Подробные сведения об образце  
 Пользовательское действие может служить для предотвращения прохождения транзакции к другой службе, если в данном сценарии поток транзакций нежелателен. В среде выполнения рабочего процесса реализована встроенная поддержка подавления внешних транзакций в классе <xref:System.Activities.NativeActivity>, но для ее применения необходимо создать пользовательское действие <xref:System.Activities.NativeActivity>, подобное показанному в данном образце.  
  
 Сценарий состоит из трех частей. Сначала <xref:System.Activities.Statements.TransactionScope> создает транзакцию среды выполнения, которая становится внешней. Это подтверждается пользовательским действием, выводящим местные и распределенные идентификаторы транзакции. Затем транзакция переходит к удаленной службе, после чего начинается вторая часть. В ходе второй части рабочий процесс входит в область `SuppressTransactionScope` и вновь повторяет процесс вывода идентификаторов транзакций и потоковой передачи транзакций. Однако пользовательское действие не находит внешнюю транзакцию, и сообщение, передаваемое службе, не содержит транзакции. В результате служба создает транзакцию, а это значит, что распределенные идентификаторы, выводимые на клиенте и в службе, не совпадают между собой. Последняя часть выполняется, когда закрывается `SuppressTransactionScope`, а среда исполнения вновь становится внешней, о чем свидетельствует другое сообщение, отправленное в службу с распределенным идентификатором, совпадающим с идентификатором первого сообщения.  
  
 Само действие является производным от <xref:System.Activities.NativeActivity>, поскольку оно должно запланировать дочернее действие и добавить свойство выполнения. У `SuppressTransactionScope` есть <xref:System.Activities.Variable> типа <xref:System.Activities.RuntimeTransactionHandle>, которое следует использовать вместо поля типа <xref:System.Activities.RuntimeTransactionHandle>, поскольку дескриптор необходимо инициировать. Идентификатор `Variable<RuntimeTransactionHandle>` добавляется к метаданным действия как переменная реализации, поскольку он используется только для внутренних задач.  
  
 При совершении действия сперва проверяется, был ли указан текст, и, если он был указан, то задается свойство `SuppressTransaction` для <xref:System.Activities.RuntimeTransactionHandle>. После задания свойства оно добавляется к свойствам исполнения и становится внешним. Это значит, что любое дочернее по отношению к `SuppressTransactionScope` действие может видеть свойство, и, следовательно, обеспечивает подавление транзакции среды подавления и приводит к формированию исключения во вложенной области <xref:System.Activities.Statements.TransactionScope>. После добавления дескриптора к свойствам исполнения планируется запуск текста.  
  
#### <a name="to-use-this-sample"></a>Использование этого образца  
  
1.  Откройте решение SuppressTransactionScope.sln в [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Чтобы построить решение, нажмите клавиши CTRL + SHIFT + B или выберите **построить решение** из **построения** меню.  
  
3.  После успешного построения щелкните решение правой кнопкой мыши и выберите **назначить запускаемые проекты**. В диалоговом окне выберите **несколько запускаемых проектов** и убедитесь, что для обоих проектов задано действие **запустить**.  
  
4.  Нажмите клавишу F5 или выберите **начать отладку** из **отладки** меню. Кроме того, нажмите клавиши CTRL + F5 или выберите **Запуск без отладки** из **отладки** меню для запуска без отладки.  
  
    > [!NOTE]
    >  Перед запуском клиента необходимо запустить сервер. Данные, выводимые в окне консоли, в котором размещена служба, указывают время начала работы службы.  
  
> [!IMPORTANT]
>  Образцы уже могут быть установлены на компьютере. Перед продолжением проверьте следующий каталог (по умолчанию).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Если этот каталог не существует, перейдите к [Windows Communication Foundation (WCF) и образцы Windows Workflow Foundation (WF) для .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) для загрузки всех Windows Communication Foundation (WCF) и [!INCLUDE[wf1](../../../../includes/wf1-md.md)] образцов. Этот образец расположен в следующем каталоге.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\SuppressTransactionScope`