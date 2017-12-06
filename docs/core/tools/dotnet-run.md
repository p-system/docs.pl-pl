---
title: 'Uruchom polecenie: .NET Core interfejsu wiersza polecenia platformy DotNet'
description: "Dotnet, uruchom polecenie zapewnia to wygodny sposób do uruchamiania aplikacji z kodu źródłowego."
author: mairaw
ms.author: mairaw
ms.date: 09/24/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 7670934199d7d4b8a7c5e598142366ef1eb3ef1c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-run"></a><span data-ttu-id="4138d-103">Uruchom DotNet</span><span class="sxs-lookup"><span data-stu-id="4138d-103">dotnet run</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="4138d-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4138d-104">Name</span></span>

<span data-ttu-id="4138d-105">`dotnet run`-Uruchamia źródła kodu bez jawnego kompilowania i uruchamiania poleceń.</span><span class="sxs-lookup"><span data-stu-id="4138d-105">`dotnet run` - Runs source code without any explicit compile or launch commands.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4138d-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="4138d-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="4138d-107">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="4138d-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet run [-c|--configuration] [-f|--framework] [--force] [--launch-profile] [--no-build] [--no-dependencies] [--no-launch-profile] [--no-restore] [-p|--project] [--runtime] [[--] [application arguments]]
dotnet run [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4138d-108">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="4138d-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet run [-c|--configuration] [-f|--framework] [-p|--project] [[--] [application arguments]]
dotnet run [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="4138d-109">Opis</span><span class="sxs-lookup"><span data-stu-id="4138d-109">Description</span></span>

<span data-ttu-id="4138d-110">`dotnet run` Polecenia oferuje wygodny sposób do uruchamiania aplikacji z kodu źródłowego za pomocą jednego polecenia.</span><span class="sxs-lookup"><span data-stu-id="4138d-110">The `dotnet run` command provides a convenient option to run your application from the source code with one command.</span></span> <span data-ttu-id="4138d-111">Jest to przydatne w przypadku szybkiego iteracyjne programowanie z wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="4138d-111">It's useful for fast iterative development from the command line.</span></span> <span data-ttu-id="4138d-112">Polecenie zależy od [ `dotnet build` ](dotnet-build.md) do kompilacji kodu.</span><span class="sxs-lookup"><span data-stu-id="4138d-112">The command depends on the [`dotnet build`](dotnet-build.md) command to build the code.</span></span> <span data-ttu-id="4138d-113">Wszelkie wymagania dotyczące kompilacji, takim jak projekt musi zostać przywrócona, dotyczą `dotnet run` również.</span><span class="sxs-lookup"><span data-stu-id="4138d-113">Any requirements for the build, such as that the project must be restored first, apply to `dotnet run` as well.</span></span> 

<span data-ttu-id="4138d-114">Pliki wyjściowe są zapisywane w domyślnej lokalizacji, która jest `bin/<configuration>/<target>`.</span><span class="sxs-lookup"><span data-stu-id="4138d-114">Output files are written into the default location, which is `bin/<configuration>/<target>`.</span></span> <span data-ttu-id="4138d-115">Na przykład jeśli masz `netcoreapp1.0` aplikacji i uruchom `dotnet run`, dane wyjściowe są umieszczane w `bin/Debug/netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="4138d-115">For example if you have a `netcoreapp1.0` application and you run `dotnet run`, the output is placed in `bin/Debug/netcoreapp1.0`.</span></span> <span data-ttu-id="4138d-116">Pliki zostaną zastąpione, zgodnie z potrzebami.</span><span class="sxs-lookup"><span data-stu-id="4138d-116">Files are overwritten as needed.</span></span> <span data-ttu-id="4138d-117">Pliki tymczasowe są umieszczane w `obj` katalogu.</span><span class="sxs-lookup"><span data-stu-id="4138d-117">Temporary files are placed in the `obj` directory.</span></span> 

<span data-ttu-id="4138d-118">Jeśli projekt określa wielu struktur, wykonywania `dotnet run` powoduje błąd, chyba że `-f|--framework <FRAMEWORK>` opcja służy do określania platformę.</span><span class="sxs-lookup"><span data-stu-id="4138d-118">If the project specifies multiple frameworks, executing `dotnet run` results in an error unless the `-f|--framework <FRAMEWORK>` option is used to specify the framework.</span></span>

<span data-ttu-id="4138d-119">`dotnet run` Polecenie jest używane w kontekście projektów nie skompilowane zestawy.</span><span class="sxs-lookup"><span data-stu-id="4138d-119">The `dotnet run` command is used in the context of projects, not built assemblies.</span></span> <span data-ttu-id="4138d-120">Jeśli zastanawiasz się do uruchomienia aplikacji zależnych od framework DLL zamiast tego należy użyć [dotnet](dotnet.md) bez polecenia.</span><span class="sxs-lookup"><span data-stu-id="4138d-120">If you're trying to run a framework-dependent application DLL instead, you must use [dotnet](dotnet.md) without a command.</span></span> <span data-ttu-id="4138d-121">Na przykład, aby uruchomić `myapp.dll`, użyj:</span><span class="sxs-lookup"><span data-stu-id="4138d-121">For example, to run `myapp.dll`, use:</span></span>

```
dotnet myapp.dll
```

<span data-ttu-id="4138d-122">Aby uzyskać więcej informacji na temat `dotnet` sterowników, zobacz [.NET Core wiersza polecenia narzędzia (CLI)](index.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="4138d-122">For more information on the `dotnet` driver, see the [.NET Core Command Line Tools (CLI)](index.md) topic.</span></span>

<span data-ttu-id="4138d-123">Aby uruchomić aplikację, `dotnet run` polecenia rozpoznaje zależności aplikacji, które znajdują się poza udostępnionym środowiska uruchomieniowego z pamięci podręcznej NuGet.</span><span class="sxs-lookup"><span data-stu-id="4138d-123">In order to run the application, the `dotnet run` command resolves the dependencies of the application that are outside of the shared runtime from the NuGet cache.</span></span> <span data-ttu-id="4138d-124">Ponieważ używa zależności w pamięci podręcznej, nie zalecamy używania `dotnet run` do uruchamiania aplikacji w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="4138d-124">Because it uses cached dependencies, it's not recommended to use `dotnet run` to run applications in production.</span></span> <span data-ttu-id="4138d-125">Zamiast tego [tworzenia wdrożenia](../deploying/index.md) przy użyciu [ `dotnet publish` ](dotnet-publish.md) polecenia i wdrażanie publikowanych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="4138d-125">Instead, [create a deployment](../deploying/index.md) using the [`dotnet publish`](dotnet-publish.md) command and deploy the published output.</span></span>

## <a name="options"></a><span data-ttu-id="4138d-126">Opcje</span><span class="sxs-lookup"><span data-stu-id="4138d-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="4138d-127">.NET core 2.x</span><span class="sxs-lookup"><span data-stu-id="4138d-127">.NET Core 2.x</span></span>](#tab/netcore2x)

`--`

<span data-ttu-id="4138d-128">Argumenty rozgranicza `dotnet run` z argumentów uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4138d-128">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="4138d-129">Wszystkie argumenty po tym są przekazywane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4138d-129">All arguments after this one are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="4138d-130">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4138d-130">Defines the build configuration.</span></span> <span data-ttu-id="4138d-131">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="4138d-131">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="4138d-132">Tworzenie i działanie aplikacji przy użyciu określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="4138d-132">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="4138d-133">Platformę należy określić w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="4138d-133">The framework must be specified in the project file.</span></span>

`--force`

<span data-ttu-id="4138d-134">Wymusza wszystkie zależności, które można rozwiązać, nawet jeśli ostatniego przywracanie zakończyło się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="4138d-134">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="4138d-135">Jest to równoważne usuwanie *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="4138d-135">This is equivalent to deleting *project.assets.json*.</span></span>

`-h|--help`

<span data-ttu-id="4138d-136">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="4138d-136">Prints out a short help for the command.</span></span>

`--launch-profile <NAME>`

<span data-ttu-id="4138d-137">Nazwa uruchomienie profilu (jeśli istnieje) do użycia podczas uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4138d-137">The name of the launch profile (if any) to use when launching the application.</span></span> <span data-ttu-id="4138d-138">Profile uruchamiania są zdefiniowane w *launchSettings.json* pliku i są zwykle nazywane `Development`, `Staging` i `Production`.</span><span class="sxs-lookup"><span data-stu-id="4138d-138">Launch profiles are defined in the *launchSettings.json* file and are typically called `Development`, `Staging` and `Production`.</span></span> <span data-ttu-id="4138d-139">Aby uzyskać więcej informacji, zobacz [Praca w środowiskach wielu](/aspnet/core/fundamentals/environments).</span><span class="sxs-lookup"><span data-stu-id="4138d-139">For more information, see [Working with multiple environments](/aspnet/core/fundamentals/environments).</span></span>

`--no-build`

<span data-ttu-id="4138d-140">Nie Skompiluj projekt przed uruchomieniem.</span><span class="sxs-lookup"><span data-stu-id="4138d-140">Doesn't build the project before running.</span></span>

`--no-dependencies`

<span data-ttu-id="4138d-141">Podczas przywracania projektu z projektu do projektu (P2P) odwołań, przywraca i nie odwołuje się do projektu głównego.</span><span class="sxs-lookup"><span data-stu-id="4138d-141">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--no-launch-profile`

<span data-ttu-id="4138d-142">Nie próbuj używać *launchSettings.json* do skonfigurowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4138d-142">Doesn't attempt to use *launchSettings.json* to configure the application.</span></span>

`--no-restore`

<span data-ttu-id="4138d-143">Nie wykonać przywracanie niejawne, podczas uruchamiania polecenia.</span><span class="sxs-lookup"><span data-stu-id="4138d-143">Doesn't perform an implicit restore when running the command.</span></span>

`-p|--project <PATH>`

<span data-ttu-id="4138d-144">Określa ścieżkę pliku projektu do uruchomienia (folder lub ścieżka pełna).</span><span class="sxs-lookup"><span data-stu-id="4138d-144">Specifies the path of the project file to run (folder name or full path).</span></span> <span data-ttu-id="4138d-145">Domyślnie do bieżącego katalogu, jeśli nie określono.</span><span class="sxs-lookup"><span data-stu-id="4138d-145">It defaults to the current directory if not specified.</span></span>

`--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="4138d-146">Określa docelowe środowisko uruchomieniowe pod kątem przywracania pakietów dla.</span><span class="sxs-lookup"><span data-stu-id="4138d-146">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="4138d-147">Aby uzyskać listę identyfikatorów środowiska uruchomieniowego (RID), zobacz [katalogu RID](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="4138d-147">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4138d-148">.NET core 1.x</span><span class="sxs-lookup"><span data-stu-id="4138d-148">.NET Core 1.x</span></span>](#tab/netcore1x)

`--`

<span data-ttu-id="4138d-149">Argumenty rozgranicza `dotnet run` z argumentów uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4138d-149">Delimits arguments to `dotnet run` from arguments for the application being run.</span></span> <span data-ttu-id="4138d-150">Wszystkie argumenty po tym są przekazywane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4138d-150">All arguments after this one are passed to the application run.</span></span>

`-c|--configuration {Debug|Release}`

<span data-ttu-id="4138d-151">Definiuje konfigurację kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4138d-151">Defines the build configuration.</span></span> <span data-ttu-id="4138d-152">Wartość domyślna to `Debug`.</span><span class="sxs-lookup"><span data-stu-id="4138d-152">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="4138d-153">Tworzenie i działanie aplikacji przy użyciu określonego [framework](../../standard/frameworks.md).</span><span class="sxs-lookup"><span data-stu-id="4138d-153">Builds and runs the app using the specified [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="4138d-154">Platformę należy określić w pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="4138d-154">The framework must be specified in the project file.</span></span>

`-h|--help`

<span data-ttu-id="4138d-155">Drukuje krótkich pomocy dla polecenia.</span><span class="sxs-lookup"><span data-stu-id="4138d-155">Prints out a short help for the command.</span></span>

`-p|--project <PATH/PROJECT.csproj>`

<span data-ttu-id="4138d-156">Określa ścieżkę i nazwę pliku projektu.</span><span class="sxs-lookup"><span data-stu-id="4138d-156">Specifies the path and name of the project file.</span></span> <span data-ttu-id="4138d-157">(Patrz Notatka). Domyślnie do bieżącego katalogu, jeśli nie określono.</span><span class="sxs-lookup"><span data-stu-id="4138d-157">(See the NOTE.) It defaults to the current directory if not specified.</span></span>

> [!NOTE]
> <span data-ttu-id="4138d-158">Użyj ścieżka i nazwa pliku projektu z `-p|--project` opcji.</span><span class="sxs-lookup"><span data-stu-id="4138d-158">Use the path and name of the project file with the `-p|--project` option.</span></span> <span data-ttu-id="4138d-159">Regresja w interfejsu wiersza polecenia uniemożliwia, podając ścieżkę folderu z platformą .NET Core 1.x zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="4138d-159">A regression in the CLI prevents providing a folder path with .NET Core 1.x SDK.</span></span> <span data-ttu-id="4138d-160">Aby uzyskać więcej informacji na temat tego problemu, zobacz [dotnet Uruchom -p, nie można uruchomić projektu (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span><span class="sxs-lookup"><span data-stu-id="4138d-160">For more information about this issue, see [dotnet run -p, can not start a project (dotnet/cli #5992)](https://github.com/dotnet/cli/issues/5992).</span></span>

---

## <a name="examples"></a><span data-ttu-id="4138d-161">Przykłady</span><span class="sxs-lookup"><span data-stu-id="4138d-161">Examples</span></span>

<span data-ttu-id="4138d-162">Uruchom projekt w bieżącym katalogu:</span><span class="sxs-lookup"><span data-stu-id="4138d-162">Run the project in the current directory:</span></span>

`dotnet run`

<span data-ttu-id="4138d-163">Uruchamia określony projekt:</span><span class="sxs-lookup"><span data-stu-id="4138d-163">Run the specified project:</span></span>

`dotnet run --project /projects/proj1/proj1.csproj`

<span data-ttu-id="4138d-164">Uruchom projekt w bieżącym katalogu ( `--help` argument w tym przykładzie jest przekazywany do aplikacji, ponieważ `--` argument jest używany):</span><span class="sxs-lookup"><span data-stu-id="4138d-164">Run the project in the current directory (the `--help` argument in this example is passed to the application, since the `--` argument is used):</span></span>

`dotnet run --configuration Release -- --help`