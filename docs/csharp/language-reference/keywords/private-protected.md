---
title: prywatne chronione (odwołanie w C#)
ms.date: 11/15/2017
author: sputier
ms.openlocfilehash: 0d511f55f44511590fbe92a98cef118e0cb482e2
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34457254"
---
# <a name="private-protected-c-reference"></a>prywatne chronione (odwołanie w C#)
`private protected` Kombinacja słów kluczowych jest modyfikator dostępu elementu członkowskiego. Prywatny chroniony element członkowski jest dostępny przez typy pochodzące z zawierający klasy, ale tylko w obrębie zawierający go zestaw. Porównanie `private protected` z innych modyfikatorów dostępu, zobacz [poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md). 

> [!NOTE]
> `private protected` Modyfikator dostępu jest nieprawidłowy w języku C# wersji 7.2 lub nowszej.
   
## <a name="example"></a>Przykład  
 Prywatny chroniony element członkowski klasy podstawowej jest dostępny z typów pochodnych w zawierający go zestaw, tylko wtedy, gdy statycznych typu zmiennej typu klasy pochodnej. Rozważmy na przykład następujący segment kodu:  
  
 ```csharp
 // Assembly1.cs  
 // Compile with: /target:library  
 public class BaseClass
 {
     private protected int myValue = 0;
 }
 
 public class DerivedClass1 : BaseClass
 {
     void Access()
     {
         BaseClass baseObject = new BaseClass();
 
         // Error CS1540, because myValue can only be accessed by
         // classes derived from BaseClass.
         // baseObject.myValue = 5;  
 
         // OK, accessed through the current derived class instance
         myValue = 5;
     }
 }
```  
  
```csharp  
 // Assembly2.cs  
 // Compile with: /reference:Assembly1.dll  
 class DerivedClass2 : BaseClass
 {
     void Access()
     {
         // Error CS0122, because myValue can only be
         // accessed by types in Assembly1
         // myValue = 10;
     }
 }
```  
 Ten przykład zawiera dwa pliki `Assembly1.cs` i `Assembly2.cs`. Pierwszy plik zawiera klasę podstawową publicznego `BaseClass`i typu pochodnego w `DerivedClass1`. `BaseClass` właścicielem prywatny chroniony element członkowski, `myValue`, który `DerivedClass1` próbuje uzyskać dostęp na dwa sposoby. Pierwsza próba uzyskania dostępu `myValue` za pośrednictwem wystąpienia `BaseClass` spowoduje błąd. Jednak próba używać go jako dziedziczonego elementu członkowskiego w `DerivedClass1` powiedzie się.
W drugim pliku, próba uzyskania dostępu do `myValue` jako dziedziczonego elementu członkowskiego z `DerivedClass2` spowoduje błąd, są one dostępne przez typy pochodne w zestaw1 wyłącznie. 

 Członkowie struktury nie mogą być `private protected` ponieważ struktury nie może być dziedziczona.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)   
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)   
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)   
 [Modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md)   
 [Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md)   
 [Modyfikatory](../../../csharp/language-reference/keywords/modifiers.md)   
 [Publiczna](../../../csharp/language-reference/keywords/public.md)   
 [Prywatne](../../../csharp/language-reference/keywords/private.md)   
 [wewnętrzny](../../../csharp/language-reference/keywords/internal.md)   
 [Problemy z zabezpieczeniami dla wewnętrznego wirtualnego słowa kluczowe](https://msdn.microsoft.com/library/heyd8kky(v=vs.110))
