---
title: "Porady: zapisywanie tekstu do plików za pomocą StreamWriter w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- files [Visual Basic], writing to
- text, writing to files
- writing to files [Visual Basic], StreamWriter
ms.assetid: 99762e57-ef46-4dcc-8959-a8f79c22f067
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 874bb9cb88bbf25cb6208a0a33858855a7b26a49
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-write-text-to-files-with-a-streamwriter-in-visual-basic"></a><span data-ttu-id="2580b-102">Porady: zapisywanie tekstu do plików za pomocą StreamWriter w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2580b-102">How to: Write Text to Files with a StreamWriter in Visual Basic</span></span>
<span data-ttu-id="2580b-103">W tym przykładzie otwiera <xref:System.IO.StreamWriter> obiekt z `My.Computer.FileSystem.OpenTextFileWriter` — metoda i używa go do zapisu do pliku tekstowego z ciągiem <xref:System.IO.TextWriter.WriteLine%2A> metody <xref:System.IO.StreamWriter> klasy.</span><span class="sxs-lookup"><span data-stu-id="2580b-103">This example opens a <xref:System.IO.StreamWriter> object with the `My.Computer.FileSystem.OpenTextFileWriter` method and uses it to write a string to a text file with the <xref:System.IO.TextWriter.WriteLine%2A> method of the <xref:System.IO.StreamWriter> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2580b-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2580b-104">Example</span></span>  
 [!code-vb[VbFileIOWrite#5](../../../../visual-basic/developing-apps/programming/drives-directories-files/codesnippet/VisualBasic/how-to-write-text-to-files-with-a-streamwriter_1.vb)]  
  
## <a name="robust-programming"></a><span data-ttu-id="2580b-105">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="2580b-105">Robust Programming</span></span>  
 <span data-ttu-id="2580b-106">Następujące warunki mogą spowodować wyjątek:</span><span class="sxs-lookup"><span data-stu-id="2580b-106">The following conditions may cause an exception:</span></span>  
  
-   <span data-ttu-id="2580b-107">Plik istnieje i jest tylko do odczytu (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="2580b-107">The file exists and is read-only (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="2580b-108">Dysk jest pełny (<xref:System.IO.IOException>).</span><span class="sxs-lookup"><span data-stu-id="2580b-108">The disk is full (<xref:System.IO.IOException>).</span></span>  
  
-   <span data-ttu-id="2580b-109">Nazwa ścieżki jest za długa (<xref:System.IO.PathTooLongException>).</span><span class="sxs-lookup"><span data-stu-id="2580b-109">The pathname is too long (<xref:System.IO.PathTooLongException>).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="2580b-110">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="2580b-110">.NET Framework Security</span></span>  
 <span data-ttu-id="2580b-111">W tym przykładzie tworzy nowy plik, jeśli plik już nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="2580b-111">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="2580b-112">Jeśli aplikacja musi utworzyć plik, że aplikacja musi `Create` dostępu do folderu.</span><span class="sxs-lookup"><span data-stu-id="2580b-112">If an application needs to create a file, that application needs `Create` access for the folder.</span></span> <span data-ttu-id="2580b-113">Jeśli plik już istnieje, aplikacja musi tylko `Write` dostępu niższego poziomu uprawnień.</span><span class="sxs-lookup"><span data-stu-id="2580b-113">If the file already exists, the application needs only `Write` access, a lesser privilege.</span></span> <span data-ttu-id="2580b-114">Jeśli to możliwe, jest bardziej bezpieczne tworzenie pliku podczas wdrażania i udzielać tylko `Read` dostęp do jednego pliku, a nie `Create` dostępu dla folderu.</span><span class="sxs-lookup"><span data-stu-id="2580b-114">Where possible, it is more secure to create the file during deployment, and only grant `Read` access to a single file, rather than `Create` access for a folder.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2580b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2580b-115">See Also</span></span>  
 <xref:System.IO.StreamWriter>  
 <xref:Microsoft.VisualBasic.FileIO.FileSystem.OpenTextFileWriter%2A>  
 [<span data-ttu-id="2580b-116">Porady: Odczyt z plików tekstowych</span><span class="sxs-lookup"><span data-stu-id="2580b-116">How to: Read from Text Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/how-to-read-from-text-files.md)  
 [<span data-ttu-id="2580b-117">Zapisywanie w plikach</span><span class="sxs-lookup"><span data-stu-id="2580b-117">Writing to Files</span></span>](../../../../visual-basic/developing-apps/programming/drives-directories-files/writing-to-files.md)