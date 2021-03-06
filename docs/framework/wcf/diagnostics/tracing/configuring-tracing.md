---
title: Настройка трассировки
ms.date: 03/30/2017
helpviewer_keywords:
- tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
ms.openlocfilehash: f9603f79992c31ad1af3b6c672b448ab031ba78d
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/07/2018
---
# <a name="configuring-tracing"></a>Настройка трассировки
В этом разделе описывается, как включить трассировку, настроить создание трассировки источниками трассировки и задать уровни трассировки, задать распространение и трассировку действий для поддержки сквозной корреляции трассировки, а также настроить доступ прослушивателей трассировки к трассировкам.  
  
 Рекомендации параметры трассировки в рабочей среде или среде отладки, см. в разделе [рекомендуемые параметры для трассировки и ведения журнала сообщений](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
> [!IMPORTANT]
>  В Windows 8, чтобы приложение могло создавать журналы трассировки, необходимо запустить его с расширенными правами доступа (запуск от имени администратора).  
  
## <a name="enabling-tracing"></a>Включение трассировки  
 Windows Communication Foundation (WCF) выдает следующие данные для диагностической трассировки:  
  
-   Трассировки основных этапов процесса по всем компонентам приложений, таких как вызовы операций, исключения кода, предупреждения и прочие значительные события обработки.  
  
-   События ошибок Windows при сбоях возможности трассировки. В разделе [ведение журнала событий](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
 Трассировка WCF, построены на основе <xref:System.Diagnostics>. Чтобы воспользоваться трассировкой, необходимо определить источники трассировки в файле конфигурации или в коде. WCF определяет источник трассировки для каждой сборки, WCF. `System.ServiceModel` Источник трассировки является наиболее общий источник трассировки WCF и записывает этапов обработки через стек связи WCF от входа и выхода из транспорта до входа и выхода из пользовательского кода. Источник трассировки `System.ServiceModel.MessageLogging` записывает все сообщения, проходящие через систему.  
  
 По умолчанию трассировка отключена. Чтобы включить трассировку, необходимо создать прослушиватель трассировки и задать уровень трассировки, отличное от «Off» для выбранного источника трассировки в конфигурации. в противном случае WCF не создает трассировку. Если прослушиватель не указан, трассировка автоматически отключается. Если прослушиватель определен, но уровень не указан, по умолчанию устанавливается уровень «Off», при котором трассировка не создается.  
  
 Если используются точки расширяемости WCF, такие как вызов пользовательской операции, следует создавать свои собственные трассировки. Это так, как при реализации точки расширяемости WCF не сможет создавать стандартные трассировки в пути по умолчанию. Если поддержка трассировки вручную путем создания трассировки не реализована, можно не увидеть ожидаемые трассировки.  
  
 Трассировку можно настроить, внеся изменения в файл конфигурации приложения: Web.config (для веб-приложений) или Appname.exe.config (для резидентных приложений). Ниже приводится пример подобного изменения. Дополнительные сведения об этих параметрах см. в разделе «Настройка трассировки потребления трассировки прослушивателями».  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="traceListener"   
                   type="System.Diagnostics.XmlWriterTraceListener"   
                   initializeData= "c:\log\Traces.svclog" />  
            </listeners>  
         </source>  
      </sources>  
   </system.diagnostics>  
</configuration>  
```  
  
> [!NOTE]
>  Чтобы изменить файл конфигурации проекта службы WCF в Visual Studio, щелкните правой кнопкой мыши файл конфигурации приложения: Web.config для веб-приложений, либо Appname.exe.config для резидентных приложений в **обозревателе решений** . Выберите **изменить конфигурацию WCF** пункт контекстного меню. Будет запущен [средство редактирования конфигурации (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md), что позволяет изменить параметры конфигурации для служб WCF с помощью графического пользовательского интерфейса.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>Настройка создания трассировки источниками трассировки  
 WCF определяет источник трассировки для каждой сборки. Трассировки, созданные в пределах сборки, доступны прослушивателям, определенным для этого источника. Определяются следующие источники трассировки:  
  
-   System.ServiceModel: Записывает в журнал все этапы обработки WCF, каждый раз, когда конфигурация для чтения, обработка сообщения в транспорте, обработка событий безопасности, сообщение отправляется в пользовательском коде и т. д.  
  
-   System.ServiceModel.MessageLogging: записывает в журнал все сообщения, проходящие через систему.  
  
-   System.IdentityModel.  
  
-   System.ServiceModel.Activation.  
  
-   System.IO.Log: средство ведения журнала для интерфейса платформы .NET Framework для системы CLFS.  
  
-   System.Runtime.Serialization: регистрирует в журнале чтение и запись объектов.  
  
-   CardSpace.  
  
 Можно настроить все источники трассировки так, чтобы они использовали один и тот же (общий) прослушиватель, как показано в следующем примере конфигурации.  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="CardSpace">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IO.Log">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.Runtime.Serialization">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IdentityModel">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
        </sources>  
  
        <sharedListeners>  
            <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\log\Traces.svclog" />  
        </sharedListeners>  
    </system.diagnostics>  
</configuration>  
```  
  
 Кроме того, можно добавить пользовательские источники трассировки, создающие трассировки пользовательского кода, как показано в следующем примере.  
  
```xml  
<system.diagnostics>  
   <sources>  
       <source name="UserTraceSource" switchValue="Warning, ActivityTracing" >  
          <listeners>  
              <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="C:\logs\UserTraces.svclog" />  
          </listeners>  
       </source>  
   </sources>  
   <trace autoflush="true" />   
</system.diagnostics>  
```  
  
 Дополнительные сведения о создании источников трассировки, определенное пользователем. в разделе [расширение трассировки](../../../../../docs/framework/wcf/samples/extending-tracing.md).  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>Настройка потребления трассировки прослушивателями трассировки  
 Во время выполнения WCF веб-каналов данных трассировки прослушивателям, которые обработки данных. WCF предоставляет несколько стандартных прослушивателей для <xref:System.Diagnostics>, отличающихся форматом выводимых данных. Можно добавлять пользовательские типы прослушивателей.  
  
 С помощью `add` можно задать имя и тип прослушивателя трассировки, который требуется использовать. В данном примере конфигурации создается прослушиватель с именем `traceListener` и добавляется стандартный прослушиватель трассировки .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) в качестве типа, который требуется использовать. Для каждого источника можно добавить любое количество прослушивателей трассировки. Если прослушиватель трассировки выполняет трассировку в файл, необходимо указать расположение и имя выходного файла в файле конфигурации. Для этого необходимо указать имя файла для этого прослушивателя в качестве значения для `initializeData`. Если имя файла не указано, используется случайное имя, сгенерированное на основе используемого типа прослушивателя. Если используется <xref:System.Diagnostics.XmlWriterTraceListener>, создается имя файла без расширения. Если реализовать пользовательский прослушиватель, с помощью этого атрибута также можно получать другие данные инициализации, помимо имени файла. Например, с его помощью можно указать идентификатор базы данных.  
  
 Пользовательский прослушиватель трассировки можно настроить так, чтобы он отправлял трассировку по сети, например в удаленную базу данных. Разработчику приложения следует обеспечить надлежащее управление доступом к журналам трассировки на удаленном компьютере.  
  
 Также можно настроить прослушиватель трассировки программно. Дополнительные сведения см. в разделе [как: Создание и инициализация прослушивателей трассировки](http://go.microsoft.com/fwlink/?LinkId=94648) и [Создание TraceListener настраиваемый](http://go.microsoft.com/fwlink/?LinkId=96239).  
  
> [!CAUTION]
>  Поскольку прослушиватель `System.Diagnostics.XmlWriterTraceListener` не является потокобезопасным, источник трассировки может монопольно блокировать ресурсы при выводе трассировки. Если несколько потоков выводят трассировку в источник трассировки, использующий (согласно заданным настройкам) этот прослушиватель, может возникнуть состязание за ресурсы, что приводит к существенному падению производительности. Чтобы устранить эту проблему, реализуйте потокобезопасный пользовательский прослушиватель.  
  
## <a name="trace-level"></a>Уровень трассировки  
 Уровень трассировки контролируется параметром `switchValue` источника трассировки. Доступные уровни трассировки приведены в следующей таблице.  
  
|Уровень трассировки|Характер отслеживаемых событий|Содержимое отслеживаемых событий|Отслеживаемые события|Целевая категория пользователей|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Off|Н/Д|Н/Д|Трассировки не создаются.|Н/Д|  
|Critical|«Негативные» события: указывающие о непредвиденном состоянии обработки или об ошибке.||В журнал заносятся необработанные исключения, в том числе следующие:<br /><br /> -OutOfMemoryException<br />-ThreadAbortException (среда CLR вызывает ThreadAbortExceptionHandler)<br />-StackOverflowException (не может быть перехвачено)<br />-ConfigurationErrorsException<br />-SEHException<br />-Запуска ошибки<br />-События Failfast<br />-Система зависает<br />-Подозрительные сообщения: трассировки сообщений, которые приводят к сбою приложения.|Администраторы<br /><br /> Разработчики приложений|  
|Error|«Негативные» события: указывающие о непредвиденном состоянии обработки или об ошибке.|Возникло непредвиденное состояние обработки. Приложению не удалось выполнить задачу требуемым образом. Впрочем, приложение все еще работает.|Все исключения заносятся в журнал.|Администраторы<br /><br /> Разработчики приложений|  
|Предупреждение|«Негативные» события: указывающие о непредвиденном состоянии обработки или об ошибке.|Возникла (или может возникнуть) проблема, но приложение все же работает надлежащим образом. Впрочем, его правильное выполнение может прекратиться.|-Приложение получает больше запросов, чем его параметрами регулирования.<br />-Принимающая очередь близка к заданному максимальному пределу емкости.<br />-Превышено время ожидания.<br />-Учетные данные не принимаются.|Администраторы<br /><br /> Разработчики приложений|  
|Сведения|«Позитивные» события: отмечающие успешно пройденные основные этапы|Успешно пройденные важные этапы выполнения приложения, вне зависимости от того, правильно ли работает приложение.|Как правило, создаются сообщения, полезные для мониторинга и диагностики состояния системы, измерений производительности или профилирования. Эту информацию можно использовать для планирования загрузки и управления производительностью.<br /><br /> -Создание каналов.<br />-Создание конечной точки прослушивателей.<br />-Сообщение вводит и оставляет транспорта.<br />-Извлечение маркера безопасности.<br />-Чтение параметра конфигурации.|Администраторы<br /><br /> Разработчики приложений<br /><br /> Разработчики программных продуктов.|  
|Verbose|«Позитивные» события: отмечающие успешно пройденные основные этапы.|Создаются события низкого уровня как для пользовательского кода, так и для обслуживания.|Как правило, этот уровень можно использовать для отладки или оптимизации приложения.<br /><br /> -Распознанный заголовок сообщения.|Администраторы<br /><br /> Разработчики приложений<br /><br /> Разработчики программных продуктов.|  
|ActivityTracing||События переходов между действиями по обработке и компонентами.|Этот уровень позволяет администраторам и разработчикам коррелировать приложения из одного домена приложений.<br /><br /> -Трассировки границ действий, таких как запуск и остановка.<br />-Трассировки для перенаправлений.|Все|  
|Все||Приложение может работать надлежащим образом. Создаются все события.|Все вышеперечисленные события.|Все|  
  
 Каждый уровень трассировки от Verbose до Critical включает все вышестоящие уровни, за исключением уровня "Off". Например, если прослушиватель прослушивает уровень Warning, он получает трассировки, имеющие уровень Critical, Error и Warning. Уровень All включает в себя все события уровней от Verbose до Critical, а также события ActivityTracing (прослеживание действий).  
  
> [!CAUTION]
>  Уровни Information, Verbose и ActivityTracing создают большое количество трассировок, что может негативно сказаться на производительности в отношении обработки сообщений, если все доступные ресурсы компьютера использованы.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Настройка распространения и трассировки действий для корреляции  
 Для атрибута `activityTracing` можно задать значение `switchValue`, чтобы включить трассировку действий, создающую трассировку для границ действий и передач в пределах конечных точек.  
  
> [!NOTE]
>  При использовании некоторых возможностей расширяемости в WCF, можно получить <xref:System.NullReferenceException> при включении трассировки действий. Чтобы устранить эту проблему, проверьте файл конфигурации своего приложения: атрибут `switchValue` для соответствующего источника трассировки не должен иметь значение `activityTracing`.  
  
 Атрибут `propagateActivity` указывает, должно ли действие распространяться на другие конечные точки, участвующие в обмене сообщениями. Если присвоить ему значение `true`, можно с помощью файлов трассировки, созданных любыми двумя конечными точками, проследить прохождение набора трассировок от одной конечной точки до набора трассировок на другой конечной точке.  
  
 Дополнительные сведения о трассировка и распространение действий см. в разделе [распространения](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md).  
  
 Оба `propagateActivity` и `ActivityTracing` логические значения применяются к источнику трассировки System.ServiceModel. `ActivityTracing` Значение также применяется к любому источнику трассировки, включая WCF или определенные пользователем.  
  
 Атрибут `propagateActivity` нельзя использовать для пользовательских источников трассировок. Для распространения идентификатора действия пользовательского кода необходимо убедиться, что ServiceModel `ActivityTracing` не задано, тогда как ServiceModel `propagateActivity` имеет значение `true`.  
  
## <a name="see-also"></a>См. также  
 [Трассировка](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Администрирование и диагностика](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Практическое руководство. Создание и инициализация прослушивателей трассировки](http://go.microsoft.com/fwlink/?LinkId=94648)  
 [Создание пользовательский прослушиватель трассировки](http://go.microsoft.com/fwlink/?LinkId=96239)
