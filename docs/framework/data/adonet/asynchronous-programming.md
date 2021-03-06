---
title: Programowanie asynchroniczne
ms.date: 03/30/2017
ms.assetid: 85da7447-7125-426e-aa5f-438a290d1f77
ms.openlocfilehash: 29324a07ffdaf99d1b7631ad8e94e773ed509fcc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759910"
---
# <a name="asynchronous-programming"></a>Programowanie asynchroniczne

W tym temacie omówiono obsługę programowania asynchronicznego w [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] dostawcy danych programu SQL Server (SqlClient) w tym ulepszenia są wprowadzane do obsługi funkcji asynchronicznych programowania, który został wprowadzony w [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
## <a name="legacy-asynchronous-programming"></a>Programowanie asynchroniczne starszej wersji  
 Przed [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], programowanie asynchroniczne z SqlClient została wykonana z następujących metod i `Asynchronous Processing=true` właściwości połączenia:  
  
1.  <xref:System.Data.SqlClient.SqlCommand.BeginExecuteNonQuery%2A?displayProperty=nameWithType>  
  
2.  <xref:System.Data.SqlClient.SqlCommand.BeginExecuteReader%2A?displayProperty=nameWithType>  
  
3.  <xref:System.Data.SqlClient.SqlCommand.BeginExecuteXmlReader%2A?displayProperty=nameWithType>  
  
 Ta funkcja pozostanie na liście SqlClient w [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)].  
  
 Począwszy od [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], tych metod nie wymagają już `Asynchronous Processing=true` w parametrach połączenia.  
  
## <a name="asynchronous-programming-features-added-in-includenetv45includesnet-v45-mdmd"></a>Dodane w funkcje programowanie asynchroniczne [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)]  
 Nowa funkcja programowania asynchronicznego udostępnia proste techniki dokonanie asynchroniczne kodu.  
  
 Aby uzyskać więcej informacji na temat funkcji programowania asynchronicznego, która została wprowadzona w systemie [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], zobacz:  
  
- [Programowanie asynchroniczne w języku C#](../../../csharp/async.md)

- [Programowanie asynchroniczne z Async i Await (Visual Basic)](../../../visual-basic/programming-guide/concepts/async/index.md)

- [Przy użyciu nowych metod asynchronicznych w SqlDataReader w .net 4.5 (część 1)](https://blogs.msdn.microsoft.com/adonet/2012/04/20/using-sqldatareaders-new-async-methods-in-net-4-5/)

- [Przy użyciu nowych metod asynchronicznych w SqlDataReader w .net 4.5 (część 2)](https://blogs.msdn.microsoft.com/adonet/2012/07/15/using-sqldatareaders-new-async-methods-in-net-4-5-part-2-examples/)
 
 Gdy interfejsu użytkownika nie odpowiada lub serwer nie działa, prawdopodobnie należy swój kod, aby była bardziej asynchroniczna.  Pisanie kodu asynchroniczny został tradycyjnie użyty instalowanie wywołanie zwrotne (nazywanych również kontynuacji) Express logiki, która występuje po zakończeniu operacji asynchronicznej. Stwarza to struktury kodu asynchroniczne porównaniu synchroniczne kodu.  
  
 Można teraz wywołać do metod asynchronicznych bez przy użyciu wywołania zwrotne i bez dzielenia kodu wielu metod lub wyrażenia lambda.  
  
 `async` Modyfikator Określa, czy metoda jest asynchroniczne. Podczas wywoływania metody `async` metody, zwracany jest zadanie. Gdy `await` operator zostaną zastosowane do zadania, bieżącej metody kończy się natychmiast. Po zakończeniu zadania wykonywania wznawia w tej samej metody.
  
> [!WARNING]
>  Wywołania asynchroniczne nie są obsługiwane, jeśli aplikacja używa również `Context Connection` słowo kluczowe parametrów połączenia.  
  
 Wywoływanie `async` — metoda nie przydzielić wszelkie dodatkowe wątki. Istniejące wątku zakończenia We/Wy może zajmować krótko po zakończeniu.  
  
 Dodano następujące metody w [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)] do obsługi programowania asynchronicznego:  
  
-   <xref:System.Data.Common.DbConnection.OpenAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbCommand.ExecuteDbDataReaderAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbCommand.ExecuteNonQueryAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbCommand.ExecuteReaderAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbCommand.ExecuteScalarAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbDataReader.GetFieldValueAsync%2A>  
  
-   <xref:System.Data.Common.DbDataReader.IsDBNullAsync%2A>  
  
-   <xref:System.Data.Common.DbDataReader.NextResultAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.Common.DbDataReader.ReadAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlConnection.OpenAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlCommand.ExecuteNonQueryAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlCommand.ExecuteReaderAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlCommand.ExecuteScalarAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlCommand.ExecuteXmlReaderAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.NextResultAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlDataReader.ReadAsync%2A?displayProperty=nameWithType>  
  
-   <xref:System.Data.SqlClient.SqlBulkCopy.WriteToServerAsync%2A?displayProperty=nameWithType>  
  
 Inni członkowie asynchroniczne zostały dodane do obsługi [obsługuje przesyłania strumieniowego SqlClient](../../../../docs/framework/data/adonet/sqlclient-streaming-support.md).  
  
### <a name="synchronous-to-asynchronous-connection-open"></a>Synchronicznego w celu otworzenia połączenia asynchronicznego  
 Można uaktualnić istniejącą aplikację do użycia nowej funkcji asynchronicznej. Załóżmy na przykład, aplikacja ma algorytm synchroniczne połączenia i blokuje wątku interfejsu użytkownika za każdym razem ustanawiania połączenia z bazą danych, i po nawiązaniu połączenia aplikacji wywołania procedury przechowywanej, która sygnalizuje innym użytkownikom ten, który właśnie zalogowany.  
  
```csharp
using SqlConnection conn = new SqlConnection("…");  
{  
   conn.Open();  
   using (SqlCommand cmd = new SqlCommand("StoredProcedure_Logon", conn))  
   {  
      cmd.ExecuteNonQuery();  
   }  
}  
```  
  
 Po przekonwertowaniu, aby korzystać z nowych funkcji asynchronicznych, program będzie wyglądała:  
  
```csharp
using System;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class A {  
  
   static async Task<int> Method(SqlConnection conn, SqlCommand cmd) {  
      await conn.OpenAsync();  
      await cmd.ExecuteNonQueryAsync();  
      return 1;  
   }  
  
   public static void Main() {  
      using (SqlConnection conn = new SqlConnection("Data Source=(local); Initial Catalog=NorthWind; Integrated Security=SSPI")) {  
         SqlCommand command = new SqlCommand("select top 2 * from orders", conn);  
  
         int result = A.Method(conn, command).Result;  
  
         SqlDataReader reader = command.ExecuteReader();  
         while (reader.Read())  
            Console.WriteLine(String.Format("{0}", reader[0]));  
      }  
   }  
}  
```  
  
### <a name="adding-the-new-asynchronous-feature-in-an-existing-application-mixing-old-and-new-patterns"></a>Dodawanie nowej funkcji asynchronicznych w istniejącej aplikacji (mieszanie starej i nowej wzorców)  
 Istnieje również możliwość dodać nową funkcję asynchroniczną (SqlConnection::OpenAsync) bez zmieniania istniejących logiki asynchroniczne. Na przykład, jeśli aplikacja używa obecnie:  
  
```csharp
AsyncCallback productList = new AsyncCallback(ProductList);  
SqlConnection conn = new SqlConnection("…");  
conn.Open();  
SqlCommand cmd = new SqlCommand("SELECT * FROM [Current Product List]", conn);  
IAsyncResult ia = cmd.BeginExecuteReader(productList, cmd);  
```  
  
 Można rozpocząć używanie nowego wzorca asynchronicznego bez znacznie zmiana istniejących algorytmu.  
  
```csharp
using System;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class A {  
   static void ProductList(IAsyncResult result) { }  
  
   public static void Main() {  
      // AsyncCallback productList = new AsyncCallback(ProductList);  
      // SqlConnection conn = new SqlConnection("Data Source=(local); Initial Catalog=NorthWind; Integrated Security=SSPI");  
      // conn.Open();  
      // SqlCommand cmd = new SqlCommand("select top 2 * from orders", conn);  
      // IAsyncResult ia = cmd.BeginExecuteReader(productList, cmd);  
  
      AsyncCallback productList = new AsyncCallback(ProductList);  
      SqlConnection conn = new SqlConnection("Data Source=(local); Initial Catalog=NorthWind; Integrated Security=SSPI");  
      conn.OpenAsync().ContinueWith((task) => {  
         SqlCommand cmd = new SqlCommand("select top 2 * from orders", conn);  
         IAsyncResult ia = cmd.BeginExecuteReader(productList, cmd);  
      }, TaskContinuationOptions.OnlyOnRanToCompletion);  
   }  
}  
```  
  
### <a name="using-the-base-provider-model-and-the-new-asynchronous-feature"></a>Przy użyciu modelu podstawowego dostawcy i nowej funkcji asynchronicznych  
 Należy utworzyć narzędzie, które jest w stanie podłączyć się do różnych baz danych i wykonywanie zapytań. Można użyć modelu podstawowego dostawcy i nowej funkcji asynchronicznej.  
  
 Kontroler transakcji rozproszonych (MSDTC) firmy Microsoft musi być włączona serwer do korzystania z transakcji rozproszonych. Aby uzyskać informacje na temat włączania usługi MSDTC, zobacz [jak włączyć usługi MSDTC na serwerze sieci Web](http://msdn.microsoft.com/library/dd327979.aspx).  
  
```csharp
using System;  
using System.Data.Common;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class A {  
   static async Task PerformDBOperationsUsingProviderModel(string connectionString, string providerName) {  
      DbProviderFactory factory = DbProviderFactories.GetFactory(providerName);  
      using (DbConnection connection = factory.CreateConnection()) {  
         connection.ConnectionString = connectionString;  
         await connection.OpenAsync();  
  
         DbCommand command = connection.CreateCommand();  
         command.CommandText = "SELECT * FROM AUTHORS";  
  
         using (DbDataReader reader = await command.ExecuteReaderAsync()) {  
            while (await reader.ReadAsync()) {  
               for (int i = 0; i < reader.FieldCount; i++) {  
                  // Process each column as appropriate  
                  object obj = await reader.GetFieldValueAsync<object>(i);  
                  Console.WriteLine(obj);  
               }  
            }  
         }  
      }  
   }  
  
   public static void Main()   
   {  
       SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder();  
       // replace these with your own values  
       builder.DataSource = "your_server";  
       builder.InitialCatalog = "pubs";  
       builder.IntegratedSecurity = true;  
       string provider = "System.Data.SqlClient";  
  
       Task task = PerformDBOperationsUsingProviderModel(builder.ConnectionString, provider);  
       task.Wait();  
   }  
}  
```  
  
### <a name="using-sql-transactions-and-the-new-asynchronous-feature"></a>Przy użyciu transakcji SQL i nowej funkcji asynchronicznych  
  
```csharp
using System;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class Program {  
   static void Main() {  
      string connectionString =  
          "Persist Security Info=False;Integrated Security=SSPI;database=Northwind;server=(local)";  
      Task task = ExecuteSqlTransaction(connectionString);  
      task.Wait();  
   }  
  
   static async Task ExecuteSqlTransaction(string connectionString) {  
      using (SqlConnection connection = new SqlConnection(connectionString)) {  
         await connection.OpenAsync();  
  
         SqlCommand command = connection.CreateCommand();  
         SqlTransaction transaction = null;  
  
         // Start a local transaction.  
         transaction = await Task.Run<SqlTransaction>(  
             () => connection.BeginTransaction("SampleTransaction")  
             );  
  
         // Must assign both transaction object and connection  
         // to Command object for a pending local transaction  
         command.Connection = connection;  
         command.Transaction = transaction;  
  
         try {  
            command.CommandText =  
                "Insert into Region (RegionID, RegionDescription) VALUES (555, 'Description')";  
            await command.ExecuteNonQueryAsync();  
  
            command.CommandText =  
                "Insert into Region (RegionID, RegionDescription) VALUES (556, 'Description')";  
            await command.ExecuteNonQueryAsync();  
  
            // Attempt to commit the transaction.  
            await Task.Run(() => transaction.Commit());  
            Console.WriteLine("Both records are written to database.");  
         }  
         catch (Exception ex) {  
            Console.WriteLine("Commit Exception Type: {0}", ex.GetType());  
            Console.WriteLine("  Message: {0}", ex.Message);  
  
            // Attempt to roll back the transaction.  
            try {  
               transaction.Rollback();  
            }  
            catch (Exception ex2) {  
               // This catch block will handle any errors that may have occurred  
               // on the server that would cause the rollback to fail, such as  
               // a closed connection.  
               Console.WriteLine("Rollback Exception Type: {0}", ex2.GetType());  
               Console.WriteLine("  Message: {0}", ex2.Message);  
            }  
         }  
      }  
   }  
}  
```  
  
### <a name="using-sql-transactions-and-the-new-asynchronous-feature"></a>Przy użyciu transakcji SQL i nowej funkcji asynchronicznych  
 W aplikacji dla przedsiębiorstw może być konieczne dodanie transakcji rozproszonych w niektórych scenariuszach, aby włączyć transakcji między wieloma serwerami bazy danych. Można użyć obszaru nazw System.Transactions i zarejestrować transakcji rozproszonej, w następujący sposób:  
  
```csharp
using System;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
using System.Transactions;  
  
class Program {  
   public static void Main()   
   {  
       SqlConnectionStringBuilder builder = new SqlConnectionStringBuilder();  
       // replace these with your own values  
       builder.DataSource = "your_server";  
       builder.InitialCatalog = "your_data_source";  
       builder.IntegratedSecurity = true;  
  
       Task task = ExecuteDistributedTransaction(builder.ConnectionString, builder.ConnectionString);  
       task.Wait();  
   }  
  
   static async Task ExecuteDistributedTransaction(string connectionString1, string connectionString2) {  
      using (SqlConnection connection1 = new SqlConnection(connectionString1))  
      using (SqlConnection connection2 = new SqlConnection(connectionString2)) {  
         using (CommittableTransaction transaction = new CommittableTransaction()) {  
            await connection1.OpenAsync();  
            connection1.EnlistTransaction(transaction);  
  
            await connection2.OpenAsync();  
            connection2.EnlistTransaction(transaction);  
  
            try {  
               SqlCommand command1 = connection1.CreateCommand();  
               command1.CommandText = "Insert into RegionTable1 (RegionID, RegionDescription) VALUES (100, 'Description')";  
               await command1.ExecuteNonQueryAsync();  
  
               SqlCommand command2 = connection2.CreateCommand();  
               command2.CommandText = "Insert into RegionTable2 (RegionID, RegionDescription) VALUES (100, 'Description')";  
               await command2.ExecuteNonQueryAsync();  
  
               transaction.Commit();  
            }  
            catch (Exception ex) {  
               Console.WriteLine("Exception Type: {0}", ex.GetType());  
               Console.WriteLine("  Message: {0}", ex.Message);  
  
               try {  
                  transaction.Rollback();  
               }  
               catch (Exception ex2) {  
                  Console.WriteLine("Rollback Exception Type: {0}", ex2.GetType());  
                  Console.WriteLine("  Message: {0}", ex2.Message);  
               }  
            }  
         }  
      }  
   }  
}  
```  
  
### <a name="cancelling-an-asynchronous-operation"></a>Anulowanie operacji asynchronicznej  
 Możesz anulować żądanie asynchroniczne przy użyciu <xref:System.Threading.CancellationToken>.  
  
```csharp
using System;  
using System.Data.SqlClient;  
using System.Threading;  
using System.Threading.Tasks;  
  
namespace Samples {  
   class CancellationSample {  
      public static void Main(string[] args) {  
         CancellationTokenSource source = new CancellationTokenSource();  
         source.CancelAfter(2000); // give up after 2 seconds  
         try {  
            Task result = CancellingAsynchronousOperations(source.Token);  
            result.Wait();  
         }  
         catch (AggregateException exception) {  
            if (exception.InnerException is SqlException) {  
               Console.WriteLine("Operation canceled");  
            }  
            else {  
               throw;  
            }  
         }  
      }  
  
      static async Task CancellingAsynchronousOperations(CancellationToken cancellationToken) {  
         using (SqlConnection connection = new SqlConnection("Server=(local);Integrated Security=true")) {  
            await connection.OpenAsync(cancellationToken);  
  
            SqlCommand command = new SqlCommand("WAITFOR DELAY '00:10:00'", connection);  
            await command.ExecuteNonQueryAsync(cancellationToken);  
         }  
      }  
   }  
}  
```  
  
### <a name="asynchronous-operations-with-sqlbulkcopy"></a>Operacje asynchroniczne z SqlBulkCopy  
 Funkcje asynchroniczne również zostały dodane do <xref:System.Data.SqlClient.SqlBulkCopy?displayProperty=nameWithType> z <xref:System.Data.SqlClient.SqlBulkCopy.WriteToServerAsync%2A?displayProperty=nameWithType>.  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Data;  
using System.Data.Odbc;  
using System.Data.SqlClient;  
using System.Linq;  
using System.Text;  
using System.Threading;  
using System.Threading.Tasks;  
  
namespace SqlBulkCopyAsyncCodeSample {  
   class Program {  
      static string selectStatment = "SELECT * FROM [pubs].[dbo].[titles]";  
      static string createDestTableStatement =  
          @"CREATE TABLE {0} (  
            [title_id] [varchar](6) NOT NULL,  
            [title] [varchar](80) NOT NULL,  
            [type] [char](12) NOT NULL,  
            [pub_id] [char](4) NULL,  
            [price] [money] NULL,  
            [advance] [money] NULL,  
            [royalty] [int] NULL,  
            [ytd_sales] [int] NULL,  
            [notes] [varchar](200) NULL,  
            [pubdate] [datetime] NOT NULL)";  
  
      // Replace the connection string if needed, for instance to connect to SQL Express: @"Server=(local)\SQLEXPRESS;Database=Demo;Integrated Security=true"  
      // static string connectionString = @"Server=(localdb)\V11.0;Database=Demo";  
      static string connectionString = @"Server=(local);Database=Demo;Integrated Security=true";  
  
      // static string odbcConnectionString = @"Driver={SQL Server};Server=(localdb)\V11.0;UID=oledb;Pwd=1Password!;Database=Demo";  
      static string odbcConnectionString = @"Driver={SQL Server};Server=(local);Database=Demo;Integrated Security=true";  
  
      // static string marsConnectionString = @"Server=(localdb)\V11.0;Database=Demo;MultipleActiveResultSets=true;";  
      static string marsConnectionString = @"Server=(local);Database=Demo;MultipleActiveResultSets=true;Integrated Security=true";  
  
      // Replace the Server name with your actual sql azure server name and User ID/Password  
      static string azureConnectionString = @"Server=SqlAzure;User ID=myUserID;Password=myPassword;Database=Demo";  
  
      static void Main(string[] args) {  
         SynchronousSqlBulkCopy();  
         AsyncSqlBulkCopy().Wait();  
         MixSyncAsyncSqlBulkCopy().Wait();  
         AsyncSqlBulkCopyNotifyAfter().Wait();  
         AsyncSqlBulkCopyDataRows().Wait();  
         // AsyncSqlBulkCopySqlServerToSqlAzure().Wait();  
         // AsyncSqlBulkCopyCancel().Wait();  
         AsyncSqlBulkCopyMARS().Wait();  
      }  
  
      // 3.1.1 Synchronous bulk copy in .NET 4.5  
      private static void SynchronousSqlBulkCopy() {  
         using (SqlConnection conn = new SqlConnection(connectionString)) {  
            conn.Open();  
            DataTable dt = new DataTable();  
            using (SqlCommand cmd = new SqlCommand(selectStatment, conn)) {  
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);  
               adapter.Fill(dt);  
  
               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
               cmd.CommandText = string.Format(createDestTableStatement, temptable);  
               cmd.ExecuteNonQuery();  
  
               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {  
                  bcp.DestinationTableName = temptable;  
                  bcp.WriteToServer(dt);  
               }  
            }  
         }  
  
      }  
  
      // 3.1.2 Asynchrounous bulk copy in .NET 4.5  
      private static async Task AsyncSqlBulkCopy() {  
         using (SqlConnection conn = new SqlConnection(connectionString)) {  
            await conn.OpenAsync();  
            DataTable dt = new DataTable();  
            using (SqlCommand cmd = new SqlCommand(selectStatment, conn)) {  
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);  
               adapter.Fill(dt);  
  
               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
               cmd.CommandText = string.Format(createDestTableStatement, temptable);  
               await cmd.ExecuteNonQueryAsync();  
  
               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {  
                  bcp.DestinationTableName = temptable;  
                  await bcp.WriteToServerAsync(dt);  
               }  
            }  
         }  
      }  
  
      // 3.2 Add new Async.NET capabilities in an existing application (Mixing synchronous and asynchornous calls)  
      private static async Task MixSyncAsyncSqlBulkCopy() {  
         using (OdbcConnection odbcconn = new OdbcConnection(odbcConnectionString)) {  
            odbcconn.Open();  
            using (OdbcCommand odbccmd = new OdbcCommand(selectStatment, odbcconn)) {  
               using (OdbcDataReader odbcreader = odbccmd.ExecuteReader()) {  
                  using (SqlConnection conn = new SqlConnection(connectionString)) {  
                     await conn.OpenAsync();  
                     string temptable = "temptable";//"[#" + Guid.NewGuid().ToString("N") + "]";  
                     SqlCommand createCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), conn);  
                     await createCmd.ExecuteNonQueryAsync();  
                     using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {  
                        bcp.DestinationTableName = temptable;  
                        await bcp.WriteToServerAsync(odbcreader);  
                     }  
                  }  
               }  
            }  
         }  
      }  
  
      // 3.3 Using the NotifyAfter property  
      private static async Task AsyncSqlBulkCopyNotifyAfter() {  
         using (SqlConnection conn = new SqlConnection(connectionString)) {  
            await conn.OpenAsync();  
            DataTable dt = new DataTable();  
            using (SqlCommand cmd = new SqlCommand(selectStatment, conn)) {  
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);  
               adapter.Fill(dt);  
  
               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
               cmd.CommandText = string.Format(createDestTableStatement, temptable);  
               await cmd.ExecuteNonQueryAsync();  
  
               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {  
                  bcp.DestinationTableName = temptable;  
                  bcp.NotifyAfter = 5;  
                  bcp.SqlRowsCopied += new SqlRowsCopiedEventHandler(OnSqlRowsCopied);  
                  await bcp.WriteToServerAsync(dt);  
               }  
            }  
         }  
      }  
  
      private static void OnSqlRowsCopied(object sender, SqlRowsCopiedEventArgs e) {  
         Console.WriteLine("Copied {0} so far...", e.RowsCopied);  
      }  
  
      // 3.4 Using the new SqlBulkCopy Async.NET capabilities with DataRow[]  
      private static async Task AsyncSqlBulkCopyDataRows() {  
         using (SqlConnection conn = new SqlConnection(connectionString)) {  
            await conn.OpenAsync();  
            DataTable dt = new DataTable();  
            using (SqlCommand cmd = new SqlCommand(selectStatment, conn)) {  
               SqlDataAdapter adapter = new SqlDataAdapter(cmd);  
               adapter.Fill(dt);  
               DataRow[] rows = dt.Select();  
  
               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
               cmd.CommandText = string.Format(createDestTableStatement, temptable);  
               await cmd.ExecuteNonQueryAsync();  
  
               using (SqlBulkCopy bcp = new SqlBulkCopy(conn)) {  
                  bcp.DestinationTableName = temptable;  
                  await bcp.WriteToServerAsync(rows);  
               }  
            }  
         }  
      }  
  
      // 3.5 Copying data from SQL Server to SQL Azure in .NET 4.5  
      //private static async Task AsyncSqlBulkCopySqlServerToSqlAzure() {  
      //   using (SqlConnection srcConn = new SqlConnection(connectionString))  
      //   using (SqlConnection destConn = new SqlConnection(azureConnectionString)) {  
      //      await srcConn.OpenAsync();  
      //      await destConn.OpenAsync();  
      //      using (SqlCommand srcCmd = new SqlCommand(selectStatment, srcConn)) {  
      //         using (SqlDataReader reader = await srcCmd.ExecuteReaderAsync()) {  
      //            string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
      //            using (SqlCommand destCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), destConn)) {  
      //               await destCmd.ExecuteNonQueryAsync();  
      //               using (SqlBulkCopy bcp = new SqlBulkCopy(destConn)) {  
      //                  bcp.DestinationTableName = temptable;  
      //                  await bcp.WriteToServerAsync(reader);  
      //               }  
      //            }  
      //         }  
      //      }  
      //   }  
      //}  
  
      // 3.6 Cancelling an Asynchronous Operation to SQL Azure  
      //private static async Task AsyncSqlBulkCopyCancel() {  
      //   CancellationTokenSource cts = new CancellationTokenSource();  
      //   using (SqlConnection srcConn = new SqlConnection(connectionString))  
      //   using (SqlConnection destConn = new SqlConnection(azureConnectionString)) {  
      //      await srcConn.OpenAsync(cts.Token);  
      //      await destConn.OpenAsync(cts.Token);  
      //      using (SqlCommand srcCmd = new SqlCommand(selectStatment, srcConn)) {  
      //         using (SqlDataReader reader = await srcCmd.ExecuteReaderAsync(cts.Token)) {  
      //            string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
      //            using (SqlCommand destCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), destConn)) {  
      //               await destCmd.ExecuteNonQueryAsync(cts.Token);  
      //               using (SqlBulkCopy bcp = new SqlBulkCopy(destConn)) {  
      //                  bcp.DestinationTableName = temptable;  
      //                  await bcp.WriteToServerAsync(reader, cts.Token);  
      //                  //Cancel Async SqlBulCopy Operation after 200 ms  
      //                  cts.CancelAfter(200);  
      //               }  
      //            }  
      //         }  
      //      }  
      //   }  
      //}  
  
      // 3.7 Using Async.Net and MARS  
      private static async Task AsyncSqlBulkCopyMARS() {  
         using (SqlConnection marsConn = new SqlConnection(marsConnectionString)) {  
            await marsConn.OpenAsync();  
  
            SqlCommand titlesCmd = new SqlCommand("SELECT * FROM [pubs].[dbo].[titles]", marsConn);  
            SqlCommand authorsCmd = new SqlCommand("SELECT * FROM [pubs].[dbo].[authors]", marsConn);  
            //With MARS we can have multiple active results sets on the same connection  
            using (SqlDataReader titlesReader = await titlesCmd.ExecuteReaderAsync())  
            using (SqlDataReader authorsReader = await authorsCmd.ExecuteReaderAsync()) {  
               await authorsReader.ReadAsync();  
  
               string temptable = "[#" + Guid.NewGuid().ToString("N") + "]";  
               using (SqlConnection destConn = new SqlConnection(connectionString)) {  
                  await destConn.OpenAsync();  
                  using (SqlCommand destCmd = new SqlCommand(string.Format(createDestTableStatement, temptable), destConn)) {  
                     await destCmd.ExecuteNonQueryAsync();  
                     using (SqlBulkCopy bcp = new SqlBulkCopy(destConn)) {  
                        bcp.DestinationTableName = temptable;  
                        await bcp.WriteToServerAsync(titlesReader);  
                     }  
                  }  
               }  
            }  
         }  
      }  
   }  
}  
```  
  
## <a name="asynchronously-using-multiple-commands-with-mars"></a>Asynchronicznie za pomocą wielu poleceń z MARS  
 Przykład otwiera pojedynczego połączenia **AdventureWorks** bazy danych. Przy użyciu <xref:System.Data.SqlClient.SqlCommand> obiektu, <xref:System.Data.SqlClient.SqlDataReader> jest tworzony. Jak czytnik jest używany, a drugie <xref:System.Data.SqlClient.SqlDataReader> jest otwarty przy użyciu danych z pierwszego <xref:System.Data.SqlClient.SqlDataReader> jako dane wejściowe do klauzuli WHERE dla drugiego czytnika.  
  
> [!NOTE]
>  W poniższym przykładzie użyto przykładowej **AdventureWorks** bazy danych programu SQL Server. W przykładowym kodzie w podanym ciągu połączenia przyjęto założenie, że baza danych jest zainstalowany i dostępny na komputerze lokalnym. Zmodyfikuj parametry połączenia w razie potrzeby dla danego środowiska.  
  
```csharp
using System;  
using System.Data;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class Class1 {  
   static void Main() {  
      Task task = MultipleCommands();  
      task.Wait();  
   }  
  
   static async Task MultipleCommands() {  
      // By default, MARS is disabled when connecting to a MARS-enabled.  
      // It must be enabled in the connection string.  
      string connectionString = GetConnectionString();  
  
      int vendorID;  
      SqlDataReader productReader = null;  
      string vendorSQL =  
        "SELECT VendorId, Name FROM Purchasing.Vendor";  
      string productSQL =  
        "SELECT Production.Product.Name FROM Production.Product " +  
        "INNER JOIN Purchasing.ProductVendor " +  
        "ON Production.Product.ProductID = " +  
        "Purchasing.ProductVendor.ProductID " +  
        "WHERE Purchasing.ProductVendor.VendorID = @VendorId";  
  
      using (SqlConnection awConnection =  
        new SqlConnection(connectionString)) {  
         SqlCommand vendorCmd = new SqlCommand(vendorSQL, awConnection);  
         SqlCommand productCmd =  
           new SqlCommand(productSQL, awConnection);  
  
         productCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
         await awConnection.OpenAsync();  
         using (SqlDataReader vendorReader = await vendorCmd.ExecuteReaderAsync()) {  
            while (await vendorReader.ReadAsync()) {  
               Console.WriteLine(vendorReader["Name"]);  
  
               vendorID = (int)vendorReader["VendorId"];  
  
               productCmd.Parameters["@VendorId"].Value = vendorID;  
               // The following line of code requires a MARS-enabled connection.  
               productReader = await productCmd.ExecuteReaderAsync();  
               using (productReader) {  
                  while (await productReader.ReadAsync()) {  
                     Console.WriteLine("  " +  
                       productReader["Name"].ToString());  
                  }  
               }  
            }  
         }  
      }  
   }  
  
   private static string GetConnectionString() {  
      // To avoid storing the connection string in your code, you can retrive it from a configuration file.  
      return "Data Source=(local);Integrated Security=SSPI;Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";  
   }  
}  
```  
  
## <a name="asynchronously-reading-and-updating-data-with-mars"></a>Asynchronicznie odczytywanie i aktualizowanie danych za pomocą MARS  
 MARS umożliwia połączenie ma być używany dla obu operacje odczytu dla operacji i danych manipulacji języka z więcej niż jednym oczekującą operację. Ta funkcja eliminuje potrzebę stosowania aplikacji biznesowych w radzeniu sobie z błędami zajęty połączenia. Ponadto MARS można zastąpić użytkownika kursorów po stronie serwera, które zazwyczaj zużywać więcej zasobów. Na koniec, ponieważ wiele operacji może działać w ramach pojedynczego połączenia, mogą współużytkować tego samego kontekstu transakcji, eliminuje konieczność użycia **sp_getbindtoken** i **procedury sp_bindsession** przechowywana w systemie procedury.  
  
 Następującej aplikacji konsoli Pokazuje, jak korzystać z dwóch <xref:System.Data.SqlClient.SqlDataReader> obiektów, z których trzy <xref:System.Data.SqlClient.SqlCommand> obiektów i jeden <xref:System.Data.SqlClient.SqlConnection> obiektu z włączoną MARS. Pierwszy obiekt polecenie pobiera listę dostawców, których zdolności kredytowej wynosi 5. Drugi obiekt polecenia używa dostawcy podany identyfikator z <xref:System.Data.SqlClient.SqlDataReader> załadować drugi <xref:System.Data.SqlClient.SqlDataReader> z wszystkich produktów dla określonego dostawcy. Każdy rekord produktu odwiedzenia przez drugą <xref:System.Data.SqlClient.SqlDataReader>. Obliczeń do określenia, jakie nowe **OnOrderQty** powinien być. Trzeci obiektu command jest następnie używany do aktualizacji **ProductVendor** tabeli przy użyciu nowej wartości. Całego procesu odbywa się w ramach jednej transakcji jest przywracana na końcu.  
  
> [!NOTE]
>  W poniższym przykładzie użyto przykładowej **AdventureWorks** bazy danych programu SQL Server. W przykładowym kodzie w podanym ciągu połączenia przyjęto założenie, że baza danych jest zainstalowany i dostępny na komputerze lokalnym. Zmodyfikuj parametry połączenia w razie potrzeby dla danego środowiska.  
  
```csharp
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Data;  
using System.Data.SqlClient;  
using System.Threading.Tasks;  
  
class Program {  
   static void Main() {  
      Task task = ReadingAndUpdatingData();  
      task.Wait();  
   }  
  
   static async Task ReadingAndUpdatingData() {  
      // By default, MARS is disabled when connecting to a MARS-enabled host.  
      // It must be enabled in the connection string.  
      string connectionString = GetConnectionString();  
  
      SqlTransaction updateTx = null;  
      SqlCommand vendorCmd = null;  
      SqlCommand prodVendCmd = null;  
      SqlCommand updateCmd = null;  
  
      SqlDataReader prodVendReader = null;  
  
      int vendorID = 0;  
      int productID = 0;  
      int minOrderQty = 0;  
      int maxOrderQty = 0;  
      int onOrderQty = 0;  
      int recordsUpdated = 0;  
      int totalRecordsUpdated = 0;  
  
      string vendorSQL =  
          "SELECT VendorID, Name FROM Purchasing.Vendor " +  
          "WHERE CreditRating = 5";  
      string prodVendSQL =  
          "SELECT ProductID, MaxOrderQty, MinOrderQty, OnOrderQty " +  
          "FROM Purchasing.ProductVendor " +  
          "WHERE VendorID = @VendorID";  
      string updateSQL =  
          "UPDATE Purchasing.ProductVendor " +  
          "SET OnOrderQty = @OrderQty " +  
          "WHERE ProductID = @ProductID AND VendorID = @VendorID";  
  
      using (SqlConnection awConnection =  
        new SqlConnection(connectionString)) {  
         await awConnection.OpenAsync();  
         updateTx = await Task.Run(() => awConnection.BeginTransaction());  
  
         vendorCmd = new SqlCommand(vendorSQL, awConnection);  
         vendorCmd.Transaction = updateTx;  
  
         prodVendCmd = new SqlCommand(prodVendSQL, awConnection);  
         prodVendCmd.Transaction = updateTx;  
         prodVendCmd.Parameters.Add("@VendorId", SqlDbType.Int);  
  
         updateCmd = new SqlCommand(updateSQL, awConnection);  
         updateCmd.Transaction = updateTx;  
         updateCmd.Parameters.Add("@OrderQty", SqlDbType.Int);  
         updateCmd.Parameters.Add("@ProductID", SqlDbType.Int);  
         updateCmd.Parameters.Add("@VendorID", SqlDbType.Int);  
  
         using (SqlDataReader vendorReader = await vendorCmd.ExecuteReaderAsync()) {  
            while (await vendorReader.ReadAsync()) {  
               Console.WriteLine(vendorReader["Name"]);  
  
               vendorID = (int)vendorReader["VendorID"];  
               prodVendCmd.Parameters["@VendorID"].Value = vendorID;  
               prodVendReader = await prodVendCmd.ExecuteReaderAsync();  
  
               using (prodVendReader) {  
                  while (await prodVendReader.ReadAsync()) {  
                     productID = (int)prodVendReader["ProductID"];  
  
                     if (prodVendReader["OnOrderQty"] == DBNull.Value) {  
                        minOrderQty = (int)prodVendReader["MinOrderQty"];  
                        onOrderQty = minOrderQty;  
                     }  
                     else {  
                        maxOrderQty = (int)prodVendReader["MaxOrderQty"];  
                        onOrderQty = (int)(maxOrderQty / 2);  
                     }  
  
                     updateCmd.Parameters["@OrderQty"].Value = onOrderQty;  
                     updateCmd.Parameters["@ProductID"].Value = productID;  
                     updateCmd.Parameters["@VendorID"].Value = vendorID;  
  
                     recordsUpdated = await updateCmd.ExecuteNonQueryAsync();  
                     totalRecordsUpdated += recordsUpdated;  
                  }  
               }  
            }  
         }  
         Console.WriteLine("Total Records Updated: ", totalRecordsUpdated.ToString());  
         await Task.Run(() => updateTx.Rollback());  
         Console.WriteLine("Transaction Rolled Back");  
      }  
   }  
  
   private static string GetConnectionString() {  
      // To avoid storing the connection string in your code, you can retrive it from a configuration file.  
      return "Data Source=(local);Integrated Security=SSPI;Initial Catalog=AdventureWorks;MultipleActiveResultSets=True";  
   }  
}  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Pobieranie i modyfikowanie danych ADO.NET](../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)
