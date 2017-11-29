---
title: "Tworzenie klasy utrzymującej funkcje DLL"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- COM interop, DLL functions
- unmanaged functions
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, creating class for functions
- DLL functions
ms.assetid: e08e4c34-0223-45f7-aa55-a3d8dd979b0f
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ac3c3542e46168f5903ff0425740a29f16253733
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="creating-a-class-to-hold-dll-functions"></a><span data-ttu-id="dffc4-102">Tworzenie klasy utrzymującej funkcje DLL</span><span class="sxs-lookup"><span data-stu-id="dffc4-102">Creating a Class to Hold DLL Functions</span></span>
<span data-ttu-id="dffc4-103">Zawijanie często używanych funkcji DLL w klasie zarządzanej jest efektywnym sposobem Hermetyzowanie funkcjonalność platformy.</span><span class="sxs-lookup"><span data-stu-id="dffc4-103">Wrapping a frequently used DLL function in a managed class is an effective approach to encapsulate platform functionality.</span></span> <span data-ttu-id="dffc4-104">Chociaż nie jest to konieczne, aby to zrobić w każdym przypadku, podając otoki klasy jest wygodne, ponieważ definiujący funkcje DLL może być skomplikowane i podatne na błędy.</span><span class="sxs-lookup"><span data-stu-id="dffc4-104">Although it is not mandatory to do so in every case, providing a class wrapper is convenient because defining DLL functions can be cumbersome and error-prone.</span></span> <span data-ttu-id="dffc4-105">Programowanie w Visual Basic lub C# musisz zadeklarować funkcji DLL w obrębie klasy lub module języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="dffc4-105">If you are programming in Visual Basic or C#, you must declare DLL functions within a class or Visual Basic module.</span></span>  
  
 <span data-ttu-id="dffc4-106">W obrębie klasy należy zdefiniować statycznej metody dla każdej funkcji DLL, który ma zostać wywołana.</span><span class="sxs-lookup"><span data-stu-id="dffc4-106">Within a class, you define a static method for each DLL function you want to call.</span></span> <span data-ttu-id="dffc4-107">Definicja może zawierać dodatkowe informacje, takie jak zestaw znaków lub Konwencja wywoływania używany do przekazywania argumenty metody; pomijając te informacje, wybierz ustawienia domyślne.</span><span class="sxs-lookup"><span data-stu-id="dffc4-107">The definition can include additional information, such as the character set or the calling convention used in passing method arguments; by omitting this information, you select the default settings.</span></span> <span data-ttu-id="dffc4-108">Pełną listę opcji deklaracji i domyślne ustawienia, zobacz [tworzenie prototypów w kodzie zarządzane](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span><span class="sxs-lookup"><span data-stu-id="dffc4-108">For a complete list of declaration options and their default settings, see [Creating Prototypes in Managed Code](../../../docs/framework/interop/creating-prototypes-in-managed-code.md).</span></span>  
  
 <span data-ttu-id="dffc4-109">Po opakowaniu mogą wywoływać metod w funkcji, jak wywoływać metod w statycznej funkcji.</span><span class="sxs-lookup"><span data-stu-id="dffc4-109">Once wrapped, you can call methods on the function as you call methods on any other static function.</span></span> <span data-ttu-id="dffc4-110">Wywołanie platformy uchwytów odpowiadającego wyeksportowanej funkcji automatycznie.</span><span class="sxs-lookup"><span data-stu-id="dffc4-110">Platform invoke handles the underlying exported function automatically.</span></span>  
  
 <span data-ttu-id="dffc4-111">Podczas projektowania zarządzanej klasy dla platformy wywołania, należy wziąć pod uwagę relacje między klasy i funkcje biblioteki DLL.</span><span class="sxs-lookup"><span data-stu-id="dffc4-111">When designing a managed class for platform invoke, consider the relationships between classes and DLL functions.</span></span> <span data-ttu-id="dffc4-112">Możesz na przykład:</span><span class="sxs-lookup"><span data-stu-id="dffc4-112">For example, you can:</span></span>  
  
-   <span data-ttu-id="dffc4-113">Deklarowanie funkcji DLL w ramach istniejącej klasy.</span><span class="sxs-lookup"><span data-stu-id="dffc4-113">Declare DLL functions within an existing class.</span></span>  
  
-   <span data-ttu-id="dffc4-114">Utwórz poszczególnych klas dla każdej funkcji DLL, zachowanie funkcji w izolowanej i łatwe do odnalezienia.</span><span class="sxs-lookup"><span data-stu-id="dffc4-114">Create an individual class for each DLL function, keeping functions isolated and easy to find.</span></span>  
  
-   <span data-ttu-id="dffc4-115">Utwórz jedną klasę dla zestawu powiązanych funkcji DLL tworzą logiczne grupy i zmniejsza obciążenie.</span><span class="sxs-lookup"><span data-stu-id="dffc4-115">Create one class for a set of related DLL functions to form logical groupings and reduce overhead.</span></span>  
  
 <span data-ttu-id="dffc4-116">Można określić nazwę klasy i metody jako użytkownik należy.</span><span class="sxs-lookup"><span data-stu-id="dffc4-116">You can name the class and its methods as you please.</span></span> <span data-ttu-id="dffc4-117">Aby uzyskać przykłady pokazujące, które pokazują, jak utworzyć. Deklaracje opartych na potrzeby używania z platformy invoke, zobacz [organizowanie danych za pomocą wywołania platformy](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="dffc4-117">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](../../../docs/framework/interop/marshaling-data-with-platform-invoke.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dffc4-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dffc4-118">See Also</span></span>  
 [<span data-ttu-id="dffc4-119">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="dffc4-119">Consuming Unmanaged DLL Functions</span></span>](../../../docs/framework/interop/consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="dffc4-120">Identyfikowanie funkcji w bibliotekach DLL</span><span class="sxs-lookup"><span data-stu-id="dffc4-120">Identifying Functions in DLLs</span></span>](../../../docs/framework/interop/identifying-functions-in-dlls.md)  
 [<span data-ttu-id="dffc4-121">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="dffc4-121">Creating Prototypes in Managed Code</span></span>](../../../docs/framework/interop/creating-prototypes-in-managed-code.md)  
 [<span data-ttu-id="dffc4-122">Wywoływanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="dffc4-122">Calling a DLL Function</span></span>](../../../docs/framework/interop/calling-a-dll-function.md)