---
title: Реализация повторных попыток с экспоненциальной выдержкой
description: Архитектура микрослужб .NET для контейнерных приложений .NET | Реализация повторных попыток с экспоненциальной выдержкой
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 7f909c6f81abce80bfdf118112271f1f87254793
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-retries-with-exponential-backoff"></a>Реализация повторных попыток с экспоненциальной выдержкой

[*Повторные попытки с экспоненциальной выдержкой*](https://docs.microsoft.com/azure/architecture/patterns/retry) — это метод, который пытается повторить операцию с экспоненциально растущим временем ожидания, пока не будет достигнуто максимальное число повторных попыток ([экспоненциальная выдержка](https://en.wikipedia.org/wiki/Exponential_backoff)). Этот метод учитывает тот факт, что облачные ресурсы могут быть периодически недоступны в течение нескольких секунд по различным причинам. Например, оркестратор может перемещать контейнер на другой узел в кластере для балансировки нагрузки. В течение этого времени некоторые запросы могут завершиться с ошибкой. Другой пример — база данных, например база данных SQL Azure. В этом случае база данных может перемещаться на другой сервер для балансировки нагрузки. Во время этого перемещения она может быть недоступна в течение нескольких секунд.

Существует множество подходов для реализации логики повторных попыток с экспоненциальной выдержкой.


>[!div class="step-by-step"]
[Назад] (partial-failure-strategies.md) [Далее] (implement-resilient-entity-framework-core-sql-connections.md)
