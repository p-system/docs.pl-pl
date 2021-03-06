---
title: 'Porady: Konfigurowanie trwałości za pomocą elementu WorkflowServiceHost'
ms.date: 03/30/2017
ms.assetid: e31cd4df-13a3-4a9a-9be8-5243e0055356
ms.openlocfilehash: 9035ded1ca533d9b2107d90f605e15c9ce915965
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493206"
---
# <a name="how-to-configure-persistence-with-workflowservicehost"></a>Porady: Konfigurowanie trwałości za pomocą elementu WorkflowServiceHost
W tym temacie opisano sposób konfigurowania funkcji magazynu wystąpienia przepływu pracy SQL do włączenia trwałości dla przepływów pracy obsługiwanych w <xref:System.ServiceModel.Activities.WorkflowServiceHost> przy użyciu pliku konfiguracji. Przed użyciem funkcji magazynu wystąpienia przepływu pracy SQL należy utworzyć bazę danych SQL używanego w taki sposób, aby utrwalić wystąpienia przepływu pracy. Aby uzyskać więcej informacji, zobacz [porady: Włącz trwałość SQL dla przepływów pracy i przepływ pracy usług](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md).  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-configuration"></a>Aby skonfigurować Magazyn wystąpienia przepływu pracy SQL w konfiguracji  
  
1.  Właściwości magazynu wystąpienia przepływu pracy SQL można skonfigurować za pośrednictwem <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, zachowanie usługi, która umożliwia zmianę ustawień za pomocą pliku XML konfiguracji. W poniższym przykładzie konfiguracji pokazano, jak skonfigurować Magazyn wystąpienia przepływu pracy SQL przy użyciu <`sqlWorkflowInstanceStore`> Zachowanie elementu w pliku konfiguracji.  
  
    ```xml  
    <serviceBehaviors>  
        <behavior name="">  
            <sqlWorkflowInstanceStore   
                 connectionString="provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true"  
                 instanceEncodingOption="GZip | None"  
                 instanceCompletionAction="DeleteAll | DeleteNothing"  
                 instanceLockedExceptionAction="NoRetry | SimpleRetry | AggressiveRetry"  
                 hostLockRenewalPeriod="00:00:30"   
                 runnableInstancesDetectionPeriod="00:00:05">  
            <sqlWorkflowInstanceStore/>  
        </behavior>  
    </serviceBehaviors>  
    ```  
  
     Aby uzyskać więcej informacji na temat konfigurowania magazynu wystąpienia przepływu pracy SQL, zobacz [porady: Włącz trwałość SQL dla przepływów pracy i przepływ pracy usług](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Aby uzyskać więcej informacji o poszczególnych ustawieniach dla <`sqlWorkflowInstanceStore`> element zachowania, zobacz [magazyn wystąpienia przepływu pracy SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server AppFabric zapewnia magazynie trwałości. Aby uzyskać więcej informacji, zobacz [systemu Windows Server aplikacji sieci szkieletowej trwałości](http://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    >  W poprzednim przykładzie konfiguracji używa uproszczona konfiguracja. Aby uzyskać więcej informacji, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)  
  
### <a name="to-configure-the-sql-workflow-instance-store-in-code"></a>Aby skonfigurować Magazyn wystąpienia przepływu pracy SQL w kodzie  
  
1.  Właściwości magazynu wystąpienia przepływu pracy SQL można skonfigurować za pośrednictwem <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior>, zachowanie usługi, która umożliwia zmianę ustawień za pomocą kodu. Poniższy przykład pokazuje, jak skonfigurować Magazyn wystąpienia przepływu pracy SQL przy użyciu <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> element zachowania w kodzie  
  
    ```csharp  
    host.Description.Behaviors.Add(new SqlWorkflowInstanceStoreBehavior  
    {  
       ConnectionString = "provider=System.Data.SqlClient;Data Source=(local);Initial Catalog=DefaultPersistenceProviderDb;Integrated Security=True;Async=true",  
       InstanceEncodingOption = "GZip | None",  
       InstanceCompletionAction = "DeleteAll | DeleteNothing",  
       InstanceLockedExceptionAction = "NoRetry | SimpleRetry | AggressiveRetry",  
       HostLockRenewalPeriod = new TimeSpan(00, 00, 30),  
       RunnableInstancesDetectionPeriod = new TimeSpan(00, 00, 05)  
    });  
    ```  
  
     Aby uzyskać więcej informacji na temat konfigurowania magazynu wystąpienia przepływu pracy SQL, zobacz [porady: Włącz trwałość SQL dla przepływów pracy i przepływ pracy usług](../../../../docs/framework/windows-workflow-foundation/how-to-enable-sql-persistence-for-workflows-and-workflow-services.md). Aby uzyskać więcej informacji o poszczególnych ustawieniach dla <xref:System.ServiceModel.Activities.Description.SqlWorkflowInstanceStoreBehavior> element zachowania, zobacz [magazyn wystąpienia przepływu pracy SQL](../../../../docs/framework/windows-workflow-foundation/sql-workflow-instance-store.md). Windows Server AppFabric zapewnia magazynie trwałości. Aby uzyskać więcej informacji, zobacz [systemu Windows Server aplikacji sieci szkieletowej trwałości](http://go.microsoft.com/fwlink/?LinkId=193121).  
  
    > [!NOTE]
    >  W poprzednim przykładzie konfiguracji używa uproszczona konfiguracja. Aby uzyskać więcej informacji, zobacz [uproszczona konfiguracja](../../../../docs/framework/wcf/simplified-configuration.md)  
  
     Przykład sposobu konfigurowania trwałości programowo w temacie [porady: Włącz trwałość dla przepływów pracy i przepływ pracy usług](../../../../docs/framework/windows-workflow-foundation/how-to-enable-persistence-for-workflows-and-workflow-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [Trwałość przepływu pracy](../../../../docs/framework/windows-workflow-foundation/workflow-persistence.md)  
 [Windows Server AppFabric trwałości](http://go.microsoft.com/fwlink/?LinkId=193121)
