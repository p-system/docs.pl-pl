---
title: "Porady: wykonywanie zapytań w partii (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: WCF Data Services, batch requests
ms.assetid: 3b4db7df-bd33-43a1-8ea4-63a18e131f97
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 384274b127e04004117cbb2f6d5f7764c3212d0b
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-execute-queries-in-a-batch-wcf-data-services"></a><span data-ttu-id="a1449-102">Porady: wykonywanie zapytań w partii (usługi danych WCF)</span><span class="sxs-lookup"><span data-stu-id="a1449-102">How to: Execute Queries in a Batch (WCF Data Services)</span></span>
<span data-ttu-id="a1449-103">Za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienta, można wykonać zapytania więcej niż jeden z usługą danych w pojedynczej partii.</span><span class="sxs-lookup"><span data-stu-id="a1449-103">By using the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] client library, you can execute more than one query against the data service in a single batch.</span></span> <span data-ttu-id="a1449-104">Aby uzyskać więcej informacji, zobacz [przetwarzanie wsadowe operacji](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="a1449-104">For more information, see [Batching Operations](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="a1449-105">Przykład, w tym temacie korzysta z Northwind przykładowych danych wygenerowany automatycznie i usługi klienta danych usługi klas.</span><span class="sxs-lookup"><span data-stu-id="a1449-105">The example in this topic uses the Northwind sample data service and autogenerated client data service classes.</span></span> <span data-ttu-id="a1449-106">Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span><span class="sxs-lookup"><span data-stu-id="a1449-106">This service and the client data classes are created when you complete the [WCF Data Services quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1449-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1449-107">Example</span></span>  
 <span data-ttu-id="a1449-108">Poniższy przykład przedstawia sposób wywołania <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> metoda używana tablica <xref:System.Data.Services.Client.DataServiceRequest%601> obiektów, które zawiera zapytań zwracających zarówno `Customers` i `Products` obiektów z usług danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="a1449-108">The following example shows how to call the <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> method to execute an array of <xref:System.Data.Services.Client.DataServiceRequest%601> objects that contains queries that return both `Customers` and `Products` objects from the Northwind data service.</span></span> <span data-ttu-id="a1449-109">Kolekcja <xref:System.Data.Services.Client.QueryOperationResponse%601> obiektów w zwróconym <xref:System.Data.Services.Client.DataServiceResponse> wyliczeniu i kolekcję obiektów zawartą w każdym <xref:System.Data.Services.Client.QueryOperationResponse%601> również wyliczeniu.</span><span class="sxs-lookup"><span data-stu-id="a1449-109">The collection of <xref:System.Data.Services.Client.QueryOperationResponse%601> objects in the returned <xref:System.Data.Services.Client.DataServiceResponse> is enumerated, and the collection of objects contained in each <xref:System.Data.Services.Client.QueryOperationResponse%601> is also enumerated.</span></span>  
  
 [!code-csharp[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#batchquery)]
 [!code-vb[Astoria Northwind Client#BatchQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#batchquery)]  
  
## <a name="see-also"></a><span data-ttu-id="a1449-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1449-110">See Also</span></span>  
 [<span data-ttu-id="a1449-111">Biblioteka klienta usługi danych WCF</span><span class="sxs-lookup"><span data-stu-id="a1449-111">WCF Data Services Client Library</span></span>](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)