---
title: Obsługa błędów protokołu HTTP sieci Web w programie WCF
ms.date: 03/30/2017
ms.assetid: 02891563-0fce-4c32-84dc-d794b1a5c040
ms.openlocfilehash: 228f8cdbe5ddde63f2b6afd82a27055f2241e058
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498488"
---
# <a name="wcf-web-http-error-handling"></a>Obsługa błędów protokołu HTTP sieci Web w programie WCF
Obsługa błędów protokołu HTTP sieci Web Windows Communication Foundation (WCF) umożliwia zwracanie błędów z usług WCF Web HTTP, które określają kod stanu HTTP i zwracać szczegóły błędu przy użyciu tego samego formatu co operacji (na przykład, XML lub JSON).  
  
## <a name="wcf-web-http-error-handling"></a>Obsługa błędów protokołu HTTP sieci Web w programie WCF  
 <xref:System.ServiceModel.Web.WebFaultException> Klasa definiuje konstruktora, który pozwala określić kod stanu HTTP. Ten kod stanu jest następnie zwracany do klienta. Ogólny wersji <xref:System.ServiceModel.Web.WebFaultException> klasy <xref:System.ServiceModel.Web.WebFaultException%601> pozwala na zwracany typ zdefiniowane przez użytkownika, który zawiera informacje o błędzie, który wystąpił. Ten obiekt niestandardowy jest serializowany w formacie określonym przez operację i zwracany do klienta. Poniższy przykład przedstawia sposób zwrócenia kod stanu HTTP.  
  
```  
Public string Operation1()  
{   // Operation logic  
   // ...  
   Throw new WebFaultException(HttpStatusCode.Forbidden);  
}  
```  
  
 Poniższy przykład przedstawia sposób zwracania kod stanu HTTP i informacje dodatkowe na typu zdefiniowanego przez użytkownika. `MyErrorDetail` jest zdefiniowane przez użytkownika typu, który zawiera dodatkowe informacje o błędzie, który wystąpił.  
  
```  
Public string Operation2()  
   // Operation logic  
   // ...   MyErrorDetail detail = new MyErrorDetail  
   {  
      Message = "Error Message",  
      ErrorCode = 123,  
   }  
   throw new WebFaultException<MyErrorDetail>(detail, HttpStatusCode.Forbidden);  
}  
```  
  
 Poprzedni kod zwraca odpowiedź HTTP z kodem stanu niedozwolonych i treści, która zawiera wystąpienie `MyErrorDetails` obiektu. Format `MyErrorDetails` obiektu jest określane przez:  
  
-   Wartość `ResponseFormat` parametr <xref:System.ServiceModel.Web.WebGetAttribute> lub <xref:System.ServiceModel.Web.WebInvokeAttribute> określonego w operacji usługi.  
  
-   Wartość <xref:System.ServiceModel.Description.WebHttpBehavior.AutomaticFormatSelectionEnabled%2A>.  
  
-   Wartość <xref:System.ServiceModel.Web.OutgoingWebResponseContext.Format%2A> właściwości uzyskując dostęp do <xref:System.ServiceModel.Web.OutgoingWebResponseContext>.  
  
 Aby uzyskać więcej informacji o wpływie na formatowanie operacji tych wartości, zobacz [formatowania HTTP sieci Web WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md).  
  
 <xref:System.ServiceModel.Web.WebFaultException> jest <xref:System.ServiceModel.FaultException> i w związku z tym może służyć jako model programowania wyjątek błędów dla usług, które ekspozycji punktów końcowych SOAP, a także punktów końcowych HTTP w sieci web.  
  
## <a name="see-also"></a>Zobacz też  
 [Model programowania protokołu HTTP sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [Formatowanie kodu HTTP dla sieci Web w programie WCF](../../../../docs/framework/wcf/feature-details/wcf-web-http-formatting.md)  
 [Definiowanie i określanie błędów](../../../../docs/framework/wcf/defining-and-specifying-faults.md)  
 [Obsługa wyjątków i błędów](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md)  
 [Wysyłanie i odbieranie błędów](../../../../docs/framework/wcf/sending-and-receiving-faults.md)
