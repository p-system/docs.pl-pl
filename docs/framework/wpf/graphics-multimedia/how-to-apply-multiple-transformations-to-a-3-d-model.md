---
title: "Jak zastosować wiele przekształceń do modelu 3-D"
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
helpviewer_keywords: 3-D models [WPF], applying multiple transformations to
ms.assetid: cb72245a-5560-4c96-9f58-593c66296992
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 77e9f664ababa32cf0629f513f81b1e24030eac1
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-apply-multiple-transformations-to-a-3-d-model"></a><span data-ttu-id="23d2c-102">Jak zastosować wiele przekształceń do modelu 3-D</span><span class="sxs-lookup"><span data-stu-id="23d2c-102">How to: Apply Multiple Transformations to a 3-D Model</span></span>
<span data-ttu-id="23d2c-103">Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Media3D.RotateTransform3D> i <xref:System.Windows.Media.Media3D.ScaleTransform3D> do obracania i zmieniania skali 3-w modelu.</span><span class="sxs-lookup"><span data-stu-id="23d2c-103">This sample shows how to use a <xref:System.Windows.Media.Media3D.RotateTransform3D> and a <xref:System.Windows.Media.Media3D.ScaleTransform3D> to rotate and change the scale of a 3-D model.</span></span> <span data-ttu-id="23d2c-104">Poniższy kod przedstawia sposób stosowania tych transformacji do <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> właściwość <xref:System.Windows.Media.Media3D.GeometryModel3D> w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="23d2c-104">The code below shows how to apply these transforms to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexampleinline1)]  
  
 <span data-ttu-id="23d2c-105">W kodzie:</span><span class="sxs-lookup"><span data-stu-id="23d2c-105">In code:</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexampleinline1)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="23d2c-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="23d2c-106">Example</span></span>  
 <span data-ttu-id="23d2c-107">Poniższy kod przedstawia cały przykładowy w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="23d2c-107">The following code shows the entire sample in XAML.</span></span>  
  
 [!code-xaml[3DGallery_snip#Multiple3DTransformationsExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/MultipleTransformationsExample.xaml#multiple3dtransformationsexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="23d2c-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="23d2c-108">Example</span></span>  
 <span data-ttu-id="23d2c-109">Poniżej znajduje się cała próbka w kodzie.</span><span class="sxs-lookup"><span data-stu-id="23d2c-109">Below is the entire sample in code.</span></span>  
  
 [!code-csharp[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/MultipleTransformationsExample.cs#multiple3dtransformationscodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Multiple3DTransformationsCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/multipletransformationsexample.vb#multiple3dtransformationscodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="23d2c-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23d2c-110">See Also</span></span>  
 [<span data-ttu-id="23d2c-111">Przekształć skali 3-modelu</span><span class="sxs-lookup"><span data-stu-id="23d2c-111">Transform the Scale of a 3-D Model</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-transform-the-scale-of-a-3-d-model.md)