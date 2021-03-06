---
title: Konfigurowanie parametrów i typów danych parametrów
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 537d8a2c-d40b-4000-83eb-bc1fcc93f707
ms.openlocfilehash: 320a45af1c2f3b460c23d8320c456120643902f7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759546"
---
# <a name="configuring-parameters-and-parameter-data-types"></a>Konfigurowanie parametrów i typów danych parametrów
Polecenie obiektów parametry do przekazania wartości do instrukcji SQL lub procedur składowanych, zapewniając Sprawdzanie typu i weryfikacji. W odróżnieniu od tekst polecenia parametr wejściowy jest traktowany jako wartość literału nie jako kod wykonywalny. Dzięki temu zabezpieczenia przed atakami "Iniekcja kodu SQL", w których osoba atakująca Wstawia polecenie Zabezpieczenia dokonywania na serwerze do instrukcji SQL.  
  
 Sparametryzowanych poleceń także może zwiększyć wydajność wykonywania zapytań, ponieważ pomagają dokładne dopasowanie przychodzące polecenie z planu prawidłowego zapytania w pamięci podręcznej serwera bazy danych. Aby uzyskać więcej informacji, zobacz [buforowanie Plan wykonania i ponowne użycie](http://go.microsoft.com/fwlink/?LinkId=120424) i [parametrów i wykonanie planu ponowne użycie](http://go.microsoft.com/fwlink/?LinkId=120423) w dokumentacji SQL Server — książki Online. Oprócz korzyści bezpieczeństwo i wydajność sparametryzowanych poleceń zapewniają wygodną metodę organizowania wartości przekazany do źródła danych.  
  
 A <xref:System.Data.Common.DbParameter> obiektu można tworzyć za pomocą jego konstruktora lub dodając go do <xref:System.Data.Common.DbCommand.DbParameterCollection%2A> przez wywołanie metody `Add` metody <xref:System.Data.Common.DbParameterCollection> kolekcji. `Add` Metoda będzie przyjmować jako danych wejściowych w argumentach konstruktora lub parametr obiektu, w zależności od dostawcy danych.  
  
## <a name="supplying-the-parameterdirection-property"></a>Udostępnia właściwości właściwość ParameterDirection  
 Dodając parametry, należy podać <xref:System.Data.ParameterDirection> właściwości dla parametrów innych niż parametrów wejściowych. W poniższej tabeli przedstawiono `ParameterDirection` wartości, których można używać z <xref:System.Data.ParameterDirection> wyliczenia.  
  
|Nazwa elementu członkowskiego|Opis|  
|-----------------|-----------------|  
|<xref:System.Data.ParameterDirection.Input>|Parametr jest parametrem wejściowym. Domyślnie włączone.|  
|<xref:System.Data.ParameterDirection.InputOutput>|Parametr może wykonywać zarówno danych wejściowych i wyjściowych.|  
|<xref:System.Data.ParameterDirection.Output>|Parametr jest parametrem wyjściowym.|  
|<xref:System.Data.ParameterDirection.ReturnValue>|Parametr reprezentuje wartością zwracaną operacji, takiej jak procedury składowanej, funkcji wbudowanej lub funkcję zdefiniowaną przez użytkownika.|  
  
## <a name="working-with-parameter-placeholders"></a>Praca z parametru symbole zastępcze  
 Składnia parametru symbole zastępcze zależy od źródła danych. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Dostawców danych obsługi nazywania i określanie parametrów i symbole zastępcze parametru inaczej. Ta składnia jest dostosowane do określonego źródła danych, zgodnie z opisem w poniższej tabeli.  
  
|Dostawca danych|Składnia nazwy parametru|  
|-------------------|-----------------------------|  
|<xref:System.Data.SqlClient>|Używa nazwanych parametrów w formacie `@` *parametername*.|  
|<xref:System.Data.OleDb>|Używa wskaźników parametrów pozycyjnych wskazywanym przez znak zapytania (`?`).|  
|<xref:System.Data.Odbc>|Używa wskaźników parametrów pozycyjnych wskazywanym przez znak zapytania (`?`).|  
|<xref:System.Data.OracleClient>|Używa nazwanych parametrów w formacie `:` *parmname* (lub *parmname*).|  
  
## <a name="specifying-parameter-data-types"></a>Określenie typów danych parametrów  
 Typ danych parametru jest specyficzne dla [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych. Określenie typu konwertuje wartość `Parameter` do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ dostawcy danych przed przekazaniem wartość ze źródłem danych. Można również określić typ `Parameter` w sposób ogólny, ustawiając `DbType` właściwość `Parameter` obiektu do określonego <xref:System.Data.DbType>.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Typu dostawcy danych `Parameter` obiektu jest wywnioskowany na podstawie [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu `Value` z `Parameter` obiekt, lub z `DbType` z `Parameter` obiektu. W poniższej tabeli przedstawiono wnioskowany `Parameter` typ oparty na obiekt przekazany jako `Parameter` wartość lub określony `DbType`.  
  
|Typ programu .NET Framework|DbType|SqlDbType|OleDbType|OdbcType|Typu OracleType|  
|-------------------------|------------|---------------|---------------|--------------|----------------|  
|<xref:System.Boolean>|Boolean|bitowe|Boolean|bitowe|Byte|  
|<xref:System.Byte>|Byte|TinyInt|UnsignedTinyInt|TinyInt|Byte|  
|byte[]|plików binarnych|VarBinary`.` niejawnej konwersji zakończy się niepowodzeniem, jeśli tablica bajtów jest większy niż maksymalny rozmiar VarBinary, czyli 8000 bajtów. Tablice typu byte jest większy niż 8000 bajtów, jawnie ustaw <xref:System.Data.SqlDbType>.|VarBinary|plików binarnych|nieprzetworzone|  
|<xref:System.Char>|``|Wnioskowanie <xref:System.Data.SqlDbType> z char nie jest obsługiwane.|Char|Char|Byte|  
|<xref:System.DateTime>|DataGodzina|DataGodzina|DBTimeStamp|DataGodzina|DataGodzina|  
|<xref:System.DateTimeOffset>|DateTimeOffset|DateTimeOffset w programie SQL Server 2008. Wnioskowanie <xref:System.Data.SqlDbType> z DateTimeOffset nie jest obsługiwany w wersjach programu SQL Server starszych niż SQL Server 2008.|||DataGodzina|  
|<xref:System.Decimal>|Wartość dziesiętna|Wartość dziesiętna|Wartość dziesiętna|numeryczne|Wartość liczbowa|  
|<xref:System.Double>|Double|Float|Double|Double|Double|  
|<xref:System.Single>|Single|Rzeczywiste|Single|Rzeczywiste|Float|  
|<xref:System.Guid>|Identyfikator GUID|UniqueIdentifier|Identyfikator GUID|UniqueIdentifier|nieprzetworzone|  
|<xref:System.Int16 >|Int16|SmallInt|SmallInt|SmallInt|Int16|  
|<xref:System.Int32>|Int32|int|int|int|Int32|  
|<xref:System.Int64>|Int64|BigInt|BigInt|BigInt|Wartość liczbowa|  
|<xref:System.Object>|Obiekt|Variant|Variant|Wnioskowanie OdbcType z obiektu nie jest obsługiwane.|Blob|  
|<xref:System.String>|String|NVarChar. Ta niejawna konwersja zakończy się niepowodzeniem, jeśli ciąg jest większy niż maksymalny rozmiar NVarChar, która jest 4000 znaków. Ciągi większej niż 4000 znaków, należy jawnie ustawić <xref:System.Data.SqlDbType>.|VarWChar|NVarChar|NVarChar|  
|<xref:System.TimeSpan>|Godzina|Czas w programie SQL Server 2008. Wnioskowanie <xref:System.Data.SqlDbType> z TimeSpan nie jest obsługiwany w wersjach programu SQL Server starszych niż SQL Server 2008.|DBTime|Godzina|DataGodzina|  
|<xref:System.UInt16>|UInt16|Wnioskowanie <xref:System.Data.SqlDbType> z UInt16 nie jest obsługiwane.|UnsignedSmallInt|int|UInt16|  
|<xref:System.UInt32>|UInt32|Wnioskowanie <xref:System.Data.SqlDbType> z UInt32 nie jest obsługiwane.|unsignedInt|BigInt|UInt32|  
|<xref:System.UInt64>|UInt64|Wnioskowanie <xref:System.Data.SqlDbType> z UInt64 nie jest obsługiwane.|UnsignedBigInt|numeryczne|Wartość liczbowa|  
||AnsiString|VarChar|VarChar|VarChar|VarChar|  
||AnsiStringFixedLength|Char|Char|Char|Char|  
|``|Waluta|oszczędność pieniędzy|Waluta|Wnioskowanie `OdbcType` z `Currency` nie jest obsługiwane.|Wartość liczbowa|  
|``|Data|Data w programie SQL Server 2008. Wnioskowanie <xref:System.Data.SqlDbType> od daty nie jest obsługiwany w wersjach programu SQL Server starszych niż SQL Server 2008.|DBDate|Data|DataGodzina|  
|``|SByte|Wnioskowanie <xref:System.Data.SqlDbType> z SByte nie jest obsługiwane.|TinyInt|Wnioskowanie `OdbcType` z SByte nie jest obsługiwane.|SByte|  
||StringFixedLength|NChar|WChar|NChar|NChar|  
||Godzina|Czas w programie SQL Server 2008. Wnioskowanie <xref:System.Data.SqlDbType> od czasu nie jest obsługiwany w wersjach programu SQL Server starszych niż SQL Server 2008.|DBTime|Godzina|DataGodzina|  
||VarNumeric|Wnioskowanie <xref:System.Data.SqlDbType> z VarNumeric nie jest obsługiwane.|VarNumeric|Wnioskowanie `OdbcType` z VarNumeric nie jest obsługiwane.|Wartość liczbowa|  
|Typ zdefiniowany przez użytkownika (obiekt z <xref:Microsoft.SqlServer.Server.SqlUserDefinedAggregateAttribute>|Obiekt lub ciąg, w zależności od dostawcy (SqlClient zawsze zwraca obiekt, Odbc zawsze zwraca wartość typu ciąg, dostawcy danych zarządzanych OleDb zobaczyć albo|SqlDbType.Udt Jeśli <xref:Microsoft.SqlServer.Server.SqlUserDefinedTypeAttribute> jest obecny, w przeciwnym razie Variant|OleDbType.VarWChar (jeśli ma wartość null) w przeciwnym razie OleDbType.Variant.|OdbcType.NVarChar|Nieobsługiwane|  
  
> [!NOTE]
>  Konwersje z dziesiętną na inne typy są zawężanie konwersji, które zaokrąglona wartość dziesiętna do najbliższej wartości całkowitej w kierunku zera. Jeśli wynik konwersji nie można przedstawić w typie docelowym <xref:System.OverflowException> jest generowany.  
  
> [!NOTE]
>  Wartość null parametru są wysyłane do serwera, należy określić <xref:System.DBNull>, a nie `null` (`Nothing` w języku Visual Basic). Wartość null w systemie jest pusty obiekt, który nie ma wartości. <xref:System.DBNull> jest używana do reprezentowania wartości null. Aby uzyskać więcej informacji o wartości null bazy danych, zobacz [Obsługa wartości zerowych](../../../../docs/framework/data/adonet/sql/handling-null-values.md).  
  
## <a name="deriving-parameter-information"></a>Wyprowadzanie informacje o parametrach  
 Parametry mogą również pochodzić z za pomocą procedury składowanej `DbCommandBuilder` klasy. Zarówno `SqlCommandBuilder` i `OleDbCommandBuilder` klasy udostępnia metody statyczne, `DeriveParameters`, która automatycznie wypełnia kolekcję parametrów dla obiekt polecenia, który używa parametru informacji z procedury składowanej. Należy pamiętać, że `DeriveParameters` zastępuje wszelkie istniejące informacje parametr dla polecenia.  
  
> [!NOTE]
>  Wyprowadzanie informacje o parametrach wiąże spadek wydajności, ponieważ wymaga dodatkowych operacji dostępu do źródła danych, aby pobrać informacje. Jeśli informacje o parametrach jest znany w czasie projektowania, może poprawić wydajność aplikacji, jawnie ustawiając parametrów.  
  
 Aby uzyskać więcej informacji, zobacz [generowania poleceń CommandBuilders](../../../../docs/framework/data/adonet/generating-commands-with-commandbuilders.md).  
  
## <a name="using-parameters-with-a-sqlcommand-and-a-stored-procedure"></a>Przy użyciu parametrów z SqlCommand i procedury składowanej  
 Procedury składowane oferują wiele zalet w aplikacjach opartych na danych. Przy użyciu procedur składowanych, operacje bazy danych można być hermetyzowany za pomocą jednego polecenia, zoptymalizowane pod kątem najlepszą wydajność i rozszerzona o dodatkowe zabezpieczenia. Mimo że można wywołać procedurę składowaną przez przekazanie nazwę procedury składowanej następuje argumenty parametrów jako instrukcji SQL przy użyciu <xref:System.Data.Common.DbCommand.Parameters%2A> Kolekcja [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.Common.DbCommand> obiektu umożliwia bardziej jawnie definiować przechowywane Parametry procedur i dostępu do danych wyjściowych, parametrów i wartości zwracane.  
  
> [!NOTE]
>  Sparametryzowanych instrukcji są wykonywane na serwerze przy użyciu `sp_executesql,` co umożliwia ponowne planu zapytania. Kursory lokalne lub zmiennych w `sp_executesql` partii nie są widoczne dla partii, który wywołuje `sp_executesql`. Ostatnie zmiany w kontekście bazy danych tylko do końca `sp_executesql` instrukcji. Aby uzyskać więcej informacji zobacz dokumentację SQL Server — książki Online.  
  
 Korzystając z parametrów z <xref:System.Data.SqlClient.SqlCommand> programu SQL Server wykonaj procedurę składowaną w, nazwy parametrów dodane do <xref:System.Data.SqlClient.SqlCommand.Parameters%2A> kolekcji muszą być zgodne z nazwami znaczników parametr w procedurze składowanej. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Dostawcy danych programu SQL Server nie obsługuje symbolu zastępczego znak zapytania (?) przekazywania parametrów do instrukcji SQL lub procedurę składowaną. Traktuje parametry w procedurze składowanej jako nazwane parametry, a wyszukuje dopasowywania parametru znaczników. Na przykład `CustOrderHist` procedury składowanej jest definiowana za pomocą parametru o nazwie `@CustomerID`. Po kodzie wykonuje procedurę składowaną, również należy użyć parametru o nazwie `@CustomerID`.  
  
```  
CREATE PROCEDURE dbo.CustOrderHist @CustomerID varchar(5)  
```  
  
### <a name="example"></a>Przykład  
 W tym przykładzie przedstawiono sposób wywoływania procedur składowanych serwera SQL `Northwind` przykładowej bazy danych. Nazwa procedury składowanej jest `dbo.SalesByCategory` i zawiera parametru wejściowego o nazwie `@CategoryName` z typem danych `nvarchar(15)`. Kod tworzy nową <xref:System.Data.SqlClient.SqlConnection> wewnątrz using zablokować, tak aby połączenie zostanie usunięty po zakończeniu procedury. <xref:System.Data.SqlClient.SqlCommand> i <xref:System.Data.SqlClient.SqlParameter> obiekty są tworzone i ustawić ich właściwości. A <xref:System.Data.SqlClient.SqlDataReader> wykonuje `SqlCommand` i zwraca zestawu wyników z procedury składowanej, wyświetlając dane wyjściowe w oknie konsoli.  
  
> [!NOTE]
>  Zamiast tworzyć `SqlCommand` i `SqlParameter` obiektów, a następnie ustawić właściwości w osobnych instrukcji, można zamiast tego wybrać opcję Użyj jednej z przeciążone konstruktory do ustawiania wielu właściwości w jednej instrukcji.  
  
 [!code-csharp[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/csharp/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/CS/source.cs#1)]
 [!code-vb[DataWorks SqlClient.StoredProcedure#1](../../../../samples/snippets/visualbasic/VS_Snippets_ADO.NET/DataWorks SqlClient.StoredProcedure/VB/source.vb#1)]  
  
## <a name="using-parameters-with-an-oledbcommand-or-odbccommand"></a>Przy użyciu parametrów przy użyciu OleDbCommand lub OdbcCommand  
 Korzystając z parametrów z <xref:System.Data.OleDb.OleDbCommand> lub <xref:System.Data.Odbc.OdbcCommand>, kolejność parametrów dodanych do `Parameters` kolekcji muszą być zgodne kolejność parametrów zdefiniowanych w procedury przechowywanej. [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Dostawcy danych OLE DB i [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych ODBC Traktuj parametry w procedurze składowanej jako symbole zastępcze i zastosować wartości parametrów w kolejności. Ponadto zwrócić wartość parametrów musi być pierwszym parametry dodane do `Parameters` kolekcji.  
  
 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] Dostawcy danych OLE DB i [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych ODBC nie obsługują parametrów nazwanych parametrów może być przekazywany do instrukcji SQL lub procedurę składowaną. W takim przypadku należy użyć symbolu zastępczego znak zapytania (?), jak w poniższym przykładzie.  
  
```  
SELECT * FROM Customers WHERE CustomerID = ?  
```  
  
 W rezultacie, w kolejności `Parameter` obiekty są dodawane do `Parameters` kolekcji bezpośrednio musi odpowiadać pozycja? symbol zastępczy dla parametru.  
  
### <a name="oledb-example"></a>Przykład OleDb  
  
```vb  
Dim command As OleDbCommand = New OleDbCommand( _  
  "SampleProc", connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As OleDbParameter = command.Parameters.Add( _  
  "RETURN_VALUE", OleDbType.Integer)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@InputParm", OleDbType.VarChar, 12)  
parameter.Value = "Sample Value"  
  
parameter = command.Parameters.Add( _  
  "@OutputParm", OleDbType.VarChar, 28)  
parameter.Direction = ParameterDirection.Output  
```  
  
```csharp  
OleDbCommand command = new OleDbCommand("SampleProc", connection);  
command.CommandType = CommandType.StoredProcedure;  
  
OleDbParameter parameter = command.Parameters.Add(  
  "RETURN_VALUE", OleDbType.Integer);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add(  
  "@InputParm", OleDbType.VarChar, 12);  
parameter.Value = "Sample Value";  
  
parameter = command.Parameters.Add(  
  "@OutputParm", OleDbType.VarChar, 28);  
parameter.Direction = ParameterDirection.Output;  
```  
  
## <a name="odbc-example"></a>Przykład ODBC  
  
```vb  
Dim command As OdbcCommand = New OdbcCommand( _  
  "{ ? = CALL SampleProc(?, ?) }", connection)  
command.CommandType = CommandType.StoredProcedure  
  
Dim parameter As OdbcParameter = command.Parameters.Add("RETURN_VALUE", OdbcType.Int)  
parameter.Direction = ParameterDirection.ReturnValue  
  
parameter = command.Parameters.Add( _  
  "@InputParm", OdbcType.VarChar, 12)  
parameter.Value = "Sample Value"  
  
parameter = command.Parameters.Add( _  
  "@OutputParm", OdbcType.VarChar, 28)  
parameter.Direction = ParameterDirection.Output  
```  
  
```csharp  
OdbcCommand command = new OdbcCommand( _  
  "{ ? = CALL SampleProc(?, ?) }", connection);  
command.CommandType = CommandType.StoredProcedure;  
  
OdbcParameter parameter = command.Parameters.Add( _  
  "RETURN_VALUE", OdbcType.Int);  
parameter.Direction = ParameterDirection.ReturnValue;  
  
parameter = command.Parameters.Add( _  
  "@InputParm", OdbcType.VarChar, 12);  
parameter.Value = "Sample Value";  
  
parameter = command.Parameters.Add( _  
  "@OutputParm", OdbcType.VarChar, 28);  
parameter.Direction = ParameterDirection.Output;  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Polecenia i parametry](../../../../docs/framework/data/adonet/commands-and-parameters.md)  
 [Parametry elementu DataAdapter](../../../../docs/framework/data/adonet/dataadapter-parameters.md)  
 [Mapowanie typu danych w ADO.NET](../../../../docs/framework/data/adonet/data-type-mappings-in-ado-net.md)  
 [ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów](http://go.microsoft.com/fwlink/?LinkId=217917)
