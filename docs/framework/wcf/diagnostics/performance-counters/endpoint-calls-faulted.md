---
title: "Punkt końcowy: Wywołania zwracające błędy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 271e6284-9c4b-465f-b619-069e1555a5e4
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e0997050887721f4b72eb2a69f41be966936b25c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="endpoint-calls-faulted"></a><span data-ttu-id="73281-102">Punkt końcowy: Wywołania zwracające błędy</span><span class="sxs-lookup"><span data-stu-id="73281-102">Endpoint: Calls Faulted</span></span>
<span data-ttu-id="73281-103">Nazwa licznika: Wywołania zwracające błędy.</span><span class="sxs-lookup"><span data-stu-id="73281-103">Counter Name: Calls Faulted.</span></span>  
  
## <a name="description"></a><span data-ttu-id="73281-104">Opis</span><span class="sxs-lookup"><span data-stu-id="73281-104">Description</span></span>  
 <span data-ttu-id="73281-105">Liczba wywołań tego punktu końcowego, które zwrócone błędy.</span><span class="sxs-lookup"><span data-stu-id="73281-105">Number of calls to this endpoint that have returned faults.</span></span> <span data-ttu-id="73281-106">W [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] komunikacji metody usług aplikacji, przetwarzania przy użyciu protokołu SOAP komunikatów "fault" informacje o błędzie.</span><span class="sxs-lookup"><span data-stu-id="73281-106">In [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] applications, service methods communicate processing error information using SOAP fault messages.</span></span> <span data-ttu-id="73281-107">Błędach SOAP są typów komunikatów, które są zawarte w metadanych dla operacji usługi i dlatego należy utworzyć kontrakt błędu, w której klienci mogą używać, aby ich wykonanie bardziej niezawodne lub interakcyjne.</span><span class="sxs-lookup"><span data-stu-id="73281-107">SOAP faults are message types that are included in the metadata for a service operation and therefore create a fault contract that clients can use to make their execution more robust or interactive.</span></span> <span data-ttu-id="73281-108">Ponieważ błędach SOAP są wyrażane klientom w postaci XML, są one bardzo interoperacyjne.</span><span class="sxs-lookup"><span data-stu-id="73281-108">Since SOAP faults are expressed to clients in XML form, they are highly interoperable.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73281-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="73281-109">See Also</span></span>  
 [<span data-ttu-id="73281-110">Określanie i obsługa błędów w kontraktach i usługach</span><span class="sxs-lookup"><span data-stu-id="73281-110">Specifying and Handling Faults in Contracts and Services</span></span>](../../../../../docs/framework/wcf/specifying-and-handling-faults-in-contracts-and-services.md)