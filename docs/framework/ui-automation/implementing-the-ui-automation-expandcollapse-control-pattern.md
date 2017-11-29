---
title: "Implementacja wzorca formantu ExpandCollapse dla automatyzacji interfejsu użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- UI Automation, ExpandCollapse control pattern
- ExpandCollapse control pattern
- control patterns, ExpandCollapse
ms.assetid: 1dbabb8c-0d68-47c1-a35e-1c01cb01af26
caps.latest.revision: "25"
author: Xansky
ms.author: mhopkins
manager: markl
ms.openlocfilehash: 877fac575255159c82d1c1e3c3c4b3dbb803198e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-ui-automation-expandcollapse-control-pattern"></a><span data-ttu-id="d0a16-102">Implementacja wzorca kontrolki ExpandCollapse dla automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="d0a16-102">Implementing the UI Automation ExpandCollapse Control Pattern</span></span>
> [!NOTE]
>  <span data-ttu-id="d0a16-103">Ta dokumentacja jest przeznaczony dla deweloperów .NET Framework, które chcą korzystać zarządzanej [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] klas zdefiniowanych w <xref:System.Windows.Automation> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d0a16-103">This documentation is intended for .NET Framework developers who want to use the managed [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] classes defined in the <xref:System.Windows.Automation> namespace.</span></span> <span data-ttu-id="d0a16-104">Aby uzyskać najnowsze informacje o [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], zobacz [interfejsu API systemu Windows automatyzacji: automatyzacji interfejsu użytkownika](http://go.microsoft.com/fwlink/?LinkID=156746).</span><span class="sxs-lookup"><span data-stu-id="d0a16-104">For the latest information about [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)], see [Windows Automation API: UI Automation](http://go.microsoft.com/fwlink/?LinkID=156746).</span></span>  
  
 <span data-ttu-id="d0a16-105">W tym temacie przedstawiono wskazówki i konwencje dotyczące implementowania <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>, wraz z informacjami dotyczącymi właściwości, metod i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="d0a16-105">This topic introduces guidelines and conventions for implementing <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>, including information about properties, methods, and events.</span></span> <span data-ttu-id="d0a16-106">Łącza do dodatkowe informacje są wyświetlane na końcu przeglądu.</span><span class="sxs-lookup"><span data-stu-id="d0a16-106">Links to additional references are listed at the end of the overview.</span></span>  
  
 <span data-ttu-id="d0a16-107"><xref:System.Windows.Automation.ExpandCollapsePattern> — Wzorzec formantu jest używana do obsługi formantów, które wizualnie Rozwiń, aby wyświetlić więcej zawartości i zwijanie ukrycia zawartości.</span><span class="sxs-lookup"><span data-stu-id="d0a16-107">The <xref:System.Windows.Automation.ExpandCollapsePattern> control pattern is used to support controls that visually expand to display more content and collapse to hide content.</span></span> <span data-ttu-id="d0a16-108">Przykłady formantów, które implementują wzorzec tego formantu można znaleźć [formantu wzorzec mapowania dla klientów automatyzacji interfejsu użytkownika](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span><span class="sxs-lookup"><span data-stu-id="d0a16-108">For examples of controls that implement this control pattern, see [Control Pattern Mapping for UI Automation Clients](../../../docs/framework/ui-automation/control-pattern-mapping-for-ui-automation-clients.md).</span></span>  
  
<a name="Implementation_Guidelines_and_Conventions"></a>   
## <a name="implementation-guidelines-and-conventions"></a><span data-ttu-id="d0a16-109">Implementacja — wskazówki i konwencje</span><span class="sxs-lookup"><span data-stu-id="d0a16-109">Implementation Guidelines and Conventions</span></span>  
 <span data-ttu-id="d0a16-110">Podczas implementowania ExpandCollapse — wzorzec kontrolki, należy zwrócić uwagę następujące wskazówki i konwencje:</span><span class="sxs-lookup"><span data-stu-id="d0a16-110">When implementing the ExpandCollapse control pattern, note the following guidelines and conventions:</span></span>  
  
-   <span data-ttu-id="d0a16-111">Formanty agregacji — skompilowanej za pomocą obiektów podrzędnych, co stanowi interfejsu użytkownika dla funkcji Rozwiń/Zwiń — musi obsługiwać <xref:System.Windows.Automation.ExpandCollapsePattern> kontrolować wzorzec ich elementy podrzędne nie.</span><span class="sxs-lookup"><span data-stu-id="d0a16-111">Aggregate controls—built with child objects that provide the UI with expand/collapse functionality—must support the <xref:System.Windows.Automation.ExpandCollapsePattern> control pattern whereas their child elements do not.</span></span> <span data-ttu-id="d0a16-112">Na przykład wbudowana w kombinację pola listy, przycisk i formantów edycji kontrolki pola kombi, ale jest tylko pola kombi nadrzędnego, który musi obsługiwać <xref:System.Windows.Automation.ExpandCollapsePattern>.</span><span class="sxs-lookup"><span data-stu-id="d0a16-112">For example, a combo box control is built with a combination of list box, button, and edit controls, but it is only the parent combo box that must support the <xref:System.Windows.Automation.ExpandCollapsePattern>.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="d0a16-113">Wyjątkiem jest formant menu, która jest agregacją pojedyncze obiekty MenuItem.</span><span class="sxs-lookup"><span data-stu-id="d0a16-113">An exception is the menu control, which is an aggregate of individual MenuItem objects.</span></span> <span data-ttu-id="d0a16-114">Obiekty MenuItem może obsługiwać <xref:System.Windows.Automation.ExpandCollapsePattern> — wzorzec formantu, ale nadrzędnego Menu sterowania nie.</span><span class="sxs-lookup"><span data-stu-id="d0a16-114">The MenuItem objects can support the <xref:System.Windows.Automation.ExpandCollapsePattern> control pattern, but the parent Menu control cannot.</span></span> <span data-ttu-id="d0a16-115">Podobne wyjątek dotyczy formantów drzewa i element drzewa.</span><span class="sxs-lookup"><span data-stu-id="d0a16-115">A similar exception applies to the Tree and Tree Item controls.</span></span>  
  
-   <span data-ttu-id="d0a16-116">Gdy <xref:System.Windows.Automation.ExpandCollapseState> formantu ma ustawioną wartość <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>, wszelkie <xref:System.Windows.Automation.ExpandCollapsePattern> funkcje są obecnie nieaktywne formantu i jest tylko informacje można uzyskać za pomocą tego wzorca formantu <xref:System.Windows.Automation.ExpandCollapseState>.</span><span class="sxs-lookup"><span data-stu-id="d0a16-116">When the <xref:System.Windows.Automation.ExpandCollapseState> of a control is set to <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>, any <xref:System.Windows.Automation.ExpandCollapsePattern> functionality is currently inactive for the control and the only information that can be obtained using this control pattern is the <xref:System.Windows.Automation.ExpandCollapseState>.</span></span> <span data-ttu-id="d0a16-117">Jeśli później zostaną dodane wszystkie jego obiekty podrzędne, <xref:System.Windows.Automation.ExpandCollapseState> zmiany i <xref:System.Windows.Automation.ExpandCollapsePattern> funkcji jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="d0a16-117">If any child objects are subsequently added, the <xref:System.Windows.Automation.ExpandCollapseState> changes and <xref:System.Windows.Automation.ExpandCollapsePattern> functionality is activated.</span></span>  
  
-   <span data-ttu-id="d0a16-118"><xref:System.Windows.Automation.ExpandCollapseState>odwołuje się do widoczność obiektów natychmiastowego podrzędnych. nie odwołuje się do widoczność wszystkie obiekty zależne.</span><span class="sxs-lookup"><span data-stu-id="d0a16-118"><xref:System.Windows.Automation.ExpandCollapseState> refers to the visibility of immediate child objects only; it does not refer to the visibility of all descendant objects.</span></span>  
  
-   <span data-ttu-id="d0a16-119">Rozwiń węzeł, a funkcja zwijania jest specyficzne dla formantu.</span><span class="sxs-lookup"><span data-stu-id="d0a16-119">Expand and Collapse functionality is control-specific.</span></span> <span data-ttu-id="d0a16-120">Poniżej przedstawiono przykłady tego zachowania.</span><span class="sxs-lookup"><span data-stu-id="d0a16-120">The following are examples of this behavior.</span></span>  
  
    -   <span data-ttu-id="d0a16-121">Menu osobiste Office może być MenuItem trzy stanowy (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>, <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> i <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>) gdy formant określa stan przyjęcie, kiedy <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="d0a16-121">The Office Personal Menu can be a tri-state MenuItem (<xref:System.Windows.Automation.ExpandCollapseState.Expanded>, <xref:System.Windows.Automation.ExpandCollapseState.Collapsed> and <xref:System.Windows.Automation.ExpandCollapseState.PartiallyExpanded>) where the control specifies the state to adopt when an <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> or <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> is called.</span></span>  
  
    -   <span data-ttu-id="d0a16-122">Wywoływanie <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> na TreeItem może wyświetlać wszystkie elementy podrzędne lub tylko bezpośrednie elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="d0a16-122">Calling <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> on a TreeItem may display all descendants or only immediate children.</span></span>  
  
    -   <span data-ttu-id="d0a16-123">Jeśli wywołanie <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> w formancie przechowuje informacje o stanie jego elementy podrzędne zdarzenia zmiany widoczność mają być wysyłane, nie zdarzenia zmiany stanu Jeśli formant nadrzędny nie przechowuje stanu jego elementy podrzędne, jeśli zwinięte, może formantu zniszczyć wszystkie elementy podrzędne, które nie są już widoczne i wywołaj zdarzenie niszczone; lub może go zmienić <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> dla każdego obiektu podrzędnego i zgłoś zdarzenie zmiany widoczności.</span><span class="sxs-lookup"><span data-stu-id="d0a16-123">If calling <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> or <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> on a control maintains the state of its descendants, a visibility change event should be sent, not a state change event If the parent control does not maintain the state of its descendants when collapsed, the control may destroy all the descendants that are no longer visible and raise a destroyed event; or it may change the <xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A> for each descendant and raise a visibility change event.</span></span>  
  
-   <span data-ttu-id="d0a16-124">Aby zagwarantować nawigacji, jest pożądane dla obiekt w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa (z odpowiednią widoczność stanu), niezależnie od jego obiektów nadrzędnych <xref:System.Windows.Automation.ExpandCollapseState>.</span><span class="sxs-lookup"><span data-stu-id="d0a16-124">To guarantee navigation, it is desirable for an object to be in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree (with appropriate visibility state) regardless of its parents <xref:System.Windows.Automation.ExpandCollapseState>.</span></span> <span data-ttu-id="d0a16-125">Jeśli elementy podrzędne są generowane na żądanie, mogą występować jedynie w [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] drzewa po będzie wyświetlany dla czasu lub najpierw tylko, gdy są one widoczne.</span><span class="sxs-lookup"><span data-stu-id="d0a16-125">If descendants are generated on demand, they may only appear in the [!INCLUDE[TLA2#tla_uiautomation](../../../includes/tla2sharptla-uiautomation-md.md)] tree after being displayed for the first time or only while they are visible.</span></span>  
  
<a name="Required_Members_for_the_IValueProvider_Interface"></a>   
## <a name="required-members-for-iexpandcollapseprovider"></a><span data-ttu-id="d0a16-126">Wymagane elementy IExpandCollapseProvider</span><span class="sxs-lookup"><span data-stu-id="d0a16-126">Required Members for IExpandCollapseProvider</span></span>  
 <span data-ttu-id="d0a16-127">Poniższe właściwości i metody są wymagane do wykonania <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.</span><span class="sxs-lookup"><span data-stu-id="d0a16-127">The following properties and methods are required for implementing <xref:System.Windows.Automation.Provider.IExpandCollapseProvider>.</span></span>  
  
|<span data-ttu-id="d0a16-128">Wymagane elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d0a16-128">Required members</span></span>|<span data-ttu-id="d0a16-129">Typ elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="d0a16-129">Member type</span></span>|<span data-ttu-id="d0a16-130">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d0a16-130">Notes</span></span>|  
|----------------------|-----------------|-----------|  
|<xref:System.Windows.Automation.Provider.IExpandCollapseProvider.ExpandCollapseState%2A>|<span data-ttu-id="d0a16-131">Właściwość</span><span class="sxs-lookup"><span data-stu-id="d0a16-131">Property</span></span>|<span data-ttu-id="d0a16-132">Brak</span><span class="sxs-lookup"><span data-stu-id="d0a16-132">None</span></span>|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A>|<span data-ttu-id="d0a16-133">Metoda</span><span class="sxs-lookup"><span data-stu-id="d0a16-133">Method</span></span>|<span data-ttu-id="d0a16-134">Brak</span><span class="sxs-lookup"><span data-stu-id="d0a16-134">None</span></span>|  
|<xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A>|<span data-ttu-id="d0a16-135">Metoda</span><span class="sxs-lookup"><span data-stu-id="d0a16-135">Method</span></span>|<span data-ttu-id="d0a16-136">Brak</span><span class="sxs-lookup"><span data-stu-id="d0a16-136">None</span></span>|  
|<xref:System.Windows.Automation.AutomationPropertyChangedEventHandler>|<span data-ttu-id="d0a16-137">Zdarzenie</span><span class="sxs-lookup"><span data-stu-id="d0a16-137">Event</span></span>|<span data-ttu-id="d0a16-138">Ten formant nie ma żadnych skojarzonych zdarzeń; Użyj tego Delegat ogólny.</span><span class="sxs-lookup"><span data-stu-id="d0a16-138">This control has no associated events; use this generic delegate.</span></span>|  
  
<a name="Exceptions"></a>   
## <a name="exceptions"></a><span data-ttu-id="d0a16-139">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="d0a16-139">Exceptions</span></span>  
 <span data-ttu-id="d0a16-140">Dostawców należy zgłosić następujące wyjątki.</span><span class="sxs-lookup"><span data-stu-id="d0a16-140">Providers must throw the following exceptions.</span></span>  
  
|<span data-ttu-id="d0a16-141">Typ wyjątku</span><span class="sxs-lookup"><span data-stu-id="d0a16-141">Exception type</span></span>|<span data-ttu-id="d0a16-142">Warunek</span><span class="sxs-lookup"><span data-stu-id="d0a16-142">Condition</span></span>|  
|--------------------|---------------|  
|<xref:System.InvalidOperationException>|<span data-ttu-id="d0a16-143">Albo <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> lub <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> jest wywoływane, gdy <xref:System.Windows.Automation.ExpandCollapseState>  =  <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>.</span><span class="sxs-lookup"><span data-stu-id="d0a16-143">Either <xref:System.Windows.Automation.ExpandCollapsePattern.Expand%2A> or <xref:System.Windows.Automation.ExpandCollapsePattern.Collapse%2A> is called when the <xref:System.Windows.Automation.ExpandCollapseState> = <xref:System.Windows.Automation.ExpandCollapseState.LeafNode>.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d0a16-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d0a16-144">See Also</span></span>  
 [<span data-ttu-id="d0a16-145">Przegląd wzorców formantu automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="d0a16-145">UI Automation Control Patterns Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-overview.md)  
 [<span data-ttu-id="d0a16-146">Obsługa wzorców formantów dostawcy automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="d0a16-146">Support Control Patterns in a UI Automation Provider</span></span>](../../../docs/framework/ui-automation/support-control-patterns-in-a-ui-automation-provider.md)  
 [<span data-ttu-id="d0a16-147">Wzorce formantów automatyzacji interfejsu użytkownika dla klientów</span><span class="sxs-lookup"><span data-stu-id="d0a16-147">UI Automation Control Patterns for Clients</span></span>](../../../docs/framework/ui-automation/ui-automation-control-patterns-for-clients.md)  
 [<span data-ttu-id="d0a16-148">Nawigowanie po elementach automatyzacji interfejsu użytkownika przy użyciu opcji TreeWalker</span><span class="sxs-lookup"><span data-stu-id="d0a16-148">Navigate Among UI Automation Elements with TreeWalker</span></span>](../../../docs/framework/ui-automation/navigate-among-ui-automation-elements-with-treewalker.md)  
 [<span data-ttu-id="d0a16-149">Przegląd drzewa automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="d0a16-149">UI Automation Tree Overview</span></span>](../../../docs/framework/ui-automation/ui-automation-tree-overview.md)  
 [<span data-ttu-id="d0a16-150">Używanie buforowania w automatyzacji interfejsu użytkownika</span><span class="sxs-lookup"><span data-stu-id="d0a16-150">Use Caching in UI Automation</span></span>](../../../docs/framework/ui-automation/use-caching-in-ui-automation.md)