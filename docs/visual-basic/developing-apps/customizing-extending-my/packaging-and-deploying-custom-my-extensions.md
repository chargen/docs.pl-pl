---
title: "Pakowanie i wdrażanie niestandardowych rozszerzeń My (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- My namespace [Visual Basic], customizing
- My namespace
- My namespace [Visual Basic], extending
ms.assetid: fd89c54b-0290-4c50-95a3-ff17d4487a21
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 94a9ea977d0add14ae9f0c9a889b008b94610ee0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="packaging-and-deploying-custom-my-extensions-visual-basic"></a><span data-ttu-id="72212-102">Pakowanie i wdrażanie niestandardowych rozszerzeń My (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="72212-102">Packaging and deploying custom My extensions (Visual Basic)</span></span>
<span data-ttu-id="72212-103">Visual Basic umożliwia łatwe do wdrożenia niestandardowe `My` rozszerzeń nazw przy użyciu szablonów programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="72212-103">Visual Basic provides an easy way for you to deploy your custom `My` namespace extensions by using Visual Studio templates.</span></span> <span data-ttu-id="72212-104">Jeśli tworzysz szablon projektu, dla którego Twojej `My` rozszerzenia są integralną częścią nowy typ projektu, po prostu może zawierać niestandardowe `My` kod rozszerzenia w projekcie podczas eksportowania szablonu.</span><span class="sxs-lookup"><span data-stu-id="72212-104">If you are creating a project template for which your `My` extensions are an integral part of the new project type, you can just include your custom `My` extension code with the project when you export the template.</span></span> <span data-ttu-id="72212-105">Aby uzyskać więcej informacji na temat eksportowania szablonów projektu, zobacz [porady: Tworzenie szablonów projektów](/visualstudio/ide/how-to-create-project-templates).</span><span class="sxs-lookup"><span data-stu-id="72212-105">For more information about exporting project templates, see [How to: Create Project Templates](/visualstudio/ide/how-to-create-project-templates).</span></span>  
  
 <span data-ttu-id="72212-106">Jeśli niestandardowe `My` rozszerzenia znajduje się w pliku kodu pojedynczego, możesz wyeksportować plik jako szablon elementu, który użytkownicy mogą dodawać do dowolnego typu projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="72212-106">If your custom `My` extension is in a single code file, you can export the file as an item template that users can add to any type of Visual Basic project.</span></span> <span data-ttu-id="72212-107">Następnie możesz dostosować szablon elementu, aby włączyć dodatkowe funkcje i zachowanie dla niestandardowych `My` rozszerzenia w projektach Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="72212-107">You can then customize the item template to enable additional capabilities and behavior for your custom `My` extension in a Visual Basic project.</span></span> <span data-ttu-id="72212-108">Te możliwości są następujące:</span><span class="sxs-lookup"><span data-stu-id="72212-108">Those capabilities include the following:</span></span>  
  
-   <span data-ttu-id="72212-109">Zezwalanie użytkownikom na zarządzanie niestandardowe `My` rozszerzenia **Moje rozszerzenia** strony projektanta projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="72212-109">Allowing users to manage your custom `My` extension from the **My Extensions** page of the Visual Basic Project Designer.</span></span>  
  
-   <span data-ttu-id="72212-110">Automatyczne dodawanie niestandardowe `My` rozszerzenia, gdy odwołanie do określonego zestawu jest dodawany do projektu.</span><span class="sxs-lookup"><span data-stu-id="72212-110">Automatically adding your custom `My` extension when a reference to a specified assembly is added to a project.</span></span>  
  
-   <span data-ttu-id="72212-111">Ukrywanie `My` szablon elementu rozszerzenia w **Dodaj element** okna dialogowego, dzięki czemu nie znajduje się na liście elementów projektu.</span><span class="sxs-lookup"><span data-stu-id="72212-111">Hiding the `My` extension item template in the **Add Item** dialog box so that it is not included in the list of project items.</span></span>  
  
 <span data-ttu-id="72212-112">W tym temacie omówiono sposób pakiet niestandardowy `My` rozszerzenia jako szablon ukryty element, który można zarządzać za pomocą **Moje rozszerzenia** strony projektanta projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="72212-112">This topic discusses how to package a custom `My` extension as a hidden item template that can be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="72212-113">Niestandardowa `My` rozszerzenia można również dodać automatycznie podczas dodawania do projektu odwołanie do określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="72212-113">The custom `My` extension can also be added automatically when a reference to a specified assembly is added to a project.</span></span>  
  
## <a name="create-a-my-namespace-extension"></a><span data-ttu-id="72212-114">Utwórz moje rozszerzenie przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="72212-114">Create a My namespace extension</span></span>  
 <span data-ttu-id="72212-115">Pierwszym krokiem podczas tworzenia pakietu wdrożeniowego dla niestandardowego `My` rozszerzenia jest utworzenie rozszerzenia jako plik pojedynczy kod.</span><span class="sxs-lookup"><span data-stu-id="72212-115">The first step in creating a deployment package for a custom `My` extension is to create the extension as a single code file.</span></span> <span data-ttu-id="72212-116">Szczegółowe informacje i wskazówki dotyczące sposobu tworzenia niestandardowego `My` rozszerzenia, zobacz [rozszerzanie My Namespace w Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span><span class="sxs-lookup"><span data-stu-id="72212-116">For details and guidance about how to create a custom `My` extension, see [Extending the My Namespace in Visual Basic](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md).</span></span>  
  
## <a name="export-a-my-namespace-extension-as-an-item-template"></a><span data-ttu-id="72212-117">Eksportuj Moje rozszerzenie przestrzeni nazw jako szablon elementu</span><span class="sxs-lookup"><span data-stu-id="72212-117">Export a My namespace extension as an item template</span></span>  
 <span data-ttu-id="72212-118">Po utworzeniu pliku kodu, który zawiera Twoje `My` rozszerzenie przestrzeni nazw, możesz wyeksportować plik kodu jako szablon elementu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="72212-118">After you have a code file that includes your `My` namespace extension, you can export the code file as a Visual Studio item template.</span></span> <span data-ttu-id="72212-119">Aby uzyskać instrukcje na temat sposobu eksportowania pliku jako szablon elementu programu Visual Studio, zobacz [porady: Tworzenie szablonów elementów](/visualstudio/ide/how-to-create-item-templates).</span><span class="sxs-lookup"><span data-stu-id="72212-119">For instructions on how to export a file as a Visual Studio item template, see [How to: Create Item Templates](/visualstudio/ide/how-to-create-item-templates).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="72212-120">Jeśli Twoje `My` rozszerzenie przestrzeni nazw ma zależność w określonym zestawie, można dostosować szablon elementu, aby automatycznie zainstalować z `My` rozszerzenia nazw podczas dodawania odwołania do tego zestawu.</span><span class="sxs-lookup"><span data-stu-id="72212-120">If your `My` namespace extension has a dependency on a particular assembly, you can customize your item template to automatically install your `My` namespace extension when a reference to that assembly is added.</span></span> <span data-ttu-id="72212-121">W związku z tym można wykluczyć odwołanie do zestawu, podczas eksportowania pliku kodu jako szablon elementu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="72212-121">As a result, you will want to exclude that assembly reference when you export the code file as a Visual Studio item template.</span></span>  
  
## <a name="customize-the-item-template"></a><span data-ttu-id="72212-122">Dostosowywanie szablonu elementu</span><span class="sxs-lookup"><span data-stu-id="72212-122">Customize the item template</span></span>  
 <span data-ttu-id="72212-123">Można włączyć można zarządzać za pomocą szablonu elementu **Moje rozszerzenia** strony projektanta projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="72212-123">You can enable your item template to be managed from the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="72212-124">Można również włączyć szablon elementu, który ma zostać dodana automatycznie po dodaniu do projektu odwołanie do określonego zestawu.</span><span class="sxs-lookup"><span data-stu-id="72212-124">You can also enable the item template to be added automatically when a reference to a specified assembly is added to a project.</span></span> <span data-ttu-id="72212-125">Aby włączyć te modyfikacje, będzie Dodaj nowy plik o nazwie pliku CustomData szablonu i następnie dodać nowego elementu do pliku XML w pliku .vstemplate.</span><span class="sxs-lookup"><span data-stu-id="72212-125">To enable these customizations, you will add a new file, called the CustomData file, to your template, and then add a new element to the XML in your .vstemplate file.</span></span>  
  
### <a name="add-the-customdata-file"></a><span data-ttu-id="72212-126">Dodaj plik CustomData</span><span class="sxs-lookup"><span data-stu-id="72212-126">Add the CustomData file</span></span>  
 <span data-ttu-id="72212-127">Plik CustomData jest plik tekstowy, który ma rozszerzenie nazwy pliku. CustomData (nazwa pliku można ustawić dowolną wartość zrozumiały dla szablonu) i który zawiera kod XML.</span><span class="sxs-lookup"><span data-stu-id="72212-127">The CustomData file is a text file that has a file name extension of .CustomData (the file name can be set to any value meaningful to your template) and that contains XML.</span></span> <span data-ttu-id="72212-128">Kod XML w pliku CustomData nakazuje Visual Basic, aby uwzględnić Twojej `My` rozszerzenia, gdy użytkownicy używają **Moje rozszerzenia** strony projektanta projektu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="72212-128">The XML in the CustomData file instructs Visual Basic to include your `My` extension when users use the **My Extensions** page of the Visual Basic Project Designer.</span></span> <span data-ttu-id="72212-129">Możesz opcjonalnie dodać <`AssemblyFullName>` atrybutu CustomData pliku XML.</span><span class="sxs-lookup"><span data-stu-id="72212-129">You can optionally add the <`AssemblyFullName>` attribute to your CustomData file XML.</span></span> <span data-ttu-id="72212-130">Powoduje to, że Visual Basic, aby automatycznie zainstalować niestandardowe `My` rozszerzenia, gdy odwołanie do określonego zestawu jest dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="72212-130">This instructs Visual Basic to automatically install your custom `My` extension when a reference to a particular assembly is added to the project.</span></span> <span data-ttu-id="72212-131">Można użyć dowolnego edytora tekstu lub edytora XML, aby utworzyć plik CustomData, a następnie dodaj go do szablonu elementu skompresowanego folderu (pliku .zip).</span><span class="sxs-lookup"><span data-stu-id="72212-131">You can use any text editor or XML editor to create the CustomData file, and then add it to your item template's compressed folder (.zip file).</span></span>  
  
 <span data-ttu-id="72212-132">Na przykład następujący kod XML zawiera zawartość pliku CustomData, który doda element szablonu do folderu Moje rozszerzenia projektu Visual Basic, gdy odwołanie do zestawu Microsoft.VisualBasic.PowerPacks.Vs.dll jest dodane do projektu.</span><span class="sxs-lookup"><span data-stu-id="72212-132">For example, the following XML shows the contents of a CustomData file that will add the template item to the My Extensions folder of a Visual Basic project when a reference to the Microsoft.VisualBasic.PowerPacks.Vs.dll assembly is added to the project.</span></span>  
  
```xml  
<VBMyExtensionTemplate   
    ID="Microsoft.VisualBasic.Samples.MyExtensions.MyPrinterInfo"   
    Version="1.0.0.0"  
    AssemblyFullName="Microsoft.VisualBasic.PowerPacks.vs"  
/>  
```  
  
 <span data-ttu-id="72212-133">Zawiera plik CustomData <`VBMyExtensionTemplate>` element, który ma atrybuty wymienione w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="72212-133">The CustomData file contains a <`VBMyExtensionTemplate>` element that has attributes as listed in the following table.</span></span>  
  
|<span data-ttu-id="72212-134">Atrybut</span><span class="sxs-lookup"><span data-stu-id="72212-134">Attribute</span></span>|<span data-ttu-id="72212-135">Opis</span><span class="sxs-lookup"><span data-stu-id="72212-135">Description</span></span>|  
|---|---|  
|`ID`|<span data-ttu-id="72212-136">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="72212-136">Required.</span></span> <span data-ttu-id="72212-137">Unikatowy identyfikator dla rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="72212-137">A unique identifier for the extension.</span></span> <span data-ttu-id="72212-138">Jeśli rozszerzenie o tym identyfikatorze został już dodany do projektu, użytkownik nie będzie monitowany dodać ją ponownie.</span><span class="sxs-lookup"><span data-stu-id="72212-138">If the extension that has this ID has already been added to the project, the user will not be prompted to add it again.</span></span>|  
|`Version`|<span data-ttu-id="72212-139">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="72212-139">Required.</span></span> <span data-ttu-id="72212-140">Numer wersji dla szablonu elementu.</span><span class="sxs-lookup"><span data-stu-id="72212-140">A version number for the item template.</span></span>|  
|`AssemblyFullName`|<span data-ttu-id="72212-141">Opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="72212-141">Optional.</span></span> <span data-ttu-id="72212-142">Nazwa zestawu.</span><span class="sxs-lookup"><span data-stu-id="72212-142">An assembly name.</span></span> <span data-ttu-id="72212-143">Gdy odwołanie do tego zestawu zostanie dodany do projektu, użytkownik będzie monitu o dodanie `My` rozszerzenia na podstawie tego szablonu elementu.</span><span class="sxs-lookup"><span data-stu-id="72212-143">When a reference to this assembly is added to the project, the user will be prompted to add the `My` extension from this item template.</span></span>|  
  
### <a name="add-the-customdatasignature-element-to-the-vstemplate-file"></a><span data-ttu-id="72212-144">Dodaj \<customdatasignature — > w pliku .vstemplate — element</span><span class="sxs-lookup"><span data-stu-id="72212-144">Add the \<CustomDataSignature> element to the .vstemplate file</span></span>  
 <span data-ttu-id="72212-145">Aby zidentyfikować szablonu elementów programu Visual Studio jako `My` rozszerzenie przestrzeni nazw, należy również zmodyfikować plik .vstemplate szablonu elementu.</span><span class="sxs-lookup"><span data-stu-id="72212-145">To identify your Visual Studio item template as a `My` namespace extension, you must also modify the .vstemplate file for your item template.</span></span> <span data-ttu-id="72212-146">Należy dodać `<CustomDataSignature>` elementu `<TemplateData>` elementu.</span><span class="sxs-lookup"><span data-stu-id="72212-146">You must add a `<CustomDataSignature>` element to the `<TemplateData>` element.</span></span> <span data-ttu-id="72212-147">`<CustomDataSignature>` Element musi zawierać tekst `Microsoft.VisualBasic.MyExtension`, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="72212-147">The `<CustomDataSignature>` element must contain the text `Microsoft.VisualBasic.MyExtension`, as shown in the following example.</span></span>  
  
```xml  
<CustomDataSignature>Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
```  
  
 <span data-ttu-id="72212-148">Nie można bezpośrednio modyfikować pliki w skompresowanym folderze (pliku .zip).</span><span class="sxs-lookup"><span data-stu-id="72212-148">You cannot modify files in a compressed folder (.zip file) directly.</span></span> <span data-ttu-id="72212-149">Należy skopiować plik .vstemplate ze skompresowanego folderu, go zmodyfikować i następnie zastąpić plik .vstemplate ze skompresowanego folderu kopii zaktualizowane.</span><span class="sxs-lookup"><span data-stu-id="72212-149">You must copy the .vstemplate file from the compressed folder, modify it, and then replace the .vstemplate file in the compressed folder with your updated copy.</span></span>  
  
 <span data-ttu-id="72212-150">W poniższym przykładzie pokazano zawartość pliku .vstemplate, który ma `<CustomDataSignature>` elementu dodany.</span><span class="sxs-lookup"><span data-stu-id="72212-150">The following example shows the contents of a .vstemplate file that has the `<CustomDataSignature>` element added.</span></span>  
  
```xml  
<VSTemplate Version="2.0.0" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005" Type="Item">  
  <TemplateData>  
    <DefaultName>MyCustomExtensionModule.vb</DefaultName>  
    <Name>MyPrinterInfo</Name>  
    <Description>Custom My Extensions Item Template</Description>  
    <ProjectType>VisualBasic</ProjectType>  
    <SortOrder>10</SortOrder>  
    <Icon>__TemplateIcon.ico</Icon>  
    <CustomDataSignature      >Microsoft.VisualBasic.MyExtension</CustomDataSignature>  
  </TemplateData>  
  <TemplateContent>  
    <References />  
    <ProjectItem SubType="Code"   
                 TargetFileName="$fileinputname$.vb"  
                 ReplaceParameters="true"  
     >MyCustomExtensionModule.vb</ProjectItem>  
  </TemplateContent>  
</VSTemplate>  
```  
  
## <a name="install-the-template"></a><span data-ttu-id="72212-151">Zainstaluj szablonu</span><span class="sxs-lookup"><span data-stu-id="72212-151">Install the template</span></span>  
 <span data-ttu-id="72212-152">Aby zainstalować szablon, należy skopiować skompresowanym folderze (pliku .zip) w folderze Szablony elementów Visual Basic (na przykład Moje Documents\Visual Studio 2008\Templates\Item Templates\Visual podstawowe).</span><span class="sxs-lookup"><span data-stu-id="72212-152">To install the template, you can copy the compressed folder (.zip file) to the Visual Basic item templates folder (for example, My Documents\Visual Studio 2008\Templates\Item Templates\Visual Basic).</span></span> <span data-ttu-id="72212-153">Alternatywnie możesz opublikować szablon jako plik Instalator programu Visual Studio (.vsi).</span><span class="sxs-lookup"><span data-stu-id="72212-153">Alternatively, you can publish the template as a Visual Studio Installer (.vsi) file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72212-154">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72212-154">See also</span></span>  
 [<span data-ttu-id="72212-155">Rozszerzanie Moje Namespace w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72212-155">Extending the My Namespace in Visual Basic</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-my-namespace.md)  
 [<span data-ttu-id="72212-156">Rozszerzanie modelu aplikacji Visual Basic</span><span class="sxs-lookup"><span data-stu-id="72212-156">Extending the Visual Basic Application Model</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/extending-the-visual-basic-application-model.md)  
 [<span data-ttu-id="72212-157">Dostosowywanie, które obiekty są dostępne w mojej</span><span class="sxs-lookup"><span data-stu-id="72212-157">Customizing Which Objects are Available in My</span></span>](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)  
 [<span data-ttu-id="72212-158">Strona Moje rozszerzenia, Projektant projektu</span><span class="sxs-lookup"><span data-stu-id="72212-158">My Extensions Page, Project Designer</span></span>](/visualstudio/ide/reference/my-extensions-page-project-designer-visual-basic)