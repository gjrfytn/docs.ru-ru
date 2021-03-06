---
title: Отложенные вычисления (F#)
description: 'Узнайте, как F # отложенные вычисления могут повысить производительность приложений и библиотек.'
ms.date: 05/16/2016
ms.openlocfilehash: 1c4eb6ab247c44a04a9d145185e2de7ec01b8e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="lazy-computations"></a>Отложенные вычисления

*Отложенные вычисления* — это вычисления, которые выполняются немедленно, а когда требуется результат. Это может помочь повысить производительность кода.

## <a name="syntax"></a>Синтаксис

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Примечания

В предыдущем синтаксисе *выражение* — код, который вычисляется только в том случае, когда требуется результат и *идентификатор* представляет собой значение, результат сохраняется. Значение имеет тип [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), где фактический тип, используемый для `'T` определяется на основе значения выражения.

Отложенные вычисления позволяют повысить производительность, ограничивая выполнение вычислений только ситуаций, в которых потребуется результат.

Чтобы принудительно выполнить вычисления, вызовите метод `Force`. `Force` вызывает выполнение вычисления только один раз. Последующие вызовы `Force` возвращают же результат, но не выполняется никакой код.

Следующий код иллюстрирует использование отложенного вычисления и использования `Force`. В этом коде тип `result` — `Lazy<int>`и `Force` возвращает `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Отложенные вычисления, но не `Lazy` введите, используется также для последовательностей. Дополнительные сведения см. в разделе [последовательности](sequences.md).

## <a name="see-also"></a>См. также

[Справочник по языку F#](index.md)

[Lazyextensions-модуль](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
