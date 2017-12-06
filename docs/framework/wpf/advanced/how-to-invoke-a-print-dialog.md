---
title: "Jak wywołać okno dialogowe drukowania"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ba541b367e56a809fa444528dccd69860c4de46
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-invoke-a-print-dialog"></a><span data-ttu-id="3e798-102">Jak wywołać okno dialogowe drukowania</span><span class="sxs-lookup"><span data-stu-id="3e798-102">How to: Invoke a Print Dialog</span></span>
<span data-ttu-id="3e798-103">Aby zapewnić możliwość drukowania z aplikacji, możesz po prostu utworzyć i otworzyć <xref:System.Windows.Controls.PrintDialog> obiektu.</span><span class="sxs-lookup"><span data-stu-id="3e798-103">To provide the ability to print from you application, you can simply create and open a <xref:System.Windows.Controls.PrintDialog> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3e798-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="3e798-104">Example</span></span>  
 <span data-ttu-id="3e798-105"><xref:System.Windows.Controls.PrintDialog> Kontrola zapewnia jeden punkt wejścia dla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguracji i [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] przesyłania zadania.</span><span class="sxs-lookup"><span data-stu-id="3e798-105">The <xref:System.Windows.Controls.PrintDialog> control provides a single entry point for [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration, and [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] job submission.</span></span> <span data-ttu-id="3e798-106">Kontrolka jest łatwy w użyciu i mogą zostać utworzone przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] znaczników lub kodu.</span><span class="sxs-lookup"><span data-stu-id="3e798-106">The control is easy to use and can be instantiated by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup or code.</span></span> <span data-ttu-id="3e798-107">W poniższym przykładzie pokazano, jak utworzyć wystąpienia, a następnie otwórz formantu w kodzie i drukowania z niego.</span><span class="sxs-lookup"><span data-stu-id="3e798-107">The following example demonstrates how to instantiate and open the control in code and how to print from it.</span></span> <span data-ttu-id="3e798-108">Widoczny jest również sposób upewnij się, że okno dialogowe zapewni użytkownika ustawianie określonego zakresu stron.</span><span class="sxs-lookup"><span data-stu-id="3e798-108">It also shows how to ensure that the dialog will give the user the option of setting a specific range of pages.</span></span> <span data-ttu-id="3e798-109">Przykład kodu zakłada, że plik FixedDocumentSequence.xps w folderze głównym dysku C:.</span><span class="sxs-lookup"><span data-stu-id="3e798-109">The example code assumes that there is a file FixedDocumentSequence.xps in the root of the C: drive.</span></span>  
  
 [!code-csharp[printdialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 <span data-ttu-id="3e798-110">Po otwarciu okna dialogowego, użytkownicy będą mogli wybrać z drukarek zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="3e798-110">Once the dialog is open, users will be able to select from the printers installed on their computer.</span></span> <span data-ttu-id="3e798-111">Mają również możliwość wyboru [modułu zapisywania dokumentów XPS firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=147319) utworzyć [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] zamiast drukowania pliku.</span><span class="sxs-lookup"><span data-stu-id="3e798-111">They will also have the option of selecting the [Microsoft XPS Document Writer](http://go.microsoft.com/fwlink/?LinkId=147319) to create an [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] file instead of printing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3e798-112"><xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Kontrolę nad [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], która została szczegółowo opisana w tym temacie nie należy mylić z <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> składnika [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3e798-112">The <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> control of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], which is discussed in this topic, should not be confused with the <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> component of [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)].</span></span>  
  
 <span data-ttu-id="3e798-113">Mówiąc ściślej, można użyć <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> metody bez konieczności otwierania okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="3e798-113">Strictly speaking, you can use the <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> method without ever opening the dialog.</span></span> <span data-ttu-id="3e798-114">W tym sensie formant może służyć jako niewidocznym składnik drukowania.</span><span class="sxs-lookup"><span data-stu-id="3e798-114">In that sense, the control can be used as an unseen printing component.</span></span> <span data-ttu-id="3e798-115">Jednak ze względu na wydajność, byłoby lepiej użyć <xref:System.Printing.PrintQueue.AddJob%2A> metody lub jedną z wielu <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> i <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter>.</span><span class="sxs-lookup"><span data-stu-id="3e798-115">But for performance reasons, it would be better to use either the <xref:System.Printing.PrintQueue.AddJob%2A> method or one of the many <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> and <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> methods of the <xref:System.Windows.Xps.XpsDocumentWriter>.</span></span> <span data-ttu-id="3e798-116">Aby uzyskać więcej informacji na ten temat, zobacz [programowo plików XPS drukowania](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md) i.</span><span class="sxs-lookup"><span data-stu-id="3e798-116">For more about this, see [Programmatically Print XPS Files](../../../../docs/framework/wpf/advanced/how-to-programmatically-print-xps-files.md) and .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e798-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3e798-117">See Also</span></span>  
 <xref:System.Windows.Controls.PrintDialog>  
 [<span data-ttu-id="3e798-118">Dokumentów na platformie WPF</span><span class="sxs-lookup"><span data-stu-id="3e798-118">Documents in WPF</span></span>](../../../../docs/framework/wpf/advanced/documents-in-wpf.md)  
 [<span data-ttu-id="3e798-119">Omówienie drukowania</span><span class="sxs-lookup"><span data-stu-id="3e798-119">Printing Overview</span></span>](../../../../docs/framework/wpf/advanced/printing-overview.md)  
 [<span data-ttu-id="3e798-120">Moduł zapisywania dokumentów XPS firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="3e798-120">Microsoft XPS Document Writer</span></span>](http://go.microsoft.com/fwlink/?LinkId=147319)