---
title: "Porady: ustawienie pozycji tabulatorów w rysowanym tekście"
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
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e561e8096780301230071e869dac482a6a908a5e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a><span data-ttu-id="dc8fa-102">Porady: ustawienie pozycji tabulatorów w rysowanym tekście</span><span class="sxs-lookup"><span data-stu-id="dc8fa-102">How to: Set Tab Stops in Drawn Text</span></span>
<span data-ttu-id="dc8fa-103">Można ustawić tabulatorów tekstu przez wywołanie metody <xref:System.Drawing.StringFormat.SetTabStops%2A> metody <xref:System.Drawing.StringFormat> obiektu, a następnie przekazywanie, który <xref:System.Drawing.StringFormat> do obiektu <xref:System.Drawing.Graphics.DrawString%2A> metody <xref:System.Drawing.Graphics> klasy.</span><span class="sxs-lookup"><span data-stu-id="dc8fa-103">You can set tab stops for text by calling the <xref:System.Drawing.StringFormat.SetTabStops%2A> method of a <xref:System.Drawing.StringFormat> object and then passing that <xref:System.Drawing.StringFormat> object to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dc8fa-104"><xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> Ma obsługuje dodawanie punktów tabulacji narysowanego tekstu, mimo że można rozszerzyć istniejącą kartę przestanie używać <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> flagi.</span><span class="sxs-lookup"><span data-stu-id="dc8fa-104">The <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> does not support adding tab stops to drawn text, although you can expand existing tab stops using the <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> flag.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dc8fa-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="dc8fa-105">Example</span></span>  
 <span data-ttu-id="dc8fa-106">Poniższy przykład przedstawia tabulatorów 150, 250 i 350.</span><span class="sxs-lookup"><span data-stu-id="dc8fa-106">The following example sets tab stops at 150, 250, and 350.</span></span> <span data-ttu-id="dc8fa-107">Następnie kod wyświetla listę z kartami nazwy i wyniki testu.</span><span class="sxs-lookup"><span data-stu-id="dc8fa-107">Then, the code displays a tabbed list of names and test scores.</span></span>  
  
 <span data-ttu-id="dc8fa-108">Na poniższej ilustracji przedstawiono tekst z kartami.</span><span class="sxs-lookup"><span data-stu-id="dc8fa-108">The following illustration shows the tabbed text.</span></span>  
  
 <span data-ttu-id="dc8fa-109">![Czcionki tekstu](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")</span><span class="sxs-lookup"><span data-stu-id="dc8fa-109">![Fonts Text](../../../../docs/framework/winforms/advanced/media/fontstext4.png "fontstext4")</span></span>  
  
 <span data-ttu-id="dc8fa-110">Poniższy kod powoduje przekazanie dwa argumenty <xref:System.Drawing.StringFormat.SetTabStops%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="dc8fa-110">The following code passes two arguments to the <xref:System.Drawing.StringFormat.SetTabStops%2A> method.</span></span> <span data-ttu-id="dc8fa-111">Drugi argument jest tablica zawierająca kartę przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="dc8fa-111">The second argument is an array that contains tab offsets.</span></span> <span data-ttu-id="dc8fa-112">Pierwszy argument przekazany do <xref:System.Drawing.StringFormat.SetTabStops%2A> ma wartość 0, co oznacza, że pierwsze przesunięcie w tablicy jest mierzony z pozycji 0, do lewej krawędzi prostokątem.</span><span class="sxs-lookup"><span data-stu-id="dc8fa-112">The first argument passed to <xref:System.Drawing.StringFormat.SetTabStops%2A> is 0, which indicates that the first offset in the array is measured from position 0, the left edge of the bounding rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#41](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="dc8fa-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="dc8fa-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="dc8fa-114">Powyższy przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="dc8fa-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc8fa-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dc8fa-115">See Also</span></span>  
 [<span data-ttu-id="dc8fa-116">Używanie czcionek i tekstu</span><span class="sxs-lookup"><span data-stu-id="dc8fa-116">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 [<span data-ttu-id="dc8fa-117">Porady: Rysowanie tekstu z GDI</span><span class="sxs-lookup"><span data-stu-id="dc8fa-117">How to: Draw Text with GDI</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-text-with-gdi.md)