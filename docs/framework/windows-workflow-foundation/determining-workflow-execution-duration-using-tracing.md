---
title: "Określanie czas wykonywania przepływu pracy za pomocą śledzenia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c635dbd551eaba6ce338c38564480d0f5cfae553
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="determining-workflow-execution-duration-using-tracing"></a><span data-ttu-id="19d81-102">Określanie czas wykonywania przepływu pracy za pomocą śledzenia</span><span class="sxs-lookup"><span data-stu-id="19d81-102">Determining Workflow Execution Duration Using Tracing</span></span>
<span data-ttu-id="19d81-103">W tym temacie pokazano, jak określić czas potrzebny pomyślnie zakończono, hostowanie Samoobsługowe przepływu pracy można wykonać za pomocą śledzenia przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="19d81-103">This topic demonstrates how to determine the time it takes for a successfully completed, self-hosted workflow to execute by using workflow tracing.</span></span>  
  
### <a name="to-determine-workflow-application-execution-duration-by-using-workflow-tracing"></a><span data-ttu-id="19d81-104">Aby określić czas wykonywania aplikacji przepływu pracy za pomocą śledzenia przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="19d81-104">To determine workflow application execution duration by using workflow tracing</span></span>  
  
1.  <span data-ttu-id="19d81-105">Otwórz [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="19d81-105">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  <span data-ttu-id="19d81-106">Wybierz **pliku**, **nowe**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="19d81-106">Select **File**, **New**, **Project**.</span></span>  <span data-ttu-id="19d81-107">W obszarze **C#**, wybierz pozycję **przepływu pracy** węzła.</span><span class="sxs-lookup"><span data-stu-id="19d81-107">Under **C#**, select the **Workflow** node.</span></span>  <span data-ttu-id="19d81-108">Wybierz **Aplikacja konsoli przepływu pracy** z listy szablonów.</span><span class="sxs-lookup"><span data-stu-id="19d81-108">Select **Workflow Console Application** from the list of templates.</span></span>  <span data-ttu-id="19d81-109">Nazwa nowego projektu `WorkflowDurationTracing` i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="19d81-109">Name the new project `WorkflowDurationTracing` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="19d81-110">Otwórz Workflow1.xaml.</span><span class="sxs-lookup"><span data-stu-id="19d81-110">Open Workflow1.xaml.</span></span>  <span data-ttu-id="19d81-111">Przeciągnij <xref:System.Activities.Statements.Delay> działania na powierzchnię projektanta.</span><span class="sxs-lookup"><span data-stu-id="19d81-111">Drag a <xref:System.Activities.Statements.Delay> activity onto the designer surface.</span></span> <span data-ttu-id="19d81-112">Wartość 00:00:10 (dziesięć sekund) należy przypisać do właściwości Duration działania.</span><span class="sxs-lookup"><span data-stu-id="19d81-112">Assign the value 00:00:10 (ten seconds) to the Duration property of the activity.</span></span>  
  
3.  <span data-ttu-id="19d81-113">Otwórz Podgląd zdarzeń, klikając **Start**, **Uruchom**i wprowadzając `eventvwr.exe`.</span><span class="sxs-lookup"><span data-stu-id="19d81-113">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
4.  <span data-ttu-id="19d81-114">Jeśli nie zostało włączone śledzenie przepływu pracy, rozwiń **Dzienniki aplikacji i usług**, **Microsoft**, **Windows**, **aplikacji serwera aplikacji** .</span><span class="sxs-lookup"><span data-stu-id="19d81-114">If you haven’t enabled workflow tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="19d81-115">Wybierz **widoku**, **wyświetlanie analityczne i debugowania dzienniki**.</span><span class="sxs-lookup"><span data-stu-id="19d81-115">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="19d81-116">Kliknij prawym przyciskiem myszy **debugowania** i wybierz **Włącz dziennik**.</span><span class="sxs-lookup"><span data-stu-id="19d81-116">Right-click **Debug** and select **Enable Log**.</span></span> <span data-ttu-id="19d81-117">Pozostaw otwarte Podgląd zdarzeń, tak aby po uruchomieniu przepływu pracy można wyświetlać danych śledzenia.</span><span class="sxs-lookup"><span data-stu-id="19d81-117">Leave Event Viewer open so that traces can be viewed after the workflow is run.</span></span>  
  
5.  <span data-ttu-id="19d81-118">Uruchom aplikację przepływu pracy, naciskając klawisze CTRL + SHIFT + B.</span><span class="sxs-lookup"><span data-stu-id="19d81-118">Execute the workflow application by pressing CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="19d81-119">W Podglądzie zdarzeń Znajdź ostatnie zdarzenie o identyfikatorze 1009 i komunikat podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="19d81-119">In Event Viewer, find a recent event with ID 1009 and a message similar to the following.</span></span> <span data-ttu-id="19d81-120">Zanotuj czasie rejestrowania komunikatu.</span><span class="sxs-lookup"><span data-stu-id="19d81-120">Make a note of the time that the message was logged.</span></span>  
  
 <span data-ttu-id="19d81-121">**Działanie nadrzędne ", nazwa wyświetlana: '', identyfikator wystąpienia:" podrzędnych zaplanowanego działania "WorkflowDurationTracking.Workflow1", nazwa wyświetlana: "Workflow1", identyfikator wystąpienia: "1".**</span><span class="sxs-lookup"><span data-stu-id="19d81-121">**Parent Activity '', DisplayName: '', InstanceId: '' scheduled child Activity 'WorkflowDurationTracking.Workflow1', DisplayName: 'Workflow1', InstanceId: '1'.**</span></span>  
  
7.  <span data-ttu-id="19d81-122">Znajdź inne ostatnie zdarzenie o identyfikatorze 1001 i komunikat podobny do następującego.</span><span class="sxs-lookup"><span data-stu-id="19d81-122">Find another recent event with ID 1001 and a message similar to the following.</span></span>  <span data-ttu-id="19d81-123">Odejmowanie poprzedniej czas komunikatu z wartość zarejestrowane ten komunikat, aby określić czas wykonywania przepływu pracy, która powinna być około 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="19d81-123">Subtract the previous message time from this message’s Logged value to determine workflow execution duration, which should be around 10 seconds.</span></span>  
  
 <span data-ttu-id="19d81-124">**Obiekt WorkflowInstance o identyfikatorze: "1bbac57b-3322-498e-9e27-8833fda3a5bf" zostało zakończone w stanie zamkniętym.**</span><span class="sxs-lookup"><span data-stu-id="19d81-124">**WorkflowInstance Id: '1bbac57b-3322-498e-9e27-8833fda3a5bf' has completed in the Closed state.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19d81-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19d81-125">See Also</span></span>  
 [<span data-ttu-id="19d81-126">Śledzenie przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="19d81-126">Workflow Tracing</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 [<span data-ttu-id="19d81-127">Windows Server AppFabric monitorowania</span><span class="sxs-lookup"><span data-stu-id="19d81-127">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="19d81-128">Monitorowanie aplikacji przy użyciu rozwiązania AppFabric</span><span class="sxs-lookup"><span data-stu-id="19d81-128">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)