---
title: "Label — Informacje o formancie (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: Label
helpviewer_keywords:
- images [Windows Forms], displaying in labels
- labels
- Label control [Windows Forms], about Label control
ms.assetid: dcad7f44-11b7-4c55-b0c0-d984ade43d7d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f55cfb6afa8ad533aac84b391a7cd6fef83d72d8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="label-control-overview-windows-forms"></a><span data-ttu-id="2f0ec-102">Label — Informacje o formancie (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="2f0ec-102">Label Control Overview (Windows Forms)</span></span>
<span data-ttu-id="2f0ec-103">Formularze systemu Windows <xref:System.Windows.Forms.Label> formanty są używane do wyświetlania tekstu lub obrazów, które nie mogą być edytowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2f0ec-103">Windows Forms <xref:System.Windows.Forms.Label> controls are used to display text or images that cannot be edited by the user.</span></span> <span data-ttu-id="2f0ec-104">Są one używane do identyfikowania obiektów na formularzu — podaj opis jaką dany formant będzie wykonywać na przykład po kliknięciu lub wyświetlać informacje w odpowiedzi na zdarzenie środowiska wykonawczego lub proces w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2f0ec-104">They are used to identify objects on a form — to provide a description of what a certain control will do if clicked, for example, or to display information in response to a run-time event or process in your application.</span></span> <span data-ttu-id="2f0ec-105">Na przykład można etykiety Dodawanie opisową podpisów do pól tekstowych, pola listy, pola kombi itd.</span><span class="sxs-lookup"><span data-stu-id="2f0ec-105">For example, you can use labels to add descriptive captions to text boxes, list boxes, combo boxes, and so on.</span></span> <span data-ttu-id="2f0ec-106">Można również napisać kod, który zmienia tekst wyświetlany przez etykiety w odpowiedzi na zdarzenia w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="2f0ec-106">You can also write code that changes the text displayed by a label in response to events at run time.</span></span> <span data-ttu-id="2f0ec-107">Na przykład aplikacja zajmuje kilka minut przetwarzania zmian, można wyświetlić komunikat o stanie przetwarzania w etykiecie.</span><span class="sxs-lookup"><span data-stu-id="2f0ec-107">For example, if your application takes a few minutes to process a change, you can display a processing-status message in a label.</span></span>  
  
## <a name="working-with-the-label-control"></a><span data-ttu-id="2f0ec-108">Praca z formantem etykiety</span><span class="sxs-lookup"><span data-stu-id="2f0ec-108">Working with the Label Control</span></span>  
 <span data-ttu-id="2f0ec-109">Ponieważ <xref:System.Windows.Forms.Label> formantu nie można ustawić fokusu, może również służyć do tworzenia kluczy dostępu dla innych formantów.</span><span class="sxs-lookup"><span data-stu-id="2f0ec-109">Because the <xref:System.Windows.Forms.Label> control cannot receive the focus, it can also be used to create access keys for other controls.</span></span> <span data-ttu-id="2f0ec-110">Klucz dostępu umożliwia użytkownikowi wybranie innego formantu, naciskając klawisz ALT z kluczem dostępu.</span><span class="sxs-lookup"><span data-stu-id="2f0ec-110">An access key allows a user to select the other control by pressing the ALT key with the access key.</span></span> <span data-ttu-id="2f0ec-111">Aby uzyskać więcej informacji, zobacz [tworzenie dostępu do kluczy dla formantów formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) i [porady: Tworzenie klawiszy dostępu z formantów etykiet formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md).</span><span class="sxs-lookup"><span data-stu-id="2f0ec-111">For more information, see [Creating Access Keys for Windows Forms Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-for-windows-forms-controls.md) and [How to: Create Access Keys with Windows Forms Label Controls](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md).</span></span>  
  
 <span data-ttu-id="2f0ec-112">Podpis wyświetlany w etykiecie znajduje się w <xref:System.Windows.Forms.Label.Text%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2f0ec-112">The caption displayed in the label is contained in the <xref:System.Windows.Forms.Label.Text%2A> property.</span></span> <span data-ttu-id="2f0ec-113"><xref:System.Windows.Forms.Label.TextAlign%2A> Właściwości można ustawić wyrównania tekstu w etykiecie.</span><span class="sxs-lookup"><span data-stu-id="2f0ec-113">The <xref:System.Windows.Forms.Label.TextAlign%2A> property allows you to set the alignment of the text within the label.</span></span> <span data-ttu-id="2f0ec-114">Aby uzyskać więcej informacji, zobacz [porady: Ustawianie tekst wyświetlany przez formant formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span><span class="sxs-lookup"><span data-stu-id="2f0ec-114">For more information, see [How to: Set the Text Displayed by a Windows Forms Control](../../../../docs/framework/winforms/controls/how-to-set-the-text-displayed-by-a-windows-forms-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f0ec-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f0ec-115">See Also</span></span>  
 <xref:System.Windows.Forms.Label>  
 [<span data-ttu-id="2f0ec-116">Porady: rozmiar formantu etykiety pasujący do jego zawartości formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2f0ec-116">How to: Size a Windows Forms Label Control to Fit Its Contents</span></span>](../../../../docs/framework/winforms/controls/how-to-size-a-windows-forms-label-control-to-fit-its-contents.md)  
 [<span data-ttu-id="2f0ec-117">Porady: Tworzenie klawiszy dostępu za pomocą formantów etykiet formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="2f0ec-117">How to: Create Access Keys with Windows Forms Label Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-create-access-keys-with-windows-forms-label-controls.md)