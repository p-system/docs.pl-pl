---
title: "Śledzenie SQL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bcaebeb1-b9e5-49e8-881b-e49af66fd341
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0c2b9eb78c6d8e7125d65ec8fea4c1611ac55e2c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="sql-tracking"></a><span data-ttu-id="10494-102">Śledzenie SQL</span><span class="sxs-lookup"><span data-stu-id="10494-102">SQL Tracking</span></span>
<span data-ttu-id="10494-103">W tym przykładzie pokazano, jak pisać niestandardowe uczestnika śledzenia SQL, który zapisuje śledzenie rekordów bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="10494-103">This sample demonstrates how to write a custom SQL tracking participant, that writes tracking records to a SQL database.</span></span> [!INCLUDE[wf](../../../../includes/wf-md.md)]<span data-ttu-id="10494-104">udostępnia śledzenia wgląd we wykonywania wystąpienia przepływu pracy przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="10494-104"> provides workflow tracking to gain visibility into the execution of a workflow instance.</span></span> <span data-ttu-id="10494-105">Środowisko uruchomieniowe śledzenia emituje przepływu pracy śledzenia rekordów podczas wykonywania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="10494-105">The tracking runtime emits workflow tracking records during the execution of the workflow.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="10494-106">przepływ pracy śledzenia, zobacz [przepływu pracy śledzenia i śledzenia](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span><span class="sxs-lookup"><span data-stu-id="10494-106"> workflow tracking, see [Workflow Tracking and Tracing](../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md).</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="10494-107">Aby użyć tego przykładu</span><span class="sxs-lookup"><span data-stu-id="10494-107">To use this sample</span></span>  
  
1.  <span data-ttu-id="10494-108">Sprawdź, zainstalowany jest program SQL Server 2008, SQL Server 2008 Express lub nowszej.</span><span class="sxs-lookup"><span data-stu-id="10494-108">Verify you have SQL Server 2008, SQL Server 2008 Express or newer installed.</span></span> <span data-ttu-id="10494-109">Skrypty z przykładowej założono korzystanie z wystąpienia programu SQL Express na komputerze lokalnym.</span><span class="sxs-lookup"><span data-stu-id="10494-109">The scripts packaged with the sample assume the use of a SQL Express instance on your local computer.</span></span> <span data-ttu-id="10494-110">Jeśli masz inne wystąpienie Zmodyfikuj skrypty związanych z bazy danych przed uruchomieniem próbki.</span><span class="sxs-lookup"><span data-stu-id="10494-110">If you have a different instance please modify the database-related scripts before running the sample.</span></span>  
  
2.  <span data-ttu-id="10494-111">Utwórz bazę danych śledzenia programu SQL Server, uruchamiając Trackingsetup.cmd w katalogu skryptów (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span><span class="sxs-lookup"><span data-stu-id="10494-111">Create the SQL Server tracking database by running Trackingsetup.cmd in the scripts directory (\WF\Basic\Tracking\SqlTracking\CS\Scripts).</span></span> <span data-ttu-id="10494-112">Spowoduje to utworzenie bazy danych o nazwie TrackingSample.</span><span class="sxs-lookup"><span data-stu-id="10494-112">This creates a database called TrackingSample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="10494-113">Skrypt tworzy bazy danych w domyślnym wystąpieniu programu SQL Express.</span><span class="sxs-lookup"><span data-stu-id="10494-113">The script creates the database on the default instance of SQL Express.</span></span> <span data-ttu-id="10494-114">Jeśli użytkownik chce go zainstalować na wystąpieniu innej bazy danych, zmodyfikuj plik skryptu Trackingsetup.cmd.</span><span class="sxs-lookup"><span data-stu-id="10494-114">If you want to install it on a different database instance, edit the Trackingsetup.cmd script.</span></span>  
  
3.  <span data-ttu-id="10494-115">Otwórz SqlTrackingSample.sln w [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="10494-115">Open SqlTrackingSample.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
4.  <span data-ttu-id="10494-116">Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="10494-116">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
5.  <span data-ttu-id="10494-117">Naciśnij klawisz F5, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="10494-117">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="10494-118">Oknie przeglądarki zostanie otwarty i zawiera katalog zawierający informacje o aplikacji.</span><span class="sxs-lookup"><span data-stu-id="10494-118">The browser window opens and shows the directory listing for the application.</span></span>  
  
6.  <span data-ttu-id="10494-119">W przeglądarce kliknij przycisk StockPriceService.xamlx.</span><span class="sxs-lookup"><span data-stu-id="10494-119">In the browser, click StockPriceService.xamlx.</span></span>  
  
7.  <span data-ttu-id="10494-120">W przeglądarce pojawi się stronie StockPriceService zawiera Usługa lokalna adres WSDL.</span><span class="sxs-lookup"><span data-stu-id="10494-120">The browser displays the StockPriceService page, which contains the local service WSDL address.</span></span> <span data-ttu-id="10494-121">Skopiuj ten adres.</span><span class="sxs-lookup"><span data-stu-id="10494-121">Copy this address.</span></span>  
  
     <span data-ttu-id="10494-122">Przykładem usługa lokalna adres WSDL jest http://localhost:65193/StockPriceService.xamlx?wsdl.</span><span class="sxs-lookup"><span data-stu-id="10494-122">An example of the local service WSDL address is http://localhost:65193/StockPriceService.xamlx?wsdl.</span></span>  
  
8.  <span data-ttu-id="10494-123">Przy użyciu [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], uruchomić klienta testowego WCF (WcfTestClient.exe).</span><span class="sxs-lookup"><span data-stu-id="10494-123">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], run the WCF test client (WcfTestClient.exe).</span></span> <span data-ttu-id="10494-124">Znajduje się w katalogu 10.0\Common7\IDE programu Microsoft Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="10494-124">It is located in the Microsoft Visual Studio 10.0\Common7\IDE directory.</span></span>  
  
9. <span data-ttu-id="10494-125">W kliencie testowym WCF, kliknij przycisk **pliku** menu i wybierz **Dodaj usługę**.</span><span class="sxs-lookup"><span data-stu-id="10494-125">In the WCF test client, click the **File** menu and select **Add Service**.</span></span> <span data-ttu-id="10494-126">Wklej adres usługi lokalnej w polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="10494-126">Paste the local service address in the textbox.</span></span> <span data-ttu-id="10494-127">Kliknij przycisk **OK** aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="10494-127">Click **OK** to close the dialog.</span></span>  
  
10. <span data-ttu-id="10494-128">W kliencie testowym WCF, kliknij dwukrotnie **GetStockPrice**.</span><span class="sxs-lookup"><span data-stu-id="10494-128">In the WCF test client, double click **GetStockPrice**.</span></span> <span data-ttu-id="10494-129">Spowoduje to otwarcie `GetStockPrice` operacja, która przyjmuje jeden parametr typu w wartości `Contoso` i kliknij przycisk **Invoke**.</span><span class="sxs-lookup"><span data-stu-id="10494-129">This opens the `GetStockPrice` operation that takes one parameter, type in the value `Contoso` and click **Invoke**.</span></span>  
  
11. <span data-ttu-id="10494-130">Rejestruje emitowany śledzenia są zapisywane do bazy danych SQL.</span><span class="sxs-lookup"><span data-stu-id="10494-130">The emitted tracking records are written to a SQL database.</span></span> <span data-ttu-id="10494-131">Aby wyświetlić rekordy śledzenia, należy otworzyć TrackingSample bazy danych w programie SQL Management Studio i przejdź do tabel.</span><span class="sxs-lookup"><span data-stu-id="10494-131">To view the tracking records, open the TrackingSample database in SQL Management Studio and navigate to the tables.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="10494-132">SQL Server Management Studio, zobacz [wprowadzenie do programu SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645).</span><span class="sxs-lookup"><span data-stu-id="10494-132"> SQL Server Management Studio, see [Introducing SQL Server Management Studio](http://go.microsoft.com/fwlink/?LinkId=165645).</span></span> <span data-ttu-id="10494-133">SQL Server 2008 Management Studio Express można pobrać [tutaj](http://go.microsoft.com/fwlink/?LinkId=180520).</span><span class="sxs-lookup"><span data-stu-id="10494-133">SQL Server 2008 Management Studio Express can be downloaded [here](http://go.microsoft.com/fwlink/?LinkId=180520).</span></span> <span data-ttu-id="10494-134">Uruchamianie zapytania select w tabelach wyświetla dane przechowywane w tabelach odpowiednie rekordy śledzenia.</span><span class="sxs-lookup"><span data-stu-id="10494-134">Running a select query on the tables displays the data within the tracking records stored in the respective tables.</span></span>  
  
#### <a name="to-uninstall-the-sample"></a><span data-ttu-id="10494-135">Aby odinstalować próbki</span><span class="sxs-lookup"><span data-stu-id="10494-135">To uninstall the sample</span></span>  
  
1.  <span data-ttu-id="10494-136">Uruchom skrypt theTrackingcleanup.cmd w katalogu próbki (\WF\Basic\Tracking\SqlTracking).</span><span class="sxs-lookup"><span data-stu-id="10494-136">Run theTrackingcleanup.cmd script in the sample directory (\WF\Basic\Tracking\SqlTracking).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="10494-137">Trackingcleanup.cmd próbuje usunąć bazę danych programu SQL Express komputera lokalnego.</span><span class="sxs-lookup"><span data-stu-id="10494-137">The Trackingcleanup.cmd attempts to delete the database in your local computer SQL Express.</span></span> <span data-ttu-id="10494-138">Jeśli korzystasz z innego wystąpienia programu SQL server, należy edytować Trackingcleanup.cmd.</span><span class="sxs-lookup"><span data-stu-id="10494-138">If you are using another SQL server instance, edit Trackingcleanup.cmd.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="10494-139">Próbki mogą być zainstalowane na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="10494-139">The samples may already be installed on your computer.</span></span> <span data-ttu-id="10494-140">Przed kontynuowaniem sprawdź, czy są dostępne dla następującego katalogu (ustawienie domyślne).</span><span class="sxs-lookup"><span data-stu-id="10494-140">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="10494-141">Jeśli ten katalog nie istnieje, przejdź do [Windows Communication Foundation (WCF) i Windows Workflow Foundation (WF) przykłady dla programu .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pobrać wszystkie [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] i [!INCLUDE[wf1](../../../../includes/wf1-md.md)] próbek.</span><span class="sxs-lookup"><span data-stu-id="10494-141">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="10494-142">W tym przykładzie znajduje się w następującym katalogu.</span><span class="sxs-lookup"><span data-stu-id="10494-142">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Tracking\SqlTracking`  
  
## <a name="see-also"></a><span data-ttu-id="10494-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="10494-143">See Also</span></span>  
 [<span data-ttu-id="10494-144">Przykłady monitorowania AppFabric</span><span class="sxs-lookup"><span data-stu-id="10494-144">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)