---
title: Operacje asynchroniczne
ms.date: 03/30/2017
ms.assetid: e7d32c3c-bf78-4bfc-a357-c9e82e4a4b3c
ms.openlocfilehash: 97564600f6f4fb9d4990398527dd2e45fcb9f015
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33352982"
---
# <a name="asynchronous-operations"></a>Operacje asynchroniczne
Niektóre operacje bazy danych, takich jak wykonania polecenia może być czasochłonne znaczące. W takim przypadku aplikacji jednowątkowych należy blokować innych operacji i poczekaj na zakończenie przed kontynuowaniem ich własnych operacji polecenia. Z kolei możliwość przypisania długotrwałej operacji do wątku w tle pozwala na pozostają aktywne w trakcie operacji wątku pierwszego planu. W aplikacji Windows na przykład delegowanie długotrwałej operacji do wątku w tle umożliwia wątku interfejsu użytkownika będzie odpowiadać podczas wykonywania operacji.  
  
 .NET Framework zapewnia kilka standardowych asynchroniczne wzorce projektowe których deweloperzy mogą wykorzystać wątki w tle i bez interfejsu użytkownika lub o wysokim priorytecie wątków na zakończenie innych operacji. ADO.NET obsługuje tych samym wzorce projektowe w jego <xref:System.Data.SqlClient.SqlCommand> klasy. W szczególności <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A>, i <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A> metody łączyć się z <xref:System.Data.SqlClient.SqlCommand.EndExecuteNonQuery%2A>, <xref:System.Data.SqlClient.SqlCommand.EndExecuteReader%2A>, i <xref:System.Data.SqlClient.SqlCommand.EndExecuteXmlReader%2A> metod, zapewniają obsługę asynchronicznego.  
  
> [!NOTE]
>  Programowanie asynchroniczne jest podstawowych funkcji programu .NET Framework i ADO.NET wykorzystuje pełną standardowe wzorce projektowe. Aby uzyskać więcej informacji o różnych technik asynchroniczne dostępne dla deweloperów, zobacz [wywołanie asynchroniczne synchroniczne metody](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md).  
  
 Mimo że używanie metod asynchronicznych ADO.NET funkcji nie dodawać uwagi użytkownika, istnieje duże prawdopodobieństwo, że więcej umożliwia deweloperom funkcje asynchroniczne w ADO.NET niż w innych obszarach programu .NET Framework. Należy mieć świadomość korzyści i problemów tworzenie aplikacji wielowątkowych. Przykłady, które należy wykonać w tym punkcie sekcji kilka ważnych problemów tym deweloperzy należy wziąć pod uwagę podczas tworzenia aplikacji, które włączać funkcje wielowątkowych.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Aplikacje systemu Windows z wykorzystaniem wywołania zwrotnego](../../../../../docs/framework/data/adonet/sql/windows-applications-using-callbacks.md)  
 Przykład pokazująca, jak można wykonać polecenia asynchroniczne bezpiecznie, poprawnie obsługi interakcji z formularza i jego zawartość z oddzielnym wątku.  
  
 [Aplikacje ASP.NET z wykorzystaniem uchwytów oczekiwania](../../../../../docs/framework/data/adonet/sql/aspnet-apps-using-wait-handles.md)  
 Przykład pokazująca, jak można wykonywać wiele równoczesnych polecenia ze strony programu ASP.NET, zarządzanie operację po zakończeniu wszystkich poleceń za pomocą uchwyty oczekiwania.  
  
 [Sondowanie aplikacji konsoli](../../../../../docs/framework/data/adonet/sql/polling-in-console-applications.md)  
 Przykład zastosowanie sondowania czekać na zakończenie wykonywania polecenia asynchroniczne z aplikacji konsoli. Ta technika obowiązuje również w bibliotece klas lub innych aplikacji bez interfejsu użytkownika.  
  
## <a name="see-also"></a>Zobacz też  
 [SQL Server i ADO.NET](../../../../../docs/framework/data/adonet/sql/index.md)  
 [Wywoływanie metod synchronicznych w sposób asynchroniczny](../../../../../docs/standard/asynchronous-programming-patterns/calling-synchronous-methods-asynchronously.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
