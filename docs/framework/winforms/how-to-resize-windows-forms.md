---
title: "Porady: zmienianie rozmiarów formularzy systemu Windows"
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
- resizing Windows Forms
- Windows Forms, resizing
ms.assetid: 5d9dd47e-e68c-48c9-a0a3-a9ff34ba009d
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e38339eceef97c4d6f64dffdea9ac04c598b70a3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-resize-windows-forms"></a><span data-ttu-id="ed00b-102">Porady: zmienianie rozmiarów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ed00b-102">How to: Resize Windows Forms</span></span>
<span data-ttu-id="ed00b-103">Można określić rozmiar formularza systemu Windows na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="ed00b-103">You can specify the size of your Windows Form in several ways.</span></span> <span data-ttu-id="ed00b-104">Można zmienić wysokość i szerokość formularza programowo, ustawiając nową wartość dla <xref:System.Windows.Forms.Form.Size%2A> właściwości, lub Dostosuj <xref:System.Windows.Forms.Control.Height%2A> lub <xref:System.Windows.Forms.Control.Width%2A> właściwości pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="ed00b-104">You can change both the height and the width of the form programmatically by setting a new value for the <xref:System.Windows.Forms.Form.Size%2A> property, or adjust the <xref:System.Windows.Forms.Control.Height%2A> or <xref:System.Windows.Forms.Control.Width%2A> properties individually.</span></span> <span data-ttu-id="ed00b-105">Jeśli używasz [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], można zmienić rozmiar przy użyciu narzędzia Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="ed00b-105">If you are using [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)], you can change the size using the Windows Forms Designer.</span></span> <span data-ttu-id="ed00b-106">Zobacz też [porady: Zmienianie rozmiaru Windows Forms przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/37k2zkwx\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="ed00b-106">Also see [How to: Resize Windows Forms Using the Designer](http://msdn.microsoft.com/library/37k2zkwx\(v=vs.110\)).</span></span>  
  
### <a name="to-resize-a-form-programmatically"></a><span data-ttu-id="ed00b-107">Aby programowo zmienić rozmiar formularza</span><span class="sxs-lookup"><span data-stu-id="ed00b-107">To resize a form programmatically</span></span>  
  
-   <span data-ttu-id="ed00b-108">Zdefiniuj rozmiar formularza w czasie wykonywania, ustawiając <xref:System.Windows.Forms.Form.Size%2A> właściwości formularza.</span><span class="sxs-lookup"><span data-stu-id="ed00b-108">Define the size of a form at run time by setting the <xref:System.Windows.Forms.Form.Size%2A> property of the form.</span></span>  
  
     <span data-ttu-id="ed00b-109">Poniższy przykład kodu pokazuje rozmiar formularza ustawiona na 100 x 100 pikseli.</span><span class="sxs-lookup"><span data-stu-id="ed00b-109">The following code example shows the form size set to 100 × 100 pixels.</span></span>  
  
    ```vb  
    Form1.Size = New System.Drawing.Size(100, 100)  
    ```  
  
    ```csharp  
    Form1.Size = new System.Drawing.Size(100, 100);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(100, 100);  
    ```  
  
### <a name="to-change-form-width-and-height-programmatically"></a><span data-ttu-id="ed00b-110">Aby zmienić programowo formularza szerokości i wysokości.</span><span class="sxs-lookup"><span data-stu-id="ed00b-110">To change form width and height programmatically</span></span>  
  
-   <span data-ttu-id="ed00b-111">Po <xref:System.Windows.Forms.Form.Size%2A> jest zdefiniowany, zmienić za pomocą formularza wysokość lub szerokość <xref:System.Windows.Forms.Control.Width%2A> lub <xref:System.Windows.Forms.Control.Height%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed00b-111">After the <xref:System.Windows.Forms.Form.Size%2A> is defined, change either the form height or width by using the <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>  
  
     <span data-ttu-id="ed00b-112">Poniższy przykład kodu pokazuje szerokość formularza ustawioną 300 pikseli od lewej krawędzi formularza, natomiast wysokość pozostaje stała.</span><span class="sxs-lookup"><span data-stu-id="ed00b-112">The following code example shows the width of the form set to 300 pixels from the left edge of the form, whereas the height stays constant.</span></span>  
  
    ```vb  
    Form1.Width = 300  
    ```  
  
    ```csharp  
    Form1.Width = 300;  
    ```  
  
    ```cpp  
    Form1->Width = 300;  
    ```  
  
     <span data-ttu-id="ed00b-113">—lub—</span><span class="sxs-lookup"><span data-stu-id="ed00b-113">-or-</span></span>  
  
     <span data-ttu-id="ed00b-114">Zmień <xref:System.Drawing.Size.Width%2A> lub <xref:System.Drawing.Size.Height%2A> przez ustawienie <xref:System.Windows.Forms.Form.Size%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed00b-114">Change <xref:System.Drawing.Size.Width%2A> or <xref:System.Drawing.Size.Height%2A> by setting the <xref:System.Windows.Forms.Form.Size%2A> property.</span></span>  
  
     <span data-ttu-id="ed00b-115">Jednakże, jak pokazano w poniższym przykładzie kodu, ta metoda jest bardziej skomplikowane niż ustawienie tylko <xref:System.Windows.Forms.Control.Width%2A> lub <xref:System.Windows.Forms.Control.Height%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed00b-115">However, as the following code example shows, this approach is more cumbersome than just setting <xref:System.Windows.Forms.Control.Width%2A> or <xref:System.Windows.Forms.Control.Height%2A> properties.</span></span>  
  
    ```vb  
    Form1.Size = New Size(300, Form1.Size.Height)  
    ```  
  
    ```csharp  
    Form1.Size = new Size(300, Form1.Size.Height);  
    ```  
  
    ```cpp  
    Form1->Size = System::Drawing::Size(300, Form1->Size.Height);  
    ```  
  
### <a name="to-change-form-size-by-increments-programmatically"></a><span data-ttu-id="ed00b-116">Aby zmienić rozmiar formularza krokami programowo</span><span class="sxs-lookup"><span data-stu-id="ed00b-116">To change form size by increments programmatically</span></span>  
  
-   <span data-ttu-id="ed00b-117">Aby zwiększyć rozmiar formularza, ustaw <xref:System.Drawing.Size.Width%2A> i <xref:System.Drawing.Size.Height%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="ed00b-117">To increment the size of the form, set the <xref:System.Drawing.Size.Width%2A> and <xref:System.Drawing.Size.Height%2A> properties.</span></span>  
  
     <span data-ttu-id="ed00b-118">Poniższy przykład kodu pokazuje szerokość formularza ustawiona na większą niż bieżące ustawienie 200 pikseli.</span><span class="sxs-lookup"><span data-stu-id="ed00b-118">The following code example shows the width of the form set to 200 pixels wider than the current setting.</span></span>  
  
    ```vb  
    Form1.Width += 200  
    ```  
  
    ```csharp  
    Form1.Width += 200;  
    ```  
  
    ```cpp  
    Form1->Width += 200;  
    ```  
  
    > [!CAUTION]
    >  <span data-ttu-id="ed00b-119">Zawsze używaj <xref:System.Drawing.Size.Height%2A> lub <xref:System.Drawing.Size.Width%2A> zmienić wymiaru formularza, chyba że ustawiasz szerokość i wysokość wymiarów w tym samym czasie, ustawiając dla właściwości <xref:System.Windows.Forms.Form.Size%2A> właściwości na nowy <xref:System.Drawing.Size> struktury.</span><span class="sxs-lookup"><span data-stu-id="ed00b-119">Always use the <xref:System.Drawing.Size.Height%2A> or <xref:System.Drawing.Size.Width%2A> property to change a dimension of a form, unless you are setting both height and width dimensions at the same time by setting the <xref:System.Windows.Forms.Form.Size%2A> property to a new <xref:System.Drawing.Size> structure.</span></span> <span data-ttu-id="ed00b-120"><xref:System.Windows.Forms.Form.Size%2A> Zwraca <xref:System.Drawing.Size> struktury, która jest typem wartości.</span><span class="sxs-lookup"><span data-stu-id="ed00b-120">The <xref:System.Windows.Forms.Form.Size%2A> property returns a <xref:System.Drawing.Size> structure, which is a value type.</span></span> <span data-ttu-id="ed00b-121">Nie można przypisać nową wartość dla właściwości typu wartości.</span><span class="sxs-lookup"><span data-stu-id="ed00b-121">You cannot assign a new value to the property of a value type.</span></span> <span data-ttu-id="ed00b-122">W związku z tym Poniższy przykładowy kod nie zostanie skompilowany.</span><span class="sxs-lookup"><span data-stu-id="ed00b-122">Therefore, the following code example will not compile.</span></span>  
  
    ```vb  
    ' NOTE: CODE WILL NOT COMPILE  
    Dim f As New Form()  
    f.Size.Width += 100  
    ```  
  
    ```csharp  
    // NOTE: CODE WILL NOT COMPILE  
    Form f = new Form();  
    f.Size.Width += 100;  
    ```  
  
    ```cpp  
    // NOTE: CODE WILL NOT COMPILE  
    Form^ f = gcnew Form();  
    f->Size->X += 100;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ed00b-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ed00b-123">See Also</span></span>  
 [<span data-ttu-id="ed00b-124">Wprowadzenie do formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="ed00b-124">Getting Started with Windows Forms</span></span>](../../../docs/framework/winforms/getting-started-with-windows-forms.md)  
 [<span data-ttu-id="ed00b-125">Rozszerzanie aplikacji Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ed00b-125">Enhancing Windows Forms Applications</span></span>](../../../docs/framework/winforms/advanced/index.md)