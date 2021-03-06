---
title: 'Konfigurowanie projektów (F #)'
description: 'Dowiedz się, jak podczas pracy z projektów F # w programie Visual Studio za pomocą projektanta projektu.'
ms.date: 05/16/2016
ms.openlocfilehash: a6c9539945bbd32748ffca1434c984402bc3f17b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="configuring-projects-in-visual-studio"></a>Konfigurowanie projektów programu Visual Studio

> [!NOTE]
W tym artykule nie jest aktualny najnowsze Visual Studio.  Zostaną zaktualizowane.

Ten temat zawiera informacje o sposobie używania **projektanta projektu** podczas pracy z projektów F #. Korzystanie z projektów F # nie jest znacznie różni się od Praca z projektami Visual Basic lub C#. Dokumentacja ogólna projektu programu Visual Studio można użyć jako odwołanie do podstawowej często, korzystając z języka F #. W tym temacie zawiera linki do odpowiednich informacji w dokumentacji programu Visual Studio dla ustawień, które są współużytkowane z innymi językami Visual Studio, a także opisano ustawienia specyficzne dla języka F #.

## <a name="project-designer"></a>Projektant projektu
**Projektanta projektu** użytkowania ogólne są opisane w temacie w pełni [wprowadzenie do projektanta projektu](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7) w dokumentacji programu Visual Studio. **Projektanta projektu** składa się z wielu stronach w rozbiciu na funkcje. Strony dostępne dla projektów języka F # są przeważnie podzbiór tych, które są dostępne dla innych języków. W poniższej tabeli opisano stron obsługiwane w F #. Stron, które nie są dostępne odnoszą się do funkcji, które nie są dostępne w języku F #, lub które są dostępne tylko w wyniku zmiany opcji wiersza polecenia. Stron, które są dostępne w języku F # przypominać najlepiej, stron C#, więc zostanie podane łącze do odpowiednich C# **projektanta projektu** strony.

|Strony projektanta projektu|Linki pokrewne|Opis|
|---------------------|-------------|-----------|
|`Application`|[Strona aplikacji, Projektant projektu &#40;C&#35;&#41;](https://msdn.microsoft.com/library/ms247046.aspx)|Można określić ustawienia na poziomie aplikacji i właściwości, takich jak czy tworzenie biblioteki lub pliku wykonywalnego, jakiej wersji programu .NET Framework jest element docelowy aplikacji i informacje o którym zasobu pliki aplikacji używane są przechowywane.|
|`Build`|[Strona kompilacji, Projektant projektu &#40;C&#35;&#41;](https://msdn.microsoft.com/library/kb4wyys2.aspx)|Umożliwia kontrolowanie sposobu kompilowania kodu.|
|`Build Events`|[Strona zdarzenia kompilacji, Projektant projektu &#40;C&#35;&#41;](https://msdn.microsoft.com/library/kb4wyys2.aspx)|Można określić polecenie do uruchomienia przed lub po kompilacji.|
|`Debug`|[Strona debugowania, Projektant projektu](https://msdn.microsoft.com/library/2wcdezs5.aspx)|Umożliwia sterowanie, jak aplikacja zostanie uruchomiona podczas debugowania. Obejmuje to co wiersza polecenia oraz katalog początkowy aplikacji jest i specjalne debugowania tryby, które chcesz włączyć, takich jak SQL i kodu natywnego.|
|`Reference Paths`|[Zarządzanie odwołaniami w projekcie](/visualstudio/ide/managing-references-in-a-project)|Pozwala określić, gdzie do wyszukiwania zestawów, która zależy od kodu.|

## <a name="f-specific-settings"></a>F #-określonych ustawień
Poniższa tabela zawiera podsumowanie ustawień, które są specyficzne dla języka F #:

|Strony projektanta projektu|Ustawienie|Opis|
|---------------------|-------|-----------|
|`Build`|`Generate tail calls`|Jeśli zaznaczone, umożliwia użycie tail instrukcji języka pośredniego (MSIL) firmy Microsoft. Powoduje to, że ramka stosu zostanie ponownie tail funkcji cyklicznej. Odpowiednikiem `--tailcalls` — opcja kompilatora.|
|`Build`|`Other flags`|Umożliwia określenie kompilatora dodatkowe opcje wiersza polecenia.|

## <a name="see-also"></a>Zobacz też
 [Rozpoczynanie pracy z F # w programie Visual Studio](../get-started/get-started-visual-studio.md)  
 [Opcje kompilatora](../language-reference/compiler-options.md)  
 [Wprowadzenie do projektanta projektu](https://msdn.microsoft.com/library/898dd854-c98d-430c-ba1b-a913ce3c73d7(v=vs.100))
