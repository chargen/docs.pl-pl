---
title: "Typy wyliczeniowe (C# przewodnik programowania w języku)"
ms.date: 09/10/2017
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- enumerations [C#]
- enums [C#]
- C# Language, enums
- bit flags [C#]
ms.assetid: 64a9b731-9e3c-4336-8a09-018db2aa10b7
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 13ec7d5d2a44cddb2b7f440c8d811c2e4060d432
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="enumeration-types-c-programming-guide"></a><span data-ttu-id="b43e6-102">Typy wyliczeniowe (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="b43e6-102">Enumeration types (C# Programming Guide)</span></span>

<span data-ttu-id="b43e6-103">Typ wyliczenia (nazywana również wyliczenie lub wyliczenia) umożliwia wydajne do zdefiniowania zestawu o nazwie stałe całkowite, przypisane do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b43e6-103">An enumeration type (also named an enumeration or an enum) provides an efficient way to define a set of named integral constants that may be assigned to a variable.</span></span> <span data-ttu-id="b43e6-104">Na przykład załóżmy, że trzeba zdefiniować zmienną, której wartość reprezentuje dzień tygodnia.</span><span class="sxs-lookup"><span data-stu-id="b43e6-104">For example, assume that you have to define a variable whose value will represent a day of the week.</span></span> <span data-ttu-id="b43e6-105">Istnieje tylko siedem istotnych wartości, które kiedykolwiek zapisze tej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="b43e6-105">There are only seven meaningful values which that variable will ever store.</span></span> <span data-ttu-id="b43e6-106">Aby zdefiniować te wartości, można użyć typem wyliczenia, który został zadeklarowany za pomocą [wyliczenia](../../csharp/language-reference/keywords/enum.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="b43e6-106">To define those values, you can use an enumeration type, which is declared by using the [enum](../../csharp/language-reference/keywords/enum.md) keyword.</span></span>

[!code-csharp[csProgGuideEnums#1](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#1)]

<span data-ttu-id="b43e6-107">Domyślnie jest typu bazowego dla każdego elementu w elemencie enum [int](../../csharp/language-reference/keywords/int.md). Można określić inny typ liczbowy integralną przy użyciu dwukropek, jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b43e6-107">By default the underlying type of each element in the enum is [int](../../csharp/language-reference/keywords/int.md). You can specify another integral numeric type by using a colon, as shown in the previous example.</span></span> <span data-ttu-id="b43e6-108">Aby uzyskać pełną listę możliwych typów, zobacz [enum (odwołanie w C#)](../../csharp/language-reference/keywords/enum.md).</span><span class="sxs-lookup"><span data-stu-id="b43e6-108">For a full list of possible types, see [enum (C# Reference)](../../csharp/language-reference/keywords/enum.md).</span></span>

<span data-ttu-id="b43e6-109">Możesz sprawdzić podstawowej wartości liczbowych przez rzutowanie na typ podstawowy, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="b43e6-109">You can verify the underlying numeric values by casting  to the underlying type, as the following example shows.</span></span>

```csharp
Day today = Day.Monday;
int dayNumber =(int)today;
Console.WriteLine("{0} is day number #{1}.", today, dayNumber);

Month thisMonth = Month.Dec;
byte monthNumber = (byte)thisMonth;
Console.WriteLine("{0} is month number #{1}.", thisMonth, monthNumber);

// Output:
// Monday is day number #1.
// Dec is month number #11.
```

<span data-ttu-id="b43e6-110">Zalety korzystania z wyliczeniem zamiast typu liczbowego są następujące:</span><span class="sxs-lookup"><span data-stu-id="b43e6-110">The following are advantages of using an enum instead of a numeric type:</span></span>

- <span data-ttu-id="b43e6-111">Wyraźnie określ wartości, które są prawidłowe dla zmiennej kodu klienta.</span><span class="sxs-lookup"><span data-stu-id="b43e6-111">You clearly specify for client code which values are valid for the variable.</span></span>

- <span data-ttu-id="b43e6-112">W [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], IntelliSense wyświetla zdefiniowanymi wartościami.</span><span class="sxs-lookup"><span data-stu-id="b43e6-112">In [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], IntelliSense lists the defined values.</span></span>

<span data-ttu-id="b43e6-113">Jeśli nie określisz wartości elementów na liście modułu wyliczającego, wartości są automatycznie zwiększana o 1.</span><span class="sxs-lookup"><span data-stu-id="b43e6-113">When you do not specify values for the elements in the enumerator list, the values are automatically incremented by 1.</span></span> <span data-ttu-id="b43e6-114">W poprzednim przykładzie `Day.Sunday` ma wartość 0, `Day.Monday` ma wartość 1 i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="b43e6-114">In the previous example, `Day.Sunday` has a value of 0, `Day.Monday` has a value of 1, and so on.</span></span> <span data-ttu-id="b43e6-115">Podczas tworzenia nowego `Day` obiektu, będzie mieć wartość domyślną równą `Day.Sunday` (0), jeśli nie zostanie jawnie przypisany jej wartość.</span><span class="sxs-lookup"><span data-stu-id="b43e6-115">When you create a new `Day` object, it will have a default value of `Day.Sunday` (0) if you do not explicitly assign it a value.</span></span> <span data-ttu-id="b43e6-116">Podczas tworzenia wyliczenia wybierz najbardziej logicznym wartość domyślną i nadaj mu wartość zero.</span><span class="sxs-lookup"><span data-stu-id="b43e6-116">When you create an enum, select the most logical default value and give it a value of zero.</span></span> <span data-ttu-id="b43e6-117">Który spowoduje, że wszystkie typy wyliczeniowe za tę wartość domyślną, jeśli nie są one jawnie przypisywane wartość po ich utworzeniu.</span><span class="sxs-lookup"><span data-stu-id="b43e6-117">That will cause all enums to have that default value if they are not explicitly assigned a value when they are created.</span></span>

<span data-ttu-id="b43e6-118">Jeśli zmienna `meetingDay` jest typu `Day`, a następnie (bez jawnego rzutowania) można przypisać tylko ona jedną z wartości zdefiniowanych przez `Day`.</span><span class="sxs-lookup"><span data-stu-id="b43e6-118">If the variable `meetingDay` is of type `Day`, then (without an explicit cast) you can only assign it one of the values defined by `Day`.</span></span> <span data-ttu-id="b43e6-119">I zmiana dzień spotkania można przypisać nowe wartości z `Day` do `meetingDay`:</span><span class="sxs-lookup"><span data-stu-id="b43e6-119">And if the meeting day changes, you can assign a new value from `Day` to `meetingDay`:</span></span>

[!code-csharp[csProgGuideEnums#4](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#4)]

> [!NOTE]
> <span data-ttu-id="b43e6-120">Można przypisać dowolną wartość całkowitą dowolnego do `meetingDay`.</span><span class="sxs-lookup"><span data-stu-id="b43e6-120">It's possible to assign any arbitrary integer value to `meetingDay`.</span></span> <span data-ttu-id="b43e6-121">Na przykład ten wiersz kodu nie generuje błąd: `meetingDay = (Day) 42`.</span><span class="sxs-lookup"><span data-stu-id="b43e6-121">For example, this line of code does not produce an error: `meetingDay = (Day) 42`.</span></span> <span data-ttu-id="b43e6-122">Jednak użytkownik nie należy tego robić ponieważ niejawne oczekuje się, że zmiennej wyliczenia będzie zawierać tylko jedną z wartości zdefiniowanych przez wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="b43e6-122">However, you should not do this because the implicit expectation is that an enum variable will only hold one of the values defined by the enum.</span></span> <span data-ttu-id="b43e6-123">Aby przypisać dowolną wartość do zmiennej typu wyliczenia jest wprowadzenie duże ryzyko błędów.</span><span class="sxs-lookup"><span data-stu-id="b43e6-123">To assign an arbitrary value to a variable of an enumeration type is to introduce a high risk for errors.</span></span>

<span data-ttu-id="b43e6-124">Można przypisać wartości do elementów na liście modułu wyliczającego dla typu wyliczeniowego, a także można użyć obliczanej wartości:</span><span class="sxs-lookup"><span data-stu-id="b43e6-124">You can assign any values to the elements in the enumerator list of an enumeration type, and you can also use computed values:</span></span>

[!code-csharp[csProgGuideEnums#3](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#3)]

## <a name="enumeration-types-as-bit-flags"></a><span data-ttu-id="b43e6-125">Typy wyliczeniowe jako flagi bitów</span><span class="sxs-lookup"><span data-stu-id="b43e6-125">Enumeration types as bit flags</span></span>

<span data-ttu-id="b43e6-126">Typem wyliczenia można użyć do definiowania flagi bitów, co włącza wystąpienie typu wyliczenia w celu przechowywania dowolnej kombinacji wartości, które są zdefiniowane na liście modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="b43e6-126">You can use an enumeration type to define bit flags, which enables an instance of the enumeration type to store any combination of the values that are defined in the enumerator list.</span></span> <span data-ttu-id="b43e6-127">(Oczywiście niektórych kombinacji nie może być przydatne lub dozwolonych w kodzie programu.)</span><span class="sxs-lookup"><span data-stu-id="b43e6-127">(Of course, some combinations may not be meaningful or allowed in your program code.)</span></span>

<span data-ttu-id="b43e6-128">Utwórz nieco wyliczenia flag, stosując <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybut i odpowiednio definiowanie wartości, aby `AND`, `OR`, `NOT` i `XOR` Operacje bitowe mogą być wykonywane na nich.</span><span class="sxs-lookup"><span data-stu-id="b43e6-128">You create a bit flags enum by applying the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute and defining the values appropriately so that `AND`, `OR`, `NOT` and `XOR` bitwise operations can be performed on them.</span></span> <span data-ttu-id="b43e6-129">W nieco wyliczenia flag obejmują nazwanej stałej o wartości zero oznacza "nie flagi są ustawione."</span><span class="sxs-lookup"><span data-stu-id="b43e6-129">In a bit flags enum, include a named constant with a value of zero that means "no flags are set."</span></span> <span data-ttu-id="b43e6-130">Nie ma flagi wartość równą zero, jeśli nie oznacza to "nie flagi są ustawiane".</span><span class="sxs-lookup"><span data-stu-id="b43e6-130">Do not give a flag a value of zero if it does not mean "no flags are set".</span></span>

<span data-ttu-id="b43e6-131">W poniższym przykładzie inna wersja `Day` wyliczenia, które nosi nazwę `Days`, jest zdefiniowany.</span><span class="sxs-lookup"><span data-stu-id="b43e6-131">In the following example, another version of the `Day` enum, which is named `Days`, is defined.</span></span> <span data-ttu-id="b43e6-132">`Days`ma `Flags` atrybutów i wartości jest przypisany następny większy potęgą liczby 2.</span><span class="sxs-lookup"><span data-stu-id="b43e6-132">`Days` has the `Flags` attribute, and each value is assigned the next greater power of 2.</span></span> <span data-ttu-id="b43e6-133">Dzięki temu można utworzyć `Days` zmiennej, którego wartość jest `Days.Tuesday | Days.Thursday`.</span><span class="sxs-lookup"><span data-stu-id="b43e6-133">This enables you to create a `Days` variable whose value is `Days.Tuesday | Days.Thursday`.</span></span>

[!code-csharp[csProgGuideEnums#2](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#2)]

<span data-ttu-id="b43e6-134">Aby ustawić flagę w wyliczeniu, użyj operatora testu koniunkcji `OR` operatora, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b43e6-134">To set a flag on an enum, use the bitwise `OR` operator as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#6](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#6)]

<span data-ttu-id="b43e6-135">Aby określić, czy ustawiono flagę określonych, użyj bitowej `AND` operacji, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b43e6-135">To determine whether a specific flag is set, use a bitwise `AND` operation, as shown in the following example:</span></span>

[!code-csharp[csProgGuideEnums#7](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#7)]

<span data-ttu-id="b43e6-136">Aby uzyskać więcej informacji o tym, co należy wziąć pod uwagę podczas definiowania Typy wyliczeniowe z <xref:System.FlagsAttribute?displayProperty=nameWithType> atrybutów, zobacz <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b43e6-136">For more information about what to consider when you define enumeration types with the <xref:System.FlagsAttribute?displayProperty=nameWithType> attribute, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

## <a name="using-the-systemenum-methods-to-discover-and-manipulate-enum-values"></a><span data-ttu-id="b43e6-137">Przy użyciu metod element System.Enum do odnajdywania i manipulowania wartości wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b43e6-137">Using the System.Enum methods to discover and manipulate enum values</span></span>

<span data-ttu-id="b43e6-138">Wszystkie typy wyliczeniowe są wystąpieniami klasy <xref:System.Enum?displayProperty=nameWithType> typu.</span><span class="sxs-lookup"><span data-stu-id="b43e6-138">All enums are instances of the <xref:System.Enum?displayProperty=nameWithType> type.</span></span> <span data-ttu-id="b43e6-139">Nie może wyprowadzać nowe klasy z <xref:System.Enum?displayProperty=nameWithType>, ale jego metody umożliwia odnajdywanie informacji o i manipulowania wartości w określonym wystąpieniu wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b43e6-139">You cannot derive new classes from <xref:System.Enum?displayProperty=nameWithType>, but you can use its methods to discover information about and manipulate values in an enum instance.</span></span>

[!code-csharp[csProgGuideEnums#5](../../../samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideEnums/CS/Enums.cs#5)]

<span data-ttu-id="b43e6-140">Aby uzyskać więcej informacji, zobacz <xref:System.Enum?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="b43e6-140">For more information, see <xref:System.Enum?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="b43e6-141">Można również utworzenie nowej metody dla wyliczenia za pomocą metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="b43e6-141">You can also create a new method for an enum by using an extension method.</span></span> <span data-ttu-id="b43e6-142">Aby uzyskać więcej informacji, zobacz [porady: utworzenie nowej metody wyliczania](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="b43e6-142">For more information, see [How to: Create a New Method for an Enumeration](../../csharp/programming-guide/classes-and-structs/how-to-create-a-new-method-for-an-enumeration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b43e6-143">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b43e6-143">See also</span></span>
 <xref:System.Enum?displayProperty=nameWithType>  
 [<span data-ttu-id="b43e6-144">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b43e6-144">C# Programming Guide</span></span>](../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b43e6-145">wyliczenia</span><span class="sxs-lookup"><span data-stu-id="b43e6-145">enum</span></span>](../../csharp/language-reference/keywords/enum.md)