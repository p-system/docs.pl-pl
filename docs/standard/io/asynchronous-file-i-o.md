---
title: Asynchroniczne We/Wy pliku
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- streams, synchronous streams
- asynchronous I/O
- synchronous I/O
- streams, asynchronous streams
- I/O [.NET Framework], asynchronous I/O
- Stream class, synchronous I/O
- data streams, asynchronous streams
- Stream class, asynchronous I/O
- multiple I/O requests
- data streams, synchronous streams
ms.assetid: dbdd55e7-d6b9-4f9e-8abb-ab0edd4457f7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 270ae5a8cfa7c69c7caa0896dfe23b84db48f659
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33575521"
---
# <a name="asynchronous-file-io"></a>Asynchroniczne We/Wy pliku
Mechanizm operacji asynchronicznych umożliwia wykonywanie operacji We/Wy mocno obciążających zasoby bez blokowania wątku głównego. Ten aspekt dotyczący wydajności jest szczególnie ważny w aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] lub aplikacjach [!INCLUDE[desktop_appname](../../../includes/desktop-appname-md.md)], gdzie czasochłonne operacje strumieniowe mogą zablokować wątek interfejsu użytkownika i spowodować, że aplikacja będzie wyglądać, jakby przestała działać.  
  
 Począwszy od oprogramowania [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] typy We/Wy zawierają metody asynchroniczne, które upraszczają wykonywanie operacji asynchronicznych. Metoda asynchroniczna ma w nazwie element `Async`, np. <xref:System.IO.Stream.ReadAsync%2A>, <xref:System.IO.Stream.WriteAsync%2A>, <xref:System.IO.Stream.CopyToAsync%2A>, <xref:System.IO.Stream.FlushAsync%2A>, <xref:System.IO.TextReader.ReadLineAsync%2A> lub <xref:System.IO.TextReader.ReadToEndAsync%2A>. Te metody asynchroniczne są implementowane w klasach strumieniowych, takich jak <xref:System.IO.Stream>, <xref:System.IO.FileStream> i <xref:System.IO.MemoryStream>, oraz klasach służących do odczytu /zapisu do strumieni, takich jak <xref:System.IO.TextReader> i <xref:System.IO.TextWriter>.  
  
 W programie .NET Framework w wersji 4 i starszych do implementowania asynchronicznych operacji We/Wy należy używać metod takich jak <xref:System.IO.Stream.BeginRead%2A> i <xref:System.IO.Stream.EndRead%2A>. Metody te są nadal dostępne w programie [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] do obsługi starszego kodu, natomiast metody asynchroniczne pozwalają znacznie łatwiej implementować asynchroniczne operacje We/Wy.  
  
 Począwszy od wersji [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] program Visual Studio zawiera dwa słowa kluczowe do programowania asynchronicznego:  
  
 Modyfikator `Async` (Visual Basic) lub `async` (C#), który służy do oznaczania metody zawierającej operację asynchroniczną.  
  
 Operator `Await` (Visual Basic) lub `await` (C#), który jest stosowany do wyniku metody asynchronicznej.  
  
 W celu implementowania asynchronicznych operacji We/Wy należy używać tych słów kluczowych w połączeniu z metodami asynchronicznymi, jak pokazano w przykładach poniżej. Aby uzyskać więcej informacji, zobacz [programowanie asynchroniczne z Async i Await](https://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7).  
  
 W tym przykładzie pokazano, jak za pomocą dwóch obiektów <xref:System.IO.FileStream> skopiować pliki asynchronicznie z jednego katalogu do innego. Program obsługi zdarzeń <xref:System.Web.UI.WebControls.Button.Click> kontrolki <xref:System.Windows.Controls.Button> jest oznaczony modyfikatorem `async`, ponieważ wywołuje metodę asynchroniczną.  
  
 [!code-csharp[Asynchronous_File_IO_async#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example.cs#1)]
 [!code-vb[Asynchronous_File_IO_async#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example.vb#1)]  
  
 Następny przykład jest podobny do poprzedniego, tylko obiekty <xref:System.IO.StreamReader> i <xref:System.IO.StreamWriter> służą do asynchronicznego odczytywania i zapisywania zawartości pliku tekstowego.  
  
 [!code-csharp[Asynchronous_File_IO_async#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Asynchronous_File_IO_async/cs/example2.cs#2)]
 [!code-vb[Asynchronous_File_IO_async#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Asynchronous_File_IO_async/vb/example2.vb#2)]  
  
 W kolejnym przykładzie pokazano plik związany z kodem i plik XAML, które służą do otwarcia pliku w postaci klasy <xref:System.IO.Stream> w aplikacji [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)], a następnie odczytania jego zawartości przy użyciu wystąpienia klasy <xref:System.IO.StreamReader>. Metoda asynchroniczna umożliwia otwarcie pliku jako strumienia i odczytanie jego zawartości.  
  
 [!code-csharp[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml.cs#2)]
 [!code-vb[System.IO.WindowsRuntimeStorageExtensions#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/vb/blankpage.xaml.vb#2)]  
  
 [!code-xaml[System.IO.WindowsRuntimeStorageExtensions#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.io.windowsruntimestorageextensions/cs/blankpage.xaml#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.IO.Stream>  
 [We/Wy plików i strumieni](../../../docs/standard/io/index.md)  
 [Programowanie asynchroniczne z Async i Await](https://msdn.microsoft.com/library/db854f91-ccef-4035-ae4d-0911fde808c7)
