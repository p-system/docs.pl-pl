---
title: Transakcyjne kolejki.
ms.date: 03/30/2017
ms.assetid: b1b011dd-5e0b-482c-9bb0-9d8727038f14
ms.openlocfilehash: b125158a113079d87eb6926393d5a2b5fe326824
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519684"
---
# <a name="transacted-queues"></a>Transakcyjne kolejki.
W tym przykładzie pokazano, jak zintegrować kolejek oraz transakcje w systemie Windows Workflow Foundation (WF) do tworzenia niezawodnych i skalowalnych usług. A <!--zz <xref:System.Activities.TransactionScope>--> `System.Activities.TransactionScope` jest używany w przepływie pracy klienta do wysyłania wiadomości do kolejki w transakcji za pomocą <xref:System.ServiceModel.NetMsmqBinding>. A <xref:System.ServiceModel.Activities.TransactedReceiveScope> jest używany na serwerze do odbierania wiadomości z kolejki i zaktualizowanie stanu przepływu pracy w tej samej transakcji.  
  
## <a name="demonstrates"></a>Demonstracje  
 <xref:System.Activities.Statements.TransactionScope>, <xref:System.ServiceModel.Activities.TransactedReceiveScope>, <xref:System.ServiceModel.NetMsmqBinding>, <xref:System.ServiceModel.Activities.Receive>i na podstawie zawartości korelacji.  
  
## <a name="discussion"></a>Omówienie  
 Aby zademonstrować funkcje omówione w tym przykładzie `RewardsPoints` usługi przepływu pracy został utworzony, która przechowuje informacje o punktach zdobytych i używany dla danego konta. Klient używa <xref:System.Activities.WorkflowInvoker> do symulowania zamieszczając różnych żądań w kolejce. Aby wysłać wiadomość do kolejki w ramach transakcji <xref:System.ServiceModel.Activities.Send> działania może być umieszczony wewnątrz <xref:System.Activities.Statements.TransactionScope.Body%2A> z <xref:System.Activities.Statements.TransactionScope>. W tym przykładzie klient uruchamia najpierw następuje serwera, aby zademonstrować sposób umieszczonych w kolejce wiadomości mogą rozdzielenie klienta i serwera aplikacji.  
  
 Po zakończeniu pracy klienta, skonfigurowane i usługi hostowanej. Zaraz po otwarciu, rozpoczyna przetwarzanie komunikatów, które już zostały umieszczone w kolejce. Każdy komunikat jest odbierany i przetwarzany w tej samej transakcji serwera. W tym przykładzie jest pierwszy komunikat `CreateAccount` żądania, która tworzy wystąpienie i inicjuje korelację zawartości na podstawie nazwy konta przekazanych jako część komunikatu żądania. Modelowanie rodzaj usługi może oczekiwać w świecie rzeczywistym dwa <xref:System.ServiceModel.Activities.TransactedReceiveScope> działań, które przetwarzają `AddPoints` i `UsePoints` wiadomości są umieszczane w równoległych gałęziach w `while` pętli, dzięki czemu mogą one przetworzone komunikaty wielokrotnie w dowolnej kolejności.  
  
 <xref:System.Activities.Statements.TransactionScope> i <xref:System.ServiceModel.Activities.TransactedReceiveScope> ma każdego punktu niejawne trwałości na końcu ich zakresy przy użyciu tych działań w [!INCLUDE[wf1](../../../../includes/wf1-md.md)] połączeniu z kolejek jest to niezawodny sposób przenoszenia przepływu pracy z jednego spójnego stanu do następnego, przy jednoczesnym zapewnieniu, że komunikaty są nigdy nie zostanie utracone.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Aby skonfigurować, kompilacji, a następnie uruchom próbki  
  
1.  Instalowanie i konfigurowanie usługi MSMQ. Zobacz [Instalowanie usługi kolejkowania komunikatów](http://go.microsoft.com/fwlink/?LinkId=178526) szczegółowe informacje.  
  
2.  Upewnij się, że usługa MSDTC jest uruchomiona, wykonując następujące polecenie w wierszu polecenia. `net start msdtc`  
  
3.  Skompiluj projekt i otworzyć plik wykonywalny lub Otwórz projekt w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] i wybierz opcję uruchomienia z menu Debugowanie. Najpierw tworzenia kolejki, a następnie klient uruchamia i przesyła wiadomości do kolejki i na koniec uruchomienia usługi i komunikaty są przetwarzane. Aby zakończyć działanie programu, naciśnij klawisz ENTER.  
  
> [!IMPORTANT]
>  Próbki mogą być zainstalowane na tym komputerze. Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) do pobrania wszystkich Windows Communication Foundation (WCF) i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek. W tym przykładzie znajduje się w następującym katalogu.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedQueues`
