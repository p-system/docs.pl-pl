---
title: 'Porady: wykonywanie zapytań usługi danych asynchronicznych (usługi danych WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
ms.assetid: 902a2dc1-d0e9-4b00-90a8-becc4cb1f6a7
ms.openlocfilehash: 4d8e8f15bbb1efeb0b26e452d1b2a51772be9ed7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33358716"
---
# <a name="how-to-execute-asynchronous-data-service-queries-wcf-data-services"></a>Porady: wykonywanie zapytań usługi danych asynchronicznych (usługi danych WCF)
Za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] biblioteki klienta asynchroniczne operacje można wykonywać klient serwer, takich jak wykonywanie kwerend i zapisywania zmian. Aby uzyskać więcej informacji, zobacz [operacji asynchronicznych](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
> [!NOTE]
>  W aplikacji, gdzie należy wywołać metodę wywołania zwrotnego na konkretnym wątkiem, musisz jawnie kierować wykonywanie <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metody. Aby uzyskać więcej informacji, zobacz [operacji asynchronicznych](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md).  
  
 Przykład, w tym temacie korzysta z Northwind przykładowych danych wygenerowany automatycznie i usługi klienta danych usługi klas. Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób wykonania zapytania asynchronicznego przez wywołanie metody <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metodę, aby uruchomić zapytanie. Wbudowanej delegata wywołania <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> metodę w celu wyświetlenia wyników zapytania.  
  
 [!code-csharp[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#executequeryasync)]
 [!code-vb[Astoria Northwind Client#ExecuteQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#executequeryasync)]  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
