---
title: DataSets
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 037f3991-7bbc-424b-b52e-8b03585d3e34
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: ff43b9279130ed710d9d88cbf2ba5ead4a6f0ebc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="diffgrams"></a><span data-ttu-id="13fa6-102">DataSets</span><span class="sxs-lookup"><span data-stu-id="13fa6-102">DiffGrams</span></span>
<span data-ttu-id="13fa6-103">Elementu DiffGram jest w formacie XML, który identyfikuje bieżące i oryginalne wersje elementów danych.</span><span class="sxs-lookup"><span data-stu-id="13fa6-103">A DiffGram is an XML format that identifies current and original versions of data elements.</span></span> <span data-ttu-id="13fa6-104"><xref:System.Data.DataSet> Używa formatu elementu DiffGram do ładowania i utrwalić jego zawartość, a do serializacji jego zawartość dla transportu przez połączenie sieciowe.</span><span class="sxs-lookup"><span data-stu-id="13fa6-104">The <xref:System.Data.DataSet> uses the DiffGram format to load and persist its contents, and to serialize its contents for transport across a network connection.</span></span> <span data-ttu-id="13fa6-105">Gdy <xref:System.Data.DataSet> są zapisywane jako elementu DiffGram wypełnia elementu DiffGram niezbędne informacje, aby dokładnie odtworzyć zawartość, jednak nie schematu z <xref:System.Data.DataSet>, łącznie z obu wartości w kolumnie **oryginalne** i **bieżącego** wersje wiersza, informacje o błędzie wiersza i kolejności wierszy.</span><span class="sxs-lookup"><span data-stu-id="13fa6-105">When a <xref:System.Data.DataSet> is written as a DiffGram, it populates the DiffGram with all the necessary information to accurately recreate the contents, though not the schema, of the <xref:System.Data.DataSet>, including column values from both the **Original** and **Current** row versions, row error information, and row order.</span></span>  
  
 <span data-ttu-id="13fa6-106">Podczas wysyłania i pobierania <xref:System.Data.DataSet> z usługi XML sieci Web niejawnie używany jest format elementu DiffGram.</span><span class="sxs-lookup"><span data-stu-id="13fa6-106">When sending and retrieving a <xref:System.Data.DataSet> from an XML Web service, the DiffGram format is implicitly used.</span></span> <span data-ttu-id="13fa6-107">Ponadto podczas ładowania zawartości <xref:System.Data.DataSet> z XML za pomocą **ReadXml** metody, lub podczas zapisywania zawartości <xref:System.Data.DataSet> za pomocą XML **WriteXml** metody, można określić czy zawartość odczytu lub zapisu jako elementu DiffGram.</span><span class="sxs-lookup"><span data-stu-id="13fa6-107">Additionally, when loading the contents of a <xref:System.Data.DataSet> from XML using the **ReadXml** method, or when writing the contents of a <xref:System.Data.DataSet> in XML using the **WriteXml** method, you can specify that the contents be read or written as a DiffGram.</span></span> <span data-ttu-id="13fa6-108">Aby uzyskać więcej informacji, zobacz [podczas ładowania zestawu danych z pliku XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) i [zapisywanie zawartości zestawu danych jako dane XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span><span class="sxs-lookup"><span data-stu-id="13fa6-108">For more information, see [Loading a DataSet from XML](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md) and [Writing DataSet Contents as XML Data](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md).</span></span>  
  
 <span data-ttu-id="13fa6-109">Format elementu DiffGram jest głównie używane w programie .NET Framework jako formatu serializacji zawartości <xref:System.Data.DataSet>, umożliwia także DataSets zmodyfikować dane w tabelach w bazie danych programu Microsoft SQL Server.</span><span class="sxs-lookup"><span data-stu-id="13fa6-109">While the DiffGram format is primarily used by the .NET Framework as a serialization format for the contents of a <xref:System.Data.DataSet>, you can also use DiffGrams to modify data in tables in a Microsoft SQL Server database.</span></span>  
  
 <span data-ttu-id="13fa6-110">Elementu Diffgram jest generowany przez zapisywanie zawartości wszystkich tabel do  **\<elementu diffgram >** elementu.</span><span class="sxs-lookup"><span data-stu-id="13fa6-110">A Diffgram is generated by writing the contents of all tables to a **\<diffgram>** element.</span></span>  
  
### <a name="to-generate-a-diffgram"></a><span data-ttu-id="13fa6-111">Aby wygenerować obiektu Diffgram</span><span class="sxs-lookup"><span data-stu-id="13fa6-111">To generate a Diffgram</span></span>  
  
1.  <span data-ttu-id="13fa6-112">Generowanie listy tabel głównego (to znaczy tabele bez żadnych nadrzędnego).</span><span class="sxs-lookup"><span data-stu-id="13fa6-112">Generate a list of Root tables (that is, tables without any parent).</span></span>  
  
2.  <span data-ttu-id="13fa6-113">Dla każdej tabeli i jego elementy podrzędne na liście zapisać bieżącą wersję wszystkich wierszy w pierwszej sekcji elementu Diffgram.</span><span class="sxs-lookup"><span data-stu-id="13fa6-113">For each table and its descendants in the list, write out the current version of all rows in the first Diffgram section.</span></span>  
  
3.  <span data-ttu-id="13fa6-114">Dla każdej tabeli w <xref:System.Data.DataSet>, Zapisz oryginalnej wersji wszystkie wiersze w  **\<przed >** części elementu Diffgram.</span><span class="sxs-lookup"><span data-stu-id="13fa6-114">For each table in the <xref:System.Data.DataSet>, write out the original version of all rows, if any, in the **\<before>** section of the Diffgram.</span></span>  
  
4.  <span data-ttu-id="13fa6-115">Dla wierszy zawierających błędy zapisu zawartości w błąd  **\<błędy >** części elementu Diffgram.</span><span class="sxs-lookup"><span data-stu-id="13fa6-115">For rows that have errors, write the error content in the **\<errors>** section of the Diffgram.</span></span>  
  
 <span data-ttu-id="13fa6-116">Elementu Diffgram są przetwarzane w kolejności od początku pliku XML na końcu.</span><span class="sxs-lookup"><span data-stu-id="13fa6-116">A Diffgram is processed in order from beginning of the XML file to the end.</span></span>  
  
### <a name="to-process-a-diffgram"></a><span data-ttu-id="13fa6-117">Do elementu Diffgram procesu</span><span class="sxs-lookup"><span data-stu-id="13fa6-117">To process a Diffgram</span></span>  
  
1.  <span data-ttu-id="13fa6-118">Proces w pierwszej sekcji elementu Diffgram, zawierający bieżącą wersję wierszy.</span><span class="sxs-lookup"><span data-stu-id="13fa6-118">Process the first section of the Diffgram that contains the current version of the rows.</span></span>  
  
2.  <span data-ttu-id="13fa6-119">Przetwarzanie drugi lub  **\<przed >** sekcję zawierającą z oryginalną wersją wiersza zmodyfikowane i usuniętych wierszy.</span><span class="sxs-lookup"><span data-stu-id="13fa6-119">Process the second or the **\<before>** section that contains the original row version of modified and deleted rows.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="13fa6-120">Jeśli wiersz jest oznaczony jako usunięte, operacja usuwania można usunąć wiersza elementy podrzędne również, w zależności od `Cascade` właściwości bieżącego <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="13fa6-120">If a row is marked deleted, the delete operation can delete the row's descendants as well, depending on the `Cascade` property of the current <xref:System.Data.DataSet>.</span></span>  
  
3.  <span data-ttu-id="13fa6-121">Proces  **\<błędy >** sekcji.</span><span class="sxs-lookup"><span data-stu-id="13fa6-121">Process the **\<errors>** section.</span></span> <span data-ttu-id="13fa6-122">Ustaw informacje o błędzie dla określonych wiersza i kolumny dla każdego elementu w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="13fa6-122">Set the error information for the specified row and column for each item in this section.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="13fa6-123">Jeśli ustawisz <xref:System.Data.XmlWriteMode> do elementu Diffgram, zawartość elementu docelowego <xref:System.Data.DataSet> i oryginalny <xref:System.Data.DataSet> mogą się różnić.</span><span class="sxs-lookup"><span data-stu-id="13fa6-123">If you set the <xref:System.Data.XmlWriteMode> to Diffgram, the content of the target <xref:System.Data.DataSet> and the original <xref:System.Data.DataSet> may differ.</span></span>  
  
## <a name="diffgram-format"></a><span data-ttu-id="13fa6-124">Format elementu DiffGram</span><span class="sxs-lookup"><span data-stu-id="13fa6-124">DiffGram Format</span></span>  
 <span data-ttu-id="13fa6-125">Format elementu DiffGram jest podzielone na trzy części: bieżące dane, oryginalne (lub "przed") danych i sekcji błędy, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="13fa6-125">The DiffGram format is divided into three sections: the current data, the original (or "before") data, and an errors section, as shown in the following example.</span></span>  
  
```xml  
<?xml version="1.0"?>  
<diffgr:diffgram   
         xmlns:msdata="urn:schemas-microsoft-com:xml-msdata"  
         xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1"  
         xmlns:xsd="http://www.w3.org/2001/XMLSchema">  
  
   <DataInstance>  
   </DataInstance>  
  
  <diffgr:before>  
  </diffgr:before>  
  
  <diffgr:errors>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
 <span data-ttu-id="13fa6-126">Format elementu DiffGram składa się z następujących bloków danych:</span><span class="sxs-lookup"><span data-stu-id="13fa6-126">The DiffGram format consists of the following blocks of data:</span></span>  
  
 <span data-ttu-id="13fa6-127">**\<**  ***DataInstance***  **>**</span><span class="sxs-lookup"><span data-stu-id="13fa6-127">**\<**  ***DataInstance***  **>**</span></span>  
 <span data-ttu-id="13fa6-128">Nazwa tego elementu ***DataInstance***, jest używana do celów wyjaśnienie w niniejszej dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="13fa6-128">The name of this element, ***DataInstance***, is used for explanation purposes in this documentation.</span></span> <span data-ttu-id="13fa6-129">A ***DataInstance*** reprezentuje element <xref:System.Data.DataSet> lub wiersz <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="13fa6-129">A ***DataInstance*** element represents a <xref:System.Data.DataSet> or a row of a <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="13fa6-130">Zamiast *DataInstance*, zawiera nazwę elementu <xref:System.Data.DataSet> lub <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="13fa6-130">Instead of *DataInstance*, the element would contain the name of the <xref:System.Data.DataSet> or <xref:System.Data.DataTable>.</span></span> <span data-ttu-id="13fa6-131">Ten blok format elementu DiffGram zawiera bieżące dane, czy został on zmodyfikowany lub nie.</span><span class="sxs-lookup"><span data-stu-id="13fa6-131">This block of the DiffGram format contains the current data, whether it has been modified or not.</span></span> <span data-ttu-id="13fa6-132">Element lub wiersza, który został zmodyfikowany, jest oznaczone symbolem **diffgr:hasChanges** adnotacji.</span><span class="sxs-lookup"><span data-stu-id="13fa6-132">An element, or row, that has been modified is identified with the **diffgr:hasChanges** annotation.</span></span>  
  
 <span data-ttu-id="13fa6-133">**\<diffgr: przed >**</span><span class="sxs-lookup"><span data-stu-id="13fa6-133">**\<diffgr:before>**</span></span>  
 <span data-ttu-id="13fa6-134">Ten blok format elementu DiffGram zawiera oryginalnej wersji wiersza.</span><span class="sxs-lookup"><span data-stu-id="13fa6-134">This block of the DiffGram format contains the original version of a row.</span></span> <span data-ttu-id="13fa6-135">Elementy w tym bloku są dopasowywane do elementów w ***DataInstance*** zablokowane, używając **diffgr:id** adnotacji.</span><span class="sxs-lookup"><span data-stu-id="13fa6-135">Elements in this block are matched to elements in the ***DataInstance*** block using the **diffgr:id** annotation.</span></span>  
  
 <span data-ttu-id="13fa6-136">**\<diffgr:errors >**</span><span class="sxs-lookup"><span data-stu-id="13fa6-136">**\<diffgr:errors>**</span></span>  
 <span data-ttu-id="13fa6-137">Ten blok format elementu DiffGram zawiera informacje o błędzie dla danego wiersza w ***DataInstance*** bloku.</span><span class="sxs-lookup"><span data-stu-id="13fa6-137">This block of the DiffGram format contains error information for a particular row in the ***DataInstance*** block.</span></span> <span data-ttu-id="13fa6-138">Elementy w tym bloku są dopasowywane do elementów w ***DataInstance*** zablokowane, używając **diffgr:id** adnotacji.</span><span class="sxs-lookup"><span data-stu-id="13fa6-138">Elements in this block are matched to elements in the ***DataInstance*** block using the **diffgr:id** annotation.</span></span>  
  
## <a name="diffgram-annotations"></a><span data-ttu-id="13fa6-139">Adnotacje elementu DiffGram</span><span class="sxs-lookup"><span data-stu-id="13fa6-139">DiffGram Annotations</span></span>  
 <span data-ttu-id="13fa6-140">DataSets użyć kilku adnotacje do powiązania elementów z innego elementu DiffGram bloki wersje innego wiersza lub informacje o błędzie w <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="13fa6-140">DiffGrams use several annotations to relate elements from the different DiffGram blocks that represent different row versions or error information in the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="13fa6-141">W poniższej tabeli opisano adnotacje elementu DiffGram, które są zdefiniowane w przestrzeni nazw elementu DiffGram **urn: schemas-microsoft-com: XML-elementu diffgram-v1**.</span><span class="sxs-lookup"><span data-stu-id="13fa6-141">The following table describes the DiffGram annotations that are defined in the DiffGram namespace **urn:schemas-microsoft-com:xml-diffgram-v1**.</span></span>  
  
|<span data-ttu-id="13fa6-142">Adnotacja</span><span class="sxs-lookup"><span data-stu-id="13fa6-142">Annotation</span></span>|<span data-ttu-id="13fa6-143">Opis</span><span class="sxs-lookup"><span data-stu-id="13fa6-143">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="13fa6-144">**Identyfikator**</span><span class="sxs-lookup"><span data-stu-id="13fa6-144">**id**</span></span>|<span data-ttu-id="13fa6-145">Używany do elementów w parę  **\<diffgr: przed >** i  **\<diffgr:errors >** bloków do elementów w  **\<**  ***DataInstance***  **>**  bloku.</span><span class="sxs-lookup"><span data-stu-id="13fa6-145">Used to pair the elements in the **\<diffgr:before>** and **\<diffgr:errors>** blocks to elements in the **\<** ***DataInstance*** **>** block.</span></span> <span data-ttu-id="13fa6-146">Wartości z **diffgr:id** adnotacji mają postać *[Nazwa_tabeli] [RowIdentifier]*.</span><span class="sxs-lookup"><span data-stu-id="13fa6-146">Values with the **diffgr:id** annotation are in the form *[TableName][RowIdentifier]*.</span></span> <span data-ttu-id="13fa6-147">Na przykład: `<Customers diffgr:id="Customers1">`.</span><span class="sxs-lookup"><span data-stu-id="13fa6-147">For example: `<Customers diffgr:id="Customers1">`.</span></span>|  
|<span data-ttu-id="13fa6-148">**Parametr parentId**</span><span class="sxs-lookup"><span data-stu-id="13fa6-148">**parentId**</span></span>|<span data-ttu-id="13fa6-149">Identyfikuje element, który z  **\<**  ***DataInstance***  **>**  bloku jest elementem nadrzędnym bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="13fa6-149">Identifies which element from the **\<** ***DataInstance*** **>** block is the parent element of the current element.</span></span> <span data-ttu-id="13fa6-150">Wartości z **diffgr:parentId** adnotacji mają postać *[Nazwa_tabeli] [RowIdentifier]*.</span><span class="sxs-lookup"><span data-stu-id="13fa6-150">Values with the **diffgr:parentId** annotation are in the form *[TableName][RowIdentifier]*.</span></span> <span data-ttu-id="13fa6-151">Na przykład: `<Orders diffgr:parentId="Customers1">`.</span><span class="sxs-lookup"><span data-stu-id="13fa6-151">For example: `<Orders diffgr:parentId="Customers1">`.</span></span>|  
|<span data-ttu-id="13fa6-152">**hasChanges**</span><span class="sxs-lookup"><span data-stu-id="13fa6-152">**hasChanges**</span></span>|<span data-ttu-id="13fa6-153">Identyfikuje wiersz w  **\<**  ***DataInstance***  **>**  zablokować zmienione.</span><span class="sxs-lookup"><span data-stu-id="13fa6-153">Identifies a row in the **\<** ***DataInstance*** **>** block as modified.</span></span> <span data-ttu-id="13fa6-154">**HasChanges** adnotacji może mieć jedną z następujących dwóch wartości:</span><span class="sxs-lookup"><span data-stu-id="13fa6-154">The **hasChanges** annotation can have one of the following two values:</span></span><br /><br /> <span data-ttu-id="13fa6-155">**dodaje**</span><span class="sxs-lookup"><span data-stu-id="13fa6-155">**inserted**</span></span><br /> <span data-ttu-id="13fa6-156">Identyfikuje **Added** wiersza.</span><span class="sxs-lookup"><span data-stu-id="13fa6-156">Identifies an **Added** row.</span></span><br /><br /> <span data-ttu-id="13fa6-157">**zmodyfikowane**</span><span class="sxs-lookup"><span data-stu-id="13fa6-157">**modified**</span></span><br /> <span data-ttu-id="13fa6-158">Identyfikuje **zmodyfikowane** wiersza, który zawiera **oryginalnego** wersja wiersza w  **\<diffgr: przed >** bloku.</span><span class="sxs-lookup"><span data-stu-id="13fa6-158">Identifies a **Modified** row that contains an **Original** row version in the **\<diffgr:before>** block.</span></span> <span data-ttu-id="13fa6-159">Należy pamiętać, że **usunięte** wierszy będą miały **oryginalnego** wersja wiersza w  **\<diffgr: przed >** bloku, ale będą się żaden element adnotacjami w  **\<**  ***DataInstance***  **>**  bloku.</span><span class="sxs-lookup"><span data-stu-id="13fa6-159">Note that **Deleted** rows will have an **Original** row version in the **\<diffgr:before>** block, but there will be no annotated element in the **\<** ***DataInstance*** **>** block.</span></span>|  
|<span data-ttu-id="13fa6-160">**hasErrors**</span><span class="sxs-lookup"><span data-stu-id="13fa6-160">**hasErrors**</span></span>|<span data-ttu-id="13fa6-161">Identyfikuje wiersz w  **\<**  ***DataInstance***  **>**  zablokować z **RowError**.</span><span class="sxs-lookup"><span data-stu-id="13fa6-161">Identifies a row in the **\<** ***DataInstance*** **>** block with a **RowError**.</span></span> <span data-ttu-id="13fa6-162">Błędny element znajduje się w  **\<diffgr:errors >** bloku.</span><span class="sxs-lookup"><span data-stu-id="13fa6-162">The error element is placed in the **\<diffgr:errors>** block.</span></span>|  
|<span data-ttu-id="13fa6-163">**Błąd**</span><span class="sxs-lookup"><span data-stu-id="13fa6-163">**Error**</span></span>|<span data-ttu-id="13fa6-164">Tekst zawiera **RowError** dla określonego elementu w  **\<diffgr:errors >** bloku.</span><span class="sxs-lookup"><span data-stu-id="13fa6-164">Contains the text of the **RowError** for a particular element in the **\<diffgr:errors>** block.</span></span>|  
  
 <span data-ttu-id="13fa6-165"><xref:System.Data.DataSet> Obejmuje dodatkowych adnotacji podczas odczytywania lub zapisywania jego zawartość jako elementu DiffGram.</span><span class="sxs-lookup"><span data-stu-id="13fa6-165">The <xref:System.Data.DataSet> includes additional annotations when reading or writing its contents as a DiffGram.</span></span> <span data-ttu-id="13fa6-166">W poniższej tabeli opisano te dodatkowe adnotacje, które są zdefiniowane w przestrzeni nazw **urn: schemas-microsoft-com: XML-msdata**.</span><span class="sxs-lookup"><span data-stu-id="13fa6-166">The following table describes these additional annotations, which are defined in the namespace **urn:schemas-microsoft-com:xml-msdata**.</span></span>  
  
|<span data-ttu-id="13fa6-167">Adnotacja</span><span class="sxs-lookup"><span data-stu-id="13fa6-167">Annotation</span></span>|<span data-ttu-id="13fa6-168">Opis</span><span class="sxs-lookup"><span data-stu-id="13fa6-168">Description</span></span>|  
|----------------|-----------------|  
|<span data-ttu-id="13fa6-169">**RowOrder**</span><span class="sxs-lookup"><span data-stu-id="13fa6-169">**RowOrder**</span></span>|<span data-ttu-id="13fa6-170">Zachowuje kolejności wierszy oryginalnych danych i identyfikuje indeks wiersza, w szczególności <xref:System.Data.DataTable>.</span><span class="sxs-lookup"><span data-stu-id="13fa6-170">Preserves the row order of the original data and identifies the index of a row in a particular <xref:System.Data.DataTable>.</span></span>|  
|<span data-ttu-id="13fa6-171">**Ukryte**</span><span class="sxs-lookup"><span data-stu-id="13fa6-171">**Hidden**</span></span>|<span data-ttu-id="13fa6-172">Identyfikuje kolumny jako mający **ColumnMapping** ustawioną właściwość **MappingType.Hidden**.</span><span class="sxs-lookup"><span data-stu-id="13fa6-172">Identifies a column as having a **ColumnMapping** property set to **MappingType.Hidden**.</span></span> <span data-ttu-id="13fa6-173">Ten atrybut jest zapisywany w formacie **msdata: ukryte** *[nazwa_kolumny]*= "*wartość*".</span><span class="sxs-lookup"><span data-stu-id="13fa6-173">The attribute is written in the format **msdata:hidden** *[ColumnName]*="*value*".</span></span> <span data-ttu-id="13fa6-174">Na przykład: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.</span><span class="sxs-lookup"><span data-stu-id="13fa6-174">For example: `<Customers diffgr:id="Customers1" msdata:hiddenContactTitle="Owner">`.</span></span><br /><br /> <span data-ttu-id="13fa6-175">Należy pamiętać, że ukrytych kolumn tylko są zapisywane jako atrybut elementu DiffGram, jeśli zawierają one dane.</span><span class="sxs-lookup"><span data-stu-id="13fa6-175">Note that hidden columns are only written as a DiffGram attribute if they contain data.</span></span> <span data-ttu-id="13fa6-176">W przeciwnym razie są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="13fa6-176">Otherwise, they are ignored.</span></span>|  
  
## <a name="sample-diffgram"></a><span data-ttu-id="13fa6-177">Przykład elementu DiffGram</span><span class="sxs-lookup"><span data-stu-id="13fa6-177">Sample DiffGram</span></span>  
 <span data-ttu-id="13fa6-178">Poniżej przedstawiono przykład formatu elementu DiffGram.</span><span class="sxs-lookup"><span data-stu-id="13fa6-178">An example of the DiffGram format is shown below.</span></span> <span data-ttu-id="13fa6-179">Ten przykład przedstawia wynik aktualizacja wiersza w tabeli, aby zmiany zostały przekazane.</span><span class="sxs-lookup"><span data-stu-id="13fa6-179">This example shows the result of an update to a row in a table before the changes have been committed.</span></span> <span data-ttu-id="13fa6-180">Wiersz z CustomerID "ALFKI" został zmodyfikowany, ale nie zostały zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="13fa6-180">The row with a CustomerID of "ALFKI" has been modified, but not updated.</span></span> <span data-ttu-id="13fa6-181">W związku z tym istnieje **bieżącego** wiersz z **diffgr:id** z "Przekształcana w nazwę Klienci1" w  **\<**  ***DataInstance***  **>**  bloku, a **oryginalnego** wiersz z **diffgr:id** z "Przekształcana w nazwę Klienci1" w  **\<diffgr: przed >**bloku.</span><span class="sxs-lookup"><span data-stu-id="13fa6-181">As a result, there is a **Current** row with a **diffgr:id** of "Customers1" in the **\<** ***DataInstance*** **>** block, and an **Original** row with a **diffgr:id** of "Customers1" in the **\<diffgr:before>** block.</span></span> <span data-ttu-id="13fa6-182">Zawiera wiersz z CustomerID "ANATR" **RowError**, więc jest adnotowany przy `diffgr:hasErrors="true"` i jest elementem pokrewne  **\<diffgr:errors >** bloku.</span><span class="sxs-lookup"><span data-stu-id="13fa6-182">The row with a CustomerID of "ANATR" includes a **RowError**, so it is annotated with `diffgr:hasErrors="true"` and there is a related element in the **\<diffgr:errors>** block.</span></span>  
  
```xml  
<diffgr:diffgram xmlns:msdata="urn:schemas-microsoft-com:xml-msdata" xmlns:diffgr="urn:schemas-microsoft-com:xml-diffgram-v1">  
  <CustomerDataSet>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0" diffgr:hasChanges="modified">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>New Company</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers2" msdata:rowOrder="1" diffgram:hasErrors="true">  
      <CustomerID>ANATR</CustomerID>  
      <CompanyName>Ana Trujillo Emparedados y Helados</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers3" msdata:rowOrder="2">  
      <CustomerID>ANTON</CustomerID>  
      <CompanyName>Antonio Moreno Taquera</CompanyName>  
    </Customers>  
    <Customers diffgr:id="Customers4" msdata:rowOrder="3">  
      <CustomerID>AROUT</CustomerID>  
      <CompanyName>Around the Horn</CompanyName>  
    </Customers>  
  </CustomerDataSet>  
  <diffgr:before>  
    <Customers diffgr:id="Customers1" msdata:rowOrder="0">  
      <CustomerID>ALFKI</CustomerID>  
      <CompanyName>Alfreds Futterkiste</CompanyName>  
    </Customers>  
  </diffgr:before>  
  <diffgr:errors>  
    <Customers diffgr:id="Customers2" diffgr:Error="An optimistic concurrency violation has occurred for this row."/>  
  </diffgr:errors>  
</diffgr:diffgram>  
```  
  
## <a name="see-also"></a><span data-ttu-id="13fa6-183">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="13fa6-183">See Also</span></span>  
 [<span data-ttu-id="13fa6-184">Za pomocą języka XML w zestawie danych</span><span class="sxs-lookup"><span data-stu-id="13fa6-184">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 [<span data-ttu-id="13fa6-185">Podczas ładowania zestawu danych z pliku XML</span><span class="sxs-lookup"><span data-stu-id="13fa6-185">Loading a DataSet from XML</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/loading-a-dataset-from-xml.md)  
 [<span data-ttu-id="13fa6-186">Zapisywanie zawartości zestawu danych jako dane XML</span><span class="sxs-lookup"><span data-stu-id="13fa6-186">Writing DataSet Contents as XML Data</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/writing-dataset-contents-as-xml-data.md)  
 [<span data-ttu-id="13fa6-187">Zbiory danych, DataTables i DataViews</span><span class="sxs-lookup"><span data-stu-id="13fa6-187">DataSets, DataTables, and DataViews</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/index.md)  
 [<span data-ttu-id="13fa6-188">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="13fa6-188">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)