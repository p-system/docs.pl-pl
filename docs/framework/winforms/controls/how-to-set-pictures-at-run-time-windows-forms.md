---
title: "Porady: ustawienie obrazów w czasie wykonywania (Formularze systemu Windows)"
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
- pictures [Windows Forms], setting display
- examples [Windows Forms], PictureBox control
- bitmaps [Windows Forms], displaying in PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding images
- images [Windows Forms], adding with PictureBox control [Windows Forms]
- PictureBox control [Windows Forms], adding pictures
ms.assetid: 18ca41d0-68a5-4660-985e-a6c1fbc01d76
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 429c0c928d8bff4f837186040288d9447fc18687
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-set-pictures-at-run-time-windows-forms"></a><span data-ttu-id="ad3f2-102">Porady: ustawienie obrazów w czasie wykonywania (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="ad3f2-102">How to: Set Pictures at Run Time (Windows Forms)</span></span>
<span data-ttu-id="ad3f2-103">Można programowo Ustawianie obrazu wyświetlanego przez program Windows Forms <xref:System.Windows.Forms.PictureBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="ad3f2-103">You can programmatically set the image displayed by a Windows Forms <xref:System.Windows.Forms.PictureBox> control.</span></span>  
  
### <a name="to-set-a-picture-programmatically"></a><span data-ttu-id="ad3f2-104">Aby ustawić programowo obrazu</span><span class="sxs-lookup"><span data-stu-id="ad3f2-104">To set a picture programmatically</span></span>  
  
-   <span data-ttu-id="ad3f2-105">Ustaw <xref:System.Windows.Forms.PictureBox.Image%2A> za pomocą właściwości <xref:System.Drawing.Image.FromFile%2A> metody <xref:System.Drawing.Image> klasy.</span><span class="sxs-lookup"><span data-stu-id="ad3f2-105">Set the <xref:System.Windows.Forms.PictureBox.Image%2A> property using the <xref:System.Drawing.Image.FromFile%2A> method of the <xref:System.Drawing.Image> class.</span></span>  
  
     <span data-ttu-id="ad3f2-106">W poniższym przykładzie ścieżka zestawu dla lokalizacji obrazu jest folder Moje dokumenty.</span><span class="sxs-lookup"><span data-stu-id="ad3f2-106">In the example below, the path set for the location of the image is the My Documents folder.</span></span> <span data-ttu-id="ad3f2-107">Tej operacji, ponieważ można założyć, że większość komputerów z systemem operacyjnym Windows będzie zawierać tego katalogu.</span><span class="sxs-lookup"><span data-stu-id="ad3f2-107">This is done, because you can assume that most computers running the Windows operating system will include this directory.</span></span> <span data-ttu-id="ad3f2-108">To umożliwia użytkownikom z poziomami dostępu minimalny system bezpiecznego uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ad3f2-108">This also allows users with minimal system access levels to safely run the application.</span></span> <span data-ttu-id="ad3f2-109">W poniższym przykładzie założono formularza z <xref:System.Windows.Forms.PictureBox> kontroli już dodany.</span><span class="sxs-lookup"><span data-stu-id="ad3f2-109">The example below assumes a form with a <xref:System.Windows.Forms.PictureBox> control already added.</span></span>  
  
    ```vb  
    Private Sub LoadNewPict()  
       ' You should replace the bold image   
       ' in the sample below with an icon of your own choosing.  
       PictureBox1.Image = Image.FromFile _  
       (System.Environment.GetFolderPath _  
       (System.Environment.SpecialFolder.Personal) _  
       & "\Image.gif")  
    End Sub  
    ```  
  
    ```csharp  
    private void LoadNewPict(){  
       // You should replace the bold image   
       // in the sample below with an icon of your own choosing.  
       // Note the escape character used (@) when specifying the path.  
       pictureBox1.Image = Image.FromFile  
       (System.Environment.GetFolderPath  
       (System.Environment.SpecialFolder.Personal)  
       + @"\Image.gif");  
    }  
    ```  
  
    ```cpp  
    private:  
       void LoadNewPict()  
       {  
          // You should replace the bold image   
          // in the sample below with an icon of your own choosing.  
          pictureBox1->Image = Image::FromFile(String::Concat(  
             System::Environment::GetFolderPath(  
             System::Environment::SpecialFolder::Personal),  
             "\\Image.gif"));  
       }  
    ```  
  
### <a name="to-clear-a-graphic"></a><span data-ttu-id="ad3f2-110">Aby wyczyścić grafiki</span><span class="sxs-lookup"><span data-stu-id="ad3f2-110">To clear a graphic</span></span>  
  
-   <span data-ttu-id="ad3f2-111">Po pierwsze zwalniają pamięć używana przez obraz, a następnie wyczyść grafiki.</span><span class="sxs-lookup"><span data-stu-id="ad3f2-111">First, release the memory being used by the image, and then clear the graphic.</span></span> <span data-ttu-id="ad3f2-112">Wyrzucanie elementów bezużytecznych zwolnić pamięć później w przypadku zarządzania pamięcią problem.</span><span class="sxs-lookup"><span data-stu-id="ad3f2-112">Garbage collection will free up the memory later if memory management becomes a problem.</span></span>  
  
    ```vb  
    If Not (PictureBox1.Image Is Nothing) Then  
       PictureBox1.Image.Dispose()  
       PictureBox1.Image = Nothing  
    End If  
    ```  
  
    ```csharp  
    if (pictureBox1.Image != null)   
    {  
       pictureBox1.Image.Dispose();  
       pictureBox1.Image = null;  
    }  
    ```  
  
    ```cpp  
    if (pictureBox1->Image != nullptr)  
    {  
       pictureBox1->Image->Dispose();  
       pictureBox1->Image = nullptr;  
    }  
    ```  
  
    > [!NOTE]
    >  <span data-ttu-id="ad3f2-113">Aby uzyskać więcej informacji o tym, dlaczego należy używać <xref:System.Drawing.Image.Dispose%2A> metody w ten sposób, zobacz [czyszczenie zasobów niezarządzanych](../../../../docs/standard/garbage-collection/unmanaged.md).</span><span class="sxs-lookup"><span data-stu-id="ad3f2-113">For more information on why you should use the <xref:System.Drawing.Image.Dispose%2A> method in this way, see [Cleaning Up Unmanaged Resources](../../../../docs/standard/garbage-collection/unmanaged.md).</span></span>  
  
     <span data-ttu-id="ad3f2-114">Ten kod spowoduje wyczyszczenie obrazu, nawet jeśli grafiki został załadowany do formantu w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="ad3f2-114">This code will clear the image even if a graphic was loaded into the control at design time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad3f2-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad3f2-115">See Also</span></span>  
 <xref:System.Windows.Forms.PictureBox>  
 <xref:System.Drawing.Image.FromFile%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="ad3f2-116">Informacje o formancie PictureBox</span><span class="sxs-lookup"><span data-stu-id="ad3f2-116">PictureBox Control Overview</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-overview-windows-forms.md)  
 [<span data-ttu-id="ad3f2-117">Porady: Dodawanie zdjęcia przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="ad3f2-117">How to: Load a Picture Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-load-a-picture-using-the-designer-windows-forms.md)  
 [<span data-ttu-id="ad3f2-118">Porady: modyfikowanie rozmiaru lub położenia obrazu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="ad3f2-118">How to: Modify the Size or Placement of a Picture at Run Time</span></span>](../../../../docs/framework/winforms/controls/how-to-modify-the-size-or-placement-of-a-picture-at-run-time-windows-forms.md)  
 [<span data-ttu-id="ad3f2-119">PictureBox — formant</span><span class="sxs-lookup"><span data-stu-id="ad3f2-119">PictureBox Control</span></span>](../../../../docs/framework/winforms/controls/picturebox-control-windows-forms.md)