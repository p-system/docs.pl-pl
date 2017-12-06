---
title: "Porady: włączanie widoku Tile w formancie ListView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- tile view feature
- tiling
- Windows Forms, controls
- ListView control [Windows Forms], tile view
ms.assetid: c20e67a3-2d94-413d-9fcf-ecbd0fe251da
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 280f4929b700e125b094eb1965eb140a3b180b99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-tile-view-in-a-windows-forms-listview-control"></a><span data-ttu-id="2a4b6-102">Porady: włączanie widoku Tile w formancie ListView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2a4b6-102">How to: Enable Tile View in a Windows Forms ListView Control</span></span>
<span data-ttu-id="2a4b6-103">Korzystając z funkcji Widok kafelków <xref:System.Windows.Forms.ListView> kontroli, możesz podać visual równowagi między informacji graficznych i tekstowych.</span><span class="sxs-lookup"><span data-stu-id="2a4b6-103">With the tile view feature of the <xref:System.Windows.Forms.ListView> control, you can provide a visual balance between graphical and textual information.</span></span> <span data-ttu-id="2a4b6-104">Wyświetlane dla elementu w widoku tile informacji tekstowych jest taka sama jak informacji o kolumnie zdefiniowanych w widoku szczegółów.</span><span class="sxs-lookup"><span data-stu-id="2a4b6-104">The textual information displayed for an item in tile view is the same as the column information defined for details view.</span></span> <span data-ttu-id="2a4b6-105">Widoku Tile współdziała z funkcjami znak grupowania lub wstawiania w <xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="2a4b6-105">Tile view works in combination with either the grouping or insertion mark features in the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
 <span data-ttu-id="2a4b6-106">Widoku tile używa ikona 32 x 32 pikseli i kilka wierszy tekstu, jak pokazano na poniższych ilustracjach.</span><span class="sxs-lookup"><span data-stu-id="2a4b6-106">The tile view uses a 32 x 32 pixel icon and several lines of text, as shown in the following images.</span></span>  
  
 <span data-ttu-id="2a4b6-107">![Widok sąsiadujący w formancie ListView](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span><span class="sxs-lookup"><span data-stu-id="2a4b6-107">![Tile View in a ListView Control](../../../../docs/framework/winforms/controls/media/listviewtile.gif "ListViewTile")</span></span>  
<span data-ttu-id="2a4b6-108">Kafelek widoku ikon i tekst</span><span class="sxs-lookup"><span data-stu-id="2a4b6-108">Tile view icons and text</span></span>  
  
 <span data-ttu-id="2a4b6-109">Aby włączyć widoku kafelków, ustaw <xref:System.Windows.Forms.ListView.View%2A> właściwości <xref:System.Windows.Forms.View.Tile>.</span><span class="sxs-lookup"><span data-stu-id="2a4b6-109">To enable tile view, set the <xref:System.Windows.Forms.ListView.View%2A> property to <xref:System.Windows.Forms.View.Tile>.</span></span> <span data-ttu-id="2a4b6-110">Przez ustawienie można dostosować rozmiar Kafelki <xref:System.Windows.Forms.ListView.TileSize%2A> właściwości, a liczba wierszy tekstu wyświetlane na kafelku dostosowując <xref:System.Windows.Forms.ListView.Columns%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2a4b6-110">You can adjust the size of the tiles by setting the <xref:System.Windows.Forms.ListView.TileSize%2A> property, and the number of text lines displayed in the tile by adjusting the <xref:System.Windows.Forms.ListView.Columns%2A> collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2a4b6-111">Jest dostępna tylko w widoku tile [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] podczas wywołania aplikacji <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="2a4b6-111">The tile view is available only on [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] when your application calls the <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="2a4b6-112">W starszych systemach operacyjnych, dowolny kod związane z widoku tile nie obowiązuje, a <xref:System.Windows.Forms.ListView> kontrolka ma być wyświetlana w widoku dużych ikon.</span><span class="sxs-lookup"><span data-stu-id="2a4b6-112">On earlier operating systems, any code related to the tile view has no effect, and the <xref:System.Windows.Forms.ListView> control displays in the large icon view.</span></span> <span data-ttu-id="2a4b6-113">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2a4b6-113">For more information, see <xref:System.Windows.Forms.ListView.View%2A?displayProperty=nameWithType>.</span></span>  
  
### <a name="to-set-tile-view-programmatically"></a><span data-ttu-id="2a4b6-114">Aby programowo Ustawianie widoku kafelków</span><span class="sxs-lookup"><span data-stu-id="2a4b6-114">To set tile view programmatically</span></span>  
  
1.  <span data-ttu-id="2a4b6-115">Użyj <xref:System.Windows.Forms.View> wyliczenie <xref:System.Windows.Forms.ListView> formantu.</span><span class="sxs-lookup"><span data-stu-id="2a4b6-115">Use the <xref:System.Windows.Forms.View> enumeration of the <xref:System.Windows.Forms.ListView> control.</span></span>  
  
    ```vb  
    ListView1.View = View.Tile  
    ```  
  
    ```csharp  
    listView1.View = View.Tile;  
    ```  
  
## <a name="example"></a><span data-ttu-id="2a4b6-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="2a4b6-116">Example</span></span>  
 <span data-ttu-id="2a4b6-117">W poniższym przykładzie kompletny kod pokazuje widoku Tile z Kafelki zmodyfikować, aby wyświetlić trzy wiersze tekstu.</span><span class="sxs-lookup"><span data-stu-id="2a4b6-117">The following complete code example demonstrates Tile view with tiles modified to show three lines of text.</span></span> <span data-ttu-id="2a4b6-118">Aby zapobiec zawijania wierszy został dostosowany rozmiar kafelka.</span><span class="sxs-lookup"><span data-stu-id="2a4b6-118">The tile size has been adjusted to prevent line-wrapping.</span></span>  
  
 [!code-cpp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CPP/listviewtilingexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/CS/listviewtilingexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.Tiling#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.Tiling/VB/listviewtilingexample.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2a4b6-119">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="2a4b6-119">Compiling the Code</span></span>  
 <span data-ttu-id="2a4b6-120">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="2a4b6-120">This example requires:</span></span>  
  
-   <span data-ttu-id="2a4b6-121">Odwołania do zestawów systemu i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="2a4b6-121">References to the System and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="2a4b6-122">Plik ikony o nazwie book.ico w tym samym katalogu co plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="2a4b6-122">An icon file named book.ico in the same directory as the executable file.</span></span>  
  
 <span data-ttu-id="2a4b6-123">Informacji dotyczących tworzenia tego przykładu z wiersza polecenia dla [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] lub [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2a4b6-123">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="2a4b6-124">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="2a4b6-124">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="2a4b6-125">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="2a4b6-125">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2a4b6-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2a4b6-126">See Also</span></span>  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.TileSize%2A>  
 [<span data-ttu-id="2a4b6-127">ListView — formant</span><span class="sxs-lookup"><span data-stu-id="2a4b6-127">ListView Control</span></span>](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [<span data-ttu-id="2a4b6-128">Informacje o formancie ListView</span><span class="sxs-lookup"><span data-stu-id="2a4b6-128">ListView Control Overview</span></span>](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [<span data-ttu-id="2a4b6-129">Funkcje systemu Windows XP i formantów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2a4b6-129">Windows XP Features and Windows Forms Controls</span></span>](http://msdn.microsoft.com/en-us/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)