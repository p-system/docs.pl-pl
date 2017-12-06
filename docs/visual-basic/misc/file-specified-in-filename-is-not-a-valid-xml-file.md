---
title: "Plik określony w nazwie pliku nie jest prawidłowym plikiem XML"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: c4c30bf3-e0ad-4bc8-89e0-2c3e49e9793b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: f3275608a1871ac981eb5b3aa39f0be6ab4e758e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="file-specified-in-filename-is-not-a-valid-xml-file"></a><span data-ttu-id="6637e-102">Plik określony w nazwie pliku nie jest prawidłowym plikiem XML</span><span class="sxs-lookup"><span data-stu-id="6637e-102">File specified in FileName is not a valid XML file</span></span>
<span data-ttu-id="6637e-103">Nazwa pliku, który został dostarczony nie jest prawidłowym plikiem XML.</span><span class="sxs-lookup"><span data-stu-id="6637e-103">The file name that you supplied is not a valid XML file.</span></span> <span data-ttu-id="6637e-104">Aby określić dozwolonych struktury i zawartości dokumentu XML, można użyć definicji typu dokumentu (DTD), schemat Microsoft XML-danych (XDR) lub schematu schematu XML definition language (XSD).</span><span class="sxs-lookup"><span data-stu-id="6637e-104">To specify the allowed structure and content of an XML document, you can use a Document Type Definition (DTD), a Microsoft XML-Data Reduced (XDR) schema, or an XML Schema definition language (XSD) schema.</span></span> <span data-ttu-id="6637e-105">Schematy XSD jest preferowany sposób, aby określić gramatyki XML w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="6637e-105">XSD schemas are the preferred way to specify XML grammars in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="6637e-106">W niektórych wcześniejszych wersjach programu Visual Studio **Projektant XML** jest Projektant typizowane zbiory danych i schemat XML.</span><span class="sxs-lookup"><span data-stu-id="6637e-106">In some earlier versions of Visual Studio, the **XML Designer** is the designer for typed datasets and XML schema.</span></span> <span data-ttu-id="6637e-107">**Projektant XML** nadal można tworzyć i edytować pliki schematów XML.</span><span class="sxs-lookup"><span data-stu-id="6637e-107">The **XML Designer** can still be used to create and edit XML schema files.</span></span> <span data-ttu-id="6637e-108">Jednak w [!INCLUDE[vs_current_long](~/includes/vs-current-long-md.md)], Projektant tworzenia i edytowania typizowane zbiory danych **Projektant obiektów Dataset**.</span><span class="sxs-lookup"><span data-stu-id="6637e-108">However, in [!INCLUDE[vs_current_long](~/includes/vs-current-long-md.md)], the designer for creating and editing typed datasets is the **Dataset Designer**.</span></span> <span data-ttu-id="6637e-109">Aby uzyskać więcej informacji, zobacz [tworzenie i edytowanie wpisanych zestawów danych](/visualstudio/data-tools/creating-and-editing-typed-datasets).</span><span class="sxs-lookup"><span data-stu-id="6637e-109">For more information, see [Creating and Editing Typed Datasets](/visualstudio/data-tools/creating-and-editing-typed-datasets).</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="6637e-110">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="6637e-110">To correct this error</span></span>  
  
-   <span data-ttu-id="6637e-111">Sprawdź, czy są podawania poprawnej nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="6637e-111">Check that you are supplying the correct file name.</span></span>  
  
-   <span data-ttu-id="6637e-112">Sprawdź, czy określony plik zawiera prawidłowy kod XML przez ładowanie pliku XML, który chcesz sprawdzić do **Projektant XML**.</span><span class="sxs-lookup"><span data-stu-id="6637e-112">Check that the specified file contains valid XML by loading the XML file that you want to check into the **XML Designer**.</span></span> <span data-ttu-id="6637e-113">Z **XML** menu, kliknij przycisk **zweryfikować XML**.</span><span class="sxs-lookup"><span data-stu-id="6637e-113">From the **XML** menu, click **Validate XML**.</span></span> <span data-ttu-id="6637e-114">Błędy są wyświetlane w **listy zadań**.</span><span class="sxs-lookup"><span data-stu-id="6637e-114">Errors are displayed in the **Task List**.</span></span>  
  
-   <span data-ttu-id="6637e-115">Jeśli plik XML ma skojarzony schemat XML, sprawdź, czy elementy są widoczne w zdefiniowanej strukturze i że zawartość poszczególnych elementów zgodne typy zadeklarowane danych określonej w schemacie.</span><span class="sxs-lookup"><span data-stu-id="6637e-115">If the XML file has an associated XML Schema, check that the elements appear in the defined structure and that the content of the individual elements conforms to the declared data types specified in the schema.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6637e-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6637e-116">See Also</span></span>  
 <xref:System.Xml>  
 [<span data-ttu-id="6637e-117">Porady: analizowanie ścieżek pliku</span><span class="sxs-lookup"><span data-stu-id="6637e-117">How to: Parse File Paths</span></span>](../../visual-basic/developing-apps/programming/drives-directories-files/how-to-parse-file-paths.md)