---
title: Formatowanie wiadomości w usług przepływu pracy
ms.date: 03/30/2017
ms.assetid: 6d15d44b-20f8-4cb7-bd4f-598c32781ebc
ms.openlocfilehash: eac9f7042dbcbd31f9a8c7d5e56c7b7d2ab62156
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33513789"
---
# <a name="formatting-messages-in-workflow-services"></a>Formatowanie wiadomości w usług przepływu pracy
W tym przykładzie pokazano sposób inny użytkownik, typy mogą być używane w działaniach obsługi komunikatów (WF usługi). Usługa próbki jest usługą zatwierdzenia proste wydatków i udostępnia trzy operacje. `ApproveExpense` pobiera typ kontraktu danych i przedstawia sposób użycia znanych typów. Zwraca operacji `true` lub `false` na podstawie ilości wydatków. `ApprovePO` pobiera typ elementu XmlSerializer i zwraca `true` lub `false` na podstawie ilości wydatków.`ApprovedVendor` pobiera typ kontraktu komunikatu i zwraca `true` lub `false` Jeśli dostawca znajduje się lista zatwierdzonych dostawców lub jeśli żądanie pochodzi z działu finansowego (dział finansowy może używać dowolnego dostawcy).  
  
#### <a name="to-use-this-sample"></a>Aby użyć tego przykładu  
  
1.  Załadowanie projektu rozwiązania w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i skompilować projekt.  
  
2.  Najpierw uruchom usługę wygenerowanych w \FormatterService\bin\debug\ [katalogu podstawowego rozwiązania]  
  
3.  Po drugie Uruchom aplikację klienta wygenerowanego w \FormatterClient\bin\debug [katalogu podstawowego rozwiązania].  
  
4.  Klient wymaga trzech operacji w usłudze i wyświetla wyniki. Po zakończeniu naciśnij klawisz ENTER, aby zamknąć klienta, a następnie usługi.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\Formatter`