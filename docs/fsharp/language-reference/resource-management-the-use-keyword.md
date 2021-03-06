---
title: 'Управление ресурсами: ключевое слово use (F#)'
description: 'Дополнительные сведения о F # ключевое слово «use» и «использование» функции, который может управлять инициализацией и освобождением ресурсов.'
ms.date: 05/16/2016
ms.openlocfilehash: c75783080d1d87c6ee75aede500d3d0b3fdf8355
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="resource-management-the-use-keyword"></a>Управление ресурсами: ключевое слово use

В этом разделе описывается ключевое слово `use` и `using` функции, которые позволяют управлять инициализацией и освобождением ресурсов.

## <a name="resources"></a>Ресурсы
Термин *ресурсов* используется более чем одним способом. Да, ресурсы могут быть данные, которые приложение использует, такие как строки, графики и т. д, но в этом контексте *ресурсов* содержатся ссылки на ресурсы операционной системы или программного обеспечения, такие как контексты графических устройств, дескрипторы файлов, сети и базы данных, подключения, параллельных объектов, таких как дескрипторы ожидания и т. д. Использование этих ресурсов приложениями подразумевает получение ресурса от операционной системы или другого поставщика ресурсов, за которым следует более поздней версии ресурса в пул, чтобы его можно предоставить другому приложению. Проблемы возникают, если приложения не выводят ресурсы обратно в пуле.

## <a name="managing-resources"></a>Управление ресурсами
Для эффективного и ответственного управления ресурсами в приложении необходимо освобождать ресурсы, своевременно и предсказуемым образом. .NET Framework помогает сделать это, предоставляя `System.IDisposable` интерфейса. Тип, реализующий `System.IDisposable` имеет `System.IDisposable.Dispose` метод, который правильно освобождает ресурсы. Грамотно сконструированные приложения обеспечивают `System.IDisposable.Dispose` немедленно вызывается, когда любой объект, который содержит ограниченным ресурсом больше не нужен. К счастью большинство языков .NET предоставляют поддержки, чтобы облегчить эту задачу, а F # не является исключением. Существует две полезные языковые конструкции, которые поддерживают шаблон dispose: `use` привязки и `using` функции.

## <a name="use-binding"></a>Использование привязки
`use` Ключевое слово имеет форму напоминает `let` привязки:

Используйте *значение* = *выражение*

Он предоставляет те же функциональные возможности, как `let` привязки, но добавляет вызов `Dispose` для значения, если значение выходит за пределы области. Обратите внимание, что компилятор вставляет проверку значения на null, поэтому, если значение равно `null`, вызов `Dispose` не выполняется.

В следующем примере показано, как автоматически закрывать файл с помощью `use` ключевое слово.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6301.fs)]

>[!NOTE]
Можно использовать `use` в вычислительных выражениях в этом случае настроенную версию `use` используется выражение. Дополнительные сведения см. в разделе [последовательности](sequences.md), [асинхронные рабочие потоки](asynchronous-workflows.md), и [вычислительных выражениях](computation-expressions.md).


## <a name="using-function"></a>с помощью функции
`using` Функция имеет следующий вид:

`using` (*expression1*) *функции или лямбда*

В `using` выражение, *expression1* создает объект, который должен быть удален. Результат *expression1* (объект, который необходимо освободить) становится аргумент *значение*в *функции или лямбда*, который является либо функцию, ожидающую один оставшийся аргумент типа, который соответствует значению, полученных при *expression1*, или лямбда-выражение, которое ожидает аргумент этого типа. В конце выполнения функции среда выполнения вызывает `Dispose` и освобождает ресурсы (пока значение `null`, в этом случае попытка вызова Dispose не предпринимается).

В следующем примере демонстрируется `using` выражение с лямбда-выражением.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6302.fs)]

В следующем примере показано `using` выражение с функцией.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6303.fs)]

Обратите внимание, что функция может быть функцией, которая уже применены некоторые аргументы. Это действие представлено в следующем примере кода: Он создает файл, содержащий строку `XYZ`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet6304.fs)]

`using` Функции и `use` привязки — практически эквивалентные способы решения и то же. `using` Ключевое слово предоставляет больший контроль над тем, когда `Dispose` вызывается. При использовании `using`, `Dispose` вызывается в конце функции или лямбда-выражения; при использовании `use` ключевое слово, `Dispose` вызывается в конце содержащего его блока кода. В общем случае лучше использовать `use` вместо `using` функции.


## <a name="see-also"></a>См. также
[Справочник по языку F#](index.md)
