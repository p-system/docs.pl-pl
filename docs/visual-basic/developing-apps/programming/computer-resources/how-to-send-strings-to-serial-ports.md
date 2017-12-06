---
title: "Porady: wysyłanie ciągów do portów seryjnych w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- ports, sending strings to
- strings [Visual Basic], sending to serial ports
- My.Computer.Ports object
- serial ports, sending strings to
ms.assetid: 6ebf46cd-b2d0-4b2c-9a1f-be177b22ad52
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 95c67b344572d21f418cbc14d350e6ff28611bd3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-send-strings-to-serial-ports-in-visual-basic"></a><span data-ttu-id="ad42c-102">Porady: wysyłanie ciągów do portów seryjnych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ad42c-102">How to: Send Strings to Serial Ports in Visual Basic</span></span>
<span data-ttu-id="ad42c-103">W tym temacie opisano sposób użycia `My.Computer.Ports` na wysyłanie ciągów do portów szeregowych komputera w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ad42c-103">This topic describes how to use `My.Computer.Ports` to send strings to the computer's serial ports in [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="ad42c-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="ad42c-104">Example</span></span>  
 <span data-ttu-id="ad42c-105">W tym przykładzie wysyła ciąg do portu szeregowego COM1.</span><span class="sxs-lookup"><span data-stu-id="ad42c-105">This example sends a string to the COM1 serial port.</span></span> <span data-ttu-id="ad42c-106">Może być konieczne użycie innego portu szeregowego na tym komputerze.</span><span class="sxs-lookup"><span data-stu-id="ad42c-106">You may need to use a different serial port on your computer.</span></span>  
  
 <span data-ttu-id="ad42c-107">Użyj `My.Computer.Ports.OpenSerialPort` metodę, aby uzyskać odwołania do portu.</span><span class="sxs-lookup"><span data-stu-id="ad42c-107">Use the `My.Computer.Ports.OpenSerialPort` method to obtain a reference to the port.</span></span> <span data-ttu-id="ad42c-108">Aby uzyskać więcej informacji, zobacz <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span><span class="sxs-lookup"><span data-stu-id="ad42c-108">For more information, see <xref:Microsoft.VisualBasic.Devices.Ports.OpenSerialPort%2A>.</span></span>  
  
 <span data-ttu-id="ad42c-109">`Using` Bloku umożliwia zamknięcie portu szeregowego, nawet jeśli generuje wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ad42c-109">The `Using` block allows the application to close the serial port even if it generates an exception.</span></span> <span data-ttu-id="ad42c-110">Cały kod, który manipuluje portu szeregowego powinien pojawić się w tym bloku lub poziomu `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="ad42c-110">All code that manipulates the serial port should appear within this block or within a `Try...Catch...Finally` block.</span></span>  
  
 <span data-ttu-id="ad42c-111"><xref:System.IO.Ports.SerialPort.WriteLine%2A> Metoda wysyła dane do portu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="ad42c-111">The <xref:System.IO.Ports.SerialPort.WriteLine%2A> method sends the data to the serial port.</span></span>  
  
 [!code-vb[VbVbalrMyComputer#33](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-send-strings-to-serial-ports_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="ad42c-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="ad42c-112">Compiling the Code</span></span>  
  
-   <span data-ttu-id="ad42c-113">W tym przykładzie założono komputer korzysta z `COM1`.</span><span class="sxs-lookup"><span data-stu-id="ad42c-113">This example assumes the computer is using `COM1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="ad42c-114">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="ad42c-114">Robust Programming</span></span>  
 <span data-ttu-id="ad42c-115">W tym przykładzie założono komputer korzysta z `COM1`; w celu zapewnienia większej elastyczności, kod pozwolić użytkownikowi na wybranie wybranego portu szeregowego z listy dostępnych portów.</span><span class="sxs-lookup"><span data-stu-id="ad42c-115">This example assumes the computer is using `COM1`; for more flexibility, the code should allow the user to select the desired serial port from a list of available ports.</span></span> <span data-ttu-id="ad42c-116">Aby uzyskać więcej informacji, zobacz [porady: portów seryjnych dostępne Pokaż](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span><span class="sxs-lookup"><span data-stu-id="ad42c-116">For more information, see [How to: Show Available Serial Ports](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md).</span></span>  
  
 <span data-ttu-id="ad42c-117">W tym przykładzie użyto `Using` bloku, aby się upewnić, że aplikacja zamyka port, nawet jeśli zgłasza wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ad42c-117">This example uses a `Using` block to make sure that the application closes the port even if it throws an exception.</span></span> <span data-ttu-id="ad42c-118">Aby uzyskać więcej informacji, zobacz [instrukcji Using](../../../../visual-basic/language-reference/statements/using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="ad42c-118">For more information, see [Using Statement](../../../../visual-basic/language-reference/statements/using-statement.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad42c-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad42c-119">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType>  
 [<span data-ttu-id="ad42c-120">Porady: modemy dostępowe powiązane z portami seryjnymi</span><span class="sxs-lookup"><span data-stu-id="ad42c-120">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [<span data-ttu-id="ad42c-121">Porady: wyświetlanie dostępnych portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="ad42c-121">How to: Show Available Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-show-available-serial-ports.md)