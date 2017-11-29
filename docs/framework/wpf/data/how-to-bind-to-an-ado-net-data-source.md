---
title: "Jak powiązać ze źródłem danych ADO.NET"
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
helpviewer_keywords:
- data binding [WPF], binding to ADO.NET data sources
- ADO.NET data sources [WPF], binding to
- binding [WPF], to ADO.NET data sources
ms.assetid: a70c6d7b-7b38-4fdf-b655-4804db7c8315
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0eb555bb9f21385d2d0b66fe0dd39112c8350dec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-an-adonet-data-source"></a><span data-ttu-id="2dc82-102">Jak powiązać ze źródłem danych ADO.NET</span><span class="sxs-lookup"><span data-stu-id="2dc82-102">How to: Bind to an ADO.NET Data Source</span></span>
<span data-ttu-id="2dc82-103">W tym przykładzie pokazano, jak można powiązać [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> formant [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="2dc82-103">This example shows how to bind a [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] <xref:System.Windows.Controls.ListBox> control to an [!INCLUDE[TLA#tla_adonet](../../../../includes/tlasharptla-adonet-md.md)] `DataSet`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2dc82-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="2dc82-104">Example</span></span>  
 <span data-ttu-id="2dc82-105">W tym przykładzie `OleDbConnection` obiektu służy do łączenia się ze źródłem danych, która jest `Access MDB` pliku, który określono w parametrach połączenia.</span><span class="sxs-lookup"><span data-stu-id="2dc82-105">In this example, an `OleDbConnection` object is used to connect to the data source which is an `Access MDB` file that is specified in the connection string.</span></span> <span data-ttu-id="2dc82-106">Po nawiązaniu połączenia `OleDbDataAdpater` tworzony jest obiekt.</span><span class="sxs-lookup"><span data-stu-id="2dc82-106">After the connection is established, an `OleDbDataAdpater` object is created.</span></span> <span data-ttu-id="2dc82-107">`OleDbDataAdpater` Obiektu wykonuje select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] instrukcji, aby pobrać zestaw rekordów z bazy danych.</span><span class="sxs-lookup"><span data-stu-id="2dc82-107">The `OleDbDataAdpater` object executes a select [!INCLUDE[TLA#tla_sql](../../../../includes/tlasharptla-sql-md.md)] statement to retrieve the recordset from the database.</span></span> <span data-ttu-id="2dc82-108">Wyniki z [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] polecenia są przechowywane w `DataTable` z `DataSet` przez wywołanie metody `Fill` metody `OleDbDataAdapter`.</span><span class="sxs-lookup"><span data-stu-id="2dc82-108">The results from the [!INCLUDE[TLA2#tla_sql](../../../../includes/tla2sharptla-sql-md.md)] command are stored in a `DataTable` of the `DataSet` by calling the `Fill` method of the `OleDbDataAdapter`.</span></span> <span data-ttu-id="2dc82-109">`DataTable` w tym przykładzie nosi nazwę `BookTable`.</span><span class="sxs-lookup"><span data-stu-id="2dc82-109">The `DataTable` in this example is named `BookTable`.</span></span> <span data-ttu-id="2dc82-110">Następnie w przykładzie <xref:System.Windows.FrameworkElement.DataContext%2A> właściwość <xref:System.Windows.Controls.ListBox> do `DataSet` obiektu.</span><span class="sxs-lookup"><span data-stu-id="2dc82-110">The example then sets the <xref:System.Windows.FrameworkElement.DataContext%2A> property of the <xref:System.Windows.Controls.ListBox> to the `DataSet` object.</span></span>  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 <span data-ttu-id="2dc82-111">Firma Microsoft może następnie powiązać <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> właściwość <xref:System.Windows.Controls.ListBox> do `BookTable` z `DataSet`:</span><span class="sxs-lookup"><span data-stu-id="2dc82-111">We can then bind the <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> property of the <xref:System.Windows.Controls.ListBox> to `BookTable` of the `DataSet`:</span></span>  
  
 [!code-xaml[ADODataSet#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="2dc82-112">`BookItemTemplate`jest <xref:System.Windows.DataTemplate> definiuje sposób wyświetlania danych:</span><span class="sxs-lookup"><span data-stu-id="2dc82-112">`BookItemTemplate` is the <xref:System.Windows.DataTemplate> that defines how the data appears:</span></span>  
  
 [!code-xaml[ADODataSet#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml#3)]  
  
 <span data-ttu-id="2dc82-113">`IntColorConverter` Konwertuje `int` na kolor.</span><span class="sxs-lookup"><span data-stu-id="2dc82-113">The `IntColorConverter` converts an `int` to a color.</span></span> <span data-ttu-id="2dc82-114">Podczas korzystania z tego konwertera <xref:System.Windows.Controls.TextBlock.Background%2A> kolor trzeci <xref:System.Windows.Controls.TextBlock> zostanie wyświetlony zielony Jeśli wartość `NumPages` jest mniejsza niż 350 i czerwone.</span><span class="sxs-lookup"><span data-stu-id="2dc82-114">With the use of this converter, the <xref:System.Windows.Controls.TextBlock.Background%2A> color of the third <xref:System.Windows.Controls.TextBlock> appears green if the value of `NumPages` is less than 350 and red otherwise.</span></span> <span data-ttu-id="2dc82-115">Implementacja konwerter nie jest wyświetlane w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="2dc82-115">The implementation of the converter is not shown here.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2dc82-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2dc82-116">See Also</span></span>  
 <xref:System.Windows.Data.BindingListCollectionView>  
 [<span data-ttu-id="2dc82-117">Omówienie powiązania danych</span><span class="sxs-lookup"><span data-stu-id="2dc82-117">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="2dc82-118">Tematy porad</span><span class="sxs-lookup"><span data-stu-id="2dc82-118">How-to Topics</span></span>](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)