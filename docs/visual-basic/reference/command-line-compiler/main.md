---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51a527dfddd2b78ac1c0559420298a66eb4b63f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652925"
---
# <a name="-main"></a>-main
Określa klasę lub moduł, który zawiera `Sub Main` procedury.  
  
## <a name="syntax"></a>Składnia  
  
```  
-main:location  
```  
  
## <a name="arguments"></a>Argumenty  
 `location`  
 Wymagana. Nazwa klasy lub moduł, który zawiera `Sub Main` procedury wywoływanej po uruchomieniu programu. Może to być w formie **-main: moduł** lub **-main:namespace.module**.  
  
## <a name="remarks"></a>Uwagi  
 Użyj tej opcji, podczas tworzenia pliku wykonywalnego lub program wykonywalny systemu Windows. Jeśli **-głównym** pominięto opcja, kompilator szuka prawidłowej udostępnionych `Sub Main` we wszystkich publicznych klasy i moduły.  
  
 Zobacz [Main procedury w Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) omówienie różne formy `Main` procedury.  
  
 Gdy `location` jest klasa, która dziedziczy <xref:System.Windows.Forms.Form>, kompilator udostępnia domyślny `Main` procedury, która uruchamia aplikację, jeśli nie ma klasy `Main` procedury. Dzięki temu można skompilować kodu w wierszu polecenia, który został utworzony w środowisku programistycznym.  
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>Aby ustawić — główny w programie Visual Studio zintegrowane środowisko programistyczne  
  
1.  Projekt wybrany w **Eksploratora rozwiązań**. Na **projektu** menu, kliknij przycisk **właściwości**.  
  
2.  Kliknij przycisk **aplikacji** kartę.  
  
3.  Upewnij się, że **struktury aplikacji Włącz** nie zaznaczono pola wyboru.  
  
4.  Zmodyfikuj wartość w **obiekt uruchomieniowy** pole.  
  
## <a name="example"></a>Przykład  
 Poniższy kod kompiluje `T2.vb` i `T3.vb`, określania który `Sub Main` procedury zostaną znalezione w `Test2` klasy.  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Kompilator w wierszu polecenia programu Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-docelowego (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Procedura główna w Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
