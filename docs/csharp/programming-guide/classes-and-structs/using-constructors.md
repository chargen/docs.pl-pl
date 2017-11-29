---
title: "Używanie konstruktorów (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: constructors [C#], about constructors
ms.assetid: 464253b2-fd5d-469a-836d-df0fdf2a43f7
caps.latest.revision: "26"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: eb9fcd1e4090da300de17c7fd808669ba51767c6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-constructors-c-programming-guide"></a><span data-ttu-id="21052-102">Używanie konstruktorów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="21052-102">Using Constructors (C# Programming Guide)</span></span>
<span data-ttu-id="21052-103">Gdy [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md) jest utworzona, jest nazywany jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="21052-103">When a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md) is created, its constructor is called.</span></span> <span data-ttu-id="21052-104">Konstruktory ma taką samą nazwę jak klasy lub struktury i zwykle inicjowania elementów członkowskich danych nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="21052-104">Constructors have the same name as the class or struct, and they usually initialize the data members of the new object.</span></span>  
  
 <span data-ttu-id="21052-105">W poniższym przykładzie klasa o nazwie `Taxi` jest definiowana za pomocą prostego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="21052-105">In the following example, a class named `Taxi` is defined by using a simple constructor.</span></span> <span data-ttu-id="21052-106">Ta klasa jest następnie utworzono wystąpienie [nowe](../../../csharp/language-reference/keywords/new.md) operatora.</span><span class="sxs-lookup"><span data-stu-id="21052-106">This class is then instantiated with the [new](../../../csharp/language-reference/keywords/new.md) operator.</span></span> <span data-ttu-id="21052-107">`Taxi` Konstruktor jest wywoływany przez `new` operator natychmiast po pamięci zarezerwowanej dla nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="21052-107">The `Taxi` constructor is invoked by the `new` operator immediately after memory is allocated for the new object.</span></span>  
  
 [!code-csharp[csProgGuideObjects#53](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_1.cs)]  
  
 <span data-ttu-id="21052-108">Konstruktor, który nie przyjmuje żadnych parametrów jest nazywany *domyślnego konstruktora*.</span><span class="sxs-lookup"><span data-stu-id="21052-108">A constructor that takes no parameters is called a *default constructor*.</span></span> <span data-ttu-id="21052-109">Konstruktory domyślne są wywoływane zawsze, gdy obiekt zostanie uruchomiony przy użyciu `new` operatora i argumenty nie są dostarczane do `new`.</span><span class="sxs-lookup"><span data-stu-id="21052-109">Default constructors are invoked whenever an object is instantiated by using the `new` operator and no arguments are provided to `new`.</span></span> <span data-ttu-id="21052-110">Aby uzyskać więcej informacji, zobacz [konstruktorów wystąpienia](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="21052-110">For more information, see [Instance Constructors](../../../csharp/programming-guide/classes-and-structs/instance-constructors.md).</span></span>  
  
 <span data-ttu-id="21052-111">Jeśli klasa jest [statycznych](../../../csharp/language-reference/keywords/static.md), klasy bez konstruktorów podano publicznego konstruktora domyślnego za pomocą kompilatora C# umożliwiające tworzenie wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="21052-111">Unless the class is [static](../../../csharp/language-reference/keywords/static.md), classes without constructors are given a public default constructor by the C# compiler in order to enable class instantiation.</span></span> <span data-ttu-id="21052-112">Aby uzyskać więcej informacji, zobacz [klasy statyczne i statycznych elementów członkowskich klasy](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span><span class="sxs-lookup"><span data-stu-id="21052-112">For more information, see [Static Classes and Static Class Members](../../../csharp/programming-guide/classes-and-structs/static-classes-and-static-class-members.md).</span></span>  
  
 <span data-ttu-id="21052-113">Klasę można zapobiec uruchamianiu przez Konstruktor prywatny, w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="21052-113">You can prevent a class from being instantiated by making the constructor private, as follows:</span></span>  
  
 [!code-csharp[csProgGuideObjects#11](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_2.cs)]  
  
 <span data-ttu-id="21052-114">Aby uzyskać więcej informacji, zobacz [konstruktory prywatne](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="21052-114">For more information, see [Private Constructors](../../../csharp/programming-guide/classes-and-structs/private-constructors.md).</span></span>  
  
 <span data-ttu-id="21052-115">Konstruktory [struktury](../../../csharp/language-reference/keywords/struct.md) typy przypominać konstruktorów klasy, ale `structs` nie mogą zawierać jawny Konstruktor domyślny, ponieważ zostało ono określone automatycznie przez kompilator.</span><span class="sxs-lookup"><span data-stu-id="21052-115">Constructors for [struct](../../../csharp/language-reference/keywords/struct.md) types resemble class constructors, but `structs` cannot contain an explicit default constructor because one is provided automatically by the compiler.</span></span> <span data-ttu-id="21052-116">Ten konstruktor inicjuje wszystkie pola w `struct` do wartości domyślnych.</span><span class="sxs-lookup"><span data-stu-id="21052-116">This constructor initializes each field in the `struct` to the default values.</span></span> <span data-ttu-id="21052-117">Aby uzyskać więcej informacji, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).</span><span class="sxs-lookup"><span data-stu-id="21052-117">For more information, see [Default Values Table](../../../csharp/language-reference/keywords/default-values-table.md).</span></span> <span data-ttu-id="21052-118">Jednak ten konstruktor domyślny jest wywoływana tylko jeśli `struct` zostanie uruchomiony z `new`.</span><span class="sxs-lookup"><span data-stu-id="21052-118">However, this default constructor is only invoked if the `struct` is instantiated with `new`.</span></span> <span data-ttu-id="21052-119">Na przykład ten kod używa domyślnego konstruktora dla <xref:System.Int32>, dzięki czemu zapewni zainicjowanej liczbę całkowitą:</span><span class="sxs-lookup"><span data-stu-id="21052-119">For example, this code uses the default constructor for <xref:System.Int32>, so that you are assured that the integer is initialized:</span></span>  
  
```  
int i = new int();  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="21052-120">Następujący kod, jednak powoduje błąd kompilatora, ponieważ nie używa `new`, ponieważ klient próbuje użyć obiektu, który nie został zainicjowany:</span><span class="sxs-lookup"><span data-stu-id="21052-120">The following code, however, causes a compiler error because it does not use `new`, and because it tries to use an object that has not been initialized:</span></span>  
  
```  
int i;  
Console.WriteLine(i);  
```  
  
 <span data-ttu-id="21052-121">Możesz też na podstawie obiektów `structs` (w tym wszystkie wbudowane typy liczbowe) można zainicjować lub przypisać i następnie używany jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="21052-121">Alternatively, objects based on `structs` (including all built-in numeric types) can be initialized or assigned and then used as in the following example:</span></span>  
  
```  
int a = 44;  // Initialize the value type...  
int b;  
b = 33;      // Or assign it before using it.  
Console.WriteLine("{0}, {1}", a, b);  
```  
  
 <span data-ttu-id="21052-122">Dlatego wywołanie domyślnego konstruktora dla typu wartości nie jest wymagane.</span><span class="sxs-lookup"><span data-stu-id="21052-122">So calling the default constructor for a value type is not required.</span></span>  
  
 <span data-ttu-id="21052-123">Obie klasy i `structs` można definiować konstruktorów przyjmujących parametrów.</span><span class="sxs-lookup"><span data-stu-id="21052-123">Both classes and `structs` can define constructors that take parameters.</span></span> <span data-ttu-id="21052-124">Konstruktorów przyjmujących parametrów musi zostać wywołana za pomocą `new` instrukcji lub [podstawowej](../../../csharp/language-reference/keywords/base.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="21052-124">Constructors that take parameters must be called through a `new` statement or a [base](../../../csharp/language-reference/keywords/base.md) statement.</span></span> <span data-ttu-id="21052-125">Klasy i `structs` można również zdefiniować wiele konstruktorów i nie będzie konieczne zdefiniowanie konstruktora domyślnego.</span><span class="sxs-lookup"><span data-stu-id="21052-125">Classes and `structs` can also define multiple constructors, and neither is required to define a default constructor.</span></span> <span data-ttu-id="21052-126">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="21052-126">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#54](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_3.cs)]  
  
 <span data-ttu-id="21052-127">Ta klasa można utworzyć przy użyciu jednej z następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="21052-127">This class can be created by using either of the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#55](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_4.cs)]  
  
 <span data-ttu-id="21052-128">Można użyć konstruktora `base` — słowo kluczowe można wywołać konstruktora klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="21052-128">A constructor can use the `base` keyword to call the constructor of a base class.</span></span> <span data-ttu-id="21052-129">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="21052-129">For example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#56](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_5.cs)]  
  
 <span data-ttu-id="21052-130">W tym przykładzie konstruktora dla klasy podstawowej jest wywoływana przed wykonaniem dla konstruktora bloku.</span><span class="sxs-lookup"><span data-stu-id="21052-130">In this example, the constructor for the base class is called before the block for the constructor is executed.</span></span> <span data-ttu-id="21052-131">`base` z lub bez parametrów można używać słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="21052-131">The `base` keyword can be used with or without parameters.</span></span> <span data-ttu-id="21052-132">Wszystkie parametry konstruktora mogą być używane jako parametry `base`, lub jako część wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="21052-132">Any parameters to the constructor can be used as parameters to `base`, or as part of an expression.</span></span> <span data-ttu-id="21052-133">Aby uzyskać więcej informacji, zobacz [podstawowej](../../../csharp/language-reference/keywords/base.md).</span><span class="sxs-lookup"><span data-stu-id="21052-133">For more information, see [base](../../../csharp/language-reference/keywords/base.md).</span></span>  
  
 <span data-ttu-id="21052-134">W klasie pochodnej, jeśli konstruktora klasy podstawowej nie jest jawnie wywołać przy użyciu `base` — słowo kluczowe, Konstruktor domyślny, jeśli istnieje, jest nazywany niejawnie.</span><span class="sxs-lookup"><span data-stu-id="21052-134">In a derived class, if a base-class constructor is not called explicitly by using the `base` keyword, the default constructor, if there is one, is called implicitly.</span></span> <span data-ttu-id="21052-135">Oznacza to, że następujące deklaracje konstruktora skutecznie są takie same:</span><span class="sxs-lookup"><span data-stu-id="21052-135">This means that the following constructor declarations are effectively the same:</span></span>  
  
 [!code-csharp[csProgGuideObjects#58](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_6.cs)]  
  
 [!code-csharp[csProgGuideObjects#57](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_7.cs)]  
  
 <span data-ttu-id="21052-136">Jeśli klasą podstawową nie oferuje konstruktora domyślnego, klasy pochodnej wprowadzić jawnego wywołania konstruktora podstawowego przy użyciu `base`.</span><span class="sxs-lookup"><span data-stu-id="21052-136">If a base class does not offer a default constructor, the derived class must make an explicit call to a base constructor by using `base`.</span></span>  
  
 <span data-ttu-id="21052-137">Konstruktor może wywołać innego konstruktora w tym samym obiekcie za pomocą [to](../../../csharp/language-reference/keywords/this.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="21052-137">A constructor can invoke another constructor in the same object by using the [this](../../../csharp/language-reference/keywords/this.md) keyword.</span></span> <span data-ttu-id="21052-138">Podobnie jak `base`, `this` mogą być używane z lub bez parametrów i wszelkie parametry w Konstruktorze są dostępne jako parametry `this`, lub jako część wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="21052-138">Like `base`, `this` can be used with or without parameters, and any parameters in the constructor are available as parameters to `this`, or as part of an expression.</span></span> <span data-ttu-id="21052-139">Na przykład drugi Konstruktor w poprzednim przykładzie można ponownego napisania przy użyciu `this`:</span><span class="sxs-lookup"><span data-stu-id="21052-139">For example, the second constructor in the previous example can be rewritten using `this`:</span></span>  
  
 [!code-csharp[csProgGuideObjects#59](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_8.cs)]  
  
 <span data-ttu-id="21052-140">Korzystanie z `this` — słowo kluczowe w poprzednim przykładzie powoduje, że ten konstruktor do wywołania:</span><span class="sxs-lookup"><span data-stu-id="21052-140">The use of the `this` keyword in the previous example causes this constructor to be called:</span></span>  
  
 [!code-csharp[csProgGuideObjects#60](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/using-constructors_9.cs)]  
  
 <span data-ttu-id="21052-141">Konstruktory może być oznaczony jako [publicznego](../../../csharp/language-reference/keywords/public.md), [prywatnej](../../../csharp/language-reference/keywords/private.md), [chronione](../../../csharp/language-reference/keywords/protected.md), [wewnętrzny](../../../csharp/language-reference/keywords/internal.md), [chronionych wewnętrznych](../../../csharp/language-reference/keywords/protected-internal.md)lub [prywatne chronione](../../../csharp/language-reference/keywords/private-protected.md).</span><span class="sxs-lookup"><span data-stu-id="21052-141">Constructors can be marked as [public](../../../csharp/language-reference/keywords/public.md), [private](../../../csharp/language-reference/keywords/private.md), [protected](../../../csharp/language-reference/keywords/protected.md), [internal](../../../csharp/language-reference/keywords/internal.md), [protected internal](../../../csharp/language-reference/keywords/protected-internal.md) or [private protected](../../../csharp/language-reference/keywords/private-protected.md).</span></span> <span data-ttu-id="21052-142">Te modyfikatorów dostępu zdefiniuj, jak użytkownicy klasy można utworzyć klasy.</span><span class="sxs-lookup"><span data-stu-id="21052-142">These access modifiers define how users of the class can construct the class.</span></span> <span data-ttu-id="21052-143">Aby uzyskać więcej informacji, zobacz [modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span><span class="sxs-lookup"><span data-stu-id="21052-143">For more information, see [Access Modifiers](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).</span></span>  
  
 <span data-ttu-id="21052-144">Konstruktor może być zadeklarowany jako statyczny przy użyciu [statycznych](../../../csharp/language-reference/keywords/static.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="21052-144">A constructor can be declared static by using the [static](../../../csharp/language-reference/keywords/static.md) keyword.</span></span> <span data-ttu-id="21052-145">Konstruktory statyczne są nazywane automatycznie, bezpośrednio przed wszystkie pola statyczne są dostępne i są zazwyczaj używane do zainicjowania statyczni członkowie klas.</span><span class="sxs-lookup"><span data-stu-id="21052-145">Static constructors are called automatically, immediately before any static fields are accessed, and are generally used to initialize static class members.</span></span> <span data-ttu-id="21052-146">Aby uzyskać więcej informacji, zobacz [konstruktory statyczne](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span><span class="sxs-lookup"><span data-stu-id="21052-146">For more information, see [Static Constructors](../../../csharp/programming-guide/classes-and-structs/static-constructors.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="21052-147">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="21052-147">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="21052-148">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21052-148">See Also</span></span>  
 [<span data-ttu-id="21052-149">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="21052-149">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="21052-150">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="21052-150">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)  
 [<span data-ttu-id="21052-151">Konstruktory</span><span class="sxs-lookup"><span data-stu-id="21052-151">Constructors</span></span>](../../../csharp/programming-guide/classes-and-structs/constructors.md)  
 [<span data-ttu-id="21052-152">Finalizatory</span><span class="sxs-lookup"><span data-stu-id="21052-152">Finalizers</span></span>](../../../csharp/programming-guide/classes-and-structs/destructors.md)