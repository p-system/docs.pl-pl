---
title: /keyfile
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- /keyfile compiler option [Visual Basic]
- keyfile compiler option [Visual Basic]
- -keyfile compiler option [Visual Basic]
ms.assetid: ffa82a4b-517a-4c6c-9889-5bae7b534bb8
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 33c9bdf3cf055ea005542f8b2471963b16c16122
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="keyfile"></a><span data-ttu-id="001fc-102">/keyfile</span><span class="sxs-lookup"><span data-stu-id="001fc-102">/keyfile</span></span>
<span data-ttu-id="001fc-103">Określa plik zawierający klucz lub parę kluczy, aby zapewnić silnej nazwy zestawu.</span><span class="sxs-lookup"><span data-stu-id="001fc-103">Specifies a file containing a key or key pair to give an assembly a strong name.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="001fc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="001fc-104">Syntax</span></span>  
  
```  
/keyfile:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="001fc-105">Argumenty</span><span class="sxs-lookup"><span data-stu-id="001fc-105">Arguments</span></span>  
 `file`  
 <span data-ttu-id="001fc-106">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="001fc-106">Required.</span></span> <span data-ttu-id="001fc-107">Plik, który zawiera klucz.</span><span class="sxs-lookup"><span data-stu-id="001fc-107">File that contains the key.</span></span> <span data-ttu-id="001fc-108">Jeśli nazwa pliku zawiera spację, nazwę należy ująć w cudzysłów ("").</span><span class="sxs-lookup"><span data-stu-id="001fc-108">If the file name contains a space, enclose the name in quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="001fc-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="001fc-109">Remarks</span></span>  
 <span data-ttu-id="001fc-110">Kompilator wstawia klucz publiczny w manifeście zestawu i podpisuje następnie zestawie końcowym z kluczem prywatnym.</span><span class="sxs-lookup"><span data-stu-id="001fc-110">The compiler inserts the public key into the assembly manifest and then signs the final assembly with the private key.</span></span> <span data-ttu-id="001fc-111">Aby wygenerować plik klucza, wpisz `sn -k file` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="001fc-111">To generate a key file, type `sn -k file` at the command line.</span></span> <span data-ttu-id="001fc-112">Aby uzyskać więcej informacji, zobacz [Sn.exe (narzędzie silnej nazwy)](https://msdn.microsoft.com/library/k5b5tt23).</span><span class="sxs-lookup"><span data-stu-id="001fc-112">For more information, see [Sn.exe (Strong Name Tool)](https://msdn.microsoft.com/library/k5b5tt23).</span></span>  
  
 <span data-ttu-id="001fc-113">Jeśli kompilacji z `/target:module`, nazwa pliku klucza jest przechowywany w module i włączyć do zestawu, który jest tworzony podczas kompilowania zestawu z [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span><span class="sxs-lookup"><span data-stu-id="001fc-113">If you compile with `/target:module`, the name of the key file is held in the module and incorporated into the assembly that is created when you compile an assembly with [/addmodule](../../../visual-basic/reference/command-line-compiler/addmodule.md).</span></span>  
  
 <span data-ttu-id="001fc-114">Można również przekazać do kompilatora z informacjami szyfrowania [/KeyContainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span><span class="sxs-lookup"><span data-stu-id="001fc-114">You can also pass your encryption information to the compiler with [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md).</span></span> <span data-ttu-id="001fc-115">Użyj [/DelaySign](../../../visual-basic/reference/command-line-compiler/delaysign.md) Jeśli chcesz częściowo podpisanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="001fc-115">Use [/delaysign](../../../visual-basic/reference/command-line-compiler/delaysign.md) if you want a partially signed assembly.</span></span>  
  
 <span data-ttu-id="001fc-116">Tę opcję można również określić jako atrybut niestandardowy (<xref:System.Reflection.AssemblyKeyFileAttribute>) w kodzie źródłowym dla każdy moduł język pośredni firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="001fc-116">You can also specify this option as a custom attribute (<xref:System.Reflection.AssemblyKeyFileAttribute>) in the source code for any Microsoft intermediate language module.</span></span>  
  
 <span data-ttu-id="001fc-117">W przypadku obu `/keyfile` i [/KeyContainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) podano (przez opcję wiersza polecenia lub przez atrybut niestandardowy) w tej samej kompilacji, kompilator po raz pierwszy próbuje kontener kluczy.</span><span class="sxs-lookup"><span data-stu-id="001fc-117">In case both `/keyfile` and [/keycontainer](../../../visual-basic/reference/command-line-compiler/keycontainer.md) are specified (either by command-line option or by custom attribute) in the same compilation, the compiler first tries the key container.</span></span> <span data-ttu-id="001fc-118">Jeśli który zakończy się powodzeniem, zestaw jest podpisany z informacjami w kontenerze kluczy.</span><span class="sxs-lookup"><span data-stu-id="001fc-118">If that succeeds, then the assembly is signed with the information in the key container.</span></span> <span data-ttu-id="001fc-119">Jeśli kompilator nie może znaleźć kontener kluczy, spróbuje określić za pomocą pliku `/keyfile`.</span><span class="sxs-lookup"><span data-stu-id="001fc-119">If the compiler does not find the key container, it tries the file specified with `/keyfile`.</span></span> <span data-ttu-id="001fc-120">Jeśli to się powiedzie, zestaw jest podpisany za pomocą informacji w pliku klucza i informacje o kluczu został zainstalowany w kontenerze kluczy (podobnie jak `sn -i`) tak, aby w następnej kompilacji, kontener kluczy będzie nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="001fc-120">If this succeeds, the assembly is signed with the information in the key file, and the key information is installed in the key container (similar to `sn -i`) so that on the next compilation, the key container will be valid.</span></span>  
  
 <span data-ttu-id="001fc-121">Należy pamiętać, że plik klucza może zawierać tylko klucz publiczny.</span><span class="sxs-lookup"><span data-stu-id="001fc-121">Note that a key file might contain only the public key.</span></span>  
  
 <span data-ttu-id="001fc-122">Zobacz [tworzenie i zestawy Using Strong-Named](https://msdn.microsoft.com/library/xwb8f617) Aby uzyskać więcej informacji na temat podpisywania zestawu.</span><span class="sxs-lookup"><span data-stu-id="001fc-122">See [Creating and Using Strong-Named Assemblies](https://msdn.microsoft.com/library/xwb8f617) for more information on signing an assembly.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="001fc-123">`/keyfile` Opcja nie jest dostępne w [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] środowisko projektowe; jest dostępna tylko podczas kompilowania kodu w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="001fc-123">The `/keyfile` option is not available from within the [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] development environment; it is available only when compiling from the command line.</span></span>  
  
## <a name="example"></a><span data-ttu-id="001fc-124">Przykład</span><span class="sxs-lookup"><span data-stu-id="001fc-124">Example</span></span>  
 <span data-ttu-id="001fc-125">Poniższy kod tworzy plik źródłowy `Input.vb` i określa plik klucza.</span><span class="sxs-lookup"><span data-stu-id="001fc-125">The following code compiles source file `Input.vb` and specifies a key file.</span></span>  
  
```  
vbc /keyfile:myfile.sn input.vb  
```  
  
## <a name="see-also"></a><span data-ttu-id="001fc-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="001fc-126">See Also</span></span>  
 [<span data-ttu-id="001fc-127">Zestawy i Globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="001fc-127">Assemblies and the Global Assembly Cache</span></span>](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [<span data-ttu-id="001fc-128">Kompilator w wierszu polecenia programu Visual Basic</span><span class="sxs-lookup"><span data-stu-id="001fc-128">Visual Basic Command-Line Compiler</span></span>](../../../visual-basic/reference/command-line-compiler/index.md)  
 [<span data-ttu-id="001fc-129">/ Reference (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="001fc-129">/reference (Visual Basic)</span></span>](../../../visual-basic/reference/command-line-compiler/reference.md)  
 [<span data-ttu-id="001fc-130">Kompilacja przykładów — wiersze poleceń</span><span class="sxs-lookup"><span data-stu-id="001fc-130">Sample Compilation Command Lines</span></span>](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)