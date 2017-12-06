---
title: "Jak zmienić rozmiar kolumn przy użyciu GridSplitter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- grid columns [WPF], resizing
- GridSplitter control [WPF], resizing grid columns
- resizing grid columns [WPF]
ms.assetid: 47b20fe6-7adc-4aa6-9693-b4e184eef74b
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5c8299a3f4885618601c8087a61c21dc5d989813
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-resize-columns-with-a-gridsplitter"></a><span data-ttu-id="f9b48-102">Jak zmienić rozmiar kolumn przy użyciu GridSplitter</span><span class="sxs-lookup"><span data-stu-id="f9b48-102">How to: Resize Columns with a GridSplitter</span></span>
<span data-ttu-id="f9b48-103">W tym przykładzie przedstawiono sposób tworzenia pionowym <xref:System.Windows.Controls.GridSplitter> Aby ponownie rozesłać odstęp między kolumnami w <xref:System.Windows.Controls.Grid> bez zmieniania wymiary <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="f9b48-103">This example shows how to create a vertical <xref:System.Windows.Controls.GridSplitter> in order to redistribute the space between two columns in a <xref:System.Windows.Controls.Grid> without changing the dimensions of the <xref:System.Windows.Controls.Grid>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9b48-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="f9b48-104">Example</span></span>  
 <span data-ttu-id="f9b48-105">**Jak utworzyć GridSplitter nakładany na krawędzi kolumny**</span><span class="sxs-lookup"><span data-stu-id="f9b48-105">**How to create a GridSplitter that overlays the edge of a column**</span></span>  
  
 <span data-ttu-id="f9b48-106">Aby określić <xref:System.Windows.Controls.GridSplitter> który zmienia rozmiar kolumn sąsiadujących ze sobą w <xref:System.Windows.Controls.Grid>ustaw <xref:System.Windows.Controls.Grid.Column%2A> dołączona właściwość do jednej z kolumn, które chcesz zmienić.</span><span class="sxs-lookup"><span data-stu-id="f9b48-106">To specify a <xref:System.Windows.Controls.GridSplitter> that resizes adjacent columns in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Column%2A> attached property to one of the columns that you want to resize.</span></span> <span data-ttu-id="f9b48-107">Jeśli Twoje <xref:System.Windows.Controls.Grid> ma więcej niż jeden wiersz, ustaw <xref:System.Windows.Controls.Grid.RowSpan%2A> dołączona właściwość liczby wierszy.</span><span class="sxs-lookup"><span data-stu-id="f9b48-107">If your <xref:System.Windows.Controls.Grid> has more than one row, set the <xref:System.Windows.Controls.Grid.RowSpan%2A> attached property to the number of rows.</span></span> <span data-ttu-id="f9b48-108">Następnie ustaw <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> właściwości <xref:System.Windows.HorizontalAlignment.Left> lub <xref:System.Windows.HorizontalAlignment.Right> (wyrównanie, które można ustawić zależy od na dwie kolumny, które chcesz zmienić).</span><span class="sxs-lookup"><span data-stu-id="f9b48-108">Then set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> property to <xref:System.Windows.HorizontalAlignment.Left> or <xref:System.Windows.HorizontalAlignment.Right> (which alignment you set depends on which two columns you want to resize).</span></span> <span data-ttu-id="f9b48-109">Wreszcie, ustaw <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> właściwości <xref:System.Windows.VerticalAlignment.Stretch>.</span><span class="sxs-lookup"><span data-stu-id="f9b48-109">Finally, set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> property to <xref:System.Windows.VerticalAlignment.Stretch>.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterColumnOverlay](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplittercolumnoverlay)]  
  
 <span data-ttu-id="f9b48-110">A <xref:System.Windows.Controls.GridSplitter> , która nie ma kolumny może być zasłonięty przez inne formanty w <xref:System.Windows.Controls.Grid>.</span><span class="sxs-lookup"><span data-stu-id="f9b48-110">A <xref:System.Windows.Controls.GridSplitter> that does not have its own column may be obscured by other controls in the <xref:System.Windows.Controls.Grid>.</span></span> <span data-ttu-id="f9b48-111">Aby uzyskać więcej informacji na temat uniknąć tego problemu, zobacz [Sure upewnij, że GridSplitter jest widoczny](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span><span class="sxs-lookup"><span data-stu-id="f9b48-111">For more information about how to prevent this issue, see [Make Sure That a GridSplitter Is Visible](../../../../docs/framework/wpf/controls/how-to-make-sure-that-a-gridsplitter-is-visible.md).</span></span>  
  
 <span data-ttu-id="f9b48-112">**Jak utworzyć GridSplitter, która zajmuje kolumny**</span><span class="sxs-lookup"><span data-stu-id="f9b48-112">**How to create a GridSplitter that occupies a column**</span></span>  
  
 <span data-ttu-id="f9b48-113">Aby określić <xref:System.Windows.Controls.GridSplitter> który zajmuje kolumny w <xref:System.Windows.Controls.Grid>ustaw <xref:System.Windows.Controls.Grid.Column%2A> dołączona właściwość do jednej z kolumn, które chcesz zmienić.</span><span class="sxs-lookup"><span data-stu-id="f9b48-113">To specify a <xref:System.Windows.Controls.GridSplitter> that occupies a column in a <xref:System.Windows.Controls.Grid>, set the <xref:System.Windows.Controls.Grid.Column%2A> attached property to one of the columns that you want to resize.</span></span> <span data-ttu-id="f9b48-114">Jeśli siatka ma więcej niż jeden wiersz, ustaw <xref:System.Windows.Controls.Grid.RowSpan%2A> dołączona właściwość liczby wierszy.</span><span class="sxs-lookup"><span data-stu-id="f9b48-114">If your Grid has more than one row, set the <xref:System.Windows.Controls.Grid.RowSpan%2A> attached property to the number of rows.</span></span> <span data-ttu-id="f9b48-115">Następnie ustaw <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> do <xref:System.Windows.HorizontalAlignment.Center>ustaw <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> właściwości <xref:System.Windows.VerticalAlignment.Stretch>i ustaw <xref:System.Windows.Controls.ColumnDefinition.Width%2A> kolumny, która zawiera <xref:System.Windows.Controls.GridSplitter> do <xref:System.Windows.GridLength.Auto%2A>.</span><span class="sxs-lookup"><span data-stu-id="f9b48-115">Then set the <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> to <xref:System.Windows.HorizontalAlignment.Center>, set the <xref:System.Windows.FrameworkElement.VerticalAlignment%2A> property to <xref:System.Windows.VerticalAlignment.Stretch>, and set the <xref:System.Windows.Controls.ColumnDefinition.Width%2A> of the column that contains the <xref:System.Windows.Controls.GridSplitter> to <xref:System.Windows.GridLength.Auto%2A>.</span></span>  
  
 <span data-ttu-id="f9b48-116">Poniższy przykład przedstawia sposób definiowania pionowym <xref:System.Windows.Controls.GridSplitter> zajmuje kolumny i zmienia rozmiar kolumn po obu stronach.</span><span class="sxs-lookup"><span data-stu-id="f9b48-116">The following example shows how to define a vertical <xref:System.Windows.Controls.GridSplitter> that occupies a column and resizes the columns on either side of it.</span></span>  
  
 [!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart1)]  
[!code-xaml[GridSplitterRowColumn#GridSplitterEntireColumnPart2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridSplitterRowColumn/CS/Window1.xaml#gridsplitterentirecolumnpart2)]  
  
## <a name="see-also"></a><span data-ttu-id="f9b48-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9b48-117">See Also</span></span>  
 <xref:System.Windows.Controls.GridSplitter>  
 [<span data-ttu-id="f9b48-118">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="f9b48-118">How-to Topics</span></span>](../../../../docs/framework/wpf/controls/gridsplitter-how-to-topics.md)