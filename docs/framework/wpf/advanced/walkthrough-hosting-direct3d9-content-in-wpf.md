---
title: "Wskazówki: hosing zawartości Direct3D9 w WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Direct3D9 [WPF interoperability], hosting Direct3D9 content
- WPF [WPF], hosting Direct3D9 content
ms.assetid: 60983736-0ab5-42cc-8b16-e9fbde261a43
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ec80eed37777fc7b17b435e1bef63ecbb94bdf46
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-hosting-direct3d9-content-in-wpf"></a><span data-ttu-id="91071-102">Wskazówki: hosing zawartości Direct3D9 w WPF</span><span class="sxs-lookup"><span data-stu-id="91071-102">Walkthrough: Hosting Direct3D9 Content in WPF</span></span>
<span data-ttu-id="91071-103">W tym przewodniku pokazano, jak udostępnić zawartość Direct3D9 w aplikacji Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="91071-103">This walkthrough shows how to host Direct3D9 content in a Windows Presentation Foundation (WPF) application.</span></span>  
  
 <span data-ttu-id="91071-104">W tym przewodniku należy wykonać następujące zadania:</span><span class="sxs-lookup"><span data-stu-id="91071-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="91071-105">Utwórz projekt WPF do hostowania zawartości Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="91071-105">Create a WPF project to host the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="91071-106">Importuj zawartość Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="91071-106">Import the Direct3D9 content.</span></span>  
  
-   <span data-ttu-id="91071-107">Wyświetl zawartość Direct3D9 przy użyciu <xref:System.Windows.Interop.D3DImage> klasy.</span><span class="sxs-lookup"><span data-stu-id="91071-107">Display the Direct3D9 content by using the <xref:System.Windows.Interop.D3DImage> class.</span></span>  
  
 <span data-ttu-id="91071-108">Po ukończeniu będzie wiadomo, jak udostępniać zawartość Direct3D9 w aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="91071-108">When you are finished, you will know how to host Direct3D9 content in a WPF application.</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="91071-109">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="91071-109">Prerequisites</span></span>  
 <span data-ttu-id="91071-110">Następujące składniki są wymagane do przeprowadzenia tego instruktażu:</span><span class="sxs-lookup"><span data-stu-id="91071-110">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev10_long](../../../../includes/vs-dev10-long-md.md)]<span data-ttu-id="91071-111">.</span><span class="sxs-lookup"><span data-stu-id="91071-111">.</span></span>  
  
-   <span data-ttu-id="91071-112">Program DirectX SDK 9 lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="91071-112">DirectX SDK 9 or later.</span></span>  
  
-   <span data-ttu-id="91071-113">Biblioteki DLL zawierającej Direct3D9 zawartość w formacie zgodnym z WPF.</span><span class="sxs-lookup"><span data-stu-id="91071-113">A DLL that contains Direct3D9 content in a WPF-compatible format.</span></span> <span data-ttu-id="91071-114">Aby uzyskać więcej informacji, zobacz [WPF i współdziałanie Direct3D9](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) i [wskazówki: tworzenie zawartości Direct3D9 dla hostingu na platformie WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="91071-114">For more information, see [WPF and Direct3D9 Interoperation](../../../../docs/framework/wpf/advanced/wpf-and-direct3d9-interoperation.md) and [Walkthrough: Creating Direct3D9 Content for Hosting in WPF](../../../../docs/framework/wpf/advanced/walkthrough-creating-direct3d9-content-for-hosting-in-wpf.md).</span></span>  
  
## <a name="creating-the-wpf-project"></a><span data-ttu-id="91071-115">Tworzenie projektu WPF</span><span class="sxs-lookup"><span data-stu-id="91071-115">Creating the WPF Project</span></span>  
 <span data-ttu-id="91071-116">Pierwszym krokiem jest utworzenie projektu aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="91071-116">The first step is to create the project for the WPF application.</span></span>  
  
#### <a name="to-create-the-wpf-project"></a><span data-ttu-id="91071-117">Aby utworzyć projekt WPF</span><span class="sxs-lookup"><span data-stu-id="91071-117">To create the WPF project</span></span>  
  
-   <span data-ttu-id="91071-118">Utwórz nowy projekt aplikacji WPF języka Visual C# o nazwie `D3DHost`.</span><span class="sxs-lookup"><span data-stu-id="91071-118">Create a new WPF Application project in Visual C# named `D3DHost`.</span></span> <span data-ttu-id="91071-119">Aby uzyskać więcej informacji, zobacz [porady: Tworzenie nowego projektu aplikacji WPF](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span><span class="sxs-lookup"><span data-stu-id="91071-119">For more information, see [How to: Create a New WPF Application Project](http://msdn.microsoft.com/en-us/1f6aea7a-33e1-4d3f-8555-1daa42e95d82).</span></span>  
  
     <span data-ttu-id="91071-120">Otwiera MainWindow.xaml w [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span><span class="sxs-lookup"><span data-stu-id="91071-120">MainWindow.xaml opens in the [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)].</span></span>  
  
## <a name="importing-the-direct3d9-content"></a><span data-ttu-id="91071-121">Importowanie zawartości Direct3D9</span><span class="sxs-lookup"><span data-stu-id="91071-121">Importing the Direct3D9 Content</span></span>  
 <span data-ttu-id="91071-122">Możesz zaimportować zawartość Direct3D9 niezarządzanej dll przy użyciu `DllImport` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="91071-122">You import the Direct3D9 content from an unmanaged DLL by using the `DllImport` attribute.</span></span>  
  
#### <a name="to-import-direct3d9-content"></a><span data-ttu-id="91071-123">Aby zaimportować zawartość Direct3D9</span><span class="sxs-lookup"><span data-stu-id="91071-123">To import Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="91071-124">Otwórz MainWindow.xaml.cs w edytorze kodu.</span><span class="sxs-lookup"><span data-stu-id="91071-124">Open MainWindow.xaml.cs in the Code Editor.</span></span>  
  
2.  <span data-ttu-id="91071-125">Zastąp następujący kod automatycznie wygenerowanego kodu.</span><span class="sxs-lookup"><span data-stu-id="91071-125">Replace the automatically generated code with the following code.</span></span>  
  
     [!code-csharp[System.Windows.Interop.D3DImage#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml.cs#1)]  
  
## <a name="hosting-the-direct3d9-content"></a><span data-ttu-id="91071-126">Hostowanie zawartości Direct3D9</span><span class="sxs-lookup"><span data-stu-id="91071-126">Hosting the Direct3D9 Content</span></span>  
 <span data-ttu-id="91071-127">Na koniec użyj <xref:System.Windows.Interop.D3DImage> klasy obsługujące zawartość Direct3D9.</span><span class="sxs-lookup"><span data-stu-id="91071-127">Finally, use the <xref:System.Windows.Interop.D3DImage> class to host the Direct3D9 content.</span></span>  
  
#### <a name="to-host-the-direct3d9-content"></a><span data-ttu-id="91071-128">Aby udostępnić zawartość Direct3D9</span><span class="sxs-lookup"><span data-stu-id="91071-128">To host the Direct3D9 content</span></span>  
  
1.  <span data-ttu-id="91071-129">W MainWindow.xaml Zamień następujące XAML XAML wygenerowanej automatycznie.</span><span class="sxs-lookup"><span data-stu-id="91071-129">In MainWindow.xaml, replace the automatically generated XAML with the following XAML.</span></span>  
  
     [!code-xaml[System.Windows.Interop.D3DImage#10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/System.Windows.Interop.D3DImage/CS/window1.xaml#10)]  
  
2.  <span data-ttu-id="91071-130">Skompiluj projekt.</span><span class="sxs-lookup"><span data-stu-id="91071-130">Build the project.</span></span>  
  
3.  <span data-ttu-id="91071-131">Skopiuj biblioteki DLL zawierającej Direct3D9 zawartość do folderu bin/Debug.</span><span class="sxs-lookup"><span data-stu-id="91071-131">Copy the DLL that contains the Direct3D9 content to the bin/Debug folder.</span></span>  
  
4.  <span data-ttu-id="91071-132">Naciśnij klawisz F5, aby uruchomić projekt.</span><span class="sxs-lookup"><span data-stu-id="91071-132">Press F5 to run the project.</span></span>  
  
     <span data-ttu-id="91071-133">Zawartość Direct3D9 jest wyświetlana w aplikacji WPF.</span><span class="sxs-lookup"><span data-stu-id="91071-133">The Direct3D9 content appears within the WPF application.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91071-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91071-134">See Also</span></span>  
 <xref:System.Windows.Interop.D3DImage>  
 [<span data-ttu-id="91071-135">Zagadnienia dotyczące wydajności Direct3D9 i współdziałanie z WPF</span><span class="sxs-lookup"><span data-stu-id="91071-135">Performance Considerations for Direct3D9 and WPF Interoperability</span></span>](../../../../docs/framework/wpf/advanced/performance-considerations-for-direct3d9-and-wpf-interoperability.md)