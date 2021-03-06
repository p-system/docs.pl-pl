---
title: Jak animować punkt z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- key frames [WPF], animating Points with
- Points [WPF], animating with key frames
- animation [WPF], Points with key frames
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
ms.openlocfilehash: a59ceb62d7feb33d2cc8a747a7bfb85e551d785c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557358"
---
# <a name="how-to-animate-a-point-by-using-key-frames"></a>Jak animować punkt z wykorzystaniem klatek kluczowych
Ten przykład przedstawia sposób użycia <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> klasy do animowania <xref:System.Windows.Point>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przenosi elipsy trójkątny ścieżce. W przykładzie użyto <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> klasy do animowania <xref:System.Windows.Media.EllipseGeometry.Center%2A> właściwość <xref:System.Windows.Media.EllipseGeometry>. Ta animacja używa trzech klatek kluczowych w następujący sposób:  
  
1.  Podczas pierwszego pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.LinearPointKeyFrame> klasę, aby przenieść elipsy wzdłuż ścieżki stałą szybkością z punktu początkowego. Liniowy klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.LinearPointKeyFrame> utworzyć smooth interpolacji liniowej między wartościami.  
  
2.  W końcu następnej pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> klasy nagle przejście elipsy wzdłuż ścieżki do pozycji dalej. Odrębny klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> tworzenie nagłym przeskoków między wartościami.  
  
3.  Podczas końcowego dwusekundowe używa wystąpienia <xref:System.Windows.Media.Animation.SplinePointKeyFrame> klasę, aby przenieść elipsy z powrotem do punktu początkowego. Ramek kluczowych krzywej składanej, takich jak <xref:System.Windows.Media.Animation.SplinePointKeyFrame> utworzyć zmiennej przejścia między wartościami zgodnie z wartościami <xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> właściwości. W tym przykładzie animacji rozpoczyna się powoli i przyspiesza wykładniczo do końca segmentu czasu.  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 Pełny przykład, zobacz [klatek kluczowych animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
 Spójności z innymi przykładami animacji, użyj wersji kodu w tym przykładzie <xref:System.Windows.Media.Animation.Storyboard> obiekt do zastosowania <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>. Jednak podczas stosowania pojedynczego animacji w kodzie, łatwiej jest użyć <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> metody zamiast <xref:System.Windows.Media.Animation.Storyboard>. Na przykład zobacz [animowania właściwości bez Using scenorysu](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>  
 <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Media.EllipseGeometry>  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Klatki kluczowe — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
