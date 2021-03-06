---
title: Elementy wewnętrzne hosta usługi przepływu pracy
ms.date: 03/30/2017
ms.assetid: af44596f-bf6a-4149-9f04-08d8e8f45250
ms.openlocfilehash: 55458dce498ac2630b7c69b743e0c0df1d5c4e92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505508"
---
# <a name="workflow-service-host-internals"></a>Elementy wewnętrzne hosta usługi przepływu pracy
<xref:System.ServiceModel.WorkflowServiceHost> zapewnia hosta usługi przepływu pracy. Odpowiada do nasłuchiwania dla komunikatów przychodzących i routingu je do odpowiednich przepływu pracy wystąpienie usługi, kontroluje zwalnianie i przechowywanie bezczynne przepływy pracy i więcej. W tym temacie opisano, jak obiekt WorkflowServiceHost przetwarza wiadomości przychodzących.  
  
## <a name="workflowservicehost-overview"></a>Omówienie obiektu WorkflowServiceHost  
 <xref:System.ServiceModel.WorkflowServiceHost> Klasa jest używana do hostowania usług przepływu pracy. On nasłuchuje przychodzących wiadomości i kieruje je do wystąpienia odpowiednią usługę, tworzenie nowych wystąpień lub załadować istniejących wystąpień z magazynu trwałego zgodnie z potrzebami.  Na poniższym diagramie przedstawiono dotyczące wysokiego poziomu <xref:System.ServiceModel.WorkflowServiceHost> działa.  
  
 ![Omówienie obiektu WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/media/wfshhighlevel.gif "WFSHHighLevel")  
  
 Ten diagram przedstawia który <xref:System.ServiceModel.WorkflowServiceHost> ładuje definicji usługi przepływu pracy z plików .xamlx i ładuje informacje o konfiguracji z pliku konfiguracji. Ładuje również konfigurację śledzenia, z profilu śledzenia. <xref:System.ServiceModel.WorkflowServiceHost> udostępnia punkt końcowy kontroli przepływu pracy, dzięki czemu można wysyłać operacji kontroli do wystąpienia przepływu pracy.  Aby uzyskać więcej informacji, zobacz [punkt końcowy kontroli przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md) i [przepływu pracy zarządzania punktu końcowego próbki](../../../../docs/framework/windows-workflow-foundation/samples/workflow-management-endpoint-sample.md).  
  
 <xref:System.ServiceModel.WorkflowServiceHost> udostępnia również punkty końcowe aplikacji, które nasłuchuje przychodzących komunikatów aplikacji. Po odebraniu komunikatu przychodzącego (jeśli jest aktualnie załadowany) są wysyłane do przepływu pracy odpowiednie wystąpienie usługi. W razie potrzeby nowego wystąpienia przepływu pracy jest tworzony. Lub jeśli utrwaleniu istniejące wystąpienie jest ładowany w sklepie trwałości.  
  
## <a name="workflowservicehost-details"></a>Szczegóły obiektu WorkflowServiceHost  
 Na poniższym diagramie przedstawiono sposób <xref:System.ServiceModel.WorkflowServiceHost> obsługuje komunikaty nieco bardziej szczegółowo.  
  
 ![Przepływ komunikatów hosta usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/media/wfshmessageflow.gif "WFSHMessageFlow")  
  
 Ten diagram przedstawia trzy różne punkty końcowe, punkt końcowy aplikacji, punkt końcowy kontroli przepływu pracy i punktu końcowego hostingu przepływu pracy. Punkt końcowy aplikacji odbiera komunikaty, które są powiązane wystąpienia określonego przepływu pracy. Punkt końcowy kontroli przepływu pracy nasłuchuje operacji kontroli. Punkt końcowy obsługującym przepływ pracy nasłuchuje wiadomości, które powodują <xref:System.ServiceModel.WorkflowServiceHost> do ładowania i wykonywania innych niż usługowe przepływów pracy. Jak pokazano na rysunku wszystkie komunikaty są przetwarzane przez środowisko wykonawcze usługi WCF.  Ograniczanie wystąpienia usługi przepływu pracy jest realizowane za pośrednictwem <xref:System.ServiceModel.Description.ServiceThrottlingBehavior.MaxConcurrentInstances%2A> właściwości. Ta właściwość będzie ograniczyć liczbę wystąpień usługi jednoczesnych przepływów pracy. Po przekroczeniu wszelkie dodatkowe tej przepustnicy żądań dla nowych wystąpień usługi przepływu pracy lub żądań do aktywowania wystąpień przepływów pracy utrwalonych zostaną umieszczone w kolejce. Żądań w kolejce są przetwarzane w kolejności FIFO niezależnie od tego, czy są one żądania dotyczące nowego wystąpienia lub uruchomione wystąpienie utrwalonych. Informacje o zasadach hosta jest ładowany określającą, jak zostały omówione nieobsługiwanych wyjątków i jak usług bezczynności przepływu pracy są zwolnione i utrwalone. Aby uzyskać więcej informacji na temat tych tematów w temacie [porady: Konfigurowanie przepływu pracy nieobsługiwany wyjątek zachowanie przy użyciu klasy WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md) i [porady: Konfigurowanie zachowania bezczynności za pomocą elementu WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-idle-behavior-with-workflowservicehost.md). Wystąpienia przepływu pracy są zachowywane zgodnie z zasadami hosta i są ładowane w razie potrzeby. Aby uzyskać więcej informacji o trwałości przepływu pracy, zobacz: [porady: Konfigurowanie trwałości przy użyciu klasy WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/how-to-configure-persistence-with-workflowservicehost.md), [Tworzenie usługi przepływu pracy długotrwałe](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md), i [utrwalania przepływu pracy ](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md).  
  
 Na poniższej ilustracji przedstawiono tak zwany WorkflowServiceHost.Open.  
  
 ![Gdy jest wywoływana WorkflowServiceHost.Open](../../../../docs/framework/wcf/feature-details/media/wfhostopen.gif "WFHostOpen")  
  
 Przepływ pracy zostanie załadowany z XAML i drzewo działań jest tworzone. <xref:System.ServiceModel.WorkflowServiceHost> Przegląda drzewo działania i tworzy opisu usługi. Konfiguracja zostanie zastosowana do hosta. Na koniec hosta rozpoczyna nasłuchiwanie dla komunikatów przychodzących.  
  
 Na poniższej ilustracji przedstawiono co <xref:System.ServiceModel.WorkflowServiceHost> po otrzymaniu komunikatu powiązany dla działania Receive, który ma ustawioną wartość CanCreateInstance `true`.  
  
 ![Hosta usługi przepływu pracy odbiera komunikat](../../../../docs/framework/wcf/feature-details/media/wfhreceivemessagecci.gif "WFHReceiveMessageCCI")  
  
 Komunikat dociera i jest przetwarzany przez stos kanału WCF. Limity są sprawdzane i są wykonywane zapytania dotyczące korelacji. Wiadomość zostanie dostarczona, jeśli komunikat jest przeznaczony dla istniejącego wystąpienia. Jeśli nowe wystąpienie musi zostać utworzona, zostanie sprawdzony właściwości CanCreateInstance działanie Receive. Jeśli wartość jest ustawiona na wartość true, utworzono nowe wystąpienie i wiadomość zostanie dostarczona.  
  
 Na poniższej ilustracji przedstawiono co <xref:System.ServiceModel.WorkflowServiceHost> po otrzymaniu komunikatu powiązany dla działania Receive, CanCreateInstance ustawionym na wartość false.  
  
 ![Obiekt WorkflowServiceHost odbiera komunikat](../../../../docs/framework/wcf/feature-details/media/wfshreceivemessage.gif "WFSHReceiveMessage")  
  
 Komunikat dociera i jest przetwarzany przez stos kanału WCF. Limity są sprawdzane i są wykonywane zapytania dotyczące korelacji. Komunikat przeznaczony dla istniejącego wystąpienia (ponieważ CanCreateInstance ma wartość false), wystąpienie zostanie załadowany z magazynu, wznowieniu działania zakładki i wykonuje przepływ pracy.  
  
> [!WARNING]
>  Hosta usługi przepływu pracy nie będzie można otworzyć, jeśli program SQL Server jest skonfigurowany do nasłuchiwania tylko protokół nazwany potok.  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Hostowanie usług przepływu pracy](../../../../docs/framework/wcf/feature-details/hosting-workflow-services.md)  
 [Punkt końcowy kontroli przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-control-endpoint.md)  
 [Przykład punktu końcowego zarządzania przepływem pracy](../../../../docs/framework/windows-workflow-foundation/samples/workflow-management-endpoint-sample.md)  
 [Instrukcje: konfigurowanie zachowania dotyczącego nieobsługiwanego wyjątku przepływu pracy przy użyciu klasy WorkflowServiceHost](../../../../docs/framework/wcf/feature-details/config-workflow-unhandled-exception-workflowservicehost.md)  
 [Tworzenie długo działającej usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/creating-a-long-running-workflow-service.md)  
 [Trwałość przepływu pracy](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)
