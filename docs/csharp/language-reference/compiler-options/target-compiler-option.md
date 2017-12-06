---
title: -docelowego (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4666f0305fc2de35c1fa594ccef3dd3a64c0f67c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="target-c-compiler-options"></a><span data-ttu-id="d0ee5-102">/target (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="d0ee5-102">/target (C# Compiler Options)</span></span>
<span data-ttu-id="d0ee5-103">**/Target** — opcja kompilatora można określić w jednym z czterech formularzy:</span><span class="sxs-lookup"><span data-stu-id="d0ee5-103">The **/target** compiler option can be specified in one of four forms:</span></span>  
  
 [<span data-ttu-id="d0ee5-104">/ target: appcontainerexe</span><span class="sxs-lookup"><span data-stu-id="d0ee5-104">/target:appcontainerexe</span></span>](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 <span data-ttu-id="d0ee5-105">Aby utworzyć plik .exe [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d0ee5-105">To create an .exe file for [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] apps.</span></span>  
  
 [<span data-ttu-id="d0ee5-106">/ target: exe</span><span class="sxs-lookup"><span data-stu-id="d0ee5-106">/target:exe</span></span>](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 <span data-ttu-id="d0ee5-107">Aby utworzyć plik .exe.</span><span class="sxs-lookup"><span data-stu-id="d0ee5-107">To create an .exe file.</span></span>  
  
 [<span data-ttu-id="d0ee5-108">/ target: Library</span><span class="sxs-lookup"><span data-stu-id="d0ee5-108">/target:library</span></span>](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 <span data-ttu-id="d0ee5-109">Aby utworzyć biblioteki kodu.</span><span class="sxs-lookup"><span data-stu-id="d0ee5-109">To create a code library.</span></span>  
  
 [<span data-ttu-id="d0ee5-110">/ target: module</span><span class="sxs-lookup"><span data-stu-id="d0ee5-110">/target:module</span></span>](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 <span data-ttu-id="d0ee5-111">Aby utworzyć moduł.</span><span class="sxs-lookup"><span data-stu-id="d0ee5-111">To create a module.</span></span>  
  
 [<span data-ttu-id="d0ee5-112">/ target: winexe</span><span class="sxs-lookup"><span data-stu-id="d0ee5-112">/target:winexe</span></span>](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 <span data-ttu-id="d0ee5-113">Aby utworzyć program systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="d0ee5-113">To create a Windows program.</span></span>  
  
 [<span data-ttu-id="d0ee5-114">/ target: winmdobj</span><span class="sxs-lookup"><span data-stu-id="d0ee5-114">/target:winmdobj</span></span>](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 <span data-ttu-id="d0ee5-115">Aby utworzyć plik pośredni .winmdobj.</span><span class="sxs-lookup"><span data-stu-id="d0ee5-115">To create an intermediate .winmdobj file.</span></span>  
  
 <span data-ttu-id="d0ee5-116">Jeśli nie podasz **/target: module**, **/target** powoduje, że manifestu zestawu .NET Framework do umieszczenia w pliku wyjściowym.</span><span class="sxs-lookup"><span data-stu-id="d0ee5-116">Unless you specify **/target:module**, **/target** causes a .NET Framework assembly manifest to be placed in an output file.</span></span> <span data-ttu-id="d0ee5-117">Aby uzyskać więcej informacji, zobacz [zestawy w środowisku uruchomieniowym języka](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) i [takie same atrybuty wspólne](../../programming-guide/concepts/attributes/common-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="d0ee5-117">For more information, see [Assemblies in the Common Language Runtime](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) and [Common Attributes](../../programming-guide/concepts/attributes/common-attributes.md).</span></span>  
  
 <span data-ttu-id="d0ee5-118">Manifest zestawu jest umieszczany w pierwszym pliku wyjściowego .exe w kompilacji lub w pierwszej biblioteki DLL, jeśli plik wyjściowy .exe nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="d0ee5-118">The assembly manifest is placed in the first .exe output file in the compilation or in the first DLL, if there is no .exe output file.</span></span> <span data-ttu-id="d0ee5-119">Na przykład, w wierszu polecenia następujący plik manifestu zostaną umieszczone w `1.exe`:</span><span class="sxs-lookup"><span data-stu-id="d0ee5-119">For example, in the following command line, the manifest will be placed in `1.exe`:</span></span>  
  
```console  
csc /out:1.exe t1.cs /out:2.netmodule t2.cs  
```  
  
 <span data-ttu-id="d0ee5-120">Kompilator tworzy tylko jeden manifest zestawu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="d0ee5-120">The compiler creates only one assembly manifest per compilation.</span></span> <span data-ttu-id="d0ee5-121">Informacje o wszystkich plików w kompilacji jest umieszczany w manifeście zestawu.</span><span class="sxs-lookup"><span data-stu-id="d0ee5-121">Information about all files in a compilation is placed in the assembly manifest.</span></span> <span data-ttu-id="d0ee5-122">Wszystkie pliki z wyjątkiem tych, utworzone za pomocą wyjściowe **/target: module** może zawierać manifest zestawu.</span><span class="sxs-lookup"><span data-stu-id="d0ee5-122">All output files except those created with **/target:module** can contain an assembly manifest.</span></span> <span data-ttu-id="d0ee5-123">Podczas produkowania wielu plików wyjściowych w wierszu polecenia, można utworzyć tylko jeden zestaw manifestu i należy przejść do pierwszego pliku wyjściowego, określona w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="d0ee5-123">When producing multiple output files at the command line, only one assembly manifest can be created and it must go into the first output file specified on the command line.</span></span> <span data-ttu-id="d0ee5-124">Niezależnie od tego, jakie pierwszy plik wyjściowy jest (**/target: exe**, **/target: winexe**, **/target: Library** lub **/target: module**), inne pliki wyjściowe wygenerowane w tej samej kompilacji musi być modułów (**/target: module**).</span><span class="sxs-lookup"><span data-stu-id="d0ee5-124">No matter what the first output file is (**/target:exe**, **/target:winexe**, **/target:library** or **/target:module**), any other output files produced in the same compilation must be modules (**/target:module**).</span></span>  
  
 <span data-ttu-id="d0ee5-125">W przypadku utworzenia zestawu, może oznaczać, że całość lub część kodu jest zgodny ze specyfikacją CLS <xref:System.CLSCompliantAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d0ee5-125">If you create an assembly, you can indicate that all or part of your code is CLS compliant with the <xref:System.CLSCompliantAttribute> attribute.</span></span>  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 <span data-ttu-id="d0ee5-126">Aby uzyskać więcej informacji na temat ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span><span class="sxs-lookup"><span data-stu-id="d0ee5-126">For more information about setting this compiler option programmatically, see <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0ee5-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0ee5-127">See Also</span></span>  
 [<span data-ttu-id="d0ee5-128">Opcje kompilatora C#</span><span class="sxs-lookup"><span data-stu-id="d0ee5-128">C# Compiler Options</span></span>](../../../csharp/language-reference/compiler-options/index.md)  
 [<span data-ttu-id="d0ee5-129">Zarządzanie właściwościami projektów i rozwiązań</span><span class="sxs-lookup"><span data-stu-id="d0ee5-129">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)  
 [<span data-ttu-id="d0ee5-130">/ subsystemversion (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="d0ee5-130">/subsystemversion (C# Compiler Options)</span></span>](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)