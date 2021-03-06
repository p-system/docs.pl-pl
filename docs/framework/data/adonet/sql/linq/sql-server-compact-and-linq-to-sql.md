---
title: SQL Server Compact i LINQ do SQL
ms.date: 03/30/2017
ms.assetid: 59022359-a5a2-4c42-9a6a-5c0259c3ad17
ms.openlocfilehash: 74b8a7a6dfc9a4050dbba9a8c2f6969dba42656c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33355789"
---
# <a name="sql-server-compact-and-linq-to-sql"></a>SQL Server Compact i LINQ do SQL
SQL Server Compact to domyślna baza danych zainstalowana z programem Visual Studio. Aby uzyskać więcej informacji, zobacz [Pave – za pośrednictwem przy użyciu programu SQL Server Compact (Visual Studio)](http://msdn.microsoft.com/library/13320dd1-94e5-4077-bf76-8df253695ccc).  
  
 W tym temacie przedstawiono podstawowe różnice w użycia, konfiguracji, zestawy funkcji i zakres [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje.  
  
## <a name="characteristics-of-sql-server-compact-in-relation-to-linq-to-sql"></a>Właściwości programu SQL Server Compact w odniesieniu do LINQ do SQL  
 Domyślnie program SQL Server Compact są zainstalowane dla wszystkich wersji programu Visual Studio i w związku z tym jest dostępny na komputerze dewelopera do użycia z [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]. Wdrażanie aplikacji, która używa programu SQL Server Compact, ale i [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] różni się od aplikacji serwera SQL. SQL Server Compact nie jest częścią programu .NET Framework i w związku z tym musi być z aplikacji lub oddzielnie pobrane z witryny Microsoft.  
  
 Należy uwzględnić następujące cechy:  
  
-   SQL Server Compact, jest dostarczana jako bibliotekę DLL, która może służyć do atakowania pliki bazy danych (z rozszerzeniem sdf) bezpośrednio.  
  
-   SQL Server Compact działa w ten sam proces jako aplikacja klienta. Wydajność programu SQL Server Compact komunikacji w związku z tym może być znacznie wyższa niż komunikacji z serwerem SQL. Z drugiej strony programu SQL Server Compact wymagają współdziałanie zarządzane i niezarządzane kodu przy użyciu jego koszty związane.  
  
-   Rozmiar programu SQL Server Compact biblioteki DLL jest mała. Ta funkcja pozwala zmniejszyć rozmiar ogólną aplikacji.  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] Środowiska uruchomieniowego i narzędzie wiersza polecenia SQLMetal obsługuje program SQL Server Compact.  
  
-   [!INCLUDE[vs_ordesigner_long](../../../../../../includes/vs-ordesigner-long-md.md)] Nie obsługuje programu SQL Server Compact.  
  
## <a name="feature-set"></a>Zestaw funkcji  
 SQL Server Compact zestaw funkcji jest znacznie prostsze niż zestaw funkcji programu SQL Server w następujący sposób, który może mieć wpływ na [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] aplikacji:  
  
-   SQL Server Compact nie obsługuje procedur składowanych ani widoków.  
  
-   SQL Server Compact obsługuje tylko typy danych i funkcji SQL.  
  
-   SQL Server Compact obsługuje tylko podzestaw konstrukcji SQL.  
  
-   SQL Server Compact zawiera tylko minimalne optymalizację. Istnieje możliwość, że niektórych kwerend może upłynął limit czasu.  
  
-   SQL Server Compact nie obsługuje częściowej relacji zaufania.  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
