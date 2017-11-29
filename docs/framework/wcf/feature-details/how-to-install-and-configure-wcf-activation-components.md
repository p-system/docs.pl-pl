---
title: "Instrukcje: Instalowanie i konfigurowanie składników aktywacji programu WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: HTTP activation [WCF]
ms.assetid: 33a7054a-73ec-464d-83e5-b203aeded658
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77dec85ee12250080fc487d120749892a148ef17
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-install-and-configure-wcf-activation-components"></a><span data-ttu-id="83a10-102">Instrukcje: Instalowanie i konfigurowanie składników aktywacji programu WCF</span><span class="sxs-lookup"><span data-stu-id="83a10-102">How to: Install and Configure WCF Activation Components</span></span>
<span data-ttu-id="83a10-103">W tym temacie opisano kroki wymagane do skonfigurowania Windows Process Activation Service (znanej także jako Usługa WAS) na [!INCLUDE[wv](../../../../includes/wv-md.md)] hosta [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] protokoły sieciowe usług, które nie komunikują się za pośrednictwem protokołu HTTP.</span><span class="sxs-lookup"><span data-stu-id="83a10-103">This topic describes the steps required to set up Windows Process Activation Service (also known as WAS) on [!INCLUDE[wv](../../../../includes/wv-md.md)] to host [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services that do not communicate over HTTP network protocols.</span></span> <span data-ttu-id="83a10-104">W poniższych sekcjach opisano czynności dla tej konfiguracji:</span><span class="sxs-lookup"><span data-stu-id="83a10-104">The following sections outline the steps for this configuration:</span></span>  
  
-   <span data-ttu-id="83a10-105">Zainstaluj (lub potwierdź instalacji) [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] składników aktywacji.</span><span class="sxs-lookup"><span data-stu-id="83a10-105">Install (or confirm the installation of) the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] activation components.</span></span>  
  
-   <span data-ttu-id="83a10-106">Skonfiguruj WAS do obsługi protokołu innego niż HTTP.</span><span class="sxs-lookup"><span data-stu-id="83a10-106">Configure WAS to support a non-HTTP protocol.</span></span> <span data-ttu-id="83a10-107">Poniższa procedura umożliwia skonfigurowanie [!INCLUDE[wv](../../../../includes/wv-md.md)] aktywacji TCP.</span><span class="sxs-lookup"><span data-stu-id="83a10-107">The following procedure configures [!INCLUDE[wv](../../../../includes/wv-md.md)] for TCP activation.</span></span>  
  
 <span data-ttu-id="83a10-108">Po zainstalowaniu i skonfigurowaniu WAS, zobacz [porady: hostowanie usługi WCF w WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) dla procedury tworzenia [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi udostępniającej punktu końcowego protokołu HTTP, który wykorzystuje WAS.</span><span class="sxs-lookup"><span data-stu-id="83a10-108">After installing and configuring WAS, see [How to: Host a WCF Service in WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md) for the procedures to create a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that exposes an non-HTTP endpoint that employs WAS.</span></span>  
  
### <a name="to-install-the-wcf-non-http-activation-components"></a><span data-ttu-id="83a10-109">Aby zainstalować składniki Aktywacja bez HTTP programu WCF</span><span class="sxs-lookup"><span data-stu-id="83a10-109">To install the WCF non-HTTP activation components</span></span>  
  
1.  <span data-ttu-id="83a10-110">Kliknij przycisk **Start** przycisk, a następnie kliknij przycisk **Panelu sterowania**.</span><span class="sxs-lookup"><span data-stu-id="83a10-110">Click the **Start** button, and then click **Control Panel**.</span></span>  
  
2.  <span data-ttu-id="83a10-111">Kliknij przycisk **programy**, a następnie kliknij przycisk **programy i funkcje**.</span><span class="sxs-lookup"><span data-stu-id="83a10-111">Click **Programs**, and then click **Programs and Features**.</span></span>  
  
3.  <span data-ttu-id="83a10-112">Na **zadania** menu, kliknij przycisk **Włącz lub wyłącz funkcje systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="83a10-112">On the **Tasks** menu, click **Turn Windows features on or off**.</span></span>  
  
4.  <span data-ttu-id="83a10-113">Znajdź [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] węzła, wybierz, a następnie rozwiń węzeł.</span><span class="sxs-lookup"><span data-stu-id="83a10-113">Find the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] node, select and then expand it.</span></span>  
  
5.  <span data-ttu-id="83a10-114">Wybierz **składników aktywacji programu WCF bez Http** i Zapisz ustawienia.</span><span class="sxs-lookup"><span data-stu-id="83a10-114">Select the **WCF Non-Http Activation Components** box and save the setting.</span></span>  
  
### <a name="to-configure-the-was-to-support-tcp-activation"></a><span data-ttu-id="83a10-115">Aby skonfigurować usługi WAS do obsługi aktywacji TCP</span><span class="sxs-lookup"><span data-stu-id="83a10-115">To configure the WAS to support TCP activation</span></span>  
  
1.  <span data-ttu-id="83a10-116">Aby zapewnić obsługę aktywacji net.tcp, domyślnej witryny sieci Web musi zostać powiązana do portów net.tcp.</span><span class="sxs-lookup"><span data-stu-id="83a10-116">To support net.tcp activation, the default Web site must first be bound to a net.tcp port.</span></span> <span data-ttu-id="83a10-117">Można to zrobić za pomocą Appcmd.exe, który jest instalowany z [!INCLUDE[iisver](../../../../includes/iisver-md.md)] narzędzi zarządzania.</span><span class="sxs-lookup"><span data-stu-id="83a10-117">You can do this by using Appcmd.exe, which is installed with the [!INCLUDE[iisver](../../../../includes/iisver-md.md)] management toolset.</span></span> <span data-ttu-id="83a10-118">W oknie wiersza polecenia uprawnień administratora uruchom następujące polecenie.</span><span class="sxs-lookup"><span data-stu-id="83a10-118">In an administrator-level Command Prompt window, run the following command.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site" -+bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="83a10-119">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="83a10-119">This command is a single line of text.</span></span> <span data-ttu-id="83a10-120">To polecenie dodaje powiązania witryny net.tcp, do domyślnej witryny sieci Web nasłuchiwanie na porcie TCP 808 z żadną nazwą hosta.</span><span class="sxs-lookup"><span data-stu-id="83a10-120">This command adds a net.tcp site binding to the default Web site listening on TCP port 808 with any host name.</span></span>  
  
2.  <span data-ttu-id="83a10-121">Mimo że wszystkie aplikacje w obrębie lokacji korzystają wspólnej powiązanie net.tcp, każdej aplikacji można włączyć obsługę net.tcp pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="83a10-121">Although all applications within a site share a common net.tcp binding, each application can enable net.tcp support individually.</span></span> <span data-ttu-id="83a10-122">Aby włączyć net.tcp dla aplikacji, uruchom następujące polecenie z wiersza polecenia z uprawnieniami administratora na poziomie.</span><span class="sxs-lookup"><span data-stu-id="83a10-122">To enable net.tcp for the application, run the following command from an administrator-level command prompt.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app   
    "Default Web Site/<WCF Application>" /enabledProtocols:http,net.tcp  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="83a10-123">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="83a10-123">This command is a single line of text.</span></span> <span data-ttu-id="83a10-124">To polecenie włącza /\<*aplikacja WCF*> aplikacji, aby uzyskać dostęp za pomocą obu http://localhost*/\<aplikacja WCF >* i net.tcp:// localhost /*\<aplikacja WCF >*.</span><span class="sxs-lookup"><span data-stu-id="83a10-124">This command enables the /\<*WCF Application*> application to be accessed using both http://localhost*/\<WCF Application>* and net.tcp://localhost/*\<WCF Application>*.</span></span>  
  
     <span data-ttu-id="83a10-125">Usuń powiązanie witryny net.tcp, dodane dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="83a10-125">Remove the net.tcp site binding you added for this sample.</span></span>  
  
     <span data-ttu-id="83a10-126">Dla wygody następujące dwa kroki są implementowane w pliku wsadowym o nazwie RemoveNetTcpSiteBinding.cmd znajduje się w katalogu próbki.</span><span class="sxs-lookup"><span data-stu-id="83a10-126">As a convenience, the following two steps are implemented in a batch file called RemoveNetTcpSiteBinding.cmd located in the sample directory.</span></span>  
  
    1.  <span data-ttu-id="83a10-127">Usuń net.tcp z listy włączonych protokołów, uruchamiając następujące polecenie w oknie wiersza polecenia poziomie administratora.</span><span class="sxs-lookup"><span data-stu-id="83a10-127">Remove net.tcp from the list of enabled protocols by running the following command in an administrator-level Command Prompt window.</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set app   
        "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="83a10-128">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="83a10-128">This command is a single line of text.</span></span>  
  
    2.  <span data-ttu-id="83a10-129">Usuń powiązanie witryny net.tcp, uruchamiając następujące polecenie w oknie wiersza polecenia z podwyższonym poziomem uprawnień:</span><span class="sxs-lookup"><span data-stu-id="83a10-129">Remove the net.tcp site binding by running the following command in an elevated Command Prompt window:</span></span>  
  
        ```  
        %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
        --bindings.[protocol='net.tcp',bindingInformation='808:*']  
        ```  
  
        > [!NOTE]
        >  <span data-ttu-id="83a10-130">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="83a10-130">This command is a single line of text.</span></span>  
  
### <a name="to-remove-nettcp-from-the-list-of-enabled-protocols"></a><span data-ttu-id="83a10-131">Aby usunąć z listy włączonych protokołów net.tcp</span><span class="sxs-lookup"><span data-stu-id="83a10-131">To remove net.tcp from the list of enabled protocols</span></span>  
  
1.  <span data-ttu-id="83a10-132">Aby usunąć net.tcp z listy włączonych protokołów, uruchom następujące polecenie w oknie wiersza polecenia poziomie administratora.</span><span class="sxs-lookup"><span data-stu-id="83a10-132">To remove net.tcp from the list of enabled protocols, run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set app "Default Web Site/servicemodelsamples<WCF Application>" " /enabledProtocols:http  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="83a10-133">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="83a10-133">This command is a single line of text.</span></span>  
  
### <a name="to-remove-the-nettcp-site-binding"></a><span data-ttu-id="83a10-134">Aby usunąć powiązanie witryny usługi net.tcp</span><span class="sxs-lookup"><span data-stu-id="83a10-134">To remove the net.tcp site binding</span></span>  
  
1.  <span data-ttu-id="83a10-135">Aby usunąć lokację net.tcp powiązanie uruchom następujące polecenie w oknie wiersza polecenia poziomie administratora.</span><span class="sxs-lookup"><span data-stu-id="83a10-135">To remove the net.tcp site binding run the following command in an administrator-level Command Prompt window.</span></span>  
  
    ```  
    %windir%\system32\inetsrv\appcmd.exe set site "Default Web Site"   
    -bindings.[protocol='net.tcp',bindingInformation='808:*']  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="83a10-136">To polecenie jest pojedynczy wiersz tekstu.</span><span class="sxs-lookup"><span data-stu-id="83a10-136">This command is a single line of text.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83a10-137">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="83a10-137">See Also</span></span>  
 [<span data-ttu-id="83a10-138">Aktywacja TCP</span><span class="sxs-lookup"><span data-stu-id="83a10-138">TCP Activation</span></span>](../../../../docs/framework/wcf/samples/tcp-activation.md)  
 [<span data-ttu-id="83a10-139">Aktywacja usługi MSMQ</span><span class="sxs-lookup"><span data-stu-id="83a10-139">MSMQ Activation</span></span>](../../../../docs/framework/wcf/samples/msmq-activation.md)  
 [<span data-ttu-id="83a10-140">Aktywowanie elementu Namedpipe</span><span class="sxs-lookup"><span data-stu-id="83a10-140">NamedPipe Activation</span></span>](../../../../docs/framework/wcf/samples/namedpipe-activation.md)  
 [<span data-ttu-id="83a10-141">Windows Server AppFabric funkcje hostingu</span><span class="sxs-lookup"><span data-stu-id="83a10-141">Windows Server App Fabric Hosting Features</span></span>](http://go.microsoft.com/fwlink/?LinkId=201276)