---
title: "Kopiowanie istniejących węzłów z jednego dokumentu do innego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3caa78c1-3448-4b7b-b83c-228ee857635e
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 0f20e5bd595c8eb49360e58f281a8cf6eda89acf
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="copying-existing-nodes-from-one-document-to-another"></a><span data-ttu-id="456e3-102">Kopiowanie istniejących węzłów z jednego dokumentu do innego</span><span class="sxs-lookup"><span data-stu-id="456e3-102">Copying Existing Nodes from One Document to Another</span></span>
<span data-ttu-id="456e3-103">**ImportNode** metody to mechanizm, za pomocą którego węzeł lub całego węzła poddrzewo zostaną skopiowane z jednego **XmlDocument** na inny.</span><span class="sxs-lookup"><span data-stu-id="456e3-103">The **ImportNode** method is the mechanism by which a node or entire node subtree is copied from one **XmlDocument** to another.</span></span> <span data-ttu-id="456e3-104">Węzeł zwracana z wywołania jest kopią węzła w dokumencie źródłowym, w tym wartości atrybutów, nazwa węzła typu węzła i wszystkie atrybuty związane z przestrzeni nazw, takie jak prefiks, nazwę lokalną i przestrzeń nazw identyfikatora URI (Uniform Resource).</span><span class="sxs-lookup"><span data-stu-id="456e3-104">The node returned from the call is a copy of the node from the source document, including attribute values, the node name, node type, and all namespace-related attributes such as the prefix, local name, and namespace Uniform Resource Identifier (URI).</span></span> <span data-ttu-id="456e3-105">Dokument źródłowy nie zostanie zmieniona.</span><span class="sxs-lookup"><span data-stu-id="456e3-105">The source document is not changed.</span></span> <span data-ttu-id="456e3-106">Po zaimportowaniu tego węzła, musisz dodać je do drzewa przy użyciu jednej z metod służy do wstawiania węzłów.</span><span class="sxs-lookup"><span data-stu-id="456e3-106">After you have imported the node, you still have to add it to the tree using one of the methods used to insert nodes.</span></span>  
  
 <span data-ttu-id="456e3-107">Gdy węzeł jest dołączony do jego nowy dokument, nowy dokument jest właścicielem tego węzła.</span><span class="sxs-lookup"><span data-stu-id="456e3-107">When the node is attached to its new document, the new document owns the node.</span></span> <span data-ttu-id="456e3-108">Przyczyną jest podczas tworzenia każdego węzła dokument będący właścicielem, nawet jeśli węzły są tworzone w fragmenty innego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="456e3-108">The reason is that each node, when created, has an owning document, even if the nodes are created in separate document fragments.</span></span> <span data-ttu-id="456e3-109">Jest wymaganie od XML modelu DOM (Document Object) i są wymuszane przez projekt tworzenie fabryki na **XmlDocument** klasy.</span><span class="sxs-lookup"><span data-stu-id="456e3-109">This is a requirement of the XML Document Object Model (DOM) and is enforced by the factory creation design on the **XmlDocument** class.</span></span> <span data-ttu-id="456e3-110">Na przykład **funkcji CreateElement**, jest to jedyny sposób, aby utworzyć nowe węzły.</span><span class="sxs-lookup"><span data-stu-id="456e3-110">For example, **CreateElement**, is the only way to create new nodes.</span></span>  
  
 <span data-ttu-id="456e3-111">W zależności od typu węzła importowanych węzła i wartość *głębokie* parametru, dodatkowe informacje są kopiowane jako odpowiednie.</span><span class="sxs-lookup"><span data-stu-id="456e3-111">Depending on the node type of the imported node and the value of the *deep* parameter, additional information is copied as appropriate.</span></span> <span data-ttu-id="456e3-112">Ta metoda próbuje duplikatów zachowanie oczekiwane, jeśli fragment XML lub źródła HTML został skopiowany z jednego dokumentu do innego dla faktów, XML, dwa dokumenty może mieć innego dokumentu definicje typów (elementów DTD).</span><span class="sxs-lookup"><span data-stu-id="456e3-112">This method attempts to mirror the behavior expected if a fragment of XML or HTML source was copied from one document to another, accounting for the fact that for XML, the two documents may have different document type definitions (DTDs).</span></span>  
  
 <span data-ttu-id="456e3-113">W poniższej tabeli opisano określone zachowanie dla każdego typu węzła, który można zaimportować.</span><span class="sxs-lookup"><span data-stu-id="456e3-113">The following table describes the specific behavior for each type of node that can be imported.</span></span>  
  
|<span data-ttu-id="456e3-114">Typ węzła</span><span class="sxs-lookup"><span data-stu-id="456e3-114">Node Type</span></span>|<span data-ttu-id="456e3-115">*głębokie* parametr ma wartość true</span><span class="sxs-lookup"><span data-stu-id="456e3-115">*deep* parameter is true</span></span>|<span data-ttu-id="456e3-116">*głębokie* parametr ma wartość false</span><span class="sxs-lookup"><span data-stu-id="456e3-116">*deep* parameter is false</span></span>|  
|---------------|------------------------------|-------------------------------|  
|<span data-ttu-id="456e3-117">Element XmlAttribute</span><span class="sxs-lookup"><span data-stu-id="456e3-117">XmlAttribute</span></span>|<span data-ttu-id="456e3-118"><xref:System.Xml.XmlAttribute.Specified%2A> Ustawiono **true** na XmlAttribute.</span><span class="sxs-lookup"><span data-stu-id="456e3-118">The <xref:System.Xml.XmlAttribute.Specified%2A> is set to **true** on the XmlAttribute.</span></span> <span data-ttu-id="456e3-119">Elementy podrzędne źródła **XmlAttribute** rekursywnie zaimportowane i wynikowy węzły są odbierane do utworzenia odpowiedniego poddrzewa.</span><span class="sxs-lookup"><span data-stu-id="456e3-119">The descendants of the source **XmlAttribute** are recursively imported and the resulting nodes reassembled to form the corresponding subtree.</span></span>|<span data-ttu-id="456e3-120">*Głębokie* parametru nie ma zastosowania do **XmlAttribute** węzłów, ponieważ zawierają one ich węzłów podrzędnych z nimi po zaimportowaniu.</span><span class="sxs-lookup"><span data-stu-id="456e3-120">The *deep* parameter does not apply to **XmlAttribute** nodes, because they always carry their child nodes with them when imported.</span></span>|  
|<span data-ttu-id="456e3-121">XmlCDataSection</span><span class="sxs-lookup"><span data-stu-id="456e3-121">XmlCDataSection</span></span>|<span data-ttu-id="456e3-122">Kopiuje węzła, w tym jego dane.</span><span class="sxs-lookup"><span data-stu-id="456e3-122">Copies the node, including its data.</span></span>|<span data-ttu-id="456e3-123">Kopiuje węzła, w tym jego dane.</span><span class="sxs-lookup"><span data-stu-id="456e3-123">Copies the node, including its data.</span></span>|  
|<span data-ttu-id="456e3-124">XmlComment</span><span class="sxs-lookup"><span data-stu-id="456e3-124">XmlComment</span></span>|<span data-ttu-id="456e3-125">Kopiuje węzła, w tym jego dane.</span><span class="sxs-lookup"><span data-stu-id="456e3-125">Copies the node, including its data.</span></span>|<span data-ttu-id="456e3-126">Kopiuje węzła, w tym jego dane.</span><span class="sxs-lookup"><span data-stu-id="456e3-126">Copies the node, including its data.</span></span>|  
|<span data-ttu-id="456e3-127">XmlDocumentFragment</span><span class="sxs-lookup"><span data-stu-id="456e3-127">XmlDocumentFragment</span></span>|<span data-ttu-id="456e3-128">Elementów podrzędnych węzła źródłowego są rekursywnie zaimportowane i wynikowy węzłów odbierane do utworzenia odpowiedniego poddrzewa.</span><span class="sxs-lookup"><span data-stu-id="456e3-128">The descendants of the source node are recursively imported and the resulting nodes reassembled to form the corresponding subtree.</span></span>|<span data-ttu-id="456e3-129">Pusta **XmlDocumentFragment** jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="456e3-129">An empty **XmlDocumentFragment** is created.</span></span>|  
|<span data-ttu-id="456e3-130">XmlDocumentType</span><span class="sxs-lookup"><span data-stu-id="456e3-130">XmlDocumentType</span></span>|<span data-ttu-id="456e3-131">Kopiuje węzła, w tym jego data.*</span><span class="sxs-lookup"><span data-stu-id="456e3-131">Copies the node, including its data.*</span></span>|<span data-ttu-id="456e3-132">Kopiuje węzła, w tym jego data.*</span><span class="sxs-lookup"><span data-stu-id="456e3-132">Copies the node, including its data.*</span></span>|  
|<span data-ttu-id="456e3-133">Element XmlElement</span><span class="sxs-lookup"><span data-stu-id="456e3-133">XmlElement</span></span>|<span data-ttu-id="456e3-134">Elementy podrzędne elementu źródła są rekursywnie zaimportowane i wynikowy węzłów odbierane do utworzenia odpowiedniego poddrzewa.</span><span class="sxs-lookup"><span data-stu-id="456e3-134">The descendants of the source element are recursively imported and the resulting nodes reassembled to form the corresponding subtree.</span></span> <span data-ttu-id="456e3-135">**Uwaga:** domyślne atrybuty nie są kopiowane.</span><span class="sxs-lookup"><span data-stu-id="456e3-135">**Note:**  Default attributes are not copied.</span></span> <span data-ttu-id="456e3-136">Jeśli importowany do dokumentu definiuje domyślne atrybuty dla tej nazwy elementu, te są przypisane.</span><span class="sxs-lookup"><span data-stu-id="456e3-136">If the document being imported into defines default attributes for this element name, those are assigned.</span></span>|<span data-ttu-id="456e3-137">Określony atrybut węzły elementu źródłowego zostały zaimportowane i wygenerowany **XmlAttribute** węzły są dołączone do nowego elementu.</span><span class="sxs-lookup"><span data-stu-id="456e3-137">Specified attribute nodes of the source element are imported, and the generated **XmlAttribute** nodes are attached to the new element.</span></span> <span data-ttu-id="456e3-138">Węzły podrzędne nie są kopiowane.</span><span class="sxs-lookup"><span data-stu-id="456e3-138">The descendant nodes are not copied.</span></span> <span data-ttu-id="456e3-139">**Uwaga:** domyślne atrybuty nie są kopiowane.</span><span class="sxs-lookup"><span data-stu-id="456e3-139">**Note:**  Default attributes are not copied.</span></span> <span data-ttu-id="456e3-140">Jeśli importowany do dokumentu definiuje domyślne atrybuty dla tej nazwy elementu, te są przypisane.</span><span class="sxs-lookup"><span data-stu-id="456e3-140">If the document being imported into defines default attributes for this element name, those are assigned.</span></span>|  
|<span data-ttu-id="456e3-141">XmlEntityReference</span><span class="sxs-lookup"><span data-stu-id="456e3-141">XmlEntityReference</span></span>|<span data-ttu-id="456e3-142">Ponieważ dokumenty źródłowy i docelowy mogą mieć jednostek określony inaczej, ta metoda tylko kopiuje **XmlEntityReference** węzła.</span><span class="sxs-lookup"><span data-stu-id="456e3-142">Because the source and destination documents could have the entities defined differently, this method only copies the **XmlEntityReference** node.</span></span> <span data-ttu-id="456e3-143">Tekst zastępczy nie jest włączony.</span><span class="sxs-lookup"><span data-stu-id="456e3-143">The replacement text is not included.</span></span> <span data-ttu-id="456e3-144">Jeśli plik docelowy ma jednostki zdefiniowane, jego wartość jest przypisany.</span><span class="sxs-lookup"><span data-stu-id="456e3-144">If the destination document has the entity defined, its value is assigned.</span></span>|<span data-ttu-id="456e3-145">Ponieważ dokumenty źródłowy i docelowy mogą mieć jednostek określony inaczej, ta metoda tylko kopiuje **XmlEntityReference** węzła.</span><span class="sxs-lookup"><span data-stu-id="456e3-145">Because the source and destination documents could have the entities defined differently, this method only copies the **XmlEntityReference** node.</span></span> <span data-ttu-id="456e3-146">Tekst zastępczy nie jest włączony.</span><span class="sxs-lookup"><span data-stu-id="456e3-146">The replacement text is not included.</span></span> <span data-ttu-id="456e3-147">Jeśli plik docelowy ma jednostki zdefiniowane, jego wartość jest przypisany.</span><span class="sxs-lookup"><span data-stu-id="456e3-147">If the destination document has the entity defined, its value is assigned.</span></span>|  
|<span data-ttu-id="456e3-148">XmlProcessingInstruction</span><span class="sxs-lookup"><span data-stu-id="456e3-148">XmlProcessingInstruction</span></span>|<span data-ttu-id="456e3-149">Kopiuje wartości docelowej i danych z węzła zaimportowany.</span><span class="sxs-lookup"><span data-stu-id="456e3-149">Copies the target and data value from the imported node.</span></span>|<span data-ttu-id="456e3-150">Kopiuje wartości docelowej i danych z węzła zaimportowany.</span><span class="sxs-lookup"><span data-stu-id="456e3-150">Copies the target and data value from the imported node.</span></span>|  
|<span data-ttu-id="456e3-151">XmlText</span><span class="sxs-lookup"><span data-stu-id="456e3-151">XmlText</span></span>|<span data-ttu-id="456e3-152">Kopiuje węzła, w tym jego dane.</span><span class="sxs-lookup"><span data-stu-id="456e3-152">Copies the node, including its data.</span></span>|<span data-ttu-id="456e3-153">Kopiuje węzła, w tym jego dane.</span><span class="sxs-lookup"><span data-stu-id="456e3-153">Copies the node, including its data.</span></span>|  
|<span data-ttu-id="456e3-154">XmlSignificantWhitespace</span><span class="sxs-lookup"><span data-stu-id="456e3-154">XmlSignificantWhitespace</span></span>|<span data-ttu-id="456e3-155">Kopiuje węzła, w tym jego dane.</span><span class="sxs-lookup"><span data-stu-id="456e3-155">Copies the node, including its data.</span></span>|<span data-ttu-id="456e3-156">Kopiuje węzła, w tym jego dane.</span><span class="sxs-lookup"><span data-stu-id="456e3-156">Copies the node, including its data.</span></span>|  
|<span data-ttu-id="456e3-157">XmlWhitespace</span><span class="sxs-lookup"><span data-stu-id="456e3-157">XmlWhitespace</span></span>|<span data-ttu-id="456e3-158">Kopiuje węzła, w tym jego dane.</span><span class="sxs-lookup"><span data-stu-id="456e3-158">Copies the node, including its data.</span></span>|<span data-ttu-id="456e3-159">Kopiuje węzła, w tym jego dane.</span><span class="sxs-lookup"><span data-stu-id="456e3-159">Copies the node, including its data.</span></span>|  
|<span data-ttu-id="456e3-160">XmlDeclaration</span><span class="sxs-lookup"><span data-stu-id="456e3-160">XmlDeclaration</span></span>|<span data-ttu-id="456e3-161">Kopiuje wartości docelowej i danych z węzła zaimportowany.</span><span class="sxs-lookup"><span data-stu-id="456e3-161">Copies the target and data value from the imported node.</span></span>|<span data-ttu-id="456e3-162">Kopiuje wartości docelowej i danych z węzła zaimportowany.</span><span class="sxs-lookup"><span data-stu-id="456e3-162">Copies the target and data value from the imported node.</span></span>|  
|<span data-ttu-id="456e3-163">Wszystkie inne typy węzła</span><span class="sxs-lookup"><span data-stu-id="456e3-163">All other node types</span></span>|<span data-ttu-id="456e3-164">Nie można zaimportować typu węzła.</span><span class="sxs-lookup"><span data-stu-id="456e3-164">These node types cannot be imported.</span></span>|<span data-ttu-id="456e3-165">Nie można zaimportować typu węzła.</span><span class="sxs-lookup"><span data-stu-id="456e3-165">These node types cannot be imported.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="456e3-166">Mimo że można zaimportować węzłów dokumentu, dokument może mieć tylko jeden typ dokumentu.</span><span class="sxs-lookup"><span data-stu-id="456e3-166">Although DocumentType nodes can be imported, a document can only have one DocumentType.</span></span> <span data-ttu-id="456e3-167">Dlatego po zaimportowaniu typu dokumentu przed wstawieniem do drzewa, musisz upewnić się, że nie ma dokumentu typu w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="456e3-167">So, once you have imported the document type, before inserting it into tree you have to make sure that there is no document type in the document.</span></span> <span data-ttu-id="456e3-168">Aby uzyskać informacje dotyczące usuwania węzłów, zobacz [wartości z dokumentu XML, zawartość i usuwanie węzłów](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span><span class="sxs-lookup"><span data-stu-id="456e3-168">For information on removing nodes, see [Removing Nodes, Content, and Values from an XML Document](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="456e3-169">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="456e3-169">See Also</span></span>  
 [<span data-ttu-id="456e3-170">Modelu obiektu dokumentu XML modelu DOM)</span><span class="sxs-lookup"><span data-stu-id="456e3-170">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)