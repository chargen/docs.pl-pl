---
title: RelativeSource MarkupExtension
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: RelativeSource
helpviewer_keywords:
- RelativeSource markup extensions [WPF]
- XAML [WPF], RelativeSource markup extension
ms.assetid: 26be4721-49b5-4717-a92e-7d54ad0d3a81
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 41978e7b91c50b33649bd88e23d22fce7a272c5b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="relativesource-markupextension"></a><span data-ttu-id="c2b97-102">RelativeSource MarkupExtension</span><span class="sxs-lookup"><span data-stu-id="c2b97-102">RelativeSource MarkupExtension</span></span>
<span data-ttu-id="c2b97-103">Określa właściwości <xref:System.Windows.Data.RelativeSource> źródle powiązania do użycia w [powiązania — rozszerzenie znaczników](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), lub gdy ustawienie <xref:System.Windows.Data.Binding.RelativeSource%2A> właściwość <xref:System.Windows.Data.Binding> elementu w języku XAML.</span><span class="sxs-lookup"><span data-stu-id="c2b97-103">Specifies properties of a <xref:System.Windows.Data.RelativeSource> binding source, to be used within a [Binding Markup Extension](../../../../docs/framework/wpf/advanced/binding-markup-extension.md), or when setting the <xref:System.Windows.Data.Binding.RelativeSource%2A> property of a <xref:System.Windows.Data.Binding> element established in XAML.</span></span>  
  
## <a name="xaml-attribute-usage"></a><span data-ttu-id="c2b97-104">Użycie atrybutu języka XAML</span><span class="sxs-lookup"><span data-stu-id="c2b97-104">XAML Attribute Usage</span></span>  
  
```xml  
<Binding RelativeSource="{RelativeSource modeEnumValue}" .../>  
```  
  
## <a name="xaml-attribute-usage-nested-within-binding-extension"></a><span data-ttu-id="c2b97-105">Użycie atrybutu języka XAML (zagnieżdżonego w rozszerzeniu Binding)</span><span class="sxs-lookup"><span data-stu-id="c2b97-105">XAML Attribute Usage (nested within Binding extension)</span></span>  
  
```xml  
<object property="{Binding RelativeSource={RelativeSource modeEnumValue} ...}" .../>  
```  
  
## <a name="xaml-object-element-usage"></a><span data-ttu-id="c2b97-106">Użycie elementu obiektu języka XAML</span><span class="sxs-lookup"><span data-stu-id="c2b97-106">XAML Object Element Usage</span></span>  
  
```xml  
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource Mode="modeEnumValue"/>  
  </Binding.RelativeSource>  
</Binding>  
- or   
<Binding>  
  <Binding.RelativeSource>  
    <RelativeSource  
      Mode="FindAncestor"  
      AncestorType="{x:Type typeName}"  
      AncestorLevel="intLevel"  
    />  
  </Binding.RelativeSource>  
</Binding>  
```  
  
## <a name="xaml-values"></a><span data-ttu-id="c2b97-107">Wartości XAML</span><span class="sxs-lookup"><span data-stu-id="c2b97-107">XAML Values</span></span>  
  
|||  
|-|-|  
|`modeEnumValue`|<span data-ttu-id="c2b97-108">Jeden z poniższych:</span><span class="sxs-lookup"><span data-stu-id="c2b97-108">One of the following:</span></span><br /><br /> <span data-ttu-id="c2b97-109">-Token ciągu `Self`; odpowiada <xref:System.Windows.Data.RelativeSource> utworzonego za jego <xref:System.Windows.Data.RelativeSource.Mode%2A> ustawioną właściwość <xref:System.Windows.Data.RelativeSourceMode.Self>.</span><span class="sxs-lookup"><span data-stu-id="c2b97-109">-   The string token `Self`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.Self>.</span></span><br /><span data-ttu-id="c2b97-110">-Token ciągu `TemplatedParent`; odpowiada <xref:System.Windows.Data.RelativeSource> utworzonego za jego <xref:System.Windows.Data.RelativeSource.Mode%2A> ustawioną właściwość <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span><span class="sxs-lookup"><span data-stu-id="c2b97-110">-   The string token `TemplatedParent`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.TemplatedParent>.</span></span><br /><span data-ttu-id="c2b97-111">-Token ciągu `PreviousData`; odpowiada <xref:System.Windows.Data.RelativeSource> utworzonego za jego <xref:System.Windows.Data.RelativeSource.Mode%2A> ustawioną właściwość <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span><span class="sxs-lookup"><span data-stu-id="c2b97-111">-   The string token `PreviousData`; corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.PreviousData>.</span></span><br /><span data-ttu-id="c2b97-112">-Poniżej zamieszczono informacje na `FindAncestor` tryb.</span><span class="sxs-lookup"><span data-stu-id="c2b97-112">-   See below for information on `FindAncestor` mode.</span></span>|  
|`FindAncestor`|<span data-ttu-id="c2b97-113">Token ciągu `FindAncestor`.</span><span class="sxs-lookup"><span data-stu-id="c2b97-113">The string token `FindAncestor`.</span></span> <span data-ttu-id="c2b97-114">Za pomocą tego tokenu zgodnie z którymi przechodzi w tryb `RelativeSource` Określa typ elementu nadrzędnego i opcjonalnie na poziomie nadrzędnym.</span><span class="sxs-lookup"><span data-stu-id="c2b97-114">Using this token enters a mode whereby a `RelativeSource` specifies an ancestor type and optionally an ancestor level.</span></span> <span data-ttu-id="c2b97-115">Odpowiada to <xref:System.Windows.Data.RelativeSource> utworzonego za jego <xref:System.Windows.Data.RelativeSource.Mode%2A> ustawioną właściwość <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span><span class="sxs-lookup"><span data-stu-id="c2b97-115">This corresponds to a <xref:System.Windows.Data.RelativeSource> as created with its <xref:System.Windows.Data.RelativeSource.Mode%2A> property set to <xref:System.Windows.Data.RelativeSourceMode.FindAncestor>.</span></span>|  
|`typeName`|<span data-ttu-id="c2b97-116">Wymagany dla `FindAncestor` trybu.</span><span class="sxs-lookup"><span data-stu-id="c2b97-116">Required for `FindAncestor` mode.</span></span> <span data-ttu-id="c2b97-117">Nazwa typu, który wypełnia <xref:System.Windows.Data.RelativeSource.AncestorType%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="c2b97-117">The name of a type, which fills the <xref:System.Windows.Data.RelativeSource.AncestorType%2A> property.</span></span>|  
|`intLevel`|<span data-ttu-id="c2b97-118">Opcjonalny w przypadku `FindAncestor` tryb.</span><span class="sxs-lookup"><span data-stu-id="c2b97-118">Optional for `FindAncestor` mode.</span></span> <span data-ttu-id="c2b97-119">Poziom elementu nadrzędnego (patrząc w kierunku nadrzędności w drzewie logicznym).</span><span class="sxs-lookup"><span data-stu-id="c2b97-119">An ancestor level (evaluated towards the parent direction in the logical tree).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c2b97-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c2b97-120">Remarks</span></span>  
 <span data-ttu-id="c2b97-121">`{RelativeSource TemplatedParent}`Powiązanie użycia to technika klucza, która dotyczy większych koncepcji oddzielenie logiki formantu i formantu interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c2b97-121">`{RelativeSource TemplatedParent}` binding usages are a key technique that addresses a larger concept of the separation of a control's UI and a control's logic.</span></span> <span data-ttu-id="c2b97-122">Umożliwia tworzenie powiązań z wewnątrz definicji szablonu do elementu nadrzędnego używającego szablonu (tzn. do wystąpienia obiektu, do którego w czasie wykonywania szablon jest stosowany).</span><span class="sxs-lookup"><span data-stu-id="c2b97-122">This enables binding from within the template definition to the templated parent (the run time object instance where the template is applied).</span></span> <span data-ttu-id="c2b97-123">Dla tego przypadku [rozszerzenie znacznika TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) w rzeczywistości jest skróconą formą następującego wyrażenia powiązania: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span><span class="sxs-lookup"><span data-stu-id="c2b97-123">For this case, the [TemplateBinding Markup Extension](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) is in fact a shorthand for the following binding expression: `{Binding RelativeSource={RelativeSource TemplatedParent}}`.</span></span> <span data-ttu-id="c2b97-124">`TemplateBinding`lub `{RelativeSource TemplatedParent}` użycia są tylko odpowiednie w języku XAML, który definiuje szablonu.</span><span class="sxs-lookup"><span data-stu-id="c2b97-124">`TemplateBinding` or `{RelativeSource TemplatedParent}` usages are both only relevant within the XAML that defines a template.</span></span> <span data-ttu-id="c2b97-125">Aby uzyskać więcej informacji, zobacz [rozszerzenie znacznika TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)</span><span class="sxs-lookup"><span data-stu-id="c2b97-125">For more information, see [TemplateBinding Markup Extension](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)</span></span>  
  
 <span data-ttu-id="c2b97-126">`{RelativeSource FindAncestor}`jest głównie używane w szablonów kontrolki lub przewidywalną niezależne kompozycji interfejsu użytkownika, w przypadkach, gdy formant zawsze powinien być w drzewie wizualnym określonego typu elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="c2b97-126">`{RelativeSource FindAncestor}` is mainly used in control templates or predictable self-contained UI compositions, for cases where a control is always expected to be in a visual tree of a certain ancestor type.</span></span> <span data-ttu-id="c2b97-127">Na przykład użyć elementów formantu elementów `FindAncestor` użycia w celu powiązania właściwości ich elementów kontroli nadrzędnego elementu nadrzędnego.</span><span class="sxs-lookup"><span data-stu-id="c2b97-127">For example, items of an items control might use `FindAncestor` usages to bind to properties of their items control parent ancestor.</span></span> <span data-ttu-id="c2b97-128">Elementy, które są częścią kompozycji formantu w szablonie można także użyć `FindAncestor` powiązania z elementy nadrzędne w tej samej struktury kompozycji.</span><span class="sxs-lookup"><span data-stu-id="c2b97-128">Or, elements that are part of control composition in a template can use `FindAncestor` bindings to the parent elements in that same composition structure.</span></span>  
  
 <span data-ttu-id="c2b97-129">W składni elementu obiektu `FindAncestor` tryb opisane w sekcjach składni języka XAML, drugi obiekt elementu jest używana składnia specjalnie z myślą o `FindAncestor` tryb.</span><span class="sxs-lookup"><span data-stu-id="c2b97-129">In the object element syntax for `FindAncestor` mode shown in the XAML Syntax sections, the second object element syntax is used specifically for `FindAncestor` mode.</span></span> <span data-ttu-id="c2b97-130">`FindAncestor`tryb wymaga <xref:System.Windows.Data.RelativeSource.AncestorType%2A> wartość.</span><span class="sxs-lookup"><span data-stu-id="c2b97-130">`FindAncestor` mode requires an <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value.</span></span> <span data-ttu-id="c2b97-131">Należy ustawić <xref:System.Windows.Data.RelativeSource.AncestorType%2A> jako przy użyciu atrybutu [x: Type — rozszerzenie znaczników](../../../../docs/framework/xaml-services/x-type-markup-extension.md) odwołanie do typu elementu nadrzędnego do wyszukania.</span><span class="sxs-lookup"><span data-stu-id="c2b97-131">You must set <xref:System.Windows.Data.RelativeSource.AncestorType%2A> as an attribute using an [x:Type Markup Extension](../../../../docs/framework/xaml-services/x-type-markup-extension.md) reference to the type of ancestor to look for.</span></span> <span data-ttu-id="c2b97-132"><xref:System.Windows.Data.RelativeSource.AncestorType%2A> Wartość jest używana podczas przetwarzania żądania wiązania w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c2b97-132">The <xref:System.Windows.Data.RelativeSource.AncestorType%2A> value is used when the binding request is processed at run-time.</span></span>  
  
 <span data-ttu-id="c2b97-133">Dla `FindAncestor` tryb, opcjonalna właściwość <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> może pomóc odróżniania wyszukiwania elementu nadrzędnego w przypadkach, w przypadku, gdy jest prawdopodobnie więcej niż jednego elementu nadrzędnego tego typu istniejącego w drzewie elementu.</span><span class="sxs-lookup"><span data-stu-id="c2b97-133">For `FindAncestor` mode, the optional property <xref:System.Windows.Data.RelativeSource.AncestorLevel%2A> can help disambiguate the ancestor lookup in cases where there is possibly more than one ancestor of that type existing in the element tree.</span></span>  
  
 <span data-ttu-id="c2b97-134">Aby uzyskać więcej informacji na temat sposobu użycia `FindAncestor` tryb, zobacz <xref:System.Windows.Data.RelativeSource>.</span><span class="sxs-lookup"><span data-stu-id="c2b97-134">For more information on how to use the `FindAncestor` mode, see <xref:System.Windows.Data.RelativeSource>.</span></span>  
  
 <span data-ttu-id="c2b97-135">`{RelativeSource Self}`jest przydatne w scenariuszach między te dwie właściwości gdzie jedną właściwość wystąpienia zależy od wartość inna właściwość w tym samym wystąpieniu i Brak relacji właściwości zależności ogólne (na przykład koercja) już istnieje.</span><span class="sxs-lookup"><span data-stu-id="c2b97-135">`{RelativeSource Self}` is useful for scenarios where one property of an instance should depend on the value of another property of the same instance, and no general dependency property relationship (such as coercion) already exists between those two properties.</span></span> <span data-ttu-id="c2b97-136">Mimo że rzadko, że dwie właściwości istnieje w obiekcie tak, aby wartości są identyczne dosłownie (i tak samo wpisywania), można także zastosować `Converter` parametr do powiązania, które ma `{RelativeSource Self}`i używania do konwersji między źródłem i typy elementów docelowych.</span><span class="sxs-lookup"><span data-stu-id="c2b97-136">Although it is rare that two properties exist on an object such that the values are literally identical (and are identically typed), you can also apply a `Converter` parameter to a binding that has `{RelativeSource Self}`, and use the converter to convert between source and target types.</span></span> <span data-ttu-id="c2b97-137">Inny scenariusz `{RelativeSource Self}` jest częścią <xref:System.Windows.MultiDataTrigger>.</span><span class="sxs-lookup"><span data-stu-id="c2b97-137">Another scenario for `{RelativeSource Self}` is as part of a <xref:System.Windows.MultiDataTrigger>.</span></span>  
  
 <span data-ttu-id="c2b97-138">Na przykład definiuje następujące XAML <xref:System.Windows.Shapes.Rectangle> element takie wprowadzonym niezależnie od tego, jakie korzyści dla <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.Shapes.Rectangle> jest zawsze kwadrat:`<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span><span class="sxs-lookup"><span data-stu-id="c2b97-138">For example, the following XAML defines a <xref:System.Windows.Shapes.Rectangle> element such that no matter what value is entered for <xref:System.Windows.FrameworkElement.Width%2A>, the <xref:System.Windows.Shapes.Rectangle> is always a square: `<Rectangle Width="200" Height="{Binding RelativeSource={RelativeSource Self}, Path=Width}" .../>`</span></span>  
  
 <span data-ttu-id="c2b97-139">`{RelativeSource PreviousData}`jest przydatne w szablonach danych lub w przypadkach, gdy powiązania użycia kolekcji jako źródła danych.</span><span class="sxs-lookup"><span data-stu-id="c2b97-139">`{RelativeSource PreviousData}` is useful either in data templates, or in cases where bindings are using a collection as the data source.</span></span> <span data-ttu-id="c2b97-140">Można użyć `{RelativeSource PreviousData}` aby wyróżnić relacji między elementami danych sąsiadujących ze sobą w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c2b97-140">You can use `{RelativeSource PreviousData}` to highlight relationships between adjacent data items in the collection.</span></span> <span data-ttu-id="c2b97-141">Powiązane technika jest ustanowienie <xref:System.Windows.Data.MultiBinding> między elementami bieżącego i poprzedniego źródła danych i użycia konwertera dla tego powiązania w celu obliczenia różnicy między dwoma elementami i ich właściwości.</span><span class="sxs-lookup"><span data-stu-id="c2b97-141">A related technique is to establish a <xref:System.Windows.Data.MultiBinding> between the current and previous items in the data source, and use a converter on that binding to determine the difference between the two items and their properties.</span></span>  
  
 <span data-ttu-id="c2b97-142">W poniższym przykładzie pierwszy <xref:System.Windows.Controls.TextBlock> w elementach szablonów wskazuje aktualną liczbę.</span><span class="sxs-lookup"><span data-stu-id="c2b97-142">In the following example, the first <xref:System.Windows.Controls.TextBlock> in the items template displays the current number.</span></span> <span data-ttu-id="c2b97-143">Drugi <xref:System.Windows.Controls.TextBlock> powiązanie <xref:System.Windows.Data.MultiBinding> nominalnie zawierającego dwa <xref:System.Windows.Data.Binding> consistuents: bieżącego rekordu, a obiekt binding używający celowo poprzedniego rekordu danych przy użyciu `{RelativeSource PreviousData}`.</span><span class="sxs-lookup"><span data-stu-id="c2b97-143">The second <xref:System.Windows.Controls.TextBlock> binding is a <xref:System.Windows.Data.MultiBinding> that nominally has two <xref:System.Windows.Data.Binding> consistuents: the current record, and a binding that deliberately uses the previous data record by using `{RelativeSource PreviousData}`.</span></span> <span data-ttu-id="c2b97-144">Następnie konwertera na <xref:System.Windows.Data.MultiBinding> oblicza różnicę i zwraca go do powiązania.</span><span class="sxs-lookup"><span data-stu-id="c2b97-144">Then, a converter on the <xref:System.Windows.Data.MultiBinding> calculates the difference and returns it to the binding.</span></span>  
  
```xml  
<ListBox Name="fibolist">  
    <ListBox.ItemTemplate>  
        <DataTemplate>  
            <StackPanel Orientation="Horizontal">  
            <TextBlock Text="{Binding}"/>  
            <TextBlock>, difference = </TextBlock>  
                <TextBlock>  
                    <TextBlock.Text>  
                        <MultiBinding Converter="{StaticResource DiffConverter}">  
                            <Binding/>  
                            <Binding RelativeSource="{RelativeSource PreviousData}"/>  
                        </MultiBinding>  
                    </TextBlock.Text>  
                </TextBlock>  
            </StackPanel>  
        </DataTemplate>  
    </ListBox.ItemTemplate>  
```  
  
 <span data-ttu-id="c2b97-145">Zobacz opisujący wiązanie danych koncepcji nie objętych w tym miejscu [omówienie powiązania danych](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="c2b97-145">Describing data binding as a concept is not covered here, see [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
 <span data-ttu-id="c2b97-146">W [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] implementacji procesora XAML, obsługę tego rozszerzenia znacznika jest definiowana za pomocą <xref:System.Windows.Data.RelativeSource> klasy.</span><span class="sxs-lookup"><span data-stu-id="c2b97-146">In the [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] XAML processor implementation, the handling for this markup extension is defined by the <xref:System.Windows.Data.RelativeSource> class.</span></span>  
  
 <span data-ttu-id="c2b97-147">`RelativeSource`to rozszerzenie znacznika.</span><span class="sxs-lookup"><span data-stu-id="c2b97-147">`RelativeSource` is a markup extension.</span></span> <span data-ttu-id="c2b97-148">Rozszerzenia znaczników są zazwyczaj implementowane w sytuacji, gdy istnieje wymóg, aby wartości atrybutów były wyprowadzane w postaci innej niż wartości literałów lub nazwy programów obsługi, a wymóg ma charakter bardziej globalny niż zwykłe umieszczenie konwerterów typów w niektórych typach lub właściwościach.</span><span class="sxs-lookup"><span data-stu-id="c2b97-148">Markup extensions are typically implemented when there is a requirement to escape attribute values to be other than literal values or handler names, and the requirement is more global than just putting type converters on certain types or properties.</span></span> <span data-ttu-id="c2b97-149">Wszystkie rozszerzenia znaczników w XAML, użyj `{` i `}` znaków w ich składni atrybutu Konwencji, za pomocą którego procesora XAML rozpoznaje, że rozszerzenie znacznika musi przetworzyć atrybutu.</span><span class="sxs-lookup"><span data-stu-id="c2b97-149">All markup extensions in XAML use the `{` and `}` characters in their attribute syntax, which is the convention by which a XAML processor recognizes that a markup extension must process the attribute.</span></span> <span data-ttu-id="c2b97-150">Aby uzyskać więcej informacji, zobacz [rozszerzenia znaczników i WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span><span class="sxs-lookup"><span data-stu-id="c2b97-150">For more information, see [Markup Extensions and WPF XAML](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2b97-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2b97-151">See Also</span></span>  
 <xref:System.Windows.Data.Binding>  
 [<span data-ttu-id="c2b97-152">Style i tworzenia szablonów</span><span class="sxs-lookup"><span data-stu-id="c2b97-152">Styling and Templating</span></span>](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [<span data-ttu-id="c2b97-153">Omówienie XAML (WPF)</span><span class="sxs-lookup"><span data-stu-id="c2b97-153">XAML Overview (WPF)</span></span>](../../../../docs/framework/wpf/advanced/xaml-overview-wpf.md)  
 [<span data-ttu-id="c2b97-154">Rozszerzenia znaczników i WPF XAML</span><span class="sxs-lookup"><span data-stu-id="c2b97-154">Markup Extensions and WPF XAML</span></span>](../../../../docs/framework/wpf/advanced/markup-extensions-and-wpf-xaml.md)  
 [<span data-ttu-id="c2b97-155">Omówienie powiązania danych</span><span class="sxs-lookup"><span data-stu-id="c2b97-155">Data Binding Overview</span></span>](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [<span data-ttu-id="c2b97-156">Przegląd deklaracji powiązania</span><span class="sxs-lookup"><span data-stu-id="c2b97-156">Binding Declarations Overview</span></span>](../../../../docs/framework/wpf/data/binding-declarations-overview.md)  
 [<span data-ttu-id="c2b97-157">x: Type — rozszerzenie znaczników</span><span class="sxs-lookup"><span data-stu-id="c2b97-157">x:Type Markup Extension</span></span>](../../../../docs/framework/xaml-services/x-type-markup-extension.md)