---
title: Hosting .NET Core
description: "Hostowanie środowiska uruchomieniowego .NET Core z kodu natywnego"
keywords: .NET, .NET core hostingu, Hosting .NET Core
author: mjrousos
ms.author: mikerou
ms.date: 2/3/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13edec8b-614d-47ed-9e95-ed6d3b94ec0c
ms.openlocfilehash: 1f0983b909244dda7270d3eff01dc302383639a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="hosting-net-core"></a><span data-ttu-id="f8f27-104">Hosting .NET Core</span><span class="sxs-lookup"><span data-stu-id="f8f27-104">Hosting .NET Core</span></span>

<span data-ttu-id="f8f27-105">Podobnie jak wszystkie kodu zarządzanego aplikacje .NET Core są wykonywane przez hosta.</span><span class="sxs-lookup"><span data-stu-id="f8f27-105">Like all managed code, .NET Core applications are executed by a host.</span></span> <span data-ttu-id="f8f27-106">Host jest odpowiedzialna za uruchamianie środowiska uruchomieniowego (w tym składników, takich jak JIT i moduł zbierający elementy bezużyteczne), tworzenie aplikacji i wywoływanie zarządzać punktów wejścia.</span><span class="sxs-lookup"><span data-stu-id="f8f27-106">The host is responsible for starting the runtime (including components like the JIT and garbage collector), creating AppDomains, and invoking managed entry points.</span></span>

<span data-ttu-id="f8f27-107">Hostowanie środowiska uruchomieniowego .NET Core zaawansowanego scenariusza i, w większości przypadków .NET Core deweloperzy nie musisz martwić się o hosting ponieważ procesy kompilacji platformy .NET Core zapewnia domyślnego hosta do uruchamiania aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f8f27-107">Hosting the .NET Core runtime is an advanced scenario and, in most cases, .NET Core developers don't need to worry about hosting because .NET Core build processes provide a default host to run .NET Core applications.</span></span> <span data-ttu-id="f8f27-108">W niektórych sytuacjach specjalne jednak może być przydatne do jawnie hosta środowiska uruchomieniowego .NET Core, albo jako sposób wywoływania z kodu zarządzanego w procesie native lub w celu uzyskania większą kontrolę nad sposób działania środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f8f27-108">In some specialized circumstances, though, it can be useful to explicitly host the .NET Core runtime, either as a means of invoking managed code in a native process or in order to gain more control over how the runtime works.</span></span>

<span data-ttu-id="f8f27-109">Ten artykuł zawiera omówienie kroki niezbędne do uruchomienia środowiska uruchomieniowego .NET Core z kodu macierzystego, Tworzenie domeny aplikacji początkowej (<xref:System.AppDomain>) i wykonywanie kodu zarządzanego w nim.</span><span class="sxs-lookup"><span data-stu-id="f8f27-109">This article gives an overview of the steps necessary to start the .NET Core runtime from native code, create an initial application domain (<xref:System.AppDomain>), and execute managed code in it.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f8f27-110">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f8f27-110">Prerequisites</span></span>

<span data-ttu-id="f8f27-111">Natywnych aplikacji nie są hosty, w tym samouczku opisano konstruowanie aplikacji C++, na hoście platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f8f27-111">Because hosts are native applications, this tutorial will cover constructing a C++ application to host .NET Core.</span></span> <span data-ttu-id="f8f27-112">Konieczne będzie środowiska programowania C++ (takim jak udostępniany przez [programu Visual Studio](https://www.visualstudio.com/downloads/)).</span><span class="sxs-lookup"><span data-stu-id="f8f27-112">You will need a C++ development environment (such as that provided by [Visual Studio](https://www.visualstudio.com/downloads/)).</span></span>

<span data-ttu-id="f8f27-113">Trzeba będzie także prostą aplikację .NET Core, aby przetestować hosta, dlatego należy zainstalować [.NET Core SDK](https://www.microsoft.com/net/core) i [kompilacji małych przetestuj aplikację .NET Core](../../core/tutorials/with-visual-studio.md) (na przykład aplikacja "Hello World").</span><span class="sxs-lookup"><span data-stu-id="f8f27-113">You will also want a simple .NET Core application to test the host with, so you should install the [.NET Core SDK](https://www.microsoft.com/net/core) and [build a small .NET Core test app](../../core/tutorials/with-visual-studio.md) (such as a 'Hello World' app).</span></span> <span data-ttu-id="f8f27-114">Aplikacja "Hello World" utworzone przez nowy szablon projektu konsoli .NET Core jest wystarczająca.</span><span class="sxs-lookup"><span data-stu-id="f8f27-114">The 'Hello World' app created by the new .NET Core console project template is sufficient.</span></span>

<span data-ttu-id="f8f27-115">W tym samouczku i jego skojarzony przykładowa kompilacji hosta systemu Windows; Zobacz uwagi na końcu tego artykułu o hostingu w systemie Unix.</span><span class="sxs-lookup"><span data-stu-id="f8f27-115">This tutorial and its associated sample build a Windows host; see the notes at the end of this article about hosting on Unix.</span></span>

## <a name="creating-the-host"></a><span data-ttu-id="f8f27-116">Tworzenie hosta</span><span class="sxs-lookup"><span data-stu-id="f8f27-116">Creating the host</span></span>

<span data-ttu-id="f8f27-117">A [hosta próbki](https://github.com/dotnet/docs/tree/master/samples/core/hosting) Demonstrowanie procedury opisane w tym artykule jest dostępny w repozytorium GitHub dotnet/docs.</span><span class="sxs-lookup"><span data-stu-id="f8f27-117">A [sample host](https://github.com/dotnet/docs/tree/master/samples/core/hosting) demonstrating the steps outlined in this article is available in the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="f8f27-118">Komentarze w przykładowym *host.cpp* pliku wyraźnie Skojarz ponumerowane kroki z tego samouczka, z którym jest przeprowadzana w próbce.</span><span class="sxs-lookup"><span data-stu-id="f8f27-118">Comments in the sample's *host.cpp* file clearly associate the numbered steps from this tutorial with where they're performed in the sample.</span></span> <span data-ttu-id="f8f27-119">Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="f8f27-119">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="f8f27-120">Należy pamiętać, że host próbki jest przeznaczona do zastosowania w przypadku uczenia celów, więc jest lekki na sprawdzanie błędów ani zaprojektowano w celu wyróżnienia czytelności za pośrednictwem wydajności.</span><span class="sxs-lookup"><span data-stu-id="f8f27-120">Keep in mind that the sample host is meant to be used for learning purposes, so it is light on error checking and is designed to emphasize readability over efficiency.</span></span> <span data-ttu-id="f8f27-121">Więcej przykładów w rzeczywistych hosta są dostępne w [dotnet/środowisko coreclr](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="f8f27-121">More real-world host samples are available in the [dotnet/coreclr](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts) repository.</span></span> <span data-ttu-id="f8f27-122">[Hosta CoreRun](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun), w szczególności jest dobrym hosta ogólnego przeznaczenia badanie po odczytaniu za pośrednictwem próbki prostsze.</span><span class="sxs-lookup"><span data-stu-id="f8f27-122">The [CoreRun host](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun), in particular, is a good general-purpose host to study after reading through the simpler sample.</span></span>

### <a name="a-note-about-mscoreeh"></a><span data-ttu-id="f8f27-123">Uwagi dotyczące mscoree.h</span><span class="sxs-lookup"><span data-stu-id="f8f27-123">A note about mscoree.h</span></span>
<span data-ttu-id="f8f27-124">Podstawowy .NET Core interfejs hosta (`ICLRRuntimeHost2`) jest zdefiniowany w [MSCOREE. IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL).</span><span class="sxs-lookup"><span data-stu-id="f8f27-124">The primary .NET Core hosting interface (`ICLRRuntimeHost2`) is defined in [MSCOREE.IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL).</span></span> <span data-ttu-id="f8f27-125">Nagłówkiem w wersji tego pliku (mscoree.h), hosta należy do odwołania, jest generowany przez MIDL podczas [podstawowego środowiska wykonawczego .NET](https://github.com/dotnet/coreclr/) jest wbudowana.</span><span class="sxs-lookup"><span data-stu-id="f8f27-125">A header version of this file (mscoree.h), which your host will need to reference, is produced via MIDL when the [.NET Core runtime](https://github.com/dotnet/coreclr/) is built.</span></span> <span data-ttu-id="f8f27-126">Jeśli nie chcesz utworzyć środowiska uruchomieniowego .NET Core, mscoree.h jest również dostępny jako [wstępnie skompilowanego nagłówka](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) w repozytorium dotnet/środowisko coreclr.</span><span class="sxs-lookup"><span data-stu-id="f8f27-126">If you do not want to build the .NET Core runtime, mscoree.h is also available as a [pre-built header](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) in the dotnet/coreclr repository.</span></span> <span data-ttu-id="f8f27-127">[Instrukcje dotyczące tworzenia środowiska uruchomieniowego .NET Core](https://github.com/dotnet/coreclr#building-the-repository) znajdują się w repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="f8f27-127">[Instructions on building the .NET Core runtime](https://github.com/dotnet/coreclr#building-the-repository) can be found in its GitHub repository.</span></span> 

### <a name="step-1---identify-the-managed-entry-point"></a><span data-ttu-id="f8f27-128">Krok 1 — ustalenie zarządzany punkt wejścia</span><span class="sxs-lookup"><span data-stu-id="f8f27-128">Step 1 - Identify the managed entry point</span></span>
<span data-ttu-id="f8f27-129">Po odwołujące się do niezbędne nagłówki ([mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) i stdio.h, na przykład), przede wszystkim hosta .NET Core trzeba wykonać jest zlokalizować punktu wejścia zarządzanych, będzie używana.</span><span class="sxs-lookup"><span data-stu-id="f8f27-129">After referencing necessary headers ([mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) and stdio.h, for example), one of the first things a .NET Core host must do is locate the managed entry point it will be using.</span></span> <span data-ttu-id="f8f27-130">W naszym hosta próbki odbywa się wykonując tylko pierwszy argument wiersza polecenia do naszej hosta jako ścieżka do pliku binarnego, zarządzane którego `main` będzie można wykonać metody.</span><span class="sxs-lookup"><span data-stu-id="f8f27-130">In our sample host, this is done by just taking the first command line argument to our host as the path to a managed binary whose `main` method will be executed.</span></span>

[!code-cpp[NetCoreHost#1](../../../samples/core/hosting/host.cpp#1)]

### <a name="step-2---find-and-load-coreclrdll"></a><span data-ttu-id="f8f27-131">Krok 2 — Znajdź i obciążenia CoreCLR.dll</span><span class="sxs-lookup"><span data-stu-id="f8f27-131">Step 2 - Find and load CoreCLR.dll</span></span>
<span data-ttu-id="f8f27-132">Środowisko uruchomieniowe .NET Core API znajdują się w *CoreCLR.dll* (w systemie Windows).</span><span class="sxs-lookup"><span data-stu-id="f8f27-132">The .NET Core runtime APIs are in *CoreCLR.dll* (on Windows).</span></span> <span data-ttu-id="f8f27-133">Uzyskać naszych hostingu interfejsu (`ICLRRuntimeHost2`), należy odnaleźć i załadować *CoreCLR.dll*.</span><span class="sxs-lookup"><span data-stu-id="f8f27-133">To get our hosting interface (`ICLRRuntimeHost2`), it's necessary to find and load *CoreCLR.dll*.</span></span> <span data-ttu-id="f8f27-134">Do hosta, aby zdefiniować sposób zlokalizuje Konwencja *CoreCLR.dll*.</span><span class="sxs-lookup"><span data-stu-id="f8f27-134">It is up to the host to define a convention for how it will locate *CoreCLR.dll*.</span></span> <span data-ttu-id="f8f27-135">Niektóre hosty oczekiwać, że plik, który będzie znajdować się w dobrze znanej lokalizacji komputera (na przykład % programfiles%\dotnet\shared\Microsoft.NETCore.App\1.1.0).</span><span class="sxs-lookup"><span data-stu-id="f8f27-135">Some hosts expect the file to be present in a well-known machine-wide location (such as %programfiles%\dotnet\shared\Microsoft.NETCore.App\1.1.0).</span></span> <span data-ttu-id="f8f27-136">Inne oczekuje, że *CoreCLR.dll* zostanie pobrany z lokalizacji obok wybranego hosta siebie lub aplikacji ma być obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="f8f27-136">Others expect that *CoreCLR.dll* will be loaded from a location next to either the host itself or the app to be hosted.</span></span> <span data-ttu-id="f8f27-137">Inne nadal może można znaleźć zmiennej środowiskowej można znaleźć biblioteki.</span><span class="sxs-lookup"><span data-stu-id="f8f27-137">Still others might consult an environment variable to find the library.</span></span>

<span data-ttu-id="f8f27-138">W systemie Linux lub Mac jest podstawowa Biblioteka środowiska uruchomieniowego *libcoreclr.so* lub *libcoreclr.dylib*odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="f8f27-138">On Linux or Mac, the core runtime library is *libcoreclr.so* or *libcoreclr.dylib*, respectively.</span></span>

<span data-ttu-id="f8f27-139">Nasze przykładowe hosta sondy kilka wspólnej lokalizacji dla *CoreCLR.dll*.</span><span class="sxs-lookup"><span data-stu-id="f8f27-139">Our sample host probes a few common locations for *CoreCLR.dll*.</span></span> <span data-ttu-id="f8f27-140">Znaleziono jeden raz, zostać załadowany za pośrednictwem `LoadLibrary` (lub `dlopen` na Linux/Mac).</span><span class="sxs-lookup"><span data-stu-id="f8f27-140">Once found, it must be loaded via `LoadLibrary` (or `dlopen` on Linux/Mac).</span></span>

[!code-cpp[NetCoreHost#2](../../../samples/core/hosting/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost2-instance"></a><span data-ttu-id="f8f27-141">Krok 3 — Pobierz wystąpienia ICLRRuntimeHost2</span><span class="sxs-lookup"><span data-stu-id="f8f27-141">Step 3 - Get an ICLRRuntimeHost2 Instance</span></span>
<span data-ttu-id="f8f27-142">`ICLRRuntimeHost2` Interfejs hosta jest pobierana przez wywołanie metody `GetProcAddress` (lub `dlsym` na systemie Linux/Mac) na `GetCLRRuntimeHost`, a następnie wywoływania tej funkcji.</span><span class="sxs-lookup"><span data-stu-id="f8f27-142">The `ICLRRuntimeHost2` hosting interface is retrieved by calling `GetProcAddress` (or `dlsym` on Linux/Mac) on `GetCLRRuntimeHost`, and then invoking that function.</span></span> 

[!code-cpp[NetCoreHost#3](../../../samples/core/hosting/host.cpp#3)]

### <a name="step-4---setting-startup-flags-and-starting-the-runtime"></a><span data-ttu-id="f8f27-143">Krok 4 — ustawienie flagi uruchamiania i uruchamianie środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="f8f27-143">Step 4 - Setting startup flags and starting the runtime</span></span>
<span data-ttu-id="f8f27-144">Z `ICLRRuntimeHost2` dostępnych, możemy teraz określić flagi uruchamiania całego środowiska uruchomieniowego i uruchomić środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f8f27-144">With an `ICLRRuntimeHost2` in-hand, we can now specify runtime-wide startup flags and start the runtime.</span></span> <span data-ttu-id="f8f27-145">Flagi uruchamiania określi, które moduł zbierający elementy bezużyteczne (GC) Aby użyć (równoczesnych lub serwera), czy używamy AppDomain jednego lub wielu obiektów AppDomain i jakie zasady optymalizacji modułu ładującego (dla neutralne dla domen ładowania zestawów).</span><span class="sxs-lookup"><span data-stu-id="f8f27-145">Startup flags will determine which garbage collector (GC) to use (concurrent or server), whether we will use a single AppDomain or multiple AppDomains, and what loader optimization policy to use (for domain-neutral loading of assemblies).</span></span>

[!code-cpp[NetCoreHost#4](../../../samples/core/hosting/host.cpp#4)]

<span data-ttu-id="f8f27-146">Środowisko uruchomieniowe zostanie uruchomiony przy użyciu wywołania `Start` funkcji.</span><span class="sxs-lookup"><span data-stu-id="f8f27-146">The runtime is started with a call to the `Start` function.</span></span>

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a><span data-ttu-id="f8f27-147">Krok 5 — ustawienia przygotowanie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="f8f27-147">Step 5 - Preparing AppDomain settings</span></span>
<span data-ttu-id="f8f27-148">Po uruchomieniu środowiska uruchomieniowego, chcemy do konfigurowania elementu AppDomain.</span><span class="sxs-lookup"><span data-stu-id="f8f27-148">Once the runtime is started, we will want to set up an AppDomain.</span></span> <span data-ttu-id="f8f27-149">Istnieje wiele opcji, które należy określić podczas tworzenia AppDomain .NET, więc przygotowanie tych pierwszej.</span><span class="sxs-lookup"><span data-stu-id="f8f27-149">There are a number of options that must be specified when creating a .NET AppDomain, however, so it's necessary to prepare those first.</span></span>

<span data-ttu-id="f8f27-150">Flagi AppDomain określić zachowania elementu AppDomain związanych z bezpieczeństwem i interop.</span><span class="sxs-lookup"><span data-stu-id="f8f27-150">AppDomain flags specify AppDomain behaviors related to security and interop.</span></span> <span data-ttu-id="f8f27-151">Starsze hostów Silverlight używane te ustawienia do kodu użytkownika piaskownicy, ale większość nowoczesnych hosty .NET Core uruchamiane przy pełnym zaufaniu kod użytkownika i włączyć interop.</span><span class="sxs-lookup"><span data-stu-id="f8f27-151">Older Silverlight hosts used these settings to sandbox user code, but most modern .NET Core hosts run user code as full trust and enable interop.</span></span>

[!code-cpp[NetCoreHost#5](../../../samples/core/hosting/host.cpp#5)]

<span data-ttu-id="f8f27-152">Po podjęciu decyzji, które AppDomain flagi do użycia, właściwości elementu AppDomain muszą być zdefiniowane.</span><span class="sxs-lookup"><span data-stu-id="f8f27-152">After deciding which AppDomain flags to use, AppDomain properties must be defined.</span></span> <span data-ttu-id="f8f27-153">Właściwości są pary klucz wartość ciągów.</span><span class="sxs-lookup"><span data-stu-id="f8f27-153">The properties are key/value pairs of strings.</span></span> <span data-ttu-id="f8f27-154">Wiele właściwości odnoszą się do elementu AppDomain zostanie jak ładowanie zestawów.</span><span class="sxs-lookup"><span data-stu-id="f8f27-154">Many of the properties relate to how the AppDomain will load assemblies.</span></span>

<span data-ttu-id="f8f27-155">Wspólne właściwości domeny aplikacji obejmują:</span><span class="sxs-lookup"><span data-stu-id="f8f27-155">Common AppDomain properties include:</span></span>

* <span data-ttu-id="f8f27-156">`TRUSTED_PLATFORM_ASSEMBLIES`Jest to lista ścieżek zestawu (rozdzielonych przez ';' w systemie Windows i ":" w systemie Unix) który elementu AppDomain powinien ustalić ich priorytety ładowania i zapewnia pełne zaufanie (nawet w częściowo zaufane domeny).</span><span class="sxs-lookup"><span data-stu-id="f8f27-156">`TRUSTED_PLATFORM_ASSEMBLIES` This is a list of assembly paths (delimited by ';' on Windows and ':' on Unix) which the AppDomain should prioritize loading and give full trust to (even in partially-trusted domains).</span></span> <span data-ttu-id="f8f27-157">Ta lista jest przeznaczona do zawierają zestawy 'Struktury' i innych zaufanych modułów, podobny do pamięci podręcznej GAC w scenariuszach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="f8f27-157">This list is meant to contain 'Framework' assemblies and other trusted modules, similar to the GAC in .NET Framework scenarios.</span></span> <span data-ttu-id="f8f27-158">Niektóre hosty wprowadzi żadnej biblioteki obok *coreclr.dll* na tej liście ustalony manifestów listę zaufanych zestawów ich w celach innych osób.</span><span class="sxs-lookup"><span data-stu-id="f8f27-158">Some hosts will put any library next to *coreclr.dll* on this list, others have hard-coded manifests listing trusted assemblies for their purposes.</span></span>
* <span data-ttu-id="f8f27-159">`APP_PATHS`Jest to lista ścieżek do sondowania w dla zestawu, jeśli nie można znaleźć na liście zestawów (TPA) TPM.</span><span class="sxs-lookup"><span data-stu-id="f8f27-159">`APP_PATHS` This is a list of paths to probe in for an assembly if it can't be found in the trusted platform assemblies (TPA) list.</span></span> <span data-ttu-id="f8f27-160">Te ścieżki mają być lokalizacji, gdzie można znaleźć zestawów użytkowników.</span><span class="sxs-lookup"><span data-stu-id="f8f27-160">These paths are meant to be the locations where users' assemblies can be found.</span></span> <span data-ttu-id="f8f27-161">W trybie piaskownicy AppDomain zestawów załadowanych z tych ścieżek będzie można udzielać tylko częściowej relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="f8f27-161">In a sandboxed AppDomain, assemblies loaded from these paths will only be granted partial trust.</span></span> <span data-ttu-id="f8f27-162">Wspólne ścieżki APP_PATH obejmują ścieżka aplikacji docelowej został załadowany z ani innych lokalizacji, w którym zasoby użytkownika wiadomo, że na żywo.</span><span class="sxs-lookup"><span data-stu-id="f8f27-162">Common APP_PATH paths include the path the target app was loaded from or other locations where user assets are known to live.</span></span>
*  <span data-ttu-id="f8f27-163">`APP_NI_PATHS`Ta lista jest bardzo podobny do APP_PATHS z tą różnicą, że ma ma być ścieżek, które będzie sondowany dla obrazów natywnych.</span><span class="sxs-lookup"><span data-stu-id="f8f27-163">`APP_NI_PATHS` This list is very similar to APP_PATHS except that it's meant to be paths that will be probed for native images.</span></span>
*  <span data-ttu-id="f8f27-164">`NATIVE_DLL_SEARCH_DIRECTORIES`Ta właściwość jest lista ścieżek, które moduł ładujący powinien sondowania wywołanego wyszukiwanie natywnych bibliotek DLL za pośrednictwem p/invoke.</span><span class="sxs-lookup"><span data-stu-id="f8f27-164">`NATIVE_DLL_SEARCH_DIRECTORIES` This property is a list of paths the loader should probe when looking for native DLLs called via p/invoke.</span></span>
*  <span data-ttu-id="f8f27-165">`PLATFORM_RESOURCE_ROOTS`Ta lista zawiera ścieżki do sondowania w zestawów satelickich zasobów (w podfolderach specyficzne dla kultury).</span><span class="sxs-lookup"><span data-stu-id="f8f27-165">`PLATFORM_RESOURCE_ROOTS` This list includes paths to probe in for resource satellite assemblies (in culture-specific sub-directories).</span></span>
*  <span data-ttu-id="f8f27-166">`AppDomainCompatSwitch`Ten ciąg Określa, które Osobliwości zgodności ma być używany dla zestawów bez jawnego Moniker platformy docelowej (atrybut poziomu zestawu wskazującą Framework, które zestawu jest przeznaczona do uruchomienia).</span><span class="sxs-lookup"><span data-stu-id="f8f27-166">`AppDomainCompatSwitch` This string specifies which compatibility quirks should be used for assemblies without an explicit Target Framework Moniker (an assembly-level attribute indicating which Framework an assembly is meant to run against).</span></span> <span data-ttu-id="f8f27-167">Zazwyczaj powinien to być ustawiony na `"UseLatestBehaviorWhenTFMNotSpecified"` , ale niektóre hosty mogą wolą starsze Silverlight lub Windows Phone zgodności Osobliwości, zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="f8f27-167">Typically, this should be set to `"UseLatestBehaviorWhenTFMNotSpecified"` but some hosts may prefer to get older Silverlight or Windows Phone compatibility quirks, instead.</span></span>

<span data-ttu-id="f8f27-168">W naszym [hosta prosty przykład](https://github.com/dotnet/docs/tree/master/samples/core/hosting), te właściwości są skonfigurowane w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="f8f27-168">In our [simple sample host](https://github.com/dotnet/docs/tree/master/samples/core/hosting), these properties are set up as follows:</span></span>

[!code-cpp[NetCoreHost#6](../../../samples/core/hosting/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a><span data-ttu-id="f8f27-169">Krok 6 — utworzenie domeny aplikacji</span><span class="sxs-lookup"><span data-stu-id="f8f27-169">Step 6 - Create the AppDomain</span></span>
<span data-ttu-id="f8f27-170">Gdy wszystkie flagi AppDomain i właściwości są przygotowywane `ICLRRuntimeHost2::CreateAppDomainWithManager` może służyć do konfigurowania elementu AppDomain.</span><span class="sxs-lookup"><span data-stu-id="f8f27-170">Once all AppDomain flags and properties are prepared, `ICLRRuntimeHost2::CreateAppDomainWithManager` can be used to set up the AppDomain.</span></span> <span data-ttu-id="f8f27-171">Ta funkcja przyjmuje opcjonalnie pełni kwalifikowanej nazwy zestawu i nazwa typu do użycia jako Menedżer AppDomain domeny.</span><span class="sxs-lookup"><span data-stu-id="f8f27-171">This function optionally takes a fully qualified assembly name and type name to use as the domain's AppDomain manager.</span></span> <span data-ttu-id="f8f27-172">Menedżer AppDomain można zezwolić na hosta kontrolować niektóre aspekty zachowanie domeny aplikacji i może udostępniać punktów wejścia do uruchamiania kodu zarządzanego, jeśli host nie ma zostać bezpośrednio wywoływać kod użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f8f27-172">An AppDomain manager can allow a host to control some aspects of AppDomain behavior and may provide entry points for launching managed code if the host doesn't intend to invoke user code directly.</span></span>   

[!code-cpp[NetCoreHost#7](../../../samples/core/hosting/host.cpp#7)]

### <a name="step-7---run-managed-code"></a><span data-ttu-id="f8f27-173">Krok 7 — Uruchom kod zarządzany!</span><span class="sxs-lookup"><span data-stu-id="f8f27-173">Step 7 - Run managed code!</span></span>
<span data-ttu-id="f8f27-174">Z elementu AppDomain skonfigurowaniu i uruchomieniu hosta można teraz rozpocząć wykonywania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="f8f27-174">With an AppDomain up and running, the host can now start executing managed code.</span></span> <span data-ttu-id="f8f27-175">Najprostszym sposobem, w tym celu jest użycie `ICLRRuntimeHost2::ExecuteAssembly` do wywołania metody punktu wejścia zarządzanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f8f27-175">The easiest way to do this is to use `ICLRRuntimeHost2::ExecuteAssembly` to invoke a managed assembly's entry point method.</span></span> <span data-ttu-id="f8f27-176">Należy pamiętać, że ta funkcja działa tylko w jednej domenie scenariuszach.</span><span class="sxs-lookup"><span data-stu-id="f8f27-176">Note that this function only works in single-domain scenarios.</span></span>

[!code-cpp[NetCoreHost#8](../../../samples/core/hosting/host.cpp#8)]

<span data-ttu-id="f8f27-177">Inną opcję, jeśli `ExecuteAssembly` nie odpowiada potrzebom na hoście, jest użycie `CreateDelegate` Aby utworzyć wskaźnik funkcji do statycznego zarządzane metody.</span><span class="sxs-lookup"><span data-stu-id="f8f27-177">Another option, if `ExecuteAssembly` doesn't meet your host's needs, is to use `CreateDelegate` to create a function pointer to a static managed method.</span></span> <span data-ttu-id="f8f27-178">Wymaga to hosta wiedzieć podpis metody jest wywoływanie (Aby utworzyć typ wskaźnika funkcji), ale pozwala hostom elastyczność do wywołania kodu innego niż wpisu zestawu punktu.</span><span class="sxs-lookup"><span data-stu-id="f8f27-178">This requires the host to know the signature of the method it is calling into (in order to create the function pointer type) but allows hosts the flexibility to invoke code other than an assembly's entry point.</span></span>

```C++
void *pfnDelegate = NULL;
hr = runtimeHost->CreateDelegate(
  domainId,
  L"HW, Version=1.0.0.0, Culture=neutral",  // Target managed assembly
  L"ConsoleApplication.Program",            // Target managed type
  L"Main",                                  // Target entry point (static method)
  (INT_PTR*)&pfnDelegate);

((MainMethodFp*)pfnDelegate)(NULL);
```

### <a name="step-8---clean-up"></a><span data-ttu-id="f8f27-179">Krok 8 - Oczyszczanie</span><span class="sxs-lookup"><span data-stu-id="f8f27-179">Step 8 - Clean up</span></span>
<span data-ttu-id="f8f27-180">Na koniec hosta powinien oczyszczanie po sam zwalnianie domen aplikacji, zatrzymując środowiska uruchomieniowego i zwalniania `ICLRRuntimeHost2` odwołania.</span><span class="sxs-lookup"><span data-stu-id="f8f27-180">Finally, the host should clean up after itself by unloading AppDomains, stopping the runtime, and releasing the `ICLRRuntimeHost2` reference.</span></span>

[!code-cpp[NetCoreHost#9](../../../samples/core/hosting/host.cpp#9)]

## <a name="about-hosting-net-core-on-unix"></a><span data-ttu-id="f8f27-181">O hostingu .NET Core w systemie Unix</span><span class="sxs-lookup"><span data-stu-id="f8f27-181">About Hosting .NET Core on Unix</span></span>
<span data-ttu-id="f8f27-182">Oprogramowanie .NET core to produkt i platform, działających w systemach operacyjnych Windows, Linux lub Mac.</span><span class="sxs-lookup"><span data-stu-id="f8f27-182">.NET Core is a cross-platform product, running on Windows, Linux, and Mac operating systems.</span></span> <span data-ttu-id="f8f27-183">Jednak jako natywnych aplikacji hosty dla różnych platform ma pewne różnice między nimi.</span><span class="sxs-lookup"><span data-stu-id="f8f27-183">As native applications, though, hosts for different platforms will have some differences between them.</span></span> <span data-ttu-id="f8f27-184">Proces opisany powyżej użycia `ICLRRuntimeHost2` do uruchamiania środowiska uruchomieniowego, utworzyć elementu AppDomain i wykonać kod zarządzany, powinny działać na dowolnym obsługiwanym systemie operacyjnym.</span><span class="sxs-lookup"><span data-stu-id="f8f27-184">The process described above of using `ICLRRuntimeHost2` to start the runtime, create an AppDomain, and execute managed code, should work on any supported operating system.</span></span> <span data-ttu-id="f8f27-185">Jednak interfejsów zdefiniowanych w mscoree.h może być skomplikowane do pracy z na platformach systemu Unix, ponieważ biblioteka mscoree sprawia, że wiele założenia Win32.</span><span class="sxs-lookup"><span data-stu-id="f8f27-185">However, the interfaces defined in mscoree.h can be cumbersome to work with on Unix platforms since mscoree makes many Win32 assumptions.</span></span>

<span data-ttu-id="f8f27-186">Aby hostingu na platformach systemu Unix jest łatwiejsze, zbiór więcej otoki niezależny od platformy obsługi interfejsu API są dostępne w [coreclrhost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h).</span><span class="sxs-lookup"><span data-stu-id="f8f27-186">To make hosting on Unix platforms easier, a set of more platform-neutral hosting API wrappers are available in [coreclrhost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h).</span></span>

<span data-ttu-id="f8f27-187">Przykład użycia coreclrhost.h (zamiast bezpośrednio mscoree.h) są widoczne w [hosta UnixCoreRun](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts).</span><span class="sxs-lookup"><span data-stu-id="f8f27-187">An example of using coreclrhost.h (instead of mscoree.h directly) can be seen in the [UnixCoreRun host](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts).</span></span> <span data-ttu-id="f8f27-188">Kroki umożliwiające korzystanie z interfejsów API z coreclrhost.h do obsługi środowiska uruchomieniowego są podobne do czynności, korzystając z mscoree.h:</span><span class="sxs-lookup"><span data-stu-id="f8f27-188">The steps to use the APIs from coreclrhost.h to host the runtime are similar to the steps when using mscoree.h:</span></span>

1. <span data-ttu-id="f8f27-189">Określenie kodu zarządzanego do wykonania (polecenia wiersz parametrów, na przykład).</span><span class="sxs-lookup"><span data-stu-id="f8f27-189">Identify the managed code to execute (from command line parameters, for example).</span></span> 
2. <span data-ttu-id="f8f27-190">Ładowanie biblioteki środowisko CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="f8f27-190">Load the CoreCLR library.</span></span>
    1. `dlopen("./libcoreclr.so", RTLD_NOW | RTLD_LOCAL);` 
3. <span data-ttu-id="f8f27-191">Pobierz wskaźników funkcji do przez środowisko CoreCLR `coreclr_initialize`, `coreclr_create_delegate`, `coreclr_execute_assembly`, i `coreclr_shutdown` funkcji przy użyciu`dlsym`</span><span class="sxs-lookup"><span data-stu-id="f8f27-191">Get function pointers to CoreCLR's `coreclr_initialize`, `coreclr_create_delegate`, `coreclr_execute_assembly`, and `coreclr_shutdown` functions using `dlsym`</span></span>
    1. `coreclr_initialize_ptr coreclr_initialize = (coreclr_initialize_ptr)dlsym(coreclrLib, "coreclr_initialize");`
4. <span data-ttu-id="f8f27-192">Ustawianie właściwości domeny aplikacji (na przykład lista TPA).</span><span class="sxs-lookup"><span data-stu-id="f8f27-192">Set up AppDomain properties (such as the TPA list).</span></span> <span data-ttu-id="f8f27-193">To jest taka sama jak krok 5 z przepływu mscoree powyżej.</span><span class="sxs-lookup"><span data-stu-id="f8f27-193">This is the same as step 5 from the mscoree workflow, above.</span></span>
5. <span data-ttu-id="f8f27-194">Użyj `coreclr_initialize` Aby uruchomić środowisko uruchomieniowe i utworzyć elementu AppDomain.</span><span class="sxs-lookup"><span data-stu-id="f8f27-194">Use `coreclr_initialize` to start the runtime and create an AppDomain.</span></span> <span data-ttu-id="f8f27-195">Spowoduje to również utworzenie `hostHandle` wskaźnika, który będzie używany w przyszłości hosting wywołania.</span><span class="sxs-lookup"><span data-stu-id="f8f27-195">This will also create a `hostHandle` pointer that will be used in future hosting calls.</span></span>
    1. <span data-ttu-id="f8f27-196">Należy pamiętać, że ta funkcja wykonuje role oba kroki 4 i 6 z poprzednich przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f8f27-196">Note that this function performs the roles of both steps 4 and 6 from the previous workflow.</span></span> 
6. <span data-ttu-id="f8f27-197">Użyj jednej `coreclr_execute_assembly` lub `coreclr_create_delegate` do wykonania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="f8f27-197">Use either `coreclr_execute_assembly` or `coreclr_create_delegate` to execute managed code.</span></span> <span data-ttu-id="f8f27-198">Te funkcje są odpowiednikiem w bibliotece mscoree `ExecuteAssembly` i `CreateDelegate` funkcji z kroku 7 poprzedniej przepływu pracy.</span><span class="sxs-lookup"><span data-stu-id="f8f27-198">These functions are analogous to mscoree's `ExecuteAssembly` and `CreateDelegate` functions from step 7 of the previous workflow.</span></span>
7. <span data-ttu-id="f8f27-199">Użyj `coreclr_shutdown` aby zwolnić elementu AppDomain i zamknąć środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="f8f27-199">Use `coreclr_shutdown` to unload the AppDomain and shut down the runtime.</span></span> 

## <a name="conclusion"></a><span data-ttu-id="f8f27-200">Wniosek</span><span class="sxs-lookup"><span data-stu-id="f8f27-200">Conclusion</span></span>
<span data-ttu-id="f8f27-201">Po utworzeniu hosta może być testowana uruchamiając go z poziomu wiersza polecenia, a następnie przekazywanie argumentów (na przykład zarządzaną aplikację do uruchamiania) oczekuje hosta.</span><span class="sxs-lookup"><span data-stu-id="f8f27-201">Once your host is built, it can be tested by running it from the command line and passing any arguments (like the managed app to run) the host expects.</span></span> <span data-ttu-id="f8f27-202">Podczas określania aplikacji .NET Core dla hosta do uruchomienia, należy użyć pliku .dll, który jest generowany przez `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="f8f27-202">When specifying the .NET Core app for the host to run, be sure to use the .dll that is produced by `dotnet build`.</span></span> <span data-ttu-id="f8f27-203">Pliki wykonywalne utworzonego przez `dotnet publish` niezależne aplikacje są faktycznie domyślne .NET Core hosta (tak, aby aplikację można uruchomić bezpośrednio z poziomu wiersza polecenia w połączeniach scenariuszach); kod użytkownika jest kompilowany do biblioteki dll o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="f8f27-203">Executables produced by `dotnet publish` for self-contained applications are actually the default .NET Core host (so that the app can be launched directly from the command line in mainline scenarios); user code is compiled into a dll of the same name.</span></span> 

<span data-ttu-id="f8f27-204">Jeśli początkowo działają rzeczy, dokładnie sprawdzić, które *coreclr.dll* jest dostępny w lokalizacji oczekiwany przez hosta, wszystkie wymagane biblioteki Framework znajdują się na liście TPA, która odpowiada tym środowisko CoreCLR bitowości (32 - lub 64-bitowy) jak Host został skompilowany.</span><span class="sxs-lookup"><span data-stu-id="f8f27-204">If things don't work initially, double-check that *coreclr.dll* is available in the location expected by the host, that all necessary Framework libraries are in the TPA list, and that CoreCLR's bitness (32- or 64-bit) matches how the host was built.</span></span>

<span data-ttu-id="f8f27-205">Hostowanie środowiska uruchomieniowego .NET Core jest zaawansowanym scenariuszu nie wymagają wielu deweloperów, że dla tych, którzy muszą uruchomić kodu zarządzanego z natywnego procesu lub którzy muszą mieć większą kontrolę nad zachowanie środowiska uruchomieniowego .NET Core, może być bardzo przydatne.</span><span class="sxs-lookup"><span data-stu-id="f8f27-205">Hosting the .NET Core runtime is an advanced scenario that many developers won't require, but for those who need to launch managed code from a native process, or who need more control over the .NET Core runtime's behavior, it can be very useful.</span></span> <span data-ttu-id="f8f27-206">Ponieważ .NET Core jest w stanie uruchomić side-by-side ze sobą, jest nawet możliwe utworzenie hosta, na którym zainicjować i rozpocząć wielu wersji środowiska uruchomieniowego .NET Core i wykonaj aplikacje na wszystkich z nich w tym samym procesie.</span><span class="sxs-lookup"><span data-stu-id="f8f27-206">Because .NET Core is able to run side-by-side with itself, it's even possible to create hosts which initialize and start multiple versions of the .NET Core runtime and execute apps on all of them in the same process.</span></span> 