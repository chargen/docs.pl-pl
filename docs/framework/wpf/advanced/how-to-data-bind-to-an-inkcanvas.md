---
title: Jak powiązać dane z InkCanvas
ms.date: 03/30/2017
helpviewer_keywords:
- InkCanvas [WPF], binding data to
- binding data [WPF], to InkCanvas
ms.assetid: 8d6b4d9e-ea7f-4412-ba83-3feccec5a515
ms.openlocfilehash: 4081ae7dd6854934804062cfce60d10106c1e1d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-data-bind-to-an-inkcanvas"></a>Jak powiązać dane z InkCanvas
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano, jak można powiązać <xref:System.Windows.Controls.InkCanvas.Strokes%2A> właściwość <xref:System.Windows.Controls.InkCanvas> do innego <xref:System.Windows.Controls.InkCanvas>.  
  
 [!code-xaml[InkCanvasBindingSnippet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#2)]  
  
 W poniższym przykładzie pokazano, jak można powiązać <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> właściwości ze źródłem danych.  
  
 [!code-xaml[InkCanvasBindingSnippet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#3)]  
[!code-xaml[InkCanvasBindingSnippet#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window2.xaml#4)]  
  
 Poniższy przykład deklaruje dwa <xref:System.Windows.Controls.InkCanvas> obiektów w kodzie XAML i ustanawia powiązania danych między nimi i innych źródeł danych.  Pierwszy <xref:System.Windows.Controls.InkCanvas>o nazwie `ic`, jest powiązany z dwóch źródeł danych.  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A> i <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A> właściwości `ic` są powiązane z <xref:System.Windows.Controls.ListBox> obiektów, które z kolei są powiązane z tablicami zdefiniowane w pliku XAML.  <xref:System.Windows.Controls.InkCanvas.EditingMode%2A>, <xref:System.Windows.Controls.InkCanvas.DefaultDrawingAttributes%2A>, I <xref:System.Windows.Controls.InkCanvas.Strokes%2A> właściwości drugiego <xref:System.Windows.Controls.InkCanvas> powiązanych do pierwszej <xref:System.Windows.Controls.InkCanvas>, `ic`.  
  
 [!code-xaml[InkCanvasBindingSnippet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkCanvasBindingSnippet/CS/Window1.xaml#1)]
