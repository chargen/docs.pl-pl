---
title: 'Porady: testowanie zachowania UserControl w czasie wykonywania'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UserControl class [Windows Forms], testing
- user controls [Windows Forms], testing
- composite controls [Windows Forms], testing
- UserControl Test Container
- UserControl class [Windows Forms], run-time behavior
ms.assetid: 4e4d5c49-1346-40ac-9d96-40211b573583
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2ce4f821a7b964b3ed2e03c795346b47bb88d618
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="9d2d9-102">Porady: testowanie zachowania UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="9d2d9-102">How to: Test the Run-Time Behavior of a UserControl</span></span>
<span data-ttu-id="9d2d9-103">Podczas opracowywania <xref:System.Windows.Forms.UserControl>, należy przetestować jego zachowania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-103">When you develop a <xref:System.Windows.Forms.UserControl>, you need to test its run-time behavior.</span></span> <span data-ttu-id="9d2d9-104">Można utworzyć projekt oddzielne aplikacji systemu Windows i umieścić formantu w formularzu testu, ale ta procedura jest niewygodne.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-104">You can create a separate Windows-based application project and place your control on a test form, but this procedure is inconvenient.</span></span> <span data-ttu-id="9d2d9-105">Sposób szybciej i łatwiej jest użycie **kontener testu UserControl** dostarczane przez program Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-105">A faster and easier way is to use the **UserControl Test Container** provided by Visual Studio.</span></span> <span data-ttu-id="9d2d9-106">Ten kontener testowy rozpoczyna się bezpośrednio z projektu biblioteki sterowania systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-106">This test container starts directly from your Windows control library project.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9d2d9-107">W celu załadować kontenera testu z <xref:System.Windows.Forms.UserControl>, kontrolka musi mieć co najmniej jeden konstruktor publiczny.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-107">For the test container to load your <xref:System.Windows.Forms.UserControl>, the control must have at least one public constructor.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d2d9-108">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="9d2d9-109">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="9d2d9-110">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="9d2d9-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d2d9-111">Formant Visual C++ nie można przetestować przy użyciu **kontener testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-111">A Visual C++ control cannot be tested using the **UserControl Test Container**.</span></span>  
  
### <a name="to-test-the-run-time-behavior-of-a-usercontrol"></a><span data-ttu-id="9d2d9-112">Aby przetestować zachowania UserControl w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="9d2d9-112">To test the run-time behavior of a UserControl</span></span>  
  
1.  <span data-ttu-id="9d2d9-113">Tworzenie projektu biblioteki sterowania systemu Windows o nazwie **TestContainerExample**.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-113">Create a Windows control library project called **TestContainerExample**.</span></span> <span data-ttu-id="9d2d9-114">Aby uzyskać więcej informacji, zobacz [szablon biblioteki systemu Windows formantu](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span><span class="sxs-lookup"><span data-stu-id="9d2d9-114">For details, see [Windows Control Library Template](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="9d2d9-115">W **Projektant formularzy systemu Windows**, przeciągnij <xref:System.Windows.Forms.Label> kontrolować z **przybornika** na powierzchnię projektu formantu.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-115">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3.  <span data-ttu-id="9d2d9-116">Naciśnij klawisz F5, aby skompilować projekt i uruchomić **kontener testu UserControl**.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-116">Press F5 to build the project and run the **UserControl Test Container**.</span></span> <span data-ttu-id="9d2d9-117">Kontener testu jest wyświetlany z Twojej <xref:System.Windows.Forms.UserControl> w **Podgląd** okienka.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-117">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4.  <span data-ttu-id="9d2d9-118">Wybierz <xref:System.Windows.Forms.Control.BackColor%2A> właściwości wyświetlane w <xref:System.Windows.Forms.PropertyGrid> formantu z prawej strony **Podgląd** okienka.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-118">Select the <xref:System.Windows.Forms.Control.BackColor%2A> property displayed in the <xref:System.Windows.Forms.PropertyGrid> control to the right of the **Preview** pane.</span></span> <span data-ttu-id="9d2d9-119">Zmień wartość na `ControlDark`.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-119">Change its value to `ControlDark`.</span></span> <span data-ttu-id="9d2d9-120">Sprawdź, czy formant zmienia kolor ciemniejszego.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-120">Observe that the control changes to a darker color.</span></span> <span data-ttu-id="9d2d9-121">Spróbuj zmienić wartości innych właściwości i obserwować wpływ na formantu.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-121">Try changing other property values and observe the effect on your control.</span></span>  
  
5.  <span data-ttu-id="9d2d9-122">Kliknij przycisk **dokowania wypełnienia kontrolki użytkownika** poniższe pole wyboru **Podgląd** okienka.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-122">Click the **Dock Fill User Control** check box below the **Preview** pane.</span></span> <span data-ttu-id="9d2d9-123">Sprawdź, czy do wypełnienia w okienku zostanie zmieniony rozmiar formantu.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-123">Observe that the control is resized to fill the pane.</span></span> <span data-ttu-id="9d2d9-124">Zmień rozmiar kontener testu i sprawdź, czy okienko zostanie zmieniony rozmiar formantu.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-124">Resize the test container and observe that the control is resized with the pane.</span></span>  
  
6.  <span data-ttu-id="9d2d9-125">Zamknij kontener testu.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-125">Close the test container.</span></span>  
  
7.  <span data-ttu-id="9d2d9-126">Dodaj inny formant użytkownika do **TestContainerExample** projektu.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-126">Add another user control to the **TestContainerExample** project.</span></span> <span data-ttu-id="9d2d9-127">Aby uzyskać więcej informacji, zobacz [NIB: porady: Dodawanie istniejących elementów do projektu](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span><span class="sxs-lookup"><span data-stu-id="9d2d9-127">For details, see [NIB:How to: Add Existing Items to a Project](http://msdn.microsoft.com/en-us/15f4cfb7-78ab-457f-9f14-099a25a6a2d3).</span></span>  
  
8.  <span data-ttu-id="9d2d9-128">W **Projektant formularzy systemu Windows**, przeciągnij <xref:System.Windows.Forms.Button> kontrolować z **przybornika** na powierzchnię projektu formantu.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-128">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.Button> control from the **Toolbox** onto the control's design surface.</span></span>  
  
9. <span data-ttu-id="9d2d9-129">Naciśnij klawisz F5, aby skompilować projekt i uruchomić kontener testu.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-129">Press F5 to build the project and run the test container.</span></span>  
  
10. <span data-ttu-id="9d2d9-130">Kliknij przycisk **wybierz kontrolkę użytkownika** <xref:System.Windows.Forms.ComboBox> do przełączania między formantami dwóch użytkowników.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-130">Click the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls.</span></span>  
  
## <a name="testing-user-controls-from-another-project"></a><span data-ttu-id="9d2d9-131">Testowanie kontrolek użytkownika z innego projektu</span><span class="sxs-lookup"><span data-stu-id="9d2d9-131">Testing User Controls from Another Project</span></span>  
 <span data-ttu-id="9d2d9-132">Formanty użytkownika z innych projektów można przetestować w kontenerze testowym bieżącego projektu.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-132">You can test user controls from other projects in your current project's test container.</span></span>  
  
#### <a name="to-test-user-controls-from-another-project"></a><span data-ttu-id="9d2d9-133">Aby przetestować kontrolek użytkownika z innego projektu</span><span class="sxs-lookup"><span data-stu-id="9d2d9-133">To test user controls from another project</span></span>  
  
1.  <span data-ttu-id="9d2d9-134">Tworzenie projektu biblioteki sterowania systemu Windows o nazwie **TestContainerExample2**.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-134">Create a Windows control library project called **TestContainerExample2**.</span></span> <span data-ttu-id="9d2d9-135">Aby uzyskać więcej informacji, zobacz [szablon biblioteki systemu Windows formantu](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span><span class="sxs-lookup"><span data-stu-id="9d2d9-135">For details, see [Windows Control Library Template](http://msdn.microsoft.com/en-us/722f4e2d-1310-4ed5-8f33-593337ab66b4).</span></span>  
  
2.  <span data-ttu-id="9d2d9-136">W **Projektant formularzy systemu Windows**, przeciągnij <xref:System.Windows.Forms.RadioButton> kontrolować z **przybornika** na powierzchnię projektu formantu.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-136">In the **Windows Forms Designer**, drag a <xref:System.Windows.Forms.RadioButton> control from the **Toolbox** onto the control's design surface.</span></span>  
  
3.  <span data-ttu-id="9d2d9-137">Naciśnij klawisz F5, aby skompilować projekt i uruchomić kontener testu.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-137">Press F5 to build the project and run the test container.</span></span> <span data-ttu-id="9d2d9-138">Kontener testu jest wyświetlany z Twojej <xref:System.Windows.Forms.UserControl> w **Podgląd** okienka.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-138">The test container appears with your <xref:System.Windows.Forms.UserControl> in the **Preview** pane.</span></span>  
  
4.  <span data-ttu-id="9d2d9-139">Kliknij przycisk **obciążenia** przycisku.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-139">Click the **Load** button.</span></span>  
  
5.  <span data-ttu-id="9d2d9-140">W **Otwórz** okno dialogowe, przejdź do **TestContainerExample**.dll, które zostały utworzone w poprzedniej procedurze.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-140">In the **Open** dialog box, navigate to **TestContainerExample**.dll, which you built in the previous procedure.</span></span> <span data-ttu-id="9d2d9-141">Wybierz **TestContainerExample**dll i kliknij przycisk **Otwórz** przycisk, aby załadować kontrolki użytkownika</span><span class="sxs-lookup"><span data-stu-id="9d2d9-141">Select **TestContainerExample**.dll and click the **Open** button to load the user controls</span></span>  
  
6.  <span data-ttu-id="9d2d9-142">Użyj **wybierz kontrolkę użytkownika** <xref:System.Windows.Forms.ComboBox> do przełączania między formantami dwóch użytkowników z **TestContainerExample** projektu.</span><span class="sxs-lookup"><span data-stu-id="9d2d9-142">Use the **Select User Control**<xref:System.Windows.Forms.ComboBox> to switch between the two user controls from the **TestContainerExample** project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d2d9-143">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d2d9-143">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 [<span data-ttu-id="9d2d9-144">Porady: autoryzowanie formantów złożonych</span><span class="sxs-lookup"><span data-stu-id="9d2d9-144">How to: Author Composite Controls</span></span>](../../../../docs/framework/winforms/controls/how-to-author-composite-controls.md)  
 [<span data-ttu-id="9d2d9-145">Wskazówki: Tworzenie formantu złożonego za pomocą Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9d2d9-145">Walkthrough: Authoring a Composite Control with Visual Basic</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [<span data-ttu-id="9d2d9-146">Wskazówki: Tworzenie formantu złożonego za pomocą Visual C#</span><span class="sxs-lookup"><span data-stu-id="9d2d9-146">Walkthrough: Authoring a Composite Control with Visual C#</span></span>](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)  
 [<span data-ttu-id="9d2d9-147">Projektanta formantów użytkownika</span><span class="sxs-lookup"><span data-stu-id="9d2d9-147">User Control Designer</span></span>](http://msdn.microsoft.com/en-us/2abb9eec-ba32-45cb-b73d-8b52a8bd6bf1)