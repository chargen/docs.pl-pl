---
title: 'Porady: formanty pozycji na formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
f1_keywords:
- Location
- Location.Y
- Location.X
helpviewer_keywords:
- controls [Windows Forms]
- controls [Windows Forms], moving
- snaplines
- controls [Windows Forms], positioning
ms.assetid: 4693977e-34a4-4f19-8221-68c3120c2b2b
ms.openlocfilehash: 6db021f2b1a29c3ef52a182c45bbc7878feebb97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-position-controls-on-windows-forms"></a>Porady: formanty pozycji na formularzach systemu Windows
Formanty pozycji, za pomocą projektanta formularzy systemu Windows lub określ <xref:System.Windows.Forms.Control.Location%2A> właściwości.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-position-a-control-on-the-design-surface-of-the-windows-forms-designer"></a>Aby umieścić kontrolkę na powierzchnię projektanta formularzy systemu Windows  
  
-   Przeciągnij kontrolki w odpowiedniej lokalizacji przy użyciu myszy.  
  
    > [!NOTE]
    >  Wybierz kontrolkę i przenieść go z STRZAŁKĄ klucze do bardziej precyzyjne rozmieszczanie. Ponadto *linie przyciągania* ułatwiają rozmieszczenie formantów w formularzu. Aby uzyskać więcej informacji, zobacz [wskazówki: rozmieszczanie formantów na formularzach systemu Windows przy użyciu linie przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md).  
  
### <a name="to-position-a-control-using-the-properties-window"></a>Aby umieścić kontrolkę w oknie właściwości  
  
1.  Kliknij formant, który ma zostać ustawiony.  
  
2.  W **właściwości** okna, wartości typu <xref:System.Windows.Forms.Control.Location%2A> właściwości oddzielonych przecinkami, aby umieścić kontrolki wewnątrz jej kontenera.  
  
     Pierwsza liczba (X) jest odległość między lewą krawędzią kontenera; Druga liczba (Y) jest odległość od górnej granicy obszaru kontenera (w pikselach).  
  
    > [!NOTE]
    >  Można rozwinąć <xref:System.Windows.Forms.Control.Location%2A> właściwość do typu **X** i **Y** wartości pojedynczo.  
  
### <a name="to-position-a-control-programmatically"></a>Aby programowo położenie formantu  
  
1.  Ustaw <xref:System.Windows.Forms.Control.Location%2A> właściwości formantu <xref:System.Drawing.Point>.  
  
    ```vb  
    Button1.Location = New Point(100, 100)  
    ```  
  
    ```csharp  
    button1.Location = new Point(100, 100);  
    ```  
  
    ```cpp  
    button1->Location = Point(100, 100);  
    ```  
  
2.  Zmień współrzędną X lokalizacji kontrolki przy użyciu <xref:System.Windows.Forms.Control.Left%2A> podwłaściwości.  
  
    ```vb  
    Button1.Left = 300  
    ```  
  
    ```csharp  
    button1.Left = 300;  
    ```  
  
    ```cpp  
    button1->Left = 300;  
    ```  
  
### <a name="to-increment-a-controls-location-programmatically"></a>Aby zwiększyć programowo położenie formantu  
  
1.  Ustaw <xref:System.Windows.Forms.Control.Left%2A> podwłaściwości, aby zwiększyć współrzędną X formantu.  
  
    ```vb  
    Button1.Left += 200  
    ```  
  
    ```csharp  
    button1.Left += 200;  
    ```  
  
    ```cpp  
    button1->Left += 200;  
    ```  
  
    > [!NOTE]
    >  Użyj <xref:System.Windows.Forms.Control.Location%2A> właściwości można ustawić formantu X i Y pozycji jednocześnie. Aby ustawić pozycji pojedynczo, użyj formantu <xref:System.Windows.Forms.Control.Left%2A> (**X**) lub <xref:System.Windows.Forms.Control.Top%2A> (**Y**) podwłaściwości. Nie należy próbować ustawiane niejawnie współrzędne X i Y <xref:System.Drawing.Point> strukturę, która reprezentuje przycisk lokalizacji, ponieważ ta struktura zawiera kopię współrzędnych przycisku.  
  
## <a name="see-also"></a>Zobacz też  
 [Kontrolki formularzy Windows Forms](../../../../docs/framework/winforms/controls/index.md)  
 [Przewodnik: rozmieszczanie kontrolek na formularzach Windows Forms za pomocą linii przyciągania](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-snaplines.md)  
 [Przewodnik: rozmieszczanie kontrolek w aplikacji Windows Forms za pomocą kontrolki TableLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)  
 [Przewodnik: rozmieszczanie kontrolek w formularzach Windows Forms za pomocą kontrolki FlowLayoutPanel](../../../../docs/framework/winforms/controls/walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)  
 [Rozmieszczanie kontrolek na formularzach Windows Forms](../../../../docs/framework/winforms/controls/arranging-controls-on-windows-forms.md)  
 [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](../../../../docs/framework/winforms/controls/labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)  
 [Kontrolki do użycia w formularzach Windows Forms](../../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md)  
 [Kontrolki formularzy Windows Forms według funkcji](../../../../docs/framework/winforms/controls/windows-forms-controls-by-function.md)  
 [Porady: Ustawianie lokalizacji ekranu formularzy systemu Windows](http://msdn.microsoft.com/library/cb023ab7-dea7-4284-9aa6-8c03c59b60c6)
