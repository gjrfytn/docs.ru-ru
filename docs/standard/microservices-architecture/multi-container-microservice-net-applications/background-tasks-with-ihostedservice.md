---
title: Реализация фоновых задач в микрослужбах с помощью IHostedService и класса BackgroundService
description: Архитектура микрослужб .NET для упакованных в контейнеры приложений .NET | Реализация фоновых задач в микрослужбах с помощью IHostedService и класса BackgroundService
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 083d2a8c6a0d1649f8bfb2c21a92fb43381fe9ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a>Реализация фоновых задач в микрослужбах с помощью IHostedService и класса BackgroundService

Рано или поздно вам может потребоваться реализовать фоновые задачи и запланированные задания в приложении на основе микрослужб или приложении любого другого типа. Разница при использовании архитектуры микрослужб в том, что вы можете реализовать отдельный процесс или контейнер для размещения таких фоновых задач, чтобы затем масштабировать его по мере необходимости, или даже обеспечить выполнение единственного экземпляра этого процесса или контейнера микрослужбы.

Если посмотреть шире, в .NET Core такие задачи называются размещенными службами, так как они представляют собой службы или логику, размещаемые в узле, приложении или микрослужбе. Обратите внимание на то, что в этом случае под размещенной службой понимается просто класс с логикой фоновой задачи.

Начиная с версии .NET Core 2.0, платформа предоставляет новый интерфейс <xref:Microsoft.Extensions.Hosting.IHostedService>, который позволяет легко реализовывать размещенные службы. Главная идея заключается в том, что вы можете регистрировать несколько фоновых задач (размещенных служб), которые выполняются в фоновом режиме в процессе работы веб-узла или обычного узла, как показано на рисунке ниже.

![](./media/image26.png)

**Рис. 8-25**. Использование интерфейса IHostedService в классах WebHost и Host

Обратите внимание на различие между `WebHost` и `Host`. `WebHost` (базовый класс, реализующий интерфейс `IWebHost`) в ASP.NET Core 2.0 — это артефакт инфраструктуры, с помощью которого процесс получает доступ к возможностям сервера HTTP, например при реализации веб-приложения MVC или службы веб-интерфейса API. Он предоставляет все новые преимущества инфраструктуры в ASP.NET Core, позволяя использовать внедрение зависимостей, вставлять промежуточные слои в конвейер HTTP и, в частности, применять `IHostedServices` для фоновых задач.

`Host` (базовый класс, реализующий интерфейс `IHost`) — это новшество в .NET Core 2.1. По существу, класс `Host` обеспечивает практически такую же инфраструктуру, что и класс `WebHost` (внедрение зависимостей, размещенные службы и т. д.), но в этом случае узел должен представлять собой более простой процесс без связанных с MVC веб-интерфейсами API или сервером HTTP возможностей.

Таким образом, вы можете либо создать специальный процесс узла с помощью интерфейса IHost для реализации только размещенных служб, например микрослужбу, предназначенную специально для размещения `IHostedServices`, либо вы можете расширить существующий класс `WebHost` в ASP.NET Core, например существующий веб-интерфейс API ASP.NET Core или приложение MVC. 

Каждый подход имеет свои преимущества и недостатки в зависимости от потребностей бизнеса и требований к масштабируемости. Основной принцип заключается в том, что если фоновые задачи не связаны с HTTP (IWebHost), в .NET Core 2.1 следует использовать интерфейс IHost, если это возможно.

## <a name="registering-hosted-services-in-your-webhost-or-host"></a>Регистрация размещенных служб в WebHost или Host

Давайте более подробно разберем интерфейс `IHostedService`, так как его использование в классах `WebHost` и `Host` во многом схоже. 

Библиотека SignalR — один из примеров артефактов, использующих размещенные службы, однако ее можно применять и для более простых задач, таких как следующие:

-   фоновая задача опроса базы данных для поиска изменений;
-   запланированная задача для периодического обновления кэша;
-   реализация QueueBackgroundWorkItem, которая позволяет задаче выполняться в фоновом потоке;
-   обработка сообщений из очереди сообщений веб-приложения в фоновом режиме при использовании общих служб, таких как `ILogger`;
-   фоновая задача, запускаемая с помощью `Task.Run()`.

Выполнение любого из этих действий можно перенести в фоновую задачу на основе IHostedService.

Для добавления одного или нескольких экземпляров `IHostedServices` в `WebHost` или `Host` их следует зарегистрировать посредством стандартного внедрения зависимостей в классе ASP.NET Core `WebHost` (или в классе `Host` в .NET Core 2.1). Фактически размещенные службы регистрируются в известном методе `ConfigureServices()` класса `Startup`, как в следующем коде типичного класса ASP.NET WebHost: 

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{            
    //Other DI registrations;

    // Register Hosted Services
    services.AddSingleton<IHostedService, GracePeriodManagerService>();
    services.AddSingleton<IHostedService, MyHostedServiceB>();
    services.AddSingleton<IHostedService, MyHostedServiceC>();
    //...
}
```

В этом коде размещенная служба `GracePeriodManagerService` представляет собой реальный код микрослужбы размещения заказов в приложении eShopOnContainers, а другие две службы — это просто дополнительные примеры.

Выполнение фоновой задачи `IHostedService` согласуется с временем существования приложения (узла или микрослужбы). Задачи регистрируются при запуске приложения, а при завершении его работы есть возможность произвести надлежащую обработку или очистку.

Фоновый поток можно запускать для выполнения любой задачи и без использования `IHostedService`. Различие именно в том, что будет происходить при завершении работы приложения: поток будет просто завершаться без возможности надлежащей очистки.


## <a name="the-ihostedservice-interface"></a>Интерфейс IHostedService

При регистрации интерфейса `IHostedService` платформа .NET Core вызывает методы `StartAsync()` и `StopAsync()` типа `IHostedService` во время запуска и остановки приложения соответственно. В частности, метод запуска вызывается после запуска сервера и активации `IApplicationLifetime.ApplicationStarted`.

Определение интерфейса `IHostedService` в .NET Core выглядит следующим образом.

```csharp
namespace Microsoft.Extensions.Hosting
{
    //
    // Summary:
    //     Defines methods for objects that are managed by the host.
    public interface IHostedService
    {
        //
        // Summary:
        // Triggered when the application host is ready to start the service.
        Task StartAsync(CancellationToken cancellationToken);
        //
        // Summary:
        // Triggered when the application host is performing a graceful shutdown.
        Task StopAsync(CancellationToken cancellationToken);
    }
}
```
Как было показано ранее, вы можете создать несколько реализаций IHostedService и зарегистрировать их в методе `ConfigureService()` в контейнере внедрения зависимостей. Все эти размещенные службы будут запускаться и останавливаться вместе с приложением или микрослужбой.

Разработчик отвечает за обработку завершения действия или работы служб при вызове метода `StopAsync()` узлом.

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a>Реализация IHostedService с помощью пользовательского класса размещенной службы, производного от базового класса BackgroundService

Можно пойти дальше и создать пользовательский класс размещенной службы с нуля, реализовав интерфейс `IHostedService`, как это требуется делать в .NET Core 2.0. 

Однако поскольку большинство фоновых задач имеют одинаковые потребности в отношении управления токенами отмены и других типичных операций, в .NET Core 2.1 будет доступен очень удобный абстрактный базовый класс BackgroundService, от которого можно будет производить наследование.

Он будет выполнять основную часть работы, связанной с настройкой фоновой задачи. Имейте в виду, что этот класс будет входить в состав библиотеки .NET Core 2.1, поэтому писать его не нужно.

Однако на момент написания этой статьи платформа .NET Core 2.1 еще не была выпущена. Поэтому в приложение eShopOnContainers, которое в настоящее время использует .NET Core 2.0, этот класс временно включен из репозитория .NET Core 2.1 с открытым кодом (требуется только лицензия на открытый код), так как он совместим с текущим интерфейсом IHostedService в .NET Core 2.0. Когда платформа .NET Core 2.1 будет выпущена, нужно будет лишь указать соответствующий пакет NuGet.

Следующий код — это абстрактный базовый класс BackgroundService, реализованный в .NET Core 2.1:

```csharp
// Copyright (c) .NET Foundation. Licensed under the Apache License, Version 2.0. 
/// <summary>
/// Base class for implementing a long running <see cref="IHostedService"/>.
/// </summary>
public abstract class BackgroundService : IHostedService, IDisposable
{
    private Task _executingTask;
    private readonly CancellationTokenSource _stoppingCts = 
                                                   new CancellationTokenSource();

    protected abstract Task ExecuteAsync(CancellationToken stoppingToken);

    public virtual Task StartAsync(CancellationToken cancellationToken)
    {
        // Store the task we're executing
        _executingTask = ExecuteAsync(_stoppingCts.Token);

        // If the task is completed then return it, 
        // this will bubble cancellation and failure to the caller
        if (_executingTask.IsCompleted)
        {
            return _executingTask;
        }

        // Otherwise it's running
        return Task.CompletedTask;
    }
    
    public virtual async Task StopAsync(CancellationToken cancellationToken)
    {
        // Stop called without start
        if (_executingTask == null)
        {
            return;
        }

        try
        {
            // Signal cancellation to the executing method
            _stoppingCts.Cancel();
        }
        finally
        {
            // Wait until the task completes or the stop token triggers
            await Task.WhenAny(_executingTask, Task.Delay(Timeout.Infinite,
                                                          cancellationToken));
        }

    }

    public virtual void Dispose()
    {
        _stoppingCts.Cancel();
    }
}
```

Благодаря такой унаследованной реализации при создании собственного класса размещенной службы, производного от приведенного выше абстрактного базового класса, необходимо просто реализовать в нем метод `ExecuteAsync()`. Пример представлен в следующем упрощенном коде из приложения eShopOnContainers, который опрашивает базу данных и при необходимости публикует события интеграции в шине событий.

```csharp
public class GracePeriodManagerService : BackgroundService
{        
    private readonly ILogger<GracePeriodManagerService> _logger;
    private readonly OrderingBackgroundSettings _settings;

    private readonly IEventBus _eventBus;

    public GracePeriodManagerService(IOptions<OrderingBackgroundSettings> settings,
                                     IEventBus eventBus,
                                     ILogger<GracePeriodManagerService> logger)
        {
            //Constructor’s parameters validations...       
        }

        protected override async Task ExecuteAsync(CancellationToken stoppingToken)
        {
            _logger.LogDebug($"GracePeriodManagerService is starting.");

            stoppingToken.Register(() => 
                    _logger.LogDebug($" GracePeriod background task is stopping."));

            while (!stoppingToken.IsCancellationRequested)
            {
                _logger.LogDebug($"GracePeriod task doing background work.");

                // This eShopOnContainers method is quering a database table 
                // and publishing events into the Event Bus (RabbitMS / ServiceBus)
                CheckConfirmedGracePeriodOrders();

                await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
            }
            
            _logger.LogDebug($"GracePeriod background task is stopping.");

        }

        protected override async Task StopAsync (CancellationToken stoppingToken)
        {
               // Run your graceful clean-up actions
        }
}
```

В этом конкретном случае выполняется метод приложения eShopOnContainers, который выполняет запрос к таблице базы данных для поиска заказов с определенным состоянием, а при применении изменений события интеграции публикуются через шину событий (она может быть основана на RabbitMQ или служебной шине Azure). 

Естественно, вместо этого можно выполнять любую другую фоновую бизнес-задачу.

По умолчанию для токена отмены задается время ожидания, равное 5 секундам, хотя это значение можно изменить при создании `WebHost` с помощью расширения `UseShutdownTimeout` интерфейса `IWebHostBuilder`. Это означает, что отмена службы ожидается в течение 5 секунд. В противном случае ее работа будет завершена внезапно.

В следующем коде это время изменяется на 10 секунд:

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a>Сводная диаграмма классов

На приведенном ниже рисунке 8-26 представлена наглядная сводка классов и интерфейсов, которые задействованы в реализации IHostedService.
 
![](./media/image27.png)

**Рис. 8-26**. Диаграмма классов и интерфейсов, связанных с IHostedService

### <a name="deployment-considerations-and-takeaways"></a>Основные положения и моменты, связанные с развертыванием

Важно отметить, что способ развертывания узла `WebHost` в ASP.NET Core или `Host` в .NET Core может влиять на конечное решение. Например, если вы развертываете `WebHost` в службах IIS или обычной службе приложений Azure, работа узла может быть завершена из-за перезапуска пула приложений. Однако если вы развертываете узел как контейнер в оркестраторе, таком как Kubernetes или Service Fabric, вы можете контролировать гарантированное число активных экземпляров узла. Кроме того, в облачной среде можно рассмотреть другие подходы, особенно предназначенные для таких сценариев, как Функции Azure. 

Даже при развертывании `WebHost` в пуле приложений применим ряд сценариев, таких как повторное заполнение или сброс кэша в памяти для приложения.

Интерфейс `IHostedService` предоставляет удобный способ запуска фоновых задач в веб-приложении ASP.NET Core (в .NET Core 2.0) или в любом процессе или узле (при использовании `IHost` начиная с .NET Core 2.1). Его главное преимущество — это возможность надлежащей отмены с целью очистки кода фоновых задач при завершении работы самого узла.


#### <a name="additional-resources"></a>Дополнительные ресурсы

-   **Создание запланированной задачи в ASP.NET Core или Standard 2.0** 

    [*https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html*](https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html)

-   **Реализация интерфейса IHostedService в ASP.NET Core 2.0** 

    [*https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice*](https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice)

-   **Образцы размещения в ASP.NET Core 2.1** 

    [*https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample*](https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample)



>[!div class="step-by-step"]
[Назад] (test-aspnet-core-services-web-apps.md) [Далее] (../microservice-ddd-cqrs-patterns/index.md)
