---
title: "Połączone słowniki zasobów"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- merged resource dictionaries [WPF]
- dictionaries [WPF], merged resources
ms.assetid: d159531f-05d4-49fd-b951-c332de51e5bc
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ce02b772bacf2115a1bb74039fdff30a46fea8b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="merged-resource-dictionaries"></a><span data-ttu-id="3f9c4-102">Połączone słowniki zasobów</span><span class="sxs-lookup"><span data-stu-id="3f9c4-102">Merged Resource Dictionaries</span></span>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]<span data-ttu-id="3f9c4-103">zasoby obsługuje funkcji słownika zasobów scalone.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-103"> resources support a merged resource dictionary feature.</span></span> <span data-ttu-id="3f9c4-104">Ta funkcja udostępnia sposób definiowania zasobów część [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacji poza skompilowanych [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-104">This feature provides a way to define the resources portion of a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] application outside of the compiled [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] application.</span></span> <span data-ttu-id="3f9c4-105">Następnie można udostępniać zasoby w aplikacjach i są również więcej wygodny sposób izolowany lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-105">Resources can then be shared across applications and are also more conveniently isolated for localization.</span></span>  
  
## <a name="introducing-a-merged-resource-dictionary"></a><span data-ttu-id="3f9c4-106">Wprowadzenie do słownika zasobów scalony</span><span class="sxs-lookup"><span data-stu-id="3f9c4-106">Introducing a Merged Resource Dictionary</span></span>  
 <span data-ttu-id="3f9c4-107">W znaczniku można użyć następującej składni wprowadzenie słownik zasobów scalone do strony:</span><span class="sxs-lookup"><span data-stu-id="3f9c4-107">In markup, you use the following syntax to introduce a merged resource dictionary into a page:</span></span>  
  
 [!code-xaml[ResourceMergeDictionary#MergedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ResourceMergeDictionary/CS/default.xaml#mergedxaml)]  
  
 <span data-ttu-id="3f9c4-108">Należy pamiętać, że <xref:System.Windows.ResourceDictionary> element nie ma [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md), które są zazwyczaj wymagane dla wszystkich elementów w kolekcji zasobów.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-108">Note that the <xref:System.Windows.ResourceDictionary> element does not have an [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md), which is generally required for all items in a resource collection.</span></span> <span data-ttu-id="3f9c4-109">Ale innego <xref:System.Windows.ResourceDictionary> odwołanie w <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekcja jest szczególnych przypadkach, zarezerwowane dla tego scenariusza słownika zasobów scalone.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-109">But another <xref:System.Windows.ResourceDictionary> reference within the <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> collection is a special case, reserved for this merged resource dictionary scenario.</span></span> <span data-ttu-id="3f9c4-110"><xref:System.Windows.ResourceDictionary> Powoduje to wprowadzenie scalone słownik zasobów nie może mieć [dyrektywy x: Key](../../../../docs/framework/xaml-services/x-key-directive.md).</span><span class="sxs-lookup"><span data-stu-id="3f9c4-110">The <xref:System.Windows.ResourceDictionary> that introduces a merged resource dictionary cannot have an [x:Key Directive](../../../../docs/framework/xaml-services/x-key-directive.md).</span></span> <span data-ttu-id="3f9c4-111">Zazwyczaj każdego <xref:System.Windows.ResourceDictionary> w <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> określa kolekcji <xref:System.Windows.ResourceDictionary.Source%2A> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-111">Typically, each <xref:System.Windows.ResourceDictionary> within the <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> collection specifies a <xref:System.Windows.ResourceDictionary.Source%2A> attribute.</span></span> <span data-ttu-id="3f9c4-112">Wartość <xref:System.Windows.ResourceDictionary.Source%2A> powinien być [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] rozwiązań do lokalizacji pliku zasobów do scalenia.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-112">The value of <xref:System.Windows.ResourceDictionary.Source%2A> should be a [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] that resolves to the location of the resources file to be merged.</span></span> <span data-ttu-id="3f9c4-113">Miejsce docelowe tego [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] musi być inny [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] pliku z <xref:System.Windows.ResourceDictionary> jako jego elementu głównego.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-113">The destination of that [!INCLUDE[TLA2#tla_uri](../../../../includes/tla2sharptla-uri-md.md)] must be another [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file, with <xref:System.Windows.ResourceDictionary> as its root element.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f9c4-114">Aby zdefiniować zasoby w ramach dozwolone <xref:System.Windows.ResourceDictionary> jako alternatywę do określania, który jest określony jako słownika scalone <xref:System.Windows.ResourceDictionary.Source%2A>, lub oprócz uwzględniono niezależnie od zasobów z określonego źródła.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-114">It is legal to define resources within a <xref:System.Windows.ResourceDictionary> that is specified as a merged dictionary, either as an alternative to specifying <xref:System.Windows.ResourceDictionary.Source%2A>, or in addition to whatever resources are included from the specified source.</span></span> <span data-ttu-id="3f9c4-115">Jednak to nie jest typowym scenariuszem; główne scenariusz scalonych słownikach polega na scaleniu zasobów z lokalizacji zewnętrznych plików.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-115">However, this is not a common scenario; the main scenario for merged dictionaries is to merge resources from external file locations.</span></span> <span data-ttu-id="3f9c4-116">Jeśli chcesz określić zasobów w ramach znaczników strony, należy zwykle zdefiniować w głównym <xref:System.Windows.ResourceDictionary> , a nie w scalonych słownikach.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-116">If you want to specify resources within the markup for a page, you should typically define these in the main <xref:System.Windows.ResourceDictionary> and not in the merged dictionaries.</span></span>  
  
## <a name="merged-dictionary-behavior"></a><span data-ttu-id="3f9c4-117">Zachowanie połączony słownik</span><span class="sxs-lookup"><span data-stu-id="3f9c4-117">Merged Dictionary Behavior</span></span>  
 <span data-ttu-id="3f9c4-118">Zasoby w scalonych słownikach zajmują miejsce w zakres wyszukiwania zasobów, który jest zaraz po zakres słownik zasobów główne, które zostaną scalone.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-118">Resources in a merged dictionary occupy a location in the resource lookup scope that is just after the scope of the main resource dictionary they are merged into.</span></span> <span data-ttu-id="3f9c4-119">Mimo że klucza zasobów muszą być unikatowe w dowolnej poszczególnych słownika, klucz może istnieć wiele razy w zestawie scalonych słownikach.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-119">Although a resource key must be unique within any individual dictionary, a key can exist multiple times in a set of merged dictionaries.</span></span> <span data-ttu-id="3f9c4-120">W takim przypadku zasobów, która jest zwracana będzie pochodził z ostatnich słownik znaleziono sekwencyjnie w <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-120">In this case, the resource that is returned will come from the last dictionary found sequentially in the <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> collection.</span></span> <span data-ttu-id="3f9c4-121">Jeśli <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> kolekcji został zdefiniowany w [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], kolejność scalonych słownikach w kolekcji to kolejność elementów, zgodnie z znaczników.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-121">If the <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> collection was defined in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], then the order of the merged dictionaries in the collection is the order of the elements as provided in the markup.</span></span> <span data-ttu-id="3f9c4-122">Jeśli klucz jest zdefiniowany w podstawowym słowniku, a także w słowniku, który został scalony, zasobów, która jest zwracana będzie pochodził z podstawowego słownika.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-122">If a key is defined in the primary dictionary and also in a dictionary that was merged, then the resource that is returned will come from the primary dictionary.</span></span> <span data-ttu-id="3f9c4-123">Tych reguł ustawiania zakresu stosowane jednakowo dla odwołania do zasobu statycznych i dynamicznych zasobów odwołań.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-123">These scoping rules apply equally for both static resource references and dynamic resource references.</span></span>  
  
### <a name="merged-dictionaries-and-code"></a><span data-ttu-id="3f9c4-124">Scalonych słownikach i kod</span><span class="sxs-lookup"><span data-stu-id="3f9c4-124">Merged Dictionaries and Code</span></span>  
 <span data-ttu-id="3f9c4-125">Scalonych słownikach mogą być dodawane do `Resources` słownika przy użyciu kodu.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-125">Merged dictionaries can be added to a `Resources` dictionary through code.</span></span> <span data-ttu-id="3f9c4-126">Wartość domyślna jest początkowo pusta <xref:System.Windows.ResourceDictionary> znajdujące się w każdej `Resources` właściwość również ma wartość domyślną, początkowo pusta <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> właściwości kolekcji.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-126">The default, initially empty <xref:System.Windows.ResourceDictionary> that exists for any `Resources` property also has a default, initially empty <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> collection property.</span></span> <span data-ttu-id="3f9c4-127">Aby dodać scalonych słownika przy użyciu kodu, należy uzyskać odwołanie do podstawowej żądany <xref:System.Windows.ResourceDictionary>, pobrać jego <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> wartość właściwości i wywołanie `Add` na ogólnej `Collection` zawarte w <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-127">To add a merged dictionary through code, you obtain a reference to the desired primary <xref:System.Windows.ResourceDictionary>, get its <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A> property value, and call `Add` on the generic `Collection` that is contained in <xref:System.Windows.ResourceDictionary.MergedDictionaries%2A>.</span></span> <span data-ttu-id="3f9c4-128">Możesz dodać obiekt musi być nowy <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-128">The object you add must be a new <xref:System.Windows.ResourceDictionary>.</span></span> <span data-ttu-id="3f9c4-129">W kodzie, nie należy ustawiać <xref:System.Windows.ResourceDictionary.Source%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-129">In code, you do not set the <xref:System.Windows.ResourceDictionary.Source%2A> property.</span></span> <span data-ttu-id="3f9c4-130">Zamiast tego należy uzyskać <xref:System.Windows.ResourceDictionary> obiektu przez utworzenie jednego lub jeden ładowania.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-130">Instead, you must obtain a <xref:System.Windows.ResourceDictionary> object by either creating one or loading one.</span></span> <span data-ttu-id="3f9c4-131">Aby załadować istniejący <xref:System.Windows.ResourceDictionary> do wywołania <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> na istniejącym [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] strumień plików, który ma <xref:System.Windows.ResourceDictionary> katalogu głównego, następnie rzutowanie <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> zwrócić wartość do <xref:System.Windows.ResourceDictionary>.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-131">One way to load an existing <xref:System.Windows.ResourceDictionary> to call <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> on an existing [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file stream that has a <xref:System.Windows.ResourceDictionary> root, then casting the <xref:System.Windows.Markup.XamlReader.Load%2A?displayProperty=nameWithType> return value to <xref:System.Windows.ResourceDictionary>.</span></span>  
  
### <a name="merged-resource-dictionary-uris"></a><span data-ttu-id="3f9c4-132">Identyfikatory URI słownika zasobów scalony</span><span class="sxs-lookup"><span data-stu-id="3f9c4-132">Merged Resource Dictionary URIs</span></span>  
 <span data-ttu-id="3f9c4-133">Istnieje kilka technik sposobu obejmują słownik scalonych zasobów, które są oznaczone [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] formatu, który będzie używany.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-133">There are several techniques for how to include a merged resource dictionary, which are indicated by the [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)] format that you will use.</span></span> <span data-ttu-id="3f9c4-134">Ogólnie rzecz biorąc, te techniki można podzielić na dwie kategorie: zasoby, które są kompilowane jako część projektu i zasobów, które nie są kompilowane w ramach projektu.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-134">Broadly speaking, these techniques can be divided into two categories: resources that are compiled as part of the project, and resources that are not compiled as part of the project.</span></span>  
  
 <span data-ttu-id="3f9c4-135">Dla zasobów, które są kompilowane w ramach projektu można użyć ścieżki względnej, która odwołuje się do lokalizacji zasobów.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-135">For resources that are compiled as part of the project, you can use a relative path that refers to the resource location.</span></span> <span data-ttu-id="3f9c4-136">Ścieżka względna jest oceniane podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-136">The relative path is evaluated during compilation.</span></span> <span data-ttu-id="3f9c4-137">Zasób musi być zdefiniowany jako część projektu jako akcja kompilacji zasobu.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-137">Your resource must be defined as part of the project as a Resource build action.</span></span> <span data-ttu-id="3f9c4-138">Jeśli plik .xaml zasobów w projekcie jako zasób, nie trzeba kopiować pliku zasobu do katalogu wyjściowego, zasób jest już uwzględniona w obrębie skompilowanej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-138">If you include a resource .xaml file in the project as Resource, you do not need to copy the resource file to the output directory, the resource is already included within the compiled application.</span></span> <span data-ttu-id="3f9c4-139">Można również użyć akcji kompilacji zawartości, ale należy następnie skopiuj pliki do katalogu wyjściowego oraz wdrożyć pliki zasobów w tej samej relacji ścieżka do pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-139">You can also use Content build action, but you must then copy the files to the output directory and also deploy the resource files in the same path relationship to the executable.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3f9c4-140">Nie należy używać akcji kompilacji osadzony zasób.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-140">Do not use the Embedded Resource build action.</span></span> <span data-ttu-id="3f9c4-141">Akcja kompilacji, sama jest obsługiwana dla [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikacje, ale rozpoznanie <xref:System.Windows.ResourceDictionary.Source%2A> nie obejmuje <xref:System.Resources.ResourceManager>i dlatego nie można oddzielić pojedynczego zasobu spoza strumienia.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-141">The build action itself is supported for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications, but the resolution of <xref:System.Windows.ResourceDictionary.Source%2A> does not incorporate <xref:System.Resources.ResourceManager>, and thus cannot separate the individual resource out of the stream.</span></span> <span data-ttu-id="3f9c4-142">Można nadal używać osadzonego zasobu do innych celów, tak długo, jak również używane <xref:System.Resources.ResourceManager> dostęp do zasobów.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-142">You could still use Embedded Resource for other purposes so long as you also used <xref:System.Resources.ResourceManager> to access the resources.</span></span>  
  
 <span data-ttu-id="3f9c4-143">Powiązane technika jest użycie identyfikatora URI Pack do [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] plików i odwołuje się do niego jako źródło.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-143">A related technique is to use a Pack URI to a [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] file, and refer to it as Source.</span></span> <span data-ttu-id="3f9c4-144">Adres URI pakietu umożliwia odwołania do składników zestawów występujących w odwołaniach i innych technik.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-144">Pack URI enables references to components of referenced assemblies and other techniques.</span></span> <span data-ttu-id="3f9c4-145">Aby uzyskać więcej informacji na identyfikatory URI pakietu, zobacz [zasób w aplikacji WPF, zawartość i pliki danych](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).</span><span class="sxs-lookup"><span data-stu-id="3f9c4-145">For more information on Pack URIs, see [WPF Application Resource, Content, and Data Files](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md).</span></span>  
  
 <span data-ttu-id="3f9c4-146">Dla zasobów, które nie są kompilowane w ramach projektu identyfikator URI jest oceniane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-146">For resources that are not compiled as part of the project, the URI is evaluated at run time.</span></span> <span data-ttu-id="3f9c4-147">Np. w pliku można użyć typowych transportu identyfikatora URI: lub http: Aby odwołać się do pliku zasobów.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-147">You can use a common URI transport such as file: or http: to refer to the resource file.</span></span> <span data-ttu-id="3f9c4-148">Wadą podejście Nieskompilowane zasobów jest ten plik: dostępu wymaga dodatkowe kroki wdrażania i http: dostępu oznacza strefy zabezpieczeń Internet.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-148">The disadvantage of using the noncompiled resource approach is that file: access requires additional deployment steps, and http: access implies the Internet security zone.</span></span>  
  
### <a name="reusing-merged-dictionaries"></a><span data-ttu-id="3f9c4-149">Ponowne wykorzystywanie scalonych słownikach</span><span class="sxs-lookup"><span data-stu-id="3f9c4-149">Reusing Merged Dictionaries</span></span>  
 <span data-ttu-id="3f9c4-150">Można użyć ponownie lub udostępnić scalonych słownikach zasobów między aplikacjami, ponieważ można scalić słownika zasobów może być przywoływany przez dowolne prawidłowe [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3f9c4-150">You can reuse or share merged resource dictionaries between applications, because the resource dictionary to merge can be referenced through any valid [!INCLUDE[TLA#tla_uri](../../../../includes/tlasharptla-uri-md.md)].</span></span> <span data-ttu-id="3f9c4-151">Dokładnie tak jak to będzie zależeć od strategii wdrażania aplikacji i która aplikacja modelu należy wykonać.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-151">Exactly how you do this will depend on your application deployment strategy and which application model you follow.</span></span> <span data-ttu-id="3f9c4-152">Wyżej wymienione strategii identyfikatora URI elementu Pack umożliwia często źródła scalonych zasobów w wielu projektach podczas tworzenia za pomocą udostępniania odwołania do zestawu.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-152">The aforementioned Pack URI strategy provides a way to commonly source a merged resource across multiple projects during development by sharing an assembly reference.</span></span> <span data-ttu-id="3f9c4-153">W tym scenariuszu zasoby nadal są dystrybuowane przez klienta, a co najmniej jedną z aplikacji, należy wdrożyć przywoływanego zestawu.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-153">In this scenario the resources are still distributed by the client, and at least one of the applications must deploy the referenced assembly.</span></span> <span data-ttu-id="3f9c4-154">Istnieje również możliwość odwołania scalonych zasobów za pomocą rozproszonego identyfikator URI, który korzysta z protokołu http.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-154">It is also possible to reference merged resources through a distributed URI that uses the http protocol.</span></span>  
  
 <span data-ttu-id="3f9c4-155">Zapisywanie scalonych słownikach miejscowego plików lub do lokalnego magazynu udostępnionego jest inny możliwe słownik scalonych / scenariusz wdrażania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-155">Writing merged dictionaries as local application files or to local shared storage is another possible merged dictionary / application deployment scenario.</span></span>  
  
### <a name="localization"></a><span data-ttu-id="3f9c4-156">Lokalizacja</span><span class="sxs-lookup"><span data-stu-id="3f9c4-156">Localization</span></span>  
 <span data-ttu-id="3f9c4-157">Jeśli zasoby, które muszą być lokalizowany są izolowane do słowników, które scalone z podstawowego słownika i przechowywane jako utracić [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], te pliki, które może być lokalizowany oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-157">If resources that need to be localized are isolated to dictionaries that are merged into primary dictionaries, and kept as loose [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], these files can be localized separately.</span></span> <span data-ttu-id="3f9c4-158">Ta technika jest lekki alternatywą do lokalizowania zestawów satelickich zasobów.</span><span class="sxs-lookup"><span data-stu-id="3f9c4-158">This technique is a lightweight alternative to localizing  the satellite resource assemblies.</span></span> <span data-ttu-id="3f9c4-159">Aby uzyskać więcej informacji, zobacz [omówienie lokalizacja i globalizacja WPF](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3f9c4-159">For details, see [WPF Globalization and Localization Overview](../../../../docs/framework/wpf/advanced/wpf-globalization-and-localization-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f9c4-160">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f9c4-160">See Also</span></span>  
 <xref:System.Windows.ResourceDictionary>  
 [<span data-ttu-id="3f9c4-161">Zasoby dla języka XAML</span><span class="sxs-lookup"><span data-stu-id="3f9c4-161">XAML Resources</span></span>](../../../../docs/framework/wpf/advanced/xaml-resources.md)  
 [<span data-ttu-id="3f9c4-162">Zasoby i kod</span><span class="sxs-lookup"><span data-stu-id="3f9c4-162">Resources and Code</span></span>](../../../../docs/framework/wpf/advanced/resources-and-code.md)  
 [<span data-ttu-id="3f9c4-163">Zasób w aplikacji WPF, zawartość i plików danych</span><span class="sxs-lookup"><span data-stu-id="3f9c4-163">WPF Application Resource, Content, and Data Files</span></span>](../../../../docs/framework/wpf/app-development/wpf-application-resource-content-and-data-files.md)