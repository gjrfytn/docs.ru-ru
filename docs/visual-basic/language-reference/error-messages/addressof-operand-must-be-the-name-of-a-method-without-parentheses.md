---
title: '&#39;AddressOf&#39; операнд должен быть именем метода (без скобок)'
ms.date: 07/20/2015
f1_keywords:
- vbc30577
- bc30577
helpviewer_keywords:
- BC30577
ms.assetid: c2c55640-5c61-4e66-97a4-4322020c6001
ms.openlocfilehash: 701d86e03d9b14236eec8436d99ec40cebbbcd44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 05/04/2018
---
# <a name="39addressof39-operand-must-be-the-name-of-a-method-without-parentheses"></a>&#39;AddressOf&#39; операнд должен быть именем метода (без скобок)
Оператор `AddressOf` создает экземпляр делегата процедуры, ссылающийся на конкретную процедуру. Синтаксис выглядит следующим образом.  
  
 `AddressOf` `procedurename`  
  
 Вставить круглые скобки вокруг аргумента `AddressOf`, которые не нужны.  
  
 **Идентификатор ошибки:** BC30577  
  
## <a name="to-correct-this-error"></a>Исправление ошибки  
  
1.  Удалите круглые скобки вокруг аргумента `AddressOf`.  
  
2.  Убедитесь, что аргумент является именем метода.  
  
## <a name="see-also"></a>См. также  
 [Оператор AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Делегаты](../../../visual-basic/programming-guide/language-features/delegates/index.md)
