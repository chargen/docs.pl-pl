---
title: Jak animować kolor z wykorzystaniem klatek kluczowych
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- colors [WPF], animating with key frames
- animation [WPF], colors with key frames
- key frames [WPF], animating colors with
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
ms.openlocfilehash: 7d89a1f9c24c93bd6b05265092bde09e8cf6eff5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-animate-color-by-using-key-frames"></a>Jak animować kolor z wykorzystaniem klatek kluczowych
W tym przykładzie pokazano, jak animować <xref:System.Windows.Media.SolidColorBrush.Color%2A> z <xref:System.Windows.Media.SolidColorBrush> przy użyciu klucza ramki.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> klasy do animowania <xref:System.Windows.Media.SolidColorBrush.Color%2A> właściwość <xref:System.Windows.Media.SolidColorBrush>. Ta animacja używa trzech klatek kluczowych w następujący sposób:  
  
1.  Podczas pierwszego dwusekundowe używa wystąpienia <xref:System.Windows.Media.Animation.LinearColorKeyFrame> klasy stopniowo zmiana koloru z zielonego na czerwony. Liniowy klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.LinearColorKeyFrame> utworzyć liniowej przejścia między wartościami.  
  
2.  W końcu następnej pół sekundy używa wystąpienia <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> klasę, aby szybko zmienić kolor czerwony żółty. Odrębny klatek kluczowych, takich jak <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> utworzyć nagłym zmiany między wartościami, oznacza to, zmiana koloru w tej części animacji występuje szybko i nie jest niewielkie.  
  
3.  Podczas końcowego dwusekundowe używa wystąpienia <xref:System.Windows.Media.Animation.SplineColorKeyFrame> klasy ponownie zmienić kolor — teraz z powrotem żółty zielony. Ramek kluczowych krzywej składanej, takich jak <xref:System.Windows.Media.Animation.SplineColorKeyFrame> utworzyć zmiennej przejścia między wartościami zgodnie z wartościami <xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> właściwości. W tym przykładzie zmianę koloru rozpoczyna się powoli i przyspiesza wykładniczo do końca segmentu czasu.  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xaml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 Pełny przykład, zobacz [klatek kluczowych animacji próbki](http://go.microsoft.com/fwlink/?LinkID=160012).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Media.SolidColorBrush.Color%2A>  
 <xref:System.Windows.Media.SolidColorBrush>  
 <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>  
 [Animacje kluczowych klatek — przegląd](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)  
 [Klatki kluczowe — tematy z instrukcjami](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)
