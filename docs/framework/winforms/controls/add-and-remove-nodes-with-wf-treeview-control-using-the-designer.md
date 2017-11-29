---
title: "Porady: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- examples [Windows Forms], TreeView control
- TreeView control [Windows Forms], removing nodes
- tree nodes in TreeView control
- TreeView control [Windows Forms], adding nodes
ms.assetid: 35bf1750-045e-4ec5-97cb-b47b0dbdaa2c
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f6295f915e9204e9996d8902b07a3dfc4c5c2ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-and-remove-nodes-with-the-windows-forms-treeview-control-using-the-designer"></a><span data-ttu-id="bc449-102">Porady: dodawanie i usuwanie węzłów za pomocą kontrolki TreeView formularzy systemu Windows przy użyciu narzędzia Projektant</span><span class="sxs-lookup"><span data-stu-id="bc449-102">How to: Add and Remove Nodes with the Windows Forms TreeView Control Using the Designer</span></span>
<span data-ttu-id="bc449-103">Ponieważ formularzy systemu Windows <xref:System.Windows.Forms.TreeView> kontroli wyświetlane węzły w hierarchiczny sposób, dodając należy zwrócić uwagę na to jego węzeł nadrzędny węzła.</span><span class="sxs-lookup"><span data-stu-id="bc449-103">Because the Windows Forms <xref:System.Windows.Forms.TreeView> control displays nodes in a hierarchical manner, when adding a node you must pay attention to what its parent node is.</span></span>  
  
 <span data-ttu-id="bc449-104">Poniższa procedura wymaga **aplikacji systemu Windows** projekt zawierający formularz <xref:System.Windows.Forms.TreeView> formantu.</span><span class="sxs-lookup"><span data-stu-id="bc449-104">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.TreeView> control.</span></span> <span data-ttu-id="bc449-105">Informacje o konfigurowaniu tych projektu, zobacz [jak: utworzyć projekt aplikacji systemu Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) i [porady: dodawanie formantów do formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="bc449-105">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc449-106">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="bc449-106">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="bc449-107">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="bc449-107">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="bc449-108">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="bc449-108">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-or-remove-nodes-in-the-designer"></a><span data-ttu-id="bc449-109">Aby dodać lub usunąć węzły w Projektancie</span><span class="sxs-lookup"><span data-stu-id="bc449-109">To add or remove nodes in the designer</span></span>  
  
1.  <span data-ttu-id="bc449-110">Wybierz <xref:System.Windows.Forms.TreeView> formantu.</span><span class="sxs-lookup"><span data-stu-id="bc449-110">Select the <xref:System.Windows.Forms.TreeView> control.</span></span>  
  
2.  <span data-ttu-id="bc449-111">W **właściwości** okna, kliknij przycisk **wielokropka** (![VisualStudioEllipsesButton — zrzut ekranu](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) znajdujący się obok <xref:System.Windows.Forms.TreeView.Nodes%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="bc449-111">In the **Properties** window, click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button next to the <xref:System.Windows.Forms.TreeView.Nodes%2A> property.</span></span>  
  
     <span data-ttu-id="bc449-112">**Edytor TreeNode** pojawi się.</span><span class="sxs-lookup"><span data-stu-id="bc449-112">The **TreeNode Editor** appears.</span></span>  
  
3.  <span data-ttu-id="bc449-113">Aby dodać węzły, węzeł główny musi istnieć; Jeśli nie istnieje, należy najpierw dodać głównego, klikając **Dodawanie głównego** przycisku.</span><span class="sxs-lookup"><span data-stu-id="bc449-113">To add nodes, a root node must exist; if one does not exist, you must first add a root by clicking the **Add Root** button.</span></span> <span data-ttu-id="bc449-114">Następnie można dodać węzłów podrzędnych Wybieranie katalogu głównego lub inny węzeł, a następnie klikając polecenie **Dodaj obiekt podrzędny** przycisku.</span><span class="sxs-lookup"><span data-stu-id="bc449-114">You can then add child nodes by selecting the root or any other node and clicking the **Add Child** button.</span></span>  
  
4.  <span data-ttu-id="bc449-115">Aby usunąć węzłów, wybierz węzeł, aby usunąć, a następnie kliknij przycisk **usunąć** przycisku.</span><span class="sxs-lookup"><span data-stu-id="bc449-115">To delete nodes, select the node to delete and then click the **Delete** button.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc449-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc449-116">See Also</span></span>  
 [<span data-ttu-id="bc449-117">TreeView — formant</span><span class="sxs-lookup"><span data-stu-id="bc449-117">TreeView Control</span></span>](../../../../docs/framework/winforms/controls/treeview-control-windows-forms.md)  
 [<span data-ttu-id="bc449-118">Informacje o formancie TreeView</span><span class="sxs-lookup"><span data-stu-id="bc449-118">TreeView Control Overview</span></span>](../../../../docs/framework/winforms/controls/treeview-control-overview-windows-forms.md)  
 [<span data-ttu-id="bc449-119">Porady: ustawienie ikon dla formantu TreeView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bc449-119">How to: Set Icons for the Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-set-icons-for-the-windows-forms-treeview-control.md)  
 [<span data-ttu-id="bc449-120">Porady: iterowanie wszystkich węzłów formantu TreeView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bc449-120">How to: Iterate Through All Nodes of a Windows Forms TreeView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-iterate-through-all-nodes-of-a-windows-forms-treeview-control.md)  
 [<span data-ttu-id="bc449-121">Porady: Określanie, który węzeł TreeView został kliknięty</span><span class="sxs-lookup"><span data-stu-id="bc449-121">How to: Determine Which TreeView Node Was Clicked</span></span>](../../../../docs/framework/winforms/controls/how-to-determine-which-treeview-node-was-clicked-windows-forms.md)  
 [<span data-ttu-id="bc449-122">Porady: Dodawanie niestandardowych informacji do formantu TreeView lub ListView (formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="bc449-122">How to: Add Custom Information to a TreeView or ListView Control (Windows Forms)</span></span>](../../../../docs/framework/winforms/controls/add-custom-information-to-a-treeview-or-listview-control-wf.md)