---
title: Массивы в Visual Basic
ms.date: 12/06/2017
f1_keywords:
- vb.Array
helpviewer_keywords:
- arrays [Visual Basic]
- Visual Basic, arrays
ms.assetid: dbf29737-b589-4443-bee6-a27588d9c67e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b6c1db0131f2a150dc1b00dd5e6dafc3a418f05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="arrays-in-visual-basic"></a>Массивы в Visual Basic
Массив — это набор значений, которые называются *элементы*, логически связанных друг с другом. Например массив может состоять из число учеников в каждом классе школы; Каждый элемент массива представляет число учеников в одном классе. Аналогичным образом массив может состоять из Стьюдента оценок для класса; Каждый элемент массива представляет один уровень.    

Это возможно отдельные переменные для хранения всех элементов данных. Например, если наше приложение анализирует оценок учащихся, мы используем отдельной переменной для Оценка каждого учащегося, таких как `englishGrade1`, `englishGrade2`и т. д. Такой подход имеет три основные ограничения:
- У нас есть известны во время разработки, точно сколько оценок, нам нужно обработать.
- Обработка большого количества уровней быстро становится громоздким. Это в свою очередь, делает более вероятно, окажет серьезных ошибок приложения.
- Трудно поддерживать. Каждый новый уровень, мы добавим требует, что приложение будет изменен, повторной компиляции и повторного развертывания.  
 
 С помощью массива, можно ссылаться на эти связанные значения с тем же именем и использовать это число, которое называется *индекс* или *индекс* для идентификации отдельного элемента по его позиции в массиве. Индексы массива в диапазоне от 0 до величины, чем общее число элементов в массиве. При использовании Visual Basic синтаксис для определения размера массива указываются наибольшего индекса, не общее число элементов в массиве. Можно работать с массивом как единое целое, и возможность прохода его элементы избавляет от необходимости знать точно сколько элементов во время разработки.
  
 Несколько простых примеров перед подробным описанием:  
  
```vb  
' Declare a single-dimension array of 5 numbers.  
Dim numbers(4) As Integer   
  
'Declare a single-dimension array and set its 4 values.  
Dim numbers = New Integer() {1, 2, 4, 8}  
  
' Change the size of an existing array to 16 elements and retain the current values.
ReDim Preserve numbers(15)
  
' Redefine the size of an existing array and reset the values.
ReDim numbers(15)  
  
' Declare a 6 x 6 multidimensional array.
Dim matrix(5, 5) As Double  
  
' Declare a 4 x 3 multidimensional array and set array element values.  
Dim matrix = New Integer(3, 2) {{1, 2, 3}, {2, 3, 4}, {3, 4, 5}, {4, 5, 6}}  
  
' Declare a jagged array  
Dim sales()() As Double = New Double(11)() {}  
```  
  
 ## <a name="in-this-article"></a>Содержание этой статьи
  
- [Элементы массива простого массива](#array-elements-in-a-simple-array)  
  
- [Создание массива](#creating-an-array)  
  
- [Хранение значений в массиве](#storing-values-in-an-array)  
  
- [Заполнение массива с помощью литералов массива](#populating-an-array-with-array-literals)  
  
- [Перебор массива](#iterating-through-an-array)  
  
- [Размер массива](#BKMK_ArraySize)  

- [Тип массива](#the-array-type)  
  
- [Массивы как возвращаемые значения и параметры](#arrays-as-return-values-and-parameters)  
- [Массивы массивов](#jagged-arrays)  
  
- [Массивы с нулевой длиной](#zero-length-arrays)  

- [Разделение массив](#splitting-an-array)
  
- [Коллекции как альтернатива массивам](#collections-as-an-alternative-to-arrays)  
  
##  <a name="array-elements-in-a-simple-array"></a>Элементы массива простого массива  

Давайте создадим массив с именем `students` для хранения числа учеников в каждом классе школы. Индексы элементов находятся в диапазоне от 0 до 6. Используя этот массив проще, чем объявлять семь отдельных переменных.

На следующем рисунке показана `students` массива. Для каждого элемента массива:  
  
-   индекс элемента представляет школьный класс (индекс 0 представляет детский сад);
  
-   значение, содержащееся в элементе, представляет число учеников в этом классе.
  
 ![Изображение массива, где показано количество учеников](../../../../visual-basic/programming-guide/language-features/arrays/media/arrayexampleschool.gif "ArrayExampleSchool")  
Элементы массива students  
 
В следующем примере содержится код Visual Basic, который создает и использует массива:

 [!code-vb[simple-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/simple-array.vb)]  

Пример выполняет три действия:

- Он объявляет `students` массив с 7 элементов. Число `6` в массиве указывает на последний индекс в массиве; это один меньше, чем число элементов в массиве.
- Он назначает значения каждого элемента в массиве. Элементы массива осуществляется с помощью имени массива, включая индекс отдельный элемент в круглые скобки.
- В нем перечислены каждого значения массива. В этом примере [ `For` ](../../../language-reference/statements/for-next-statement.md) инструкцию, чтобы доступ к каждому элементу массива по номеру индекса.
  
 `students` Массива в предыдущем примере используется одномерный массив, так как он использует один индекс. Массив, использующий более одного индекса называется *многомерные*. Дополнительные сведения см. в оставшейся части этой статьи и [размерности массивов в Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md).  
  
##  <a name="creating-an-array"></a>Создание массива  
 
Размер массива можно определить несколькими способами: 

- Можно указать размер при объявлении массива:
  
    [!code-vb[creating1](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#1)]  
  
 - Можно использовать `New` предложений, чтобы указать размер массива при его создании:  
  
    [!code-vb[creating2](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#2)]  
  
 При наличии существующего массива, его размер можно переопределить с помощью [ `Redim` ](../../../../visual-basic/language-reference/statements/redim-statement.md) инструкции. Можно указать, что `Redim` инструкции сохранить значения, которые находятся в массиве, или можно указать, создать пустой массив. В приведенном ниже примере показаны различные варианты использования оператора `Redim` для изменения размера существующего массива.  
  
 [!code-vb[redimensioning](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#3)]  
  
 Дополнительные сведения см. в разделе [оператор ReDim](../../../../visual-basic/language-reference/statements/redim-statement.md).  
  
##  <a name="storing-values-in-an-array"></a>Сохранение значений в массиве
 
 К любой позиции в массиве можно получить доступ, используя индекс типа `Integer`. Вы можете сохранять и извлекать значения массива, ссылаясь на позицию в нем с помощью индекса, заключенного в скобки. Индексы для многомерных массивов разделяются запятыми (,). Для каждого измерения массива требуется один индекс. 

Приведенный ниже показаны некоторые операторы, которые хранят и извлекают значения в массивах.
  
 [!code-vb[store-and-retrieve](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/store-and-retrieve.vb)]  
  
## <a name="populating-an-array-with-array-literals"></a>Заполнение массива с помощью литералов массива
 С помощью литерала массива, в то же время ее создании можно заполнить массив с начальным набором значений. Литерал массива состоит из списка разделенных запятыми значений, заключенных в фигурные скобки (`{}`).  
  
 При создании массива с помощью литерала массива можно либо указать тип массива, либо использовать определение типа для задания типа массива. В следующем примере показано, как параметры.  
  
 [!code-vb[create-with-literals](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#4)]  
  
 При использовании определения типа тип массива определяется *главным типом* в список литеральных значений. Главный тип — тип, до которого могут быть расширены все другие типы массива. Если такой уникальный тип нельзя определить, то главным будет тип, до которого можно сузить все другие типы массива. Если ни один из указанных уникальных типов нельзя определить, главным типом будет `Object`. Например, если список значений для литерала массива содержит значения типов `Integer`, `Long`и `Double`, результирующий массив будет иметь тип `Double`. Поскольку `Integer` и `Long` расширяются только до `Double`, `Double` является главным типом. Для получения дополнительной информации см. [Widening and Narrowing Conversions](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md). 
 
> [!NOTE] 
> Вывод типа можно использовать только для массивов, которые определены как локальные переменные в члена типа. Если отсутствует определение явный тип, массивов, определенных с помощью литералов массива на уровне класса имеют тип `Object[]`. Дополнительные сведения см. в разделе [вывод локального типа](../variables/local-type-inference.md). 

Обратите внимание, что в предыдущем примере определяется `values` как массив объектов типа `Double` несмотря на всех литералов массива типа `Integer`. Вы можете создать этот массив, поскольку значения литерала массива можно расширить до `Double` значения. 
  
 Можно также создать и заполнить многомерного массива с помощью *вложенные литералы массива*. Вложенные литералы массива должны иметь несколько измерений, результирующему массиву. В следующем примере создается двухмерный массив целых чисел с помощью вложенных литералов массива.  
  
 [!code-vb[nested-array-literals](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#5)]  
  
При использовании вложенных литералов массива для создания и заполнения массива, возникает ошибка, если количество элементов в вложенных литералах массива не совпадают. Ошибка также возникает в том случае, если явно объявляется переменная массива с разным числом измерений, чем литералы массива. 
  
Так же, как для одномерных массивов, можно полагаться на определение типа при создании многомерного массива с помощью вложенных литералов массива. Выводимый тип является главным типом для всех значений всех литералов массива все уровень вложенности. В следующем примере создается двухмерный массив типа `Double[,]` из значения, которые относятся к типу `Integer` и `Double`.  
  
 [!code-vb[nested-type-inference](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/create-array.vb#6)]  
  
 Дополнительные примеры можно найти в статье [How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md) (Практическое руководство. Инициализация переменной массива в Visual Basic).  
  
##  <a name="iterating-through-an-array"></a>Перебор массива  
 При итерации по массиву доступа каждого элемента в массиве от наименьшего индекса и заканчивая самым верхним или от самого высокого до самого низкого уровня. Как правило, использования либо [для... Следующий оператор](../../../../visual-basic/language-reference/statements/for-next-statement.md) или [For Each... Следующий оператор](../../../../visual-basic/language-reference/statements/for-each-next-statement.md) для перебора элементов в массиве. Если вы не знаете верхней границы массива, можно вызвать <xref:System.Array.GetUpperBound%2A?displayProperty=nameWithType> метод, чтобы получить наибольшее значение индекса. Несмотря на то, что почти является наименьшее значение индекса всегда равно 0, можно вызвать <xref:System.Array.GetLowerBound%2A?displayProperty=nameWithType> метод, чтобы получить наименьшее значение индекса.   
  
 Следующий пример перебор одномерного массива с помощью [ `For...Next` ](../../../../visual-basic/language-reference/statements/for-next-statement.md) инструкции. 
  
 [!code-vb[iterate-one-dimensional-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate1d.vb)]  
  
 Следующий пример перебор многомерного массива с помощью [ `For...Next` ](../../../../visual-basic/language-reference/statements/for-next-statement.md) инструкции. Метод <xref:System.Array.GetUpperBound%2A> имеет параметр, который определяет измерение. `GetUpperBound(0)` Возвращает наибольший индекс первого измерения и `GetUpperBound(1)` Возвращает наибольший индекс второго измерения.
  
 [!code-vb[iterate-two-dimensional-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate2d.vb)]  
  
 В следующем примере используется [For Each... Следующий оператор](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)для перечисления элементов одномерного массива и двумерным массивом.  
  
 [!code-vb[iterate-for-each-next](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/iterate-for-each-next.vb)]  
  
## <a name="array-size"></a>Размер массива  

 Размер массива является произведением длин всех его измерений. Он представляет собой общее число элементов, в данный момент содержащихся в массиве.  Например в следующем примере объявляется двухмерного массива с четырьмя элементами в каждом измерении. Как показывают выходные данные примера, размер массива равен 16 (или (3 + 1) * (3 + 1).

 [!code-vb[array-size](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size.vb)]  

> [!NOTE] 
> В этом описании размер массива не применяется к массивы массивов. Сведения о массивов массивов и определения размера массива массивов см [ступенчатые массивы](#jagged-arrays) раздела.
  
  Размер массива можно определить с помощью свойства <xref:System.Array.Length%2A?displayProperty=nameWithType>. Длина каждого измерения многомерного массива можно найти с помощью <xref:System.Array.GetLength%2A?displayProperty=nameWithType> метод.  
  
 Можно изменять размер переменной массива, назначив ей новый объект массива, к нему или с помощью [ `ReDim` инструкции](../../../../visual-basic/language-reference/statements/redim-statement.md) инструкции. В следующем примере используется `ReDim` инструкцию, чтобы сделать 51-элементного массива массив из 100 элементов.

 [!code-vb[resize-an-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-size2.vb)]  
  
 Существует ряд особенностей, о которых следует помнить при работе с размером массива.  
  
|||  
|---|---|  
|Длина измерения|Индекс каждого измерения начинается с 0, что означает, что он диапазоне от 0 до верхней границы. Таким образом длина данного измерения равна 1 больше его объявленной верхней границы этого измерения.|  
|Ограничения длины|Длина каждого измерения массива ограничена максимальным значением `Integer` тип данных, который является <xref:System.Int32.MaxValue?displayProperty=nameWithType> или (2 ^ 31) - 1. Однако общий размер массива также ограничен доступной памятью в системе. При попытке инициализировать массив, размер которого превышает объем доступной памяти, среда выполнения создает <xref:System.OutOfMemoryException>.|  
|Размер и размер элемента|Размер массива не зависит от типа его элементов. Размер всегда представляет общее число элементов, а не количество байтов, которые они занимают в памяти.|  
|Затраты памяти|Небезопасно делать какие-либо предположения относительно способа хранения массива в памяти. Хранение зависит от разрядности платформы, поэтому один и тот же массив может занимать больше памяти в 64-разрядных системах, чем в 32-разрядных. В зависимости от конфигурации системы при инициализации массива среда CLR может использовать такие способы хранения, как упаковка элементов максимально близко друг к другу или выравнивание всех элементов по естественным аппаратным границам памяти. Кроме того, массив нуждается в хранении служебной информации, и размер этой информации возрастает при добавлении каждого измерения.|  

## <a name="the-array-type"></a>Тип массива 
 Каждый массив имеет тип данных, который отличается от типа данных его элементов. Не существует единого типа данных, подходящего для всех массивов. Вместо этого тип данных массива определяется числом измерений ( *рангом*) массива и типом данных его элементов. Две переменные массивов имеют те же данные, тип только, когда они имеют одинаковый ранг и их элементы имеют одинаковый тип данных. Длины измерений массива не влияют на тип данных массива.  
  
 Каждый массив наследуется от класса <xref:System.Array?displayProperty=nameWithType>, и вы можете объявить переменную типа `Array`, но не можете создать массив типа `Array`. Например несмотря на то, что в следующем коде объявляется `arr` переменной с типом `Array` и вызывает <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> метод для создания массива, тип массива оказывается Object [].

 [!code-vb[array-class](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-class.vb)] 

Кроме того, [оператор ReDim`Array` не может работать с переменной, объявленной с типом ](../../../../visual-basic/language-reference/statements/redim-statement.md). По этой причине, а также для типизации рекомендуется объявлять каждый массив как конкретный тип.  
  
 Выяснить тип данных массива или его элементов можно несколькими способами. 
  
-   Можно вызвать <xref:System.Object.GetType%2A> метод для переменной, чтобы получить <xref:System.Type> , представляющий тип времени выполнения переменной. Объект <xref:System.Type> содержит подробные сведения в своих свойствах и методах.  
  
-   Можно передать переменную <xref:Microsoft.VisualBasic.Information.TypeName%2A> функцию для получения `String` на имя типа времени выполнения.  
  
 В следующем примере вызывается как `GetType` метод и `TypeName` функцию, чтобы определить тип массива. Тип массива — `Byte(,)`. Обратите внимание, что <xref:System.Type.BaseType%2A?displayProperty=nameWithType> свойство также указывает, что базовый тип массива байтов <xref:System.Array> класса.  
  
 [!code-vb[array-type](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/array-type.vb)]  
  
##  <a name="arrays-as-return-values-and-parameters"></a>Массивы как возвращаемые значения и параметры  
 Чтобы вернуть массив из процедуры `Function`, укажите тип данных массива и число измерений в качестве типа возвращаемого значения [оператора Function](../../../../visual-basic/language-reference/statements/function-statement.md). Внутри функции объявите локальную переменную массива с тем же числом измерений и типом данных. В [оператор Return](../../../../visual-basic/language-reference/statements/return-statement.md) включите локальную переменную массива без скобок.  
  
 Чтобы задать массив в качестве параметра процедуры `Sub` или `Function` , определите параметр как массив с указанными типом данных и количеством измерений. В вызове процедуры передайте переменную массива с того же типа данных и количеством измерений.  
  
 В следующем примере `GetNumbers` возврата функцией `Integer()`, одномерный массив типа `Integer`. Процедура `ShowNumbers` принимает аргумент `Integer()` . 
  
 [!code-vb[return-value-and-params](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params.vb)]  
  
 В следующем примере `GetNumbersMultiDim` возврата функцией `Integer(,)`, двухмерный массив типа `Integer`.  Процедура `ShowNumbersMultiDim` принимает аргумент `Integer(,)` .  
  
 [!code-vb[multidimensional-return-value](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/return-values-and-params-2d.vb)]  
  
## <a name="jagged-arrays"></a>Массивы массивов  
 
Иногда структура данных в приложении является двухмерной, но не прямоугольной. Например может использовать массив для хранения данных о высокой температуре каждый день месяца. Первого измерения массива, представляющее месяц, но второго измерения представляет количество дней и неоднородно количество дней в месяце. Объект *массив массивов*, также называемый *массив массивов*, предназначенный для таких сценариев. Массив массивов — это массив, элементы которого также являются массивами. Массив массивов и каждый элемент в нем могут иметь одно или несколько измерений.  
  
 В следующем примере массив месяцев, каждый элемент которого представляет собой массив дней. В примере используется массив массивов, поскольку в разных месяцах различное число дней.  В примере показано создание массива массивов, присвоения значений и получение и отображение его значения.
  
 [!code-vb[jagged-arrays](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged.vb)]  

Предыдущий пример присваивает значения массива массивов на основе по элементам с помощью `For...Next` цикла. Также можно присваивать значения к элементам массива массивов с помощью вложенных литералов массива. Однако попытка использовать вложенные литералы массива (например, ```Dim valuesjagged = {{1, 2}, {2, 3, 4}}```) создает ошибку компилятора [BC30568](../../../,,/../misc/bc30568.md). Чтобы исправить эту ошибку, заключите внутренние литералы массива в круглые скобки. Круглые скобки заставляют вычисляемое выражение литерала массива, а полученные значения используются со внешним литералом массива, как показано в следующем примере.  
  
 [!code-vb[jagged-array-initialization](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-assign.vb)] 

Массив массивов — одномерный массив, элементы которого содержат массивы. Таким образом <xref:System.Array.Length%2A?displayProperty=nameWithType> свойство и `Array.GetLength(0)` метод возвращает количество элементов в одномерном массиве и `Array.GetLength(1)` вызывает <xref:System.IndexOutOfRangeException> так как не многомерный массив массивов. Определить количество элементов в каждом подмассиве путем получения значения каждого подмассива <xref:System.Array.Length%2A?displayProperty=nameWithType> свойство. В следующем примере для определения количества элементов в массив массивов.

[!code-vb[jagged-array-size](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/jagged-length.vb)] 

## <a name="zero-length-arrays"></a>Массивы с нулевой длиной  
Visual Basic различает неинициализированным массив (массив, значение которого является `Nothing`) и *массив нулевой длины* или пустой массив (массив без элементов.) Массив неинициализированным то, которое не было номерами элементов или все значения назначенного ему его. Пример:

```vb
Dim arr() As String
```
Массив нулевой длины объявлен с измерение -1. Пример:

```vb
Dim arrZ(-1) As String
```
Массив нулевой длины может потребоваться создать в указанных ниже случаях.  
  
-   Без дополнительного <xref:System.NullReferenceException> исключения, код должен обращаться к членам <xref:System.Array> класса, такие как <xref:System.Array.Length%2A> или <xref:System.Array.Rank%2A>, или вызов функции Visual Basic, таких как <xref:Microsoft.VisualBasic.Information.UBound%2A>.  
  
-   Вы хотите сохранить простой, не выполняя проверку для кода `Nothing` как особый случай.  
  
-   Код взаимодействует с интерфейсом API, который требует передачи массива нулевой длины в одну или несколько процедур или возвращает массив нулевой длины из одной или нескольких процедур.

## <a name="splitting-an-array"></a>Разделение массив

В некоторых случаях может потребоваться разбить на несколько массивов в одном массиве. Это включает в себя определение точки или точек, в которых массив является для разбиения, а затем spitting массива в двух или более отдельных массива. 

> [!NOTE] 
> В этом разделе не рассматриваются Разделение одной строки на массив строк, на основе некоторых разделителя. Сведения о разделение строки см. в разделе <xref:System.String.Split%2A?displayProperty=nameWithType> метод.

Приведены наиболее распространенные условия для разделения массив.

- Количество элементов в массиве. Например можно разбить на число приблизительно равные части больше указанного числа элементов массива. Для этой цели можно использовать значение, возвращаемое либо <xref:System.Array.Length%2A?displayProperty=nameWithType> или <xref:System.Array.GetLength%2A?displayProperty=nameWithType> метод.

- Значение элемента, который служит в качестве разделителя, который указывает, где следует разбить массива. Можно выполнить поиск определенного значения путем вызова <xref:System.Array.FindIndex%2A?displayProperty=nameWithType> и <xref:System.Array.FindLastIndex%2A?displayProperty=nameWithType> методы.
 
После определения индекс или индексы, в которых следует разбить массива, затем можно создать отдельные массивы путем вызова <xref:System.Array.Copy%2A?displayProperty=nameWithType> метод. 

В следующем примере массив разбиваются на два массива приблизительно одинакового размера. (Если нечетное число элементов массива, первый массив содержит один элемент больше, чем второй.) 

[!code-vb[splitting-an-array-by-length](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/split1.vb)] 

Следующий пример разделяет массив строк в двух массивов, в зависимости от наличия элемент, значение которого равно «zzz», который служит в качестве разделителя массивов. Новые массивы не включают элемент, содержащий разделитель.

[!code-vb[splitting-an-array-by-delimiter](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/split2.vb)] 

## <a name="joining-arrays"></a>Присоединение массивов

Число массивов, могут быть объединены в один массив большего размера. Чтобы сделать это, можно использовать <xref:System.Array.Copy%2A?displayProperty=nameWithType> метода. 

> [!NOTE] 
> В этом разделе не рассматривается присоединение массив строк в одну строку. Сведения о соединении массив строк см. в разделе <xref:System.String.Join%2A?displayProperty=nameWithType> метод.

Перед копированием элементы каждого массива в новый массив, необходимо сначала убедиться, что при инициализации массива, чтобы оно было достаточно большим, чтобы accompodate нового массива. Это можно сделать одним из двух способов.

- Используйте [ `ReDim Preserve` ](../../../../visual-basic/language-reference/statements/redim-statement.md) инструкцию, чтобы динамически разверните массива, прежде чем добавлять новые элементы к нему. Это самый простой способ, но он может привести к снижению производительности и чрезмерного потребления памяти при копировании больших массивов.
- Общее количество элементов, необходимых для нового большого массива, а затем добавлять к нему элементы каждого массива-источника.

В следующем примере второй подход добавьте четыре массива с десять элементов в одном массиве.  

[!code-vb[joining-an-array](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/join.vb)] 

Поскольку в этом случае исходные массивы все малы, мы также динамически разверните массива как мы добавим элементы каждого нового массива. Эту задачу решает следующий код.

[!code-vb[joining-an-array-dynamically](../../../../../samples/snippets/visualbasic/programming-guide/language-features/arrays/join2.vb)] 

##  <a name="collections-as-an-alternative-to-arrays"></a>Коллекции как альтернатива массивам  
 Массивы удобнее всего использовать для создания фиксированного числа строго типизированных объектов и работы с ними. Коллекции предоставляют более гибкий способ работы с группами объектов. В отличие от массивов, которых требуется явно изменить размер массива с [ `ReDim` инструкции](../../../../visual-basic/language-reference/statements/redim-statement.md), коллекции увеличиваться и уменьшаться динамически при необходимости изменения приложения.  
  
 При использовании `ReDim` для изменения размера массива, Visual Basic создает новый массив и освобождает предыдущий. Это занимает время выполнения. Таким образом Если число элементов при работе изменяется часто или нельзя предсказать максимальное число необходимых элементов, обычно будет получить более высокую производительность с помощью коллекции.  
  
 Некоторые коллекции допускают назначение ключа любому объекту, который добавляется в коллекцию, чтобы в дальнейшем можно было быстро извлечь связанный с ключом объект из коллекции.  
  
 Если коллекция содержит элементы только одного типа данных, можно использовать один из классов в пространстве имен <xref:System.Collections.Generic?displayProperty=nameWithType> . Универсальная коллекция обеспечивает строгую типизацию, так что в нее нельзя добавить другие типы данных.  
  
 Более подробную информацию о коллекциях см. в статье [Коллекции](../../concepts/collections.md).
  
## <a name="related-topics"></a>См. также  
  
|Термин|Определение|  
|----------|----------------|  
|[Array Dimensions in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/array-dimensions.md)|Объяснение ранга и измерений в массиве.|  
|[How to: Initialize an Array Variable in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-initialize-an-array-variable.md) (Практическое руководство. Инициализация переменной массива в Visual Basic)|Описывается заполнение массивов начальными значениями.|  
|[How to: Sort An Array in Visual Basic](../../../../visual-basic/programming-guide/language-features/arrays/how-to-sort-an-array.md) (Практическое руководство. Сортировка массива в Visual Basic)|Показано, как сортировать элементы массива в алфавитном порядке.|  
|[Практическое руководство. Присвоение одного массива другому](../../../../visual-basic/programming-guide/language-features/arrays/how-to-assign-one-array-to-another-array.md)|Описываются правила и действия для присвоения массива другой переменной массива.|  
|[Устранение неполадок, связанных с массивами](../../../../visual-basic/programming-guide/language-features/arrays/troubleshooting-arrays.md)|Рассматриваются некоторые общие проблемы, возникающие при работе с массивами.|  
  
## <a name="see-also"></a>См. также  
 <xref:System.Array?displayProperty=nameWithType>  
 [Оператор Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)  
 [Оператор reDim](../../../../visual-basic/language-reference/statements/redim-statement.md)
