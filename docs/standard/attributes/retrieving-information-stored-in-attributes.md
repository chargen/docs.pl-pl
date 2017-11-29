---
title: Pobieranie informacji przechowywanych w atrybutach
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- retrieving attributes
- multiple attribute instances
- attributes [.NET Framework], retrieving
ms.assetid: 37dfe4e3-7da0-48b6-a3d9-398981524e1c
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 9d3fd9a5a49d65b37d2cdb5107e9c516a6df5847
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="retrieving-information-stored-in-attributes"></a><span data-ttu-id="68f45-102">Pobieranie informacji przechowywanych w atrybutach</span><span class="sxs-lookup"><span data-stu-id="68f45-102">Retrieving Information Stored in Attributes</span></span>
<span data-ttu-id="68f45-103">Podczas pobierania atrybutów niestandardowych jest prosty proces.</span><span class="sxs-lookup"><span data-stu-id="68f45-103">Retrieving a custom attribute is a simple process.</span></span> <span data-ttu-id="68f45-104">Po pierwsze Zadeklaruj wystąpienie atrybutu, który ma zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="68f45-104">First, declare an instance of the attribute you want to retrieve.</span></span> <span data-ttu-id="68f45-105">Następnie należy użyć <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> metodę, aby zainicjować nowy atrybut na wartość atrybutu do pobrania.</span><span class="sxs-lookup"><span data-stu-id="68f45-105">Then, use the <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType> method to initialize the new attribute to the value of the attribute you want to retrieve.</span></span> <span data-ttu-id="68f45-106">Po zainicjowaniu nowy atrybut po prostu użyć jego właściwości w celu uzyskania wartości.</span><span class="sxs-lookup"><span data-stu-id="68f45-106">Once the new attribute is initialized, you simply use its properties to get the values.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="68f45-107">W tym temacie opisano, jak pobrać atrybutów dla kodu ładowane do kontekstu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="68f45-107">This topic describes how to retrieve attributes for code loaded into the execution context.</span></span> <span data-ttu-id="68f45-108">Aby pobrać atrybutów dla kodu ładowane do kontekstu reflection-only, należy użyć <xref:System.Reflection.CustomAttributeData> klasy, jak pokazano w [porady: zestawy obciążenia w kontekście Reflection-Only](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span><span class="sxs-lookup"><span data-stu-id="68f45-108">To retrieve attributes for code loaded into the reflection-only context, you must use the <xref:System.Reflection.CustomAttributeData> class, as shown in [How to: Load Assemblies into the Reflection-Only Context](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).</span></span>  
  
 <span data-ttu-id="68f45-109">W tej sekcji opisano sposoby można pobrać atrybutów:</span><span class="sxs-lookup"><span data-stu-id="68f45-109">This section describes the following ways to retrieve attributes:</span></span>  
  
-   [<span data-ttu-id="68f45-110">Trwa pobieranie jedno wystąpienie atrybutu</span><span class="sxs-lookup"><span data-stu-id="68f45-110">Retrieving a single instance of an attribute</span></span>](#cpconretrievingsingleinstanceofattribute)  
  
-   [<span data-ttu-id="68f45-111">Pobieranie wielu wystąpień atrybut zastosowany do tego samego zakresu</span><span class="sxs-lookup"><span data-stu-id="68f45-111">Retrieving multiple instances of an attribute applied to the same scope</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtosamescope)  
  
-   [<span data-ttu-id="68f45-112">Pobieranie wielu wystąpień atrybutem stosowanym do różnych zakresów</span><span class="sxs-lookup"><span data-stu-id="68f45-112">Retrieving multiple instances of an attribute applied to different scopes</span></span>](#cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes)  
  
<a name="cpconretrievingsingleinstanceofattribute"></a>   
## <a name="retrieving-a-single-instance-of-an-attribute"></a><span data-ttu-id="68f45-113">Trwa pobieranie jedno wystąpienie atrybutu</span><span class="sxs-lookup"><span data-stu-id="68f45-113">Retrieving a Single Instance of an Attribute</span></span>  
 <span data-ttu-id="68f45-114">W poniższym przykładzie `DeveloperAttribute` (opisane w poprzedniej sekcji) jest stosowana do `MainApp` klasy na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="68f45-114">In the following example, the `DeveloperAttribute` (described in the previous section) is applied to the `MainApp` class on the class level.</span></span> <span data-ttu-id="68f45-115">`GetAttribute` Używa metody **metody GetCustomAttribute** można pobrać wartości przechowywane w `DeveloperAttribute` na poziomie klasy przed ich wyświetlania w konsoli.</span><span class="sxs-lookup"><span data-stu-id="68f45-115">The `GetAttribute` method uses **GetCustomAttribute** to retrieve the values stored in `DeveloperAttribute` on the class level before displaying them to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#18](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#18)]
 [!code-csharp[Conceptual.Attributes.Usage#18](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#18)]
 [!code-vb[Conceptual.Attributes.Usage#18](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#18)]  
  
 <span data-ttu-id="68f45-116">Ten program wyświetla następujący tekst podczas wykonywania.</span><span class="sxs-lookup"><span data-stu-id="68f45-116">This program displays the following text when executed.</span></span>  
  
```  
The Name Attribute is: Joan Smith.  
The Level Attribute is: 42.  
The Reviewed Attribute is: True.  
```  
  
 <span data-ttu-id="68f45-117">Jeśli ten atrybut nie zostanie znaleziony, **metody GetCustomAttribute** inicjuje metody `MyAttribute` ma wartość null.</span><span class="sxs-lookup"><span data-stu-id="68f45-117">If the attribute is not found, the **GetCustomAttribute** method initializes `MyAttribute` to a null value.</span></span> <span data-ttu-id="68f45-118">W tym przykładzie sprawdza `MyAttribute` dla wystąpienia obiektu i powiadamia użytkownika, jeśli nie jest odnaleźć atrybutu.</span><span class="sxs-lookup"><span data-stu-id="68f45-118">This example checks `MyAttribute` for such an instance and notifies the user if no attribute is found.</span></span> <span data-ttu-id="68f45-119">Jeśli `DeveloperAttribute` nie została odnaleziona w zakresie klasy następujący komunikat wyświetlany w konsoli.</span><span class="sxs-lookup"><span data-stu-id="68f45-119">If the `DeveloperAttribute` is not found in the class scope, the following message displays to the console.</span></span>  
  
```  
The attribute was not found.   
```  
  
 <span data-ttu-id="68f45-120">W przykładzie założono, że definicja atrybutu znajduje się w bieżącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="68f45-120">This example assumes that the attribute definition is in the current namespace.</span></span> <span data-ttu-id="68f45-121">Pamiętaj, aby zaimportować przestrzeni nazw, w której znajduje się definicja atrybutu, jeśli nie znajduje się w bieżącej przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="68f45-121">Remember to import the namespace in which the attribute definition resides if it is not in the current namespace.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtosamescope"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-the-same-scope"></a><span data-ttu-id="68f45-122">Pobieranie wielu wystąpień atrybut zastosowany do tego samego zakresu</span><span class="sxs-lookup"><span data-stu-id="68f45-122">Retrieving Multiple Instances of an Attribute Applied to the Same Scope</span></span>  
 <span data-ttu-id="68f45-123">W poprzednim przykładzie klasa do zbadania i określony atrybut można znaleźć są przekazywane do <xref:System.Attribute.GetCustomAttribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="68f45-123">In the previous example, the class to inspect and the specific attribute to find are passed to <xref:System.Attribute.GetCustomAttribute%2A>.</span></span> <span data-ttu-id="68f45-124">Ten kod działa także jeśli tylko jedno wystąpienie atrybutu jest stosowana na poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="68f45-124">That code works well if only one instance of an attribute is applied on the class level.</span></span> <span data-ttu-id="68f45-125">Jednak jeśli wiele wystąpień atrybutu są stosowane na tym samym poziomie klasy **metody GetCustomAttribute** — metoda nie pobiera wszystkie informacje.</span><span class="sxs-lookup"><span data-stu-id="68f45-125">However, if multiple instances of an attribute are applied on the same class level, the **GetCustomAttribute** method does not retrieve all the information.</span></span> <span data-ttu-id="68f45-126">W przypadkach, gdy wiele wystąpień tego samego atrybutu są stosowane do tego samego zakresu, można użyć <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> można umieścić wszystkie wystąpienia atrybutu do tablicy.</span><span class="sxs-lookup"><span data-stu-id="68f45-126">In cases where multiple instances of the same attribute are applied to the same scope, you can use <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType> to place all instances of an attribute into an array.</span></span> <span data-ttu-id="68f45-127">Na przykład, jeśli dwa wystąpienia `DeveloperAttribute` są stosowane na poziomie klasy w tej samej klasy `GetAttribute` metody można zmodyfikować, aby wyświetlić informacje znajdujące się w obu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="68f45-127">For example, if two instances of `DeveloperAttribute` are applied on the class level of the same class, the `GetAttribute` method can be modified to display the information found in both attributes.</span></span> <span data-ttu-id="68f45-128">Pamiętaj, aby zastosować wielu atrybutów na tym samym poziomie atrybutu musi być zdefiniowana z **AllowMultiple** ustawioną właściwość **true** w <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="68f45-128">Remember, to apply multiple attributes on the same level, the attribute must be defined with the **AllowMultiple** property set to **true** in the <xref:System.AttributeUsageAttribute>.</span></span>  
  
 <span data-ttu-id="68f45-129">Poniższy przykładowy kod przedstawia sposób użycia **GetCustomAttributes** metodę w celu utworzenia tablicę, która odwołuje się do wszystkich wystąpień `DeveloperAttribute` w dowolnej podanej klasy.</span><span class="sxs-lookup"><span data-stu-id="68f45-129">The following code example shows how to use the **GetCustomAttributes** method to create an array that references all instances of `DeveloperAttribute` in any given class.</span></span> <span data-ttu-id="68f45-130">Wartości wszystkich atrybutów są następnie wyświetlane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="68f45-130">The values of all attributes are then displayed to the console.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#19](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#19)]
 [!code-csharp[Conceptual.Attributes.Usage#19](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#19)]
 [!code-vb[Conceptual.Attributes.Usage#19](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#19)]  
  
 <span data-ttu-id="68f45-131">Jeśli nie zostaną znalezione żadne atrybuty, ten kod ostrzega o tym użytkownika.</span><span class="sxs-lookup"><span data-stu-id="68f45-131">If no attributes are found, this code alerts the user.</span></span> <span data-ttu-id="68f45-132">W przeciwnym razie informacje zawarte w obu wystąpień `DeveloperAttribute` jest wyświetlany.</span><span class="sxs-lookup"><span data-stu-id="68f45-132">Otherwise, the information contained in both instances of `DeveloperAttribute` is displayed.</span></span>  
  
<a name="cpconretrievingmultipleinstancesofattributeappliedtodifferentscopes"></a>   
## <a name="retrieving-multiple-instances-of-an-attribute-applied-to-different-scopes"></a><span data-ttu-id="68f45-133">Pobieranie wielu wystąpień atrybutem stosowanym do różnych zakresów</span><span class="sxs-lookup"><span data-stu-id="68f45-133">Retrieving Multiple Instances of an Attribute Applied to Different Scopes</span></span>  
 <span data-ttu-id="68f45-134"><xref:System.Attribute.GetCustomAttributes%2A> i <xref:System.Attribute.GetCustomAttribute%2A> metody wyszukiwania całej klasy i nie zwraca wszystkie wystąpienia atrybutów w tej klasy.</span><span class="sxs-lookup"><span data-stu-id="68f45-134">The <xref:System.Attribute.GetCustomAttributes%2A> and <xref:System.Attribute.GetCustomAttribute%2A> methods do not search an entire class and return all instances of an attribute in that class.</span></span> <span data-ttu-id="68f45-135">Zamiast wyszukiwania tylko jeden określonej metody lub członka naraz.</span><span class="sxs-lookup"><span data-stu-id="68f45-135">Rather, they search only one specified method or member at a time.</span></span> <span data-ttu-id="68f45-136">Jeśli masz klasy z tego samego atrybutu zastosowane do każdego elementu członkowskiego i chcesz pobrać wartości na wszystkie atrybuty, które są stosowane do tych członków, należy podać co metody lub członka indywidualnie do **GetCustomAttributes** i  **Metody GetCustomAttribute**.</span><span class="sxs-lookup"><span data-stu-id="68f45-136">If you have a class with the same attribute applied to every member and you want to retrieve the values in all the attributes applied to those members, you must supply every method or member individually to **GetCustomAttributes** and **GetCustomAttribute**.</span></span>  
  
 <span data-ttu-id="68f45-137">Poniższy przykład kodu klasy jako parametr przyjmuje i wyszukuje `DeveloperAttribute` (zdefiniowanych wcześniej) na poziomie klasy i co poszczególne metody tej klasy.</span><span class="sxs-lookup"><span data-stu-id="68f45-137">The following code example takes a class as a parameter and searches for the `DeveloperAttribute` (defined previously) on the class level and on every individual method of that class.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#20](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source3.cpp#20)]
 [!code-csharp[Conceptual.Attributes.Usage#20](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source3.cs#20)]
 [!code-vb[Conceptual.Attributes.Usage#20](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source3.vb#20)]  
  
 <span data-ttu-id="68f45-138">Jeśli nie wystąpienia `DeveloperAttribute` znajdują się na poziomie metody lub klasa, `GetAttribute` metoda powiadamia użytkownika, którego nie znaleziono żadnych atrybutów i wyświetla nazwę metody lub klasa, która nie zawiera atrybutu.</span><span class="sxs-lookup"><span data-stu-id="68f45-138">If no instances of the `DeveloperAttribute` are found on the method level or class level, the `GetAttribute` method notifies the user that no attributes were found and displays the name of the method or class that does not contain the attribute.</span></span> <span data-ttu-id="68f45-139">Jeśli atrybut zostanie znaleziony, `Name`, `Level`, i `Reviewed` pola są wyświetlane w konsoli.</span><span class="sxs-lookup"><span data-stu-id="68f45-139">If an attribute is found, the `Name`, `Level`, and `Reviewed` fields are displayed to the console.</span></span>  
  
 <span data-ttu-id="68f45-140">Korzystając z członkami <xref:System.Type> klasy można pobrać poszczególnych metod i elementów członkowskich w klasie przekazany.</span><span class="sxs-lookup"><span data-stu-id="68f45-140">You can use the members of the <xref:System.Type> class to get the individual methods and members in the passed class.</span></span> <span data-ttu-id="68f45-141">W tym przykładzie najpierw wysyła zapytanie **typu** obiektu, aby uzyskać informacje o atrybutach dotyczące poziomie klasy.</span><span class="sxs-lookup"><span data-stu-id="68f45-141">This example first queries the **Type** object to get attribute information for the class level.</span></span> <span data-ttu-id="68f45-142">Następnie używa <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> umieścić wystąpień wszystkich metod do tablicy <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> obiektów można pobrać informacji o atrybut na poziomie metody.</span><span class="sxs-lookup"><span data-stu-id="68f45-142">Next, it uses <xref:System.Type.GetMethods%2A?displayProperty=nameWithType> to place instances of all methods into an array of <xref:System.Reflection.MemberInfo?displayProperty=nameWithType> objects to retrieve attribute information for the method level.</span></span> <span data-ttu-id="68f45-143">Można również użyć <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> metodę sprawdzania, czy atrybuty na poziomie właściwości lub <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> do sprawdzenia atrybuty na poziomie konstruktora.</span><span class="sxs-lookup"><span data-stu-id="68f45-143">You can also use the <xref:System.Type.GetProperties%2A?displayProperty=nameWithType> method to check for attributes on the property level or <xref:System.Type.GetConstructors%2A?displayProperty=nameWithType> to check for attributes on the constructor level.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68f45-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68f45-144">See Also</span></span>  
 <xref:System.Type?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttribute%2A?displayProperty=nameWithType>  
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="68f45-145">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="68f45-145">Attributes</span></span>](../../../docs/standard/attributes/index.md)