---
title: "Porady: wyświetlanie obrazów w komórkach formantu DataGridView formularzy systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], displaying images
- data grids [Windows Forms], displaying in grids
- DataGridView control [Windows Forms], displaying images
- data grids [Windows Forms], displaying images in cells
ms.assetid: 53b13d31-1b56-476d-9ab4-18bfac138a22
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0b2e06298d0ead9a2dd9fa554af0c42df5d61d56
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-images-in-cells-of-the-windows-forms-datagridview-control"></a><span data-ttu-id="80c17-102">Porady: wyświetlanie obrazów w komórkach formantu DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="80c17-102">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="80c17-103">Obraz lub grafikę to jedna z wartości, które można wyświetlić w wierszu danych.</span><span class="sxs-lookup"><span data-stu-id="80c17-103">A picture or graphic is one of the values that you can display in a row of data.</span></span> <span data-ttu-id="80c17-104">Często te grafiki formę pracownika zdjęcie lub logo firmy.</span><span class="sxs-lookup"><span data-stu-id="80c17-104">Frequently, these graphics take the form of an employee's photograph or a company logo.</span></span>  
  
 <span data-ttu-id="80c17-105">Dołączanie obrazów jest proste, podczas wyświetlania danych w ramach <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="80c17-105">Incorporating pictures is simple when you display data within the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="80c17-106"><xref:System.Windows.Forms.DataGridView> Kontroli natywnie obsługuje dowolny format obrazu obsługiwany przez <xref:System.Drawing.Image> klasy, a także OLE obraz format używany przez niektóre bazy danych.</span><span class="sxs-lookup"><span data-stu-id="80c17-106">The <xref:System.Windows.Forms.DataGridView> control natively handles any image format supported by the <xref:System.Drawing.Image> class, as well as the OLE picture format used by some databases.</span></span>  
  
 <span data-ttu-id="80c17-107">Jeśli <xref:System.Windows.Forms.DataGridView> formantu źródła danych zawiera kolumnę obrazów, będą one wyświetlane automatycznie przez <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="80c17-107">If the <xref:System.Windows.Forms.DataGridView> control's data source has a column of images, they will be displayed automatically by the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <span data-ttu-id="80c17-108">Poniższy przykład kodu pokazuje, jak wyodrębnić ikony z zasobu osadzonego i przekształcić ją w mapy bitowej do wyświetlenia w każdej komórce kolumny obrazu.</span><span class="sxs-lookup"><span data-stu-id="80c17-108">The following code example demonstrates how to extract an icon from an embedded resource and convert it to a bitmap for display in every cell of an image column.</span></span> <span data-ttu-id="80c17-109">Na przykład innego zamienia wartości tekstowej komórek odpowiednich obrazów, zobacz [porady: dostosowywanie formatowania danych w formancie DataGridView formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="80c17-109">For another example that replaces textual cell values with corresponding images, see [How to: Customize Data Formatting in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80c17-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="80c17-110">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#050)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#050](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#050)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="80c17-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="80c17-111">Compiling the Code</span></span>  
 <span data-ttu-id="80c17-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="80c17-112">This example requires:</span></span>  
  
-   <span data-ttu-id="80c17-113">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="80c17-113">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="80c17-114">Zasobów osadzonych ikona o nazwie `tree.ico`.</span><span class="sxs-lookup"><span data-stu-id="80c17-114">An embedded icon resource named `tree.ico`.</span></span>  
  
-   <span data-ttu-id="80c17-115">Odwołuje się do <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, i <xref:System.Drawing?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="80c17-115">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Drawing?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="80c17-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="80c17-116">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="80c17-117">Wierszy i kolumn podstawowe funkcje komórek w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="80c17-117">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="80c17-118">Porady: dostosowywanie formatowania danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="80c17-118">How to: Customize Data Formatting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md)