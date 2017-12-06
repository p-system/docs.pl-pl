---
title: "Porady: tworzenie figur z linii, krzywych i kształtów"
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
helpviewer_keywords:
- figures [Windows Forms], creating from shapes
- figures [Windows Forms], creating from lines
ms.assetid: 82fd56c7-b443-4765-9b7c-62ce030656ec
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b382e0e1a627d7f61ce8ac664ac47d98c3725cad
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-figures-from-lines-curves-and-shapes"></a><span data-ttu-id="6be42-102">Porady: tworzenie figur z linii, krzywych i kształtów</span><span class="sxs-lookup"><span data-stu-id="6be42-102">How to: Create Figures from Lines, Curves, and Shapes</span></span>
<span data-ttu-id="6be42-103">Do utworzenia rysunku, należy utworzyć <xref:System.Drawing.Drawing2D.GraphicsPath>, a następnie wywołać metod, takich jak <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> i <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, aby dodać elementów podstawowych do ścieżki.</span><span class="sxs-lookup"><span data-stu-id="6be42-103">To create a figure, construct a <xref:System.Drawing.Drawing2D.GraphicsPath>, and then call methods, such as <xref:System.Drawing.Drawing2D.GraphicsPath.AddLine%2A> and <xref:System.Drawing.Drawing2D.GraphicsPath.AddCurve%2A>, to add primitives to the path.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6be42-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6be42-104">Example</span></span>  
 <span data-ttu-id="6be42-105">W poniższych przykładach kodu Utwórz ścieżek, które mają dane:</span><span class="sxs-lookup"><span data-stu-id="6be42-105">The following code examples create paths that have figures:</span></span>  
  
-   <span data-ttu-id="6be42-106">W pierwszym przykładzie jest tworzony ścieżki, która zawiera jedną wartość.</span><span class="sxs-lookup"><span data-stu-id="6be42-106">The first example creates a path that has a single figure.</span></span> <span data-ttu-id="6be42-107">Rysunek składa się z jednego łuk. Łuk ma kąt odchylenia –180 stopni, która jest zegara w układzie współrzędnych domyślne.</span><span class="sxs-lookup"><span data-stu-id="6be42-107">The figure consists of a single arc. The arc has a sweep angle of –180 degrees, which is counterclockwise in the default coordinate system.</span></span>  
  
-   <span data-ttu-id="6be42-108">W drugim przykładzie jest tworzony ścieżki, która ma dwa rysunki.</span><span class="sxs-lookup"><span data-stu-id="6be42-108">The second example creates a path that has two figures.</span></span> <span data-ttu-id="6be42-109">Pierwszą jest łuk znak wiersza.</span><span class="sxs-lookup"><span data-stu-id="6be42-109">The first figure is an arc followed by a line.</span></span> <span data-ttu-id="6be42-110">Drugi rysunek to linia następuje krzywej znak wiersza.</span><span class="sxs-lookup"><span data-stu-id="6be42-110">The second figure is a line followed by a curve followed by a line.</span></span> <span data-ttu-id="6be42-111">Pierwszą pozostanie otwarte, a drugi rysunek jest zamknięty.</span><span class="sxs-lookup"><span data-stu-id="6be42-111">The first figure is left open, and the second figure is closed.</span></span>  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#21)]  
  
 [!code-csharp[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.ConstructingDrawingPaths#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ConstructingDrawingPaths/VB/Class1.vb#22)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6be42-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6be42-112">Compiling the Code</span></span>  
 <span data-ttu-id="6be42-113">Poprzednich przykładach są przeznaczone do użytku z formularzy systemu Windows, a potrzebują <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="6be42-113">The previous examples are designed for use with Windows Forms, and they require <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of the <xref:System.Windows.Forms.Control.Paint> event handler.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6be42-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6be42-114">See Also</span></span>  
 <xref:System.Drawing.Drawing2D.GraphicsPath>  
 [<span data-ttu-id="6be42-115">Konstruowanie i rysowanie ścieżek</span><span class="sxs-lookup"><span data-stu-id="6be42-115">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)  
 [<span data-ttu-id="6be42-116">Rysowanie linii i kształtów za pomocą pióra</span><span class="sxs-lookup"><span data-stu-id="6be42-116">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)