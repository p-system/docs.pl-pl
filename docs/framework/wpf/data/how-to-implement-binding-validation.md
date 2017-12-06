---
title: "Jak implementować powiązaną walidację"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- validation of binding [WPF]
- data binding [WPF], validation of binding
- binding [WPF], validation of
ms.assetid: eb98b33d-9866-49ae-b981-bc5ff20d607a
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec860cc9cc58febd98d8642c98a50ec296592d02
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-implement-binding-validation"></a><span data-ttu-id="95dbc-102">Jak implementować powiązaną walidację</span><span class="sxs-lookup"><span data-stu-id="95dbc-102">How to: Implement Binding Validation</span></span>
<span data-ttu-id="95dbc-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> i wyzwalacz style wizualne, aby poinformować użytkownika, gdy wprowadzono nieprawidłową wartość oparte na niestandardowej reguły walidacji.</span><span class="sxs-lookup"><span data-stu-id="95dbc-103">This example shows how to use an <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> and a style trigger to provide visual feedback to inform the user when an invalid value is entered, based on a custom validation rule.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95dbc-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="95dbc-104">Example</span></span>  
 <span data-ttu-id="95dbc-105">Zawartość tekstu <xref:System.Windows.Controls.TextBox> w poniższym przykładzie jest powiązany z `Age` właściwości (typ int) obiektu źródła powiązanie o nazwie `ods`.</span><span class="sxs-lookup"><span data-stu-id="95dbc-105">The text content of the <xref:System.Windows.Controls.TextBox> in the following example is bound to the `Age` property (of type int) of a binding source object named `ods`.</span></span> <span data-ttu-id="95dbc-106">Powiązanie jest skonfigurowany do użycia reguły sprawdzania poprawności, o nazwie `AgeRangeRule` tak, aby po wprowadzeniu znaków nienumerycznych lub wartość, która jest mniejsza niż 21 lub większa niż 130, czerwony wykrzyknik jest wyświetlany obok pola tekstowego, a podpowiedzi z komunikatem o błędzie gdzie n użytkownik przesuwa wskaźnik myszy nad pole tekstowe.</span><span class="sxs-lookup"><span data-stu-id="95dbc-106">The binding is set up to use a validation rule named `AgeRangeRule` so that if the user enters non-numeric characters or a value that is smaller than 21 or greater than 130, a red exclamation mark appears next to the text box and a tool tip with the error message appears when the user moves the mouse over the text box.</span></span>  
  
 [!code-xaml[BindValidation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="95dbc-107">Poniższy przykład przedstawia implementację `AgeRangeRule`, który dziedziczy z <xref:System.Windows.Controls.ValidationRule> i zastępuje <xref:System.Windows.Controls.ValidationRule.Validate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="95dbc-107">The following example shows the implementation of `AgeRangeRule`, which inherits from <xref:System.Windows.Controls.ValidationRule> and overrides the <xref:System.Windows.Controls.ValidationRule.Validate%2A> method.</span></span> <span data-ttu-id="95dbc-108">Metoda Int32.Parse() jest wywoływana na wartość, aby upewnić się, że nie zawiera nieprawidłowych znaków.</span><span class="sxs-lookup"><span data-stu-id="95dbc-108">The Int32.Parse() method is called on the value to make sure that it does not contain any invalid characters.</span></span> <span data-ttu-id="95dbc-109"><xref:System.Windows.Controls.ValidationRule.Validate%2A> Metoda zwraca <xref:System.Windows.Controls.ValidationResult> wskazujące, że jeśli wartość jest prawidłowa na podstawie tego, czy zostanie przechwycony wyjątek podczas analizowania i określa, czy wartość wieku znajduje się poza dolną i górną granicę.</span><span class="sxs-lookup"><span data-stu-id="95dbc-109">The <xref:System.Windows.Controls.ValidationRule.Validate%2A> method returns a <xref:System.Windows.Controls.ValidationResult> that indicates if the value is valid based on whether an exception is caught during the parsing and whether the age value is outside of the lower and upper bounds.</span></span>  
  
 [!code-csharp[BindValidation#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/AgeRangeRule.cs#3)]  
  
 <span data-ttu-id="95dbc-110">W poniższym przykładzie przedstawiono niestandardowego <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` tworzącą czerwony wykrzyknik w celu powiadomienia użytkownika Błąd sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="95dbc-110">The following example shows the custom <xref:System.Windows.Controls.ControlTemplate> `validationTemplate` that creates a red exclamation mark to notify the user of a validation error.</span></span> <span data-ttu-id="95dbc-111">Formant szablony są używane do ponownego zdefiniowania wyglądu formantu.</span><span class="sxs-lookup"><span data-stu-id="95dbc-111">Control templates are used to redefine the appearance of a control.</span></span>  
  
 [!code-xaml[BindValidation#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#4)]  
  
 <span data-ttu-id="95dbc-112">Jak pokazano w poniższym przykładzie <xref:System.Windows.Controls.ToolTip> który zawiera komunikat o błędzie jest tworzony przy użyciu style o nazwie `textBoxInError`.</span><span class="sxs-lookup"><span data-stu-id="95dbc-112">As shown in the following example, the <xref:System.Windows.Controls.ToolTip> that shows the error message is created using the style named `textBoxInError`.</span></span> <span data-ttu-id="95dbc-113">Jeśli wartość <xref:System.Windows.Controls.Validation.HasError%2A> jest `true`, wyzwalacz ustawia podpowiedzi bieżącego <xref:System.Windows.Controls.TextBox> do jego pierwszego błędu sprawdzania poprawności.</span><span class="sxs-lookup"><span data-stu-id="95dbc-113">If the value of <xref:System.Windows.Controls.Validation.HasError%2A> is `true`, the trigger sets the tool tip of the current <xref:System.Windows.Controls.TextBox> to its first validation error.</span></span> <span data-ttu-id="95dbc-114"><xref:System.Windows.Data.Binding.RelativeSource%2A> Ustawiono <xref:System.Windows.Data.RelativeSourceMode.Self>odwołujący się do bieżącego elementu.</span><span class="sxs-lookup"><span data-stu-id="95dbc-114">The <xref:System.Windows.Data.Binding.RelativeSource%2A> is set to <xref:System.Windows.Data.RelativeSourceMode.Self>, referring to the current element.</span></span>  
  
 [!code-xaml[BindValidation#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindValidation/CSharp/Window1.xaml#5)]  
  
 <span data-ttu-id="95dbc-115">Aby uzyskać pełny przykład, zobacz [powiązania przykładowych weryfikacji](http://go.microsoft.com/fwlink/?LinkID=159972).</span><span class="sxs-lookup"><span data-stu-id="95dbc-115">For the complete example, see [Binding Validation Sample](http://go.microsoft.com/fwlink/?LinkID=159972).</span></span>  
  
 <span data-ttu-id="95dbc-116">Należy pamiętać, że jeśli nie podasz niestandardowego <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> domyślny szablon błąd powinien zapewniać wizualne użytkownikowi, gdy występuje błąd weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="95dbc-116">Note that if you do not provide a custom <xref:System.Windows.Controls.Validation.ErrorTemplate%2A> the default error template appears to provide visual feedback to the user when there is a validation error.</span></span> <span data-ttu-id="95dbc-117">Zobacz "Sprawdzanie poprawności danych" w [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="95dbc-117">See "Data Validation" in [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md) for more information.</span></span> <span data-ttu-id="95dbc-118">Ponadto [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] zawiera reguły poprawności wbudowanych przechwytuje wyjątków, które są generowane podczas aktualizacji powiązania właściwości source.</span><span class="sxs-lookup"><span data-stu-id="95dbc-118">Also, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] provides a built-in validation rule that catches exceptions that are thrown during the update of the binding source property.</span></span> <span data-ttu-id="95dbc-119">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.Controls.ExceptionValidationRule>.</span><span class="sxs-lookup"><span data-stu-id="95dbc-119">For more information, see <xref:System.Windows.Controls.ExceptionValidationRule>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95dbc-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95dbc-120">See Also</span></span>  
 [<span data-ttu-id="95dbc-121">Omówienie powiązania danych</span><span class="sxs-lookup"><span data-stu-id="95dbc-121">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="95dbc-122">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="95dbc-122">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)