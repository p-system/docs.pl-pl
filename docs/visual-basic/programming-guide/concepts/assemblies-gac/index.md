---
title: "Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fcf78ff1-f1ab-4a5d-b6d8-00d2046b6c80
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8a53a153851973c735a430056520b01c27b1ef59
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="assemblies-and-the-global-assembly-cache-visual-basic"></a><span data-ttu-id="1d3f4-102">Zestawy i Globalna pamięć podręczna zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d3f4-102">Assemblies and the Global Assembly Cache (Visual Basic)</span></span>
<span data-ttu-id="1d3f4-103">Zestawy stanowią podstawową jednostkę wdrożenia, kontroli wersji, ponownemu, zakresu aktywacji i uprawnień zabezpieczeń dla. Aplikacja Asp.net.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-103">Assemblies form the fundamental unit of deployment, version control, reuse, activation scoping, and security permissions for a .NET-based application.</span></span> <span data-ttu-id="1d3f4-104">Zestawy formę plik wykonywalny (.exe) lub dołączana dynamicznie biblioteka (dll) pliku i są blokami konstrukcyjnymi programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-104">Assemblies take the form of an executable (.exe) file or dynamic link library (.dll) file, and are the building blocks of the .NET Framework.</span></span> <span data-ttu-id="1d3f4-105">Zawierają środowisko uruchomieniowe języka wspólnego o informacje, które należy znać typ implementacji.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-105">They provide the common language runtime with the information it needs to be aware of type implementations.</span></span> <span data-ttu-id="1d3f4-106">Można potraktować zestawu jako kolekcję typów i zasobów, które tworzą jednostkę logiczną funkcjonalności i są tworzone współdziałają ze sobą.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-106">You can think of an assembly as a collection of types and resources that form a logical unit of functionality and are built to work together.</span></span>  
  
 <span data-ttu-id="1d3f4-107">Zestawy mogą zawierać przynajmniej jeden moduł.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-107">Assemblies can contain one or more modules.</span></span> <span data-ttu-id="1d3f4-108">Na przykład większych projektów mogą być planowane w taki sposób, że kilka indywidualnych deweloperów działać w oddzielnych modułów, wszystkie najbliższych, aby utworzyć w jednym zestawie.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-108">For example, larger projects may be planned in such a way that several individual developers work on separate modules, all coming together to create a single assembly.</span></span> <span data-ttu-id="1d3f4-109">Aby uzyskać więcej informacji o modułach, zobacz temat [porady: tworzenie zestawów Multifile](https://msdn.microsoft.com/library/226t7yxe).</span><span class="sxs-lookup"><span data-stu-id="1d3f4-109">For more information about modules, see the topic [How to: Build a Multifile Assembly](https://msdn.microsoft.com/library/226t7yxe).</span></span>  
  
 <span data-ttu-id="1d3f4-110">Zestawy mieć następujące właściwości:</span><span class="sxs-lookup"><span data-stu-id="1d3f4-110">Assemblies have the following properties:</span></span>  
  
-   <span data-ttu-id="1d3f4-111">Zestawy są zaimplementowane jako pliki .exe lub dll.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-111">Assemblies are implemented as .exe or .dll files.</span></span>  
  
-   <span data-ttu-id="1d3f4-112">Można udostępniać zestawu między aplikacjami, ustawiając dla niego w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-112">You can share an assembly between applications by putting it in the global assembly cache.</span></span> <span data-ttu-id="1d3f4-113">Zestawy muszą być o silnych nazwach, aby mogły one zostać uwzględnione w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-113">Assemblies must be strong-named before they can be included in the global assembly cache.</span></span> <span data-ttu-id="1d3f4-114">Aby uzyskać więcej informacji, zobacz [zestawy Strong-Named](https://msdn.microsoft.com/library/wd40t7ad).</span><span class="sxs-lookup"><span data-stu-id="1d3f4-114">For more information, see [Strong-Named Assemblies](https://msdn.microsoft.com/library/wd40t7ad).</span></span>  
  
-   <span data-ttu-id="1d3f4-115">Zestawy są ładowane do pamięci tylko wtedy, jeśli są wymagane.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-115">Assemblies are only loaded into memory if they are required.</span></span> <span data-ttu-id="1d3f4-116">Jeśli nie są używane, nie są załadowane.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-116">If they are not used, they are not loaded.</span></span> <span data-ttu-id="1d3f4-117">Oznacza to, że zestawy mogą być wydajnym sposobem zarządzania zasobami w większych projektów.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-117">This means that assemblies can be an efficient way to manage resources in larger projects.</span></span>  
  
-   <span data-ttu-id="1d3f4-118">Informacje o zestawie można uzyskać programistycznie przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-118">You can programmatically obtain information about an assembly by using reflection.</span></span> <span data-ttu-id="1d3f4-119">Aby uzyskać więcej informacji, zobacz [odbicie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span><span class="sxs-lookup"><span data-stu-id="1d3f4-119">For more information, see [Reflection (Visual Basic)](../../../../visual-basic/programming-guide/concepts/reflection.md).</span></span>  
  
-   <span data-ttu-id="1d3f4-120">Jeśli do załadowania zestawu jedynie, aby sprawdzić, należy użyć metody takich jak <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-120">If you want to load an assembly only to inspect it, use a method such as <xref:System.Reflection.Assembly.ReflectionOnlyLoadFrom%2A>.</span></span>  
  
## <a name="assembly-manifest"></a><span data-ttu-id="1d3f4-121">Manifest zestawu</span><span class="sxs-lookup"><span data-stu-id="1d3f4-121">Assembly Manifest</span></span>  
 <span data-ttu-id="1d3f4-122">W każdym zestawie jest *manifest zestawu*.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-122">Within every assembly is an *assembly manifest*.</span></span> <span data-ttu-id="1d3f4-123">Podobnie jak spisu treści, manifest zestawu zawiera następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="1d3f4-123">Similar to a table of contents, the assembly manifest contains the following:</span></span>  
  
-   <span data-ttu-id="1d3f4-124">Tożsamość zestawu (jego nazwa i wersja).</span><span class="sxs-lookup"><span data-stu-id="1d3f4-124">The assembly's identity (its name and version).</span></span>  
  
-   <span data-ttu-id="1d3f4-125">Tabela plików opisujące wszystkie pliki wchodzące w skład zestawu, na przykład innych zestawów utworzonego pliku .exe lub .dll opiera się na, lub nawet mapy bitowej i pliki Readme.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-125">A file table describing all the other files that make up the assembly, for example, any other assemblies you created that your .exe or .dll file relies on, or even bitmap or Readme files.</span></span>  
  
-   <span data-ttu-id="1d3f4-126">*Lista odwołań zestawu*, który znajduje się lista wszystkich zależności zewnętrznych — biblioteki lub inne pliki wymagań aplikacji, które mogło zostać utworzone przez innego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-126">An *assembly reference list*, which is a list of all external dependencies—.dlls or other files your application needs that may have been created by someone else.</span></span> <span data-ttu-id="1d3f4-127">Odwołania do zestawów zawierają odwołania do obiektów zarówno globalnych, jak i prywatnych.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-127">Assembly references contain references to both global and private objects.</span></span> <span data-ttu-id="1d3f4-128">Globalne obiekty znajdują się w globalnej pamięci podręcznej zestawów, dostępne dla innych aplikacji, w folderze System32 przypominające obszaru.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-128">Global objects reside in the global assembly cache, an area available to other applications, somewhat like the System32 directory.</span></span> <span data-ttu-id="1d3f4-129"><xref:Microsoft.VisualBasic?displayProperty=nameWithType> Przestrzeń nazw jest przykładem zestawu w globalnej pamięci podręcznej zestawów.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-129">The <xref:Microsoft.VisualBasic?displayProperty=nameWithType> namespace is an example of an assembly in the global assembly cache.</span></span> <span data-ttu-id="1d3f4-130">Obiekty prywatne muszą być w katalogu albo poziomu jako lub poniżej katalogu, w którym jest zainstalowana aplikacja.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-130">Private objects must be in a directory at either the same level as or below the directory in which your application is installed.</span></span>  
  
 <span data-ttu-id="1d3f4-131">Ponieważ zestawy zawierają informacje o zawartości, przechowywanie wersji i zależności, aplikacje utworzone przy użyciu języka Visual Basic nie należy polegać na wartości rejestru systemu Windows w celu poprawnego działania.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-131">Because assemblies contain information about content, versioning, and dependencies, the applications you create with Visual Basic do not rely on Windows registry values to function properly.</span></span> <span data-ttu-id="1d3f4-132">Zestawy zmniejszyć konflikty .dll i upewnić aplikacji, bardziej niezawodne i łatwiejsze do wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-132">Assemblies reduce .dll conflicts and make your applications more reliable and easier to deploy.</span></span> <span data-ttu-id="1d3f4-133">W wielu przypadkach można zainstalować. Aplikacji opartej na sieci za pomocą kopiowania plików do komputera docelowego.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-133">In many cases, you can install a .NET-based application simply by copying its files to the target computer.</span></span>  
  
 <span data-ttu-id="1d3f4-134">Aby uzyskać więcej informacji, zobacz [manifestu zestawu](https://msdn.microsoft.com/library/1w45z383).</span><span class="sxs-lookup"><span data-stu-id="1d3f4-134">For more information see [Assembly Manifest](https://msdn.microsoft.com/library/1w45z383).</span></span>  
  
## <a name="adding-a-reference-to-an-assembly"></a><span data-ttu-id="1d3f4-135">Dodawanie odwołania do zestawu</span><span class="sxs-lookup"><span data-stu-id="1d3f4-135">Adding a Reference to an Assembly</span></span>  
 <span data-ttu-id="1d3f4-136">Aby użyć zestawu, należy dodać odwołanie do niej.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-136">To use an assembly, you must add a reference to it.</span></span> <span data-ttu-id="1d3f4-137">Następnie użyj [Imports — instrukcja](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) wybierz przestrzeń nazw elementów, którego chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-137">Next, you use the [Imports statement](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) to choose the namespace of the items you want to use.</span></span> <span data-ttu-id="1d3f4-138">Po odwołuje się do zestawu i zaimportowane, wszystkie dostępne klasy, właściwości, metody i inni członkowie ich przestrzenie nazw są dostępne dla aplikacji tak, jakby ich kodem należały pliku źródłowego.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-138">Once an assembly is referenced and imported, all the accessible classes, properties, methods, and other members of its namespaces are available to your application as if their code were part of your source file.</span></span>  
  
## <a name="creating-an-assembly"></a><span data-ttu-id="1d3f4-139">Tworzenie zestawu</span><span class="sxs-lookup"><span data-stu-id="1d3f4-139">Creating an Assembly</span></span>  
 <span data-ttu-id="1d3f4-140">Kompilowanie aplikacji przez skompilowanie go z poziomu wiersza polecenia przy użyciu kompilatora wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-140">Compile your application by building it from the command line using the command-line compiler.</span></span> <span data-ttu-id="1d3f4-141">Aby uzyskać więcej informacji o tworzeniu zestawów z wiersza polecenia, zobacz [tworzenie z wiersza polecenia](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span><span class="sxs-lookup"><span data-stu-id="1d3f4-141">For details about building assemblies from the command line, see [Building from the Command Line](../../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1d3f4-142">Tworzenie zestawu w programie Visual Studio na **kompilacji** menu wybierz **kompilacji**.</span><span class="sxs-lookup"><span data-stu-id="1d3f4-142">To build an assembly in Visual Studio, on the **Build** menu choose **Build**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1d3f4-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d3f4-143">See Also</span></span>  
 [<span data-ttu-id="1d3f4-144">Zestawy w środowisko uruchomieniowe języka wspólnego</span><span class="sxs-lookup"><span data-stu-id="1d3f4-144">Assemblies in the Common Language Runtime</span></span>](https://msdn.microsoft.com/library/k3677y81)  
 [<span data-ttu-id="1d3f4-145">Przyjazne zestawy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d3f4-145">Friend Assemblies (Visual Basic)</span></span>](friend-assemblies.md)  
 [<span data-ttu-id="1d3f4-146">Porady: dzielenie się zestawem z innymi aplikacjami (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d3f4-146">How to: Share an Assembly with Other Applications (Visual Basic)</span></span>](how-to-share-an-assembly-with-other-applications.md)  
 [<span data-ttu-id="1d3f4-147">Porady: ładowanie i zwalnianie zestawów (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d3f4-147">How to: Load and Unload Assemblies (Visual Basic)</span></span>](how-to-load-and-unload-assemblies.md)  
 [<span data-ttu-id="1d3f4-148">Porady: Określanie, czy plik jest zestawem (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d3f4-148">How to: Determine If a File Is an Assembly (Visual Basic)</span></span>](how-to-determine-if-a-file-is-an-assembly.md)  
 [<span data-ttu-id="1d3f4-149">Porady: tworzenie i korzystanie z zestawów przy użyciu wiersza polecenia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d3f4-149">How to: Create and Use Assemblies Using the Command Line (Visual Basic)</span></span>](how-to-create-and-use-assemblies-using-the-command-line.md)  
 [<span data-ttu-id="1d3f4-150">Wskazówki: Osadzanie typów z zarządzanych zestawów w programie Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d3f4-150">Walkthrough: Embedding Types from Managed Assemblies in Visual Studio (Visual Basic)</span></span>](walkthrough-embedding-types-from-managed-assemblies-in-vs.md)  
 [<span data-ttu-id="1d3f4-151">Wskazówki: Osadzanie informacji o typie z zestawów Microsoft Office w Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d3f4-151">Walkthrough: Embedding Type Information from Microsoft Office Assemblies in Visual Studio (Visual Basic)</span></span>](walkthrough-embedding-type-information-from-microsoft-office-assemblies-in-vs.md)