---
title: "x:Array — Rozszerzenie znaczników"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- x:Array
- xArray
helpviewer_keywords:
- x:Array [XAML Services]
- XAML [XAML Services], x:Array markup extension
ms.assetid: c5358e14-d24c-44c7-b5eb-6062a4fd981c
caps.latest.revision: "20"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 2cefdee5ca2d1b0a6c79325365aa101d767b6926
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="xarray-markup-extension"></a><span data-ttu-id="6f1a6-102">x:Array — Rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="6f1a6-102">x:Array Markup Extension</span></span>
<span data-ttu-id="6f1a6-103">Zapewnia obsługę ogólne dla tablic obiektów w języku XAML, za pomocą rozszerzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-103">Provides general support for arrays of objects in XAML through a markup extension.</span></span> <span data-ttu-id="6f1a6-104">Odpowiada to `x:ArrayExtension` typu XAML w [MS-XAML].</span><span class="sxs-lookup"><span data-stu-id="6f1a6-104">This corresponds to the `x:ArrayExtension` XAML type in [MS-XAML].</span></span>  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="6f1a6-105">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="6f1a6-105">XAML Object Element Usage</span></span>  
  
```  
<x:Array Type="typeName">  
  arrayContents  
</x:Array>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="6f1a6-106">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="6f1a6-106">XAML Values</span></span>  
  
|||  
|-|-|  
|`typeName`|<span data-ttu-id="6f1a6-107">Nazwa typu który Twojej `x:Array` będzie zawierać.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-107">The name of the type that your `x:Array` will contain.</span></span> <span data-ttu-id="6f1a6-108">`typeName`może być (i często jest) i jest poprzedzony dla XAML przestrzeni nazw, która zawiera XAML definicje typów.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-108">`typeName` may be (and often is) prefixed for a XAML namespace that contains the XAML type definitions.</span></span>|  
|`arrayContents`|<span data-ttu-id="6f1a6-109">Zawartość elementów przypisanego do wewnętrznej `ArrayExtension.Items` właściwości.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-109">The items content that is assigned to the intrinsic `ArrayExtension.Items` property.</span></span> <span data-ttu-id="6f1a6-110">Zazwyczaj te elementy są określone jako co najmniej jeden obiekt zawartym w elemencie `x:Array` otwierające i zamykające znaczniki.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-110">Typically, these items are specified as one or more object elements contained within the `x:Array` opening and closing tags.</span></span> <span data-ttu-id="6f1a6-111">Obiekty określone w tym miejscu powinny być można przypisać do typu XAML, określonego w `typeName`.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-111">Objects specified here are expected to be assignable to the XAML type specified in `typeName`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f1a6-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6f1a6-112">Remarks</span></span>  
 <span data-ttu-id="6f1a6-113">`Type`jest wymagany atrybut dla wszystkich `x:Array` obiekt elementów.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-113">`Type` is a required attribute for all `x:Array` object elements.</span></span> <span data-ttu-id="6f1a6-114">A `Type` wartość parametru nie trzeba używać `x:Type` — rozszerzenie znaczników; krótkim Nazwa typu jest typu XAML, który może być określony jako ciąg.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-114">A `Type` parameter value does not need to use an `x:Type` markup extension; the short name of the type is   a XAML type, which can be specified as a string.</span></span>  
  
 <span data-ttu-id="6f1a6-115">W implementacji usług .NET Framework XAML, relacja między XAML typ danych wejściowych i wyjściowych CLR <xref:System.Type> utworzony tablicy ma wpływ kontekst usługi rozszerzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-115">In the .NET Framework XAML Services implementation, the relationship between the input XAML type and the output CLR <xref:System.Type> of the created array is influenced by service context for markup extensions.</span></span> <span data-ttu-id="6f1a6-116">Dane wyjściowe <xref:System.Type> jest <xref:System.Xaml.XamlType.UnderlyingType%2A> wejściowego typu XAML po wyszukiwania niezbędnych <xref:System.Xaml.XamlType> oparte na kontekst schematu XAML i <xref:System.Windows.Markup.IXamlTypeResolver> usługi udostępnia kontekst.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-116">The output <xref:System.Type> is the <xref:System.Xaml.XamlType.UnderlyingType%2A> of the input XAML type, after looking up the necessary <xref:System.Xaml.XamlType> based on XAML schema context and the <xref:System.Windows.Markup.IXamlTypeResolver> service the context provides.</span></span>  
  
 <span data-ttu-id="6f1a6-117">Podczas przetwarzania zawartości tablicy są przypisane do `ArrayExtension.Items` wewnętrzną właściwość.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-117">When processed, the array contents are assigned to the `ArrayExtension.Items` intrinsic property.</span></span> <span data-ttu-id="6f1a6-118">W <xref:System.Windows.Markup.ArrayExtension> implementacji jest reprezentowane przez <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-118">In the <xref:System.Windows.Markup.ArrayExtension> implementation, this is represented by <xref:System.Windows.Markup.ArrayExtension.Items%2A?displayProperty=nameWithType>.</span></span>  
  
 <span data-ttu-id="6f1a6-119">W implementacji usług .NET Framework XAML obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.Markup.ArrayExtension> klasy.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-119">In the .NET Framework XAML Services implementation, the handling for this markup extension is defined by the <xref:System.Windows.Markup.ArrayExtension> class.</span></span> <span data-ttu-id="6f1a6-120"><xref:System.Windows.Markup.ArrayExtension>nie jest zapieczętowany i może służyć jako podstawa implementacji rozszerzenie znaczników typu tablicy niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-120"><xref:System.Windows.Markup.ArrayExtension> is not sealed, and could be used as the basis for a markup extension implementation for a custom array type.</span></span>  
  
 <span data-ttu-id="6f1a6-121">`x:Array`jest kilka przeznaczonych do ogólne rozszerzalności języka w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-121">`x:Array` is more intended for general language extensibility in XAML.</span></span> <span data-ttu-id="6f1a6-122">Ale `x:Array` może także służyć do określania wartości XAML niektórych właściwości, które przyjmować obsługiwane XAML kolekcji jako ich zawartość właściwości strukturalne.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-122">But `x:Array` can also be useful for specifying XAML values of certain properties that take XAML-supported collections as their structured property content.</span></span> <span data-ttu-id="6f1a6-123">Na przykład można określić zawartości <xref:System.Collections.IEnumerable> właściwości o `x:Array` użycia.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-123">For example, you could specify the contents of an <xref:System.Collections.IEnumerable> property with an `x:Array` usage.</span></span>  
  
 <span data-ttu-id="6f1a6-124">`x:Array`to rozszerzenie znacznika.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-124">`x:Array` is a markup extension.</span></span> <span data-ttu-id="6f1a6-125">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-125">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="6f1a6-126">`x:Array`jest częściowo wyjątek od tej reguły, ponieważ zamiast zapewnienie obsługi wartość atrybutu alternatywnego `x:Array` zapewnia alternatywny Obsługa zawartość tekst wewnętrzny.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-126">`x:Array` is partially an exception to that rule because instead of providing alternative attribute value handling, `x:Array` provides alternative handling of its inner text content.</span></span> <span data-ttu-id="6f1a6-127">To zachowanie umożliwia typy, które nie mogą być obsługiwane przez istniejącego modelu zawartości można grupować w tablicy i odwołuje się w dalszej części kodu powiązanego podczas uzyskiwania dostępu do tablicy o nazwie; Możesz wywołać <xref:System.Array> metod do pobrania tablicy poszczególne elementy.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-127">This behavior enables types that might not be supported by an existing content model to be grouped into an array and referenced later in code-behind by accessing the named array; you can call <xref:System.Array> methods to get individual array items.</span></span>  
  
 <span data-ttu-id="6f1a6-128">Wszystkie rozszerzenia znaczników w XAML przy użyciu nawiasy klamrowe ({,}`)` w ich Składnia atrybutu, który jest Konwencji, za pomocą którego procesora XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć wartości atrybutu.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-128">All markup extensions in XAML use the braces ({,}`)` in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute value.</span></span> <span data-ttu-id="6f1a6-129">Aby uzyskać więcej informacji na temat rozszerzeń znaczników w ogólności, zobacz [typy konwerterów i rozszerzenia znaczników dla XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="6f1a6-129">For more information about markup extensions in general, see [Type Converters and Markup Extensions for XAML](../../../docs/framework/xaml-services/type-converters-and-markup-extensions-for-xaml.md).</span></span>  
  
 <span data-ttu-id="6f1a6-130">W języku XAML 2009 `x:Array` jest zdefiniowany jako język pierwotnych zamiast rozszerzenia znaczników.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-130">In XAML 2009, `x:Array` is defined as a language primitive instead of a markup extension.</span></span> <span data-ttu-id="6f1a6-131">Aby uzyskać więcej informacji, zobacz [typy wbudowane dla wspólnych elementów podstawowych języka XAML](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).</span><span class="sxs-lookup"><span data-stu-id="6f1a6-131">For more information, see [Built-in Types for Common XAML Language Primitives](../../../docs/framework/xaml-services/built-in-types-for-common-xaml-language-primitives.md).</span></span>  
  
## <a name="wpf-usage-notes"></a><span data-ttu-id="6f1a6-132">Uwagi dotyczące użycia WPF</span><span class="sxs-lookup"><span data-stu-id="6f1a6-132">WPF Usage Notes</span></span>  
 <span data-ttu-id="6f1a6-133">Zazwyczaj elementy obiektu wypełnić `x:Array` nie są elementami, które istnieją w [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] nazw XAML i muszą być mapowane prefiks przestrzeni nazw XAML innych niż domyślne.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-133">Typically, the object elements that populate an `x:Array` are not elements that exist in the [!INCLUDE[TLA2#tla_winclient](../../../includes/tla2sharptla-winclient-md.md)] XAML namespace, and require a prefix mapping to a non-default XAML namespace.</span></span>  
  
 <span data-ttu-id="6f1a6-134">Na przykład poniżej przedstawiono prosty tablicę dwa ciągi z `sys` prefiksu (a także `x`) zdefiniowane na poziomie tablicy.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-134">For example, the following is a simple array of two strings, with the `sys` prefix (and also `x`) defined at the level of the array.</span></span>  
  
 <span data-ttu-id="6f1a6-135">[xaml]</span><span class="sxs-lookup"><span data-stu-id="6f1a6-135">[xaml]</span></span>  
  
 `<x:Array Type="sys:String" xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"`  
  
 `xmlns:sys="clr-namespace:System;assembly=mscorlib">`  
  
 `<sys:String>Hello</sys:String>`  
  
 `<sys:String>World</sys:String>`  
  
 `</x:Array>`  
  
 <span data-ttu-id="6f1a6-136">Dla niestandardowych typów, które są używane jako elementy tablicy klasa muszą również obsługiwać wymagania dotyczące uruchamianiu jako elementy obiektu w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="6f1a6-136">For custom types that are used as array elements, the class must also support the requirements for being instantiated in XAML as object elements.</span></span> <span data-ttu-id="6f1a6-137">Aby uzyskać więcej informacji, zobacz [XAML oraz klas niestandardowych dla WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="6f1a6-137">For more information, see [XAML and Custom Classes for WPF](../../../docs/framework/wpf/advanced/xaml-and-custom-classes-for-wpf.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f1a6-138">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6f1a6-138">See Also</span></span>  
 [<span data-ttu-id="6f1a6-139">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="6f1a6-139">Markup Extensions and WPF XAML</span></span>](../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="6f1a6-140">Typy migrowane z WPF do System.Xaml</span><span class="sxs-lookup"><span data-stu-id="6f1a6-140">Types Migrated from WPF to System.Xaml</span></span>](../../../docs/framework/xaml-services/types-migrated-from-wpf-to-system-xaml.md)