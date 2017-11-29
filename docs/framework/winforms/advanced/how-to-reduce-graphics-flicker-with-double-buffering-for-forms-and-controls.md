---
title: "Porady: zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek"
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
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6d1b22babcc653f999ff500a5e52a12616fc1ae4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a><span data-ttu-id="d2923-102">Porady: zmniejszanie migotania grafiki za pomocą podwójnego buforowania formularzy i kontrolek</span><span class="sxs-lookup"><span data-stu-id="d2923-102">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>
<span data-ttu-id="d2923-103">Podwójne buforowanie używa bufora pamięci rozwiązywania problemów migotania skojarzone z wielu operacji malowania.</span><span class="sxs-lookup"><span data-stu-id="d2923-103">Double buffering uses a memory buffer to address the flicker problems associated with multiple paint operations.</span></span> <span data-ttu-id="d2923-104">Po włączeniu podwójnego buforowania wszystkie operacje paint najpierw są renderowane w buforze pamięci zamiast powierzchni rysowania na ekranie.</span><span class="sxs-lookup"><span data-stu-id="d2923-104">When double buffering is enabled, all paint operations are first rendered to a memory buffer instead of the drawing surface on the screen.</span></span> <span data-ttu-id="d2923-105">Po ukończeniu wszystkich działań programu paint, bufora pamięci jest kopiowana bezpośrednio na powierzchni rysowania skojarzonych z nim.</span><span class="sxs-lookup"><span data-stu-id="d2923-105">After all paint operations are completed, the memory buffer is copied directly to the drawing surface associated with it.</span></span> <span data-ttu-id="d2923-106">Grafika tylko jedna operacja jest wykonywana na ekranie, migotanie obrazu skojarzonego z operacjami malowania złożonego wyeliminowania. W przypadku większości aplikacji domyślne podwójnego buforowania dostarczonych przez [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zapewni najlepsze wyniki.</span><span class="sxs-lookup"><span data-stu-id="d2923-106">Because only one graphics operation is performed on the screen, the image flickering associated with complex painting operations is eliminated.For most applications, the default double buffering provided by the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] will provide the best results.</span></span> <span data-ttu-id="d2923-107">Standardowe formanty formularzy systemu Windows są dwa razy buforowana domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d2923-107">Standard Windows Forms controls are double buffered by default.</span></span> <span data-ttu-id="d2923-108">Można włączyć domyślny podwójnego buforowania w formularzach i utworzone formantów na dwa sposoby.</span><span class="sxs-lookup"><span data-stu-id="d2923-108">You can enable default double buffering in your forms and authored controls in two ways.</span></span> <span data-ttu-id="d2923-109">Można albo zestaw <xref:System.Windows.Forms.Control.DoubleBuffered%2A> właściwości `true`, lub możesz wywołać <xref:System.Windows.Forms.Control.SetStyle%2A> metodę, aby ustawić <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flaga `true`.</span><span class="sxs-lookup"><span data-stu-id="d2923-109">You can either set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`, or you can call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span> <span data-ttu-id="d2923-110">Obie metody włączy domyślne podwójnego buforowania formularza lub kontrolki i podaj renderowania pozbawione migotania grafiki.</span><span class="sxs-lookup"><span data-stu-id="d2923-110">Both methods will enable default double buffering for your form or control and provide flicker-free graphics rendering.</span></span> <span data-ttu-id="d2923-111">Wywoływanie <xref:System.Windows.Forms.Control.SetStyle%2A> metody jest zalecane tylko w przypadku kontrolek niestandardowych, dla których napisano kod renderowania.</span><span class="sxs-lookup"><span data-stu-id="d2923-111">Calling the <xref:System.Windows.Forms.Control.SetStyle%2A> method is recommended only for custom controls for which you have written all the rendering code.</span></span>  
  
 <span data-ttu-id="d2923-112">W bardziej zaawansowanych podwójnego buforowania, takich scenariuszach animacji lub pamięci Zaawansowane zarządzanie można zaimplementować własne podwójnego buforowania logiki.</span><span class="sxs-lookup"><span data-stu-id="d2923-112">For more advanced double buffering scenarios, such as animation or advanced memory management, you can implement your own double buffering logic.</span></span> <span data-ttu-id="d2923-113">Aby uzyskać więcej informacji, zobacz [porady: ręczne zarządzanie buforowana grafika](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="d2923-113">For more information, see [How to: Manually Manage Buffered Graphics](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span></span>  
  
### <a name="to-reduce-flicker"></a><span data-ttu-id="d2923-114">Aby zmniejszyć migotania</span><span class="sxs-lookup"><span data-stu-id="d2923-114">To reduce flicker</span></span>  
  
-   <span data-ttu-id="d2923-115">Ustaw <xref:System.Windows.Forms.Control.DoubleBuffered%2A> właściwości `true`.</span><span class="sxs-lookup"><span data-stu-id="d2923-115">Set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 <span data-ttu-id="d2923-116">\-lub -</span><span class="sxs-lookup"><span data-stu-id="d2923-116">\- or -</span></span>  
  
-   <span data-ttu-id="d2923-117">Wywołanie <xref:System.Windows.Forms.Control.SetStyle%2A> metodę, aby ustawić <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flaga `true`.</span><span class="sxs-lookup"><span data-stu-id="d2923-117">Call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="d2923-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2923-118">See Also</span></span>  
 <xref:System.Windows.Forms.Control.DoubleBuffered%2A>  
 <xref:System.Windows.Forms.Control.SetStyle%2A>  
 [<span data-ttu-id="d2923-119">Podwójnie buforowana grafika</span><span class="sxs-lookup"><span data-stu-id="d2923-119">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [<span data-ttu-id="d2923-120">Grafika i rysowanie w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d2923-120">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)