---
title: "Wstrzymywanie i wznawianie przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 11f38339-79c7-4295-b610-24a7223bbf6d
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0d7637a9d49100d3a46ceb3c49769cacae14b5e8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="pausing-and-resuming-a-workflow"></a><span data-ttu-id="72113-102">Wstrzymywanie i wznawianie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="72113-102">Pausing and Resuming a Workflow</span></span>
<span data-ttu-id="72113-103">Przepływy pracy będzie wstrzymywanie i wznawianie w odpowiedzi na zakładek i działania blokujące, takich jak <xref:System.Activities.Statements.Delay>, ale przepływu pracy można również można jawnie wstrzymana, zwolnione i został wznowiony przy użyciu trwałości.</span><span class="sxs-lookup"><span data-stu-id="72113-103">Workflows will pause and resume in response to bookmarks and blocking activities such as <xref:System.Activities.Statements.Delay>, but a workflow can also be explicitly paused, unloaded, and resumed by using persistence.</span></span>  
  
## <a name="pausing-a-workflow"></a><span data-ttu-id="72113-104">Wstrzymywanie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="72113-104">Pausing a Workflow</span></span>  
 <span data-ttu-id="72113-105">Aby wstrzymać przepływ pracy, należy użyć <xref:System.Activities.WorkflowApplication.Unload%2A>.</span><span class="sxs-lookup"><span data-stu-id="72113-105">To pause a workflow, use <xref:System.Activities.WorkflowApplication.Unload%2A>.</span></span>  <span data-ttu-id="72113-106">Ta metoda żądania że przepływ pracy utrwalić zwolnienia i zgłosi <xref:System.TimeoutException> Jeśli przepływ pracy nie spowoduje usunięcia w ciągu 30 sekund.</span><span class="sxs-lookup"><span data-stu-id="72113-106">This method requests that the workflow persist and unload, and will throw a <xref:System.TimeoutException> if the workflow does not unload in 30 seconds.</span></span>  
  
```csharp  
try  
{  
    // attempt to unload will fail if the workflow is idle within a NoPersistZone  
    application.Unload(TimeSpan.FromSeconds(5));  
}  
catch (TimeoutException e)  
{  
    Console.WriteLine(e.Message);  
}  
```  
  
## <a name="resuming-a-workflow"></a><span data-ttu-id="72113-107">Wznawianie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="72113-107">Resuming a Workflow</span></span>  
 <span data-ttu-id="72113-108">Aby wznowić przepływ pracy wcześniej wstrzymana i nie załadowany, należy użyć <xref:System.Activities.WorkflowApplication.Load%2A>.</span><span class="sxs-lookup"><span data-stu-id="72113-108">To resume a previously paused and unloaded workflow, use <xref:System.Activities.WorkflowApplication.Load%2A>.</span></span> <span data-ttu-id="72113-109">Ta metoda ładuje przepływu pracy z magazynem trwałości do pamięci.</span><span class="sxs-lookup"><span data-stu-id="72113-109">This method loads a workflow from a persistence store into memory.</span></span>  
  
```csharp  
WorkflowApplication application = new WorkflowApplication(activity);  
application.InstanceStore = instanceStore;  
application.Load(id);  
```  
  
## <a name="example"></a><span data-ttu-id="72113-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="72113-110">Example</span></span>  
 <span data-ttu-id="72113-111">Poniższy przykład kodu pokazuje, jak wstrzymać i wznowić przepływ pracy przy użyciu trwałości.</span><span class="sxs-lookup"><span data-stu-id="72113-111">The following code sample demonstrates how to pause and resume a workflow by using persistence.</span></span>  
  
```csharp  
static string bkName = "bkName";  
static void Main(string[] args)   
{  
    StartAndUnloadInstance();  
}  
  
static void StartAndUnloadInstance()   
{  
    AutoResetEvent waitHandler = new AutoResetEvent(false);  
    WorkflowApplication wfApp = new WorkflowApplication(GetDelayedWF());  
    SqlWorkflowInstanceStore instanceStore = SetupSqlpersistenceStore();  
    wfApp.InstanceStore = instanceStore;  
    wfApp.Extensions.Add(SetupMyFileTrackingParticipant);  
    wfApp.PersistableIdle = (e) => {          ///persists application state and remove it from memory   
    return PersistableIdleAction.Unload;  
    };  
    wfApp.Unloaded = (e) => {  
        waitHandler.Set();  
    };  
    Guid id = wfApp.Id;  
    wfApp.Run();  
    waitHandler.WaitOne();  
    LoadAndCompleteInstance(id);  
}  
  
static void LoadAndCompleteInstance(Guid id)   
{            
    Console.WriteLine("Press <enter> to load the persisted workflow");  
    Console.ReadLine();  
    AutoResetEvent waitHandler = new AutoResetEvent(false);  
    WorkflowApplication wfApp = new WorkflowApplication(new Workflow1());  
    wfApp.InstanceStore =  
        new SqlWorkflowInstanceStore(ConfigurationManager.AppSettings["SqlWF4PersistenceConnectionString"].ToString());  
    wfApp.Completed = (workflowApplicationCompletedEventArgs) => {  
        Console.WriteLine("\nWorkflowApplication has Completed in the {0} state.",  
            workflowApplicationCompletedEventArgs.CompletionState);  
    };  
    wfApp.Unloaded = (workflowApplicationEventArgs) => {  
        Console.WriteLine("WorkflowApplication has Unloaded\n");  
        waitHandler.Set();  
    };  
    wfApp.Load(id);  
    wfApp.Run();  
    waitHandler.WaitOne();  
}  
  
public static Activity GetDelayedWF()   
{  
    return new Sequence {  
        Activities ={  
            new WriteLine{Text="Workflow Started"},  
            new Delay{Duration=TimeSpan.FromSeconds(10)},  
            new WriteLine{Text="Workflow Ended"}  
        }  
    };  
}  
  
private static SqlWorkflowInstanceStore SetupSqlpersistenceStore()   
{   
     string connectionString = ConfigurationManager.AppSettings["SqlWF4PersistenceConnectionString"].ToString();  
    SqlWorkflowInstanceStore sqlWFInstanceStore = new SqlWorkflowInstanceStore(connectionString);  
    sqlWFInstanceStore.InstanceCompletionAction = InstanceCompletionAction.DeleteAll;  
    InstanceHandle handle = sqlWFInstanceStore.CreateInstanceHandle();  
    InstanceView view = sqlWFInstanceStore.Execute(handle, new CreateWorkflowOwnerCommand(), TimeSpan.FromSeconds(5));  
    handle.Free();  
    sqlWFInstanceStore.DefaultInstanceOwner = view.InstanceOwner;  
    return sqlWFInstanceStore;  
}  
```