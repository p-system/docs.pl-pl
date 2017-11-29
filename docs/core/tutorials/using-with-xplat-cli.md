---
title: "Rozpoczynanie pracy z platformą .NET Core za pomocą interfejsu wiersza polecenia"
description: "Samouczek krok po kroku, pokazujący sposób rozpocząć pracę z platformą .NET Core w systemie Windows, Linux lub macOS przy użyciu interfejsu wiersza polecenia (CLI) platformy .NET Core."
keywords: Oprogramowanie .NET core, interfejsu wiersza polecenia
author: cartermp
ms.author: mairaw
ms.date: 03/08/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 41632e63-d5c6-4427-a09e-51dc1116d45f
ms.openlocfilehash: 19622cca1dd28d4d2248d69f1b4081c352a0c4f4
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="getting-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a><span data-ttu-id="41a7a-104">Rozpoczynanie pracy z platformą .NET Core w systemie Windows/Linux/macOS przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="41a7a-104">Getting started with .NET Core on Windows/Linux/macOS using the command line</span></span>

<span data-ttu-id="41a7a-105">W tym temacie opisano, jak można rozpocząć tworzenie aplikacji cross platform na tym komputerze przy użyciu narzędzi interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="41a7a-105">This topic will show you how to start developing cross-platforms apps in your machine using the .NET Core CLI tools.</span></span>

<span data-ttu-id="41a7a-106">Jeśli znasz zestaw narzędzi interfejsu wiersza polecenia platformy .NET Core odczytu [Omówienie zestawu SDK programu .NET Core](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="41a7a-106">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="41a7a-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="41a7a-107">Prerequisites</span></span>

- <span data-ttu-id="41a7a-108">[Oprogramowanie .NET core SDK 1.0](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="41a7a-108">[.NET Core SDK 1.0](https://www.microsoft.com/net/download/core).</span></span>
- <span data-ttu-id="41a7a-109">Edytor tekstu lub dowolnego edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="41a7a-109">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="41a7a-110">Witaj, aplikacji konsoli!</span><span class="sxs-lookup"><span data-stu-id="41a7a-110">Hello, Console App!</span></span>

<span data-ttu-id="41a7a-111">Możesz [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/HelloMsBuild) z dotnet/docs repozytorium GitHub.</span><span class="sxs-lookup"><span data-stu-id="41a7a-111">You can [view or download the sample code](https://github.com/dotnet/docs/tree/master/samples/core/console-apps/HelloMsBuild) from the dotnet/docs GitHub repository.</span></span> <span data-ttu-id="41a7a-112">Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="41a7a-112">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="41a7a-113">Otwórz wiersz polecenia i Utwórz folder o nazwie *Hello*.</span><span class="sxs-lookup"><span data-stu-id="41a7a-113">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="41a7a-114">Przejdź do folderu, który został utworzony i wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="41a7a-114">Navigate to the folder you created and type the following:</span></span>

```
$ dotnet new console
$ dotnet restore
$ dotnet run
```

<span data-ttu-id="41a7a-115">Poznajmy Szybkie wskazówki:</span><span class="sxs-lookup"><span data-stu-id="41a7a-115">Let's do a quick walkthrough:</span></span>

1. `$ dotnet new console`

   <span data-ttu-id="41a7a-116">[`dotnet new`](../tools/dotnet-new.md)Tworzy aktualne `Hello.csproj` pliku projektu z zależnościami, które są niezbędne do tworzenia aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="41a7a-116">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="41a7a-117">Tworzy również `Program.cs`, podstawowe plik zawierający punkt wejścia dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="41a7a-117">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>
   
   <span data-ttu-id="41a7a-118">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="41a7a-118">`Hello.csproj`:</span></span>

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]   

   <span data-ttu-id="41a7a-119">Plik projektu określa wszystko, co jest potrzebne do przywrócenia zależności i kompilacji programu.</span><span class="sxs-lookup"><span data-stu-id="41a7a-119">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="41a7a-120">`OutputType` Określa tag tworzymy plik wykonywalny, innymi słowy aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="41a7a-120">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="41a7a-121">`TargetFramework` Tag Określa, jakie implementacji .NET możemy docelowych.</span><span class="sxs-lookup"><span data-stu-id="41a7a-121">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="41a7a-122">W scenariuszu zaawansowanym, można określić wiele platform docelowych i kompilacji do wszystkich tych w ramach jednej operacji.</span><span class="sxs-lookup"><span data-stu-id="41a7a-122">In an advance scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="41a7a-123">W tym samouczku firma Microsoft będzie osadzania kompilowanie tylko dla platformy .NET Core 1.0.</span><span class="sxs-lookup"><span data-stu-id="41a7a-123">In this tutorial, we'll stick to building only for .NET Core 1.0.</span></span>

   <span data-ttu-id="41a7a-124">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="41a7a-124">`Program.cs`:</span></span>

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]   

   <span data-ttu-id="41a7a-125">Program, który rozpoczyna się od `using System`, co oznacza, że "Przenieś wszystko `System` przestrzeni nazw do zakresu dla tego pliku".</span><span class="sxs-lookup"><span data-stu-id="41a7a-125">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="41a7a-126">`System` Przestrzeń nazw zawiera podstawowe konstrukcji `string`, lub typy liczbowe.</span><span class="sxs-lookup"><span data-stu-id="41a7a-126">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="41a7a-127">Następnie definicję przestrzeni nazw o nazwie `Hello`.</span><span class="sxs-lookup"><span data-stu-id="41a7a-127">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="41a7a-128">Można to zmienić, do dowolnych znaków.</span><span class="sxs-lookup"><span data-stu-id="41a7a-128">You can change this to anything you want.</span></span> <span data-ttu-id="41a7a-129">Klasa o nazwie `Program` jest zdefiniowany w tej przestrzeni nazw z `Main` metody pobierającej tablicy ciągów jako jej argument.</span><span class="sxs-lookup"><span data-stu-id="41a7a-129">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="41a7a-130">Ta tablica zawiera listę argumentów przekazana wywołanego skompilowany program.</span><span class="sxs-lookup"><span data-stu-id="41a7a-130">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="41a7a-131">Ta tablica nie jest używany, jak: wszystkich zadań programu jest napisanie "Witaj świecie!"</span><span class="sxs-lookup"><span data-stu-id="41a7a-131">As it is, this array is not used: all the program is doing is to write "Hello World!"</span></span> <span data-ttu-id="41a7a-132">w konsoli.</span><span class="sxs-lookup"><span data-stu-id="41a7a-132">to the console.</span></span> <span data-ttu-id="41a7a-133">Później, wybierzemy zmiany do kodu, który będzie używać tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="41a7a-133">Later, we'll make changes to the code that will make use of this argument.</span></span>

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

2. `$ dotnet restore`

   <span data-ttu-id="41a7a-134">[`dotnet restore`](../tools/dotnet-restore.md)Wywołano [NuGet](https://www.nuget.org/) (.NET package manager) w celu przywrócenia drzewie zależności.</span><span class="sxs-lookup"><span data-stu-id="41a7a-134">[`dotnet restore`](../tools/dotnet-restore.md) calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="41a7a-135">Analizuje NuGet *Hello.csproj* plików, pliki do pobrania zależności określone w pliku (lub grabs je z pamięci podręcznej na komputerze) i zapisuje *obj/project.assets.json* pliku.</span><span class="sxs-lookup"><span data-stu-id="41a7a-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies stated in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file.</span></span>  <span data-ttu-id="41a7a-136">*Project.assets.json* plik jest niezbędny można było skompilować i uruchomić.</span><span class="sxs-lookup"><span data-stu-id="41a7a-136">The *project.assets.json* file is necessary to be able to compile and run.</span></span>
   
   <span data-ttu-id="41a7a-137">*Project.assets.json* plik jest utrwalona i pełny zestaw wykres zależności NuGet i inne informacje opisujące aplikację.</span><span class="sxs-lookup"><span data-stu-id="41a7a-137">The *project.assets.json* file is a persisted and complete set of the graph of NuGet dependencies and other information describing an app.</span></span>  <span data-ttu-id="41a7a-138">Ten plik jest odczytywany przez innych narzędzi, takich jak [ `dotnet build` ](../tools/dotnet-build.md) i [ `dotnet run` ](../tools/dotnet-run.md), umożliwiając im procesu kodu źródłowego z poprawny zestaw zależności NuGet i powiązanie rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="41a7a-138">This file is read by other tools, such as [`dotnet build`](../tools/dotnet-build.md) and [`dotnet run`](../tools/dotnet-run.md), enabling them to process the source code with a correct set of NuGet dependencies and binding resolutions.</span></span>
   
3. `$ dotnet run`

   <span data-ttu-id="41a7a-139">[`dotnet run`](../tools/dotnet-run.md)wywołania [ `dotnet build` ](../tools/dotnet-build.md) do upewnij się, że kompilacji są wbudowane elementy docelowe, a następnie wywołania `dotnet <assembly.dll>` do uruchomienia aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="41a7a-139">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>
   
    ```
    $ dotnet run
    Hello World!
    ```

    <span data-ttu-id="41a7a-140">Alternatywnie można również wykonywać [ `dotnet build` ](../tools/dotnet-build.md) skompilować kod bez uruchamiania Kompilowanie aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="41a7a-140">Alternatively, you can also execute [`dotnet build`](../tools/dotnet-build.md) to compile the code without running the build console applications.</span></span> <span data-ttu-id="41a7a-141">Powoduje to skompilowanej aplikacji jako plik DLL, który może być uruchamiane przy `dotnet bin\Debug\netcoreapp1.0\Hello.dll` w systemie Windows (Użyj `/` dla systemów z systemem innym niż Windows).</span><span class="sxs-lookup"><span data-stu-id="41a7a-141">This results in a compiled application as a DLL file that can be run with `dotnet bin\Debug\netcoreapp1.0\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span> <span data-ttu-id="41a7a-142">Argumenty do aplikacji mogą określać również, jak można zauważyć później na temat.</span><span class="sxs-lookup"><span data-stu-id="41a7a-142">You may also specify arguments to the application as you'll see later on the topic.</span></span>

    ```
    $ dotnet bin\Debug\netcoreapp1.0\Hello.dll
    Hello World!
    ```

    <span data-ttu-id="41a7a-143">W ramach scenariusza zaawansowanego jest możliwe utworzenie aplikacji jako autonomiczny zestaw plików specyficzne dla platformy, które mogą być wdrożone i uruchom na komputerze, na którym nie muszą być .NET Core zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="41a7a-143">As an advanced scenario, it's possible to build the application as a self-contained set of platform-specific files that can be deployed and run to a machine that doesn't necessarily have .NET Core installed.</span></span> <span data-ttu-id="41a7a-144">Zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="41a7a-144">See [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

### <a name="augmenting-the-program"></a><span data-ttu-id="41a7a-145">Rozbudować program</span><span class="sxs-lookup"><span data-stu-id="41a7a-145">Augmenting the program</span></span>

<span data-ttu-id="41a7a-146">Zmieńmy nieco program.</span><span class="sxs-lookup"><span data-stu-id="41a7a-146">Let's change the program a bit.</span></span> <span data-ttu-id="41a7a-147">Numery Fibonacci fun, więc Dodajmy oprócz Użyj argument greet osoby uruchomiona aplikacja.</span><span class="sxs-lookup"><span data-stu-id="41a7a-147">Fibonacci numbers are fun, so let's add that in addition to use the argument to greet the person running the app.</span></span>

1. <span data-ttu-id="41a7a-148">Zastąp zawartość z *Program.cs* pliku następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="41a7a-148">Replace the contents of your *Program.cs*  file with the following code:</span></span>

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]   

2. <span data-ttu-id="41a7a-149">Wykonanie [ `dotnet build` ](../tools/dotnet-build.md) do kompilacji zmian.</span><span class="sxs-lookup"><span data-stu-id="41a7a-149">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

3. <span data-ttu-id="41a7a-150">Uruchom program przekazanie parametru do aplikacji:</span><span class="sxs-lookup"><span data-stu-id="41a7a-150">Run the program passing a parameter to the app:</span></span>

   ```
   $ dotnet run -- John
   Hello John!
   Fibonacci Numbers 1-15:
   1: 0
   2: 1
   3: 1
   4: 2
   5: 3
   6: 5
   7: 8
   8: 13
   9: 21
   10: 34
   11: 55
   12: 89
   13: 144
   14: 233
   15: 377
   ```

<span data-ttu-id="41a7a-151">I to już wszystko!</span><span class="sxs-lookup"><span data-stu-id="41a7a-151">And that's it!</span></span>  <span data-ttu-id="41a7a-152">Można rozszerzyć `Program.cs` żadnym chcesz.</span><span class="sxs-lookup"><span data-stu-id="41a7a-152">You can augment `Program.cs` any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="41a7a-153">Praca z wieloma plikami</span><span class="sxs-lookup"><span data-stu-id="41a7a-153">Working with multiple files</span></span>

<span data-ttu-id="41a7a-154">Pojedynczych plików jest poprawna dla programów jednorazowe prostego, ale jeśli tworzysz złożonych aplikacji jest teraz zawierają wiele plików źródłowych w projekcie najczęściej kompilacji wylogowuje na poprzednim przykładzie Fibonacci przez buforowanie niektórych wartości Fibonacci i dodać niektóre cykliczne funkcje.</span><span class="sxs-lookup"><span data-stu-id="41a7a-154">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple source files on your project Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span> 

1. <span data-ttu-id="41a7a-155">Dodaj nowy plik wewnątrz *Hello* katalog o nazwie *FibonacciGenerator.cs* następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="41a7a-155">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]   

2. <span data-ttu-id="41a7a-156">Zmień `Main` metody w Twojej *Program.cs* plik, aby utworzyć wystąpienia klasy nowy i Wywołaj jej metodę jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="41a7a-156">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. <span data-ttu-id="41a7a-157">Wykonanie [ `dotnet build` ](../tools/dotnet-build.md) do kompilacji zmian.</span><span class="sxs-lookup"><span data-stu-id="41a7a-157">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

4. <span data-ttu-id="41a7a-158">Uruchamianie aplikacji, wykonując [ `dotnet run` ](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="41a7a-158">Run your app by executing [`dotnet run`](../tools/dotnet-run.md).</span></span> <span data-ttu-id="41a7a-159">Poniżej przedstawiono dane wyjściowe programu:</span><span class="sxs-lookup"><span data-stu-id="41a7a-159">The following shows the program output:</span></span>

   ```
   0
   1
   1
   2
   3
   5
   8
   13
   21
   34
   55
   89
   144
   233
   377
   ```

<span data-ttu-id="41a7a-160">I to już wszystko!</span><span class="sxs-lookup"><span data-stu-id="41a7a-160">And that's it!</span></span> <span data-ttu-id="41a7a-161">Teraz możesz rozpocząć używać, podstawowe koncepcje przedstawiono w tym miejscu do tworzenia własnych programów.</span><span class="sxs-lookup"><span data-stu-id="41a7a-161">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

<span data-ttu-id="41a7a-162">Należy pamiętać, że poleceń i kroki opisane w tym samouczku do uruchamiania aplikacji są używane tylko w czasie tworzenia.</span><span class="sxs-lookup"><span data-stu-id="41a7a-162">Note that the commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="41a7a-163">Gdy wszystko jest gotowe do wdrożenia aplikacji, należy spojrzeć na różnych [strategii wdrażania](../deploying/index.md) dla aplikacji .NET Core i [ `dotnet publish` ](../tools/dotnet-publish.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="41a7a-163">Once you're ready to deploy your app, you'll want to take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

## <a name="see-also"></a><span data-ttu-id="41a7a-164">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41a7a-164">See also</span></span>

[<span data-ttu-id="41a7a-165">Organizowanie i testowanie projektów przy użyciu narzędzi interfejsu wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="41a7a-165">Organizing and testing projects with the .NET Core CLI tools</span></span>](testing-with-cli.md)