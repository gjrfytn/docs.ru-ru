---
title: "Таблица принятия решений. Платформы .NET Framework для Docker"
description: "Архитектура Микрослужбами .NET для приложений .NET в контейнерах | Таблицы решений, платформы .NET Framework для Docker"
keywords: "Docker, микрослужбы, ASP.NET, контейнер"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 4889662c4d887bebd320389e3ced6aae1c93133b
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 10/22/2017
---
# <a name="decision-table-net-frameworks-to-use-for-docker"></a><span data-ttu-id="94107-105">В решениях: платформы .NET Framework для Docker</span><span class="sxs-lookup"><span data-stu-id="94107-105">Decision table: .NET frameworks to use for Docker</span></span>

<span data-ttu-id="94107-106">В следующей таблице показаны следует ли использовать контейнеры .NET Framework или .NET Core и Windows или Linux.</span><span class="sxs-lookup"><span data-stu-id="94107-106">The following summarizes whether to use .NET Framework or .NET Core, and Windows or Linux containers.</span></span> <span data-ttu-id="94107-107">Следует помните, что для контейнеров Linux на основе Linux Docker узлов (виртуальные машины или серверы) может потребоваться для контейнеров Windows требуется Windows Server на основе Docker узлов (виртуальные машины или серверы).</span><span class="sxs-lookup"><span data-stu-id="94107-107">Remember that for Linux containers, you need Linux-based Docker hosts (VMs or servers) and that for Windows Containers you need Windows Server based Docker hosts (VMs or servers).</span></span>

<span data-ttu-id="94107-108">Есть несколько функций приложения, которые влияют на решение.</span><span class="sxs-lookup"><span data-stu-id="94107-108">There are several features of your application that affect your decision.</span></span> <span data-ttu-id="94107-109">После принятия решения следует сравнить важность этих функций.</span><span class="sxs-lookup"><span data-stu-id="94107-109">You should weigh the importance of these features when making your decision.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="94107-110">На компьютерах разработчиков будет выполняться один узел Docker, Windows или Linux.</span><span class="sxs-lookup"><span data-stu-id="94107-110">Your development machines will run one Docker host, either Linux or Windows.</span></span> <span data-ttu-id="94107-111">Связанные микрослужбами, которую требуется выполнять и тестировать вместе в одном решении потребуется для запуска на одной платформе контейнера.</span><span class="sxs-lookup"><span data-stu-id="94107-111">Related microservices that you want to run and test together in one solution will all need to run on the same container platform.</span></span>

* <span data-ttu-id="94107-112">Выбор архитектуры приложения является **Микрослужбами в контейнерах**.</span><span class="sxs-lookup"><span data-stu-id="94107-112">Your application architecture choice is **Microservices on containers**.</span></span>
    - <span data-ttu-id="94107-113">Выбор реализация .NET должно быть *.NET Core*.</span><span class="sxs-lookup"><span data-stu-id="94107-113">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="94107-114">Выбор платформы контейнер может быть как *контейнеров Linux* или *контейнеры Windows*.</span><span class="sxs-lookup"><span data-stu-id="94107-114">Your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
* <span data-ttu-id="94107-115">Выбор архитектуры приложения является **монолитные приложения**.</span><span class="sxs-lookup"><span data-stu-id="94107-115">Your application architecture choice is a **Monolithic application**.</span></span>
    - <span data-ttu-id="94107-116">Выбор .NET реализация может быть как *.NET Core* или *.NET Framework*.</span><span class="sxs-lookup"><span data-stu-id="94107-116">Your .NET implementation choice can be either *.NET Core* or *.NET Framework*.</span></span>
    - <span data-ttu-id="94107-117">Если вы выбрали *.NET Core*, Выбор платформы контейнер может быть как *контейнеров Linux* или *контейнеры Windows*.</span><span class="sxs-lookup"><span data-stu-id="94107-117">If you have chosen *.NET Core*, your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
    - <span data-ttu-id="94107-118">Если вы выбрали *.NET Framework*, Выбор платформы контейнер должен быть *контейнеры Windows*.</span><span class="sxs-lookup"><span data-stu-id="94107-118">If you have chosen *.NET Framework*, your container platform choice must be *Windows containers*.</span></span>
* <span data-ttu-id="94107-119">Приложение будет **новый контейнер разработка («зеленый поле»)**.</span><span class="sxs-lookup"><span data-stu-id="94107-119">Your application is a  **New container-based development ("green-field")**.</span></span>
    - <span data-ttu-id="94107-120">Выбор реализация .NET должно быть *.NET Core*.</span><span class="sxs-lookup"><span data-stu-id="94107-120">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="94107-121">Выбор платформы контейнер может быть как *контейнеров Linux* или *контейнеры Windows*.</span><span class="sxs-lookup"><span data-stu-id="94107-121">Your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
* <span data-ttu-id="94107-122">Приложение будет **миграции приложений прежних версий («коричневый поле») Windows Server для контейнеров**</span><span class="sxs-lookup"><span data-stu-id="94107-122">Your application is a **Windows Server legacy app ("brown-field") migration to containers**</span></span>
    - <span data-ttu-id="94107-123">Выбор реализация .NET — *.NET Framework* зависимости от платформы.</span><span class="sxs-lookup"><span data-stu-id="94107-123">Your .NET implementation choice is *.NET Framework* based on framework dependency.</span></span>
    - <span data-ttu-id="94107-124">Выбор платформы контейнер должен быть *контейнеры Windows* из-за зависимости платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94107-124">Your container platform choice must be *Windows containers* because of the .NET Framework dependency.</span></span>
* <span data-ttu-id="94107-125">Задача разработки приложения — **лучших в своем классе производительность и масштабируемость**.</span><span class="sxs-lookup"><span data-stu-id="94107-125">Your application's design goal is **Best-in-class performance and scalability**.</span></span>
    - <span data-ttu-id="94107-126">Выбор реализация .NET должно быть *.NET Core*.</span><span class="sxs-lookup"><span data-stu-id="94107-126">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="94107-127">Выбор платформы контейнер может быть как *контейнеров Linux* или *контейнеры Windows*.</span><span class="sxs-lookup"><span data-stu-id="94107-127">Your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
* <span data-ttu-id="94107-128">Построение приложения с помощью **ASP.NET Core**.</span><span class="sxs-lookup"><span data-stu-id="94107-128">You built your application using **ASP.NET Core**.</span></span>
    - <span data-ttu-id="94107-129">Выбор реализация .NET должно быть *.NET Core*.</span><span class="sxs-lookup"><span data-stu-id="94107-129">Your .NET implementation choice should be *.NET Core*.</span></span>
    - <span data-ttu-id="94107-130">Можно использовать *.NET Framework* реализации, когда у вас есть другие зависимости от платформы.</span><span class="sxs-lookup"><span data-stu-id="94107-130">You can use the *.NET Framework* implementation, if you have other framework dependencies.</span></span>
    - <span data-ttu-id="94107-131">Если вы выбрали *.NET Core*, Выбор платформы контейнер может быть как *контейнеров Linux* или *контейнеры Windows*.</span><span class="sxs-lookup"><span data-stu-id="94107-131">If you have chosen *.NET Core*, your container platform choice can be either *Linux containers* or *Windows containers*.</span></span>
    - <span data-ttu-id="94107-132">Если вы выбрали *.NET Framework*, Выбор платформы контейнер должен быть *контейнеры Windows*.</span><span class="sxs-lookup"><span data-stu-id="94107-132">If you have chosen *.NET Framework*, your container platform choice must be *Windows containers*.</span></span>
* <span data-ttu-id="94107-133">Построение приложения с помощью **4 ASP.NET (MVC 5, веб-API 2 и веб-форм)**.</span><span class="sxs-lookup"><span data-stu-id="94107-133">You built your application using **ASP.NET 4 (MVC 5, Web API 2, and Web Forms)**.</span></span>
    - <span data-ttu-id="94107-134">Выбор реализация .NET — *.NET Framework* зависимости от платформы.</span><span class="sxs-lookup"><span data-stu-id="94107-134">Your .NET implementation choice is *.NET Framework* based on framework dependency.</span></span>
    - <span data-ttu-id="94107-135">Выбор платформы контейнер должен быть *контейнеры Windows* из-за зависимости платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94107-135">Your container platform choice must be *Windows containers* because of the .NET Framework dependency.</span></span>
* <span data-ttu-id="94107-136">Приложение использует **службам SignalR**.</span><span class="sxs-lookup"><span data-stu-id="94107-136">Your application uses **SignalR services**.</span></span>
    - <span data-ttu-id="94107-137">Выбор .NET реализация может быть *.NET Framework*, или *.NET Core 2.1 (после его выпуска) или более поздней версии*.</span><span class="sxs-lookup"><span data-stu-id="94107-137">Your .NET implementation choice can be *.NET Framework*, or *.NET Core 2.1 (when released) or later*.</span></span>
    - <span data-ttu-id="94107-138">Выбор платформы контейнер должен быть *контейнеры Windows* при выборе реализацию SignalR в .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94107-138">Your container platform choice must be *Windows containers* if you chose the SignalR implementation in .NET Framework.</span></span>
    - <span data-ttu-id="94107-139">Выбор платформы контейнер может быть Linux с контейнерами или контейнерами Windows, при выборе реализации SignalR Core .NET 2.1 или более поздней версии (после его выпуска).</span><span class="sxs-lookup"><span data-stu-id="94107-139">Your container platform choice can be either Linux containers or Windows containers if you chose the SignalR implementation in .NET Core 2.1 or later (when released).</span></span>  
    - <span data-ttu-id="94107-140">Когда **службам SignalR** проведение *.NET Core*, можно использовать *Linux контейнерами или контейнерами Windows*.</span><span class="sxs-lookup"><span data-stu-id="94107-140">When **SignalR services** run on *.NET Core*, you can use *Linux containers or Windows Containers*.</span></span>
* <span data-ttu-id="94107-141">Приложение использует **WCF, WF, а также другие прежние платформы**.</span><span class="sxs-lookup"><span data-stu-id="94107-141">Your application uses **WCF, WF, and other legacy frameworks**.</span></span>
    - <span data-ttu-id="94107-142">Выбор реализация .NET — *.NET Framework*, или *.NET Core (в план в будущих выпусках)*.</span><span class="sxs-lookup"><span data-stu-id="94107-142">Your .NET implementation choice is *.NET Framework*, or *.NET Core (in the roadmap for a future release)*.</span></span>
    - <span data-ttu-id="94107-143">Выбор платформы контейнер должен быть *контейнеры Windows* из-за зависимости платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94107-143">Your container platform choice must be *Windows containers* because of the .NET Framework dependency.</span></span>
* <span data-ttu-id="94107-144">Приложение включает в себя **служб потребления Azure**.</span><span class="sxs-lookup"><span data-stu-id="94107-144">Your application involves **Consumption of Azure services**.</span></span>
    - <span data-ttu-id="94107-145">Выбор реализация .NET — *.NET Framework*, или *.NET Core (служб в конце концов все Azure выведет клиентские пакеты SDK для .NET Core)*.</span><span class="sxs-lookup"><span data-stu-id="94107-145">Your .NET implementation choice is *.NET Framework*, or *.NET Core (eventually all Azure services will provide client SDKs for .NET Core)*.</span></span>
    - <span data-ttu-id="94107-146">Выбор платформы контейнер должен быть *контейнеры Windows* при использовании интерфейсов API клиента .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="94107-146">Your container platform choice must be *Windows containers* if you use .NET Framework client APIs.</span></span>
    - <span data-ttu-id="94107-147">При использовании интерфейсов API, доступные для клиента *.NET Core*, можно также выбрать между *Linux контейнеры и контейнеры Windows*.</span><span class="sxs-lookup"><span data-stu-id="94107-147">If you use client APIs available for *.NET Core*, you can also choose between *Linux containers and Windows containers*.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="94107-148">[Предыдущие] (net-framework контейнера scenarios.md) [Далее] (net контейнера os-targets.md)</span><span class="sxs-lookup"><span data-stu-id="94107-148">[Previous] (net-framework-container-scenarios.md) [Next] (net-container-os-targets.md)</span></span>