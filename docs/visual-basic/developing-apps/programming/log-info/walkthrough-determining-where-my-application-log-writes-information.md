---
title: Ustalanie, gdzie My.Application.Log zapisuje informacje (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My.Log object, output location
- output, application log location
- My.Application.Log object, outpout location
- event logs, determining output location
- application event logs, output location
- applications [Visual Basic], output location
ms.assetid: 5b70143a-7741-45f2-ae1d-03324a3a4189
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4df7a80907b29a5eea79992f46c46603cbe2cc81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-determining-where-myapplicationlog-writes-information-visual-basic"></a><span data-ttu-id="c0155-102">Wskazówki: ustalanie, gdzie My.Application.Log zapisuje informacje (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0155-102">Walkthrough: Determining Where My.Application.Log Writes Information (Visual Basic)</span></span>
<span data-ttu-id="c0155-103">`My.Application.Log` Obiektu można zapisać informacji do kilku odbiorniki dzienników.</span><span class="sxs-lookup"><span data-stu-id="c0155-103">The `My.Application.Log` object can write information to several log listeners.</span></span> <span data-ttu-id="c0155-104">Odbiorniki logu są konfigurowane przez plik konfiguracji komputera i może zostać zastąpiona przez pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0155-104">The log listeners are configured by the computer's configuration file and can be overridden by an application's configuration file.</span></span> <span data-ttu-id="c0155-105">W tym temacie opisano ustawienia domyślne i jak określić ustawienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0155-105">This topic describes the default settings and how to determine the settings for your application.</span></span>  
  
 <span data-ttu-id="c0155-106">Aby uzyskać więcej informacji o domyślnych lokalizacji danych wyjściowych, zobacz [Praca z dziennikami aplikacji](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span><span class="sxs-lookup"><span data-stu-id="c0155-106">For more information about the default output locations, see [Working with Application Logs](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md).</span></span>  
  
### <a name="to-determine-the-listeners-for-myapplicationlog"></a><span data-ttu-id="c0155-107">Aby określić odbiorników dla obiektu My.Application.Log</span><span class="sxs-lookup"><span data-stu-id="c0155-107">To determine the listeners for My.Application.Log</span></span>  
  
1.  <span data-ttu-id="c0155-108">Zlokalizuj plik konfiguracji zestawu.</span><span class="sxs-lookup"><span data-stu-id="c0155-108">Locate the assembly's configuration file.</span></span> <span data-ttu-id="c0155-109">Jeśli tworzysz zestawu, możesz uzyskać dostęp app.config w [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] z **Eksploratora rozwiązań**.</span><span class="sxs-lookup"><span data-stu-id="c0155-109">If you are developing the assembly, you can access the app.config in [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] from the **Solution Explorer**.</span></span> <span data-ttu-id="c0155-110">W przeciwnym razie nazwa pliku konfiguracji jest nazwą zestawu dołączony ".config" i znajduje się w tym samym katalogu co zestaw.</span><span class="sxs-lookup"><span data-stu-id="c0155-110">Otherwise, the configuration file name is the assembly's name appended with ".config", and it is located in the same directory as the assembly.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="c0155-111">Nie każdy zestaw ma pliku konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="c0155-111">Not every assembly has a configuration file.</span></span>  
  
     <span data-ttu-id="c0155-112">Plik konfiguracji jest plikiem XML.</span><span class="sxs-lookup"><span data-stu-id="c0155-112">The configuration file is an XML file.</span></span>  
  
2.  <span data-ttu-id="c0155-113">Zlokalizuj `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource" znajduje się w `<sources>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="c0155-113">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", located in the `<sources>` section.</span></span> <span data-ttu-id="c0155-114">`<sources>` Sekcja znajduje się w `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="c0155-114">The `<sources>` section is located in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
     <span data-ttu-id="c0155-115">Jeśli nie istnieją następujące sekcje, a następnie skonfigurować pliku konfiguracji komputera `My.Application.Log` dziennika odbiorników.</span><span class="sxs-lookup"><span data-stu-id="c0155-115">If these sections do not exist, then the computer's configuration file may configure the `My.Application.Log` log listeners.</span></span> <span data-ttu-id="c0155-116">W poniższych krokach opisano sposób określania definiuje plik konfiguracji komputera:</span><span class="sxs-lookup"><span data-stu-id="c0155-116">The following steps describe how to determine what the computer configuration file defines:</span></span>  
  
    1.  <span data-ttu-id="c0155-117">Znajdź plik machine.config komputera.</span><span class="sxs-lookup"><span data-stu-id="c0155-117">Locate the computer's machine.config file.</span></span> <span data-ttu-id="c0155-118">Zazwyczaj znajduje się on w *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* katalogu, gdzie `SystemRoot` katalog systemu operacyjnego i `frameworkVersion` jest wersja [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c0155-118">Typically, it is located in the *SystemRoot\Microsoft.NET\Framework\frameworkVersion\CONFIG* directory, where `SystemRoot` is the operating system directory, and `frameworkVersion` is the version of the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
         <span data-ttu-id="c0155-119">Ustawienia w pliku machine.config może zostać przesłonięta przez pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0155-119">The settings in machine.config can be overridden by an application's configuration file.</span></span>  
  
         <span data-ttu-id="c0155-120">Jeśli nie istnieją elementy opcjonalne wymienione poniżej, można je utworzyć.</span><span class="sxs-lookup"><span data-stu-id="c0155-120">If the optional elements listed below do not exist, you can create them.</span></span>  
  
    2.  <span data-ttu-id="c0155-121">Zlokalizuj `<listeners>` sekcji w `<source>` sekcji z `name` atrybutu "DefaultSource" w `<sources>` sekcji w `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="c0155-121">Locate the `<listeners>` section, in the `<source>` section with the `name` attribute "DefaultSource", in the `<sources>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
         <span data-ttu-id="c0155-122">Jeśli nie istnieją tych sekcji, a następnie `My.Application.Log` ma odbiorniki logu domyślne.</span><span class="sxs-lookup"><span data-stu-id="c0155-122">If these sections do not exist, then the `My.Application.Log` has only the default log listeners.</span></span>  
  
3.  <span data-ttu-id="c0155-123">Zlokalizuj <`add>` elementów <`listeners>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="c0155-123">Locate the <`add>` elements in the <`listeners>` section.</span></span>  
  
     <span data-ttu-id="c0155-124">Odbiorniki logu nazwanego, aby dodać te elementy `My.Application.Log` źródła.</span><span class="sxs-lookup"><span data-stu-id="c0155-124">These elements add the named log listeners to `My.Application.Log` source.</span></span>  
  
4.  <span data-ttu-id="c0155-125">Zlokalizuj `<add>` elementy z nazwami odbiorniki logu w `<sharedListeners>` sekcji w `<system.diagnostics>` części, lokacja najwyższego poziomu `<configuration>` sekcji.</span><span class="sxs-lookup"><span data-stu-id="c0155-125">Locate the `<add>` elements with the names of the log listeners in the `<sharedListeners>` section, in the `<system.diagnostics>` section, in the top-level `<configuration>` section.</span></span>  
  
5.  <span data-ttu-id="c0155-126">Dla wielu typów udostępnione obiekty nasłuchujące dane inicjowania odbiornika zawiera opis gdzie odbiornika kieruje dane:</span><span class="sxs-lookup"><span data-stu-id="c0155-126">For many types of shared listeners, the listener's initialization data includes a description of where the listener directs the data:</span></span>  
  
    -   <span data-ttu-id="c0155-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> odbiornika zapisuje do pliku dziennika, zgodnie z opisem w wprowadzenie.</span><span class="sxs-lookup"><span data-stu-id="c0155-127">A <xref:Microsoft.VisualBasic.Logging.FileLogTraceListener?displayProperty=nameWithType> listener writes to a file log, as described in the introduction.</span></span>  
  
    -   <span data-ttu-id="c0155-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> odbiornika zapisuje informacje w dzienniku zdarzeń komputera określona przez `initializeData` parametru.</span><span class="sxs-lookup"><span data-stu-id="c0155-128">A <xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType> listener writes information to the computer event log specified by the `initializeData` parameter.</span></span> <span data-ttu-id="c0155-129">Aby wyświetlić dziennik zdarzeń, można użyć **Eksploratora serwera** lub **Podgląd zdarzeń systemu Windows**.</span><span class="sxs-lookup"><span data-stu-id="c0155-129">To view an event log, you can use **Server Explorer** or **Windows Event Viewer**.</span></span> <span data-ttu-id="c0155-130">Aby uzyskać więcej informacji, zobacz [zdarzenia ETW w programie .NET Framework](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299).</span><span class="sxs-lookup"><span data-stu-id="c0155-130">For more information, see [ETW Events in the .NET Framework](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299).</span></span>  
  
    -   <span data-ttu-id="c0155-131"><xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> i <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> odbiorników zapisać do pliku określonego w `initializeData` parametru.</span><span class="sxs-lookup"><span data-stu-id="c0155-131">The <xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType> and <xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType> listeners write to the file specified in the `initializeData` parameter.</span></span>  
  
    -   <span data-ttu-id="c0155-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> odbiornika zapisuje do wiersza polecenia konsoli.</span><span class="sxs-lookup"><span data-stu-id="c0155-132">A <xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType> listener writes to the command-line console.</span></span>  
  
    -   <span data-ttu-id="c0155-133">Aby dowiedzieć się, w którym innych typów odbiorniki logu zapisywać informacje zapoznaj się dokumentacją tego typu.</span><span class="sxs-lookup"><span data-stu-id="c0155-133">For information about where other types of log listeners write information, consult that type's documentation.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0155-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c0155-134">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Logging.Log?displayProperty=nameWithType>  
 <xref:System.Diagnostics.DefaultTraceListener>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.DelimitedListTraceListener>  
 <xref:System.Diagnostics.XmlWriterTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics>  
 [<span data-ttu-id="c0155-135">Praca z dziennikami aplikacji</span><span class="sxs-lookup"><span data-stu-id="c0155-135">Working with Application Logs</span></span>](../../../../visual-basic/developing-apps/programming/log-info/working-with-application-logs.md)  
 [<span data-ttu-id="c0155-136">Porady: wyjątki rejestru</span><span class="sxs-lookup"><span data-stu-id="c0155-136">How to: Log Exceptions</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-log-exceptions.md)  
 [<span data-ttu-id="c0155-137">Porady: zapisywanie wiadomości rejestru</span><span class="sxs-lookup"><span data-stu-id="c0155-137">How to: Write Log Messages</span></span>](../../../../visual-basic/developing-apps/programming/log-info/how-to-write-log-messages.md)  
 [<span data-ttu-id="c0155-138">Wskazówki: Zmienianie, gdzie My.Application.Log zapisuje informacje</span><span class="sxs-lookup"><span data-stu-id="c0155-138">Walkthrough: Changing Where My.Application.Log Writes Information</span></span>](../../../../visual-basic/developing-apps/programming/log-info/walkthrough-changing-where-my-application-log-writes-information.md)  
 [<span data-ttu-id="c0155-139">Zdarzenia ETW w programie .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c0155-139">ETW Events in the .NET Framework</span></span>](http://msdn.microsoft.com/library/d186276f-6afb-4dfd-bf3c-4251edc2c299)  
 [<span data-ttu-id="c0155-140">Rozwiązywanie problemów: Odbiorniki logu</span><span class="sxs-lookup"><span data-stu-id="c0155-140">Troubleshooting: Log Listeners</span></span>](../../../../visual-basic/developing-apps/programming/log-info/troubleshooting-log-listeners.md)