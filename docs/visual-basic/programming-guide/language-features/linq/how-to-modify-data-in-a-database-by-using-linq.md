---
title: 'Porady: modyfikowanie danych w bazie danych za pomocą LINQ (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inserting rows [LINQ to SQL]
- deleting rows [LINQ to SQL]
- updating rows [LINQ to SQL]
- inserting data [Visual Basic]
- deleting data
- data [Visual Basic], updating
- updating data [LINQ]
- queries [LINQ in Visual Basic], data changes in database
- queries [LINQ in Visual Basic], how-to topics
ms.assetid: cf52635f-0c1b-46c3-aff1-bdf181cf19b1
ms.openlocfilehash: 617bb62f9009c507658b5d1262657cb4dfa860e9
ms.sourcegitcommit: d955cb4c681d68cf301d410925d83f25172ece86
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/07/2018
ms.locfileid: "34827114"
---
# <a name="how-to-modify-data-in-a-database-by-using-linq-visual-basic"></a>Porady: modyfikowanie danych w bazie danych za pomocą LINQ (Visual Basic)
Zintegrowane języka zapytań zapytania (LINQ) ułatwiają dostęp do bazy danych i modyfikować wartości w bazie danych.  
  
 Poniższy przykład przedstawia sposób tworzenia nowej aplikacji, które są pobierane i informacji o aktualizacjach w bazie danych programu SQL Server.  
  
 W przykładach w tym temacie użyto przykładowej bazy danych Northwind. Jeśli nie ma tej bazy danych na komputerze deweloperskim, można go pobrać z Microsoft Download Center. Aby uzyskać instrukcje, zobacz [pobieranie przykładowe bazy danych](../../../../framework/data/adonet/sql/linq/downloading-sample-databases.md).  
  
### <a name="to-create-a-connection-to-a-database"></a>Aby utworzyć połączenie z bazą danych  
  
1.  W programie Visual Studio Otwórz **Eksploratora serwera**/**Eksploratora bazy danych** klikając **widoku** menu, a następnie wybierz **wEksploratorzeserwera** / **Bazy danych Explorer**.  
  
2.  Kliknij prawym przyciskiem myszy **połączenia danych** w **Eksploratora serwera**/**Eksploratora bazy danych**i kliknij przycisk **Dodawanie połączenia**.  
  
3.  Określ prawidłowe połączenie z przykładową bazą danych Northwind.  
  
### <a name="to-add-a-project-with-a-linq-to-sql-file"></a>Aby dodać projekt za pomocą LINQ do SQL pliku  
  
1.  W programie Visual Studio na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu**. Wybierz pozycję Visual Basic **aplikacji Windows Forms** jako typ projektu.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**. Wybierz **klasy LINQ do SQL** szablon elementu.  
  
3.  Nadaj nazwę plikowi `northwind.dbml`. Kliknij przycisk **Dodaj**. Projektant obiektów relacyjnych (Projektanta obiektów relacyjnych) jest otwarty dla `northwind.dbml` pliku.  
  
### <a name="to-add-tables-to-query-and-modify-to-the-designer"></a>Aby dodać tabele, aby zapytania i modyfikować do projektanta  
  
1.  W **Eksploratora serwera**/**Eksploratora bazy danych**, rozwiń węzeł połączenia z bazą danych Northwind. Rozwiń węzeł **tabel** folderu.  
  
     Po zamknięciu Projektanta obiektów relacyjnych, możesz uruchomić go przez dwukrotne kliknięcie `northwind.dbml` pliku dodanego wcześniej.  
  
2.  Tabeli Klienci kliknij i przeciągnij go do lewego okienka projektanta.  
  
     Projektant tworzy nowy obiekt klienta dla projektu.  
  
3.  Zapisz zmiany i zamknij projektanta.  
  
4.  Zapisz projekt.  
  
### <a name="to-add-code-to-modify-the-database-and-display-the-results"></a>Aby dodać kod do modyfikowania bazy danych i wyświetlić wyniki  
  
1.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.DataGridView> formant na domyślnego formularza systemu Windows dla projektu, Form1.  
  
2.  Po dodaniu tabel do Projektanta obiektów relacyjnych projektanta dodane <xref:System.Data.Linq.DataContext> obiektu do projektu. Ten obiekt zawiera kod, który można uzyskać dostępu do tabeli klientów. Zawiera kod, który definiuje obiekt klienta i kolekcję klientów dla tabeli. <xref:System.Data.Linq.DataContext> Obiektu dla nosi nazwę projektu na podstawie nazwy pliku .dbml. Dla tego projektu <xref:System.Data.Linq.DataContext> nosi nazwę obiektu `northwindDataContext`.  
  
     Można utworzyć wystąpienia <xref:System.Data.Linq.DataContext> obiektu w kodzie i zapytania i modyfikować kolekcji klientów określony przez Projektanta obiektów relacyjnych. Zmiany wprowadzone do kolekcji klientów nie są uwzględniane w bazie danych do czasu przesłania przez wywołanie metody <xref:System.Data.Linq.DataContext.SubmitChanges%2A> metody <xref:System.Data.Linq.DataContext> obiektu.  
  
     Kliknij dwukrotnie formularza systemu Windows, Formularz1, aby dodać kod, aby <xref:System.Windows.Forms.Form.Load> zdarzenia kwerendę klientów tabelę, która jest ujawniona jako właściwość z <xref:System.Data.Linq.DataContext>. Dodaj następujący kod:  
  
    ```vb  
    Private db As northwindDataContext  
  
    Private Sub Form1_Load(ByVal sender As System.Object,   
                           ByVal e As System.EventArgs  
                          ) Handles MyBase.Load  
      db = New northwindDataContext()  
  
      RefreshData()  
    End Sub  
  
    Private Sub RefreshData()  
      Dim customers = From cust In db.Customers   
                      Where cust.City(0) = "W"   
                      Select cust  
  
      DataGridView1.DataSource = customers  
    End Sub  
    ```  
  
3.  Z **przybornika**, przeciągnij trzy <xref:System.Windows.Forms.Button> formantów do formularza. Wybierz pierwsze `Button` formantu. W **właściwości** ustaw `Name` z `Button` formant `AddButton` i `Text` do `Add`. Wybierz przycisk drugi i ustaw `Name` właściwości `UpdateButton` i `Text` właściwości `Update`. Wybierz przycisk trzeci i ustaw `Name` właściwości `DeleteButton` i `Text` właściwości `Delete`.  
  
4.  Kliknij dwukrotnie **Dodaj** przycisk, aby dodać kod, aby jego `Click` zdarzeń. Dodaj następujący kod:  
  
    ```vb  
    Private Sub AddButton_Click(ByVal sender As System.Object,   
                                ByVal e As System.EventArgs  
                               ) Handles AddButton.Click  
      Dim cust As New Customer With {   
        .City = "Wellington",   
        .CompanyName = "Blue Yonder Airlines",   
        .ContactName = "Jill Frank",   
        .Country = "New Zealand",   
        .CustomerID = "JILLF"}  
  
      db.Customers.InsertOnSubmit(cust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
5.  Kliknij dwukrotnie **aktualizacji** przycisk, aby dodać kod, aby jego `Click` zdarzeń. Dodaj następujący kod:  
  
    ```vb  
    Private Sub UpdateButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles UpdateButton.Click  
      Dim updateCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      updateCust.ContactName = "Jill Shrader"  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
6.  Kliknij dwukrotnie **usunąć** przycisk, aby dodać kod, aby jego `Click` zdarzeń. Dodaj następujący kod:  
  
    ```vb  
    Private Sub DeleteButton_Click(ByVal sender As System.Object, _  
                                   ByVal e As System.EventArgs  
                                  ) Handles DeleteButton.Click  
      Dim deleteCust = (From cust In db.Customers   
                        Where cust.CustomerID = "JILLF").ToList()(0)  
  
      db.Customers.DeleteOnSubmit(deleteCust)  
  
      Try  
        db.SubmitChanges()  
      Catch  
        ' Handle exception.  
      End Try  
  
      RefreshData()  
    End Sub  
    ```  
  
7.  Naciśnij klawisz F5, aby uruchomić projekt. Kliknij przycisk **Dodaj** do dodawania nowego rekordu. Kliknij przycisk **aktualizacji** można zmodyfikować w nowym rekordzie. Kliknij przycisk **usunąć** do usunięcia w nowym rekordzie.  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ](../../../../visual-basic/programming-guide/language-features/linq/index.md)  
 [Zapytania](../../../../visual-basic/language-reference/queries/queries.md)  
 [LINQ to SQL](../../../../framework/data/adonet/sql/linq/index.md)  
 [Metody DataContext (Projektanta obiektów relacyjnych)](/visualstudio/data-tools/datacontext-methods-o-r-designer)  
 [Porady: przypisywanie procedur składowanych do wykonywania aktualizacji, wstawienia i usunięcia (Projektanta obiektów relacyjnych)](http://msdn.microsoft.com/library/e88224ab-ff61-4a3a-b6b8-6f3694546cac)
