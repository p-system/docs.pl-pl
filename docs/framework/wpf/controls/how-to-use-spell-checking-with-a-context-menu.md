---
title: "Jak użyć sprawdzania pisowni z menu kontekstowym"
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
- enabling spell checking in a text box [WPF]
- reenabling spell checking in a text box [WPF]
- spell checking with a context menu [WPF]
ms.assetid: 61f69a20-2ff3-4056-9060-e32f4483ec5e
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 257f343a7fa01e251159797a83e89b533292b6b8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-spell-checking-with-a-context-menu"></a><span data-ttu-id="af04d-102">Jak użyć sprawdzania pisowni z menu kontekstowym</span><span class="sxs-lookup"><span data-stu-id="af04d-102">How to: Use Spell Checking with a Context Menu</span></span>
<span data-ttu-id="af04d-103">Domyślnie po włączeniu sprawdzania w formancie edycji pisowni, takich jak <xref:System.Windows.Controls.TextBox> lub <xref:System.Windows.Controls.RichTextBox>, Pobierz sprawdzanie pisowni wybory w menu kontekstowym.</span><span class="sxs-lookup"><span data-stu-id="af04d-103">By default, when you enable spell checking in an editing control like <xref:System.Windows.Controls.TextBox> or <xref:System.Windows.Controls.RichTextBox>, you get spell-checking choices in the context menu.</span></span> <span data-ttu-id="af04d-104">Na przykład po użytkowników prawym przyciskiem myszy wyrazu otrzymują zestaw sugestie dotyczące pisowni lub opcję **Ignoruj wszystkie**.</span><span class="sxs-lookup"><span data-stu-id="af04d-104">For example, when users right-click a misspelled word, they get a set of spelling suggestions or the option to **Ignore All**.</span></span> <span data-ttu-id="af04d-105">Jednak aby zastąpić domyślne menu kontekstowe z własnych menu kontekstowe niestandardowych, te funkcje zostaną utracone i trzeba napisać kod, aby ponownie włączyć funkcję Sprawdzanie pisowni w menu kontekstowym.</span><span class="sxs-lookup"><span data-stu-id="af04d-105">However, when you override the default context menu with your own custom context menu, this functionality is lost, and you need to write code to reenable the spell-checking feature in the context menu.</span></span> <span data-ttu-id="af04d-106">Poniższy przykład pokazuje, jak je włączyć na <xref:System.Windows.Controls.TextBox>.</span><span class="sxs-lookup"><span data-stu-id="af04d-106">The following example shows how to enable this on a <xref:System.Windows.Controls.TextBox>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="af04d-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="af04d-107">Example</span></span>  
 <span data-ttu-id="af04d-108">W poniższym przykładzie przedstawiono [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] tworzącą <xref:System.Windows.Controls.TextBox> z niektórych zdarzeń, które są używane do implementowania menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="af04d-108">The following example shows the [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] that creates a <xref:System.Windows.Controls.TextBox> with some events that are used to implement the context menu.</span></span>  
  
 [!code-xaml[TextBoxMiscSnippets_snip#SpellerCustomContextMenuExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml#spellercustomcontextmenuexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="af04d-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="af04d-109">Example</span></span>  
 <span data-ttu-id="af04d-110">Poniższy przykład przedstawia kod, który implementuje menu kontekstowego.</span><span class="sxs-lookup"><span data-stu-id="af04d-110">The following example shows the code that implements the context menu.</span></span>  
  
 [!code-csharp[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/speller_custom_context_menu.xaml.cs#spellercustomcontextmenucodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#SpellerCustomContextMenuCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/speller_custom_context_menu.xaml.vb#spellercustomcontextmenucodeexamplewholepage)]  
  
 <span data-ttu-id="af04d-111">Kod używany w przypadku tej z <xref:System.Windows.Controls.RichTextBox> przypomina.</span><span class="sxs-lookup"><span data-stu-id="af04d-111">The code used for doing this with a <xref:System.Windows.Controls.RichTextBox> is similar.</span></span> <span data-ttu-id="af04d-112">Główną różnicą jest parametr przekazany do `GetSpellingError` metody.</span><span class="sxs-lookup"><span data-stu-id="af04d-112">The main difference is in the parameter passed to the `GetSpellingError` method.</span></span> <span data-ttu-id="af04d-113">Aby uzyskać <xref:System.Windows.Controls.TextBox>, Przekaż indeks całkowitą położenia karetki:</span><span class="sxs-lookup"><span data-stu-id="af04d-113">For a <xref:System.Windows.Controls.TextBox>, pass the integer index of the caret position:</span></span>  
  
 `spellingError = myTextBox.GetSpellingError(caretIndex);`  
  
 <span data-ttu-id="af04d-114">Aby uzyskać <xref:System.Windows.Controls.RichTextBox>, Przekaż <xref:System.Windows.Documents.TextPointer> położenia karetki, który określa:</span><span class="sxs-lookup"><span data-stu-id="af04d-114">For a <xref:System.Windows.Controls.RichTextBox>, pass the <xref:System.Windows.Documents.TextPointer> that specifies the caret position:</span></span>  
  
 `spellingError = myRichTextBox.GetSpellingError(myRichTextBox.CaretPosition);`  
  
## <a name="see-also"></a><span data-ttu-id="af04d-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af04d-115">See Also</span></span>  
 [<span data-ttu-id="af04d-116">TextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="af04d-116">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="af04d-117">RichTextBox — omówienie</span><span class="sxs-lookup"><span data-stu-id="af04d-117">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="af04d-118">Włącz sprawdzanie w formancie edycji tekstu pisowni</span><span class="sxs-lookup"><span data-stu-id="af04d-118">Enable Spell Checking in a Text Editing Control</span></span>](../../../../docs/framework/wpf/controls/how-to-enable-spell-checking-in-a-text-editing-control.md)  
 [<span data-ttu-id="af04d-119">Menu kontekstowe niestandardowych za pomocą pola tekstowego</span><span class="sxs-lookup"><span data-stu-id="af04d-119">Use a Custom Context Menu with a TextBox</span></span>](../../../../docs/framework/wpf/controls/how-to-use-a-custom-context-menu-with-a-textbox.md)