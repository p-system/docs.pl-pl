---
title: "Dane binarne i duża wartość serwera SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e00827b3-7511-4b2d-91d7-851ca86cc6b5
caps.latest.revision: "5"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 9065f467cd353c17471db2c0d67001a188459819
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="sql-server-binary-and-large-value-data"></a><span data-ttu-id="2182b-102">Dane binarne i duża wartość serwera SQL</span><span class="sxs-lookup"><span data-stu-id="2182b-102">SQL Server Binary and Large-Value Data</span></span>
<span data-ttu-id="2182b-103">Program SQL Server stanowi `max` specyfikator, który zwiększa pojemność `varchar`, `nvarchar`, i `varbinary` typy danych.</span><span class="sxs-lookup"><span data-stu-id="2182b-103">SQL Server provides the `max` specifier, which expands the storage capacity of the `varchar`, `nvarchar`, and `varbinary` data types.</span></span> <span data-ttu-id="2182b-104">`varchar(max)`, `nvarchar(max)`, i `varbinary(max)` są nazywane *typów danych dużych wartości*.</span><span class="sxs-lookup"><span data-stu-id="2182b-104">`varchar(max)`, `nvarchar(max)`, and `varbinary(max)` are collectively called *large-value data types*.</span></span> <span data-ttu-id="2182b-105">Typy danych dużej wartości umożliwiają przechowywanie maksymalnie 2 ^ 31-1 bajtów danych.</span><span class="sxs-lookup"><span data-stu-id="2182b-105">You can use the large-value data types to store up to 2^31-1 bytes of data.</span></span>  
  
 <span data-ttu-id="2182b-106">SQL Server 2008 wprowadza atrybut FILESTREAM, który jest typem danych, ale raczej atrybut, który jest zdefiniowany dla kolumny, dzięki czemu duża wartość danych do przechowywania w systemie plików, zamiast w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="2182b-106">SQL Server 2008 introduces the FILESTREAM attribute, which is not a data type, but rather an attribute that can be defined on a column, allowing large-value data to be stored on the file system instead of in the database.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="2182b-107">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="2182b-107">In This Section</span></span>  
 [<span data-ttu-id="2182b-108">Modyfikowanie dużej wartości (wartość maksymalna) danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2182b-108">Modifying Large-Value (max) Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/modifying-large-value-max-data.md)  
 <span data-ttu-id="2182b-109">Opisuje sposób pracy z typami danych dużej wartości.</span><span class="sxs-lookup"><span data-stu-id="2182b-109">Describes how to work with the large-value data types.</span></span>  
  
 [<span data-ttu-id="2182b-110">Danych FILESTREAM</span><span class="sxs-lookup"><span data-stu-id="2182b-110">FILESTREAM Data</span></span>](../../../../../docs/framework/data/adonet/sql/filestream-data.md)  
 <span data-ttu-id="2182b-111">Opisuje sposób pracy z danymi dużej wartości przechowywane w programie SQL Server 2008 mających atrybut FILESTREAM.</span><span class="sxs-lookup"><span data-stu-id="2182b-111">Describes how to work with large-value data stored in SQL Server 2008 with the FILESTREAM attribute.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2182b-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2182b-112">See Also</span></span>  
 [<span data-ttu-id="2182b-113">Danych programu SQL Server typy i ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2182b-113">SQL Server Data Types and ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-types.md)  
 [<span data-ttu-id="2182b-114">Operacje danych serwera SQL w ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2182b-114">SQL Server Data Operations in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/sql/sql-server-data-operations.md)  
 [<span data-ttu-id="2182b-115">Trwa pobieranie i modyfikowanie danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2182b-115">Retrieving and Modifying Data in ADO.NET</span></span>](../../../../../docs/framework/data/adonet/retrieving-and-modifying-data.md)  
 [<span data-ttu-id="2182b-116">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="2182b-116">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)