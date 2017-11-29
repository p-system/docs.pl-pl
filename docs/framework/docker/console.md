---
title: Uruchamianie aplikacji konsoli w Docker
description: "Dowiedz się, jak wykonać istniejącej aplikacji konsoli .NET Framework i uruchom go w kontenerze Docker systemu Windows."
author: spboyer
keywords: Aplikacje kontenera, konsoli .NET
ms.date: 09/28/2016
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.openlocfilehash: 2fdce1e131eaa0d6952b2910f73105f097487711
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="running-console-applications-in-windows-containers"></a><span data-ttu-id="a12c2-104">Uruchamianie aplikacji konsoli w kontenerach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a12c2-104">Running console applications in Windows containers</span></span>

<span data-ttu-id="a12c2-105">Aplikacje konsoli są używane dla wielu celów; proste wysyłanie kwerend stanu długotrwałej obraz dokumentu przetwarzania zadań.</span><span class="sxs-lookup"><span data-stu-id="a12c2-105">Console applications are used for many purposes; from simple querying of a status to long running document image processing tasks.</span></span> <span data-ttu-id="a12c2-106">W każdym przypadku spełnia możliwość uruchamiania i skalowania tych aplikacji z ograniczeniami nabycia sprzętu, czasu uruchamiania lub uruchamianie wielu wystąpień.</span><span class="sxs-lookup"><span data-stu-id="a12c2-106">In any case, the ability to start up and scale these applications are met with limitations of hardware acquisitions, startup times or running multiple instances.</span></span>

<span data-ttu-id="a12c2-107">Kontenery przenoszenie aplikacji konsoli do użycia Docker i Windows Server umożliwia uruchamiania tych aplikacji od stanu czystego, umożliwiając im wykonywanie operacji, a następnie zamknięcie prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="a12c2-107">Moving your console applications to use Docker and Windows Server containers allows for starting these applications from a clean state, enabling them to perform the operation and then shutdown cleanly.</span></span> <span data-ttu-id="a12c2-108">W tym temacie opisano kroki niezbędne do przeniesienia aplikacji konsoli do systemu Windows na podstawie kontenera i uruchomić go za pomocą skryptu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a12c2-108">This topic will show the steps needed to move a console application to a Windows based container and start it using a PowerShell script.</span></span>

<span data-ttu-id="a12c2-109">Przykładowa aplikacja konsolowa jest prosty przykład, w tym przypadku przyjmuje argument pytanie i zwraca losowe odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="a12c2-109">The sample console application is a simple example which takes an argument, a question in this case, and returns a random answer.</span></span> <span data-ttu-id="a12c2-110">Może to potrwać `customer_id` przetworzyć ich podatki i tworzenie miniatur dla `image_url` argumentu.</span><span class="sxs-lookup"><span data-stu-id="a12c2-110">This could take a `customer_id` and process their taxes, or create a thumbnail for an `image_url` argument.</span></span>

<span data-ttu-id="a12c2-111">Oprócz odpowiedzi `Environment.MachineName` został dodany do odpowiedzi wskazują różnice między uruchomieniem aplikacji lokalnie i w kontenerze systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="a12c2-111">In addition to the answer, the `Environment.MachineName` has been added to the response to show the difference between running the application locally and in a Windows container.</span></span> <span data-ttu-id="a12c2-112">Podczas uruchamiania aplikacji lokalnie, nazwę komputera lokalnego ma zostać zwrócony, a podczas uruchamiania w kontenerze systemu Windows; Identyfikator sesji kontenera jest zwracana.</span><span class="sxs-lookup"><span data-stu-id="a12c2-112">When running the application locally, your local machine name should be returned and when running in a Windows Container; the container session id is returned.</span></span>

<span data-ttu-id="a12c2-113">[Pełny przykład](https://github.com/dotnet/docs/tree/master/samples/framework/docker/ConsoleRandomAnswerGenerator) jest dostępny w repozytorium dotnet/docs w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="a12c2-113">The [complete example](https://github.com/dotnet/docs/tree/master/samples/framework/docker/ConsoleRandomAnswerGenerator) is available in the dotnet/docs repository on GitHub.</span></span> <span data-ttu-id="a12c2-114">Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="a12c2-114">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="a12c2-115">Należy zapoznać się z niektórych Docker warunki przed rozpoczęciem pracy na przenoszenie aplikacji do kontenera.</span><span class="sxs-lookup"><span data-stu-id="a12c2-115">You need to be familiar with some Docker terms before you begin working on moving your application to a container.</span></span>

> <span data-ttu-id="a12c2-116">A *Docker obrazu* jest tylko do odczytu szablonu, który definiuje środowisko uruchomionych kontenera, w tym system operacyjny (OS), składniki systemu i aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a12c2-116">A *Docker image* is a read-only template that defines the environment for a running container, including the operating system (OS), system components, and application(s).</span></span>

<span data-ttu-id="a12c2-117">Ważna cechą obrazy usługi Docker jest, że obrazy składają się z obrazu podstawowego.</span><span class="sxs-lookup"><span data-stu-id="a12c2-117">One important feature of Docker images is that images are composed from a base image.</span></span> <span data-ttu-id="a12c2-118">Każdy nowy obraz dodaje niewielki zestaw funkcji do istniejącego obrazu.</span><span class="sxs-lookup"><span data-stu-id="a12c2-118">Each new image adds a small set of features to an existing image.</span></span> 

> <span data-ttu-id="a12c2-119">A *kontenera Docker* jest uruchomione wystąpienie obrazu.</span><span class="sxs-lookup"><span data-stu-id="a12c2-119">A *Docker container* is a running instance of an image.</span></span> 

<span data-ttu-id="a12c2-120">Skalowanie aplikacji przez uruchomienie tego samego obrazu w wielu kontenerów.</span><span class="sxs-lookup"><span data-stu-id="a12c2-120">You scale an application by running the same image in many containers.</span></span>
<span data-ttu-id="a12c2-121">Koncepcyjnie jest podobny do uruchamiania tej samej aplikacji w wielu hostach.</span><span class="sxs-lookup"><span data-stu-id="a12c2-121">Conceptually, this is similar to running the same application in multiple hosts.</span></span>

<span data-ttu-id="a12c2-122">Więcej o architekturze Docker można uzyskać, odczytując [omówienie Docker](https://docs.docker.com/engine/understanding-docker/) w witrynie Docker.</span><span class="sxs-lookup"><span data-stu-id="a12c2-122">You can learn more about the Docker architecture by reading the [Docker Overview](https://docs.docker.com/engine/understanding-docker/) on the Docker site.</span></span> 

<span data-ttu-id="a12c2-123">Przenoszenie aplikacji konsoli jest wykonanie kilku kroków.</span><span class="sxs-lookup"><span data-stu-id="a12c2-123">Moving your console application is a matter of a few steps.</span></span>

1. [<span data-ttu-id="a12c2-124">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="a12c2-124">Build the application</span></span>](#building-the-application)
1. [<span data-ttu-id="a12c2-125">Tworzenie plik Dockerfile obrazu</span><span class="sxs-lookup"><span data-stu-id="a12c2-125">Creating a Dockerfile for the image</span></span>](#creating-the-dockerfile)
1. [<span data-ttu-id="a12c2-126">Proces, aby skompilować i uruchomić kontenera Docker</span><span class="sxs-lookup"><span data-stu-id="a12c2-126">Process to build and run the Docker container</span></span>](#creating-the-image)

## <a name="prerequisites"></a><span data-ttu-id="a12c2-127">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="a12c2-127">Prerequisites</span></span>
<span data-ttu-id="a12c2-128">Kontenery systemu Windows są obsługiwane w [systemu Windows 10 Anniversary aktualizacji](https://www.microsoft.com/en-us/software-download/windows10/) lub [systemu Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).</span><span class="sxs-lookup"><span data-stu-id="a12c2-128">Windows containers are supported on [Windows 10 Anniversary Update](https://www.microsoft.com/en-us/software-download/windows10/) or [Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).</span></span>

> [!NOTE]
><span data-ttu-id="a12c2-129">Jeśli używasz systemu Windows Server 2016, należy włączyć kontenery ręcznie ponieważ Instalator Docker dla systemu Windows nie włączy tę funkcję.</span><span class="sxs-lookup"><span data-stu-id="a12c2-129">If you are using Windows Server 2016, you must enable containers manually since the Docker for Windows installer will not enable the feature.</span></span> <span data-ttu-id="a12c2-130">Upewnij się, że wszystkie aktualizacje uruchomiono dla systemu operacyjnego, a następnie postępuj zgodnie z instrukcjami [wdrażania hosta kontenera](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment) artykuł, aby zainstalować kontenery i funkcje Docker.</span><span class="sxs-lookup"><span data-stu-id="a12c2-130">Make sure all updates have run for the OS and then follow the instructions from the [Container Host Deployment](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment) article to install the containers and Docker features.</span></span>

<span data-ttu-id="a12c2-131">Musisz mieć Docker dla systemu Windows, wersja 1.12 26 lub nowszej wersji Beta do obsługi systemu Windows kontenerów.</span><span class="sxs-lookup"><span data-stu-id="a12c2-131">You need to have Docker for Windows, version 1.12 Beta 26 or higher to support Windows containers.</span></span> <span data-ttu-id="a12c2-132">Domyślnie Docker umożliwia kontenery opartymi na systemie Linux; Przełącz się do kontenerów systemu Windows przez kliknięcie prawym przyciskiem myszy ikonę Docker na pasku zadań i wybierz **przełączyć się do systemu Windows kontenery**.</span><span class="sxs-lookup"><span data-stu-id="a12c2-132">By default, Docker enables Linux based containers; switch to Windows containers by right clicking the Docker icon in the system tray and select **Switch to Windows containers**.</span></span> <span data-ttu-id="a12c2-133">Docker uruchomi proces zmiany i może być wymagane ponowne uruchomienie.</span><span class="sxs-lookup"><span data-stu-id="a12c2-133">Docker will run the process to change and a restart may be required.</span></span>

![Kontenery systemu Windows](./media/console/SwitchContainer.png)

## <a name="building-the-application"></a><span data-ttu-id="a12c2-135">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="a12c2-135">Building the application</span></span>
<span data-ttu-id="a12c2-136">Zwykle aplikacje konsoli są dystrybuowane za pomocą Instalatora, FTP lub udziału plików wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="a12c2-136">Typically console applications are distributed through an installer, FTP, or File Share deployment.</span></span> <span data-ttu-id="a12c2-137">W przypadku wdrażania w danym kontenerze, zasoby muszą być skompilowane i przygotowane do lokalizacji, która może być używana podczas tworzenia obrazu Docker.</span><span class="sxs-lookup"><span data-stu-id="a12c2-137">When deploying to a container, the assets need to be compiled and staged to a location that can be used when the Docker image is created.</span></span>

<span data-ttu-id="a12c2-138">W *build.ps1*, skrypt używa [MSBuild](https://msdn.microsoft.com/library/dd393574.aspx) skompilować aplikację, aby ukończyć zadanie tworzenia zasoby.</span><span class="sxs-lookup"><span data-stu-id="a12c2-138">In *build.ps1*, the script uses [MSBuild](https://msdn.microsoft.com/library/dd393574.aspx) to compile the application to complete the task of building the assets.</span></span> <span data-ttu-id="a12c2-139">Istnieje kilka parametrów przekazanych do MSBuild, aby zakończyć wymagane zasoby.</span><span class="sxs-lookup"><span data-stu-id="a12c2-139">There are a few parameters passed to MSBuild to finalize the needed assets.</span></span> <span data-ttu-id="a12c2-140">Nazwa pliku projektu lub rozwiązania do skompilowania, lokalizacja dane wyjściowe, i na koniec konfiguracji (debugowania lub wersji).</span><span class="sxs-lookup"><span data-stu-id="a12c2-140">The name of the project file or solution to be compiled, the location for the output and finally the configuration (Release or Debug).</span></span>

<span data-ttu-id="a12c2-141">W wywołaniu `Invoke-MSBuild` `OutputPath` ustawiono **publikowania** i `Configuration` ustawioną **wersji**.</span><span class="sxs-lookup"><span data-stu-id="a12c2-141">In the call to `Invoke-MSBuild` the `OutputPath` is set to **publish** and  `Configuration` set to **Release**.</span></span> 

```
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj /p:OutputPath=.\publish /p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a><span data-ttu-id="a12c2-142">Tworzenie plik Dockerfile</span><span class="sxs-lookup"><span data-stu-id="a12c2-142">Creating the Dockerfile</span></span>
<span data-ttu-id="a12c2-143">Obraz podstawowy używany dla konsoli aplikacji .NET Framework jest `microsoft/windowsservercore`, ogólnie dostępna w [Centrum Docker](https://hub.docker.com/r/microsoft/windowsservercore/).</span><span class="sxs-lookup"><span data-stu-id="a12c2-143">The base image used for a console .NET Framework application is `microsoft/windowsservercore`, publicly available on [Docker Hub](https://hub.docker.com/r/microsoft/windowsservercore/).</span></span> <span data-ttu-id="a12c2-144">Obraz podstawowy zawiera minimalnej instalacji systemu Windows Server 2016, .NET Framework 4.6.2 i służy jako podstawowy obraz systemu operacyjnego Windows kontenerów.</span><span class="sxs-lookup"><span data-stu-id="a12c2-144">The base image contains a minimal installation of Windows Server 2016, .NET Framework 4.6.2 and serves as the base OS image for Windows Containers.</span></span>

```
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```
<span data-ttu-id="a12c2-145">W pierwszym wierszu plik Dockerfile wyznacza przy użyciu obrazu podstawowego [ `FROM` ](https://docs.docker.com/engine/reference/builder/#/from) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a12c2-145">The first line in the Dockerfile designates the base image using the [`FROM`](https://docs.docker.com/engine/reference/builder/#/from) instruction.</span></span> <span data-ttu-id="a12c2-146">Następnie [ `ADD` ](https://docs.docker.com/engine/reference/builder/#/add) w pliku kopiuje zasoby aplikacji z **publikowania** folderu do folderu głównego kontenera i ostatnich; ustawienie [ `ENTRYPOINT` ](https://docs.docker.com/engine/reference/builder/#/entrypoint) stanów obrazu jest tego polecenia lub aplikacji, które zostanie uruchomione po uruchomieniu kontenera.</span><span class="sxs-lookup"><span data-stu-id="a12c2-146">Next, [`ADD`](https://docs.docker.com/engine/reference/builder/#/add) in the file copies the application assets from the **publish** folder to root folder of the container and last; setting the [`ENTRYPOINT`](https://docs.docker.com/engine/reference/builder/#/entrypoint) of the image states that this is the command or application that will run when the container starts.</span></span> 

## <a name="creating-the-image"></a><span data-ttu-id="a12c2-147">Tworzenie obrazu</span><span class="sxs-lookup"><span data-stu-id="a12c2-147">Creating the image</span></span>
<span data-ttu-id="a12c2-148">Aby utworzyć obraz Docker, następujący kod został dodany do *build.ps1* skryptu.</span><span class="sxs-lookup"><span data-stu-id="a12c2-148">In order to create the Docker image, the following code is added to the *build.ps1* script.</span></span> <span data-ttu-id="a12c2-149">Po uruchomieniu skryptu `console-random-answer-generator` obraz został utworzony za pomocą zasoby skompilowana z MSBuild zdefiniowane w [tworzenie aplikacji](#building-the-application) sekcji.</span><span class="sxs-lookup"><span data-stu-id="a12c2-149">When the script is run, the `console-random-answer-generator` image is created using the assets compiled from MSBuild defined in the [Building the application](#building-the-application) section.</span></span>

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

<span data-ttu-id="a12c2-150">Uruchom przy użyciu skryptu `.\build.ps1` w wierszu polecenia programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a12c2-150">Run the script using `.\build.ps1` from the PowerShell command prompt.</span></span>

<span data-ttu-id="a12c2-151">Po zakończeniu kompilacji przy użyciu `docker images` polecenie z wiersza polecenia lub w wierszu polecenia programu PowerShell; zobaczysz, że obraz został utworzony i gotowych do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="a12c2-151">When the build is complete, using the `docker images` command from a command line or PowerShell prompt; you'll see that the image is created and ready to be run.</span></span>

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a><span data-ttu-id="a12c2-152">Uruchomione w kontenerze</span><span class="sxs-lookup"><span data-stu-id="a12c2-152">Running the container</span></span>
<span data-ttu-id="a12c2-153">Kontener można uruchomić z wiersza polecenia, używając polecenia Docker.</span><span class="sxs-lookup"><span data-stu-id="a12c2-153">You can start the container from the command line using the Docker commands.</span></span>

```
docker run console-random-answer-generator "Are you a square container?"
```

<span data-ttu-id="a12c2-154">Dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="a12c2-154">The output is</span></span>

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

<span data-ttu-id="a12c2-155">Po uruchomieniu `docker ps -a` poleceń w programie PowerShell, widać, że kontener nadal istnieje.</span><span class="sxs-lookup"><span data-stu-id="a12c2-155">If you run the `docker ps -a` command from PowerShell, you can see that the container still exists.</span></span>

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS                          
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago      
```

<span data-ttu-id="a12c2-156">W kolumnie Stan wynika, że na "około minutę temu", jest kompletna aplikacja i może zostać zamknięty.</span><span class="sxs-lookup"><span data-stu-id="a12c2-156">The STATUS column shows at "About a minute ago", the application was complete and could be shut down.</span></span> <span data-ttu-id="a12c2-157">Jeśli polecenie zostało uruchomione kilkaset razy, byłoby STU kontenery static po lewej stronie z bezczynne.</span><span class="sxs-lookup"><span data-stu-id="a12c2-157">If the command was run a hundred times, there would be a hundred containers left static with no work to do.</span></span> <span data-ttu-id="a12c2-158">W scenariuszu początku idealne operacja zakończyła się w pracy i zamknięcie lub czyszczenia.</span><span class="sxs-lookup"><span data-stu-id="a12c2-158">In the beginning scenario the ideal operation was to do the work and shutdown or cleanup.</span></span> <span data-ttu-id="a12c2-159">Aby osiągnąć ten przepływ pracy, dodawanie `--rm` opcji w celu `docker run` polecenia spowoduje usunięcie kontenera natychmiast `Exited` odebraniu sygnału.</span><span class="sxs-lookup"><span data-stu-id="a12c2-159">To accomplish that workflow, adding the `--rm` option to the `docker run` command will remove the container as soon as the `Exited` signal is received.</span></span>

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

<span data-ttu-id="a12c2-160">Uruchomienie polecenia przy użyciu tej opcji, a następnie sprawdzając w danych wyjściowych `docker ps -a` polecenie; Zwróć uwagę, że identyfikator kontenera ( `Environment.MachineName`) nie jest na liście.</span><span class="sxs-lookup"><span data-stu-id="a12c2-160">Running the command with this option and then looking at the output of `docker ps -a` command; notice that the container id (the `Environment.MachineName`) is not in the list.</span></span>

### <a name="running-the-container-using-powershell"></a><span data-ttu-id="a12c2-161">Uruchomiona kontenera przy użyciu programu PowerShell</span><span class="sxs-lookup"><span data-stu-id="a12c2-161">Running the container using PowerShell</span></span>
<span data-ttu-id="a12c2-162">W przykładowych plików projektu jest również *run.ps1* czyli przykładowy sposób do uruchamiania aplikacji akceptować argumenty przy użyciu programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a12c2-162">In the sample project files there is also a *run.ps1* which is an example of how to use PowerShell to run the application accepting the arguments.</span></span>

<span data-ttu-id="a12c2-163">Aby uruchomić, Otwórz program PowerShell i użyj następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="a12c2-163">To run, open PowerShell and use the following command:</span></span>

```
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a><span data-ttu-id="a12c2-164">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="a12c2-164">Summary</span></span>
<span data-ttu-id="a12c2-165">Wystarczy dodać plik Dockerfile i publikowanie aplikacji, containerize aplikacji konsoli .NET Framework i teraz korzystać z uruchamiając wiele wystąpień, czystego uruchomienia i zatrzymania i więcej możliwości systemu Windows Server 2016 bez żadnego na wszystkich zmian w kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a12c2-165">Just by adding a Dockerfile and publishing the application, you can containerize your .NET Framework console applications and now take the advantage of running multiple instances, clean start and stop and more Windows Server 2016 capabilities without making any changes to the application code at all.</span></span>