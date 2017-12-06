---
title: "SqlMetal.exe (Narzędzie generowania kodu)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLMetal [LINQ to SQL]
- code generation tool
- SQLMetal.exe
- LINQ to SQL, serialization
- LINQ to SQL, DBML files
- LINQ to SQL, SQLMetal
ms.assetid: 819e5a96-7646-4fdb-b14b-fe31221b0614
caps.latest.revision: "43"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c54f304117c86066e18bfb40f3b3640819647ac0
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="sqlmetalexe-code-generation-tool"></a><span data-ttu-id="4a3ab-102">SqlMetal.exe (Narzędzie generowania kodu)</span><span class="sxs-lookup"><span data-stu-id="4a3ab-102">SqlMetal.exe (Code Generation Tool)</span></span>
<span data-ttu-id="4a3ab-103">Narzędzie wiersza polecenia SqlMetal generuje kod i mapowania dla [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] składnika [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4a3ab-103">The SqlMetal command-line tool generates code and mapping for the [!INCLUDE[vbtecdlinq](../../../includes/vbtecdlinq-md.md)] component of the [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].</span></span> <span data-ttu-id="4a3ab-104">Stosując opisane w dalszej części tego tematu opcje, można za pomocą programu SqlMetal wykonać kilka różnych akcji, takich jak:</span><span class="sxs-lookup"><span data-stu-id="4a3ab-104">By applying options that appear later in this topic, you can instruct SqlMetal to perform several different actions that include the following:</span></span>  
  
-   <span data-ttu-id="4a3ab-105">Na podstawie bazy danych — generowanie kodu źródłowego i atrybutów mapowania lub pliku mapowania.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-105">From a database, generate source code and mapping attributes or a mapping file.</span></span>  
  
-   <span data-ttu-id="4a3ab-106">Na podstawie bazy danych — generowanie pliku języka Intermediate Database Markup Language (dbml) na potrzeby dostosowywania.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-106">From a database, generate an intermediate database markup language (.dbml) file for customization.</span></span>  
  
-   <span data-ttu-id="4a3ab-107">Na podstawie pliku dbml — generowanie kodu i atrybutów mapowania lub pliku mapowania.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-107">From a .dbml file, generate code and mapping attributes or a mapping file.</span></span>  
  
 <span data-ttu-id="4a3ab-108">To narzędzie jest instalowane automatycznie z programem Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-108">This tool is automatically installed with Visual Studio.</span></span> <span data-ttu-id="4a3ab-109">Domyślnie plik znajduje się w `drive`: \Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-109">By default, the file is located at `drive`:\Program Files\Microsoft SDKs\Windows\v`n.nn`\bin.</span></span> <span data-ttu-id="4a3ab-110">Jeśli nie zostanie zainstalowany program Visual Studio, można także uzyskać plik SQLMetal, pobierając [zestaw Windows SDK](http://go.microsoft.com/fwlink/?LinkId=142225).</span><span class="sxs-lookup"><span data-stu-id="4a3ab-110">If you do not install Visual Studio, you can also get the SQLMetal file by downloading the [Windows SDK](http://go.microsoft.com/fwlink/?LinkId=142225).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a3ab-111">Deweloperzy korzystający z programu Visual Studio umożliwia również [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] można wygenerować klas jednostek.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-111">Developers who use Visual Studio can also use the [!INCLUDE[vs_ordesigner_long](../../../includes/vs-ordesigner-long-md.md)] to generate entity classes.</span></span> <span data-ttu-id="4a3ab-112">Podejście z użyciem wiersza polecenia dobrze sprawdza się w przypadku dużych baz danych.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-112">The command-line approach scales well for large databases.</span></span> <span data-ttu-id="4a3ab-113">Program SqlMetal to narzędzie wiersza polecenia, więc można użyć go w procesie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-113">Because SqlMetal is a command-line tool, you can use it in a build process.</span></span>  
  
 <span data-ttu-id="4a3ab-114">Aby uruchomić narzędzie, należy użyć wiersza polecenia dewelopera (lub wiersza polecenia programu Visual Studio w systemie Windows 7).</span><span class="sxs-lookup"><span data-stu-id="4a3ab-114">To run the tool, use the Developer Command Prompt (or the Visual Studio Command Prompt in Windows 7).</span></span> <span data-ttu-id="4a3ab-115">Aby uzyskać więcej informacji, zobacz [wiersze polecenia](../../../docs/framework/tools/developer-command-prompt-for-vs.md). W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="4a3ab-115">For more information, see [Command Prompts](../../../docs/framework/tools/developer-command-prompt-for-vs.md).At the command prompt, type the following:</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a3ab-116">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a3ab-116">Syntax</span></span>  
  
```  
sqlmetal [options] [<input file>]  
```  
  
## <a name="options"></a><span data-ttu-id="4a3ab-117">Opcje</span><span class="sxs-lookup"><span data-stu-id="4a3ab-117">Options</span></span>  
 <span data-ttu-id="4a3ab-118">Aby wyświetlić najbardziej aktualną listę opcji, należy wpisać `sqlmetal /?` w wierszu polecenia z zainstalowanych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-118">To view the most current option list, type `sqlmetal /?` at a command prompt from the installed location.</span></span>  
  
 <span data-ttu-id="4a3ab-119">**Opcje połączenia**</span><span class="sxs-lookup"><span data-stu-id="4a3ab-119">**Connection Options**</span></span>  
  
|<span data-ttu-id="4a3ab-120">Opcja</span><span class="sxs-lookup"><span data-stu-id="4a3ab-120">Option</span></span>|<span data-ttu-id="4a3ab-121">Opis</span><span class="sxs-lookup"><span data-stu-id="4a3ab-121">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4a3ab-122">**/ Server:**  *\<name >*</span><span class="sxs-lookup"><span data-stu-id="4a3ab-122">**/server:** *\<name>*</span></span>|<span data-ttu-id="4a3ab-123">Określa nazwę serwera bazy danych.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-123">Specifies database server name.</span></span>|  
|<span data-ttu-id="4a3ab-124">**/ bazy danych:**  *\<name >*</span><span class="sxs-lookup"><span data-stu-id="4a3ab-124">**/database:** *\<name>*</span></span>|<span data-ttu-id="4a3ab-125">Określa wykaz baz danych na serwerze.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-125">Specifies database catalog on server.</span></span>|  
|<span data-ttu-id="4a3ab-126">**/ User:**  *\<name >*</span><span class="sxs-lookup"><span data-stu-id="4a3ab-126">**/user:** *\<name>*</span></span>|<span data-ttu-id="4a3ab-127">Określa identyfikator logowania użytkownika. Wartość domyślna: Użyj uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-127">Specifies logon user id. Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="4a3ab-128">**/ password:**  *\<hasło >*</span><span class="sxs-lookup"><span data-stu-id="4a3ab-128">**/password:** *\<password>*</span></span>|<span data-ttu-id="4a3ab-129">Określa hasło logowania.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-129">Specifies logon password.</span></span> <span data-ttu-id="4a3ab-130">Wartość domyślna: Użyj uwierzytelniania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-130">Default value: Use Windows authentication.</span></span>|  
|<span data-ttu-id="4a3ab-131">**/ conn:**  *\<ciąg połączenia >*</span><span class="sxs-lookup"><span data-stu-id="4a3ab-131">**/conn:** *\<connection string>*</span></span>|<span data-ttu-id="4a3ab-132">Określa parametry połączenia z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-132">Specifies database connection string.</span></span> <span data-ttu-id="4a3ab-133">Nie można używać z **/Server**, **/bazy danych**, **User**, lub **/Password** opcje.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-133">Cannot be used with **/server**, **/database**, **/user**, or **/password** options.</span></span><br /><br /> <span data-ttu-id="4a3ab-134">W parametrach połączenia nie można umieszczać nazwy pliku.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-134">Do not include the file name in the connection string.</span></span> <span data-ttu-id="4a3ab-135">Zamiast tego należy określić nazwę pliku w wierszu polecenia jako plik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-135">Instead, add the file name to the command line as the input file.</span></span> <span data-ttu-id="4a3ab-136">Na przykład poniższy wiersz określa "c:\northwnd.mdf" jako pliku wejściowego: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-136">For example, the following line specifies "c:\northwnd.mdf" as the input file: **sqlmetal /code:"c:\northwind.cs" /language:csharp "c:\northwnd.mdf"**.</span></span>|  
|<span data-ttu-id="4a3ab-137">**/ timeout:**  *\<sekund >*</span><span class="sxs-lookup"><span data-stu-id="4a3ab-137">**/timeout:** *\<seconds>*</span></span>|<span data-ttu-id="4a3ab-138">Określa wartość limitu czasu używaną, gdy program SqlMetal uzyskuje dostęp do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-138">Specifies time-out value when SqlMetal accesses the database.</span></span> <span data-ttu-id="4a3ab-139">Wartość domyślna: 0 (czyli brak limitu czasu).</span><span class="sxs-lookup"><span data-stu-id="4a3ab-139">Default value: 0 (that is, no time limit).</span></span>|  
  
 <span data-ttu-id="4a3ab-140">**Opcje wyodrębniania**</span><span class="sxs-lookup"><span data-stu-id="4a3ab-140">**Extraction options**</span></span>  
  
|<span data-ttu-id="4a3ab-141">Opcja</span><span class="sxs-lookup"><span data-stu-id="4a3ab-141">Option</span></span>|<span data-ttu-id="4a3ab-142">Opis</span><span class="sxs-lookup"><span data-stu-id="4a3ab-142">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4a3ab-143">**/views**</span><span class="sxs-lookup"><span data-stu-id="4a3ab-143">**/views**</span></span>|<span data-ttu-id="4a3ab-144">Wyodrębnia widoki bazy danych.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-144">Extracts database views.</span></span>|  
|<span data-ttu-id="4a3ab-145">**/Functions**</span><span class="sxs-lookup"><span data-stu-id="4a3ab-145">**/functions**</span></span>|<span data-ttu-id="4a3ab-146">Wyodrębnia funkcje bazy danych.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-146">Extracts database functions.</span></span>|  
|<span data-ttu-id="4a3ab-147">**/sprocs**</span><span class="sxs-lookup"><span data-stu-id="4a3ab-147">**/sprocs**</span></span>|<span data-ttu-id="4a3ab-148">Wyodrębnia procedury składowane.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-148">Extracts stored procedures.</span></span>|  
  
 <span data-ttu-id="4a3ab-149">**Opcje wyjściowe**</span><span class="sxs-lookup"><span data-stu-id="4a3ab-149">**Output options**</span></span>  
  
|<span data-ttu-id="4a3ab-150">Opcja</span><span class="sxs-lookup"><span data-stu-id="4a3ab-150">Option</span></span>|<span data-ttu-id="4a3ab-151">Opis</span><span class="sxs-lookup"><span data-stu-id="4a3ab-151">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4a3ab-152">**/dbml** *[: plik]*</span><span class="sxs-lookup"><span data-stu-id="4a3ab-152">**/dbml** *[:file]*</span></span>|<span data-ttu-id="4a3ab-153">Wysyła dane wyjściowe w postaci pliku dbml.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-153">Sends output as .dbml.</span></span> <span data-ttu-id="4a3ab-154">Nie można używać z **/map** opcji.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-154">Cannot be used with **/map** option.</span></span>|  
|<span data-ttu-id="4a3ab-155">**/ Kod** *[: plik]*</span><span class="sxs-lookup"><span data-stu-id="4a3ab-155">**/code** *[:file]*</span></span>|<span data-ttu-id="4a3ab-156">Wysyła dane wyjściowe w postaci kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-156">Sends output as source code.</span></span> <span data-ttu-id="4a3ab-157">Nie można używać z **/dbml** opcji.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-157">Cannot be used with **/dbml** option.</span></span>|  
|<span data-ttu-id="4a3ab-158">**/ map** *[: plik]*</span><span class="sxs-lookup"><span data-stu-id="4a3ab-158">**/map** *[:file]*</span></span>|<span data-ttu-id="4a3ab-159">Generuje plik mapowania XML zamiast atrybutów.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-159">Generates an XML mapping file instead of attributes.</span></span> <span data-ttu-id="4a3ab-160">Nie można używać z **/dbml** opcji.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-160">Cannot be used with **/dbml** option.</span></span>|  
  
 <span data-ttu-id="4a3ab-161">**Różne**</span><span class="sxs-lookup"><span data-stu-id="4a3ab-161">**Miscellaneous**</span></span>  
  
|<span data-ttu-id="4a3ab-162">Opcja</span><span class="sxs-lookup"><span data-stu-id="4a3ab-162">Option</span></span>|<span data-ttu-id="4a3ab-163">Opis</span><span class="sxs-lookup"><span data-stu-id="4a3ab-163">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4a3ab-164">**/Language:**  *\<języka >*</span><span class="sxs-lookup"><span data-stu-id="4a3ab-164">**/language:** *\<language>*</span></span>|<span data-ttu-id="4a3ab-165">Określa język kodu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-165">Specifies source code language.</span></span><br /><br /> <span data-ttu-id="4a3ab-166">Nieprawidłowa  *\<języka >*: vb, csharp.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-166">Valid *\<language>*: vb, csharp.</span></span><br /><br /> <span data-ttu-id="4a3ab-167">Wartość domyślna: pochodzi z rozszerzeniem nazwy pliku kodu.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-167">Default value: Derived from extension on code file name.</span></span>|  
|<span data-ttu-id="4a3ab-168">**/ NAMESPACE:**  *\<name >*</span><span class="sxs-lookup"><span data-stu-id="4a3ab-168">**/namespace:** *\<name>*</span></span>|<span data-ttu-id="4a3ab-169">Określa przestrzeń nazw wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-169">Specifies namespace of the generated code.</span></span> <span data-ttu-id="4a3ab-170">Wartość domyślna: brak przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-170">Default value: no namespace.</span></span>|  
|<span data-ttu-id="4a3ab-171">**/ Context:**  *\<typu >*</span><span class="sxs-lookup"><span data-stu-id="4a3ab-171">**/context:** *\<type>*</span></span>|<span data-ttu-id="4a3ab-172">Określa nazwę klasy kontekstu danych.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-172">Specifies name of data context class.</span></span> <span data-ttu-id="4a3ab-173">Wartość domyślna: pochodzi z nazwy bazy danych.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-173">Default value: Derived from database name.</span></span>|  
|<span data-ttu-id="4a3ab-174">**/entitybase:**  *\<typu >*</span><span class="sxs-lookup"><span data-stu-id="4a3ab-174">**/entitybase:** *\<type>*</span></span>|<span data-ttu-id="4a3ab-175">Określa klasę bazową klas obiektów w generowanym kodzie.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-175">Specifies the base class of the entity classes in the generated code.</span></span> <span data-ttu-id="4a3ab-176">Wartość domyślna: obiekty nie mają klasy bazowej.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-176">Default value: Entities have no base class.</span></span>|  
|<span data-ttu-id="4a3ab-177">**/ pluralize**</span><span class="sxs-lookup"><span data-stu-id="4a3ab-177">**/pluralize**</span></span>|<span data-ttu-id="4a3ab-178">Automatycznie zmienia nazwy klas i składowych na liczbę mnogą lub pojedynczą.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-178">Automatically pluralizes or singularizes class and member names.</span></span><br /><br /> <span data-ttu-id="4a3ab-179">Ta opcja jest dostępna tylko w Stanach Zjednoczonych Wersja w języku angielskim.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-179">This option is available only in the U.S. English version.</span></span>|  
|<span data-ttu-id="4a3ab-180">**/Serialization:**  *\<opcji >*</span><span class="sxs-lookup"><span data-stu-id="4a3ab-180">**/serialization:** *\<option>*</span></span>|<span data-ttu-id="4a3ab-181">Generuje klasy, które można serializować.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-181">Generates serializable classes.</span></span><br /><br /> <span data-ttu-id="4a3ab-182">Nieprawidłowa  *\<opcji >*: Brak Unidirectional.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-182">Valid *\<option>*: None, Unidirectional.</span></span> <span data-ttu-id="4a3ab-183">Wartość domyślna: None.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-183">Default value: None.</span></span><br /><br /> <span data-ttu-id="4a3ab-184">Aby uzyskać więcej informacji, zobacz [szeregowanie](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span><span class="sxs-lookup"><span data-stu-id="4a3ab-184">For more information, see [Serialization](../../../docs/framework/data/adonet/sql/linq/serialization.md).</span></span>|  
  
 <span data-ttu-id="4a3ab-185">**Plik wejściowy**</span><span class="sxs-lookup"><span data-stu-id="4a3ab-185">**Input File**</span></span>  
  
|<span data-ttu-id="4a3ab-186">Opcja</span><span class="sxs-lookup"><span data-stu-id="4a3ab-186">Option</span></span>|<span data-ttu-id="4a3ab-187">Opis</span><span class="sxs-lookup"><span data-stu-id="4a3ab-187">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="4a3ab-188">**\<Plik wejściowy >**</span><span class="sxs-lookup"><span data-stu-id="4a3ab-188">**\<input file>**</span></span>|<span data-ttu-id="4a3ab-189">Określa plik .mdf programu SQL Server Express [!INCLUDE[ssEW](../../../includes/ssew-md.md)] pliku .sdf lub .dbml pliku pośredniego.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-189">Specifies a SQL Server Express .mdf file, a [!INCLUDE[ssEW](../../../includes/ssew-md.md)] .sdf file, or a .dbml intermediate file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4a3ab-190">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a3ab-190">Remarks</span></span>  
 <span data-ttu-id="4a3ab-191">Działanie programu SqlMetal w rzeczywistości obejmuje wykonanie dwóch kroków:</span><span class="sxs-lookup"><span data-stu-id="4a3ab-191">SqlMetal functionality actually involves two steps:</span></span>  
  
-   <span data-ttu-id="4a3ab-192">Wyodrębnienie metadanych bazy danych do pliku dbml.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-192">Extracting the metadata of the database into a .dbml file.</span></span>  
  
-   <span data-ttu-id="4a3ab-193">Wygenerowanie pliku wyjściowego z kodem.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-193">Generating a code output file.</span></span>  
  
     <span data-ttu-id="4a3ab-194">Za pomocą odpowiednich opcji wiersza polecenia, można utworzyć [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] lub kodu źródłowego C#, lub można utworzyć mapowania pliku XML.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-194">By using the appropriate command-line options, you can produce [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or C# source code, or you can produce an XML mapping file.</span></span>  
  
 <span data-ttu-id="4a3ab-195">Aby wyodrębnić metadane z pliku mdf, należy określić nazwę pliku mdf po wszystkich innych opcjach.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-195">To extract the metadata from an .mdf file, you must specify the name of the .mdf file after all other options.</span></span>  
  
 <span data-ttu-id="4a3ab-196">Jeśli nie **/Server** jest określony, **localhost/sqlexpress** zakłada, że.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-196">If no **/server** is specified, **localhost/sqlexpress** is assumed.</span></span>  
  
 [!INCLUDE[sqprsqext](../../../includes/sqprsqext-md.md)]<span data-ttu-id="4a3ab-197">zgłasza wyjątek, jeśli spełnione są co najmniej jeden z następujących warunków:</span><span class="sxs-lookup"><span data-stu-id="4a3ab-197"> throws an exception if one or more of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="4a3ab-198">Program SqlMetal próbuje wyodrębnić procedurę składowaną, którą sam wywołuje.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-198">SqlMetal tries to extract a stored procedure that calls itself.</span></span>  
  
-   <span data-ttu-id="4a3ab-199">Poziom zagnieżdżenia procedury składowanej, funkcji lub widoku przekracza 32.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-199">The nesting level of a stored procedure, function, or view exceeds 32.</span></span>  
  
     <span data-ttu-id="4a3ab-200">Program SqlMetal przechwytuje ten wyjątek i zgłasza go jako ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-200">SqlMetal catches this exception and reports it as a warning.</span></span>  
  
 <span data-ttu-id="4a3ab-201">Aby określić nazwę pliku wejściowego, należy dodać ją do wiersza polecenia jako plik wejściowy.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-201">To specify an input file name, add the name to the command line as the input file.</span></span> <span data-ttu-id="4a3ab-202">Łącznie z nazwą pliku w ciągu połączenia (przy użyciu **/conn** opcji) nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-202">Including the file name in the connection string (using the **/conn** option) is not supported.</span></span>  
  
## <a name="examples"></a><span data-ttu-id="4a3ab-203">Przykłady</span><span class="sxs-lookup"><span data-stu-id="4a3ab-203">Examples</span></span>  
 <span data-ttu-id="4a3ab-204">Generuje plik dbml zawierający wyodrębnione metadane SQL:</span><span class="sxs-lookup"><span data-stu-id="4a3ab-204">Generate a .dbml file that includes extracted SQL metadata:</span></span>  
  
 <span data-ttu-id="4a3ab-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span><span class="sxs-lookup"><span data-stu-id="4a3ab-205">**sqlmetal /server:myserver /database:northwind /dbml:mymeta.dbml**</span></span>  
  
 <span data-ttu-id="4a3ab-206">Generuje plik dbml zawierający metadane SQL wyodrębnione z pliku mdf przy użyciu programu SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="4a3ab-206">Generate a .dbml file that includes extracted SQL metadata from an .mdf file by using SQL Server Express:</span></span>  
  
 <span data-ttu-id="4a3ab-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span><span class="sxs-lookup"><span data-stu-id="4a3ab-207">**sqlmetal /dbml:mymeta.dbml mydbfile.mdf**</span></span>  
  
 <span data-ttu-id="4a3ab-208">Generuje plik dbml zawierający metadane SQL wyodrębnione z programu SQL Server Express:</span><span class="sxs-lookup"><span data-stu-id="4a3ab-208">Generate a .dbml file that includes extracted SQL metadata from SQL Server Express:</span></span>  
  
 <span data-ttu-id="4a3ab-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span><span class="sxs-lookup"><span data-stu-id="4a3ab-209">**sqlmetal /server:.\sqlexpress /dbml:mymeta.dbml /database:northwind**</span></span>  
  
 <span data-ttu-id="4a3ab-210">Generuje kod źródłowy na podstawie pliku metadanych dbml:</span><span class="sxs-lookup"><span data-stu-id="4a3ab-210">Generate source code from a .dbml metadata file:</span></span>  
  
 <span data-ttu-id="4a3ab-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span><span class="sxs-lookup"><span data-stu-id="4a3ab-211">**sqlmetal /namespace:nwind /code:nwind.cs /language:csharp mymetal.dbml**</span></span>  
  
 <span data-ttu-id="4a3ab-212">Generuje kod źródłowy bezpośrednio na podstawie metadanych SQL:</span><span class="sxs-lookup"><span data-stu-id="4a3ab-212">Generate source code from SQL metadata directly:</span></span>  
  
 <span data-ttu-id="4a3ab-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span><span class="sxs-lookup"><span data-stu-id="4a3ab-213">**sqlmetal /server:myserver /database:northwind /namespace:nwind /code:nwind.cs /language:csharp**</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4a3ab-214">Jeśli używasz **/ pluralize** opcję z przykładowej bazy danych Northwind, należy pamiętać o następujących zasadach.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-214">When you use the **/pluralize** option with the Northwind sample database, note the following behavior.</span></span> <span data-ttu-id="4a3ab-215">Gdy program SqlMetal tworzy nazwy tabel typu wiersz, nazwy tabel mają liczbę pojedynczą.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-215">When SqlMetal makes row-type names for tables, the table names are singular.</span></span> <span data-ttu-id="4a3ab-216">Gdy ułatwia <xref:System.Data.Linq.DataContext> właściwości dla tabel, nazwy tabeli są liczbie mnogiej.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-216">When it makes <xref:System.Data.Linq.DataContext> properties for tables, the table names are plural.</span></span> <span data-ttu-id="4a3ab-217">Przypadkowo nazwy tabel w przykładowej bazie danych Northwind mają już liczbę mnogą.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-217">Coincidentally, the tables in the Northwind sample database are already plural.</span></span> <span data-ttu-id="4a3ab-218">Dlatego też nie widać działania tej części opcji.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-218">Therefore, you do not see that part working.</span></span> <span data-ttu-id="4a3ab-219">Popularną praktyką jest nadawanie tabelom w bazie danych nazw w liczbie pojedynczej, ale równie popularną praktyką na platformie .NET jest nadawanie kolekcjom nazw w liczbie mnogiej.</span><span class="sxs-lookup"><span data-stu-id="4a3ab-219">Although it is common practice to name database tables singular, it is also a common practice in .NET to name collections plural.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a3ab-220">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4a3ab-220">See Also</span></span>  
 [<span data-ttu-id="4a3ab-221">Porady: Generowanie modelu obiektów w Visual Basic lub C#</span><span class="sxs-lookup"><span data-stu-id="4a3ab-221">How to: Generate the Object Model in Visual Basic or C#</span></span>](../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-in-visual-basic-or-csharp.md)  
 [<span data-ttu-id="4a3ab-222">Generowanie kodu w składniku LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="4a3ab-222">Code Generation in LINQ to SQL</span></span>](../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="4a3ab-223">Mapowanie zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="4a3ab-223">External Mapping</span></span>](../../../docs/framework/data/adonet/sql/linq/external-mapping.md)