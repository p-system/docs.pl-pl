---
title: Przyjazne zestawy (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 9b3d5716-e6e4-47a7-a3e9-084d7fba5c28
ms.openlocfilehash: 91bc33f33c4fc34c6e0f3ae197ecd2b876161de3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33644384"
---
# <a name="friend-assemblies-visual-basic"></a>Przyjazne zestawy (Visual Basic)
A *przyjaznego zestawu* jest zestawie, do którego mogą uzyskać dostęp do innego zestawu [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) typy i składniki. Po zidentyfikowaniu zestawu jako zestawu friend, masz już Oznacz typy i składniki jako public je, aby były dostępne dla innych zestawów. Jest to szczególnie wygodne w następujących scenariuszach:  
  
-   Podczas przeprowadzania testów jednostkowych, po uruchomieniu testu kodu osobny zestaw, ponieważ wymaga dostępu do elementów członkowskich w zestawie testowane oznaczonych jako `Friend`.  
  
-   Podczas tworzenia biblioteki klas i ma zostać dodany do biblioteki są zawarte w oddzielne zestawy, ale wymagają dostępu do elementów członkowskich w istniejących zestawów, które są oznaczone jako `Friend`.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu, aby zidentyfikować jeden lub więcej zestawów przyjazne dla danego zestawu. W poniższym przykładzie użyto <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut w zestawie A i zestawu Określa `AssemblyB` jako przyjaznego zestawu. Dzięki temu zestawu `AssemblyB` dostęp do wszystkich typów i członków w zestawie, które są oznaczone jako `Friend`.  
  
> [!NOTE]
>  Podczas kompilowania zestawu (zestawu `AssemblyB`) będzie uzyskiwać dostęp wewnętrzne typy lub wewnętrzne elementy członkowskie z innego zestawu (zestawu *A*), należy jawnie określić nazwę pliku wyjściowego (.exe lub .dll) przy użyciu **/out** — opcja kompilatora. Jest to wymagane, ponieważ kompilator nie ma jeszcze wygenerowany nazwę zestawu, w którym jest ona tworzenie w czasie, który jest wiązany odwołań zewnętrznych. Aby uzyskać więcej informacji, zobacz [/out (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/out.md).  
  
```vb  
Imports System.Runtime.CompilerServices  
Imports System  
<Assembly: InternalsVisibleTo("AssemblyB")>   
  
' Friend class.  
Friend Class FriendClass  
    Public Sub Test()  
        Console.WriteLine("Sample Class")  
    End Sub  
End Class  
  
' Public class with a Friend method.  
Public Class ClassWithFriendMethod  
    Friend Sub Test()  
        Console.WriteLine("Sample Method")  
    End Sub  
End Class  
```  
  
 Tylko zestawy, które zostaną jawnie określone jako znajomych mogą uzyskiwać dostęp do `Friend` typy i składniki. Na przykład, jeśli zestaw B jest przyjaznego zestawu A i zestawu odwołania do zestawu C B, C nie ma dostępu do `Friend` typów w A.  
  
 Kompilator wykonuje pewne podstawowe sprawdzanie poprawności nazwy przyjaznego zestawu przekazany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybutu. Jeśli zestaw *A* deklaruje *B* jako przyjaznego zestawu reguł sprawdzania poprawności, są następujące:  
  
-   Jeśli zestaw *A* jest silną nazwę zestawu *B* musi również być silnej nazwy. Nazwy przyjaznego zestawu, który jest przekazywany do atrybutu musi zawierać nazwę zestawu i klucz publiczny klucz silnej nazwy, który jest używany do podpisywania zestawu *B*.  
  
     Nazwy przyjaznego zestawu, który jest przekazywany do <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute> atrybut nie może być silnej nazwy zestawu *B*: nie ma zestawu wersji, kultury, architektury lub token klucza publicznego.  
  
-   Jeśli zestaw *A* nie jest silnej nazwie, nazwy przyjaznego zestawu powinien zawierać tylko nazwę zestawu. Aby uzyskać więcej informacji, zobacz [porady: tworzenie niepodpisanych przyjazne zestawy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md).  
  
-   Jeśli zestaw *B* jest silnej nazwie, należy określić klucz silnej nazwy zestawu *B* za pomocą ustawienie projektu lub wiersza polecenia `/keyfile` — opcja kompilatora. Aby uzyskać więcej informacji, zobacz [porady: tworzenie podpisanego przyjazne zestawy (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md).  
  
 <xref:System.Security.Permissions.StrongNameIdentityPermission> Klasa udostępnia także możliwość udostępniania typów, z następującymi różnicami:  
  
-   <xref:System.Security.Permissions.StrongNameIdentityPermission> dotyczy poszczególnych typu przyjaznego zestawu dotyczy całego zestawu.  
  
-   Jeśli istnieją setki typów w zestawie *A* , który ma zostać udostępniona w zestawie *B*, należy dodać <xref:System.Security.Permissions.StrongNameIdentityPermission> do wszystkich z nich. Jeśli używasz przyjaznego zestawu, wystarczy raz zadeklarować relacji friend.  
  
-   Jeśli używasz <xref:System.Security.Permissions.StrongNameIdentityPermission>, typów, aby udostępnić musi być zadeklarowana jako publiczną. Jeśli używasz przyjaznego zestawu udostępnionego typy są deklarowane jako `Friend`.  
  
 Informacje na temat dostępu zestawu `Friend` typy i metody z pliku modułu (plik z rozszerzeniem modułu .netmodule), zobacz [/moduleassemblyname (Visual Basic)](../../../../visual-basic/reference/command-line-compiler/moduleassemblyname.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.CompilerServices.InternalsVisibleToAttribute>  
 <xref:System.Security.Permissions.StrongNameIdentityPermission>  
 [Porady: tworzenie nieoznaczonych przyjaznych zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-unsigned-friend-assemblies.md)  
 [Porady: tworzenie oznaczonych przyjaznych zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/how-to-create-signed-friend-assemblies.md)  
 [Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)](../../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Pojęcia związane z programowaniem](../../../../visual-basic/programming-guide/concepts/index.md)
