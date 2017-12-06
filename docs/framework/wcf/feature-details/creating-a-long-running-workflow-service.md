---
title: "Tworzenie długo działającej usługi przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4c39bd04-5b8a-4562-a343-2c63c2821345
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 65aa61ec53c00ed69d55d36fb023dc92c77e1f13
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="creating-a-long-running-workflow-service"></a><span data-ttu-id="9efd5-102">Tworzenie długo działającej usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9efd5-102">Creating a Long-running Workflow Service</span></span>
<span data-ttu-id="9efd5-103">W tym temacie opisano sposób tworzenia usługi przepływu pracy długotrwałe.</span><span class="sxs-lookup"><span data-stu-id="9efd5-103">This topic describes how to create a long-running workflow service.</span></span> <span data-ttu-id="9efd5-104">Długotrwałe usług przepływu pracy mogą działać przez dłuższy czas.</span><span class="sxs-lookup"><span data-stu-id="9efd5-104">Long running workflow services may run for long periods of time.</span></span> <span data-ttu-id="9efd5-105">W pewnym momencie przepływ pracy może być bezczynności oczekiwanie na dodatkowe informacje.</span><span class="sxs-lookup"><span data-stu-id="9efd5-105">At some point the workflow may go idle waiting for some additional information.</span></span> <span data-ttu-id="9efd5-106">W takim przypadku przepływ pracy zostanie na stałe zapisana bazy danych SQL i zostanie usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="9efd5-106">When this occurs the workflow is persisted to a SQL database and is removed from memory.</span></span> <span data-ttu-id="9efd5-107">Po udostępnieniu dodatkowe informacje wystąpienia przepływu pracy jest ładowany do pamięci i kontynuuje wykonywanie.</span><span class="sxs-lookup"><span data-stu-id="9efd5-107">When the additional information becomes available the workflow instance is loaded back into memory and continues executing.</span></span>  <span data-ttu-id="9efd5-108">W tym scenariuszu w przypadku implementowania bardzo uproszczonego systemu porządkowania.</span><span class="sxs-lookup"><span data-stu-id="9efd5-108">In this scenario you are implementing a very simplified ordering system.</span></span>  <span data-ttu-id="9efd5-109">Klient wysyła początkowy komunikat do usługi przepływu pracy, aby uruchomić kolejność.</span><span class="sxs-lookup"><span data-stu-id="9efd5-109">The client sends an initial message to the workflow service to start the order.</span></span> <span data-ttu-id="9efd5-110">Zwraca identyfikator zamówienia do klienta.</span><span class="sxs-lookup"><span data-stu-id="9efd5-110">It returns an order ID to the client.</span></span> <span data-ttu-id="9efd5-111">W tym momencie usługi przepływu pracy jest oczekiwanie na kolejny komunikat z klienta i przechodzi w stan bezczynności i zostanie na stałe zapisana bazy danych programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="9efd5-111">At this point the workflow service is waiting for another message from the client and goes into the idle state and is persisted to a SQL Server database.</span></span>  <span data-ttu-id="9efd5-112">Gdy klient wysyła następny komunikat do kolejność elementów, usługi przepływu pracy jest ładowany do pamięci i zakończeniu przetwarzania zamówienia.</span><span class="sxs-lookup"><span data-stu-id="9efd5-112">When the client sends the next message to order an item, the workflow service is loaded back into memory and finishes processing the order.</span></span> <span data-ttu-id="9efd5-113">W przykładowym kodzie zwraca ciąg informujący, że element został dodany do zlecenia.</span><span class="sxs-lookup"><span data-stu-id="9efd5-113">In the code sample it returns a string stating the item has been added to the order.</span></span> <span data-ttu-id="9efd5-114">Przykładowy kod ma nie być rzeczywistych stosowania technologii, ale zamiast prosty przykład, który przedstawiono długotrwała usług przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9efd5-114">The code sample is not meant to be a real world application of the technology, but rather a simple sample that illustrates long running workflow services.</span></span> <span data-ttu-id="9efd5-115">W tym temacie założono, wiesz, jak utworzyć [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projekty i rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9efd5-115">This topic assumes you know how to create [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] projects and solutions.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="9efd5-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="9efd5-116">Prerequisites</span></span>  
 <span data-ttu-id="9efd5-117">Musi mieć zainstalowane, aby korzystać z tego przewodnika następujące oprogramowanie:</span><span class="sxs-lookup"><span data-stu-id="9efd5-117">You must have the following software installed to use this walkthrough:</span></span>  
  
1.  <span data-ttu-id="9efd5-118">Microsoft SQL Server 2008</span><span class="sxs-lookup"><span data-stu-id="9efd5-118">Microsoft SQL Server 2008</span></span>  
  
2.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]  
  
3.  <span data-ttu-id="9efd5-119">Microsoft[!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9efd5-119">Microsoft  [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]</span></span>  
  
4.  <span data-ttu-id="9efd5-120">Znasz WCF i [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] i wiedzieć, jak tworzyć projekty/rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9efd5-120">You are familiar with WCF and [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] and know how to create projects/solutions.</span></span>  
  
### <a name="to-setup-the-sql-database"></a><span data-ttu-id="9efd5-121">Konfiguracja bazy danych SQL</span><span class="sxs-lookup"><span data-stu-id="9efd5-121">To Setup the SQL Database</span></span>  
  
1.  <span data-ttu-id="9efd5-122">Aby wystąpienia usługi przepływu pracy utrwalenia musi mieć zainstalowany program Microsoft SQL Server i skonfiguruj bazę danych do przechowywania wystąpień utrwalonych przepływów pracy.</span><span class="sxs-lookup"><span data-stu-id="9efd5-122">In order for workflow service instances to be persisted you must have Microsoft SQL Server installed and you must configure a database to store the persisted workflow instances.</span></span> <span data-ttu-id="9efd5-123">Uruchom program Microsoft SQL Management Studio, klikając **Start** przycisku, wybierając **wszystkie programy**, **Microsoft SQL Server 2008**, i **programu Microsoft SQL Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="9efd5-123">Run Microsoft SQL Management Studio by clicking the **Start** button, selecting **All Programs**, **Microsoft SQL Server 2008**, and **Microsoft SQL Management Studio**.</span></span>  
  
2.  <span data-ttu-id="9efd5-124">Kliknij przycisk **Connect** przycisk, aby zalogować się do wystąpienia programu SQL Server</span><span class="sxs-lookup"><span data-stu-id="9efd5-124">Click the **Connect** button to log on to the SQL Server instance</span></span>  
  
3.  <span data-ttu-id="9efd5-125">Kliknij prawym przyciskiem myszy **baz danych** w widoku drzewa, a następnie wybierz **nowej bazy danych...**</span><span class="sxs-lookup"><span data-stu-id="9efd5-125">Right click **Databases** in the tree view and select **New Database..**</span></span> <span data-ttu-id="9efd5-126">Aby utworzyć nową bazę danych o nazwie `SQLPersistenceStore`.</span><span class="sxs-lookup"><span data-stu-id="9efd5-126">to create a new database called `SQLPersistenceStore`.</span></span>  
  
4.  <span data-ttu-id="9efd5-127">Uruchom plik skryptu SqlWorkflowInstanceStoreSchema.sql znajduje się w katalogu C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en w bazie danych SQLPersistenceStore, aby skonfigurować schematów potrzebne bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9efd5-127">Run the SqlWorkflowInstanceStoreSchema.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database schemas.</span></span>  
  
5.  <span data-ttu-id="9efd5-128">Uruchom plik skryptu SqlWorkflowInstanceStoreLogic.sql znajduje się w katalogu C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en w bazie danych SQLPersistenceStore, aby skonfigurować logiki potrzebne bazy danych.</span><span class="sxs-lookup"><span data-stu-id="9efd5-128">Run the SqlWorkflowInstanceStoreLogic.sql script file located in the C:\Windows\Microsoft.NET\Framework\v4.0\SQL\en directory on the SQLPersistenceStore database to set up the needed database logic.</span></span>  
  
### <a name="to-create-the-web-hosted-workflow-service"></a><span data-ttu-id="9efd5-129">Aby utworzyć sieci Web hostowanej usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9efd5-129">To Create the Web Hosted Workflow Service</span></span>  
  
1.  <span data-ttu-id="9efd5-130">Utwórz pustą [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] rozwiązania, nadaj mu nazwę `OrderProcessing`.</span><span class="sxs-lookup"><span data-stu-id="9efd5-130">Create an empty [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] solution, name it `OrderProcessing`.</span></span>  
  
2.  <span data-ttu-id="9efd5-131">Dodaj nową [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] projektu aplikacji usługi przepływu pracy o nazwie `OrderService` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9efd5-131">Add a new [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Workflow Service Application project called `OrderService` to the solution.</span></span>  
  
3.  <span data-ttu-id="9efd5-132">W oknie dialogowym właściwości projektu, zaznacz **Web** kartę.</span><span class="sxs-lookup"><span data-stu-id="9efd5-132">In the project properties dialog, select the **Web** tab.</span></span>  
  
    1.  <span data-ttu-id="9efd5-133">W obszarze **Akcja uruchamiania** wybierz **określonej strony** i określ `Service1.xamlx`.</span><span class="sxs-lookup"><span data-stu-id="9efd5-133">Under **Start Action** select **Specific Page** and specify `Service1.xamlx`.</span></span>  
  
         <span data-ttu-id="9efd5-134">![Właściwości sieci Web projektu usługi przepływu pracy](../../../../docs/framework/wcf/feature-details/media/startaction.png "StartAction")</span><span class="sxs-lookup"><span data-stu-id="9efd5-134">![Workflow Service Project Web Properties](../../../../docs/framework/wcf/feature-details/media/startaction.png "StartAction")</span></span>  
  
    2.  <span data-ttu-id="9efd5-135">W obszarze **serwerów** wybierz **Użyj lokalnym serwerem sieci Web IIS**.</span><span class="sxs-lookup"><span data-stu-id="9efd5-135">Under **Servers** select **Use Local IIS Web server**.</span></span>  
  
         <span data-ttu-id="9efd5-136">![Ustawienia serwera sieci Web w lokalnej](../../../../docs/framework/wcf/feature-details/media/uselocalwebserver.png "UseLocalWebServer")</span><span class="sxs-lookup"><span data-stu-id="9efd5-136">![Local Web Server Settings](../../../../docs/framework/wcf/feature-details/media/uselocalwebserver.png "UseLocalWebServer")</span></span>  
  
        > [!WARNING]
        >  <span data-ttu-id="9efd5-137">Należy uruchomić [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] w trybie administratora, aby to ustawienie.</span><span class="sxs-lookup"><span data-stu-id="9efd5-137">You must run [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] in administrator mode to make this setting.</span></span>  
  
         <span data-ttu-id="9efd5-138">Następujące dwa kroki konfigurowania projektu usługi przepływu pracy, który ma być obsługiwana przez usługi IIS.</span><span class="sxs-lookup"><span data-stu-id="9efd5-138">These two steps configure the workflow service project to be hosted by IIS.</span></span>  
  
4.  <span data-ttu-id="9efd5-139">Otwórz `Service1.xamlx` przypadku nie otwarto już i usuń istniejącą **ReceiveRequest** i **SendResponse** działań.</span><span class="sxs-lookup"><span data-stu-id="9efd5-139">Open `Service1.xamlx` if it is not open already and delete the existing **ReceiveRequest** and **SendResponse** activities.</span></span>  
  
5.  <span data-ttu-id="9efd5-140">Wybierz **usługa Sekwencyjna** działania i kliknij przycisk **zmienne** link i dodać zmienne pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="9efd5-140">Select the **Sequential Service** activity and click the **Variables** link and add the variables shown in the following illustration.</span></span> <span data-ttu-id="9efd5-141">W ten sposób dodaje niektóre zmienne, które będą używane później w usłudze przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9efd5-141">Doing this adds some variables that will be used later on in the workflow service.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9efd5-142">Jeśli obiekt CorrelationHandle nie ma listy rozwijanej Typ zmiennej, wybierz **Przeglądaj w poszukiwaniu typy** z listy rozwijanej.</span><span class="sxs-lookup"><span data-stu-id="9efd5-142">If CorrelationHandle is not in the Variable Type drop-down, select **Browse for types** from the drop-down.</span></span> <span data-ttu-id="9efd5-143">Typ obiektu CorrelationHandle w **nazwy typu** polu, wybierz obiekt CorrelationHandle w polu listy i kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9efd5-143">Type CorrelationHandle in the **Type name** box, select CorrelationHandle from the listbox and click **OK**.</span></span>  
  
     <span data-ttu-id="9efd5-144">![Dodawanie zmiennych](../../../../docs/framework/wcf/feature-details/media/addvariables.gif "AddVariables")</span><span class="sxs-lookup"><span data-stu-id="9efd5-144">![Add Variables](../../../../docs/framework/wcf/feature-details/media/addvariables.gif "AddVariables")</span></span>  
  
6.  <span data-ttu-id="9efd5-145">Przeciągnij i upuść **ReceiveAndSendReply** szablon działania do **usługa Sekwencyjna** działania.</span><span class="sxs-lookup"><span data-stu-id="9efd5-145">Drag and drop a **ReceiveAndSendReply** activity template into the **Sequential Service** activity.</span></span> <span data-ttu-id="9efd5-146">Ten zbiór działań zostanie wyświetlony komunikat z klienta i wysyłać odpowiedzi ponownie.</span><span class="sxs-lookup"><span data-stu-id="9efd5-146">This set of activities will receive a message from a client and send a reply back.</span></span>  
  
    1.  <span data-ttu-id="9efd5-147">Wybierz **Receive** działania i ustaw właściwości wyróżnione na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="9efd5-147">Select the **Receive** activity and set the properties highlighted in the following illustration.</span></span>  
  
         <span data-ttu-id="9efd5-148">![Właściwości działania odbierania zestawu](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties.png "SetReceiveProperties")</span><span class="sxs-lookup"><span data-stu-id="9efd5-148">![Set Receive Activity Properties](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties.png "SetReceiveProperties")</span></span>  
  
         <span data-ttu-id="9efd5-149">Właściwość DisplayName ustawia nazwę wyświetlaną dla działania Receive w projektancie.</span><span class="sxs-lookup"><span data-stu-id="9efd5-149">The DisplayName property sets the name displayed for the Receive activity in the designer.</span></span> <span data-ttu-id="9efd5-150">Właściwości ServiceContractName i OperationName Określ nazwę kontraktu usługi i operacji, które są implementowane przez działanie Receive.</span><span class="sxs-lookup"><span data-stu-id="9efd5-150">The ServiceContractName and OperationName properties specify the name of the service contract and operation that are implemented by the Receive activity.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="9efd5-151">używania kontraktów w przepływie pracy usług zobacz [za pomocą kontraktów w przepływie pracy](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span><span class="sxs-lookup"><span data-stu-id="9efd5-151"> how contracts are used in Workflow services see [Using Contracts in Workflow](../../../../docs/framework/wcf/feature-details/using-contracts-in-workflow.md).</span></span>  
  
    2.  <span data-ttu-id="9efd5-152">Kliknij przycisk **zdefiniuj...**  łącze w **ReceiveStartOrder** działania i ustaw właściwości wyświetlane na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="9efd5-152">Click the **Define...** link in the **ReceiveStartOrder** activity and set the properties shown in the following illustration.</span></span>  <span data-ttu-id="9efd5-153">Zwróć uwagę, że **parametry** przycisk radiowy zostanie wybrany, parametr o nazwie `p_customerName` jest powiązany z `customerName` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9efd5-153">Notice that the **Parameters** radio button is selected, a parameter named `p_customerName` is bound to the `customerName` variable.</span></span> <span data-ttu-id="9efd5-154">Spowoduje to skonfigurowanie **Receive** działanie, aby odbierać niektóre dane i powiązać te dane do zmiennych lokalnych.</span><span class="sxs-lookup"><span data-stu-id="9efd5-154">This configures the **Receive** activity to receive some data and bind that data to local variables.</span></span>  
  
         <span data-ttu-id="9efd5-155">![Ustawienia danych odebranych przez działanie Receive](../../../../docs/framework/wcf/feature-details/media/setreceivecontent.png "SetReceiveContent")</span><span class="sxs-lookup"><span data-stu-id="9efd5-155">![Setting the data received by the Receive activity](../../../../docs/framework/wcf/feature-details/media/setreceivecontent.png "SetReceiveContent")</span></span>  
  
    3.  <span data-ttu-id="9efd5-156">Wybierz **SendReplyToReceive** działania i ustaw dla właściwości wyróżnione pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="9efd5-156">Select The **SendReplyToReceive** activity and set the highlighted property shown in the following illustration.</span></span>  
  
         <span data-ttu-id="9efd5-157">![Ustawianie właściwości działania SendReply](../../../../docs/framework/wcf/feature-details/media/setreplyproperties.png "SetReplyProperties")</span><span class="sxs-lookup"><span data-stu-id="9efd5-157">![Setting the properties of the SendReply activity](../../../../docs/framework/wcf/feature-details/media/setreplyproperties.png "SetReplyProperties")</span></span>  
  
    4.  <span data-ttu-id="9efd5-158">Kliknij przycisk **zdefiniuj...**  łącze w **SendReplyToStartOrder** działania i ustaw właściwości wyświetlane na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="9efd5-158">Click the **Define...** link in the **SendReplyToStartOrder** activity and set the properties shown in the following illustration.</span></span> <span data-ttu-id="9efd5-159">Zwróć uwagę, że **parametry** przycisk radiowy zostanie wybrany; parametr o nazwie `p_orderId` jest powiązany z `orderId` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9efd5-159">Notice that the **Parameters** radio button is selected; a parameter named `p_orderId` is bound to the `orderId` variable.</span></span> <span data-ttu-id="9efd5-160">To ustawienie określa, że działanie SendReplyToStartOrder zwróci wartość typu ciąg do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="9efd5-160">This setting specifies that the SendReplyToStartOrder activity will return a value of type string to the caller.</span></span>  
  
         <span data-ttu-id="9efd5-161">![Konfigurowanie danych zawartości działania SendReply](../../../../docs/framework/wcf/feature-details/media/setreplycontent.png "SetReplyContent")</span><span class="sxs-lookup"><span data-stu-id="9efd5-161">![Configuring the SendReply activity content data](../../../../docs/framework/wcf/feature-details/media/setreplycontent.png "SetReplyContent")</span></span>  
  
    5.  <span data-ttu-id="9efd5-162">Przeciągnij i upuść działanie Przypisz między **Receive** i **SendReply** działań i ustaw właściwości, jak pokazano na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="9efd5-162">Drag and drop an Assign activity in between the **Receive** and **SendReply** activities and set the properties as shown in the following illustration:</span></span>  
  
         <span data-ttu-id="9efd5-163">![Dodawanie działaniu assign](../../../../docs/framework/wcf/feature-details/media/addassign.png "AddAssign")</span><span class="sxs-lookup"><span data-stu-id="9efd5-163">![Adding an assign activity](../../../../docs/framework/wcf/feature-details/media/addassign.png "AddAssign")</span></span>  
  
         <span data-ttu-id="9efd5-164">Tworzy nowy identyfikator zamówienia i umieszcza wartość w zmiennej orderId.</span><span class="sxs-lookup"><span data-stu-id="9efd5-164">This creates a new order ID and places the value in the orderId variable.</span></span>  
  
    6.  <span data-ttu-id="9efd5-165">Wybierz **ReplyToStartOrder** działania.</span><span class="sxs-lookup"><span data-stu-id="9efd5-165">Select the **ReplyToStartOrder** activity.</span></span> <span data-ttu-id="9efd5-166">W oknie dialogowym właściwości kliknij przycisk wielokropka **CorrelationInitializers**.</span><span class="sxs-lookup"><span data-stu-id="9efd5-166">In the properties window click the ellipsis button for **CorrelationInitializers**.</span></span> <span data-ttu-id="9efd5-167">Wybierz **dodać inicjatora** połączyć, wprowadź `orderIdHandle` w polu tekstowym inicjatora wybierz inicjatora korelacji zapytań dla typu korelacji, a następnie wybierz p_orderId w polu listy rozwijanej kwerendy XPATH.</span><span class="sxs-lookup"><span data-stu-id="9efd5-167">Select the **Add initializer** link, enter `orderIdHandle` in the Initializer text box, select Query correlation initializer for the Correlation type, and select p_orderId under the XPATH Queries dropdown box.</span></span> <span data-ttu-id="9efd5-168">Te ustawienia są wyświetlane na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="9efd5-168">These settings are shown in the following illustration.</span></span> <span data-ttu-id="9efd5-169">Kliknij przycisk **OK**.</span><span class="sxs-lookup"><span data-stu-id="9efd5-169">Click **OK**.</span></span>  <span data-ttu-id="9efd5-170">To inicjuje korelację między klientem a to wystąpienie usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9efd5-170">This initializes a correlation between the client and this instance of the workflow service.</span></span> <span data-ttu-id="9efd5-171">Jeśli wiadomość zawierającą porządek ten identyfikator jest odebrana jest kierowany do tego wystąpienia usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9efd5-171">When a message containing this order ID is received it is routed to this instance of the workflow service.</span></span>  
  
         <span data-ttu-id="9efd5-172">![Dodawanie inicjatora korelacji](../../../../docs/framework/wcf/feature-details/media/addcorrelationinitializers.png "AddCorrelationInitializers")</span><span class="sxs-lookup"><span data-stu-id="9efd5-172">![Adding a correlation initializer](../../../../docs/framework/wcf/feature-details/media/addcorrelationinitializers.png "AddCorrelationInitializers")</span></span>  
  
7.  <span data-ttu-id="9efd5-173">Przeciągnij i upuść innego **ReceiveAndSendReply** działania na końcu przepływu pracy (poza **sekwencji** zawierający pierwszy **Receive** i  **SendReply** działań).</span><span class="sxs-lookup"><span data-stu-id="9efd5-173">Drag and drop another **ReceiveAndSendReply** activity to the end of the workflow (outside the **Sequence** containing the first **Receive** and **SendReply** activities).</span></span> <span data-ttu-id="9efd5-174">Zostanie wyświetlony to drugi komunikat wysyłany przez klienta i odpowiedzieć na.</span><span class="sxs-lookup"><span data-stu-id="9efd5-174">This will receive the second message sent by the client and respond to it.</span></span>  
  
    1.  <span data-ttu-id="9efd5-175">Wybierz **sekwencji** zawierający nowo dodanego **Receive** i **SendReply** działania i kliknij przycisk **zmienne** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9efd5-175">Select the **Sequence** that contains the newly added **Receive** and **SendReply** activities and click the **Variables** button.</span></span> <span data-ttu-id="9efd5-176">Dodaj zmienną wyróżnione na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="9efd5-176">Add the variable highlighted in the following illustration:</span></span>  
  
         <span data-ttu-id="9efd5-177">![Dodawanie nowych zmiennych](../../../../docs/framework/wcf/feature-details/media/addorderitemidvariable.png "AddOrderItemIdVariable")</span><span class="sxs-lookup"><span data-stu-id="9efd5-177">![Adding new variables](../../../../docs/framework/wcf/feature-details/media/addorderitemidvariable.png "AddOrderItemIdVariable")</span></span>  
  
    2.  <span data-ttu-id="9efd5-178">Wybierz **Receive** działania i ustaw właściwości wyświetlane na poniższej ilustracji:</span><span class="sxs-lookup"><span data-stu-id="9efd5-178">Select the **Receive** activity and set the properties shown in the following illustration:</span></span>  
  
         <span data-ttu-id="9efd5-179">![Ustaw właściwości acitivity Receive](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties2.png "SetReceiveProperties2")</span><span class="sxs-lookup"><span data-stu-id="9efd5-179">![Set the Receive acitivity properties](../../../../docs/framework/wcf/feature-details/media/setreceiveproperties2.png "SetReceiveProperties2")</span></span>  
  
    3.  <span data-ttu-id="9efd5-180">Kliknij przycisk **zdefiniuj...**  łącze w **ReceiveAddItem** działania i Dodaj parametry pokazano na poniższej ilustracji: spowoduje to skonfigurowanie działanie receive, aby zaakceptować dwa parametry: identyfikator zamówienia i identyfikator elementu porządkowana.</span><span class="sxs-lookup"><span data-stu-id="9efd5-180">Click the **Define...** link in the **ReceiveAddItem** activity and add the parameters shown in the following illustration:This configures the receive activity to accept two parameters, the order ID and the ID of the item being ordered.</span></span>  
  
         <span data-ttu-id="9efd5-181">![Określanie parametrów dla drugiego odbierania](../../../../docs/framework/wcf/feature-details/media/addreceive2parameters.png "AddReceive2Parameters")</span><span class="sxs-lookup"><span data-stu-id="9efd5-181">![Specifying parameters for the second receive](../../../../docs/framework/wcf/feature-details/media/addreceive2parameters.png "AddReceive2Parameters")</span></span>  
  
    4.  <span data-ttu-id="9efd5-182">Kliknij przycisk **CorrelateOn** wielokropka przycisk, a następnie wprowadź `orderIdHandle`.</span><span class="sxs-lookup"><span data-stu-id="9efd5-182">Click the **CorrelateOn** ellipsis button and enter `orderIdHandle`.</span></span> <span data-ttu-id="9efd5-183">W obszarze **kwerendy XPath**, kliknij strzałkę listy rozwijanej i wybierz `p_orderId`.</span><span class="sxs-lookup"><span data-stu-id="9efd5-183">Under **XPath Queries**, click the drop down arrow and select `p_orderId`.</span></span> <span data-ttu-id="9efd5-184">Spowoduje to skonfigurowanie korelację na drugiej stronie działanie odbierania.</span><span class="sxs-lookup"><span data-stu-id="9efd5-184">This configures the correlation on the second receive activity.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="9efd5-185">Zobacz korelacji [korelacji](../../../../docs/framework/wcf/feature-details/correlation.md).</span><span class="sxs-lookup"><span data-stu-id="9efd5-185"> correlation see [Correlation](../../../../docs/framework/wcf/feature-details/correlation.md).</span></span>  
  
         <span data-ttu-id="9efd5-186">![Ustawienie właściwości CorrelatesOn](../../../../docs/framework/wcf/feature-details/media/correlateson.png "CorrelatesOn")</span><span class="sxs-lookup"><span data-stu-id="9efd5-186">![Setting the CorrelatesOn property](../../../../docs/framework/wcf/feature-details/media/correlateson.png "CorrelatesOn")</span></span>  
  
    5.  <span data-ttu-id="9efd5-187">Przeciągnij i upuść **Jeśli** działanie natychmiast po **ReceiveAddItem** działania.</span><span class="sxs-lookup"><span data-stu-id="9efd5-187">Drag and drop an **If** activity immediately after the **ReceiveAddItem** activity.</span></span> <span data-ttu-id="9efd5-188">To działanie działa tak samo jak w przypadku instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9efd5-188">This activity acts just like an if statement.</span></span>  
  
        1.  <span data-ttu-id="9efd5-189">Ustaw **warunku** właściwości`itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span><span class="sxs-lookup"><span data-stu-id="9efd5-189">Set the **Condition** property to `itemId=="Zune HD" (itemId="Zune HD" for Visual Basic)`</span></span>  
  
        2.  <span data-ttu-id="9efd5-190">Przeciągnij i upuść **przypisać** do działania w **następnie** sekcji, a drugi do **Else** sekcję ustawić właściwości **przypisać** działania, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="9efd5-190">Drag and drop an **Assign** activity in to the **Then** section and another into the **Else** section set the properties of the **Assign** activities as shown in the following illustration.</span></span>  
  
             <span data-ttu-id="9efd5-191">![Przypisywanie wynik wywołania usługi](../../../../docs/framework/wcf/feature-details/media/resultassign.png "ResultAssign")</span><span class="sxs-lookup"><span data-stu-id="9efd5-191">![Assigning the result of the service call](../../../../docs/framework/wcf/feature-details/media/resultassign.png "ResultAssign")</span></span>  
  
             <span data-ttu-id="9efd5-192">Jeśli warunek nie jest `true` **następnie** sekcji zostaną wykonane.</span><span class="sxs-lookup"><span data-stu-id="9efd5-192">If the condition is `true` the **Then** section will be executed.</span></span> <span data-ttu-id="9efd5-193">Jeśli warunek nie jest `false` **Else** sekcji jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="9efd5-193">If the condition is `false` the **Else** section is executed.</span></span>  
  
        3.  <span data-ttu-id="9efd5-194">Wybierz **SendReplyToReceive** działania i zestaw **DisplayName** właściwości pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="9efd5-194">Select the **SendReplyToReceive** activity and set the **DisplayName** property shown in the following illustration.</span></span>  
  
             <span data-ttu-id="9efd5-195">![Ustawianie właściwości działania SendReply](../../../../docs/framework/wcf/feature-details/media/setreply2properties.png "SetReply2Properties")</span><span class="sxs-lookup"><span data-stu-id="9efd5-195">![Setting the SendReply activity properties](../../../../docs/framework/wcf/feature-details/media/setreply2properties.png "SetReply2Properties")</span></span>  
  
        4.  <span data-ttu-id="9efd5-196">Kliknij przycisk **zdefiniuj...**  łącze w **SetReplyToAddItem** działania i skonfiguruj go tak, jak pokazano na poniższej ilustracji.</span><span class="sxs-lookup"><span data-stu-id="9efd5-196">Click the **Define ...** link in the **SetReplyToAddItem** activity and configure it as shown in the following illustration.</span></span> <span data-ttu-id="9efd5-197">Spowoduje to skonfigurowanie **SendReplyToAddItem** działaniu zwracać wartość `orderResult` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9efd5-197">This configures the **SendReplyToAddItem** activity to return the value in the `orderResult` variable.</span></span>  
  
             <span data-ttu-id="9efd5-198">![Ustawienia powiązania danych dla działanie SendReply programu](../../../../docs/framework/wcf/feature-details/media/replytoadditemcontent.gif "ReplyToAddItemContent")</span><span class="sxs-lookup"><span data-stu-id="9efd5-198">![Setting the data binding for the SendReply activit](../../../../docs/framework/wcf/feature-details/media/replytoadditemcontent.gif "ReplyToAddItemContent")</span></span>  
  
8.  <span data-ttu-id="9efd5-199">Otwórz plik web.config i dodaj następujące elementy w \<zachowanie > sekcji, aby umożliwić utrwalania przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9efd5-199">Open the web.config file and add the following elements in the \<behavior> section to enable workflow persistence.</span></span>  
  
    ```xml  
    <sqlWorkflowInstanceStore connectionString="Data Source=your-machine\SQLExpress;Initial Catalog=SQLPersistenceStore;Integrated Security=True;Asynchronous Processing=True" instanceEncodingOption="None" instanceCompletionAction="DeleteAll" instanceLockedExceptionAction="BasicRetry" hostLockRenewalPeriod="00:00:30" runnableInstancesDetectionPeriod="00:00:02" />  
              <workflowIdle timeToUnload="0"/>  
    ```  
  
    > [!WARNING]
    >  <span data-ttu-id="9efd5-200">Upewnij się, że zmieniło hosta i nazwa wystąpienia serwera SQL w poprzednim fragmentu kodu.</span><span class="sxs-lookup"><span data-stu-id="9efd5-200">Make sure to replace your host and SQL server instance name in the previous code snippet.</span></span>  
  
9. <span data-ttu-id="9efd5-201">Skompiluj rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="9efd5-201">Build the solution.</span></span>  
  
### <a name="to-create-a-client-application-to-call-the-workflow-service"></a><span data-ttu-id="9efd5-202">Aby utworzyć aplikację klienta do wywołania tej usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9efd5-202">To Create a Client Application to Call the Workflow Service</span></span>  
  
1.  <span data-ttu-id="9efd5-203">Dodaj nowy projekt aplikacji konsoli o nazwie `OrderClient` do rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9efd5-203">Add a new Console application project called `OrderClient` to the solution.</span></span>  
  
2.  <span data-ttu-id="9efd5-204">Dodaj odwołania do następujących zestawów do `OrderClient` projektu</span><span class="sxs-lookup"><span data-stu-id="9efd5-204">Add references to the following assemblies to the `OrderClient` project</span></span>  
  
    1.  <span data-ttu-id="9efd5-205">System.ServiceModel.dll</span><span class="sxs-lookup"><span data-stu-id="9efd5-205">System.ServiceModel.dll</span></span>  
  
    2.  <span data-ttu-id="9efd5-206">System.ServiceModel.Activities.dll</span><span class="sxs-lookup"><span data-stu-id="9efd5-206">System.ServiceModel.Activities.dll</span></span>  
  
3.  <span data-ttu-id="9efd5-207">Dodaj odwołania do usługi do usługi przepływu pracy i określ `OrderService` jako obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="9efd5-207">Add a service reference to the workflow service and specify `OrderService` as the namespace.</span></span>  
  
4.  <span data-ttu-id="9efd5-208">W `Main()` metody projektu klienta, Dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="9efd5-208">In the `Main()` method of the client project add the following code:</span></span>  
  
    ```  
    static void Main(string[] args)  
    {  
       // Send initial message to start the workflow service  
       Console.WriteLine("Sending start message");  
       StartOrderClient startProxy = new StartOrderClient();  
       string orderId = startProxy.StartOrder("Kim Abercrombie");  
  
       // The workflow service is now waiting for the second message to be sent  
       Console.WriteLine("Workflow service is idle...");  
       Console.WriteLine("Press [ENTER] to send an add item message to reactivate the workflow service...");  
       Console.ReadLine();  
  
       // Send the second message  
       Console.WriteLine("Sending add item message");  
       AddItemClient addProxy = new AddItemClient();  
       AddItem item = new AddItem();  
       item.p_itemId = "Zune HD";  
       item.p_orderId = orderId;  
  
       string orderResult = addProxy.AddItem(item);  
       Console.WriteLine("Service returned: " + orderResult);  
    }  
    ```  
  
5.  <span data-ttu-id="9efd5-209">Skompiluj rozwiązanie, a następnie uruchom `OrderClient` aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9efd5-209">Build the solution and run the `OrderClient` application.</span></span> <span data-ttu-id="9efd5-210">Klient zostanie wyświetlony następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="9efd5-210">The client will display the following text:</span></span>  
  
    ```Output  
    Sending start messageWorkflow service is idle...Press [ENTER] to send an add item message to reactivate the workflow service...  
    ```  
  
6.  <span data-ttu-id="9efd5-211">Aby sprawdzić, czy utrwaleniu usługi przepływu pracy, uruchom program SQL Server Management Studio, przechodząc do **Start** menu, wybranie opcji **wszystkie programy**, **Microsoft SQL Server 2008**, **Programu SQL Server Management Studio**.</span><span class="sxs-lookup"><span data-stu-id="9efd5-211">To verify that the workflow service has been persisted, start the SQL Server Management Studio by going to the **Start** menu, Selecting **All Programs**, **Microsoft SQL Server 2008**, **SQL Server Management Studio**.</span></span>  
  
    1.  <span data-ttu-id="9efd5-212">W okienku po lewej stronie rozwiń węzeł, **baz danych**, **SQLPersistenceStore**, **widoków** i kliknij prawym przyciskiem myszy **System.Activities.DurableInstancing.Instances**  i wybierz **zaznacz 1000 pierwszych wierszy**.</span><span class="sxs-lookup"><span data-stu-id="9efd5-212">In the left hand pane expand, **Databases**, **SQLPersistenceStore**, **Views** and right click **System.Activities.DurableInstancing.Instances** and select **Select Top 1000 Rows**.</span></span> <span data-ttu-id="9efd5-213">W **wyniki** Sprawdź okienko zobacz co najmniej jedno wystąpienie na liście.</span><span class="sxs-lookup"><span data-stu-id="9efd5-213">In the **Results** pane verify you see at least one instance listed.</span></span> <span data-ttu-id="9efd5-214">Mogą istnieć inne wystąpienia z poprzednie uruchomienia, jeśli wystąpił wyjątek podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="9efd5-214">There may be other instances from prior runs if an exception occurred while running.</span></span> <span data-ttu-id="9efd5-215">Możesz usunąć istniejące wiersze, klikając prawym przyciskiem myszy **System.Activities.DurableInstancing.Instances** i wybierając **Edytuj pierwszych 200 wierszy**, naciskając klawisz **Execute** przycisku wybranie wszystkich wierszy w okienku wyników, a użycie **usunąć**.</span><span class="sxs-lookup"><span data-stu-id="9efd5-215">You can delete existing rows by right clicking **System.Activities.DurableInstancing.Instances** and selecting **Edit Top 200 rows**, pressing the **Execute** button, selecting all rows in the results pane and selecting **delete**.</span></span>  <span data-ttu-id="9efd5-216">Aby sprawdzić wystąpienia wyświetlana w bazie danych jest wystąpienie aplikacji utworzone, sprawdź, widok wystąpienia jest pusta, przed uruchomieniem klienta.</span><span class="sxs-lookup"><span data-stu-id="9efd5-216">To verify the instance displayed in the database is the instance your application created, verify the instances view is empty prior to running the client.</span></span> <span data-ttu-id="9efd5-217">Gdy klient jest uruchomiony ponownie uruchom zapytanie (zaznacz 1000 pierwszych wierszy) i sprawdź dodano nowe wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="9efd5-217">Once the client is running re-run the query (Select Top 1000 Rows) and verify a new instance has been added.</span></span>  
  
7.  <span data-ttu-id="9efd5-218">Naciśnij klawisz enter, aby wysłać wiadomość elementu Dodaj do usługi przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="9efd5-218">Press enter to send the add item message to the workflow service.</span></span> <span data-ttu-id="9efd5-219">Klient zostanie wyświetlony następujący tekst:</span><span class="sxs-lookup"><span data-stu-id="9efd5-219">The client will display the following text:</span></span>  
  
    ```Output  
    Sending add item messageService returned: Item added to orderPress any key to continue . . .  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9efd5-220">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9efd5-220">See Also</span></span>  
 [<span data-ttu-id="9efd5-221">Usługi przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="9efd5-221">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)