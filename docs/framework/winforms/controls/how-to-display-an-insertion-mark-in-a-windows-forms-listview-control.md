---
title: 'Porady: wyświetlanie znacznika wstawiania w formancie ListView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- ListView control [Windows Forms], drag operations
- graphics [Windows Forms], insertion marks
- drop and drag [Windows Forms], insertion marks
- insertion marks
ms.assetid: 88d0a15b-25fd-4dc3-a685-297351311940
ms.openlocfilehash: b948b8500f9f4067094186aa15a206908fb98c7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532915"
---
# <a name="how-to-display-an-insertion-mark-in-a-windows-forms-listview-control"></a>Porady: wyświetlanie znacznika wstawiania w formancie ListView formularzy systemu Windows
Znacznika wstawiania w <xref:System.Windows.Forms.ListView> kontroli wyświetlani użytkownicy punktu, w którym zostanie wstawiony przeciąganego elementów. Gdy użytkownik przeciągnie element do punktu między dwoma innymi elementami, znacznika wstawiania zawiera oczekiwanej lokalizacji nowego elementu.  
  
> [!NOTE]
>  Funkcja znacznika wstawiania jest dostępna tylko na [!INCLUDE[WinXpFamily](../../../../includes/winxpfamily-md.md)] podczas wywołania aplikacji <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody. W starszych systemach operacyjnych każdy kod związany z znacznika wstawiania nie ma wpływu i znacznika wstawiania nie będą wyświetlane. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Forms.ListViewInsertionMark>.  
  
 Na poniższej ilustracji przedstawiono znacznika wstawiania:  
  
 ![Znacznika wstawiania ListView](../../../../docs/framework/winforms/controls/media/listviewinsertion.gif "ListViewInsertion")  
  
 W poniższym przykładzie pokazano, jak korzystać z tej funkcji.  
  
## <a name="example"></a>Przykład  
 [!code-cpp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CPP/listviewinsertionmarkexample.cpp#1)]
 [!code-csharp[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/CS/listviewinsertionmarkexample.cs#1)]
 [!code-vb[System.Windows.Forms.ListView.InsertionMark#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ListView.InsertionMark/VB/listviewinsertionmarkexample.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu i System.Windows.Forms.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ListView>  
 <xref:System.Windows.Forms.ListView.InsertionMark%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ListViewInsertionMark>  
 [Kontrolka ListView](../../../../docs/framework/winforms/controls/listview-control-windows-forms.md)  
 [ListView, kontrolka — omówienie](../../../../docs/framework/winforms/controls/listview-control-overview-windows-forms.md)  
 [Funkcje systemu Windows XP i formantów formularzy systemu Windows](http://msdn.microsoft.com/library/bc7fab94-fce9-4bf1-a8ad-a5837c91c3c0)  
 [Przewodnik: wykonywanie operacji przeciągania i upuszczania w formularzach Windows Forms](../../../../docs/framework/winforms/advanced/walkthrough-performing-a-drag-and-drop-operation-in-windows-forms.md)
