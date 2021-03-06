---
title: 'Fixed — słowo kluczowe (F #)'
description: 'Dowiedz się, jak można "przypiąć" lokalnie na stosie zapobiegające kolekcji F # "fixed" — słowo kluczowe.'
ms.date: 04/24/2017
ms.openlocfilehash: 913ee4d7b0f6b2437793d4788e53556d6be6c4db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563879"
---
# <a name="the-fixed-keyword"></a>Fixed — słowo kluczowe

F # 4.1 wprowadza `fixed` — słowo kluczowe, dzięki czemu można "numer pin" lokalnej na stosie, aby zapobiec jej zebrane lub przenieść podczas wyrzucania elementów bezużytecznych.  Jest używany dla niskiego poziomu scenariuszy programowania.

## <a name="syntax"></a>Składnia

```fsharp
use ptr = fixed expression
```

## <a name="remarks"></a>Uwagi

Spowoduje to rozszerzenie składni wyrażeń umożliwia wyodrębnianie wskaźnik i powiązania jej nazwę, który uniemożliwił zebrane lub przenieść podczas wyrzucania elementów bezużytecznych.  

Wskaźnik z wyrażenia został rozwiązany za pomocą `fixed` — słowo kluczowe jest powiązana z identyfikatorem za pośrednictwem `use` — słowo kluczowe.  Semantyka tego są podobne do zarządzania zasobami za pośrednictwem `use` — słowo kluczowe.  Wskaźnik myszy zostanie rozwiązany, gdy znajduje się w zakresie, a po jest spoza zakresu, nie zostanie rozwiązany.  `fixed` Nie można użyć poza kontekstem `use` powiązania.  Wskaźnik musi powiązać nazwę zawierającą `use`.

Użycie `fixed` musi wystąpić w wyrażeniu w funkcji lub metody.  Nie można używać w zakresie poziomu skryptów lub poziom modułu.

Podobnie jak cały kod wskaźnika jest niebezpieczne feature i będzie emitować ostrzeżenia, gdy jest używany.

## <a name="example"></a>Przykład

```fsharp
open Microsoft.FSharp.NativeInterop

type Point = { mutable X: int; mutable Y: int}

let squareWithPointer (p: nativeptr<int>) =
    // Dereference the pointer at the 0th address.
    let mutable value = NativePtr.get p 0

    // Perform some work
    value <- value * value

    // Set the value in the pointer at the 0th address.
    NativePtr.set p 0 value

let pnt = { X = 1; Y = 2 }
printfn "pnt before - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 2

// Note that the use of 'fixed' is inside a function.
// You cannot fix a pointer at a script-level or module-level scope.
let doPointerWork() =
    use ptr = fixed &pnt.Y

    // Square the Y value
    squareWithPointer ptr
    printfn "pnt after - X: %d Y: %d" pnt.X pnt.Y // prints 1 and 4

doPointerWork()
```

## <a name="see-also"></a>Zobacz też

[Nativeptr — moduł](https://msdn.microsoft.com/visualfsharpdocs/conceptual/nativeinterop.nativeptr-module-%5Bfsharp%5D)
