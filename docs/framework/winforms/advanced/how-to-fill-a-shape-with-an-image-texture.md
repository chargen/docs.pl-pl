---
title: 'Porady: wypełnianie kształtów teksturą obrazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], using with brushes
- bitmaps [Windows Forms], using texture
- shapes [Windows Forms], filling with images
ms.assetid: 508da5a6-2433-4d2b-9680-eaeae4e96e3b
ms.openlocfilehash: c1eb090bebcced125193c1db16087b6165d27ff3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-fill-a-shape-with-an-image-texture"></a>Porady: wypełnianie kształtów teksturą obrazu
Możesz wpisać kształtu zamkniętego teksturą przy użyciu <xref:System.Drawing.Image> klasy i <xref:System.Drawing.TextureBrush> klasy.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład wypełnia elipsę z obrazem. Tworzy kod <xref:System.Drawing.Image> obiekt, a następnie przekazuje adres, który <xref:System.Drawing.Image> obiektu jako argument <xref:System.Drawing.TextureBrush.%23ctor%2A> konstruktora. Trzeci instrukcji skaluje obraz i czwarty instrukcji wypełnia elipsy powtarzane kopie skalowanie obrazu.  
  
 W poniższym kodzie <xref:System.Drawing.TextureBrush.Transform%2A> właściwość zawiera transformacji zastosowanych do obrazu przed narysowaniem go. Załóżmy, że oryginalny obraz ma 640 pikseli szerokości i wysokości 480 pikseli. Transformacja zmniejsza obraz do 75 × 75 przez ustawienie wartości skalowania poziomie i w pionie.  
  
> [!NOTE]
>  W poniższym przykładzie rozmiar obrazu jest 75 × 75 i rozmiaru elipsy wynosi 150 x 250. Ponieważ obrazu jest mniejszy niż elipsy, który jest jego wypełniania, elipsy jest rozmieszczany przy użyciu obrazu. Ustawianie widoku kafelków oznacza, że obraz jest powtarzany w poziomie i w pionie do granicy kształt zostanie osiągnięty. Aby uzyskać więcej informacji na temat fragmentu, zobacz [porady: kafelka kształtu obrazem](../../../../docs/framework/winforms/advanced/how-to-tile-a-shape-with-an-image.md).  
  
 [!code-csharp[System.Drawing.UsingABrush#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingABrush/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.UsingABrush#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingABrush/VB/Class1.vb#21)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Poprzedni przykład jest przeznaczony do użytku z formularzy systemu Windows i wymaga <xref:System.Windows.Forms.PaintEventArgs> `e`, który jest parametrem <xref:System.Windows.Forms.Control.Paint> obsługi zdarzeń.  
  
## <a name="see-also"></a>Zobacz też  
 [Używanie pędzla do wypełniania kształtów](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)
