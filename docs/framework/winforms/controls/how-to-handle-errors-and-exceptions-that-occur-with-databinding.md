---
title: 'Porady: obsługa błędów i wyjątków występujących za powodu powiązania danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- error handling [Windows Forms], examples
- data binding [Windows Forms], examples
- examples [Windows Forms], error handling
- error handling [Windows Forms], data binding
- data binding [Windows Forms], error handling
- BindingSource component [Windows Forms], handling errors and exceptions
ms.assetid: eddc5bad-9513-47df-ab28-f02d8dff7892
ms.openlocfilehash: c7c05eb8d858c1f911e148def1c714e3caf74c95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532265"
---
# <a name="how-to-handle-errors-and-exceptions-that-occur-with-databinding"></a>Porady: obsługa błędów i wyjątków występujących za powodu powiązania danych
Często wyjątków i błędów są dokonywane na podstawowym obiektów biznesowych gdy związane z formantami. Można przechwycić te błędy i wyjątki, a następnie odzyskać lub przekazać informacje o błędzie dla użytkownika obsługa <xref:System.Windows.Forms.Binding.BindingComplete> zdarzenia dla konkretnej <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, lub <xref:System.Windows.Forms.CurrencyManager> składnika.  
  
## <a name="example"></a>Przykład  
 Ten przykład kodu pokazuje sposób obsługi błędów i wyjątków występujących podczas operacji wiązania danych. Demonstracja przechwycić błędy Obsługa <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> zdarzenie <xref:System.Windows.Forms.Binding> obiektów. Aby przechwycić błędy i wyjątki przez Obsługa tego zdarzenia, należy włączyć formatowania dla powiązania. Można włączyć formatowania powiązania jest zbudowanych lub dodanie do kolekcji powiązanie lub przez ustawienie <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> właściwości `true`.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 Podczas wykonywania kodu, a pusty ciąg została wprowadzona nazwa części lub wartość mniejsza niż 100 jest wprowadzono numer części pojawi się komunikat. Jest to wynik Obsługa <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> zdarzenia dla tych powiązań pola tekstowego.  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, System.Drawing i System.Windows.Forms.  
  
 Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć w tym przykładzie w programie Visual Studio przez wklejenie kodu do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=nameWithType>  
 [BindingSource, składnik](../../../../docs/framework/winforms/controls/bindingsource-component.md)
