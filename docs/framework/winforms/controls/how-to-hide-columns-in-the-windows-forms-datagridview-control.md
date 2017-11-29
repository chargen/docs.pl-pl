---
title: 'Porady: ukrywanie kolumn w formancie DataGridView formularzy systemu Windows'
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
- DataGridView control [Windows Forms], hiding columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
ms.assetid: 3f94143a-2ef0-49a5-a22a-b2e6f9289642
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d4c0dd32e6d0633a18d18905992d5defbe838923
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e1ce1-102">Porady: ukrywanie kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e1ce1-102">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e1ce1-103">Czasami można wyświetlić tylko niektóre kolumny, które są dostępne w formularzach systemu Windows <xref:System.Windows.Forms.DataGridView> formantu.</span><span class="sxs-lookup"><span data-stu-id="e1ce1-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="e1ce1-104">Na przykład możesz chcieć Pokaż pracownika wynagrodzenie kolumny do użytkowników przy użyciu poświadczeń zarządzania są ukryte go od innych użytkowników.</span><span class="sxs-lookup"><span data-stu-id="e1ce1-104">For example, you might want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="e1ce1-105">Alternatywnie można powiązać ze źródłem danych, który zawiera wiele kolumn, tylko niektóre z nich ma być wyświetlany formant.</span><span class="sxs-lookup"><span data-stu-id="e1ce1-105">Alternately, you might want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="e1ce1-106">W takim przypadku zwykle spowoduje usunięcie kolumn nie są zainteresowane wyświetlanie zamiast możesz je ukryć.</span><span class="sxs-lookup"><span data-stu-id="e1ce1-106">In this case, you will typically remove the columns you are not interested in displaying rather than hide them.</span></span>  
  
 <span data-ttu-id="e1ce1-107">W <xref:System.Windows.Forms.DataGridView> kontroli, <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> wartość właściwości kolumny określa, czy jest wyświetlany tej kolumny.</span><span class="sxs-lookup"><span data-stu-id="e1ce1-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property value of a column determines whether that column is displayed.</span></span>  
  
 <span data-ttu-id="e1ce1-108">Brak obsługi dla tego zadania w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e1ce1-108">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="e1ce1-109">Zobacz też [porady: ukrywanie kolumn w Windows Forms DataGridView formantu przy użyciu narzędzia Projektant](http://msdn.microsoft.com/library/kaswfbes\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="e1ce1-109">Also see [How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/kaswfbes\(v=vs.110\)).</span></span>  
  
### <a name="to-hide-a-column-programmatically"></a><span data-ttu-id="e1ce1-110">Aby programowo Ukryj kolumnę</span><span class="sxs-lookup"><span data-stu-id="e1ce1-110">To hide a column programmatically</span></span>  
  
-   <span data-ttu-id="e1ce1-111">Ustaw <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> właściwości `false`.</span><span class="sxs-lookup"><span data-stu-id="e1ce1-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> property to `false`.</span></span> <span data-ttu-id="e1ce1-112">Aby ukryć `CustomerID` kolumny, która jest generowana automatycznie podczas wiązania z danymi, umieść poniższy przykładowy kod w <xref:System.Windows.Forms.DataGridView.DataBindingComplete> obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="e1ce1-112">To hide a `CustomerID` column that is automatically generated during data binding, place the following code example in a <xref:System.Windows.Forms.DataGridView.DataBindingComplete> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#063](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#063)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#063](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#063)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e1ce1-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e1ce1-113">Compiling the Code</span></span>  
 <span data-ttu-id="e1ce1-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e1ce1-114">This example requires:</span></span>  
  
-   <span data-ttu-id="e1ce1-115">A <xref:System.Windows.Forms.DataGridView> formantu o nazwie `dataGridView1` zawiera kolumny o nazwie `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="e1ce1-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `CustomerID`.</span></span>  
  
-   <span data-ttu-id="e1ce1-116">Odwołuje się do <xref:System?displayProperty=nameWithType> i <xref:System.Windows.Forms?displayProperty=nameWithType> zestawów.</span><span class="sxs-lookup"><span data-stu-id="e1ce1-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1ce1-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1ce1-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="e1ce1-118">Wierszy i kolumn podstawowe funkcje komórek w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e1ce1-118">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="e1ce1-119">Porady: usuwanie utworzonych automatycznie kolumn z systemu Windows do formantu DataGridView formularzy</span><span class="sxs-lookup"><span data-stu-id="e1ce1-119">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 [<span data-ttu-id="e1ce1-120">Porady: Zmienianie kolejności kolumn w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e1ce1-120">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)